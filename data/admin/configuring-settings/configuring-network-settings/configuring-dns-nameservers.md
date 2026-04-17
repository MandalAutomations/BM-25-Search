# Configuring DNS nameservers

GitHub Enterprise Server uses the dynamic host configuration protocol (DHCP) for DNS settings when DHCP leases provide nameservers. If nameservers are not provided by a dynamic host configuration protocol (DHCP) lease, or if you need to use specific DNS settings, you can specify the nameservers manually.

The nameservers you specify must resolve your GitHub Enterprise Server instance's hostname.

> \[!WARNING]
> Do not change the hostname for GitHub Enterprise Server after initial setup. Changing the hostname will cause unexpected behavior, up to and including instance outages and invalidation of users' security keys. If you have changed the hostname for your instance and are experiencing problems, contact GitHub Enterprise Support or GitHub Premium Support.

## Configuring nameservers using the virtual machine console

1. Using your virtualization platform tools, open the virtual machine console.
2. To start your network setup, press **S**.
3. Configure nameservers for your instance.
4. To finish configuring your settings, press **D**.

## Configuring nameservers using the administrative shell

1. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

2. To edit your nameservers, use the `ghe-setup-network` command in visual mode. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-setup-network).

   ```shell
   ghe-setup-network -v
   ```

3. To add your new nameserver entries to your GitHub Enterprise Server instance, run the following:

   ```shell
   sudo service resolvconf restart
   sudo service dnsmasq restart
   ```