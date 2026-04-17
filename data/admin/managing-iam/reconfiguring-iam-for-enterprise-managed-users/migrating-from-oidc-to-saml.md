# Migrating from OIDC to SAML

If you're using OpenID Connect (OIDC) to authenticate members in your enterprise with managed users, you can migrate to SAML SSO.

> \[!NOTE] OpenID Connect (OIDC) and Conditional Access Policy (CAP) support for Enterprise Managed Users is only available for Microsoft Entra ID (previously known as Azure AD).

## About migration of an enterprise with managed users from OIDC to SAML

To migrate from OIDC to SAML, you will first disable OIDC, which will suspend all managed user accounts, remove all SCIM-provisioned external groups, and delete linked identities.

Then, you will configure SAML and SCIM. At this time, users, groups, and identities will be re-provisioned.

If you're new to Enterprise Managed Users and haven't yet configured authentication for your enterprise, you do not need to migrate and can set up SAML single sign-on (SSO) immediately. For more information, see [Configuring SAML single sign-on for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-saml-single-sign-on-for-enterprise-managed-users).

> \[!WARNING]
> When you migrate to a new IdP or tenant, connections between GitHub teams and IdP groups are removed, and are not reinstated after the migration. This will remove all members from the team and leave the team unconnected to your IdP, which may cause disruption if you use team sync to manage access to organizations or licenses from your IdP. We recommend you use the "External groups" endpoints of the REST API to gather information about your teams setup before you migrate, and to reinstate connections afterwards. For more information, see [REST API endpoints for external groups](/en/enterprise-cloud@latest/rest/teams/external-groups).

## Prerequisites

* Your enterprise on GitHub must currently be configured to use OIDC for authentication. For more information, see [Configuring OIDC for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-oidc-for-enterprise-managed-users).
* You'll need to access both your enterprise on GitHub and your tenant on Entra ID.

  * To configure the GitHub Enterprise Managed User (OIDC) application on Entra ID, you must sign into the Entra ID tenant as a user with the Global Administrator role.
  * To sign in as the setup user for your enterprise on GitHub, you must use a recovery code for the enterprise. For more information, see [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes).
* Schedule a time to migrate when people aren't actively using your enterprise's resources. During the migration, users cannot access your enterprise until after you configure the new application and users as re-provisioned.

## Migrating your enterprise

1. Sign in as the setup user for your enterprise with the username **SHORTCODE\_admin**, replacing SHORTCODE with your enterprise's shortcode.

2. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

3. When prompted to continue to your identity provider, click **Use a recovery code** and sign in using one of your enterprise's recovery codes.

   > \[!NOTE]
   > You must use a recovery code for your enterprise, not your user account. For more information, see [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes).

4. At the top of the page, click **Identity provider**.

5. Under **Identity Provider**, click **Single sign-on configuration**.

6. Deselect **OIDC single sign-on**.

7. Confirm and click **Disable OIDC single sign-on**.

8. Configure SAML authentication and SCIM provisioning. See [Tutorial: Microsoft Entra single sign-on (SSO) integration with GitHub Enterprise Managed User](https://learn.microsoft.com/entra/identity/saas-apps/github-enterprise-managed-user-tutorial) on Microsoft Learn.