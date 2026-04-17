# Removing a member from your organization

If members of your organization no longer require access to any repositories owned by the organization, you can remove them from the organization.

## 1. Understand the effects of removing a member

When you remove members from an organization:

* If you use volume license billing, the paid license count does not automatically downgrade. To pay for fewer licenses after removing users from your organization, follow the steps in [Downgrading your account's plan](/en/billing/managing-the-plan-for-your-github-account/downgrading-your-accounts-plan).
* Removed members will lose access to private forks of your organization's private repositories, but they may still have local copies. However, they cannot sync local copies with your organization's repositories. Ultimately, you are responsible for ensuring that people who have lost access to a repository delete any confidential information or intellectual property.
* When private repositories are forked to other organizations, those organizations are able to control access to the fork network. This means users may retain access to the forks even after losing access to the original organization because they will still have explicit access via a fork.
* Removed members will also lose access to private forks of your organization's internal repositories, if the removed member is not a member of any other organization owned by the same enterprise account.
* Any organization invitations sent by a removed member, that have not been accepted, are canceled and will not be accessible.
* If the organization is part of an enterprise on GitHub Enterprise Cloud and the user is still a member of at least one other organization in the enterprise, the user will retain access to repositories with internal visibility in the organization that they are removed from.
* If the organization is part of an enterprise on GitHub Enterprise Cloud and the user is no longer a member of any organizations in it, the user will either become an enterprise unaffiliated member or be removed from the enterprise, depending on your settings. See [About user offboarding on GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/concepts/identity-and-access-management/user-offboarding).
* When you remove a user from your organization, their membership data is saved for three months. You can restore their data, or any private forks they owned of your organization's repositories, if you invite the user to rejoin the organization within that time frame. For more information, see [Reinstating a former member of your organization](/en/organizations/managing-membership-in-your-organization/reinstating-a-former-member-of-your-organization).

## 2. Share best practices

To help the person you're removing from your organization transition and help ensure they delete confidential information or intellectual property, we recommend sharing a checklist of best practices for leaving your organization. For an example, see [Prepare for job change](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-your-personal-account/best-practices-for-leaving-your-company).

## 3. Understand how you manage organization membership (enterprises only)

If the organization is on GitHub Enterprise Cloud, you may manage organization membership from an identity provider.

If you have an enterprise with personal accounts, check if you are using SCIM provisioning in the organization to manage membership. If you are, remove the user from the GitHub application in your IdP and from any IdP groups that are linked to teams with access to the organization. See [About SCIM for organizations](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/about-scim-for-organizations).

If you use Enterprise Managed Users, check the "member type" of the user to see if their membership is managed manually or by IdP groups. If the user is "Managed by IdP groups", remove the user from any IdP groups that are linked to teams with access to the organization. See [Viewing people in your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/viewing-people-in-your-enterprise#filtering-by-member-type-in-an-enterprise-with-managed-users).

## 4. Remove the user manually

If the user's organization membership is **not** managed with by a SCIM integration, you can remove the user from an organization manually.

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. Click the name of your organization.
3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.

   ![Screenshot of the horizontal navigation bar for an organization. A tab, labeled with a person icon and "People," is outlined in dark orange.](/assets/images/help/organizations/organization-people-tab.png)
4. Select the member or members you'd like to remove from the organization.

   ![Screenshot of the first two users in a list of organization members. To the left of each member, a checkbox is checked and outlined in dark orange.](/assets/images/help/teams/list-of-members-selected-bulk.png)
5. Above the list of members, select the **X members selected...** dropdown menu, and click **Remove from organization**.

   ![Screenshot of the list of organization members. Above the list, a dropdown menu, labeled "2 members selected..." is outlined in dark orange.](/assets/images/help/teams/user-bulk-management-options.png)
6. Review the member or members who will be removed from the organization, then click **Remove members**.

## Further reading

* [Removing organization members from a team](/en/organizations/organizing-members-into-teams/removing-organization-members-from-a-team)