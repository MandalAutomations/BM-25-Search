# REST API endpoints for artifact attestations

Use the REST API to manage artifact attestations.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## List attestations by bulk subject digests

```
POST /users/{username}/attestations/bulk-list
```

List a collection of artifact attestations associated with any entry in a list of subject digests owned by a user.
The collection of attestations returned by this endpoint is filtered according to the authenticated user's permissions; if the authenticated user cannot read a repository, the attestations associated with that repository will not be included in the response. In addition, when using a fine-grained access token the attestations:read permission is required.
Please note: in order to offer meaningful security benefits, an attestation's signature and timestamps must be cryptographically verified, and the identity of the attestation signer must be validated. Attestations can be verified using the GitHub CLI attestation verify command. For more information, see our guide on how to use artifact attestations to establish a build's provenance.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

- **`username`** (string) (required)
  The handle for the GitHub user account.




#### Body parameters

- **`subject_digests`** (array of strings) (required)
  List of subject digests to fetch attestations for.

- **`predicate_type`** (string)
  Optional filter for fetching attestations with a given predicate type.
This option accepts provenance, sbom, release, or freeform text
for custom predicate types.





### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/users/USERNAME/attestations/bulk-list \
  -d '{
  "subject_digests": [
    "sha256:abc123",
    "sha512:def456"
  ]
}'
```

**Response schema (Status: 200):**

* `attestations_subject_digests`: object, additional properties: array or null
* `page_info`: object:
  * `has_next`: boolean
  * `has_previous`: boolean
  * `next`: string
  * `previous`: string





## Delete attestations in bulk

```
POST /users/{username}/attestations/delete-request
```

Delete artifact attestations in bulk by either subject digests or unique ID.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.




#### Body parameters

- **`subject_digests`** (array of strings) (required)
  List of subject digests associated with the artifact attestations to delete.





### HTTP response status codes


- **200** - OK


- **404** - Resource not found





## Delete attestations by subject digest

```
DELETE /users/{username}/attestations/digest/{subject_digest}
```

Delete an artifact attestation by subject digest.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`subject_digest`** (string) (required)
  Subject Digest






### HTTP response status codes


- **200** - OK


- **204** - No Content


- **404** - Resource not found




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/users/USERNAME/attestations/digest/SUBJECT_DIGEST
```

**Response schema (Status: 200):**




#### Example 2: Status Code 204

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/users/USERNAME/attestations/digest/SUBJECT_DIGEST
```

**Response schema (Status: 204):**





## Delete attestations by ID

```
DELETE /users/{username}/attestations/{attestation_id}
```

Delete an artifact attestation by unique ID that is associated with a repository owned by a user.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`attestation_id`** (integer) (required)
  Attestation ID






### HTTP response status codes


- **200** - OK


- **204** - No Content


- **403** - Forbidden


- **404** - Resource not found




### Code examples



#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/users/USERNAME/attestations/ATTESTATION_ID
```

**Response schema (Status: 200):**




#### Example 2: Status Code 204

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/users/USERNAME/attestations/ATTESTATION_ID
```

**Response schema (Status: 204):**





## List attestations

```
GET /users/{username}/attestations/{subject_digest}
```

List a collection of artifact attestations with a given subject digest that are associated with repositories owned by a user.
The collection of attestations returned by this endpoint is filtered according to the authenticated user's permissions; if the authenticated user cannot read a repository, the attestations associated with that repository will not be included in the response. In addition, when using a fine-grained access token the attestations:read permission is required.
Please note: in order to offer meaningful security benefits, an attestation's signature and timestamps must be cryptographically verified, and the identity of the attestation signer must be validated. Attestations can be verified using the GitHub CLI attestation verify command. For more information, see our guide on how to use artifact attestations to establish a build's provenance.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`before`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results before this cursor. For more information, see "Using pagination in the REST API."

- **`after`** (string)
  A cursor, as given in the Link header. If specified, the query only searches for results after this cursor. For more information, see "Using pagination in the REST API."

- **`username`** (string) (required)
  The handle for the GitHub user account.

- **`subject_digest`** (string) (required)
  Subject Digest

- **`predicate_type`** (string)
  Optional filter for fetching attestations with a given predicate type.
This option accepts provenance, sbom, release, or freeform text
for custom predicate types.






### HTTP response status codes


- **200** - OK


- **201** - Created


- **204** - No Content


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/users/USERNAME/attestations/SUBJECT_DIGEST
```

**Response schema (Status: 200):**

* `attestations`: array of objects:
  * `repository_id`: integer
  * `bundle_url`: string
  * `initiator`: string