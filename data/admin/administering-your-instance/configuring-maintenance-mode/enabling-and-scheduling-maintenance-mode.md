# Enabling and scheduling maintenance mode

Some standard maintenance procedures, such as upgrading GitHub.com or restoring backups, require the instance to be taken offline for normal use.

## About maintenance mode

Some types of operations require that you take your GitHub Enterprise Server instance offline and put it into maintenance mode:

* Upgrading to a new version of GitHub Enterprise Server
* Increasing CPU, memory, or storage resources allocated to the virtual machine
* Migrating data from one virtual machine to another
* Restoring data from a GitHub Enterprise Server Backup Utilities snapshot
* Troubleshooting certain types of critical application issues

We recommend that you schedule a maintenance window for at least 30 minutes in the future to give users time to prepare. When a maintenance window is scheduled, all users will see a banner when accessing the site.

When the instance is in maintenance mode, all normal HTTP and Git access is refused. This includes web and API requests, for which the appliance responds with status code `503` (Service Unavailable). Git fetch, clone, and push operations are also rejected with an error message indicating that the site is temporarily unavailable. GitHub Actions jobs will not be executed. Visiting the site in a browser results in a maintenance page.

You can perform initial validation of your maintenance operation by configuring an IP exception list to allow access to your GitHub Enterprise Server instance from only the IP addresses and ranges provided. Attempts to access your GitHub Enterprise Server instance from IP addresses not specified on the IP exception list will receive a response consistent with those sent when the instance is in maintenance mode.

## Enabling maintenance mode immediately or scheduling a maintenance window for a later time

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
4. In the top navigation bar, click **Maintenance**.

   ![Screenshot of the header of the Management Console. A tab, labeled "Maintenance", is highlighted with an orange outline.](/assets/images/enterprise/management-console/maintenance-tab.png)
5. Under "Enable and schedule", select **Enable maintenance mode**, then decide whether to enable maintenance mode immediately or to schedule a maintenance window for a future time.
   * To enable maintenance mode immediately, select the dropdown menu and click **now**.
   * To schedule a maintenance window for a future time, select the dropdown menu and click a start time.
6. Optionally, to set a custom message for users to see during the maintenance window, in the "Set a maintenance mode message" field, type a message.
7. When you're satisfied with the timing of the window and the optional message, click **Save**. If you selected "now", your instance will be put into maintenance mode immediately.

## Validating changes in maintenance mode using the IP exception list

The IP exception list provides controlled and restricted access to your GitHub Enterprise Server instance, which is ideal for initial validation of server health following a maintenance operation. Once enabled, your GitHub Enterprise Server instance will be taken out of maintenance mode and available only to the configured IP addresses. The maintenance mode checkbox will be updated to reflect the change in state.

If you re-enable maintenance mode, the IP exception list will be disabled and your GitHub Enterprise Server instance will return to maintenance mode. If you just disable the IP exception list, your GitHub Enterprise Server instance will return to normal operation.

You can also use a command-line utility to configure the IP exception list. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-maintenance) and [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
4. In the top navigation bar, click **Maintenance**, then confirm maintenance mode is already enabled.

   ![Screenshot of the header of the Management Console. A tab, labeled "Maintenance", is highlighted with an orange outline.](/assets/images/enterprise/management-console/maintenance-tab.png)
5. Under "Enable and configure IP exception list", select **Enable IP exception list**.
6. To the right of the checkbox for enabling the list, type a valid list of space-separated IP addresses or CIDR blocks that should be allowed to access your GitHub Enterprise Server instance.
7. Optionally, to set a custom message for users to see during the maintenance window, in the "Set a maintenance mode message" field, type a message.
8. Click **Save**.

## Managing maintenance mode using the REST API

You can manage maintenance mode on your GitHub Enterprise Server instance using the REST API. For more information, see [REST API endpoints for managing GitHub Enterprise Server](/en/enterprise-server@3.20/rest/enterprise-admin/manage-ghes#get-the-status-of-maintenance-mode).

## Managing maintenance mode using the GitHub CLI

You can manage maintenance mode on your GitHub Enterprise Server instance using the GitHub CLI `gh es` extension. For more information, see the GH ES CLI usage documentation for [`gh es maintenance set`](https://github.com/github/gh-es/blob/main/USAGE.md#gh-es-maintenance-set) and [`gh es maintenance get`](https://github.com/github/gh-es/blob/main/USAGE.md#gh-es-maintenance-get).

For more information, see [Administering your instance using the GitHub CLI](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/administering-your-instance-using-the-github-cli).

## Managing maintenance mode using SSH

If you have SSH access, you can use the `ghe-maintenance` command line utility to can set or unset maintenance mode for a GitHub Enterprise Server instance with one node, or multiple nodes in a high-availability configuration. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/accessing-the-administrative-shell-ssh) and [Command-line utilities](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/command-line-utilities#ghe-maintenance).

## Managing maintenance mode for a cluster using SSH

If you have SSH access to your GitHub Enterprise Server instance, you can use the `ghe-cluster-maintenance` command line utility to set or unset maintenance mode for every node in a cluster. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/accessing-the-administrative-shell-ssh) and [Command-line utilities](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/command-line-utilities#ghe-cluster-maintenance).

```shell
$ ghe-cluster-maintenance -h
# Shows options
$ ghe-cluster-maintenance -q
# Queries the current mode
$ ghe-cluster-maintenance -s
# Sets maintenance mode
$ ghe-cluster-maintenance -s "MESSAGE"
# Sets maintenance mode with a custom message
$ ghe-cluster-maintenance -m "MESSAGE"
# Updates the custom message
$ ghe-cluster-maintenance -u
# Unsets maintenance mode
```