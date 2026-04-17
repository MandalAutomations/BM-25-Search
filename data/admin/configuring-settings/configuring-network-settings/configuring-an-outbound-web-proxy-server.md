# Configuring an outbound web proxy server

A proxy server provides an additional level of security for GitHub.com.

## About configuration of a proxy for GitHub Enterprise Server

When a proxy server is enabled for your GitHub Enterprise Server instance, outbound messages sent by GitHub Enterprise Server are first sent through the proxy server, unless the destination host is added as an HTTP proxy exclusion. Types of outbound messages include outgoing webhooks, uploading bundles, and fetching legacy avatars. The proxy server's URL is the protocol, domain or IP address, plus the port number, for example `http://127.0.0.1:8123`.

> \[!NOTE]
> To connect your GitHub Enterprise Server instance to GitHub.com, your proxy configuration must allow connectivity to `github.com` and `api.github.com`. For more information, see [Enabling GitHub Connect for GitHub.com](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/managing-github-connect).

If GitHub Actions is enabled for your enterprise, only HTTP proxies are supported. SOCKS5 and HTTPS proxies are not supported. For more information about using GitHub Actions with GitHub Enterprise Server, see [Getting started with GitHub Actions for GitHub Enterprise Server](/en/enterprise-server@3.20/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/getting-started-with-github-actions-for-github-enterprise-server).

## Configuring an outbound web proxy server

You can configure an outbound proxy server your GitHub Enterprise Server instance, and you can configure exceptions for connections to specific domains.

Your instance validates the hostnames for proxy exclusion using the list of IANA's registered top-level domains (TLDs). For more information, see the [list of TLDs](https://data.iana.org/TLD/tlds-alpha-by-domain.txt) on the IANA website.

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the "Settings" sidebar, click **Privacy** and uncheck **Private mode**.

5. Under **HTTP Proxy Server**, type the URL of your proxy server.

6. Optionally, under **HTTP Proxy Exclusion**, type any hosts that do not require proxy access, separating hosts with commas. The following rules apply to top-level domains (TLDs) and IP addresses that you exclude from the proxy.

   * When you exclude a TLD, you can exclude all hosts in a domain from requiring proxy access using `.` as a wildcard prefix, such as `.octo-org.tentacle`.
   * Your instance validates the hostnames you exclude using the list of IANA's registered TLDs. For more information, see the [list of TLDs](https://data.iana.org/TLD/tlds-alpha-by-domain.txt) on the IANA website. If you want to exclude an unregistered TLD, see [Excluding additional unregistered TLDs from the proxy](#excluding-additional-unregistered-tlds-from-the-proxy).
   * You can exclude a full, valid IPv4 or IPv6 address.
   * You cannot exclude an IPv4 or IPv6 address using a preceding or trailing dot as a wildcard.

7. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

8. Wait for the configuration run to complete.

## Excluding additional unregistered TLDs from the proxy

You can configure your instance's proxy settings to exclude unregistered TLDs that aren't specified in the [list of TLDs](https://data.iana.org/TLD/tlds-alpha-by-domain.txt) on the IANA website.

When you exclude additional unregistered TLDs, you must use `.` as a wildcard prefix. If the TLD is `tentacle`, you must exclude `.tentacle`. You cannot exclude an unregistered TLD without the preceding `.`.

1. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

2. Enter the following command, replacing `COMMA-SEPARATED-TLD-LIST` with a comma-separated list of TLDs, each prefixed by a `.` wildcard.

   ```shell
   ghe-config noproxy.exception-tld-list "COMMA-SEPARATED-TLD-LIST"
   ```

   For example:

   ```shell
   ghe-config noproxy.exception-tld-list ".example,.internal"
   ```

3. To apply the configuration, run the following command.

   > \[!NOTE]
   > During a configuration run, services on your GitHub Enterprise Server instance may restart, which can cause brief downtime for users.

   ```shell copy
   ghe-config-apply
   ```

4. Wait for the configuration run to complete.