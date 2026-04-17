# Viewing API insights in your organization

You can view REST API activity for your entire organization or specific apps and users.

## About API insights

As a GitHub Enterprise Cloud organization owner, you and your designated users can view REST API activity for your entire organization or specific apps and users. This helps you understand the sources of your REST API activity and manage against your primary rate limits, giving you visibility into the timeframe, apps, and API endpoints involved. To learn more about primary rate limits, see [Rate limits for the REST API](/en/enterprise-cloud@latest/rest/using-the-rest-api/rate-limits-for-the-rest-api#about-primary-rate-limits).

> \[!NOTE] Currently, this feature supports only the `core` category of REST API endpoints and primary rate limits. API activity for search, GitHub Actions (using the [`GITHUB_TOKEN`](/en/enterprise-cloud@latest/actions/security-for-github-actions/security-guides/automatic-token-authentication) secret), and secondary rate-limiting are not supported. For information about API categories, see [REST API endpoints for rate limits](/en/enterprise-cloud@latest/rest/rate-limit/rate-limit). To learn more about primary and secondary rate limits, see [Rate limits for the REST API](/en/enterprise-cloud@latest/rest/using-the-rest-api/rate-limits-for-the-rest-api).

## Enabling access to API insights

Organization owners can create custom organization roles to allow people to view API insights for their organization. To provide users with access, select the **View organization API insights** permission when creating a custom organization role. Then assign the custom role to an organization member or team. For more information, see [Permissions of custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles).

> \[!WARNING] Granting access to organization non-owners will allow them to view API insights for all users and apps in the organization, so privacy should be considered.

## Understanding API insights aggregation

The time period selection feature allows you to view API insights over predefined periods or a custom period, as detailed in the following table. By default, data is presented in Coordinated Universal Time (UTC). You can change the data displayed from UTC to your browser's time zone in the "Period" drop down menu at the top-right of the page.

<div class="ghd-tool rowheaders">

| Period          | Description                                                                                                |
| --------------- | ---------------------------------------------------------------------------------------------------------- |
| Last 30 minutes | Data from the last 30 minutes to when the page is viewed.                                                  |
| Last 1 hour     | Data from the last 1 hour to when the page is viewed.                                                      |
| Last 3 hours    | Data from the last 3 hours to when the page is viewed.                                                     |
| Last 12 hours   | Data from the last 12 hours to when the page is viewed.                                                    |
| Last 24 hours   | (Default) Data from the last 24 hours to when the page is viewed.                                          |
| Last 7 days     | Data from the last 7 days to when the page is viewed.                                                      |
| Last 31 days    | Data from the last 31 days to when the page is viewed.                                                     |
| Custom          | Data from a custom date and time range that you provide. Custom ranges must begin within the last 31 days. |

</div>

## Viewing API insights for an organization

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. Click the name of your organization.
3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights**.

   ![Screenshot of the horizontal navigation bar for an organization. A tab, labeled with a graph icon and "Insights," is outlined in dark orange.](/assets/images/help/organizations/org-nav-insights-tab.png)
4. In the "Insights" navigation menu, click **REST API**.
5. Optionally, to select a time period to view API insights for, choose an option from the **Period** drop down menu at the top-right of the page. For more information, see [Understanding API insights aggregation](#understanding-api-insights-aggregation).
6. Optionally, to switch between displaying dates and times in Coordinated Universal Time (UTC) or the local time zone used by your browser, select "UTC" or "Local" from the **Period** drop down menu at the top-right of the page.
7. Optionally, to select how granularly to display REST API requests on the chart, choose an option from the **Interval** drop down menu at the top-right of the page. Large intervals show summaries of the API activity on the chart while smaller intervals show greater detail for the selected time period. The chart does not automatically update to show new activity.

The selected period and interval automatically become part of the page URL so that if you share the URL with someone, they will see the same view.

## Viewing API insights for an organization's apps and users

The "Actors" table displays GitHub Apps and users that made REST API requests in the current organization within the selected time period. The table does not automatically update to show new activity.

1. First, view API insights for an organization using the steps above in [Viewing API insights for an organization](#viewing-api-insights-for-an-organization).
2. Filter the apps and users displayed in the "Actors" table.
   1. To filter by name, enter the first few letters of the name in the search field above the "Actors" table. Then press enter.
   2. To filter by type of actor (app or user), choose an option from the **Type** drop down menu above the top-right of the "Actors" table.
   3. To filter by type of request (all or primary-rate-limited), choose an option from the **Requests** drop down menu above the top-right of the "Actors" table.

## Viewing API insights for a specific app or user in an organization

1. First, view API insights for an organization using the steps above in [Viewing API insights for an organization](#viewing-api-insights-for-an-organization).
2. Optionally, select an app in the "Actors" table to display its REST API activity and any primary-rate-limiting. The resulting view will be specific to the selected app and will display the API endpoints it accessed.
3. Optionally, select a user in the "Actors" table to display their personal REST API activity. The resulting view will be specific to the selected user and will display API activity of their personal access tokens and requests made by OAuth apps on their behalf. Both contribute to a user’s personal primary rate limit. For information about primary rate limits for users, and OAuth apps that act on their behalf, see [Rate limits for the REST API](/en/enterprise-cloud@latest/rest/using-the-rest-api/rate-limits-for-the-rest-api#primary-rate-limit-for-authenticated-users).
   1. Optionally, in the user-specific view, click on a personal access token or OAuth app to view its REST API activity made on behalf of the user.