# Making a GitHub App public or private

When registering a GitHub App, you can make it public so that other GitHub accounts can install the app, or private so that you can only install it on the account that owns the app.

## About visibility for GitHub Apps

A GitHub App can be public or private. If you set your GitHub App registration to public, any user on GitHub can install it and authorize it. If you set your GitHub App registration to private, it can only be installed on the account that owns the app. Only members of the organization that owns it can authorize it.

If you want your GitHub App to be available to organizations in a GitHub Enterprise Server instance that you are not part of, then you need to take additional steps. For more information, see [Making your GitHub App available for GitHub Enterprise Server](/en/apps/sharing-github-apps/making-your-github-app-available-for-github-enterprise-server).

If it is important for GitHub Enterprise Server users to be able to use your tool, consider using GitHub Actions instead of a GitHub App. Public actions are available on GitHub Enterprise Server instances with GitHub Connect. For more information, see [Enabling automatic access to GitHub.com actions using GitHub Connect](/en/enterprise-server@3.20/admin/github-actions/managing-access-to-actions-from-githubcom/enabling-automatic-access-to-githubcom-actions-using-github-connect) and [About GitHub Actions for enterprises](/en/enterprise-server@3.20/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/about-github-actions-for-enterprises) in the GitHub Enterprise Server documentation.

For information about changing the visibility of a GitHub App registration, see [Modifying a GitHub App registration](/en/apps/maintaining-github-apps/modifying-a-github-app).

### Public installation flow

Public GitHub Apps have a landing page with an **Install** button, so that other people can install the app on their accounts. If your GitHub App is public to all users on GitHub, you can also choose to publish it to GitHub Marketplace. For more information, see [About GitHub Marketplace for apps](/en/apps/publishing-apps-to-github-marketplace/github-marketplace-overview/about-github-marketplace).

### Private installation flow

Private GitHub Apps can only be installed on the user or organization account of the app owner. Limited information about the app will exist on a landing page for the app, and the **Install** button will only be available to organization owners and app managers for the organization that owns the app, or the personal account if the GitHub App is owned by an individual account.