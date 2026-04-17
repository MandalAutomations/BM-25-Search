# REST API endpoints for dependency review

Use the REST API to interact with dependency changes.

## About dependency review

You can use the REST API to view dependency changes, and the security impact of these changes, before you add them to your environment. You can view the diff of dependencies between two commits of a repository, including vulnerability data for any version updates with known vulnerabilities. For more information about dependency review, see [About dependency review](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get a diff of the dependencies between commits

```
GET /repos/{owner}/{repo}/dependency-graph/compare/{basehead}
```

Gets the diff of the dependency changes between two commits of a repository, based on the changes to the dependency manifests made in those commits.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`basehead`** (string) (required)
  The base and head Git revisions to compare. The Git revisions will be resolved to commit SHAs. Named revisions will be resolved to their corresponding HEAD commits, and an appropriate merge base will be determined. This parameter expects the format {base}...{head}.

* **`name`** (string)
  The full path, relative to the repository root, of the dependency manifest file.

### HTTP response status codes

* **200** - OK

* **403** - Response for a private repository when GitHub Advanced Security is not enabled, or if used against a fork

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dependency-graph/compare/BASEHEAD
```

**Response schema (Status: 200):**

Array of objects:

* `change_type`: required, string, enum: `added`, `removed`
* `manifest`: required, string
* `ecosystem`: required, string
* `name`: required, string
* `version`: required, string
* `package_url`: required, string or null
* `license`: required, string or null
* `source_repository_url`: required, string or null
* `vulnerabilities`: required, array of objects:
  * `severity`: required, string
  * `advisory_ghsa_id`: required, string
  * `advisory_summary`: required, string
  * `advisory_url`: required, string
* `scope`: required, string, enum: `unknown`, `runtime`, `development`