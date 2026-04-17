# Changing your platform

How to change the platform that runs GitHub.com

In some cases, you may need to change the platform on which your GitHub Enterprise Server instance runs, such as moving from VMware to Azure.

## Recommendations

You should carefully plan any out migration procedures and consider first testing on a staging environment. For more information, see [Setting up a staging instance](/en/enterprise-server@3.20/admin/installing-your-enterprise-server/setting-up-a-github-enterprise-server-instance/setting-up-a-staging-instance).

Moving platforms using a replica will require the least amount of time for the migration process but will require you to make changes to your live environment in order to setup the replication.

Moving via backup and restore will not require any changes to your live environment, however the migration will take a significant amount of time. The specific amount of time to complete the migration will vary based the performance of your backup host, and the network speeds between your backup host and the new instance. Maintenance mode should also be enabled throughout the process otherwise users may be able to make changes which will not be reflected on your new instance.

> \[!WARNING]
> You should not use utilities which convert your GitHub Enterprise Server instance from one platform to another. Doing so could cause unintended side effects such as system instability.

## Move platforms using a HA replica

1. Set up a new GitHub Enterprise Server instance on your chosen platform. See [Setting up a GitHub Enterprise Server instance](/en/enterprise-server@3.20/admin/installation/setting-up-a-github-enterprise-server-instance).
2. Configure your new GitHub Enterprise Server instance as a replica. See [Creating a high availability replica](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/configuring-high-availability/creating-a-high-availability-replica).
3. Failover to your replica. See [Initiating a failover to your replica appliance](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/configuring-high-availability/initiating-a-failover-to-your-replica-appliance).

## Moving platforms using backup and restore

1. Setup backups for your existing GitHub Enterprise Server instance. See [Configuring backups on your instance using Backup Utilities](/en/enterprise-server@3.20/admin/backing-up-and-restoring-your-instance/configuring-backups-on-your-instance).
2. Set up a new GitHub Enterprise Server instance on your chosen platform. See [Setting up a GitHub Enterprise Server instance](/en/enterprise-server@3.20/admin/installation/setting-up-a-github-enterprise-server-instance).
3. Communicate the upcoming downtime to your users and enable maintenance mode. For more information, see the following articles.

   * [Customizing user messages for your enterprise](/en/enterprise-server@3.20/admin/managing-accounts-and-repositories/communicating-information-to-users-in-your-enterprise/customizing-user-messages-for-your-enterprise#creating-a-mandatory-message)
   * [Enabling and scheduling maintenance mode](/en/enterprise-server@3.20/admin/administering-your-instance/configuring-maintenance-mode/enabling-and-scheduling-maintenance-mode)
4. Create a new backup of your existing GitHub Enterprise Server instance.
5. Restore the backup to your new GitHub Enterprise Server instance. If you are using GitHub Actions, see [Backing up and restoring GitHub Enterprise Server with GitHub Actions enabled](/en/enterprise-server@3.20/admin/managing-github-actions-for-your-enterprise/advanced-configuration-and-troubleshooting/backing-up-and-restoring-github-enterprise-server-with-github-actions-enabled)
6. Update the DNS to point to the address of your new GitHub Enterprise Server instance.
7. Disable maintenance mode and let users know they can continue normal operations.

## Further reading

* [About GitHub Enterprise Server](/en/enterprise-server@3.20/admin/overview/about-github-enterprise-server)
* [About high availability configuration](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/configuring-high-availability/about-high-availability-configuration)
* [Configuring backups on your instance using Backup Utilities](/en/enterprise-server@3.20/admin/backing-up-and-restoring-your-instance/configuring-backups-on-your-instance#about-github-enterprise-server-backup-utilities)