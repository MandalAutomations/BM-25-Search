# Enabling GitHub Connect for GitHub.com

Enable GitHub Connect to access additional features and workflows from GitHub.com on GitHub.com.

You can access additional features and workflows on your GitHub Enterprise Server instance by enabling GitHub Connect. See [About GitHub Connect](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/about-github-connect).

## What happens when GitHub Connect is enabled?

When you enable GitHub Connect, you configure a connection between your GitHub Enterprise Server instance and an enterprise account on GitHub Enterprise Cloud. The connection uses HTTPS over ports 443 or 80 and is secured by TLS.

Enabling GitHub Connect creates a GitHub App owned by the enterprise account on GitHub Enterprise Cloud. GitHub Enterprise Server uses the GitHub App's credentials to make requests to GitHub Enterprise Cloud.

GitHub Enterprise Server stores credentials from the GitHub App. The following credentials will be replicated to all nodes in a high availability or cluster environment, and stored in any backups, including snapshots created by GitHub Enterprise Server Backup Utilities.

* An authentication token, which is valid for one hour
* A private key, which is used to generate a new authentication token

## Prerequisites

* You must have an enterprise account on GitHub.com that uses GitHub Enterprise Cloud.
* Your enterprise account on GitHub.com must be invoiced. Enterprise accounts on the free trial of GitHub Enterprise Cloud or that pay by credit card cannot be connected to your GitHub Enterprise Server instance.
* If your enterprise account on GitHub.com uses IP allow lists, you must add the IP address or network for your GitHub Enterprise Server instance to your IP allow list. See [Enforcing policies for security settings in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-security-settings-in-your-enterprise#managing-allowed-ip-addresses-for-organizations-in-your-enterprise) in the GitHub Enterprise Cloud documentation.
* To configure a connection, your proxy configuration must allow connectivity to `github.com`, `api.github.com`, and `uploads.github.com`. For more information, see [Configuring an outbound web proxy server](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/configuring-an-outbound-web-proxy-server).
* If you have previously enabled GitHub Connect for an enterprise on GHE.com, you must change your configuration to allow connections to GitHub.com. See [Enabling GitHub Connect for GHE.com](/en/enterprise-server@3.20/admin/configuring-settings/configuring-github-connect/enabling-github-connect-for-ghecom#reenabling-connections-to-githubcom).

## Enabling GitHub Connect

To enable GitHub Connect, you must be an enterprise owner on both GitHub Enterprise Server and GitHub Enterprise Cloud.

1. Sign in to your GitHub Enterprise Server instance and GitHub.com.

2. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.

3. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plug" aria-label="plug" role="img"><path d="M4 8H2.5a1 1 0 0 0-1 1v5.25a.75.75 0 0 1-1.5 0V9a2.5 2.5 0 0 1 2.5-2.5H4V5.133a1.75 1.75 0 0 1 1.533-1.737l2.831-.353.76-.913c.332-.4.825-.63 1.344-.63h.782c.966 0 1.75.784 1.75 1.75V4h2.25a.75.75 0 0 1 0 1.5H13v4h2.25a.75.75 0 0 1 0 1.5H13v.75a1.75 1.75 0 0 1-1.75 1.75h-.782c-.519 0-1.012-.23-1.344-.63l-.761-.912-2.83-.354A1.75 1.75 0 0 1 4 9.867Zm6.276-4.91-.95 1.14a.753.753 0 0 1-.483.265l-3.124.39a.25.25 0 0 0-.219.248v4.734c0 .126.094.233.219.249l3.124.39a.752.752 0 0 1 .483.264l.95 1.14a.25.25 0 0 0 .192.09h.782a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25h-.782a.25.25 0 0 0-.192.09Z"></path></svg> GitHub Connect**.

4. Under "GitHub Connect is not enabled yet", click **Enable GitHub Connect**. By clicking **Enable GitHub Connect**, you agree to the [GitHub Terms for Additional Products and Features](/en/site-policy/github-terms/github-terms-for-additional-products-and-features#connect).

5. To the right of the enterprise account you'd like to connect, click **Connect**.