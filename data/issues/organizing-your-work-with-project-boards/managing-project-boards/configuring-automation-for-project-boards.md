# Configuring automation for projects (classic)

You can set up automatic workflows to move issues and pull requests to a project (classic) column when a specified event occurs.

> \[!NOTE]
>
> * Projects, the all-new projects experience, is now available. For more information about Projects, see [About Projects](/en/enterprise-server@3.16/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).
> * You can only create a new project (classic) for an organization, repository,  or user that already has at least one project (classic).  If you're unable to create a project (classic), create a project instead.

To set up automatic workflows for a repository project (classic), you must have write access to the repository. Organization owners and members can configure automatic workflows on an organization-wide project (classic). For more information, see [About automation for projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/about-automation-for-project-boards).

You can use a project (classic) template to create a project (classic) with automation already configured. For more information, see [About projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/about-project-boards#templates-for-project-boards).

When you close a project (classic), any workflow automation configured for the project (classic) will pause. If you reopen a project (classic), you have the option to sync automation, which updates the position of the cards on the board according to the automation settings configured for the project. For more information, see [Reopening a closed project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/reopening-a-closed-project-board) or [Closing a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/closing-a-project-board).

> \[!TIP]
> To edit columns that already have configured automation, click **Manage** at the bottom of the column.

1. Navigate to the project (classic) you want to automate.
2. In the column you want to automate, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Column menu" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>.
   ![Screenshot showing a column in a project. The menu icon is highlighted with an orange outline.](/assets/images/help/projects/edit-column-button.png)
3. Click **Manage automation**.
4. Using the Preset drop-down menu, select an automation preset.
5. Select the workflow automations you want to configure for the column.
6. Click **Update automation**.

## Further reading

* [About automation for projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/about-automation-for-project-boards)