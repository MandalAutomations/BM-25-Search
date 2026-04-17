# Enabling GitHub Advanced Security products for your enterprise

You can configure GitHub Enterprise Server to include GitHub Advanced Security products. This provides extra features that help users find and fix security problems in their code.

## About enabling GitHub Advanced Security products

GitHub Advanced Security features help developers improve and maintain the security and quality of code. For more information, see [About GitHub Advanced Security](/en/enterprise-server@3.20/get-started/learning-about-github/about-github-advanced-security).

When you enable GitHub Advanced Security for your enterprise, repository administrators in all organizations can enable the features unless you set up a policy to restrict access. See [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-server@3.20/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-code-security-and-analysis-for-your-enterprise).

You can also enable or disable GitHub Secret Protection or GitHub Code Security features via the API. For more information, see [REST API endpoints for secret scanning](/en/enterprise-server@3.20/rest/secret-scanning#enable-or-disable-security-features-for-an-enterprise) in the REST API documentation.

For guidance on a phased deployment of GitHub Advanced Security, see [Introduction to adopting GitHub Advanced Security at scale](/en/enterprise-server@3.20/code-security/adopting-github-advanced-security-at-scale/introduction-to-adopting-github-advanced-security-at-scale).

## Checking whether your license includes Advanced Security

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. Under **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**, click **License**.
4. If your license includes GitHub Secret Protection, GitHub Code Security, or GitHub Advanced Security, the license page includes a section showing details of current usage.

## Prerequisites for enabling Secret Protection and Code Security

1. Upgrade your GitHub Enterprise license to include Secret Protection and Code Security. For information about licensing, see [GitHub Advanced Security license billing](/en/enterprise-server@3.20/billing/managing-billing-for-your-products/managing-billing-for-github-advanced-security/about-billing-for-github-advanced-security).
2. Download the new license file. See [Downloading your license for GitHub Enterprise](/en/enterprise-server@3.20/billing/managing-your-license-for-github-enterprise/downloading-your-license-for-github-enterprise).
3. Upload the new license file to GitHub Enterprise Server. See [Uploading a new license to GitHub Enterprise Server](/en/enterprise-server@3.20/billing/managing-your-license-for-github-enterprise/uploading-a-new-license-to-github-enterprise-server).
4. Review the prerequisites for the features you plan to enable.

   * Code scanning, see [Configuring code scanning for your appliance](/en/enterprise-server@3.20/admin/code-security/managing-github-advanced-security-for-your-enterprise/configuring-code-scanning-for-your-appliance#prerequisites-for-code-scanning).
   * Secret scanning, see [Configuring secret scanning for your appliance](/en/enterprise-server@3.20/admin/code-security/managing-github-advanced-security-for-your-enterprise/configuring-secret-scanning-for-your-appliance#prerequisites-for-secret-scanning).
   * Dependabot, see [Enabling Dependabot for your enterprise](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/enabling-dependabot-for-your-enterprise).

## Enabling and disabling Advanced Security features

> \[!WARNING]
>
> * Changing this setting will cause user-facing services on GitHub Enterprise Server to restart. You should time this change carefully, to minimize downtime for users.
> * You should communicate any changes you plan to make to feature enablement settings to organization owners before making them, so as not to impact existing security configurations that have been rolled out by organizations in your enterprise.

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the "Settings" sidebar, click **Security**.

5. Under "Security," select the features that you want to enable and deselect any features you want to disable.

6. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

7. Wait for the configuration run to complete.

When GitHub Enterprise Server has finished restarting, you're ready to set up any additional resources required for newly enabled features. See [Configuring code scanning for your appliance](/en/enterprise-server@3.20/admin/code-security/managing-github-advanced-security-for-your-enterprise/configuring-code-scanning-for-your-appliance).

## Enabling or disabling Advanced Security features via the administrative shell (SSH)

You can enable or disable features programmatically on GitHub Enterprise Server. For more information about the administrative shell and command-line utilities for GitHub Enterprise Server, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh) and [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-config).

For example, you can enable any Advanced Security feature with your infrastructure-as-code tooling when you deploy an instance for staging or disaster recovery.

1. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

2. Enable features for Advanced Security.

   * To enable code scanning, enter the following commands.

     ```shell copy
     ghe-config app.minio.enabled true
     ghe-config app.code-scanning.enabled true
     ```

   * To enable secret scanning, enter the following command.

     ```shell copy
     ghe-config app.secret-scanning.enabled true
     ```

   * Optionally, to enable validity checks for secret scanning:
     * Enter the following command:

       ```shell copy
       ghe-config app.secret-scanning.validity-checks-available-on-instance true`
       ```

     * To check whether outbound connection is possible, use:

       ```shell copy
       /usr/local/share/enterprise/ghe-secret-scanning-validity-checks-connection-test
       ```

   * To enable the dependency graph, enter the following command.

     ```shell copy
     ghe-config app.dependency-graph.enabled true
     ```

3. Optionally, disable features for Advanced Security.

   * To disable code scanning, enter the following commands.

     ```shell copy
     ghe-config app.code-scanning.enabled false
     ```

     * Optionally, if you disable code scanning, you can also disable the internal MinIO service for Advanced Security. If Dependabot updates are enabled for the instance and you want to disable this service, you must also disable Dependabot updates. Disabling the service does not affect MinIO storage for GitHub Actions or GitHub Packages. For more information about Dependabot updates, see [Enabling Dependabot for your enterprise](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/enabling-dependabot-for-your-enterprise).

       * To disable Dependabot updates, enter the following command.

         ```shell copy
         ghe-config app.dependabot.enabled false
         ```

       * To disable MinIO, enter the following command.

         ```shell copy
         ghe-config app.minio.enabled false
         ```

   * To disable secret scanning, enter the following command.

     ```shell copy
     ghe-config app.secret-scanning.enabled false
     ```

   * To disable the dependency graph, enter the following command.

     ```shell
     ghe-config app.dependency-graph.enabled false
     ```

4. To apply the configuration, run the following command.

   > \[!NOTE]
   > During a configuration run, services on your GitHub Enterprise Server instance may restart, which can cause brief downtime for users.

   ```shell copy
   ghe-config-apply
   ```

5. Wait for the configuration run to complete.