# Security log events

Learn about security log events recorded for your personal account.

> \[!NOTE]
> This article contains the events that may appear in your user account's security log. For the events that can appear in an organization's audit log, see [Audit log events for your organization](/en/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/audit-log-events-for-your-organization)."

## About security log events

The name for each audit log entry is composed of a category of events, followed by an operation type. For example, the `repo.create` entry refers to the `create` operation on the `repo` category. The reference information in this article is grouped by categories.

## Audit log events

### Common fields

The following fields are included in most audit log events: `@timestamp`, `_document_id`, `action`, `actor`, `actor_id`, `business`, `business_id`, `created_at`, `hashed_token`, `operation_type`, `org`, `org_id`, `programmatic_access_type`, `repo`, `repo_id`, `repository`, `repository_id`, `request_access_security_header`, `request_id`, `token_id`, `token_scopes`, `user`, `user_agent`, `user_id`

Each event below lists only its additional fields beyond these common fields.

### account

#### `account.plan_change`

The account's plan changed.

**Reference:** [How GitHub billing works](/en/billing/managing-the-plan-for-your-github-account/about-billing-for-plans)

### actions\_cache

#### `actions_cache.delete`

A GitHub Actions cache was deleted using the REST API.

**Additional fields:** `oauth_application_id`, `actions_cache_id`, `actions_cache_key`, `actions_cache_version`, `actions_cache_scope`

### artifact

#### `artifact.destroy`

A workflow run artifact was manually deleted.

### billing

#### `billing.budget_create`

A billing budget was created for a business or organization. Includes details about the budget limit, alerting preferences, and recipients.

**Additional fields:** `customer_id`, `target_amount`, `target_type`, `target_id`, `alert_enabled`, `status`, `actor_is_bot`, `pricing_target_type`, `pricing_target_id`, `budget_limit_type`, `alert_recipient_user_ids`, `exclude_cost_center_usage`

#### `billing.budget_delete`

A billing budget was deleted for a business or organization. Includes details about the removed budget and any alerting settings.

**Additional fields:** `customer_id`, `uuid`, `status`, `actor_is_bot`

#### `billing.budget_update`

A billing budget was updated for a business or organization. Includes details about the updated limit and alerting settings.

**Additional fields:** `customer_id`, `target_amount`, `target_type`, `target_id`, `alert_enabled`, `status`, `actor_is_bot`, `old_target_amount`, `old_budget_limit_type`, `old_alert_enabled`, `old_target_id`, `old_pricing_target_type`, `old_pricing_target_id`

#### `billing.change_billing_type`

The way the account pays for GitHub was changed.

**Reference:** [Managing your payment and billing information](/en/billing/managing-your-github-billing-settings/adding-or-editing-a-payment-method)

#### `billing.change_email`

The billing email address changed.

**Additional fields:** `email`

**Reference:** [Managing your payment and billing information](/en/billing/managing-your-github-billing-settings/setting-your-billing-email)

#### `billing.overage_policy_updated`

The premium request paid usage policy for your GitHub account was changed.

**Additional fields:** `actor_is_bot`

**Reference:** /copilot/how-tos/manage-and-track-spending/manage-request-allowances#setting-a-policy-for-paid-usage

### billing\_customer

#### `billing_customer.azure_subscription_linked`

Azure subscription has been linked on this account.

#### `billing_customer.azure_subscription_unlinked`

Azure subscription has been unlinked on this account.

### business

#### `business.add_admin`

An enterprise owner was added to an enterprise.

**Additional fields:** `name`

**Reference:** [Inviting people to manage your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/inviting-people-to-manage-your-enterprise)

#### `business.add_billing_manager`

A billing manager was added to an enterprise.

**Additional fields:** `name`

#### `business.add_support_entitlee`

A support entitlement was added to a member of an enterprise.

**Additional fields:** `name`

**Reference:** [Managing support entitlements for your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/managing-support-entitlements-for-your-enterprise)

#### `business.remove_admin`

An enterprise owner was removed from an enterprise.

**Additional fields:** `name`

**Reference:** [Inviting people to manage your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/inviting-people-to-manage-your-enterprise)

#### `business.remove_billing_manager`

A billing manager was removed from an enterprise.

**Additional fields:** `name`

#### `business.remove_member`

A member was removed from an enterprise.

#### `business.remove_support_entitlee`

A support entitlement was removed from a member of an enterprise.

**Additional fields:** `name`

**Reference:** [Managing support entitlements for your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/managing-support-entitlements-for-your-enterprise)

#### `business.security_center_export_code_scanning_metrics`

A CSV export was requested on the "CodeQL pull request alerts" page.

**Additional fields:** `query`, `filename`, `requested_at`, `start_date`, `end_date`, `actor_is_bot`

#### `business.security_center_export_coverage`

A CSV export was requested on the "Coverage" page.

**Additional fields:** `query`, `filename`, `requested_at`, `actor_is_bot`

#### `business.security_center_export_overview_dashboard`

A CSV export was requested on the "Overview Dashboard" page.

**Additional fields:** `query`, `filename`, `requested_at`, `start_date`, `end_date`, `actor_is_bot`

#### `business.security_center_export_risk`

A CSV export was requested on the "Risk" page.

**Additional fields:** `query`, `filename`, `requested_at`, `actor_is_bot`

#### `business.set_actions_cache_retention_policy`

The cache retention policy for GitHub Actions was set for an enterprise.

**Additional fields:** `name`, `actor_is_bot`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise)

#### `business.set_actions_cache_storage_policy`

The cache storage policy for GitHub Actions was set for an enterprise.

**Additional fields:** `name`, `actor_is_bot`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise)

#### `business.set_actions_fork_pr_approvals_policy`

The policy for requiring approvals for workflows from public forks was changed for an enterprise.

**Additional fields:** `name`, `policy`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise#enforcing-a-policy-for-fork-pull-requests-in-your-enterprise)

#### `business.set_actions_private_fork_pr_approvals_policy`

The policy for requiring approval for fork pull request workflows from collaborators without write access to private repos was changed for an enterprise.

**Additional fields:** `name`, `policy`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise#enforcing-a-policy-for-fork-pull-requests-in-private-repositories)

#### `business.set_actions_retention_limit`

The retention period for GitHub Actions artifacts and logs was changed for an enterprise.

**Additional fields:** `name`, `limit`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise#enforcing-a-policy-for-artifact-and-log-retention-in-your-enterprise)

#### `business.set_default_workflow_permissions`

The default permissions granted to the GITHUB\_TOKEN when running workflows were changed for an enterprise.

**Additional fields:** `name`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise#enforcing-a-policy-for-workflow-permissions-in-your-enterprise)

#### `business.set_fork_pr_workflows_policy`

The policy for fork pull request workflows was changed for an enterprise.

**Additional fields:** `name`, `policy`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise#enforcing-a-policy-for-fork-pull-requests-in-your-enterprise)

#### `business.set_workflow_permission_can_approve_pr`

The policy for allowing GitHub Actions to create and approve pull requests was changed for an enterprise.

**Additional fields:** `name`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise#preventing-github-actions-from-creating-or-approving-pull-requests)

### checks

#### `checks.auto_trigger_disabled`

Automatic creation of check suites was disabled on a repository in the organization or enterprise.

**Additional fields:** `visibility`

**Reference:** /rest/checks#update-repository-preferences-for-check-suites

#### `checks.auto_trigger_enabled`

Automatic creation of check suites was enabled on a repository in the organization or enterprise.

**Additional fields:** `visibility`, `public_repo`

**Reference:** /rest/checks#update-repository-preferences-for-check-suites

#### `checks.delete_logs`

Logs in a check suite were deleted.

### codespaces

#### `codespaces.allow_permissions`

A codespace using custom permissions from its devcontainer.json file was launched.

**Additional fields:** `origin_repository`

#### `codespaces.connect`

Credentials for a codespace were refreshed.

**Additional fields:** `pull_request_id`, `owner`, `name`, `public_repo`, `actor_is_bot`, `machine_type`, `devcontainer_path`

#### `codespaces.create`

A codespace was created

**Additional fields:** `pull_request_id`, `owner`, `name`, `actor_is_bot`, `machine_type`, `devcontainer_path`

**Reference:** [Creating a codespace for a repository](/en/codespaces/developing-in-codespaces/creating-a-codespace-for-a-repository)

#### `codespaces.destroy`

A user deleted a codespace.

**Additional fields:** `pull_request_id`, `owner`, `name`

**Reference:** [Deleting a codespace](/en/codespaces/developing-in-codespaces/deleting-a-codespace)

#### `codespaces.export_environment`

A codespace was exported to a branch on GitHub.

**Additional fields:** `oauth_application_id`, `owner`, `public_repo`

#### `codespaces.restore`

A codespace was restored.

**Additional fields:** `owner`, `public_repo`

#### `codespaces.start_environment`

A codespace was started.

**Additional fields:** `name`, `owner`, `pull_request_id`, `machine_type`, `devcontainer_path`, `public_repo`

#### `codespaces.suspend_environment`

A codespace was stopped.

**Additional fields:** `owner`, `public_repo`

#### `codespaces.trusted_repositories_access_update`

A personal account's access and security setting for Codespaces were updated.

**Reference:** [Managing access to other repositories within your codespace](/en/codespaces/managing-codespaces-for-your-organization/managing-repository-access-for-your-organizations-codespaces)

### copilot

#### `copilot.cfb_seat_added`

A Copilot Business or Copilot Enterprise seat was added for a user and they have received access to GitHub Copilot. This can occur as the result of directly assigning a seat for a user, assigning a seat for a team, or setting the organization to allow access for all members.

#### `copilot.cfb_seat_assignment_created`

A Copilot Business or Copilot Enterprise seat assignment was newly created for a user or a team, and seats are being created.

**Reference:** [What is GitHub Copilot?](/en/copilot/overview-of-github-copilot/about-github-copilot-for-business)

#### `copilot.cfb_seat_assignment_refreshed`

A seat assignment that was previously pending cancellation was re-assigned and the user will retain access to Copilot.

#### `copilot.cfb_seat_assignment_reused`

A Copilot Business or Copilot Enterprise seat assignment was re-created for a user who already had a seat with no pending cancellation date, and the user will retain access to Copilot.

#### `copilot.cfb_seat_assignment_unassigned`

A user or team's Copilot Business or Copilot Enterprise seat assignment was unassigned, and the user(s) will lose access to Copilot at the end of the current billing cycle.

#### `copilot.cfb_seat_cancelled`

A user's Copilot Business or Copilot Enterprise seat was canceled, and the user no longer has access to Copilot.

**Additional fields:** `seat_assignment`

#### `copilot.cfb_seat_cancelled_by_staff`

A user's Copilot Business or Copilot Enterprise seat was canceled manually by GitHub staff, and the user no longer has access to Copilot.

#### `copilot.swe_agent_repo_disabled`

Specific repositories were disabled from using Copilot coding agent.

**Additional fields:** `owner_type`, `owner`, `public_repo`

#### `copilot.swe_agent_repo_enabled`

Specific repositories were enabled to use Copilot coding agent.

**Additional fields:** `owner_type`, `owner`, `public_repo`

#### `copilot.swe_agent_repo_enablement_updated`

Copilot coding agent access was updated for the organization's or user's repositories.

**Additional fields:** `new_access`, `old_access`, `owner_type`, `owner`

### dependabot\_alerts

#### `dependabot_alerts.disable`

Dependabot alerts were disabled for all existing repositories.

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization#enabling-or-disabling-a-feature-for-all-existing-repositories

#### `dependabot_alerts.enable`

Dependabot alerts were enabled for all existing repositories.

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization#enabling-or-disabling-a-feature-for-all-existing-repositories

### dependabot\_alerts\_new\_repos

#### `dependabot_alerts_new_repos.disable`

Dependabot alerts were disabled for all new repositories.

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization#enabling-or-disabling-a-feature-automatically-when-new-repositories-are-added

#### `dependabot_alerts_new_repos.enable`

Dependabot alerts were enabled for all new repositories.

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization#enabling-or-disabling-a-feature-automatically-when-new-repositories-are-added

### dependabot\_closure\_request

#### `dependabot_closure_request.approve`

Dismissal of Dependabot alerts was approved.

**Additional fields:** `number`, `alert_number`, `public_repo`, `actor_is_bot`

**Reference:** [About Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

#### `dependabot_closure_request.cancel`

Dismissal request for Dependabot alerts was canceled.

**Additional fields:** `number`, `alert_number`, `public_repo`, `actor_is_bot`

**Reference:** [About Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

#### `dependabot_closure_request.create`

Dismissal of Dependabot alerts was requested.

**Additional fields:** `number`, `alert_number`, `public_repo`, `actor_is_bot`

**Reference:** [About Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

#### `dependabot_closure_request.deny`

Dismissal of Dependabot alerts was denied.

**Additional fields:** `number`, `alert_number`, `public_repo`, `actor_is_bot`

**Reference:** [About Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

### dependabot\_repository\_access

#### `dependabot_repository_access.repositories_updated`

The repositories that Dependabot can access were updated.

### dependabot\_security\_updates

#### `dependabot_security_updates.disable`

Dependabot security updates were disabled for all existing repositories.

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization

#### `dependabot_security_updates.enable`

Dependabot security updates were enabled for all existing repositories.

### dependabot\_security\_updates\_new\_repos

#### `dependabot_security_updates_new_repos.disable`

Dependabot security updates were disabled for all new repositories.

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization

#### `dependabot_security_updates_new_repos.enable`

Dependabot security updates were enabled for all new repositories.

### dependency\_graph

#### `dependency_graph.disable`

The dependency graph was disabled for all existing repositories.

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization

#### `dependency_graph.enable`

The dependency graph was enabled for all existing repositories.

### dependency\_graph\_new\_repos

#### `dependency_graph_new_repos.disable`

The dependency graph was disabled for all new repositories.

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization

#### `dependency_graph_new_repos.enable`

The dependency graph was enabled for all new repositories.

### environment

#### `environment.add_protection_rule`

A GitHub Actions deployment protection rule was created via the API.

**Additional fields:** `name`

**Reference:** [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#deployment-protection-rules)

#### `environment.create_actions_secret`

A secret was created for a GitHub Actions environment.

**Additional fields:** `oauth_application_id`, `key`, `visibility`, `public_repo`

**Reference:** [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#environment-secrets)

#### `environment.create_actions_variable`

A variable was created for a GitHub Actions environment.

**Additional fields:** `key`, `visibility`, `environment_name`, `public_repo`, `actor_is_bot`

**Reference:** [Store information in variables](/en/actions/learn-github-actions/variables#creating-configuration-variables-for-an-environment)

#### `environment.delete`

An environment was deleted.

**Additional fields:** `name`, `public_repo`, `actor_is_bot`

**Reference:** [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#deleting-an-environment)

#### `environment.remove_actions_secret`

A secret was deleted for a GitHub Actions environment.

**Additional fields:** `oauth_application_id`, `key`, `public_repo`

**Reference:** [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#environment-secrets)

#### `environment.remove_actions_variable`

A variable was deleted for a GitHub Actions environment.

**Additional fields:** `key`, `environment_name`, `public_repo`

**Reference:** [Store information in variables](/en/actions/learn-github-actions/variables#creating-configuration-variables-for-an-environment)

#### `environment.remove_protection_rule`

A GitHub Actions deployment protection rule was deleted via the API.

**Additional fields:** `name`, `public_repo`

**Reference:** [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#deployment-protection-rules)

#### `environment.update_actions_secret`

A secret was updated for a GitHub Actions environment.

**Additional fields:** `oauth_application_id`, `key`, `visibility`, `public_repo`

**Reference:** [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#environment-secrets)

#### `environment.update_actions_variable`

A variable was updated for a GitHub Actions environment.

**Additional fields:** `key`, `visibility`, `environment_name`, `public_repo`

**Reference:** [Store information in variables](/en/actions/learn-github-actions/variables#creating-configuration-variables-for-an-environment)

#### `environment.update_protection_rule`

A GitHub Actions deployment protection rule was updated via the API.

**Additional fields:** `new_value`, `approvers_was`, `approvers`, `can_admins_bypass`, `prevent_self_review`

**Reference:** [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#deployment-protection-rules)

### gist

#### `gist.create`

A gist was created.

**Additional fields:** `gist_id`, `visibility`

#### `gist.destroy`

A gist was deleted.

**Additional fields:** `gist_id`, `visibility`

#### `gist.visibility_change`

The visibility of a gist was updated.

**Additional fields:** `gist_id`, `visibility`

### git\_signing\_ssh\_public\_key

#### `git_signing_ssh_public_key.create`

An SSH key was added to a user account as a Git commit signing key.

**Additional fields:** `title`, `key`, `fingerprint`

**Reference:** /authentication/managing-commit-signature-verification/telling-git-about-your-signing-key

#### `git_signing_ssh_public_key.delete`

An SSH key was removed from a user account as a Git commit signing key.

**Additional fields:** `title`, `key`, `fingerprint`, `explanation`

**Reference:** /authentication/managing-commit-signature-verification/telling-git-about-your-signing-key

### hook

#### `hook.active_changed`

A hook's active status was updated.

**Additional fields:** `name`, `events`, `active`, `active_was`, `hook_id`

#### `hook.config_changed`

A hook's configuration was changed.

**Additional fields:** `name`, `hook_id`, `oauth_application_id`, `events`

#### `hook.create`

A new hook was added.

**Additional fields:** `oauth_application`, `oauth_application_id`, `hook_id`, `events`, `name`

**Reference:** [About webhooks](/en/get-started/exploring-integrations/about-webhooks)

#### `hook.destroy`

A hook was deleted.

**Additional fields:** `events`, `name`, `oauth_application_id`, `hook_id`

#### `hook.events_changed`

A hook's configured events were changed.

**Additional fields:** `events`, `name`, `events_were`, `hook_id`, `oauth_application_id`

### integration

#### `integration.create`

A GitHub App was created.

**Additional fields:** `name`, `integration`, `application_client_id`

#### `integration.destroy`

A GitHub App was deleted.

**Additional fields:** `name`, `integration`

#### `integration.manager_added`

A member of an enterprise or organization was added as a GitHub App manager.

**Additional fields:** `name`, `manager`, `integration`

**Reference:** /organizations/managing-programmatic-access-to-your-organization/adding-and-removing-github-app-managers-in-your-organization#giving-someone-the-ability-to-manage-all-github-apps-owned-by-the-organization

#### `integration.manager_removed`

A member of an enterprise or organization was removed from being a GitHub App manager.

**Additional fields:** `integration`, `name`, `manager`

**Reference:** /organizations/managing-programmatic-access-to-your-organization/adding-and-removing-github-app-managers-in-your-organization#removing-a-github-app-managers-permissions-for-the-entire-organization

#### `integration.remove_client_secret`

A client secret for a GitHub App was removed.

**Additional fields:** `name`, `integration`

#### `integration.revoke_all_tokens`

All user tokens for a GitHub App were requested to be revoked.

**Additional fields:** `name`, `integration`, `application_client_id`

#### `integration.revoke_tokens`

Token(s) for a GitHub App were revoked.

**Additional fields:** `name`, `integration`, `application_client_id`

#### `integration.suspend`

A GitHub App was suspended.

**Additional fields:** `name`, `integration`, `application_client_id`

**Reference:** /apps/maintaining-github-apps/suspending-a-github-app-installation

#### `integration.transfer`

Ownership of a GitHub App was transferred to another user or organization.

**Additional fields:** `name`, `transfer_to_id`, `requester`, `requester_id`, `transfer_to`, `integration`, `transfer_from`, `transfer_from_id`, `transfer_from_type`, `transfer_to_type`

**Reference:** /apps/maintaining-github-apps/transferring-ownership-of-a-github-app

#### `integration.unsuspend`

A GitHub App was unsuspended.

**Additional fields:** `name`, `integration`, `application_client_id`

**Reference:** /apps/maintaining-github-apps/suspending-a-github-app-installation

### integration\_installation

#### `integration_installation.create`

A GitHub App was installed.

**Additional fields:** `name`, `repository_selection`, `integration`, `application_client_id`

**Reference:** /apps/using-github-apps/authorizing-github-apps

#### `integration_installation.destroy`

A GitHub App was uninstalled.

**Additional fields:** `repository_selection`, `integration`, `name`, `application_client_id`

**Reference:** /apps/using-github-apps/reviewing-and-modifying-installed-github-apps#blocking-access

#### `integration_installation.repositories_added`

Repositories were added to a GitHub App.

**Additional fields:** `repository_selection`, `name`, `integration`, `repositories_added`, `repositories_added_names`, `actor_is_bot`, `application_client_id`

**Reference:** /apps/using-github-apps/reviewing-and-modifying-installed-github-apps#modifying-repository-access

#### `integration_installation.repositories_removed`

Repositories were removed from a GitHub App.

**Additional fields:** `repository_selection`, `repositories_removed`, `integration`, `name`, `repositories_removed_names`, `actor_is_bot`, `application_client_id`

**Reference:** /apps/using-github-apps/reviewing-and-modifying-installed-github-apps#modifying-repository-access

#### `integration_installation.suspend`

A GitHub App was suspended.

**Additional fields:** `name`, `repository_selection`, `integration`, `application_client_id`

**Reference:** /apps/using-github-apps/reviewing-and-modifying-installed-github-apps#blocking-access

#### `integration_installation.unsuspend`

A GitHub App was unsuspended.

**Additional fields:** `name`, `repository_selection`, `integration`

**Reference:** /apps/using-github-apps/reviewing-and-modifying-installed-github-apps#blocking-access

#### `integration_installation.version_updated`

Permissions for a GitHub App were updated.

**Additional fields:** `integration`, `name`, `repository_selection`, `application_client_id`

**Reference:** /apps/using-github-apps/approving-updated-permissions-for-a-github-app

### issue\_dependencies

#### `issue_dependencies.blocked_by_add`

An issue was marked as blocked by another issue.

**Additional fields:** `title`, `public_repo`, `actor_is_bot`

#### `issue_dependencies.blocked_by_remove`

The blocked by relationship between an issue and another issue was removed.

**Additional fields:** `title`, `public_repo`

#### `issue_dependencies.blocking_add`

An issue was marked as blocking another issue.

**Additional fields:** `title`, `public_repo`, `actor_is_bot`

#### `issue_dependencies.blocking_remove`

The blocking relationship between an issue and another issue was removed.

**Additional fields:** `title`, `public_repo`, `actor_is_bot`

### marketplace\_agreement\_signature

#### `marketplace_agreement_signature.create`

The GitHub Marketplace Developer Agreement was signed.

### marketplace\_listing

#### `marketplace_listing.approve`

A listing was approved for inclusion in GitHub Marketplace.

**Additional fields:** `secondary_category`, `primary_category`, `marketplace_listing`, `integration`

#### `marketplace_listing.change_category`

A category for a listing for an app in GitHub Marketplace was changed.

**Additional fields:** `primary_category`, `marketplace_listing`, `integration`, `secondary_category`

#### `marketplace_listing.create`

A listing for an app in GitHub Marketplace was created.

**Additional fields:** `primary_category`, `oauth_application`, `marketplace_listing`, `secondary_category`, `oauth_application_id`

#### `marketplace_listing.delist`

A listing was removed from GitHub Marketplace.

**Additional fields:** `secondary_category`, `marketplace_listing`, `primary_category`, `integration`

#### `marketplace_listing.redraft`

A listing was sent back to draft state.

**Additional fields:** `secondary_category`, `oauth_application_id`, `oauth_application`, `marketplace_listing`, `primary_category`

#### `marketplace_listing.reject`

A listing was not accepted for inclusion in GitHub Marketplace.

**Additional fields:** `primary_category`, `secondary_category`, `marketplace_listing`, `oauth_application`, `oauth_application_id`

### merge\_queue

#### `merge_queue.pull_request_dequeued`

A pull request was removed from a merge queue.

**Additional fields:** `public_repo`

#### `merge_queue.pull_request_queue_jump`

A pull request was moved ahead in a merge queue.

**Additional fields:** `oauth_application_id`, `public_repo`

#### `merge_queue.queue_cleared`

A merge queue was cleared.

**Additional fields:** `public_repo`

#### `merge_queue.update_settings`

The settings for a merge queue were updated.

**Additional fields:** `max_entries_to_build`, `min_entries_to_merge`, `public_repo`

### migration

#### `migration.create`

A migration file was created for transferring data from a source location (such as a GitHub.com organization or a GitHub Enterprise Server instance) to a target GitHub Enterprise Server instance.

**Additional fields:** `actor_is_bot`

### oauth\_access

#### `oauth_access.create`

An OAuth access token was generated.

**Additional fields:** `oauth_application_name`

**Reference:** /apps/oauth-apps/building-oauth-apps/authorizing-oauth-apps, [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

#### `oauth_access.destroy`

An OAuth access token was deleted.

**Additional fields:** `explanation`, `oauth_application_name`

**Reference:** /apps/oauth-apps/building-oauth-apps/authorizing-oauth-apps

#### `oauth_access.regenerate`

An OAuth access token was regenerated.

**Additional fields:** `oauth_application_name`

#### `oauth_access.revoke`

An OAuth access token was revoked.

#### `oauth_access.update`

An OAuth access token was updated.

### oauth\_application

#### `oauth_application.create`

An OAuth application was created.

**Additional fields:** `oauth_application_id`, `oauth_application`

**Reference:** /apps/oauth-apps/building-oauth-apps/authenticating-to-the-rest-api-with-an-oauth-app#registering-your-app

#### `oauth_application.destroy`

An OAuth application was deleted.

**Additional fields:** `oauth_application_id`, `oauth_application`

**Reference:** /apps/oauth-apps/building-oauth-apps/authenticating-to-the-rest-api-with-an-oauth-app#registering-your-app

#### `oauth_application.generate_client_secret`

An OAuth application's secret key was generated.

**Additional fields:** `oauth_application`, `oauth_application_id`

**Reference:** /apps/oauth-apps/building-oauth-apps/authenticating-to-the-rest-api-with-an-oauth-app#registering-your-app

#### `oauth_application.remove_client_secret`

An OAuth application's secret key was deleted.

**Additional fields:** `oauth_application`, `oauth_application_id`

**Reference:** /apps/oauth-apps/building-oauth-apps/authenticating-to-the-rest-api-with-an-oauth-app#registering-your-app

#### `oauth_application.reset_secret`

The secret key for an OAuth application was reset.

**Additional fields:** `oauth_application`, `oauth_application_id`

**Reference:** /apps/oauth-apps/building-oauth-apps/authenticating-to-the-rest-api-with-an-oauth-app#registering-your-app

#### `oauth_application.revoke_all_tokens`

All user tokens for an OAuth application were requested to be revoked.

**Additional fields:** `oauth_application`, `oauth_application_id`

**Reference:** /apps/oauth-apps/building-oauth-apps/authenticating-to-the-rest-api-with-an-oauth-app#registering-your-app

#### `oauth_application.revoke_tokens`

Token(s) for an OAuth application were revoked.

**Additional fields:** `oauth_application_id`, `oauth_application`

**Reference:** /apps/oauth-apps/building-oauth-apps/authenticating-to-the-rest-api-with-an-oauth-app#registering-your-app

#### `oauth_application.transfer`

An OAuth application was transferred from one account to another.

**Additional fields:** `oauth_application`, `oauth_application_id`

**Reference:** /apps/oauth-apps/building-oauth-apps/authenticating-to-the-rest-api-with-an-oauth-app#registering-your-app

### oauth\_authorization

#### `oauth_authorization.create`

An authorization for an OAuth application was created.

**Additional fields:** `actor_is_bot`, `oauth_application_name`

**Reference:** /apps/oauth-apps/using-oauth-apps/authorizing-oauth-apps

#### `oauth_authorization.destroy`

An authorization for an OAuth application was deleted.

**Additional fields:** `explanation`, `actor_is_bot`, `oauth_application_name`

**Reference:** [Reviewing and revoking authorization of GitHub Apps](/en/apps/using-github-apps/reviewing-your-authorized-integrations)

#### `oauth_authorization.update`

An authorization for an OAuth application was updated.

**Additional fields:** `actor_is_bot`, `oauth_application_name`

**Reference:** /apps/oauth-apps/using-oauth-apps/authorizing-oauth-apps

### org

#### `org.add_member`

A user joined an organization.

**Additional fields:** `permission`, `actor_is_bot`

#### `org.add_outside_collaborator`

An outside collaborator was added to a repository.

**Additional fields:** `inviter`, `public_repo`, `permission`, `invitee`

#### `org.advanced_security_disabled_for_new_repos`

GitHub Advanced Security was disabled for new repositories in an organization.

#### `org.advanced_security_disabled_on_all_repos`

GitHub Advanced Security was disabled for all repositories in an organization.

#### `org.advanced_security_enabled_for_new_repos`

GitHub Advanced Security was enabled for new repositories in an organization.

#### `org.advanced_security_enabled_on_all_repos`

GitHub Advanced Security was enabled for all repositories in an organization.

#### `org.remove_member`

A member was removed from an organization, either manually or due to a two-factor authentication requirement.

#### `org.security_center_export_code_scanning_metrics`

A CSV export was requested on the CodeQL pull request alerts page.

**Additional fields:** `query`, `filename`, `requested_at`, `start_date`, `end_date`, `actor_is_bot`

#### `org.security_center_export_coverage`

A CSV export was requested on the Coverage page.

**Additional fields:** `query`, `filename`, `requested_at`, `actor_is_bot`

#### `org.security_center_export_overview_dashboard`

A CSV export was requested on the Overview Dashboard page.

**Additional fields:** `query`, `filename`, `requested_at`, `start_date`, `end_date`, `actor_is_bot`

#### `org.security_center_export_risk`

A CSV export was requested on the Risk page.

**Additional fields:** `query`, `filename`, `requested_at`, `actor_is_bot`

#### `org.set_actions_cache_retention_policy`

The cache retention policy for GitHub Actions was set for an organization.

**Additional fields:** `actor_is_bot`

**Reference:** /organizations/managing-organization-settings/managing-github-actions-settings-for-your-organization

#### `org.set_actions_cache_storage_policy`

The cache storage policy for GitHub Actions was set for an organization.

**Additional fields:** `actor_is_bot`

**Reference:** /organizations/managing-organization-settings/managing-github-actions-settings-for-your-organization

#### `org.set_actions_fork_pr_approvals_policy`

The setting for requiring approvals for workflows from public forks was changed for an organization.

**Additional fields:** `policy`

**Reference:** /organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#requiring-approval-for-workflows-from-public-forks

#### `org.set_actions_private_fork_pr_approvals_policy`

The policy for requiring approval for fork pull request workflows from collaborators without write access to private repos was changed for an organization.

**Additional fields:** `policy`

**Reference:** /organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#enabling-workflows-for-private-repository-forks

#### `org.set_actions_retention_limit`

The retention period for GitHub Actions artifacts and logs in an organization was changed.

**Additional fields:** `limit`

**Reference:** /organizations/managing-organization-settings/configuring-the-retention-period-for-github-actions-artifacts-and-logs-in-your-organization

#### `org.set_default_workflow_permissions`

The default permissions granted to the GITHUB\_TOKEN when running workflows were changed for an organization.

**Reference:** /organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#setting-the-permissions-of-the-github\_token-for-your-organization

#### `org.set_fork_pr_workflows_policy`

The policy for workflows on private repository forks was changed.

**Additional fields:** `policy`

**Reference:** /organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#enabling-workflows-for-private-repository-forks

#### `org.set_workflow_permission_can_approve_pr`

The policy for allowing GitHub Actions to create and approve pull requests was changed for an organization.

**Reference:** /organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#preventing-github-actions-from-creating-or-approving-pull-requests

#### `org.update_member`

A person's role was changed from owner to member or member to owner.

**Additional fields:** `old_permission`, `permission`

#### `org.update_member_repository_creation_permission`

The create repository permission for organization members was changed.

**Additional fields:** `permission`, `visibility`

#### `org.update_member_repository_invitation_permission`

An organization owner changed the policy setting for organization members inviting outside collaborators to repositories.

**Additional fields:** `permission`

**Reference:** [Setting permissions for adding outside collaborators](/en/organizations/managing-organization-settings/setting-permissions-for-adding-outside-collaborators)

### pages\_protected\_domain

#### `pages_protected_domain.create`

A GitHub Pages verified domain was created for an organization or enterprise.

**Additional fields:** `owner`, `owner_type`, `domain`, `state`

**Reference:** /pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages

#### `pages_protected_domain.delete`

A GitHub Pages verified domain was deleted from an organization or enterprise.

**Additional fields:** `owner`, `owner_type`, `domain`, `state`

**Reference:** /pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages

#### `pages_protected_domain.verify`

A GitHub Pages domain was verified for an organization or enterprise.

**Additional fields:** `owner`, `owner_type`, `domain`, `state`

**Reference:** /pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages

### passkey

#### `passkey.register`

A new passkey was added.

**Additional fields:** `nickname`

#### `passkey.remove`

A new passkey was removed.

**Additional fields:** `nickname`

### payment\_method

#### `payment_method.create`

A new payment method was added, such as a new credit card or PayPal account.

#### `payment_method.remove`

A payment method was removed.

#### `payment_method.update`

An existing payment method was updated.

### personal\_access\_token

#### `personal_access_token.access_granted`

A fine-grained personal access token was granted access to resources.

**Additional fields:** `user_programmatic_access_id`, `user_programmatic_access_name`, `repository_selection`

**Reference:** /organizations/managing-programmatic-access-to-your-organization/managing-requests-for-personal-access-tokens-in-your-organization

#### `personal_access_token.access_revoked`

A fine-grained personal access token was revoked. The token can still read public organization resources.

**Additional fields:** `user_programmatic_access_id`, `user_programmatic_access_name`, `repository_selection`

**Reference:** /organizations/managing-programmatic-access-to-your-organization/reviewing-and-revoking-personal-access-tokens-in-your-organization

#### `personal_access_token.create`

Triggered when you create a fine-grained personal access token.

**Additional fields:** `user_programmatic_access_name`, `repository_selection`

#### `personal_access_token.credential_regenerated`

Triggered when you regenerate a fine-grained personal access token.

**Additional fields:** `user_programmatic_access_name`

#### `personal_access_token.credential_revoked`

A fine-grained personal access token was revoked by GitHub Advanced Security.

**Additional fields:** `user_programmatic_access_name`

**Reference:** /code-security/getting-started/github-security-features#secret-scanning-alerts-for-users

#### `personal_access_token.destroy`

Triggered when you delete a fine-grained personal access token.

**Additional fields:** `user_programmatic_access_name`, `explanation`

#### `personal_access_token.request_cancelled`

A pending request for a fine-grained personal access token to access organization resources was canceled.

**Additional fields:** `user_programmatic_access_name`, `repository_selection`, `user_programmatic_access_request_id`

#### `personal_access_token.request_created`

Triggered when a fine-grained personal access token was created to access organization resources and the organization requires approval before the token can access organization resources.

**Additional fields:** `user_programmatic_access_id`, `user_programmatic_access_name`, `repository_selection`, `user_programmatic_access_request_id`

**Reference:** /organizations/managing-programmatic-access-to-your-organization/managing-requests-for-personal-access-tokens-in-your-organization

#### `personal_access_token.request_denied`

A request for a fine-grained personal access token to access organization resources was denied.

**Additional fields:** `user_programmatic_access_name`, `repository_selection`, `user_programmatic_access_request_id`

**Reference:** /organizations/managing-programmatic-access-to-your-organization/managing-requests-for-personal-access-tokens-in-your-organization

#### `personal_access_token.update`

A fine-grained personal access token was updated.

**Additional fields:** `user_programmatic_access_name`, `repository_selection`

**Reference:** /authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#fine-grained-personal-access-tokens

### profile\_picture

#### `profile_picture.update`

A profile picture was updated.

**Additional fields:** `owner`

**Reference:** [Personalize your profile](/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile)

### project

#### `project.access`

A project board visibility was changed.

#### `project.close`

A project board was closed.

**Additional fields:** `project_id`, `project_kind`

**Reference:** [Closing a project (classic)](/en/issues/organizing-your-work-with-project-boards/managing-project-boards/closing-a-project-board)

#### `project.create`

A project board was created.

#### `project.delete`

A project board was deleted.

#### `project.link`

A repository was linked to a project board.

#### `project.open`

A project board was reopened.

**Additional fields:** `project_id`, `project_kind`, `project_name`

**Reference:** [Reopening a closed project (classic)](/en/issues/organizing-your-work-with-project-boards/managing-project-boards/reopening-a-closed-project-board)

#### `project.rename`

A project board was renamed.

**Additional fields:** `old_name`

#### `project.unlink`

A repository was unlinked from a project board.

#### `project.update_org_permission`

The project's base-level permission for all organization members was changed or removed.

#### `project.update_team_permission`

A team's project board permission level was changed or when a team was added or removed from a project board.

**Additional fields:** `team`

#### `project.update_user_permission`

A user was added to or removed from a project board or had their permission level changed.

#### `project.visibility_private`

A project's visibility was changed from public to private.

**Additional fields:** `project_id`, `project_kind`, `project_name`

#### `project.visibility_public`

A project's visibility was changed from private to public.

**Additional fields:** `project_id`, `project_kind`, `project_name`

### project\_collaborator

#### `project_collaborator.add`

A collaborator was added to a project.

**Additional fields:** `collaborator_type`, `collaborator`, `actor_is_bot`, `public_project`, `project_name`, `project_role`, `old_project_role`

#### `project_collaborator.remove`

A collaborator was removed from a project.

**Additional fields:** `collaborator_type`, `collaborator`

#### `project_collaborator.update`

A project collaborator's permission level was changed.

**Additional fields:** `public_project`, `project_name`, `collaborator_type`, `project_role`, `old_project_role`, `project_id`, `collaborator`

### project\_field

#### `project_field.create`

A field was created in a project board.

**Reference:** /issues/planning-and-tracking-with-projects/understanding-fields

#### `project_field.delete`

A field was deleted in a project board.

**Reference:** /issues/planning-and-tracking-with-projects/understanding-fields/deleting-custom-fields

### project\_view

#### `project_view.create`

A view was created in a project board.

**Reference:** /issues/planning-and-tracking-with-projects/customizing-views-in-your-project/managing-your-views

#### `project_view.delete`

A view was deleted in a project board.

**Reference:** /issues/planning-and-tracking-with-projects/customizing-views-in-your-project/managing-your-views

### protected\_branch

#### `protected_branch.update_merge_queue_enforcement_level`

Enforcement of the merge queue was modified for a branch.

**Additional fields:** `name`, `merge_queue_enforcement_level`, `public_repo`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-merge-queue

### public\_key

#### `public_key.create`

An SSH key was added to a user account or a deploy key was added to a repository.

**Additional fields:** `read_only`, `key`, `fingerprint`, `title`

**Reference:** /authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

#### `public_key.delete`

An SSH key was removed from a user account or a deploy key was removed from a repository.

**Additional fields:** `fingerprint`, `read_only`, `explanation`, `key`, `title`

**Reference:** /authentication/keeping-your-account-and-data-secure/reviewing-your-ssh-keys

#### `public_key.unverification_failure`

A user account's SSH key or a repository's deploy key was unable to be unverified.

**Additional fields:** `title`, `key`, `fingerprint`, `read_only`

**Reference:** /authentication/connecting-to-github-with-ssh/managing-deploy-keys#deploy-keys

#### `public_key.unverify`

A user account's SSH key or a repository's deploy key was unverified.

**Additional fields:** `title`, `key`, `read_only`, `explanation`, `fingerprint`

**Reference:** /authentication/connecting-to-github-with-ssh/managing-deploy-keys#deploy-keys

#### `public_key.update`

A user account's SSH key or a repository's deploy key was updated.

**Additional fields:** `key`, `fingerprint`, `read_only`, `title`

**Reference:** /authentication/connecting-to-github-with-ssh/managing-deploy-keys#deploy-keys

#### `public_key.verification_failure`

A user account's SSH key or a repository's deploy key was unable to be verified.

**Additional fields:** `key`, `fingerprint`, `oauth_application_id`, `title`, `read_only`

**Reference:** /authentication/connecting-to-github-with-ssh/managing-deploy-keys#deploy-keys

#### `public_key.verify`

A user account's SSH key or a repository's deploy key was verified.

**Additional fields:** `key`, `fingerprint`, `title`, `read_only`

**Reference:** /authentication/connecting-to-github-with-ssh/managing-deploy-keys#deploy-keys

### repo

#### `repo.access`

The visibility of a repository changed.

**Additional fields:** `visibility`, `previous_visibility`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility

#### `repo.actions_enabled`

GitHub Actions was enabled for a repository.

**Reference:** organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/reviewing-the-audit-log-for-your-organization#using-the-audit-log-api

#### `repo.add_member`

A collaborator was added to a repository.

**Additional fields:** `visibility`, `oauth_application_id`

**Reference:** [Inviting collaborators to a personal repository](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository)

#### `repo.add_topic`

A topic was added to a repository.

**Additional fields:** `topic`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/classifying-your-repository-with-topics

#### `repo.advanced_security_disabled`

GitHub Advanced Security was disabled for a repository.

**Additional fields:** `actor_is_bot`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository

#### `repo.advanced_security_enabled`

GitHub Advanced Security was enabled for a repository.

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository

#### `repo.archived`

A repository was archived.

**Additional fields:** `visibility`

**Reference:** /repositories/archiving-a-github-repository

#### `repo.change_merge_setting`

Pull request merge options were changed for a repository.

**Additional fields:** `oauth_application_id`, `public_repo`, `actor_is_bot`

#### `repo.code_scanning_analysis_deleted`

Code scanning analysis for a repository was deleted.

**Additional fields:** `oauth_application_id`, `public_repo`, `tool`, `category`

**Reference:** /rest/code-scanning#delete-a-code-scanning-analysis-from-a-repository

#### `repo.code_scanning_configuration_for_branch_deleted`

A code scanning configuration for a branch of a repository was deleted.

**Additional fields:** `tool`, `branch`, `category`, `public_repo`

**Reference:** [Resolving code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/managing-code-scanning-alerts-for-your-repository#removing-stale-configurations-and-alerts-from-a-branch)

#### `repo.config.disable_collaborators_only`

The interaction limit for collaborators only was disabled.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-repository

#### `repo.config.disable_contributors_only`

The interaction limit for prior contributors only was disabled in a repository.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-repository

#### `repo.config.disable_sockpuppet_disallowed`

The interaction limit for existing users only was disabled in a repository.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-repository

#### `repo.config.enable_collaborators_only`

The interaction limit for collaborators only was enabled in a repository  Users that are not collaborators or organization members were unable to interact with a repository for a set duration.

**Additional fields:** `oauth_application_id`

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-repository

#### `repo.config.enable_contributors_only`

The interaction limit for prior contributors only was enabled in a repository  Users that are not prior contributors, collaborators or organization members were unable to interact with a repository for a set duration.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-repository

#### `repo.config.enable_sockpuppet_disallowed`

The interaction limit for existing users was enabled in a repository  New users aren't able to interact with a repository for a set duration  Existing users of the repository, contributors, collaborators or organization members are able to interact with a repository.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-repository

#### `repo.configure_self_hosted_jit_runner`

A new just-in-time GitHub Actions self-hosted runner was configured

**Additional fields:** `oauth_application_id`, `public_repo`

**Reference:** /rest/actions/self-hosted-runners#create-configuration-for-a-just-in-time-runner-for-a-repository

#### `repo.create`

A repository was created.

**Additional fields:** `visibility`, `request_category`, `oauth_application_id`, `request_method`, `public_repo`, `actor_is_bot`

**Reference:** /repositories/creating-and-managing-repositories/creating-a-new-repository

#### `repo.create_actions_secret`

A GitHub Actions secret was created for a repository.

**Additional fields:** `key`

**Reference:** [Using secrets in GitHub Actions](/en/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository)

#### `repo.create_actions_variable`

A GitHub Actions variable was created for a repository.

**Additional fields:** `key`, `visibility`, `public_repo`

**Reference:** [Store information in variables](/en/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository)

#### `repo.create_integration_secret`

A Codespaces or Dependabot secret was created for a repository.

**Additional fields:** `key`, `visibility`, `integration`, `public_repo`

#### `repo.destroy`

A repository was deleted.

**Additional fields:** `request_category`, `visibility`, `request_method`, `oauth_application_id`, `actor_is_bot`

**Reference:** /repositories/creating-and-managing-repositories/deleting-a-repository

#### `repo.pages_cname`

A GitHub Pages custom domain was modified in a repository.

**Additional fields:** `visibility`, `cname`, `old_cname`

#### `repo.pages_create`

A GitHub Pages site was created.

**Additional fields:** `visibility`

#### `repo.pages_destroy`

A GitHub Pages site was deleted.

**Additional fields:** `visibility`

#### `repo.pages_https_redirect_disabled`

HTTPS redirects were disabled for a GitHub Pages site.

**Additional fields:** `visibility`

#### `repo.pages_https_redirect_enabled`

HTTPS redirects were enabled for a GitHub Pages site.

**Additional fields:** `visibility`

#### `repo.pages_private`

A GitHub Pages site visibility was changed to private.

**Additional fields:** `visibility`

#### `repo.pages_public`

A GitHub Pages site visibility was changed to public.

**Additional fields:** `visibility`

#### `repo.pages_soft_delete`

A GitHub Pages site was soft-deleted because its owner's plan changed.

**Additional fields:** `visibility`, `public_repo`

#### `repo.pages_soft_delete_restore`

A GitHub Pages site that was previously soft-deleted was restored.

**Additional fields:** `visibility`, `public_repo`

#### `repo.pages_source`

A GitHub Pages source was modified.

**Additional fields:** `visibility`

#### `repo.register_self_hosted_runner`

A new self-hosted runner was registered.

**Reference:** [Adding self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners#adding-a-self-hosted-runner-to-a-repository)

#### `repo.remove_actions_secret`

A GitHub Actions secret was deleted for a repository.

**Additional fields:** `key`

**Reference:** [Using secrets in GitHub Actions](/en/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository)

#### `repo.remove_actions_variable`

A GitHub Actions variable was deleted for a repository.

**Additional fields:** `key`, `public_repo`

**Reference:** [Store information in variables](/en/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository)

#### `repo.remove_integration_secret`

A Codespaces or Dependabot secret was deleted for a repository.

**Additional fields:** `key`, `integration`, `public_repo`

#### `repo.remove_member`

A collaborator was removed from a repository.

**Additional fields:** `visibility`

**Reference:** [Removing a collaborator from a personal repository](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/removing-a-collaborator-from-a-personal-repository)

#### `repo.remove_self_hosted_runner`

A self-hosted runner was removed.

**Reference:** [Removing self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/removing-self-hosted-runners#removing-a-runner-from-a-repository)

#### `repo.remove_topic`

A topic was removed from a repository.

**Additional fields:** `topic`

#### `repo.rename`

A repository was renamed.

**Additional fields:** `old_name`, `visibility`

**Reference:** /repositories/creating-and-managing-repositories/renaming-a-repository

#### `repo.set_actions_cache_retention_policy`

The cache retention policy for GitHub Actions was set for a repository.

**Additional fields:** `visibility`, `public_repo`, `actor_is_bot`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository

#### `repo.set_actions_cache_storage_policy`

The cache storage policy for GitHub Actions was set for a repository.

**Additional fields:** `visibility`, `public_repo`, `actor_is_bot`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository

#### `repo.set_actions_fork_pr_approvals_policy`

The setting for requiring approvals for workflows from public forks was changed for a repository.

**Additional fields:** `visibility`, `policy`, `public_repo`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#configuring-required-approval-for-workflows-from-public-forks

#### `repo.set_actions_private_fork_pr_approvals_policy`

The policy for requiring approval for fork pull request workflows from collaborators without write access to private repos was changed for a repository.

**Additional fields:** `visibility`, `policy`, `public_repo`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#enabling-workflows-for-forks-of-private-repositories

#### `repo.set_actions_retention_limit`

The retention period for GitHub Actions artifacts and logs in a repository was changed.

**Additional fields:** `visibility`, `limit`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#configuring-the-retention-period-for-github-actions-artifacts-and-logs-in-your-repository

#### `repo.set_default_workflow_permissions`

The default permissions granted to the GITHUB\_TOKEN when running workflows were changed for a repository.

**Additional fields:** `visibility`, `public_repo`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#setting-the-permissions-of-the-github\_token-for-your-repository

#### `repo.set_fork_pr_workflows_policy`

Triggered when the policy for workflows on private repository forks is changed.

**Additional fields:** `visibility`, `policy`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#enabling-workflows-for-private-repository-forks

#### `repo.set_workflow_permission_can_approve_pr`

The policy for allowing GitHub Actions to create and approve pull requests was changed for a repository.

**Additional fields:** `visibility`, `public_repo`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#preventing-github-actions-from-creating-or-approving-pull-requests

#### `repo.staff_unlock`

An enterprise owner or GitHub staff (with permission from a repository administrator) temporarily unlocked the repository.

#### `repo.temporary_access_granted`

Temporary access was enabled for a repository.

**Additional fields:** `public_repo`

**Reference:** [Accessing user-owned repositories in your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-repositories-in-your-enterprise/accessing-user-owned-repositories-in-your-enterprise)

#### `repo.transfer`

A user accepted a request to receive a transferred repository.

**Additional fields:** `owner`, `old_user`, `visibility`, `repo_was`

**Reference:** /repositories/creating-and-managing-repositories/transferring-a-repository

#### `repo.transfer_outgoing`

A repository was transferred to another repository network.

**Additional fields:** `new_nwo`, `visibility`, `public_repo`

#### `repo.transfer_start`

A user sent a request to transfer a repository to another user or organization.

**Additional fields:** `visibility`

#### `repo.unarchived`

A repository was unarchived.

**Additional fields:** `visibility`

**Reference:** /repositories/archiving-a-github-repository

#### `repo.update_actions_access_settings`

The setting to control how a repository was used by GitHub Actions workflows in other repositories was changed.

**Additional fields:** `visibility`, `policy`, `old_policy`

#### `repo.update_actions_secret`

A GitHub Actions secret was updated for a repository.

**Additional fields:** `oauth_application_id`, `key`

**Reference:** [Using secrets in GitHub Actions](/en/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository)

#### `repo.update_actions_settings`

A repository administrator changed GitHub Actions policy settings for a repository.

**Additional fields:** `visibility`, `new_policy`, `old_policy`, `updated_access_policy`, `actor_is_bot`

#### `repo.update_actions_variable`

A GitHub Actions variable was updated for a repository.

**Additional fields:** `key`, `visibility`, `public_repo`

**Reference:** [Store information in variables](/en/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository)

#### `repo.update_default_branch`

The default branch for a repository was changed.

**Additional fields:** `visibility`, `actor_is_bot`

#### `repo.update_integration_secret`

A Codespaces or Dependabot secret was updated for a repository.

**Additional fields:** `key`, `visibility`, `integration`, `public_repo`

#### `repo.update_member`

A user's permission to a repository was changed.

**Additional fields:** `oauth_application_id`, `visibility`, `old_permission`, `old_base_role`, `old_repo_permission`, `old_repo_base_role`, `new_repo_base_role`, `new_repo_permission`, `actor_is_bot`

### repository\_image

#### `repository_image.create`

An image to represent a repository was uploaded.

**Additional fields:** `content_type`

#### `repository_image.destroy`

An image to represent a repository was deleted.

**Additional fields:** `content_type`

### repository\_invitation

#### `repository_invitation.accept`

An invitation to join a repository was accepted.

**Additional fields:** `invitee`, `inviter`

#### `repository_invitation.cancel`

An invitation to join a repository was canceled.

**Additional fields:** `inviter`, `invitee`

#### `repository_invitation.create`

An invitation to join a repository was sent.

**Additional fields:** `invitee`, `inviter`

#### `repository_invitation.reject`

An invitation to join a repository was declined.

**Additional fields:** `invitee`, `inviter`

### repository\_ruleset

#### `repository_ruleset.create`

A repository ruleset was created.

**Additional fields:** `name`, `public_repo`, `ruleset_id`, `ruleset_name`, `ruleset_enforcement`, `ruleset_source_type`, `ruleset_rules`, `ruleset_conditions`, `ruleset_bypass_actors`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/creating-rulesets-for-a-repository

#### `repository_ruleset.destroy`

A repository ruleset was deleted.

**Additional fields:** `name`, `public_repo`, `ruleset_id`, `ruleset_name`, `ruleset_enforcement`, `ruleset_source_type`, `ruleset_rules`, `ruleset_bypass_actors`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository#deleting-a-ruleset

#### `repository_ruleset.update`

A repository ruleset was edited.

**Additional fields:** `old_name`, `public_repo`, `ruleset_id`, `ruleset_name`, `ruleset_enforcement`, `ruleset_source_type`, `ruleset_rules_updated`, `ruleset_conditions_added`, `ruleset_conditions_deleted`, `ruleset_old_enforcement`, `ruleset_rules_added`, `ruleset_rules_deleted`, `ruleset_old_name`, `ruleset_conditions_updated`, `ruleset_bypass_actors_added`, `ruleset_bypass_actors_deleted`, `ruleset_bypass_actors_updated`, `actor_is_bot`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository#editing-a-ruleset

### security\_key

#### `security_key.register`

A security key was registered for an account.

#### `security_key.remove`

A security key was removed from an account.

### social\_identity

#### `social_identity.linked`

A user linked a social identity to their account.

#### `social_identity.unlinked`

A user unlinked a social identity from their account.

#### `social_identity.unlinked_all`

A user unlinked all social identities from their account.

### sponsors

#### `sponsors.agreement_sign`

A GitHub Sponsors agreement was signed on behalf of an organization.

**Additional fields:** `sponsors_listing_id`

#### `sponsors.custom_amount_settings_change`

Custom amounts for GitHub Sponsors were enabled or disabled, or the suggested custom amount was changed.

**Additional fields:** `sponsors_listing_id`

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/managing-your-sponsorship-tiers

#### `sponsors.fiscal_host_change`

The fiscal host for a GitHub Sponsors listing was updated.

**Additional fields:** `sponsors_listing_id`

#### `sponsors.repo_funding_links_file_action`

The FUNDING file in a repository was changed.

**Reference:** /repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/displaying-a-sponsor-button-in-your-repository

#### `sponsors.sponsor_sponsorship_cancel`

A sponsorship was canceled.

**Reference:** [Downgrading a sponsorship](/en/billing/managing-billing-for-github-sponsors/downgrading-a-sponsorship)

#### `sponsors.sponsor_sponsorship_create`

A sponsorship was created, by sponsoring an account.

**Reference:** /sponsors/sponsoring-open-source-contributors/about-sponsorships-fees-and-taxes

#### `sponsors.sponsor_sponsorship_payment_complete`

After you sponsor an account and a payment has been processed, the sponsorship payment was marked as complete.

**Additional fields:** `active`

**Reference:** /sponsors/sponsoring-open-source-contributors/about-sponsorships-fees-and-taxes

#### `sponsors.sponsor_sponsorship_preference_change`

The option to receive email updates from a sponsored account was changed.

**Reference:** /sponsors/sponsoring-open-source-contributors/managing-your-sponsorship

#### `sponsors.sponsor_sponsorship_tier_change`

A sponsorship was upgraded or downgraded.

**Reference:** [Upgrading a sponsorship](/en/billing/managing-billing-for-github-sponsors/upgrading-a-sponsorship), [Downgrading a sponsorship](/en/billing/managing-billing-for-github-sponsors/downgrading-a-sponsorship)

#### `sponsors.sponsored_developer_approve`

A GitHub Sponsors account was approved.

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-personal-account

#### `sponsors.sponsored_developer_create`

A GitHub Sponsors account was created.

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-personal-account

#### `sponsors.sponsored_developer_disable`

A GitHub Sponsors account was disabled.

**Additional fields:** `sponsors_listing_id`

#### `sponsors.sponsored_developer_profile_update`

The profile for GitHub Sponsors account was edited.

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/editing-your-profile-details-for-github-sponsors

#### `sponsors.sponsored_developer_redraft`

A GitHub Sponsors account was returned to draft state from approved state.

#### `sponsors.sponsored_developer_request_approval`

An application for GitHub Sponsors was submitted for approval.

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-personal-account

#### `sponsors.sponsored_developer_tier_description_update`

The description for a sponsorship tier was changed.

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/managing-your-sponsorship-tiers

#### `sponsors.sponsored_developer_update_newsletter_send`

Triggered when you send an email update to your sponsors.

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/contacting-your-sponsors

#### `sponsors.sponsors_patreon_user_create`

A Patreon account was linked to a user account for use with GitHub Sponsors.

**Additional fields:** `patreon_email`, `patreon_username`

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/enabling-sponsorships-through-patreon#linking-your-patreon-account-to-your-github-account

#### `sponsors.sponsors_patreon_user_destroy`

A Patreon account for use with GitHub Sponsors was unlinked from a user account.

**Additional fields:** `patreon_email`, `patreon_username`

**Reference:** [Unlinking your Patreon account from GitHub](/en/sponsors/sponsoring-open-source-contributors/unlinking-your-patreon-account-from-your-github-account)

#### `sponsors.update_tier_repository`

A GitHub Sponsors tier changed access for a repository.

**Additional fields:** `sponsors_listing_id`

#### `sponsors.update_tier_welcome_message`

The welcome message for a GitHub Sponsors tier for an organization was updated.

**Additional fields:** `sponsors_listing_id`

#### `sponsors.waitlist_join`

You join the waitlist to join GitHub Sponsors.

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-personal-account

#### `sponsors.withdraw_agreement_signature`

A signature was withdrawn from a GitHub Sponsors agreement that applies to an organization.

**Additional fields:** `sponsors_listing_id`

### sub\_issues

#### `sub_issues.parent_issue_add`

A parent issue was added to an issue.

**Additional fields:** `title`, `public_repo`, `actor_is_bot`

#### `sub_issues.parent_issue_remove`

A parent issue was removed from an issue.

**Additional fields:** `title`, `public_repo`, `actor_is_bot`

#### `sub_issues.sub_issue_add`

A sub-issue was added to an issue.

**Additional fields:** `title`, `public_repo`, `actor_is_bot`

#### `sub_issues.sub_issue_remove`

A sub-issue was removed from an issue.

**Additional fields:** `title`, `public_repo`, `actor_is_bot`

### successor\_invitation

#### `successor_invitation.accept`

Triggered when you accept a succession invitation.

**Reference:** [Maintaining ownership continuity of your personal account's repositories](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/maintaining-ownership-continuity-of-your-personal-accounts-repositories)

#### `successor_invitation.cancel`

Triggered when you cancel a succession invitation.

**Reference:** [Maintaining ownership continuity of your personal account's repositories](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/maintaining-ownership-continuity-of-your-personal-accounts-repositories)

#### `successor_invitation.create`

Triggered when you create a succession invitation.

**Reference:** [Maintaining ownership continuity of your personal account's repositories](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/maintaining-ownership-continuity-of-your-personal-accounts-repositories)

#### `successor_invitation.decline`

Triggered when you decline a succession invitation.

**Reference:** [Maintaining ownership continuity of your personal account's repositories](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/maintaining-ownership-continuity-of-your-personal-accounts-repositories)

#### `successor_invitation.revoke`

Triggered when you revoke a succession invitation.

**Reference:** [Maintaining ownership continuity of your personal account's repositories](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/maintaining-ownership-continuity-of-your-personal-accounts-repositories)

### trusted\_device

#### `trusted_device.register`

A new trusted device was added.

#### `trusted_device.remove`

A trusted device was removed.

### two\_factor\_authentication

#### `two_factor_authentication.add_factor`

A secondary authentication factor was added to a user account.

**Reference:** /authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication

#### `two_factor_authentication.disabled`

Two-factor authentication was disabled for a user account.

**Reference:** [Disabling two-factor authentication for your personal account](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/disabling-two-factor-authentication-for-your-personal-account)

#### `two_factor_authentication.enabled`

Two-factor authentication was enabled for a user account.

**Reference:** [Configuring two-factor authentication](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication)

#### `two_factor_authentication.password_reset_fallback_sms`

A one-time password code was sent to a user account fallback phone number.

#### `two_factor_authentication.recovery_codes_regenerated`

Two factor recovery codes were regenerated for a user account.

#### `two_factor_authentication.remove_factor`

A secondary authentication factor was removed from a user account.

**Reference:** /authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication

#### `two_factor_authentication.sign_in_fallback_sms`

A one-time password code was sent to a user account fallback phone number.

#### `two_factor_authentication.update_fallback`

The two-factor authentication fallback for a user account was changed.

### user

#### `user.add_email`

An email address was added to a user account.

**Additional fields:** `email`

**Reference:** [Adding an email address to your GitHub account](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/adding-an-email-address-to-your-github-account)

#### `user.async_delete`

An asynchronous job was started to destroy a user account, eventually triggering a user.delete event.

#### `user.audit_log_export`

Audit log entries were exported.

#### `user.block_user`

A user was blocked by another user.

**Additional fields:** `blocked_user`

#### `user.change_password`

A user changed their password.

#### `user.codespaces_trusted_repo_access_granted`

Triggered when you allow the codespaces you create for a repository to access other repositories owned by your personal account.

**Reference:** [Managing access to other repositories within your codespace](/en/codespaces/managing-codespaces-for-your-organization/managing-repository-access-for-your-organizations-codespaces)

#### `user.codespaces_trusted_repo_access_revoked`

Triggered when you disallow the codespaces you create for a repository to access other repositories owned by your personal account.

**Reference:** [Managing access to other repositories within your codespace](/en/codespaces/managing-codespaces-for-your-organization/managing-repository-access-for-your-organizations-codespaces)

#### `user.create`

A new user account was created.

**Additional fields:** `email`

#### `user.create_integration_secret`

A user secret for Codespaces was created.

**Additional fields:** `key`, `visibility`, `integration`

#### `user.creation_rate_limit_exceeded`

The rate of creation of user accounts, applications, issues, pull requests or other resources exceeded the configured rate limits, or too many users were followed too quickly.

**Additional fields:** `oauth_application_id`

#### `user.delete`

A user account was destroyed by an asynchronous job.

#### `user.demote`

A site administrator was demoted to an ordinary user account.

**Additional fields:** `oauth_application_id`

#### `user.destroy`

A user deleted his or her account, triggering user.async\_delete.

#### `user.failed_login`

A user tried to sign in with an incorrect username, password, or two-factor authentication code.

#### `user.forgot_password`

A user requested a password reset.

**Additional fields:** `email`

**Reference:** /authentication/keeping-your-account-and-data-secure/updating-your-github-access-credentials

#### `user.hide_private_contributions_count`

A user changed the visibility of their private contributions. The number of contributions to private repositories on the user's profile are now hidden.

**Reference:** [Manage visibility settings for private contributions](/en/account-and-profile/setting-up-and-managing-your-github-profile/managing-contribution-settings-on-your-profile/showing-your-private-contributions-and-achievements-on-your-profile)

#### `user.login`

A user signed in.

**Additional fields:** `passkey_nickname`

#### `user.logout`

A user signed out.

#### `user.new_device_used`

A user signed in from a new device.

#### `user.promote`

An ordinary user account was promoted to a site administrator.

**Additional fields:** `oauth_application_id`

#### `user.recreate`

A user's account was restored.

#### `user.remove_email`

An email address was removed from a user account.

**Additional fields:** `email`

#### `user.remove_integration_secret`

A user secret for Codespaces was deleted.

**Additional fields:** `key`, `integration`

#### `user.rename`

A username was changed.

**Additional fields:** `old_login`

#### `user.reset_password`

A user reset their account password.

#### `user.show_private_contributions_count`

A user changed the visibility of their private contributions. The number of contributions to private repositories on the user's profile are now shown.

**Reference:** [Manage visibility settings for private contributions](/en/account-and-profile/setting-up-and-managing-your-github-profile/managing-contribution-settings-on-your-profile/showing-your-private-contributions-and-achievements-on-your-profile)

#### `user.sign_in_from_unrecognized_device`

A user signed in from an unrecognized device.

#### `user.sign_in_from_unrecognized_device_and_location`

A user signed in from an unrecognized device and location.

#### `user.suspend`

A user account was suspended.

**Additional fields:** `oauth_application_id`

#### `user.two_factor_challenge_failure`

A 2FA challenge issued for a user account failed.

#### `user.two_factor_challenge_success`

A 2FA challenge issued for a user account succeeded.

#### `user.two_factor_recover`

A user used their 2FA recovery codes.

#### `user.two_factor_recovery_codes_downloaded`

A user downloaded 2FA recovery codes for their account.

#### `user.two_factor_recovery_codes_printed`

A user printed 2FA recovery codes for their account.

#### `user.two_factor_recovery_codes_viewed`

A user viewed 2FA recovery codes for their account.

#### `user.two_factor_requested`

A user was prompted for a two-factor authentication code.

**Reference:** /authentication/securing-your-account-with-two-factor-authentication-2fa/accessing-github-using-two-factor-authentication

#### `user.unblock_user`

A user was unblocked by another user.

**Additional fields:** `blocked_user`

#### `user.unsuspend`

A user account was unsuspended.

**Additional fields:** `oauth_application_id`

#### `user.update_integration_secret`

A user secret for Codespaces was updated.

**Additional fields:** `key`, `visibility`, `integration`

### user\_email

#### `user_email.confirm_claim`

An enterprise managed user claimed an email address.

**Additional fields:** `actor_is_bot`

### user\_status

#### `user_status.destroy`

Triggered when you clear the status on your profile.

**Additional fields:** `message`, `limited_availability`, `emoji`

#### `user_status.update`

Triggered when you set or change the status on your profile.

**Additional fields:** `limited_availability`, `message`, `emoji`

**Reference:** [Personalize your profile](/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile#setting-a-status)

### workflows

#### `workflows.approve_workflow_job`

A workflow job was approved.

**Additional fields:** `workflow_run_id`, `run_number`, `public_repo`

**Reference:** [Reviewing deployments](/en/actions/managing-workflow-runs/reviewing-deployments)

#### `workflows.delete_workflow_run`

A workflow run was deleted.

**Additional fields:** `workflow_run_id`, `started_at`, `head_branch`, `head_sha`, `trigger_id`

**Reference:** [Deleting a workflow run](/en/actions/managing-workflow-runs/deleting-a-workflow-run)

#### `workflows.disable_workflow`

A workflow was disabled.

**Additional fields:** `workflow_id`, `public_repo`, `actor_is_bot`

#### `workflows.enable_workflow`

A workflow was enabled, after previously being disabled by disable\_workflow.

**Additional fields:** `workflow_id`, `public_repo`

#### `workflows.pin_workflow`

A workflow was pinned.

**Additional fields:** `public_repo`, `workflow_id`, `actor_is_bot`

#### `workflows.reject_workflow_job`

A workflow job was rejected.

**Additional fields:** `workflow_run_id`, `run_number`, `public_repo`

**Reference:** [Reviewing deployments](/en/actions/managing-workflow-runs/reviewing-deployments)

#### `workflows.unpin_workflow`

A workflow was unpinned after previously being pinned.

**Additional fields:** `public_repo`, `workflow_id`, `actor_is_bot`