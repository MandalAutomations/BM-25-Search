# Assessing adoption of security features

See which teams and repositories have already enabled features for secure coding, and identify any that are not yet protected.

You can use security overview to see which repositories and teams have already enabled each security feature, and where people need more encouragement to adopt these features.

> \[!NOTE] "Pull request alerts" are reported as enabled only when code scanning has analyzed at least one pull request since alerts were enabled for the repository.

## Viewing the enablement of security features for an organization

You can view data to assess the enablement of features for secure coding across repositories in an organization.

1. On GitHub, navigate to the main page of the organization.
2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
3. To display the "Security coverage" view, in the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-meter" aria-label="meter" role="img"><path d="M8 1.5a6.5 6.5 0 1 0 6.016 4.035.75.75 0 0 1 1.388-.57 8 8 0 1 1-4.37-4.37.75.75 0 1 1-.569 1.389A6.473 6.473 0 0 0 8 1.5Zm6.28.22a.75.75 0 0 1 0 1.06l-4.063 4.064a2.5 2.5 0 1 1-1.06-1.06L13.22 1.72a.75.75 0 0 1 1.06 0ZM7 8a1 1 0 1 0 2 0 1 1 0 0 0-2 0Z"></path></svg> Coverage**.
4. Use options in the page summary to filter results to show the repositories you want to assess. The list of repositories and metrics displayed on the page automatically update to match your current selection. For more information on filtering, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview).
   * Use the **Teams** dropdown to show information only for the repositories owned by one or more teams. For more information, see [Managing team access to an organization repository](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-team-access-to-an-organization-repository).
   * Click **NUMBER enabled** or **NUMBER not enabled** in the header for any feature to show only the repositories with that feature enabled or not enabled.
   * At the top of the list of repositories, click **NUMBER Archived** to show only repositories that are archived.
   * Click in the search box to add further filters to the repositories displayed.

## Viewing the enablement of features for secure coding in an enterprise

You can view data to assess the enablement of security features across organizations in an enterprise.

1. Navigate to GitHub Enterprise Cloud.
2. In the top-right corner of GitHub, click your profile picture.
3. Depending on your environment, click **Enterprise**, or click **Enterprises** then click the enterprise you want to view.
4. At the top of the page, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
5. To display the "Security coverage" view, in the sidebar, click **Coverage**.
6. Use options in the page summary to filter results to show the repositories you want to assess. The list of repositories and metrics displayed on the page automatically update to match your current selection. For more information on filtering, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview).
   * Use the **Teams** dropdown to show information only for the repositories owned by one or more teams. For more information, see [Managing team access to an organization repository](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-team-access-to-an-organization-repository).

   * Click **NUMBER enabled** or **NUMBER not enabled** in the header for any feature to show only the repositories with that feature enabled or not enabled.

   * At the top of the list of repositories, click **NUMBER Archived** to show only repositories that are archived.

   * Click in the search box to add further filters to the repositories displayed.
   > \[!TIP]
   > You can use the `owner` filter in the search field to filter the data by organization. For more information, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview#repository-owner-name-and-type-filters).

## Viewing enablement trends for an organization

You can view data to assess the enablement status and enablement status trends of security features for an organization.

1. On GitHub, navigate to the main page of the organization.
2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
3. In the sidebar, under "Insights," click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-meter" aria-label="meter" role="img"><path d="M8 1.5a6.5 6.5 0 1 0 6.016 4.035.75.75 0 0 1 1.388-.57 8 8 0 1 1-4.37-4.37.75.75 0 1 1-.569 1.389A6.473 6.473 0 0 0 8 1.5Zm6.28.22a.75.75 0 0 1 0 1.06l-4.063 4.064a2.5 2.5 0 1 1-1.06-1.06L13.22 1.72a.75.75 0 0 1 1.06 0ZM7 8a1 1 0 1 0 2 0 1 1 0 0 0-2 0Z"></path></svg> Enablement**.
4. Click on one of the tabs for "Dependabot," "Code scanning," or "Secret scanning" to view enablement trends and the percentage of repositories in your organization with that feature enabled. This data is displayed as a graph and a detailed table.
5. Optionally, use the options at the top of the "Enablement trends" view page to filter the group of repositories you want to see enablement trends for.
   * Use the date picker to set the time range that you want to view enablement trends for.
   * Click in the search box to add further filters on the enablement trends displayed. The filters you can apply are the same as those for the "Overview" dashboard view. For more information, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview).

     ![Screenshot of the "Enablement trends" view for an organization, showing Dependabot status and trends over 30 days, with a filter applied.](/assets/images/help/security-overview/security-overview-enablement-trends.png)

## Viewing enablement trends for an enterprise

You can view data to assess the enablement status and enablement status trends of security features across organizations in an enterprise.

1. Navigate to GitHub Enterprise Cloud.
2. In the top-right corner of GitHub, click your profile picture.
3. Depending on your environment, click **Enterprise**, or click **Enterprises** then click the enterprise you want to view.
4. At the top of the page, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
5. To display the "Enablement trends" view, in the sidebar, under "Insights", click **Enablement**.
6. Click on one of the tabs for "Dependabot," "Code scanning," or "Secret scanning" to view enablement trends and the percentage of repositories across organizations in your enterprise with that feature enabled. This data is displayed as a graph and a detailed table.
7. Optionally, use the options at the top of the "Enablement trends" view page to filter the group of repositories you want to see enablement trends for.
   * Use the date picker to set the time range that you want to view enablement trends for.
   * Click in the search box to add further filters on the enablement trends displayed. For more information, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview).

> \[!TIP] You can use the `owner:` filter in the search field to filter the data by organization. For more information, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview).

## Acting on enablement data

After you have reviewed enablement coverage, consider the following actions.

1. Check if your enterprise has configured overly restrictive policies that limit the use of security features. See [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-code-security-and-analysis-for-your-enterprise).

2. Enable features that should be enabled on all repositories. For information on enabling features for a whole organization, see [Configuring security features in your organization](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization).

   For example, secret scanning alerts and push protection reduce the risk of a security leak no matter what information is stored in the repository. If you see repositories that don't already use these features, you should either enable them or discuss an enablement plan with the team who owns the repository.

3. For other features, consider whether the feature should be enabled in more repositories. For example, there would be no point in enabling Dependabot for repositories that only use ecosystems or languages that are unsupported. As such, it's normal to have some repositories where these features are not enabled.

## Next steps

You can download a CSV file of the data displayed on the "Security coverage" page. This data file can be used for efforts like security research and in-depth data analysis, and can integrate easily with external datasets. See [Exporting data from security overview](/en/code-security/security-overview/exporting-data-from-security-overview).

You can use the "Enablement trends" view to see enablement status and enablement status trends over time for Dependabot, code scanning, or secret scanning across repositories or organizations. See [Viewing enablement trends for an organization](#viewing-enablement-trends-for-an-organization) or [Viewing enablement trends for an enterprise](#viewing-enablement-trends-for-an-enterprise).