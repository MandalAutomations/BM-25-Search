# Converting an organization member to an outside collaborator

If a current member of your organization only needs access to certain repositories, such as consultants or temporary employees, you can convert them to an outside collaborator.

## About conversion of organization members to outside collaborators

You can convert a member of an organization to an outside collaborator. For more information about outside collaborators, see [Adding outside collaborators to repositories in your organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-outside-collaborators/adding-outside-collaborators-to-repositories-in-your-organization).

If the organization is owned by an enterprise, converting an organization member to an outside collaborator may be restricted. For more information, see [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-inviting-outside-collaborators-to-repositories) in the GitHub Enterprise Cloud documentation.

Unless you are on a free plan, adding an outside collaborator to a private repository will use one of your paid licenses. For more information, see "[About per-user pricing](/en/billing/managing-the-plan-for-your-github-account/about-per-user-pricing)." When you add an outside collaborator to a repository, you'll also need to add them to any forks of the repository you'd like them to access.

After converting a member to an outside collaborator, they will no longer be an explicit member of the organization and will be removed from all teams. They will retain repository access to those they were directly added to, as well as those added through their former team memberships. They will no longer be able to:

* Create teams
* See all organization members and teams
* @mention any visible team
* Be a team maintainer

For more information, see [Roles in an organization](/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization).

We recommend reviewing the organization member's access to repositories to ensure their access is as you expect. For more information, see [Managing an individual's access to an organization repository](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/managing-an-individuals-access-to-an-organization-repository).

When you convert an organization member to an outside collaborator, their privileges as organization members are saved for three months so that you can restore their membership privileges if you invite them to rejoin your organization within that time frame. For more information, see [Reinstating a former member of your organization](/en/organizations/managing-membership-in-your-organization/reinstating-a-former-member-of-your-organization).

## Converting an organization member to an outside collaborator

> \[!NOTE]
> You may not be able to convert an organization member to an outside collaborator, if an organization owner has restricted your ability to add outside collaborators.

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. Click the name of your organization.
3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.

   ![Screenshot of the horizontal navigation bar for an organization. A tab, labeled with a person icon and "People," is outlined in dark orange.](/assets/images/help/organizations/organization-people-tab.png)
4. Select the person or people you'd like to convert to outside collaborators.

   ![Screenshot of the first two users in a list of organization members. To the left of each member, a checkbox is checked and outlined in dark orange.](/assets/images/help/teams/list-of-members-selected-bulk.png)
5. Above the list of members, select the **X members selected...** dropdown menu and click **Convert to outside collaborator**.

   ![Screenshot of the list of organization members. Above the list, a dropdown menu, labeled "2 members selected..." is outlined in dark orange.](/assets/images/help/teams/user-bulk-management-options.png)
6. Read the information about converting members to outside collaborators, then click **Convert to outside collaborator**.