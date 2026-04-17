# Identity and access management fundamentals

Administrators must decide how users will access the enterprise's resources on GitHub.

## What is IAM for GitHub?

To control access to your enterprise's resources, you can allow people to use a personal account on GitHub.com and optionally configure additional SAML access restrictions, or you can provision and control the accounts for your enterprise using your identity provider (IdP) with Enterprise Managed Users.

After learning more about authentication and provisioning for each of these options, to determine which method is best for your enterprise, see [Choosing an enterprise type for GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-iam-for-your-enterprise/identifying-the-best-authentication-method-for-your-enterprise).

## Which authentication method are available to me?

When you create an enterprise on GitHub, you can decide how people authenticate to access your resources and who controls the user accounts.

* [Authentication through GitHub.com](#authentication-through-githubcom)
* [Authentication through GitHub.com with additional SAML access restriction](#authentication-through-githubcom-with-additional-saml-access-restriction)
* [Authentication with Enterprise Managed Users and federation](#authentication-with-enterprise-managed-users-and-federation)

### Authentication through GitHub.com

With authentication solely through GitHub.com, each person you want to grant access to your enterprise must create and manage a personal account on GitHub.com. After you grant access to your enterprise, the member can access your enterprise's resources after signing into the account on GitHub.com. The member manages the account, and can contribute to other enterprises, organizations, and repositories on GitHub.com. For more information about personal accounts, see [Creating an account on GitHub](/en/enterprise-cloud@latest/get-started/signing-up-for-github/signing-up-for-a-new-github-account).

### Authentication through GitHub.com with additional SAML access restriction

If you configure additional SAML access restriction, each person you want to grant access to your enterprise must create and manage a personal account on GitHub.com. After you grant access to your enterprise, the member can access your enterprise's resources only after authenticating successfully for both the account on GitHub.com and for an account on your SAML identity provider (IdP). The member can contribute to other enterprises, organizations, and repositories on GitHub.com using their personal account. For more information about requiring SAML authentication for all access your enterprise's resources, see [About SAML for enterprise IAM](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/about-saml-for-enterprise-iam).

You can choose between configuring SAML at the enterprise level, which applies the same SAML configuration to all organizations within the enterprise, and configuring SAML separately for individual organizations. For more information, see [Deciding whether to configure SAML for your enterprise or your organizations](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/deciding-whether-to-configure-saml-for-your-enterprise-or-your-organizations).

### Authentication with Enterprise Managed Users and federation

If you need more control of the accounts for your enterprise members on GitHub, you can use Enterprise Managed Users. With Enterprise Managed Users, you provision and manage accounts for your enterprise members on GitHub using your IdP. Each member signs into an account that you create, and your enterprise manages the account. Contributions outside the enterprise are restricted. For more information, see [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/about-enterprise-managed-users).

## How does provisioning work?

If you use [authentication through GitHub.com with additional SAML access restriction](#authentication-through-githubcom-with-additional-saml-access-restriction), people create personal accounts on GitHub.com, and you can grant those personal accounts access to resources in your enterprise. You do not provision accounts.

Alternatively, if you use [Enterprise Managed Users](#authentication-with-enterprise-managed-users-and-federation), you must configure your IdP to provision user accounts within your enterprise on GitHub.com using System for Cross-domain Identity Management (SCIM). For more information, see [Provisioning accounts for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/provisioning-user-accounts-for-enterprise-managed-users).

## Which IdPs are supported?

If you choose to create an enterprise that uses personal accounts on GitHub.com, you can configure additional authentication with an external identity management system that adheres to the SAML 2.0 standard. GitHub also officially supports and tests some identity management systems. For more information, see [Configuring SAML single sign-on for your enterprise](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/configuring-saml-single-sign-on-for-your-enterprise#supported-identity-providers).

GitHub partners with some developers of identity management systems to provide a "paved-path" integration with Enterprise Managed Users. To simplify your configuration and ensure full support, **use a single partner IdP for both authentication and provisioning.** If you use a partner identity provider (IdP), you can configure one application on your IdP to provide authentication and provisioning. The IdP must support the SAML 2.0 standard. Alternatively, if you use Entra ID (previously known as Azure AD), you can configure OpenID Connect (OIDC) authentication. If you don't use a partner IdP, or if you only use a partner IdP for authentication, you can integrate IdPs that implement the SAML 2.0 and System for Cross-domain Identity Management (SCIM) 2.0 standards. For more information, see [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/understanding-iam-for-enterprises/about-enterprise-managed-users#about-authentication-and-user-provisioning).

## Further reading

* [Enterprise accounts](/en/enterprise-cloud@latest/admin/overview/about-enterprise-accounts)
* [Can I create accounts for people in my organization?](/en/enterprise-cloud@latest/organizations/managing-membership-in-your-organization/can-i-create-accounts-for-people-in-my-organization)