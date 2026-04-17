# Project (classic) permissions for an organization

Organization owners and people with project (classic) admin permissions can customize who has read, write, and admin permissions to your organization's projects (classic).

> \[!NOTE]
>
> * Projects, the all-new projects experience, is now available. For more information about Projects, see [About Projects](/en/enterprise-server@3.16/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).
> * You can only create a new project (classic) for an organization, repository,  or user that already has at least one project (classic).  If you're unable to create a project (classic), create a project instead.

## Permissions overview

There are three levels of permissions to a project (classic) for people and teams:

* **Read**, which gives people permission to view a project (classic).
* **Write**, which gives people permission to view a project (classic), link repositories to a project (classic), and interact with a project (classic). For more information, see [Linking a repository to a project (classic)](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/linking-a-repository-to-a-project-board).
* **Admin**, which gives people permission to view a project (classic), interact with a project (classic), manage project (classic) settings, and manage other people's access to the project (classic).

Organization owners and people with admin permissions can give a person access to an organization project (classic) individually, as an outside collaborator or organization member, or through their membership in a team or organization. An outside collaborator is someone who is not an organization member but given permissions to collaborate in your organization.

Organization owners and people with admin permissions to a project (classic) can also:

* Set default project (classic) permissions for all organization members.
* Manage access to the project (classic) for organization members, teams, and outside collaborators. For more information, see [Managing team access to an organization project (classic)](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/managing-team-access-to-an-organization-project-board), [Managing an individual's access to an organization project (classic)](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/managing-an-individuals-access-to-an-organization-project-board), or [Managing access to a project (classic) for organization members](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/managing-access-to-a-project-board-for-organization-members).
* Manage project (classic) visibility. For more information, see [Managing access to a project (classic) for organization members](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/managing-access-to-a-project-board-for-organization-members).

## Cascading permissions for projects (classic)

If a person has multiple avenues of access to an organization project (classic) (individually, through a team, or as an organization member), the highest project (classic) permission level overrides lower permission levels.

For example, if an organization owner has given all organization members read permissions to a project (classic), and a project (classic) admin gives an organization member write permissions to that board as an individual collaborator, that person would have write permissions to the project (classic).

## Project (classic) visibility

Organization owners can control the ability of organization members to create public projects and projects (classic), or change the visibility of existing projects and projects (classic) to public. For more information, see [Allowing project visibility changes in your organization](/en/enterprise-server@3.16/organizations/managing-organization-settings/allowing-project-visibility-changes-in-your-organization).

By default, user-owned and organization-wide projects (classic) are private and only visible to people with read, write, or admin permissions to the project (classic). A public project (classic) is visible to anyone with the project (classic)'s URL. Repository-level projects (classic) share the visibility of their repository. That is, a private repository will have a private project, and this visibility cannot be changed. You can change the project (classic)'s visibility from private to public and back again. For more information, see [Changing project (classic) visibility](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/changing-project-board-visibility).

## Further reading

* [Changing project (classic) visibility](/en/enterprise-server@3.16/issues/organizing-your-work-with-project-boards/managing-project-boards/changing-project-board-visibility)
* [Managing an individual's access to an organization project (classic)](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/managing-an-individuals-access-to-an-organization-project-board)
* [Managing team access to an organization project (classic)](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/managing-team-access-to-an-organization-project-board)
* [Managing access to a project (classic) for organization members](/en/enterprise-server@3.16/organizations/managing-access-to-your-organizations-project-boards/managing-access-to-a-project-board-for-organization-members)