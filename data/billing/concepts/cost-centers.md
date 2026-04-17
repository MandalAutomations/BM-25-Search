# Cost centers

Attribute spending to specific parts of your business.

Cost centers allow you to attribute usage and spending to business units, improving accountability, forecasting, and cost allocation. You can also apply one or more budgets to them to control costs.

## Cost center creation

* **Enterprise owners and billing managers** can create and edit cost centers for **any resource**.
* **Organization owners** can create and edit cost centers that contain **resources in their organization**.

When you create a cost center, you define which resources it contains from users, repositories, and organizations. If your account is billed through Azure, you can also add an Azure subscription to bill usage to a different Azure subscription than the enterprise default.

To get started with cost centers, see [Controlling and tracking costs at scale](/en/billing/tutorials/control-costs-at-scale).

## Cost center allocation

To allocate metered spending to a cost center, you add repositories, organizations, or users to the cost center.

* For **usage-based** products, like GitHub Actions, cost centers are charged based on the **repositories or organizations** in the cost center, as this is where the usage takes place.
* For **license-based** products, like GitHub Copilot, cost centers are charged based on the **users** in the cost center.
* For products billed by **premium request** usage, like Copilot cloud agent, cost centers are charged based on the **users** in the cost center, or the **organization that granted the user's GitHub Copilot license** if the user isn't directly assigned to a cost center.

Cost centers only apply to metered usage, and do not work with volume or subscription billing.

For more details, see [Cost center allocation for different products](/en/billing/reference/cost-center-allocation).

## Cost center limitations

* The maximum number of active cost centers per enterprise is 250.
* The maximum number of resources per cost center is 25,000.
* A maximum of 50 resources can be added to or removed from a cost center at a time.
* Azure subscriptions can only be added to or removed from cost centers through the UI.
* Outside collaborators or unaffiliated users can only be added to cost centers via the cost center API. For more information, see [Controlling and tracking costs at scale](/en/billing/tutorials/control-costs-at-scale#add-resources-to-the-cost-center).