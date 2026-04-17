# Managing bots and service accounts with SAML single sign-on

Organizations that have enabled SAML single sign-on can retain access for bots and service accounts.

To retain access for bots and service accounts, organization administrators can [enable](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/enabling-and-testing-saml-single-sign-on-for-your-organization), but **not** [enforce](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/enforcing-saml-single-sign-on-for-your-organization) SAML single sign-on for their organization. If you need to enforce SAML single sign-on for your organization, you can create an external identity for the bot or service account with your identity provider (IdP).

> \[!NOTE]
> If you enforce SAML single sign-on for your organization and **do not** have external identities set up for bots and service accounts with your IdP, they will be removed from your organization.

## Further reading

* [About identity and access management with SAML single sign-on](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/about-identity-and-access-management-with-saml-single-sign-on)