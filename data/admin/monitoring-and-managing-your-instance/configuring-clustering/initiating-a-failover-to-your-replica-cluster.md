# Initiating a failover to your replica cluster

If your GitHub Enterprise Server cluster fails, you can fail over to the replica.

## About failover to your replica cluster

If the data center for your active cluster experiences a failure and you've configured high availability, you can fail over to your replica cluster.

Failing over to your replica cluster promotes it to be your new active cluster, and decouples the new active cluster from the old active cluster. The nodes in your old active cluster are placed in maintenance mode if they are in a healthy enough state for this operation to be performed.

After failover, you will have two standalone clusters without high availability configured. You can reconfigure replication from the new active cluster. For more information, see [Configuring high availability replication for a cluster](/en/enterprise-server@3.20/admin/enterprise-management/configuring-high-availability-replication-for-a-cluster#reconfiguring-high-availability-replication-after-a-failover).

## Prerequisites

To fail over to replica nodes, you must have configured high availability replication for your cluster. For more information, see [Configuring high availability replication for a cluster](/en/enterprise-server@3.20/admin/enterprise-management/configuring-high-availability-replication-for-a-cluster).

## Initiating a failover to your replica cluster

1. SSH into the primary MySQL node in the replica cluster. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/accessing-the-administrative-shell-ssh#enabling-access-to-the-administrative-shell-via-ssh).

2. To begin the failover to the secondary cluster and configure the nodes to respond to requests, run the following command.

   ```shell
   ghe-cluster-failover
   ```

3. After the configuration run finishes, GitHub Enterprise Server displays the following message.

   ```shell
   Finished cluster configuration
   ```

4. Update the DNS record to point to the IP address of the load balancer for your replica cluster. After the TTL period expires, requests will be directed to the replica cluster.

After GitHub Enterprise Server returns you to the prompt and your DNS updates propagate, you've finished failing over. Users can access GitHub Enterprise Server using the usual hostname for your cluster.