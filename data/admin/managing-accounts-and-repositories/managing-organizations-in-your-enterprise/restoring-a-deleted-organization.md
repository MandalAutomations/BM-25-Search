# Restoring a deleted organization

You can partially restore an organization that was previously deleted on GitHub.com.

## About organization restoration

You can use the site admin dashboard to restore an organization that was previously deleted on your GitHub Enterprise Server instance, as long as the audit log Elasticsearch indices contain the data for the `org.delete` event.

Immediately after you restore an organization, the organization will not be exactly the same as it was prior to the deletion. You'll have to manually restore any repositories that were owned by the organization. For more information, see [Restoring a deleted repository](/en/enterprise-server@3.20/admin/user-management/managing-repositories-in-your-enterprise/restoring-a-deleted-repository).

You can also use the audit log to help you manually re-add teams and organization members. For more information, see [Restoring members and teams](#restoring-members-and-teams).

## Restoring an organization

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. Under "Search users, organizations, enterprises, teams, repositories, gists, and applications", search for the organization.

   ![Screenshot of the "Search" page of the "Site admin" settings. The button to search users, labeled "Search," is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/search-for-things.png)

4. Under "Deleted accounts", to the right of the organization you want to restore, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Show more options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> dropdown menu, then click **Recreate**.

## Restoring members and teams

You can use the audit log to find a list of the previous members and teams of the organization, then recreate them manually. For more information about using the audit log, see [Auditing users across your enterprise](/en/enterprise-server@3.20/admin/user-management/managing-users-in-your-enterprise/auditing-users-across-your-enterprise).

In all the search phrases below, replace ORGANIZATION with the name of the organization and TEAM with the name of the team.

### Restoring organization members

1. To find all users who were added to and removed from the organization, search the audit log for `action:org.add_member org:ORGANIZATION` and `action:org.remove_member org:ORGANIZATION`.
2. Manually add to the organization each user that should still be a member. For more information, see [Adding people to your organization](/en/enterprise-server@3.20/organizations/managing-membership-in-your-organization/adding-people-to-your-organization).

### Restoring teams

1. To find each team name, search the audit log for `action:team.create org:ORGANIZATION`.
2. Manually recreate the team. For more information, see [Creating an organization team](/en/enterprise-server@3.20/organizations/organizing-members-into-teams/creating-a-team).
3. To find the members that have been added to each team, search for `action:team.add_member team:"ORGANIZATION/TEAM"`.
4. Manually re-add the team members. For more information, see [Adding organization members to a team](/en/enterprise-server@3.20/organizations/organizing-members-into-teams/adding-organization-members-to-a-team).
5. To find the repositories that the team was granted access to, search for `action:team.add_repository team:"ORGANIZATION/TEAM"`.
6. To find the access level that the team was granted for each repository, search for `action:team.update_repository_permission team:"ORGANIZATION/TEAM"`.
7. Manually give the team access again. For more information, see [Managing team access to an organization repository](/en/enterprise-server@3.20/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/managing-team-access-to-an-organization-repository).