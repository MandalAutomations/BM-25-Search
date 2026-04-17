# Enabling GitHub Connect for GHE.com

Enable GitHub Connect to share data between GHE.com and GitHub.com.

You can access additional features and workflows on your GitHub Enterprise Server instance by enabling GitHub Connect. See [About GitHub Connect](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/about-github-connect).

If you're connecting to an enterprise on **GHE.com**:

* Server Statistics is not available.
* GitHub.com actions are not available.

## What happens when GitHub Connect is enabled?

When you enable GitHub Connect, you configure a connection between your GitHub Enterprise Server instance and an enterprise account on GitHub Enterprise Cloud. The connection uses HTTPS over ports 443 or 80 and is secured by TLS.

Enabling GitHub Connect creates a GitHub App owned by the enterprise account on GitHub Enterprise Cloud. GitHub Enterprise Server uses the GitHub App's credentials to make requests to GitHub Enterprise Cloud.

GitHub Enterprise Server stores credentials from the GitHub App. The following credentials will be replicated to all nodes in a high availability or cluster environment, and stored in any backups, including snapshots created by GitHub Enterprise Server Backup Utilities.

* An authentication token, which is valid for one hour
* A private key, which is used to generate a new authentication token

## Prerequisites

* **Administrative access:** You need administrative access to both an enterprise account on GHE.com and a GitHub Enterprise Server instance.
* **Version requirement:** Your GitHub Enterprise Server instance must run GitHub Enterprise Server 3.12 or later.
* **Proxy configuration:** If using a proxy server, allow connectivity to the following GHE.com hostnames (replace SUBDOMAIN with your enterprise's subdomain).

  * `SUBDOMAIN.ghe.com`
  * `api.SUBDOMAIN.ghe.com`
  * `uploads.SUBDOMAIN.ghe.com`

  See [Configuring an outbound web proxy server](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/configuring-an-outbound-web-proxy-server).

## Step 1: Enable connection to GHE.com

By default, GitHub Connect connects GitHub Enterprise Server to GitHub.com. You must enable your instance to connect to your enterprise's subdomain of GHE.com.

To enable the connection, someone with administrative SSH access to your GitHub Enterprise Server instance must complete the following tasks.

1. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

2. To enable your instance to connect to GHE.com for GitHub Connect, run the following command. Replace SUBDOMAIN with the subdomain for your enterprise on GHE.com, for example `octocorp`.

   ```shell copy
   ghe-config app.github.github-connect-ghe-com-enabled true
   ghe-config app.github.github-connect-ghe-com-subdomain "SUBDOMAIN"
   ```

3. To apply the configuration, run the following command.

   > \[!NOTE] During a configuration run, services on your GitHub Enterprise Server instance may restart, which can cause brief downtime for users.

   ```shell copy
   ghe-config-apply
   ```

After the run completes, you can configure GitHub Connect.

## Step 2: Enable GitHub Connect

To enable GitHub Connect, you must be an enterprise owner on both GitHub Enterprise Server and GitHub Enterprise Cloud.

People with a user account in both environments can connect the accounts from your GitHub Enterprise Server instance.

1. Sign in to your GitHub Enterprise Server instance and GHE.com.

2. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.

3. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plug" aria-label="plug" role="img"><path d="M4 8H2.5a1 1 0 0 0-1 1v5.25a.75.75 0 0 1-1.5 0V9a2.5 2.5 0 0 1 2.5-2.5H4V5.133a1.75 1.75 0 0 1 1.533-1.737l2.831-.353.76-.913c.332-.4.825-.63 1.344-.63h.782c.966 0 1.75.784 1.75 1.75V4h2.25a.75.75 0 0 1 0 1.5H13v4h2.25a.75.75 0 0 1 0 1.5H13v.75a1.75 1.75 0 0 1-1.75 1.75h-.782c-.519 0-1.012-.23-1.344-.63l-.761-.912-2.83-.354A1.75 1.75 0 0 1 4 9.867Zm6.276-4.91-.95 1.14a.753.753 0 0 1-.483.265l-3.124.39a.25.25 0 0 0-.219.248v4.734c0 .126.094.233.219.249l3.124.39a.752.752 0 0 1 .483.264l.95 1.14a.25.25 0 0 0 .192.09h.782a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25h-.782a.25.25 0 0 0-.192.09Z"></path></svg> GitHub Connect**.

4. Under "GitHub Connect is not enabled yet", click **Enable GitHub Connect**. By clicking **Enable GitHub Connect**, you agree to the [GitHub Terms for Additional Products and Features](/en/site-policy/github-terms/github-terms-for-additional-products-and-features#connect).

5. To the right of the enterprise account you'd like to connect, click **Connect**.

6. Choose which individual features of GitHub Connect you want to enable. See [About GitHub Connect](/en/enterprise-server@3.20/admin/configuring-settings/configuring-github-connect/about-github-connect#github-connect-features).

## Reenabling connections to GitHub.com

If you need to reenable GitHub Connect for GitHub.com, you must reconfigure your settings.

1. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

2. Run the following command.

   ```shell copy
   ghe-config app.github.github-connect-ghe-com-enabled false
   ```

3. To apply the configuration, run the following command.

   > \[!NOTE] During a configuration run, services on your GitHub Enterprise Server instance may restart, which can cause brief downtime for users.

   ```shell copy
   ghe-config-apply
   ```

4. Enable GitHub Connect on GitHub.com. See [Enabling GitHub Connect for GitHub.com](/en/enterprise-server@3.20/admin/configuring-settings/configuring-github-connect/enabling-github-connect-for-githubcom).