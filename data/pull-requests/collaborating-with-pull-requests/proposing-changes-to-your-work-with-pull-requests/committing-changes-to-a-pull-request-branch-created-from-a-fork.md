# Committing changes to a pull request branch created from a fork

You can commit changes on a pull request branch that was created from a fork of your repository with permission from the pull request creator.

You can only make commits on pull request branches that:

* Are opened in a repository that you have push access to and that were created from a fork of that repository
* Are on a user-owned fork
* Have permission granted from the pull request creator
* Don't have [branch restrictions](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#restrict-who-can-push-to-matching-branches) that will prevent you from committing

Only the user who created the pull request can give you permission to push commits to the user-owned fork. For more information, see [Allowing changes to a pull request branch created from a fork](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/allowing-changes-to-a-pull-request-branch-created-from-a-fork).

> \[!NOTE]
> You can also make commits to a pull request branch from a fork of your repository through GitHub.com by creating your own copy (or fork) of the fork of your repository and committing changes to the same head branch that the original pull request changes were created on. For some general guidelines, see [Creating a pull request from a fork](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork).

1. On GitHub, navigate to the main page of the fork (or copy of your repository) where the pull request branch was created.

2. Above the list of files, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code**.

   ![Screenshot of the list of files on the landing page of a repository. The "Code" button is highlighted with a dark orange outline.](/assets/images/help/repository/code-button.png)

3. Copy the URL for the repository.

   * To clone the repository using HTTPS, under "HTTPS", click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg>.
   * To clone the repository using an SSH key, including a certificate issued by your organization's SSH certificate authority, click **SSH**, then click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg>.
   * To clone a repository using GitHub CLI, click **GitHub CLI**, then click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg>.

     ![Screenshot of the "Code" dropdown menu. To the right of the HTTPS URL for the repository, a copy icon is outlined in dark orange.](/assets/images/help/repository/https-url-clone-cli.png)

4. Open <span class="platform-mac">Terminal</span><span class="platform-linux">Terminal</span><span class="platform-windows">Git Bash</span>.

   > \[!TIP]
   > If you prefer to clone the fork using GitHub Desktop, then see [Cloning a repository](/en/repositories/creating-and-managing-repositories/cloning-a-repository#cloning-a-repository-to-github-desktop).

5. Change the current working directory to the location where you want to download the cloned directory.

   ```shell
   cd open-source-projects
   ```

6. Type `git clone`, and then paste the URL you copied in Step 3.

   ```shell
   git clone https://github.com/USERNAME/FORK-OF-THE-REPOSITORY
   ```

7. Press **Enter**. Your local clone will be created.

   ```shell
   $ git clone https://github.com/USERNAME/FORK-OF-THE-REPOSITORY
   > Cloning into `FORK-OF-THE-REPOSITORY`...
   > remote: Counting objects: 10, done.
   > remote: Compressing objects: 100% (8/8), done.
   > remove: Total 10 (delta 1), reused 10 (delta 1)
   > Unpacking objects: 100% (10/10), done.
   ```

   > \[!TIP]
   > The error message "fatal: destination path 'REPOSITORY-NAME' already exists and is not an empty directory" means that your current working directory already contains a repository with the same name. To resolve the error, you must clone the fork in a different directory.

8. Navigate into your new cloned repository.

   ```shell
   cd FORK-OF-THE-REPOSITORY
   ```

9. Switch branches to the compare branch of the pull request where the original changes were made. If you navigate to the original pull request, you'll see the compare branch at the top of the pull request.

   In this example, the compare branch is `test-branch`:

   ```shell
   git checkout TEST-BRANCH
   ```

   > \[!TIP]
   > For more information about pull request branches, including examples, see [Creating a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request#changing-the-branch-range-and-destination-repository).

10. At this point, you can do anything you want with this branch. You can push new commits to it, run some local tests, or merge other branches into the branch. Make modifications as you like.

11. After you commit your changes to the head branch of the pull request you can push your changes up to the original pull request directly. In this example, the head branch is `test-branch`:

    ```shell
    $ git push origin test-branch
    > Counting objects: 32, done.
    > Delta compression using up to 8 threads.
    > Compressing objects: 100% (26/26), done.
    > Writing objects: 100% (29/29), 74.94 KiB | 0 bytes/s, done.
    > Total 29 (delta 8), reused 0 (delta 0)
    > To https://github.com/USERNAME/FORK-OF-THE-REPOSITORY.git
    > 12da2e9..250e946  TEST-BRANCH -> TEST-BRANCH
    ```

Your new commits will be reflected on the original pull request on GitHub.com.

## Further Reading

* [About forks](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks)