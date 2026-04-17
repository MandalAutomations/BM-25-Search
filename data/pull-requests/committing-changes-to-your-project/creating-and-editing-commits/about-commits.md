# About commits

You can save small groups of meaningful changes as commits.

## About commits

Similar to saving a file that's been edited, a commit records changes to one or more files in your branch. Git assigns each commit a unique ID, called a SHA or hash, that identifies:

* The specific changes
* When the changes were made
* Who created the changes

When you make a commit, you must include a commit message that briefly describes the changes.

If the repository you are committing to has compulsory commit signoffs enabled, and you are committing via the web interface, you will automatically sign off on the commit as part of the commit process. For more information, see [Managing the commit signoff policy for your repository](/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/managing-the-commit-signoff-policy-for-your-repository).

You can add a co-author on any commits you collaborate on. For more information, see [Creating a commit with multiple authors](/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/creating-a-commit-with-multiple-authors).

You can also create a commit on behalf of an organization. For more information, see [Creating a commit on behalf of an organization](/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/creating-a-commit-on-behalf-of-an-organization).

Rebasing allows you to change a series of commits and can modify the order of the commits in your timeline. For more information, see [About Git rebase](/en/get-started/using-git/about-git-rebase).

## About commit branches and tag labels

You can see which branch a commit is on by looking at the labels beneath the commit on the commit page.

1. On GitHub, navigate to the main page of the repository.
2. On the main page of the repository, above the file list, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-history" aria-label="history" role="img"><path d="m.427 1.927 1.215 1.215a8.002 8.002 0 1 1-1.6 5.685.75.75 0 1 1 1.493-.154 6.5 6.5 0 1 0 1.18-4.458l1.358 1.358A.25.25 0 0 1 3.896 6H.25A.25.25 0 0 1 0 5.75V2.104a.25.25 0 0 1 .427-.177ZM7.75 4a.75.75 0 0 1 .75.75v2.992l2.028.812a.75.75 0 0 1-.557 1.392l-2.5-1A.751.751 0 0 1 7 8.25v-3.5A.75.75 0 0 1 7.75 4Z"></path></svg> commits**.

   ![Screenshot of the main page for a repository. A clock icon and "178 commits" is highlighted with an orange outline.](/assets/images/help/commits/commits-page.png)
3. To navigate to a specific commit, click the commit message for that commit.

   ![Screenshot of a commit in the commit list for a repository. "Update README.md" is highlighted with an orange outline.](/assets/images/help/commits/commit-message-link.png)
4. To see what branch the commit is on, check the label below the commit message.

   ![Screenshot of a commit summary. A branch icon and "main" are highlighted with an orange outline.](/assets/images/help/commits/commit-branch-indicator.png)

If your commit is not on the default branch (`main`), the label will show the branches which contain the commit. If the commit is part of an unmerged pull request, you can click the link to go to the pull request.

Once the commit is on the default branch, any tags that contain the commit will be shown and the default branch will be the only branch listed. For more information on tags, see [Git Basics - Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging) in the Git documentation.

![Screenshot of a commit summary. The tag icon and "v2.3.4" are highlighted with an orange outline.](/assets/images/help/commits/commit-tag-label.png)

## Using the file tree

You can use the file tree to navigate between files in a commit.

1. On GitHub, navigate to the main page of the repository.
2. On the main page of the repository, above the file list, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-history" aria-label="history" role="img"><path d="m.427 1.927 1.215 1.215a8.002 8.002 0 1 1-1.6 5.685.75.75 0 1 1 1.493-.154 6.5 6.5 0 1 0 1.18-4.458l1.358 1.358A.25.25 0 0 1 3.896 6H.25A.25.25 0 0 1 0 5.75V2.104a.25.25 0 0 1 .427-.177ZM7.75 4a.75.75 0 0 1 .75.75v2.992l2.028.812a.75.75 0 0 1-.557 1.392l-2.5-1A.751.751 0 0 1 7 8.25v-3.5A.75.75 0 0 1 7.75 4Z"></path></svg> commits**.

   ![Screenshot of the main page for a repository. A clock icon and "178 commits" is highlighted with an orange outline.](/assets/images/help/commits/commits-page.png)
3. To navigate to a specific commit, click the commit message for that commit.

   ![Screenshot of a commit in the commit list for a repository. "Update README.md" is highlighted with an orange outline.](/assets/images/help/commits/commit-message-link.png)
4. Click on a file in the file tree to view the corresponding file diff. If the file tree is hidden, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-sidebar-collapse" aria-label="The sidebar collapse icon" role="img"><path d="M6.823 7.823a.25.25 0 0 1 0 .354l-2.396 2.396A.25.25 0 0 1 4 10.396V5.604a.25.25 0 0 1 .427-.177Z"></path><path d="M1.75 0h12.5C15.216 0 16 .784 16 1.75v12.5A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0ZM1.5 1.75v12.5c0 .138.112.25.25.25H9.5v-13H1.75a.25.25 0 0 0-.25.25ZM11 14.5h3.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25H11Z"></path></svg> to display the file tree.

   > \[!NOTE]
   > The file tree will not display if your screen width is too narrow or if the commit only includes one file.

   ![Screenshot of the "Files changed" tab of a pull request. In the left sidebar, the file tree is outlined in dark orange.](/assets/images/help/repository/file-tree.png)
5. To filter by file path, enter part or all of the file path in the **Filter changed files** search box.

## Further reading

* [Committing and reviewing changes to your project in GitHub Desktop](/en/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop#about-commits) on GitHub Desktop