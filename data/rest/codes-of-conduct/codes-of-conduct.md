# REST API endpoints for codes of conduct

Use the REST API to get information about codes of conduct.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get all codes of conduct

```
GET /codes_of_conduct
```

Returns array of all GitHub's codes of conduct.



### HTTP response status codes


- **200** - OK


- **304** - Not modified




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/codes_of_conduct
```

**Response schema (Status: 200):**

Array of `Code Of Conduct`:
  * `key`: required, string
  * `name`: required, string
  * `url`: required, string, format: uri
  * `body`: string
  * `html_url`: required, string or null, format: uri





## Get a code of conduct

```
GET /codes_of_conduct/{key}
```

Returns information about the specified GitHub code of conduct.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`key`** (string) (required)






### HTTP response status codes


- **200** - OK


- **304** - Not modified


- **404** - Resource not found




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/codes_of_conduct/KEY
```

**Response schema (Status: 200):**

* `key`: required, string
* `name`: required, string
* `url`: required, string, format: uri
* `body`: string
* `html_url`: required, string or null, format: uri