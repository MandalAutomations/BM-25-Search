# What happens to forks when a repository is deleted or changes visibility?

Deleting your repository or changing its visibility affects that repository's forks.

> \[!WARNING]
>
> * If you remove a person’s access to a private repository, any of their forks of that private repository are deleted. Local clones of the private repository are retained. If a team's access to a private repository is revoked or a team with access to a private repository is deleted, and team members do not have access to the repository through another team, private forks of the repository will be deleted.
> * You are responsible for ensuring that people who have lost access to a repository delete any confidential information or intellectual property.
> * People with admin permissions to a private repository can disallow forking of that repository, and organization owners can disallow forking of any private repository in an organization. For more information, see [Managing the forking policy for your organization](/en/organizations/managing-organization-settings/managing-the-forking-policy-for-your-organization) and [Managing the forking policy for your repository](/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/managing-the-forking-policy-for-your-repository).

## Deleting a private repository

When you delete a private repository, all of its private forks are also deleted.

## Deleting a public repository

When you delete a public repository, the oldest, active public fork is chosen to be the new upstream repository. All other repositories are forked off of this new upstream and subsequent pull requests go to this new upstream repository.

## Private forks and permissions

Private forks inherit the permissions structure of the upstream repository. This helps owners of private repositories maintain control over their code. For example, if the upstream repository is private and gives read/write access to a team, then the same team will have read/write access to any forks of the private upstream repository. Only team permissions (not individual permissions) are inherited by private forks.

> \[!NOTE]
> When you change base permissions for an organization, permissions for private forks are not automatically updated. For more information, see [Setting base permissions for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/setting-base-permissions-for-an-organization#about-base-permissions-for-an-organization).

## Changing a public repository to a private repository

If a public repository is made private, its public forks are split off into a new network. As with deleting a public repository, one of the existing public forks is chosen to be the new upstream repository and all other repositories are forked off of this new upstream. Subsequent pull requests go to this new upstream repository.

In other words, a public repository's forks will remain public in their own separate repository network even after the upstream repository is made private. This allows the fork owners to continue to work and collaborate without interruption. If public forks were not moved into a separate network in this way, the owners of those forks would need to get the appropriate [access permissions](/en/get-started/learning-about-github/access-permissions-on-github) to pull changes from and submit pull requests to the (now private) upstream repository—even though they didn't need those permissions before.

> \[!WARNING]
>
> * Making a public repository private will permanently remove stars and watchers associated to users that will no longer have access to this repository. If you decide to make the repository public in the future, it will not be possible to restore these stars and watchers, and this will affect its repository rankings.
> * Dependency graph and Dependabot alerts will remain enabled with permission to perform read-only analysis on this repository. Any custom Dependabot alert rules will be disabled unless Code Security is enabled for this repository.
> * Code scanning will become unavailable unless Code Security is enabled for this repository.
> * Current forks will remain public and will be detached from this repository.

### Deleting the private repository

If a public repository is made private and then deleted, its public forks will continue to exist in a separate network.

## Changing a private repository to a public repository

When a private repository is made public, all the commits in that repository, including any commits previously pushed to private forks of that repository, will be migrated to a new public repository network and become visible to everyone. Any previously created private forks will remain private but will become disconnected from the original repository that was made public. Each private fork will become a separate private repository and create its own independent network of repositories. Any new changes made to these networks will not be accessible from the original repository that was made public.

### Deleting the public repository

If a private repository is made public and then deleted, its private forks will continue to exist as standalone private repositories in separate networks.

## Further reading

* [Setting repository visibility](/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility)
* [About forks](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks)
* [Managing the forking policy for your repository](/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/managing-the-forking-policy-for-your-repository)
* [Managing the forking policy for your organization](/en/organizations/managing-organization-settings/managing-the-forking-policy-for-your-organization)
* [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-on-forking-private-or-internal-repositories)