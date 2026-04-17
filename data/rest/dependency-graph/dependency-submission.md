# REST API endpoints for dependency submission

Use the REST API to submit dependencies.

## About dependency submissions

You can use the REST API to submit dependencies for a project. This enables you to add dependencies, such as those resolved when software is compiled or built, to GitHub's dependency graph feature, providing a more complete picture of all of your project's dependencies.

The dependency graph shows any dependencies you submit using the API in addition to any dependencies that are identified from manifest or lock files in the repository (for example, a `package-lock.json` file in a JavaScript project). For more information about viewing the dependency graph, see [Exploring the dependencies of a repository](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/exploring-the-dependencies-of-a-repository#viewing-the-dependency-graph).

Submitted dependencies will receive Dependabot alerts and Dependabot security updates for any known vulnerabilities. You will only get Dependabot alerts for dependencies that are from one of the supported ecosystems for the GitHub Advisory Database. For more information about these ecosystems, see [About the GitHub Advisory database](/en/code-security/security-advisories/global-security-advisories/about-the-github-advisory-database#github-reviewed-advisories). For transitive dependencies submitted via the dependency submission API, Dependabot will automatically open pull requests to update the parent dependency, if an update is available.

Submitted dependencies will be shown in dependency review, but are *not* available in your organization's dependency insights.

> \[!NOTE]
> The dependency review API and the dependency submission API work together. This means that the dependency review API will include dependencies submitted via the dependency submission API.

You can submit dependencies in the form of a snapshot. A snapshot is a set of dependencies associated with a commit SHA and other metadata, that reflects the current state of your repository for a commit. You can choose to use pre-made actions or create your own actions to submit your dependencies in the required format each time your project is built. For more information, see [Using the dependency submission API](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/using-the-dependency-submission-api).

You can submit multiple sets of dependencies to be included in your dependency graph. The REST API uses the `job.correlator` property and the `detector.name` category of the snapshot to ensure the latest submissions for each workflow get shown. The `correlator` property itself is the primary field you will use to keep independent submissions distinct. An example `correlator` could be a simple combination of two variables available in actions runs: `<GITHUB_WORKFLOW> <GITHUB_JOB>`.

A repository can use multiple methods for dependency submission, which can cause the same package manifest to be scanned multiple times, potentially with different outputs from each scan. Dependency graph uses deduplication logic to parse the outputs, prioritizing the most accurate information for each manifest file.

Dependency graph displays only one instance of each manifest file using the following precedence rules.

1. **User submissions** take the highest priority, because they are usually created during artifact builds they have the most complete information.
   * If there are multiple manual snapshots from different detectors, they are sorted alphabetically by correlator and the first one used.
   * If there are two correlators with the same detector, the resolved dependencies are merged. For more information about correlators and detectors, see [REST API endpoints for dependency submission](/en/rest/dependency-graph/dependency-submission).
2. **Automatic submissions** have the second-highest priority since they are also created during artifact builds, but are not submitted by users.
3. **Static analysis results** are used when no other data is available.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Create a snapshot of dependencies for a repository

```
POST /repos/{owner}/{repo}/dependency-graph/snapshots
```

Create a new snapshot of a repository's dependencies.
The authenticated user must have access to the repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

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

* **`version`** (integer) (required)
  The version of the repository snapshot submission.

* **`job`** (object) (required)
  * **`id`** (string) (required)
    The external ID of the job.
  * **`correlator`** (string) (required)
    Correlator provides a key that is used to group snapshots submitted over time. Only the "latest" submitted snapshot for a given combination of job.correlator and detector.name will be considered when calculating a repository's current dependencies. Correlator should be as unique as it takes to distinguish all detection runs for a given "wave" of CI workflow you run. If you're using GitHub Actions, a good default value for this could be the environment variables GITHUB\_WORKFLOW and GITHUB\_JOB concatenated together. If you're using a build matrix, then you'll also need to add additional key(s) to distinguish between each submission inside a matrix variation.
  * **`html_url`** (string)
    The url for the job.

* **`sha`** (string) (required)
  The commit SHA associated with this dependency snapshot. Maximum length: 40 characters.

* **`ref`** (string) (required)
  The repository branch that triggered this snapshot.

* **`detector`** (object) (required)
  A description of the detector used.
  * **`name`** (string) (required)
    The name of the detector used.
  * **`version`** (string) (required)
    The version of the detector used.
  * **`url`** (string) (required)
    The url of the detector used.

* **`metadata`** (object)
  User-defined metadata to store domain-specific information limited to 8 keys with scalar values.

* **`manifests`** (object)
  A collection of package manifests, which are a collection of related dependencies declared in a file or representing a logical group of dependencies.
  * **`key`** (object)
    A user-defined key to represent an item in manifests.
    * **`name`** (string) (required)
      The name of the manifest.
    * **`file`** (object)
      * **`source_location`** (string)
        The path of the manifest file relative to the root of the Git repository.
    * **`metadata`** (object)
      User-defined metadata to store domain-specific information limited to 8 keys with scalar values.
    * **`resolved`** (object)
      A collection of resolved package dependencies.
      * **`key`** (object)
        A user-defined key to represent an item in resolved.
        * **`package_url`** (string)
          Package-url (PURL) of dependency. See <https://github.com/package-url/purl-spec> for more details.
        * **`metadata`** (object)
          User-defined metadata to store domain-specific information limited to 8 keys with scalar values.
        * **`relationship`** (string)
          A notation of whether a dependency is requested directly by this manifest or is a dependency of another dependency.
          Can be one of: `direct`, `indirect`
        * **`scope`** (string)
          A notation of whether the dependency is required for the primary build artifact (runtime) or is only used for development. Future versions of this specification may allow for more granular scopes.
          Can be one of: `runtime`, `development`
        * **`dependencies`** (array of strings)
          Array of package-url (PURLs) of direct child dependencies.

* **`scanned`** (string) (required)
  The time at which the snapshot was scanned.

### HTTP response status codes

* **201** - Created

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/dependency-graph/snapshots \
  -d '{
  "version": 0,
  "sha": "ce587453ced02b1526dfb4cb910479d431683101",
  "ref": "refs/heads/main",
  "job": {
    "correlator": "yourworkflowname_youractionname",
    "id": "yourrunid"
  },
  "detector": {
    "name": "octo-detector",
    "version": "0.0.1",
    "url": "https://github.com/octo-org/octo-repo"
  },
  "scanned": "2022-06-14T20:25:00Z",
  "manifests": {
    "package-lock.json": {
      "name": "package-lock.json",
      "file": {
        "source_location": "src/package-lock.json"
      },
      "resolved": {
        "@actions/core": {
          "package_url": "pkg:/npm/%40actions/core@1.1.9",
          "dependencies": [
            "@actions/http-client"
          ]
        },
        "@actions/http-client": {
          "package_url": "pkg:/npm/%40actions/http-client@1.0.7",
          "dependencies": [
            "tunnel"
          ]
        },
        "tunnel": {
          "package_url": "pkg:/npm/tunnel@0.0.6"
        }
      }
    }
  }
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `created_at`: required, string
* `result`: required, string
* `message`: required, string