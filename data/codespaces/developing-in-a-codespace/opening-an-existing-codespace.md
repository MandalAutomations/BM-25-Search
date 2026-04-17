# Opening an existing codespace

You can reopen a codespace that you have closed or stopped and return to your work.

You can reopen any of your active or stopped codespaces on GitHub, in Visual Studio Code, or by using GitHub CLI. You can't reopen a codespace that has been deleted. See [Understanding the codespace lifecycle](/en/codespaces/about-codespaces/understanding-the-codespace-lifecycle).

You can view all your codespaces on the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces). From this page, you can:

* Open, stop, or delete your codespaces.
* See who owns (and may be billed for) your codespaces: your personal account, or organizations you belong to. See [GitHub Codespaces billing](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/about-billing-for-github-codespaces).
* See the machine type, size, and status of your codespaces.
* Create a new codespace, either by choosing one of GitHub's templates or by clicking **New codespace**. See [Creating a codespace from a template](/en/codespaces/developing-in-a-codespace/creating-a-codespace-from-a-template) and [Creating a codespace for a repository](/en/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository).
* Prevent automatic deletion of a codespace. See [Configuring automatic deletion of your codespaces](/en/codespaces/setting-your-user-preferences/configuring-automatic-deletion-of-your-codespaces?tool=webui#avoiding-automatic-deletion-of-codespaces).

<div class="ghd-tool webui">

## Resuming a codespace from a repository page

You can quickly resume a codespace when you're viewing a repository on GitHub.

1. With the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code** tab of your repository displayed on GitHub, press <kbd>,</kbd> (the comma key).

   The "Resume codespace" page is displayed. This allows you to resume your most recently used codespace for the currently selected branch of the repository or, if you were viewing a pull request, for the topic branch of the pull request.

   ![Screenshot of the "Resume codespace" page showing the "Resume this codespace" and "Create a new one" buttons.](/assets/images/help/codespaces/resume-codespace.png)

2. Click **Resume this codespace**.

   Alternatively, if you want to create a new codespace for this branch of the repository, click **Create a new one**.

   > \[!NOTE]
   > If you don't have an existing codespace for this branch, the page is titled "Create codespace" and a button labeled **Create a new codespace** is displayed.

You can bookmark the address of this page if you want to get back to it quickly to resume your codespace. Alternatively you can use the address in a link to provide other people with a quick way of creating and resuming their own codespaces for this repository.

## Opening an existing codespace from the "Your codespaces" page

1. In the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces** to take you to the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces).
2. To open a codespace in your default editor, click the name of the codespace. You can set your default editor for Codespaces in your personal settings page. See [Setting your default editor for GitHub Codespaces](/en/codespaces/setting-your-user-preferences/setting-your-default-editor-for-github-codespaces).

   To open the codespace in an editor other than your default:

   1. Click the ellipsis (**...**) to the right of the codespace you want to open.
   2. Click **Open in**.
   3. Click **Open in APPLICATION**.

   You can open the codespace in:

   * Your browser
   * Visual Studio Code
   * JupyterLab

   If you choose **Visual Studio Code** (desktop application), you must make sure you have VS Code installed on your local machine.

   If you choose **JupyterLab**, the JupyterLab application must be installed in the codespace. The default dev container image includes JupyterLab, so codespaces created from the default image will always have JupyterLab installed. For more information about the default image, see [Introduction to dev containers](/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers#using-the-default-dev-container-configuration) and the [`devcontainers/images`](https://github.com/devcontainers/images/tree/main/src/universal) repository. If you're not using the default image in your dev container configuration, you can install JupyterLab by adding the `ghcr.io/devcontainers/features/python` feature to your `devcontainer.json` file. You should include the option `"installJupyterlab": true`. For more information, see the README for the [`python`](https://github.com/devcontainers/features/tree/main/src/python#python-python) feature, in the `devcontainers/features` repository.

## Linking to an existing codespace

You can create links to your existing codespaces. This is useful if you have a long-lived codespace that you return to frequently. You can save the link in a location of your choice, as an alternative to using the link on <https://github.com/codespaces>.

> \[!NOTE]
> You can only open your own codespaces. If someone clicks a link to one of your codespaces they will see a 404 error message.

Create a link using one of the following URL patterns. In these URLs `CODESPACE-NAME` represents the unique, permanent name of the codespace, such as `literate-space-parakeet-w5vg5ww5p793g7g9`, not the codespace's display name. You can find the name of a codespace by copying the link to the codespace on your <https://github.com/codespaces> page and extracting the codespace name from the URL.

| **Link opens in**                             | **Link syntax**                                                                    |
| --------------------------------------------- | ---------------------------------------------------------------------------------- |
| VS Code web client                            | `https://CODESPACE-NAME.github.dev`                                                |
| VS Code web client with a specified workspace | `https://CODESPACE-NAME.github.dev?folder=/workspaces/PATH/TO/WORKSPACE/DIRECTORY` |
| VS Code desktop application                   | `https://github.com/codespaces/CODESPACE-NAME?editor=vscode`                       |
| JupyterLab                                    | `https://github.com/codespaces/CODESPACE-NAME?editor=jupyter`                      |

</div>

<div class="ghd-tool vscode">

## Reopening an existing codespace

> \[!NOTE]
> To use GitHub Codespaces in VS Code, you need to install the Codespaces extension. See [Using GitHub Codespaces in Visual Studio Code](/en/codespaces/developing-in-a-codespace/using-github-codespaces-in-visual-studio-code).

1. In the VS Code desktop application, open the Command Palette with <kbd>Command</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Mac) or <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux).
2. Type "Codespaces" and select one of the following commands.
   * To open a codespace in a new window of VS Code, select **Codespaces: Open Codespace in New Window**
   * To open a codespace in the web editor, select **Codespaces: Open in Browser**
3. Click the codespace that you want to open.

   ![Screenshot of the VS Code Command Palette showing a list of codespaces available to connect to.](/assets/images/help/codespaces/open-codespace-from-vscode.png)

You can also access the commands listed above by navigating to the Remote Explorer view in VS Code and right-clicking the codespace that you want to open.

![Screenshot of a codespace selected in the Remote Explorer, with "Open in Browser" highlighted in the right-click menu.](/assets/images/help/codespaces/open-codespace-remote-explorer.png)

> \[!NOTE]
> If the Remote Explorer is not displayed in the Activity Bar:
>
> 1. Access the Command Palette. For example, by pressing <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd> (Mac) / <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux).
> 2. Type: `details`.
> 3. Click **Codespaces: Details**.

## Linking to an existing codespace

You can create links to your existing codespaces. This is useful if you have a long-lived codespace that you return to frequently. You can save the link in a location of your choice, as an alternative to using the link on <https://github.com/codespaces>.

> \[!NOTE]
> You can only open your own codespaces. If someone clicks a link to one of your codespaces they will see a 404 error message.

Create a link using one of the following URL patterns. In these URLs `CODESPACE-NAME` represents the unique, permanent name of the codespace, such as `literate-space-parakeet-w5vg5ww5p793g7g9`, not the codespace's display name. You can find the name of a codespace by copying the link to the codespace on your <https://github.com/codespaces> page and extracting the codespace name from the URL.

| **Link opens in**                             | **Link syntax**                                                                    |
| --------------------------------------------- | ---------------------------------------------------------------------------------- |
| VS Code web client                            | `https://CODESPACE-NAME.github.dev`                                                |
| VS Code web client with a specified workspace | `https://CODESPACE-NAME.github.dev?folder=/workspaces/PATH/TO/WORKSPACE/DIRECTORY` |
| VS Code desktop application                   | `https://github.com/codespaces/CODESPACE-NAME?editor=vscode`                       |
| JupyterLab                                    | `https://github.com/codespaces/CODESPACE-NAME?editor=jupyter`                      |

</div>

<div class="ghd-tool cli">

## Reopening an existing codespace

If you have installed GitHub CLI, you can use it to work with GitHub Codespaces. For installation instructions for GitHub CLI, see the [GitHub CLI repository](https://github.com/cli/cli#installation).

1. In a terminal, enter one of the following GitHub CLI commands.
   * To open a codespace in VS Code, enter:

     ```shell copy
     gh codespace code
     ```

     > \[!NOTE]
     > You must have VS Code installed on your local machine. See [Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) in the VS Code documentation.

   * To open a codespace in the browser, enter:

     ```shell copy
     gh codespace code --web
     ```

   * To open a codespace in JupyterLab, enter:

     ```shell copy
     gh codespace jupyter
     ```

     > \[!NOTE]
     > The JupyterLab application must be installed in the codespace you are opening. The default dev container image includes JupyterLab, so codespaces created from the default image will always have JupyterLab installed. For more information about the default image, see [Introduction to dev containers](/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers#using-the-default-dev-container-configuration) and the [`devcontainers/images`](https://github.com/devcontainers/images/tree/main/src/universal) repository. If you're not using the default image in your dev container configuration, you can install JupyterLab by adding the `ghcr.io/devcontainers/features/python` feature to your `devcontainer.json` file. You should include the option `"installJupyterlab": true`. For more information, see the README for the [`python`](https://github.com/devcontainers/features/tree/main/src/python#python-python) feature, in the `devcontainers/features` repository.

   * To access a codespace from the command line, over SSH, enter:

     ```shell copy
     gh codespace ssh
     ```

2. Using the arrow keys, navigate to the codespace that you want to open.

3. To open the codespace, press <kbd>Enter</kbd>.

See [`gh codespace code`](https://cli.github.com/manual/gh_codespace_code) in the GitHub CLI manual.

</div>

## Further reading

* [REST API endpoints for Codespaces organizations](/en/rest/codespaces/organizations)