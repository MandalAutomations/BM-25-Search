# Assessing the security risk of your code

You can use security overview to see which teams and repositories are affected by security alerts, and identify repositories for urgent remedial action.

## Exploring the security risks in your code

You can use the different views on your **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab to explore the security risks in your code.

* **Overview:** use to explore trends in **Detection**, **Remediation**, and **Prevention** of security alerts.
* **Risk:** use to explore the current state of repositories, across all alert types.
* **Assessments:** use to explore the current state of repositories, for secret leaks specifically
* **Findings:** use to explore code scanning, Dependabot, or secret scanning alerts in greater detail.

These views provide you with the data and filters to:

* Assess the landscape of security risk of code stored in all your repositories.
* Identify the highest impact vulnerabilities to address.
* Monitor your progress in remediating potential vulnerabilities.
* Understand how your organization is affected by secret leaks and exposures.
* Export your current selection of data for further analysis and reporting.

For information about the **Overview**, see [Viewing security insights](/en/code-security/security-overview/viewing-security-insights).

## Viewing organization-level security risks in code

1. On GitHub, navigate to the main page of the organization.

2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.

3. To display the "Security risk" view, in the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Risk**.

4. Use options in the page summary to filter results to show the repositories you want to assess. The list of repositories and metrics displayed on the page automatically update to match your current selection. For more information on filtering, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview).

   * Use the **Teams** dropdown to show information only for the repositories owned by one or more teams.
   * Click **NUMBER affected** or **NUMBER unaffected** in the header for any feature to show only the repositories with open alerts or no open alerts of that type.
   * Click any of the descriptions of "Open alerts" in the header to show only repositories with alerts of that type and category. For example, **1 critical** to show the repository with a critical alert for Dependabot.
   * At the top of the list of repositories, click **NUMBER Archived** to show only repositories that are archived.
   * Click in the search box to add further filters to the repositories displayed.

   ![Screenshot of the "Security risk" view for an organization. The options for filtering are outlined in dark orange.](/assets/images/help/security-overview/security-risk-view-highlights.png)

   > \[!NOTE] The set of unaffected repositories includes all repositories without open alerts and also any repositories where the security feature is not enabled.

5. Optionally, use the sidebar on the left to explore alerts for a specific security feature in greater detail. On each page, you can use filters that are specific to that feature to refine your search.

6. Optionally, use the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-download" aria-label="download" role="img"><path d="M2.75 14A1.75 1.75 0 0 1 1 12.25v-2.5a.75.75 0 0 1 1.5 0v2.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25v-2.5a.75.75 0 0 1 1.5 0v2.5A1.75 1.75 0 0 1 13.25 14Z"></path><path d="M7.25 7.689V2a.75.75 0 0 1 1.5 0v5.689l1.97-1.969a.749.749 0 1 1 1.06 1.06l-3.25 3.25a.749.749 0 0 1-1.06 0L4.22 6.78a.749.749 0 1 1 1.06-1.06l1.97 1.969Z"></path></svg> Export CSV** button to download a CSV file of the data currently displayed on the page for security research and in-depth data analysis. For more information, see [Exporting data from security overview](/en/code-security/security-overview/exporting-data-from-security-overview).

> \[!NOTE] The summary views ("Overview", "Coverage" and "Risk") show data only for default alerts. Secret scanning alerts for ignored directories and non-provider alerts are all omitted from these views. Consequently, the individual alert views may include a larger number of open and closed alerts.

## Viewing enterprise-level security risks in code

You can view data for security alerts across organizations in an enterprise.

> \[!TIP]
> You can use the `owner` filter in the search field to filter the data by organization. For more information, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview#repository-owner-name-and-type-filters).

1. Navigate to GitHub Enterprise Cloud.
2. In the top-right corner of GitHub, click your profile picture.
3. Depending on your environment, click **Enterprise**, or click **Enterprises** then click the enterprise you want to view.
4. At the top of the page, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
5. To display the "Security risk" view, in the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Risk**.
6. Use options in the page summary to filter results to show the repositories you want to assess. The list of repositories and metrics displayed on the page automatically update to match your current selection. For more information on filtering, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview).

   * Use the **Teams** dropdown to show information only for the repositories owned by one or more teams.
   * Click **NUMBER affected** or **NUMBER unaffected** in the header for any feature to show only the repositories with open alerts or no open alerts of that type.
   * Click any of the descriptions of "Open alerts" in the header to show only repositories with alerts of that type and category. For example, **1 critical** to show the repository with a critical alert for Dependabot.
   * At the top of the list of repositories, click **NUMBER Archived** to show only repositories that are archived.
   * Click in the search box to add further filters to the repositories displayed.

   ![Screenshot of the "Security risk" view for an enterprise. The options for filtering are outlined in dark orange.](/assets/images/help/security-overview/security-risk-view-highlights-enterprise.png)

   > \[!NOTE] The set of unaffected repositories includes all repositories without open alerts and also any repositories where the security feature is not enabled.
7. Optionally, use the sidebar on the left to explore alerts for a specific security feature in greater detail. On each page, you can use filters that are specific to that feature to refine your search.
8. Optionally, use the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-download" aria-label="download" role="img"><path d="M2.75 14A1.75 1.75 0 0 1 1 12.25v-2.5a.75.75 0 0 1 1.5 0v2.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25v-2.5a.75.75 0 0 1 1.5 0v2.5A1.75 1.75 0 0 1 13.25 14Z"></path><path d="M7.25 7.689V2a.75.75 0 0 1 1.5 0v5.689l1.97-1.969a.749.749 0 1 1 1.06 1.06l-3.25 3.25a.749.749 0 0 1-1.06 0L4.22 6.78a.749.749 0 1 1 1.06-1.06l1.97 1.969Z"></path></svg> **Export CSV** button to download a CSV file of the data currently displayed on the page for security research and in-depth data analysis. For more information, see [Exporting data from security overview](/en/code-security/security-overview/exporting-data-from-security-overview).

> \[!NOTE] The summary views ("Overview", "Coverage" and "Risk") show data only for default alerts. Secret scanning alerts for ignored directories and non-provider alerts are all omitted from these views. Consequently, the individual alert views may include a larger number of open and closed alerts.

## Next steps

When you have assessed your security risks, you are ready to create a security campaign to collaborate with developers to remediate alerts. For information about fixing security alerts at scale, see [Creating and managing security campaigns](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/creating-managing-security-campaigns) and [Running a security campaign to fix alerts at scale](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/best-practice-fix-alerts-at-scale).