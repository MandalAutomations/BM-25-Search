# Billing for GitHub Enterprise

Learn how your bill is calculated based on how many GitHub Enterprise licenses you use.

## GitHub Enterprise plan costs

Each member of your enterprise uses a license (previously known as a seat). The bill for your GitHub Enterprise plan is based on the number of licenses consumed by your enterprise.

If you have an enterprise account on GitHub Enterprise Cloud, the enterprise account is the central point for all billing within your enterprise, including the organizations that your enterprise owns. Enterprise owners and billing managers can access and manage billing for the enterprise. For more information, see [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise).

> \[!TIP]
>
> If you use GitHub Enterprise Cloud with an individual organization and do not yet have an enterprise account, you can create an enterprise account and add your organization. For more information, see [Creating an enterprise account](/en/enterprise-cloud@latest/admin/managing-your-enterprise-account/creating-an-enterprise-account).

To learn which people consume a license in your enterprise, see [People who consume a license in an organization](/en/billing/reference/license-consumption).

## Invoiced customers

For invoiced customers, each invoice includes a single bill that covers the cost of GitHub Enterprise licenses used, as well as your use of paid services. For example, in addition to your usage for GitHub Enterprise, you may also use GitHub Secret Protection.

## Billing models for GitHub Enterprise licenses

There are two billing models for GitHub Enterprise licenses: **usage-based** and **volume**.

You are already enrolled in usage-based billing if you created a trial of GitHub Enterprise Cloud on or after August 1, 2024.

If you currently pay for your GitHub Enterprise licenses by invoice with a volume, subscription, or prepaid agreement, you will continue to be billed in this way until your agreement expires. At renewal, you have the option to switch to the metered billing model.

## License usage across deployments

GitHub uses a unique-user licensing model. With the GitHub Enterprise plan, you're entitled to use both GitHub Enterprise Cloud and GitHub Enterprise Server. Your GitHub Enterprise Cloud allowance includes **one** deployment, on either GitHub.com or GHE.com.

GitHub determines how many licensed seats you're consuming based on the number of unique users across your deployments. Each user only consumes one license, no matter how many GitHub Enterprise Server instances the user uses, or how many organizations the user is a member of on your GitHub Enterprise Cloud deployment. This model allows each person to use multiple GitHub Enterprise deployments without incurring extra costs.

To ensure the same user isn't consuming more than one license for multiple enterprise deployments, you synchronize license usage between your GitHub Enterprise Server and GitHub Enterprise Cloud environments. See [Combined GitHub Enterprise cloud and server use](/en/billing/managing-your-license-for-github-enterprise/about-licenses-for-github-enterprise).

## Further reading

* [Enterprise accounts](/en/enterprise-cloud@latest/admin/overview/about-enterprise-accounts)
* [People who consume a license in an organization](/en/billing/managing-the-plan-for-your-github-account/about-per-user-pricing)
* [Viewing usage for your GitHub Enterprise plan](/en/billing/how-tos/manage-plan-and-licenses/view-enterprise-usage)
* [Managing invoices for your enterprise](/en/enterprise-cloud@latest/billing/how-tos/set-up-payment/manage-enterprise-invoice)