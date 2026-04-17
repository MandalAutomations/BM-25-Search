# License troubleshooting information for GitHub Enterprise

Troubleshoot license usage for your enterprise by understanding consumption criteria and auditing license reports.

## People who consume a license

A person consumes a license for GitHub Enterprise depending on specific criteria. If a user has not yet accepted an invitation to join your enterprise, the user still consumes a license. For more information about the people in your enterprise who consume a license, see [People who consume a license in an organization](/en/enterprise-cloud@latest/billing/managing-the-plan-for-your-github-account/about-per-user-pricing).

## Visual Studio subscribers

If the verified email address for the personal account of an enterprise member on GitHub matches the User Principal Name (UPN) for a subscriber to your Visual Studio account, the Visual Studio subscriber will automatically consume one license for Visual Studio subscriptions with GitHub Enterprise Cloud.

> \[!NOTE] For Enterprise Managed User only, to make sure a user account consumes a Visual Studio license, ensure the Visual Studio UPN matches the SCIM `userName` attribute or the email address from the linked identity on the GitHub account.

For more information, see [About Visual Studio subscriptions with GitHub Enterprise](/en/enterprise-cloud@latest/billing/managing-billing-for-your-products/managing-licenses-for-visual-studio-subscriptions-with-github-enterprise/about-visual-studio-subscriptions-with-github-enterprise).

## Users of GitHub Enterprise Cloud and GitHub Enterprise Server

For each user to consume a single license regardless of how many deployments they use, you must synchronize license usage between GitHub Enterprise Server and GitHub Enterprise Cloud. For more information, see [Syncing license usage from GitHub Enterprise Server to Cloud](/en/enterprise-cloud@latest/billing/managing-your-license-for-github-enterprise/syncing-license-usage-between-github-enterprise-server-and-github-enterprise-cloud).

After you synchronize license usage, GitHub matches user accounts on GitHub Enterprise Server with user accounts on GitHub Enterprise Cloud by email address.

1. We check the primary email address of each user on GitHub Enterprise Server.
2. We attempt to match that address with the email address for a user account on GitHub Enterprise Cloud.

### With SAML or SCIM

If your enterprise on GitHub Enterprise Cloud or any of the enterprise's organizations use SAML authentication or SCIM provisioning, we first check the linked SAML or SCIM identities to see if the identity contains one of the attributes below. We attempt to match the values of these attributes to the primary email address of each GitHub Enterprise Server user.

* `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`
* `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress`
* `username`
* `NameID`
* `emails`

### Without SAML or SCIM

If there is no match with a SAML or SCIM attribute, or if SAML authentication or SCIM provisioning is not in use, we attempt to match the primary email address on GitHub Enterprise Server with a verified email address for a user account on GitHub Enterprise Cloud. For more information about verification of email addresses on GitHub Enterprise Cloud, see [Verifying your email address](/en/enterprise-cloud@latest/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/verifying-your-email-address).

## Fields in the consumed license files

The GitHub Enterprise Cloud license usage report and GitHub Enterprise Server exported license usage file include a variety of fields to help you troubleshoot license usage for your enterprise.

For details of each field, see [License reports reference](/en/enterprise-cloud@latest/billing/reference/license-reports#github-enterprise-cloud-license-report).

## Troubleshooting steps

For troubleshooting steps, see [Troubleshooting license usage for GitHub Enterprise](/en/enterprise-cloud@latest/billing/how-tos/troubleshooting/enterprise-license-usage).