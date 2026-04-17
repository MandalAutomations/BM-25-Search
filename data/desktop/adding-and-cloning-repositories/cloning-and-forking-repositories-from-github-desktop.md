# Cloning and forking repositories from GitHub Desktop

You can use GitHub Desktop to clone and fork repositories that exist on GitHub.

## About local repositories

Repositories on GitHub are remote repositories. You can clone or fork a repository with GitHub Desktop to create a local repository on your computer.

You can create a local copy of any repository on GitHub that you have access to by cloning the repository. If you own a repository or have write permissions, you can sync between the local and remote locations. For more information, see [Syncing your branch in GitHub Desktop](/en/desktop/working-with-your-remote-repository-on-github-or-github-enterprise/syncing-your-branch-in-github-desktop).

When you clone a repository, any changes you push to GitHub will affect the original repository. To make changes without affecting the original project, you can create a separate copy by forking the repository. You can create a pull request to propose that maintainers incorporate the changes in your fork into the original upstream repository. For more information, see [About forks](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks).

When you use GitHub Desktop to push a change to a repository that you do not have write access to, GitHub Desktop will prompt you to create a fork. You can choose to use your fork to contribute to the original upstream repository or to work independently on your own project. Any existing forks default to contributing changes to their upstream repositories. You can modify this choice at any time. For more information, see [Managing fork behavior](#managing-fork-behavior).

You can also clone a repository directly from GitHub or GitHub Enterprise. For more information, see [Cloning a repository from GitHub to GitHub Desktop](/en/desktop/adding-and-cloning-repositories/cloning-a-repository-from-github-to-github-desktop).

## Cloning a repository

1. In the **File** menu, click **Clone Repository**.

   <div class="ghd-tool mac">

   ![Screenshot of the menu bar on a Mac. The "File" dropdown menu is expanded, and the "Clone Repository" option is highlighted with an orange outline.](/assets/images/help/desktop/clone-file-menu-mac.png)

   </div>

   <div class="ghd-tool windows">

   ![Screenshot of the "GitHub Desktop" menu bar on Windows. The "File" dropdown menu is expanded, and the "Clone Repository" option is outlined in orange.](/assets/images/help/desktop/clone-file-menu-windows.png)

   </div>

2. Click the tab that corresponds to the location of the repository you want to clone. You can also click **URL** to manually enter the repository location.

   ![Screenshot of the "Clone a repository" window. At the top of the window, "GitHub.com", "GitHub Enterprise" and "URL" tabs are outlined in orange.](/assets/images/help/desktop/choose-repository-location-mac.png)

3. From the list of repositories, click the repository you want to clone.

   ![Screenshot of the "Clone a repository" window. The "github/docs" repository is highlighted with an orange outline.](/assets/images/help/desktop/clone-a-repository-list-mac.png)

4. To select the local directory into which you want to clone the repository, next to the "Local Path" field, click **Choose...** and navigate to the directory.

   ![Screenshot of the "Clone a repository" window. A button, labeled "Choose", is highlighted with an orange outline.](/assets/images/help/desktop/clone-choose-button-mac.png)

5. At the bottom of the "Clone a Repository" window, click **Clone**.

## Forking a repository

You can fork a repository on GitHub or in GitHub Desktop. For information about forking on GitHub, see [Fork a repository](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo?tool=webui).

In GitHub Desktop, if you clone a repository that you do not have write access to, and then attempt to push a change to the repository, a fork will be created for you.

1. In the **File** menu, click **Clone Repository**.

   <div class="ghd-tool mac">

   ![Screenshot of the menu bar on a Mac. The "File" dropdown menu is expanded, and the "Clone Repository" option is highlighted with an orange outline.](/assets/images/help/desktop/clone-file-menu-mac.png)

   </div>

   <div class="ghd-tool windows">

   ![Screenshot of the "GitHub Desktop" menu bar on Windows. The "File" dropdown menu is expanded, and the "Clone Repository" option is outlined in orange.](/assets/images/help/desktop/clone-file-menu-windows.png)

   </div>

2. Click the tab that corresponds to the location of the repository you want to clone. In this example, we click on the URL tab.

   ![Screenshot of the "URL" tab of the "Clone a repository" window. The "GitHub.com", "GitHub Enterprise" and "URL" tabs are outlined in dark orange.](/assets/images/help/desktop/choose-repository-location-url-tab-windows.png)

3. Enter the url or path of the repository you want to clone.

   ![Screenshot of the "URL" tab of the "Clone a repository" window. The input containing "octocat/Spoon-Knife" is highlighted with an orange outline.](/assets/images/help/desktop/clone-a-repository-url-tab-name-input.png)

4. To select the local directory into which you want to clone the repository, next to the "Local Path" field, click **Choose...** and navigate to the directory.

   ![Screenshot of the "URL" tab of the "Clone a repository" window. A button, labeled "Choose", is highlighted with an orange outline.](/assets/images/help/desktop/clone-choose-button-url-windows.png)

5. At the bottom of the "Clone a Repository" window, click **Clone**.

6. To create a fork, attempt to push a change to the repository. For example, create a new branch and publish it. A prompt will appear asking if you want to fork this repository.

   ![Screenshot of the "Create a fork prompt" window. A button, labeled "Fork this repository", is highlighted with an orange outline.](/assets/images/help/desktop/create-fork-button-windows.png)

7. Read the information in the "How are you planning to use this fork?" window.
   * If you plan to use this fork for contributing to the original upstream repository, click **To contribute to the parent project**.
   * If you plan to use this fork for a project not connected to the upstream, click **For my own purposes**.

8. Click **Continue**.

## Managing fork behavior

You can change how a fork behaves with the upstream repository in GitHub Desktop.

1. In the menu bar, select **Repository**, then click **Repository settings...**.

   <div class="ghd-tool mac">

   ![Screenshot of the menu bar on a Mac. In the expanded "Repository" dropdown menu, a cursor hovers over "Repository Settings", highlighted in blue.](/assets/images/help/desktop/repository-settings-mac.png)

   </div>

   <div class="ghd-tool windows">

   ![Screenshot of the "GitHub Desktop" menu bar on Windows. In the open "Repository" dropdown menu, the "Repository Settings" option is outlined.](/assets/images/help/desktop/repository-settings-win.png)

   </div>

2. In the "Repository settings" window, in the left-hand sidebar, click **Fork Behavior**.

3. Under "I'll be using this fork...", use the radio buttons to select how you want to use the fork.

   ![Screenshot of the "Fork Behavior" pane. Two radio buttons, "To contribute to the parent repository" and "For my own purposes", are outlined in orange.](/assets/images/help/desktop/mac-fork-behavior-menu-contribute.png)

4. Click **Save**.

## Creating an alias for a local repository

You can create an alias for a local repository to help differentiate between repositories of the same name in GitHub Desktop. Creating an alias does not affect the repository's name on GitHub. In the repositories list, aliases appear in italics.

1. In the upper-left corner of GitHub Desktop, to the right of the current repository name, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="The triangle-down icon" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg>.
2. Right-click the repository you want to create an alias for, then click **Create Alias**.
3. Type an alias for the repository.
4. Click **Create Alias**.

## Further reading

* [About remote repositories](/en/get-started/git-basics/about-remote-repositories)