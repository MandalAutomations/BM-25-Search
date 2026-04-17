# About Enterprise Managed Users

Learn how your enterprise can manage the lifecycle and authentication of users on GitHub from your identity provider (IdP).

## What are Enterprise Managed Users in GitHub?

With Enterprise Managed Users, you manage the lifecycle and authentication of your users on GitHub.com or GHE.com **from an external identity management system, or IdP**:

* Your IdP **provisions new user accounts** on GitHub, with access to your enterprise.
* Users must **authenticate on your IdP** to access your enterprise's resources on GitHub.
* You control **usernames, profile data, organization membership, and repository access** from your IdP.
* If your enterprise uses OIDC SSO, GitHub will validate access to your enterprise and its resources using your IdP's **Conditional Access Policy (CAP)**. See [About support for your IdP's Conditional Access Policy](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/about-support-for-your-idps-conditional-access-policy).
* Managed user accounts **cannot create public content** or collaborate outside your enterprise. See [Abilities and restrictions of managed user accounts](/en/enterprise-cloud@latest/admin/identity-and-access-management/understanding-iam-for-enterprises/abilities-and-restrictions-of-managed-user-accounts).

> \[!NOTE] Enterprise Managed Users is not the best solution for every customer. To determine whether it's right for your enterprise, see [Choosing an enterprise type for GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/identity-and-access-management/understanding-iam-for-enterprises/choosing-an-enterprise-type-for-github-enterprise-cloud).

## How does EMUs integrate with identity management systems?

GitHub partners with some developers of identity management systems to provide a "paved-path" integration with Enterprise Managed Users. To simplify your configuration and ensure full support, **use a single partner IdP for both authentication and provisioning.**

### What are partner identity providers?

Partner IdPs provide authentication using SAML or OIDC, and provide provisioning with System for Cross-domain Identity Management (SCIM).

<div class="ghd-tool rowheaders">

| Partner IdP  | SAML                                                                                                                                                                                                                                                                                                                     | OIDC                                                                                                                                                                                                                                                                                                                                                                                                                                | SCIM                                                                                                                                                                                                                                                                                                                     |
| :----------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entra ID     | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                            | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Okta         | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Not supported" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| PingFederate | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Not supported" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |

</div>

When you use a single partner IdP for both authentication and provisioning, GitHub provides support for the application on the partner IdP and the IdP's integration with GitHub.

### Can I use identity management systems other than the supported partners?

If you cannot use a single partner IdP for both authentication and provisioning, you can use another identity management system or combination of systems. The system must:

* Adhere to **GitHub's integration guidelines**
* Provide **authentication using SAML**, adhering to SAML 2.0 specification
* Provide **user lifecycle management using SCIM**, adhering to the SCIM 2.0 specification and communicating with GitHub's REST API (see [Provisioning users and groups with SCIM using the REST API](/en/enterprise-cloud@latest/admin/identity-and-access-management/provisioning-user-accounts-for-enterprise-managed-users/provisioning-users-with-scim-using-the-rest-api))

GitHub does not expressly support mixing partner IdPs for authentication and provisioning and does not test all identity management systems. **GitHub's support team may not be able to assist you with issues related to mixed or untested systems.** If you need help, you must consult the system's documentation, support team, or other resources.

> \[!IMPORTANT] The combination of **Okta and Entra ID** for SSO and SCIM (in either order) is explicitly **not supported**. GitHub's SCIM API will return an error to the identity provider on provisioning attempts if this combination is configured.

## How are usernames and profile information managed for EMUs?

GitHub automatically creates a username for each developer by normalizing an identifier provided by your IdP. If the unique parts of the identifier are removed during normalization, a conflict may occur. See [Username considerations for external authentication](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-iam-for-your-enterprise/username-considerations-for-external-authentication#resolving-username-problems).

The profile name and email address of a managed user account is provided by the IdP:

* Managed user accounts *cannot* change their profile name or email address on GitHub.
* The IdP can only provide one email address.
* Changing a user's email address in your IdP will unlink the user from the contribution history associated with the old email address.

## How are roles and access managed for EMUs?

In your IdP, you can give each managed user account a **role in your enterprise**, such as member, owner, or guest collaborator. See [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise).

Organization memberships (and repository access) can be managed manually, or you can **update memberships automatically using IdP groups**. See [Managing team memberships with identity provider groups](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/managing-team-memberships-with-identity-provider-groups).

## How do managed user accounts authenticate to GitHub?

The locations where managed user accounts can authenticate to GitHub depends on how you configure authentication (SAML or OIDC). See [Authenticating with Enterprise Managed Users](/en/enterprise-cloud@latest/authentication/authenticating-with-single-sign-on/authenticating-with-a-managed-user-account).

By default, when an unauthenticated user attempts to access your enterprise, GitHub displays a 404 error. You can optionally enable automatic redirects to single sign-on (SSO) instead. See [Enforcing policies for security settings in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-security-settings-in-your-enterprise#managing-sso-for-unauthenticated-users).

## Further reading

* [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users)