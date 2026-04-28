# Preparing your organization for usage-based billing

Review your estimated costs under usage-based billing and take steps to prepare your organization before the transition.

<!-- expires 2026-06-01 -->

On June 1, 2026, Copilot is moving to usage-based billing with GitHub AI Credits. **Starting in early May**, use the tools below to understand how this change affects your organization and prepare before the transition takes effect.

<!-- end expires 2026-06-01 -->

## Preview your bill (coming in early May)

From the announcement banner on your enterprise home page, billing overview page, or premium request analytics page, click **Preview my bill** to see how your current usage translates to GitHub AI Credits.

The modal shows a side-by-side comparison of your actual spend under the current billing model and your estimated spend under usage-based billing, based on your April 2026 billing period. A difference indicator shows whether your estimated spend is higher, lower, or roughly equal.

Amounts shown are gross totals before discounts, promotional included usage, and contractual adjustments.

## Download the usage report

From the billing preview modal, click **Download CSV** to request a detailed usage report. You can also request the report from the premium request analytics page or via the API. The report is generated asynchronously and delivered via email to the requesting admin.

The report includes one row per user, per model, per day. Alongside the existing columns for your current billing data, two additional columns show the estimated equivalent under usage-based billing:

* `aic_quantity`: The number of AI credits consumed
* `aic_gross_amount`: The estimated cost in USD under usage-based billing

## Explore the billing preview tool

For a more detailed breakdown, you can upload your CSV to the billing preview tool (coming early May). The tool gives you an interactive view of your estimated costs broken down by model, user, and SKU.

Your data stays in your browser; nothing is uploaded to a server.

## Take action before the transition

Based on what you've learned from the billing preview and usage report, you can take steps to prepare:

* **Review and adjust your budgets**. Existing enterprise-level budgets for premium requests will automatically carry over to AI credits. Review them in your enterprise billing settings to make sure they still reflect the limits you want.
* **Plan for pooled AI credits**. Under usage-based billing, each license comes with a monthly amount of included AI credits, which are pooled across your organization. Consider how this changes your cost structure. Teams with uneven usage patterns may benefit.
* **Communicate the change internally**. Let your teams know that billing is changing and what it means for their day-to-day use of Copilot.