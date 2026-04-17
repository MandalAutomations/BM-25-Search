# Contributing to a project

Learn how to contribute to a project through forking.

Contributing to a project on GitHub is an essential skill for developers and collaborators working together to achieve shared goals. Whether you're fixing bugs, adding features, or improving documentation, the process of contributing ensures structured and efficient collaboration.

By following the GitHub flow of forking repositories, creating branches, and submitting pull requests, you can propose changes to a project and get feedback without disrupting other people's work.

This guide provides instructions on contributing to a project using the GitHub UI and the command line. For more information on contributing with GitHub Desktop, see [Cloning and forking repositories from GitHub Desktop](/en/desktop/adding-and-cloning-repositories/cloning-and-forking-repositories-from-github-desktop). For the same with GitHub CLI (Command Line Interface), see [GitHub CLI quickstart](/en/github-cli/github-cli/quickstart).

## About forking

If you want to contribute to someone else's project but don’t have permission to make changes directly, you can create your own copy of the project, make updates, and then suggest those updates for inclusion in the main project. This process is often called a "fork and pull request" workflow.

When you create your own copy (or "fork") of a project, it’s like making a new workspace that shares code with the original project. This is useful for open-source projects or anytime you don’t have write access to the original project.

Once you’ve made your changes in your copy, you can submit them as a pull request, which is a way to propose changes back to the main project. For more information, see [Fork a repository](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo).

## Creating your own copy of a project

This tutorial uses [the Spoon-Knife project](https://github.com/octocat/Spoon-Knife), a test repository that's hosted on GitHub that lets you test the fork and pull request workflow.

1. Navigate to the `Spoon-Knife` project at <https://github.com/octocat/Spoon-Knife>.
2. In the top-right corner of the page, click **Fork**.

   ![Screenshot of the main page of repository. A button, labeled with a fork icon and "Fork 59.3k," is outlined in dark orange.](/assets/images/help/repository/fork-button.png)
3. Under "Owner," select the dropdown menu and click an owner for the forked repository.
   > \[!NOTE] If your username is grayed out, it's because the fork already exists. Instead, you should bring your existing fork up to date. For more information, see [Syncing a fork](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork#syncing-a-fork-branch-from-the-web-ui).
4. By default, forks are named the same as their upstream repositories. Optionally, to further distinguish your fork, in the "Repository name" field, type a name.
5. Optionally, in the "Description" field, type a description of your fork.
6. Optionally, select **Copy the DEFAULT branch only**.

   For many forking scenarios, such as contributing to open-source projects, you only need to copy the default branch. If you do not select this option, all branches will be copied into the new fork.
7. Click **Create fork**.

> \[!NOTE]
> If you want to copy additional branches from the upstream repository, you can do so from the **Branches** page. For more information, see [Creating and deleting branches within your repository](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository).

## Cloning a fork to your computer

You've successfully forked the Spoon-Knife repository, but so far, it only exists on GitHub. To be able to work on the project, you will need to clone it to your computer.

You can clone your fork with the command line, GitHub CLI, or GitHub Desktop.

1. On GitHub, navigate to **your fork** of the Spoon-Knife repository.

2. Above the list of files, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code**.

   ![Screenshot of the list of files on the landing page of a repository. The "Code" button is highlighted with a dark orange outline.](/assets/images/help/repository/code-button.png)

3. Copy the URL for the repository.

   * To clone the repository using HTTPS, under "HTTPS", click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg>.
   * To clone the repository using an SSH key, including a certificate issued by your organization's SSH certificate authority, click **SSH**, then click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg>.
   * To clone a repository using GitHub CLI, click **GitHub CLI**, then click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="Copy to clipboard" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg>.

     ![Screenshot of the "Code" dropdown menu. To the right of the HTTPS URL for the repository, a copy icon is outlined in dark orange.](/assets/images/help/repository/https-url-clone-cli.png)

4. On Mac or Linux, open Terminal. On Windows, open Git Bash.

5. Change the current working directory to the location where you want the cloned directory.

6. Type `git clone`, and then paste the URL you copied earlier. It will look like this, with your GitHub username instead of `YOUR-USERNAME`:

   ```shell
   git clone https://github.com/YOUR-USERNAME/Spoon-Knife
   ```

7. Press **Enter**. Your local clone will be created.

   ```shell
   $ git clone https://github.com/YOUR-USERNAME/Spoon-Knife
   > Cloning into `Spoon-Knife`...
   > remote: Counting objects: 10, done.
   > remote: Compressing objects: 100% (8/8), done.
   > remove: Total 10 (delta 1), reused 10 (delta 1)
   > Unpacking objects: 100% (10/10), done.
   ```

## Creating a branch to work on

Before making changes to the project, you should create a new branch and check it out. By keeping changes in their own branch, you follow GitHub flow and ensure that it will be easier to contribute to the same project again in the future. See [GitHub flow](/en/get-started/using-github/github-flow#following-github-flow).

```shell
git branch BRANCH-NAME
git checkout BRANCH-NAME
```

## Making and pushing changes

Go ahead and make a few changes to the project using your favorite text editor, like [Visual Studio Code](https://code.visualstudio.com). You could, for example, change the text in `index.html` to add your GitHub username.

When you're ready to submit your changes, stage and commit your changes. `git add .` tells Git that you want to include all of your changes in the next commit. `git commit` takes a snapshot of those changes.

```shell
git add .
git commit -m "a short description of the change"
```

When you stage and commit files, you essentially tell Git, "Take a snapshot of my changes." You can continue to make more changes and take more commit snapshots.

Right now, your changes only exist locally. When you're ready to push your changes up to GitHub, push your changes to the remote.

```shell
git push
```

## Making a pull request

Creating a pull request is the final step in producing a fork of someone else's project. When you've made a beneficial change and want to propose it to the original repository, you'll create a pull request for a maintainer to review.

To do so, navigate to the repository on GitHub where your project lives. For this example, it would be at `https://github.com/<your_username>/Spoon-Knife`. You'll see a banner indicating that your branch is one commit ahead of `octocat:main`. Click **Contribute** and then **Open a pull request**.

GitHub will bring you to a page that shows the differences between your fork and the `octocat/Spoon-Knife` repository. Click **Create pull request**.

GitHub will bring you to a page where you can enter a title and a description of your changes. It's important to provide as much useful information and a rationale for why you're making this pull request in the first place. The project owner needs to be able to determine whether your change is as useful to everyone as you think it is. Finally, click **Create pull request**.

## Familiarizing yourself with a project

If you're new to a project, you can use Copilot to help you understand the purpose of the repository, examine files, and dive into specific lines of code. See [Using GitHub Copilot to explore projects](/en/get-started/exploring-projects-on-github/using-github-copilot-to-explore-projects).