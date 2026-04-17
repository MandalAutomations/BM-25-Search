# Deleting a GitHub App

You can delete GitHub Apps that you own if you no longer want to use or maintain the app.

> \[!NOTE]
> If you want to remove a GitHub App that you use but do not own, see [Reviewing and modifying installed GitHub Apps](/en/apps/using-github-apps/reviewing-and-modifying-installed-github-apps#blocking-access) instead.

## About deleting GitHub Apps

If you own a GitHub App or are an app manager for a GitHub App, you can delete the GitHub App registration. For more information about GitHub App managers, see [About GitHub App managers](/en/apps/maintaining-github-apps/about-github-app-managers).

When you delete a GitHub App registration, the app will be uninstalled from all accounts that the app is installed on.

> \[!NOTE]
> If your GitHub App is published on GitHub Marketplace, you must remove your app from GitHub Marketplace before you can delete your app. For more information, see [Deleting your app listing from GitHub Marketplace](/en/apps/publishing-apps-to-github-marketplace/listing-an-app-on-github-marketplace/deleting-your-github-app-listing-from-github-marketplace).

## Deleting a GitHub App

1. In the upper-right corner of any page on GitHub, click your profile picture.

2. Navigate to your account settings.
   * For an app owned by a personal account, click **Settings**.
   * For an app owned by an organization:
     1. Click **Your organizations**.
     2. To the right of the organization, click **Settings**.

3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Developer settings**.

4. In the left sidebar, click **GitHub Apps**.

5. Select the GitHub App you want to delete.

6. In the left sidebar, click **Advanced**.

7. Click **Delete GitHub App**.

8. In the confirmation box, type the name of the GitHub App to confirm you want to delete it.

9. Click **I understand the consequences, delete this GitHub App**.

These steps only delete your GitHub App registration, and all of the installations it may have. They do not delete any code that you wrote for your app. However, any code that relies on your GitHub App's credentials will no longer function.