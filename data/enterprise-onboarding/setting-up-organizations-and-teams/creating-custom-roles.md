# Creating custom roles

Create custom organization roles with fine-grained permissions tailored to your enterprise needs.

To tailor access management to your company's needs, you can create custom roles for your enterprise account and organizations.

Custom roles are sets of permissions for settings and resources that you can assign to users and teams. To learn best practices for using roles on GitHub, see [Identifying the roles required by your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-roles-in-your-enterprise/identify-role-requirements).

## Creating enterprise custom roles

> \[!NOTE] This feature is in public preview and subject to change.

Enterprise custom roles grant access to a subset of enterprise settings, such as viewing audit logs and creating organizations. GitHub plans to expand the list of available permissions over time.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-globe" aria-label="globe" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM5.78 8.75a9.64 9.64 0 0 0 1.363 4.177c.255.426.542.832.857 1.215.245-.296.551-.705.857-1.215A9.64 9.64 0 0 0 10.22 8.75Zm4.44-1.5a9.64 9.64 0 0 0-1.363-4.177c-.307-.51-.612-.919-.857-1.215a9.927 9.927 0 0 0-.857 1.215A9.64 9.64 0 0 0 5.78 7.25Zm-5.944 1.5H1.543a6.507 6.507 0 0 0 4.666 5.5c-.123-.181-.24-.365-.352-.552-.715-1.192-1.437-2.874-1.581-4.948Zm-2.733-1.5h2.733c.144-2.074.866-3.756 1.58-4.948.12-.197.237-.381.353-.552a6.507 6.507 0 0 0-4.666 5.5Zm10.181 1.5c-.144 2.074-.866 3.756-1.58 4.948-.12.197-.237.381-.353.552a6.507 6.507 0 0 0 4.666-5.5Zm2.733-1.5a6.507 6.507 0 0 0-4.666-5.5c.123.181.24.365.353.552.714 1.192 1.436 2.874 1.58 4.948Z"></path></svg> Enterprise roles**, then click **Role management**.
4. Click **Create custom role**.
5. Enter the details, then click **Create role**.

## Creating organization custom roles

Organization custom roles grant access to organization settings and repositories. Custom organization roles created at the enterprise level use the same permissions and base roles as roles created at the organization level. For more information, see [Permissions of custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles).

Enterprise owners can create and edit custom organization roles, but cannot assign them. Organization owners can assign custom roles in an organization.

> \[!NOTE] An enterprise can create up to 20 custom organization roles. This limit applies to the enterprise: each organization can also create up to 20 custom organization roles.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. In the left sidebar, select **Organization roles**.
4. Click **Create custom role**.
5. Enter the details, then click **Create role**.

## Next steps

You can manage role assignments at scale using teams. Learn about teams in your enterprise and organizations in [About teams in an enterprise](/en/enterprise-cloud@latest/enterprise-onboarding/setting-up-organizations-and-teams/about-teams-in-an-enterprise).