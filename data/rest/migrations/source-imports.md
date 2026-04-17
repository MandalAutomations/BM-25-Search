# REST API endpoints for source imports

Use the REST API to start an import from a Git source repository.

## About source imports

> \[!WARNING]
> Due to very low levels of usage and available alternatives, the Source Imports API has been retired. For more details and alternatives, see the [changelog](https://gh.io/source-imports-api-deprecation).

You can use these endpoints to start an import from a Git repository hosted with another service. This is the same functionality as the GitHub Importer. For more information, see [Importing a repository with GitHub Importer](/en/migrations/importing-source-code/using-github-importer/importing-a-repository-with-github-importer). A typical source import would start the import and then (optionally) update the authors and/or update the preference for using Git LFS if large files exist in the import. You can also create a webhook that listens for the [`RepositoryImportEvent`](/en/webhooks-and-events/webhooks/webhook-events-and-payloads#repository_import) to find out the status of the import.

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

The following diagram provides a more detailed example:

```text
+---------+                     +--------+                              +---------------------+
| Tooling |                     | GitHub |                              | Original Repository |
+---------+                     +--------+                              +---------------------+
     |                              |                                              |
     |  Start import                |                                              |
     |----------------------------->|                                              |
     |                              |                                              |
     |                              |  Download source data                        |
     |                              |--------------------------------------------->|
     |                              |                        Begin streaming data  |
     |                              |<---------------------------------------------|
     |                              |                                              |
     |  Get import progress         |                                              |
     |----------------------------->|                                              |
     |       "status": "importing"  |                                              |
     |<-----------------------------|                                              |
     |                              |                                              |
     |  Get commit authors          |                                              |
     |----------------------------->|                                              |
     |                              |                                              |
     |  Map a commit author         |                                              |
     |----------------------------->|                                              |
     |                              |                                              |
     |                              |                                              |
     |                              |                       Finish streaming data  |
     |                              |<---------------------------------------------|
     |                              |                                              |
     |                              |  Rewrite commits with mapped authors         |
     |                              |------+                                       |
     |                              |      |                                       |
     |                              |<-----+                                       |
     |                              |                                              |
     |                              |  Update repository on GitHub                 |
     |                              |------+                                       |
     |                              |      |                                       |
     |                              |<-----+                                       |
     |                              |                                              |
     |  Map a commit author         |                                              |
     |----------------------------->|                                              |
     |                              |  Rewrite commits with mapped authors         |
     |                              |------+                                       |
     |                              |      |                                       |
     |                              |<-----+                                       |
     |                              |                                              |
     |                              |  Update repository on GitHub                 |
     |                              |------+                                       |
     |                              |      |                                       |
     |                              |<-----+                                       |
     |                              |                                              |
     |  Get large files             |                                              |
     |----------------------------->|                                              |
     |                              |                                              |
     |  opt_in to Git LFS           |                                              |
     |----------------------------->|                                              |
     |                              |  Rewrite commits for large files             |
     |                              |------+                                       |
     |                              |      |                                       |
     |                              |<-----+                                       |
     |                              |                                              |
     |                              |  Update repository on GitHub                 |
     |                              |------+                                       |
     |                              |      |                                       |
     |                              |<-----+                                       |
     |                              |                                              |
     |  Get import progress         |                                              |
     |----------------------------->|                                              |
     |        "status": "complete"  |                                              |
     |<-----------------------------|                                              |
     |                              |                                              |
     |                              |                                              |
```

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get an import status

```
GET /repos/{owner}/{repo}/import
```

View the progress of an import.
Warning

Endpoint closing down notice: Due to very low levels of usage and available alternatives, this endpoint is closing down and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the changelog.

Import status
This section includes details about the possible values of the status field of the Import Progress response.
An import that does not have errors will progress through these steps:

detecting - the "detection" step of the import is in progress because the request did not include a vcs parameter. The import is identifying the type of source control present at the URL.
importing - the "raw" step of the import is in progress. This is where commit data is fetched from the original repository. The import progress response will include commit\_count (the total number of raw commits that will be imported) and percent (0 - 100, the current progress through the import).
mapping - the "rewrite" step of the import is in progress. This is where SVN branches are converted to Git branches, and where author updates are applied. The import progress response does not include progress information.
pushing - the "push" step of the import is in progress. This is where the importer updates the repository on GitHub. The import progress response will include push\_percent, which is the percent value reported by git push when it is "Writing objects".
complete - the import is complete, and the repository is ready on GitHub.

If there are problems, you will see one of these in the status field:

auth\_failed - the import requires authentication in order to connect to the original repository. To update authentication for the import, please see the Update an import section.
error - the import encountered an error. The import progress response will include the failed\_step and an error message. Contact GitHub Support for more information.
detection\_needs\_auth - the importer requires authentication for the originating repository to continue detection. To update authentication for the import, please see the Update an import section.
detection\_found\_nothing - the importer didn't recognize any source control at the URL. To resolve, Cancel the import and retry with the correct URL.
detection\_found\_multiple - the importer found several projects or repositories at the provided URL. When this is the case, the Import Progress response will also include a project\_choices field with the possible project choices as values. To update project choice, please see the Update an import section.

The project\_choices field
When multiple projects are found at the provided URL, the response hash will include a project\_choices field, the value of which is an array of hashes each representing a project choice. The exact key/value pairs of the project hashes will differ depending on the version control type.
Git LFS related fields
This section includes details about Git LFS related fields that may be present in the Import Progress response.

use\_lfs - describes whether the import has been opted in or out of using Git LFS. The value can be opt\_in, opt\_out, or undecided if no action has been taken.
has\_large\_files - the boolean value describing whether files larger than 100MB were found during the importing step.
large\_files\_size - the total size in gigabytes of files larger than 100MB found in the originating repository.
large\_files\_count - the total number of files larger than 100MB found in the originating repository. To see a list of these files, make a "Get Large Files" request.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **503** - Unavailable due to service under maintenance.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/import
```

**Response schema (Status: 200):**

* `vcs`: required, string or null
* `use_lfs`: boolean
* `vcs_url`: required, string
* `svc_root`: string
* `tfvc_project`: string
* `status`: required, string, enum: `auth`, `error`, `none`, `detecting`, `choose`, `auth_failed`, `importing`, `mapping`, `waiting_to_push`, `pushing`, `complete`, `setup`, `unknown`, `detection_found_multiple`, `detection_found_nothing`, `detection_needs_auth`
* `status_text`: string or null
* `failed_step`: string or null
* `error_message`: string or null
* `import_percent`: integer or null
* `commit_count`: integer or null
* `push_percent`: integer or null
* `has_large_files`: boolean
* `large_files_size`: integer
* `large_files_count`: integer
* `project_choices`: array of objects:
  * `vcs`: string
  * `tfvc_project`: string
  * `human_name`: string
* `message`: string
* `authors_count`: integer or null
* `url`: required, string, format: uri
* `html_url`: required, string, format: uri
* `authors_url`: required, string, format: uri
* `repository_url`: required, string, format: uri
* `svn_root`: string

## Start an import

```
PUT /repos/{owner}/{repo}/import
```

Start a source import to a GitHub repository using GitHub Importer.
Importing into a GitHub repository with GitHub Actions enabled is not supported and will
return a status 422 Unprocessable Entity response.
Warning

Endpoint closing down notice: Due to very low levels of usage and available alternatives, this endpoint is closing down and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the changelog.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

* **`vcs_url`** (string) (required)
  The URL of the originating repository.

* **`vcs`** (string)
  The originating VCS type. Without this parameter, the import job will take additional time to detect the VCS type before beginning the import. This detection step will be reflected in the response.
  Can be one of: `subversion`, `git`, `mercurial`, `tfvc`

* **`vcs_username`** (string)
  If authentication is required, the username to provide to vcs\_url.

* **`vcs_password`** (string)
  If authentication is required, the password to provide to vcs\_url.

* **`tfvc_project`** (string)
  For a tfvc import, the name of the project that is being imported.

### HTTP response status codes

* **201** - Created

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

* **503** - Unavailable due to service under maintenance.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/import \
  -d '{
  "vcs": "subversion",
  "vcs_url": "http://svn.mycompany.com/svn/myproject",
  "vcs_username": "octocat",
  "vcs_password": "secret"
}'
```

**Response schema (Status: 201):**

Same response schema as [Get an import status](#get-an-import-status).

## Update an import

```
PATCH /repos/{owner}/{repo}/import
```

An import can be updated with credentials or a project choice by passing in the appropriate parameters in this API
request. If no parameters are provided, the import will be restarted.
Some servers (e.g. TFS servers) can have several projects at a single URL. In those cases the import progress will
have the status detection\_found\_multiple and the Import Progress response will include a project\_choices array.
You can select the project to import by providing one of the objects in the project\_choices array in the update request.
Warning

Endpoint closing down notice: Due to very low levels of usage and available alternatives, this endpoint is closing down and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the changelog.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

* **`vcs_username`** (string)
  The username to provide to the originating repository.

* **`vcs_password`** (string)
  The password to provide to the originating repository.

* **`vcs`** (string)
  The type of version control system you are migrating from.
  Can be one of: `subversion`, `tfvc`, `git`, `mercurial`

* **`tfvc_project`** (string)
  For a tfvc import, the name of the project that is being imported.

### HTTP response status codes

* **200** - OK

* **503** - Unavailable due to service under maintenance.

### Code examples

#### Update authentication for an import

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/import \
  -d '{
  "vcs_username": "octocat",
  "vcs_password": "secret"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an import status](#get-an-import-status).

#### Updating the project choice

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/import \
  -d '{
  "vcs": "tfvc",
  "tfvc_project": "project1",
  "human_name": "project1 (tfs)"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an import status](#get-an-import-status).

#### Restarting an import

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/import
```

**Response schema (Status: 200):**

Same response schema as [Get an import status](#get-an-import-status).

## Cancel an import

```
DELETE /repos/{owner}/{repo}/import
```

Stop an import for a repository.
Warning

Endpoint closing down notice: Due to very low levels of usage and available alternatives, this endpoint is closing down and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the changelog.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **204** - No Content

* **503** - Unavailable due to service under maintenance.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/import
```

**Response schema (Status: 204):**

## Get commit authors

```
GET /repos/{owner}/{repo}/import/authors
```

Each type of source control system represents authors in a different way. For example, a Git commit author has a display name and an email address, but a Subversion commit author just has a username. The GitHub Importer will make the author information valid, but the author might not be correct. For example, it will change the bare Subversion username hubot into something like hubot <hubot@12341234-abab-fefe-8787-fedcba987654>.
This endpoint and the Map a commit author endpoint allow you to provide correct Git author information.
Warning

Endpoint closing down notice: Due to very low levels of usage and available alternatives, this endpoint is closing down and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the changelog.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`since`** (integer)
  A user ID. Only return users with an ID greater than this ID.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **503** - Unavailable due to service under maintenance.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/import/authors
```

**Response schema (Status: 200):**

Array of `Porter Author`:

* `id`: required, integer
* `remote_id`: required, string
* `remote_name`: required, string
* `email`: required, string
* `name`: required, string
* `url`: required, string, format: uri
* `import_url`: required, string, format: uri

## Map a commit author

```
PATCH /repos/{owner}/{repo}/import/authors/{author_id}
```

Update an author's identity for the import. Your application can continue updating authors any time before you push
new commits to the repository.
Warning

Endpoint closing down notice: Due to very low levels of usage and available alternatives, this endpoint is closing down and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the changelog.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`author_id`** (integer) (required)

#### Body parameters

* **`email`** (string)
  The new Git author email.

* **`name`** (string)
  The new Git author name.

### HTTP response status codes

* **200** - OK

* **404** - Resource not found

* **422** - Validation failed, or the endpoint has been spammed.

* **503** - Unavailable due to service under maintenance.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/import/authors/AUTHOR_ID \
  -d '{
  "email": "hubot@github.com",
  "name": "Hubot the Robot"
}'
```

**Response schema (Status: 200):**

* `id`: required, integer
* `remote_id`: required, string
* `remote_name`: required, string
* `email`: required, string
* `name`: required, string
* `url`: required, string, format: uri
* `import_url`: required, string, format: uri

## Get large files

```
GET /repos/{owner}/{repo}/import/large_files
```

List files larger than 100MB found during the import
Warning

Endpoint closing down notice: Due to very low levels of usage and available alternatives, this endpoint is closing down and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the changelog.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **503** - Unavailable due to service under maintenance.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/import/large_files
```

**Response schema (Status: 200):**

Array of `Porter Large File`:

* `ref_name`: required, string
* `path`: required, string
* `oid`: required, string
* `size`: required, integer

## Update Git LFS preference

```
PATCH /repos/{owner}/{repo}/import/lfs
```

You can import repositories from Subversion, Mercurial, and TFS that include files larger than 100MB. This ability
is powered by Git LFS.
You can learn more about our LFS feature and working with large files on our help
site.
Warning

Endpoint closing down notice: Due to very low levels of usage and available alternatives, this endpoint is closing down and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the changelog.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

* **`use_lfs`** (string) (required)
  Whether to store large files during the import. opt\_in means large files will be stored using Git LFS. opt\_out means large files will be removed during the import.
  Can be one of: `opt_in`, `opt_out`

### HTTP response status codes

* **200** - OK

* **422** - Validation failed, or the endpoint has been spammed.

* **503** - Unavailable due to service under maintenance.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/import/lfs \
  -d '{
  "use_lfs": "opt_in"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get an import status](#get-an-import-status).