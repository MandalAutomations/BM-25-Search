# Migrating from LDAP to SAML with SCIM

Learn how to migrate your GitHub Enterprise Server instance from LDAP authentication to SAML single sign-on with SCIM provisioning for centralized user management.

## About migrating from LDAP to SAML and SCIM

If your GitHub Enterprise Server instance currently uses LDAP authentication, you can migrate to SAML single sign-on (SSO) with SCIM provisioning for enhanced user lifecycle management capabilities. This migration allows you to automatically provision, update, and deprovision user accounts from your identity provider (IdP).

> \[!NOTE]
> You can use either SAML or LDAP, but not both.

**Prerequisites:**

* You must be a site administrator on GitHub Enterprise Server.
* You must have administrative access to your SAML identity provider.
* Your IdP must support SAML 2.0 and SCIM 2.0 protocols.
* You should complete a backup of your instance before beginning the migration.

SCIM provisioning requires SAML authentication as a prerequisite, so this migration involves four distinct phases:

1. **Migrate to SAML authentication**: Replace LDAP with SAML SSO.
2. **Test and verify SAML**: Confirm authentication works and users link correctly.
3. **Enable SCIM provisioning**: Add automated user management capabilities.
4. **Test and verify SCIM**: Confirm provisioning links identities to existing accounts.

This document assumes familiarity with SAML authentication and SCIM provisioning. For more information on these topics, please see [Configuring SAML single sign-on for your enterprise](/en/enterprise-server@3.20/admin/managing-iam/using-saml-for-enterprise-iam/configuring-saml-single-sign-on-for-your-enterprise) and [About user provisioning with SCIM on GitHub Enterprise Server](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/user-provisioning-with-scim-on-ghes).

## 1. Understand LDAP vs SCIM user creation patterns

Before you begin the migration, it's important to understand the key differences between how LDAP and SCIM handle user management on GitHub Enterprise Server.

| Attribute                   | LDAP                                                                                                                                                                                                                                                                                                                                                        | SCIM                                                                                                                                                              |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Appliance configuration** | You configure the user ID attribute (default `uid`) and other LDAP settings in the management console. This configuration determines how to map between LDAP users and GitHub users. For more information about configuring LDAP, see [Using LDAP](/en/enterprise-server@3.20/admin/managing-iam/using-ldap-for-enterprise-iam/using-ldap#ldap-attributes). | Enable SAML authentication first, then configure SCIM provisioning with an authentication token.                                                                  |
| **User creation timing**    | Just-in-time: Users are created on first sign-in after successful LDAP authentication.                                                                                                                                                                                                                                                                      | Pre-authentication: Users must be provisioned via SCIM before they can authenticate.                                                                              |
| **Initial username source** | GitHub username is based on the normalized LDAP identifier configured during setup.                                                                                                                                                                                                                                                                         | GitHub username is based on the normalized SCIM `userName` value from your IdP.                                                                                   |
| **Username management**     | Flexible: Administrators can change GitHub usernames independently of LDAP. Usernames can drift from LDAP identifiers over time while maintaining authentication through LDAP mappings. See [Username reference](/en/enterprise-server@3.20/account-and-profile/reference/username-reference#changing-your-username).                                       | Strict: GitHub usernames always correspond to the normalized SCIM `userName` from your IdP. Username changes on the GitHub side are not allowed.                  |
| **User attribute control**  | Hybrid: Some attributes managed by LDAP, others can be managed on the appliance.                                                                                                                                                                                                                                                                            | Full IdP control: All user attributes are managed through SCIM updates from your IdP.                                                                             |
| **Authentication flow**     | GitHub Enterprise Server authenticates with your LDAP server and looks up the existing LDAP mapping to locate  the user.                                                                                                                                                                                                                                    | During SAML SSO, an external identity lookup is performed to locate the provisioned user for authentication.                                                      |
| **Key characteristic**      | Hybrid system where GitHub user data (especially usernames) can be partially managed on the appliance independently of the LDAP server.                                                                                                                                                                                                                     | Full identity provider control: The state of GitHub users depends entirely on what the IdP sends through SCIM, and usernames cannot drift from the source system. |

### Username normalization and compatibility

GitHub Enterprise Server normalizes usernames according to specific rules that apply consistently across LDAP, SAML, and SCIM. Understanding these rules is critical for successful migration.

For more information about username normalization, see [Username considerations for external authentication](/en/enterprise-server@3.20/admin/managing-iam/iam-configuration-reference/username-considerations-for-external-authentication#about-username-normalization).

## 2. Plan your migration

Before beginning the migration, you need to understand your current setup, prepare your identity provider, and establish backup access methods. The planning phase is critical to ensure a smooth transition.

### Preparing to map from LDAP to SCIM

The critical migration challenge is bridging between the LDAP and SCIM user management approaches:

**LDAP users (existing state)**:

* Have GitHub usernames that may have changed since initial creation
* Retain authentication ability through LDAP mappings regardless of username changes

**SCIM users (target state)**:

* Must be provisioned before authentication
* Must have GitHub usernames that match their normalized SCIM `userName` values
* Can be linked to an external identity with their existing GitHub account during SCIM user provisioning, but only if the normalized SCIM `userName` matches their existing GitHub username

### Migration mapping requirements

To successfully link SCIM identities to existing LDAP users, you'll need to capture the current state of the users on your instance:

1. **Export existing GitHub usernames**: Use the site admin interface, API, or CLI to get a complete list of current GitHub usernames on your instance. For more information about the users API, see [REST API endpoints for users](/en/enterprise-server@3.20/rest/users/users?apiVersion=2022-11-28#list-users). For more information about the command-line utility to export users, see [Command-line utilities](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/command-line-utilities#ghe-user-csv).
2. **Map GitHub usernames to real users in your IdP**: Determine which identities correspond to each GitHub username in your enterprise.
3. **Configure the SCIM `userName` attribute**: Ensure your IdP provisions SCIM users with `userName` values that match the existing GitHub usernames you would like to link.

**Important**: The target for mapping is always the **current GitHub username** on your instance, not the original LDAP User ID or any other identifier.

### Key planning considerations

**Important considerations:**

* **Downtime required**: This migration requires downtime during a maintenance window to change authentication settings.
* **User impact**: After the migration, users will need to authenticate through your SAML IdP instead of LDAP credentials.
* **Team membership**: LDAP team synchronization will be replaced by SCIM group provisioning if supported by your IdP. LDAP-mapped teams will need to be updated with an appropriate SCIM group where applicable.

### Capture the state of your LDAP configuration

Record your current LDAP setup to plan equivalent SAML/SCIM mappings:

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
4. In the "Settings" sidebar, click **Authentication**.
5. Document the following LDAP settings:
   * **Domain base** and restricted user groups
   * **User ID attribute** (this was used to create GitHub usernames)
   * **Profile name, email, and other attribute mappings**
   * **Administrators group configuration**
   * **Team synchronization settings**
6. Ensure you have saved a list of existing users on your instance that you will be linking to a SCIM identity.

## 3. Migrate to SAML and SCIM

Once you've completed planning, you can begin migrating from LDAP to SAML authentication. This involves configuring SAML on both your identity provider and GitHub Enterprise Server, then carefully testing the configuration before proceeding to SCIM.

**Important**: When configuring SAML, enable "Allow creation of accounts with built-in authentication" to reduce the number of steps required when enabling SCIM.

### Enabling SAML authentication

For detailed SAML configuration steps, see [Configuring SAML single sign-on for your enterprise](/en/enterprise-server@3.20/admin/managing-iam/using-saml-for-enterprise-iam/configuring-saml-single-sign-on-for-your-enterprise).

After enabling SAML, test the authentication system before proceeding to SCIM. With any IdP account assigned to the SAML application configured against your instance, verify that you are able to successfully perform an SSO login.

**Do not proceed to SCIM until SAML authentication is working correctly.**

### Enable SCIM provisioning

After confirming SAML authentication works correctly, you can enable SCIM for automated user management. SCIM must be configured on both GitHub Enterprise Server and your identity provider.

For detailed steps to enable SCIM, see [Configuring SCIM provisioning to manage users](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users).

#### Test SCIM provisioning

Test SCIM provisioning to ensure the SCIM provisioned users are linked to existing user accounts correctly.

For users who already have accounts from the LDAP/SAML migration:

1. **Assign user to SCIM application** in your IdP.
2. **Verify automatic linking**: Check that SCIM automatically links to the existing account:
   * Users retain same username and account data
   * No duplicate accounts are created
   * SCIM identity shows as linked in the enterprise settings, and site admin interfaces. For more information, see [Viewing and managing a user's SAML access to your enterprise](/en/enterprise-server@3.20/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/viewing-and-managing-a-users-saml-access-to-your-enterprise#viewing-a-linked-identity).
3. **Review audit logs**: Look for `external_identity.scim_api_success` and `external_identity.provision` events showing successful linking to existing users.

For new users not previously in your instance:

1. **Verify user creation**: Check that the user appears in GitHub Enterprise Server with correct attributes.
2. **Test authentication**: Confirm the new user can authenticate via SAML.
3. **Test attribute updates**: Update user information in IdP and confirm changes sync.
4. **Test deprovisioning**: Remove user access and confirm they are suspended.

### Roll out SCIM to all users

For all remaining users who aren't yet provisioned via SCIM:

1. **Gradually assign users** to the GitHub Enterprise Server application in your IdP.
2. **Monitor linking process**: Watch for successful automatic linking based on username matching.
3. **Track progress**: Use audit logs to monitor `external_identity` events for linking progress.
4. **Address any conflicts**: Resolve username conflicts or mapping issues as they arise.

## 4. Update team and organization membership

After your migration, if you previously used LDAP group synchronization to control team memberships, you can replace those team mappings with SCIM groups. If reusing existing an team, you will need to remove all team members prior to linking an IdP group.

For more information, see [Managing team memberships with identity provider groups](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/managing-team-memberships-with-identity-provider-groups).