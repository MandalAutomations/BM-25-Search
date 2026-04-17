# Pushing changes to GitHub from GitHub Desktop

As you commit changes to your project locally, you can push those changes to GitHub from GitHub Desktop so that others may access them from the remote repository.

## About pushing changes to GitHub

When you push changes, you send the committed changes in your local repository to the remote repository on GitHub. If you change your project locally and want other people to have access to the changes, you must push the changes to GitHub.

Before pushing changes, you should update your local branch to include any commits that have been added to the remote repository. If someone has made commits on the remote that are not on your local branch, GitHub Desktop will prompt you to fetch the new commits before pushing your changes to avoid merge conflicts. For more information, see [Syncing your branch in GitHub Desktop](/en/desktop/working-with-your-remote-repository-on-github-or-github-enterprise/syncing-your-branch-in-github-desktop).

Repository administrators can enable protections on a branch. If you're working on a branch that's protected, you won't be able to delete or force push to the branch. Repository administrators can enable other protected branch settings to enforce specific workflows before a branch can be merged. For more information, see [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

Repository administrators can also enable rulesets for a branch, which will prevent a push from completing if a ruleset has not been followed. For example, a ruleset may require a specific branch naming convention, or an issue number at the start of a commit message. GitHub Desktop will warn about rulesets to help prevent your branch from getting into a state where you would be unable to push your changes. For more information, see [About rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

## Pushing changes to GitHub

> \[!NOTE]
> GitHub Desktop will reject a push if it exceeds certain limits.
>
> * A push contains a large file over 100 MiB in size.
> * A push is over 2 GiB in total size.
>
> If you configure Git Large File Storage to track your large files, you can push large files that would normally be rejected. For more information, see [About Git Large File Storage and GitHub Desktop](/en/desktop/configuring-and-customizing-github-desktop/about-git-large-file-storage-and-github-desktop).

1. To push your local changes to the remote repository, in the repository bar, click **Push origin**.

   ![Screenshot of the repository bar. A button, labeled "Push origin", is highlighted with an orange outline.](/assets/images/help/desktop/push-to-origin.png)
2. If there are commits on the remote branch that you don't have on your local branch, GitHub Desktop prompts you to fetch new commits from the remote. In the "New Commits on Remote" window, click **Fetch**.
3. Optionally, click **Preview Pull Request** to open a preview dialog where you can review your changes and begin to create a pull request. For more information, see [Creating an issue or pull request from GitHub Desktop](/en/desktop/working-with-your-remote-repository-on-github-or-github-enterprise/creating-an-issue-or-pull-request-from-github-desktop).

   ![Screenshot of the "No local changes" view. A button, labeled "Preview Pull Request", is highlighted with an orange outline.](/assets/images/help/desktop/mac-preview-pull-request.png)

## Further reading

* [GitHub glossary](/en/get-started/learning-about-github/github-glossary#push) in the GitHub glossary
* [Committing and reviewing changes to your project in GitHub Desktop](/en/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop)
* [Using Git](/en/get-started/using-git)