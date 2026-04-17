# Getting started with GitHub Packages for your enterprise

You can start using GitHub Packages on GitHub.com by enabling the feature, configuring third-party storage, configuring the ecosystems you want to support, and updating your TLS certificate.

> \[!NOTE]
> GitHub Packages on GitHub Enterprise Server does not currently support clustering.

## Step 1: Check whether GitHub Packages is available for your enterprise

GitHub Packages is available in GitHub Enterprise Server 3.0 or higher. If you're using an earlier version of GitHub Enterprise Server, you'll have to upgrade to use GitHub Packages. For more information about upgrading your GitHub Enterprise Server instance, see [About upgrades to new releases](/en/enterprise-server@3.20/admin/overview/about-upgrades-to-new-releases).

## Step 2: Review hardware requirements

If you plan to enable Container registry for the users of your instance, at least 10% more CPU resources are required.

We recommend reviewing the levels of activity for users and automations on the instance to ensure that you have provisioned adequate CPU for your users. For more information, see [Monitoring your instance](/en/enterprise-server@3.20/admin/enterprise-management/monitoring-your-appliance).

For more information about minimum hardware requirements for your GitHub Enterprise Server instance, see the hardware considerations for your instance's platform.

* [AWS](/en/enterprise-server@3.20/admin/installation/setting-up-a-github-enterprise-server-instance/installing-github-enterprise-server-on-aws#hardware-considerations)
* [Azure](/en/enterprise-server@3.20/admin/installation/setting-up-a-github-enterprise-server-instance/installing-github-enterprise-server-on-azure#hardware-considerations)
* [Google Cloud Platform](/en/enterprise-server@3.20/admin/installation/setting-up-a-github-enterprise-server-instance/installing-github-enterprise-server-on-google-cloud-platform#hardware-considerations)
* [Hyper-V](/en/enterprise-server@3.20/admin/installation/setting-up-a-github-enterprise-server-instance/installing-github-enterprise-server-on-hyper-v#hardware-considerations)
* [OpenStack KVM](/en/enterprise-server@3.20/admin/installation/setting-up-a-github-enterprise-server-instance/installing-github-enterprise-server-on-openstack-kvm#hardware-considerations)
* [VMware](/en/enterprise-server@3.20/admin/installation/setting-up-a-github-enterprise-server-instance/installing-github-enterprise-server-on-vmware#hardware-considerations)

For more information about adjusting resources for an existing instance, see [Increasing CPU or memory resources](/en/enterprise-server@3.20/admin/enterprise-management/updating-the-virtual-machine-and-physical-resources/increasing-cpu-or-memory-resources).

## Step 3: Enable GitHub Packages and configure external storage

GitHub Packages on GitHub Enterprise Server uses external blob storage to store your packages.

After enabling GitHub Packages for your GitHub Enterprise Server instance, you'll need to prepare your third-party storage bucket. The amount of storage required depends on your usage of GitHub Packages, and the setup guidelines can vary by storage provider.

Supported external storage providers

* Amazon Web Services (AWS) S3
* Azure Blob Storage
* MinIO

To enable GitHub Packages and configure third-party storage, see:

* [Enabling GitHub Packages with AWS](/en/enterprise-server@3.20/admin/packages/enabling-github-packages-with-aws)
* [Enabling GitHub Packages with Azure Blob Storage](/en/enterprise-server@3.20/admin/packages/enabling-github-packages-with-azure-blob-storage)
* [Enabling GitHub Packages with MinIO](/en/enterprise-server@3.20/admin/packages/enabling-github-packages-with-minio)

## Step 4: Specify the package ecosystems to support on your instance

Choose which package ecosystems you'd like to enable, disable, or set to read-only on your GitHub Enterprise Server instance. Available options are Container registry, Docker, RubyGems, npm, Apache Maven, Gradle, or NuGet. For more information, see [Configuring package ecosystem support for your enterprise](/en/enterprise-server@3.20/admin/packages/configuring-package-ecosystem-support-for-your-enterprise).

## Step 5: Ensure you have a TLS certificate for your package host URL, if needed

If subdomain isolation is enabled for your GitHub Enterprise Server instance, you will need to create and upload a TLS certificate that allows the package host URL for each ecosystem you want to use, such as `containers.HOSTNAME`. Make sure each package host URL includes `https://`.

You can create the certificate manually, or you can use *Let's Encrypt*. If you already use *Let's Encrypt*, you must request a new TLS certificate after enabling GitHub Packages. For more information about package host URLs, see [Enabling subdomain isolation](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/enabling-subdomain-isolation). For more information about uploading TLS certificates to GitHub Enterprise Server, see [Configuring TLS](/en/enterprise-server@3.20/admin/configuration/configuring-network-settings/configuring-tls).

## Step 6: Check for and rename reserved names

If you want to use the Docker ecosystem with subdomain isolation disabled, you **must** first rename any user or organization named `v2` on your GitHub Enterprise Server instance, prior to enabling Docker ecosystem support in the Management Console. Docker uses a `v2` account name to manage path conflicts with the Docker API, and once Docker registry support is enabled, you won't be able to use this name anymore.

You can view a full list of logins reserved for internal use by navigating to the "Reserved logins" page in the Site admin dashboard. For more information, see [Administering your instance from the web UI](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/site-admin-dashboard#reserved-logins).