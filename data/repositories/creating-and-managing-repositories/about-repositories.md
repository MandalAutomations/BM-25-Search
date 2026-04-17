# About repositories

A repository contains all of your code, your files, and each file's revision history. You can discuss and manage your work within the repository.

## About repositories

A repository is the most basic element of GitHub. It's a place where you can store your code, your files, and each file's revision history. Repositories can have multiple collaborators and can be either public or private.

To create a new repository, go to <https://github.com/new>. For instructions, see [Quickstart for repositories](/en/repositories/creating-and-managing-repositories/quickstart-for-repositories).

## Repository terminology

Before getting started with repositories, learn these important terms.

<div class="ghd-tool rowheaders">

| Term         | Definition                                                                                                                                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Branch       | A parallel version of your code that is contained within the repository, but does not affect the primary or main branch.                                     |
| Clone        | To download a full copy of a repository's data from GitHub.com, including all versions of every file and folder.                                             |
| Fork         | A new repository that shares code and visibility settings with the original "upstream" repository.                                                           |
| Merge        | To take the changes from one branch and apply them to another.                                                                                               |
| Pull request | A request to merge changes from one branch into another.                                                                                                     |
| Remote       | A repository stored on GitHub, not on your computer.                                                                                                         |
| Upstream     | The branch on an original repository that has been forked or cloned. The corresponding branch on the cloned or forked repository is called the "downstream." |

</div>

## About repository ownership

You can own repositories individually, or you can share ownership of repositories with other people in an organization.

In either case, access to repositories is managed by permissions. For more information, see [Permission levels for a personal account repository](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-personal-account-settings/permission-levels-for-a-personal-account-repository) and [Repository roles for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).

## About collaboration

You can use repositories to manage your work and collaborate with others.

* You can use issues to collect user feedback, report software bugs, and organize tasks you'd like to accomplish. For more information, see [About issues](/en/issues/tracking-your-work-with-issues/about-issues).
* You can use GitHub Discussions to ask and answer questions, share information, make announcements, and conduct or participate in conversations about a project. For more information, see [About discussions](/en/discussions/collaborating-with-your-community-using-discussions/about-discussions).
* You can use pull requests to propose changes to a repository. For more information, see [About pull requests](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).
* You can use Projects to organize and prioritize your issues and pull requests. For more information, see [About Projects](/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).

With GitHub Free for personal accounts and organizations, you can work with unlimited collaborators on unlimited public repositories with a full feature set, or unlimited private repositories with a limited feature set. To get advanced tooling for private repositories, you can upgrade to GitHub Pro, GitHub Team, or GitHub Enterprise Cloud. For more information, see [GitHub's plans](/en/get-started/learning-about-github/githubs-plans).

## About repository visibility

You can restrict who has access to a repository by choosing a repository's visibility: public or private.

When you create a repository, you can choose to make the repository public or private. Repositories in organizations that use GitHub Enterprise Cloud and are owned by an enterprise account can also be created with internal visibility. For more information, see [the GitHub Enterprise Cloud documentation](/en/enterprise-cloud@latest/repositories/creating-and-managing-repositories/about-repositories).

* Public repositories are accessible to everyone on the internet.
* Private repositories are only accessible to you, people you explicitly share access with, and, for organization repositories, certain organization members.

### Security considerations for repository visibility

Public repositories expose your codebase to everyone, increasing the risk that attackers might exploit vulnerabilities or access sensitive information. You can mitigate these risks by enabling GitHub security features such as Dependabot, secret scanning, push protection, and code scanning for the repository. Additionally, you should add a security policy (a `SECURITY.md` file) to your repository, that outlines how vulnerabilities should be reported, to ensure that potential threats are addressed efficiently.

Although private repositories restrict access to authorized users, it's still essential to implement strong access controls, multi-factor authentication, and regular audits to mitigate risks.

For more information, see [Quickstart for securing your repository](/en/code-security/getting-started/quickstart-for-securing-your-repository).

Organization owners always have access to every repository created in an organization. For more information, see [Repository roles for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).

People with admin permissions for a repository can change an existing repository's visibility. For more information, see [Setting repository visibility](/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility).

## Next steps

Here are some helpful resources for taking your next steps with repositories.

* [Best practices for repositories](/en/repositories/creating-and-managing-repositories/best-practices-for-repositories): Learn how to use repositories most effectively.
* [Creating a new repository](/en/repositories/creating-and-managing-repositories/creating-a-new-repository): Create a new repository.
* [Creating and deleting branches within your repository](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository): Learn how to create and delete branches within your repository.
* [Creating a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request): Create a pull request to propose and collaborate on changes to a repository.