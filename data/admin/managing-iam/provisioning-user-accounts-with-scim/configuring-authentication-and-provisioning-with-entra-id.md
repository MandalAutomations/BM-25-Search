# Configuring authentication and provisioning with Entra ID

You can use a tenant in Microsoft Entra ID (previously known as Azure AD) as an identity provider (IdP) to centrally manage authentication and user provisioning for GitHub.com.

## About authentication and user provisioning with Entra ID

Entra ID is a service from Microsoft that allows you to centrally manage user accounts and access to web applications. For more information, see [What is Microsoft Entra ID?](https://learn.microsoft.com/entra/fundamentals/whatis) in the Microsoft Docs.

When you use an IdP for IAM on GitHub Enterprise Server, SAML SSO controls and secures access to enterprise resources like repositories, issues, and pull requests. SCIM automatically creates user accounts and manages access to your enterprise when you make changes on your IdP. You can also synchronize teams on GitHub with groups on your IdP.

For more information, see [About user provisioning with SCIM on GitHub Enterprise Server](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/user-provisioning-with-scim-on-ghes).

## Prerequisites

The general prerequisites for using SCIM on GitHub Enterprise Server apply. See the "Prerequisites" section in [Configuring SCIM provisioning to manage users](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users#prerequisites).

In addition:

* To configure SCIM, you must have completed **steps 1 to 4** in [Configuring SCIM provisioning to manage users](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users).
  * You will need the personal access token (classic) created for the setup user to authenticate requests from Entra ID.

* To configure authentication and user provisioning using Entra ID, you must have an Entra ID account and tenant. For more information, see the [Entra ID website](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id) and [Quickstart: Set up a tenant](https://learn.microsoft.com/entra/identity-platform/quickstart-create-new-tenant) in the Microsoft Docs.

## 1. Configure SAML

> \[!NOTE] Even if you have previously configured SAML on Entra ID, you will need to configure SAML and SCIM on a **new application** to enable SCIM provisioning.

Before starting this section, ensure you have followed steps **1 and 2** in [Configuring SCIM provisioning to manage users](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users).

### In Entra ID

1. Create the "GitHub Enterprise Server" application in Entra ID. For instructions, see the "Adding GitHub Enterprise Server from the gallery" section in Microsoft's guide [Tutorial: Microsoft Entra SSO integration with GitHub Enterprise Server](https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-ae-tutorial#adding-github-enterprise-server-from-the-gallery).

   > \[!NOTE] Do **not** use the application labeled "(Legacy)."

2. In the "GitHub Enterprise Server" application settings, click **Single sign-on** in the left sidebar, then click **SAML**.

3. In the "Basic SAML Configuration" section, click **Edit**, then add the following details.

   * "Identifier": your GitHub Enterprise Server host URL (`https://HOSTNAME.com`)
   * "Reply URL": your host URL, followed by `/saml/consume` (`https://HOSTNAME.com/saml/consume`)

4. In the "SAML certificates" section, download the SAML certificate (Base64).

5. In the "Set up GitHub Enterprise Server" section, make a note of the Login URL and Microsoft Entra Identifier.

### On GitHub Enterprise Server

1. Sign in to GitHub Enterprise Server as a user with access to the Management Console.
2. Configure SAML using the information you have gathered. See [Configuring SAML single sign-on for your enterprise](/en/enterprise-server@3.20/admin/managing-iam/using-saml-for-enterprise-iam/configuring-saml-single-sign-on-for-your-enterprise#configuring-saml-sso).

## 2. Configure SCIM

Before starting this section, ensure you have followed steps **1 to 4** in [Configuring SCIM provisioning to manage users](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users).

1. In the "GitHub Enterprise Server" application in Entra ID, click **Provisioning** in the left sidebar, then click **Get started**.
2. Select the "Automatic" provisioning mode.
3. In the "Admin Credentials" section, add the following details.

   * "Tenant URL": your GitHub Enterprise Server host URL, followed by `/api/v3/scim/v2` (`https://HOSTNAME.com/api/v3/scim/v2`)
   * "Secret Token": the personal access token (classic) created for the setup user
4. Click **Test Connection**.
5. When the test is complete, click **Save**.
6. Navigate back to the "Overview" page.
7. To provision your EntraID users to your GitHub Enterprise Server appliance, Click **Start provisioning**.

When you have finished configuring SCIM, you may want to disable some SAML settings you enabled for the configuration process. See [Configuring SCIM provisioning to manage users](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users#6-disable-optional-settings).