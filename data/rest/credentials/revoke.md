# Revocation

Use the REST API to revoke credentials that you have found exposed on GitHub or elsewhere.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Revoke a list of credentials

```
POST /credentials/revoke
```

Submit a list of credentials to be revoked. This endpoint is intended to revoke credentials the caller does not own and may have found exposed on GitHub.com or elsewhere. It can also be used for credentials associated with an old user account that you no longer have access to. Credential owners will be notified of the revocation.
This endpoint currently accepts the following credential types:

Personal access tokens (classic) (ghp_)
Fine-grained personal access tokens (github_pat_)
OAuth app access tokens (gho_)
User-to-server tokens from GitHub Apps (ghu_)
Refresh tokens from GitHub Apps (ghr_)

Revoked credentials may impact users on GitHub Free, Pro, & Team and GitHub Enterprise Cloud, and GitHub Enterprise Cloud with Enterprise Managed Users.
GitHub cannot reactivate any credentials that have been revoked; new credentials will need to be generated.
To prevent abuse, this API is limited to only 60 unauthenticated requests per hour and a max of 1000 tokens per API request.
Note

Any authenticated requests will return a 403.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.





#### Body parameters

- **`credentials`** (array of strings) (required)
  A list of credentials to be revoked, up to 1000 per request.





### HTTP response status codes


- **202** - Accepted


- **422** - Validation failed, or the endpoint has been spammed.


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/credentials/revoke \
  -d '{
  "credentials": [
    "ghp_1234567890abcdef1234567890abcdef12345678",
    "github_pat_0A1B2C3D4E5F6G7H8I9J0K_ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456",
    "gho_1234567890abcdef1234567890abcdef12345678",
    "ghu_1234567890abcdef1234567890abcdef12345678",
    "ghr_1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef1234567890ab"
  ]
}'
```

**Response schema (Status: 202):**

object