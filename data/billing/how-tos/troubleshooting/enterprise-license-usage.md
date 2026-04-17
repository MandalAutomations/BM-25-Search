# Troubleshooting license usage for GitHub Enterprise

You can troubleshoot license usage for your enterprise by auditing license reports.

## About unexpected license usage

If the number of consumed licenses for your enterprise is unexpected, you can review your consumed license report to audit your license usage across all your enterprise deployments and subscriptions. For more information, see [Viewing usage for your GitHub Enterprise plan](/en/billing/managing-your-license-for-github-enterprise/viewing-license-usage-for-github-enterprise) and [License troubleshooting information for GitHub Enterprise](/en/billing/reference/license-usage-calculation).

> \[!NOTE] For privacy reasons, enterprise owners cannot directly access the details of user accounts unless you use Enterprise Managed Users.

If you find errors, you can try the troubleshooting steps below.

## Troubleshooting consumed licenses

To ensure that each user is only consuming a single seat for different deployments and subscriptions, try the following troubleshooting steps.

1. To help identify users that are consuming multiple seats, if your enterprise uses verified domains for GitHub Enterprise Cloud, review the list of enterprise members who do not have an email address from a verified domain associated with their account on GitHub Enterprise Cloud.

   Often, these are the users who erroneously consume more than one licensed seat. For more information, see [Viewing people in your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/viewing-people-in-your-enterprise#viewing-members-without-an-email-address-from-a-verified-domain).

   > \[!NOTE]
   > To make troubleshooting easier, we recommend using verified domains with your enterprise account on GitHub Enterprise Cloud. For more information, see [Verifying or approving a domain for your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-your-enterprise/verifying-or-approving-a-domain-for-your-enterprise).

2. After you identify users who are consuming multiple seats, make sure that the same email address is associated with all of the user's accounts. For more information about which email addresses must match, see [License troubleshooting information for GitHub Enterprise](/en/billing/reference/license-usage-calculation).

3. If an email address was recently updated or verified to correct a mismatch, view the timestamp of the last license sync job. If a job hasn't run since the correction was made, manually trigger a new job. For more information, see [Syncing license usage from GitHub Enterprise Server to Cloud](/en/billing/managing-your-license-for-github-enterprise/syncing-license-usage-between-github-enterprise-server-and-github-enterprise-cloud).

If you still have questions about your consumed licenses after reviewing the troubleshooting information above, you can contact GitHub Support through the [GitHub Support portal](https://support.github.com).