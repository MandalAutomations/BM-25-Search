# About using GitHub Apps

Learn about what a GitHub App is and why you would use a GitHub App.

## About GitHub Apps

GitHub Apps are tools that extend GitHub's functionality. GitHub Apps can do things on GitHub like open issues, comment on pull requests, and manage projects. They can also do things outside of GitHub based on events that happen on GitHub. For example, a GitHub App can post on Slack when an issue is opened on GitHub.

## Finding GitHub Apps

You can discover GitHub Apps on [GitHub Marketplace](https://github.com/marketplace).

You can also build your own GitHub App. For more information, see [About creating GitHub Apps](/en/apps/creating-github-apps/setting-up-a-github-app/about-creating-github-apps).

## Using GitHub Apps

In order to use a GitHub App, you must install the app on your user or organization account. When you install the app, you grant the app permission to read or modify your account's data. The specific permissions depends on the app, and GitHub will tell you what permissions the app requested before you install the app. When you install the app on your organization or user account, you will also specify what repositories the app can access.

If the app requires any additional configuration, the app will direct you to do so. For more information, see [Installing a GitHub App from GitHub Marketplace for your personal account](/en/apps/using-github-apps/installing-a-github-app-from-github-marketplace-for-your-personal-account), [Installing a GitHub App from GitHub Marketplace for your organizations](/en/apps/using-github-apps/installing-a-github-app-from-github-marketplace-for-your-organizations), [Installing a GitHub App from a third party](/en/apps/using-github-apps/installing-a-github-app-from-a-third-party) and [Installing your own GitHub App](/en/apps/using-github-apps/installing-your-own-github-app).

You may also need to authorize a GitHub App to verify your identity, know what resources you can access, or take actions on your behalf. If you need to authorize the app, the app will prompt you to do so. When an app acts on your behalf, it has access to the same resources that you do as long as the app is installed on the account that owns the resources and you have given it the right permissions. For more information, see [Authorizing GitHub Apps](/en/apps/using-github-apps/authorizing-github-apps).

Occasionally, the GitHub App will request updated permissions. GitHub will notify you when this occurs. In order for the app to continue to function, you will need to review and approve the updated permissions. For more information, see [Approving updated permissions for a GitHub App](/en/apps/using-github-apps/approving-updated-permissions-for-a-github-app).

Before you install or authorize a GitHub App, you should make sure that you trust the app developer. If you no longer use the app, you should suspend or uninstall the app and/or revoke your authorization of the app. For more information, see [Reviewing and modifying installed GitHub Apps](/en/apps/using-github-apps/reviewing-and-modifying-installed-github-apps#blocking-access) and [Reviewing and revoking authorization of GitHub Apps](/en/apps/using-github-apps/reviewing-your-authorized-integrations).

## GitHub Apps and OAuth apps

GitHub also supports OAuth apps. Unlike GitHub Apps, you do not install an OAuth app or control what repositories it can access.

Both OAuth apps and GitHub Apps use OAuth 2.0.

OAuth apps can only act on behalf of a user, while GitHub Apps can either act on behalf of a user or independently of a user.

For more information, see [Differences between GitHub Apps and OAuth apps](/en/apps/oauth-apps/building-oauth-apps/differences-between-github-apps-and-oauth-apps) and [Authorizing OAuth apps](/en/apps/oauth-apps/using-oauth-apps/authorizing-oauth-apps).