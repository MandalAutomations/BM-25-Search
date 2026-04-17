# Enabling Dependabot for your enterprise

You can allow users to find and fix vulnerabilities in code dependencies by setting up Dependabot alerts and Dependabot updates.

## About Dependabot for GitHub Enterprise Server

Dependabot helps users find and fix vulnerabilities in their dependencies. You must first set up Dependabot for your enterprise, and then you can enable Dependabot alerts to notify users about vulnerable dependencies and Dependabot updates to fix the vulnerabilities and keep dependencies updated to the latest version.

Dependabot is just one of many features available to harden supply chain security for GitHub. For more information about the other features, see [About supply chain security for your enterprise](/en/enterprise-server@3.20/admin/code-security/managing-supply-chain-security-for-your-enterprise/about-supply-chain-security-for-your-enterprise).

### About Dependabot alerts

With Dependabot alerts, GitHub identifies insecure dependencies in repositories and creates alerts on GitHub Enterprise Server, using data from the GitHub Advisory Database and the dependency graph service.

We add advisories to the GitHub Advisory Database from the following sources:

* Security advisories reported on GitHub
* The [National Vulnerability database](https://nvd.nist.gov/)
* The [npm Security advisories database](https://github.com/advisories?query=type%3Areviewed+ecosystem%3Anpm)
* The [FriendsOfPHP database](https://github.com/FriendsOfPHP/security-advisories)
* The [Go Vulncheck database](https://pkg.go.dev/vuln/)
* The [Python Packaging Advisory database](https://github.com/pypa/advisory-database)
* The [Ruby Advisory database](https://rubysec.com/)
* The [RustSec Advisory database](https://rustsec.org/)
* Community contributions. For more information, see <https://github.com/github/advisory-database/pulls>.

If you know of another database we should be importing advisories from, tell us about it by opening an issue in <https://github.com/github/advisory-database>.

After you set up Dependabot for your enterprise, vulnerability data is synced from the GitHub Advisory Database to your instance once every hour. Only GitHub-reviewed advisories are synchronized. For more information, see [Browsing security advisories in the GitHub Advisory Database](/en/enterprise-server@3.20/code-security/security-advisories/working-with-global-security-advisories-from-the-github-advisory-database/browsing-security-advisories-in-the-github-advisory-database).

You can also choose to manually sync vulnerability data at any time. For more information, see [Viewing the vulnerability data for your enterprise](/en/enterprise-server@3.20/admin/code-security/managing-supply-chain-security-for-your-enterprise/viewing-the-vulnerability-data-for-your-enterprise).

> \[!NOTE]
> When you enable Dependabot alerts, no code or information about code from GitHub Enterprise Server is uploaded to GitHub.com or GHE.com.

When GitHub Enterprise Server receives information about a vulnerability, it identifies repositories that use the affected version of the dependency and generates Dependabot alerts. You can choose whether or not to notify users automatically about new Dependabot alerts.

For repositories with Dependabot alerts enabled, scanning is triggered on any push to the default branch that contains a manifest file or lock file. Additionally, when a new vulnerability record is added, GitHub Enterprise Server scans all existing repositories and generates alerts for any repository that is vulnerable. For more information, see [About Dependabot alerts](/en/enterprise-server@3.20/code-security/dependabot/dependabot-alerts/about-dependabot-alerts).

### About Dependabot updates

After you enable Dependabot alerts, you can choose to enable Dependabot updates. When Dependabot updates are enabled for GitHub Enterprise Server, users can configure repositories so that their dependencies are updated and kept secure automatically.

> \[!NOTE]
> Dependabot updates on GitHub Enterprise Server requires GitHub Actions with self-hosted runners.

By default, GitHub Actions runners used by Dependabot need access to the internet, to download updated packages from upstream package managers. For Dependabot updates powered by GitHub Connect, internet access provides your runners with a token that allows access to dependencies and advisories hosted on GitHub.com.

You can enable Dependabot updates for specific private registries on GitHub Enterprise Server instances with limited, or no, internet access. For more information, see [Configuring Dependabot to work with limited internet access](/en/enterprise-server@3.20/admin/code-security/managing-supply-chain-security-for-your-enterprise/configuring-dependabot-to-work-with-limited-internet-access).

With Dependabot updates, GitHub automatically creates pull requests to update dependencies in two ways.

* **Dependabot version updates:** Users add a Dependabot configuration file to the repository to enable Dependabot to create pull requests when a new version of a tracked dependency is released. For more information, see [About Dependabot version updates](/en/enterprise-server@3.20/code-security/dependabot/dependabot-version-updates/about-dependabot-version-updates).
* **Dependabot security updates:** Users toggle a repository setting to enable Dependabot to create pull requests when GitHub detects a vulnerability in one of the dependencies of the dependency graph for the repository. For more information, see [About Dependabot alerts](/en/enterprise-server@3.20/code-security/dependabot/dependabot-alerts/about-dependabot-alerts) and [About Dependabot security updates](/en/enterprise-server@3.20/code-security/dependabot/dependabot-security-updates/about-dependabot-security-updates).

## Enabling Dependabot alerts

Before you can enable Dependabot alerts, you must first set up Dependabot for your enterprise:

* You must enable GitHub Connect. For more information, see [Enabling GitHub Connect for GitHub.com](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/managing-github-connect).
* You must enable the dependency graph. For more information, see [Enabling the dependency graph for your enterprise](/en/enterprise-server@3.20/admin/code-security/managing-supply-chain-security-for-your-enterprise/enabling-the-dependency-graph-for-your-enterprise).

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plug" aria-label="plug" role="img"><path d="M4 8H2.5a1 1 0 0 0-1 1v5.25a.75.75 0 0 1-1.5 0V9a2.5 2.5 0 0 1 2.5-2.5H4V5.133a1.75 1.75 0 0 1 1.533-1.737l2.831-.353.76-.913c.332-.4.825-.63 1.344-.63h.782c.966 0 1.75.784 1.75 1.75V4h2.25a.75.75 0 0 1 0 1.5H13v4h2.25a.75.75 0 0 1 0 1.5H13v.75a1.75 1.75 0 0 1-1.75 1.75h-.782c-.519 0-1.012-.23-1.344-.63l-.761-.912-2.83-.354A1.75 1.75 0 0 1 4 9.867Zm6.276-4.91-.95 1.14a.753.753 0 0 1-.483.265l-3.124.39a.25.25 0 0 0-.219.248v4.734c0 .126.094.233.219.249l3.124.39a.752.752 0 0 1 .483.264l.95 1.14a.25.25 0 0 0 .192.09h.782a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25h-.782a.25.25 0 0 0-.192.09Z"></path></svg> GitHub Connect**.
3. Under "Dependabot", to the right of "Periodically download the GitHub Advisory Database so that users can receive vulnerability alerts for open source code dependencies", select the dropdown menu and click **Enabled without notifications**. Optionally, to enable alerts with notifications, click **Enabled with notifications**.

   ![Screenshot of the "Enable" dropdown menu for Dependabot alerts, showing the available options.](/assets/images/enterprise/site-admin-settings/dependabot-alerts-setup-dropdown.png)

   > \[!NOTE]
   > This setting controls realtime email and web notifications only. Command line interface (CLI) warnings and email digests will still be delivered regardless of which option is selected.

   > \[!TIP]
   > We recommend configuring Dependabot alerts without notifications for the first few days to avoid an overload of realtime notifications. After a few days, you can enable notifications to receive Dependabot alerts as usual.

You can now enable Dependabot alerts for all existing or new private and internal repositories in the enterprise settings page for "Advanced Security." Alternatively, repository administrators and organization owners can enable Dependabot alerts for each repository and organization. Public repositories are always enabled by default. For more information, see [Configuring Dependabot alerts](/en/enterprise-server@3.20/code-security/dependabot/dependabot-alerts/configuring-dependabot-alerts).

## Enabling Dependabot updates

Before you can enable Dependabot updates:

* You must enable Dependabot alerts for your enterprise. For more information, see "Enabling Dependabot alerts" above.
* You must enable TLS. Dependabot updates run on self-hosted runners, which need to have TLS enabled. For more information, see [Getting started with self-hosted runners for your enterprise](/en/enterprise-server@3.20/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/getting-started-with-self-hosted-runners-for-your-enterprise#prerequisites).
* You must configure GitHub Enterprise Server to use GitHub Actions with self-hosted runners. For more information, see [Getting started with GitHub Actions for GitHub Enterprise Server](/en/enterprise-server@3.20/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/getting-started-with-github-actions-for-github-enterprise-server).

Dependabot updates are not supported on GitHub Enterprise Server if your enterprise uses clustering.

> \[!NOTE]
> After you enable the dependency graph, you can use the [Dependabot action](https://github.com/github/dependabot-action). The action will raise an error if any vulnerabilities or invalid licenses are being introduced. For more information about the action, and for instructions about how to download the most recent version, see [Using the latest version of the official bundled actions](/en/enterprise-server@3.20/admin/github-actions/managing-access-to-actions-from-githubcom/using-the-latest-version-of-the-official-bundled-actions).

1. Sign in to your GitHub Enterprise Server instance at `http(s)://HOSTNAME/login`.

2. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

3. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

4. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

5. In the "Settings" sidebar, click **Security**.

6. Under "Security", select **Dependabot updates**.

7. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

8. Wait for the configuration run to complete.

9. Click **Visit your instance**.

10. Configure dedicated self-hosted runners to create the pull requests that will update dependencies. This is required because the workflows use a specific runner label. For more information, see [Managing self-hosted runners for Dependabot updates on your enterprise](/en/enterprise-server@3.20/admin/github-actions/enabling-github-actions-for-github-enterprise-server/managing-self-hosted-runners-for-dependabot-updates).

11. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.

12. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plug" aria-label="plug" role="img"><path d="M4 8H2.5a1 1 0 0 0-1 1v5.25a.75.75 0 0 1-1.5 0V9a2.5 2.5 0 0 1 2.5-2.5H4V5.133a1.75 1.75 0 0 1 1.533-1.737l2.831-.353.76-.913c.332-.4.825-.63 1.344-.63h.782c.966 0 1.75.784 1.75 1.75V4h2.25a.75.75 0 0 1 0 1.5H13v4h2.25a.75.75 0 0 1 0 1.5H13v.75a1.75 1.75 0 0 1-1.75 1.75h-.782c-.519 0-1.012-.23-1.344-.63l-.761-.912-2.83-.354A1.75 1.75 0 0 1 4 9.867Zm6.276-4.91-.95 1.14a.753.753 0 0 1-.483.265l-3.124.39a.25.25 0 0 0-.219.248v4.734c0 .126.094.233.219.249l3.124.39a.752.752 0 0 1 .483.264l.95 1.14a.25.25 0 0 0 .192.09h.782a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25h-.782a.25.25 0 0 0-.192.09Z"></path></svg> GitHub Connect**.

13. Under "Dependabot", to the right of "Users can easily upgrade to non-vulnerable open source code dependencies", click **Enable**.

When you enable Dependabot alerts, you should consider also setting up GitHub Actions for Dependabot security updates. This feature allows developers to fix vulnerabilities in their dependencies. For more information, see [Managing self-hosted runners for Dependabot updates on your enterprise](/en/enterprise-server@3.20/admin/github-actions/enabling-github-actions-for-github-enterprise-server/managing-self-hosted-runners-for-dependabot-updates).

If you need enhanced security, we recommend configuring Dependabot to use private registries. For more information, see [Configuring access to private registries for Dependabot](/en/enterprise-server@3.20/code-security/dependabot/working-with-dependabot/configuring-access-to-private-registries-for-dependabot#configuring-private-registries).