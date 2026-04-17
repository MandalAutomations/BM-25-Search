# About billing for GitHub Copilot in organizations and enterprises

Learn about pricing and billing cycles for Copilot.

## Available plans

GitHub offers the following plans for organization accounts:

* **Copilot Business** at $19 USD per user per month (Purchase additional premium requests at $0.04 USD per request)
* **Copilot Enterprise** at $39 USD per user per month (GitHub Enterprise Cloud only, purchase additional premium requests at $0.04 USD per request)

With GitHub Enterprise Cloud:

* An enterprise owner chooses the plan for each organization in the enterprise. For guidance on choosing a plan, see [Choosing your enterprise's plan for GitHub Copilot](/en/copilot/rolling-out-github-copilot-at-scale/choosing-your-enterprises-plan-for-github-copilot).

* Data-resident and FedRAMP-compliant Copilot requests include a 10% model multiplier increase. See [GitHub Copilot with data residency](/en/enterprise-cloud@latest/admin/data-residency/github-copilot-with-data-residency#pricing-for-data-resident-copilot).

## Premium requests

Paid Copilot plans include premium requests. Premium requests use advanced models and features and are subject to monthly allowances or potential overage costs. See [Requests in GitHub Copilot](/en/copilot/managing-copilot/managing-copilot-as-an-individual-subscriber/monitoring-usage-and-entitlements/avoiding-unexpected-copilot-costs).

## Seat assignment

A Copilot seat is a license to use GitHub Copilot for a user. Each month, your organization or enterprise is billed for the number of assigned seats.

Seat assignment is managed by organization owners. With GitHub Enterprise Cloud, an enterprise owner must have enabled GitHub Copilot for the organization before an organization owner can assign seats. See [Granting access to GitHub Copilot for members of your organization](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-access-to-github-copilot-in-your-organization/granting-access-to-copilot-for-members-of-your-organization).

If a user receives a seat from multiple organizations in the same enterprise, the enterprise will be billed only once, and one organization is selected and billed for the seat. To determine which organization is billed for a given user, request a detailed usage report and refer to the `organization` column for the user's Copilot license. See [Billing reports reference](/en/billing/reference/usage-reports).

## Billing cycles

Billed users are calculated at the end of each billing cycle, based on the number of GitHub Copilot seats that are assigned. Although you can add or remove seats at any time during the billing cycle, billing for removed seats continues until the end of the current billing cycle. See [Making changes to your GitHub Copilot license](/en/copilot/reference/copilot-billing/license-changes).

## Reference

For detailed reference information about billing options and the effects of changes during a billing cycle, see [GitHub Copilot billing](/en/copilot/reference/copilot-billing).