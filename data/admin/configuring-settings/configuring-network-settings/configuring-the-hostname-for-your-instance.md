# Configuring the hostname for your instance

You can provide reliable access to GitHub.com by assigning a hostname that's accessible over your network.

## About the hostname for GitHub Enterprise Server

To provide reliable access to your GitHub Enterprise Server instance via a known name on the network, you can configure a hostname. If you configure a hostname instead of using a hard-coded IP address, you will be able to change the physical hardware that your GitHub Enterprise Server instance runs on without affecting users or client software.

The hostname setting in the Management Console should be set to an appropriate fully qualified domain name (FQDN) which is resolvable on the internet or within your internal network. For example, your hostname setting could be `github.companyname.com.` Web and API requests will automatically redirect to the hostname configured in the Management Console. Note that `localhost` is not a valid hostname setting.

Hostnames must be less than 63 characters in length per [Section 2.3.4 of the Domain Names Specification RFC](https://datatracker.ietf.org/doc/html/rfc1035#section-2.3.4).

After you configure a hostname, you can enable subdomain isolation to further increase the security of your GitHub Enterprise Server instance. For more information, see [Enabling subdomain isolation](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/enabling-subdomain-isolation).

GitHub strongly recommends that you do not change the hostname for an existing GitHub Enterprise Server instance. Changing the hostname will cause unexpected behavior, up to and including instance outages. Instead, configure a new instance with the desired hostname, and then restore settings and data from the original instance to the new instance.

For more information on the supported hostname types, see [Section 2.1 of the HTTP RFC](https://tools.ietf.org/html/rfc1123#section-2).

## Configuring the hostname

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the "Settings" sidebar, click **Hostname**.

5. Under "Hostname", type the hostname you'd like to set for your GitHub Enterprise Server instance.

6. To test the DNS and SSL settings for the new hostname, click **Test domain settings**.

7. If you don't receive a green checkmark next to all entries, review your configuration for the setting that failed. For more information, see [Configuring DNS nameservers](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/configuring-dns-nameservers).

8. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

9. Wait for the configuration run to complete.

To help mitigate various cross-site scripting vulnerabilities, we recommend that you enable subdomain isolation for your GitHub Enterprise Server instance after you configure a hostname. For more information, see [Enabling subdomain isolation](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/enabling-subdomain-isolation).

## Changing the hostname

If you need to change the hostname for your GitHub Enterprise Server instance, you must restore a backup of your existing instance to a new instance with the desired hostname. For more information, see [Changing the hostname for your instance](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/changing-the-hostname-for-your-instance).

> \[!WARNING]
> Do not change the hostname for GitHub Enterprise Server after initial setup. Changing the hostname will cause unexpected behavior, up to and including instance outages and invalidation of users' security keys. If you have changed the hostname for your instance and are experiencing problems, contact GitHub Enterprise Support or GitHub Premium Support.