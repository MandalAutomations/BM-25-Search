# GitHub Spark billing

Learn how GitHub Spark is billed for users.

GitHub Spark allows users to build applications using natural-language prompts, then share the apps with teammates or deploy them to production.

> \[!NOTE]
> GitHub Spark is in public preview with [data protection](https://gh.io/dpa) and subject to change.

## Billing for Spark app creation

Each prompt consumes 4 premium requests, which draw from your plan's premium request allowance. If you have enabled premium requests over your plan's allowance, additional premium requests beyond your plan's included amount are billed at $0.04 USD per request, meaning that one prompt to Spark would cost **$0.16**. See [Requests in GitHub Copilot](/en/copilot/concepts/copilot-billing/understanding-and-managing-requests-in-copilot).

> \[!NOTE]
> Beginning November 1, 2025, Spark premium requests are attributed to a dedicated **Spark Premium Requests** SKU instead of the shared Copilot premium request SKU. This provides better cost visibility and allows you to set separate budgets specifically for Spark usage.

## Managing Spark costs

You now have more granular options for managing Spark costs:

### Budget options

* **Bundled budget**: Combine Spark premium requests with other AI product costs in a single premium request budget for simplified management.
* **Individual product budget**: Set a dedicated budget specifically for Spark for granular cost control.

For detailed information about setting up budgets, see [Setting up budgets to control spending on metered products](/en/billing/tutorials/set-up-budgets).

### Analytics and monitoring

With the dedicated SKU, you can:

* Track Spark usage separately from other Copilot features in billing analytics
* Set up alerts when Spark usage approaches budget limits
* Generate reports specifically for Spark premium request consumption

For monitoring guidance, see [Monitoring your GitHub Copilot usage and entitlements](/en/copilot/how-tos/manage-and-track-spending/monitor-premium-requests).

## Billing and limits for Spark app deployment

You can publish apps created with Spark to a deployment environment.

Deployed apps do not currently incur any charges. However, GitHub currently **limits usage** of deployed sparks based on criteria including number of HTTP requests, data transfer, and storage.

* Limits apply to the billable owner, meaning if you own 10 deployed sparks, all 10 will count towards the limits.
* When any limit is reached, the spark is unpublished for the rest of the billing period.

In the future, a new billing system will allow sparks to continue being deployed once a limit is reached, with additional usage charged to the spark's billable owner. GitHub will publish the limits once they are confirmed following a testing period. This article will be updated when more details are available.

## Further reading

* [Responsible use of GitHub Spark](/en/copilot/responsible-use-of-github-copilot-features/responsible-use-of-github-spark)
* [Building and deploying AI-powered apps with GitHub Spark](/en/copilot/tutorials/building-ai-app-prototypes)