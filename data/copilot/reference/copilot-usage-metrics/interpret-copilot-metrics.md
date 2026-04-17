# Interpreting usage and adoption metrics for GitHub Copilot

Copilot usage and adoption metrics reveal patterns in how developers engage with Copilot across your enterprise.

After you’ve viewed the Copilot usage metrics dashboard, you can use this article to interpret each chart and identify opportunities to increase adoption and engagement.

## Reviewing overall usage trends

Use the main usage charts in the dashboard to understand overall adoption and engagement patterns. These charts help you identify where usage is growing, leveling off, or declining, so you can take action to maintain engagement.

| Metric                           | What it shows                                      | How to interpret it                                                                                                       |
| :------------------------------- | :------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------ |
| IDE daily active users (DAU)     | Unique users who interacted with Copilot each day. | Sustained DAU growth signals consistent engagement; sharp declines may indicate configuration issues or reduced interest. |
| IDE weekly active users (WAU)    | Unique users active over a 7-day rolling window.   | A healthy WAU-to-license ratio (>60%) indicates strong ongoing usage.                                                     |
| Code completions acceptance rate | Percentage of suggestions accepted.                | A rising rate suggests increasing trust and usefulness; a drop may point to mismatched suggestions or workflow friction.  |

## Reviewing feature adoption

The "Requests per chat mode" and "Agent adoption" charts show how developers are using Copilot Chat and Copilot agent.

| Signal                 | What it tells you                                                 | What to look for                                                                                                                               |
| :--------------------- | :---------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------- |
| Requests per chat mode | Breakdown of chat interactions by mode—Ask, Edit, Plan, or Agent. | A balanced distribution suggests users are exploring multiple capabilities. Heavy use of one mode can highlight where enablement should focus. |
| Agent adoption         | Percentage of active users who used Copilot agent.                | Growth over time shows that developers are progressing from basic completions to more advanced Copilot features.                               |

## Reviewing model adoption

The "Model usage per day" and "Model usage per chat mode" charts help you understand which AI models are most frequently used.

| Chart                     | Description                                                    | Insights to derive                                                                                  |
| :------------------------ | :------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------- |
| Model usage per day       | Shows which AI models power Copilot Chat activity.             | Identify whether users are primarily engaging with default models or experimenting with newer ones. |
| Model usage per chat mode | Breaks down model usage by chat mode (Ask, Edit, Plan, Agent). | Monitor how model adoption evolves as new models are released.                                      |

> \[!NOTE]
> Model usage charts currently represent chat activity only. Completions data is not included in model breakdowns.

## Reviewing language usage

The "Language usage" and "Language usage per day" charts show which programming languages developers use most often with Copilot.

| Chart                  | Description                                                       | How to use it                                                                                              |
| :--------------------- | :---------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------- |
| Language usage         | Shows the share of Copilot Chat activity by programming language. | Identify where Copilot Chat provides the most value and where additional support or enablement might help. |
| Language usage per day | Tracks daily fluctuations in language activity.                   | Spot shifts in development focus or confirm whether new teams or projects are driving increased activity.  |

## Acting on your insights

Use trends in usage, feature adoption, and language activity to guide enablement and rollout planning.

| Observation                                   | Possible cause                                                        | Suggested action                                                      |
| :-------------------------------------------- | :-------------------------------------------------------------------- | :-------------------------------------------------------------------- |
| High adoption in some teams but low in others | Some teams may not have Copilot Chat enabled or configured correctly. | Verify license assignment and IDE setup; offer team-level onboarding. |
| Steady usage but low agent adoption           | Developers may not be aware of Copilot agent features.                | Share internal demos or success stories.                              |
| Drop in DAU or acceptance rate                | Configuration issues or reduced relevance of suggestions.             | Encourage feedback and verify IDE and extension versions.             |

> \[!TIP]
> Consider combining dashboard trends with feedback from surveys or retrospectives to get a full picture of Copilot’s impact on developer productivity.

## Next steps

* To access metrics programmatically, including enterprise, organization, and user-level records, see [REST API endpoints for Copilot usage metrics](/en/rest/copilot/copilot-usage-metrics).