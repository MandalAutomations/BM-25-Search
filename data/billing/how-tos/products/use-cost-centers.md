# Using cost centers to allocate costs to business units

Learn how to create and use cost centers to manage costs across your company's divisions at scale.

> \[!NOTE] Before you create or update a cost center, if you're unsure of how spending will be allocated to the cost center, see [Cost center allocation for different products](/en/billing/reference/cost-center-allocation).

## Creating a cost center

> \[!NOTE]
> An enterprise can create up to 250 cost centers.

Create cost centers to monitor and manage expenses for specific organizations or repositories. Multiple organizations, repositories, and users can be assigned to one cost center.

When you create a cost center, you can add **organizations**, **repositories**, or **users**. The cost center will then track spending for the selected entities.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-credit-card" aria-label="credit-card" role="img"><path d="M10.75 9a.75.75 0 0 0 0 1.5h1.5a.75.75 0 0 0 0-1.5h-1.5Z"></path><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25ZM14.5 6.5h-13v5.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Zm0-2.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25V5h13Z"></path></svg> Billing and licensing**.

3. Click **Cost centers**.

4. Click **New cost center** in the upper-right corner.

5. In the text box under "Name", enter a name for your cost center.

6. If your account is billed to Azure, you have the option to add an Azure ID. Your credentials will be verified against Azure to ensure the Azure IDs associated to your account are available.

7. Under **Resources**, select the organizations, repositories, and/or users that will be a part of the cost center.

   > \[!NOTE] A resource (organization, repository, or user) can only be assigned to one cost center at a time. If you add a resource that belongs to a different cost center, it will be moved to the new cost center and you will be notified.

8. Click **Create cost center**.

## Adding a budget to a cost center

After you create a cost center, you can add a monthly budget and receive alerts from the cost center to monitor your spending and usage. See [Setting up budgets to control spending on metered products](/en/billing/managing-your-billing/using-budgets-control-spending).

## Viewing cost center usage

You can view the usage of your cost centers and download the usage data for further analysis. See [Gathering insights on your spending](/en/billing/using-the-enhanced-billing-platform-for-enterprises/gathering-insights-on-your-spending).

## Viewing, editing, and deleting cost centers

You can view, edit, and delete cost centers to manage your business units effectively.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-credit-card" aria-label="credit-card" role="img"><path d="M10.75 9a.75.75 0 0 0 0 1.5h1.5a.75.75 0 0 0 0-1.5h-1.5Z"></path><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25ZM14.5 6.5h-13v5.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Zm0-2.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25V5h13Z"></path></svg> Billing and licensing**.
3. Click **Cost centers**.
4. Select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Cost center dropdown" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> to the right of a cost center, then click **View details**, **Edit**, or **Delete**.
5. Follow the prompts.

## Further reading

* [Controlling and tracking costs at scale](/en/billing/tutorials/control-costs-at-scale)
* [REST API endpoints for billing](/en/rest/enterprise-admin/billing)