# REST API endpoints for SCIM

Use the REST API to control and manage your GitHub organization members' access with SCIM.

> \[!NOTE]
> This operation allows you to provision access to an organization on GitHub Enterprise Cloud using SCIM. The operation is not available for use with Enterprise Managed Users. For more information about provisioning managed user accounts using SCIM, see [REST API endpoints for SCIM](/en/enterprise-cloud@latest/rest/enterprise-admin/scim).

## About SCIM

### SCIM Provisioning for Organizations

These endpoints are used by SCIM-enabled Identity Providers (IdPs) to automate provisioning of GitHub organization membership and are based on version 2.0 of the [SCIM standard](http://www.simplecloud.info/). IdPs should use the base URL `https://api.github.com/scim/v2/organizations/{org}/` for GitHub SCIM endpoints.

> \[!NOTE]
>
> * These endpoints are only available for individual organizations that use GitHub Enterprise Cloud with SAML SSO enabled. For more information about SCIM, see [About SCIM for organizations](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/about-scim-for-organizations). For more information about authorizing a token for a SAML SSO organization, see [Authenticating to the REST API](/en/enterprise-cloud@latest/rest/overview/authenticating-to-the-rest-api).
> * These endpoints cannot be used with an enterprise account or with an organization with managed users.

### Authentication

You must authenticate as an owner of a GitHub organization to use these endpoints. The REST API expects an OAuth 2.0 Bearer token (for example, a GitHub App user access token) to be included in the `Authorization` header. If you use a personal access token (classic) for authentication, it must have the `admin:org` scope and you must also [authorize it for use with your SAML SSO organization](/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on/authorizing-a-personal-access-token-for-use-with-saml-single-sign-on).

### Matching SAML and SCIM attributes

To successfully link a GitHub user account to a SCIM identity in an organization, specific attributes from your Identity Provider's SAML response and SCIM API provisioning call must match for a user.

#### Microsoft Entra ID for SAML

When using Entra ID (previously known as Azure AD) for SAML, the following SAML attribute and SCIM attribute must match.

| SAML attribute                                                  | Matching SCIM attribute |
| :-------------------------------------------------------------- | :---------------------- |
| `http://schemas.microsoft.com/identity/claims/objectidentifier` | `externalId`            |

#### Other IdPs for SAML

When using other IdPs for SAML, the following SAML claims and SCIM attribute must match.

| SAML attribute | Matching SCIM attribute |
| :------------- | :---------------------- |
| `NameID`       | `userName`              |

There are two different ways a GitHub user account can get linked to a SCIM identity in an organization when these SAML/SCIM attributes match:

1. For users who are not yet members of the organization:
   * The IdP sends a SCIM provisioning call to GitHub for a user who is not a member of an organization. This generates an organization invitation and an unlinked SCIM identity in the organization.
   * User authenticates via SAML in the organization.
   * GitHub automatically links the SAML and SCIM identity to the new user account in the organization.

2. For existing organization members:
   * The IdP sends a SCIM provisioning call to GitHub for a user who is already a member of the organization.
   * If the organization member does not have a linked SAML identity in the organization, this generates an organization invitation and an unlinked SCIM identity in the organization. User authenticates via SAML in the organization to link their SAML and SCIM identity.
   * If the organization member has a linked SAML identity in the organization, GitHub automatically links the SCIM identity to the existing user account in the organization. No organization invite is created.

Ensuring that a user gets properly linked to their SCIM identity in the organization can help prevent unexpected issues with SCIM deprovisioning when the user's access to the app is removed on the IdP side. For more information on auditing the linked SCIM identities in an organization, see [Troubleshooting identity and access management for your organization](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/troubleshooting-identity-and-access-management-for-your-organization#auditing-organization-members-on-github)

### Supported SCIM User attributes

| Name              | Type      | Description                                                                                                                                                                                                                                                                                                                                                                                      |
| ----------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `userName`        | `string`  | The username for the user.                                                                                                                                                                                                                                                                                                                                                                       |
| `name.givenName`  | `string`  | The first name of the user.                                                                                                                                                                                                                                                                                                                                                                      |
| `name.familyName` | `string`  | The last name of the user.                                                                                                                                                                                                                                                                                                                                                                       |
| `emails`          | `array`   | List of user emails.                                                                                                                                                                                                                                                                                                                                                                             |
| `externalId`      | `string`  | This identifier is generated by the SAML provider, and is used as a unique ID by the SAML provider to match against a GitHub user. You can find the `externalID` for a user either at the SAML provider, or using the [List SCIM provisioned identities](#list-scim-provisioned-identities) endpoint and filtering on other known attributes, such as a user's GitHub username or email address. |
| `id`              | `string`  | Identifier generated by the GitHub SCIM endpoint.                                                                                                                                                                                                                                                                                                                                                |
| `active`          | `boolean` | Used to indicate whether the identity is active (true) or should be deprovisioned (false).                                                                                                                                                                                                                                                                                                       |

> \[!NOTE]
> These endpoints are case sensitive. For example, the first letter in the `Users` endpoint must be capitalized:
>
> ```shell
> GET /scim/v2/organizations/{org}/Users/{scim_user_id}
> ```

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List SCIM provisioned identities

```
GET /scim/v2/organizations/{org}/Users
```

Retrieves a paginated list of all provisioned organization members, including pending invitations. If you provide the filter parameter, the resources for all matching provisions members are returned.
The returned list of SCIM provisioned identities from the GitHub Enterprise Cloud might not always match the organization or enterprise member list. Here is why that can occur:

When an organization invitation is generated by a SCIM integration, this creates an unlinked SCIM identity in the organization. When a user logs into their GitHub user account, visits the organization, and successfully authenticates via SAML, they get added as an organization member and linked to their SAML/SCIM identity in the organization. If the user does not do this, the SCIM identity will remain in the organization, not linked to any organization member.
A user's organization membership (inviting and removing a user to/from the organization) should only be managed by a SCIM integration when this is configured for a GitHub organization. If a GitHub user who has a linked SCIM identity is removed from the organization using the GitHub UI or non-SCIM API, as opposed to the SCIM integration, this can leave behind a stale SAML/SCIM identity in the organization for the user.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`startIndex`** (integer)
  Used for pagination: the index of the first result to return.

* **`count`** (integer)
  Used for pagination: the number of results to return.

* **`filter`** (string)
  Filters results using the equals query parameter operator (eq). You can filter results that are equal to id, userName, emails, and externalId. For example, to search for an identity with the userName Octocat, you would use this query:
  ?filter=userName%20eq%20"Octocat".
  To filter results for the identity with the email <octocat@github.com>, you would use this query:
  ?filter=emails%20eq%20"<octocat@github.com>".

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **400** - Bad request

* **403** - Forbidden

* **404** - Resource not found

* **429** - Too many requests

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/scim/v2/organizations/ORG/Users
```

**Response schema (Status: 200):**

* `schemas`: required, array of string
* `totalResults`: required, integer
* `itemsPerPage`: required, integer
* `startIndex`: required, integer
* `Resources`: required, array of `SCIM /Users`:
  * `schemas`: required, array of string
  * `id`: required, string
  * `externalId`: string or null
  * `userName`: string or null
  * `displayName`: string or null
  * `name`: object:
    * `givenName`: string or null
    * `familyName`: string or null
    * `formatted`: string or null
  * `emails`: required, array of objects:
    * `value`: required, string
    * `primary`: boolean
    * `type`: string
  * `active`: required, boolean
  * `meta`: required, object:
    * `resourceType`: string
    * `created`: string, format: date-time
    * `lastModified`: string, format: date-time
    * `location`: string, format: uri
  * `organization_id`: integer
  * `operations`: array of objects:
    * `op`: required, string, enum: `add`, `remove`, `replace`
    * `path`: string
    * `value`: one of:
      * **string**
      * **object**
      * **array**
  * `groups`: array of objects:
    * `value`: string
    * `display`: string
  * `roles`: array of objects:
    * `value`: string
    * `primary`: boolean
    * `type`: string
    * `display`: string

#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/scim/v2/organizations/ORG/Users
```

**Response schema (Status: 200):**

* `schemas`: required, array of string
* `totalResults`: required, integer
* `itemsPerPage`: required, integer
* `startIndex`: required, integer
* `Resources`: required, array of `SCIM /Users`:
  * `schemas`: required, array of string
  * `id`: required, string
  * `externalId`: string or null
  * `userName`: string or null
  * `displayName`: string or null
  * `name`: object:
    * `givenName`: string or null
    * `familyName`: string or null
    * `formatted`: string or null
  * `emails`: required, array of objects:
    * `value`: required, string
    * `primary`: boolean
    * `type`: string
  * `active`: required, boolean
  * `meta`: required, object:
    * `resourceType`: string
    * `created`: string, format: date-time
    * `lastModified`: string, format: date-time
    * `location`: string, format: uri
  * `organization_id`: integer
  * `operations`: array of objects:
    * `op`: required, string, enum: `add`, `remove`, `replace`
    * `path`: string
    * `value`: one of:
      * **string**
      * **object**
      * **array**
  * `groups`: array of objects:
    * `value`: string
    * `display`: string
  * `roles`: array of objects:
    * `value`: string
    * `primary`: boolean
    * `type`: string
    * `display`: string

## Provision and invite a SCIM user

```
POST /scim/v2/organizations/{org}/Users
```

Provisions organization membership for a user, and sends an activation email to the email address. If the user was previously a member of the organization, the invitation will reinstate any former privileges that the user had. For more information about reinstating former members, see "Reinstating a former member of your organization."

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`userName`** (string) (required)
  Configured by the admin. Could be an email, login, or username

* **`displayName`** (string)
  The name of the user, suitable for display to end-users

* **`name`** (object) (required)
  * **`givenName`** (string) (required)
  * **`familyName`** (string) (required)
  * **`formatted`** (string)

* **`emails`** (array of objects) (required)
  user emails
  * **`value`** (string) (required)
  * **`primary`** (boolean)
  * **`type`** (string)

* **`schemas`** (array of strings)

* **`externalId`** (string)

* **`groups`** (array of strings)

* **`active`** (boolean)

### HTTP response status codes

* **201** - Created

* **304** - Not modified

* **400** - Bad request

* **403** - Forbidden

* **404** - Resource not found

* **409** - Conflict

* **500** - Internal server error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/scim/v2/organizations/ORG/Users \
  -d '{
  "userName": "mona.octocat@okta.example.com",
  "externalId": "a7d0f98382",
  "name": {
    "givenName": "Monalisa",
    "familyName": "Octocat",
    "formatted": "Monalisa Octocat"
  },
  "emails": [
    {
      "value": "mona.octocat@okta.example.com",
      "primary": true
    },
    {
      "value": "monalisa@octocat.github.com"
    }
  ]
}'
```

**Response schema (Status: 201):**

* `schemas`: required, array of string
* `id`: required, string
* `externalId`: string or null
* `userName`: string or null
* `displayName`: string or null
* `name`: object:
  * `givenName`: string or null
  * `familyName`: string or null
  * `formatted`: string or null
* `emails`: required, array of objects:
  * `value`: required, string
  * `primary`: boolean
  * `type`: string
* `active`: required, boolean
* `meta`: required, object:
  * `resourceType`: string
  * `created`: string, format: date-time
  * `lastModified`: string, format: date-time
  * `location`: string, format: uri
* `organization_id`: integer
* `operations`: array of objects:
  * `op`: required, string, enum: `add`, `remove`, `replace`
  * `path`: string
  * `value`: one of:
    * **string**
    * **object**
    * **array**
* `groups`: array of objects:
  * `value`: string
  * `display`: string
* `roles`: array of objects:
  * `value`: string
  * `primary`: boolean
  * `type`: string
  * `display`: string

## Get SCIM provisioning information for a user

```
GET /scim/v2/organizations/{org}/Users/{scim_user_id}
```

Gets SCIM provisioning information for a user.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`scim_user_id`** (string) (required)
  The unique identifier of the SCIM user.

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/scim/v2/organizations/ORG/Users/SCIM_USER_ID
```

**Response schema (Status: 200):**

Same response schema as [Provision and invite a SCIM user](#provision-and-invite-a-scim-user).

## Update a provisioned organization membership

```
PUT /scim/v2/organizations/{org}/Users/{scim_user_id}
```

Replaces an existing provisioned user's information. You must provide all the information required for the user as if you were provisioning them for the first time. Any existing user information that you don't provide will be removed. If you want to only update a specific attribute, use the Update an attribute for a SCIM user endpoint instead.
You must at least provide the required values for the user: userName, name, and emails.
Warning

Setting active: false removes the user from the organization, deletes the external identity, and deletes the associated {scim\_user\_id}.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`scim_user_id`** (string) (required)
  The unique identifier of the SCIM user.

#### Body parameters

* **`schemas`** (array of strings)

* **`displayName`** (string)
  The name of the user, suitable for display to end-users

* **`externalId`** (string)

* **`groups`** (array of strings)

* **`active`** (boolean)

* **`userName`** (string) (required)
  Configured by the admin. Could be an email, login, or username

* **`name`** (object) (required)
  * **`givenName`** (string) (required)
  * **`familyName`** (string) (required)
  * **`formatted`** (string)

* **`emails`** (array of objects) (required)
  user emails
  * **`type`** (string)
  * **`value`** (string) (required)
  * **`primary`** (boolean)

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/scim/v2/organizations/ORG/Users/SCIM_USER_ID \
  -d '{
  "userName": "mona.octocat@okta.example.com",
  "externalId": "a7d0f98382",
  "name": {
    "givenName": "Monalisa",
    "familyName": "Octocat",
    "formatted": "Monalisa Octocat"
  },
  "emails": [
    {
      "value": "mona.octocat@okta.example.com",
      "primary": true
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision and invite a SCIM user](#provision-and-invite-a-scim-user).

## Update an attribute for a SCIM user

```
PATCH /scim/v2/organizations/{org}/Users/{scim_user_id}
```

Allows you to change a provisioned user's individual attributes. To change a user's values, you must provide a specific Operations JSON format that contains at least one of the add, remove, or replace operations. For examples and more information on the SCIM operations format, see the SCIM specification.
Note

Complicated SCIM path selectors that include filters are not supported. For example, a path selector defined as "path": "emails\[type eq "work"]" will not work.

Warning

If you set active:false using the replace operation (as shown in the JSON example below), it removes the user from the organization, deletes the external identity, and deletes the associated :scim\_user\_id.
{
"Operations":\[{
"op":"replace",
"value":{
"active":false
}
}]
}

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`scim_user_id`** (string) (required)
  The unique identifier of the SCIM user.

#### Body parameters

* **`schemas`** (array of strings)

* **`Operations`** (array of objects) (required)
  Set of operations to be performed
  * **`op`** (string) (required)
    Can be one of: `add`, `remove`, `replace`
  * **`path`** (string)
  * **`value`** (object or array or string)

### HTTP response status codes

* **200** - OK

* **304** - Not modified

* **400** - Bad request

* **403** - Forbidden

* **404** - Resource not found

* **429** - Too Many Requests

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/scim/v2/organizations/ORG/Users/SCIM_USER_ID \
  -d '{
  "Operations": [
    {
      "op": "replace",
      "value": {
        "displayName": "Octocat"
      }
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Provision and invite a SCIM user](#provision-and-invite-a-scim-user).

## Delete a SCIM user from an organization

```
DELETE /scim/v2/organizations/{org}/Users/{scim_user_id}
```

Deletes a SCIM user from an organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`scim_user_id`** (string) (required)
  The unique identifier of the SCIM user.

### HTTP response status codes

* **204** - No Content

* **304** - Not modified

* **403** - Forbidden

* **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/scim/v2/organizations/ORG/Users/SCIM_USER_ID
```

**Response schema (Status: 204):**