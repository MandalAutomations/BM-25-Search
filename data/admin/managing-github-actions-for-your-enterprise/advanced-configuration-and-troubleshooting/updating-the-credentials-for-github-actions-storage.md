# Updating the credentials for GitHub Actions storage

If your credentials for connecting to GitHub Actions storage change, you must update the credentials in the configuration on GitHub Enterprise Server.

## Updating the credential secret for your storage provider

To update the credential secret for your GitHub Actions storage provider on GitHub Enterprise Server, you have two options.

> \[!WARNING]
> This process is only for updating the secret key used to authenticate to your existing external storage provider. It assumes that your networking configuration, storage provider, and storage account remain unchanged.
>
> Do not use this process to switch between credential-based and OIDC-based authentication in the management console. Changing the authentication method for GitHub Actions storage may result in data loss.

1. Enable maintenance mode on the server.
2. Update the secret or obtain the updated secret from the storage provider.
3. Use the UI or CLI option below to update the GitHub Actions storage provider credential for GitHub Enterprise Server.

### Updating the credential secret using the management console

1. Navigate to the Actions section of the **Management Console**. For more information, see [Accessing the Management Console](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-web-ui/accessing-the-management-console).
2. Update the secret, or in the case of Azure Blob storage, the secret within the connection string, and then click `Test storage settings` to confirm that GitHub Enterprise Server is still able to successfully connect to the storage.
3. Click `Save settings` and wait for the services to fully restart.

### Updating the credential secret using the command line

1. Run the `ghe-actions-precheck` command to test the new Actions storage credentials and update the configuration on your GitHub Enterprise Server. For more information, see [Command-line utilities](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/command-line-utilities#ghe-actions-precheck)
2. After the Actions storage connection test is successful, you'll prompted to type `Yes` or `No` to configure Actions storage with these settings. Type `Yes` and Enter.
3. You'll see a prompt about overwriting the existing Actions storage configuration. Type `Yes` and Enter.

## Identifying authentication failures for GitHub Actions storage

If GitHub Enterprise Server can't connect to your GitHub Actions storage provider because of an incorrect secret or connection string, you'll see an `Access Denied` or authentication-related exception. This exception can appear in two situations:

* When running `ghe-check-blob-connection`, the command will report the authentication failure directly in its output.
* When `ghe-config-apply` runs, either triggered by clicking "Save settings" in the management console, or by running `ghe-config-apply` manually from the command line. The exception will appear in the `/data/user/common/ghe-config.log` file. When this occurs, `ghe-config-apply` won't complete, which can cause an unexpected outage of services on your appliance.

Once the storage provider configuration on GitHub Enterprise Server is updated with the correct secret or connection string, you can run `ghe-config-apply` to ensure the job re-runs and completes successfully.

> \[!NOTE] Connection failures can also result from other causes, such as network issues or misconfigured storage endpoints. If the error doesn't appear to be authentication-related, review the full error output for additional details.

For more information on `ghe-check-blob-connection`, see [Command-line utilities](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/command-line-utilities#ghe-check-blob-connection).
For more information on `ghe-config-apply`, see [Command-line utilities](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/command-line-utilities#ghe-config-apply).