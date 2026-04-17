# Setting up Visual Studio subscriptions with GitHub Enterprise

Your team's subscription to Visual Studio can also provide access to GitHub Enterprise.

> \[!NOTE] Customers with a Visual Studio bundle can **switch to usage-based billing** for GitHub Enterprise licenses. This allows you to pay for licenses on a flexible monthly cycle for users who are not part of your Visual Studio subscription. See [Usage-based billing for enterprise licenses](/en/enterprise-cloud@latest/billing/concepts/enterprise-billing/usage-based-licenses).

Visual Studio subscriptions with GitHub Enterprise is a combined offering from Microsoft that allows a subscriber to use both Visual Studio and GitHub Enterprise. See [About Visual Studio subscriptions with GitHub Enterprise](/en/enterprise-cloud@latest/billing/managing-billing-for-your-products/managing-licenses-for-visual-studio-subscriptions-with-github-enterprise/about-visual-studio-subscriptions-with-github-enterprise).

## Prerequisites

* Your team's Visual Studio subscription must include GitHub Enterprise. For more information, see:
  * [Visual Studio Subscriptions and Benefits](https://visualstudio.microsoft.com/subscriptions/) on the Visual Studio website
  * [Overview of admin responsibilities](https://docs.microsoft.com/en-us/visualstudio/subscriptions/admin-responsibilities) in Microsoft Docs.

* Your team must have an enterprise on GitHub, see [Enterprise accounts](/en/enterprise-cloud@latest/admin/overview/about-enterprise-accounts).
  * If you're not sure whether your team has an enterprise, contact your GitHub administrator.
  * If you're not sure who on your team is responsible for GitHub services, contact [GitHub's Sales team](https://github.com/enterprise/contact).

## Setting up Visual Studio subscriptions with GitHub Enterprise

To set up Visual Studio subscriptions with GitHub Enterprise, members of your team must complete the following tasks.

One person may be able to complete the tasks because the person has all of the roles, but you may need to coordinate the tasks with multiple people. For more information, see [Roles for Visual Studio subscriptions with GitHub Enterprise reference](/en/enterprise-cloud@latest/billing/reference/roles-for-visual-studio).

1. A GitHub enterprise owner must create at least one organization in your enterprise. For more information, see [Adding organizations to your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-organizations-in-your-enterprise/adding-organizations-to-your-enterprise).

2. The Visual Studio subscription admin must assign a license for Visual Studio to a subscriber in the [administrator portal for Visual Studio subscriptions](https://visualstudio.microsoft.com/subscriptions-administration/). For more information, see [Overview of the Visual Studio Subscriptions Administrator Portal](https://docs.microsoft.com/en-us/visualstudio/subscriptions/using-admin-portal) and [Assign Visual Studio Licenses in the Visual Studio Subscriptions Administration Portal](https://docs.microsoft.com/en-us/visualstudio/subscriptions/assign-license) in Microsoft Docs.

3. Optionally, if the Visual Studio subscription admin assigned licenses to subscribers in Visual Studio before adding GitHub Enterprise to the subscription, the subscription admin can move the subscribers to the combined offering in the Visual Studio administration portal. For more information, see [Manage Visual Studio subscriptions with GitHub Enterprise](https://docs.microsoft.com/en-us/visualstudio/subscriptions/assign-github#moving-to-visual-studio-with-github-enterprise) in Microsoft Docs.

4. If the Visual Studio subscription admin has not disabled email notifications, the subscriber will receive two confirmation emails. For more information, see [Visual Studio subscriptions with GitHub Enterprise](https://docs.microsoft.com/en-us/visualstudio/subscriptions/access-github#what-is-the-visual-studio-subscription-with-github-enterprise-setup-process) in Microsoft Docs.

5. A GitHub organization owner must invite the subscriber to the organization created in step 1. The subscriber can accept the invitation with an existing personal account or create a new account. After the subscriber joins the organization, the subscriber becomes an enterprise member. For more information, see [Inviting users to join your organization](/en/enterprise-cloud@latest/organizations/managing-membership-in-your-organization/inviting-users-to-join-your-organization).

   > \[!TIP]
   >
   > * While not required, we recommend that the organization owner sends an invitation to the same email address used for the subscriber's User Primary Name (UPN). When the email address on GitHub matches the subscriber's UPN, you can ensure that another enterprise does not claim the subscriber's license.
   > * If the subscriber accepts the invitation to the organization with an existing personal account on GitHub, we recommend that the subscriber add the email address they use for Visual Studio to their personal account on GitHub. For more information, see [Adding an email address to your GitHub account](/en/enterprise-cloud@latest/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/adding-an-email-address-to-your-github-account).
   > * If the organization owner must invite a large number of subscribers, a script may make the process faster. For more information, see [the sample PowerShell script](https://github.com/github/platform-samples/blob/master/api/powershell/invite_members_to_org.ps1) in the `github/platform-samples` repository.

6. If any enterprise members aren't automatically matched to their Visual Studio account, an enterprise owner can match the accounts manually on GitHub. See [Reconciling users across Visual Studio and GitHub](#reconciling-users-across-visual-studio-and-github).

After Visual Studio subscriptions with GitHub Enterprise is set up for subscribers on your team, enterprise owners can review licensing information on GitHub. For more information, see [Viewing usage for your GitHub Enterprise plan](/en/enterprise-cloud@latest/billing/managing-the-plan-for-your-github-account/viewing-the-subscription-and-usage-for-your-enterprise-account).

## Reconciling users across Visual Studio and GitHub

To stay compliant with the terms of use, a GitHub **enterprise owner** should ensure all user accounts are correctly matched across GitHub and Visual Studio.

Most users are automatically matched across GitHub and Visual Studio. If a user has different email addresses in GitHub and Visual Studio, you may need to match the accounts manually.

Under the terms of use, the GitHub account and Visual Studio account for a single license must belong to the same person.

### 1. Audit user mappings

To audit your user mappings, download a summary of assigned users from the Visual Studio portal, and compare it against the verified emails of users in your GitHub enterprise. See [Viewing people in your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/viewing-people-in-your-enterprise#viewing-members-email-addresses).

### 2. Match users to Visual Studio

When you've identified GitHub users who aren't correctly matched to their Visual Studio account, you can update the mappings on GitHub. You can't update mappings for users who have been automatically matched.

1. Go to your enterprise on GitHub and click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-credit-card" aria-label="credit-card" role="img"><path d="M10.75 9a.75.75 0 0 0 0 1.5h1.5a.75.75 0 0 0 0-1.5h-1.5Z"></path><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25ZM14.5 6.5h-13v5.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Zm0-2.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25V5h13Z"></path></svg> Billing and licensing**.
2. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Licensing**.
3. On the Licensing page, next to "Enterprise Cloud", click **Manage**.
4. In the list of users, look for users with an "Enterprise" license type. These are enterprise members that aren't matched to a user in your Visual Studio subscription.
5. To match a user to their Visual Studio account, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **Change to Visual Studio license**.
6. Select the user's Visual Studio login email, then click **Confirm change**.

## Viewing available licenses

You can view the number of GitHub Enterprise licenses available to your enterprise on GitHub.com. The list of pending invitations includes subscribers who are not yet members of at least one organization in your enterprise. For more information, see [Viewing usage for your GitHub Enterprise plan](/en/enterprise-cloud@latest/billing/managing-the-plan-for-your-github-account/viewing-the-subscription-and-usage-for-your-enterprise-account) and [Viewing people in your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/viewing-people-in-your-enterprise#viewing-members-and-outside-collaborators).

> \[!TIP] If you download a CSV file with your enterprise's license usage in step 6 of [Viewing usage for your GitHub Enterprise plan](/en/enterprise-cloud@latest/billing/managing-the-plan-for-your-github-account/viewing-the-subscription-and-usage-for-your-enterprise-account#viewing-the-subscription-and-usage-for-your-enterprise-account), any members with a missing value for the "Name" or "Profile" columns have not yet accepted an invitation to join an organization within the enterprise.

You can also see pending GitHub Enterprise invitations to subscribers in the [administrator portal for Visual Studio subscriptions](https://visualstudio.microsoft.com/subscriptions-administration/).

## Further reading

* [Getting started with GitHub Enterprise Cloud](/en/enterprise-cloud@latest/get-started/onboarding/getting-started-with-github-enterprise-cloud)