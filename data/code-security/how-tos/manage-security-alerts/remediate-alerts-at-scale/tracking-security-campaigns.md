# Tracking security campaigns

Use the campaign tracking views to monitor remediation progress, identify stalled work, and measure campaign impact across your organization.

> \[!NOTE]
> Campaigns for secret scanning alerts are currently in public preview and are subject to change.

## Tracking campaigns across your organization

The tracking view helps you quickly assess the health of your organization’s campaigns. You can use it to identify campaigns with a high number of open alerts, check whether work has started, and determine whether campaigns are on track to meet their due dates.

To display the campaign tracking view, navigate to the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for the organization, then in the left sidebar click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-goal" aria-label="goal" role="img"><path d="M13.637 2.363h-.001l1.676.335c.09.018.164.084.19.173a.25.25 0 0 1-.062.249l-1.373 1.374a.876.876 0 0 1-.619.256H12.31L9.45 7.611A1.5 1.5 0 1 1 6.5 8a1.501 1.501 0 0 1 1.889-1.449l2.861-2.862V2.552c0-.232.092-.455.256-.619L12.88.559a.25.25 0 0 1 .249-.062c.089.026.155.1.173.19Z"></path><path d="M2 8a6 6 0 1 0 11.769-1.656.751.751 0 1 1 1.442-.413 7.502 7.502 0 0 1-12.513 7.371A7.501 7.501 0 0 1 10.069.789a.75.75 0 0 1-.413 1.442A6.001 6.001 0 0 0 2 8Z"></path><path d="M5 8a3.002 3.002 0 0 0 4.699 2.476 3 3 0 0 0 1.28-2.827.748.748 0 0 1 1.045-.782.75.75 0 0 1 .445.61A4.5 4.5 0 1 1 8.516 3.53a.75.75 0 1 1-.17 1.49A3 3 0 0 0 5 8Z"></path></svg> Campaigns**. To display campaigns for secrets, click the **Secrets** tab at the top of the page.

![Screenshot of the security campaigns overview page. The "Secrets" campaign tab is outlined in orange.](/assets/images/help/security/security-campaigns-tracking-overview-2tabs.png)

The tracking view shows you a summary of "Open" and "Closed" campaigns, with the total alert count across all campaigns of that type. The view breaks down the total alert count into the following alert statuses:

* **Open**: the alert is still active and has not yet been addressed.
* **In progress** (code campaigns only): work has started to fix the alert—at least one branch or pull request has been created from the campaign view or alert page.
* **Fixed**: the alert has been resolved, either within or outside of the campaign workflow.
* **Dismissed**: the alert was reviewed but intentionally not fixed; it has been dismissed.

Review the proportion of alerts in each status to understand where action is needed. A high number of **Open** alerts may indicate that remediation has not yet started, while a low number of **In progress** alerts could signal that teams need additional guidance or prioritization.

## Tracking a single campaign

You can similarly track how a single campaign is progressing by viewing the campaign's own tracking page.

To display the tracking page for a campaign, navigate to the "Campaigns" page, select **Code** or **Secrets** campaigns, and then select the campaign you want to view from the list of campaigns.

![Screenshot of campaign tracking view for "Testing Campaigns for CodeQL". The campaign progress is outlined in dark orange.](/assets/images/help/security/driver-sec-campaign-view.png)

The tracking view for a single campaign helps you evaluate whether remediation is progressing as expected and whether additional follow-up is required.

The following indicators help you evaluate whether remediation is progressing as expected and whether additional follow-up is required.

* **Campaign progress**: how many alerts are closed (fixed or dismissed), in progress, or still left to review.
* **Status**: how the campaign is progressing towards its due date.
* **Copilot Autofix** (code campaigns only): number of alerts where Copilot Autofix can generate a fix to resolve the alert.

For example, if many alerts remain open as the due date approaches, you may need to follow up with repository owners or adjust the campaign timeline.

You can also explore campaign repositories and alerts to identify which teams are actively addressing alerts and which may need follow-up.

* **Repository details:** you can expand any repository to show the progress in alert remediation.
* **Alert details:** you can set the "Group by" option to **None** to show a list of all alerts.

You can filter both of these views to focus on a subset of repositories or alerts. For code campaigns, any alerts that are in progress are listed first.