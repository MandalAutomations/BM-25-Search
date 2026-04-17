# Audit log events for your enterprise

Review the events recorded in an enterprise's audit log.

> \[!NOTE] This article lists events that may appear in the audit log for an **enterprise**. For the events that can appear in a user account's security log or the audit log for an organization, see [Security log events](/en/enterprise-cloud@latest/authentication/keeping-your-account-and-data-secure/security-log-events) and [Audit log events for your organization](/en/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/audit-log-events-for-your-organization).

## What types of events are included?

* **Without Enterprise Managed Users**, the audit log only includes events related to the enterprise account and the organizations within it.
* **With Enterprise Managed Users**, the audit log also includes user events, which are not listed here. For that list, see [Security log events](/en/enterprise-cloud@latest/authentication/keeping-your-account-and-data-secure/security-log-events).

## Audit log events

### Common fields

The following fields are included in most audit log events: `@timestamp`, `_document_id`, `action`, `actor`, `actor_id`, `business`, `business_id`, `created_at`, `hashed_token`, `operation_type`, `org`, `org_id`, `programmatic_access_type`, `repo`, `repo_id`, `repository`, `repository_id`, `request_access_security_header`, `request_id`, `token_id`, `token_scopes`, `user`, `user_agent`, `user_id`

Each event below lists only its additional fields beyond these common fields.

### account

#### `account.plan_change`

The account's plan changed.

**Reference:** [How GitHub billing works](/en/enterprise-cloud@latest/billing/managing-the-plan-for-your-github-account/about-billing-for-plans)

### actions\_cache

#### `actions_cache.delete`

A GitHub Actions cache was deleted using the REST API.

**Additional fields:** `oauth_application_id`, `actions_cache_id`, `actions_cache_key`, `actions_cache_version`, `actions_cache_scope`

### advisory\_credit

#### `advisory_credit.accept`

Credit was accepted for a security advisory.

**Additional fields:** `ghsa_id`, `recipient`

**Reference:** [Editing a repository security advisory](/en/enterprise-cloud@latest/code-security/security-advisories/working-with-repository-security-advisories/editing-a-repository-security-advisory)

#### `advisory_credit.create`

Someone was added to the credit section of a security advisory.

**Additional fields:** `ghsa_id`, `recipient`

#### `advisory_credit.decline`

Credit was declined for a security advisory.

**Additional fields:** `ghsa_id`, `recipient`, `public_repo`

#### `advisory_credit.destroy`

Someone was removed from the credit section of a security advisory.

**Additional fields:** `ghsa_id`, `recipient`, `public_repo`

### api

#### `api.request`

An API request was made to an endpoint for the enterprise, or an enterprise owned resource. This event is only included if API Request Events is enabled in the enterprise's audit log settings. This event is only available via audit log streaming.

**Additional fields:** `request_method`, `query_string`, `request_body`, `status_code`, `url_path`, `public_repo`, `route`, `rate_limit_remaining`, `actor_is_bot`

**Reference:** [Streaming the audit log for your enterprise](/en/enterprise-cloud@latest/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/streaming-the-audit-log-for-your-enterprise#enabling-audit-log-streaming-of-api-requests)

### artifact

#### `artifact.destroy`

A workflow run artifact was manually deleted.

### audit\_log\_streaming

#### `audit_log_streaming.check`

A manual check of the endpoint configured for audit log streaming was performed.

**Additional fields:** `audit_log_stream_result`, `audit_log_stream_sink_details`

#### `audit_log_streaming.create`

An endpoint was added for audit log streaming.

**Additional fields:** `audit_log_stream_sink`, `audit_log_stream_id`

#### `audit_log_streaming.destroy`

An audit log streaming endpoint was deleted.

**Additional fields:** `audit_log_stream_id`, `audit_log_stream_sink_details`

#### `audit_log_streaming.update`

An endpoint configuration was updated for audit log streaming, such as the stream was paused, enabled, or disabled.

**Additional fields:** `audit_log_stream_enabled`, `audit_log_stream_sink`, `new_s3_bucket`, `old_s3_bucket`, `secrets_updated`, `new_s3_arn_role`, `old_s3_arn_role`, `new_azure_blob_container`, `old_azure_blob_container`, `new_event_hub_instance`, `old_event_hub_instance`, `new_splunk_domain`, `old_splunk_domain`, `ssl_verify`, `old_gc_bucket`

### auto\_approve\_personal\_access\_token\_requests

#### `auto_approve_personal_access_token_requests.disable`

Triggered when the organization must approve fine-grained personal access tokens before the tokens can access organization resources. See also: personal\_access\_token.auto\_approve\_grant\_requests\_disabled

**Reference:** /organizations/managing-programmatic-access-to-your-organization/setting-a-personal-access-token-policy-for-your-organization

#### `auto_approve_personal_access_token_requests.enable`

Triggered when fine-grained personal access tokens can access organization resources without prior approval. See also: personal\_access\_token.auto\_approve\_grant\_requests\_enabled

**Reference:** /organizations/managing-programmatic-access-to-your-organization/setting-a-personal-access-token-policy-for-your-organization

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

**Reference:** [Managing your payment and billing information](/en/enterprise-cloud@latest/billing/managing-your-github-billing-settings/adding-or-editing-a-payment-method)

#### `billing.change_email`

The billing email address changed.

**Additional fields:** `email`

**Reference:** [Managing your payment and billing information](/en/enterprise-cloud@latest/billing/managing-your-github-billing-settings/setting-your-billing-email)

#### `billing.cost_center_create`

A cost center was created for a business or organization.

**Additional fields:** `name`

#### `billing.cost_center_delete`

A cost center was deleted from a business or organization.

#### `billing.cost_center_resource_added`

A resource was added to a cost center for a business or organization.

**Additional fields:** `name`, `resource_id`, `resource_type`, `actor_is_bot`

#### `billing.cost_center_resource_removed`

A resource was removed from a cost center for a business or organization.

**Additional fields:** `name`, `resource_id`, `resource_type`, `actor_is_bot`

#### `billing.cost_center_update`

A cost center was updated for a business or organization.

**Additional fields:** `name`, `actor_is_bot`

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

#### `business.add_disallowed_two_factor_method`

An enterprise prevented access to resources by users with the given two-factor method.

**Additional fields:** `name`, `two_factor_method`, `actor_is_bot`

#### `business.add_organization`

An organization was added to an enterprise.

**Additional fields:** `name`, `organization_upgrade`

#### `business.add_support_entitlee`

A support entitlement was added to a member of an enterprise.

**Additional fields:** `name`

**Reference:** [Managing support entitlements for your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/managing-support-entitlements-for-your-enterprise)

#### `business.advanced_security_metered_usage_lock`

Enablement for Advanced Security features on new repositories has been locked for this enterprise.

**Additional fields:** `actor_is_bot`

#### `business.advanced_security_metered_usage_unlock`

Enablement for Advanced Security features on new repositories has been unlocked for this enterprise.

**Additional fields:** `actor_is_bot`

#### `business.advanced_security_policy_update`

An enterprise owner created, updated, or removed a policy for GitHub Advanced Security.

**Additional fields:** `name`, `new_policy`

**Reference:** [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-code-security-and-analysis-for-your-enterprise)

#### `business.audit_log_export`

An export of the enterprise audit log was created. If the export included a query, the log will list the query used and the number of audit log entries matching that query.

**Additional fields:** `query_phrase`

**Reference:** [Exporting audit log activity for your enterprise](admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/exporting-audit-log-activity-for-your-enterprise)

#### `business.audit_log_git_event_export`

An export of the enterprise's Git events was created.

**Additional fields:** `start`, `end`

**Reference:** [Exporting audit log activity for your enterprise](admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/exporting-audit-log-activity-for-your-enterprise)

#### `business.cancel_admin_invitation`

An invitation for someone to be an owner of an enterprise was canceled.

**Additional fields:** `invitation_id`, `name`

#### `business.cancel_billing_manager_invitation`

An invitation for someone to be an billing manager of an enterprise was canceled.

**Additional fields:** `name`, `invitation_id`

#### `business.cancel_trial`

The trial of GitHub Enterprise Cloud was canceled.

**Additional fields:** `name`

**Reference:** [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud)

#### `business.change_seats_plan_type`

The seats plan type was changed for an enterprise.

**Additional fields:** `name`, `seats_plan_type_was`, `seats_plan_type`, `actor_is_bot`

#### `business.clear_actions_settings`

An enterprise owner or site administrator cleared GitHub Actions policy settings for an enterprise.

**Additional fields:** `name`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise)

#### `business.clear_default_repository_permission`

An enterprise owner cleared the base repository permission policy setting for an enterprise.

**Additional fields:** `name`

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-base-repository-permissions)

#### `business.clear_disallowed_two_factor_methods`

Cleared two-factor authentication restrictions for an enterprise.

**Additional fields:** `name`, `actor_is_bot`

#### `business.clear_members_can_create_repos`

An enterprise owner cleared a restriction on repository creation in organizations in the enterprise.

**Additional fields:** `name`, `visibility`

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#setting-a-policy-for-repository-creation)

#### `business.code_scanning_autofix_policy_update`

The policy for Code scanning autofix was updated for an enterprise.

**Additional fields:** `name`, `new_policy`, `actor_is_bot`

#### `business.code_scanning_autofix_third_party_tools_policy_update`

The policy for Code scanning autofix third party tools was updated for an enterprise.

**Additional fields:** `name`, `new_policy`, `actor_is_bot`

**Reference:** /code-security/getting-started/github-security-features#available-with-github-code-security

#### `business.code_security_enablement_policy_update`

The policy for Code Security enablement was updated for an enterprise.

**Additional fields:** `name`, `new_policy`, `actor_is_bot`

**Reference:** /code-security/getting-started/github-security-features#available-with-github-code-security

#### `business.code_security_metered_usage_lock`

Enablement for Code Security features on new repositories has been locked for this enterprise.

**Additional fields:** `actor_is_bot`

#### `business.code_security_metered_usage_unlock`

Enablement for Code Security features on new repositories has been unlocked for this enterprise.

**Additional fields:** `actor_is_bot`

#### `business.connect_usage_metrics_export`

Server statistics were exported for the enterprise.

**Additional fields:** `name`

**Reference:** [Exporting Server Statistics](/en/enterprise-cloud@latest/admin/monitoring-activity-in-your-enterprise/analyzing-how-your-team-works-with-server-statistics/exporting-server-statistics)

#### `business.convert_trial`

The enterprise account on a trial of GitHub Enterprise Cloud was upgraded to a paid enterprise account.

**Additional fields:** `name`

**Reference:** [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud)

#### `business.create`

An enterprise was created.

**Additional fields:** `name`

#### `business.create_trial`

A trial of GitHub Enterprise Cloud began.

**Additional fields:** `name`

**Reference:** [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud)

#### `business.delete`

The enterprise was deleted.

**Additional fields:** `name`

**Reference:** [Deleting an enterprise account](/en/enterprise-cloud@latest/admin/overview/deleting-an-enterprise-account)

#### `business.delete_custom_image`

A custom image was deleted for an enterprise.

**Additional fields:** `name`, `actor_is_bot`

**Reference:** /actions/how-tos/manage-runners/larger-runners/use-custom-images

#### `business.delete_custom_image_version`

A custom image version was deleted for an enterprise.

**Additional fields:** `name`, `actor_is_bot`

**Reference:** /actions/how-tos/manage-runners/larger-runners/use-custom-images

#### `business.disable_oidc`

OIDC single sign-on was disabled for an enterprise.

**Reference:** [Configuring OIDC for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-oidc-for-enterprise-managed-users)

#### `business.disable_open_scim`

SCIM provisioning for custom integrations that use the REST API was disabled for the enterprise.

#### `business.disable_saml`

SAML single sign-on was disabled for an enterprise.

**Additional fields:** `issuer`, `name`, `sso_url`

#### `business.disable_source_ip_disclosure`

Display of IP addresses within audit log events for the enterprise was disabled.

**Reference:** [Displaying IP addresses in the audit log for your enterprise](/en/enterprise-cloud@latest/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/displaying-ip-addresses-in-the-audit-log-for-your-enterprise)

#### `business.disable_two_factor_requirement`

The requirement for members to have two-factor authentication enabled to access an enterprise was disabled.

**Additional fields:** `name`

#### `business.enable_oidc`

OIDC single sign-on was enabled for an enterprise.

**Reference:** [Configuring OIDC for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-oidc-for-enterprise-managed-users)

#### `business.enable_open_scim`

SCIM provisioning for custom integrations that use the REST API was enabled for the enterprise.

#### `business.enable_saml`

SAML single sign-on was enabled for an enterprise.

**Additional fields:** `name`, `sso_url`, `issuer`

#### `business.enable_source_ip_disclosure`

Display of IP addresses within audit log events for the enterprise was enabled.

**Reference:** [Displaying IP addresses in the audit log for your enterprise](/en/enterprise-cloud@latest/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/displaying-ip-addresses-in-the-audit-log-for-your-enterprise)

#### `business.enable_two_factor_requirement`

The requirement for members to have two-factor authentication enabled to access an enterprise was enabled.

**Additional fields:** `name`

#### `business.enterprise_server_license_download`

A GitHub Enterprise Server license was downloaded.

#### `business.expire_trial`

The trial of GitHub Enterprise Cloud expired.

**Additional fields:** `name`

**Reference:** [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud)

#### `business.github_models_billing_disabled`

GitHub Models billing was disabled for the business.

**Additional fields:** `name`, `actor_is_bot`

#### `business.github_models_billing_enabled`

GitHub Models billing was enabled for the business.

**Additional fields:** `name`, `actor_is_bot`

#### `business.import_license_usage`

License usage information was imported from a GitHub Enterprise Server instance to an enterprise account on GitHub.com.

**Additional fields:** `name`

**Reference:** [Syncing license usage from GitHub Enterprise Server to Cloud](/en/enterprise-cloud@latest/billing/managing-your-license-for-github-enterprise/syncing-license-usage-between-github-enterprise-server-and-github-enterprise-cloud#manually-uploading-github-enterprise-server-license-usage)

#### `business.invite_admin`

An invitation for someone to be an enterprise owner of an enterprise was sent.

**Additional fields:** `name`, `invitation_id`

#### `business.invite_billing_manager`

An invitation for someone to be a billing manager of an enterprise was sent.

**Additional fields:** `invitation_id`, `name`

#### `business.invite_unaffiliated_member`

An invitation for someone to join an enterprise was sent.

**Additional fields:** `name`, `invitation_id`, `email`, `actor_is_bot`

#### `business.members_can_update_protected_branches.clear`

An enterprise owner unset a policy for whether members of an enterprise can update protected branches on repositories for individual organizations. Organization owners can choose whether to allow updating protected branches settings.

**Additional fields:** `name`

#### `business.members_can_update_protected_branches.disable`

The ability for enterprise members to update branch protection rules was disabled. Only enterprise owners can update protected branches.

**Additional fields:** `name`

#### `business.members_can_update_protected_branches.enable`

The ability for enterprise members to update branch protection rules was enabled. Enterprise owners and members can update protected branches.

**Additional fields:** `name`

#### `business.members_limit_reached`

An enterprise has reached its members limit.

**Additional fields:** `name`, `limit`, `count`, `actor_is_bot`

#### `business.organizations_limit_reached`

An enterprise has reached its organizations limit.

**Additional fields:** `name`, `limit`, `count`, `actor_is_bot`

#### `business.organizations_limit_warning`

An enterprise is approaching its organizations limit.

**Additional fields:** `name`, `limit`, `count`, `actor_is_bot`

#### `business.proxy_security_header_disabled`

The proxy security header was disabled for an enterprise. All users on the network can now access GitHub, unless blocked by other means.

**Additional fields:** `actor_is_bot`

#### `business.proxy_security_header_enabled`

The proxy security header was enabled for an enterprise. When the header is provided in requests, only Enterprise Managed Users matching the header will be able to access GitHub.

**Additional fields:** `actor_is_bot`

#### `business.proxy_security_header_unsatisfied`

A user outside the enterprise tried to access GitHub while the proxy security header was enabled and provided in the request.

**Additional fields:** `name`, `actor_is_bot`

#### `business.recovery_code_failed`

An enterprise owner failed to sign into a enterprise with an external identity provider (IdP) using a recovery code.

**Additional fields:** `name`, `reason`

**Reference:** [Accessing your enterprise account if your identity provider is unavailable](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/accessing-your-enterprise-account-if-your-identity-provider-is-unavailable)

#### `business.recovery_code_used`

An enterprise owner successfully signed into an enterprise with an external identity provider (IdP) using a recovery code.

**Additional fields:** `name`

**Reference:** [Accessing your enterprise account if your identity provider is unavailable](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/accessing-your-enterprise-account-if-your-identity-provider-is-unavailable)

#### `business.recovery_codes_downloaded`

An enterprise owner downloaded the enterprise's SSO recovery codes.

**Additional fields:** `name`

**Reference:** [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes)

#### `business.recovery_codes_generated`

An enterprise owner generated the enterprise's SSO recovery codes.

**Additional fields:** `name`

**Reference:** [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes)

#### `business.recovery_codes_printed`

An enterprise owner printed the enterprise's SSO recovery codes.

**Additional fields:** `name`

**Reference:** [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes)

#### `business.recovery_codes_viewed`

An enterprise owner viewed the enterprise's SSO recovery codes.

**Additional fields:** `name`

**Reference:** [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes)

#### `business.remove_admin`

An enterprise owner was removed from an enterprise.

**Additional fields:** `name`

**Reference:** [Inviting people to manage your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/inviting-people-to-manage-your-enterprise)

#### `business.remove_billing_manager`

A billing manager was removed from an enterprise.

**Additional fields:** `name`

#### `business.remove_disallowed_two_factor_method`

Removed a two-factor authentication method restriction for an enterprise.

**Additional fields:** `name`, `two_factor_method`, `actor_is_bot`

#### `business.remove_member`

A member was removed from an enterprise.

#### `business.remove_organization`

An organization was removed from an enterprise.

**Additional fields:** `name`

#### `business.remove_support_entitlee`

A support entitlement was removed from a member of an enterprise.

**Additional fields:** `name`

**Reference:** [Managing support entitlements for your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/managing-support-entitlements-for-your-enterprise)

#### `business.rename_slug`

The slug for the enterprise URL was renamed.

**Additional fields:** `name`

#### `business.restore`

The deleted enterprise was restored.

**Additional fields:** `name`

#### `business.revoke_external_identity`

The external identity for a member in an enterprise was revoked.

**Additional fields:** `name`

#### `business.revoke_sso_session`

The SAML single sign-on session for a member in an enterprise was revoked.

**Additional fields:** `name`

#### `business.secret_protection_metered_usage_lock`

Enablement for Secret Protection features on new repositories has been locked for this enterprise.

**Additional fields:** `actor_is_bot`

#### `business.secret_protection_metered_usage_unlock`

Enablement for Secret Protection features on new repositories has been unlocked for this enterprise.

**Additional fields:** `actor_is_bot`

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

#### `business.sso_response`

A SAML single sign-on (SSO) response was generated when a member attempted to authenticate with your enterprise. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `issuer`, `name`

#### `business.update_actions_settings`

An enterprise owner or site administrator updated GitHub Actions policy settings for an enterprise.

**Additional fields:** `name`, `updated_github_owned_allowed`, `updated_verified_allowed`, `updated_patterns`, `new_policy`, `old_policy`, `updated_access_policy`

**Reference:** [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise)

#### `business.update_default_repository_permission`

The base repository permission setting was updated for all organizations in an enterprise.

**Additional fields:** `permission`, `name`, `old_permission`

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-base-repository-permissions)

#### `business.update_member_repository_creation_permission`

The repository creation setting was updated for an enterprise.

**Additional fields:** `name`, `permission`, `visibility`

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-repository-creation)

#### `business.update_member_repository_invitation_permission`

The policy setting for enterprise members inviting outside collaborators to repositories was updated.

**Additional fields:** `permission`, `name`

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-inviting-outside-collaborators-to-repositories)

#### `business.update_saml_provider_settings`

The SAML single sign-on provider settings for an enterprise were updated.

**Additional fields:** `sso_url`, `name`, `issuer`

#### `business.upgrade_from_organization`

The organization was upgraded to an enterprise account.

**Reference:** [Upgrading your account's plan](/en/enterprise-cloud@latest/billing/managing-the-plan-for-your-github-account/upgrading-your-accounts-plan#upgrading-your-organizations-plan)

### business\_advanced\_security

#### `business_advanced_security.disabled`

GitHub Advanced Security was disabled for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_advanced_security.disabled_for_new_repos`

GitHub Advanced Security was disabled for new repositories in your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_advanced_security.disabled_for_new_user_namespace_repos`

GitHub Advanced Security was disabled for new user namespace repositories in your enterprise.

**Additional fields:** `actor_is_bot`

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_advanced_security.enabled`

GitHub Advanced Security was enabled for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_advanced_security.enabled_for_new_repos`

GitHub Advanced Security was enabled for new repositories in your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_advanced_security.enabled_for_new_user_namespace_repos`

GitHub Advanced Security was enabled for new user namespace repositories in your enterprise.

**Additional fields:** `actor_is_bot`

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_advanced_security.user_namespace_repos_disabled`

GitHub Advanced Security was disabled for user namespace repositories in your enterprise.

**Additional fields:** `actor_is_bot`

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_advanced_security.user_namespace_repos_enabled`

GitHub Advanced Security was enabled for user namespace repositories in your enterprise.

**Additional fields:** `actor_is_bot`

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

### business\_dependabot\_alerts

#### `business_dependabot_alerts.disable`

Dependabot alerts were disabled for your enterprise.

#### `business_dependabot_alerts.enable`

Dependabot alerts were enabled for your enterprise.

### business\_dependabot\_alerts\_new\_repos

#### `business_dependabot_alerts_new_repos.disable`

Dependabot alerts were disabled for new repositories in your enterprise.

#### `business_dependabot_alerts_new_repos.enable`

Dependabot alerts were enabled for new repositories in your enterprise.

### business\_secret\_scanning

#### `business_secret_scanning.disable`

Secret scanning was disabled for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_secret_scanning.disabled_for_new_repos`

Secret scanning was disabled for new repositories in your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_secret_scanning.enable`

Secret scanning was enabled for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_secret_scanning.enabled_for_new_repos`

Secret scanning was enabled for new repositories in your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

### business\_secret\_scanning\_automatic\_validity\_checks

#### `business_secret_scanning_automatic_validity_checks.disabled`

Automatic partner validation checks have been disabled at the business level

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise#managing-advanced-security-features)

#### `business_secret_scanning_automatic_validity_checks.enabled`

Automatic partner validation checks have been enabled at the business level

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise#managing-advanced-security-features)

### business\_secret\_scanning\_custom\_pattern

#### `business_secret_scanning_custom_pattern.create`

An enterprise-level custom pattern was created for secret scanning.

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-an-enterprise-account)

#### `business_secret_scanning_custom_pattern.delete`

An enterprise-level custom pattern was removed from secret scanning.

#### `business_secret_scanning_custom_pattern.publish`

An enterprise-level custom pattern was published for secret scanning.

#### `business_secret_scanning_custom_pattern.update`

Changes to an enterprise-level custom pattern were saved and a dry run was executed for secret scanning.

### business\_secret\_scanning\_custom\_pattern\_push\_protection

#### `business_secret_scanning_custom_pattern_push_protection.disabled`

Push protection for a custom pattern for secret scanning was disabled for your enterprise.

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-an-enterprise-account)

#### `business_secret_scanning_custom_pattern_push_protection.enabled`

Push protection for a custom pattern for secret scanning was enabled for your enterprise.

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-an-enterprise-account)

### business\_secret\_scanning\_generic\_secrets

#### `business_secret_scanning_generic_secrets.disabled`

Generic secrets have been disabled at the business level

**Additional fields:** `actor_is_bot`

#### `business_secret_scanning_generic_secrets.enabled`

Generic secrets have been enabled at the business level

**Additional fields:** `actor_is_bot`

### business\_secret\_scanning\_non\_provider\_patterns

#### `business_secret_scanning_non_provider_patterns.disabled`

Secret scanning for non-provider patterns was disabled at the enterprise level.

**Additional fields:** `actor_is_bot`

**Reference:** [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/secret-scanning-patterns#non-provider-patterns)

#### `business_secret_scanning_non_provider_patterns.enabled`

Secret scanning for non-provider patterns was enabled at the enterprise level.

**Additional fields:** `actor_is_bot`

**Reference:** [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/secret-scanning-patterns#non-provider-patterns)

### business\_secret\_scanning\_push\_protection

#### `business_secret_scanning_push_protection.disable`

Push protection for secret scanning was disabled for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_secret_scanning_push_protection.disabled_for_new_repos`

Push protection for secret scanning was disabled for new repositories in your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_secret_scanning_push_protection.enable`

Push protection for secret scanning was enabled for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_secret_scanning_push_protection.enabled_for_new_repos`

Push protection for secret scanning was enabled for new repositories in your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

### business\_secret\_scanning\_push\_protection\_custom\_message

#### `business_secret_scanning_push_protection_custom_message.disable`

The custom message triggered by an attempted push to a push-protected repository was disabled for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_secret_scanning_push_protection_custom_message.enable`

The custom message triggered by an attempted push to a push-protected repository was enabled for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_secret_scanning_push_protection_custom_message.update`

The custom message triggered by an attempted push to a push-protected repository was updated for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

### business\_secret\_scanning\_push\_protection\_pattern\_configuration

#### `business_secret_scanning_push_protection_pattern_configuration.push_protection_setting_changed`

The push protection setting was updated for a secret type for your enterprise.

**Additional fields:** `push_protection_setting`, `secret_type`, `secret_type_display_name`

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

#### `business_secret_scanning_push_protection_pattern_configuration.updated`

The push protection pattern configuration was updated for your enterprise.

**Reference:** [Managing GitHub Advanced Security features for your enterprise](/en/enterprise-cloud@latest/admin/code-security/managing-github-advanced-security-for-your-enterprise/managing-github-advanced-security-features-for-your-enterprise)

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

### code\_scanning

#### `code_scanning.alert_appeared_in_branch`

Existing code scanning alerts appeared in a branch.

**Additional fields:** `alert_number`, `commit_oid`, `ref`, `alert_numbers`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

#### `code_scanning.alert_closed_became_fixed`

Code scanning alerts were fixed.

**Additional fields:** `alert_number`, `commit_oid`, `ref`, `alert_numbers`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

#### `code_scanning.alert_closed_became_outdated`

Code scanning alerts were closed as outdated (all configurations they were detected in were deleted).

**Additional fields:** `alert_numbers`, `commit_oid`, `ref`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

#### `code_scanning.alert_closed_by_user`

Code scanning alerts were manually dismissed.

**Additional fields:** `alert_number`, `alert_numbers`, `dismissal_approver_id`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

#### `code_scanning.alert_closure_approved`

Dismissal of code scanning alerts was approved.

**Additional fields:** `dismissal_request_id`, `alert_number`, `public_repo`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

#### `code_scanning.alert_closure_denied`

Dismissal of code scanning alerts was denied.

**Additional fields:** `dismissal_request_id`, `alert_number`, `public_repo`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

#### `code_scanning.alert_closure_requested`

Dismissal of code scanning alerts was requested.

**Additional fields:** `dismissal_request_id`, `alert_number`, `public_repo`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

#### `code_scanning.alert_created`

Code scanning alerts were seen for the first time.

**Additional fields:** `alert_number`, `commit_oid`, `ref`, `alert_numbers`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

#### `code_scanning.alert_reappeared`

Code scanning alerts that were previously fixed reappeared.

**Additional fields:** `alert_number`, `commit_oid`, `ref`, `alert_numbers`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

#### `code_scanning.alert_reopened_by_user`

Code scanning alerts that were previously dismissed were reopened.

**Additional fields:** `alert_number`, `alert_numbers`

**Reference:** [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)

### codespaces

#### `codespaces.allow_permissions`

A codespace using custom permissions from its devcontainer.json file was launched.

**Additional fields:** `origin_repository`

#### `codespaces.attempted_to_create_from_prebuild`

An attempt to create a codespace from a prebuild was made.

**Additional fields:** `name`, `owner`, `pull_request_id`, `public_repo`

#### `codespaces.business_enablement_updated`

Enterprise setting for Codespaces ownership was updated.

**Additional fields:** `enablement`, `organization_names`

**Reference:** /codespaces/managing-codespaces-for-your-organization/choosing-who-owns-and-pays-for-codespaces-in-your-organization

#### `codespaces.connect`

Credentials for a codespace were refreshed.

**Additional fields:** `pull_request_id`, `owner`, `name`, `public_repo`, `actor_is_bot`, `machine_type`, `devcontainer_path`

#### `codespaces.create`

A codespace was created

**Additional fields:** `pull_request_id`, `owner`, `name`, `actor_is_bot`, `machine_type`, `devcontainer_path`

**Reference:** [Creating a codespace for a repository](/en/enterprise-cloud@latest/codespaces/developing-in-codespaces/creating-a-codespace-for-a-repository)

#### `codespaces.destroy`

A user deleted a codespace.

**Additional fields:** `pull_request_id`, `owner`, `name`

**Reference:** [Deleting a codespace](/en/enterprise-cloud@latest/codespaces/developing-in-codespaces/deleting-a-codespace)

#### `codespaces.export_environment`

A codespace was exported to a branch on GitHub.

**Additional fields:** `oauth_application_id`, `owner`, `public_repo`

#### `codespaces.policy_group_created`

Policies were applied to codespaces in an organization or enterprise.

#### `codespaces.policy_group_deleted`

Policies were removed from codespaces in an organization or enterprise.

#### `codespaces.policy_group_updated`

Policies were updated for codespaces in an organization or enterprise.

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

**Reference:** [Managing access to other repositories within your codespace](/en/enterprise-cloud@latest/codespaces/managing-codespaces-for-your-organization/managing-repository-access-for-your-organizations-codespaces)

### commit\_comment

#### `commit_comment.destroy`

A commit comment was deleted.

#### `commit_comment.update`

A commit comment was updated.

### copilot

#### `copilot.access_revoked`

Copilot access was revoked for the organization or enterprise due to its Copilot subscription ending, an issue with billing the entity, the entity being marked spammy, or the entity being suspended.

**Additional fields:** `reason`, `plan`, `owner`

#### `copilot.cfb_enterprise_org_enablement_changed`

The Copilot enablement policy changed at the enterprise level to either allow or disable access for all organizations, or to allow access for selected organizations.

**Additional fields:** `previous_value`, `current_value`, `actor_is_bot`

#### `copilot.cfb_enterprise_settings_changed`

Copilot feature settings were changed at the enterprise level.

#### `copilot.cfb_org_settings_changed`

Copilot feature settings were changed at the organization level.

#### `copilot.cfb_seat_added`

A Copilot Business or Copilot Enterprise seat was added for a user and they have received access to GitHub Copilot. This can occur as the result of directly assigning a seat for a user, assigning a seat for a team, or setting the organization to allow access for all members.

#### `copilot.cfb_seat_assignment_created`

A Copilot Business or Copilot Enterprise seat assignment was newly created for a user or a team, and seats are being created.

**Reference:** [What is GitHub Copilot?](/en/enterprise-cloud@latest/copilot/overview-of-github-copilot/about-github-copilot-for-business)

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

#### `copilot.cfb_seat_management_changed`

The seat management setting was changed at the organization level to either enable or disable Copilot access for all members of the organization, or to enable Copilot access for selected members or teams.

**Additional fields:** `old_value`, `new_value`, `actor_is_bot`

#### `copilot.clickwrap_save_event`

The GitHub Copilot Product Terms or Pre-Release Preview Terms were accepted.

#### `copilot.content_exclusion_changed`

The excluded paths for GitHub Copilot were updated.

**Additional fields:** `excluded_paths`, `owner_type`

#### `copilot.enterprise_enablement_changed`

Copilot access was enabled or disabled at the enterprise level.

**Additional fields:** `previous_value`, `current_value`

#### `copilot.plan_changed`

The plan for GitHub Copilot was updated.

**Additional fields:** `old_plan`, `plan`, `actor_is_bot`

**Reference:** [GitHub Copilot licenses](/en/enterprise-cloud@latest/billing/managing-billing-for-github-copilot/about-billing-for-github-copilot)

#### `copilot.plan_downgrade_scheduled`

The plan for GitHub Copilot was scheduled to be downgraded.

**Additional fields:** `owner`, `actor_is_bot`, `current_plan`, `scheduled_plan`

### custom\_property\_definition

#### `custom_property_definition.create`

A new custom property definition was created.

**Additional fields:** `property_name`, `value_type`, `required`, `default_value`, `definition_id`

**Reference:** /organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization

#### `custom_property_definition.destroy`

A custom property definition was deleted.

**Additional fields:** `property_name`, `value_type`, `required`, `default_value`, `definition_id`, `allowed_values`

**Reference:** /organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization

#### `custom_property_definition.update`

A custom property definition was updated.

**Additional fields:** `property_name`, `value_type`, `required`, `default_value`, `old_allowed_values`, `allowed_values`, `definition_id`, `old_required`, `old_default_value`, `old_value_type`, `old_values_editable_by`, `values_editable_by`

**Reference:** /organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization

### custom\_property\_value

#### `custom_property_value.create`

A repository's custom property value was manually set for the first time.

**Additional fields:** `definition_id`, `property_name`, `value`, `public_repo`, `actor_is_bot`

**Reference:** /organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization

#### `custom_property_value.destroy`

A repository's custom property value was deleted.

**Additional fields:** `public_repo`

**Reference:** /organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization

#### `custom_property_value.update`

A repository's custom property value was updated.

**Additional fields:** `public_repo`, `definition_id`

**Reference:** /organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization

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

**Reference:** [About Dependabot alerts](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

#### `dependabot_closure_request.cancel`

Dismissal request for Dependabot alerts was canceled.

**Additional fields:** `number`, `alert_number`, `public_repo`, `actor_is_bot`

**Reference:** [About Dependabot alerts](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

#### `dependabot_closure_request.create`

Dismissal of Dependabot alerts was requested.

**Additional fields:** `number`, `alert_number`, `public_repo`, `actor_is_bot`

**Reference:** [About Dependabot alerts](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

#### `dependabot_closure_request.deny`

Dismissal of Dependabot alerts was denied.

**Additional fields:** `number`, `alert_number`, `public_repo`, `actor_is_bot`

**Reference:** [About Dependabot alerts](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

### dependabot\_repository\_access

#### `dependabot_repository_access.default_access_level_updated`

The default repository access for Dependabot was updated.

**Additional fields:** `access_level`, `actor_is_bot`

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

### enterprise

#### `enterprise.configure_self_hosted_jit_runner`

A new just-in-time GitHub Actions self-hosted runner was configured

**Additional fields:** `oauth_application_id`

**Reference:** /rest/actions/self-hosted-runners#create-configuration-for-a-just-in-time-runner-for-an-enterprise

#### `enterprise.register_self_hosted_runner`

A new GitHub Actions self-hosted runner was registered.

**Reference:** [Adding self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners#adding-a-self-hosted-runner-to-a-repository)

#### `enterprise.remove_self_hosted_runner`

A GitHub Actions self-hosted runner was removed.

**Reference:** [Removing self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/removing-self-hosted-runners#removing-a-runner-from-a-repository)

#### `enterprise.runner_group_created`

A GitHub Actions self-hosted runner group was created.

**Additional fields:** `runner_group_id`, `runner_group_restricted_to_workflows`

**Reference:** [Removing self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/removing-self-hosted-runners#removing-a-runner-from-a-repository)

#### `enterprise.runner_group_removed`

A GitHub Actions self-hosted runner group was removed.

**Additional fields:** `runner_group_id`

**Reference:** [Managing access to self-hosted runners using groups](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#removing-a-self-hosted-runner-group)

#### `enterprise.runner_group_renamed`

A GitHub Actions self-hosted runner group was renamed.

**Additional fields:** `runner_group_id`

**Reference:** [Managing access to self-hosted runners using groups](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#changing-the-access-policy-of-a-self-hosted-runner-group)

#### `enterprise.runner_group_runner_removed`

The REST API was used to remove a GitHub Actions self-hosted runner from a group.

**Additional fields:** `oauth_application_id`, `runner_group_id`, `runner_id`

**Reference:** /rest/actions#remove-a-self-hosted-runner-from-a-group-for-an-organization

#### `enterprise.runner_group_runners_added`

A GitHub Actions self-hosted runner was added to a group.

**Additional fields:** `runner_group_id`

**Reference:** [Managing access to self-hosted runners using groups](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#moving-a-self-hosted-runner-to-a-group)

#### `enterprise.runner_group_runners_updated`

A GitHub Actions runner group's list of members was updated.

**Additional fields:** `oauth_application_id`, `runner_group_id`

**Reference:** /rest/actions#set-self-hosted-runners-in-a-group-for-an-organization

#### `enterprise.runner_group_updated`

The configuration of a GitHub Actions self-hosted runner group was changed.

**Additional fields:** `runner_group_id`, `runner_group_name`, `runner_group_allow_public`, `runner_group_restricted_to_workflows`, `runner_group_selected_workflow_refs`, `network_configuration_id`

**Reference:** [Managing access to self-hosted runners using groups](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#changing-the-access-policy-of-a-self-hosted-runner-group)

#### `enterprise.runner_group_visiblity_updated`

The visibility of a GitHub Actions self-hosted runner group was updated via the REST API.

**Additional fields:** `runner_group_id`, `visibility`

**Reference:** /rest/actions#update-a-self-hosted-runner-group-for-an-organization

#### `enterprise.self_hosted_runner_offline`

The GitHub Actions runner application was stopped. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `runner_id`, `runner_name`

**Reference:** [Monitoring and troubleshooting self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/monitoring-and-troubleshooting-self-hosted-runners#checking-the-status-of-a-self-hosted-runner)

#### `enterprise.self_hosted_runner_online`

The GitHub Actions runner application was started. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `runner_id`, `runner_name`

**Reference:** [Monitoring and troubleshooting self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/monitoring-and-troubleshooting-self-hosted-runners#checking-the-status-of-a-self-hosted-runner)

#### `enterprise.self_hosted_runner_updated`

The GitHub Actions runner application was updated. This event is not included in the JSON/CSV export.

**Additional fields:** `runner_id`, `runner_name`, `source_version`, `target_version`, `runner_group_id`, `runner_group_name`

**Reference:** [Self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners#about-self-hosted-runners)

### enterprise\_announcement

#### `enterprise_announcement.create`

A global announcement banner was created for the enterprise.

**Additional fields:** `owner`, `owner_type`, `message`

**Reference:** [Customizing user messages for your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/communicating-information-to-users-in-your-enterprise/customizing-user-messages-for-your-enterprise#creating-a-global-announcement-banner)

#### `enterprise_announcement.destroy`

A global announcement banner was removed from the enterprise.

**Additional fields:** `owner`, `owner_type`

**Reference:** [Customizing user messages for your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/communicating-information-to-users-in-your-enterprise/customizing-user-messages-for-your-enterprise)

#### `enterprise_announcement.update`

A global announcement banner was updated for the enterprise.

**Additional fields:** `owner`, `owner_type`, `message`, `old_message`

**Reference:** [Customizing user messages for your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/communicating-information-to-users-in-your-enterprise/customizing-user-messages-for-your-enterprise)

### enterprise\_domain

#### `enterprise_domain.approve`

A domain was approved for an enterprise.

**Additional fields:** `owner_type`, `domain_name`, `owner`

**Reference:** [Verifying or approving a domain for your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-your-enterprise/verifying-or-approving-a-domain-for-your-enterprise#approving-a-domain-for-your-enterprise-account)

#### `enterprise_domain.create`

A domain was added to an enterprise.

**Additional fields:** `owner_type`, `domain_name`, `owner`

**Reference:** [Verifying or approving a domain for your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-your-enterprise/verifying-or-approving-a-domain-for-your-enterprise#verifying-a-domain-for-your-enterprise-account)

#### `enterprise_domain.destroy`

A domain was removed from an enterprise.

**Additional fields:** `owner_type`, `domain_name`, `owner`

**Reference:** [Verifying or approving a domain for your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-your-enterprise/verifying-or-approving-a-domain-for-your-enterprise#removing-an-approved-or-verified-domain)

#### `enterprise_domain.verify`

A domain was verified for an enterprise.

**Additional fields:** `owner_type`, `domain_name`, `owner`

**Reference:** [Verifying or approving a domain for your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-your-enterprise/verifying-or-approving-a-domain-for-your-enterprise#verifying-a-domain-for-your-enterprise-account)

### enterprise\_installation

#### `enterprise_installation.create`

The GitHub App associated with a GitHub Connect connection was created.

**Reference:** [Enabling GitHub Connect for GitHub.com](/en/enterprise-cloud@latest/admin/configuration/configuring-github-connect/managing-github-connect)

#### `enterprise_installation.destroy`

The GitHub App associated with a GitHub Connect connection was deleted.

**Reference:** [Enabling GitHub Connect for GitHub.com](/en/enterprise-cloud@latest/admin/configuration/configuring-github-connect/managing-github-connect)

### enterprise\_role

#### `enterprise_role.assign`

An enterprise role was assigned to a user or enterprise team.

**Additional fields:** `enterprise_role_id`, `enterprise_role_name`, `actor_is_bot`

**Reference:** [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/roles-in-an-enterprise)

#### `enterprise_role.create`

A custom enterprise role was created in an enterprise.

**Additional fields:** `name`, `owner`, `role_permissions`, `base_role`, `actor_is_bot`

**Reference:** [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/roles-in-an-enterprise)

#### `enterprise_role.destroy`

A custom enterprise role was deleted in an enterprise.

**Additional fields:** `name`, `owner`, `role_permissions`, `base_role`, `actor_is_bot`

**Reference:** [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/roles-in-an-enterprise)

#### `enterprise_role.revoke`

A user or enterprise team was unassigned an enterprise role.

**Additional fields:** `enterprise_role_id`, `enterprise_role_name`, `actor_is_bot`

**Reference:** [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/roles-in-an-enterprise)

#### `enterprise_role.update`

A custom enterprise role was edited in an enterprise.

**Additional fields:** `name`, `owner`, `role_permissions`, `base_role`, `old_role_permissions`, `actor_is_bot`

**Reference:** [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/roles-in-an-enterprise)

### enterprise\_team

#### `enterprise_team.add_member`

A new member was added to the enterprise team or an IdP group linked to an enterprise team, or an IdP group was linked to an enterprise team.

**Additional fields:** `enterprise_team_id`, `enterprise_team`

#### `enterprise_team.copilot_assignment`

A license for GitHub Copilot was assigned to an enterprise team.

**Additional fields:** `enterprise_team_id`, `enterprise_team`, `actor_is_bot`

#### `enterprise_team.copilot_unassignment`

A license for GitHub Copilot was unassigned from an enterprise team.

**Additional fields:** `enterprise_team_id`, `enterprise_team`, `actor_is_bot`

#### `enterprise_team.create`

A new enterprise team was created.

**Additional fields:** `enterprise_team_id`, `enterprise_team`

#### `enterprise_team.destroy`

An enterprise team was deleted.

**Additional fields:** `enterprise_team_id`, `enterprise_team`, `actor_is_bot`

#### `enterprise_team.remove_member`

A member was removed from the enterprise team or an IdP group linked to an enterprise team, or an IdP group was unlinked from an enterprise team.

**Additional fields:** `enterprise_team_id`, `enterprise_team`

#### `enterprise_team.rename`

The name of an enterprise team was changed.

**Additional fields:** `name`, `enterprise_team_id`, `enterprise_team`, `actor_is_bot`

### environment

#### `environment.add_protection_rule`

A GitHub Actions deployment protection rule was created via the API.

**Additional fields:** `name`

**Reference:** [Managing environments for deployment](/en/enterprise-cloud@latest/actions/deployment/targeting-different-environments/using-environments-for-deployment#deployment-protection-rules)

#### `environment.create_actions_secret`

A secret was created for a GitHub Actions environment.

**Additional fields:** `oauth_application_id`, `key`, `visibility`, `public_repo`

**Reference:** [Managing environments for deployment](/en/enterprise-cloud@latest/actions/deployment/targeting-different-environments/using-environments-for-deployment#environment-secrets)

#### `environment.create_actions_variable`

A variable was created for a GitHub Actions environment.

**Additional fields:** `key`, `visibility`, `environment_name`, `public_repo`, `actor_is_bot`

**Reference:** [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-an-environment)

#### `environment.delete`

An environment was deleted.

**Additional fields:** `name`, `public_repo`, `actor_is_bot`

**Reference:** [Managing environments for deployment](/en/enterprise-cloud@latest/actions/deployment/targeting-different-environments/using-environments-for-deployment#deleting-an-environment)

#### `environment.remove_actions_secret`

A secret was deleted for a GitHub Actions environment.

**Additional fields:** `oauth_application_id`, `key`, `public_repo`

**Reference:** [Managing environments for deployment](/en/enterprise-cloud@latest/actions/deployment/targeting-different-environments/using-environments-for-deployment#environment-secrets)

#### `environment.remove_actions_variable`

A variable was deleted for a GitHub Actions environment.

**Additional fields:** `key`, `environment_name`, `public_repo`

**Reference:** [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-an-environment)

#### `environment.remove_protection_rule`

A GitHub Actions deployment protection rule was deleted via the API.

**Additional fields:** `name`, `public_repo`

**Reference:** [Managing environments for deployment](/en/enterprise-cloud@latest/actions/deployment/targeting-different-environments/using-environments-for-deployment#deployment-protection-rules)

#### `environment.update_actions_secret`

A secret was updated for a GitHub Actions environment.

**Additional fields:** `oauth_application_id`, `key`, `visibility`, `public_repo`

**Reference:** [Managing environments for deployment](/en/enterprise-cloud@latest/actions/deployment/targeting-different-environments/using-environments-for-deployment#environment-secrets)

#### `environment.update_actions_variable`

A variable was updated for a GitHub Actions environment.

**Additional fields:** `key`, `visibility`, `environment_name`, `public_repo`

**Reference:** [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-an-environment)

#### `environment.update_protection_rule`

A GitHub Actions deployment protection rule was updated via the API.

**Additional fields:** `new_value`, `approvers_was`, `approvers`, `can_admins_bypass`, `prevent_self_review`

**Reference:** [Managing environments for deployment](/en/enterprise-cloud@latest/actions/deployment/targeting-different-environments/using-environments-for-deployment#deployment-protection-rules)

### external\_group

#### `external_group.add_member`

A user was added to an external group.

**Additional fields:** `external_group`, `external_group_id`, `scim_group_id`

#### `external_group.delete`

An external group was deleted.

**Additional fields:** `oauth_application_id`, `scim_group_id`

#### `external_group.link`

An external group was linked to a GitHub team.

**Additional fields:** `external_group_id`, `external_group`, `scim_group_id`

#### `external_group.provision`

An external group was created.

**Additional fields:** `oauth_application_id`

#### `external_group.remove_member`

A user was removed from an external group.

**Additional fields:** `external_group`, `external_group_id`

#### `external_group.scim_api_failure`

Failed external group SCIM API request.

**Additional fields:** `request_method`, `query_string`, `api_request_body`, `route`, `status_code`, `url_path`, `scim_group_id`, `message`, `actor_is_bot`

**Reference:** [REST API endpoints for SCIM](/en/enterprise-cloud@latest/rest/scim/scim)

#### `external_group.scim_api_success`

Successful external group SCIM API request. Excludes GET API requests.

**Additional fields:** `request_method`, `query_string`, `api_request_body`, `route`, `status_code`, `url_path`, `scim_group_id`, `actor_is_bot`

**Reference:** [REST API endpoints for SCIM](/en/enterprise-cloud@latest/rest/scim/scim)

#### `external_group.unlink`

An external group was unlinked to a GitHub team.

**Additional fields:** `external_group_id`, `external_group`

#### `external_group.update`

An external group was updated.

**Additional fields:** `oauth_application_id`, `scim_group_id`

#### `external_group.update_display_name`

An external group's display name was updated.

**Additional fields:** `external_group_id`, `external_group`, `scim_group_id`

### external\_identity

#### `external_identity.deprovision`

An external identity was deprovisioned, suspending the linked GitHub user.

**Additional fields:** `oauth_application_id`

#### `external_identity.provision`

An external identity was created and linked to a GitHub user.

**Additional fields:** `scim_user_id`

#### `external_identity.scim_api_failure`

Failed external identity SCIM API request.

**Additional fields:** `request_method`, `query_string`, `api_request_body`, `route`, `status_code`, `url_path`, `scim_user_id`, `message`, `actor_is_bot`

**Reference:** [REST API endpoints for SCIM](/en/enterprise-cloud@latest/rest/scim/scim)

#### `external_identity.scim_api_success`

Successful external identity SCIM API request. Excludes GET API requests.

**Additional fields:** `request_method`, `query_string`, `api_request_body`, `route`, `status_code`, `url_path`, `scim_user_id`, `actor_is_bot`

**Reference:** [REST API endpoints for SCIM](/en/enterprise-cloud@latest/rest/scim/scim)

#### `external_identity.update`

An external identity was updated.

**Additional fields:** `scim_user_id`

### git

Note: Git events have special access requirements and retention policies that differ from other audit log events. For GitHub Enterprise Cloud, access Git events via the REST API only with 7-day retention. For GitHub Enterprise Server, Git events must be enabled in audit log configuration and are not included in search results.

#### `git.clone`

A repository was cloned. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `transport_protocol`, `repository_public`, `transport_protocol_name`

#### `git.fetch`

Changes were fetched from a repository. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `transport_protocol`, `repository_public`, `transport_protocol_name`

#### `git.push`

Changes were pushed to a repository. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `transport_protocol`, `repository_public`, `transport_protocol_name`

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

**Reference:** [About webhooks](/en/enterprise-cloud@latest/get-started/exploring-integrations/about-webhooks)

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

### integration\_installation\_request

#### `integration_installation_request.close`

A request to install a GitHub App was either approved or denied by an owner, or canceled by the member who opened the request.

**Additional fields:** `url`, `integration`, `reason`, `application_client_id`

**Reference:** /apps/using-github-apps/requesting-a-github-app-from-your-organization-owner

#### `integration_installation_request.create`

A member requested that an owner install a GitHub App.

**Additional fields:** `requester`, `url`, `integration`, `application_client_id`

**Reference:** /apps/using-github-apps/requesting-a-github-app-from-your-organization-owner

### ip\_allow\_list

#### `ip_allow_list.disable`

An IP allow list was disabled.

#### `ip_allow_list.disable_for_installed_apps`

An IP allow list was disabled for installed GitHub Apps.

#### `ip_allow_list.disable_idp_ip_allowlist_for_web`

Identity Provider based IP allow list for web interactions was disabled.

**Additional fields:** `actor_is_bot`

#### `ip_allow_list.disable_user_level_enforcement`

IP allow list user level enforcement was disabled.

#### `ip_allow_list.enable`

An IP allow list was enabled.

#### `ip_allow_list.enable_for_installed_apps`

An IP allow list was enabled for installed GitHub Apps.

#### `ip_allow_list.enable_idp_ip_allowlist_for_web`

Identity Provider based IP allow list for web interactions was enabled.

**Additional fields:** `actor_is_bot`

#### `ip_allow_list.enable_user_level_enforcement`

IP allow list user level enforcement was enabled.

### ip\_allow\_list\_entry

#### `ip_allow_list_entry.create`

An IP address was added to an IP allow list.

**Additional fields:** `active`, `ip_allow_list_entry`

#### `ip_allow_list_entry.destroy`

An IP address was deleted from an IP allow list.

**Additional fields:** `ip_allow_list_entry`, `active`

#### `ip_allow_list_entry.update`

An IP address or its description was changed.

**Additional fields:** `ip_allow_list_entry`, `active`

### issue

#### `issue.destroy`

An issue was deleted from the repository.

**Additional fields:** `title`

**Reference:** [Deleting an issue](/en/enterprise-cloud@latest/issues/tracking-your-work-with-issues/deleting-an-issue)

#### `issue.pinned`

An issue was pinned to a repository.

**Additional fields:** `owner_type`, `number`, `event`

**Reference:** [Pinning an issue to your repository](/en/enterprise-cloud@latest/issues/tracking-your-work-with-issues/pinning-an-issue-to-your-repository)

#### `issue.transfer`

An issue was transferred to another repository.

**Additional fields:** `owner_type`, `number`

**Reference:** [Transferring an issue to another repository](/en/enterprise-cloud@latest/issues/tracking-your-work-with-issues/transferring-an-issue-to-another-repository)

#### `issue.unpinned`

An issue was unpinned from a repository.

**Additional fields:** `event`, `number`, `owner_type`

**Reference:** [Pinning an issue to your repository](/en/enterprise-cloud@latest/issues/tracking-your-work-with-issues/pinning-an-issue-to-your-repository)

### issue\_comment

#### `issue_comment.destroy`

A comment on an issue was deleted from the repository.

**Additional fields:** `oauth_application_id`

#### `issue_comment.pinned`

A comment on an issue was pinned to a repository.

**Additional fields:** `oauth_application_id`, `public_repo`, `actor_is_bot`

#### `issue_comment.unpinned`

A comment on an issue was unpinned from a repository.

**Additional fields:** `public_repo`, `actor_is_bot`

#### `issue_comment.update`

A comment on an issue (other than the initial one) changed.

**Additional fields:** `oauth_application_id`

### issues

#### `issues.deletes_disabled`

The ability for enterprise members to delete issues was disabled  Members cannot delete issues in any organizations in an enterprise.

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-deleting-issues)

#### `issues.deletes_enabled`

The ability for enterprise members to delete issues was enabled  Members can delete issues in any organizations in an enterprise.

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-deleting-issues)

#### `issues.deletes_policy_cleared`

An enterprise owner cleared the policy setting for allowing members to delete issues in an enterprise.

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-deleting-issues)

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

### members\_can\_create\_pages

For more information, see "Managing the publication of GitHub Pages sites for your organization."

#### `members_can_create_pages.disable`

The ability for members to publish GitHub Pages sites was disabled.

**Reference:** /organizations/managing-organization-settings/managing-the-publication-of-github-pages-sites-for-your-organization

#### `members_can_create_pages.enable`

The ability for members to publish GitHub Pages sites was enabled.

**Reference:** /organizations/managing-organization-settings/managing-the-publication-of-github-pages-sites-for-your-organization

### members\_can\_create\_public\_pages

#### `members_can_create_public_pages.disable`

The ability for members to publish public GitHub Pages was disabled  Members cannot publish public GitHub Pages in an organization.

**Reference:** /organizations/managing-organization-settings/managing-the-publication-of-github-pages-sites-for-your-organization

#### `members_can_create_public_pages.enable`

The ability for members to publish public GitHub Pages was enabled  Members can publish public GitHub Pages in an organization.

**Reference:** /organizations/managing-organization-settings/managing-the-publication-of-github-pages-sites-for-your-organization

### members\_can\_delete\_repos

#### `members_can_delete_repos.clear`

An enterprise owner cleared the policy setting for deleting or transferring repositories in any organizations in an enterprise.

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-repository-deletion-and-transfer)

#### `members_can_delete_repos.disable`

The ability for enterprise members to delete repositories was disabled  Members cannot delete or transfer repositories in any organizations in an enterprise.

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-repository-deletion-and-transfer)

#### `members_can_delete_repos.enable`

The ability for enterprise members to delete repositories was enabled  Members can delete or transfer repositories in any organizations in an enterprise.

**Reference:** [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-repository-deletion-and-transfer)

### members\_can\_view\_dependency\_insights

#### `members_can_view_dependency_insights.clear`

An enterprise owner cleared the policy setting for viewing dependency insights in any organizations in an enterprise.

#### `members_can_view_dependency_insights.disable`

The ability for enterprise members to view dependency insights was disabled. Members cannot view dependency insights in any organizations in an enterprise.

**Reference:** [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-dependency-insights-in-your-enterprise)

#### `members_can_view_dependency_insights.enable`

The ability for enterprise members to view dependency insights was enabled. Members can view dependency insights in any organizations in an enterprise.

**Reference:** [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-dependency-insights-in-your-enterprise)

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

#### `migration.destroy_file`

A migration file for transferring data from a source location (such as a GitHub.com organization or a GitHub Enterprise Server instance) to a target GitHub Enterprise Server instance was deleted.

#### `migration.download`

A migration file for transferring data from a source location (such as a GitHub.com organization or a GitHub Enterprise Server instance) to a target GitHub Enterprise Server instance was downloaded.

**Additional fields:** `oauth_application_id`, `actor_is_bot`

### network\_configuration

#### `network_configuration.create`

A network configuration for a hosted compute service was created.

**Additional fields:** `actor_is_bot`, `selected_service`, `network_settings_ids`, `previous_settings_ids`, `network_configuration_id`, `failover_network_settings_ids`, `failover_network_enabled`

**Reference:** [About networking for hosted compute products in your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-private-networking-for-hosted-compute-products/about-networking-for-hosted-compute-products)

#### `network_configuration.delete`

A network configuration for a hosted compute service was deleted.

**Additional fields:** `actor_is_bot`, `network_configuration_id`

**Reference:** [About networking for hosted compute products in your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-private-networking-for-hosted-compute-products/about-networking-for-hosted-compute-products)

#### `network_configuration.update`

A network configuration for a hosted compute service was updated.

**Additional fields:** `actor_is_bot`, `selected_service`, `network_settings_ids`, `previous_settings_ids`, `failover_network_settings_ids`, `failover_network_enabled`

**Reference:** [About networking for hosted compute products in your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-private-networking-for-hosted-compute-products/about-networking-for-hosted-compute-products)

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

### org

#### `org.accept_business_invitation`

An invitation sent to an organization to join an enterprise was accepted.

**Reference:** [Adding organizations to your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-organizations-in-your-enterprise/adding-organizations-to-your-enterprise#inviting-an-organization-to-join-your-enterprise-account)

#### `org.add_billing_manager`

A billing manager was added to an organization.

**Reference:** /organizations/managing-peoples-access-to-your-organization-with-roles/adding-a-billing-manager-to-your-organization

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

#### `org.advanced_security_entity_policy_update`

An enterprise owner updated the GitHub Advanced Security access policy for repositories owned by the organization.

**Additional fields:** `new_policy`, `actor_is_bot`

**Reference:** [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-advanced-security-in-your-enterprise)

#### `org.advanced_security_policy_selected_member_disabled`

An enterprise owner prevented GitHub Advanced Security features from being enabled for repositories owned by the organization.

**Reference:** [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-advanced-security-in-your-enterprise)

#### `org.advanced_security_policy_selected_member_enabled`

An enterprise owner allowed GitHub Advanced Security features to be enabled for repositories owned by the organization.

**Additional fields:** `actor_is_bot`

**Reference:** [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-advanced-security-in-your-enterprise)

#### `org.audit_log_export`

An export of the organization audit log was created. If the export included a query, the log will list the query used and the number of audit log entries matching that query.

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/reviewing-the-audit-log-for-your-organization#exporting-the-audit-log

#### `org.audit_log_git_event_export`

An export of the organization's Git events was created.

**Additional fields:** `start`, `end`

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/audit-log-events-for-your-organization

#### `org.block_user`

An organization owner blocked a user from accessing the organization's repositories.

**Additional fields:** `blocked_user`

**Reference:** /communities/maintaining-your-safety-on-github/blocking-a-user-from-your-organization

#### `org.cancel_business_invitation`

An invitation for an organization to join an enterprise was revoked

**Additional fields:** `initiated_from`

**Reference:** [Adding organizations to your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-organizations-in-your-enterprise/adding-organizations-to-your-enterprise#inviting-an-organization-to-join-your-enterprise-account)

#### `org.cancel_invitation`

An invitation sent to a user to join an organization was revoked.

**Additional fields:** `email`, `invitation_id`, `invitee_email`

#### `org.code_scanning_autofix_disabled`

Autofix for code scanning alerts was disabled for an organization.

**Additional fields:** `actor_is_bot`

#### `org.code_scanning_autofix_enabled`

Autofix for code scanning alerts was enabled for an organization.

**Additional fields:** `actor_is_bot`

#### `org.code_scanning_autofix_third_party_tools_disabled`

Autofix for third party tools for code scanning alerts was disabled for an organization.

**Additional fields:** `actor_is_bot`

#### `org.code_scanning_autofix_third_party_tools_enabled`

Autofix for third party tools for code scanning alerts was enabled for an organization.

**Additional fields:** `actor_is_bot`

#### `org.codeql_disabled`

Code scanning using the default setup was disabled for an organization.

**Reference:** [Configuring default setup for code scanning at scale](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning-at-scale)

#### `org.codeql_enabled`

Code scanning using the default setup was enabled for an organization.

**Reference:** [Configuring default setup for code scanning at scale](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning-at-scale)

#### `org.codespaces_access_updated`

Access to use Codespaces on internal and private repositories was updated for an organization.

**Additional fields:** `enablement`

**Reference:** /codespaces/managing-codespaces-for-your-organization/enabling-or-disabling-github-codespaces-for-your-organization

#### `org.codespaces_ownership_updated`

Ownership and payment for codespaces was updated for an organization.

**Additional fields:** `owner_type`

**Reference:** /codespaces/managing-codespaces-for-your-organization/choosing-who-owns-and-pays-for-codespaces-in-your-organization

#### `org.codespaces_team_access_allowed`

A team has been allowed to use Codespaces for an organization.

**Additional fields:** `team`

#### `org.codespaces_team_access_revoked`

A team has been prevented from using Codespaces for an organization.

**Additional fields:** `team`

#### `org.codespaces_trusted_repo_access_granted`

GitHub Codespaces was granted trusted repository access to all other repositories in an organization.

**Reference:** [Managing access to other repositories within your codespace](/en/enterprise-cloud@latest/codespaces/managing-codespaces-for-your-organization/managing-repository-access-for-your-organizations-codespaces)

#### `org.codespaces_trusted_repo_access_revoked`

GitHub Codespaces trusted repository access to all other repositories in an organization was revoked.

**Reference:** [Managing access to other repositories within your codespace](/en/enterprise-cloud@latest/codespaces/managing-codespaces-for-your-organization/managing-repository-access-for-your-organizations-codespaces)

#### `org.codespaces_user_access_allowed`

A user has been allowed to use Codespaces for an organization.

#### `org.codespaces_user_access_revoked`

A user has been prevented from using Codespaces for an organization.

#### `org.config.disable_collaborators_only`

The interaction limit for collaborators only for an organization was disabled.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-organization#limiting-interactions-in-your-organization

#### `org.config.disable_contributors_only`

The interaction limit for prior contributors only for an organization was disabled.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-organization#limiting-interactions-in-your-organization

#### `org.config.disable_sockpuppet_disallowed`

The interaction limit for existing users only for an organization was disabled.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-organization#limiting-interactions-in-your-organization

#### `org.config.enable_collaborators_only`

The interaction limit for collaborators only for an organization was enabled.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-organization#limiting-interactions-in-your-organization

#### `org.config.enable_contributors_only`

The interaction limit for prior contributors only for an organization was enabled.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-organization#limiting-interactions-in-your-organization

#### `org.config.enable_sockpuppet_disallowed`

The interaction limit for existing users only for an organization was enabled.

**Reference:** /communities/moderating-comments-and-conversations/limiting-interactions-in-your-organization#limiting-interactions-in-your-organization

#### `org.configure_self_hosted_jit_runner`

A new just-in-time GitHub Actions self-hosted runner was configured

**Reference:** /rest/actions/self-hosted-runners#create-configuration-for-a-just-in-time-runner-for-an-organization

#### `org.confirm_business_invitation`

An invitation for an organization to join an enterprise was confirmed.

**Reference:** [Adding organizations to your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-organizations-in-your-enterprise/adding-organizations-to-your-enterprise#inviting-an-organization-to-join-your-enterprise-account)

#### `org.create`

An organization was created.

**Reference:** /organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch

#### `org.create_actions_secret`

A GitHub Actions secret was created for an organization.

**Additional fields:** `key`

**Reference:** [Using secrets in GitHub Actions](/en/enterprise-cloud@latest/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-an-organization)

#### `org.create_actions_variable`

A GitHub Actions variable was created for an organization.

**Additional fields:** `key`, `visibility`

**Reference:** [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-an-organization)

#### `org.create_integration_secret`

A Codespaces or Dependabot secret was created for an organization.

**Additional fields:** `key`, `visibility`, `integration`

#### `org.delete`

An organization was deleted by a user or staff.

#### `org.disable_member_team_creation_permission`

Team creation was limited to owners.

**Reference:** /organizations/managing-organization-settings/setting-team-creation-permissions-in-your-organization

#### `org.disable_oauth_app_restrictions`

Third-party application access restrictions for an organization were disabled.

**Reference:** /organizations/managing-oauth-access-to-your-organizations-data/disabling-oauth-app-access-restrictions-for-your-organization

#### `org.disable_reader_discussion_creation_permission`

An organization owner limited discussion creation to users with at least triage permission in an organization.

**Reference:** /organizations/managing-organization-settings/managing-discussion-creation-for-repositories-in-your-organization

#### `org.disable_saml`

SAML single sign-on was disabled for an organization.

**Additional fields:** `sso_url`, `issuer`

#### `org.disable_two_factor_requirement`

A two-factor authentication requirement was disabled for the organization.

#### `org.display_commenter_full_name_disabled`

An organization owner disabled the display of a commenter's full name in an organization. Members cannot see a comment author's full name.

#### `org.display_commenter_full_name_enabled`

An organization owner enabled the display of a commenter's full name in an organization. Members can see a comment author's full name.

#### `org.enable_member_team_creation_permission`

Team creation by members was allowed.

**Reference:** /organizations/managing-organization-settings/setting-team-creation-permissions-in-your-organization

#### `org.enable_oauth_app_restrictions`

Third-party application access restrictions for an organization were enabled.

**Reference:** /organizations/managing-oauth-access-to-your-organizations-data/enabling-oauth-app-access-restrictions-for-your-organization

#### `org.enable_reader_discussion_creation_permission`

An organization owner allowed users with read access to create discussions in an organization

**Reference:** /organizations/managing-organization-settings/managing-discussion-creation-for-repositories-in-your-organization

#### `org.enable_saml`

SAML single sign-on was enabled for the organization.

**Additional fields:** `sso_url`, `issuer`

**Reference:** [Enabling and testing SAML single sign-on for your organization](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/enabling-and-testing-saml-single-sign-on-for-your-organization)

#### `org.enable_two_factor_requirement`

Two-factor authentication is now required for the organization.

**Reference:** /organizations/keeping-your-organization-secure/managing-two-factor-authentication-for-your-organization/requiring-two-factor-authentication-in-your-organization

#### `org.integration_manager_added`

An organization owner granted a member access to manage all GitHub Apps owned by an organization.

**Additional fields:** `manager`

#### `org.integration_manager_removed`

An organization owner removed access to manage all GitHub Apps owned by an organization from an organization member.

**Additional fields:** `manager`

#### `org.invite_member`

A new user was invited to join an organization.

**Additional fields:** `invitation_id`, `invitee_email`

**Reference:** /organizations/managing-membership-in-your-organization/inviting-users-to-join-your-organization

#### `org.invite_to_business`

An organization was invited to join an enterprise.

#### `org.members_can_update_protected_branches.disable`

The ability for enterprise members to update protected branches was disabled. Only enterprise owners can update protected branches.

#### `org.members_can_update_protected_branches.enable`

The ability for enterprise members to update protected branches was enabled. Members of an organization can update protected branches.

#### `org.members_limit_warning`

An organization is approaching its members limit.

**Additional fields:** `limit`, `count`, `actor_is_bot`

#### `org.oauth_app_access_approved`

Access to an organization was granted for an OAuth App.

**Additional fields:** `url`, `oauth_application_name`

**Reference:** /organizations/managing-oauth-access-to-your-organizations-data/approving-oauth-apps-for-your-organization

#### `org.oauth_app_access_denied`

Access was disabled for an OAuth App that was previously approved.

**Additional fields:** `url`, `oauth_application_name`

**Reference:** /organizations/managing-oauth-access-to-your-organizations-data/denying-access-to-a-previously-approved-oauth-app-for-your-organization

#### `org.oauth_app_access_requested`

An organization member requested that an owner grant an OAuth App access to an organization.

**Additional fields:** `url`, `oauth_application_name`

#### `org.recovery_code_failed`

An organization owner failed to sign into a organization with an external identity provider (IdP) using a recovery code.

**Additional fields:** `reason`

**Reference:** [Accessing your organization if your identity provider is unavailable](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/accessing-your-organization-if-your-identity-provider-is-unavailable)

#### `org.recovery_code_used`

An organization owner successfully signed into an organization with an external identity provider (IdP) using a recovery code.

**Reference:** [Accessing your organization if your identity provider is unavailable](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/accessing-your-organization-if-your-identity-provider-is-unavailable)

#### `org.recovery_codes_downloaded`

An organization owner downloaded the organization's SSO recovery codes.

**Reference:** [Downloading your organization's SAML single sign-on recovery codes](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/downloading-your-organizations-saml-single-sign-on-recovery-codes)

#### `org.recovery_codes_generated`

An organization owner generated the organization's SSO recovery codes.

**Reference:** [Downloading your organization's SAML single sign-on recovery codes](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/downloading-your-organizations-saml-single-sign-on-recovery-codes)

#### `org.recovery_codes_printed`

An organization owner printed the organization's SSO recovery codes.

**Reference:** [Downloading your organization's SAML single sign-on recovery codes](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/downloading-your-organizations-saml-single-sign-on-recovery-codes)

#### `org.recovery_codes_viewed`

An organization owner viewed the organization's SSO recovery codes.

**Reference:** [Downloading your organization's SAML single sign-on recovery codes](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/downloading-your-organizations-saml-single-sign-on-recovery-codes)

#### `org.register_self_hosted_runner`

A new self-hosted runner was registered.

**Additional fields:** `actor_is_bot`

**Reference:** [Adding self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners#adding-a-self-hosted-runner-to-an-organization)

#### `org.remove_actions_secret`

A GitHub Actions secret was removed from an organization.

**Additional fields:** `key`

**Reference:** [Using secrets in GitHub Actions](/en/enterprise-cloud@latest/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-an-organization)

#### `org.remove_actions_variable`

A GitHub Actions variable was removed from an organization.

**Additional fields:** `key`

**Reference:** [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-an-organization)

#### `org.remove_billing_manager`

A billing manager was removed from an organization, either manually or due to a two-factor authentication requirement.

**Reference:** /organizations/managing-peoples-access-to-your-organization-with-roles/removing-a-billing-manager-from-your-organization, /organizations/keeping-your-organization-secure/managing-two-factor-authentication-for-your-organization/requiring-two-factor-authentication-in-your-organization

#### `org.remove_integration_secret`

A Codespaces or Dependabot secret was removed from an organization.

**Additional fields:** `key`, `integration`

#### `org.remove_member`

A member was removed from an organization, either manually or due to a two-factor authentication requirement.

#### `org.remove_outside_collaborator`

An outside collaborator was removed from an organization, either manually or due to a two-factor authentication requirement.

#### `org.remove_self_hosted_runner`

A self-hosted runner was removed.

**Reference:** [Removing self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/removing-self-hosted-runners#removing-a-runner-from-an-organization)

#### `org.rename`

An organization was renamed.

**Additional fields:** `old_login`

#### `org.required_workflow_create`

Triggered when a required workflow is created.

**Reference:** /actions/using-workflows/required-workflows

#### `org.required_workflow_delete`

Triggered when a required workflow is deleted.

**Reference:** /actions/using-workflows/required-workflows

#### `org.required_workflow_update`

Triggered when a required workflow is updated.

**Reference:** /actions/using-workflows/required-workflows

#### `org.restore_member`

An organization member was restored.

**Reference:** /organizations/managing-membership-in-your-organization/reinstating-a-former-member-of-your-organization

#### `org.runner_group_created`

A self-hosted runner group was created.

**Additional fields:** `runner_group_id`, `runner_group_restricted_to_workflows`, `runner_group_selected_workflow_refs`, `network_configuration_id`

**Reference:** [Managing access to self-hosted runners using groups](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#creating-a-self-hosted-runner-group-for-an-organization)

#### `org.runner_group_removed`

A self-hosted runner group was removed.

**Additional fields:** `runner_group_id`

**Reference:** [Managing access to self-hosted runners using groups](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#removing-a-self-hosted-runner-group)

#### `org.runner_group_renamed`

A self-hosted runner group was renamed.

**Additional fields:** `runner_group_id`

**Reference:** [Managing access to self-hosted runners using groups](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#changing-the-access-policy-of-a-self-hosted-runner-group)

#### `org.runner_group_runner_removed`

The REST API was used to remove a self-hosted runner from a group.

**Additional fields:** `oauth_application_id`, `runner_group_id`, `runner_id`

**Reference:** /rest/actions#remove-a-self-hosted-runner-from-a-group-for-an-organization

#### `org.runner_group_runners_added`

A self-hosted runner was added to a group.

**Additional fields:** `runner_group_id`

**Reference:** [Managing access to self-hosted runners using groups](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#moving-a-self-hosted-runner-to-a-group)

#### `org.runner_group_runners_updated`

A runner group's list of members was updated.

**Additional fields:** `oauth_application_id`, `runner_group_id`

**Reference:** /rest/actions#set-self-hosted-runners-in-a-group-for-an-organization

#### `org.runner_group_updated`

The configuration of a self-hosted runner group was changed.

**Additional fields:** `runner_group_id`, `runner_group_name`, `runner_group_allow_public`, `runner_group_restricted_to_workflows`, `runner_group_selected_workflow_refs`, `network_configuration_id`

**Reference:** [Managing access to self-hosted runners using groups](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#changing-the-access-policy-of-a-self-hosted-runner-group)

#### `org.runner_group_visiblity_updated`

The visibility of a self-hosted runner group was updated via the REST API.

**Additional fields:** `runner_group_id`, `visibility`

**Reference:** /rest/actions#update-a-self-hosted-runner-group-for-an-organization

#### `org.secret_scanning_custom_pattern_push_protection_disabled`

Push protection for a custom pattern for secret scanning was disabled for an organization.

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-an-organization)

#### `org.secret_scanning_custom_pattern_push_protection_enabled`

Push protection for a custom pattern for secret scanning was enabled for an organization.

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-an-organization)

#### `org.secret_scanning_push_protection_custom_message_disabled`

The custom message triggered by an attempted push to a push-protected repository was disabled for an organization.

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/protecting-pushes-with-secret-scanning#enabling-secret-scanning-as-a-push-protection-for-an-organization)

#### `org.secret_scanning_push_protection_custom_message_enabled`

The custom message triggered by an attempted push to a push-protected repository was enabled for an organization.

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/protecting-pushes-with-secret-scanning#enabling-secret-scanning-as-a-push-protection-for-an-organization)

#### `org.secret_scanning_push_protection_custom_message_updated`

The custom message triggered by an attempted push to a push-protected repository was updated for an organization.

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/protecting-pushes-with-secret-scanning#enabling-secret-scanning-as-a-push-protection-for-an-organization)

#### `org.secret_scanning_push_protection_disable`

Push protection for secret scanning was disabled.

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/protecting-pushes-with-secret-scanning)

#### `org.secret_scanning_push_protection_enable`

Push protection for secret scanning was enabled.

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations)

#### `org.secret_scanning_push_protection_new_repos_disable`

Push protection for secret scanning was disabled for all new repositories in the organization.

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations)

#### `org.secret_scanning_push_protection_new_repos_enable`

Push protection for secret scanning was enabled for all new repositories in the organization.

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations)

#### `org.self_hosted_runner_offline`

The runner application was stopped. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `runner_id`, `runner_name`

**Reference:** [Monitoring and troubleshooting self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/monitoring-and-troubleshooting-self-hosted-runners#checking-the-status-of-a-self-hosted-runner)

#### `org.self_hosted_runner_online`

The runner application was started. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `runner_id`, `runner_name`

**Reference:** [Monitoring and troubleshooting self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/monitoring-and-troubleshooting-self-hosted-runners#checking-the-status-of-a-self-hosted-runner)

#### `org.self_hosted_runner_updated`

The runner application was updated. This event is not included in the JSON/CSV export.

**Additional fields:** `runner_id`, `runner_name`, `source_version`, `target_version`, `runner_group_id`, `runner_group_name`

**Reference:** [Self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners#about-self-hosted-runners)

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

#### `org.sso_response`

A SAML single sign-on (SSO) response was generated when a member attempted to authenticate with your organization. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `issuer`, `actor_is_bot`

#### `org.transfer`

An organization was transferred between enterprise accounts.

**Additional fields:** `from_business`, `to_business`

**Reference:** [Adding organizations to your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-organizations-in-your-enterprise/adding-organizations-to-your-enterprise#transferring-an-organization-between-enterprise-accounts)

#### `org.transfer_outgoing`

An organization was transferred between enterprise accounts.

**Additional fields:** `from_business`, `to_business`

**Reference:** [Adding organizations to your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/adding-organizations-to-your-enterprise#transferring-an-organization-between-enterprise-accounts)

#### `org.unblock_user`

A user was unblocked from an organization.

**Additional fields:** `oauth_application_id`, `blocked_user`

**Reference:** /communities/maintaining-your-safety-on-github/unblocking-a-user-from-your-organization

#### `org.update_actions_secret`

A GitHub Actions secret was updated for an organization.

**Additional fields:** `oauth_application_id`, `key`

**Reference:** [Using secrets in GitHub Actions](/en/enterprise-cloud@latest/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-an-organization)

#### `org.update_actions_settings`

An organization owner or site administrator updated GitHub Actions policy settings for an organization.

**Additional fields:** `new_policy`, `updated_allowed_types`, `old_policy`, `updated_access_policy`

**Reference:** /organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization

#### `org.update_actions_variable`

A GitHub Actions variable was updated for an organization.

**Additional fields:** `key`, `visibility`

**Reference:** [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-an-organization)

#### `org.update_default_repository_permission`

The default repository permission level for organization members was changed.

**Additional fields:** `permission`, `old_permission`

#### `org.update_immutable_releases_settings_policy`

The settings policy for immutable releases was updated for an organization.

**Additional fields:** `old_policy`, `new_policy`, `actor_is_bot`

#### `org.update_integration_secret`

A Codespaces or Dependabot secret was updated for an organization.

**Additional fields:** `key`, `visibility`, `integration`

#### `org.update_member`

A person's role was changed from owner to member or member to owner.

**Additional fields:** `old_permission`, `permission`

#### `org.update_member_repository_creation_permission`

The create repository permission for organization members was changed.

**Additional fields:** `permission`, `visibility`

#### `org.update_member_repository_invitation_permission`

An organization owner changed the policy setting for organization members inviting outside collaborators to repositories.

**Additional fields:** `permission`

**Reference:** [Setting permissions for adding outside collaborators](/en/enterprise-cloud@latest/organizations/managing-organization-settings/setting-permissions-for-adding-outside-collaborators)

#### `org.update_new_repository_default_branch_setting`

The name of the default branch was changed for new repositories in the organization.

**Reference:** /organizations/managing-organization-settings/managing-the-default-branch-name-for-repositories-in-your-organization

#### `org.update_saml_provider_settings`

An organization's SAML provider settings were updated.

**Additional fields:** `sso_url`, `issuer`

#### `org.update_terms_of_service`

An organization changed between the Standard Terms of Service and the GitHub Customer Agreement.

**Reference:** /organizations/managing-organization-settings/upgrading-to-the-github-customer-agreement

### org\_credential\_authorization

#### `org_credential_authorization.deauthorize`

A member removed the SSO (SAML or OIDC) authorization from a credential that had access to your organization.

**Additional fields:** `actor_is_bot`, `oauth_credential_type`, `managed_oauth_access_id`, `managed_token_id`, `managed_oauth_scopes`, `managed_token_scopes`, `managed_hashed_token`

**Reference:** [Authorizing a personal access token for use with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on/authorizing-a-personal-access-token-for-use-with-saml-single-sign-on)

#### `org_credential_authorization.grant`

A member authorized credentials for use with SAML or OIDC single sign-on.

**Additional fields:** `actor_is_bot`, `oauth_credential_type`, `managed_oauth_access_id`, `managed_token_id`, `managed_oauth_scopes`, `managed_token_scopes`, `managed_hashed_token`

**Reference:** [Authenticating with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on)

#### `org_credential_authorization.revoke`

An owner revoked authorized credentials.

**Additional fields:** `owner`, `oauth_application_id`, `oauth_credential_type`, `managed_oauth_access_id`, `managed_token_id`, `managed_oauth_scopes`, `managed_token_scopes`, `managed_hashed_token`

**Reference:** [Viewing and managing a member's SAML access to your organization](/en/enterprise-cloud@latest/organizations/granting-access-to-your-organization-with-saml-single-sign-on/viewing-and-managing-a-members-saml-access-to-your-organization)

### org\_secret\_scanning\_automatic\_validity\_checks

#### `org_secret_scanning_automatic_validity_checks.disabled`

Automatic partner validation checks have been disabled at the organization level

**Additional fields:** `actor_is_bot`

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization#allowing-validity-checks-for-partner-patterns-in-an-organization

#### `org_secret_scanning_automatic_validity_checks.enabled`

Automatic partner validation checks have been enabled at the organization level

**Additional fields:** `actor_is_bot`

**Reference:** /organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization#allowing-validity-checks-for-partner-patterns-in-an-organization

### org\_secret\_scanning\_custom\_pattern

#### `org_secret_scanning_custom_pattern.create`

A custom pattern was created for secret scanning in an organization.

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-an-organization)

#### `org_secret_scanning_custom_pattern.delete`

A custom pattern was removed from secret scanning in an organization.

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#removing-a-custom-pattern)

#### `org_secret_scanning_custom_pattern.publish`

A custom pattern was published for secret scanning in an organization.

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-an-organization)

#### `org_secret_scanning_custom_pattern.update`

Changes to a custom pattern were saved and a dry run was executed for secret scanning in an organization.

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#editing-a-custom-pattern)

### org\_secret\_scanning\_generic\_secrets

#### `org_secret_scanning_generic_secrets.disabled`

Generic secrets have been disabled at the organization level

#### `org_secret_scanning_generic_secrets.enabled`

Generic secrets have been enabled at the organization level

### org\_secret\_scanning\_non\_provider\_patterns

#### `org_secret_scanning_non_provider_patterns.disabled`

Secret scanning for non-provider patterns was disabled at the organization level.

**Additional fields:** `actor_is_bot`

**Reference:** [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/secret-scanning-patterns#non-provider-patterns)

#### `org_secret_scanning_non_provider_patterns.enabled`

Secret scanning for non-provider patterns was enabled at the organization level.

**Additional fields:** `actor_is_bot`

**Reference:** [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/secret-scanning-patterns#non-provider-patterns)

### org\_secret\_scanning\_push\_protection\_bypass\_list

#### `org_secret_scanning_push_protection_bypass_list.add`

A role or team was added to the push protection bypass list at the organization level.

**Additional fields:** `actor_is_bot`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#enabling-delegated-bypass-for-push-protection)

#### `org_secret_scanning_push_protection_bypass_list.disable`

Push protection settings for "Users who can bypass push protection for secret scanning" changed from "Specific roles or teams" to "Anyone with write access" at the organization level.

**Additional fields:** `actor_is_bot`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#enabling-delegated-bypass-for-push-protection)

#### `org_secret_scanning_push_protection_bypass_list.enable`

Push protection settings for "Users who can bypass push protection for secret scanning" changed from "Anyone with write access" to "Specific roles or teams" at the organization level.

**Additional fields:** `actor_is_bot`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#enabling-delegated-bypass-for-push-protection)

#### `org_secret_scanning_push_protection_bypass_list.remove`

A role or team was removed from the push protection bypass list at the organization level.

**Additional fields:** `actor_is_bot`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#enabling-delegated-bypass-for-push-protection)

### org\_secret\_scanning\_push\_protection\_pattern\_configuration

#### `org_secret_scanning_push_protection_pattern_configuration.push_protection_setting_changed`

The push protection setting was updated for a secret type for your organization.

**Additional fields:** `push_protection_setting`, `secret_type`, `secret_type_display_name`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations)

#### `org_secret_scanning_push_protection_pattern_configuration.updated`

The push protection pattern configuration was updated for your organization.

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations)

### organization\_custom\_property\_definition

#### `organization_custom_property_definition.create`

A new organization custom property definition was created.

**Additional fields:** `definition_id`, `property_name`, `description`, `value_type`, `required`, `allowed_values`, `default_value`, `actor_is_bot`

**Reference:** /admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/managing-custom-properties-for-organization-in-your-enterprise

#### `organization_custom_property_definition.destroy`

An organization custom property definition was deleted.

**Additional fields:** `definition_id`, `property_name`, `description`, `value_type`, `required`, `allowed_values`, `default_value`, `actor_is_bot`

**Reference:** /admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/managing-custom-properties-for-organization-in-your-enterprise

#### `organization_custom_property_definition.update`

An organization custom property definition was updated.

**Additional fields:** `definition_id`, `property_name`, `old_values_editable_by`, `values_editable_by`, `actor_is_bot`, `old_allowed_values`, `old_default_value`, `old_required`

**Reference:** /admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/managing-custom-properties-for-organization-in-your-enterprise

### organization\_custom\_property\_value

#### `organization_custom_property_value.create`

An organization's custom property value was manually set for the first time.

**Additional fields:** `definition_id`, `property_name`, `value`, `actor_is_bot`

**Reference:** /admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/managing-custom-properties-for-organization-in-your-enterprise

#### `organization_custom_property_value.destroy`

An organization's custom property value was deleted.

**Additional fields:** `definition_id`, `property_name`, `value`, `actor_is_bot`

**Reference:** /admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/managing-custom-properties-for-organization-in-your-enterprise

### organization\_default\_label

#### `organization_default_label.create`

A default label was created for repositories in an organization.

**Reference:** /organizations/managing-organization-settings/managing-default-labels-for-repositories-in-your-organization#creating-a-default-label

#### `organization_default_label.destroy`

A default label was deleted for repositories in an organization.

**Reference:** /organizations/managing-organization-settings/managing-default-labels-for-repositories-in-your-organization#deleting-a-default-label

#### `organization_default_label.update`

A default label was edited for repositories in an organization.

**Reference:** /organizations/managing-organization-settings/managing-default-labels-for-repositories-in-your-organization#editing-a-default-label

### organization\_domain

#### `organization_domain.approve`

A domain was approved for an organization.

**Additional fields:** `owner_type`, `domain_name`, `owner`

**Reference:** /organizations/managing-organization-settings/verifying-or-approving-a-domain-for-your-organization#approving-a-domain-for-your-organization

#### `organization_domain.create`

A domain was added to an organization.

**Additional fields:** `domain_name`

**Reference:** /organizations/managing-organization-settings/verifying-or-approving-a-domain-for-your-organization#verifying-a-domain-for-your-organization

#### `organization_domain.destroy`

A domain was removed from an organization.

**Additional fields:** `domain_name`

**Reference:** /organizations/managing-organization-settings/verifying-or-approving-a-domain-for-your-organization#removing-an-approved-or-verified-domain

#### `organization_domain.verify`

A domain was verified for an organization.

**Additional fields:** `domain_name`

**Reference:** /organizations/managing-organization-settings/verifying-or-approving-a-domain-for-your-organization#verifying-a-domain-for-your-organization

### organization\_projects\_change

#### `organization_projects_change.clear`

An enterprise owner cleared the policy setting for organization-wide project boards in an enterprise.

**Reference:** [Enforcing policies for projects in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-projects-in-your-enterprise#enforcing-a-policy-for-organization-wide-project-boards)

#### `organization_projects_change.disable`

Organization projects were disabled for all organizations in an enterprise.

**Reference:** [Enforcing policies for projects in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-projects-in-your-enterprise#enforcing-a-policy-for-organization-wide-project-boards)

#### `organization_projects_change.enable`

Organization projects were enabled for all organizations in an enterprise.

**Reference:** [Enforcing policies for projects in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-projects-in-your-enterprise#enforcing-a-policy-for-organization-wide-project-boards)

### organization\_role

#### `organization_role.assign`

An organization role was assigned to a user or team.

**Additional fields:** `organization_role_id`, `organization_role_name`, `actor_is_bot`

**Reference:** [Permissions of custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)

#### `organization_role.create`

A custom organization role was created in an organization.

**Additional fields:** `name`, `owner`, `role_permissions`, `base_role`, `actor_is_bot`

**Reference:** [Permissions of custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)

#### `organization_role.destroy`

A custom organization role was deleted in an organization.

**Additional fields:** `name`, `owner`, `role_permissions`, `base_role`

**Reference:** [Permissions of custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)

#### `organization_role.revoke`

A user or team was unassigned an organization role.

**Additional fields:** `organization_role_id`, `organization_role_name`

**Reference:** [Permissions of custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)

#### `organization_role.update`

A custom organization role was edited in an organization.

**Additional fields:** `name`, `owner`, `role_permissions`, `base_role`, `old_role_permissions`, `actor_is_bot`, `old_base_role`

**Reference:** [Permissions of custom organization roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)

### organization\_wide\_project\_base\_role

#### `organization_wide_project_base_role.update`

An organization's default project base role was updated.

**Additional fields:** `old_project_base_role`, `new_project_base_role`, `actor_is_bot`

### packages

#### `packages.package_deleted`

An entire package was deleted.

**Additional fields:** `package`, `actor_is_bot`

**Reference:** /packages/learn-github-packages/deleting-and-restoring-a-package

#### `packages.package_published`

A package was published or republished to an organization.

**Additional fields:** `package`, `ecosystem`, `version_count`, `is_republished`, `actor_is_bot`

#### `packages.package_version_deleted`

A specific package version was deleted.

**Additional fields:** `package`, `version`, `ecosystem`, `actor_is_bot`

**Reference:** /packages/learn-github-packages/deleting-and-restoring-a-package

#### `packages.package_version_published`

A specific package version was published or republished to a package.

**Additional fields:** `ecosystem`, `package`, `version`, `is_republished`, `actor_is_bot`

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

#### `personal_access_token.access_restriction_disabled`

The configured restriction for access to resources via personal access tokens was disabled.

**Additional fields:** `actor_is_bot`

#### `personal_access_token.access_restriction_enabled`

The configured restriction for access to resources via personal access tokens was enabled.

**Additional fields:** `actor_is_bot`

#### `personal_access_token.access_restriction_reset`

The configured restriction for access to resources via personal access tokens was reset and delegated to organizations.

**Additional fields:** `actor_is_bot`

#### `personal_access_token.access_revoked`

A fine-grained personal access token was revoked. The token can still read public organization resources.

**Additional fields:** `user_programmatic_access_id`, `user_programmatic_access_name`, `repository_selection`

**Reference:** /organizations/managing-programmatic-access-to-your-organization/reviewing-and-revoking-personal-access-tokens-in-your-organization

#### `personal_access_token.auto_approve_grant_requests_disabled`

Triggered when fine-grained personal access tokens can access organization resources without prior approval.

**Additional fields:** `actor_is_bot`

#### `personal_access_token.auto_approve_grant_requests_enabled`

Triggered when the organization must approve fine-grained personal access tokens before the tokens can access organization resources.

**Additional fields:** `actor_is_bot`

#### `personal_access_token.auto_approve_grant_requests_reset`

Triggered when the enterprise delegates to the organizations when to require approval for fine-grained personal access tokens before the tokens can access organization resources.

**Additional fields:** `actor_is_bot`

#### `personal_access_token.expiration_limit_set`

A personal access token expiration limit was set.

**Additional fields:** `token_expiration`, `old_token_expiration`, `exempt_administrators`, `actor_is_bot`

#### `personal_access_token.expiration_limit_unset`

A personal access token expiration limit was unset.

**Additional fields:** `old_token_expiration`, `actor_is_bot`

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

### prebuild\_configuration

#### `prebuild_configuration.create`

A GitHub Codespaces prebuild configuration for a repository was created.

**Additional fields:** `branch`, `public_repo`

**Reference:** /codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds

#### `prebuild_configuration.destroy`

A GitHub Codespaces prebuild configuration for a repository was deleted.

**Additional fields:** `branch`, `public_repo`

**Reference:** /codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds

#### `prebuild_configuration.run_triggered`

A user initiated a run of a GitHub Codespaces prebuild configuration for a repository branch.

**Additional fields:** `branch`, `public_repo`

**Reference:** /codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds

#### `prebuild_configuration.update`

A GitHub Codespaces prebuild configuration for a repository was edited.

**Additional fields:** `branch`, `public_repo`

**Reference:** /codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds

### private\_repository\_forking

#### `private_repository_forking.clear`

An enterprise owner cleared the policy setting for allowing forks of private and internal repositories, for a repository, organization or enterprise.

#### `private_repository_forking.disable`

An enterprise owner disabled the policy setting for allowing forks of private and internal repositories, for a repository, organization or enterprise. Private and internal repositories are never allowed to be forked.

#### `private_repository_forking.enable`

An enterprise owner enabled the policy setting for allowing forks of private and internal repositories, for a repository, organization or enterprise. Private and internal repositories are always allowed to be forked.

### profile\_picture

#### `profile_picture.update`

A profile picture was updated.

**Additional fields:** `owner`

**Reference:** [Personalize your profile](/en/enterprise-cloud@latest/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile)

### project

#### `project.access`

A project board visibility was changed.

#### `project.close`

A project board was closed.

**Additional fields:** `project_id`, `project_kind`

**Reference:** [Closing a project (classic)](/en/enterprise-cloud@latest/issues/organizing-your-work-with-project-boards/managing-project-boards/closing-a-project-board)

#### `project.create`

A project board was created.

#### `project.delete`

A project board was deleted.

#### `project.link`

A repository was linked to a project board.

#### `project.open`

A project board was reopened.

**Additional fields:** `project_id`, `project_kind`, `project_name`

**Reference:** [Reopening a closed project (classic)](/en/enterprise-cloud@latest/issues/organizing-your-work-with-project-boards/managing-project-boards/reopening-a-closed-project-board)

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

### project\_base\_role

#### `project_base_role.update`

A project's base role was updated.

**Additional fields:** `old_project_base_role`, `new_project_base_role`, `project_number`, `public_project`, `project_id`, `actor_is_bot`

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

#### `protected_branch.authorized_users_teams`

The users, teams, or integrations allowed to bypass a branch protection were changed.

**Additional fields:** `name`, `oauth_application_id`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches

#### `protected_branch.branch_allowances`

A protected branch allowance was given to a specific user, team or integration.

**Additional fields:** `name`, `authorized_actors`, `policy`, `public_repo`

#### `protected_branch.create`

Branch protection was enabled on a branch.

**Additional fields:** `name`, `authorized_actor_names`, `required_deployments_enforcement_level`, `merge_queue_enforcement_level`, `create_protected`

#### `protected_branch.destroy`

Branch protection was disabled on a branch.

**Additional fields:** `name`, `required_deployments_enforcement_level`, `merge_queue_enforcement_level`, `create_protected`

#### `protected_branch.dismiss_stale_reviews`

Enforcement of dismissing stale pull requests was updated on a branch.

**Additional fields:** `dismiss_stale_reviews_on_push`, `name`

#### `protected_branch.dismissal_restricted_users_teams`

Enforcement of restricting users and/or teams who can dismiss reviews was updated on a branch.

**Additional fields:** `oauth_application_id`, `authorized_actors_only`, `authorized_actors`, `name`

#### `protected_branch.policy_override`

A branch protection requirement was overridden by a repository administrator.

**Additional fields:** `reasons`, `before`, `after`, `branch`, `overridden_codes`, `referrer`, `deploy_key_fingerprint`, `compliant_pull_request_ids`, `rule_suite_id`

#### `protected_branch.rejected_ref_update`

A branch update attempt was rejected.

**Additional fields:** `branch`, `before`, `overridden_codes`, `after`, `reasons`, `deploy_key_fingerprint`, `compliant_pull_request_ids`, `actor_is_bot`, `rule_suite_id`

#### `protected_branch.update_admin_enforced`

Branch protection was enforced for repository administrators.

**Additional fields:** `admin_enforced`, `name`

#### `protected_branch.update_allow_force_pushes_enforcement_level`

Force pushes were enabled or disabled for a branch.

**Additional fields:** `name`, `allow_force_pushes_enforcement_level`

#### `protected_branch.update_ignore_approvals_from_contributors`

Ignoring of approvals from contributors to a pull request was enabled or disabled for a branch.

**Additional fields:** `name`, `ignore_approvals_from_contributors`, `public_repo`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule

#### `protected_branch.update_lock_allows_fetch_and_merge`

Fork syncing was enabled or disabled for a read-only branch

**Additional fields:** `name`, `lock_allows_fetch_and_merge`, `public_repo`

**Reference:** repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#lock-branch

#### `protected_branch.update_lock_branch_enforcement_level`

The enforcement of a branch lock was updated.

**Additional fields:** `name`, `enforcement_level`, `lock_branch_enforcement_level`, `public_repo`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#lock-branch

#### `protected_branch.update_merge_queue_enforcement_level`

Enforcement of the merge queue was modified for a branch.

**Additional fields:** `name`, `merge_queue_enforcement_level`, `public_repo`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-merge-queue

#### `protected_branch.update_name`

A branch name pattern was updated for a branch.

**Additional fields:** `name`, `old_name`, `public_repo`

#### `protected_branch.update_pull_request_reviews_enforcement_level`

Enforcement of required pull request reviews was updated for a branch. Can be 0 (deactivated), 1 (non-admins), or 2 (everyone).

**Additional fields:** `name`, `pull_request_reviews_enforcement_level`

#### `protected_branch.update_require_code_owner_review`

Enforcement of required code owner review was updated for a branch.

**Additional fields:** `require_code_owner_review`, `name`

#### `protected_branch.update_require_last_push_approval`

Someone other than the person who pushed the last code-modifying commit to the branch must approve pull requests for the branch.

**Additional fields:** `name`, `require_last_push_approval`, `public_repo`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-pull-request-reviews-before-merging

#### `protected_branch.update_required_approving_review_count`

Enforcement of the required number of approvals before merging was updated on a branch.

**Additional fields:** `required_approving_review_count`, `name`

#### `protected_branch.update_required_status_checks_enforcement_level`

Enforcement of required status checks was updated for a branch.

**Additional fields:** `name`, `required_status_checks_enforcement_level`

#### `protected_branch.update_signature_requirement_enforcement_level`

Enforcement of required commit signing was updated for a branch.

**Additional fields:** `name`, `signature_requirement_enforcement_level`

#### `protected_branch.update_strict_required_status_checks_policy`

Enforcement of required status checks was updated for a branch.

**Additional fields:** `name`, `strict_required_status_checks_policy`

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

### pull\_request

#### `pull_request.close`

A pull request was closed without being merged.

**Additional fields:** `pull_request_id`, `pull_request_url`, `actor_is_bot`

**Reference:** /pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/closing-a-pull-request

#### `pull_request.converted_to_draft`

A pull request was converted to a draft.

**Additional fields:** `pull_request_id`, `pull_request_url`

**Reference:** /pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/changing-the-stage-of-a-pull-request#converting-a-pull-request-to-a-draft

#### `pull_request.create`

A pull request was created.

**Additional fields:** `pull_request_id`, `pull_request_url`, `actor_is_bot`, `actor_is_agent`

**Reference:** /pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request

#### `pull_request.create_review_request`

A review was requested on a pull request.

**Additional fields:** `pull_request_id`, `reviewer_type`, `reviewer`, `reviewer_id`, `pull_request_url`, `actor_is_agent`

**Reference:** /pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews

#### `pull_request.in_progress`

A pull request was marked as in progress.

**Additional fields:** `pull_request_id`

#### `pull_request.indirect_merge`

A pull request was considered merged because the pull request's commits were merged into the target branch.

**Additional fields:** `pull_request_id`, `pull_request_url`

#### `pull_request.merge`

A pull request was merged.

**Additional fields:** `pull_request_id`, `pull_request_url`, `actor_is_bot`

**Reference:** /pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/merging-a-pull-request

#### `pull_request.ready_for_review`

A pull request was marked as ready for review.

**Additional fields:** `pull_request_id`, `pull_request_url`

**Reference:** /pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/changing-the-stage-of-a-pull-request#marking-a-pull-request-as-ready-for-review

#### `pull_request.rebase`

A pull request was rebased.

**Additional fields:** `pull_request_id`, `pull_request_url`, `pull_request_title`, `public_repo`

#### `pull_request.remove_review_request`

A review request was removed from a pull request.

**Additional fields:** `pull_request_id`, `reviewer_type`, `reviewer`, `reviewer_id`, `pull_request_url`

**Reference:** /pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews

#### `pull_request.reopen`

A pull request was reopened after previously being closed.

**Additional fields:** `pull_request_id`, `pull_request_url`

### pull\_request\_review

#### `pull_request_review.delete`

A review on a pull request was deleted.

**Additional fields:** `pull_request_id`, `review_id`, `pull_request_url`

#### `pull_request_review.dismiss`

A review on a pull request was dismissed.

**Additional fields:** `pull_request_id`, `review_id`, `pull_request_url`

**Reference:** /pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/dismissing-a-pull-request-review

#### `pull_request_review.submit`

A review on a pull request was submitted.

**Additional fields:** `pull_request_id`, `review_id`, `pull_request_url`, `actor_is_agent`

**Reference:** /pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request#submitting-your-review

### pull\_request\_review\_comment

#### `pull_request_review_comment.create`

A review comment was added to a pull request.

**Additional fields:** `comment_id`, `actor_is_agent`

**Reference:** /pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews

#### `pull_request_review_comment.delete`

A review comment on a pull request was deleted.

**Additional fields:** `comment_id`

#### `pull_request_review_comment.update`

A review comment on a pull request was changed.

**Additional fields:** `comment_id`

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

**Reference:** [Inviting collaborators to a personal repository](/en/enterprise-cloud@latest/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository)

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

#### `repo.code_scanning_autofix_disabled`

Autofix for code scanning alerts was disabled for a repository.

**Additional fields:** `public_repo`, `actor_is_bot`

#### `repo.code_scanning_autofix_enabled`

Autofix for code scanning alerts was enabled for a repository.

**Additional fields:** `public_repo`, `actor_is_bot`

#### `repo.code_scanning_autofix_third_party_tools_disabled`

Autofix for third party tools for code scanning alerts was disabled for a repository.

**Additional fields:** `public_repo`, `actor_is_bot`

#### `repo.code_scanning_autofix_third_party_tools_enabled`

Autofix for third party tools for code scanning alerts was enabled for a repository.

**Additional fields:** `public_repo`, `actor_is_bot`

#### `repo.code_scanning_configuration_for_branch_deleted`

A code scanning configuration for a branch of a repository was deleted.

**Additional fields:** `tool`, `branch`, `category`, `public_repo`

**Reference:** [Resolving code scanning alerts](/en/enterprise-cloud@latest/code-security/code-scanning/managing-code-scanning-alerts/managing-code-scanning-alerts-for-your-repository#removing-stale-configurations-and-alerts-from-a-branch)

#### `repo.code_scanning_delegated_alert_dismissal_disabled`

Prevention of direct alert dismissal for code scanning was disabled for a repository.

**Additional fields:** `public_repo`

#### `repo.code_scanning_delegated_alert_dismissal_enabled`

Prevention of direct alert dismissal for code scanning was enabled for a repository.

**Additional fields:** `public_repo`

#### `repo.codeql_disabled`

Code scanning using the default setup was disabled for a repository.

**Additional fields:** `public_repo`

**Reference:** [Configuring default setup for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning)

#### `repo.codeql_enabled`

Code scanning using the default setup was enabled for a repository.

**Additional fields:** `public_repo`, `query_suite`, `threat_model`, `languages`

**Reference:** [Configuring default setup for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning)

#### `repo.codeql_updated`

Code scanning using the default setup was updated for a repository.

**Additional fields:** `query_suite`, `threat_model`, `languages`, `public_repo`, `actor_is_bot`

**Reference:** [Configuring default setup for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning)

#### `repo.codespaces_trusted_repo_access_granted`

GitHub Codespaces was granted trusted repository access to this repository.

**Additional fields:** `public_repo`

#### `repo.codespaces_trusted_repo_access_revoked`

GitHub Codespaces trusted repository access to this repository was revoked.

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

**Reference:** [Using secrets in GitHub Actions](/en/enterprise-cloud@latest/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository)

#### `repo.create_actions_variable`

A GitHub Actions variable was created for a repository.

**Additional fields:** `key`, `visibility`, `public_repo`

**Reference:** [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository)

#### `repo.create_integration_secret`

A Codespaces or Dependabot secret was created for a repository.

**Additional fields:** `key`, `visibility`, `integration`, `public_repo`

#### `repo.destroy`

A repository was deleted.

**Additional fields:** `request_category`, `visibility`, `request_method`, `oauth_application_id`, `actor_is_bot`

**Reference:** /repositories/creating-and-managing-repositories/deleting-a-repository

#### `repo.download_zip`

A source code archive of a repository was downloaded as a ZIP file.

**Additional fields:** `visibility`, `public_repo`, `actor_is_bot`

**Reference:** /repositories/working-with-files/using-files/downloading-source-code-archives

#### `repo.immutable_releases_settings_disabled`

The setting for immutable releases was disabled for a repository.

**Additional fields:** `visibility`, `public_repo`, `actor_is_bot`

#### `repo.immutable_releases_settings_enabled`

The setting for immutable releases was enabled for a repository.

**Additional fields:** `visibility`, `public_repo`, `actor_is_bot`

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

**Reference:** [Adding self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners#adding-a-self-hosted-runner-to-a-repository)

#### `repo.remove_actions_secret`

A GitHub Actions secret was deleted for a repository.

**Additional fields:** `key`

**Reference:** [Using secrets in GitHub Actions](/en/enterprise-cloud@latest/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository)

#### `repo.remove_actions_variable`

A GitHub Actions variable was deleted for a repository.

**Additional fields:** `key`, `public_repo`

**Reference:** [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository)

#### `repo.remove_integration_secret`

A Codespaces or Dependabot secret was deleted for a repository.

**Additional fields:** `key`, `integration`, `public_repo`

#### `repo.remove_member`

A collaborator was removed from a repository.

**Additional fields:** `visibility`

**Reference:** [Removing a collaborator from a personal repository](/en/enterprise-cloud@latest/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/removing-a-collaborator-from-a-personal-repository)

#### `repo.remove_self_hosted_runner`

A self-hosted runner was removed.

**Reference:** [Removing self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/removing-self-hosted-runners#removing-a-runner-from-a-repository)

#### `repo.remove_topic`

A topic was removed from a repository.

**Additional fields:** `topic`

#### `repo.rename`

A repository was renamed.

**Additional fields:** `old_name`, `visibility`

**Reference:** /repositories/creating-and-managing-repositories/renaming-a-repository

#### `repo.rename_branch`

A branch was renamed.

**Additional fields:** `old_branch`, `new_branch`, `default_branch`, `public_repo`, `actor_is_bot`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/renaming-a-branch

#### `repo.self_hosted_runner_offline`

The runner application was stopped. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `runner_id`, `runner_name`

**Reference:** [Monitoring and troubleshooting self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/monitoring-and-troubleshooting-self-hosted-runners#checking-the-status-of-a-self-hosted-runner)

#### `repo.self_hosted_runner_online`

The runner application was started. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `runner_id`, `runner_name`

**Reference:** [Monitoring and troubleshooting self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/monitoring-and-troubleshooting-self-hosted-runners#checking-the-status-of-a-self-hosted-runner)

#### `repo.self_hosted_runner_updated`

The runner application was updated. This event is not included in the JSON/CSV export.

**Additional fields:** `runner_id`, `runner_name`, `source_version`, `target_version`, `runner_group_id`, `runner_group_name`

**Reference:** [Self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners#about-self-hosted-runners)

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

**Reference:** [Using secrets in GitHub Actions](/en/enterprise-cloud@latest/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository)

#### `repo.update_actions_settings`

A repository administrator changed GitHub Actions policy settings for a repository.

**Additional fields:** `visibility`, `new_policy`, `old_policy`, `updated_access_policy`, `actor_is_bot`

#### `repo.update_actions_variable`

A GitHub Actions variable was updated for a repository.

**Additional fields:** `key`, `visibility`, `public_repo`

**Reference:** [Store information in variables](/en/enterprise-cloud@latest/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository)

#### `repo.update_default_branch`

The default branch for a repository was changed.

**Additional fields:** `visibility`, `actor_is_bot`

#### `repo.update_integration_secret`

A Codespaces or Dependabot secret was updated for a repository.

**Additional fields:** `key`, `visibility`, `integration`, `public_repo`

#### `repo.update_member`

A user's permission to a repository was changed.

**Additional fields:** `oauth_application_id`, `visibility`, `old_permission`, `old_base_role`, `old_repo_permission`, `old_repo_base_role`, `new_repo_base_role`, `new_repo_permission`, `actor_is_bot`

### repository\_advisory

#### `repository_advisory.close`

Someone closed a security advisory.

**Reference:** [About repository security advisories](/en/enterprise-cloud@latest/code-security/security-advisories/working-with-repository-security-advisories/about-repository-security-advisories)

#### `repository_advisory.cve_request`

Someone requested a CVE (Common Vulnerabilities and Exposures) number from GitHub for a draft security advisory.

#### `repository_advisory.github_broadcast`

GitHub made a security advisory public in the GitHub Advisory Database.

**Additional fields:** `public_repo`

#### `repository_advisory.github_withdraw`

GitHub withdrew a security advisory that was published in error.

#### `repository_advisory.open`

Someone opened a draft security advisory.

#### `repository_advisory.publish`

Someone published a security advisory.

#### `repository_advisory.reopen`

Someone reopened as draft security advisory.

**Additional fields:** `public_repo`

#### `repository_advisory.update`

Someone edited a draft or published security advisory.

### repository\_branch\_protection\_evaluation

#### `repository_branch_protection_evaluation.disable`

Branch protections were disabled for the repository.

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule

#### `repository_branch_protection_evaluation.enable`

Branch protections were enabled for this repository.

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule

### repository\_code\_security

#### `repository_code_security.disable`

Code security was disabled for a repository.

**Additional fields:** `public_repo`, `actor_is_bot`

#### `repository_code_security.enable`

Code security was enabled for a repository.

**Additional fields:** `public_repo`, `actor_is_bot`

### repository\_content\_analysis

#### `repository_content_analysis.disable`

Data use settings were disabled for a private repository.

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository#enabling-or-disabling-security-and-analysis-features-for-private-repositories

#### `repository_content_analysis.enable`

Data use settings were enabled for a private repository.

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository#enabling-or-disabling-security-and-analysis-features-for-private-repositories

### repository\_dependency\_graph

#### `repository_dependency_graph.disable`

The dependency graph was disabled for a private repository.

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-fea, tures-for-your-repository/managing-security-and-analysis-settings-for-your-repository#enabling-or-disabling-security-and-analysis-features-for-private-repositories

#### `repository_dependency_graph.enable`

The dependency graph was enabled for a private repository.

**Additional fields:** `public_repo`, `actor_is_bot`

### repository\_dependency\_updates\_self\_hosted

#### `repository_dependency_updates_self_hosted.disabled`

Dependency updates on self-hosted runners was disabled.

**Additional fields:** `public_repo`

**Reference:** [Configuring Dependabot on self-hosted runners](code-security/how-tos/secure-your-supply-chain/manage-your-dependency-security/managing-dependabot-on-self-hosted-runners)

#### `repository_dependency_updates_self_hosted.enabled`

Dependency updates on self-hosted runners was enabled.

**Additional fields:** `topic`, `public_repo`, `actor_is_bot`, `actor_is_agent`

**Reference:** [Configuring Dependabot on self-hosted runners](code-security/how-tos/secure-your-supply-chain/manage-your-dependency-security/managing-dependabot-on-self-hosted-runners)

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

### repository\_projects\_change

#### `repository_projects_change.clear`

The repository projects policy was removed for an organization, or all organizations in the enterprise  Organization owners can now control their repository projects settings.

**Reference:** [Enforcing policies for projects in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-projects-in-your-enterprise)

#### `repository_projects_change.disable`

Repository projects were disabled for a repository, all repositories in an organization, or all organizations in an enterprise.

#### `repository_projects_change.enable`

Repository projects were enabled for a repository, all repositories in an organization, or all organizations in an enterprise.

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

### repository\_secret\_scanning

#### `repository_secret_scanning.disable`

Secret scanning was disabled for a repository.

**Additional fields:** `public_repo`

**Reference:** [About secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/about-secret-scanning)

#### `repository_secret_scanning.enable`

Secret scanning was enabled for a repository.

### repository\_secret\_scanning\_automatic\_validity\_checks

#### `repository_secret_scanning_automatic_validity_checks.disabled`

Automatic partner validation checks have been disabled at the repository level

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository#allowing-validity-checks-for-partner-patterns-in-a-repository

#### `repository_secret_scanning_automatic_validity_checks.enabled`

Automatic partner validation checks have been enabled at the repository level

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository#allowing-validity-checks-for-partner-patterns-in-a-repository

### repository\_secret\_scanning\_custom\_pattern

#### `repository_secret_scanning_custom_pattern.create`

A custom pattern was created for secret scanning in a repository.

**Additional fields:** `public_repo`

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-a-repository)

#### `repository_secret_scanning_custom_pattern.delete`

A custom pattern was removed from secret scanning in a repository.

**Additional fields:** `public_repo`

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#removing-a-custom-pattern)

#### `repository_secret_scanning_custom_pattern.publish`

A custom pattern was published for secret scanning in a repository.

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-a-repository)

#### `repository_secret_scanning_custom_pattern.update`

Changes to a custom pattern were saved and a dry run was executed for secret scanning in a repository.

**Additional fields:** `public_repo`

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#editing-a-custom-pattern)

### repository\_secret\_scanning\_custom\_pattern\_push\_protection

#### `repository_secret_scanning_custom_pattern_push_protection.disabled`

Push protection for a custom pattern for secret scanning was disabled for your repository.

**Additional fields:** `public_repo`

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-a-repository)

#### `repository_secret_scanning_custom_pattern_push_protection.enabled`

Push protection for a custom pattern for secret scanning was enabled for your repository.

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/defining-custom-patterns-for-secret-scanning#defining-a-custom-pattern-for-a-repository)

### repository\_secret\_scanning\_extended\_metadata

#### `repository_secret_scanning_extended_metadata.disabled`

Metadata for secret scanning alerts has been disabled at the repository level

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** [Enabling extended metadata checks for your repository](/en/enterprise-cloud@latest/code-security/secret-scanning/enabling-secret-scanning-features/enabling-extended-metadata-checks-for-your-repository)

#### `repository_secret_scanning_extended_metadata.enabled`

Metadata for secret scanning alerts has been enabled at the repository level

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** [Enabling extended metadata checks for your repository](/en/enterprise-cloud@latest/code-security/secret-scanning/enabling-secret-scanning-features/enabling-extended-metadata-checks-for-your-repository)

### repository\_secret\_scanning\_generic\_secrets

#### `repository_secret_scanning_generic_secrets.disabled`

Generic secrets have been disabled at the repository level

**Additional fields:** `public_repo`, `actor_is_bot`

#### `repository_secret_scanning_generic_secrets.enabled`

Generic secrets have been enabled at the repository level

**Additional fields:** `public_repo`, `actor_is_bot`

### repository\_secret\_scanning\_non\_provider\_patterns

#### `repository_secret_scanning_non_provider_patterns.disabled`

Secret scanning for non-provider patterns was disabled at the repository level.

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/secret-scanning-patterns#non-provider-patterns)

#### `repository_secret_scanning_non_provider_patterns.enabled`

Secret scanning for non-provider patterns was enabled at the repository level.

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/secret-scanning-patterns#non-provider-patterns)

### repository\_secret\_scanning\_push\_protection

#### `repository_secret_scanning_push_protection.disable`

Secret scanning push protection was disabled for a repository.

**Additional fields:** `public_repo`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/protecting-pushes-with-secret-scanning)

#### `repository_secret_scanning_push_protection.enable`

Secret scanning push protection was enabled for a repository.

**Additional fields:** `public_repo`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/protecting-pushes-with-secret-scanning)

### repository\_secret\_scanning\_push\_protection\_bypass\_list

#### `repository_secret_scanning_push_protection_bypass_list.add`

A role or team was added to the push protection bypass list at the repository level.

**Additional fields:** `public_repo`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#enabling-delegated-bypass-for-push-protection)

#### `repository_secret_scanning_push_protection_bypass_list.disable`

Push protection settings for "Users who can bypass push protection for secret scanning" changed from "Specific roles or teams" to "Anyone with write access" at the repository level.

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#enabling-delegated-bypass-for-push-protection)

#### `repository_secret_scanning_push_protection_bypass_list.enable`

Push protection settings for "Users who can bypass push protection for secret scanning" changed from "Anyone with write access" to "Specific roles or teams" at the repository level.

**Additional fields:** `public_repo`, `actor_is_bot`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#enabling-delegated-bypass-for-push-protection)

#### `repository_secret_scanning_push_protection_bypass_list.remove`

A role or team was removed from the push protection bypass list at the repository level.

**Additional fields:** `public_repo`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#enabling-delegated-bypass-for-push-protection)

### repository\_security\_configuration

#### `repository_security_configuration.applied`

A code security configuration was applied to a repository.

**Additional fields:** `security_configuration_id`, `security_configuration_name`, `repository_security_configuration_state`, `repository_security_configuration_failure_reason`, `public_repo`, `actor_is_bot`

#### `repository_security_configuration.failed`

A code security configuration failed to attach to the repository.

**Additional fields:** `security_configuration_id`, `security_configuration_name`, `repository_security_configuration_failure_reason`, `public_repo`, `actor_is_bot`

#### `repository_security_configuration.removed`

A code security configuration was removed from a repository.

**Additional fields:** `security_configuration_id`, `security_configuration_name`, `repository_security_configuration_state`, `repository_security_configuration_failure_reason`, `public_repo`, `actor_is_bot`

#### `repository_security_configuration.removed_by_settings_change`

A code security configuration was removed due to a change in repository or enterprise settings.

**Additional fields:** `security_configuration_id`, `security_configuration_name`, `repository_security_configuration_state`, `repository_security_configuration_failure_reason`, `public_repo`, `actor_is_bot`

### repository\_security\_updates

#### `repository_security_updates.disable`

Dependabot security updates was disabled.

**Additional fields:** `public_repo`

**Reference:** [Configuring Dependabot security updates](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates)

#### `repository_security_updates.enable`

Dependabot security updates was enabled.

**Additional fields:** `public_repo`, `actor_is_bot`, `actor_is_agent`

**Reference:** [Configuring Dependabot security updates](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates)

### repository\_visibility\_change

#### `repository_visibility_change.clear`

The repository visibility change setting was cleared for an organization or enterprise.

**Reference:** /organizations/managing-organization-settings/restricting-repository-visibility-changes-in-your-organization, [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-changes-to-repository-visibility)

#### `repository_visibility_change.disable`

The ability for enterprise members to update a repository's visibility was disabled. Members are unable to change repository visibilities in an organization, or all organizations in an enterprise.

#### `repository_visibility_change.enable`

The ability for enterprise members to update a repository's visibility was enabled. Members are able to change repository visibilities in an organization, or all organizations in an enterprise.

### repository\_vulnerability\_alert

#### `repository_vulnerability_alert.auto_dismiss`

A Dependabot alert was automatically dismissed because its metadata matches an enabled Dependabot rule.

**Additional fields:** `alert_id`, `alert_number`, `ghsa_id`, `public_repo`, `owner`, `vulnerability_alert_rule_id`, `vulnerability_alert_rule_name`

**Reference:** [About Dependabot auto-triage rules](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/using-alert-rules-to-prioritize-dependabot-alerts)

#### `repository_vulnerability_alert.auto_reopen`

A previously auto-dismissed Dependabot alert was automatically reopened because its metadata no longer matches an enabled Dependabot rule.

**Additional fields:** `alert_id`, `alert_number`, `ghsa_id`, `public_repo`, `owner`, `vulnerability_alert_rule_id`, `vulnerability_alert_rule_name`

**Reference:** [About Dependabot auto-triage rules](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/using-alert-rules-to-prioritize-dependabot-alerts)

#### `repository_vulnerability_alert.create`

GitHub created a Dependabot alert because the repository uses a vulnerable dependency.

**Additional fields:** `alert_id`, `alert_number`

**Reference:** [About Dependabot alerts](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

#### `repository_vulnerability_alert.dismiss`

A Dependabot alert was manually dismissed.

**Additional fields:** `alert_id`, `dismiss_reason`, `dismiss_comment`, `alert_number`, `actor_is_bot`

#### `repository_vulnerability_alert.reintroduce`

A Dependabot alert was automatically reopened because the repository resumed use of a vulnerable dependency.

**Additional fields:** `alert_id`, `public_repo`, `owner`, `alert_number`

#### `repository_vulnerability_alert.reopen`

A Dependabot alert was manually reopened.

**Additional fields:** `alert_id`, `owner`, `public_repo`, `alert_number`

#### `repository_vulnerability_alert.resolve`

Changes were pushed to update and resolve a Dependabot alert in a project dependency.

**Additional fields:** `alert_id`, `alert_number`

#### `repository_vulnerability_alert.withdraw`

A Dependabot alert was withdrawn.

**Additional fields:** `alert_id`, `alert_number`, `ghsa_id`, `active`, `public_repo`, `owner`

### repository\_vulnerability\_alerts

#### `repository_vulnerability_alerts.authorized_users_teams`

The list of people or teams authorized to receive Dependabot alerts for the repository was updated.

**Reference:** /repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository#granting-access-to-security-alerts

#### `repository_vulnerability_alerts.disable`

Dependabot alerts was disabled.

#### `repository_vulnerability_alerts.enable`

Dependabot alerts was enabled.

**Additional fields:** `actor_is_bot`

### repository\_vulnerability\_alerts\_auto\_dismissal

#### `repository_vulnerability_alerts_auto_dismissal.disable`

Automatic dismissal of low-impact Dependabot alerts was disabled for the repository.

**Additional fields:** `public_repo`

#### `repository_vulnerability_alerts_auto_dismissal.enable`

Automatic dismissal of low-impact Dependabot alerts was enabled for the repository.

**Additional fields:** `public_repo`, `actor_is_bot`

### required\_status\_check

#### `required_status_check.create`

A status check was marked as required for a protected branch.

**Additional fields:** `context`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-status-checks-before-merging

#### `required_status_check.destroy`

A status check was no longer marked as required for a protected branch.

**Additional fields:** `context`

**Reference:** /repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-status-checks-before-merging

### restrict\_notification\_delivery

#### `restrict_notification_delivery.disable`

Email notification restrictions for an organization or enterprise were disabled.

**Additional fields:** `owner`

**Reference:** [Restricting email notifications for your organization](/en/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/restricting-email-notifications-for-your-organization), [Restricting email notifications for your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/restricting-email-notifications-for-your-enterprise)

#### `restrict_notification_delivery.enable`

Email notification restrictions for an organization or enterprise were enabled.

**Additional fields:** `owner`

**Reference:** [Restricting email notifications for your organization](/en/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/restricting-email-notifications-for-your-organization), [Restricting email notifications for your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/restricting-email-notifications-for-your-enterprise)

### role

#### `role.create`

A new custom repository role was created.

**Additional fields:** `name`, `owner`, `base_role`, `role_permissions`, `old_role_permissions`

**Reference:** [Managing custom repository roles for an organization](/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/managing-custom-repository-roles-for-an-organization)

#### `role.destroy`

A custom repository role was deleted.

**Additional fields:** `name`, `owner`, `role_permissions`, `base_role`

**Reference:** [Managing custom repository roles for an organization](/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/managing-custom-repository-roles-for-an-organization)

#### `role.update`

A custom repository role was edited.

**Additional fields:** `name`, `owner`, `role_permissions`, `base_role`, `old_role_permissions`, `old_base_role`

**Reference:** [Managing custom repository roles for an organization](/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/managing-custom-repository-roles-for-an-organization)

### secret\_scanning

#### `secret_scanning.disable`

Secret scanning was disabled for all existing repositories.

**Reference:** [About secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/about-secret-scanning)

#### `secret_scanning.enable`

Secret scanning was enabled for all existing repositories.

**Reference:** [About secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/about-secret-scanning)

### secret\_scanning\_alert

#### `secret_scanning_alert.assign`

A user was assigned to a secret scanning alert.

**Additional fields:** `number`, `secret_type`, `secret_type_display_name`, `publicly_leaked`, `multi_repo`

**Reference:** [Manage secret scanning alerts](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning)

#### `secret_scanning_alert.create`

GitHub detected a secret and created a secret scanning alert.

**Additional fields:** `number`, `secret_type`, `secret_type_display_name`, `publicly_leaked`, `multi_repo`

**Reference:** [Manage secret scanning alerts](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning)

#### `secret_scanning_alert.delete`

A secret scanning alert was deleted by GitHub.

**Additional fields:** `number`, `secret_type`, `secret_type_display_name`, `publicly_leaked`, `multi_repo`, `reason`

**Reference:** [Manage secret scanning alerts](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning)

#### `secret_scanning_alert.public_leak`

A secret scanning alert was leaked in a public repo.

**Additional fields:** `number`, `secret_type`, `secret_type_display_name`, `publicly_leaked`, `multi_repo`

**Reference:** [Manage secret scanning alerts](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning)

#### `secret_scanning_alert.reopen`

A secret scanning alert was reopened.

**Additional fields:** `number`, `public_repo`, `secret_type_display_name`

#### `secret_scanning_alert.report`

A leaked secret was reported to the secret's provider by secret scanning.

**Additional fields:** `number`, `secret_type`, `secret_type_display_name`, `secret_type_provider`, `report_result`

**Reference:** [Resolving alerts from secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning/resolving-alerts)

#### `secret_scanning_alert.resolve`

A secret scanning alert was resolved.

**Additional fields:** `number`, `resolution`, `public_repo`, `secret_type`, `secret_type_display_name`, `publicly_leaked`, `multi_repo`

#### `secret_scanning_alert.revoke`

A secret scanning alert was revoked.

**Additional fields:** `number`, `public_repo`

#### `secret_scanning_alert.unassign`

A user was unassigned from a secret scanning alert.

**Additional fields:** `number`, `secret_type`, `secret_type_display_name`, `publicly_leaked`, `multi_repo`

**Reference:** [Manage secret scanning alerts](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning)

#### `secret_scanning_alert.validate`

A secret scanning alert was validated.

**Additional fields:** `number`, `previous_validity`, `current_validity`, `secret_type`, `secret_type_display_name`, `publicly_leaked`, `multi_repo`

**Reference:** [Manage secret scanning alerts](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning)

### secret\_scanning\_closure\_request

#### `secret_scanning_closure_request.approve`

A request to close a secret scanning alert was approved by a user.

**Additional fields:** `number`, `alert_number`, `request_reviewer_comment`, `public_repo`, `actor_is_bot`

#### `secret_scanning_closure_request.deny`

A request to close a secret scanning alert was denied by a user.

**Additional fields:** `number`, `alert_number`, `request_reviewer_comment`, `public_repo`, `actor_is_bot`

### secret\_scanning\_new\_repos

#### `secret_scanning_new_repos.disable`

Secret scanning was disabled for all new repositories.

**Reference:** [About secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/about-secret-scanning)

#### `secret_scanning_new_repos.enable`

Secret scanning was enabled for all new repositories.

**Reference:** [About secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/about-secret-scanning)

### secret\_scanning\_push\_protection

#### `secret_scanning_push_protection.bypass`

Triggered when a user bypasses the push protection on a secret detected by secret scanning.

**Additional fields:** `number`, `push_protection_bypass_reason`, `secret_type`, `secret_type_display_name`, `publicly_leaked`, `multi_repo`, `request_reviewer`, `request_reviewer_id`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/protecting-pushes-with-secret-scanning#bypassing-push-protection-for-a-secret)

### secret\_scanning\_push\_protection\_request

#### `secret_scanning_push_protection_request.approve`

A request to bypass secret scanning push protection was approved by a user.

**Additional fields:** `number`, `public_repo`, `actor_is_bot`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#managing-requests-to-bypass-push-protection)

#### `secret_scanning_push_protection_request.cancel`

A user canceled a request to bypass secret scanning push protection.

**Additional fields:** `number`, `public_repo`, `actor_is_bot`

**Reference:** /code-security/secret-scanning/working-with-push-protection#requesting-bypass-privileges-when-working-with-the-command-line

#### `secret_scanning_push_protection_request.complete`

A user pushed a commit containing a secret for which there is an approved secret scanning push protection bypass request.

**Additional fields:** `number`, `public_repo`, `actor_is_bot`

**Reference:** /code-security/secret-scanning/working-with-push-protection#requesting-bypass-privileges-when-working-with-the-command-line

#### `secret_scanning_push_protection_request.deny`

A request to bypass secret scanning push protection was denied by a user.

**Additional fields:** `number`, `public_repo`, `actor_is_bot`, `request_reviewer_comment`

**Reference:** [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/push-protection-for-repositories-and-organizations#managing-requests-to-bypass-push-protection)

#### `secret_scanning_push_protection_request.request`

A user requested to bypass secret scanning push protection.

**Additional fields:** `number`, `public_repo`, `actor_is_bot`

**Reference:** /code-security/secret-scanning/working-with-push-protection#requesting-bypass-privileges-when-working-with-the-command-line

### secret\_scanning\_scan

#### `secret_scanning_scan.completed`

A secret scanning scan has completed on this repository.

**Additional fields:** `source`, `type`, `source_slug`, `type_slug`, `started_at`, `completed_at`, `public_repo`, `secret_types`, `custom_pattern_name`, `custom_pattern_scope`

**Reference:** [About secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/about-secret-scanning)

### security\_configuration

#### `security_configuration.create`

A security configuration was created

**Additional fields:** `security_configuration_id`, `security_configuration_name`, `security_configuration_description`, `security_configuration_created_at`, `security_configuration_updated_at`, `security_configuration_enable_ghas`, `security_configuration_private_vulnerability_reporting`, `security_configuration_dependency_graph`, `security_configuration_dependabot_alerts`, `security_configuration_dependabot_security_updates`, `security_configuration_code_scanning`, `security_configuration_secret_scanning`, `security_configuration_secret_scanning_push_protection`, `security_configuration_secret_scanning_validity_checks`, `actor_is_bot`, `security_configuration_dependency_graph_autosubmit_action`, `security_configuration_secret_scanning_non_provider_patterns`, `security_configuration_secret_scanning_delegated_bypass`, `security_configuration_secret_scanning_generic_secrets`, `security_configuration_secret_scanning_delegated_alert_dismissal`, `security_configuration_code_scanning_delegated_alert_dismissal`, `security_configuration_code_security_sku_enabled`, `security_configuration_secret_protection_sku_enabled`, `security_configuration_dependabot_delegated_alert_dismissal`, `security_configuration_secret_scanning_extended_metadata`

#### `security_configuration.delete`

A security configuration was deleted

**Additional fields:** `security_configuration_id`, `security_configuration_name`, `security_configuration_description`, `security_configuration_created_at`, `security_configuration_updated_at`, `security_configuration_enable_ghas`, `security_configuration_private_vulnerability_reporting`, `security_configuration_dependency_graph`, `security_configuration_dependabot_alerts`, `security_configuration_dependabot_security_updates`, `security_configuration_code_scanning`, `security_configuration_secret_scanning`, `security_configuration_secret_scanning_push_protection`, `security_configuration_secret_scanning_validity_checks`, `actor_is_bot`, `security_configuration_dependency_graph_autosubmit_action`, `security_configuration_secret_scanning_non_provider_patterns`, `security_configuration_secret_scanning_delegated_bypass`, `security_configuration_secret_scanning_delegated_alert_dismissal`, `security_configuration_code_scanning_delegated_alert_dismissal`, `security_configuration_code_security_sku_enabled`, `security_configuration_secret_protection_sku_enabled`, `security_configuration_dependabot_delegated_alert_dismissal`, `security_configuration_secret_scanning_extended_metadata`

#### `security_configuration.update`

A security configuration was updated

**Additional fields:** `security_configuration_id`, `security_configuration_name`, `security_configuration_description`, `security_configuration_created_at`, `security_configuration_updated_at`, `security_configuration_enable_ghas`, `security_configuration_private_vulnerability_reporting`, `security_configuration_dependency_graph`, `security_configuration_dependabot_alerts`, `security_configuration_dependabot_security_updates`, `security_configuration_code_scanning`, `security_configuration_secret_scanning`, `security_configuration_secret_scanning_push_protection`, `security_configuration_secret_scanning_validity_checks`, `actor_is_bot`, `security_configuration_dependency_graph_autosubmit_action`, `security_configuration_secret_scanning_non_provider_patterns`, `security_configuration_secret_scanning_delegated_bypass`, `security_configuration_secret_scanning_generic_secrets`, `security_configuration_secret_scanning_delegated_alert_dismissal`, `security_configuration_code_scanning_delegated_alert_dismissal`, `security_configuration_code_security_sku_enabled`, `security_configuration_secret_protection_sku_enabled`, `security_configuration_dependabot_delegated_alert_dismissal`, `security_configuration_secret_scanning_extended_metadata`

### security\_configuration\_default

#### `security_configuration_default.delete`

A default security configuration setting for new repositories was removed.

**Additional fields:** `default_for_new_private_repos`, `default_for_new_public_repos`, `security_configuration_name`, `actor_is_bot`

#### `security_configuration_default.update`

A default security configuration setting for new repositories was updated.

**Additional fields:** `default_for_new_private_repos`, `default_for_new_public_repos`, `security_configuration_name`, `actor_is_bot`

### security\_configuration\_policy

#### `security_configuration_policy.update`

A security configuration policy was updated

**Additional fields:** `enforcement`, `security_configuration_name`

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

**Reference:** [Downgrading a sponsorship](/en/enterprise-cloud@latest/billing/managing-billing-for-github-sponsors/downgrading-a-sponsorship)

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

**Reference:** [Upgrading a sponsorship](/en/enterprise-cloud@latest/billing/managing-billing-for-github-sponsors/upgrading-a-sponsorship), [Downgrading a sponsorship](/en/enterprise-cloud@latest/billing/managing-billing-for-github-sponsors/downgrading-a-sponsorship)

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

#### `sponsors.sponsors_patreon_user_create`

A Patreon account was linked to a user account for use with GitHub Sponsors.

**Additional fields:** `patreon_email`, `patreon_username`

**Reference:** /sponsors/receiving-sponsorships-through-github-sponsors/enabling-sponsorships-through-patreon#linking-your-patreon-account-to-your-github-account

#### `sponsors.sponsors_patreon_user_destroy`

A Patreon account for use with GitHub Sponsors was unlinked from a user account.

**Additional fields:** `patreon_email`, `patreon_username`

**Reference:** [Unlinking your Patreon account from GitHub](/en/enterprise-cloud@latest/sponsors/sponsoring-open-source-contributors/unlinking-your-patreon-account-from-your-github-account)

#### `sponsors.update_tier_repository`

A GitHub Sponsors tier changed access for a repository.

**Additional fields:** `sponsors_listing_id`

#### `sponsors.update_tier_welcome_message`

The welcome message for a GitHub Sponsors tier for an organization was updated.

**Additional fields:** `sponsors_listing_id`

#### `sponsors.withdraw_agreement_signature`

A signature was withdrawn from a GitHub Sponsors agreement that applies to an organization.

**Additional fields:** `sponsors_listing_id`

### ssh\_certificate\_authority

#### `ssh_certificate_authority.create`

An SSH certificate authority for an organization or enterprise was created.

**Additional fields:** `fingerprint`, `openssh_public_key`

**Reference:** [Managing your organization's SSH certificate authorities](/en/enterprise-cloud@latest/organizations/managing-git-access-to-your-organizations-repositories/managing-your-organizations-ssh-certificate-authorities), [Enforcing policies for security settings in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-security-settings-in-your-enterprise#managing-ssh-certificate-authorities-for-your-enterprise)

#### `ssh_certificate_authority.destroy`

An SSH certificate authority for an organization or enterprise was deleted.

**Additional fields:** `fingerprint`, `openssh_public_key`

**Reference:** [Managing your organization's SSH certificate authorities](/en/enterprise-cloud@latest/organizations/managing-git-access-to-your-organizations-repositories/managing-your-organizations-ssh-certificate-authorities), [Enforcing policies for security settings in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-security-settings-in-your-enterprise#managing-ssh-certificate-authorities-for-your-enterprise)

### ssh\_certificate\_requirement

#### `ssh_certificate_requirement.disable`

The requirement for members to use SSH certificates to access an organization resources was disabled.

**Reference:** [Managing your organization's SSH certificate authorities](/en/enterprise-cloud@latest/organizations/managing-git-access-to-your-organizations-repositories/managing-your-organizations-ssh-certificate-authorities), [Enforcing policies for security settings in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-security-settings-in-your-enterprise#managing-ssh-certificate-authorities-for-your-enterprise)

#### `ssh_certificate_requirement.enable`

The requirement for members to use SSH certificates to access an organization resources was enabled.

**Reference:** [Managing your organization's SSH certificate authorities](/en/enterprise-cloud@latest/organizations/managing-git-access-to-your-organizations-repositories/managing-your-organizations-ssh-certificate-authorities), [Enforcing policies for security settings in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-security-settings-in-your-enterprise#managing-ssh-certificate-authorities-for-your-enterprise)

### sso\_lockdown

#### `sso_lockdown.disable`

SSO lockdown for users was disabled.

**Additional fields:** `actor_is_bot`

#### `sso_lockdown.enable`

SSO lockdown for users was enabled.

**Additional fields:** `actor_is_bot`

### sso\_redirect

Note: Automatically redirecting users to sign in is currently in beta for Enterprise Managed Users and subject to change.

#### `sso_redirect.disable`

Automatic redirects for users to single sign-on (SSO) was disabled.

#### `sso_redirect.enable`

Automatic redirects for users to single sign-on (SSO) was enabled.

### staff

#### `staff.set_domain_token_expiration`

The verification code expiry time for an organization or enterprise domain was set.

**Additional fields:** `owner_type`, `domain_name`, `token_expires_at`, `owner`

#### `staff.unverify_domain`

An organization or enterprise domain was unverified.

**Additional fields:** `owner_type`, `domain_name`, `owner`

#### `staff.verify_domain`

An organization or enterprise domain was verified.

**Additional fields:** `domain_name`

### team

#### `team.add_member`

A member of an organization was added to a team.

**Additional fields:** `team`, `team_type`

**Reference:** /organizations/organizing-members-into-teams/adding-organization-members-to-a-team

#### `team.add_repository`

A team was given access and permissions to a repository.

**Additional fields:** `team`, `actor_is_bot`

#### `team.add_to_organization`

A team was added to an organization.

**Additional fields:** `team_type`, `team`, `actor_is_bot`

#### `team.change_parent_team`

A child team was created or a child team's parent was changed.

**Additional fields:** `team`

**Reference:** /organizations/organizing-members-into-teams/moving-a-team-in-your-organizations-hierarchy

#### `team.change_privacy`

A team's privacy level was changed.

**Additional fields:** `team`, `team_type`

**Reference:** /organizations/organizing-members-into-teams/changing-team-visibility

#### `team.create`

A new team is created.

**Additional fields:** `oauth_application_id`, `team`, `team_type`

#### `team.demote_maintainer`

A user was demoted from a team maintainer to a team member.

**Additional fields:** `team`

**Reference:** /organizations/organizing-members-into-teams/assigning-the-team-maintainer-role-to-a-team-member

#### `team.destroy`

A team was deleted.

**Additional fields:** `team`, `team_type`

#### `team.promote_maintainer`

A user was promoted from a team member to a team maintainer.

**Additional fields:** `team`

**Reference:** /organizations/organizing-members-into-teams/assigning-the-team-maintainer-role-to-a-team-member#promoting-an-organization-member-to-team-maintainer

#### `team.remove_from_organization`

A team was removed from an organization.

**Additional fields:** `team_type`, `team`, `actor_is_bot`

#### `team.remove_member`

An organization member was removed from a team.

**Additional fields:** `team`, `team_type`

**Reference:** /organizations/organizing-members-into-teams/removing-organization-members-from-a-team

#### `team.remove_repository`

A repository was removed from a team's control.

**Additional fields:** `team`

#### `team.rename`

A team's name was changed.

**Additional fields:** `name`, `team`, `team_type`

#### `team.update_repository_permission`

A team's permission to a repository was changed.

**Additional fields:** `team`, `old_permission`, `permission`, `new_repo_permission`, `new_repo_base_role`, `old_repo_permission`, `old_repo_base_role`

### team\_sync\_tenant

#### `team_sync_tenant.disabled`

Team synchronization with a tenant was disabled.

**Reference:** [Managing team synchronization for your organization](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/managing-team-synchronization-for-your-organization), [Managing team synchronization for organizations in your enterprise](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/managing-team-synchronization-for-organizations-in-your-enterprise)

#### `team_sync_tenant.enabled`

Team synchronization with a tenant was enabled.

**Reference:** [Managing team synchronization for your organization](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/managing-team-synchronization-for-your-organization), [Managing team synchronization for organizations in your enterprise](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/managing-team-synchronization-for-organizations-in-your-enterprise)

#### `team_sync_tenant.update_okta_credentials`

The Okta credentials for team synchronization with a tenant were changed.

### user\_content\_edit

#### `user_content_edit.delete`

Triggered when a user content edit is deleted.

**Additional fields:** `user_content_id`, `user_content_type`, `deleted_by`, `editor_id`, `deleted_at`, `editor`, `deleted_by_id`, `deleted_content`

### user\_email

#### `user_email.confirm_claim`

An enterprise managed user claimed an email address.

**Additional fields:** `actor_is_bot`

### vulnerability\_alert\_rule

#### `vulnerability_alert_rule.create`

A Dependabot rule was created.

**Additional fields:** `vulnerability_alert_rule_id`, `vulnerability_alert_rule_name`

#### `vulnerability_alert_rule.delete`

A Dependabot rule was deleted.

**Additional fields:** `vulnerability_alert_rule_id`, `vulnerability_alert_rule_name`

#### `vulnerability_alert_rule.disable`

A Dependabot rule was disabled for a single repository or disabled by default for an organization.

**Additional fields:** `vulnerability_alert_rule_id`, `vulnerability_alert_rule_name`, `public_repo`

#### `vulnerability_alert_rule.enable`

A Dependabot rule was enabled for a single repository or enabled by default for an organization.

**Additional fields:** `vulnerability_alert_rule_id`, `vulnerability_alert_rule_name`, `public_repo`

#### `vulnerability_alert_rule.force_disable`

A Dependabot rule was enabled for an organization and cannot be disabled for its repositories.

**Additional fields:** `vulnerability_alert_rule_id`, `vulnerability_alert_rule_name`

#### `vulnerability_alert_rule.force_enable`

A Dependabot rule was disabled for an organization and cannot be enabled for its repositories.

**Additional fields:** `vulnerability_alert_rule_id`, `vulnerability_alert_rule_name`

#### `vulnerability_alert_rule.update`

A Dependabot rule's conditions, actions, or metadata changed.

**Additional fields:** `vulnerability_alert_rule_id`, `vulnerability_alert_rule_name`

### workflows

#### `workflows.approve_workflow_job`

A workflow job was approved.

**Additional fields:** `workflow_run_id`, `run_number`, `public_repo`

**Reference:** [Reviewing deployments](/en/enterprise-cloud@latest/actions/managing-workflow-runs/reviewing-deployments)

#### `workflows.cancel_workflow_run`

A workflow run was cancelled.

**Additional fields:** `started_at`, `event`, `name`, `workflow_run_id`, `head_branch`, `head_sha`, `run_number`, `cancelled_at`, `workflow_id`, `trigger_id`, `public_repo`

**Reference:** [Canceling a workflow run](/en/enterprise-cloud@latest/actions/managing-workflow-runs/canceling-a-workflow)

#### `workflows.completed_workflow_run`

A workflow status changed to completed. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `started_at`, `event`, `name`, `workflow_run_id`, `head_branch`, `head_sha`, `completed_at`, `conclusion`, `run_number`, `workflow_id`, `trigger_id`, `run_attempt`, `actor_is_bot`, `actor_is_agent`

**Reference:** [Viewing workflow run history](/en/enterprise-cloud@latest/actions/monitoring-and-troubleshooting-workflows/viewing-workflow-run-history)

#### `workflows.created_workflow_run`

A workflow run was create. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `started_at`, `event`, `name`, `workflow_run_id`, `head_branch`, `head_sha`, `workflow_id`, `trigger_id`, `public_repo`, `actor_is_bot`, `actor_is_agent`

**Reference:** [Understanding GitHub Actions](/en/enterprise-cloud@latest/actions/learn-github-actions/understanding-github-actions#create-an-example-workflow)

#### `workflows.delete_workflow_run`

A workflow run was deleted.

**Additional fields:** `workflow_run_id`, `started_at`, `head_branch`, `head_sha`, `trigger_id`

**Reference:** [Deleting a workflow run](/en/enterprise-cloud@latest/actions/managing-workflow-runs/deleting-a-workflow-run)

#### `workflows.disable_workflow`

A workflow was disabled.

**Additional fields:** `workflow_id`, `public_repo`, `actor_is_bot`

#### `workflows.enable_workflow`

A workflow was enabled, after previously being disabled by disable\_workflow.

**Additional fields:** `workflow_id`, `public_repo`

#### `workflows.pin_workflow`

A workflow was pinned.

**Additional fields:** `public_repo`, `workflow_id`, `actor_is_bot`

#### `workflows.prepared_workflow_job`

A workflow job was started. Includes the list of secrets that were provided to the job. This event is not available in the web interface, only via the REST API, audit log streaming, or JSON/CSV exports.

**Additional fields:** `workflow_run_id`, `job_name`, `runner_labels`, `is_hosted_runner`, `environment_name`, `secrets_passed`, `runner_owner_type`, `job_workflow_ref`, `calling_workflow_refs`, `calling_workflow_shas`, `imposer_repo`

**Reference:** [Events that trigger workflows](/en/enterprise-cloud@latest/actions/using-workflows/events-that-trigger-workflows)

#### `workflows.reject_workflow_job`

A workflow job was rejected.

**Additional fields:** `workflow_run_id`, `run_number`, `public_repo`

**Reference:** [Reviewing deployments](/en/enterprise-cloud@latest/actions/managing-workflow-runs/reviewing-deployments)

#### `workflows.rerun_workflow_run`

A workflow run was re-run.

**Additional fields:** `started_at`, `event`, `name`, `workflow_run_id`, `head_branch`, `head_sha`, `run_number`, `workflow_id`, `trigger_id`, `run_attempt`, `rerun_type`, `check_run_id`, `actor_is_bot`

**Reference:** [Re-running workflows and jobs](/en/enterprise-cloud@latest/actions/managing-workflow-runs/re-running-workflows-and-jobs)

#### `workflows.unpin_workflow`

A workflow was unpinned after previously being pinned.

**Additional fields:** `public_repo`, `workflow_id`, `actor_is_bot`