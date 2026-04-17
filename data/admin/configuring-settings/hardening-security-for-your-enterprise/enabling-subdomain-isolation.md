# Enabling subdomain isolation

You can set up subdomain isolation to securely separate user-supplied content from other portions of your GitHub Enterprise Server appliance.

## About subdomain isolation

Subdomain isolation mitigates cross-site scripting and other related vulnerabilities. For more information, see [Cross-site scripting](https://en.wikipedia.org/wiki/Cross-site_scripting) on Wikipedia. We highly recommend that you enable subdomain isolation on your GitHub Enterprise Server instance.

When subdomain isolation is enabled, GitHub Enterprise Server replaces several paths with subdomains. After enabling subdomain isolation, attempts to access the previous paths for some user-supplied content, such as `http(s)://HOSTNAME/raw/`, may return `404` errors.

| Path without subdomain isolation         | Path with subdomain isolation    |
| ---------------------------------------- | -------------------------------- |
| `http(s)://HOSTNAME/`                    | `http(s)://docker.HOSTNAME/`     |
| `http(s)://HOSTNAME/_registry/npm/`      | `https://npm.HOSTNAME/`          |
| `http(s)://HOSTNAME/_registry/rubygems/` | `https://rubygems.HOSTNAME/`     |
| `http(s)://HOSTNAME/_registry/maven/`    | `https://maven.HOSTNAME/`        |
| `http(s)://HOSTNAME/_registry/nuget/`    | `https://nuget.HOSTNAME/`        |
| `http(s)://HOSTNAME/assets/`             | `http(s)://assets.HOSTNAME/`     |
| `http(s)://HOSTNAME/avatars/`            | `http(s)://avatars.HOSTNAME/`    |
| `http(s)://HOSTNAME/codeload/`           | `http(s)://codeload.HOSTNAME/`   |
| `http(s)://HOSTNAME/gist/`               | `http(s)://gist.HOSTNAME/`       |
| `http(s)://HOSTNAME/media/`              | `http(s)://media.HOSTNAME/`      |
| `http(s)://HOSTNAME/notebooks/`          | `http(s)://notebooks.HOSTNAME/`  |
| `http(s)://HOSTNAME/pages/`              | `http(s)://pages.HOSTNAME/`      |
| `http(s)://HOSTNAME/raw/`                | `http(s)://raw.HOSTNAME/`        |
| `http(s)://HOSTNAME/reply/`              | `http(s)://reply.HOSTNAME/`      |
| `http(s)://HOSTNAME/uploads/`            | `http(s)://uploads.HOSTNAME/`    |
| `http(s)://HOSTNAME/viewscreen/`         | `http(s)://viewscreen.HOSTNAME/` |
| Not supported                            | `https://containers.HOSTNAME/`   |

## Prerequisites

> \[!WARNING]
> If subdomain isolation is disabled, we recommend also disabling GitHub Pages on your enterprise. There will be no way to isolate user-supplied GitHub Pages content from the rest of your enterprise's data. For more information, see [Configuring GitHub Pages for your enterprise](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/configuring-github-pages-for-your-enterprise).

Before you enable subdomain isolation, you must configure your network settings for your new domain.

* Specify a valid domain name as your hostname, instead of an IP address. For more information, see [Configuring the hostname for your instance](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/configuring-a-hostname).

> \[!WARNING]
> Do not change the hostname for GitHub Enterprise Server after initial setup. Changing the hostname will cause unexpected behavior, up to and including instance outages and invalidation of users' security keys. If you have changed the hostname for your instance and are experiencing problems, contact GitHub Enterprise Support or GitHub Premium Support.

* Set up a wildcard Domain Name System (DNS) record or individual DNS records for the subdomains listed above. We recommend creating an A record for `*.HOSTNAME` that points to your server's IP address so you don't have to create multiple records for each subdomain.
* Get a wildcard Transport Layer Security (TLS) certificate for `*.HOSTNAME` with a Subject Alternative Name (SAN) for both `HOSTNAME` and the wildcard domain `*.HOSTNAME`. For example, if your hostname is `github.octoinc.com`, get a certificate with the Common Name value set to `*.github.octoinc.com` and a SAN value set to both `github.octoinc.com` and `*.github.octoinc.com`.
* Enable TLS on your appliance. For more information, see [Configuring TLS](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/configuring-tls).

## Enabling subdomain isolation

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the "Settings" sidebar, click **Hostname**.

5. Select **Subdomain isolation (recommended)**.

6. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

7. Wait for the configuration run to complete.