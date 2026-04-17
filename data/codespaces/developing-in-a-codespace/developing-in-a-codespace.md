# Developing in a codespace

You can work in a codespace using your browser, Visual Studio Code, or in a command shell.

## About development with GitHub Codespaces

You can develop code in a codespace using your choice of tool:

* A command shell, via an SSH connection initiated using GitHub CLI
* The Visual Studio Code desktop application
* A browser-based version of Visual Studio Code

<div class="ghd-tool webui">

The tabs in this article allow you to switch between information for each of these ways of working. You're currently on the tab for the web browser version of Visual Studio Code.

## Working in a codespace in the browser

Using Codespaces in the browser provides you with a fully featured development experience. You can edit code, debug, use Git commands, and run your application.

![Annotated screenshot of the five main components of the user interface: side bar, activity bar, editor, panels, status bar.](/assets/images/help/codespaces/codespace-overview-annotated.png)

The main components of the user interface are:

1. **Side bar** - By default, this area shows your project files in the Explorer.
2. **Activity bar** - This displays the Views and provides you with a way to switch between them. You can reorder the Views by dragging and dropping them.
3. **Editor** - This is where you edit your files. You can right-click the tab for a file to access options such as locating the file in the Explorer.
4. **Panels** - This is where you can see output and debug information, as well as the default place for the integrated Terminal.
5. **Status bar** - This area provides you with useful information about your codespace and project. For example, the branch name, configured ports, and more.
   For the best experience with GitHub Codespaces, we recommend using a Chromium-based browser, like Google Chrome or Microsoft Edge. For more information, see [Troubleshooting GitHub Codespaces clients](/en/codespaces/troubleshooting/troubleshooting-github-codespaces-clients).

### Customizing the codespaces for a repository

You can customize the codespaces that are created for a repository by creating or updating the dev container configuration for the repository. You can do this from within a codespace. After you change a dev container configuration, you can apply the changes to the current codespace by rebuilding the Docker container for the codespace. For more information, see [Introduction to dev containers](/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers).

### Personalizing your codespace

You can use a [dotfiles](https://dotfiles.github.io/tutorials/) repository and [Settings Sync](https://code.visualstudio.com/docs/editor/settings-sync) to personalize aspects of the codespace environment for any codespace that you create. Personalization can include shell preferences and additional tools. For more information, see [Personalizing GitHub Codespaces for your account](/en/codespaces/setting-your-user-preferences/personalizing-github-codespaces-for-your-account).

### Running your app from a codespace

You can forward ports in your codespace to test and debug your application. You can also manage the port protocol and share the port within your organization or publicly. For more information, see [Forwarding ports in your codespace](/en/codespaces/developing-in-codespaces/forwarding-ports-in-your-codespace).

### Committing your changes

When you've made changes to your codespace, either new code or configuration changes, you'll want to commit your changes. Committing configuration changes to your repository ensures that anyone else who creates a codespace from this repository has the same configuration. Any customization you do, such as adding VS Code extensions, will be available to all users.

For this tutorial, you created a codespace from a template repository, so the code in your codespace is not yet stored in a repository. You can create a repository by publishing the current branch to GitHub.

For information, see [Using source control in your codespace](/en/codespaces/developing-in-codespaces/using-source-control-in-your-codespace?tool=webui#publishing-a-codespace-created-from-a-template).

### Using the Visual Studio Code Command Palette

The Visual Studio Code Command Palette allows you to access and manage many features for Codespaces and Visual Studio Code. For more information, see [Using the Visual Studio Code Command Palette in GitHub Codespaces](/en/codespaces/codespaces-reference/using-the-vs-code-command-palette-in-codespaces).

## Navigating to an existing codespace

1. You can see every available codespace that you have created on the "Your codespaces" page. To display this page, in the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces**. This takes you to [github.com/codespaces](https://github.com/codespaces).
2. Click the name of the codespace you want to develop in.

   ![Screenshot of a list of three codespaces on the https://github.com/codespaces page.](/assets/images/help/codespaces/your-codespaces-list.png)

Alternatively, you can see any of your codespaces for a specific repository by navigating to that repository, clicking the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code** button and selecting the **Codespaces** tab. The dropdown menu will display all active codespaces for the repository.

</div>

<div class="ghd-tool vscode">

The tabs in this article allow you to switch between information for each of these ways of working. You're currently on the tab for Visual Studio Code.

## Working in a codespace in VS Code

GitHub Codespaces provides you with the full development experience of Visual Studio Code. You can edit code, debug, and use Git commands while developing in a codespace with VS Code. For more information, see the [VS Code documentation](https://code.visualstudio.com/docs).

![Annotated screenshot of the five main components of the user interface: side bar, activity bar, editor, panels, status bar.](/assets/images/help/codespaces/codespace-annotated-vscode.png)

The main components of the user interface are:

1. **Side bar** - By default, this area shows your project files in the Explorer.
2. **Activity bar** - This displays the Views and provides you with a way to switch between them. You can reorder the Views by dragging and dropping them.
3. **Editor** - This is where you edit your files. You can right-click the tab for a file to access options such as locating the file in the Explorer.
4. **Panels** - This is where you can see output and debug information, as well as the default place for the integrated Terminal.
5. **Status bar** - This area provides you with useful information about your codespace and project. For example, the branch name, configured ports, and more.

For more information on using VS Code, see the [User Interface guide](https://code.visualstudio.com/docs/getstarted/userinterface) in the VS Code documentation.

You can connect to your codespace directly from VS Code. For more information, see [Using GitHub Codespaces in Visual Studio Code](/en/codespaces/developing-in-codespaces/using-github-codespaces-in-visual-studio-code).

For troubleshooting information, see [Troubleshooting GitHub Codespaces clients](/en/codespaces/troubleshooting/troubleshooting-github-codespaces-clients).

### Customizing the codespaces for a repository

You can customize the codespaces that are created for a repository by creating or updating the dev container configuration for the repository. You can do this from within a codespace. After you change a dev container configuration, you can apply the changes to the current codespace by rebuilding the Docker container for the codespace. For more information, see [Introduction to dev containers](/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers).

### Personalizing your codespace

You can use a [dotfiles](https://dotfiles.github.io/tutorials/) repository and [Settings Sync](https://code.visualstudio.com/docs/editor/settings-sync) to personalize aspects of the codespace environment for any codespace that you create. Personalization can include shell preferences and additional tools. For more information, see [Personalizing GitHub Codespaces for your account](/en/codespaces/setting-your-user-preferences/personalizing-github-codespaces-for-your-account).

### Running your app from a codespace

You can forward ports in your codespace to test and debug your application. You can also manage the port protocol and share the port within your organization or publicly. For more information, see [Forwarding ports in your codespace](/en/codespaces/developing-in-codespaces/forwarding-ports-in-your-codespace).

### Committing your changes

When you've made changes to your codespace, either new code or configuration changes, you'll want to commit your changes. Committing configuration changes to your repository ensures that anyone else who creates a codespace from this repository has the same configuration. Any customization you do, such as adding VS Code extensions, will be available to all users.

For this tutorial, you created a codespace from a template repository, so the code in your codespace is not yet stored in a repository. You can create a repository by publishing the current branch to GitHub.

For information, see [Using source control in your codespace](/en/codespaces/developing-in-codespaces/using-source-control-in-your-codespace?tool=webui#publishing-a-codespace-created-from-a-template).

### Using the Visual Studio Code Command Palette

The Visual Studio Code Command Palette allows you to access and manage many features for Codespaces and Visual Studio Code. For more information, see [Using the Visual Studio Code Command Palette in GitHub Codespaces](/en/codespaces/codespaces-reference/using-the-vs-code-command-palette-in-codespaces).

## Navigating to an existing codespace

1. You can see every available codespace that you have created on the "Your codespaces" page. To display this page, in the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces**. This takes you to [github.com/codespaces](https://github.com/codespaces).
2. Click the name of the codespace you want to develop in.

   ![Screenshot of a list of three codespaces on the https://github.com/codespaces page.](/assets/images/help/codespaces/your-codespaces-list.png)

Alternatively, you can see any of your codespaces for a specific repository by navigating to that repository, clicking the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code** button and selecting the **Codespaces** tab. The dropdown menu will display all active codespaces for the repository.

</div>

<div class="ghd-tool cli">

The tabs in this article allow you to switch between information for each of these ways of working. You're currently on the tab for GitHub CLI.

## Working in a codespace in a command shell

> \[!NOTE]
> To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

You can use GitHub CLI to create a new codespace, or start an existing codespace, and then SSH to it. Once connected, you can work on the command line using your preferred command-line tools.

After installing GitHub CLI and authenticating with your GitHub account you can use the command `gh codespace [<SUBCOMMAND>...] --help` to browse the help information. Alternatively, you can view the same reference information at <https://cli.github.com/manual/gh_codespace>.

For more information, see [Using GitHub Codespaces with GitHub CLI](/en/codespaces/developing-in-a-codespace/using-github-codespaces-with-github-cli).

</div>