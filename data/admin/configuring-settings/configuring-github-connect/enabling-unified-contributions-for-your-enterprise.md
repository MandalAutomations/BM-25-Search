# Enabling unified contributions for your enterprise

You can allow users to include anonymized contribution counts for their work on GitHub.com in their contribution graphs on GitHub Enterprise Cloud.

## About unified contributions

As an enterprise owner, you can allow end users to send anonymized contribution counts for their work from your GitHub Enterprise Server instance to their contribution graph on GitHub.com or GHE.com.

After you enable unified contributions, before individual users can send contribution counts from your GitHub Enterprise Server instance to GitHub Enterprise Cloud, each user must also connect their user account on GitHub Enterprise Server with an account on GitHub Enterprise Cloud. For more information, see [Sharing contributions from GitHub Enterprise Server](/en/enterprise-server@3.20/account-and-profile/setting-up-and-managing-your-github-profile/managing-contribution-settings-on-your-profile/sending-enterprise-contributions-to-your-githubcom-profile).

GitHub requests updates hourly using GitHub Connect.

If the enterprise owner disables the functionality or individual users opt out of the connection, the contribution counts from GitHub Enterprise Server will be deleted on GitHub Enterprise Cloud. If the user reconnects their profiles after disabling them, the contribution counts for the past 90 days are restored.

GitHub Enterprise Server **only** sends the contribution count and source (GitHub Enterprise Server) for connected users. It does not send any information about the contribution or how it was made.

## Enabling unified contributions

Before enabling unified contributions on your GitHub Enterprise Server instance, you must enable GitHub Connect. See [Enabling GitHub Connect for GHE.com](/en/enterprise-server@3.20/admin/configuring-settings/configuring-github-connect/enabling-github-connect-for-ghecom) or [Enabling GitHub Connect for GitHub.com](/en/enterprise-server@3.20/admin/configuring-settings/configuring-github-connect/enabling-github-connect-for-githubcom).

1. Sign in to GitHub Enterprise Server and GitHub Enterprise Cloud.
2. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
3. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
4. In the left sidebar, click **Enterprise overview**.
5. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plug" aria-label="plug" role="img"><path d="M4 8H2.5a1 1 0 0 0-1 1v5.25a.75.75 0 0 1-1.5 0V9a2.5 2.5 0 0 1 2.5-2.5H4V5.133a1.75 1.75 0 0 1 1.533-1.737l2.831-.353.76-.913c.332-.4.825-.63 1.344-.63h.782c.966 0 1.75.784 1.75 1.75V4h2.25a.75.75 0 0 1 0 1.5H13v4h2.25a.75.75 0 0 1 0 1.5H13v.75a1.75 1.75 0 0 1-1.75 1.75h-.782c-.519 0-1.012-.23-1.344-.63l-.761-.912-2.83-.354A1.75 1.75 0 0 1 4 9.867Zm6.276-4.91-.95 1.14a.753.753 0 0 1-.483.265l-3.124.39a.25.25 0 0 0-.219.248v4.734c0 .126.094.233.219.249l3.124.39a.752.752 0 0 1 .483.264l.95 1.14a.25.25 0 0 0 .192.09h.782a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25h-.782a.25.25 0 0 0-.192.09Z"></path></svg> GitHub Connect**.
6. To the right of "Unified contributions", click **Enable**.

   ![Screenshot of the "Unified contributions" option on the GitHub Connect page. The "Enable" button is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/dotcom-ghe-connection-request-access.png)
7. [Sign in](https://enterprise.github.com/login) to the GitHub Enterprise Server site to receive further instructions.

When you request access, we may redirect you to the GitHub Enterprise Server site to check your current terms of service.