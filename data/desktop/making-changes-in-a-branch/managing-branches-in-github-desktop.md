# Managing branches in GitHub Desktop

You can use GitHub Desktop to create a new branch off of an existing branch in your repository so you can safely experiment with changes.

## About managing branches

You can use branches to safely experiment with changes to your project. Branches isolate your development work from other branches in the repository. For example, you could use a branch to develop a new feature or fix a bug.

You always create a branch from an existing branch. Typically, you might create a branch from the default branch of your repository. You can then work on this new branch in isolation from changes that other people are making to the repository.

You can also create a branch starting from a previous commit in a branch's history. This can be helpful if you need to return to an earlier view of the repository to investigate a bug, or to create a hot fix on top of your latest release.

Once you're satisfied with your work, you can create a pull request to merge your changes in the current branch into another branch. For more information, see [Creating an issue or pull request from GitHub Desktop](/en/desktop/working-with-your-remote-repository-on-github-or-github-enterprise/creating-an-issue-or-pull-request-from-github-desktop) and [About pull requests](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

You can always create a branch in GitHub Desktop if you have read access to a repository, but you can only push the branch to GitHub if you have write access to the repository.

Repository administrators can enable protections on a branch. If you're working on a branch that's protected, you won't be able to delete or force push to the branch. Repository administrators can enable other protected branch settings to enforce specific workflows before a branch can be merged. For more information, see [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

Repository administrators can also enable rulesets. Rulesets can be used to require specific branch names when creating a new branch, or to allow only users with bypass permissions to publish a new branch to the remote repository. GitHub Desktop will show a warning and prevent the branch from being created if the branch does not follow the rulesets. For more information, see [About rulesets](/en/enterprise-cloud@latest/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

## Creating a branch

> \[!TIP]
> The first new branch you create will be based on the default branch. If you have more than one branch, you can choose to base the new branch on the currently checked out branch or the default branch.

1. At the top of the app, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> Current Branch** and then in the list of branches, click the branch that you want to base your new branch on.

   ![Screenshot of the "Current Branch" dropdown view. Under "Recent Branches", a branch, named "my-feature", is highlighted with an orange outline.](/assets/images/help/desktop/select-branch-from-dropdown.png)

2. Click **New Branch**.

   ![Screenshot of the "Current Branch" dropdown view. Next to the "Filter" field, a button, labeled "New Branch", is outlined in orange.](/assets/images/help/desktop/new-branch-button-mac.png)

3. In the "Create a Branch" window, under "Name", type the name of the new branch.

4. Under "Create branch based on...", select a base branch for your new branch.

5. Click **Create Branch**.

## Creating a branch from a previous commit

1. In the left sidebar, click **History**.

   ![Screenshot of the "History" tab in the sidebar. Above a list of commits, the tab button, labeled "History", is highlighted with an orange outline.](/assets/images/help/desktop/history-tab-in-commit-sidebar.png)

2. Right-click on the commit you would like to create a new branch from and select **Create Branch from Commit**.

   ![Screenshot of a list of commits in the "History" tab. Next to a commit, the cursor hovers the "Create Branch from Commit" option in a context menu.](/assets/images/help/desktop/create-branch-from-commit-context-menu.png)

3. In the "Create a Branch" window, under "Name", type the name of the new branch.

4. Click **Create Branch**.

## Publishing a branch

If you create a branch in GitHub Desktop, you'll need to publish the branch to make it available for collaboration on GitHub.

1. In the repository bar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> Current Branch**, then click the branch that you want to publish.
   ![Screenshot of the "Current Branch" dropdown view. Under "Recent Branches", a branch, named "my-feature", is highlighted with an orange outline.](/assets/images/help/desktop/select-branch-from-dropdown.png)
2. Click **Publish branch**.
   ![Screenshot of the repository bar. On the right-hand side, a button, labeled "Publish branch", is highlighted with an orange outline.](/assets/images/help/desktop/publish-branch-button.png)

## Switching between branches

You can view and make commits to any of your repository's branches. If you have uncommitted, saved changes, you'll need to decide what to do with your changes before you can switch branches. You can commit your changes on the current branch, stash your changes to temporarily save them on the current branch, or bring the changes to your new branch. If you want to commit your changes before switching branches, see [Committing and reviewing changes to your project in GitHub Desktop](/en/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop).

> \[!TIP]
> You can set a default behavior for switching branches in the **Prompts** settings. For more information, see [Configuring basic settings in GitHub Desktop](/en/desktop/configuring-and-customizing-github-desktop/configuring-basic-settings-in-github-desktop).

1. In the repository bar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> Current Branch**, then click the branch that you want to switch to.
   ![Screenshot of the "Current Branch" dropdown view. Under "Recent Branches", a branch, named "my-feature", is highlighted with an orange outline.](/assets/images/help/desktop/select-branch-from-dropdown.png)
2. If you have saved, uncommitted changes, in the "Switch Branch" window, select **Leave my changes on CURRENT-BRANCH** or **Bring my changes to NEW-BRANCH**, then click **Switch Branch**.

## Deleting a branch

You can't delete a branch if it's currently associated with an open pull request. You cannot undo deleting a branch.

<div class="ghd-tool mac">

1. In the repository bar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> Current Branch**, then click the branch that you want to delete.
   ![Screenshot of the "Current Branch" dropdown view. Under "Recent Branches", a branch, named "my-feature", is highlighted with an orange outline.](/assets/images/help/desktop/select-branch-from-dropdown.png)
2. In your menu bar, click **Branch**, then click **Delete...**. You can also press <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>D</kbd>.
   ![Screenshot of the menu bar on a Mac. In the expanded "Branch" dropdown menu, the cursor hovers over the "Delete" option, highlighted in blue.](/assets/images/help/desktop/delete-branch-mac.png)

</div>

<div class="ghd-tool windows">

1. In the repository bar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> Current Branch**, then click the branch that you want to delete.
   ![Screenshot of the "Current Branch" dropdown view. Under "Recent Branches", a branch, named "my-feature", is highlighted with an orange outline.](/assets/images/help/desktop/select-branch-from-dropdown.png)
2. In your menu bar, click **Branch**, then click **Delete...**. You can also press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.
   ![Screenshot of the "GitHub Desktop" menu bar on Windows. In the expanded "Branch" dropdown menu, an option labeled "Delete" is outlined in orange.](/assets/images/help/desktop/delete-branch-win.png)

</div>

## Further reading

* [Cloning a repository from GitHub to GitHub Desktop](/en/desktop/adding-and-cloning-repositories/cloning-a-repository-from-github-to-github-desktop)
* [GitHub glossary](/en/get-started/learning-about-github/github-glossary#branch) in the GitHub glossary
* [About branches](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)
* [Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) in the Git documentation
* [Stashing changes in GitHub Desktop](/en/desktop/making-changes-in-a-branch/stashing-changes-in-github-desktop)