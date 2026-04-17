# Viewing the Copilot usage metrics dashboard

Monitor adoption trends and use of Copilot to support long-term enablement.

After your initial rollout, the Copilot usage metrics dashboard helps you monitor how usage evolves over time. By exploring adoption, feature, model, and language trends, you can see how developers are engaging with Copilot and identify areas where additional enablement or communication may drive deeper value.

## Prerequisite

To access Copilot usage metrics, the **"Copilot usage metrics"** policy must be enabled:

* [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies#defining-policies-for-your-enterprise)
* [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies#enabling-copilot-features-and-models-in-your-organization)

## Accessing the dashboard

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. Click the **Insights** tab.
3. In the left sidebar, click **Copilot usage**.

Data in the dashboard is based only on IDE telemetry, and may appear up to three full UTC days behind the current date. See [GitHub Copilot usage metrics](/en/copilot/concepts/copilot-metrics).

## Using Copilot Chat to analyze exported data

For deeper analysis, you can export NDJSON reports from the dashboard and use Copilot Chat to explore the data in more detail. For example, you can ask:

```copilot copy prompt
* Which users have `user_initiated_interaction_count` > 0 but low `code_acceptance_activity_count`?
* Are there specific teams with lower adoption rates?
```

## Next steps

* To learn how to interpret the data in each chart and act on usage trends, see [Interpreting usage and adoption metrics for GitHub Copilot](/en/copilot/reference/interpret-copilot-metrics).
* To learn how to track license activation and initial usage of GitHub Copilot with usage metrics, see [Tracking license activation and initial usage with Copilot usage metrics](/en/copilot/tutorials/roll-out-at-scale/assign-licenses/track-usage-and-adoption).
* To access usage data programmatically, see [REST API endpoints for Copilot usage metrics](/en/rest/copilot/copilot-usage-metrics).