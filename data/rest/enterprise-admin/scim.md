# REST API endpoints for SCIM

Use the REST API to automate user creation and team memberships with SCIM.

> \[!NOTE]
>
> * These endpoints allow you to provision user accounts for your enterprise on GitHub Enterprise Cloud using SCIM. The operation is only available for use with Enterprise Managed Users. If you don't use Enterprise Managed Users and want to provision access to your organizations using SCIM, see [REST API endpoints for SCIM](/en/enterprise-cloud@latest/rest/enterprise-admin/scim).
> * GitHub recommends that you test provisioning in an environment that's isolated from the production data on your IdP and GitHub.

## About SCIM

To create, manage, and deactivate user accounts for your enterprise members on GitHub, your IdP must implement SCIM for communication with GitHub. SCIM is an open specification for management of user identities between systems. Different IdPs provide different experiences for the configuration of SCIM provisioning. If you don't use a partner IdP with an existing integration, you can integrate using the following API endpoints. For more information, see [Provisioning users and groups with SCIM using the REST API](/en/enterprise-cloud@latest/admin/identity-and-access-management/provisioning-user-accounts-for-enterprise-managed-users/provisioning-users-with-scim-using-the-rest-api).

### Base URL

To manage your enterprise's users and groups using SCIM, use the following base URL to communicate with the endpoints in this category.

```http
https://api.github.com/scim/v2/enterprises/{enterprise}/
```

### Authentication

To authenticate API requests, the person who configures SCIM on the IdP must use a personal access token (classic) with `scim:enterprise` scope, which the IdP must provide in the request's `Authorization` header. For more information about personal access tokens (classic), see [Managing your personal access tokens](/en/enterprise-cloud@latest/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

GitHub recommends authenticating as the setup user for the enterprise. Other user accounts are created through SCIM, so authenticating as a different user could result in unintended consequences, such as getting locked out of your enterprise. Write requests to these APIs are possible through our published IdP applications, or through direct API access to our SCIM endpoints. If another enterprise owner needs to read information from the API, use a personal access token (classic) with the `admin:enterprise` scope to make `GET` requests on your current SCIM implementation. For more information, see [Configuring SCIM provisioning for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/provisioning-user-accounts-for-enterprise-managed-users/configuring-scim-provisioning-for-enterprise-managed-users#creating-a-personal-access-token).

### Mapping of SAML and SCIM data

After a managed user account successfully authenticates to access your enterprise using SAML SSO, GitHub links the user to a SCIM provisioned identity. To link the identities successfully, the SAML identity provider and the SCIM integration must use matching unique identifiers.

GitHub requires the following SAML claim and SCIM attribute to successfully match the user with the identity provisioned by SCIM. Identity providers may differ in the field used to uniquely identify a user.

#### Microsoft Entra ID for SAML

To use Entra ID (previously known as Azure AD) for SAML, the following SAML claims and SCIM attribute must match.

| SAML claim                                                      | Matching SCIM attribute |
| :-------------------------------------------------------------- | :---------------------- |
| `http://schemas.microsoft.com/identity/claims/objectidentifier` | `externalId`            |

#### Other IdPs for SAML

To use other IdPs for SAML, the following SAML claims and SCIM attribute must match.

| SAML claim | Matching SCIM attribute |
| :--------- | :---------------------- |
| `NameID`   | `userName`              |

### Supported SCIM user attributes

`Users` endpoints in this category support the following attributes within a request's parameters.

| Name              | Type    | Description                                                                                                                                                                                                                                                                                                          |
| :---------------- | :------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `displayName`     | String  | Human-readable name for a user.                                                                                                                                                                                                                                                                                      |
| `name.formatted`  | String  | The user's full name, including all middle names, titles, and suffixes, formatted for display.                                                                                                                                                                                                                       |
| `name.givenName`  | String  | The first name of the user.                                                                                                                                                                                                                                                                                          |
| `name.familyName` | String  | The last name of the user.                                                                                                                                                                                                                                                                                           |
| `userName`        | String  | The username for the user, generated by the SCIM provider. Undergoes [normalization](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-iam-for-your-enterprise/username-considerations-for-external-authentication#about-username-normalization) before being used. Must be unique per user. |
| `emails`          | Array   | List of the user's emails.                                                                                                                                                                                                                                                                                           |
| `roles`           | Array   | List of the user's roles.                                                                                                                                                                                                                                                                                            |
| `externalId`      | String  | This identifier is generated by a SCIM provider. Must be unique per user.                                                                                                                                                                                                                                            |
| `id`              | String  | Identifier generated by the GitHub's SCIM endpoint.                                                                                                                                                                                                                                                                  |
| `active`          | Boolean | Indicates whether the identity is active (`true`) or should be suspended (`false`).                                                                                                                                                                                                                                  |

### Supported SCIM group attributes

`Groups` endpoints in this category support the following attributes within a request's parameters.

| Name          | Type   | Description                                                               |
| :------------ | :----- | :------------------------------------------------------------------------ |
| `displayName` | String | Human-readable name for a group.                                          |
| `members`     | String | List of members who are assigned to the group in SCIM provider            |
| `externalId`  | String | This identifier is generated by a SCIM provider. Must be unique per user. |

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List provisioned SCIM groups for an enterprise

```
GET /scim/v2/enterprises/{enterprise}/Groups
```

Lists provisioned SCIM groups in an enterprise.
You can improve query search time by using the excludedAttributes query parameter with a value of members to exclude members from the response.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`filter`** (string)
  If specified, only results that match the specified filter will be returned. Multiple filters are not supported. Possible filters are externalId, id, and displayName. For example, ?filter=externalId eq "9138790-10932-109120392-12321".

* **`excludedAttributes`** (string)
  Excludes the specified attribute from being returned in the results. Using this parameter can speed up response time.

* **`startIndex`** (integer)
  Used for pagination: the starting index of the first result to return when paginating through values.
  Default: `1`

* **`count`** (integer)
  Used for pagination: the number of results to return per page.
  Default: `30`

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - Success, either groups were found or not found

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Groups
```

**Response schema (Status: 200):**

* `schemas`: required, array of string, enum: `urn:ietf:params:scim:api:messages:2.0:ListResponse`
* `totalResults`: required, integer
* `Resources`: required, array of object
* `startIndex`: required, integer
* `itemsPerPage`: required, integer

## Provision a SCIM enterprise group

```
POST /scim/v2/enterprises/{enterprise}/Groups
```

Creates a SCIM group for an enterprise.
When members are part of the group provisioning payload, they're designated as external group members. Providers are responsible for maintaining a mapping between the externalId and id for each user.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`schemas`** (array of strings) (required)
  The URIs that are used to indicate the namespaces of the SCIM schemas.
  Supported values are: urn:ietf:params:scim:schemas:core:2.0:Group

* **`externalId`** (string) (required)
  A unique identifier for the resource as defined by the provisioning client.

* **`displayName`** (string) (required)
  A human-readable name for a security group.

* **`members`** (array of objects)
  The group members.
  * **`value`** (string) (required)
    The local unique identifier for the member
  * **`displayName`** (string) (required)
    The display name associated with the member

### HTTP response status codes

* **201** - Group has been created

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **409** - Duplicate record detected

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Groups \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:Group"
  ],
  "externalId": "8aa1a0c0-c4c3-4bc0-b4a5-2ef676900159",
  "displayName": "Engineering",
  "members": [
    {
      "value": "879db59-3bdf-4490-ad68-ab880a2694745",
      "displayName": "User 1"
    },
    {
      "value": "0db508eb-91e2-46e4-809c-30dcbda0c685",
      "displayName": "User 2"
    }
  ]
}'
```

**Response schema (Status: 201):**

* all of:
  * **object**
    * `schemas`: required, array of string, enum: `urn:ietf:params:scim:schemas:core:2.0:Group`, `urn:ietf:params:scim:api:messages:2.0:ListResponse`
    * `externalId`: string or null
    * `displayName`: string or null
    * `members`: array of objects:
      * `value`: required, string
      * `$ref`: required, string
      * `display`: string
  * **object**
    * `id`: string
    * `members`: array of objects:
      * `value`: string
      * `$ref`: string
      * `display`: string
    * `meta`: object:
      * `resourceType`: required, string, enum: `User`, `Group`
      * `created`: string
      * `lastModified`: string
      * `location`: string

## Get SCIM provisioning information for an enterprise group

```
GET /scim/v2/enterprises/{enterprise}/Groups/{scim_group_id}
```

Gets information about a SCIM group.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`scim_group_id`** (string) (required)
  A unique identifier of the SCIM group.

* **`excludedAttributes`** (string)
  Excludes the specified attribute from being returned in the results. Using this parameter can speed up response time.

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - Success, a group was found

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **404** - Resource not found

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Groups/SCIM_GROUP_ID
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise group](#provision-a-scim-enterprise-group).

## Set SCIM information for a provisioned enterprise group

```
PUT /scim/v2/enterprises/{enterprise}/Groups/{scim_group_id}
```

Replaces an existing provisioned group’s information.
You must provide all the information required for the group as if you were provisioning it for the first time. Any existing group information that you don't provide will be removed, including group membership. If you want to only update a specific attribute, use the Update an attribute for a SCIM enterprise group endpoint instead.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`scim_group_id`** (string) (required)
  A unique identifier of the SCIM group.

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`schemas`** (array of strings) (required)
  The URIs that are used to indicate the namespaces of the SCIM schemas.
  Supported values are: urn:ietf:params:scim:schemas:core:2.0:Group

* **`externalId`** (string) (required)
  A unique identifier for the resource as defined by the provisioning client.

* **`displayName`** (string) (required)
  A human-readable name for a security group.

* **`members`** (array of objects)
  The group members.
  * **`value`** (string) (required)
    The local unique identifier for the member
  * **`displayName`** (string) (required)
    The display name associated with the member

### HTTP response status codes

* **200** - Group was updated

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **404** - Resource not found

* **409** - Duplicate record detected

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Group

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Groups/SCIM_GROUP_ID \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:Group"
  ],
  "externalId": "8aa1a0c0-c4c3-4bc0-b4a5-2ef676900159",
  "displayName": "Engineering"
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise group](#provision-a-scim-enterprise-group).

#### Group with member

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Groups/SCIM_GROUP_ID \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:Group"
  ],
  "externalId": "8aa1a0c0-c4c3-4bc0-b4a5-2ef676900159",
  "displayName": "Engineering",
  "members": [
    {
      "value": "879db59-3bdf-4490-ad68-ab880a2694745",
      "displayName": "User 1"
    },
    {
      "value": "0db508eb-91e2-46e4-809c-30dcbda0c685",
      "displayName": "User 2"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise group](#provision-a-scim-enterprise-group).

## Update an attribute for a SCIM enterprise group

```
PATCH /scim/v2/enterprises/{enterprise}/Groups/{scim_group_id}
```

Update a provisioned group’s individual attributes.
To modify a group's values, you'll need to use a specific Operations JSON format which must include at least one of the following operations: add, remove, or replace. For examples and more information on this SCIM format, consult the SCIM specification. The update function can also be used to add group memberships.
You can submit group memberships individually or in batches for improved efficiency.
Note

Memberships are referenced via a local user id. Ensure users are created before referencing them here.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`scim_group_id`** (string) (required)
  A unique identifier of the SCIM group.

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`Operations`** (array of objects) (required)
  patch operations list
  * **`op`** (string) (required)
    Can be one of: `add`, `replace`, `remove`
  * **`path`** (string)
  * **`value`** (string)
    Corresponding 'value' of that field specified by 'path'

* **`schemas`** (array of strings) (required)
  undefinedSupported values are: urn:ietf:params:scim:api:messages:2.0:PatchOp

### HTTP response status codes

* **200** - Success, group was updated

* **204** - No Content

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **404** - Resource not found

* **409** - Duplicate record detected

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Update Group

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Groups/SCIM_GROUP_ID \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:api:messages:2.0:PatchOp"
  ],
  "Operations": [
    {
      "op": "replace",
      "path": "displayName",
      "value": "Employees"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise group](#provision-a-scim-enterprise-group).

#### Add Members

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Groups/SCIM_GROUP_ID \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:api:messages:2.0:PatchOp"
  ],
  "Operations": [
    {
      "op": "add",
      "path": "members",
      "value": [
        {
          "value": "879db59-3bdf-4490-ad68-ab880a2694745"
        },
        {
          "value": "0db508eb-91e2-46e4-809c-30dcbda0c685"
        }
      ]
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise group](#provision-a-scim-enterprise-group).

## Delete a SCIM group from an enterprise

```
DELETE /scim/v2/enterprises/{enterprise}/Groups/{scim_group_id}
```

Deletes a SCIM group from an enterprise.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`scim_group_id`** (string) (required)
  A unique identifier of the SCIM group.

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **204** - Group was deleted, no content

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **404** - Resource not found

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Groups/SCIM_GROUP_ID
```

**Response schema (Status: 204):**

## List SCIM provisioned identities for an enterprise

```
GET /scim/v2/enterprises/{enterprise}/Users
```

Lists provisioned SCIM enterprise members.
When you remove a user with a SCIM-provisioned external identity from an enterprise using a patch with active flag to false, the user's metadata remains intact. This means they can potentially re-join the enterprise later. Although, while suspended, the user can't sign in. If you want to ensure the user can't re-join in the future, use the delete request. Only users who weren't permanently deleted will appear in the result list.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`filter`** (string)
  If specified, only results that match the specified filter will be returned. Multiple filters are not supported. Possible filters are userName, externalId, id, and displayName. For example, ?filter=externalId eq "9138790-10932-109120392-12321".

* **`startIndex`** (integer)
  Used for pagination: the starting index of the first result to return when paginating through values.
  Default: `1`

* **`count`** (integer)
  Used for pagination: the number of results to return per page.
  Default: `30`

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - Success, either users were found or not found

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Users
```

**Response schema (Status: 200):**

Same response schema as [List provisioned SCIM groups for an enterprise](#list-provisioned-scim-groups-for-an-enterprise).

## Provision a SCIM enterprise user

```
POST /scim/v2/enterprises/{enterprise}/Users
```

Creates an external identity for a new SCIM enterprise user.
SCIM is responsible for user provisioning, not authentication. The actual user authentication is handled by SAML. However, with SCIM enabled, users must first be provisioned via SCIM before they can sign in through SAML.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`schemas`** (array of strings) (required)
  The URIs that are used to indicate the namespaces of the SCIM schemas.
  Supported values are: urn:ietf:params:scim:schemas:core:2.0:User

* **`externalId`** (string) (required)
  A unique identifier for the resource as defined by the provisioning client.

* **`active`** (boolean) (required)
  Whether the user active in the IdP.

* **`userName`** (string) (required)
  The username for the user.

* **`name`** (object)
  * **`formatted`** (string)
    The full name, including all middle names, titles, and suffixes as appropriate, formatted for display.
  * **`familyName`** (string) (required)
    The family name of the user.
  * **`givenName`** (string) (required)
    The given name of the user.
  * **`middleName`** (string)
    The middle name(s) of the user.

* **`displayName`** (string) (required)
  A human-readable name for the user.

* **`emails`** (array of objects) (required)
  The emails for the user.
  * **`value`** (string) (required)
    The email address.
  * **`type`** (string) (required)
    The type of email address.
  * **`primary`** (boolean) (required)
    Whether this email address is the primary address.

* **`roles`** (array of objects)
  The roles assigned to the user.
  * **`display`** (string)
  * **`type`** (string)
  * **`value`** (string) (required)
    The role value representing a user role in GitHub.
    Can be one of: `user`, `27d9891d-2c17-4f45-a262-781a0e55c80a`, `guest_collaborator`, `1ebc4a02-e56c-43a6-92a5-02ee09b90824`, `enterprise_owner`, `981df190-8801-4618-a08a-d91f6206c954`, `ba4987ab-a1c3-412a-b58c-360fc407cb10`, `billing_manager`, `0e338b8c-cc7f-498a-928d-ea3470d7e7e3`, `e6be2762-e4ad-4108-b72d-1bbe884a0f91`
  * **`primary`** (boolean)
    Is the role a primary role for the user.

### HTTP response status codes

* **201** - User has been created

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **409** - Duplicate record detected

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### User

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Users \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:User"
  ],
  "externalId": "E012345",
  "active": true,
  "userName": "E012345",
  "name": {
    "formatted": "Ms. Mona Lisa Octocat",
    "familyName": "Octocat",
    "givenName": "Mona",
    "middleName": "Lisa"
  },
  "displayName": "Mona Lisa",
  "emails": [
    {
      "value": "mlisa@example.com",
      "type": "work",
      "primary": true
    }
  ],
  "roles": [
    {
      "value": "user",
      "primary": false
    }
  ]
}'
```

**Response schema (Status: 201):**

* all of:
  * **object**
    * `schemas`: required, array of string, enum: `urn:ietf:params:scim:schemas:core:2.0:User`
    * `externalId`: string or null
    * `active`: required, boolean
    * `userName`: string
    * `name`: object:
      * `formatted`: string
      * `familyName`: string
      * `givenName`: string
      * `middleName`: string
    * `displayName`: string or null
    * `emails`: required, array of objects:
      * `value`: required, string
      * `type`: string
      * `primary`: boolean
    * `roles`: array of objects:
      * `display`: string
      * `type`: string
      * `value`: required, string, enum: `user`, `27d9891d-2c17-4f45-a262-781a0e55c80a`, `guest_collaborator`, `1ebc4a02-e56c-43a6-92a5-02ee09b90824`, `enterprise_owner`, `981df190-8801-4618-a08a-d91f6206c954`, `ba4987ab-a1c3-412a-b58c-360fc407cb10`, `billing_manager`, `0e338b8c-cc7f-498a-928d-ea3470d7e7e3`, `e6be2762-e4ad-4108-b72d-1bbe884a0f91`
      * `primary`: boolean
  * **object**
    * `id`: required, string
    * `groups`: array of objects:
      * `value`: string
      * `$ref`: string
      * `display`: string
    * `meta`: required, object:
      * `resourceType`: required, string, enum: `User`, `Group`
      * `created`: string
      * `lastModified`: string
      * `location`: string

#### Enterprise Owner

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Users \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:User"
  ],
  "externalId": "E012345",
  "active": true,
  "userName": "E012345",
  "name": {
    "formatted": "Ms. Mona Lisa Octocat",
    "familyName": "Octocat",
    "givenName": "Mona",
    "middleName": "Lisa"
  },
  "displayName": "Mona Lisa",
  "emails": [
    {
      "value": "mlisa@example.com",
      "type": "work",
      "primary": true
    }
  ],
  "roles": [
    {
      "value": "enterprise_owner",
      "primary": false
    }
  ]
}'
```

**Response schema (Status: 201):**

* all of:
  * **object**
    * `schemas`: required, array of string, enum: `urn:ietf:params:scim:schemas:core:2.0:User`
    * `externalId`: string or null
    * `active`: required, boolean
    * `userName`: string
    * `name`: object:
      * `formatted`: string
      * `familyName`: string
      * `givenName`: string
      * `middleName`: string
    * `displayName`: string or null
    * `emails`: required, array of objects:
      * `value`: required, string
      * `type`: string
      * `primary`: boolean
    * `roles`: array of objects:
      * `display`: string
      * `type`: string
      * `value`: required, string, enum: `user`, `27d9891d-2c17-4f45-a262-781a0e55c80a`, `guest_collaborator`, `1ebc4a02-e56c-43a6-92a5-02ee09b90824`, `enterprise_owner`, `981df190-8801-4618-a08a-d91f6206c954`, `ba4987ab-a1c3-412a-b58c-360fc407cb10`, `billing_manager`, `0e338b8c-cc7f-498a-928d-ea3470d7e7e3`, `e6be2762-e4ad-4108-b72d-1bbe884a0f91`
      * `primary`: boolean
  * **object**
    * `id`: required, string
    * `groups`: array of objects:
      * `value`: string
      * `$ref`: string
      * `display`: string
    * `meta`: required, object:
      * `resourceType`: required, string, enum: `User`, `Group`
      * `created`: string
      * `lastModified`: string
      * `location`: string

## Get SCIM provisioning information for an enterprise user

```
GET /scim/v2/enterprises/{enterprise}/Users/{scim_user_id}
```

Gets information about a SCIM user.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`scim_user_id`** (string) (required)
  The unique identifier of the SCIM user.

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - Success, a user was found

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **404** - Resource not found

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Users/SCIM_USER_ID
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise user](#provision-a-scim-enterprise-user).

## Set SCIM information for a provisioned enterprise user

```
PUT /scim/v2/enterprises/{enterprise}/Users/{scim_user_id}
```

Replaces an existing provisioned user's information.
You must supply complete user information, just as you would when provisioning them initially. Any previously existing data not provided will be deleted. To update only a specific attribute, refer to the Update an attribute for a SCIM user endpoint.
Warning

Setting active: false will suspend a user. As a result, their handle and primary email address will be obfuscated.
{
"schemas": \[
"urn:ietf:params:scim:schemas:core:2.0:User"
],
"externalId": "E012345",
"active": false,
"userName": "E012345",
"name": {
"familyName": "Octocat",
"givenName": "Mona",
"middleName": "Lisa"
},
"displayName": "Mona Lisa",
"emails": \[
{
"value": "<mlisa@example.com>",
"type": "work",
"primary": true
}
],
"roles": \[
{
"value": "User"
}
]
}

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`scim_user_id`** (string) (required)
  The unique identifier of the SCIM user.

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`schemas`** (array of strings) (required)
  The URIs that are used to indicate the namespaces of the SCIM schemas.
  Supported values are: urn:ietf:params:scim:schemas:core:2.0:User

* **`externalId`** (string) (required)
  A unique identifier for the resource as defined by the provisioning client.

* **`active`** (boolean) (required)
  Whether the user active in the IdP.

* **`userName`** (string) (required)
  The username for the user.

* **`name`** (object)
  * **`formatted`** (string)
    The full name, including all middle names, titles, and suffixes as appropriate, formatted for display.
  * **`familyName`** (string) (required)
    The family name of the user.
  * **`givenName`** (string) (required)
    The given name of the user.
  * **`middleName`** (string)
    The middle name(s) of the user.

* **`displayName`** (string) (required)
  A human-readable name for the user.

* **`emails`** (array of objects) (required)
  The emails for the user.
  * **`value`** (string) (required)
    The email address.
  * **`type`** (string) (required)
    The type of email address.
  * **`primary`** (boolean) (required)
    Whether this email address is the primary address.

* **`roles`** (array of objects)
  The roles assigned to the user.
  * **`display`** (string)
  * **`type`** (string)
  * **`value`** (string) (required)
    The role value representing a user role in GitHub.
    Can be one of: `user`, `27d9891d-2c17-4f45-a262-781a0e55c80a`, `guest_collaborator`, `1ebc4a02-e56c-43a6-92a5-02ee09b90824`, `enterprise_owner`, `981df190-8801-4618-a08a-d91f6206c954`, `ba4987ab-a1c3-412a-b58c-360fc407cb10`, `billing_manager`, `0e338b8c-cc7f-498a-928d-ea3470d7e7e3`, `e6be2762-e4ad-4108-b72d-1bbe884a0f91`
  * **`primary`** (boolean)
    Is the role a primary role for the user.

### HTTP response status codes

* **200** - User was updated

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **404** - Resource not found

* **409** - Duplicate record detected

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### User

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Users/SCIM_USER_ID \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:User"
  ],
  "externalId": "E012345",
  "active": true,
  "userName": "E012345",
  "name": {
    "formatted": "Ms. Mona Lisa Octocat",
    "familyName": "Octocat",
    "givenName": "Mona",
    "middleName": "Lisa"
  },
  "displayName": "Mona Lisa",
  "emails": [
    {
      "value": "mlisa@example.com",
      "type": "work",
      "primary": true
    }
  ],
  "roles": [
    {
      "value": "user",
      "primary": false
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise user](#provision-a-scim-enterprise-user).

## Update an attribute for a SCIM enterprise user

```
PATCH /scim/v2/enterprises/{enterprise}/Users/{scim_user_id}
```

Update a provisioned user's individual attributes.
To modify a user's attributes, you'll need to provide a Operations JSON formatted request that includes at least one of the following actions: add, remove, or replace. For specific examples and more information on the SCIM operations format, please refer to the SCIM specification.
Note

Complex SCIM path selectors that include filters are not supported. For example, a path selector defined as "path": "emails\[type eq "work"]" will be ineffective.

Warning

Setting active: false will suspend a user. As a result, their handle and primary email address will be obfuscated.
{
"schemas": \[
"urn:ietf:params:scim:api:messages:2.0:PatchOp"
],
"Operations": \[
{
"op": "replace",
"value": {
"active": false
}
}
]
}

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`scim_user_id`** (string) (required)
  The unique identifier of the SCIM user.

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

* **`Operations`** (array of objects) (required)
  patch operations list
  * **`op`** (string) (required)
    Can be one of: `add`, `replace`, `remove`
  * **`path`** (string)
  * **`value`** (string)
    Corresponding 'value' of that field specified by 'path'

* **`schemas`** (array of strings) (required)
  undefinedSupported values are: urn:ietf:params:scim:api:messages:2.0:PatchOp

### HTTP response status codes

* **200** - Success, user was updated

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **404** - Resource not found

* **409** - Duplicate record detected

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Multi Valued Property

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Users/SCIM_USER_ID \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:api:messages:2.0:PatchOp"
  ],
  "Operations": [
    {
      "op": "replace",
      "path": "emails[type eq 'work'].value",
      "value": "updatedEmail@microsoft.com"
    },
    {
      "op": "replace",
      "path": "name.familyName",
      "value": "updatedFamilyName"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise user](#provision-a-scim-enterprise-user).

#### Single Valued Property

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Users/SCIM_USER_ID \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:api:messages:2.0:PatchOp"
  ],
  "Operations": [
    {
      "op": "replace",
      "path": "userName",
      "value": "5b50642d-79fc-4410-9e90-4c077cdd1a59@testuser.com"
    },
    {
      "op": "replace",
      "path": "displayName",
      "value": "Monalisa Octocat"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise user](#provision-a-scim-enterprise-user).

#### Disable User

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Users/SCIM_USER_ID \
  -d '{
  "schemas": [
    "urn:ietf:params:scim:api:messages:2.0:PatchOp"
  ],
  "Operations": [
    {
      "op": "replace",
      "path": "active",
      "value": false
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision a SCIM enterprise user](#provision-a-scim-enterprise-user).

## Delete a SCIM user from an enterprise

```
DELETE /scim/v2/enterprises/{enterprise}/Users/{scim_user_id}
```

Suspends a SCIM user permanently from an enterprise. This action will: remove all the user's data,  anonymize their login, email, and display name, erase all external identity SCIM attributes, delete the user's emails, avatar, PATs, SSH keys, OAuth authorizations, GPG keys, and SAML mappings. This action is irreversible.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`scim_user_id`** (string) (required)
  The unique identifier of the SCIM user.

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **204** - User was deleted, no content

* **400** - Bad request

* **401** - Authorization failure

* **403** - Permission denied

* **404** - Resource not found

* **429** - Too many requests

* **500** - Internal server error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/scim/v2/enterprises/ENTERPRISE/Users/SCIM_USER_ID
```

**Response schema (Status: 204):**