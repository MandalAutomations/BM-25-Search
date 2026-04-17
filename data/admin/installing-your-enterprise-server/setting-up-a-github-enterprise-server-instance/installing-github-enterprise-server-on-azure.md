# Installing GitHub Enterprise Server on Azure

To install GitHub Enterprise Server on Azure, you must deploy onto a memory-optimized instance that supports premium storage.

You can deploy GitHub Enterprise Server on global Azure or Azure Government.

## Prerequisites

* You must have a GitHub Enterprise license file. For more information, see [Setting up a trial of GitHub Enterprise Server](/en/enterprise-server@3.20/admin/overview/setting-up-a-trial-of-github-enterprise-server) and [License files for GitHub Enterprise Server](/en/enterprise-server@3.20/billing/concepts/enterprise-billing/ghes-license-files).
* You must have an Azure account capable of provisioning new machines. For more information, see the [Microsoft Azure website](https://azure.microsoft.com).
* Most actions needed to launch your virtual machine (VM) may also be performed using the Azure Portal. However, we recommend installing the Azure command line interface (CLI) for initial setup. Examples using the Azure CLI 2.0 are included below. For more information, see Azure's guide [Install Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest).

## Hardware considerations

* [Minimum recommended requirements](#minimum-recommended-requirements)
* [Storage](#storage)
* [CPU and memory](#cpu-and-memory)

### Minimum recommended requirements

We recommend different hardware configurations depending on the number of user licenses for your GitHub Enterprise Server instance. If you provision more resources than the minimum recommended requirements, your instance will perform and scale better.

| User licenses                  | x86-64 vCPUs | Memory | Root storage | Attached (data) storage |  IOPS |
| :----------------------------- | -----------: | -----: | -----------: | ----------------------: | ----: |
| Trial, demo, or 10 light users |            4 |  32 GB |       400 GB |                  500 GB |   600 |
| Up to 1,000                    |            8 |  48 GB |       400 GB |                  500 GB |  3000 |
| 1,000 to 3,000                 |           16 |  64 GB |       400 GB |                 1000 GB |  6000 |
| 3,000 to 5,000                 |           32 | 128 GB |       400 GB |                 1500 GB |  9000 |
| 5,000 to 8,000                 |           48 | 256 GB |       400 GB |                 3000 GB | 12000 |
| 8,000 to 10,000+               |           64 | 512 GB |       400 GB |                 5000 GB | 15000 |

If you plan to enable GitHub Actions or GitHub Code Security for the users of your instance, more resources are required.

* GitHub Actions - increase both CPU and memory by at least 25%
* GitHub Code Security - increase both CPU and memory by at least 25%

These adjustments should be applied to the base requirements for each user tier. We recommend monitoring all changes to your resources, as further increases may be needed.

For more information about these requirements, see [Getting started with GitHub Actions for GitHub Enterprise Server](/en/enterprise-server@3.20/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/getting-started-with-github-actions-for-github-enterprise-server#review-hardware-considerations).

If you plan to enable Container registry for the users of your instance, more resources are required. For more information about these requirements, see [Getting started with GitHub Packages for your enterprise](/en/enterprise-server@3.20/admin/packages/getting-started-with-github-packages-for-your-enterprise).

For more information about adjusting resources for an existing instance, see [Increasing storage capacity](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/increasing-storage-capacity) and [Increasing CPU or memory resources](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/increasing-cpu-or-memory-resources).

### Storage

We recommend a high-performance SSD with high input/output operations per second (IOPS) and low latency for GitHub Enterprise Server. Workloads are I/O intensive. If you use a bare metal hypervisor, we recommend directly attaching the disk or using a disk from a storage area network (SAN).

Your instance requires a persistent data disk separate from the root disk. For more information, see [System overview](/en/enterprise-server@3.20/admin/overview/system-overview).

> \[!WARNING]
> Root storage refers to the total size of your instance's root disk. When the instance is booted you will see 200GB available on the root filesystem. The remaining 200GB is reserved for upgrades. For more information, see [System overview](/en/enterprise-server@3.20/admin/overview/system-overview#storage-architecture).

To configure GitHub Actions, you must provide external blob storage. For more information, see [Getting started with GitHub Actions for GitHub Enterprise Server](/en/enterprise-server@3.20/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/getting-started-with-github-actions-for-github-enterprise-server##external-storage-requirements).

The available space on the root filesystem will be 50% of the total disk size. You can resize your instance's root disk by building a new instance or using an existing instance. For more information, see [System overview](/en/enterprise-server@3.20/admin/overview/system-overview#storage-architecture) and [Increasing storage capacity](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/increasing-storage-capacity).

### CPU and memory

The CPU and memory resources that GitHub Enterprise Server requires depend on the levels of activity for users, automations, and integrations.

Any VMs you provision for your GitHub Enterprise Server instance must use the x86-64 CPU architecture. Other architectures are not supported, such as AArch64 or arm64.

If you plan to enable GitHub Actions for the users of your GitHub Enterprise Server instance, you may need to provision additional CPU and memory resources for your instance. For more information, see [Getting started with GitHub Actions for GitHub Enterprise Server](/en/enterprise-server@3.20/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/getting-started-with-github-actions-for-github-enterprise-server#review-hardware-considerations).

When you increase CPU resources, GitHub recommends adding at least 6.5 GB of memory for each vCPU (up to 16 vCPUs) that you provision for the instance. When you use more than 16 vCPUs, you don't need to add 6.5 GB of memory for each vCPU, but you should monitor your instance to ensure it has enough memory.

> \[!WARNING]
> We recommend that users configure webhook events to notify external systems of activity on GitHub Enterprise Server. Automated checks for changes, or *polling*, will negatively impact the performance and scalability of your instance. For more information, see [About webhooks](/en/enterprise-server@3.20/get-started/exploring-integrations/about-webhooks).

For more information about monitoring the capacity and performance of GitHub Enterprise Server, see [Monitoring your instance](/en/enterprise-server@3.20/admin/enterprise-management/monitoring-your-appliance).

You can increase your instance's CPU or memory resources. For more information, see [Increasing CPU or memory resources](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/increasing-cpu-or-memory-resources).

## Determining the virtual machine type

Before launching your GitHub Enterprise Server instance on Azure, you'll need to determine the machine type that best fits the needs of your organization. For more information about memory optimized machines, see [Memory optimized virtual machine sizes](https://docs.microsoft.com/en-gb/azure/virtual-machines/sizes-memory) in the Microsoft Azure documentation. To review the minimum resource requirements for GitHub Enterprise Server, see [Minimum recommended requirements](#minimum-recommended-requirements).

You can always scale up your CPU or memory by resizing your instance. Changing the resources available to your instance requires downtime for your users, so GitHub recommends over-provisioning resources to account for scale.

The GitHub Enterprise Server appliance requires a premium storage data disk, and is supported on any Azure VM that supports premium storage. Azure VM types with the `s` suffix support premium storage. For more information, see [What disk types are available in Azure?](https://docs.microsoft.com/en-us/azure/virtual-machines/disks-types#premium-ssd) and [Azure premium storage: design for high performance](https://docs.microsoft.com/en-us/azure/virtual-machines/premium-storage-performance) in the Azure documentation.

GitHub recommends a memory-optimized VM for GitHub Enterprise Server. For more information, see [Memory optimized virtual machine sizes](https://docs.microsoft.com/en-us/azure/virtual-machines/sizes-memory) in the Azure documentation.

GitHub Enterprise Server supports any region that supports your VM type. For more information about the supported regions for each VM, see Azure's [Products available by region](https://azure.microsoft.com/regions/services/).

## Creating the GitHub Enterprise Server virtual machine

To create the instance, you'll need to import the GitHub Enterprise Server image to your virtual machine and attach an additional storage volume for your instance data. For more information, see [Hardware considerations](#hardware-considerations).

1. Find the most recent GitHub Enterprise Server appliance image. For more information about the `vm image list` command, see [`az vm image list`](https://docs.microsoft.com/cli/azure/vm/image?view=azure-cli-latest#az_vm_image_list) in the Microsoft documentation.

   ```shell
   az vm image list --all -f GitHub-Enterprise | grep '"urn": "GitHub:' | sort -V
   ```

2. Create a new VM using the appliance image you found. For more information, see [az vm create](https://docs.microsoft.com/cli/azure/vm?view=azure-cli-latest#az_vm_create) in the Microsoft documentation.

   Pass in options for the name of your VM, the resource group, the size of your VM, the name of your preferred Azure region, the name of the appliance image VM you listed in the previous step, and the storage SKU for premium storage. For more information about resource groups, see [Resource groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups) in the Microsoft documentation.

   ```shell
   az vm create -n VM_NAME -g RESOURCE_GROUP --size VM_SIZE -l REGION --image APPLIANCE_IMAGE_NAME --storage-sku Premium_LRS
   ```

3. Configure the security settings on your VM to open up required ports. We recommend opening network ports selectively based on the network services you need to expose for administrative and user purposes. For more information, see [Network ports](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/network-ports#administrative-ports), and [az vm open-port](https://docs.microsoft.com/cli/azure/vm?view=azure-cli-latest#az_vm_open_port) in the Microsoft documentation. See the table below for a description of each port to determine what ports you need to open.

   ```shell
   az vm open-port -n VM_NAME -g RESOURCE_GROUP --port PORT_NUMBER
   ```

   This table identifies what each port is used for.

   | Port     | Service | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   | -------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | 22       | SSH     | Git over SSH access. Clone, fetch, and push operations to public/private repositories supported.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   | 25       | SMTP    | SMTP with encryption (STARTTLS) support.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   | 80       | HTTP    | Web application access. *All requests are redirected to the HTTPS port when SSL is enabled.*                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   | 122      | SSH     | Instance shell access. *The default SSH port (22) is dedicated to application git+ssh network traffic.*                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   | 161/UDP  | SNMP    | Required for network monitoring protocol operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   | 443      | HTTPS   | Web application and Git over HTTPS access.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   | 1194/UDP | VPN     | Secure replication network tunnel in high availability configuration. *Encrypted using WireGuard.*                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   | 8080     | HTTP    | Plain-text web based Management Console. *Not required unless SSL is disabled manually.*                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   | 8443     | HTTPS   | Secure web based Management Console. *Required for basic installation and configuration.*                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
   | 9418     | Git     | Simple Git protocol port. Clone and fetch operations to public repositories only. *Unencrypted network communication.* If you have enabled private mode on your instance, then opening this port is only required if you also enabled anonymous Git read access. For more information, see [Enforcing repository management policies in your enterprise](/en/enterprise-server@3.20/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#configuring-anonymous-git-read-access). |

4. Create and attach a new data disk to the VM, and configure the size based on your user license count. For more information, see [az vm disk attach](https://docs.microsoft.com/cli/azure/vm/disk?view=azure-cli-latest#az_vm_disk_attach) in the Microsoft documentation.

   > \[!NOTE]
   > All Azure managed disks created since June 10, 2017 are encrypted at rest by default with [Azure Storage Encryption](https://learn.microsoft.com/en-us/azure/storage/common/storage-service-encryption#about-azure-storage-service-side-encryption). Enabling Azure Disk Encryption for GitHub Enterprise Server is not supported.

   Pass in options for the name of your VM (for example, `ghe-acme-corp`), the resource group, the premium storage SKU, the size of the disk (for example, `200`), and a name for the resulting VHD.

   ```shell
   az vm disk attach --vm-name VM_NAME -g RESOURCE_GROUP --sku Premium_LRS --new -z SIZE_IN_GB --name ghe-data.vhd --caching ReadWrite
   ```

   > \[!NOTE]
   > For non-production instances to have sufficient I/O throughput, the recommended minimum disk size is 150 GiB with read/write cache enabled (`--caching ReadWrite`).

## Configuring the GitHub Enterprise Server virtual machine

To configure the instance, you must confirm the instance's status, upload a license file, set the root Management Console password, configure the instance's settings, and restart the instance.

> \[!WARNING]
> To prevent an attacker from compromising the new instance, ensure that you personally set the root Management Console password and create the first user as soon as possible.

1. Before configuring the VM, you must wait for it to enter ReadyRole status. Check the status of the VM with the `vm list` command. For more information, see [az vm list](https://docs.microsoft.com/cli/azure/vm?view=azure-cli-latest#az_vm_list) in the Microsoft documentation.

   ```shell
   $ az vm list -d -g RESOURCE_GROUP -o table
   > Name    ResourceGroup    PowerState    PublicIps     Fqdns    Location    Zones
   > ------  ---------------  ------------  ------------  -------  ----------  -------
   > VM_NAME RESOURCE_GROUP   VM running    40.76.79.202           eastus

   ```

   > \[!NOTE]
   > Azure does not automatically create a FQDNS entry for the VM. For more information, see the Azure guide [Create a fully qualified domain name in the Azure portal for a Linux VM](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn).

   1. Copy the virtual machine's public DNS name, and paste it into a web browser.
   2. At the prompt, upload your license file and set a management console password. For more information, see [Downloading your license for GitHub Enterprise](/en/enterprise-server@3.20/billing/managing-your-license-for-github-enterprise).
   3. In the [Management Console](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console), configure and save your desired settings. For more information, see [Configuring GitHub Enterprise](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise).
   4. The instance will restart automatically.
   5. Click **Visit your instance**.

## Azure extension features

GitHub Enterprise Server does not support the installation of Azure extension features. The GitHub Enterprise Server image is shipped with a customized `waagent` package which only supports basic VM management functions and blocks advanced VM management functions.

To avoid system instability of your GitHub Enterprise Server instance, the `walinuxagent` service is intentionally run in GitHub Enterprise Server in a restricted mode, explicitly disallowing the agent from being able to install other agents. VM management features that rely on additional agents and extensions beyond that which ships with GitHub Enterprise Server image, such as the Monitoring Agent extension for Azure Insights or Azure Backups, are unsupported.

Because GitHub Enterprise Server runs a customized Linux operating system with only the necessary applications and services, installing or updating operating system packages manually will overwrite these customizations and can cause unexpected behavior. For more information, see [System overview](/en/enterprise-server@3.20/admin/overview/system-overview).

## Further reading

* [System overview](/en/enterprise-server@3.20/admin/overview/system-overview)
* [About upgrades to new releases](/en/enterprise-server@3.20/admin/overview/about-upgrades-to-new-releases)