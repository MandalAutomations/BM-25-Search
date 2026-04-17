# REST API endpoints for feeds

Use the REST API to interact with GitHub feeds.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get feeds

```
GET /feeds
```

Lists the feeds available to the authenticated user. The response provides a URL for each feed. You can then get a specific feed by sending a request to one of the feed URLs.

Timeline: The GitHub global public timeline
User: The public timeline for any user, using uri_template. For more information, see "Hypermedia."
Current user public: The public timeline for the authenticated user
Current user: The private timeline for the authenticated user
Current user actor: The private timeline for activity created by the authenticated user
Current user organizations: The private timeline for the organizations the authenticated user is a member of.
Security advisories: A collection of public announcements that provide information about security-related vulnerabilities in software on GitHub.

By default, timeline resources are returned in JSON. You can specify the application/atom+xml type in the Accept header to return timeline resources in Atom format. For more information, see "Media types."
Note

Private feeds are only returned when authenticating via Basic Auth since current feed URIs use the older, non revocable auth tokens.



### HTTP response status codes


- **200** - OK




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/feeds
```

**Response schema (Status: 200):**

* `timeline_url`: required, string
* `user_url`: required, string
* `current_user_public_url`: string
* `current_user_url`: string
* `current_user_actor_url`: string
* `current_user_organization_url`: string
* `current_user_organization_urls`: array of string, format: uri
* `security_advisories_url`: string
* `repository_discussions_url`: string
* `repository_discussions_category_url`: string
* `_links`: required, object:
  * `timeline`: required, `Link With Type`:
    * `href`: required, string
    * `type`: required, string
  * `user`: required, `Link With Type`:
    * `href`: required, string
    * `type`: required, string
  * `security_advisories`: `Link With Type`:
    * `href`: required, string
    * `type`: required, string
  * `current_user`: `Link With Type`:
    * `href`: required, string
    * `type`: required, string
  * `current_user_public`: `Link With Type`:
    * `href`: required, string
    * `type`: required, string
  * `current_user_actor`: `Link With Type`:
    * `href`: required, string
    * `type`: required, string
  * `current_user_organization`: `Link With Type`:
    * `href`: required, string
    * `type`: required, string
  * `current_user_organizations`: array of `Link With Type`:
    * `href`: required, string
    * `type`: required, string
  * `repository_discussions`: `Link With Type`:
    * `href`: required, string
    * `type`: required, string
  * `repository_discussions_category`: `Link With Type`:
    * `href`: required, string
    * `type`: required, string