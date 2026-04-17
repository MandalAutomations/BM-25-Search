# Creating enterprise teams

Organize users into teams to simplify license management.

To simplify administration at scale, you can create enterprise teams. Enterprise teams can:

* Receive **Copilot Business licenses** directly from the enterprise.
* Be assigned **predefined and custom enterprise roles**, giving members access to enterprise settings.
* Be **added to organizations**, where organization administrators can grant the team additional access and permissions.
* Receive **bypass access** on rulesets.

Adding a user to a team grants them the privileges associated with the team. Removing a user from a team removes those privileges, but does not remove the user from the enterprise account.

There are **limits on enterprise teams**. You can create up to 2,500 teams for a single enterprise and add up to 5,000 users to each team. Each team can be assigned to a maximum of 1,000 organizations.

<!-- If the team size limit changes, also update the reference in "Limits on IdP group sizes" below -->

> \[!NOTE] Enterprise teams are in public preview and subject to change.

## 1. Navigate to the enterprise teams page

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-people" aria-label="people" role="img"><path d="M2 5.5a3.5 3.5 0 1 1 5.898 2.549 5.508 5.508 0 0 1 3.034 4.084.75.75 0 1 1-1.482.235 4 4 0 0 0-7.9 0 .75.75 0 0 1-1.482-.236A5.507 5.507 0 0 1 3.102 8.05 3.493 3.493 0 0 1 2 5.5ZM11 4a3.001 3.001 0 0 1 2.22 5.018 5.01 5.01 0 0 1 2.56 3.012.749.749 0 0 1-.885.954.752.752 0 0 1-.549-.514 3.507 3.507 0 0 0-2.522-2.372.75.75 0 0 1-.574-.73v-.352a.75.75 0 0 1 .416-.672A1.5 1.5 0 0 0 11 5.5.75.75 0 0 1 11 4Zm-5.5-.5a2 2 0 1 0-.001 3.999A2 2 0 0 0 5.5 3.5Z"></path></svg> Enterprise teams**.

## 2. Create a team

1. On the enterprise teams page, click **Create Enterprise team**.

2. Choose the team's name, description, and organization access.

   When you give a team access to organizations, members of the team are added directly to those organizations, without an invitation, and receive the same access as other organization members.

   * Outside collaborators and unaffiliated users in the team become standard enterprise members, meaning they have access to your enterprise's internal repositories and consume a GitHub Enterprise license.
   * Team members receive the base level of repository permissions for the organization.
   * Organization administrators can give the team additional repository access and assign them organization-level roles, but **cannot** remove any permissions granted by enterprise administrators.

3. Click **Create Enterprise team**.

## 3. Add users

There are multiple ways to add users to an enterprise team.

* [Adding users manually](#adding-users-manually)
* [Syncing with an IdP group](#syncing-with-an-idp-group) (Enterprise Managed Users only)
* Using the [REST API endpoints for enterprise team memberships](/en/enterprise-cloud@latest/rest/enterprise-teams/enterprise-team-members)

Enterprise teams can contain organization members, unaffiliated users, and outside collaborators.

### Adding users manually

1. On the enterprise teams page, click the team you want to add users to.
2. Click **Add members**, then search for and select the users you want to add.
3. Click **Add**.

### Syncing with an IdP group

If you use Enterprise Managed Users, you can sync membership of an enterprise team to a group in your identity provider. That way, any changes made to the group in the IdP (such as adding or removing a user) will be synced to the enterprise team via SCIM. For details and requirements, see [Managing team memberships with identity provider groups](/en/enterprise-cloud@latest/admin/managing-iam/provisioning-user-accounts-with-scim/managing-team-memberships-with-identity-provider-groups).

1. On the enterprise teams page, click the team you want to sync.
2. Ensure the team contains no manually assigned users. You can remove users by using the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More member actions" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** menu next to the user's name in the member list.
3. Next to the team's name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="pencil" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> Edit**.
4. Under "Manage members", click **Identity provider group**.
5. Click **Select group**, then choose the external IdP group to sync to the team. Members from the IdP group will display in the team's member list.
6. Click **Update team**.

#### Limits on IdP group sizes

If an IdP group goes over the team size limit of 5,000 users, the team will stop being synced.

For example:

* An enterprise team is initially synced with an IdP group of 5 users.
* 5,000 more users are added to the IdP group. Because the IdP group now has 5,005 users, the group isn't synced and the enterprise team remains at 5 members.
* 5 users are removed from the IdP group to bring it to 5,000 users. Syncing resumes and the enterprise team now contains the same 5,000 users as the IdP group.

## 4. Assign licenses

You can assign GitHub Copilot licenses to an enterprise team. This allows you to manage Copilot access through team membership, independent of organizations. Once you have assigned licenses to a team, users will gain or lose access to Copilot when they are added or removed from the team.

For instructions, see [Granting users access to GitHub Copilot in your enterprise](/en/enterprise-cloud@latest/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-access/grant-access#assigning-licenses-to-users-or-teams).

## 5. Assign roles

You can assign custom enterprise roles and certain predefined roles to enterprise teams. This allows you to delegate administrative duties to specific teams or provide non-administrators with permissions that will help them work independently. See [Assigning roles to people in an enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-roles-in-your-enterprise/assign-roles).