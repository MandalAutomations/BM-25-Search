# Configuring SCIM provisioning with Okta

Learn how to configure Okta to communicate with your enterprise.

## About provisioning with Okta

If you use Okta as an IdP, you can use Okta's application to provision user accounts, manage enterprise membership, and manage team memberships for organizations in your enterprise. Okta is a partner IdP, so you can simplify your authentication and provisioning configuration by using the Okta application for Enterprise Managed Users. For more information, see [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/understanding-iam-for-enterprises/about-enterprise-managed-users#about-authentication-and-user-provisioning).

Alternatively, if you only intend to use Okta for SAML authentication and you want to use a different IdP for provisioning, you can integrate with GitHub's REST API for SCIM. For more information, see [Provisioning users and groups with SCIM using the REST API](/en/enterprise-cloud@latest/admin/identity-and-access-management/provisioning-user-accounts-for-enterprise-managed-users/provisioning-users-with-scim-using-the-rest-api).

## Supported features

Enterprise Managed Users supports the following provisioning features for Okta.

| Feature                | Description                                                                                                                                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Push New Users         | Users that are assigned to the GitHub Enterprise Managed User application in Okta are automatically created in the enterprise on GitHub.                                                          |
| Push Profile Update    | Updates made to the user's profile in Okta will be pushed to GitHub.                                                                                                                              |
| Push Groups            | Groups in Okta that are assigned to the GitHub Enterprise Managed User application as Push Groups are automatically created in the enterprise on GitHub.                                          |
| Push User Deactivation | Unassigning the user from the GitHub Enterprise Managed User application in Okta will disable the user on GitHub. The user will not be able to sign in, but the user's information is maintained. |
| Reactivate Users       | Users in Okta whose Okta accounts are reactivated and who are assigned back to the GitHub Enterprise Managed User application on Okta will be enabled.                                            |

> \[!NOTE]
> Enterprise Managed Users does not support modifications to usernames.

## Prerequisites

If you're configuring SCIM provisioning for a new enterprise, make sure to complete all previous steps in the initial configuration process. See [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

In addition:

* You must use Okta's application for both authentication and provisioning.
* Your Okta product must support System for Cross-domain Identity Management (SCIM). For more information, review Okta's documentation or contact Okta's support team.

## Configuring SCIM

After you have configured your SAML settings in Okta's app, you can proceed to configure provisioning settings. If you haven't already configured SAML settings, see [Configuring SAML single sign-on with Okta for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/configuring-authentication-for-enterprise-managed-users/configuring-saml-single-sign-on-with-okta-for-enterprise-managed-users).

To configure provisioning, the setup user with the **@<em>SHORT-CODE</em>\_admin** username will need to provide a personal access token (classic) with the **scim:enterprise** scope. See [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users#create-a-personal-access-token).

1. Navigate to your GitHub Enterprise Managed User application on Okta.

2. Click the **Provisioning** tab.

3. In the settings menu, click **Integration**.

4. To make changes, click **Edit**.

5. Click **Configure API integration**.

6. In the "API Token" field, enter the personal access token (classic) belonging to the setup user.

   > \[!NOTE] "Import Groups" is **not** supported by GitHub. Selecting or deselecting the checkbox has no impact on your configuration.

   > \[!IMPORTANT]
   > For an enterprise on GitHub Enterprise Cloud with data residency (GHE.com), please enter the following URL in the **Base URL** field: `https://api.{subdomain}.ghe.com/scim/v2/enterprises/{subdomain}` (ensuring to replace `{subdomain}` with your enterprise's subdomain).
   >
   > **For example**: if your enterprise's subdomain is `acme`, the base URL would be `https://api.acme.ghe.com/scim/v2/enterprises/acme`.

7. Click **Test API Credentials**. If the test is successful, a verification message will appear at the top of the screen.

8. To save the token, click **Save**.

9. In the settings menu, click **To App**.

10. To the right of "Provisioning to App", to allow changes to be made, click **Edit**.

11. Select **Enable** to the right of **Create Users**, **Update User Attributes**, and **Deactivate Users**.

12. To finish configuring provisioning, click **Save**.

## How do I assign users and groups?

After you have configured authentication and provisioning, you will be able to provision new users on GitHub by assigning users or groups to the GitHub Enterprise Managed User application.

> \[!NOTE]
>
> To avoid exceeding GitHub's rate limit, do not assign more than 1,000 users per hour to the SCIM integration on your IdP. If you use groups to assign users to the IdP application, do not add more than 1,000 users to each group per hour. If you exceed these thresholds, attempts to provision users may fail with a "rate limit" error. You can review your IdP logs to confirm if attempted SCIM provisioning or push operations failed due to a rate limit error. The response to a failed provisioning attempt will depend on the IdP.
> For more information, see [Troubleshooting identity and access management for your enterprise](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-iam-for-your-enterprise/troubleshooting-identity-and-access-management-for-your-enterprise#scim-provisioning-errors).

You can also automatically manage organization membership by adding groups to the "Push Groups" tab in Okta. When the group is provisioned successfully, it will be available to connect to teams in the enterprise's organizations. For more information about managing teams, see [Managing team memberships with identity provider groups](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/managing-team-memberships-with-identity-provider-groups).

When assigning users, you can use the "Roles" attribute in the application on your IdP to set a user's role in your enterprise. For more information about the roles available to assign, see [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise).

> \[!NOTE]
> You can only set the "Roles" attribute for an individual user, not a group. If you want to set roles for everyone in a group that is assigned to the application in Okta, you must use the "Roles" attribute for each group member, individually.

## How do I deprovision users and groups?

To remove a user or group from GitHub, remove the user or group from both the "Assignments" tab and the "Push groups" tab in Okta. For users, make sure the user is removed from all groups in the "Push Groups" tab.