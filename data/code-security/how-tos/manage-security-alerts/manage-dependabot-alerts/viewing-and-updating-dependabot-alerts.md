# Viewing and updating Dependabot alerts

If GitHub discovers insecure dependencies in your project, you can view alert details on the Dependabot tab of your repository. Then, you can update your project to resolve or dismiss the alert.

Your repository's Dependabot tab lists all open and closed Dependabot alerts and corresponding Dependabot security updates. You can filter alerts by package, ecosystem, or manifest. You can sort the list of alerts, and you can click into specific alerts for more details. You can also dismiss or reopen alerts, either one by one or by selecting multiple alerts at once. For more information, see [About Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts).

## About updates for vulnerable dependencies in your repository

Each Dependabot alert has a unique numeric identifier and the Dependabot tab lists an alert for every detected vulnerability. Legacy Dependabot alerts grouped vulnerabilities by dependency and generated a single alert per dependency. If you navigate to a legacy Dependabot alert, you will be redirected to a Dependabot tab filtered for that package.

You can filter and sort Dependabot alerts using a variety of filters and sort options available on the user interface. For more information, see [Viewing and prioritizing Dependabot alerts](#viewing-and-prioritizing-dependabot-alerts) below.

You can also audit actions taken in response to Dependabot alerts. For more information, see [Auditing security alerts](/en/code-security/getting-started/auditing-security-alerts).

## Viewing and prioritizing Dependabot alerts

You can view, sort, and filter Dependabot alerts to focus on the alerts that matter most.

By default, alerts are sorted by **Most important**, which helps you prioritize fixes based on factors such as potential impact, actionability, and relevance. This prioritization is continuously improved and considers signals like CVSS score, dependency scope, and whether vulnerable function calls are detected.

You can view all open and closed Dependabot alerts and corresponding Dependabot security updates in your repository's Dependabot tab.

1. On GitHub, navigate to the main page of the repository.

2. Under the repository name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab. If you cannot see the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="kebab-horizontal" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, and then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality**.

3. In the "Findings" section of the sidebar, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-dependabot" aria-label="dependabot" role="img"><path d="M5.75 7.5a.75.75 0 0 1 .75.75v1.5a.75.75 0 0 1-1.5 0v-1.5a.75.75 0 0 1 .75-.75Zm5.25.75a.75.75 0 0 0-1.5 0v1.5a.75.75 0 0 0 1.5 0v-1.5Z"></path><path d="M6.25 0h2A.75.75 0 0 1 9 .75V3.5h3.25a2.25 2.25 0 0 1 2.25 2.25V8h.75a.75.75 0 0 1 0 1.5h-.75v2.75a2.25 2.25 0 0 1-2.25 2.25h-8.5a2.25 2.25 0 0 1-2.25-2.25V9.5H.75a.75.75 0 0 1 0-1.5h.75V5.75A2.25 2.25 0 0 1 3.75 3.5H7.5v-2H6.25a.75.75 0 0 1 0-1.5ZM3 5.75v6.5c0 .414.336.75.75.75h8.5a.75.75 0 0 0 .75-.75v-6.5a.75.75 0 0 0-.75-.75h-8.5a.75.75 0 0 0-.75.75Z"></path></svg> **Dependabot** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="chevron-down" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> dropdown menu, then click **Vulnerabilities**.

4. Optionally, refine the list of alerts:
   * Use the dropdown menus at the top of the list to sort or filter alerts.

     ![Screenshot of the filter and sort menus in the Dependabot tab.](/assets/images/help/graphs/dependabot-alerts-filters-checkbox.png)

   * Type directly in the search bar to filter alerts, including full-text search across alert details and related security advisories.

   * Click a label on an alert to automatically filter the list by that label.

   * To identify alerts that affect development dependencies, filter by the `scope:development` filter or look for alerts labeled "Development". This can help you prioritize alerts that affect production dependencies first.

     ![Screenshot showing the "Development" label assigned to an alert in the list of alerts.](/assets/images/help/repository/dependabot-alerts-development-label.png)

5. Click an alert to view its details. Alerts for development-scoped dependencies include a "Development" label in the "Tags" section on the alert details page.

   ![Screenshot showing the "Tags" section in the alert details page.](/assets/images/help/repository/dependabot-alerts-tags-section.png)

6. On the right panel, select an assignee by using the **Assignees** dropdown list. You can assign the alert to a user or team to establish clear ownership, or assign it to Copilot to automatically generate a fix. This clearly communicates who is responsible for triaging the alert and helps you avoid repetitive analysis. It also ensures that alerts are not missed.

7. Optionally, to suggest an improvement to the related security advisory, on the right-hand side of the alert details page, click **Suggest improvements for this advisory on the GitHub Advisory Database**. See [Editing security advisories in the GitHub Advisory Database](/en/code-security/security-advisories/working-with-global-security-advisories-from-the-github-advisory-database/editing-security-advisories-in-the-github-advisory-database).

### Tips for prioritizing alerts

* Use the **Most important** sort order to focus on alerts with the highest potential impact.
* Prioritize alerts that affect production dependencies over development dependencies.
* Use the **Assignees** feature to clarify who is responsible for addressing each alert, so your team can track and remediate vulnerabilities more effectively.
* Use Dependabot auto-triage rules to automatically prioritize or manage alerts. See [About Dependabot auto-triage rules](/en/code-security/concepts/supply-chain-security/about-dependabot-auto-triage-rules).

For more information about supported ecosystems and manifest files for dependency scope, see [Supported ecosystems and manifests for dependency scope](/en/code-security/reference/supply-chain-security/supported-ecosystems-and-manifests-for-dependency-scope).

For a complete list of available filters, see [Dependabot alert filters](/en/code-security/reference/supply-chain-security/dependabot-alerts-filters).

To retrieve alerts programmatically, see the [REST API endpoints for Dependabot alerts](/en/rest/dependabot/alerts).

## Reviewing and fixing alerts

You can review the details of a Dependabot alert to understand the vulnerability and how to fix it.

### Fixing vulnerable dependencies

1. View the details for an alert. For more information, see [Viewing and prioritizing Dependabot alerts](#viewing-and-prioritizing-dependabot-alerts) (above).

2. If you have Dependabot security updates enabled, there may be a link to a pull request that will fix the dependency. Alternatively, you can click **Create Dependabot security update** at the top of the alert details page to create a pull request.

   ![Screenshot of a Dependabot alert with the "Create Dependabot security update" button highlighted with a dark orange outline.](/assets/images/help/repository/create-dependabot-security-update-button-ungrouped.png)

3. Optionally, if you do not use Dependabot security updates, you can use the information on the page to decide which version of the dependency to upgrade to and create a pull request to update the dependency to a secure version.

4. When you're ready to update your dependency and resolve the vulnerability, merge the pull request.

   Each pull request raised by Dependabot includes information on commands you can use to control Dependabot. For more information, see [Managing pull requests for dependency updates](/en/code-security/dependabot/working-with-dependabot/managing-pull-requests-for-dependency-updates#managing-dependabot-pull-requests-with-comment-commands).

## Dismissing Dependabot alerts

> \[!NOTE]
> You can only dismiss open alerts.

If you schedule extensive work to upgrade a dependency, or decide that an alert does not need to be fixed, you can dismiss the alert. Dismissing alerts that you have already assessed makes it easier to triage new alerts as they appear.

1. [Viewing and prioritizing Dependabot alerts](#viewing-and-prioritizing-dependabot-alerts) (above).

2. Select the "Dismiss" dropdown, and click a reason for dismissing the alert. Unfixed dismissed alerts can be reopened later.

3. Optionally, add a dismissal comment. The dismissal comment will be added to the alert timeline and can be used as justification during auditing and reporting. You can retrieve or set a comment by using the GraphQL API. The comment is contained in the `dismissComment` field. For more information, see [Objects](/en/graphql/reference/objects#repositoryvulnerabilityalert) in the GraphQL API documentation.

   ![Screenshot of a Dependabot alert page, with the "Dismiss" dropdown and the option to add a dismissal comment outlined in orange.](/assets/images/help/repository/dependabot-alerts-dismissal-comment.png)

4. Click **Dismiss alert**.

### Dismissing multiple alerts at once

1. View the open Dependabot alerts.
2. Optionally, filter the list of alerts by selecting a dropdown menu, then clicking the filter that you would like to apply. You can also type filters into the search bar.
3. To the left of each alert title, select the alerts that you want to dismiss.
   ![Screenshot of the Dependabot alerts view. Two alerts are selected and these check boxes are highlighted with an orange outline.](/assets/images/help/graphs/select-multiple-alerts.png)
4. Optionally, at the top of the list of alerts, select all alerts on the page.
   ![Screenshot of the header section of the Dependabot alerts view. The "Select all" checkbox is highlighted with a dark orange outline.](/assets/images/help/graphs/select-all-alerts.png)
5. Select the "Dismiss alerts" dropdown, and click a reason for dismissing the alerts.
   ![Screenshot of a list of alerts. Below the "Dismiss alerts" button, a dropdown labeled "Select a reason to dismiss" is expanded.](/assets/images/help/graphs/dismiss-multiple-alerts.png)

## Viewing and updating closed alerts

You can view all open alerts, and you can reopen alerts that have been previously dismissed. Closed alerts that have already been fixed cannot be reopened.

1. On GitHub, navigate to the main page of the repository.

2. Under the repository name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab. If you cannot see the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="kebab-horizontal" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, and then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality**.

3. In the "Findings" section of the sidebar, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-dependabot" aria-label="dependabot" role="img"><path d="M5.75 7.5a.75.75 0 0 1 .75.75v1.5a.75.75 0 0 1-1.5 0v-1.5a.75.75 0 0 1 .75-.75Zm5.25.75a.75.75 0 0 0-1.5 0v1.5a.75.75 0 0 0 1.5 0v-1.5Z"></path><path d="M6.25 0h2A.75.75 0 0 1 9 .75V3.5h3.25a2.25 2.25 0 0 1 2.25 2.25V8h.75a.75.75 0 0 1 0 1.5h-.75v2.75a2.25 2.25 0 0 1-2.25 2.25h-8.5a2.25 2.25 0 0 1-2.25-2.25V9.5H.75a.75.75 0 0 1 0-1.5h.75V5.75A2.25 2.25 0 0 1 3.75 3.5H7.5v-2H6.25a.75.75 0 0 1 0-1.5ZM3 5.75v6.5c0 .414.336.75.75.75h8.5a.75.75 0 0 0 .75-.75v-6.5a.75.75 0 0 0-.75-.75h-8.5a.75.75 0 0 0-.75.75Z"></path></svg> **Dependabot** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="chevron-down" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> dropdown menu, then click **Vulnerabilities**.

4. To just view closed alerts, click **Closed**.

   ![Screenshot showing the list of Dependabot alerts with the "Closed" tab highlighted with a dark orange outline.](/assets/images/help/repository/dependabot-alerts-closed-checkbox.png)

5. Click the alert that you would like to view or update.

6. Optionally, if the alert was dismissed and you wish to reopen it, click **Reopen**. Alerts that have already been fixed cannot be reopened.

   ![Screenshot showing a closed Dependabot alert. A button, titled "Reopen", is highlighted in a dark orange outline.](/assets/images/help/repository/reopen-dismissed-alert.png)

### Reopening multiple alerts at once

1. View the closed Dependabot alerts.
2. To the left of each alert title, select the alerts that you want to reopen by clicking the checkbox adjacent to each alert.
3. Optionally, at the top of the list of alerts, select all closed alerts on the page.
   ![Screenshot of alerts in the "Closed" tab. The "Select all" checkbox is highlighted with a dark orange outline.](/assets/images/help/graphs/select-all-closed-alerts.png)
4. Click **Reopen** to reopen the alerts. Alerts that have already been fixed cannot be reopened.

## Reviewing the audit logs for Dependabot alerts

When a member of your organization performs an action related to Dependabot alerts, you can review the actions in the audit log. For more information about accessing the log, see [Reviewing the audit log for your organization](/en/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/reviewing-the-audit-log-for-your-organization#accessing-the-audit-log).

![Screenshot of the audit log showing Dependabot alerts.](/assets/images/help/dependabot/audit-log-ui-dependabot-alert.png)

Events in your audit log for Dependabot alerts include details such as who performed the action, what the action was, and when the action was performed. The event also includes a link to the alert itself. When a member of your organization dismisses an alert, the event displays the dismissal reason and comment. For information on the Dependabot alerts actions, see the `repository_vulnerability_alert` category in [Audit log events for your organization](/en/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/audit-log-events-for-your-organization#repository_vulnerability_alert).