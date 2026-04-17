# Enabling Server Statistics for your enterprise

You can analyze your own aggregate data from GitHub Enterprise Server and help us improve GitHub products by enabling Server Statistics.

## About Server Statistics

Server Statistics collects aggregate usage data from your GitHub Enterprise Server instance, which you can use to better anticipate the needs of your organization, understand how your team works, and show the value you get from GitHub Enterprise Server.

Server Statistics only collects certain aggregate metrics on repositories, issues, pull requests, and other features. GitHub content, such as code, issues, comments, or pull request content, is not collected. For more information, see [About Server Statistics](/en/enterprise-server@3.20/admin/monitoring-activity-in-your-enterprise/analyzing-how-your-team-works-with-server-statistics/about-server-statistics).

By enabling Server Statistics, you are also helping to improve GitHub. The aggregated data you will provide helps us understand how our customers are using GitHub, and make better and more informed product decisions, ultimately benefiting you.

## Enabling Server Statistics

Before you can enable Server Statistics, you must first connect your GitHub Enterprise Server instance to GitHub.com using GitHub Connect. For more information, see [Enabling GitHub Connect for GitHub.com](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/managing-github-connect).

You can disable Server Statistics from GitHub Enterprise Server at any time.

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plug" aria-label="plug" role="img"><path d="M4 8H2.5a1 1 0 0 0-1 1v5.25a.75.75 0 0 1-1.5 0V9a2.5 2.5 0 0 1 2.5-2.5H4V5.133a1.75 1.75 0 0 1 1.533-1.737l2.831-.353.76-.913c.332-.4.825-.63 1.344-.63h.782c.966 0 1.75.784 1.75 1.75V4h2.25a.75.75 0 0 1 0 1.5H13v4h2.25a.75.75 0 0 1 0 1.5H13v.75a1.75 1.75 0 0 1-1.75 1.75h-.782c-.519 0-1.012-.23-1.344-.63l-.761-.912-2.83-.354A1.75 1.75 0 0 1 4 9.867Zm6.276-4.91-.95 1.14a.753.753 0 0 1-.483.265l-3.124.39a.25.25 0 0 0-.219.248v4.734c0 .126.094.233.219.249l3.124.39a.752.752 0 0 1 .483.264l.95 1.14a.25.25 0 0 0 .192.09h.782a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25h-.782a.25.25 0 0 0-.192.09Z"></path></svg> GitHub Connect**.
3. Under "Share server statistics with GitHub.com", select the dropdown menu and click **Enabled** or **Disabled**.