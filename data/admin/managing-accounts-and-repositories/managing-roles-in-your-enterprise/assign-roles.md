# Assigning roles to people in an enterprise

Govern what people can do in your enterprise by assigning roles to users and teams.

Enterprise owners can assign custom and predefined **enterprise roles** to users and teams. Some roles can be assigned to enterprise teams, whereas other roles are only available for individual users. Find the section below for the role you want to assign.

For more information about using roles effectively, see [Identifying the roles required by your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-roles-in-your-enterprise/identify-role-requirements).

## Assigning app managers, security managers, and custom roles

> \[!NOTE] These roles are in public preview and subject to change.

These roles can be assigned to existing users and teams in your enterprise settings, including managed user accounts.

Before you assign a role, you may need to create a team. Teams are the best way to manage role assignments at scale. The enterprise security manager role can **only** be assigned to a team, not to individual users. See [Creating enterprise teams](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/create-enterprise-teams).

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-globe" aria-label="globe" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM5.78 8.75a9.64 9.64 0 0 0 1.363 4.177c.255.426.542.832.857 1.215.245-.296.551-.705.857-1.215A9.64 9.64 0 0 0 10.22 8.75Zm4.44-1.5a9.64 9.64 0 0 0-1.363-4.177c-.307-.51-.612-.919-.857-1.215a9.927 9.927 0 0 0-.857 1.215A9.64 9.64 0 0 0 5.78 7.25Zm-5.944 1.5H1.543a6.507 6.507 0 0 0 4.666 5.5c-.123-.181-.24-.365-.352-.552-.715-1.192-1.437-2.874-1.581-4.948Zm-2.733-1.5h2.733c.144-2.074.866-3.756 1.58-4.948.12-.197.237-.381.353-.552a6.507 6.507 0 0 0-4.666 5.5Zm10.181 1.5c-.144 2.074-.866 3.756-1.58 4.948-.12.197-.237.381-.353.552a6.507 6.507 0 0 0 4.666-5.5Zm2.733-1.5a6.507 6.507 0 0 0-4.666-5.5c.123.181.24.365.353.552.714 1.192 1.436 2.874 1.58 4.948Z"></path></svg> Enterprise roles**, then click **Role assignments**.
4. Click **Assign role**.
5. Choose the user or team and the role they should receive, then click **Assign role**.

## Assigning enterprise owners, billing managers, and guest collaborators

These roles:

* Can be chosen when you invite a user to your enterprise or provision a user from your identity provider (IdP)
* Cannot currently be assigned to enterprise teams
* Can be changed for existing users

### Assigning to new users

* If you use **Enterprise Managed Users**, roles are assigned from your IdP via the SCIM `roles` attribute.
* Otherwise, you can invite someone as a user or administrator. See [Inviting users to your enterprise directly](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/invite-users-directly) or [Inviting people to manage your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/inviting-people-to-manage-your-enterprise).

### Assigning to existing administrators

You can change an administrator's role or convert them to a regular member once they have joined your enterprise.

* If you use **Enterprise Managed Users**, you must do this from your IdP via the SCIM `roles` attribute.
* If you use an **enterprise with personal accounts**, you can change the role on your enterprise's "Administrators" page, using the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Administrator" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** menu next to the user's name. See [Viewing people in your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/viewing-people-in-your-enterprise#viewing-enterprise-administrators).

## Assigning roles in an organization

Enterprise owners cannot assign organization-level roles from the enterprise settings. An organization administrator must do this. See [Using organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/using-organization-roles#assigning-an-organization-role).