# Working on GitHub Docs in a codespace

You can use GitHub Codespaces to work on documentation for GitHub Docs.

## About GitHub Codespaces

GitHub Codespaces allows you to work in a development environment that's hosted remotely from your machine. You can get started quickly, without needing to set up the working environment or download files to your local computer.

For more information, see [Quickstart for GitHub Codespaces](/en/codespaces/quickstart).

## Working on documentation in a codespace

The following steps assume you have GitHub Codespaces set up to edit files using Visual Studio Code for Web. The steps are very similar if you have set a different editor. For more information, see [Setting your default editor for GitHub Codespaces](/en/codespaces/customizing-your-codespace/setting-your-default-editor-for-codespaces).

1. Navigate to the open source repository for GitHub Docs, [`github/docs`](https://github.com/github/docs).
2. If you're an open source contributor, create a fork of the repository, then follow the rest of the steps in this procedure from your fork. For more information, see [Fork a repository](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo).
3. Create a branch to work on. For more information, see [Creating and deleting branches within your repository](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository).
4. On the main page of the repository, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code**, then click **Create codespace on BRANCH-NAME**.

   The "Setting up your codespace" page is displayed. After a short time the browser-based version of Visual Studio Code is displayed.
5. Use the Explorer to navigate to the markdown file you want to edit. If the file is an article, it will be located in the `content` directory. If the file is reusable content, it will be located in the `data` directory.

   In most cases, the path to an article in the `content` directory matches the path in the URL, minus the `.md` file extension. For example, the source for the article `https://docs.github.com/en/codespaces/quickstart` is the markdown file `content/codespaces/quickstart.md`.<!-- markdownlint-disable-line search-replace -->
6. Edit the markdown file as required.
7. Save your changes.
8. Commit and push your changes, either using the Source Control view, or using Git commands from the Terminal. For more information, see [About Git](/en/get-started/using-git/about-git).

## Creating a pull request

1. Navigate to the "Pull requests" tab of the `github/docs` repository at [github.com/github/docs/pulls](https://github.com/github/docs/pulls).
2. Click **New pull request**.
3. If you're an open source contributor, click **compare across forks**, then choose the forked repository you created and your working branch.

   Otherwise, change the "compare" branch to your working branch.
4. Check that the changes displayed include all of the changes you made in the codespace. If they do not, this may indicate there are changes you have not pushed from the codespace to GitHub.
5. Click **Create pull request**.
6. Enter the details for your pull request and click **Create pull request**.

   Your pull request will be reviewed by a member of the GitHub Docs team.