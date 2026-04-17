# Planning and tracking work for your team or project

The essentials for using GitHub's planning and tracking tools to manage work on a team or project.

## Introduction

You can use GitHub repositories, issues, projects, and other tools to plan and track your work, whether working on an individual project or cross-functional team.

In this guide, you will learn how to create and set up a repository for collaborating with a group of people, create issue templates and forms, open issues and break down work, and establish a project for organizing and tracking issues.

## Creating a repository

When starting a new project, initiative, or feature, the first step is to create a repository. Repositories contain all of your project's files and give you a place to collaborate with others and manage your work. For more information, see [Creating a new repository](/en/repositories/creating-and-managing-repositories/creating-a-new-repository).

You can set up repositories for different purposes based on your needs. The following are some common use cases:

* **Product repositories:** Larger organizations that track their work and goals around specific products may have one or more repositories containing the code and other files. These repositories can also be used for documentation, reporting on product health or future plans for the product.
* **Project repositories:** You can create a repository for an individual project you are working on, or for a project you are collaborating on with others. For an organization that tracks work for short-lived initiatives or projects, such as a consulting firm, there is a need to report on the health of a project and move people between different projects based on skills and needs. Code for the project is often contained in a single repository.
* **Team repositories:** For an organization that groups people into teams, and brings projects to them, such as a dev tools team, code may be scattered across many repositories for the different work they need to track. In this case it may be helpful to have a team-specific repository as one place to track all the work the team is involved in.
* **Personal repositories:** You can create a personal repository to track all your work in one place, plan future tasks, or even add notes or information you want to save. You can also add collaborators if you want to share this information with others.

You can create multiple, separate repositories if you want different access permissions for the source code and for tracking issues and discussions. For more information, see [Creating an issues-only repository](/en/repositories/creating-and-managing-repositories/creating-an-issues-only-repository).

For the following examples in this guide, we will be using an example repository called Project Octocat.

## Communicating repository information

You can create a README.md file for your repository to introduce your team or project and communicate important information about it. A README is often the first item a visitor to your repository will see, so you can also provide information on how users or contributors can get started with the project and how to contact the team. For more information, see [About the repository README file](/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes).

You can also create a CONTRIBUTING.md file specifically to contain guidelines on how users or contributors can contribute and interact with the team or project, such as how to open a bug fix issue or request an improvement. For more information, see [Setting guidelines for repository contributors](/en/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors).

### README example

We can create a README.md to introduce our new project, Project Octocat.

![Screenshot of the README.md file for the octo-org/project-octocat repository, with details about the project and how to contact the team.](/assets/images/help/issues/quickstart-creating-readme.png)

## Creating issue templates

You can use issues to track the different types of work that your cross-functional team or project covers, as well as gather information from those outside of your project. The following are a few common use cases for issues.

* Release tracking: You can use an issue to track the progress for a release or the steps to complete the day of a launch.
* Large initiatives: You can use an issue to track progress on a large initiative or project, which is then linked to the smaller issues.
* Feature requests: Your team or users can create issues to request an improvement to your product or project.
* Bugs: Your team or users can create issues to report a bug.

Depending on the type of repository and project you are working on, you may prioritize certain types of issues over others. Once you have identified the most common issue types for your team, you can create issue templates and forms for your repository. Issue templates and forms allow you to create a standardized list of templates that a contributor can choose from when they open an issue in your repository. For more information, see [Configuring issue templates for your repository](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository).

### Issue template example

Below we are creating an issue template for reporting a bug in Project Octocat.

![Screenshot of the form to create a new issue template. The fields are completed to create a template named "Bug report for Project Octocat."](/assets/images/help/issues/quickstart-creating-issue-template.png)

Now that we created the bug report issue template, you are able to select it when creating a new issue in Project Octocat.

![Screenshot of the "New issue" page for octo-org/project-octocat, with the option to use the "Bug report for Project Octocat" template.](/assets/images/help/issues/quickstart-issue-creation-menu-with-template.png)

## Opening issues and breaking down work

You can organize and track your work by creating issues. For more information, see [Creating an issue](/en/issues/tracking-your-work-with-issues/creating-an-issue).

### Issue example

Here is an example of an issue created for a large initiative, front-end work, in Project Octocat.

![Screenshot of an issue called "Front-end work for Project Octocat." The issue body includes a list of tasks to complete.](/assets/images/help/issues/quickstart-create-large-initiative-issue.png)

### Sub-issues example

You can add sub-issues to an issue to quickly break down larger pieces of work into smaller issues. Sub-issues add support for hierarchies of issues on GitHub by creating relationships between your issues. You can create multiple levels of sub-issues that accurately represent your project by breaking down tasks into exactly the amount of detail that you and your team require. See [Adding sub-issues](/en/issues/tracking-your-work-with-issues/using-issues/adding-sub-issues) and [Browsing sub-issues](/en/issues/tracking-your-work-with-issues/using-issues/browsing-sub-issues).

You can use issue types to classify work in repositories across the organization, such as tasks, bugs, and features. See [Managing issue types in an organization](/en/issues/tracking-your-work-with-issues/using-issues/managing-issue-types-in-an-organization).

![Screenshot of the sub-issues section below the issue description.](/assets/images/help/issues/sub-issue.png)

### Task list example

You can use task lists to break larger issues down into smaller tasks and to track issues as part of a larger goal.  Task lists have additional functionality when added to the body of an issue. You can see the number of tasks completed out of the total at the top of the issue, and if someone closes an issue linked in the task list, the checkbox will automatically be marked as complete. For more information, see [About tasklists](/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists).

Below we have added a task list to our Project Octocat issue, breaking it down into smaller issues.

![Screenshot of an issue called "Front-end work for Project Octocat." The issue body contains a task list, with a checkbox preceding each issue link.](/assets/images/help/issues/quickstart-add-task-list-to-issue.png)

### Label example

Below is an example of a `front-end` label that we created and added to the issue.

![Screenshot of an issue called "Front-end work for Project Octocat." In the right sidebar, in the "Labels" section, the "front-end" label is applied.](/assets/images/help/issues/quickstart-add-label-to-issue.png)

## Showing which issues are blocked by, or blocking, other work

By creating issue dependencies, you can easily see and communicate which issues are blocked by, or blocking, other issues. This helps streamline coordination, prevent bottlenecks and increase transparency across the team. See [Creating issue dependencies](/en/issues/tracking-your-work-with-issues/using-issues/creating-issue-dependencies).

## Understanding new issues

> \[!NOTE] You'll need access to GitHub Copilot. For more information, see [What is GitHub Copilot?](/en/copilot/about-github-copilot/what-is-github-copilot#getting-access-to-copilot).

When working on an unfamiliar or complex issue, GitHub Copilot can help you quickly understand the context, history, and key information, so you can get started faster and with more confidence.

### Reviewing the issue

1. Navigate to an issue on GitHub.

2. In the top right of any page on GitHub, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>** icon next to the search bar.

   The GitHub Copilot Chat panel is displayed. To resize the panel, click and drag the top or left edge.

3. If the panel contains a previous conversation you had with Copilot, click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> plus sign icon at the top right of the Copilot panel to start a new conversation.

4. At the bottom of the Copilot chat panel, in the "Ask Copilot" box, type a question and press <kbd>Enter</kbd>. For example, you could enter:

   * `Summarize the main points of this issue`
   * `What’s the goal of this issue?`

Copilot's summary will help you capture the purpose and scope of the work.

### Understanding the history and comments

Issues often contain a history of discussions and decisions that can provide important context. You can use Copilot to summarize these conversations to identify key points, such as proposed solutions or unanswered questions. For example, you might ask Copilot to summarize recent comments or highlight decisions that have already been made. This helps you focus on what’s most relevant and ensures your contributions are aligned with the team’s priorities.

### Clarifying technical terms

Issues often mention technical terms, code, or files that might not be immediately clear. You can use Copilot to get explanations or context for these references. For example, you can ask about the purpose of a file or function, or the meaning of a specific term mentioned in the issue. This helps you understand the details without spending extra time searching through documentation or code.

### Getting suggestions for next steps

Once you understand the context of an issue, Copilot can help you figure out how to move forward. You can ask for suggestions on how to approach the work, like fixing a bug or implementing a new feature. For example, you might ask, “What’s the best way to resolve this issue?” or “How can I start addressing this problem?” Copilot's suggestions can provide useful starting points, helping you plan your work more effectively.

## Making decisions as a team

You can use issues and discussions to communicate and make decisions as a team on planned improvements or priorities for your project. Issues are useful when you create them for discussion of specific details, such as bug or performance reports, planning for the next quarter, or design for a new initiative. Discussions are useful for open-ended brainstorming or feedback, outside the codebase and across repositories. For more information, see [Communicating on GitHub](/en/get-started/using-github/communicating-on-github#which-discussion-tool-should-i-use).

As a team, you can also communicate updates on day-to-day tasks within issues so that everyone knows the status of work. For example, you can create an issue for a large feature that multiple people are working on, and each team member can add updates with their status or open questions in that issue.

### Issue example with project collaborators

Here is an example of project collaborators giving a status update on their work on the Project Octocat issue.

![Screenshot of an issue called "Front-end work for Project Octocat." Comments from both @codercat and @octocat provide status updates on the work.](/assets/images/help/issues/quickstart-collaborating-on-issue.png)

## Using labels to highlight project goals and status

You can create labels for a repository to categorize issues, pull requests, and discussions. GitHub also provides default labels for every new repository that you can edit or delete. Labels are useful for keeping track of project goals, bugs, types of work, and the status of an issue.

For more information, see [Managing labels](/en/issues/using-labels-and-milestones-to-track-work/managing-labels#creating-a-label).

Once you have created a label in a repository, you can apply it on any issue, pull request or discussion in the repository. You can then filter issues and pull requests by label to find all associated work. For example, find all the front end bugs in your project by filtering for issues with the `front-end` and `bug` labels. For more information, see [Filtering and searching issues and pull requests](/en/issues/tracking-your-work-with-issues/filtering-and-searching-issues-and-pull-requests).

### Label example

Below is an example of a `front-end` label that we created and added to the issue.

![Screenshot of an issue called "Front-end work for Project Octocat." In the right sidebar, in the "Labels" section, the "front-end" label is applied.](/assets/images/help/issues/quickstart-add-label-to-issue.png)

## Adding issues to a project

You can use projects on GitHub to plan and track the work for your team. A project is a customizable spreadsheet that integrates with your issues and pull requests on GitHub, automatically staying up-to-date with the information on GitHub. You can customize the layout by filtering, sorting, and grouping your issues and PRs. To get started with projects, see [Quickstart for Projects](/en/issues/planning-and-tracking-with-projects/learning-about-projects/quickstart-for-projects).

### Project example

Here is the table layout of an example project, populated with the Project Octocat issues we have created.

![Screenshot of the table view of a project, containing a list of issues, with columns for "Title," "Assignees," "Status," "Labels," and "Notes."](/assets/images/help/issues/quickstart-projects-table-view.png)

We can also view the same project as a board.

![Screenshot of the board view of a project, with issues organized into columns for "No Status," "Todo," "In Progress," and "Done."](/assets/images/help/issues/quickstart-projects-board-view.png)

## Next steps

You have now learned about the tools GitHub offers for planning and tracking your work, and made a start in setting up your cross-functional team or project repository! Here are some helpful resources for further customizing your repository and organizing your work.

* [About repositories](/en/repositories/creating-and-managing-repositories/about-repositories) for learning more about creating repositories
* [Learning about Projects](/en/issues/planning-and-tracking-with-projects/learning-about-projects) for learning more about projects
* [Changing the layout of a view](/en/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/changing-the-layout-of-a-view) for learning how to customize views for projects
* [Tracking your work with issues](/en/issues/tracking-your-work-with-issues) for learning more about different ways to create and manage issues
* [About issue and pull request templates](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/about-issue-and-pull-request-templates) for learning more about issue templates
* [Managing issue types in an organization](/en/issues/tracking-your-work-with-issues/using-issues/managing-issue-types-in-an-organization) for managing issue types
* [Managing labels](/en/issues/using-labels-and-milestones-to-track-work/managing-labels) for learning how to create, edit and delete labels
* [Adding sub-issues](/en/issues/tracking-your-work-with-issues/using-issues/adding-sub-issues) for learning about adding sub-issues
* [About tasklists](/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists) for learning more about task lists