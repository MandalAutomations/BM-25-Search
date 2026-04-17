# Registering a GitHub App

You can register a GitHub App under your personal account or under any organization you own.

## About registering GitHub Apps

You can register a GitHub App in a few different ways.

* Under your **personal account**.
* Under an **organization you own**.
* Under an **organization** that has granted you permission to manage all its apps. See [Adding and removing GitHub App managers in your organization](/en/organizations/managing-programmatic-access-to-your-organization/adding-github-app-managers-in-your-organization).

A user or organization can register up to 100 GitHub Apps, but there is no limit to how many GitHub Apps can be installed on an account.

## Registering a GitHub App

1. In the upper-right corner of any page on GitHub, click your profile picture.

2. Navigate to your account settings.
   * For an app owned by a personal account, click **Settings**.
   * For an app owned by an organization:
     1. Click **Your organizations**.
     2. To the right of the organization, click **Settings**.

3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Developer settings**.

4. In the left sidebar, click **GitHub Apps**.

5. Click **New GitHub App**.

6. Under "GitHub App name", enter a name for your app. You should choose a clear and short name. The name cannot be longer than 34 characters. Your app's name (converted to lowercase, with spaces replaced by `-`, and with special characters replaced) will be shown in the user interface when your app takes an action. For example, `My APp Näme` would display as `my-app-name`.

   The name must be unique across GitHub. You cannot use the same name as an existing GitHub account, unless it is your own user or organization name.

7. Optionally, under "Description", type a description of your app. Users will see this description when they install your app.

8. Under "Homepage URL", type the full URL to your app's website. If you don’t have a dedicated URL and your app's code is stored in a public repository, you can use that repository URL. Or, you can use the URL of the account that owns the app.

9. Optionally, under "Callback URL", enter the full URL to redirect to after a user authorizes the installation.

   You can enter up to 10 callback URLs. To add additional callback URLs, click **Add callback URL**.

   If your app does not need to act on behalf of a user (does not need to generate a user access token), this field will be ignored. If your app uses device flow instead of web application flow to generate a user access token, this field will be ignored.

   For more information about the callback URL, see [About the user authorization callback URL](/en/apps/creating-github-apps/setting-up-a-github-app/about-the-user-authorization-callback-url). For more information about generating a user access token to act on behalf of a user, see [Authenticating with a GitHub App on behalf of a user](/en/apps/creating-github-apps/authenticating-with-a-github-app/authenticating-with-a-github-app-on-behalf-of-a-user) and [Generating a user access token for a GitHub App](/en/apps/creating-github-apps/authenticating-with-a-github-app/generating-a-user-access-token-for-a-github-app).

10. Optionally, to prevent user access tokens from expiring, deselect **Expire user authorization tokens**. GitHub strongly recommends that you leave this option selected. For more information about refreshing expired tokens and the benefits of user access tokens that expire, see [Refreshing user access tokens](/en/apps/creating-github-apps/authenticating-with-a-github-app/refreshing-user-access-tokens). If your app does not need to generate a user access token, this field will be ignored.

11. Optionally, to prompt users to authorize your app when they install it, select **Request user authorization (OAuth) during installation**. If a user authorizes your app, your app can generate a user access token to make API requests on the user's behalf and attribute app activity to the user. For more information, see [Authenticating with a GitHub App on behalf of a user](/en/apps/creating-github-apps/authenticating-with-a-github-app/authenticating-with-a-github-app-on-behalf-of-a-user) and [Generating a user access token for a GitHub App](/en/apps/creating-github-apps/authenticating-with-a-github-app/generating-a-user-access-token-for-a-github-app).

12. Optionally, if you want to use device flow to generate a user access token, select **Enable Device Flow**. For more information, see [Generating a user access token for a GitHub App](/en/apps/creating-github-apps/authenticating-with-a-github-app/generating-a-user-access-token-for-a-github-app).

13. Optionally, under "Setup URL", enter the URL to redirect users to after they install your app. If additional setup is required after installation, you can use this URL to tell users what steps to take after installation. For more information, see [About the setup URL](/en/apps/creating-github-apps/setting-up-a-github-app/about-the-setup-url).

    If you selected **Request user authorization (OAuth) during installation** in an earlier step, you will not be able to enter a URL here. Users will instead be redirected to the Callback URL as part of the authorization flow, where you can describe additional setup.

14. Optionally, if you want to redirect users to the setup URL after they update an installation, select **Redirect on update**. An update includes adding or removing a repository for an installation. If "Setup URL" is blank, this will be ignored.

15. Optionally, if you do not want your app to receive webhook events, deselect **Active**. For example, if your app will only be used for authentication or does not need to respond to webhooks, deselect this option. For more information, see [Using webhooks with GitHub Apps](/en/apps/creating-github-apps/setting-up-a-github-app/using-webhooks-with-github-apps).

16. If you selected **Active** in the previous step, under "Webhook URL", enter the URL that GitHub should send webhook events to. For more information, see [Using webhooks with GitHub Apps](/en/apps/creating-github-apps/setting-up-a-github-app/using-webhooks-with-github-apps).

17. Optionally, if you selected **Active** in the previous step, under "Webhook secret", enter a secret token to secure your webhooks. GitHub highly recommends that you set a webhook secret. For more information, see [Using webhooks with GitHub Apps](/en/apps/creating-github-apps/setting-up-a-github-app/using-webhooks-with-github-apps).

18. If you entered a webhook URL, under "SSL verification", select whether to enable SSL verification. GitHub highly recommends that you enable SSL verification.

19. Under "Permissions", choose the permissions that your app needs. For each permission, select the dropdown menu and click **Read-only**, **Read & write**, or **No access**. You should select the minimum permissions necessary for your app. For more information, see [Choosing permissions for a GitHub App](/en/apps/creating-github-apps/setting-up-a-github-app/choosing-permissions-for-a-github-app).

20. If you selected **Active** in the earlier step to indicate that your app should receive webhook events, under "Subscribe to events", select the webhook events that you want your app to receive. The permissions that you selected in the previous step determine what webhook events are available. For more information about each webhook event, see [Webhook events and payloads](/en/webhooks-and-events/webhooks/webhook-events-and-payloads).

21. Under "Where can this GitHub App be installed?", select **Only on this account** or **Any account**. For more information on installation options, see [Making a GitHub App public or private](/en/apps/creating-github-apps/setting-up-a-github-app/making-a-github-app-public-or-private).

22. Click **Create GitHub App**.

## Next steps

After registering a GitHub App, you will want to write code to make your GitHub App do something. For examples of how to write code, see:

* [Quickstart for building GitHub Apps](/en/apps/creating-github-apps/writing-code-for-a-github-app/quickstart)
* [Building a GitHub App that responds to webhook events](/en/apps/creating-github-apps/guides/building-a-github-app-that-responds-to-webhook-events)
* [Building a "Login with GitHub" button with a GitHub App](/en/apps/creating-github-apps/guides/building-a-login-with-github-button-with-a-github-app)
* [Building a CLI with a GitHub App](/en/apps/creating-github-apps/guides/building-a-cli-with-a-github-app)
* [Making authenticated API requests with a GitHub App in a GitHub Actions workflow](/en/apps/creating-github-apps/writing-code-for-a-github-app/making-authenticated-api-requests-with-a-github-app-in-a-github-actions-workflow)

You should aim to follow best practices. For more information, see [Best practices for creating a GitHub App](/en/apps/creating-github-apps/setting-up-a-github-app/best-practices-for-creating-a-github-app).

Once your GitHub App is fully built, you can install your GitHub App and share your GitHub App with others. For more information, see [Installing your own GitHub App](/en/apps/using-github-apps/installing-your-own-github-app) and [Sharing your GitHub App](/en/apps/sharing-github-apps/sharing-your-github-app).

You can always make changes to the settings for your GitHub App. For more information, see [Modifying a GitHub App registration](/en/apps/maintaining-github-apps/modifying-a-github-app).