# Managing access to the Management Console

You can increase the security of GitHub.com by creating or deleting Management Console users. As the root site administrator, you can access the Management Console as well as configure Management Console authentication rate limits.

## About access to the Management Console

From the Management Console, you can initialize, configure, and monitor your GitHub Enterprise Server instance. For more information, see [About the Management Console](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console/about-the-management-console).

You can access the Management Console as the root site administrator or a Management Console user. An administrator created the root site administrator password during the initial setup process for your GitHub Enterprise Server instance. For more information about Management Console access, see [Administering your instance from the web UI](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console).

You can also use the `gh es` GitHub CLI extension to manage the root site administrator password, which controls access to the Management Console. For more information, see the [GH ES CLI usage documentation](https://github.com/github/gh-es/blob/main/USAGE.md#gh-es-access-set-password) and [Administering your instance using the GitHub CLI](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/administering-your-instance-using-the-github-cli).

## Types of Management Console accounts

There are two types of user accounts for the Management Console on a GitHub Enterprise Server instance. The root site administrator account authenticates with a password established during the initial setup of your GitHub Enterprise Server instance.

The root site administrator can create additional accounts.

### Root site administrator

Root site administrators have complete control over the Management Console. They can take every action in the Management Console, including creating and deleting Management Console user accounts.

Only the root site administrator can create and delete Management Console user accounts.

### Management Console user

Management Console users can perform most administrative tasks for your GitHub Enterprise Server instance. For heightened security, Management Console users cannot create or delete Management Console user accounts.

Management Console users, sometimes called operators, can perform basic administrative tasks for your GitHub Enterprise Server instance in the Management Console and can add SSH keys to the Management Console to grant administrative access to the instance via SSH.

## Creating or deleting a user account for the Management Console

While signed into the Management Console as the root site administrator, you can create new Management Console user accounts.

1. In the top navigation bar, click **User Management**.
2. Click **Create user**.
3. Fill in the user's name, username, and email address.
4. To finish creating the user account, click **Create**. If email notifications are configured for the instance, the user will automatically receive an invitation email with access instructions for the Management Console. For more information, see [Inviting new Management Console users](#inviting-new-management-console-users).
5. Optionally, to delete a Management Console user account, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-trash" aria-label="The trash symbol" role="img"><path d="M11 1.75V3h2.25a.75.75 0 0 1 0 1.5H2.75a.75.75 0 0 1 0-1.5H5V1.75C5 .784 5.784 0 6.75 0h2.5C10.216 0 11 .784 11 1.75ZM4.496 6.675l.66 6.6a.25.25 0 0 0 .249.225h5.19a.25.25 0 0 0 .249-.225l.66-6.6a.75.75 0 0 1 1.492.149l-.66 6.6A1.748 1.748 0 0 1 10.595 15h-5.19a1.75 1.75 0 0 1-1.741-1.575l-.66-6.6a.75.75 0 1 1 1.492-.15ZM6.5 1.75V3h3V1.75a.25.25 0 0 0-.25-.25h-2.5a.25.25 0 0 0-.25.25Z"></path></svg> to the right of any user account you wish to delete. Then confirm deletion.

## Inviting new Management Console users

If you have configured email for notifications for your GitHub Enterprise Server instance, new Management Console users will automatically receive an invitation to complete creation of the Management Console user account. For more information, see [Configuring email for notifications](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/configuring-email-for-notifications).

If you have not configured email notifications for your GitHub Enterprise Server instance, you must manually copy the Management Console invitation link and send it to the user. The user must set a password using the link before the user can access the Management Console.

1. Sign into the Management Console as the root site administrator. For more information, see [Accessing the Management Console](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console/accessing-the-management-console).
2. In the top navigation bar, click **User Management**.
3. To copy the invitation link, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link" aria-label="Copy invitation link" role="img"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg> on any Management Console user account.
4. Send the invitation link to the Management Console user. The invitation link will lead the user through the final account setup steps.

## Configuring rate limits for authentication to the Management Console

You can configure the lockout time and login attempt limits for the Management Console.

After you configure rate limits and a Management Console user exceeds the limit, the Management Console will remain locked for the duration set by the lockout time. If the root site administrator's Management Console login is locked, someone with administrative SSH access must unlock the login. To immediately unlock access to the Management Console by the root site administrator, use the `ghe-reactivate-admin-login` command via the administrative shell. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-reactivate-admin-login) and [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

If you forgot the root site administrator's password to access the Management Console, you can set a new password with the `ghe-set-password` command via the administrative shell. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-set-password) and [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. Optionally, under "Lockout time for Management Console users", type a number of minutes to lock the Management Console after too many failed login attempts. When locked out, the root site administrator must be manually unlocked.

5. Optionally, under "Login attempt limit for all users", type a maximum number of failed login attempts to allow before the Management Console is locked.

6. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

7. Wait for the configuration run to complete.