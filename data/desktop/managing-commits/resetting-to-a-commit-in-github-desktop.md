# Resetting to a commit in GitHub Desktop

You can reset to any commit up to the one that was last pushed to the remote branch.

## About resetting to a commit

If you made a series of commits and want to fix a mistake you made prior to the most recent commit, you can use "reset to commit" in GitHub Desktop to reset the changes in those commits. Resetting to a commit restores the changes in the subsequent commits to your working directory and resets the branch to the selected commit. You can then make changes before committing again, or you can discard changes that you don't want to keep. For more information, see [Committing and reviewing changes to your project in GitHub Desktop](/en/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop).

You can reset to commit up to the most recent commit that has already been pushed to the remote repository. To undo a pushed commit without disrupting the commit history for other contributors, you can revert the commit. For more information, see [Reverting a commit in GitHub Desktop](/en/desktop/managing-commits/reverting-a-commit-in-github-desktop).

If you want to edit your most recent commit message, or combine new changes with your most recent commit, you can amend a commit. For more information, see [Amending a commit in GitHub Desktop](/en/desktop/managing-commits/amending-a-commit-in-github-desktop).

## Resetting to a commit

1. In the left sidebar, click **History**.

   ![Screenshot of the "History" tab in the sidebar. Above a list of commits, the tab button, labeled "History", is highlighted with an orange outline.](/assets/images/help/desktop/history-tab-in-commit-sidebar.png)
2. Right-click on the commit you would like to reset to and select **Reset to commit**.

## Further reading

* [Git Tools - Reset Demystified](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified) in the Git documentation