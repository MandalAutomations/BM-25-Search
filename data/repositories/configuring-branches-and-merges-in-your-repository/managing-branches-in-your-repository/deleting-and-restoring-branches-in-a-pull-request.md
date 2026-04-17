# Deleting and restoring branches in a pull request

If you have write access in a repository, you can delete branches that are associated with closed or merged pull requests. You cannot delete branches that are associated with open pull requests.

## Deleting a branch used for a pull request

You can delete a branch that is associated with a pull request if the pull request has been merged or closed and there are no other open pull requests referencing the branch. For information on closing branches that are not associated with pull requests, see [Creating and deleting branches within your repository](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository#deleting-a-branch).

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Pull requests," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-pull-requests-global-nav-update.png)
3. To see a list of closed pull requests, click **Closed**.

   ![Screenshot of the "Pull requests" page for a repository. The "Closed" filter shows a checkmark icon and "31 closed". It is outlined in orange.](/assets/images/help/branches/branches-closed.png)
4. In the list of pull requests, click the pull request that's associated with the branch that you want to delete.
5. Near the bottom of the pull request, click **Delete branch**.

   This button isn't displayed if there's currently an open pull request for this branch.

## Restoring a deleted branch

You can restore the head branch of a closed pull request.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Pull requests," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-pull-requests-global-nav-update.png)
3. To see a list of closed pull requests, click **Closed**.

   ![Screenshot of the "Pull requests" page for a repository. The "Closed" filter shows a checkmark icon and "31 closed". It is outlined in orange.](/assets/images/help/branches/branches-closed.png)
4. In the list of pull requests, click the pull request that's associated with the branch that you want to restore.
5. Near the bottom of the pull request, click **Restore branch**.

## Further reading

* [Creating and deleting branches within your repository](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository)
* [Managing the automatic deletion of branches](/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-the-automatic-deletion-of-branches)