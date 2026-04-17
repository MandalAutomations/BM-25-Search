# REST API endpoints for enterprise announcement banners

The Enterprise Announcement Banners API allows you to get, set, and remove the announcement banner for your enterprise.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get announcement banner for enterprise

```
GET /enterprises/{enterprise}/announcement
```

Gets the announcement banner currently set for the enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/announcement
```

**Response schema (Status: 200):**

* `announcement`: required, string or null
* `expires_at`: required, string or null, format: date-time
* `user_dismissible`: required, boolean or null, default: `false`





## Set announcement banner for enterprise

```
PATCH /enterprises/{enterprise}/announcement
```

Sets the announcement banner to display for the enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`announcement`** (string or null) (required)
  The announcement text in GitHub Flavored Markdown. For more information about GitHub Flavored Markdown, see "Basic writing and formatting syntax."

- **`expires_at`** (string or null)
  The time at which the announcement expires. This is a timestamp in ISO 8601 format: YYYY-MM-DDTHH:MM:SSZ. To set an announcement that never expires, omit this parameter, set it to null, or set it to an empty string.

- **`user_dismissible`** (boolean or null)
  Whether an announcement can be dismissed by the user.
  Default: `false`





### HTTP response status codes


- **200** - OK




### Code examples



#### Announcement banner

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/announcement \
  -d '{
  "announcement": "Very **important** announcement about _something_.",
  "expires_at": "2021-01-01T00:00:00.000+00:00",
  "user_dismissible": false
}'
```

**Response schema (Status: 200):**

Same response schema as [Get announcement banner for enterprise](#get-announcement-banner-for-enterprise).





## Remove announcement banner from enterprise

```
DELETE /enterprises/{enterprise}/announcement
```

Removes the announcement banner currently set for the enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






### HTTP response status codes


- **204** - No Content




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/announcement
```

**Response schema (Status: 204):**