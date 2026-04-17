# Configuring OIDC for Enterprise Managed Users

Learn how to automatically manage access to your enterprise account on GitHub by configuring OpenID Connect (OIDC) single sign-on (SSO) and enabling support for your IdP's Conditional Access Policy (CAP).

> \[!NOTE] OpenID Connect (OIDC) and Conditional Access Policy (CAP) support for Enterprise Managed Users is only available for Microsoft Entra ID (previously known as Azure AD).

## About OIDC for Enterprise Managed Users

With Enterprise Managed Users, your enterprise uses your identity provider (IdP) to authenticate all members. You can use OpenID Connect (OIDC) to manage authentication for your enterprise with managed users. Enabling OIDC SSO is a one-click setup process with certificates managed by GitHub and your IdP.

When your enterprise uses OIDC SSO, GitHub will automatically use your IdP's conditional access policy (CAP) IP conditions to validate interactions with GitHub when members use the web UI or change IP addresses, and for each authentication with a personal access token or SSH key associated with a user account. See [About support for your IdP's Conditional Access Policy](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/about-support-for-your-idps-conditional-access-policy).

> \[!NOTE] CAP protection for web sessions is currently in public preview and may change.
>
> If IdP CAP support is already enabled for your enterprise, you can opt into extended protection for web sessions from your enterprise's "Authentication security" settings.
> When web session protection is enabled and a user's IP conditions are not satisfied, they can view and filter all user-owned resources but cannot view the details of the results for notifications, searches, personal dashboards, or starred repositories.

You can adjust the lifetime of a session, and how often a managed user account needs to reauthenticate with your IdP, by changing the lifetime policy property of the ID tokens issued for GitHub from your IdP. The default lifetime is one hour. See [Configure token lifetime policies](https://learn.microsoft.com/en-us/entra/identity-platform/configure-token-lifetimes#create-a-policy-and-assign-it-to-a-service-principal) in the Microsoft documentation.

To change the lifetime policy property, you will need the object ID associated with your Enterprise Managed Users OIDC. See [Finding the object ID for your Entra OIDC application](/en/enterprise-cloud@latest/admin/identity-and-access-management/configuring-authentication-for-enterprise-managed-users/finding-the-object-id-for-your-entra-oidc-application).

> \[!NOTE] If you need assistance configuring the OIDC session lifetime, contact [Microsoft Support](https://support.microsoft.com).

If you currently use SAML SSO for authentication and would prefer to use OIDC and benefit from CAP support, you can follow a migration path. For more information, see [Migrating from SAML to OIDC](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/migrating-from-saml-to-oidc).

> \[!WARNING]
> If you use GitHub Enterprise Importer to migrate an organization from your GitHub Enterprise Server instance, make sure to use a service account that is exempt from Entra ID's CAP otherwise your migration may be blocked.

## Identity provider support

Support for OIDC is available for customers using Entra ID.

Each Entra ID tenant can support only one OIDC integration with Enterprise Managed Users. If you want to connect Entra ID to more than one enterprise on GitHub, use SAML instead. See [Configuring SAML single sign-on for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-saml-single-sign-on-for-enterprise-managed-users).

OIDC does not support IdP-initiated authentication.

> \[!NOTE] Custom OIDC claims and attributes are not supported.

## Configuring OIDC for Enterprise Managed Users

1. Sign into GitHub as the setup user for your new enterprise with the username **@SHORT-CODE\_admin**.

2. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

3. At the top of the page, click **Identity provider**.

4. Under **Identity Provider**, click **Single sign-on configuration**.

5. Under "OIDC single sign-on", select **Enable OIDC configuration**.

6. To continue setup and be redirected to Entra ID, click **Save**.

7. After GitHub redirects you to your IdP, sign in, then follow the instructions to give consent and install the GitHub Enterprise Managed User (OIDC) application. After Entra ID asks for permissions for GitHub Enterprise Managed Users with OIDC, enable **Consent on behalf of your organization**, then click **Accept**.

   > \[!WARNING]
   > You must sign in to Entra ID as a user with global admin rights in order to consent to the installation of the GitHub Enterprise Managed User (OIDC) application.

8. To ensure you can still access your enterprise on GitHub if your IdP is unavailable in the future, click **Download**, **Print**, or **Copy** to save your recovery codes. For more information, see [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes).

9. Click **Enable OIDC Authentication**.

## Enabling provisioning

After you enable OIDC SSO, enable provisioning. See [Configuring SCIM provisioning for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-scim-provisioning-for-enterprise-managed-users).

## Enabling guest collaborators

You can use the role of guest collaborator to grant limited access to vendors and contractors in your enterprise. Unlike enterprise members, guest collaborators only have access to internal repositories within organizations where they are a member.

To use guest collaborators with OIDC authentication, you may need to update your settings in Entra ID. See [Enabling guest collaborators](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/enabling-guest-collaborators).