# Providing data to GitHub Support

Since GitHub Support doesn't have access to your environment, we sometimes require some additional information from you.

## About diagnostic files and support bundles

To help you troubleshoot issues with a GitHub Enterprise Server instance in your environment, GitHub Support may request one or more types of data.

| Data                    | File format | Description                                                                            |
| :---------------------- | :---------- | :------------------------------------------------------------------------------------- |
| Diagnostic file         | Plaintext   | Contains information about the instance's settings and environment.                    |
| Support bundle          | Archive     | Contains a diagnostics file and sanitized log files from the past two days by default. |
| Extended support bundle | Archive     | Contains a diagnostics file and sanitized log files from the past eight days.          |

## About log file sanitization

Authentication tokens, keys, and secrets are removed from log files in the following log directories contained within a support bundle or diagnostics file:

* `alambic-logs`
* `babeld-logs`
* `codeload-logs`
* `enterprise-manage-logs`
* `github-logs`
* `hookshot-logs`
* `lfs-server-logs`
* `semiotic-logs`
* `task-dispatcher-logs`
* `pages-logs`
* `registry-logs`
* `render-logs`
* `svn-bridge-logs`

## Creating and sharing diagnostic files

Diagnostic files are an overview of a GitHub Enterprise Server instance's settings and environment that contain:

* Client license information, including company name, expiration date, and number of user licenses
* Version numbers and SHAs
* VM architecture
* Host name, private mode, SSL settings
* Load and process listings
* Network settings
* Authentication method and details
* Number of repositories, users, and other installation data

You can download the diagnostics for your instance from the Management Console or by running the `ghe-diagnostics` command-line utility.

### Creating a diagnostic file from the Management Console

You can create a diagnostic file from the Management Console if you don't currently have SSH access.

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
4. If you have created multiple Management Console user accounts, select **Root site admin** or **Management Console user**. For more information about Management Console user accounts see, [Managing access to the Management Console](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console/managing-access-to-the-management-console).
5. Type your Management Console credentials. Then click **Continue**.
6. In the top navigation bar, click **Support**.

   ![Screenshot of the header of the Management Console. A tab, labeled "Support", is highlighted with an orange outline.](/assets/images/enterprise/management-console/support-link.png)
7. Click **Download diagnostics info**.

### Creating a diagnostic file using SSH

You can use this method without signing into the Management Console.

Use the [ghe-diagnostics](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-diagnostics) command-line utility to retrieve the diagnostics for your instance.

```shell
ssh -p122 admin@HOSTNAME -- 'ghe-diagnostics' > diagnostics.txt
```

## Creating and sharing support bundles

After you submit your support request, we may ask you to share a support bundle with our team. The support bundle is a gzip-compressed tar archive that includes diagnostics and important logs from your instance, such as:

* Authentication-related logs that may be helpful when troubleshooting authentication errors, or configuring LDAP, CAS, or SAML

* Management Console log

* `github-logs/exceptions.log`: Information about 500 errors encountered on the site

* `github-logs/audit.log`: GitHub Enterprise Server audit logs

* `babeld-logs/babeld.log`: Git proxy logs

* `system-logs/haproxy.log`: HAProxy logs

* `elasticsearch-logs/github-enterprise.log`: Elasticsearch logs

* `configuration-logs/`: GitHub Enterprise Server configuration logs

* `collectd/logs/collectd.log`: Collectd logs

* `mail-logs/mail.log`: SMTP email delivery logs

For more information, see [Audit log for an enterprise](/en/enterprise-server@3.20/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/about-the-audit-log-for-your-enterprise).

Support bundles include logs from the past two days by default. You can specify an exact duration in days. To provide logs from the past eight days, you can download an extended support bundle. For more information, see [Creating and sharing extended support bundles](#creating-and-sharing-extended-support-bundles).

> \[!TIP]
> When you contact GitHub Support, you'll be sent a confirmation email that will contain a ticket reference link. If GitHub Support asks you to upload a support bundle, you can use the ticket reference link to upload the support bundle.

### Creating a support bundle from the Management Console

You can use these steps to create and share a support bundle if you can access the web-based Management Console and have outbound internet access.

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
4. If you have created multiple Management Console user accounts, select **Root site admin** or **Management Console user**. For more information about Management Console user accounts see, [Managing access to the Management Console](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console/managing-access-to-the-management-console).
5. Type your Management Console credentials. Then click **Continue**.
6. In the top navigation bar, click **Support**.

   ![Screenshot of the header of the Management Console. A tab, labeled "Support", is highlighted with an orange outline.](/assets/images/enterprise/management-console/support-link.png)
7. Click **Download support bundle**.
8. If a support engineer has given you an upload link for your support bundle, use this link. Otherwise, visit <https://support.github.com/> and sign in (if prompted) to an enterprise account that is entitled to support.
9. Visit <https://support.github.com/uploads> and upload your support bundle.

### Creating a support bundle using SSH

You can use these steps to create and share a support bundle if you have SSH access to your GitHub Enterprise Server instance and have outbound internet access.

> \[!NOTE]
> If your GitHub Enterprise Server instance is in a geo-replication configuration, or if your instance is a cluster, you should use the `ghe-cluster-support-bundle` command to retrieve the support bundle. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-cluster-support-bundle).

1. Download the support bundle via SSH:

   ```shell
   ssh -p 122 admin@HOSTNAME -- 'ghe-support-bundle -o' > support-bundle.tgz
   ```

   For more information about the `ghe-support-bundle` command, see [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-support-bundle).
2. If a support engineer has given you an upload link for your support bundle, use this link. Otherwise, visit <https://support.github.com/> and sign in (if prompted) to an enterprise account that is entitled to support.
3. Visit <https://support.github.com/uploads> and upload your support bundle.

### Uploading a support bundle using your enterprise account

1. Navigate to GitHub Enterprise Cloud.
2. In the top-right corner of GitHub, click your profile picture.
3. Depending on your environment, click **Enterprise**, or click **Enterprises** then click the enterprise you want to view.
4. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
5. Under **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**, click **License**.
6. Under "GitHub Enterprise Help", click **Upload a support bundle**.

   ![Screenshot of the "GitHub Enterprise help" section of the enterprise settings page. The "Upload a support bundle link" is outlined in orange.](/assets/images/enterprise/support/upload-support-bundle.png)
7. Under "Select an enterprise account", use the drop-down menu to select the support bundle's associated account.
8. Under "Upload a support bundle for GitHub Enterprise Support", to select your support bundle, click **Choose file**, or drag your support bundle file onto **Choose file**.
9. Click **Upload**.

### Uploading a support bundle directly using SSH

You can directly upload a support bundle to our server if:

* You have SSH access to your GitHub Enterprise Server instance.
* Outbound HTTPS connections over TCP port 443 are allowed from your GitHub Enterprise Server instance to *enterprise-bundles.github.com* and *esbtoolsproduction.blob.core.windows.net*.

1. Upload the bundle to our support bundle server:

   ```shell
   ssh -p122 admin@HOSTNAME -- 'ghe-support-bundle -u'
   ```

## Creating and sharing extended support bundles

Support bundles include logs from the past two days by default, while *extended* support bundles include logs from the past eight days. If the events that GitHub Support is investigating occurred more than two days ago, we may ask you to share an extended support bundle. You will need SSH access to download an extended bundle - you cannot download an extended bundle from the Management Console.

To prevent bundles from becoming too large, bundles only contain logs that haven't been rotated and compressed. Log rotation on GitHub Enterprise Server happens at various frequencies (daily or weekly) for different log files, depending on how large we expect the logs to be.

### Creating an extended support bundle using SSH

You can use these steps to create and share an extended support bundle if you have SSH access to your GitHub Enterprise Server instance and you have outbound internet access.

1. Download the extended support bundle via SSH by adding the `-x` flag to the `ghe-support-bundle` command:

   ```shell
   ssh -p 122 admin@HOSTNAME -- 'ghe-support-bundle -o -x' > support-bundle.tgz
   ```

2. If a support engineer has given you an upload link for your support bundle, use this link. Otherwise, visit <https://support.github.com/> and sign in (if prompted) to an enterprise account that is entitled to support.

3. Visit <https://support.github.com/uploads> and upload your support bundle.

### Uploading an extended support bundle directly using SSH

You can directly upload a support bundle to our server if:

* You have SSH access to your GitHub Enterprise Server instance.
* Outbound HTTPS connections over TCP port 443 are allowed from your GitHub Enterprise Server instance to *enterprise-bundles.github.com* and *esbtoolsproduction.blob.core.windows.net*.

1. Upload the bundle to our support bundle server:

   ```shell
   ssh -p122 admin@HOSTNAME -- 'ghe-support-bundle -u -x'
   ```

## Further reading

* [About GitHub Support](/en/enterprise-server@3.20/support/learning-about-github-support/about-github-support)
* [Generating a Health Check for your enterprise](/en/enterprise-server@3.20/admin/enterprise-management/monitoring-your-appliance/generating-a-health-check-for-your-enterprise)