# About security campaigns

You can fix security alerts at scale by creating security campaigns and collaborating with developers to burn down your security backlog.

Once you have identified security alerts the next step is to identify the most urgent alerts and get them fixed. Security campaigns are a way to group alerts and share them with developers, so you can collaborate to remediate vulnerabilities in the code and any exposed secrets.

## Security campaigns in your day-to-day work

You can use security campaigns to support many of your aims as a security leader.

* Improving the security posture of the company by leading work to remediate alerts.
* Reinforcing security training for developers by creating a campaign of related, code scanning alerts to fix collaboratively.
* Ensuring that secret scanning alerts are resolved within your remediation target.
* Building collaborative relationships between the security team and developers to promote shared ownership of security alerts.
* Providing clarity to developers on the most urgent alerts to fix and monitoring alert remediation.

## Benefits of using security campaigns

A security campaign has many benefits over other ways of encouraging developers to remediate security alerts. In particular,

* Developers are notified about any security campaigns that they can contribute to.
* Developers can see the alerts you've highlighted for remediation without leaving their normal workflows.
* Each campaign has a named point of contact for questions, reviews, and collaboration.
* For code scanning alerts, GitHub Copilot Autofix is automatically triggered to suggest a resolution.
* For both code scanning and secret scanning, you can assign alerts in a campaign to users with write access or to Copilot cloud agent to automatically generate pull requests with fixes.

You can use one of the templates to select a group of closely related alerts for a campaign. This allows developers to build on the knowledge gained by resolving one alert and use it to fix several more, providing them with an incentive to fix multiple alerts.

In addition, you can use the REST API to create and interact with campaigns more efficiently and at scale. For more information, see [REST API endpoints for security campaigns](/en/rest/campaigns/campaigns).

## Differences between code and secret campaigns

> \[!NOTE]
> Campaigns for secret scanning alerts are currently in public preview and are subject to change.

The creation workflow is the same for all campaigns, but you will notice a few differences in progress tracking and developer experience.

<div class="ghd-tool rowheaders">

| Property                       | Code                                                                                                                                                                                                                                                                                                                                                         | Secret                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Alerts available for inclusion | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> Default branch only                 | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                            |
| Repository tracking issues     | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                     | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Not supported" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> |
| Developer notifications        | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> Requires write access to repository | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> Requires view access to alerts list                                                                        |
|                                |                                                                                                                                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Alert assignment               | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                     | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> May raise permissions                                                                                      |
|                                |                                                                                                                                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Automatic remediation support  | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> GitHub Copilot Autofix              | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Not supported" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> |

</div>

## About assigning alerts to users and Copilot cloud agent

You can assign a code scanning or secret scanning alert to any user who has **write** access for the repository.

If the assignee for a secret scanning alert **cannot view the alert list**, their permissions are temporarily raised for that alert. Any additional permissions are revoked when they are unassigned from the alert.

GitHub notifies users:

* When they are assigned to an alert
* When that alert is dismissed

For code scanning, you can also perform some of these operations programmatically using the REST API, such as assigning or unassigning users to alerts, and filtering alerts by assignee. For more information, see [REST API endpoints for code scanning](/en/rest/reference/code-scanning) in the REST API documentation. Additionally, webhooks are available to notify you when an alert is assigned or an assignment is removed.

If an autofix has been generated for alerts in a security campaign, you can select those alerts and assign them to Copilot cloud agent. Copilot will create a pull request and add you as a requested reviewer. See [Fixing alerts in a security campaign](/en/code-security/code-scanning/managing-code-scanning-alerts/fixing-alerts-in-security-campaign#assigning-alerts-to-copilot-cloud-agent).

## Next steps

* [Running a security campaign to fix alerts at scale](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/best-practice-fix-alerts-at-scale)
* [Creating and managing security campaigns](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/creating-managing-security-campaigns)