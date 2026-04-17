# Getting started with data residency for GitHub Enterprise Cloud

Set up your enterprise on GHE.com by onboarding users, enabling billing, and migrating data.

When you adopt GitHub Enterprise Cloud with data residency, you can choose where your company's code and data are stored.

In this guide, you will:

* Start a trial to create an enterprise account with data residency and a dedicated domain on GHE.com
* Add users by configuring authentication and provisioning with an identity management system
* Learn about available features, including features that work differently or require additional configuration compared to GitHub.com
* Set up billing for your enterprise
* Optionally, migrate data from another platform

After this initial setup, you'll be able to create organizations and repositories, collaborate on code, configure policies, and more.

## Prerequisites

* If you intend to pay with a Microsoft Azure subscription, you must have admin access to the Azure portal or work with someone to configure an admin consent workflow. For a full list of prerequisites, see [Connecting an Azure subscription](/en/enterprise-cloud@latest/billing/managing-the-plan-for-your-github-account/connecting-an-azure-subscription#prerequisites).

* You must ensure that client systems trust GitHub's SSH key fingerprints and can access certain hostnames and IP addresses. See [Network details for GHE.com](/en/enterprise-cloud@latest/admin/data-residency/network-details-for-ghecom).

## 1. Sign up for a trial

To get started with data residency, you will sign up for a trial. The trial:

* Lasts for **30 days**
* Includes access to most GitHub Enterprise features, though not the features listed in [Features not included in the trial](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud#features-not-included-in-the-trial)
* Allows you to create up to **three new organizations**

<a href="https://github.com/account/enterprises/new?ref_product=ghec&ref_type=trial&ref_style=button&ref_plan=enterprise" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Set up a trial of GitHub Enterprise Cloud</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

1. Visit the trial page by clicking the link above.

2. Select **Get started with managed users**.

3. Under "Data hosting", use the dropdown menu to select your region for data residency.

4. Complete the signup form. Pay close attention to the following fields:
   * **Subdomain**: This will appear in your enterprise's dedicated domain. For example: `octocorp.ghe.com`.
     > \[!NOTE]
     > Please select the subdomain carefully. You cannot change it later.
   * **Identity Provider**: GitHub partners with certain identity providers to provide a "paved-path" experience. Check whether your identity provider is a partner and ensure you understand the requirements for other systems. See [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/about-enterprise-managed-users#identity-management-systems).
   * **Admin work email**: This is where you will receive the invitation to sign in and configure the enterprise for the first time.

5. Click **Create enterprise**.

Your enterprise can take a few hours to be provisioned. When it's ready, you'll receive a welcome email and an invitation to reset your password, delivered to the "Admin work email" address.

## 2. Add users to your enterprise

Enterprises on GHE.com use Enterprise Managed Users. To create user accounts and grant access to your new enterprise on GHE.com, you must configure authentication and SCIM provisioning. See [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

### Sign in as the setup user

After we create your enterprise, you will receive an email inviting you to choose a password for the setup user, which is used to configure authentication and provisioning. The username is a randomly generated shortcode, suffixed with `_admin`.

Using an **incognito or private browsing window**:

1. Set the user's password.
2. Enable two-factor authentication (2FA), and save the user's recovery codes. See [Configuring two-factor authentication](/en/enterprise-cloud@latest/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication).

   > \[!NOTE]
   > If 2FA isn't enabled, you will need to enter your enterprise's single sign-on (SSO) recovery code each time you sign in as the setup user. You can download these codes once SSO is enabled.
3. We strongly recommend **storing the credentials for the setup user** in your company's password management tool. Someone will need to sign in as this user to update authentication settings, migrate to another identity provider or authentication method, or use your enterprise's recovery codes.

For more information about the setup user, see [Setup user](/en/enterprise-cloud@latest/admin/concepts/identity-and-access-management/setup-user).

### Create a personal access token

Next, create a personal access token that you can use to configure provisioning.

* You must be **signed in as the setup user** when you create the token.
* The token must have at least the **scim:enterprise** scope.
* The token must have **no expiration**.

To learn how to create a personal access token (classic), see [Managing your personal access tokens](/en/enterprise-cloud@latest/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

### Configure authentication

Next, configure how your members will authenticate.

**If you're using Entra ID** as your IdP, you can choose between OpenID Connect (OIDC) and Security Assertion Markup Language (SAML).

* We recommend OIDC, which includes support for Conditional Access Policies (CAP).
* If you require multiple enterprises provisioned from one tenant, you can use SAML or OIDC for the first enterprise, but must use SAML for each additional enterprise.

**If you're using another IdP**, like Okta or PingFederate, you must use SAML to authenticate your members.

To get started, read the guide for your chosen authentication method.

* [Configuring OIDC for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-oidc-for-enterprise-managed-users)
* [Configuring SAML single sign-on for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-iam-with-enterprise-managed-users/configuring-saml-single-sign-on-for-enterprise-managed-users)

### Configure provisioning

After you configure authentication, you can configure SCIM provisioning, which is how your IdP will create managed user accounts on GitHub. See [Configuring SCIM provisioning for Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/configuring-scim-provisioning-for-enterprise-managed-users).

### Manage organization membership

After authentication and provisioning are configured, you can start managing organization membership and license assignment for your managed user accounts by synchronizing IdP groups with teams. See [Managing team memberships with identity provider groups](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/managing-team-memberships-with-identity-provider-groups).

## 3. Learn about GitHub's features

When you have completed the initial setup of your enterprise, you and your enterprise's members can start using GitHub's features.

The features available with data residency on GHE.com are similar to the features available to managed user accounts on GitHub.com, with some additions and exceptions. Some features work differently or require additional configuration compared to the equivalent feature on GitHub.com. See [Feature overview for GitHub Enterprise Cloud with data residency](/en/enterprise-cloud@latest/admin/data-residency/feature-overview-for-github-enterprise-cloud-with-data-residency).

## 4. Purchase GitHub Enterprise

You can purchase GitHub Enterprise at any time during the trial. To do so, click the **Activate enterprise** button displayed on your enterprise account.

To pay for licenses and services, you can use a credit card, PayPal, or a Microsoft Azure subscription.

* To add a credit card or PayPal details, see [Managing your payment and billing information](/en/enterprise-cloud@latest/billing/managing-your-billing/managing-your-payment-and-billing-information#viewing-payment-information).
* To link an Azure subscription, see [Connecting an Azure subscription](/en/enterprise-cloud@latest/billing/managing-the-plan-for-your-github-account/connecting-an-azure-subscription#connecting-your-azure-subscription-to-your-enterprise-account).

## 5. Migrate data

To migrate existing data to your new enterprise on GHE.com, you can use GitHub's migration tools.

Optionally, you can migrate data to GHE.com during your trial. However, migrated organizations will count towards the limit of three new organizations during the trial.

* If you're migrating from GitHub.com, GitHub Enterprise Server, Azure DevOps, or Bitbucket Server, you can migrate source code history and metadata with GitHub Enterprise Importer. See [About GitHub Enterprise Importer](/en/enterprise-cloud@latest/migrations/using-github-enterprise-importer/understanding-github-enterprise-importer/about-github-enterprise-importer).
* If you're migrating from a different platform, see [Migration paths to GitHub](/en/enterprise-cloud@latest/migrations/overview/migration-paths-to-github#migrations-to-ghecom).

### Example script for GitHub Enterprise Importer

The following script demonstrates the use of GitHub Enterprise Importer for migration of an individual source repository from GitHub.com to a target repository on GHE.com. The `--target-api-url` parameter sets your enterprise on GHE.com as the destination of the migration.

You can use the environment variable definitions in the script as an example to create additional commands that migrate data using GitHub Enterprise Importer.

In the following script, **replace the following placeholder text** with actual values.

| Placeholder                  | Description                                                                                                                                                            |
| :--------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TARGET-TOKEN                 | Personal access token (PAT) for accessing the target enterprise on GHE.com                                                                                             |
| SOURCE-TOKEN                 | PAT for accessing the source resources on GitHub.com                                                                                                                   |
| TARGET-GHE-API-URL           | The URL for accessing API endpoints for your enterprise. For example, if your enterprise's subdomain is `octocorp`, this value must be `https://api.octocorp.ghe.com`. |
| SOURCE-GH-ORGANIZATION-NAME  | The name of the source organization on GitHub.com.                                                                                                                     |
| SOURCE-GH-REPOSITORY-NAME    | The name of the source repository on GitHub.com.                                                                                                                       |
| TARGET-GHE-ORGANIZATION-NAME | The name of the target organization on GHE.com.                                                                                                                        |
| TARGET-GHE-REPOSITORY-NAME   | The name of the target repository on GHE.com.                                                                                                                          |

```bash copy
#!/bin/sh

export GH_PAT="TARGET-TOKEN"
export GH_SOURCE_PAT="SOURCE-TOKEN"
export TARGET_API_URL="TARGET-GHE-API-URL"
export GITHUB_SOURCE_ORG="SOURCE-GH-ORGANIZATION-NAME"
export SOURCE_REPO="SOURCE-GH-REPOSITORY-NAME"
export GITHUB_TARGET_ORG="TARGET-GHE-ORGANIZATION-NAME"
export TARGET_REPO="TARGET-GHE-REPOSITORY-NAME"

gh gei migrate-repo --target-api-url $TARGET_API_URL --github-source-org $GITHUB_SOURCE_ORG --source-repo $SOURCE_REPO --github-target-org $GITHUB_TARGET_ORG --target-repo $TARGET_REPO --verbose
```

## Further reading

* [Resolving issues with your enterprise on GHE.com](/en/enterprise-cloud@latest/admin/data-residency/resolving-issues-with-your-enterprise-on-ghecom)