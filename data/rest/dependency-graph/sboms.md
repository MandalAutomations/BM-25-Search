# REST API endpoints for software bill of materials (SBOM)

Use the REST API to export the software bill of materials (SBOM) for a repository.

If you have at least read access to the repository, you can export the dependency graph for the repository as an SPDX-compatible, Software Bill of Materials (SBOM), via the GitHub UI or GitHub REST API. For more information, see [Exporting a software bill of materials for your repository](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/exporting-a-software-bill-of-materials-for-your-repository).

This article gives details about the REST API endpoint.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Export a software bill of materials (SBOM) for a repository.

```
GET /repos/{owner}/{repo}/dependency-graph/sbom
```

Exports the software bill of materials (SBOM) for a repository in SPDX JSON format.

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

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dependency-graph/sbom
```

**Response schema (Status: 200):**

* `sbom`: required, object:
  * `SPDXID`: required, string
  * `spdxVersion`: required, string
  * `comment`: string
  * `creationInfo`: required, object:
    * `created`: required, string
    * `creators`: required, array of string
  * `name`: required, string
  * `dataLicense`: required, string
  * `documentNamespace`: required, string
  * `packages`: required, array of objects:
    * `SPDXID`: string
    * `name`: string
    * `versionInfo`: string
    * `downloadLocation`: string
    * `filesAnalyzed`: boolean
    * `licenseConcluded`: string
    * `licenseDeclared`: string
    * `supplier`: string
    * `copyrightText`: string
    * `externalRefs`: array of objects:
      * `referenceCategory`: required, string
      * `referenceLocator`: required, string
      * `referenceType`: required, string
  * `relationships`: array of objects:
    * `relationshipType`: string
    * `spdxElementId`: string
    * `relatedSpdxElement`: string

## Fetch a software bill of materials (SBOM) for a repository.

```
GET /repos/{owner}/{repo}/dependency-graph/sbom/fetch-report/{sbom_uuid}
```

Fetches a previously generated software bill of materials (SBOM) for a repository.
When the SBOM is ready, the response is a 302 redirect to a temporary download URL for the SBOM in SPDX JSON format.
The generated SBOM report may be retained for up to one week from the original request.
The temporary download URL returned by this endpoint expires separately, and its expiry is set when the fetch request is made.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

* **`sbom_uuid`** (string) (required)
  The unique identifier of the SBOM export.

### HTTP response status codes

* **202** - SBOM is still being processed, no content is returned.

* **302** - Redirects to a temporary download URL for the completed SBOM.

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dependency-graph/sbom/fetch-report/SBOM_UUID
```

**Response schema (Status: 202):**

## Request generation of a software bill of materials (SBOM) for a repository.

```
GET /repos/{owner}/{repo}/dependency-graph/sbom/generate-report
```

Triggers a job to generate a software bill of materials (SBOM) for a repository in SPDX JSON format.

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

* **201** - Created

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dependency-graph/sbom/generate-report
```

**Response schema (Status: 201):**

* `sbom_url`: string