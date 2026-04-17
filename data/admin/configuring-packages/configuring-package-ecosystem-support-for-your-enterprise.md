# Configuring package ecosystem support for your enterprise

You can configure GitHub Packages for your enterprise by globally enabling or disabling individual package ecosystems on your enterprise, including Container registry, Docker, and npm. Learn about other configuration requirements to support specific package ecosystems.

<!-- 2148AF7B-5FF8-4B28-A808-D692FEE2225A -->

## About package ecosystem support

You can choose which package ecosystems you'd like to enable, disable, or set to read-only on your GitHub Enterprise Server instance. Available options are Container registry, Docker, RubyGems, npm, Apache Maven, Gradle, or NuGet.

## Prerequisites

Before you can configure individual package ecosystems, GitHub Packages must be enabled and configured for your instance. For more information, see [Getting started with GitHub Packages for your enterprise](/en/enterprise-server@3.20/admin/packages/getting-started-with-github-packages-for-your-enterprise).

## Enabling or disabling individual package ecosystems

To prevent new packages from being uploaded, you can set an ecosystem you previously enabled to **Read-Only**, while still allowing existing packages to be downloaded.

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the left sidebar, click **Packages**.

5. Under "Ecosystem Toggles", for each package type, select **Enabled**, **Read-Only**, or **Disabled**.

   > \[!NOTE]
   > Subdomain isolation must be enabled to toggle the Container registry options.

   ![Screenshot of the "Ecosystem toggles" section on the Settings page of the Management Console.](/assets/images/enterprise/site-admin-settings/ecosystem-toggles.png)

6. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

7. Wait for the configuration run to complete.

## Connecting to the official npm registry

If you've enabled npm packages on your enterprise and want to allow access to the official npm registry as well as the GitHub Packages npm registry, then you must perform some additional configuration.

GitHub Packages uses a transparent proxy for network traffic that connects to the official npm registry at `registry.npmjs.com`. The proxy is enabled by default and cannot be disabled.

To allow network connections to the npm registry, you will need to configure network ACLs that allow GitHub Enterprise Server to send HTTPS traffic to `registry.npmjs.com` over port 443/TCP.

Note that connections to `registry.npmjs.com` traverse through the Cloudflare network, and subsequently do not connect to a single static IP address; instead, a connection is made to an IP address within the CIDR ranges listed here: <https://www.cloudflare.com/ips/>.

If you wish to enable npm upstream sources, select `Enabled` for `npm upstreaming`.

## Next steps

As a next step, we recommend you check if you need to update or upload a TLS certificate for your packages host URL. For more information, see [Getting started with GitHub Packages for your enterprise](/en/enterprise-server@3.20/admin/packages/getting-started-with-github-packages-for-your-enterprise).