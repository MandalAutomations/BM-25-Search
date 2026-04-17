# Migrating from SAML to OIDC

If you're using SAML to authenticate members in your enterprise with managed users, you can migrate to OpenID Connect (OIDC) and benefit from support for your IdP's Conditional Access Policy.

> \[!NOTE] OpenID Connect (OIDC) and Conditional Access Policy (CAP) support for Enterprise Managed Users is only available for Microsoft Entra ID (previously known as Azure AD).

## About migration of an enterprise with managed users from SAML to OIDC

If your enterprise with managed users uses SAML SSO to authenticate with Entra ID, you can migrate to OIDC. When your enterprise uses OIDC SSO, GitHub will automatically use your IdP's conditional access policy (CAP) IP conditions to validate interactions with GitHub when members use the web UI or change IP addresses, and for each authentication with a personal access token or SSH key associated with a user account.

> \[!NOTE] CAP protection for web sessions is currently in public preview and may change.
>
> If IdP CAP support is already enabled for your enterprise, you can opt into extended protection for web sessions from your enterprise's "Authentication security" settings.
> When web session protection is enabled and a user's IP conditions are not satisfied, they can view and filter all user-owned resources but cannot view the details of the results for notifications, searches, personal dashboards, or starred repositories.

When you migrate from SAML to OIDC, managed user accounts and groups that were previously provisioned for SAML but are not provisioned by the GitHub Enterprise Managed User (OIDC) application will have "(SAML)" appended to their display names.

If you're new to Enterprise Managed Users and haven't yet configured authentication for your enterprise, you do not need to migrate and can set up OIDC single sign-on immediately. For more information, see [Configuring OIDC for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-oidc-for-enterprise-managed-users).

> \[!WARNING]
> When you migrate to a new IdP or tenant, connections between GitHub teams and IdP groups are removed, and are not reinstated after the migration. This will remove all members from the team and leave the team unconnected to your IdP, which may cause disruption if you use team sync to manage access to organizations or licenses from your IdP. We recommend you use the "External groups" endpoints of the REST API to gather information about your teams setup before you migrate, and to reinstate connections afterwards. For more information, see [REST API endpoints for external groups](/en/enterprise-cloud@latest/rest/teams/external-groups).

## Prerequisites

* Your enterprise on GitHub must currently be configured to use SAML for authentication, with Entra ID as your identity provider (IdP). For more information, see [Configuring SAML single sign-on for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-saml-single-sign-on-for-enterprise-managed-users).
* You'll need to access both your enterprise on GitHub and your tenant on Entra ID.

  * To configure the GitHub Enterprise Managed User (OIDC) application on Entra ID, you must sign into the Entra ID tenant as a user with the Global Administrator role.
  * To sign in as the setup user for your enterprise on GitHub, you must use a recovery code for the enterprise. For more information, see [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes).
* Schedule a time to migrate when people aren't actively using your enterprise's resources. During the migration, users cannot access your enterprise until after you configure the new application and users as re-provisioned.

## Migrating your enterprise

To migrate your enterprise from SAML to OIDC, you will disable your existing GitHub Enterprise Managed User application on Entra ID, prepare and begin the migration as the setup user for your enterprise on GitHub, then install and configure the new application for OIDC on Entra ID. After the migration is complete and Entra ID provisions your users, the users can authenticate to access your enterprise's resources on GitHub using OIDC.

> \[!WARNING]
> Migration of your enterprise from SAML to OIDC can take up to an hour. During the migration, users cannot access your enterprise on GitHub.

1. Before you begin the migration, sign in to Azure and disable provisioning in the existing GitHub Enterprise Managed User application.

2. If you use [Conditional Access (CA) network location policies](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/location-condition) in Entra ID, and you're currently using an IP allow list with your enterprise account or any of the organizations owned by the enterprise account, disable the IP allow lists. See [Enforcing policies for security settings in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-security-settings-in-your-enterprise#managing-allowed-ip-addresses-for-organizations-in-your-enterprise) and [Managing allowed IP addresses for your organization](/en/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-allowed-ip-addresses-for-your-organization).

3. Sign in as the setup user for your enterprise with the username **SHORTCODE\_admin**, replacing SHORTCODE with your enterprise's shortcode.

4. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

5. When prompted to continue to your identity provider, click **Use a recovery code** and sign in using one of your enterprise's recovery codes.

   > \[!NOTE]
   > You must use a recovery code for your enterprise, not your user account. For more information, see [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes).

6. At the top of the page, click **Identity provider**.

7. Under **Identity Provider**, click **Single sign-on configuration**.

8. At the bottom of the page, click **Migrate to OpenID Connect single sign-on**.

9. Read the warning, then click **Migrate to OIDC**.

10. Click **Begin OIDC migration**.

11. After GitHub redirects you to your IdP, sign in, then follow the instructions to give consent and install the GitHub Enterprise Managed User (OIDC) application. After Entra ID asks for permissions for GitHub Enterprise Managed Users with OIDC, enable **Consent on behalf of your organization**, then click **Accept**.

    > \[!WARNING]
    > You must sign in to Entra ID as a user with global admin rights in order to consent to the installation of the GitHub Enterprise Managed User (OIDC) application.

12. After you grant consent, a new browser window will open to GitHub and display a new set of recovery codes for your enterprise with managed users. Download the codes, then click **Enable OIDC authentication**.

13. Wait for the migration to complete, which can take up to an hour. To check the status of the migration, navigate to your enterprise's authentication security settings page. If "Require SAML authentication" is selected, the migration is still in progress.

    > \[!WARNING]
    > Do not provision new users from the application on Entra ID during the migration.

14. In a new tab or window, while signed in as the setup user, create a personal access token (classic) with the **scim:enterprise** scope and **no expiration** and copy it to your clipboard. For more information about creating a new token, see [Configuring SCIM provisioning for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-scim-provisioning-for-enterprise-managed-users#creating-a-personal-access-token).

15. In the provisioning settings for the GitHub Enterprise Managed User (OIDC) application in the Microsoft Entra admin center, under "Tenant URL", the tenant URL for your enterprise:
    * For **GitHub.com**: `https://api.github.com/scim/v2/enterprises/YOUR_ENTERPRISE`, replacing YOUR\_ENTERPRISE with the name of your enterprise account. For example, if your enterprise account's URL is `https://github.com/enterprises/octo-corp`, the name of the enterprise account is `octo-corp`.
    * For **GHE.com**: `https://api.SUBDOMAIN.ghe.com/scim/v2/enterprises/SUBDOMAIN`, where SUBDOMAIN is your enterprise's subdomain on GHE.com.

16. Under "Secret token", paste the personal access token (classic) with the **scim:enterprise** scope that you created earlier.

17. To test the configuration, click **Test Connection**.

18. To save your changes, at the top of the form, click **Save**.

19. In the Microsoft Entra admin center, copy the users and groups from the old GitHub Enterprise Managed User application to the new GitHub Enterprise Managed User (OIDC) application.

20. Test your configuration by provisioning a single new user.

21. If your test is successful, start provisioning for all users by clicking **Start provisioning**.