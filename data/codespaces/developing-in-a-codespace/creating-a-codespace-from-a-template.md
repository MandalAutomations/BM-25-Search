# Creating a codespace from a template

If you're starting a new project, you can create a codespace from a blank template or choose a template specially designed for the type of work you want to do.

# About templates for GitHub Codespaces

If you're starting a new project, you can get started with development work quickly by creating a codespace from a template. You'll be able to work on your project in a cloud-based development environment, save your files in the cloud, and publish your work to a new remote repository that you can share with others or clone to your local machine.

You can start from a blank template, choose from templates maintained by GitHub for popular technologies such as React or Jupyter Notebook, or launch a codespace from any template repository on GitHub.

With a blank template, you'll start with an empty directory, with access to cloud-based compute resources and the tools, languages, and runtime environments that come preinstalled with the default dev container image. With other templates, you'll get starter files for the technology you're working with, plus typically some extra files such as a README file, a `.gitignore` file, and dev container configuration files containing some custom environment configuration. For more information on dev containers and the default image, see [Introduction to dev containers](/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers).

As an example, if you create a codespace from GitHub's React template, you'll arrive in a workspace containing template files for a simple application, such as `index.js`, `app.js`, and `package.json`. Shortly after the codespace opens, a development server will start up automatically, and you will be able to view the running application in a simple browser tab within the VS Code web client.

![Screenshot of VS Code's simple browser rendering the web application in GitHub's React template.](/assets/images/help/codespaces/react-template.png)

The files and configuration included in templates are defined in template repositories. The template repository is cloned into your codespace when you create the codespace. After that, the link is severed, and your codespace won't be linked to a remote repository until you publish to one.

> \[!TIP]
> To help people get started with your framework, library, or other project, you can set up a template repository for use with GitHub Codespaces. For more information, see [Setting up a template repository for GitHub Codespaces](/en/codespaces/setting-up-your-project-for-codespaces/setting-up-your-repository/setting-up-a-template-repository-for-github-codespaces).

## Creating a codespace from a GitHub template

Templates maintained by GitHub, including the blank template, are available from the "Your codespaces" page.

1. In the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces** to take you to the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces).

2. To view the full list of templates, in the "Explore quick start templates" section, click **See all**.

   ![Screenshot of the "Explore quick start templates" section. "See all" is highlighted with a dark orange outline.](/assets/images/help/codespaces/codespace-templates-see-all.png)

3. Optionally, to view the template repository containing the files for a template, click the name of the template.

   ![Screenshot of the "Explore quick start templates" section. Three templates are listed. The templates names are outlined in orange.](/assets/images/help/codespaces/react-template-name.png)

4. Under the name of the template you want to launch, click **Use this template**.

When you create a new codespace from a template, it is always opened in the Visual Studio Code web client. You can reopen an existing codespace in any supported editor. For more information, see [Opening an existing codespace](/en/codespaces/developing-in-codespaces/opening-an-existing-codespace).

## Creating a codespace from a template repository

You can create a codespace from any template repository, then publish your work to a new repository when you are ready. For more information on template repositories, see [Creating a repository from a template](/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template#about-repository-templates).

1. On GitHub, navigate to the main page of the repository.
2. Click **Use this template**, then click **Open in a codespace**.

   ![Screenshot of the "Use this template" button and the dropdown menu expanded to show the "Open in a codespace" option.](/assets/images/help/repository/use-this-template-button.png)

   > \[!NOTE]
   > If you're a maintainer of the template repository, and want to commit changes to the template repository itself, you should create a codespace from the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code** dropdown. For more information, see [Creating a codespace for a repository](/en/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository#creating-a-codespace-for-a-repository).

When you create a new codespace from a template, it is always opened in the Visual Studio Code web client. You can reopen an existing codespace in any supported editor. For more information, see [Opening an existing codespace](/en/codespaces/developing-in-codespaces/opening-an-existing-codespace).

## Publishing to a repository on GitHub

When you work in a codespace created from a template, your work is saved on a virtual machine in the cloud, but it is not stored in a repository on GitHub.

You can save your files, close and stop your codespace, and come back to your work later. Typically, Git will come preinstalled, and the working directory will be automatically initialized as a Git repository unless you started from GitHub's blank template. This means you can immediately use Git for local source control, such as adding and committing files.

However, if you delete an unpublished codespace, or if it's automatically deleted by being left unused for the duration of the retention period, then your work will be deleted too. To persist your work, and to allow others to work on your project, you will need to publish your codespace to a repository on GitHub.

> \[!NOTE]
> If an unpublished codespace is currently billed to an organization, publishing the codespace transfers ownership and billing of the codespace to your personal account. See [GitHub Codespaces billing](/en/billing/concepts/product-billing/github-codespaces#how-costs-are-assigned-to-a-billable-account).

### Publishing from VS Code

If you're working in a codespace, you can publish it from the VS Code web client or desktop application.

1. In the Activity Bar, click the **Source Control** view.

   ![Screenshot of the VS Code Activity Bar with the source control button highlighted with an orange outline.](/assets/images/help/codespaces/source-control-activity-bar-button.png)

2. To stage your changes, click **+** next to the file you've added or changed, or next to **Changes** if you've changed multiple files and you want to stage them all.

   ![Screenshot of the "Source control" side bar with the staging button (a plus sign), to the right of "Changes," highlighted with a dark orange outline.](/assets/images/help/codespaces/codespaces-commit-stage.png)

   > \[!NOTE]
   > If you start from GitHub's blank template, you will not see a list of changes unless you have already initialized your directory as a Git repository. To publish codespaces created from the blank template, click **Publish to GitHub** in the "Source Control" view, then skip to step 5.

3. To commit your staged changes, type a commit message describing the change you've made, then click **Commit**.

   ![Screenshot of the "Source control" side bar with a commit message and, below it, the "Commit" button both highlighted with a dark orange outline.](/assets/images/help/codespaces/vscode-commit-button.png)

4. Click **Publish Branch**.

   ![Screenshot of the "Source control" side bar showing the "Publish Branch" button.](/assets/images/help/codespaces/vscode-publish-branch-button.png)

5. In the "Repository Name" dropdown, type a name for your new repository, then select **Publish to GitHub private repository** or **Publish to GitHub public repository**.

   ![Screenshot of the repository name dropdown in VS Code. Two options are shown, for publishing to a private or a public repository.](/assets/images/help/codespaces/choose-new-repository.png)

   The owner of the new repository will be the GitHub account with which you created the codespace.

6. Optionally, in the pop-up that appears in the lower right corner of the editor, click **Open on GitHub** to view the new repository on GitHub.

   ![Screenshot of a confirmation message for a successfully published repository, showing the "Open on GitHub" button.](/assets/images/help/codespaces/open-on-github.png)

When a codespace is published, you have access to a greater range of options to customize your GitHub Codespaces experience. For example, you can:

* Change the machine type of your codespace to make sure you're using resources appropriate for the work you're doing (see [Changing the machine type for your codespace](/en/codespaces/customizing-your-codespace/changing-the-machine-type-for-your-codespace)).
* Allow GitHub to automatically use GPG to sign commits you make in your codespace (see [Managing GPG verification for GitHub Codespaces](/en/codespaces/managing-your-codespaces/managing-gpg-verification-for-github-codespaces)).
* Share secrets with your codespace (see [Managing your account-specific secrets for GitHub Codespaces](/en/codespaces/managing-your-codespaces/managing-your-account-specific-secrets-for-github-codespaces)).

### Publishing from GitHub

You can publish an unpublished codespace from the "Your codespaces" page on GitHub. This is useful if you want to publish a codespace that you don't currently have open in your browser. If you do this, your work will be preserved in a repository, but there won't be a link between your existing codespace and the new repository. However, you can navigate to the new repository and create a codespace from there, and this codespace will be connected to the repository.

1. In the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces** to take you to the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces).

2. Next to the unpublished codespace, click the ellipsis (**...**), then select **Publish to a new repository**.

   ![Screenshot of the dropdown menu for a codespace, showing the "Publish to a new repository" option.](/assets/images/help/codespaces/publish-to-new-repository.png)

3. Choose a name for your new repository, set it as **Public** or **Private**, and click **Create repository**.

   ![Screenshot of the "Publish to a new repository" dropdown, with the "Name" field, "Public" and "Private" options, and "Create repository" button.](/assets/images/help/codespaces/template-new-repository-settings.png)

4. Optionally, to view the new repository, click **See repository**.

## Further reading

* [Creating a codespace for a repository](/en/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository)
* [Understanding the codespace lifecycle](/en/codespaces/about-codespaces/understanding-the-codespace-lifecycle)
* [Using source control in your codespace](/en/codespaces/developing-in-a-codespace/using-source-control-in-your-codespace)