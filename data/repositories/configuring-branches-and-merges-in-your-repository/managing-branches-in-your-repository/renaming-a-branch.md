# Renaming a branch

You can change the name of a branch in a repository.

## About renaming branches

You can rename a branch in a repository on GitHub.com. For more information about branches, see [About branches](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches).

When you rename a branch, any URLs that contain the old branch name are automatically redirected to the equivalent URL for the renamed branch. Branch protection policies are also updated, as well as the base branch for open pull requests (including those for forks) and draft releases. If the renamed branch is the head branch of an open pull request, this pull request is closed.

If a repository's default branch is renamed, GitHub provides instructions on the repository's home page directing contributors to update their local Git environments.

Although file URLs are automatically redirected, raw file URLs are not redirected. Also, GitHub does not perform any redirects if users perform a `git pull` for the previous branch name.

GitHub Actions workflows do not follow renames, so if your repository publishes an action, anyone using that action with `@{old-branch-name}` will break. You should consider adding a new branch with the original content plus an additional commit reporting that the branch name is closing down and suggesting that users migrate to the new branch name.

Organizational rulesets that apply to branches of a repository will no longer allow the repository administrator to rename branches of the targeted repository or change the default branch to another branch. Repository administrators may create and delete branches so long as they have the appropriate permissions.

## Renaming a branch

1. On GitHub, navigate to the main page of the repository.
2. From the file tree view on the left, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> branch dropdown menu, then click **View all branches**. You can also find the branch dropdown menu at the top of the integrated file editor.

   ![Screenshot of the file tree view for a repository. A dropdown menu for branches is expanded and outlined in dark orange.](/assets/images/help/repository/file-tree-view-branch-dropdown-expanded.png)
3. Next to the branch you want to rename, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> dropdown menu, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="pencil" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> Rename branch**.
4. Type a new name for the branch.
5. Review the information about local environments, then click **Rename branch**.

## Updating a local clone after a branch name changes

After you rename a branch in a repository on GitHub, any collaborator with a local clone of the repository will need to update the clone.

From the local clone of the repository on a computer, run the following commands to update the name of the default branch.

```shell
git branch -m OLD-BRANCH-NAME NEW-BRANCH-NAME
git fetch origin
git branch -u origin/NEW-BRANCH-NAME NEW-BRANCH-NAME
git remote set-head origin -a
```

Optionally, run the following command to remove tracking references to the old branch name.

```shell
git remote prune origin
```