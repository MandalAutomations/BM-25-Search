# Managing the premium request allowance for your organization or enterprise

Configure policies and budgets for premium requests, or upgrade users to Copilot Enterprise.

Each Copilot plan includes a per-user allowance for premium requests. If enabled, requests over the allowance are billed to your organization or enterprise. To learn more about premium requests, see [Requests in GitHub Copilot](/en/copilot/concepts/copilot-billing/requests-in-github-copilot). For allowances per plan, see [Plans for GitHub Copilot](/en/copilot/get-started/plans-for-github-copilot#comparing-copilot-plans).

Premium request usage beyond the allowance is governed by two complementary control layers:

* **Policy setting:** The **Premium request paid usage** policy determines whether users can surpass their included premium request allowance for each AI tool. This policy is enabled by default.
* **Budget constraints:** If your enterprise or organization has a premium request SKU-level budget or a bundled premium requests budget, premium request usage will be blocked once the budget is fully consumed for the billing period.

The **Premium request paid usage policy** must be enabled for any additional billing to occur. Budgets then control whether and when usage is stopped.

You can increase the allowance for users by ensuring the policy is enabled, editing your budgets, or upgrading users to Copilot Enterprise.

## Prerequisites

* Before making changes, download a usage report to see which developers are frequently hitting the limit or using a significant number of requests over the allowance. You may want to contact these users to understand their use cases and requirements. See [Viewing your usage of metered products and licenses](/en/billing/how-tos/products/view-productlicense-use).
* If a user receives licenses from multiple enterprises or standalone organizations, the user must select a billing entity to use premium requests. See [Managing premium request billing with multiple Copilot licenses](/en/copilot/managing-copilot/monitoring-usage-and-entitlements/monitoring-your-copilot-usage-and-entitlements#managing-premium-request-billing-with-multiple-copilot-licenses).
* For enterprises only, review which organizations are able to assign and are actively assigning Copilot access to users. See [Granting users access to GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-access/grant-access#enabling-copilot-for-organizations).

## Setting a policy for paid usage

By default, premium requests over the allowance are enabled for organizations and enterprises. This allows for uninterrupted use of premium requests, unless you have a budget that caps spending on the Premium Request SKU.

You can set the policy for an enterprise or a standalone organization.

1. Navigate to the policy settings for your enterprise or organization. See [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies) or [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies).
2. Next to "Premium request paid usage", select the policy for your organization or enterprise.
   * To configure policies for specific AI products, click **Enabled for specific products** and set the desired options.

## Updating budgets

> \[!NOTE]
> Enterprise billing managers can also edit and delete budgets.

1. Ensure the "Premium request paid usage" policy is enabled. See [Setting a policy for paid usage](#setting-a-policy-for-paid-usage).
2. Check the budgets for your enterprise or organizations, and edit or delete any budgets that "stop usage when budget limit is reached" for the Premium Request SKU. See [Setting up budgets to control spending on metered products](/en/billing/managing-your-billing/using-budgets-control-spending#editing-or-deleting-a-budget).
3. Premium request budget types:
   * **Bundled premium requests budget**: Manages all premium request SKUs together (recommended for most users)
   * **Individual SKU budgets**: Set separate budgets for each AI tool (Copilot, Spark, Copilot cloud agent)

Creating new budgets without deleting an existing budget does not override the existing budget. If **any** applicable budget with "Stop usage when budget limit is reached" enabled is exhausted, additional premium requests are blocked.

Enterprise-level budgets act as a failsafe for the entire enterprise, including any spending originating from within cost centers. If the enterprise budget is exhausted before the cost center budget, usage will be blocked. See [Budgets and alerts](/en/billing/concepts/budgets-and-alerts) for details on different scopes of budgets and stopping usage.

## Upgrading users to Copilot Enterprise

An enterprise owner can upgrade certain users to increase their base allowance of premium requests.

> \[!TIP] Copilot Business users who make more than 800 premium requests per month would save money with a Copilot Enterprise license.

1. Create a new organization in your enterprise. See [Adding organizations to your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/adding-organizations-to-your-enterprise#creating-a-new-organization).

2. Add the users who need more premium requests to the new organization.

3. Grant Copilot Enterprise licenses to all users in the organization.

   1. If needed, upgrade the enterprise to Copilot Enterprise. See [Upgrading GitHub Copilot for your enterprise](/en/enterprise-cloud@latest/copilot/how-tos/administer/enterprises/managing-the-copilot-plan-for-your-enterprise/upgrading-copilot-for-your-enterprise).

   2. Enable Copilot Enterprise for the new organization. See [Granting users access to GitHub Copilot in your enterprise](/en/enterprise-cloud@latest/copilot/how-tos/administer/enterprises/managing-access-to-copilot-in-your-enterprise/enabling-copilot-for-organizations-in-your-enterprise).

   3. Grant licenses to all users in the organization. See [Granting access to GitHub Copilot for members of your organization](/en/copilot/how-tos/administer/organizations/managing-access-to-github-copilot-in-your-organization/granting-access-to-copilot-for-members-of-your-organization#granting-access-to-github-copilot-for-all-current-and-future-users-in-your-organization).

4. Check the usage report regularly to ensure that Copilot Enterprise remains the most cost-effective option for these users.

## Organization-based premium request management

With this budget management method, budgets are scoped to cost centers with organizations as the managed resource.

Users must be assigned a Copilot license through only a single organization in the enterprise. If users are currently assigned licenses through multiple organizations within your enterprise, you must either update your assignment practices or use user-based management. For a comparison of methods, see [Management methods for premium request usage in an enterprise](/en/copilot/concepts/billing/premium-request-management).

### Setting up organization-based cost centers

1. Create a cost center and assign all organizations that contain users where no additional premium requests are required. These organizations should be the organizations that assign each user their Copilot license. Assign a $0 budget to this cost center.
2. Create a second cost center and assign organizations with users who need access to additional premium requests. These organizations should be the organizations that assign each user their Copilot license. Assign a budget to this cost center.
3. If you need more than one tier of budgets for additional premium requests, create further cost centers.

You should define a SKU-level budget for "`FEATURE` Premium Request", not a product-level budget for "Copilot". Alternatively, use "Bundled premium requests budget" to define a budget for all types of premium requests.

> \[!NOTE]
> Creating a budget scoped directly to the organization is an option, but it is not recommended due to how organization-scoped budgets interact with cost center-scoped budgets for cost centers that contain users as resources.

## User-based premium request management

With this budget management method, budgets are scoped to cost centers with users as the managed resource. When a user is added directly as a managed resource to a cost center, this takes precedence over the user being a member of any organizations that are managed resources in any cost centers.

User-based management applies to all metered, licensed products. See [Cost center allocation for different products](/en/billing/reference/cost-center-allocation#details-for-license-based-products).

> \[!NOTE]
> If your business needs to allocate license costs for GitHub Copilot and GitHub Enterprise separately from costs for GitHub Secret Protection, GitHub Code Security, or GitHub Advanced Security, you must use organization-based management.

### Setting up user-based cost centers

1. Create a cost center to contain each subset of users that needs a distinct limit on premium requests.
2. Assign the appropriate budget for premium requests to each cost center.

You should define a SKU-level budget for "`FEATURE` Premium Request", not a product-level budget for "Copilot". Alternatively, use "Bundled premium requests budget" to define a budget for all types of premium requests.