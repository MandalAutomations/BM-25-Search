# Adding users to your enterprise

Add users to your enterprise and control access to your organization's resources.

The method of adding users to your enterprise and controlling authentication varies depending on the enterprise type that you chose.

## Personal accounts

If you chose an enterprise with personal accounts, you will invite users to your enterprise with their existing GitHub account.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. On the "Members" page, click **Invite member**.
4. Search for the users you want to invite, then click **Invite**.

After you invite someone to join the enterprise account, they must accept the emailed invitation before they can access the enterprise account. Pending invitations will expire after 7 days.

Later in this onboarding journey, you will add users to teams to grant access to organizations and delegate administrative roles.

### Enabling single sign-on for personal accounts

Single sign-on (SSO) gives organization owners and enterprise owners a way to control and secure access to organization resources like repositories, issues, and pull requests.

1. Check if your SAML service is supported. See [About identity and access management with SAML single sign-on](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/about-identity-and-access-management-with-saml-single-sign-on#supported-saml-services).
2. Decide whether to configure SAML for your enterprise account or for individual organizations. See [Deciding whether to configure SAML for your enterprise or your organizations](/en/enterprise-cloud@latest/admin/managing-iam/using-saml-for-enterprise-iam/deciding-whether-to-configure-saml-for-your-enterprise-or-your-organizations).
3. If you're enabling SAML for the enterprise, you can do so now. See [Configuring SAML single sign-on for your enterprise](/en/enterprise-cloud@latest/admin/managing-iam/using-saml-for-enterprise-iam/configuring-saml-single-sign-on-for-your-enterprise).

## Enterprise Managed Users

With Enterprise Managed Users, you manage the lifecycle and authentication of your users on GitHub.com or GHE.com from an external identity management system, or IdP:

* Your IdP **provisions new user accounts** on GitHub, with access to your enterprise.
* Users must **authenticate on your IdP** to access your enterprise's resources on GitHub.
* You control **usernames, profile data, organization membership, and repository access** from your IdP.
* If your enterprise uses OIDC SSO, GitHub will validate access to your enterprise and its resources using your IdP's **Conditional Access Policy (CAP)**.
* Managed user accounts **cannot create public content** or collaborate outside your enterprise.

### Get started with managed users

To use Enterprise Managed Users, you will:

* Configure authentication using SAML or OIDC
* Configure SCIM provisioning
* Provision users to your enterprise

To get started, see [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

## Next steps

Learn about how billing will work when your trial ends. See [About enterprise billing](/en/enterprise-cloud@latest/enterprise-onboarding/getting-started-with-your-enterprise/about-enterprise-billing).