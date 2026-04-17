# Creating an issue or pull request from GitHub Desktop

You can create an issue or pull request to propose and collaborate on changes to a repository.

## About issues and pull requests

You can use issues to track ideas, bugs, tasks, and other information that's important to your project. You can create an issue in your project's repository with GitHub Desktop. For more information about issues, see [About issues](/en/issues/tracking-your-work-with-issues/about-issues).

After you create a branch and make changes to files in a project, you can create a pull request. With a pull request, you can propose, discuss, and iterate on changes before you merge the changes into the project. You can create a pull request in your project's repository with GitHub Desktop. For more information about pull requests, see [About pull requests](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

## Prerequisites

Before you create a pull request, you'll need to push changes to a branch on GitHub.

* Save and commit any changes on your local branch. For more information, see [Committing and reviewing changes to your project in GitHub Desktop](/en/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop).
* Push your local commits to the remote repository. For more information, see [Pushing changes to GitHub from GitHub Desktop](/en/desktop/making-changes-in-a-branch/pushing-changes-to-github-from-github-desktop).
* Publish your current branch to GitHub. For more information, see [Managing branches in GitHub Desktop](/en/desktop/making-changes-in-a-branch/managing-branches-in-github-desktop).

## Creating an issue

1. In the menu bar, select **Repository**, then click **Create Issue on GitHub**.

   <div class="ghd-tool mac">

   ![Screenshot of the menu bar on a Mac. In the expanded "Repository" dropdown menu, the cursor hovers over "Create Issue on GitHub".](/assets/images/help/desktop/create-issue-mac.png)

   </div>

   <div class="ghd-tool windows">

   ![Screenshot of the "GitHub Desktop" menu bar on Windows. In the "Repository" dropdown menu, the "Create Issue on GitHub" option is outlined in orange.](/assets/images/help/desktop/create-issue-windows.png)

   </div>

2. On GitHub, click **Get started** to open an issue template or click **Open a blank issue**.

> \[!NOTE]
> If issue templates aren't enabled in your current repository, GitHub Desktop will direct you to a blank issue on GitHub.

## Creating a pull request

1. Click **Preview Pull Request**. GitHub Desktop will open a preview dialog showing the diff of the changes between your current branch and the base branch.

   <div class="ghd-tool mac">

   ![Screenshot of the "No local changes" view. A button, labeled "Preview Pull Request", is highlighted with an orange outline.](/assets/images/help/desktop/mac-preview-pull-request.png)

   </div>

   <div class="ghd-tool windows">

   ![Screenshot of the "No local changes" view. A button, labeled "Preview Pull Request", is highlighted with an orange outline.](/assets/images/help/desktop/windows-preview-pull-request.png)

   </div>

   Alternatively, to go straight to GitHub to create your pull request, select the dropdown icon and click **Create Pull Request**.

2. Confirm that the branch in the **base:** dropdown menu is the branch where you want to merge your changes.
   ![Screenshot of the "Open a Pull Request" dialog window. A button with a dropdown icon, labeled "base: development", is outlined in orange.](/assets/images/help/desktop/base-branch-selection.png)

   GitHub Desktop will advise you whether the current branch can be automatically merged into the base branch.
   ![Screenshot of the "Open a Pull Request" dialog window. A status label stating "Can't automatically merge" is highlighted with an orange outline.](/assets/images/help/desktop/preview-dialog-merge-status.png)

3. Click **Create Pull Request**. GitHub Desktop will open your default browser to take you to GitHub.

4. Type a title and description for your pull request.

5. To create a pull request that is ready for review, click **Create Pull Request**.
   To create a draft pull request, use the drop-down and select **Create Draft Pull Request**, then click **Draft Pull Request**. If you are the member of an organization, you may need to request access to draft pull requests from an organization owner. See [About pull requests](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#draft-pull-requests).

## Further reading

* [Issue](/en/get-started/learning-about-github/github-glossary#issue) in the GitHub glossary
* [Pull request](/en/get-started/learning-about-github/github-glossary#pull-request) in the GitHub glossary
* [Base branch](/en/get-started/learning-about-github/github-glossary#base-branch) in the GitHub glossary
* [Topic branch](/en/get-started/learning-about-github/github-glossary#topic-branch) in the GitHub glossary