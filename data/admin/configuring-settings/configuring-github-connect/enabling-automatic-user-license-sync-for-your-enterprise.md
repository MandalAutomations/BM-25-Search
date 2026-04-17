# Enabling automatic user license sync for your enterprise

You can manage license usage across your GitHub Enterprise environments by automatically syncing user licenses from GitHub.com to GitHub Enterprise Cloud.

## About automatic license synchronization

GitHub uses a unique-user licensing model. With the GitHub Enterprise plan, you're entitled to use both GitHub Enterprise Cloud and GitHub Enterprise Server. Your GitHub Enterprise Cloud allowance includes **one** deployment, on either GitHub.com or GHE.com.

GitHub determines how many licenses you're consuming based on the number of unique users across your deployments. Each user only consumes one license, no matter how many GitHub Enterprise Server instances the user uses, or how many organizations the user is a member of on your GitHub Enterprise Cloud deployment. This model allows each person to use multiple GitHub Enterprise deployments without incurring extra costs.

For a person using multiple GitHub Enterprise environments to only consume a single license, you must synchronize license usage between environments. Then, GitHub will deduplicate users based on the email addresses associated with their user accounts. GitHub deduplicates licenses for the GitHub Enterprise plan itself, and for GitHub Advanced Security products. See [Syncing license usage from GitHub Enterprise Server to Cloud](/en/enterprise-server@3.20/billing/how-tos/manage-server-licenses/sync-license-usage). For more information, see [About GitHub Connect](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/about-github-connect#data-transmission).

If you enable automatic user license sync for your enterprise, every week, GitHub Connect will automatically synchronize license usage between GitHub Enterprise Server and your enterprise on GitHub.com or GHE.com. You can also synchronize your license data at any time outside of the automatic weekly sync, by manually triggering a license sync job. For more information, see [Syncing license usage from GitHub Enterprise Server to Cloud](/en/enterprise-server@3.20/billing/managing-your-license-for-github-enterprise/syncing-license-usage-between-github-enterprise-server-and-github-enterprise-cloud#triggering-a-license-sync-job).

If you use multiple GitHub Enterprise Server instances, you can enable automatic license sync between each of your instances and the same enterprise account on GitHub Enterprise Cloud.

After you synchronize license usage, you can see a report of consumed licenses across all your environments in the enterprise settings on GitHub Enterprise Cloud. For more information, see [Viewing usage for your GitHub Enterprise plan](/en/enterprise-cloud@latest/billing/managing-your-license-for-github-enterprise/viewing-license-usage-for-github-enterprise).

You can also manually upload GitHub Enterprise Server user license information to GitHub Enterprise Cloud. For more information, see [Syncing license usage from GitHub Enterprise Server to Cloud](/en/enterprise-server@3.20/billing/managing-your-license-for-github-enterprise/syncing-license-usage-between-github-enterprise-server-and-github-enterprise-cloud).

> \[!NOTE] To make troubleshooting easier, if you synchronize license usage and do not use Enterprise Managed Users, we highly recommend enabling verified domains for your enterprise account on GitHub Enterprise Cloud. See [Verifying or approving a domain for your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-your-enterprise/verifying-or-approving-a-domain-for-your-enterprise) in the GitHub Enterprise Cloud documentation.

## Enabling license synchronization

Before enabling license synchronization on your GitHub Enterprise Server instance, you must enable GitHub Connect. See [Enabling GitHub Connect for GHE.com](/en/enterprise-server@3.20/admin/configuring-settings/configuring-github-connect/enabling-github-connect-for-ghecom) or [Enabling GitHub Connect for GitHub.com](/en/enterprise-server@3.20/admin/configuring-settings/configuring-github-connect/enabling-github-connect-for-githubcom).

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plug" aria-label="plug" role="img"><path d="M4 8H2.5a1 1 0 0 0-1 1v5.25a.75.75 0 0 1-1.5 0V9a2.5 2.5 0 0 1 2.5-2.5H4V5.133a1.75 1.75 0 0 1 1.533-1.737l2.831-.353.76-.913c.332-.4.825-.63 1.344-.63h.782c.966 0 1.75.784 1.75 1.75V4h2.25a.75.75 0 0 1 0 1.5H13v4h2.25a.75.75 0 0 1 0 1.5H13v.75a1.75 1.75 0 0 1-1.75 1.75h-.782c-.519 0-1.012-.23-1.344-.63l-.761-.912-2.83-.354A1.75 1.75 0 0 1 4 9.867Zm6.276-4.91-.95 1.14a.753.753 0 0 1-.483.265l-3.124.39a.25.25 0 0 0-.219.248v4.734c0 .126.094.233.219.249l3.124.39a.752.752 0 0 1 .483.264l.95 1.14a.25.25 0 0 0 .192.09h.782a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25h-.782a.25.25 0 0 0-.192.09Z"></path></svg> GitHub Connect**.
3. To the right of "License sync", click **Enable**.

   ![Screenshot of the "License sync" option on the GitHub Connect page. The "Enable" button is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/enable-user-license-drop-down.png)

> \[!NOTE]
> If SAML with SCIM is enabled, the `scim-admin` setup user will not consume a license. For more information, see [Configuring SCIM provisioning to manage users](/en/enterprise-server@3.20/admin/managing-iam/provisioning-user-accounts-with-scim/configuring-scim-provisioning-for-users#1-create-a-built-in-setup-user).