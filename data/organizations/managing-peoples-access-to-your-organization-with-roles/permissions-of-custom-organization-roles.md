# Permissions of custom organization roles

You can control access to your organization's settings and repositories with custom organization roles.

You can have more granular control over the access you grant to your organization and repository's settings by creating custom organization roles. Organization roles are a way to grant an organization member the ability to administer certain subsets of settings without granting full administrative control of the organization and its repositories. For example, you could create a role that contains the "View organization audit log" permission.

You can create and assign custom organization roles in your organization's settings. You can also manage custom roles using the REST API. See [Managing custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/managing-custom-organization-roles).

## Combining organization and repository permissions

You can also create a custom organization role that includes permissions for repositories. Repository permissions grant access to all current and future repositories in the organization.

There are several ways to combine permissions for repositories and organizations.

* You can create a role that includes permissions for organization settings, a base role for repository access, or both.
* If you add a base role for repository access, you can also include additional repository permissions. You can't add repository permissions without a base repository role.

Without repository permissions or a base repository role, the organization role doesn't grant access to any repositories.

> \[!NOTE]
> Adding repository permissions to a custom organization role is currently in public preview and subject to change.

To grant access to **specific** repositories in your organization, you can create a custom repository role. See [About custom repository roles](/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/about-custom-repository-roles).

## Permissions for organization access

When you include a permission in a custom organization role, any users with that role will have access to the corresponding settings via both the web browser and API. In the organization's settings in the browser, users will see only the pages for settings they can access.

Organization permissions do not grant read, write, or administrator access to any repositories. Some permissions may implicitly grant visibility of repository metadata, as marked in the table below.

<div class="ghd-tool rowheaders">

| Permission                                                 | Description                                                                                                                                                                                     | More information                                                                                                                                                                                                                                                                                                                     |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Manage custom organization roles                           | Access to create, view, update, and delete custom organization roles within the organization. This permission does not allow a user to assign custom roles.                                     | [Managing custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/managing-custom-organization-roles)                                                                                                                                                           |
| View organization roles                                    | Access to view the organization's custom organization roles.                                                                                                                                    | [Managing custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/managing-custom-organization-roles)                                                                                                                                                           |
| Manage custom repository roles                             | Access to create, view, update, and delete the organization's custom repository roles.                                                                                                          | [Managing custom repository roles for an organization](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/managing-custom-repository-roles-for-an-organization)                                                                                                                       |
| View custom repository roles                               | Access to view the organization's custom repository roles.                                                                                                                                      | [Managing custom repository roles for an organization](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/managing-custom-repository-roles-for-an-organization)                                                                                                                       |
| Manage organization webhooks                               | Access to register and manage webhooks for the organization. Users with this permission will be able to view webhook payloads, which may contain metadata for repositories in the organization. | [REST API endpoints for organization webhooks](/en/enterprise-cloud@latest/rest/orgs/webhooks#about-organization-webhooks)                                                                                                                                                                                                           |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| Manage organization OAuth app policies                     | Access to the "OAuth app policy" settings for the organization.                                                                                                                                 | [About OAuth app access restrictions](/en/enterprise-cloud@latest/organizations/managing-oauth-access-to-your-organizations-data/about-oauth-app-access-restrictions)                                                                                                                                                                |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| Edit custom properties values at the organization level    | Access to set custom property values on all repositories in the organization.                                                                                                                   | [Managing custom properties for repositories in your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization)                                                                                                                        |
| Manage the organization's custom properties definitions    | Access to create and edit custom property definitions for the organization.                                                                                                                     | [Managing custom properties for repositories in your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization)                                                                                                                        |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| Manage organization ref update rules and rulesets          | Access to manage rulesets and view ruleset insights at the organization level.                                                                                                                  | [Managing rulesets for repositories in your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/managing-rulesets-for-repositories-in-your-organization)                                                                                                                                          |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| View organization audit log                                | Access to the audit log for the organization. The audit log may contain metadata for repositories in the organization.                                                                          | [Reviewing the audit log for your organization](/en/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/reviewing-the-audit-log-for-your-organization)                                                                                                           |
| Manage organization Actions policies                       | Access to manage all settings on the "Actions General" settings page, except for self-hosted runners settings.                                                                                  | [Disabling or limiting GitHub Actions for your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization)                                                                                                                                    |
| Manage organization Actions secrets                        | Access to create and manage Actions organization secrets.                                                                                                                                       | [Using secrets in GitHub Actions](/en/enterprise-cloud@latest/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-an-organization)                                                                                                                                                                          |
| Manage organization Actions variables                      | Access to create and manage Actions organization variables.                                                                                                                                     | [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-an-organization)                                                                                                                                                                            |
| Manage organization hosted runner custom images            | Access to create and manage custom images for your organization.                                                                                                                                | [GitHub-hosted runners](/en/enterprise-cloud@latest/actions/concepts/runners/github-hosted-runners)                                                                                                                                                                                                                                  |
| Manage organization runners and runner groups              | Access to create and manage GitHub-hosted runners, self-hosted runners, and runner groups, and control where self-hosted runners can be created.                                                | [GitHub-hosted runners](/en/enterprise-cloud@latest/actions/using-github-hosted-runners/about-github-hosted-runners/about-github-hosted-runners#overview-of-github-hosted-runners)<br><br>[Self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners) |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| View organization Actions metrics                          | View GitHub Actions metrics for your organization.                                                                                                                                              | [Viewing GitHub Actions metrics for your organization](/en/enterprise-cloud@latest/organizations/collaborating-with-groups-in-organizations/viewing-usage-metrics-for-github-actions)                                                                                                                                                |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| View organization hosted runner custom images              | View custom images for your organization.                                                                                                                                                       | [GitHub-hosted runners](/en/enterprise-cloud@latest/actions/concepts/runners/github-hosted-runners)                                                                                                                                                                                                                                  |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| Review and manage secret scanning bypass requests          | Review and manage secret scanning bypass requests for your organization.                                                                                                                        | [About delegated bypass for push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/delegated-bypass-for-push-protection)                                                                                                                             |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| Review and manage secret scanning alert dismissal requests | Review and manage secret scanning alert dismissal requests for your organization.                                                                                                               | [Enabling delegated alert dismissal for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/enabling-delegated-alert-dismissal-for-secret-scanning)                                                                                               |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| Bypass code scanning alert dismissal requests              | Bypass code scanning alert dismissal requests for your organization.                                                                                                                            | [Enabling delegated alert dismissal for code scanning](/en/enterprise-cloud@latest/code-security/how-tos/manage-security-alerts/manage-code-scanning-alerts/enabling-delegated-alert-dismissal-for-code-scanning)                                                                                                                    |
| Review code scanning alert dismissal requests              | Review and manage code scanning alert dismissal requests for your organization.                                                                                                                 | [Enabling delegated alert dismissal for code scanning](/en/enterprise-cloud@latest/code-security/how-tos/manage-security-alerts/manage-code-scanning-alerts/enabling-delegated-alert-dismissal-for-code-scanning)                                                                                                                    |
| View code scanning alert dismissal requests                | View code scanning alert dismissal requests for your organization.                                                                                                                              | [Enabling delegated alert dismissal for code scanning](/en/enterprise-cloud@latest/code-security/how-tos/manage-security-alerts/manage-code-scanning-alerts/enabling-delegated-alert-dismissal-for-code-scanning)                                                                                                                    |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| Bypass Dependabot alert dismissal requests                 | Bypass Dependabot alert dismissal requests for your organization.                                                                                                                               | [Enabling delegated alert dismissal for Dependabot](/en/enterprise-cloud@latest/code-security/how-tos/manage-security-alerts/manage-dependabot-alerts/enable-delegated-alert-dismissal)                                                                                                                                              |
| Review Dependabot alert dismissal requests                 | Review and manage Dependabot alert dismissal requests for your organization.                                                                                                                    | [Enabling delegated alert dismissal for Dependabot](/en/enterprise-cloud@latest/code-security/how-tos/manage-security-alerts/manage-dependabot-alerts/enable-delegated-alert-dismissal)                                                                                                                                              |
| View Dependabot alert dismissal requests                   | View Dependabot alert dismissal requests for your organization.                                                                                                                                 | [Enabling delegated alert dismissal for Dependabot](/en/enterprise-cloud@latest/code-security/how-tos/manage-security-alerts/manage-dependabot-alerts/enable-delegated-alert-dismissal)                                                                                                                                              |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |
| View organization Copilot metrics                          | View Copilot usage metrics for your organization.                                                                                                                                               | [GitHub Copilot usage metrics](/en/enterprise-cloud@latest/copilot/concepts/copilot-metrics)                                                                                                                                                                                                                                         |
|                                                            |                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                      |

</div>

## Base roles for repository access

The base repository role determines the initial set of permissions included in the custom role. Repository access is granted across **all** current and future repositories in the organization.

The base repository roles are:

* **Read:** Grants read access to all repositories in the organization.
* **Write:** Grants write access to all repositories in the organization.
* **Triage:** Grants triage access to all repositories in the organization.
* **Maintain:** Grants maintenance access to all repositories in the organization.
* **Admin:** Grants admin access to all repositories in the organization.

## Additional permissions for repository access

After choosing a base repository role, you can select additional permissions for your custom organization role.

You can only choose an additional permission if it's not already included in the base repository role. For example, if the base role offers **Write** access to a repository, then the "Close a pull request" permission will already be included in the base role.

### Discussions

* Create a discussion category
* Edit a discussion category
* Delete a discussion category
* Mark or unmark discussion answers
* Hide or unhide discussion comments
* Convert issues to discussions

For more information, see [GitHub Discussions documentation](/en/enterprise-cloud@latest/discussions).

### Issue and pull requests

* Assign or remove a user
* Add or remove a label

### Issue

* Close an issue
* Reopen a closed issue
* Delete an issue
* Mark an issue as a duplicate

### Merge queue

* Request a solo merge
* Jump to the front of the queue

For more information, see [Managing a merge queue](/en/enterprise-cloud@latest/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue).

### Pull request

* Close a pull request
* Reopen a closed pull request
* Request a pull request review

### Repository

* Set milestones
* Manage wiki settings
* Manage project settings
* Manage pull request merging settings
* Manage GitHub Pages settings (see [Configuring a publishing source for your GitHub Pages site](/en/enterprise-cloud@latest/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site))
* Manage webhooks
* Manage deploy keys
* Edit repository metadata
* Set interaction limits
* Set the social preview
* Push commits to protected branches
  * Base role must be `write`
  * Branch protection rules will still apply
* Create protected tags
* Delete protected tags
* Bypass branch protections
* Edit repository rules

### Security

* View code scanning alerts
* Dismiss or reopen code scanning alerts
* Delete code scanning alerts
* View Dependabot alerts
* Dismiss or reopen Dependabot alerts
* View secret scanning alerts
* Dismiss, reopen, or assign secret scanning alerts

### Actions

* Manage GitHub Actions general settings
* Manage runners
* Manage secrets
* Manage variables
* Manage environments (including environment secrets and variables)

## Precedence for different levels of access

Roles and permissions are additive. If a person is given different levels of access through different avenues, such as team membership and the base permissions for an organization, the user has the sum of all access grants. For example, if an organization owner gives an organization member a custom role that uses the "Read" inherited role, and then an organization owner sets the organization's base permission to "Write", then members with the custom role will have write access, along with any additional permissions included in the custom role.

If a person has been given conflicting access, you'll see a warning on the repository access page. The warning appears with "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-alert" aria-label="alert" role="img"><path d="M6.457 1.047c.659-1.234 2.427-1.234 3.086 0l6.082 11.378A1.75 1.75 0 0 1 14.082 15H1.918a1.75 1.75 0 0 1-1.543-2.575Zm1.763.707a.25.25 0 0 0-.44 0L1.698 13.132a.25.25 0 0 0 .22.368h12.164a.25.25 0 0 0 .22-.368Zm.53 3.996v2.5a.75.75 0 0 1-1.5 0v-2.5a.75.75 0 0 1 1.5 0ZM9 11a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Mixed roles" next to the person with the conflicting access. To see the source of the conflicting access, hover over the warning icon or click **Mixed roles**.

To resolve conflicting access, you can adjust your organization's base permissions or the team's access, or edit the custom role. For more information, see:

* [Setting base permissions for an organization](/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/setting-base-permissions-for-an-organization)
* [Managing team access to an organization repository](/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-team-access-to-an-organization-repository)
* [Editing a repository role](/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/managing-custom-repository-roles-for-an-organization#editing-a-repository-role)
* [Managing custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/managing-custom-organization-roles#editing-a-custom-role)