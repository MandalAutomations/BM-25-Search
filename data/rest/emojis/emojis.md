# REST API endpoints for emojis

Use the REST API to list and view all the available emojis to use on GitHub.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get emojis

```
GET /emojis
```

Lists all the emojis available to use on GitHub.



### HTTP response status codes


- **200** - OK


- **304** - Not modified




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/emojis
```

**Response schema (Status: 200):**

object, additional properties: string