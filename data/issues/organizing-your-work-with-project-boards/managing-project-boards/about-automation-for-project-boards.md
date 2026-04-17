# About automation for projects (classic)

You can configure automatic workflows to keep the status of project (classic) cards in sync with the associated issues and pull requests.

> \[!NOTE]
>
> * Projects, the all-new projects experience, is now available. For more information about Projects, see [About Projects](/en/enterprise-server@3.16/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).
> * You can only create a new project (classic) for an organization, repository,  or user that already has at least one project (classic).  If you're unable to create a project (classic), create a project instead.

To set up automatic workflows for a repository project (classic), you must have write access to the repository. Organization owners and members can configure automatic workflows on an organization-wide project (classic). For more information, see [Project (classic) permissions for an organization](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/project-board-permissions-for-an-organization).

You can automate actions based on triggering events for project (classic) columns. This eliminates some of the manual tasks in managing a project (classic). For example, you can configure a "To do" column, where any new issues or pull requests you add to a project (classic) are automatically moved to the configured column. For more information, see [Configuring automation for projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/configuring-automation-for-project-boards).

You can use a project (classic) template to create a project (classic) with automation already configured. For more information, see [About projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/about-project-boards#templates-for-project-boards).

Project (classic) automation can also help teams develop a shared understanding of a project (classic)'s purpose and the team's development process by creating a standard workflow for certain actions.

When you close a project (classic), any workflow automation configured for the project (classic) will pause. If you reopen a project (classic), you have the option to sync automation, which updates the position of the cards on the board according to the automation settings configured for the project. For more information, see [Reopening a closed project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/reopening-a-closed-project-board) or [Closing a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/closing-a-project-board).

## Automation options

| Column preset | Configuration options                                                                                                                                                                                                                                                                                                                                         |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| To do         | <ul><li>Move all newly added issues here</li><li>Move all newly added pull requests here</li><li>Move all reopened issues here</li><li>Move all reopened pull requests here</li></ul>                                                                                                                                                                         |
| In progress   | <ul><li>Move all newly opened pull requests here</li><li>Move all reopened issues here</li><li>Move all reopened pull requests here</li><li>Move all pull requests that meet the base branch's minimum number of required reviews here</li><li>Move all pull requests that no longer meet the base branch's minimum number of required reviews here</li></ul> |
| Done          | <ul><li>Move all closed issues here</li><li>Move all merged pull requests here</li><li>Move all closed, unmerged pull requests here</li></ul>                                                                                                                                                                                                                 |

## Project progress tracking

You can track the progress on your project (classic). Cards in the "To do", "In progress", or "Done" columns count toward the overall project progress. If progress tracking is enabled, a progress bar appears above the project (classic), on the project listing page, in the issue sidebar, and in references to the project on other projects (classic).

For more information, see [Tracking progress on your project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/tracking-work-with-project-boards/tracking-progress-on-your-project-board).

## Further reading

* [Configuring automation for projects (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/configuring-automation-for-project-boards)