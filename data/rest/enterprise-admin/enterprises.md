# REST API endpoints for enterprise access verification

Use the REST API to manage enterprise access verification configuration in your GitHub enterprise.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Disable access restrictions for an enterprise

```
POST /enterprises/{enterprise}/access-restrictions/disable
```

Disable access restriction by proxy header using the network proxy owned by the enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






### HTTP response status codes


- **200** - OK


- **400** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/access-restrictions/disable
```

**Response schema (Status: 200):**

* `message`: required, string
* `header_name`: required, string
* `header_value`: required, string





## Enable access restrictions for an enterprise

```
POST /enterprises/{enterprise}/access-restrictions/enable
```

Enable access restriction by proxy header using the network proxy owned by the enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.






### HTTP response status codes


- **200** - OK


- **400** - Forbidden


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/access-restrictions/enable
```

**Response schema (Status: 200):**

Same response schema as [Disable access restrictions for an enterprise](#disable-access-restrictions-for-an-enterprise).