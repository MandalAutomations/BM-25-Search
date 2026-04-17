# Recovering a high availability configuration

After failing over to a GitHub Enterprise Server appliance, you should regain redundancy as soon as possible rather than rely on a single appliance.

## About recovery for a high availability configuration

You can use the former primary appliance as the new replica appliance if the failover was planned or was not related to the health of the appliance. If the failover was related to an issue with the primary appliance, you may prefer to create a new replica appliance. For more information, see [Creating a high availability replica](/en/enterprise-server@3.20/admin/enterprise-management/configuring-high-availability/creating-a-high-availability-replica).

> \[!WARNING]
> You must enable maintenance mode before configuring a former primary appliance as a new replica. If you do not enable maintenance mode, you will cause a production outage.

## Configuring a former primary appliance as a new replica

1. Connect to the former primary appliance's IP address using SSH.

   ```shell
   ssh -p 122 admin@ FORMER_PRIMARY_IP
   ```

2. Enable maintenance mode on the former primary appliance. For more information, see [Enabling and scheduling maintenance mode](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/enabling-and-scheduling-maintenance-mode).

3. On the former primary appliance, run `ghe-repl-setup` with the IP address of the former replica. You may need to use the `--force` option to replace the existing configuration.

   ```shell
   ghe-repl-setup --force FORMER_REPLICA_IP
   ```

4. To add the public key to the list of authorized keys on the primary appliance, browse to `https://PRIMARY-HOSTNAME/setup/settings` and add the key you copied from the replica to the list.

5. To verify the connection to the new primary and enable replica mode for the new replica, run `ghe-repl-setup` again.

   ```shell
   ghe-repl-setup FORMER_REPLICA_IP
   ```

6. To start replication of the datastores, use the `ghe-repl-start` command.

   ```shell
   ghe-repl-start
   ```

   > \[!WARNING]
   > To ensure uninterrupted service when setting up a new replica, run `ghe-config-apply` between `ghe-repl-setup` and `ghe-repl-start`. This allows the primary server to remain available throughout the replication setup process.