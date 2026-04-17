# Enabling automatic access to GitHub.com actions using GitHub Connect

To allow GitHub Actions in your enterprise to use actions from GitHub.com, you can connect your enterprise instance to GitHub Enterprise Cloud.

> \[!NOTE]
> GitHub Enterprise Server users should use self-hosted runners. GitHub-hosted runners are **not** supported.

## About automatic access to GitHub.com actions

By default, GitHub Actions workflows on GitHub Enterprise Server cannot use actions directly from GitHub.com or [GitHub Marketplace](https://github.com/marketplace?type=actions). To make public actions from GitHub.com available on your enterprise instance, you can use GitHub Connect to integrate GitHub Enterprise Server with GitHub Enterprise Cloud.

To use actions from GitHub.com, both GitHub Enterprise Server and your self-hosted runners must be able to make outbound connections to GitHub.com. No inbound connections from GitHub.com are required. For more information. For more information, see [Self-hosted runners reference](/en/enterprise-server@3.20/actions/hosting-your-own-runners/managing-self-hosted-runners/communicating-with-self-hosted-runners#communication-between-self-hosted-runners-and-githubcom).

Alternatively, if you want stricter control over which actions are allowed in your enterprise, you can manually download and sync public actions onto your enterprise instance using the `actions-sync` tool. For more information, see [Manually syncing actions from GitHub.com](/en/enterprise-server@3.20/admin/github-actions/managing-access-to-actions-from-githubcom/manually-syncing-actions-from-githubcom).

## About resolution for actions using GitHub Connect

When a workflow uses an action by referencing the repository where the action is stored, GitHub Actions will first try to find the repository on your GitHub Enterprise Server instance. If the repository does not exist on your GitHub Enterprise Server instance, and if you have automatic access to GitHub.com enabled, GitHub Actions will try to find the repository on GitHub.com.

If a user has already created an organization and repository in your enterprise that matches an organization and repository name on GitHub.com, the repository on your enterprise will be used instead of the GitHub.com repository. For more information, see [Automatic retirement of namespaces for actions accessed on GitHub.com](#automatic-retirement-of-namespaces-for-actions-accessed-on-githubcom).

## Enabling automatic access to public GitHub.com actions

Before enabling access to public actions from GitHub.com for your enterprise, you must:

* Configure your GitHub Enterprise Server instance to use GitHub Actions. For more information, see [Getting started with GitHub Actions for GitHub Enterprise Server](/en/enterprise-server@3.20/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/getting-started-with-github-actions-for-github-enterprise-server).
* Enable GitHub Connect. For more information, see [Enabling GitHub Connect for GitHub.com](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/managing-github-connect).

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plug" aria-label="plug" role="img"><path d="M4 8H2.5a1 1 0 0 0-1 1v5.25a.75.75 0 0 1-1.5 0V9a2.5 2.5 0 0 1 2.5-2.5H4V5.133a1.75 1.75 0 0 1 1.533-1.737l2.831-.353.76-.913c.332-.4.825-.63 1.344-.63h.782c.966 0 1.75.784 1.75 1.75V4h2.25a.75.75 0 0 1 0 1.5H13v4h2.25a.75.75 0 0 1 0 1.5H13v.75a1.75 1.75 0 0 1-1.75 1.75h-.782c-.519 0-1.012-.23-1.344-.63l-.761-.912-2.83-.354A1.75 1.75 0 0 1 4 9.867Zm6.276-4.91-.95 1.14a.753.753 0 0 1-.483.265l-3.124.39a.25.25 0 0 0-.219.248v4.734c0 .126.094.233.219.249l3.124.39a.752.752 0 0 1 .483.264l.95 1.14a.25.25 0 0 0 .192.09h.782a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25h-.782a.25.25 0 0 0-.192.09Z"></path></svg> GitHub Connect**.
3. Under "Users can utilize actions from GitHub.com in workflow runs", use the drop-down menu and select **Enabled**.
4. After you enable GitHub Connect, you can use policies to restrict which public actions can be used in repositories in your enterprise. For more information, see [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-server@3.20/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise).

## Automatic retirement of namespaces for actions accessed on GitHub.com

When you enable GitHub Connect, users see no change in behavior for existing workflows because GitHub Actions searches your GitHub Enterprise Server instance for each action before falling back to GitHub.com. This ensures that any custom versions of actions your enterprise has created are used in preference to their counterparts on GitHub.com.

To ensure workflows use their intended actions and to block the potential for abuse, once an action on GitHub.com is used for the first time, the namespace associated with that action is retired in your enterprise. This blocks users from creating an organization and repository in your enterprise that match the action's namespace on GitHub.com.

After using an action from GitHub.com, if you want to create an action in your GitHub Enterprise Server instance with the same name, first you need to make the namespace for that organization and repository available.

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. In the left sidebar, under **Site admin** click **Retired namespaces**.
4. To the right of the namespace that you want use in your GitHub Enterprise Server instance, click **Unretire**.
5. Go to the relevant organization and create a new repository.

   > \[!TIP]
   > When you unretire a namespace, always create the new repository with that name as soon as possible. If a workflow calls the associated action on GitHub.com before you create the local repository, the namespace will be retired again. For actions used in workflows that run frequently, you may find that a namespace is retired again before you have time to create the local repository. In this case, you can temporarily disable the relevant workflows until you have created the new repository.