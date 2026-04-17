# REST API endpoints for organization interactions

Use the REST API to temporarily restrict which type of user can comment, open issues, or create pull requests in the organization's public repositories.

## About organization interactions

Organization owners can temporarily restrict which type of user can comment, open issues, or create pull requests in the organization's public repositories. When restrictions are enabled, only the specified type of GitHub user will be able to participate in interactions. Restrictions automatically expire after a defined duration. Here's more about the types of GitHub users:

* **Existing users:** When you limit interactions to `existing_users`, new users with accounts less than 24 hours old who have not previously contributed and are not collaborators will be temporarily restricted in the organization.
* **Contributors only:** When you limit interactions to `contributors_only`, users who have not previously contributed and are not collaborators will be temporarily restricted in the organization.
* **Collaborators only:** When you limit interactions to `collaborators_only`, users who are not collaborators will be temporarily restricted in the organization.

Setting the interaction limit at the organization level will overwrite any interaction limits that are set for individual repositories owned by the organization. To set different interaction limits for individual repositories owned by the organization, use the [Repository](/en/rest/interactions/repos) interactions endpoints instead.

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get interaction restrictions for an organization

```
GET /orgs/{org}/interaction-limits
```

Shows which type of GitHub user can interact with this organization and when the restriction expires. If there is no restrictions, you will see an empty response.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/interaction-limits
```

**Response schema (Status: 200):**

* any of:
  * **Interaction Limits**
    * `limit`: required, string, enum: `existing_users`, `contributors_only`, `collaborators_only`
    * `origin`: required, string
    * `expires_at`: required, string, format: date-time
  * **object**

## Set interaction restrictions for an organization

```
PUT /orgs/{org}/interaction-limits
```

Temporarily restricts interactions to a certain type of GitHub user in any public repository in the given organization. You must be an organization owner to set these restrictions. Setting the interaction limit at the organization level will overwrite any interaction limits that are set for individual repositories owned by the organization.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

* **`limit`** (string) (required)
  The type of GitHub user that can comment, open issues, or create pull requests while the interaction limit is in effect.
  Can be one of: `existing_users`, `contributors_only`, `collaborators_only`

* **`expiry`** (string)
  The duration of the interaction restriction. Default: one\_day.
  Can be one of: `one_day`, `three_days`, `one_week`, `one_month`, `six_months`

### HTTP response status codes

* **200** - OK

* **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/interaction-limits \
  -d '{
  "limit": "collaborators_only",
  "expiry": "one_month"
}'
```

**Response schema (Status: 200):**

* `limit`: required, string, enum: `existing_users`, `contributors_only`, `collaborators_only`
* `origin`: required, string
* `expires_at`: required, string, format: date-time

## Remove interaction restrictions for an organization

```
DELETE /orgs/{org}/interaction-limits
```

Removes all interaction restrictions from public repositories in the given organization. You must be an organization owner to remove restrictions.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/interaction-limits
```

**Response schema (Status: 204):**