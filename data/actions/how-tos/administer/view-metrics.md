# Viewing GitHub Actions metrics

You can view metrics to monitor where your organization or repositories use GitHub Actions and how they are performing.

## Viewing GitHub Actions metrics for your organization

> \[!NOTE]
> There may be a discrepancy between the **Workflows** tab's job count and the **Jobs** tab's count due to differences in how unique jobs are identified. This does not affect the total minutes calculated.

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. Click the name of your organization.
3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights**.

   ![Screenshot of the horizontal navigation bar for an organization. A tab, labeled with a graph icon and "Insights," is outlined in dark orange.](/assets/images/help/organizations/org-nav-insights-tab.png)
4. In the "Insights" navigation menu, click **Actions Usage Metrics** or click **Actions Performance Metrics**.
5. Optionally, to select a time period to view usage metrics for, choose an option from the **Period** drop down menu at the top right of the page. For more information, see [Viewing GitHub Actions metrics](/en/actions/how-tos/administering-github-actions/viewing-github-actions-metrics#understanding-github-actions-metrics-aggregation).
6. Click on the tab that contains the metrics you would like to view. For more information, see [About GitHub Actions metrics](/en/actions/concepts/about-github-actions-metrics).
7. Optionally, to filter the data displayed in a tab, create a filter.
   1. Click on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-filter" aria-label="filter" role="img"><path d="M.75 3h14.5a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1 0-1.5ZM3 7.75A.75.75 0 0 1 3.75 7h8.5a.75.75 0 0 1 0 1.5h-8.5A.75.75 0 0 1 3 7.75Zm3 4a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 0 1.5h-2.5a.75.75 0 0 1-.75-.75Z"></path></svg> Filter** button.
   2. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add a filter**.
   3. Choose a metric you would like to filter results by.
   4. Depending on the metric you chose, fill out information in the "Qualifier," "Operator," and "Value" columns.
   5. Optionally, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add a filter** to add another filter.
   6. Click **Apply**.
8. Optionally, to download usage metrics to a CSV file, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-download" aria-label="Download report" role="img"><path d="M2.75 14A1.75 1.75 0 0 1 1 12.25v-2.5a.75.75 0 0 1 1.5 0v2.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25v-2.5a.75.75 0 0 1 1.5 0v2.5A1.75 1.75 0 0 1 13.25 14Z"></path><path d="M7.25 7.689V2a.75.75 0 0 1 1.5 0v5.689l1.97-1.969a.749.749 0 1 1 1.06 1.06l-3.25 3.25a.749.749 0 0 1-1.06 0L4.22 6.78a.749.749 0 1 1 1.06-1.06l1.97 1.969Z"></path></svg>.

## Viewing GitHub Actions metrics for your repository

> \[!NOTE]
> There may be a discrepancy between the **Workflows** tab's job count and the **Jobs** tab's count due to differences in how unique jobs are identified. This does not affect the total minutes calculated.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights** tab.
3. In the "Insights" navigation menu, click **Actions Usage Metrics** or click **Actions Performance Metrics**.
4. Optionally, to select a time period to view usage metrics for, choose an option from the **Period** drop down menu at the top right of the page. For more information, see [Viewing GitHub Actions metrics](/en/actions/how-tos/administering-github-actions/viewing-github-actions-metrics#understanding-github-actions-metrics-aggregation).
5. Click on the tab that contains the metrics you would like to view. For more information, see [About GitHub Actions metrics](/en/actions/concepts/about-github-actions-metrics).
6. Optionally, to filter the data displayed in a tab, create a filter.
   1. Click on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-filter" aria-label="filter" role="img"><path d="M.75 3h14.5a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1 0-1.5ZM3 7.75A.75.75 0 0 1 3.75 7h8.5a.75.75 0 0 1 0 1.5h-8.5A.75.75 0 0 1 3 7.75Zm3 4a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 0 1.5h-2.5a.75.75 0 0 1-.75-.75Z"></path></svg> Filter** button.
   2. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add a filter**.
   3. Choose a metric you would like to filter results by.
   4. Depending on the metric you chose, fill out information in the "Qualifier," "Operator," and "Value" columns.
   5. Optionally, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add a filter** to add another filter.
   6. Click **Apply**.
7. Optionally, to download usage metrics to a CSV file, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-download" aria-label="Download report" role="img"><path d="M2.75 14A1.75 1.75 0 0 1 1 12.25v-2.5a.75.75 0 0 1 1.5 0v2.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25v-2.5a.75.75 0 0 1 1.5 0v2.5A1.75 1.75 0 0 1 13.25 14Z"></path><path d="M7.25 7.689V2a.75.75 0 0 1 1.5 0v5.689l1.97-1.969a.749.749 0 1 1 1.06 1.06l-3.25 3.25a.749.749 0 0 1-1.06 0L4.22 6.78a.749.749 0 1 1 1.06-1.06l1.97 1.969Z"></path></svg>.

## Understanding GitHub Actions metrics aggregation

The time period selection feature allows you to view GitHub Actions metrics over predefined periods, as detailed in the following table. These metrics exclude skipped runs and those that use zero minutes. Data is presented using Coordinated Universal Time (UTC) days.

<div class="ghd-tool rowheaders">

| Period                 | Description                                                                                                                      |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Current week (Mon-Sun) | Data from Monday through the current day when the page is viewed.                                                                |
| Current month          | Data from the first of the month to the current day when the page is viewed.                                                     |
| Last month             | Data from the first day to the last day of the previous month.                                                                   |
| Last 30 days           | Data from the last 30 days to when the page is viewed.                                                                           |
| Last 90 days           | Data from the last 90 days to when the page is viewed.                                                                           |
| Last year              | Data aggregated for the last 12 months.                                                                                          |
| Custom                 | Data from a custom date range. The range can be up to 100 days including the start and end dates and go back as far as one year. |

</div>