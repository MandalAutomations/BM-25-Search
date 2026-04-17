# Disabling authentication for Enterprise Managed Users

You can disable SAML or OIDC single sign-on (SSO) authentication for Enterprise Managed Users by using a recovery code to sign in as the setup user.

## About disabled authentication for Enterprise Managed Users

After you disable SAML or OIDC authentication for your enterprise, the following effects apply:

* All external identities for the enterprise, and associated email addresses for managed user accounts, will be removed. For more information, see [Viewing and managing a user's SAML access to your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/viewing-and-managing-a-users-saml-access-to-your-enterprise).
* All managed user accounts will be suspended. The suspended accounts will not be renamed. For more information, see [Viewing people in your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/viewing-people-in-your-enterprise#viewing-suspended-members).
* All personal access tokens and SSH keys associated with managed user accounts will be deleted.
* All of the external groups provisioned by SCIM will be deleted. For more information, see [Managing team memberships with identity provider groups](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/managing-team-memberships-with-identity-provider-groups).

If you later reconfigure authentication for the enterprise, external groups must be reprovisioned via SCIM, and managed user accounts must be reprovisioned before users can sign in.

> \[!NOTE]
>
> * The authentication disabling process can require substantial time to complete for enterprises with a large number of members.
> * Avatar data for managed user accounts is permanently removed upon suspension. Reprovisioned users will need to reupload their avatar.

If you want to migrate to a new identity provider (IdP) or tenant rather than disabling authentication entirely, see [Migrating your enterprise to a new identity provider or tenant](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/migrating-your-enterprise-to-a-new-identity-provider-or-tenant).

## Disabling authentication

> \[!WARNING]
> Disabling authentication and provisioning will prevent your enterprise's managed user accounts from signing in to access your enterprise on GitHub.

1. Sign in as the setup user for your enterprise with the username **SHORTCODE\_admin**, replacing SHORTCODE with your enterprise's shortcode.

2. Attempt to access your enterprise account, and use a recovery code to bypass SAML SSO or OIDC. For more information, see [Accessing your enterprise account if your identity provider is unavailable](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/accessing-your-enterprise-account-if-your-identity-provider-is-unavailable).

3. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

4. At the top of the page, click **Identity provider**.

5. Under **Identity Provider**, click **Single sign-on configuration**.

6. Next to "SAML single sign-on" or "OIDC single sign-on", click to deselect **SAML single sign-on** or **OIDC single sign-on**.

7. To confirm, click **Disable SAML single sign-on** or **Disable OIDC single sign-on**.