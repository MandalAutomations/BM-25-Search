# About user provisioning with SCIM on GitHub Enterprise Server

Learn about managing the lifecycle of user accounts with SCIM on GitHub.com.

## About user provisioning for GitHub Enterprise Server

If you use SAML single sign-on (SSO) for your GitHub Enterprise Server instance, you can configure SCIM to automatically create or suspend user accounts and grant access to your instance when you assign or unassign the application on your IdP. For more information about SCIM, see [System for Cross-domain Identity Management: Protocol (RFC 7644)](https://tools.ietf.org/html/rfc7644) on the IETF website.

If you do not configure user provisioning with SCIM, your IdP will not communicate with GitHub Enterprise Server automatically when you assign or unassign the application to a user. Without SCIM, GitHub Enterprise Server creates a user account using SAML Just-in-Time (JIT) provisioning the first time someone navigates to GitHub Enterprise Server and signs in by authenticating through your IdP.

To configure provisioning for your enterprise, you must enable provisioning on GitHub Enterprise Server, then either install and configure a provisioning application on your IdP, or configure SCIM provisioning manually using GitHub's REST API endpoints for SCIM.

## Supported identity providers

GitHub partners with some developers of identity management systems to provide a "paved-path" integration with GitHub Enterprise Server. To simplify your configuration and ensure full support, **use a single partner IdP for both authentication and provisioning.**

### Partner identity providers

The following IdPs are partner IdPs. They offer an application that you can use to configure both SAML authentication and SCIM provisioning.

* Microsoft Entra ID
* Okta
* PingFederate (public preview)

When you use a single partner IdP for both authentication and provisioning, GitHub provides support for the application on the partner IdP and the IdP's integration with GitHub. The same application must be used for both SAML authentication and SCIM provisioning. Support for PingFederate is in public preview.

We do not have a supported partner application when using Entra ID for Azure Government.

### Other identity management systems

If you cannot use a single partner IdP for both authentication and provisioning, you can use another identity management system or combination of systems. The system must:

* Adhere to **GitHub's integration guidelines**
* Provide **authentication using SAML**, adhering to SAML 2.0 specification
* Provide **user lifecycle management using SCIM**, adhering to the SCIM 2.0 specification and communicating with GitHub's REST API (see [Provisioning users and groups with SCIM using the REST API](/en/enterprise-server@3.20/admin/identity-and-access-management/provisioning-user-accounts-for-enterprise-managed-users/provisioning-users-with-scim-using-the-rest-api))

## How will I manage user lifecycles with SCIM?

With SCIM, you manage the lifecycle of user accounts from your IdP:

* When you provision a new user, your IdP will prompt your GitHub Enterprise Server instance to create an account and send an onboarding email to the user. If you assign a group to the application in your IdP, your IdP will provision accounts for all members of the group.
* When you update information associated with a user's identity on your IdP, your IdP will update the user's account on GitHub.
* When you unassign the user from the IdP application or deactivate a user's account on your IdP, your IdP will communicate with GitHub to invalidate any sessions and disable the member's account. The disabled account's information is maintained and their username is changed to a hash of their original username.
* If you reassign a user to the IdP application or reactivate their account on your IdP, the user account will be reactivated, and the username will be restored.

To configure team and organization membership, repository access, and permissions, you can use groups on your IdP. For more information, see [Managing team memberships with identity provider groups](/en/enterprise-server@3.20/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/managing-team-memberships-with-identity-provider-groups).

When SCIM is enabled, you will no longer be able to delete, suspend, or promote SCIM-provisioned users directly on GitHub Enterprise Server. You must manage these processes from your IdP. If an issue arises with your IdP and you need to manage a user directly, you will need to use the SCIM REST API to manage the user identities on your appliance (see [Provisioning users and groups with SCIM using the REST API](/en/enterprise-server@3.20/admin/identity-and-access-management/provisioning-user-accounts-for-enterprise-managed-users/provisioning-users-with-scim-using-the-rest-api)).

To view suspended members, navigate to the "Suspended Members" tab of your enterprise settings.  This page will be present when SCIM is enabled on GitHub Enterprise Server.

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Click **Suspended Members**.

## What happens when I enable SCIM?

If you currently use SAML SSO, and you are enabling SCIM, you should be aware of what happens to existing user accounts on GitHub Enterprise Server once SCIM is enabled.

* Existing users with SAML mappings will **not be able to sign in** until their identities have been provisioned by SCIM.
* Existing users created with **Built in authentication** will only be able to sign in if **Built in authentication** is still enabled.
* GitHub Enterprise Server will no longer store SAML mappings for users. Instead, SCIM identities will be stored for users when a user is provisioned.
* You will no longer see the "SAML authentication" section on the `https://HOSTNAME/users/USER/security` site admin page for users. It will not be possible to view or update SAML NameID mappings that were previously visible in this section, since these stored SAML mappings are no longer evaluated during SAML authentication when SCIM is enabled.
* When your instance receives a SCIM request, SCIM identities are matched to existing users by **comparing the SCIM `userName` attribute value with the GitHub Enterprise Server username**. This means that an existing GitHub Enterprise Server user account, regardless of whether it was originally created as a local user account or via SAML JIT-provisioning, can be converted into a SCIM-linked user account if these two values match.
  * If a user account with a matching username does exist, GitHub Enterprise Server links the SCIM identity to this user account.
  * If a user account with a matching username doesn't exist, GitHub Enterprise Server creates a new user account and links it to this SCIM identity.
* If GitHub successfully matches a user who is authenticating via SAML with an existing user account, but account details such as email address, first name, or last name don't match, the instance **overwrites the details** with values from the IdP. Any email addresses other than the primary email provisioned by SCIM will also be deleted from the user account.
* Enterprise administrators with CLI access can export a full CSV of SCIM provisioned user identities using the [ghe-scim-identities-csv](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/command-line-utilities#ghe-scim-identities-csv) tool.

## What happens during SAML authentication?

After an IdP administrator grants a person access to your GitHub Enterprise Server instance, the user can authenticate through the IdP to access GitHub Enterprise Server using SAML SSO.

* When a user authenticates through SAML, to associate a user with a SAML identity, GitHub compares a normalized `NameID` claim from the IdP (or another value you have configured) to the account's username. For details about normalization, see [Username considerations for external authentication](/en/enterprise-server@3.20/admin/identity-and-access-management/managing-iam-for-your-enterprise/username-considerations-for-external-authentication#about-username-normalization).
* If there is no account with a matching username on the instance, the user will fail to sign in.
  * To make this match, GitHub Enterprise Server compares the SAML `NameId` claim from the IdP to the SCIM `userName` attribute for each user account provisioned by SCIM on the instance.
  * Additionally, for Entra ID, GitHub Enterprise Server compares the object identifier from the SAML request with an existing SCIM external ID.
* If your environment does not use `NameID` to uniquely identify users, a site administrator can configure custom user attributes for the instance. GitHub Enterprise Server will respect this mapping when SCIM is configured. For more information about mapping user attributes, see [Configuring SAML single sign-on for your enterprise](/en/enterprise-server@3.20/admin/identity-and-access-management/using-saml-for-enterprise-iam/configuring-saml-single-sign-on-for-your-enterprise#configuring-saml-sso).

## How is SCIM disabled?

For more information on the different ways that SCIM can be disabled, see [Disabling SCIM provisioning for users](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/disabling-scim-provisioning-for-users).

## Getting started

To get started with SCIM, you will:

1. Complete initial setup, required regardless of which IdP you will use, in [Configuring SCIM provisioning to manage users](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users).
2. Configure settings in your IdP.
   * If you're using a partner IdP for authentication and provisioning, you'll follow a guide for your IdP.
   * Otherwise, you'll set up a SCIM integration with the REST API, as described in [Provisioning users and groups with SCIM using the REST API](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/provisioning-users-and-groups-with-scim-using-the-rest-api).