# Troubleshooting access to the Management Console

You can troubleshoot access problems for the Management Console.

## About problems with Management Console access

If you experience problems accessing the Management Console, you can try the following troubleshooting steps.

## Unlocking the Management Console after failed login attempts

The Management Console locks after the number of failed login attempts configured by your authentication policies. For more information, see [Managing access to the Management Console](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console/managing-access-to-the-management-console#configuring-rate-limits-for-authentication-to-the-management-console).

### Unlocking the root site administrator account

If the root site administrator's Management Console login is locked, someone with administrative SSH access must unlock the login. To immediately unlock access to the Management Console by the root site administrator, use the `ghe-reactivate-admin-login` command via the administrative shell. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-reactivate-admin-login) and [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

If you forgot the root site administrator's password to access the Management Console, you can set a new password with the `ghe-set-password` command via the administrative shell. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-set-password) and [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

### Unlocking a Management Console user account

The root site administrator can unlock access to the Management Console for other user accounts.

1. Sign into the Management Console as the root site administrator. For more information, see [Accessing the Management Console](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console/accessing-the-management-console).
2. In the top navigation bar, click **User Management**.
3. Locked user accounts will appear as "State: blocked". To unblock the user and allow authentication, to the right of the user's details, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="Unblock user" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg>.

## Troubleshooting failed connections to the Management Console

If you cannot connect to the Management Console on your GitHub Enterprise Server instance, you can review the following information to troubleshoot the problem.

### Error: "Your session has expired" for connections through a load balancer

If you access your GitHub Enterprise Server instance through a load balancer and connections to the Management Console fail with a message that your session has expired, you may need to reconfigure your load balancer. For more information, see [Using GitHub Enterprise Server with a load balancer](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/using-github-enterprise-server-with-a-load-balancer#error-your-session-has-expired-for-connections-to-the-management-console).