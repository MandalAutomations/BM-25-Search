# Configuring access to AI models in GitHub Copilot

Control which AI models your organization or enterprise can use with Copilot.

Your access to GitHub Copilot models depends on:

* Your Copilot plan.
* The client you use (for example, GitHub.com, Visual Studio Code, or JetBrains IDEs).
* Whether your organization or enterprise restricts access to specific models.

For a list of available AI models, see [Supported AI models in GitHub Copilot](/en/copilot/using-github-copilot/ai-models/supported-ai-models-in-copilot). For information on how Copilot Chat serves different AI models, see [Hosting of models for GitHub Copilot](/en/copilot/reference/ai-models/model-hosting).

## Setup for individual use

If you have a Copilot Free, Copilot Pro, or Copilot Pro+ plan, you can use AI models directly within Copilot without configuring access or managing policies.

> \[!NOTE]
> Some models may not be available depending on your plan. See [Plans for GitHub Copilot](/en/copilot/about-github-copilot/plans-for-github-copilot#models).

## Setup for organization and enterprise use

As an enterprise or organization owner, you can enable or disable access to AI models for members with a Copilot Enterprise or Copilot Business seat. See [Managing policies and features for GitHub Copilot in your organization](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/setting-policies-for-copilot-in-your-organization/managing-policies-for-copilot-in-your-organization) and [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-policies-and-features-for-copilot-in-your-enterprise).

> \[!NOTE] Models available in Copilot auto model selection will follow the policies set for an organization or enterprise. See [About Copilot auto model selection](/en/copilot/concepts/auto-model-selection).

You can also integrate your preferred custom models from supported LLM providers by bringing your own API keys. Organization owners can make custom models available for members of their organization and enterprise owners can add custom models and choose which organizations can make use of them. See [Using your LLM provider API keys with Copilot](/en/copilot/how-tos/administer-copilot/manage-for-organization/use-your-own-api-keys) for organizations and [Using your LLM provider API keys with Copilot](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/use-your-own-api-keys) for enterprise accounts.