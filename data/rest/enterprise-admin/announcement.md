# REST API endpoints for global announcements

Use the REST API to manage the global announcement banner in your enterprise.

## About announcements

You can use the REST API to manage the global announcement banner in your enterprise. For more information, see [Customizing user messages for your enterprise](/en/enterprise-server@3.20/admin/user-management/managing-users-in-your-enterprise/customizing-user-messages-for-your-enterprise#creating-a-global-announcement-banner).

> \[!NOTE]
> These endpoints only support authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2022-11-28`. Curl examples below omit these standard headers for brevity.

## Get the global announcement banner

```
GET /enterprise/announcement
```

Gets the current message and expiration date of the global announcement banner in your enterprise.

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  http(s)://HOSTNAME/api/v3/enterprise/announcement
```

**Response schema (Status: 200):**

* `announcement`: required, string or null
* `expires_at`: string or null, format: date-time
* `user_dismissible`: boolean or null, default: `false`

## Set the global announcement banner

```
PATCH /enterprise/announcement
```

Sets the message and expiration time for the global announcement banner in your enterprise.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

* **`announcement`** (string or null) (required)
  The announcement text in GitHub Flavored Markdown. For more information about GitHub Flavored Markdown, see "Basic writing and formatting syntax."

* **`expires_at`** (string or null)
  The time at which the announcement expires. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ. To set an announcement that never expires, omit this parameter, set it to null, or set it to an empty string.

* **`user_dismissible`** (boolean or null)
  Whether an announcement can be dismissed by the user.
  Default: `false`

### HTTP response status codes

* **200** - OK

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  http(s)://HOSTNAME/api/v3/enterprise/announcement \
  -d '{
  "announcement": "Very **important** announcement about _something_.",
  "expires_at": "2021-01-01T00:00:00.000+00:00"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get the global announcement banner](#get-the-global-announcement-banner).

## Remove the global announcement banner

```
DELETE /enterprise/announcement
```

Removes the global announcement banner in your enterprise.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  http(s)://HOSTNAME/api/v3/enterprise/announcement
```

**Response schema (Status: 204):**