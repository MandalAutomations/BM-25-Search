# Creating a codespace for a repository

You can create a codespace for a branch in a repository to develop online.

## About creating a codespace for a repository

You can create a codespace on GitHub, in Visual Studio Code, or by using GitHub CLI. Use the tabs in this article to display instructions for each of these ways of creating a codespace.

You can use GitHub Codespaces on your personal GitHub account, with the quota of free use included each month for accounts on the Free and Pro plans. You can continue using GitHub Codespaces beyond your monthly included storage and compute usage by providing payment details and setting a spending limit. See [GitHub Codespaces billing](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/about-billing-for-github-codespaces).

Organizations can enable members and outside collaborators to create and use codespaces at the organization's expense. For more information, see [Choosing who owns and pays for codespaces in your organization](/en/codespaces/managing-codespaces-for-your-organization/choosing-who-owns-and-pays-for-codespaces-in-your-organization).

Your ability to create codespaces from organization-owned repositories depends on several factors, including the repository's visibility and the settings of the organization or its parent enterprise. For more information, see [Troubleshooting creation and deletion of codespaces](/en/codespaces/troubleshooting/troubleshooting-creation-and-deletion-of-codespaces#no-access-to-create-a-codespace).

If you're starting a new project, you might want to create a codespace from a template and publish to a repository on GitHub later. For more information, see [Creating a codespace from a template](/en/codespaces/developing-in-a-codespace/creating-a-codespace-from-a-template).

If you create a codespace from a repository, the codespace will be associated with a specific branch, which cannot be empty. You can create more than one codespace per repository or even per branch.

You can see every available codespace that you have created on the "Your codespaces" page. To display this page, in the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces**. This takes you to [github.com/codespaces](https://github.com/codespaces).

### The codespace creation process

When you create a codespace, a number of steps happen to create and connect you to your development environment:

* Step 1: VM and storage are assigned to your codespace.
* Step 2: Container is created and your repository is cloned.
* Step 3: You can connect to the codespace.
* Step 4: Codespace continues with post-creation setup.

For more information on what happens when you create a codespace, see [Deep dive into GitHub Codespaces](/en/codespaces/about-codespaces/deep-dive).

For more information on the lifecycle of a codespace, see [Understanding the codespace lifecycle](/en/codespaces/about-codespaces/understanding-the-codespace-lifecycle).

If you want to use Git hooks for your codespace, then you should set up hooks using the `devcontainer.json` lifecycle scripts, such as `postCreateCommand`. These get executed during step 4, above. For information about the lifecycle scripts, see the [dev containers specification](https://containers.dev/implementors/json_reference/#lifecycle-scripts) on the Development Containers website. Since the dev container for your codespace is created after the repository is cloned, any [git template directory](https://git-scm.com/docs/git-init#_template_directory) configured in the dev container image will not apply to your codespace. Hooks must instead be installed after the codespace is created.

You can edit code, debug, and use Git commands while developing in a codespace with VS Code. For more information, see the [VS Code documentation](https://code.visualstudio.com/docs).

To speed up codespace creation, repository administrators can enable GitHub Codespaces prebuilds for a repository. For more information, see [About GitHub Codespaces prebuilds](/en/codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds).

## Creating a codespace for a repository

<div class="ghd-tool webui">

1. On GitHub, navigate to the main page of the repository.

2. Under the repository name, select the branch dropdown menu, which is labeled with the name of the current branch, then click the branch you want to create a codespace for.

   ![Screenshot of the expanded branch dropdown menu, listing various branches. The "trunk" dropdown menu, shown with a branch icon, is outlined in orange.](/assets/images/help/codespaces/branch-drop-down.png)

3. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code** button, then click the **Codespaces** tab.

   A message is displayed at the bottom of the dialog telling you who will pay for the codespace.

   ![Screenshot of Codespaces dialog. The message showing who will pay for the codespace is highlighted with a dark orange outline.](/assets/images/help/codespaces/who-will-pay.png)

4. Create your codespace, either using the default options, or after configuring advanced options:

   * **Use the default options**

     To create a codespace using the default options, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Create a codespace on BRANCH" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>. <br/><br/>

   * **Configure advanced options**

     To configure advanced options for your codespace, such as a different machine type or a particular `devcontainer.json` file:

     1. At the top right of the **Codespaces** tab, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Codespace repository configuration" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> and click **New with options**.

        ![Screenshot of the options dropdown in the "Codespaces" tab, with the option "New with options" highlighted.](/assets/images/help/codespaces/default-machine-type.png)

     2. On the options page for your codespace, choose your preferred options from the dropdown menus.

        ![Screenshot of the advanced options page with buttons for "Branch," "Dev container configuration," "Region," and "Machine type."](/assets/images/help/codespaces/advanced-options.png)

        The options page may also display the names of one or more secrets that it's recommended you create in your Codespaces settings. For more information, see [Recommended secrets](#recommended-secrets).

        > \[!NOTE]
        >
        > * You can bookmark the options page to give you a quick way to create a codespace for this repository and branch.
        > * The <https://github.com/codespaces/new> page provides a quick way to create a codespace for any repository and branch. You can get to this page quickly by typing `codespace.new` into your browser's address bar.
        > * For more information about dev container configuration files, see [Introduction to dev containers](/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers).
        > * For more information about machine types, see [Changing the machine type for your codespace](/en/codespaces/customizing-your-codespace/changing-the-machine-type-for-your-codespace#about-machine-types).
        > * Your choice of available machine types may be limited by a number of factors. These can include a policy configured for your organization, or a minimum machine type specification for your repository. For more information, see [Restricting access to machine types](/en/codespaces/managing-codespaces-for-your-organization/restricting-access-to-machine-types) and [Setting a minimum specification for codespace machines](/en/codespaces/setting-up-your-project-for-codespaces/configuring-dev-containers/setting-a-minimum-specification-for-codespace-machines).

     3. Click **Create codespace**.

## Recommended secrets

The names of user-defined secrets may be displayed on the advanced options page when you create a codespace. This will happen if recommended secrets have been specified in the dev container configuration you have selected. For more information, see [Specifying recommended secrets for a repository](/en/codespaces/setting-up-your-project-for-codespaces/configuring-dev-containers/specifying-recommended-secrets-for-a-repository).

<img src="/assets/images/help/codespaces/recommended-secrets.png" style="max-height:50rem" alt='Screenshot of the "Create codespace" page with four recommended secrets highlighted with a dark orange outline.' />

Entering values for these development environment secrets, when you're prompted to do so, is recommended because it's likely your project will need values for these secrets. However, supplying values is not required for you to create a codespace. You can set these secrets within the codespace if you prefer.

If you enter a value for a recommended secret, the secret will be available in the new codespace. When you click **Create codespace**, the secret is also added to your personal settings for Codespaces, so you will not need to enter a value for the secret in future when you create a codespace for this repository.

If the name of a secret is shown with a checkbox that is unavailable for selection, and no input box, this is because you already have a secret of this name configured in your personal settings for Codespaces, and you have associated it with this repository. If you've created a secret of this name but have not associated it with this repository, the checkbox will be available to select and by doing so you can update your settings to add the association.

If you want to change the value of a preselected secret you can do so from your personal settings for Codespaces at [github.com/settings/codespaces](https://github.com/settings/codespaces). For more information, see [Managing your account-specific secrets for GitHub Codespaces](/en/codespaces/managing-your-codespaces/managing-your-account-specific-secrets-for-github-codespaces).

</div>

<div class="ghd-tool vscode">

After you connect your account on GitHub to the GitHub Codespaces extension, you can create a new codespace. For more information about the GitHub Codespaces extension, see the [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=GitHub.codespaces).

1. In VS Code, in the Activity Bar, click the Remote Explorer icon.

   ![Screenshot of the Activity Bar. The icon for the "Remote Explorer" side bar (a rectangle overlaid by a circle) is highlighted with an orange outline.](/assets/images/help/codespaces/click-remote-explorer-icon-vscode.png)

   > \[!NOTE]
   > If the Remote Explorer is not displayed in the Activity Bar:
   >
   > 1. Access the Command Palette. For example, by pressing <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd> (Mac) / <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux).
   > 2. Type: `details`.
   > 3. Click **Codespaces: Details**.

2. Hover over the "Remote Explorer" side bar and click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="The plus icon" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>.

   ![Screenshot of the "Remote Explorer" side bar for GitHub Codespaces. The tooltip "Create New Codespace" is displayed beside the plus sign button.](/assets/images/help/codespaces/create-codespace-vscode.png)

3. In the text box, type the name of the repository you want to develop in, then select it.

   ![Screenshot of "octo-org/he" entered into the text box and a list of four repositories that start with this string.](/assets/images/help/codespaces/choose-repository-vscode.png)

   A message is displayed at the right side of subsequent prompts telling you who will pay for the codespace.

   ![Screenshot of a prompt for a branch, with the message "Usage paid for by hubwriter."](/assets/images/help/codespaces/who-will-pay-vscode.png)

4. Click the branch you want to develop on.

5. If prompted to choose a dev container configuration file, choose a file from the list.

6. Click the machine type you want to use.

   > \[!NOTE]
   > Your choice of available machine types may be limited by a number of factors. These can include a policy configured for your organization, or a minimum machine type specification for your repository. For more information, see [Restricting access to machine types](/en/codespaces/managing-codespaces-for-your-organization/restricting-access-to-machine-types) and [Setting a minimum specification for codespace machines](/en/codespaces/setting-up-your-project-for-codespaces/configuring-dev-containers/setting-a-minimum-specification-for-codespace-machines).

</div>

<div class="ghd-tool cli">

> \[!NOTE]
> To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

To create a new codespace, use the `gh codespace create` subcommand.

```shell
gh codespace create
```

You are prompted to choose a repository. A message is displayed telling you who will pay for the codespace. You are then prompted to choose a branch, a dev container configuration file (if more than one is available), and a machine type (if more than one is available).

Alternatively, you can use flags to specify some or all of the options:

```shell
gh codespace create -r OWNER/REPO -b BRANCH --devcontainer-path PATH -m MACHINE-TYPE
```

In this example, replace `owner/repo` with the repository identifier. Replace `branch` with the name of the branch, or the full SHA hash of the commit, that you want to be initially checked out in the codespace. If you use the `-r` flag without the `b` flag, the codespace is created from the default branch.

Replace `path` with the path to the dev container configuration file you want to use for the new codespace. If you omit this flag and more than one dev container file is available you will be prompted to choose one from a list. For more information about the dev container configuration file, see [Introduction to dev containers](/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers).

Replace `machine-type` with a valid identifier for an available machine type. Identifiers are strings such as: `basicLinux32gb` and `standardLinux32gb`. The type of machines that are available depends on the repository, your personal account, and your location. If you enter an invalid or unavailable machine type, the available types are shown in the error message. If you omit this flag and more than one machine type is available you will be prompted to choose one from a list.

For full details of the options for this command, see [the GitHub CLI manual](https://cli.github.com/manual/gh_codespace_create).

</div>

## Further reading

* [Opening an existing codespace](/en/codespaces/developing-in-a-codespace/opening-an-existing-codespace)
* [Facilitating quick creation and resumption of codespaces](/en/codespaces/setting-up-your-project-for-codespaces/setting-up-your-repository/facilitating-quick-creation-and-resumption-of-codespaces)
* [REST API endpoints for Codespaces organizations](/en/rest/codespaces/organizations)