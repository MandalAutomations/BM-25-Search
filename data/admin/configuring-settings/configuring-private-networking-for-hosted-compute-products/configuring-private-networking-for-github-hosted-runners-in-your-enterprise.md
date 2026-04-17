# Configuring private networking for GitHub-hosted runners in your enterprise

Learn how to use GitHub-hosted runners with an Azure private network.

## About Azure private networking for GitHub-hosted runners

To use GitHub-hosted runners with Azure VNET, first, configure your Azure resources. Then create a private network configuration in GitHub.

The following procedures will lead you through both steps.

For more information about troubleshooting common issues with using GitHub-hosted runners with Azure VNET, see [Troubleshooting Azure private network configurations for GitHub-hosted runners in your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-private-networking-for-hosted-compute-products/troubleshooting-azure-private-network-configurations-for-github-hosted-runners-in-your-enterprise).

## Configuring your Azure resources

You will use a script to automate configuring your Azure resources.

### Prerequisites

* Use an Azure account with the Subscription Contributor role and the Network Contributor role. These roles enable you to register the `GitHub.Network` resource provider and delegate the subnet. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) on Microsoft Learn.

* To correctly associate the subnets with the right user, Azure `NetworkSettings` resources must be created in the same subscriptions where virtual networks are created.

* To ensure resource availability/data residency, resources must be created in the same Azure region.

* Outbound network traffic from the subnet **must not** be subject to TLS interception as our Virtual Machines will not be configured to trust intermediate certificates that your network uses to perform TLS interception. For more details, see [Certificates used by Azure Firewall Premium](https://learn.microsoft.com/en-us/azure/firewall/premium-certificates#certificates-used-by-azure-firewall-premium) in the Microsoft documentation.

  If you need to use TLS interception, you can install intermediate certificates via a custom image. See [Using custom images](/en/enterprise-cloud@latest/actions/how-tos/manage-runners/larger-runners/use-custom-images).

* Save the following `.bicep` file. Name the file `actions-nsg-deployment.bicep`.

  The `.bicep` file we provide contains the minimal set of rules to use GitHub-hosted runners with Azure VNET. You may need to add rules for your specific use case.

  If you use GitHub Enterprise Cloud with data residency, in the `AllowOutBoundGitHub` section, you must also include the ingress IP ranges for GHE.com. See [Network details for GHE.com](/en/enterprise-cloud@latest/admin/data-residency/network-details-for-ghecom#ranges-for-ingress-traffic).

  > \[!NOTE]
  > As an alternative to using the following file, to allow GitHub Actions to communicate with the runners, you can allow the same firewall domains that are required for communication between self-hosted runners and GitHub. For more information, see [Self-hosted runners reference](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/communicating-with-self-hosted-runners). To determine the appropriate subnet IP address range, we recommend adding a 30% buffer to the maximum job concurrency you anticipate. For instance, if your network configuration's runners are set to a maximum job concurrency of 300, it's recommended to utilize a subnet IP address range that can accommodate at least 390 runners. This buffer helps ensure that your network can handle unexpected increases in VM needs to meet job concurrency without running out of IP addresses.

  ```bicep copy
  @description('NSG for outbound rules')
  param location string
  param nsgName string = 'actions_NSG'

  resource actions_NSG 'Microsoft.Network/networkSecurityGroups@2017-06-01' = {
    name: nsgName
    location: location
    properties: {
      securityRules: [
        {
          name: 'AllowVnetOutBoundOverwrite'
          properties: {
            protocol: 'TCP'
            sourcePortRange: '*'
            destinationPortRange: '443'
            sourceAddressPrefix: '*'
            destinationAddressPrefix: 'VirtualNetwork'
            access: 'Allow'
            priority: 200
            direction: 'Outbound'
            destinationAddressPrefixes: []
          }
        }
        {
          name: 'AllowOutBoundActions'
          properties: {
            protocol: '*'
            sourcePortRange: '*'
            destinationPortRange: '443'
            sourceAddressPrefix: '*'
            access: 'Allow'
            priority: 210
            direction: 'Outbound'
            destinationAddressPrefixes: [
              '4.175.114.51/32'
              '20.102.35.120/32'
              '4.175.114.43/32'
              '20.72.125.48/32'
              '20.19.5.100/32'
              '20.7.92.46/32'
              '20.232.252.48/32'
              '52.186.44.51/32'
              '20.22.98.201/32'
              '20.246.184.240/32'
              '20.96.133.71/32'
              '20.253.2.203/32'
              '20.102.39.220/32'
              '20.81.127.181/32'
              '52.148.30.208/32'
              '20.14.42.190/32'
              '20.85.159.192/32'
              '52.224.205.173/32'
              '20.118.176.156/32'
              '20.236.207.188/32'
              '20.242.161.191/32'
              '20.166.216.139/32'
              '20.253.126.26/32'
              '52.152.245.137/32'
              '40.118.236.116/32'
              '20.185.75.138/32'
              '20.96.226.211/32'
              '52.167.78.33/32'
              '20.105.13.142/32'
              '20.253.95.3/32'
              '20.221.96.90/32'
              '51.138.235.85/32'
              '52.186.47.208/32'
              '20.7.220.66/32'
              '20.75.4.210/32'
              '20.120.75.171/32'
              '20.98.183.48/32'
              '20.84.200.15/32'
              '20.14.235.135/32'
              '20.10.226.54/32'
              '20.22.166.15/32'
              '20.65.21.88/32'
              '20.102.36.236/32'
              '20.124.56.57/32'
              '20.94.100.174/32'
              '20.102.166.33/32'
              '20.31.193.160/32'
              '20.232.77.7/32'
              '20.102.38.122/32'
              '20.102.39.57/32'
              '20.85.108.33/32'
              '40.88.240.168/32'
              '20.69.187.19/32'
              '20.246.192.124/32'
              '20.4.161.108/32'
              '20.22.22.84/32'
              '20.1.250.47/32'
              '20.237.33.78/32'
              '20.242.179.206/32'
              '40.88.239.133/32'
              '20.121.247.125/32'
              '20.106.107.180/32'
              '20.22.118.40/32'
              '20.15.240.48/32'
              '20.84.218.150/32'
            ]
          }
        }
        {
          name: 'AllowOutBoundGitHub'
          properties: {
            protocol: '*'
            sourcePortRange: '*'
            destinationPortRange: '443'
            sourceAddressPrefix: '*'
            access: 'Allow'
            priority: 220
            direction: 'Outbound'
            destinationAddressPrefixes: [
              '140.82.112.0/20'
              '143.55.64.0/20'
              '185.199.108.0/22'
              '192.30.252.0/22'
              '20.175.192.146/32'
              '20.175.192.147/32'
              '20.175.192.149/32'
              '20.175.192.150/32'
              '20.199.39.227/32'
              '20.199.39.228/32'
              '20.199.39.231/32'
              '20.199.39.232/32'
              '20.200.245.241/32'
              '20.200.245.245/32'
              '20.200.245.246/32'
              '20.200.245.247/32'
              '20.200.245.248/32'
              '20.201.28.144/32'
              '20.201.28.148/32'
              '20.201.28.149/32'
              '20.201.28.151/32'
              '20.201.28.152/32'
              '20.205.243.160/32'
              '20.205.243.164/32'
              '20.205.243.165/32'
              '20.205.243.166/32'
              '20.205.243.168/32'
              '20.207.73.82/32'
              '20.207.73.83/32'
              '20.207.73.85/32'
              '20.207.73.86/32'
              '20.207.73.88/32'
              '20.217.135.1/32'
              '20.233.83.145/32'
              '20.233.83.146/32'
              '20.233.83.147/32'
              '20.233.83.149/32'
              '20.233.83.150/32'
              '20.248.137.48/32'
              '20.248.137.49/32'
              '20.248.137.50/32'
              '20.248.137.52/32'
              '20.248.137.55/32'
              '20.26.156.215/32'
              '20.26.156.216/32'
              '20.26.156.211/32'
              '20.27.177.113/32'
              '20.27.177.114/32'
              '20.27.177.116/32'
              '20.27.177.117/32'
              '20.27.177.118/32'
              '20.29.134.17/32'
              '20.29.134.18/32'
              '20.29.134.19/32'
              '20.29.134.23/32'
              '20.29.134.24/32'
              '20.87.245.0/32'
              '20.87.245.1/32'
              '20.87.245.4/32'
              '20.87.245.6/32'
              '20.87.245.7/32'
              '4.208.26.196/32'
              '4.208.26.197/32'
              '4.208.26.198/32'
              '4.208.26.199/32'
              '4.208.26.200/32'
              '4.225.11.196/32'
              '4.237.22.32/32'
            ]
          }
        }
        {
          name: 'AllowStorageOutbound'
          properties: {
            protocol: '*'
            sourcePortRange: '*'
            destinationPortRange: '443'
            sourceAddressPrefix: '*'
            destinationAddressPrefix: 'Storage'
            access: 'Allow'
            priority: 230
            direction: 'Outbound'
            destinationAddressPrefixes: []
          }
        }
      ]
    }
  }
  ```

### 1. Obtain the `databaseId` for your enterprise

> \[!TIP]
> Your token will require at minimum `read:enterprise` permissions to perform a successful query.

You can use the following GraphQL query to retrieve your enterprise `databaseId`. You will use the enterprise `databaseId` for the value of the `DATABASE_ID` environment variable in the next step. For more information on working with GraphQL, see [Forming calls with GraphQL](/en/enterprise-cloud@latest/graphql/guides/forming-calls-with-graphql).

| Query variable | Description                                                                                                                                                              |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `slug`         | The slug for your enterprise account, which you can identify by looking at the URL for your enterprise, `https://github.com/enterprises/SLUG` or `https://SLUG.ghe.com`. |

```graphql
query(
  $slug: String!
){
  enterprise (slug: $slug)
  {
    slug
    databaseId
  }
}
'
Variables
{
  "slug": "ENTERPRISE_SLUG"
}
```

#### Example for GitHub.com

You can use the following curl command to find your `databaseId`.

```shell copy
curl -H "Authorization: Bearer BEARER_TOKEN" -X POST \
  -d '{ "query": "query($slug: String!) { enterprise (slug: $slug) { slug databaseId } }" ,
        "variables": {
          "slug": "ENTERPRISE_SLUG"
        }
      }' \
https://api.github.com/graphql
```

#### Example for GHE.com

You can use the following GitHub CLI commands to retrieve the `databaseId`. Replace SUBDOMAIN with your enterprise's subdomain of GHE.com.

```shell copy
gh auth login -s 'read:enterprise' -h SUBDOMAIN.ghe.com

gh api graphql --hostname SUBDOMAIN.ghe.com -f query='query($slug: String!) { enterprise (slug: $slug) { slug databaseId } }' -f slug='SUBDOMAIN'
```

### 2. Use a script to configure your Azure resources

Use the following script to set up a subnet for Azure private networking. The script creates all resources in the same resource group.

To use the script, fill in the placeholder environment variable values with the actual values and run the script from a bash shell or Windows Subsystem for Linux.

> \[!NOTE]
>
> * Run the following script in the same directory where you saved the `actions-nsg-deployment.bicep` file.
> * When setting the `YOUR_AZURE_LOCATION` environment variable, use your region’s name. This value is different than your region’s display name. To see a list of names and display names, use `az account list-locations -o table`.
> * When you create the network settings resource, a service association link is applied to the subnet that you provide. This link prevents accidental deletion of the subnet while in use by the GitHub Actions service.
> * If you customize this script to use network resources in existing subnets, you must ensure any existing network interfaces (NICs) connected to the subnet are deleted before the subnet is delegated to the GitHub Actions service. Otherwise, the service will fail to apply the service association link to the subnet.

```bash copy
#!/bin/bash

# This script creates the following resources in the specified subscription:
# - Resource group
# - Network Security Group rules
# - Virtual network (vnet) and subnet
# - Network Settings with specified subnet and GitHub Enterprisedatabase ID
#
# It also registers the `GitHub.Network` resource provider with the subscription,
# delegates the created subnet to the Actions service via the `GitHub.Network/NetworkSettings`
# resource type, and applies the NSG rules to the created subnet.

# stop on failure
set -e

#set environment
export AZURE_LOCATION=YOUR_AZURE_LOCATION
export SUBSCRIPTION_ID=YOUR_SUBSCRIPTION_ID
export RESOURCE_GROUP_NAME=YOUR_RESOURCE_GROUP_NAME
export VNET_NAME=YOUR_VNET_NAME
export SUBNET_NAME=YOUR_SUBNET_NAME
export NSG_NAME=YOUR_NSG_NAME
export NETWORK_SETTINGS_RESOURCE_NAME=YOUR_NETWORK_SETTINGS_RESOURCE_NAME
export DATABASE_ID=YOUR_DATABASE_ID
export API_VERSION=2024-04-02

# These are the default values. You can adjust your address and subnet prefixes.
export ADDRESS_PREFIX=10.0.0.0/16
export SUBNET_PREFIX=10.0.0.0/24

echo
echo login to Azure
. az login --output none

echo
echo set account context $SUBSCRIPTION_ID
. az account set --subscription $SUBSCRIPTION_ID

echo
echo Register resource provider GitHub.Network
. az provider register --namespace GitHub.Network

echo
echo Create resource group $RESOURCE_GROUP_NAME at $AZURE_LOCATION
. az group create --name $RESOURCE_GROUP_NAME --location $AZURE_LOCATION

echo
echo Create NSG rules deployed with 'actions-nsg-deployment.bicep' file
. az deployment group create --resource-group $RESOURCE_GROUP_NAME --template-file ./actions-nsg-deployment.bicep --parameters location=$AZURE_LOCATION nsgName=$NSG_NAME

echo
echo Create vnet $VNET_NAME and subnet $SUBNET_NAME
. az network vnet create --resource-group $RESOURCE_GROUP_NAME --name $VNET_NAME --address-prefix $ADDRESS_PREFIX --subnet-name $SUBNET_NAME --subnet-prefixes $SUBNET_PREFIX

echo
echo Delegate subnet to GitHub.Network/networkSettings and apply NSG rules
. az network vnet subnet update --resource-group $RESOURCE_GROUP_NAME --name $SUBNET_NAME --vnet-name $VNET_NAME --delegations GitHub.Network/networkSettings --network-security-group $NSG_NAME

echo
echo Create network settings resource $NETWORK_SETTINGS_RESOURCE_NAME
. az resource create --resource-group $RESOURCE_GROUP_NAME --name $NETWORK_SETTINGS_RESOURCE_NAME --resource-type GitHub.Network/networkSettings --properties "{ \"location\": \"$AZURE_LOCATION\", \"properties\" : { \"subnetId\": \"/subscriptions/$SUBSCRIPTION_ID/resourceGroups/$RESOURCE_GROUP_NAME/providers/Microsoft.Network/virtualNetworks/$VNET_NAME/subnets/$SUBNET_NAME\", \"businessId\": \"$DATABASE_ID\" }}" --is-full-object --output table --query "{GitHubId:tags.GitHubId, name:name}" --api-version $API_VERSION

echo
echo To clean up and delete resources run the following command:
echo az group delete --resource-group $RESOURCE_GROUP_NAME
```

The script will return the full payload for the created resource. The `GitHubId` hash value returned in the payload for the created resource is the network settings resource ID you will use in the next steps while configuring a network configuration in GitHub.

## Creating a network configuration for your enterprise in GitHub

After configuring your Azure resources, you can use an Azure Virtual Network (VNET) for private networking by creating a network configuration at the enterprise or organization level. Then, you can associate that network configuration to runner groups.

Please note that initial setup must be at the enterprise level when creating the network settings configured with Azure. This is why, when obtaining the `databaseId`, the steps require you to configure the enterprise slug. Organizations are only allowed to create their own network configurations once the enterprise has been established and enabled through enterprise policy for hosted compute networking. For more information about runner groups, see [Controlling access to larger runners](/en/enterprise-cloud@latest/actions/using-github-hosted-runners/about-larger-runners/controlling-access-to-larger-runners).

Once the network configuration is associated with a runner group, all runners in that group will have access to the Azure VNET that has been connected to the underlying configuration.

### Prerequisites

Ensure your Azure resources have been configured *before* adding a network configuration in GitHub. For more information, see [Configuring private networking for GitHub-hosted runners in your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-private-networking-for-hosted-compute-products/configuring-private-networking-for-github-hosted-runners#configuring-your-azure-resources).

### 1. Add a new network configuration for your enterprise

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. In the left sidebar, click **Hosted compute networking**.
4. Click the **New network configuration** dropdown. Then click **Azure private network**.
5. Name your network configuration.
6. Click **Add Azure Virtual Network**.
7. In the popup window, enter the network settings resource ID you retrieved when you configured your Azure resources for private networking.
8. Click **Add Azure Virtual Network**.

### 2. Create a runner group for your enterprise

> \[!NOTE]
> For the runner group to be accessible by repositories within your organizations, those repositories must have access to that runner group at the organization level. For more information, see [Controlling access to larger runners](/en/enterprise-cloud@latest/actions/using-github-hosted-runners/controlling-access-to-larger-runners#changing-which-repositories-can-access-a-runner-group).

1. Create a new runner group for your enterprise. For more information about how to create a runner group, see [Controlling access to larger runners](/en/enterprise-cloud@latest/actions/using-github-hosted-runners/controlling-access-to-larger-runners#creating-a-runner-group-for-an-enterprise).
2. To choose a policy for organization access, select the **Organization access** dropdown menu and click a policy. You can configure a runner group to be accessible to a specific list of organizations, or all organizations in the enterprise.
3. While configuring your runner group, under "Network configurations," use the dropdown menu to select the network configuration you created for the Azure VNET.
4. To create the group and apply the policy, click **Create group**.

### 3. Add the GitHub-hosted runner to the enterprise runner group

> \[!NOTE]
> When adding your GitHub-hosted runner to a runner group, select the runner group you created in the previous procedures.

1. Add the GitHub-hosted runner to the runner group. For more information, see [Managing larger runners](/en/enterprise-cloud@latest/actions/using-github-hosted-runners/managing-larger-runners#adding-a-larger-runner-to-an-enterprise).

### 4. Optionally, manage network configurations

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. In the left sidebar, click **Hosted compute networking**.
4. To edit a network configuration, to the right of the network configuration, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit a network configuration" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>. Then click **Edit configuration**.
5. To disable a network configuration, to the right of the network configuration, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Menu" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>. Then click **Disable**.
6. To delete a network configuration, to the right of the network configuration, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Menu" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>. Then click **Delete**.

### 5. Optionally, add a failover network to a network configuration

> \[!NOTE]
> VNET failover is in public preview and subject to change.

You can configure a failover network for your network configuration. A failover network is a secondary Azure Virtual Network subnet, which can be in a different Azure region from your primary subnet. If your primary subnet becomes unavailable due to a regional outage or other disruption, you can enable the failover network to route runner traffic through the secondary subnet, maintaining continuity for your GitHub Actions workflows.

Key points about VNET failover:

* The failover subnet can reside in a different Azure region than the primary subnet.
* Switching between primary and failover subnets is a manual process. You enable or disable the failover network at your discretion.
* Both the primary and failover subnets must be configured with the required Azure resources (VNET/subnet, network settings, etc.) before you can use failover.
* The failover subnet must be in a [supported region](/en/enterprise-cloud@latest/admin/configuring-settings/configuring-private-networking-for-hosted-compute-products/about-azure-private-networking-for-github-hosted-runners-in-your-enterprise#about-supported-regions).

Before adding a failover network, ensure you have configured the Azure resources (VNET, subnet, network security group, and network settings resource) for the secondary subnet, following the same "Configuring your Azure resources" procedures above. The failover subnet can be in a different Azure region from your primary subnet.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. In the left sidebar, click **Hosted compute networking**.
4. Click the edit icon (<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit a network configuration" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>) next to the network configuration you want to add a failover network to. Then click **Edit configuration**.
5. Click **Add failover network**.
6. In the popup window, enter the network settings resource ID for your secondary (failover) Azure subnet.
7. Click **Add Azure Virtual Network**.
8. You will now see two subnets listed in the network configuration: the primary and the failover, labeled accordingly.

### 6. Optionally, enable or disable the failover network

After adding a failover network, you can enable it to route traffic through the secondary subnet, or disable it to return to the primary subnet.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. In the left sidebar, click **Hosted compute networking**.
4. Click the edit icon (<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit a network configuration" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>) next to the network configuration. Then click **Edit configuration**.
5. To switch to the failover network, click **Enable failover VNET**. Runner traffic will be routed through the failover subnet.
6. To switch back to the primary network, click **Disable failover VNET**. Runner traffic will return to the primary subnet.

## Enabling creation of network configurations for organizations

You can allow organization owners in an enterprise to create their own organization-level network configurations.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Policies**.
3. Click **Hosted compute networking**.
4. Under "Hosted compute networking," click **Enable**.
5. Click **Save**.

## Deleting a subnet

When you create the network settings resource, a service association link is applied to the subnet that you provide. This link prevents accidental deletion of the subnet while in use by the GitHub Actions service.

To delete the subnet, this service association link needs to be removed first. The service association link is safely removed automatically once the network settings resource is deleted.

To delete the network settings resource, the network configuration that uses it needs to be deleted first.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.

3. In the left sidebar, click **Hosted compute networking**.

4. Open the network configuration that is using the subnet that you want to delete.

5. Review the list of runner groups using the network configuration.

6. In the top-right corner, click the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Menu" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>" button. Then click **Delete configuration**.

7. To delete the network settings resource and remove the service association link, use your own inputs with following commands with the Azure CLI. For more information, see the [Azure Command-Line Interface (CLI)](https://learn.microsoft.com/en-us/cli/azure/) documentation.

   ```bash copy
   az account set --subscription $SUBSCRIPTION_ID
   az resource delete -g $RESOURCE_GROUP_NAME --name $NETWORK_SETTINGS_RESOURCE_NAME --resource-type 'GitHub.Network/networkSettings' --api-version $API_VERSION
   ```

8. Delete the subnet in Azure. For more information, see [Delete a subnet](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-manage-subnet?tabs=azure-portal#delete-a-subnet) on Microsoft Learn.