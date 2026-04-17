# Granting users access to GitHub Copilot in your enterprise

Enable Copilot for entire organizations or grant access directly to specific users.

There are two main ways to grant access to Copilot in an enterprise:

* **Assign licenses directly to users or teams** in the enterprise. This approach simplifies license management at scale and provides the option of granting Copilot licenses to users who don't consume a GitHub Enterprise license. This approach is currently only available for **Copilot Business** licenses.
* **Enable Copilot for organizations**. This approach allows you to choose Copilot Business or Copilot Enterprise for individual organizations and give organization owners control to grant licenses to the users who need them most.

## Assigning licenses to users or teams

You can assign Copilot Business licenses directly to users or enterprise teams.

When you assign licenses to an enterprise team, users receive or lose access to Copilot when they are added or removed from the team. If you use Enterprise Managed Users, you can sync the team with an identity provider (IdP) group and manage licensing from your IdP.

### Prerequisites

* Set the **Policies for enterprise-assigned users** policy to define a default setting for these users when other enterprise policies are set to "No policy". See [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies#defining-policies-for-your-enterprise).
* If you want to assign licenses to users who are not already in your enterprise, you must first invite the users (personal accounts) or provision them from your identity provider (Enterprise Managed Users). For personal accounts, see [Inviting users to your enterprise directly](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/invite-users-directly).
* If you want to assign a license to an enterprise team, you must create the team first. See [Creating enterprise teams](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/create-enterprise-teams).

### Assigning licenses

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-credit-card" aria-label="credit-card" role="img"><path d="M10.75 9a.75.75 0 0 0 0 1.5h1.5a.75.75 0 0 0 0-1.5h-1.5Z"></path><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25ZM14.5 6.5h-13v5.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Zm0-2.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25V5h13Z"></path></svg> Billing and licensing**.

3. In the left sidebar, click **Licensing**.

4. Next to "Copilot", click **Manage**.

   ![Screenshot of the Licensing page, with the "Manage" button highlighted in orange.](/assets/images/help/copilot/manage-licenses.png)

5. Click the **All members** or **Enterprise Teams** tab.

6. Click **Assign licenses**.

7. Search for users or teams, then click **Add licenses**.

8. Optionally, disable Copilot for organizations to prevent organization owners from assigning licenses. See [Disabling Copilot for organizations in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-access/disable-for-organizations).

## Enabling Copilot for organizations

If your enterprise has a Copilot Enterprise plan, you can assign licenses for either Copilot Enterprise or Copilot Business.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-credit-card" aria-label="credit-card" role="img"><path d="M10.75 9a.75.75 0 0 0 0 1.5h1.5a.75.75 0 0 0 0-1.5h-1.5Z"></path><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25ZM14.5 6.5h-13v5.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Zm0-2.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25V5h13Z"></path></svg> Billing and licensing**.

3. In the "Billing and licensing" sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Licensing**.

4. In the "Copilot" section, click **Manage**.

5. Next to "Organization access", choose whether to enable Copilot for all organizations or allow for specific organizations.

   ![Screenshot of the the "Organization access" section, with the dropdown menu highlighted.](/assets/images/help/copilot/organization-access-menu.png)

6. If you selected **Allow for specific organizations**:
   1. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations** tab.
   2. Locate the organization for which you want to enable Copilot.
   3. To the right of the organization name, select the **Copilot** dropdown menu.
      * If your enterprise has a Copilot Business plan, click **Enabled**.
      * If your enterprise has a Copilot Enterprise plan, click either **Copilot: Enterprise** or **Copilot: Business** to assign a specific Copilot plan to the organization.

### Next steps

After you've enabled Copilot for an organization in your enterprise, owners of the organization can grant access to some or all members of the organization. See [Granting access to GitHub Copilot for members of your organization](/en/copilot/managing-github-copilot-in-your-organization/managing-access-for-copilot-business-in-your-organization).

## Further reading

* [GitHub Copilot licenses](/en/billing/managing-billing-for-github-copilot/about-billing-for-github-copilot)
* [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-policies-and-features-for-copilot-in-your-enterprise)