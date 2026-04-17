# Tracking license activation and initial usage with Copilot usage metrics

Identify and act on GitHub Copilot adoption signals and activation with usage metrics.

After you assign Copilot licenses across your enterprise, you can use the Copilot usage metrics dashboard and APIs to verify that licenses are active and monitor early usage trends. This helps you evaluate whether your rollout is reaching the right people and take quick action if adoption is slower than expected.

To get a wider view of adoption, you can combine dashboard insights with qualitative feedback, for example, short pulse surveys or team check-ins.

## Prerequisite

To access Copilot usage metrics, the **"Copilot usage metrics"** policy must be enabled:

* [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies#defining-policies-for-your-enterprise)
* [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies#enabling-copilot-features-and-models-in-your-organization)

## Step 1: Access the usage metrics dashboard

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. Click the **Insights** tab.

The dashboard displays aggregated telemetry from developer IDEs and updates daily, though data may be up to 3 days behind UTC.

## Step 2: Track license activation

Use the "IDE active users" and "IDE daily active users" charts to confirm that developers are starting to use their assigned licenses.

| Metric                  | What it tells you                                                                 | How to act                                                                                                                                     |
| :---------------------- | :-------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------- |
| IDE active users        | How many licensed developers have used Copilot at least once this calendar month. | Compare to your total assigned licenses. If the number is much lower, verify IDE configuration or communicate activation steps to your teams.  |
| IDE daily active users  | How many unique users are using Copilot each day.                                 | Look for an upward trend in the first two weeks after rollout. A flat line may signal that users need additional enablement or setup guidance. |
| IDE weekly active users | Rolling 7-day total of active users.                                              | Use this to track consistency. Steady or increasing WAU indicates successful activation and recurring use.                                     |

> \[!NOTE]
> Copilot usage metrics reflect activity in supported IDEs only. Usage in Copilot Chat on GitHub.com, GitHub Mobile, Copilot code review, or Copilot CLI is not included in dashboard data.

## Step 3: Identify early adoption signals

Once licenses are active, focus on the metrics that indicate healthy early adoption.

| Signal                | Where to find it in the dashboard | What to look for                                                                                  |
| :-------------------- | :-------------------------------- | :------------------------------------------------------------------------------------------------ |
| Consistent DAU growth | “IDE daily active users” graph    | Steady increase in daily users over the first month.                                              |
| Feature variety       | “Requests per chat mode” graph    | Developers trying multiple chat modes (Ask, Edit, Plan, Agent) suggests curiosity and engagement. |
| Initial agent usage   | “Agent adoption” card             | Even small agent adoption (5–10%) early on is a positive signal of experimentation.               |

Healthy early adoption usually looks like 60–80% of assigned users showing activity within the first month.

## Step 4: Act on limited adoption signals

If your metrics show limited adoption, try one of the following strategies.

| Symptom                | Possible cause                                                       | What to do                                                                     |
| :--------------------- | :------------------------------------------------------------------- | :----------------------------------------------------------------------------- |
| Low total active users | Users haven’t activated licenses or configured Copilot in their IDE. | Re-share onboarding materials or run a short “activation check” session.       |
| Flat daily usage       | Developers tried Copilot once but aren’t returning.                  | Provide enablement resources like Copilot prompts or internal success stories. |
| No agent usage         | Teams may not know about the Copilot agent.                          | Share examples of advanced use cases to encourage exploration.                 |

You can also use Copilot Chat to help diagnose issues. For example:

```copilot copy prompt
What patterns might explain low adoption across some teams in the Copilot metrics export?
```

## Step 5: Track activation programmatically

Now that you have a sense of what adoption data is available to you and what the data tells you about your rollout, consider using the API to continue monitoring adoption over time.

1. Use the **Enterprise Usage endpoint** to retrieve aggregated data for all organizations in your enterprise.
2. Filter the export by `day` or `user_login` to identify newly activated users.
3. Compare `user_initiated_interaction_count` and `code_acceptance_activity_count` to see whether users are actively engaging after license assignment.

## Step 6: Export user-level data for deeper analysis

In some cases, you may need user-level activity data for deeper analysis or to integrate with internal BI tools. Exports are most useful when you want to analyze long-term trends or correlate adoption with other metrics (for example, productivity or enablement activities).

1. In the dashboard, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-download" aria-label="download" role="img"><path d="M2.75 14A1.75 1.75 0 0 1 1 12.25v-2.5a.75.75 0 0 1 1.5 0v2.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25v-2.5a.75.75 0 0 1 1.5 0v2.5A1.75 1.75 0 0 1 13.25 14Z"></path><path d="M7.25 7.689V2a.75.75 0 0 1 1.5 0v5.689l1.97-1.969a.749.749 0 1 1 1.06 1.06l-3.25 3.25a.749.749 0 0 1-1.06 0L4.22 6.78a.749.749 0 1 1 1.06-1.06l1.97 1.969Z"></path></svg> Export JSON** in the top-right corner.
2. Download the NDJSON file and use [Copilot Chat](https://github.com/copilot?ref_product=copilot\&ref_type=engagement\&ref_style=text) to analyze the data. For example, ask:

   ```copilot copy prompt
    * Summarize which organizations show the largest increase in `loc_added_sum` this month.
    * Identify users with high `user_initiated_interaction_count` but low `code_acceptance_activity_count`.
   ```

## Further reading

* [Reminding inactive users to use their GitHub Copilot license](/en/copilot/tutorials/roll-out-at-scale/assign-licenses/remind-inactive-users)
* [Driving GitHub Copilot adoption in your company](/en/copilot/tutorials/roll-out-at-scale/enable-developers/drive-adoption)