# GitHub Copilot premium requests

Learn how premium requests in Copilot work, including usage measurement and managing your budget.

Usage of Copilot is measured through a combination of licenses and monthly usage tracking. For more information about how license costs in Copilot work, see [GitHub Copilot licenses](/en/billing/concepts/product-billing/github-copilot-licenses).

> \[!IMPORTANT]
> Premium requests for Spark and Copilot cloud agent are tracked in dedicated SKUs from November 1, 2025. This provides better cost visibility and budget control for each AI product.

## What are premium requests?

Some Copilot features use premium requests.
Premium requests give you access to advanced models and additional AI features.

Examples include:

* Using Copilot Chat with premium models
* Large context windows or advanced reasoning models
* Features like Copilot cloud agent
* Spark app creation

Each product's premium request usage is attributed to a premium request SKU:

* **Copilot premium requests** - Chat, CLI, Code Review, Extensions, and Spaces
* **Spark premium requests** - Spark app creation
* **Copilot cloud agent premium requests** - Copilot cloud agent sessions

See [Requests in GitHub Copilot](/en/copilot/concepts/billing/copilot-requests) for details on which models and features consume premium requests and their SKU attribution.

## How usage of premium requests is measured

Usage of premium requests is tracked monthly and is based on the following factors.

### Monthly allowance

* Each plan includes a fixed number of premium requests per user per month.
* Allowances vary by plan. See [Plans for GitHub Copilot](/en/copilot/about-github-copilot/subscription-plans-for-github-copilot).
* Allowances reset on the 1st of each month at 00:00:00 UTC.

### Multiple licenses

If you receive licenses from multiple enterprises, you must choose which entity is billed for your premium requests. See [Monitoring your GitHub Copilot usage and entitlements](/en/copilot/managing-copilot/understanding-and-managing-copilot-usage/monitoring-your-copilot-usage-and-entitlements#managing-premium-request-billing-with-multiple-copilot-licenses).

### Usage by premium models

* Each interaction that uses a premium model consumes from your allowance.
* Some models use **multipliers**, meaning a single interaction may count as multiple premium requests.
* For example, advanced reasoning models may consume 5× or 20× the standard rate.
* If you exceed your allowance and overages are enabled, extra usage is billed at the standard rate.

### Usage by Copilot cloud agent

When you use Copilot cloud agent, including any Copilot custom agents, both **GitHub Actions minutes** and **premium requests** are consumed:

* **GitHub Actions minutes** come from your account’s monthly allowance of free minutes for GitHub-hosted runners. This allowance is shared with all GitHub Actions workflows. See [GitHub Actions billing](/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions#included-storage-and-minutes).
* **Premium requests** come from the monthly allowance associated with your Copilot license. This allowance is shared with other features, such as Copilot Chat.

Each cloud agent **session** consumes one premium request. A session begins when you:

* Prompt Copilot to undertake a task.
* Assign Copilot to an issue

If you run out of free minutes or premium requests, and you have *not* set up billing, a message is displayed explaining why Copilot cannot work on the task.

Copilot cloud agent uses a dedicated Copilot cloud agent premium request SKU. This SKU still pulls from your monthly allowance of premium requests, but allows for more granular budget control and monitoring.

For more information about Copilot cloud agent and Copilot custom agents, see [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent) and [About custom agents](/en/copilot/concepts/agents/cloud-agent/about-custom-agents).

## Using more than your included premium requests

If you exceed your plan's included premium requests, there are options available depending on your account type.

### Personal accounts

If you exceed your allowance, set a budget for additional premium requests or upgrade to a higher plan. See [Setting up budgets to control spending on metered products](/en/billing/managing-your-billing/using-budgets-control-spending).

### Organizations and enterprises

* Admins can control whether members are allowed to exceed their premium request allowance across AI features using the **Premium request paid usage** policy.
* Separate policy options are available for Copilot, Spark, and Copilot cloud agent. See [Managing the premium request allowance for your organization or enterprise](/en/copilot/how-tos/manage-and-track-spending/manage-request-allowances).
* Premium request budgets can be set to either monitor or block overages, with options for bundled or individual SKU management.
* Enterprises can also upgrade frequent users to Copilot Enterprise for higher included allowances.

## Paying for premium requests

Additional usage is charged to the payment method configured for your GitHub account.

If you are billed through Azure, premium request usage appears on your Azure invoice. See [Connecting an Azure subscription](/en/billing/managing-the-plan-for-your-github-account/connecting-an-azure-subscription).

## Managing your budget for premium requests

To help manage your budget for premium requests, consider the following strategies.

### Budget options for personal accounts

You can set a budget in your personal billing settings to receive alerts when you reach 75%, 90%, or 100% of your budget. Setting a premium request budget depends on the level of granularity you need:

* **Bundled premium request budget** - Combines all premium requests into a single budget (Recommended for most users)
* **Individual SKU budgets** - Set separate budgets for each AI product (Copilot, Spark, Copilot cloud agent)

### Budget options for organizations and enterprises

You can set budgets at the organization, enterprise, or cost center level. If you enable **stop usage when budget is reached**, extra premium requests are blocked when the budget runs out.

For detailed setup instructions, see [Setting up budgets to control spending on metered products](/en/billing/tutorials/set-up-budgets).

## Monitoring usage

* Track your monthly usage in your IDE, in Copilot settings on GitHub, or by downloading a usage report.
* Usage reports show all premium requests, both within and beyond the allowance, and can be used to identify high-usage users.
* Premium request analytics display usage by dedicated SKUs, providing detailed insights into which AI products consume your allowance.

For more information about monitoring your usage, see [Monitoring your GitHub Copilot usage and entitlements](/en/copilot/how-tos/manage-and-track-spending/monitor-premium-requests).