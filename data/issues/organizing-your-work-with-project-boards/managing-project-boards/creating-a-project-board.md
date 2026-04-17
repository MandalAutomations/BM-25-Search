# Creating a project (classic)

Projects (classic) can be used to create customized workflows to suit your needs, like tracking and prioritizing specific feature work, comprehensive roadmaps, or even release checklists.

> \[!NOTE]
>
> * Projects, the all-new projects experience, is now available. For more information about Projects, see [About Projects](/en/enterprise-server@3.16/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).
> * You can only create a new project (classic) for an organization, repository,  or user that already has at least one project (classic).  If you're unable to create a project (classic), create a project instead.

You can use a project (classic) template to create a project (classic) with automation already configured. For more information, see [About projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/about-project-boards#templates-for-project-boards).

You can link up to twenty-five repositories to your organization or user-owned project (classic). Linking repositories makes it easier to add issues and pull requests from those repositories to your project (classic) using **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add cards** or from the issue or pull requests sidebar. For more information, see [Linking a repository to a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/linking-a-repository-to-a-project-board).

Once you've created your project (classic), you can add issues, pull requests, and notes to it. For more information, see [Adding issues and pull requests to a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/tracking-work-with-project-boards/adding-issues-and-pull-requests-to-a-project-board) and [Adding notes to a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/tracking-work-with-project-boards/adding-notes-to-a-project-board).

You can also configure workflow automations to keep your project (classic) in sync with the status of issues and pull requests. For more information, see [About automation for projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/about-automation-for-project-boards).

You can use GitHub's API to import a project (classic). For more information, see [Mutations](/en/enterprise-server@3.16/graphql/reference/mutations#importproject).

## Creating a user-owned project (classic)

1. In the top right corner of GitHub, click your profile picture, then click **Your profile**.

   ![Screenshot of the dropdown menu under @octocat's profile picture. "Your profile" is outlined in dark orange.](/assets/images/help/profile/profile-button-avatar-menu-global-nav-update.png)

2. On the top of your profile page, in the main navigation, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-project" aria-label="project" role="img"><path d="M1.75 0h12.5C15.216 0 16 .784 16 1.75v12.5A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0ZM1.5 1.75v12.5c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25ZM11.75 3a.75.75 0 0 1 .75.75v7.5a.75.75 0 0 1-1.5 0v-7.5a.75.75 0 0 1 .75-.75Zm-8.25.75a.75.75 0 0 1 1.5 0v5.5a.75.75 0 0 1-1.5 0ZM8 3a.75.75 0 0 1 .75.75v3.5a.75.75 0 0 1-1.5 0v-3.5A.75.75 0 0 1 8 3Z"></path></svg> Projects**.

   ![Screenshot showing profile tabs. The 'Projects' tab is highlighted with an orange outline.](/assets/images/help/projects-v2/tab-projects.png)

3. Click **Projects (classic)**.

4. Click **New Project**.

5. Type a name and description for your project (classic).

6. Optionally, to add a template to your project (classic), use the **Template:** drop-down menu and click a template.

7. Under "Visibility", choose to make your project (classic) public or private.

8. Optionally, under **Linked repositories**, search for a repository you'd like to link to your project (classic).

9. Click **Create project**.

10. On your new project (classic), to add your first column, **Add a column**.

11. Under "Column name", type the name of the column you want to create.

12. Optionally, under "Automation", select an automation preset using the drop-down menu.

13. Select the workflow automations you want to configure for the column.

14. Click **Create column**.

15. Add columns to best suit your workflow.

> \[!TIP]
> To edit or remove a column from your project (classic), in the upper-right corner of the column, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="The horizontal kebab icon" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>.

## Creating an organization-wide project (classic)

> \[!NOTE]
> Organization owners can control the ability of organization members to create public projects and projects (classic), or change the visibility of existing projects and projects (classic) to public. For more information, see [Allowing project visibility changes in your organization](/en/enterprise-server@3.16/organizations/managing-organization-settings/allowing-project-visibility-changes-in-your-organization).

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. Click the name of your organization.
3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-table" aria-label="table" role="img"><path d="M0 1.75C0 .784.784 0 1.75 0h12.5C15.216 0 16 .784 16 1.75v12.5A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25ZM6.5 6.5v8h7.75a.25.25 0 0 0 .25-.25V6.5Zm8-1.5V1.75a.25.25 0 0 0-.25-.25H6.5V5Zm-13 1.5v7.75c0 .138.112.25.25.25H5v-8ZM5 5V1.5H1.75a.25.25 0 0 0-.25.25V5Z"></path></svg> Projects**.

   ![Screenshot of the horizontal navigation bar for an organization. A tab, labeled with a table icon and "Projects," is outlined in dark orange.](/assets/images/help/organizations/organization-projects-tab-table.png)
4. Click **Projects (classic)**.
5. Click **New Project**.
6. Type a name and description for your project (classic).
7. Optionally, to add a template to your project (classic), use the **Template:** drop-down menu and click a template.
8. Under "Visibility", choose to make your project (classic) public or private.
9. Optionally, under **Linked repositories**, search for a repository you'd like to link to your project (classic).
10. Click **Create project**.
11. On your new project (classic), to add your first column, **Add a column**.
12. Under "Column name", type the name of the column you want to create.
13. Optionally, under "Automation", select an automation preset using the drop-down menu.
14. Select the workflow automations you want to configure for the column.
15. Click **Create column**.
16. Add columns to best suit your workflow.

> \[!TIP]
> To edit or remove a column from your project (classic), in the upper-right corner of the column, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="The horizontal kebab icon" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>.

## Creating a repository project (classic)

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-project" aria-label="project" role="img"><path d="M1.75 0h12.5C15.216 0 16 .784 16 1.75v12.5A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0ZM1.5 1.75v12.5c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25ZM11.75 3a.75.75 0 0 1 .75.75v7.5a.75.75 0 0 1-1.5 0v-7.5a.75.75 0 0 1 .75-.75Zm-8.25.75a.75.75 0 0 1 1.5 0v5.5a.75.75 0 0 1-1.5 0ZM8 3a.75.75 0 0 1 .75.75v3.5a.75.75 0 0 1-1.5 0v-3.5A.75.75 0 0 1 8 3Z"></path></svg> Projects**.
3. Click **Projects (classic)**.
4. Click **New Project**.
5. Type a name and description for your project (classic).
6. Optionally, to add a template to your project (classic), use the **Template:** drop-down menu and click a template.
7. Click **Create project**.
8. On your new project (classic), to add your first column, **Add a column**.
9. Under "Column name", type the name of the column you want to create.
10. Optionally, under "Automation", select an automation preset using the drop-down menu.
11. Select the workflow automations you want to configure for the column.
12. Click **Create column**.
13. Add columns to best suit your workflow.

> \[!TIP]
> To edit or remove a column from your project (classic), in the upper-right corner of the column, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="The horizontal kebab icon" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>.

## Further reading

* [About projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/about-project-boards)
* [Editing a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/editing-a-project-board)
* [Closing a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/closing-a-project-board)
* [About automation for projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/about-automation-for-project-boards)