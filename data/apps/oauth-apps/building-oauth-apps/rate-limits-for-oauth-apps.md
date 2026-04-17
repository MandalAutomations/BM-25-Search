# Rate limits for OAuth apps

Rate limits restrict the rate of traffic to GitHub.com, to help ensure consistent access for all users.

> \[!NOTE]
> Consider building a GitHub App instead of an OAuth app. The rate limit for GitHub Apps using an installation access token scales with the number of repositories and number of organization users. Conversely, OAuth apps have lower rate limits and do not scale. For more information, see [Differences between GitHub Apps and OAuth apps](/en/apps/oauth-apps/building-oauth-apps/differences-between-github-apps-and-oauth-apps) and [About creating GitHub Apps](/en/apps/creating-github-apps/setting-up-a-github-app/about-creating-github-apps).

> \[!WARNING]
> OAuth apps are subject to a rate limit of **2,000 access token requests per hour**. If your application exceeds this limit, further requests to generate new access tokens will be temporarily blocked, and you may receive error responses. **This can lead to temporary outages**. Please plan your implementation accordingly to avoid potential service interruptions.

## About rate limits for OAuth apps

OAuth apps act on behalf of a user, by making requests with a user access token after the user authorizes the app. For more information, see [Authorizing OAuth apps](/en/apps/oauth-apps/building-oauth-apps/authorizing-oauth-apps).

The generation of these user access tokens is subject to a rate limit. Additionally, API requests made with these user access tokens are subject to rate limits.

## Rate limits for signing in users

OAuth apps should always cache their tokens, and only rarely need to sign in a user. Repeatedly signing in a user can indicate a bug, most frequently seen as an infinite loop between the app and GitHub. If an app signs the user in ten times within one hour, the next sign in within the same hour will require re-authorization of the application. This ensures the user is aware that the app is minting so many tokens, and provides a break in what may be an infinite loop otherwise. This ten *sign in* rate limit is distinct from the ten *token* limit also enforced for OAuth apps. For information about the ten token limit, see [Authorizing OAuth apps](/en/apps/oauth-apps/building-oauth-apps/authorizing-oauth-apps#creating-multiple-tokens-for-oauth-apps).

## Rate limits for the API

GitHub sets a limit on the number of requests a OAuth app can make to the REST API within a specific time period. It also sets a limit on the point value of queries that a OAuth app can make to the GraphQL API within a specific time period. In addition to these primary rate limits, GitHub may also apply secondary rate limits. These limits help to prevent abuse and denial-of-service attacks, and ensure that the system remains available for all users.

For more information, see [Rate limits for the REST API](/en/rest/overview/rate-limits-for-the-rest-api) and [Rate limits and query limits for the GraphQL API](/en/graphql/overview/resource-limitations).

## Further reading

* [Rate limits for the REST API](/en/rest/overview/rate-limits-for-the-rest-api)
* [Rate limits and query limits for the GraphQL API](/en/graphql/overview/resource-limitations)
* [Rate limits for GitHub Apps](/en/apps/creating-github-apps/registering-a-github-app/rate-limits-for-github-apps)