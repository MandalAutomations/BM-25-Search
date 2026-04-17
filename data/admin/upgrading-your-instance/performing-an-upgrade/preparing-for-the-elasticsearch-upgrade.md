# Preparing for the Elasticsearch upgrade in GitHub Enterprise Server 3.13

As part of upgrading GitHub Enterprise Server to version 3.13 or later, the Elasticsearch service will be upgraded.

## Overview

Elasticsearch (ES) powers the search functionality on your GitHub Enterprise Server instance. To bring the benefits of better performance and security posture, when you upgrade your instance to version 3.13 or later, the Elasticsearch version in the appliance will be upgraded from 5.6.16 to 8.7.0.

The following sections help administrators prepare for and monitor the Elasticsearch upgrade. The key points are:

* The upgrade will temporarily degrade the experience of the search and audit log features.
* If you're upgrading an instance in a cluster configuration, you must run a script to prepare your cluster for the ES upgrade. See [Upgrading a cluster](/en/enterprise-server@3.14/admin/monitoring-and-managing-your-instance/configuring-clustering/upgrading-a-cluster#upgrading-the-cluster-nodes).
* For backups, all customers should take a snapshot of their instance when the upgrade is complete.

## Impact on search and audit logs

All search indexes will be rebuilt after the upgrade to ES8. Users will experience degraded search experience during the rebuild, but the instance is otherwise expected to be functional and available. The index rebuild process depends on the size of the data set and may take a few hours to days.

Audit logs will not be available immediately after upgrade, and it may take several hours to migrate all audit logs.

We strongly recommend you take a backup (using backup-utils) immediately following completion of the index rebuild and use that snapshot for all future restores. See [Configuring backups on your instance using Backup Utilities](/en/enterprise-server@3.14/admin/backing-up-and-restoring-your-instance/configuring-backups-on-your-instance). If you restore a backup from an instance running GitHub Enterprise Server 3.11 or 3.12, then any content that relies on ES will only be available after the ES indexes have been migrated and rebuilt on the 3.13 instance.

## Monitoring the Elasticsearch upgrade

You can monitor the progress of the ES upgrade in the site admin dashboard.

1. In the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. In the left sidebar, click **Search indexes**.

When the index rebuild is complete, all the search indexes should show green and "100%."

## Changing the number of repair workers

By default, the number of index repair workers is set to the number of CPU cores divided by 8 (with an upper bound of 16). To speed up the index rebuild, you can adjust the worker count. However, before doing so, you should consider the potential impact to the load.

1. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.14/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

2. To change the number of workers, enter the following command.

   ```shell copy
   ghe-config app.github.es-workers NUMBER-OF-WORKERS
   ```

3. Run `ghe-config-apply`.

You can also adjust the worker count for individual index rebuilds in the "Search Indexes" section of the site admin dashboard. See the [Monitoring the Elasticsearch upgrade](#monitoring-the-elasticsearch-upgrade) section.