# Creating an issue

Issues can be created in a variety of ways, so you can choose the most convenient method for your workflow.

Issues can be used to keep track of bugs, enhancements, or other requests. For more information, see [About issues](/en/issues/tracking-your-work-with-issues/about-issues).

Repository administrators can disable issues for a repository. For more information, see [Disabling issues](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/disabling-issues).

## Creating an issue from a repository

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Issues," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-issues-global-nav-update.png)
3. Click **New issue**.
4. If your repository uses issue templates, next to the type of issue you'd like to open, click **Get started**.

   If the type of issue you'd like to open isn't included in the available options, click **Open a blank issue**.

   ![Screenshot of the template chooser for an issue. Below the template choices, a link, labeled "Open a blank issue," is outlined in dark orange.](/assets/images/help/issues/blank-issue-link.png)
5. In the "Title" field, type a title for your issue.
6. In the comment body field, type a description of your issue.
   To cross-reference a related discussion, paste the discussion's URL into the issue description.
7. If you're a project maintainer, you can [assign the issue to someone](/en/issues/tracking-your-work-with-issues/assigning-issues-and-pull-requests-to-other-github-users), [add it to a project](/en/issues/planning-and-tracking-with-projects/managing-items-in-your-project/adding-items-to-your-project#assigning-a-project-from-within-an-issue-or-pull-request), [associate it with a milestone](/en/issues/using-labels-and-milestones-to-track-work/associating-milestones-with-issues-and-pull-requests), [set the issue type](/en/issues/tracking-your-work-with-issues/using-issues/editing-an-issue#adding-or-changing-the-issue-type), or [apply a label](/en/issues/using-labels-and-milestones-to-track-work/managing-labels).
8. When you're finished, click **Submit new issue**.

## Creating an issue with GitHub CLI

GitHub CLI is an open source tool for using GitHub from your computer's command line. When you're working from the command line, you can use the GitHub CLI to save time and avoid switching context. To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

To create an issue, use the `gh issue create` subcommand. To skip the interactive prompts, include the `--body` and the `--title` flags.

```shell
gh issue create --title "My new issue" --body "Here are more details."
```

You can also specify assignees, labels, milestones, and projects.

```shell
gh issue create --title "My new issue" --body "Here are more details." --assignee @me,monalisa --label "bug,help wanted" --project onboarding --milestone "learning codebase"
```

## Creating an issue from a comment

You can open a new issue from a comment in an issue or pull request. When you open an issue from a comment, the issue contains a snippet showing where the comment was originally posted.

1. Navigate to the comment that you would like to open an issue from.

2. In that comment, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Show options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>.

   ![Screenshot of a comment on a pull request. The kebab button is outlined in dark orange.](/assets/images/help/pull_requests/kebab-in-pull-request-review-comment.png)

3. Click **Reference in new issue**.

4. Use the "Repository" dropdown menu, and select the repository you want to open the issue in.

5. Type a descriptive title and body for the issue.

6. Click **Create issue**.

7. If you're a project maintainer, you can [assign the issue to someone](/en/issues/tracking-your-work-with-issues/assigning-issues-and-pull-requests-to-other-github-users), [add it to a project](/en/issues/planning-and-tracking-with-projects/managing-items-in-your-project/adding-items-to-your-project#assigning-a-project-from-within-an-issue-or-pull-request), [associate it with a milestone](/en/issues/using-labels-and-milestones-to-track-work/associating-milestones-with-issues-and-pull-requests), [set the issue type](/en/issues/tracking-your-work-with-issues/using-issues/editing-an-issue#adding-or-changing-the-issue-type), or [apply a label](/en/issues/using-labels-and-milestones-to-track-work/managing-labels).

8. When you're finished, click **Submit new issue**.

## Creating an issue from code

You can open a new issue from a specific line or lines of code in a file or pull request. When you open an issue from code, the issue contains a snippet showing the line or range of code you chose. You can only open an issue in the same repository where the code is stored.

1. On GitHub, navigate to the main page of the repository.
2. Locate the code you want to reference in an issue:
   * To open an issue about code in a file, navigate to the file.
   * To open an issue about code in a pull request, navigate to the pull request and click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-diff" aria-label="diff" role="img"><path d="M8.75 1.75V5H12a.75.75 0 0 1 0 1.5H8.75v3.25a.75.75 0 0 1-1.5 0V6.5H4A.75.75 0 0 1 4 5h3.25V1.75a.75.75 0 0 1 1.5 0ZM4 13h8a.75.75 0 0 1 0 1.5H4A.75.75 0 0 1 4 13Z"></path></svg> Files changed**. Then, browse to the file that contains the code you want included in your comment, and click **View**.
3. Choose whether to select a single line or a range.

   * To select a single line of code, click the line number to highlight the line.
   * To select a range of code, click the number of the first line in the range to highlight the line of code. Then, hover over the last line of the code range, press <kbd>Shift</kbd>, and click the line number to highlight the range.
4. To the left of the code range, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Code line X options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>. In the dropdown menu, click **Reference in new issue**.

   ![Screenshot of a file, with 8 lines selected. To the left of the first selected line, a button labeled with a kebab icon is outlined in dark orange.](/assets/images/help/repository/open-new-issue-specific-line.png)
5. In the "Title" field, type a title for your issue.
6. In the comment body field, type a description of your issue.
7. If you're a project maintainer, you can [assign the issue to someone](/en/issues/tracking-your-work-with-issues/assigning-issues-and-pull-requests-to-other-github-users), [add it to a project](/en/issues/planning-and-tracking-with-projects/managing-items-in-your-project/adding-items-to-your-project#assigning-a-project-from-within-an-issue-or-pull-request), [associate it with a milestone](/en/issues/using-labels-and-milestones-to-track-work/associating-milestones-with-issues-and-pull-requests), [set the issue type](/en/issues/tracking-your-work-with-issues/using-issues/editing-an-issue#adding-or-changing-the-issue-type), or [apply a label](/en/issues/using-labels-and-milestones-to-track-work/managing-labels).
8. When you're finished, click **Submit new issue**.

## Creating an issue from discussion

People with triage permission to a repository can create an issue from a discussion.

When you create an issue from a discussion, the contents of the discussion post will be automatically included in the issue body, and any labels will be retained. Creating an issue from a discussion does not convert the discussion to an issue or delete the existing discussion. For more information about GitHub Discussions, see [About discussions](/en/discussions/collaborating-with-your-community-using-discussions/about-discussions).

1. Under your repository or organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-comment-discussion" aria-label="comment-discussion" role="img"><path d="M1.75 1h8.5c.966 0 1.75.784 1.75 1.75v5.5A1.75 1.75 0 0 1 10.25 10H7.061l-2.574 2.573A1.458 1.458 0 0 1 2 11.543V10h-.25A1.75 1.75 0 0 1 0 8.25v-5.5C0 1.784.784 1 1.75 1ZM1.5 2.75v5.5c0 .138.112.25.25.25h1a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h3.5a.25.25 0 0 0 .25-.25v-5.5a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25Zm13 2a.25.25 0 0 0-.25-.25h-.5a.75.75 0 0 1 0-1.5h.5c.966 0 1.75.784 1.75 1.75v5.5A1.75 1.75 0 0 1 14.25 12H14v1.543a1.458 1.458 0 0 1-2.487 1.03L9.22 12.28a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215l2.22 2.22v-2.19a.75.75 0 0 1 .75-.75h1a.25.25 0 0 0 .25-.25Z"></path></svg> Discussions**.

   ![Screenshot of the tabs in a GitHub repository. The "Discussions" option is outlined in dark orange.](/assets/images/help/discussions/repository-discussions-tab-global-nav-update.png)

2. In the list of discussions, click the discussion you want to view.

3. In the right sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Create issue from discussion**.

   ![Screenshot of the sidebar in a discussion. The "Create issue from discussion" option is outlined in dark orange.](/assets/images/help/discussions/create-issue-from-discussion.png)

4. In the "Title" field, type a title for your issue.

5. In the comment body field, type a description of your issue.

6. If you're a project maintainer, you can [assign the issue to someone](/en/issues/tracking-your-work-with-issues/assigning-issues-and-pull-requests-to-other-github-users), [add it to a project](/en/issues/planning-and-tracking-with-projects/managing-items-in-your-project/adding-items-to-your-project#assigning-a-project-from-within-an-issue-or-pull-request), [associate it with a milestone](/en/issues/using-labels-and-milestones-to-track-work/associating-milestones-with-issues-and-pull-requests), [set the issue type](/en/issues/tracking-your-work-with-issues/using-issues/editing-an-issue#adding-or-changing-the-issue-type), or [apply a label](/en/issues/using-labels-and-milestones-to-track-work/managing-labels).

7. When you're finished, click **Submit new issue**.

## Creating an issue from a project

You can quickly create issues without leaving your project. When using a view that is grouped by a field, creating an issue in that group will automatically set the new issue's field to the group's value. For example, if you group your view by "Status", when you create an issue in the "Todo" group, the new issue's "Status" will automatically be set to "Todo." For more information about Projects, see [About Projects](/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).

1. Navigate to your project.

2. At the bottom of a table, group of items, or a column in board layout, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus icon" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>.

   ![Screenshot showing the bottom row of a table view. The "+" button is highlighted with an orange outline.](/assets/images/help/projects-v2/omnibar-add.png)

3. Click **Create new issue**.

4. At the top of the "Create new issue" dialog, select the repository where you want the new issue to be created.

   ![Screenshot showing the "Create new issue" dialog.](/assets/images/help/projects-v2/issue-create-form.png)

5. Below the repository dropdown, type a title for the new issue.

6. Optionally, use the fields below the title field to set assignees, labels, and milestones, and add the new issue to other projects.

7. Optionally, type a description for your issue.

8. Optionally, if you want to create more issues, select **Create more** and the dialog will reopen when you create your issue.

9. Click **Create**.

## Creating an issue from a task list item

Within an issue, you can use task lists to break work into smaller tasks and track the full set of work to completion. If a task requires further tracking or discussion, you can convert the task to an issue by hovering over the task and clicking <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="The issue opened icon" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> in the upper-right corner of the task. For more information, see [About tasklists](/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists).

## Creating an issue from a URL query

You can use query parameters to open issues. Query parameters are optional parts of a URL you can customize to share a specific web page view, such as search filter results or an issue template on GitHub. To create your own query parameters, you must match the key and value pair.

> \[!TIP]
> You can also create issue templates that open with default labels, assignees, and an issue title. For more information, see [Using templates to encourage useful issues and pull requests](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests).

You must have the proper permissions for any action to use the equivalent query parameter. For example, you must have permission to add a label to an issue to use the `labels` query parameter. For more information, see [Repository roles for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).

If you create an invalid URL using query parameters, or if you don't have the proper permissions, the URL will return a `404 Not Found` error page. If you create a URL that exceeds the server limit, the URL will return a `414 URI Too Long` error page.

| Query parameter | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `title`         | `https://github.com/octo-org/octo-repo/issues/new?labels=bug&title=New+bug+report` creates an issue with the label "bug" and title "New bug report."                                                                                                                                                                                                                                                                                                                       |
| `body`          | `https://github.com/octo-org/octo-repo/issues/new?title=New+bug+report&body=Describe+the+problem.` creates an issue with the title "New bug report" and the comment "Describe the problem" in the issue body.                                                                                                                                                                                                                                                              |
| `labels`        | `https://github.com/octo-org/octo-repo/issues/new?labels=help+wanted,bug` creates an issue with the labels "help wanted" and "bug".                                                                                                                                                                                                                                                                                                                                        |
| `milestone`     | `https://github.com/octo-org/octo-repo/issues/new?milestone=testing+milestones` creates an issue with the milestone "testing milestones."                                                                                                                                                                                                                                                                                                                                  |
| `assignees`     | `https://github.com/octo-org/octo-repo/issues/new?assignees=octocat` creates an issue and assigns it to @octocat.                                                                                                                                                                                                                                                                                                                                                          |
| `projects`      | `https://github.com/octo-org/octo-repo/issues/new?title=Bug+fix&projects=octo-org/1` creates an issue with the title "Bug fix" and adds it to the organization's project 1.                                                                                                                                                                                                                                                                                                |
| `template`      | `https://github.com/octo-org/octo-repo/issues/new?template=issue_template.md` creates an issue with a template in the issue body. The `template` query parameter works with templates stored in an `ISSUE_TEMPLATE` subdirectory within the root, `docs/` or `.github/` directory in a repository. For more information, see [Using templates to encourage useful issues and pull requests](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests). |

You can also use URL query parameters to fill custom text fields that you have defined in issue form templates. Query parameters for issue form fields can also be passed to the issue template chooser. For more information, see [Syntax for GitHub's form schema](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-githubs-form-schema#keys).

## Creating an issue with Copilot Chat on GitHub

> \[!NOTE]
> This feature is in public preview and subject to change.

Creating issues manually can be repetitive and time-consuming. With Copilot, you can create issues faster by prompting in natural language, or even by uploading a screenshot. Copilot fills out the title, body, labels, assignees, and more, using your repository’s templates and structure. See [Using GitHub Copilot to create or update issues](/en/copilot/using-github-copilot/using-github-copilot-to-create-issues).

## Creating an issue from Copilot Chat in VS Code

You can also create an issue directly from Copilot Chat in VS Code, using the Model Context Protocol (MCP). See [Extending GitHub Copilot Chat with Model Context Protocol (MCP) servers](/en/copilot/customizing-copilot/extending-copilot-chat-with-mcp).

## Further reading

* [Writing on GitHub](/en/get-started/writing-on-github)