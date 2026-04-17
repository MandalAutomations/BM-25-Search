# GitHub Models billing

If you want to use GitHub Models beyond the free usage included in your account, you can choose to opt in to paid usage.

> \[!NOTE]
>
> * GitHub Models for organizations and repositories is in public preview and subject to change.
> * Billing for GitHub Models is separate from billing for GitHub Copilot. For more information about how models in GitHub Copilot are billed, see [GitHub Copilot licenses](/en/billing/managing-billing-for-your-products/about-billing-for-github-copilot).

## How use of GitHub Models is measured

Each GitHub account receives a certain amount of included **free but rate-limited** usage of GitHub Models, see [Rate limits](/en/github-models/use-github-models/prototyping-with-ai-models#rate-limits).

For usage beyond the free quota, the cost is calculated by multiplying the number of **token units** you use by the unified token unit price.

The number of model requests and tokens you have used is reset after each billing cycle.

### Token units

A token unit is calculated by multiplying the number of input and output tokens by their respective model multipliers. All model usage, regardless of the underlying provider or model, is measured in token units. While some providers display prices per 1,000 or per 1,000,000 tokens, GitHub Models standardizes billing to the token unit level. This means you are billed using a single SKU and a unified price per token unit, no matter which supported model you use. See [Costs and multipliers for using GitHub Models directly](/en/billing/reference/models-multipliers-and-costs).

### Example calculation

The following table displays how the total cost is calculated for a request using OpenAI GPT-4o:

| Model         | Input tokens used | Output tokens used | Input multiplier | Output multiplier | Total token units | Price per token unit | Total cost |
| ------------- | ----------------- | ------------------ | ---------------- | ----------------- | ----------------- | -------------------- | ---------- |
| OpenAI GPT-4o | 1,000,000         | 1,000,000          | 0.25             | 1                 | 1,250,000         | $0.00001             | $12.50     |

The following steps demonstrate how the total cost is calculated:

1. **Calculate input tokens:**
   Multiply the number of input tokens by the input multiplier.
   `1,000,000 tokens × 0.25 = 250,000 input token units`

2. **Calculate billable output tokens:**
   Multiply the number of output tokens by the output multiplier.
   `1,000,000 tokens × 1 = 1,000,000 output token units`

3. **Add billable tokens:**
   Add the billable input and output tokens.
   `250,000 (input) + 1,000,000 (output) = 1,250,000 total token units`

4. **Charges by type:**
   * **Input charge:** `250,000 × $0.00001 = $2.50`
   * **Output charge:** `1,000,000 × $0.00001 = $10.00`

5. **Calculate the total cost:**
   Multiply the total token units by the token unit price.
   `1,250,000 × $0.00001 = $12.50 for this request`

## Free use of GitHub Models

All GitHub accounts have rate-limited access to GitHub Models at no cost. These limits vary by model and are designed to support prototyping and experimentation. Limits also vary according to your GitHub Copilot plan.

Free usage includes:

* Access to all supported models in the catalog
* Rate-limited requests per model
* Usage from the GitHub Marketplace catalog

For full details of rate limits and quotas, see [Rate limits](/en/github-models/use-github-models/prototyping-with-ai-models#rate-limits).

> \[!TIP]
> If you use custom models from third-party providers with your own API keys, there is no impact on your bill in GitHub. See [Using your own API keys in GitHub Models](/en/github-models/github-models-at-scale/set-up-custom-model-integration-models-byok).

## Using more than your included quota

If your account does not have a valid payment method on file or paid use is not enabled for your account, usage is blocked once you use up your quota.

### Opting in or out of paid usage

GitHub Models billing is disabled by default for enterprises and organizations. An enterprise must enable paid usage before any organization within it can opt in to billing. Once an enterprise or organization has opted in to paid usage, the billing is enabled for all repositories owned by the enterprise or organization, including repositories owned by Enterprise Managed Users (EMUs).

For personal repositories, a user's own settings determine whether paid usage is enabled, unless the user is managed by an enterprise (EMU). In that case, the enterprise's settings apply.

* [Managing your team's model usage](/en/github-models/github-models-at-scale/manage-models-at-scale)
* [About GitHub Models](/en/github-models/about-github-models#enabling-github-models)

> \[!NOTE]
> If an enterprise has opted in to billing for GitHub Models, but an organization within the enterprise has opted out of billing, then paid GitHub Models usage is disabled for the organization, including for repositories owned by Enterprise Managed Users and the enterprise.

## Paying for GitHub Models use

You pay for additional use of GitHub Models with the payment method set up for your GitHub account. See [Managing your payment and billing information](/en/billing/how-tos/set-up-payment/manage-payment-info).

GitHub Models pricing is based on the number of token units used, at a fixed price of $0.00001 USD per token unit.

At the end of your billing cycle, GitHub calculates the cost of token units used, starting from your first request after opting in to paid usage. See [Viewing your usage of metered products and licenses](/en/billing/managing-billing-for-your-products/viewing-your-product-usage).

GitHub Models usage can be paid for by one or more of the following methods:

* For enterprises, organizations, or personal accounts directly billed by GitHub, the billing of GitHub Models is based on your metered usage for each billing period, and pricing varies by the number of model requests, tokens, and the model multiplier.
  * For invoiced accounts, contact [GitHub's Sales team](https://github.com/enterprise/contact) to discuss billing for GitHub Models usage.
* Accounts with an existing Azure subscription can use that subscription to pay for model inference by bringing their own API key for custom models. In this case, billing is based on the model provider’s pricing and is managed through the Azure subscription. See [Using your own API keys in GitHub Models](/en/github-models/github-models-at-scale/set-up-custom-model-integration-models-byok).

You are considered to be directly billed by GitHub if you pay for GitHub using a credit card, PayPal, or by invoice.

## Managing your budget for GitHub Models

> \[!NOTE] Once you opt in to paid usage, you will have access to production grade rate limits and be billed for all usage thereafter. For more information about these rate limits, see [Microsoft Foundry Models quotas and limits](https://learn.microsoft.com/en-us/azure/ai-foundry/model-inference/quotas-limits) in the Azure documentation.

Enterprises and organizations can opt in to paid usage to access expanded model capabilities, including increased request allowances and larger context windows. You can manage their spending by setting a budget.

Enterprises, organizations and personal accounts may have default budgets to limit spending. Check the budgets for your account to ensure they are appropriate for your usage needs.

For more information, see [Setting up budgets to control spending on metered products](/en/billing/managing-your-billing/using-budgets-control-spending).

## Further reading

* [About GitHub Models](/en/github-models/about-github-models)
* [Managing your team's model usage](/en/github-models/github-models-at-scale/manage-models-at-scale)