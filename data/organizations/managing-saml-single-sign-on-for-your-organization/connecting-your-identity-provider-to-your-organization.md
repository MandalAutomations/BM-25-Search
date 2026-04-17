# Connecting your identity provider to your organization

To use SAML single sign-on and SCIM, you must connect your identity provider (IdP) to your organization on GitHub.

## About connection of your IdP to your organization

When you enable SAML SSO for your GitHub organization, you connect your identity provider (IdP) to your organization. For more information, see [Enabling and testing SAML single sign-on for your organization](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/enabling-and-testing-saml-single-sign-on-for-your-organization).

> \[!NOTE]
> To use SAML single sign-on, your organization must use GitHub Enterprise Cloud. For more information about how you can try GitHub Enterprise Cloud for free, see [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud).

You can find the SAML and SCIM implementation details for your IdP in the IdP's documentation.

* Microsoft Active Directory Federation Services (AD FS) [SAML](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services)
* Microsoft Entra ID (previously known as Azure AD) [SAML](https://docs.microsoft.com/azure/active-directory/active-directory-saas-github-tutorial) and [SCIM](https://docs.microsoft.com/azure/active-directory/active-directory-saas-github-provisioning-tutorial)
* Okta [SAML](https://saml-doc.okta.com/SAML_Docs/How-to-Configure-SAML-2.0-for-Github-com.html) and [SCIM](https://developer.okta.com/standards/SCIM/)
* OneLogin [SAML](https://onelogin.service-now.com/support?id=kb_article\&sys_id=2929ddcfdbdc5700d5505eea4b9619c6) and [SCIM](https://onelogin.service-now.com/support?id=kb_article\&sys_id=5aa91d03db109700d5505eea4b96197e)
* PingOne [SAML](https://support.pingidentity.com/s/marketplace-integration/a7i1W0000004ID3QAM/github-connector)
* Shibboleth [SAML](https://shibboleth.atlassian.net/wiki/spaces/IDP4/overview)

> \[!NOTE]
> GitHub's supported identity providers for SCIM are Entra ID, Okta, and OneLogin. For more information about SCIM, see [About SCIM for organizations](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/about-scim-for-organizations).
>
> You cannot use this implementation of SCIM with an enterprise account or with an organization with managed users. If your enterprise is enabled for Enterprise Managed Users, you must use a different implementation of SCIM. Otherwise, SCIM is not available at the enterprise level. For more information, see [Configuring SCIM provisioning for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-scim-provisioning-for-enterprise-managed-users).

## SAML metadata

For more information about SAML metadata for your organization, see [SAML configuration reference](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/saml-configuration-reference).