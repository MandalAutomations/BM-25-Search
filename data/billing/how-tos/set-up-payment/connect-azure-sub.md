# Connecting an Azure subscription

You can enable and pay for usage-based billing on GitHub by connecting an Azure subscription.

You can pay for metered usage of GitHub features through Azure by connecting an Azure Subscription ID to your organization or enterprise account on GitHub. See [Azure subscription payments](/en/billing/concepts/azure-subscriptions).

> \[!NOTE] If you currently pay for your GitHub Enterprise licenses through a volume, subscription, or prepaid agreement, you will continue to be billed in this way until your agreement expires or you are invited to transition. At renewal, you have the option to switch to the metered billing model.

## Prerequisites

* You must be an owner of the GitHub organization or enterprise account you want to connect to Azure.

* You must know your Azure subscription ID. See [Get subscription and tenant IDs in the Azure portal](https://learn.microsoft.com/en-us/azure/azure-portal/get-subscription-tenant-id) in the Microsoft Docs.

* You must be logged into Azure as a user who is able to provide tenant-wide admin consent or arrange to work with an Azure AD global administrator to configure an admin consent workflow. See [Azure subscription payments](/en/billing/concepts/azure-subscriptions).

## Connecting your Azure subscription to an organization or enterprise account

1. Navigate to your organization or enterprise. For example, from the [Organizations](https://github.com/settings/organizations?ref_product=github\&ref_type=engagement\&ref_style=text) or [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) pages on GitHub.com.

2. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-credit-card" aria-label="credit-card" role="img"><path d="M10.75 9a.75.75 0 0 0 0 1.5h1.5a.75.75 0 0 0 0-1.5h-1.5Z"></path><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25ZM14.5 6.5h-13v5.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Zm0-2.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25V5h13Z"></path></svg> Billing & Licensing** to display the billing and licensing overview for the account:
   * **Organization** accounts: under "Access" in the sidebar for settings.
   * **Enterprise** accounts: a separate tab at the top of the page.

3. From the list of "Billing & licensing" pages, click **Payment information**.

4. Scroll to the bottom of the page, to the right of "Metered billing via Azure", click **Add Azure Subscription**.

5. Sign in to your Microsoft account.

6. Review the "Permissions requested" prompt. If you agree with the terms, click **Accept**.

   If you don't see a "Permissions requested" prompt, and instead see a message indicating that you need admin approval, see [Troubleshooting Azure subscription connection problems](/en/billing/how-tos/troubleshooting/azure-sub-connection).

7. Under "Select a subscription", select the Azure Subscription ID that you want to connect to your account.

   1. Select **By clicking "Connect", you are confirming that you want to be billed for metered services via the selected Azure subscription**.
   2. Click **Connect**.

   To select an Azure subscription, you must have owner permissions to the subscription. If the default tenant does not have the right permissions, you may need to specify a different tenant ID. For more information, see [Azure subscription payments](/en/billing/concepts/azure-subscriptions) and [Microsoft identity platform and OAuth 2.0 authorization code flow](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow#request-an-authorization-code) in Microsoft Docs.

## Editing or disconnecting your Azure subscription from an account

If you disconnect your Azure subscription from your account, your usage can no longer exceed the amounts included with your plan.

1. On the "Payment information" page, to the right of the subscription ID you want change.

   * **Edit the subscription**: Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit Azure Subscription" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> to edit your subscription.
   * **Disconnect the subscription** Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-trash" aria-label="Delete Azure Subscription" role="img"><path d="M11 1.75V3h2.25a.75.75 0 0 1 0 1.5H2.75a.75.75 0 0 1 0-1.5H5V1.75C5 .784 5.784 0 6.75 0h2.5C10.216 0 11 .784 11 1.75ZM4.496 6.675l.66 6.6a.25.25 0 0 0 .249.225h5.19a.25.25 0 0 0 .249-.225l.66-6.6a.75.75 0 0 1 1.492.149l-.66 6.6A1.748 1.748 0 0 1 10.595 15h-5.19a1.75 1.75 0 0 1-1.741-1.575l-.66-6.6a.75.75 0 1 1 1.492-.15ZM6.5 1.75V3h3V1.75a.25.25 0 0 0-.25-.25h-2.5a.25.25 0 0 0-.25.25Z"></path></svg> to remove the connection.

## Video demonstration of connecting a subscription

To connect an Azure subscription, you'll need appropriate access permissions on both GitHub and the Azure billing portal. This may require coordination between two different people.

To see a demo of the process from beginning to end, see [Billing GitHub consumption through an Azure subscription](https://www.youtube.com/watch?v=Y-f7JKJ4_8Y) on GitHub's YouTube channel. This video demonstrates the process for an enterprise account.

## Further reading

* [Azure subscription payments](/en/billing/concepts/azure-subscriptions)
* [Azure subscription reference](/en/billing/reference/azure-subscription)
* [Troubleshooting Azure subscription connection problems](/en/billing/how-tos/troubleshooting/azure-sub-connection)