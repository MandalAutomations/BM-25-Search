# Creating an enterprise account as a Microsoft CSP partner

Learn how to set up an enterprise account for your customer as a Microsoft Cloud Solution Provider partner.

## Prerequisites

Before you start, make sure you know:

* GitHub username of the client who will become the owner of the enterprise you create
* GitHub username for the CSP partner that must be assigned to the customer’s enterprise account to manage metered billing and access support
* Enterprise name your client would like to use
* Email address for receipts
* Number of seats your client needs in the enterprise
* Enterprise account type required by your client, see [Choosing an enterprise type for GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/choosing-an-enterprise-type-for-github-enterprise-cloud)

## Step 1: Create the enterprise account in the Azure portal

As a Microsoft CSP partner, you can get started with GitHub Enterprise from the Microsoft Azure portal.

1. Sign in to the Microsoft Azure portal.
2. In the search bar, type "GitHub" and select **GitHub** to go the landing page.
3. Select **Get started with GitHub Enterprise**.
4. Choose an enterprise type. To help you decide which choice is best for the enterprise, see [Choosing an enterprise type for GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/identity-and-access-management/understanding-iam-for-enterprises/choosing-an-enterprise-type-for-github-enterprise-cloud).
5. Complete the form with your client's information.
6. Click **Create your enterprise**.

## Step 2: Purchase GitHub Enterprise

At any time during the trial, you can purchase GitHub Enterprise for your client by linking it to their Azure subscription. If the account is later transferred to the customer, ensure the Azure subscription is fully managed by them.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, in the blue banner, click **Activate Enterprise**.

3. Click **Add Azure subscription**.

4. To sign in to your Microsoft account, follow the prompts.

5. Review the "Permissions requested" prompt. If you agree with the terms, click **Accept**.

   If you don't see a "Permissions requested" prompt, and instead see a message indicating that you need admin approval, see [Troubleshooting Azure subscription connection problems](/en/billing/how-tos/troubleshooting/azure-sub-connection).

6. Under "Select a subscription", select the Azure Subscription ID that you want to connect to your organization. To select an Azure subscription, you must have owner permissions to the subscription. If the default tenant does not have the right permissions, you may need to specify a different tenant ID. For more information, see [Azure subscription payments](/en/billing/concepts/azure-subscriptions) and [Microsoft identity platform and OAuth 2.0 authorization code flow](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow#request-an-authorization-code) in Microsoft Docs.
   1. Select **By clicking "Connect", you are confirming that you want to be billed for metered services via the selected Azure subscription**.
   2. Click **Connect**.

7. Click **Activate Enterprise**.

## Step 3: Invite your client as an enterprise owner

Invite your client to become an enterprise owner. See [Inviting people to manage your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/inviting-people-to-manage-your-enterprise#inviting-an-enterprise-administrator-to-your-enterprise-account).

## Step 4: Change your role to billing manager

Optionally, you can change your role to billing manager to manage the billing for the enterprise account, without having full administrative access.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Under "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People", click **Administrators**.
4. Confirm that your client is listed as an enterprise owner.
5. To the right of your username, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Administrator settings" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> dropdown menu, then click **Change role**.

   ![Screenshot of a user in the administrators list. A dropdown menu, labeled with a kebab icon, is highlighted with an orange outline.](/assets/images/help/business-accounts/administrator-settings.png)
6. Select **Billing manager**, then click **Change role**.

## Contacting support

As a Microsoft CSP partner, you can use the [GitHub Support for Microsoft CSP](https://support.github.com/contact?tags=partner-microsoft-csp) landing page to speak to GitHub Support. For more information about creating a support ticket, see [Creating a support ticket](/en/support/contacting-github-support/creating-a-support-ticket).