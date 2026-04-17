# Viewing your usage of metered products and licenses

Explore your use of features that are billed by usage and see how they contribute to your bill.

> \[!TIP]
> **GitHub Enterprise Server** administrators should instead see [Downloading license use for your enterprise or organization](/en/billing/how-tos/products/download-ghas-license-use).

## Viewing a summary of usage

The options available to you vary according to your role and GitHub plan.

GitHub cloud:

* Anyone can view usage data for their own personal account unless their account is managed by their enterprise (EMU).
* If you are an **owner** or **billing manager** of an enterprise, or an organization on GitHub Team, you will also have access to usage data for that organization or enterprise account.

GitHub Enterprise Server:

* Enterprise owners can access and download usage data for licenses, see [Downloading license use for your enterprise or organization](/en/billing/how-tos/products/download-ghas-license-use).

### Personal accounts

1. Open your billing overview page: [https://github.com/settings/billing](https://github.com/settings/billing?ref_product=github\&ref_type=engagement\&ref_style=text).

2. Use the tabbed view to see a summary of consumed use for each product that you use (in this example, the "Advanced Security" tab is shown).

   ![Screenshot of the tabbed view showing "Advanced Security" with the "View details" links outlined in dark orange.](/assets/images/help/billing/overview-product-summary.png)

3. Optionally, click **View details** to show more detailed information.

### Organization and enterprise accounts

1. Navigate to your organization or enterprise. For example, from the [Organizations](https://github.com/settings/organizations?ref_product=github\&ref_type=engagement\&ref_style=text) or [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) pages on GitHub.com.
2. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-credit-card" aria-label="credit-card" role="img"><path d="M10.75 9a.75.75 0 0 0 0 1.5h1.5a.75.75 0 0 0 0-1.5h-1.5Z"></path><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25ZM14.5 6.5h-13v5.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Zm0-2.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25V5h13Z"></path></svg> Billing & Licensing** to display the billing and licensing overview for the account:
   * **Organization** accounts: under "Access" in the sidebar for settings.
   * **Enterprise** accounts: a separate tab at the top of the page.

## Exploring usage data in more detail

You can also explore usage data for all metered products in more detail in the **Usage** or **Metered usage** view.

* **Filter data on the page**: click in the text box to see a list of available filters.
* **Group data**: options in the "Group" option vary based on the filters you define.
* **Choose a time period**: use the "Time Frame" option.

The metered usage chart and usage break down table both show your current choice of data.

![Screenshot of the metered usage chart showing "Actions grouped by SKU" with the three control fields outlined in dark orange.](/assets/images/help/billing/product-usage-chart.png)

> \[!TIP]
> For GitHub Actions, you can also view the billable job execution minutes for an individual workflow run. For more information, see [Viewing job execution time](/en/actions/monitoring-and-troubleshooting-workflows/viewing-job-execution-time).

## Analyzing use of premium requests

> \[!NOTE]
> Premium request analytics data are available from **August 1, 2025** onward. Separate usage data for features that use premium requests is available from **November 1, 2025** for Copilot, Spark, and Copilot cloud agent.

User-level analytics have different access permissions depending on your role.

* Enterprise owners and billing managers can see premium request analytics by user.
* Organization owners cannot view premium request analytics by user or use the `user` parameter in the API. To view user-level usage, these users can download a premium request usage report. See [Viewing your usage of metered products and licenses](/en/billing/how-tos/products/view-productlicense-use#downloading-usage-reports).

If you use premium requests, an additional **Premium request analytics** view is listed under **Usage**. You can use this view to dig deeper into how you are using included requests and where you are being billed for additional requests. For example:

* What's our total usage of premiums requests across all products?
* Are users making good use of the premium requests included in their license for Copilot?
* Which users have consumed more than their monthly quota?
* How widespread is adoption in the organizations where we rolled out Copilot?

As you change the filter, "Timeframe", and "Group by", and options, all areas of the page are updated to reflect your choices. The chart shows the top 5 consumers and combines any other consumers into "All other".

![Screenshot of the premium request analytics chart, "Usage grouped by organization", and table. A "Show Usage Breakdown" arrow is outlined.](/assets/images/help/billing/premium-request-analytics-chart.png)

To show more detailed information for the top 100 users or organizations consuming premium requests, use the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-right" aria-label="Show Usage Breakdown" role="img"><path d="M6.22 3.22a.75.75 0 0 1 1.06 0l4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L9.94 8 6.22 4.28a.75.75 0 0 1 0-1.06Z"></path></svg> shown at the start of each row to expand and collapse data.

![Screenshot of the premium request analytics table, "Usage breakdown" with the first row expanded to show a full breakdown of requests.](/assets/images/help/billing/premium-request-analytics-org-table.png)

## Downloading usage reports

Visit the "Metered Usage" page to access a metered billing report for all products, or navigate to the "Premium request analytics" page for a specialized report tailored for Premium request activity tracking.

1. At the top of the page, click **Get usage report**.
2. Specify the report details.
3. Click **Email me the report**.

When the report is ready for you to download, you'll receive a message to your primary email account with a link to download the report. The link will expire after 24 hours.

For details of the fields included in the reports, see [Billing reports reference](/en/billing/reference/billing-reports).

### Downloading the data plotted in the chart

When the chart on the "Usage" or "Premium request analytics" page shows the data you want to download, click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Chart options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> "Chart options" button and select your preferred format.

![Screenshot of the usage chart on the "Premium request analytics" page with "Chart options" open and outlined in dark orange.](/assets/images/help/billing/premium-request-analytics-chart-download.png)

## Next steps

* [Billing reports reference](/en/billing/reference/usage-reports)
* [Setting up budgets to control spending on metered products](/en/billing/managing-your-billing/using-budgets-control-spending)
* [Automating usage reporting with the REST API](/en/billing/managing-your-billing/automating-usage-reporting)