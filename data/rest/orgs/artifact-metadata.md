# REST API endpoints for artifact metadata

Use these endpoints to retrieve and manage metadata for artifacts in your organization. Artifact metadata provides information about build artifacts, their provenance, and related details.

You can use these endpoints to upload storage and deployment records for software that your organization builds with GitHub Actions. The records are displayed on the organization's linked artifacts page. See [About linked artifacts](/en/code-security/concepts/supply-chain-security/linked-artifacts).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Create an artifact deployment record

```
POST /orgs/{org}/artifacts/metadata/deployment-record
```

Create or update deployment records for an artifact associated
with an organization.
This endpoint allows you to record information about a specific
artifact, such as its name, digest, environments, cluster, and
deployment.
The deployment name has to be uniqe within a cluster (i.e a
combination of logical, physical environment and cluster) as it
identifies unique deployment.
Multiple requests for the same combination of logical, physical
environment, cluster and deployment name will only create one
record, successive request will update the existing record.
This allows for a stable tracking of a deployment where the actual
deployed artifact can change over time.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`name`** (string) (required)
  The name of the artifact.

* **`digest`** (string) (required)
  The hex encoded digest of the artifact.

* **`version`** (string)
  The artifact version.

* **`status`** (string) (required)
  The status of the artifact. Can be either deployed or decommissioned.
  Can be one of: `deployed`, `decommissioned`

* **`logical_environment`** (string) (required)
  The stage of the deployment.

* **`physical_environment`** (string)
  The physical region of the deployment.

* **`cluster`** (string)
  The deployment cluster.

* **`deployment_name`** (string) (required)
  The unique identifier for the deployment represented by the new record. To accommodate differing
  containers and namespaces within a cluster, the following format is recommended:
  {namespaceName}-{deploymentName}-{containerName}.

* **`tags`** (object)
  The tags associated with the deployment.

* **`runtime_risks`** (array of strings)
  A list of runtime risks associated with the deployment.
  Supported values are: critical-resource, internet-exposed, lateral-movement, sensitive-data

* **`github_repository`** (string)
  The name of the GitHub repository associated with the artifact. This should be used
  when there are no provenance attestations available for the artifact. The repository
  must belong to the organization specified in the path parameter.
  If a provenance attestation is available for the artifact, the API will use
  the repository information from the attestation instead of this parameter.

* **`return_records`** (boolean)
  If true, the endpoint will return the created or updated record in the response body.
  Default: `true`

### HTTP response status codes

* **200** - Artifact deployment record stored successfully.

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/artifacts/metadata/deployment-record \
  -d '{
  "name": "awesome-image",
  "digest": "sha256:1bb1e949e55dcefc6353e7b36c8897d2a107d8e8dca49d4e3c0ea8493fc0bc72",
  "status": "deployed",
  "logical_environment": "prod",
  "physical_environment": "pacific-east",
  "cluster": "moda-1",
  "deployment_name": "deployment-pod",
  "tags": {
    "data-access": "sensitive"
  }
}'
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `deployment_records`: array of `Artifact Deployment Record`:
  * `id`: integer
  * `digest`: string
  * `logical_environment`: string
  * `physical_environment`: string
  * `cluster`: string
  * `deployment_name`: string
  * `tags`: object, additional properties: string
  * `runtime_risks`: array of string, enum: `critical-resource`, `internet-exposed`, `lateral-movement`, `sensitive-data`
  * `created_at`: string
  * `updated_at`: string
  * `attestation_id`: integer or null

## Set cluster deployment records

```
POST /orgs/{org}/artifacts/metadata/deployment-record/cluster/{cluster}
```

Set deployment records for a given cluster.
If proposed records in the 'deployments' field have identical 'cluster', 'logical\_environment',
'physical\_environment', and 'deployment\_name' values as existing records, the existing records will be updated.
If no existing records match, new records will be created.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`cluster`** (string) (required)
  The cluster name.

#### Body parameters

* **`logical_environment`** (string) (required)
  The stage of the deployment.

* **`physical_environment`** (string)
  The physical region of the deployment.

* **`deployments`** (array of objects) (required)
  The list of deployments to record.
  * **`name`** (string) (required)
    The name of the artifact. Note that if multiple deployments have identical 'digest' parameter values,
    the name parameter must also be identical across all entries.
  * **`digest`** (string) (required)
    The hex encoded digest of the artifact. Note that if multiple deployments have identical 'digest' parameter values,
    the name and version parameters must also be identical across all entries.
  * **`version`** (string)
    The artifact version. Note that if multiple deployments have identical 'digest' parameter values,
    the version parameter must also be identical across all entries.
  * **`status`** (string)
    The deployment status of the artifact.
    Default: `deployed`
    Can be one of: `deployed`, `decommissioned`
  * **`deployment_name`** (string) (required)
    The unique identifier for the deployment represented by the new record. To accommodate differing
    containers and namespaces within a record set, the following format is recommended:
    {namespaceName}-{deploymentName}-{containerName}.
    The deployment\_name must be unique across all entries in the deployments array.
  * **`github_repository`** (string)
    The name of the GitHub repository associated with the artifact. This should be used
    when there are no provenance attestations available for the artifact. The repository
    must belong to the organization specified in the path parameter.
    If a provenance attestation is available for the artifact, the API will use
    the repository information from the attestation instead of this parameter.
  * **`tags`** (object)
    Key-value pairs to tag the deployment record.
  * **`runtime_risks`** (array of strings)
    A list of runtime risks associated with the deployment.
    Supported values are: critical-resource, internet-exposed, lateral-movement, sensitive-data

* **`return_records`** (boolean)
  If true, the endpoint will return the set records in the response body
  Default: `true`

### HTTP response status codes

* **200** - Deployment records created or updated successfully.

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/artifacts/metadata/deployment-record/cluster/CLUSTER \
  -d '{
  "logical_environment": "prod",
  "physical_environment": "pacific-east",
  "deployments": [
    {
      "name": "awesome-image",
      "digest": "sha256:1bb1e949e55dcefc6353e7b36c8897d2a107d8e8dca49d4e3c0ea8493fc0bc72",
      "version": "2.1.0",
      "status": "deployed",
      "deployment_name": "deployment-pod",
      "tags": {
        "runtime-risk": "sensitive-data"
      }
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an artifact deployment record](#create-an-artifact-deployment-record).

## Create artifact metadata storage record

```
POST /orgs/{org}/artifacts/metadata/storage-record
```

Create metadata storage records for artifacts associated with an organization.
This endpoint will create a new artifact storage record on behalf of any artifact matching the provided digest and
associated with a repository owned by the organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`name`** (string) (required)
  The name of the artifact.

* **`digest`** (string) (required)
  The digest of the artifact (algorithm:hex-encoded-digest).

* **`version`** (string)
  The artifact version.

* **`artifact_url`** (string)
  The URL where the artifact is stored.

* **`path`** (string)
  The path of the artifact.

* **`registry_url`** (string) (required)
  The base URL of the artifact registry.

* **`repository`** (string)
  The repository name within the registry.

* **`status`** (string)
  The status of the artifact (e.g., active, inactive).
  Default: `active`
  Can be one of: `active`, `eol`, `deleted`

* **`github_repository`** (string)
  The name of the GitHub repository associated with the artifact. This should be used
  when there are no provenance attestations available for the artifact. The repository
  must belong to the organization specified in the path parameter.
  If a provenance attestation is available for the artifact, the API will use
  the repository information from the attestation instead of this parameter.

* **`return_records`** (boolean)
  If true, the endpoint will return the created record in the response body.
  Default: `true`

### HTTP response status codes

* **200** - Artifact metadata storage record stored successfully.

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/artifacts/metadata/storage-record \
  -d '{
  "name": "libfoo",
  "version": "1.2.3",
  "digest": "sha256:1bb1e949e55dcefc6353e7b36c8897d2a107d8e8dca49d4e3c0ea8493fc0bc72",
  "artifact_url": "https://reg.example.com/artifactory/bar/libfoo-1.2.3",
  "registry_url": "https://reg.example.com/artifactory/",
  "repository": "bar",
  "status": "active"
}'
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `storage_records`: array of objects:
  * `id`: integer
  * `name`: string
  * `digest`: string
  * `artifact_url`: string or null
  * `registry_url`: string
  * `repository`: string or null
  * `status`: string
  * `created_at`: string
  * `updated_at`: string

## List artifact deployment records

```
GET /orgs/{org}/artifacts/{subject_digest}/metadata/deployment-records
```

List deployment records for an artifact metadata associated with an organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`subject_digest`** (string) (required)
  The SHA256 digest of the artifact, in the form sha256:HEX\_DIGEST.

### HTTP response status codes

* **200** - Successful response

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/artifacts/SUBJECT_DIGEST/metadata/deployment-records
```

**Response schema (Status: 200):**

* `total_count`: integer
* `deployment_records`: array of `Artifact Deployment Record`:
  * `id`: integer
  * `digest`: string
  * `logical_environment`: string
  * `physical_environment`: string
  * `cluster`: string
  * `deployment_name`: string
  * `tags`: object, additional properties: string
  * `runtime_risks`: array of string, enum: `critical-resource`, `internet-exposed`, `lateral-movement`, `sensitive-data`
  * `created_at`: string
  * `updated_at`: string
  * `attestation_id`: integer or null

## List artifact storage records

```
GET /orgs/{org}/artifacts/{subject_digest}/metadata/storage-records
```

List a collection of artifact storage records with a given subject digest that are associated with repositories owned by an organization.
The collection of storage records returned by this endpoint is filtered according to the authenticated user's permissions; if the authenticated user cannot read a repository, the attestations associated with that repository will not be included in the response. In addition, when using a fine-grained access token the content:read permission is required.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`subject_digest`** (string) (required)
  The parameter should be set to the attestation's subject's SHA256 digest, in the form sha256:HEX\_DIGEST.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/artifacts/SUBJECT_DIGEST/metadata/storage-records
```

**Response schema (Status: 200):**

* `total_count`: integer
* `storage_records`: array of objects:
  * `id`: integer
  * `name`: string
  * `digest`: string
  * `artifact_url`: string
  * `registry_url`: string
  * `repository`: string
  * `status`: string
  * `created_at`: string
  * `updated_at`: string