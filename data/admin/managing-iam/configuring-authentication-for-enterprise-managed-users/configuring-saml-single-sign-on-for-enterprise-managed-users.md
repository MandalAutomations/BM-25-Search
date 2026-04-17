# Configuring SAML single sign-on for Enterprise Managed Users

You can automatically manage access to your enterprise account on GitHub by configuring Security Assertion Markup Language (SAML) single sign-on (SSO).

**Before** following the steps in this article, make sure that your enterprise uses **managed users** and that you are signed in as the setup user whose username is your enterprise's shortcode suffixed with `_admin`. You can verify you are signed in with the correct user by checking whether your enterprise view has the "Viewing as SHORTCODE\_admin" header bar at the top of the screen. If you see this, you are signed in with the correct user and you can follow the steps in this article. For more information about the setup user, see [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

If your enterprise uses **personal accounts**, you must follow a different process to configure SAML single sign-on. See [Configuring SAML single sign-on for your enterprise](/en/enterprise-cloud@latest/admin/managing-iam/using-saml-for-enterprise-iam/configuring-saml-single-sign-on-for-your-enterprise).

## About SAML SSO for Enterprise Managed Users

With Enterprise Managed Users, access to your enterprise's resources on GitHub.com or GHE.com must be authenticated through your identity provider (IdP). Instead of signing in with a GitHub username and password, members of your enterprise will sign in through your IdP.

After you configure SAML SSO, we recommend storing your recovery codes so you can recover access to your enterprise in the event that your IdP is unavailable.

If you currently use SAML SSO for authentication and would prefer to use OIDC and benefit from CAP support, you can follow a migration path. For more information, see [Migrating from SAML to OIDC](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/migrating-from-saml-to-oidc).

## Prerequisites

* Understand the integration requirements and level of support for your IdP.

  * GitHub offers a "paved-path" integration and full support if you use a **partner IdP** for both authentication and provisioning.
  * Alternatively, you can use any system or combination of systems that conforms to SAML 2.0 and SCIM 2.0. However, support for resolving problems with these systems may be limited.

  For more details, see [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/about-enterprise-managed-users#identity-management-systems).
* Your IdP must adhere to the SAML 2.0 specification. See the [SAML Wiki](https://wiki.oasis-open.org/security) on the OASIS website.
* You must have tenant administrative access to your IdP.
* If you're configuring SAML SSO for a new enterprise, make sure to complete all previous steps in the initial configuration process. See [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

## Configure SAML SSO for Enterprise Managed Users

To configure SAML SSO for your enterprise with managed users, you must configure an application on your IdP, then configure your enterprise on GitHub. After you configure SAML SSO, you can configure user provisioning.

1. [Configure your IdP](#configure-your-idp)
2. [Configure your enterprise](#configure-your-enterprise)
3. [Enable provisioning](#enable-provisioning)

### Configure your IdP

1. If you use a partner IdP, to install the GitHub Enterprise Managed User application, click the link for your IdP and environment.

   <div class="ghd-tool rowheaders">

   | Identity provider  | App for GitHub.com                                                                                                                                                                  | App for GHE.com                                                                                                                                                                     |
   | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Microsoft Entra ID | [GitHub Enterprise Managed User](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/aad.githubenterprisemanageduser?tab=Overview)                                        | [GitHub Enterprise Managed User](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/aad.githubenterprisemanageduser?tab=Overview)                                        |
   | Okta               | [GitHub Enterprise Managed User](https://www.okta.com/integrations/github-enterprise-managed-user)                                                                                  | [GitHub Enterprise Managed User - ghe.com](https://www.okta.com/integrations/github-enterprise-managed-user-ghe-com/)                                                               |
   | PingFederate       | [PingFederate downloads website](https://www.pingidentity.com/en/resources/downloads/pingfederate.html) (navigate to the **Add-ons** tab, then select **GitHub EMU Connector 1.0**) | [PingFederate downloads website](https://www.pingidentity.com/en/resources/downloads/pingfederate.html) (navigate to the **Add-ons** tab, then select **GitHub EMU Connector 1.0**) |

   </div>

2. To configure SAML SSO for Enterprise Managed Users on a partner IdP, read the relevant documentation for your IdP and environment.

   <div class="ghd-tool rowheaders">

   | Identity provider  | Documentation for GitHub.com                                                                                                                                                                                                                                              | Documentation for GHE.com                                                                                                                                                                                                                                                 |
   | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Microsoft Entra ID | [Microsoft Learn](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/github-enterprise-managed-user-tutorial)                                                                                                                                              | [Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-enterprise-managed-user-ghe-com-tutorial)                                                                                                                                             |
   | Okta               | [Configuring SAML single sign-on with Okta for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/configuring-authentication-for-enterprise-managed-users/configuring-saml-single-sign-on-with-okta-for-enterprise-managed-users) | [Configuring SAML single sign-on with Okta for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/configuring-authentication-for-enterprise-managed-users/configuring-saml-single-sign-on-with-okta-for-enterprise-managed-users) |
   | PingFederate       | [Configuring authentication and provisioning with PingFederate](/en/enterprise-cloud@latest/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-authentication-and-provisioning-with-pingfederate) ("Prerequisites" and "1. Configure SAML" sections)     | [Configuring authentication and provisioning with PingFederate](/en/enterprise-cloud@latest/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-authentication-and-provisioning-with-pingfederate) ("Prerequisites" and "1. Configure SAML" sections)     |

   </div>

   Alternatively, if you don't use a partner IdP, you can use the SAML configuration reference for GitHub to create and configure a generic SAML 2.0 application on your IdP. See [SAML configuration reference](/en/enterprise-cloud@latest/admin/identity-and-access-management/iam-configuration-reference/saml-configuration-reference).

3. To test and configure your enterprise, assign yourself or the user that will configure SAML SSO for your enterprise on GitHub to the application you configured for Enterprise Managed Users on your IdP.

   > \[!NOTE]
   > In order to test a successful authentication connection upon configuration, at least one user must be assigned to the IdP.

4. To continue configuring your enterprise on GitHub, locate and note the following information from the application you installed on your IdP.

   | Value                            | Other names        | Description                                                      |
   | :------------------------------- | :----------------- | :--------------------------------------------------------------- |
   | IdP Sign-On URL                  | Login URL, IdP URL | Application's URL on your IdP                                    |
   | IdP Identifier URL               | Issuer             | IdP's identifier to service providers for SAML authentication    |
   | Signing certificate, PEM-encoded | Public certificate | Public certificate that IdP uses to sign authentication requests |

### Configure your enterprise

After you configure SAML SSO for Enterprise Managed Users on your IdP, you can configure your enterprise on GitHub.

After the initial configuration of SAML SSO, the only setting you can update on GitHub for your existing SAML configuration is the SAML certificate, which can be done by any member with the enterprise owner role. If you need to update the sign-on URL or issuer URL, you must first disable SAML SSO, then reconfigure SAML SSO with the new settings. For more information, see [Disabling authentication for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/configuring-authentication-for-enterprise-managed-users/disabling-authentication-for-enterprise-managed-users).

1. Sign in as the setup user for your enterprise with the username **SHORTCODE\_admin**, replacing SHORTCODE with your enterprise's shortcode.

   > \[!NOTE]
   > If you need to reset the password for your setup user, contact GitHub Support through the [GitHub Support portal](https://support.github.com). The usual password reset option by providing your email address will not work.

2. If you're using a **non-partner IdP** (an IdP other than Okta, PingFederate or Entra ID), before enabling SAML, you must update a setting so that you will be able to set up SCIM using the REST API. See [Configuring SCIM provisioning for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users#configuring-provisioning-for-other-identity-management-systems).

3. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

4. At the top of the page, click **Identity provider**.

5. Under **Identity Provider**, click **Single sign-on configuration**.

6. Under "SAML single sign-on," select **Add SAML configuration**.

7. Under **Sign on URL**, type the HTTPS endpoint of your IdP for SSO requests that you noted while configuring your IdP.

8. Under **Issuer**, type your SAML issuer URL that you noted while configuring your IdP, to verify the authenticity of sent messages.

9. Under **Public Certificate**, paste the certificate that you noted while configuring your IdP, to verify SAML responses.

   > \[!NOTE]
   > GitHub does not enforce the expiration of this SAML IdP certificate. This means that even if this certificate expires, your SAML authentication will continue to work. However, GitHub's recommendation is to update the certificate before it expires. We will accept a SAML response signed with an expired certificate, but we cannot comment on how the certificate expiring will be handled at the identity provider level. If your IdP administrator regenerates the SAML certificate, and you don't update it on the GitHub side, users will encounter a `digest mismatch` error during SAML authentication attempts due to the certificate mismatch. See [Error: Digest mismatch](/en/enterprise-cloud@latest/admin/managing-iam/using-saml-for-enterprise-iam/troubleshooting-saml-authentication#error-digest-mismatch).

10. Under the same **Public Certificate** section, select the **Signature Method** and **Digest Method** dropdown menus, then click the hashing algorithm used by your SAML issuer.

11. Before enabling SAML SSO for your enterprise, to ensure that the information you've entered is correct, click **Test SAML configuration**. This test uses Service Provider initiated (SP-initiated) authentication and must be successful before you can save the SAML settings.

12. Click **Save SAML settings**.

    > \[!NOTE]
    > After you require SAML SSO for your enterprise and save SAML settings, the setup user will continue to have access to the enterprise and will remain signed in to GitHub along with the managed user accounts provisioned by your IdP who will also have access to the enterprise.

13. To ensure you can still access your enterprise on GitHub if your IdP is unavailable in the future, click **Download**, **Print**, or **Copy** to save your recovery codes. For more information, see [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes).

### Enable provisioning

After you enable SAML SSO, enable provisioning. For more information, see [Configuring SCIM provisioning for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-scim-provisioning-for-enterprise-managed-users).

### Enable guest collaborators

You can use the role of guest collaborator to grant limited access to vendors and contractors in your enterprise. Unlike enterprise members, guest collaborators only have access to internal repositories within organizations where they are a member.

If you use Entra ID or Okta for SAML authentication, you may need to update your IdP application to use guest collaborators. For more information, see [Enabling guest collaborators](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/enabling-guest-collaborators).