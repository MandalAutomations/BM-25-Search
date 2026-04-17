# Upgrading with an upgrade package

Learn how to use an upgrade package to upgrade GitHub Enterprise Server to a newer feature release.

Using the administrative shell, you can install an upgrade package with the `ghe-upgrade` utility.

If you're running back-to-back feature version upgrades, you must ensure background jobs are complete before proceeding with the following upgrade to a feature release. GitHub recommends waiting for any background upgrade tasks to complete before upgrading a second time. See [Overview of the upgrade process](/en/enterprise-server@3.20/admin/upgrading-your-instance/preparing-to-upgrade/overview-of-the-upgrade-process) and [Upgrade requirements](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/upgrade-requirements).

While you can use a hotpatch to upgrade to the latest patch release within a feature series, you must use an upgrade package to upgrade to a newer feature release. For example, to upgrade from 2.11.10 to 2.12.4 you must use an upgrade package since these are in different feature series.

## Upgrading a standalone instance using an upgrade package

> \[!NOTE] If you've enabled automatic update checks, you don't need to download the upgrade package and can use the file that was automatically downloaded. For more information, see [Enabling automatic update checks](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/enabling-automatic-update-checks).

1. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

2. Browse to the [GitHub Enterprise Server Releases page](https://enterprise.github.com/releases). Next to the release you are upgrading to, click **Download**, then click the **Upgrading** tab. Select the appropriate platform and copy the URL for the upgrade package (*.pkg* file).

3. Download the upgrade package to your GitHub Enterprise Server instance using `curl`:

   ```shell
   admin@HOSTNAME:~$ curl -L -O UPGRADE-PKG-URL
   ```

4. Enable maintenance mode and wait for all active processes to complete on the GitHub Enterprise Server instance. See [Enabling and scheduling maintenance mode](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/enabling-and-scheduling-maintenance-mode).

   > \[!NOTE] When upgrading the primary node in a high availability configuration, the instance should already be in maintenance mode if you are following the instructions in [Upgrading the primary node with an upgrade package](#upgrading-the-primary-node-with-an-upgrade-package).

5. Run the `ghe-upgrade` command using the package file name:

   ```shell
   admin@HOSTNAME:~$ ghe-upgrade GITHUB-UPGRADE.pkg
   *** verifying upgrade package signature...
   ```

6. Confirm that you'd like to continue with the upgrade and restart after the package signature verifies. The new root filesystem writes to the secondary partition and the instance automatically restarts in maintenance mode:

   ```shell
   *** applying update...
   This package will upgrade your installation to version VERSION-NUMBER
   Current root partition: /dev/xvda1 [VERSION-NUMBER]
   Target root partition:  /dev/xvda2
   Proceed with installation? [y/N]
   ```

7. Optionally, during an upgrade to a feature release, you can monitor the status of database migrations using the `ghe-migrations` utility. See [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-migrations).

8. After the instance restarts, the upgrade will continue in the background. You cannot unset maintenance mode until the process completes.

   To check the status of background jobs, use the `ghe-check-background-upgrade-jobs` utility. If you're running back-to-back upgrades, you must ensure background jobs are complete before proceeding with the following upgrade to a feature release.

   See [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-check-background-upgrade-jobs).

   To monitor progress of the configuration run, read the output in `/data/user/common/ghe-config.log`. For example, you can tail the log by running the following command:

   ```shell
   tail -f /data/user/common/ghe-config.log
   ```

   The configuration runs in the background and you don't need to run `ghe-config-apply` explicitly unless you encounter a problem.

   > \[!WARNING] If you are upgrading a node in a multi-node cluster, running `ghe-config-apply` on the command line or saving settings in the Management Console may fail and result in an incomplete upgrade if not all the nodes are upgraded to the same version. Please use `ghe-single-config-apply` instead.

9. Optionally, after the upgrade, validate the upgrade by configuring an IP exception list to allow access to a specified list of IP addresses. See [Enabling and scheduling maintenance mode](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/enabling-and-scheduling-maintenance-mode#validating-changes-in-maintenance-mode-using-the-ip-exception-list).

10. For single node upgrades, perform any post-upgrade tasks including disabling maintenance mode so users can use your GitHub Enterprise Server instance.

    > \[!NOTE] After you upgrade an instance in a high availability configuration, you should remain in maintenance mode until you have upgraded all of the replica nodes and replication is current. See [Upgrading additional nodes with an upgrade package](#upgrading-additional-nodes-with-an-upgrade-package).

## Upgrading an instance with multiple nodes using an upgrade package

To upgrade a multi-node GitHub Enterprise Server environment using an upgrade package, you must first upgrade the primary node and wait for its configuration run to complete successfully. Only after the primary is fully upgraded and configured can you proceed to upgrade any replica or additional nodes. Attempting to upgrade other nodes before the primary is complete will result in upgrade failures.

* [Upgrading the primary node with an upgrade package](#upgrading-the-primary-node-with-an-upgrade-package)
* [Upgrading additional nodes with an upgrade package](#upgrading-additional-nodes-with-an-upgrade-package)

### Upgrading the primary node with an upgrade package

> \[!WARNING] When replication is stopped, if the primary fails, any work from before the replica is upgraded and the replication begins again will be lost.

1. On the primary node, enable maintenance mode and wait for all active processes to complete. See [Enabling and scheduling maintenance mode](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/enabling-and-scheduling-maintenance-mode).
2. Connect to the replica node over SSH as the `admin` user on port 122:

   ```shell
   ssh -p 122 admin@REPLICA_HOST
   ```
3. To stop replication on all nodes, run `ghe-repl-stop` on each node. Alternatively, if there are multiple replicas, run `ghe-repl-stop-all` on the primary node instead, which will stop replication in a single run.
4. To upgrade the primary node, follow the instructions in [Upgrading a standalone instance using an upgrade package](#upgrading-a-standalone-instance-using-an-upgrade-package).

### Upgrading additional nodes with an upgrade package

1. Upgrade the node by following the instructions in [Upgrading a standalone instance using an upgrade package](#upgrading-a-standalone-instance-using-an-upgrade-package).
2. Connect to the replica node over SSH as the `admin` user on port 122:

   ```shell
   ssh -p 122 admin@REPLICA_HOST
   ```
3. Verify the upgrade by running:

   ```shell
   ghe-version
   ```
4. On the replica node, to start replication, run `ghe-repl-start`. Alternatively, if there are multiple replicas, run `ghe-repl-start-all` on the primary node instead, which will start replications in a single run.
5. On the replica node, to make sure replication services are running correctly, run `ghe-repl-status`. This command will return `OK` for all services when a successful replication is in progress and the replica has upgraded. If the command returns `Replication is not running`, the replication may still be starting. Wait about one minute before running `ghe-repl-status` again.

> \[!NOTE]
>
> * While the resync is in progress `ghe-repl-status` may indicate that replication is behind. For example, you may see the following message.
>
>   ```text
>   CRITICAL: git replication is behind the primary by more than 1007 repositories and/or gists
>   ```
>
> * If GitHub Actions is enabled on your GitHub Enterprise Server instance, you may see a message like the following. This message is expected when replication is paused due to maintenance mode being set on the primary appliance. Once maintenance mode is unset, this message should be resolved.
>
>   ```text
>   CRITICAL: mssql replication is down, didn't find Token_Configuration!
>   ```

If `ghe-repl-status` did not return `OK`, and the explanation isn't listed in the note above, contact GitHub Enterprise Support. For more information, see [Contacting GitHub Support](/en/enterprise-server@3.20/support/contacting-github-support).

1. Repeat the steps above for each additional node.
2. After you have upgraded the last replica node and the resync is complete, disable maintenance mode so users can use your GitHub Enterprise Server instance.