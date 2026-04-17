# Supported AI models in GitHub Copilot

Learn about the supported AI models in GitHub Copilot.

GitHub Copilot supports multiple models, each with different strengths. Some models prioritize speed and cost-efficiency, while others are optimized for accuracy, reasoning, or working with multimodal inputs (like images and code together).

Depending on your Copilot plan and where you're using it—such as GitHub.com or an IDE—you may have access to different models.

> \[!NOTE]
>
> * Model availability is subject to change. Some models may be replaced or updated over time.
> * In Visual Studio Code you can add more models than those that are available by default with your Copilot subscription. See [Changing the AI model for GitHub Copilot Chat](/en/copilot/how-tos/use-ai-models/change-the-chat-model?tool=vscode#adding-more-models).

For all of the default AI models, input prompts and output completions run through GitHub Copilot's content filters for harmful, offensive, or off-topic content, and for public code matching when enabled.

## Supported AI models in Copilot

This table lists the AI models available in Copilot, along with their release status and availability in different modes.

<div class="ghd-tool rowheaders">

| Model name | Provider | Release status | Agent mode | Ask mode | Edit mode |
| ---------- | -------- | -------------- | ---------- | -------- | --------- |
|            |          |                |            |          |           |

</div>

## Supported AI models in Auto model selection

This table lists the AI models available in Auto model selection.

<div class="ghd-tool rowheaders">

| Model | Copilot cloud agent | Copilot Chat |
| ----- | ------------------- | ------------ |
|       |                     |              |

</div>

## Model retirement history

The following table lists AI models that are retired or scheduled for retirement from Copilot, along with their retirement dates and suggested alternatives.

<div class="ghd-tool rowheaders">

| Model name | Retirement date | Suggested alternative |
| ---------- | --------------- | --------------------- |
|            |                 |                       |

</div>

## Supported AI models per client

The following table shows which models are available in each client.

> \[!NOTE]
>
> * When you use Copilot Chat in supported IDEs, **Auto** will automatically select the best model for you based on availability. You can manually choose a different model to override this selection. See [About Copilot auto model selection](/en/copilot/concepts/auto-model-selection) and [Changing the AI model for GitHub Copilot Chat](/en/copilot/how-tos/use-ai-models/change-the-chat-model?tool=vscode).
> * GPT-5-Codex is supported in Visual Studio Code v1.104.1 or higher.

<div class="ghd-tool rowheaders">

| Model | GitHub.com | Copilot CLI | Visual Studio Code | Visual Studio | Eclipse | Xcode | JetBrains IDEs |
| ----- | ---------- | ----------- | ------------------ | ------------- | ------- | ----- | -------------- |
|       |            |             |                    |               |         |       |                |

</div>

## Supported AI models per Copilot plan

The following table shows which AI models are available in each Copilot plan. For more information about the plans, see [Plans for GitHub Copilot](/en/copilot/about-github-copilot/plans-for-github-copilot).

<div class="ghd-tool rowheaders">

| Available models in chat | Copilot Free | Copilot Student | Copilot Pro | Copilot Pro+ | Copilot Business | Copilot Enterprise |
| ------------------------ | ------------ | --------------- | ----------- | ------------ | ---------------- | ------------------ |
|                          |              |                 |             |              |                  |                    |

</div>

## Model multipliers

> \[!NOTE]
> The multiplier for these models are subject to change.
>
> * Claude Sonnet 4.6
> * GPT-5.4 mini

> \[!IMPORTANT] Claude Opus 4.7 is available at a promotional multiplier of 7.5x until April 30, 2026.

Each model has a premium request multiplier, based on its complexity and resource usage. If you are on a paid Copilot plan, your premium request allowance is deducted according to this multiplier.

For more information about premium requests, see [Requests in GitHub Copilot](/en/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests).

<div class="ghd-tool rowheaders">

| Model | Multiplier for **paid plans** | Multiplier for **Copilot Free** |
| ----- | ----------------------------- | ------------------------------- |
|       |                               |                                 |

</div>

## Fallback and long-term support (LTS) models

For more information about fallback and LTS models, see [Base and long-term support (LTS) models](/en/copilot/concepts/fallback-and-lts-models).

## Evaluation models

GitHub Copilot offers access to evaluation models—including top-performing open source and open-weight models—to provide the most advanced coding suggestions available.

> \[!NOTE]
> Testing of evaluation models has revealed that some may perform worse than other models on security-related or other categories of prompts. Customers are encouraged to validate code, including code security, using a range of models and thorough human review before incorporating suggestions into production.

Evaluation models may be added, updated, or removed without notice. Availability and rate limits may differ from generally available models.

## Next steps

* For task-based guidance on selecting a model, see [AI model comparison](/en/copilot/reference/ai-models/model-comparison).
* To configure which models are available to you, see [Configuring access to AI models in GitHub Copilot](/en/copilot/using-github-copilot/ai-models/configuring-access-to-ai-models-in-copilot).
* To learn how to change your current model, see [Changing the AI model for GitHub Copilot Chat](/en/copilot/using-github-copilot/ai-models/changing-the-ai-model-for-copilot-chat) or [Changing the AI model for GitHub Copilot inline suggestions](/en/copilot/how-tos/use-ai-models/change-the-completion-model).
* To learn more about Responsible Use and Responsible AI, see [Copilot Trust Center](https://copilot.github.trust.page/) and [Responsible use of GitHub Copilot features](/en/copilot/responsible-use-of-github-copilot-features).
* To learn how Copilot Chat serves different AI models, see [Hosting of models for GitHub Copilot](/en/copilot/reference/ai-models/model-hosting).