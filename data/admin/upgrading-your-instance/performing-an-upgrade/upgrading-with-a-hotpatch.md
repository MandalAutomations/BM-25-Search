# Upgrading with a hotpatch

You can use a hotpatch package to upgrade GitHub Enterprise Server to a newer patch release within a feature series.

You can upgrade GitHub Enterprise Server to the latest patch release using a hotpatch.

You can use hotpatching to upgrade to a newer patch release, but not a feature release. For example, you can upgrade from 2.10.1 to 2.10.5 because they are in the same feature series, but not from 2.10.9 to 2.11.0 because they are in a different feature series.

Hotpatches do not always require a reboot. When you install the hotpatch, you'll see a message in the terminal if any of the packages need a reboot to complete the update. You can schedule this reboot at a convenient time but we recommend rebooting as soon as practical, especially if there are any security fixes.

Hotpatches require a configuration run, which can cause a brief period of errors or unresponsiveness for some or all services on your GitHub Enterprise Server instance. You are not required to enable maintenance mode during installation of a hotpatch, but doing so will guarantee that users see a maintenance page instead of errors or timeouts. See [Enabling and scheduling maintenance mode](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/enabling-and-scheduling-maintenance-mode).

Using the Management Console, you can install a hotpatch immediately or schedule it for later installation. You can use the administrative shell to install a hotpatch with the `ghe-upgrade` utility. See [Overview of the upgrade process](/en/enterprise-server@3.20/admin/upgrading-your-instance/preparing-to-upgrade/overview-of-the-upgrade-process) and [Upgrade requirements](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/upgrade-requirements).

## Upgrading a standalone instance using a hotpatch

If you're upgrading an instance with one node using a hotpatch, and your target is a patch release, you can upgrade using Management Console. To upgrade to a feature release, you must use the administrative shell.

* [Installing a hotpatch using the Management Console](#installing-a-hotpatch-using-the-management-console)
* [Installing a hotpatch using the administrative shell](#installing-a-hotpatch-using-the-administrative-shell)

### Installing a hotpatch using the Management Console

You can use the Management Console to upgrade with a hotpatch by enabling automatic updates. You will then be presented with the latest available version of GitHub Enterprise Server that you can upgrade to.

If the upgrade target you're presented with is a feature release instead of a patch release, you cannot use the Management Console to install a hotpatch. You must install the hotpatch using the administrative shell instead.

1. Enable automatic updates. For more information, see [Enabling automatic update checks](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/enabling-automatic-update-checks).
2. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
3. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
4. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
5. In the top navigation bar, click **Updates**.

   ![Screenshot of the header of the Management Console. A tab, labeled "Updates", is highlighted with an orange outline.](/assets/images/enterprise/management-console/updates-tab.png)
6. When a new hotpatch has been downloaded, select the **Install package** dropdown menu.
   * To install immediately, click **Now**.
   * To install later, select a later date.
7. Click **Install**.

### Installing a hotpatch using the administrative shell

> \[!NOTE] If you've enabled automatic update checks, you don't need to download the upgrade package and can use the file that was automatically downloaded. For more information, see [Enabling automatic update checks](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/enabling-automatic-update-checks).

1. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

2. Browse to the [GitHub Enterprise Server Releases page](https://enterprise.github.com/releases). Next to the release you are upgrading to, click **Download**, then click the **Upgrading** tab. Copy the URL for the upgrade hotpackage (*.hpkg* file).

3. Download the upgrade package to your GitHub Enterprise Server instance using `curl`:

   ```shell
   admin@HOSTNAME:~$ curl -L -O UPGRADE-PKG-URL
   ```

4. Run the `ghe-upgrade` command using the package file name:

   ```shell
   admin@HOSTNAME:~$ ghe-upgrade GITHUB-UPGRADE.hpkg
   *** verifying upgrade package signature...
   ```

5. If at least one service or system component requires a reboot, the hotpatch upgrade script notifies you. For example, updates to the kernel, MySQL, or Elasticsearch may require a reboot.

## Upgrading an instance with multiple nodes using a hotpatch

If you are installing a hotpatch, you do not need to enter maintenance mode or stop replication.

* [Upgrading the primary node using a hotpatch](#upgrading-the-primary-node-using-a-hotpatch)
* [Upgrading additional nodes using a hotpatch](#upgrading-additional-nodes-using-a-hotpatch)

### Upgrading the primary node using a hotpatch

For instructions to upgrade the primary node, see [Installing a hotpatch using the administrative shell](#installing-a-hotpatch-using-the-administrative-shell).

### Upgrading additional nodes using a hotpatch

To upgrade an instance that comprises multiple nodes, such as a high-availability or geo-replication configuration, you must repeat the following procedure on each replica node, one at a time.

1. To upgrade the node, follow the instructions in [Installing a hotpatch using the administrative shell](#installing-a-hotpatch-using-the-administrative-shell).
2. Connect to the replica node over SSH as the `admin` user on port 122:

   ```shell
   ssh -p 122 admin@REPLICA_HOST
   ```
3. Verify the upgrade by running:

   ```shell
   ghe-version
   ```
4. Repeat the steps above for each additional node.