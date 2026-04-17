# Configuring SCIM provisioning for Enterprise Managed Users

You can manage the lifecycle of your enterprise's user accounts from your identity provider (IdP) using System for Cross-domain Identity Management (SCIM).

To create, manage, and deactivate user accounts for your enterprise members on GitHub, your IdP must implement SCIM for communication with GitHub. SCIM is an open specification for management of user identities between systems. Different IdPs provide different experiences for the configuration of SCIM provisioning.

If you use a partner IdP, you can simplify the configuration of SCIM provisioning by using the partner IdP's application. If you don't use a partner IdP for provisioning, you can implement SCIM using calls to GitHub's REST API for SCIM. For more information, see [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/about-enterprise-managed-users#identity-management-systems).

## About user lifecycle management with SCIM

With SCIM, you manage the lifecycle of user accounts from your IdP:

* After you configure provisioning for Enterprise Managed Users, your IdP uses SCIM to provision user accounts on GitHub and add the accounts to your enterprise. If you assign a group to the application in your IdP, your IdP will provision accounts for all members of the group.
* When you update information associated with a user's identity on your IdP, your IdP will update the user's account on GitHub.
* When you unassign the user from the IdP application or deactivate a user's account on your IdP, your IdP will communicate with GitHub to invalidate any sessions and disable the member's account. The disabled account's information is maintained and their username is changed to a hash of their original username, with the short code appended if applicable.
* If you reassign a user to the IdP application or reactivate their account on your IdP, the user account will be reactivated, and the username will be restored.

To configure team and organization membership, repository access, and permissions, you can use groups on your IdP. For more information, see [Managing team memberships with identity provider groups](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/managing-team-memberships-with-identity-provider-groups).

## Prerequisites

If you're configuring SCIM provisioning for a new enterprise, make sure to complete all previous steps in the initial configuration process. See [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

## Configuring user provisioning for Enterprise Managed Users

After completing the setup on GitHub, you can configure provisioning on your IdP. The instructions you should follow differ depending on whether you use a partner IdP's application for both authentication and provisioning.

* [Configuring provisioning if you use a partner IdP's application](#configuring-provisioning-if-you-use-a-partner-idps-application)
* [Configuring provisioning for other identity management systems](#configuring-provisioning-for-other-identity-management-systems)

### Configuring provisioning if you use a partner IdP's application

To use a partner IdP's application both authentication and provisioning, review the partner's instructions for configuring provisioning in the links in the following table.

<div class="ghd-tool rowheaders">

| IdP                                               | SSO method | Instructions                                                                                                                                                                                                                                                               |
| ------------------------------------------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft Entra ID (previously known as Azure AD) | OIDC       | [Tutorial: Configure GitHub Enterprise Managed User (OIDC) for automatic user provisioning](https://docs.microsoft.com/azure/active-directory/saas-apps/github-enterprise-managed-user-oidc-provisioning-tutorial) on Microsoft Learn                                      |
| Entra ID                                          | SAML       | [Tutorial: Configure GitHub Enterprise Managed User for automatic user provisioning](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/github-enterprise-managed-user-provisioning-tutorial) on Microsoft Learn                                            |
| Okta                                              | SAML       | [Configuring SCIM provisioning with Okta](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-scim-provisioning-for-enterprise-managed-users-with-okta)                                                    |
| PingFederate                                      | SAML       | The "Prerequisites" and "2. Configure SCIM" sections in [Configuring authentication and provisioning with PingFederate](/en/enterprise-cloud@latest/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-authentication-and-provisioning-with-pingfederate) |

</div>

### Configuring provisioning for other identity management systems

If you don't use a partner IdP, or if you only use a partner IdP for SAML authentication, you can manage the lifecycle of user accounts using GitHub's REST API endpoints for SCIM provisioning. See [Provisioning users and groups with SCIM using the REST API](/en/enterprise-cloud@latest/admin/identity-and-access-management/provisioning-user-accounts-for-enterprise-managed-users/provisioning-users-and-groups-with-scim-using-the-rest-api).

> \[!NOTE]
> Use of the REST API for SCIM provisioning is not supported with enterprises enabled for OIDC.

GitHub does not expressly support mixing partner IdPs for authentication and provisioning and does not test all identity management systems. **GitHub's support team may not be able to assist you with issues related to mixed or untested systems.** If you need help, you must consult the system's documentation, support team, or other resources.

> \[!IMPORTANT] The combination of **Okta and Entra ID** for SSO and SCIM (in either order) is explicitly **not supported**. GitHub's SCIM API will return an error to the identity provider on provisioning attempts if this combination is configured.

1. Sign in as the setup user for your enterprise with the username **SHORTCODE\_admin**, replacing SHORTCODE with your enterprise's shortcode.

   > \[!NOTE]
   > If you need to reset the password for your setup user, contact GitHub Support through the [GitHub Support portal](https://support.github.com). The usual password reset option by providing your email address will not work.

2. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

3. At the top of the page, click **Identity provider**.

4. Under **Identity Provider**, click **Single sign-on configuration**.

5. Under "Open SCIM Configuration", select "Enable open SCIM configuration".

6. Manage the lifecycle of your users by making calls to the REST API endpoints for SCIM provisioning. See [Provisioning users and groups with SCIM using the REST API](/en/enterprise-cloud@latest/admin/identity-and-access-management/provisioning-user-accounts-for-enterprise-managed-users/provisioning-users-and-groups-with-scim-using-the-rest-api).

## Assigning users and groups

After you have configured authentication and provisioning, you will be able to provision new users on GitHub by assigning users or groups to the GitHub Enterprise Managed User application.

When assigning users, you can use the "Roles" attribute in the application on your IdP to set a user's role in your enterprise. For more information about the roles available to assign, see [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise).

Entra ID does not support provisioning nested groups. For more information, see [How Application Provisioning works in Microsoft Entra ID](https://learn.microsoft.com/entra/identity/app-provisioning/how-provisioning-works#assignment-based-scoping) on Microsoft Learn.