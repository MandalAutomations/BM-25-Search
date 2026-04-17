# Rate limits for GitHub Apps

Rate limits restrict the rate of traffic to GitHub.com, to help ensure consistent access for all users.

GitHub sets a limit on the number of requests a GitHub App can make to the REST API within a specific time period. It also sets a limit on the point value of queries that a GitHub App can make to the GraphQL API within a specific time period. In addition to these primary rate limits, GitHub may also apply secondary rate limits. These limits help to prevent abuse and denial-of-service attacks, and ensure that the system remains available for all users.

The rate limit for GitHub Apps depends on whether the app authenticates with a user access token or an installation access token. It also depends on where the app is owned by or installed on a GitHub Enterprise Cloud organization.

For more information, see [Rate limits for the REST API](/en/rest/overview/rate-limits-for-the-rest-api) and [Rate limits and query limits for the GraphQL API](/en/graphql/overview/resource-limitations).