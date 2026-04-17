# Troubleshooting team membership with identity provider groups

If you manage team membership using groups on your identity provider (IdP), but team membership is not in sync, you can troubleshoot the problem.

## About management of team membership with IdP groups

With Enterprise Managed Users, you can manage team and organization membership within your enterprise through your IdP by connecting teams on GitHub with groups on your IdP. You can review a list of teams that you've synchronized to IdP groups from your enterprise's settings. For more information, see [Managing team memberships with identity provider groups](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/managing-team-memberships-with-identity-provider-groups#viewing-idp-groups-group-membership-and-connected-teams).

GitHub also runs a reconciliation job once per day, which synchronizes team membership with IdP group membership that is stored on GitHub, based on information previously sent from the IdP via SCIM. If this job finds that a user is a member of an IdP group in the enterprise, but they are not a member of the mapped team or its organization, the job will attempt to add the user to the organization and team.

If GitHub is unable to synchronize team membership with a group on your IdP, you can view an error message and troubleshoot the problem.

## Viewing errors for team synchronization with an IdP group

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. In the list of enterprises, click the enterprise you want to view.
3. To review a list of IdP groups, in the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key" aria-label="key" role="img"><path d="M10.5 0a5.499 5.499 0 1 1-1.288 10.848l-.932.932a.749.749 0 0 1-.53.22H7v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22H5v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22h-2A1.75 1.75 0 0 1 0 14.25v-2c0-.199.079-.389.22-.53l4.932-4.932A5.5 5.5 0 0 1 10.5 0Zm-4 5.5c-.001.431.069.86.205 1.269a.75.75 0 0 1-.181.768L1.5 12.56v1.69c0 .138.112.25.25.25h1.69l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l1.023-1.025a.75.75 0 0 1 .768-.18A4 4 0 1 0 6.5 5.5ZM11 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg> Identity provider**.
4. Under **Identity provider**, click **Groups**.
5. If synchronization for a group is experiencing problems, you'll see a message that reads "Some groups are failing to synchronize to teams. Check that you have available licenses."
6. In the list of IdP groups, click the group you'd like to review.
7. To review the synchronization error for the group, under the name of the group, click **Teams**.

   If a team is unable to sync membership with a group on your IdP, you'll see a description of the problem under the team's name and membership count.

### Error: "Out of sync due to insufficient licenses"

GitHub stores IdP group membership data for Enterprise Managed Users at the enterprise level. This data is populated and updated through Group SCIM API calls from your identity provider (IdP).

For IdP groups that are mapped to teams, GitHub runs a **daily reconciliation job** to synchronize team membership with the stored enterprise-level IdP group data. The reconciliation also runs whenever a Group SCIM API call updates group membership, or when an admin links or unlinks a team to a stored group on GitHub.

If your enterprise does not have enough licenses available, GitHub may be unable to complete this synchronization. When this occurs, you’ll see the message:

> "Out of sync due to insufficient licenses"

As a result, the affected team or organization may be missing members.

![Screenshot of the IdP group page. A warning that a team is out of sync due to insufficient licenses is outlined in dark orange.](/assets/images/help/enterprises/emu-group-team-not-synced-missing-licenses.png)

To investigate this issue, review your enterprise's total available licenses, as well as detailed information about which users are consuming licenses and why. For more information, see [People who consume a license in an organization](/en/enterprise-cloud@latest/billing/reference/github-license-users#organizations-on-github-enterprise-cloud) and [Viewing usage for your GitHub Enterprise plan](/en/enterprise-cloud@latest/billing/managing-your-license-for-github-enterprise/viewing-license-usage-for-github-enterprise).

#### Resolving the issue

To allow synchronization to complete successfully, make additional enterprise licenses available using one of the following approaches:

* **Free up existing licenses**
  * Identify which users are consuming licenses and whether they still need access.
  * Remove users from organizations or IdP groups as needed, depending on how you manage organization and team membership (see [Viewing people in your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/viewing-people-in-your-enterprise#filtering-by-member-type-in-an-enterprise-with-managed-users)):
    * If you manage your organization's membership via IdP groups, remove users from the relevant group(s).
  * Monitor these enterprise audit log events to track SCIM API calls that update group membership or managed user accounts (see [Audit log events for your enterprise](/en/enterprise-cloud@latest/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/audit-log-events-for-your-enterprise):
    * `external_group.scim_api_failure` / `external_group.scim_api_success`
    * `external_identity.scim_api_failure` / `external_identity.scim_api_success`

* **Purchase additional licenses**
  * If all current users require access, purchase more licenses for your enterprise. For more information, see [Managing user licenses for an organization or enterprise](/en/enterprise-cloud@latest/billing/how-tos/manage-plan-and-licenses/manage-user-licenses#enterprises-on-github-enterprise-cloud).

### Error: "Out of sync"

If synchronization of team membership with a group on your IdP fails due to a problem other than licensing, you'll see a message that reads "Out of sync".

![Screenshot of the IdP group page. A warning that a team is out of sync is outlined in dark orange.](/assets/images/help/enterprises/emu-group-team-not-synced-generic.png)

GitHub will try to resolve this problem automatically during the next sync, which occurs at least once daily. You may be able to resolve the problem by unlinking the impacted team from the IdP group and then linking it to the same group again. For more information, see [Managing team memberships with identity provider groups](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/managing-team-memberships-with-identity-provider-groups#managing-the-connection-between-an-existing-team-and-an-idp-group).

If the problem persists, contact [GitHub Enterprise Support](https://support.github.com) and provide details about the organization, team, and the IdP group you're experiencing problems with.