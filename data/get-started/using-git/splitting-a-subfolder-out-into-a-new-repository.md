# Splitting a subfolder out into a new repository

You can turn a folder within a Git repository into a brand new repository.

> \[!NOTE]
> You need Git version 2.22.0 or later to follow these instructions, otherwise `git filter-repo` will not work.

If you create a new clone of the repository, you won't lose any of your Git history or changes when you split a folder into a separate repository. However, note that the new repository won't have the branches and tags of the original repository.

1. Open <span class="platform-mac">Terminal</span><span class="platform-linux">Terminal</span><span class="platform-windows">Git Bash</span>.

2. Change the current working directory to the location where you want to create your new repository.

3. Clone the repository that contains the subfolder.

   ```shell
   git clone https://github.com/USERNAME/REPOSITORY-NAME
   ```

4. Change the current working directory to your cloned repository.

   ```shell
   cd REPOSITORY-NAME
   ```

5. To filter out the subfolder from the rest of the files in the repository, install [`git-filter-repo`](https://github.com/newren/git-filter-repo), then run `git filter-repo` with the following arguments.

   * `FOLDER-NAME`: The folder within your project where you'd like to create a separate repository.

   <div class="ghd-tool windows">

   > \[!TIP]
   > Windows users should use `/` to delimit folders.

   </div>

   ```shell
   $ git filter-repo --path FOLDER-NAME/
   # Filter the specified branch in your directory and remove empty commits
   ```

   The repository should now only contain the files that were in your subfolder(s).

   If you want one specific subfolder to be the new root folder of the new repository, you can use the following command:

   ```shell
   $ git filter-repo --subdirectory-filter FOLDER-NAME
   # Filter the specific branch by using a single sub-directory as the root for the new repository
   ```

6. [Create a new repository](/en/repositories/creating-and-managing-repositories/creating-a-new-repository) on GitHub.

7. At the top of your new repository on GitHub's Quick Setup page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> to copy the remote repository URL.

   ![Screenshot of the "Quick Setup" header in a repository. Next to the remote URL, an icon of two overlapping squares is outlined in orange.](/assets/images/help/repository/copy-remote-repository-url-quick-setup.png)

   > \[!TIP]
   > For information on the difference between HTTPS and SSH URLs, see [About remote repositories](/en/get-started/git-basics/about-remote-repositories).

8. Add a new remote name with the URL you copied for your repository. For example, `origin` or `upstream` are two common choices.

   ```shell
   git remote add origin https://github.com/USERNAME/REPOSITORY-NAME.git
   ```

9. Verify that the remote URL was added with your new repository name.

   ```shell
   $ git remote -v
   # Verify new remote URL
   > origin  https://github.com/USERNAME/NEW-REPOSITORY-NAME.git (fetch)
   > origin  https://github.com/USERNAME/NEW-REPOSITORY-NAME.git (push)
   ```

10. Push your changes to the new repository on GitHub.

    ```shell
    git push -u origin BRANCH-NAME
    ```