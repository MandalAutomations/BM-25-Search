# Using the latest version of the official bundled actions

You can update the actions that are bundled with your enterprise, or use actions directly from GitHub.com.

> \[!NOTE]
> GitHub Enterprise Server users should use self-hosted runners. GitHub-hosted runners are **not** supported.

Your enterprise instance includes a number of built-in actions that you can use in your workflows. For more information about the bundled actions, see [About using actions in your enterprise](/en/enterprise-server@3.20/admin/github-actions/managing-access-to-actions-from-githubcom/about-using-actions-in-your-enterprise#official-actions-bundled-with-your-enterprise-instance).

These bundled actions are a point-in-time snapshot of the official actions found at <https://github.com/actions>, so there may be newer versions of these actions available. You can use the `actions-sync` tool to update these actions, or you can configure GitHub Connect to allow access to the latest actions on GitHub.com. These options are described in the following sections.

## Using `actions-sync` to update the bundled actions

To update the bundled actions, you can use the `actions-sync` tool to update the snapshot. For more information on using `actions-sync`, see [Manually syncing actions from GitHub.com](/en/enterprise-server@3.20/admin/github-actions/managing-access-to-actions-from-githubcom/manually-syncing-actions-from-githubcom).

## Using GitHub Connect to access the latest actions

You can use GitHub Connect to allow GitHub Enterprise Server to use actions from GitHub.com. For more information, see [Enabling automatic access to GitHub.com actions using GitHub Connect](/en/enterprise-server@3.20/admin/github-actions/managing-access-to-actions-from-githubcom/enabling-automatic-access-to-githubcom-actions-using-github-connect).

Once GitHub Connect is configured, you can use the latest version of an action by deleting its local repository in the `actions` organization on your instance. For example, if your enterprise instance is using `v1` of the `actions/checkout` action, and you need to use `actions/checkout@v5` which isn't available on your enterprise instance, perform the following steps to be able to use the latest `checkout` action from GitHub.com:

1. From an enterprise owner account on GitHub Enterprise Server, navigate to the repository you want to delete from the *actions* organization (in this example `checkout`).
2. By default, site administrators are not owners of the bundled *actions* organization. To get the access required to delete the `checkout` repository, you must use the site admin tools. Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> in the upper-right corner of any page in that repository.
3. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield-lock" aria-label="shield-lock" role="img"><path d="m8.533.133 5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667l5.25-1.68a1.748 1.748 0 0 1 1.066 0Zm-.61 1.429.001.001-5.25 1.68a.251.251 0 0 0-.174.237V7c0 1.36.275 2.666 1.057 3.859.784 1.194 2.121 2.342 4.366 3.298a.196.196 0 0 0 .154 0c2.245-.957 3.582-2.103 4.366-3.297C13.225 9.666 13.5 8.358 13.5 7V3.48a.25.25 0 0 0-.174-.238l-5.25-1.68a.25.25 0 0 0-.153 0ZM9.5 6.5c0 .536-.286 1.032-.75 1.3v2.45a.75.75 0 0 1-1.5 0V7.8A1.5 1.5 0 1 1 9.5 6.5Z"></path></svg> Security** to see an overview of the security for the repository.

   ![Screenshot of the site admin details for a repository. The "Security" link is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/access-repo-security-info.png)
4. Under "Privileged access", click **Unlock**.
5. Under **Reason**, type a reason for unlocking the repository, then click **Unlock**.
6. Now that the repository is unlocked, you can leave the site admin pages and delete the repository within the `actions` organization. At the top of the page, click the repository name, in this example **checkout**, to return to the summary page.

   ![Screenshot of the site admin details for the actions/checkout repository. The name of the repository, "checkout", is a link and is outlined.](/assets/images/enterprise/site-admin-settings/display-repository-admin-summary.png)
7. Under "Repository info", click **View code** to leave the site admin pages and display the `checkout` repository.

   ![Screenshot of the site admin details for a repository. The "View code" link is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/exit-admin-page-for-repository.png)
8. Delete the `checkout` repository within the `actions` organization. For information on how to delete a repository, see [Deleting a repository](/en/enterprise-server@3.20/repositories/creating-and-managing-repositories/deleting-a-repository).
9. Configure your workflow's YAML to use `actions/checkout@v5`.
10. Each time your workflow runs, the runner will use the specified version of `actions/checkout` from GitHub.com.

    > \[!NOTE]
    > The first time the `checkout` action is used from GitHub.com, the `actions/checkout` namespace is automatically retired on your GitHub Enterprise Server instance. If you ever want to revert to using a local copy of the action, you first need to remove the namespace from retirement. For more information, see [Enabling automatic access to GitHub.com actions using GitHub Connect](/en/enterprise-server@3.20/admin/github-actions/managing-access-to-actions-from-githubcom/enabling-automatic-access-to-githubcom-actions-using-github-connect#automatic-retirement-of-namespaces-for-actions-accessed-on-githubcom).