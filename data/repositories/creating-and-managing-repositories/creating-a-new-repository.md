# Creating a new repository

You can create a new repository on your personal account or any organization where you have sufficient permissions.

> \[!TIP]
> Owners can restrict repository creation permissions in an organization. For more information, see [Restricting repository creation in your organization](/en/organizations/managing-organization-settings/restricting-repository-creation-in-your-organization).

> \[!TIP]
> You can also create a repository using the GitHub CLI. For more information, see [`gh repo create`](https://cli.github.com/manual/gh_repo_create) in the GitHub CLI documentation.

## Creating a new repository from the web UI

1. In the upper-right corner of any page, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Create something new" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>, then click **New repository**.

   ![Screenshot of a GitHub dropdown menu showing options to create new items. The menu item "New repository" is outlined in dark orange.](/assets/images/help/repository/repo-create-global-nav-update.png)

2. Optionally, to create a repository with the directory structure and files of an existing repository, select the **Choose a template** dropdown menu and click a template repository. You'll see template repositories that are owned by you and organizations you're a member of or that you've used before. For more information, see [Creating a repository from a template](/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template).

3. Optionally, if you chose to use a template, to include the directory structure and files from all branches in the template, and not just the default branch, select **Include all branches**.

4. Use the **Owner** dropdown menu to select the account you want to own the repository.
   ![Screenshot of the owner menu for a new GitHub repository. The menu shows two options, octocat and github.](/assets/images/help/repository/create-repository-owner.png)

5. Type a name for your repository (maximum 100 characters), and an optional description.

   ![Screenshot of a the first step in creating a repository. The "Repository name" field contains the text "hello-world" and is outlined in orange.](/assets/images/help/repository/create-repository-name.png)

6. Choose a repository visibility. For more information, see [About repositories](/en/repositories/creating-and-managing-repositories/about-repositories#about-repository-visibility).

7. If you're not using a template, there are a number of optional items you can pre-populate your repository with. If you're importing an existing repository to GitHub, don't choose any of these options, as you may introduce a merge conflict. You can add or create new files using the user interface or choose to add new files using the command line later. For more information, see [Importing an external Git repository using the command line](/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/importing-an-external-git-repository-using-the-command-line), [Adding a file to a repository](/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository#adding-a-file-to-a-repository-using-the-command-line), and [Addressing merge conflicts](/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts).
   * You can create a README, which is a document describing your project. For more information, see [About the repository README file](/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes).
   * You can create a *.gitignore* file, which is a set of ignore rules. For more information, see [Ignoring files](/en/get-started/git-basics/ignoring-files).
   * You can choose to add a software license for your project. For more information, see [Licensing a repository](/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository).

8. Optionally, if the personal account or organization in which you're creating uses any GitHub Apps from GitHub Marketplace, select any apps you'd like to use in the repository.

9. Optionally, if you have access to Copilot cloud agent, enter a prompt for Copilot to use to populate your repository. After the repository is created, Copilot will open a draft pull request, write the code requested, then request review from you. For more information, see [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent).

10. Click **Create repository**.

11. At the bottom of the resulting Quick Setup page, under "Import code from an old repository", you can choose to import a project to your new repository. To do so, click **Import code**.

## Creating a new repository from a URL query

You can use query parameters to pre-fill form fields when creating a new repository. Query parameters are optional parts of a URL you can customize to share a specific web page view, such as search filter results or an issue template on GitHub. To specify values for the predefined query parameters, you must match the key and value pair.

Pre-filling form fields with a URL query may be useful if you often want to create repositories with the same default settings. For example, a teacher may want each student in a class to create a repository in their personal account with the same name, description and visibility. Using a URL query, the teacher can create a link that pre-fills the repository name, description and visibility fields and share it with the whole class.

You must have the proper permissions for any action to use the equivalent query parameter. For example, you must have permission to create a repository in an organization to specify the organization as the repository owner in a query parameter. For more information, see [Repository roles for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).

If you create an invalid URL using query parameters, or if you don’t have the proper permissions, the invalid query parameters will be ignored and the rest of the URL will function as normal. If you create a URL that exceeds the server limit, the URL will return a `414 URI Too Long` error page.

| Query parameter                      | Example                                                                                                                                                                                              | Valid values                                                                                                                 |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `name`                               | `https://github.com/new?name=test-repo&owner=avocado-corp` creates a repository called "test-repo" owned by the "avocado-corp" organization.                                                         | Any valid repository name. Spaces must be replaced with `+` or `%20`.                                                        |
| `description`                        | `https://github.com/new?description=An+exciting+repository&visibility=private&owner=octocat` creates a repo with the description "An exciting repository" with private visibility owned by @octocat. | Any string. Spaces must be replaced with `+` or `%20`.                                                                       |
| `visibility`                         | `https://github.com/new?visibility=private` creates a repository with private visibility.                                                                                                            | `public`<br> `private`<br>                                                                                                   |
| `owner`                              | `https://github.com/new?owner=avocado-corp&visibility=public` creates a public repository owned by the "avocado-corp" organization.                                                                  | Any valid organization name or username. Alternatively, while signed in use `@me` to specify your user account as the owner. |
| `template_owner` and `template_name` | `https://github.com/new?owner=avocado-corp&template_owner=avocado-corp&template_name=octo-repo` creates a repository owned by the "avocado-corp" using the avocado-corp's template "octo-repo".      | The username of the template owner and the name of the repository template.                                                  |

## Creating a new repository from Copilot Chat

You can create a new repository from Copilot Chat in Visual Studio Code with the Model Context Protocol (MCP). For more information, see [Extending GitHub Copilot Chat with Model Context Protocol (MCP) servers](/en/copilot/customizing-copilot/extending-copilot-chat-with-mcp).

## Further reading

* [Quickstart for securing your repository](/en/code-security/getting-started/quickstart-for-securing-your-repository)
* [Managing user access to your organization's repositories](/en/organizations/managing-user-access-to-your-organizations-repositories)
* [Open Source Guides](https://opensource.guide/)
* [GitHub Skills](https://skills.github.com/)