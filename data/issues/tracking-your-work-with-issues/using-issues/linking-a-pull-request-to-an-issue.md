# Linking a pull request to an issue

You can link a pull request or branch to an issue to show that a fix is in progress and to automatically close the issue when the pull request or branch is merged.

## About linked issues and pull requests

You can link an issue to a pull request manually or using a supported keyword in the pull request description, that is, the summary text added by the author when they created the pull request.

When you link a pull request to the issue the pull request addresses, collaborators can see that someone is working on the issue.

When you merge a linked pull request into the **default branch** of a repository, its linked issue is automatically closed. For more information about the default branch, see [Changing the default branch](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/changing-the-default-branch).

> \[!NOTE]
> The special keywords in a pull request description are interpreted only when the pull request targets the repository's *default* branch. If the pull request targets *any other branch*, then these keywords are ignored, no links are created, and merging the PR has no effect on the issues.

## Linking a pull request to an issue using a keyword

You can link a pull request to an issue by using a supported keyword in the pull request's description or in a commit message. The pull request **must be** on the default branch.

* `close`
* `closes`
* `closed`
* `fix`
* `fixes`
* `fixed`
* `resolve`
* `resolves`
* `resolved`

If you use a keyword to reference a pull request comment in another pull request, the pull requests will be linked. Merging the referencing pull request also closes the referenced pull request.

The syntax for closing keywords depends on whether the issue is in the same repository as the pull request.

| Linked issue                    | Syntax                                | Example                                                        |
| ------------------------------- | ------------------------------------- | -------------------------------------------------------------- |
| Issue in the same repository    | KEYWORD #ISSUE-NUMBER                 | `Closes #10`                                                   |
| Issue in a different repository | KEYWORD OWNER/REPOSITORY#ISSUE-NUMBER | `Fixes octo-org/octo-repo#100`                                 |
| Multiple issues                 | Use full syntax for each issue        | `Resolves #10, resolves #123, resolves octo-org/octo-repo#100` |

The keywords can be followed by colons or in uppercase. For example: `Closes: #10`, `CLOSES #10`, or `CLOSES: #10`.

Only manually linked pull requests can be manually unlinked. To unlink an issue that you linked using a keyword, you must edit the pull request description to remove the keyword.

You can also use closing keywords in a commit message. The issue will be closed when you merge the commit into the default branch, but the pull request that contains the commit will not be listed as a linked pull request.

## Manually linking a pull request to an issue using the pull request sidebar

Anyone with write permissions to a repository can manually link a pull request to an issue from the pull request sidebar.

You can manually link up to ten issues to each pull request. The issue and pull request must be in the same repository.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Pull requests," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-pull-requests-global-nav-update.png)
3. In the list of pull requests, click the pull request that you'd like to link to an issue.
4. In the right sidebar, click **Development**.

   ![Screenshot of the issue sidebar. "Development" is outlined in dark orange.](/assets/images/help/pull_requests/development-menu.png)
5. Click the issue you want to link to the pull request.

## Manually linking a pull request or branch to an issue using the issue sidebar

Anyone with write permissions to a repository can manually link a pull request or branch to an issue from the issue sidebar.

You can manually link up to ten issues to each pull request. The issue can be in a different repository than the linked pull request or branch. Your last selected repository will be remembered.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Issues," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-issues-global-nav-update.png)
3. In the list of issues, click the issue that you'd like to link a pull request or branch to.
4. In the right sidebar, click **Development**.

   ![Screenshot of the issue sidebar. "Development" is outlined in dark orange.](/assets/images/help/issues/development-menu.png)
5. Click the repository containing the pull request or branch you want to link to the issue.
6. Click the pull request or branch you want to link to the issue.
7. Click **Apply**.

## Further reading

* [Autolinked references and URLs](/en/get-started/writing-on-github/working-with-advanced-formatting/autolinked-references-and-urls#issues-and-pull-requests)