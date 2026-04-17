# About projects (classic)

Projects (classic) on GitHub help you organize and prioritize your work.  You can create projects (classic) for specific feature work, comprehensive roadmaps, or even release checklists. With projects (classic), you have the flexibility to create customized workflows that suit your needs.

> \[!NOTE]
>
> * Projects, the all-new projects experience, is now available. For more information about Projects, see [About Projects](/en/enterprise-server@3.16/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).
> * You can only create a new project (classic) for an organization, repository,  or user that already has at least one project (classic).  If you're unable to create a project (classic), create a project instead.

Projects (classic) are made up of issues, pull requests, and notes that are categorized as cards in columns of your choosing. You can drag and drop or use keyboard shortcuts to reorder cards within a column, move cards from column to column, and change the order of columns.

Project (classic) cards contain relevant metadata for issues and pull requests, like labels, assignees, the status, and who opened it. You can view and make lightweight edits to issues and pull requests within your project (classic) by clicking on the issue or pull request's title.

You can create notes within columns to serve as task reminders, references to issues and pull requests from any repository, or to add information related to the project (classic). You can create a reference card for another project (classic) by adding a link to a note. If the note isn't sufficient for your needs, you can convert it to an issue. For more information on converting notes to issues, see [Adding notes to a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/tracking-work-with-project-boards/adding-notes-to-a-project-board).

Types of projects (classic):

* **User-owned project (classic)** can contain issues and pull requests from any personal repository.
* **Organization-wide project (classic)** can contain issues and pull requests from any repository that belongs to an organization. You can link up to twenty-five repositories to your organization or user-owned project (classic). Linking repositories makes it easier to add issues and pull requests from those repositories to your project (classic) using **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add cards** or from the issue or pull requests sidebar. For more information, see [Linking a repository to a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/linking-a-repository-to-a-project-board).
* **Repository project (classic)** are scoped to issues and pull requests within a single repository. They can also include notes that reference issues and pull requests in other repositories.

## Creating and viewing projects (classic)

To create a project (classic) for your organization, you must be an organization member. Organization owners and people with project (classic) admin permissions can customize access to the project (classic).

Organization owners can control the ability of organization members to create public projects and projects (classic), or change the visibility of existing projects and projects (classic) to public. For more information, see [Allowing project visibility changes in your organization](/en/enterprise-server@3.16/organizations/managing-organization-settings/allowing-project-visibility-changes-in-your-organization).

If an organization-owned project (classic) includes issues or pull requests from a repository that you don't have permission to view, the card will be redacted. For more information, see [Project (classic) permissions for an organization](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/project-board-permissions-for-an-organization).

The activity view shows the project (classic)'s recent history, such as cards someone created or moved between columns. To access the activity view, click **Menu** and scroll down.

To find specific cards on a project (classic) or view a subset of the cards, you can filter project (classic) cards. For more information, see [Filtering cards on a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/tracking-work-with-project-boards/filtering-cards-on-a-project-board).

To simplify your workflow and keep completed tasks off your project (classic), you can archive cards. For more information, see [Archiving cards on a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/tracking-work-with-project-boards/archiving-cards-on-a-project-board).

If you've completed all of your project (classic) tasks or no longer need to use your project (classic), you can close the project (classic). For more information, see [Closing a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/closing-a-project-board).

You can also [disable projects (classic) in a repository](/en/enterprise-server@3.16/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/disabling-project-boards-in-a-repository) or [disable projects (classic) in your organization](/en/enterprise-server@3.16/organizations/managing-organization-settings/disabling-project-boards-in-your-organization), if you prefer to track your work in a different way.

You can use GitHub's API to import a project (classic). For more information, see [Mutations](/en/enterprise-server@3.16/graphql/reference/mutations#importproject).

## Templates for projects (classic)

You can use templates to quickly set up a new project (classic). When you use a template to create a project (classic), your new board will include columns as well as cards with tips for using projects (classic). You can also choose a template with automation already configured.

| Template                     | Description                                                                                                                    |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Basic kanban                 | Track your tasks with To do, In progress, and Done columns                                                                     |
| Automated kanban             | Cards automatically move between To do, In progress, and Done columns                                                          |
| Automated kanban with review | Cards automatically move between To do, In progress, and Done columns, with additional triggers for pull request review status |
| Bug triage                   | Triage and prioritize bugs with To do, High priority, Low priority, and Closed columns                                         |

For more information on automation for projects (classic), see [About automation for projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/about-automation-for-project-boards).

## Further reading- [Creating a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/creating-a-project-board)

* [Editing a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/editing-a-project-board)
* [Adding issues and pull requests to a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/tracking-work-with-project-boards/adding-issues-and-pull-requests-to-a-project-board)
* [Project (classic) permissions for an organization](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/project-board-permissions-for-an-organization)
* [Keyboard shortcuts](/en/enterprise-server@3.16/get-started/accessibility/keyboard-shortcuts#project-boards)