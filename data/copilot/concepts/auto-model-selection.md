# About Copilot auto model selection

Automatically select models for Copilot Chat, Copilot cloud agent, and third-party agents.

## Overview

Experience less rate limiting and reduce the mental load of choosing a model by letting Copilot auto model selection choose the best available model on your behalf.

Copilot auto model selection intelligently chooses models based on real time system health and model performance.  You benefit from:

* Reduced rate limiting
* Lower latency and errors
* Discounted multipliers for paid plans (Copilot Chat only)

Auto model selection **won't** include these models:

* Models excluded by administrator policies. See [Configuring access to AI models in GitHub Copilot](/en/copilot/how-tos/copilot-on-github/set-up-copilot/configure-access-to-ai-models).
* Models with premium request multipliers greater than one. See [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models#model-multipliers).
* Models not available in your plan. See [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models#supported-ai-models-per-copilot-plan).

> \[!NOTE] Soon Copilot auto model selection will choose the best model for you based on your task.

## Auto model selection in Copilot Chat

Auto model selection is generally available in the following IDEs:

* VS Code
* JetBrains IDEs

Auto model selection is in public preview for the following IDEs:

* Visual Studio
* Eclipse
* Xcode

When you select **Auto** in Copilot Chat, Auto model selection chooses from the supported models, subject to your policies and subscription type. Models may change over time. See [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models#supported-ai-models-in-auto-model-selection).

> \[!TIP] To see which model was used for each response, hover over the response in Copilot Chat.

You can change the model Copilot uses to generate responses to chat prompts. You may find that different models perform better, or provide more useful responses, depending on the type of questions you ask. Options include premium models with advanced capabilities.  See [Changing the AI model for GitHub Copilot Chat](/en/copilot/using-github-copilot/ai-models/changing-the-ai-model-for-copilot-chat).

### Multiplier discounts

If you are on a paid Copilot plan and use auto model selection, models qualify for a 10% multiplier discount. See [Requests in GitHub Copilot](/en/copilot/concepts/billing/copilot-requests#model-multipliers).

### Enabling access during public preview

During the public preview, if you're using a Copilot Business or Copilot Enterprise plan, the organization or enterprise that provides your plan must have the **Editor preview features** policy enabled. See [Managing policies and features for GitHub Copilot in your organization](/en/enterprise-cloud@latest/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-policies-for-copilot-in-your-organization#enabling-copilot-features-in-your-organization) or [Managing policies and features for GitHub Copilot in your enterprise](/en/enterprise-cloud@latest/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-policies-and-features-for-copilot-in-your-enterprise#copilot-in-githubcom).

## Auto model selection in Copilot cloud agent

When you select **Auto** in Copilot cloud agent, Auto model selection chooses from the supported list of models, subject to your policies and subscription type. See [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models#supported-ai-models-in-auto-model-selection).

You can change the model Copilot uses. You may find that different models perform better, or provide more useful responses, depending on the type of task you give Copilot. See [Changing the AI model for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/changing-the-ai-model).

## Auto model selection in OpenAI Codex

When you select **Auto** in the OpenAI Codex coding agent, Auto model selection currently chooses from the following list of models, subject to your policies and subscription type:

* GPT-5.2-Codex
* GPT-5.3-Codex
* GPT-5.4

For more information, see [OpenAI Codex](/en/copilot/concepts/agents/openai-codex).

## Auto model selection in Anthropic Claude

When you select **Auto** in the Anthropic Claude coding agent, Auto model selection currently chooses from the following list of models, subject to your policies and subscription type:

* Claude Opus 4.5
* Claude Opus 4.6
* Claude Sonnet 4.5
* Claude Sonnet 4.6

For more information, see [Anthropic Claude](/en/copilot/concepts/agents/anthropic-claude).