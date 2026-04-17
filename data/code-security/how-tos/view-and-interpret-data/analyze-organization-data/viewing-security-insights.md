# Viewing security insights

Monitor your organization security posture, identify high-risk repositories, and track alert remediation progress using the overview dashboard in security overview.

The overview page in security overview provides a consolidated dashboard of your organization's security landscape. You can filter the dashboard by time period, tool, and other criteria to focus on specific areas of interest. For more information about the overview dashboard, available metrics, and access permissions, see [About security overview](/en/code-security/concepts/security-at-scale/about-security-overview).

You can download a CSV file of the overview dashboard data for your organization or enterprise. For more information, see [Exporting data from security overview](/en/code-security/how-tos/view-and-interpret-data/analyze-organization-data/exporting-data-from-security-overview).

> \[!NOTE] The summary views ("Overview", "Coverage" and "Risk") show data only for default alerts. Secret scanning alerts for ignored directories and non-provider alerts are all omitted from these views. Consequently, the individual alert views may include a larger number of open and closed alerts.

## Viewing the security overview dashboard

1. On GitHub, navigate to the main page of the organization.
2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
3. The overview page is the primary view that you will see after clicking on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab. To get to the dashboard from another security overview page, in the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Overview**.
4. By default, the **Detection** tab is displayed. If you want to switch to another tab to see other metrics, click **Remediation** or **Prevention**.
5. Use the options at the top of the overview page to filter the group of alerts you want to see metrics for. All of the data and metrics on the page will change as you adjust the filters.

   * Use the date picker to set the time range that you want to view alert activity and metrics for.
   * Click in the search box to add further filters on the alerts and metrics displayed.

   ![Screenshot of the overview page in security overview. Filtering options are outlined in dark orange, including the date picker and search field.](/assets/images/help/security-overview/security-overview-dashboard-filters-3-tab.png)

## Next steps

The dashboard displays metrics about alert status, remediation velocity, and high-risk repositories in your organization. For detailed explanations of each metric and how it's calculated, see [Security overview dashboard metrics](/en/code-security/reference/security-at-scale/security-overview-dashboard-metrics).

You can filter the dashboard by time period, tool, repository, and other criteria. For more information, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview).