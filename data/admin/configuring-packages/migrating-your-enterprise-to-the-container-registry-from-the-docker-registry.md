# Migrating your enterprise to the Container registry from the Docker registry

You can migrate Docker images previously stored in the Docker registry on GitHub.com to the Container registry.

> \[!NOTE] Container registry is currently in public preview for GitHub Enterprise Server and subject to change.

Both GitHub Packages and subdomain isolation must be enabled to use Container registry. For more information, see [Working with the Container registry](/en/enterprise-server@3.20/packages/working-with-a-github-packages-registry/working-with-the-container-registry).

## About the Container registry

The Container registry stores container images within your organization or personal account, and allows you to associate an image with a repository. You can choose whether to inherit permissions from a repository, or set granular permissions independently of a repository. You can also access public container images anonymously. For more information, see [Working with the Container registry](/en/enterprise-server@3.20/packages/working-with-a-github-packages-registry/working-with-the-container-registry).

For more information about configuring GitHub Packages for your GitHub Enterprise Server instance, see [Getting started with GitHub Packages for your enterprise](/en/enterprise-server@3.20/admin/packages/getting-started-with-github-packages-for-your-enterprise).

## About migration from the Docker registry

The Container registry replaces GitHub's Docker registry. If the Docker registry on your GitHub Enterprise Server instance contains images, you must manually migrate the images to the Container registry.

> \[!NOTE] GitHub Enterprise Server 3.6 supports migration for Docker images stored in organizations. A future release will support migration of user-owned images.

Any scripts or GitHub Actions workflows that use the namespace for the Docker registry, <code>docker.<em>HOSTNAME</em></code>, will continue to work after migration to the Container registry at <code>containers.<em>HOSTNAME</em></code>. For more information about the impact of migration to the Container registry, see [Migrating to the Container registry from the Docker registry](/en/enterprise-server@3.20/packages/working-with-a-github-packages-registry/migrating-to-the-container-registry-from-the-docker-registry#about-migration-from-the-docker-registry).

## Migrating organizations to the Container registry

You can start a migration of all your organizations' Docker images to the Container registry. The duration of the migration operation depends on the total number of images to migrate, and the overall load on your instance. After a successful migration, GitHub Enterprise Server will display a summary, and all future uploads of Docker images will use the Container registry.

If a site administrator has configured email notifications for your GitHub Enterprise Server instance, you will receive an email after the migration is complete. For more information, see [Configuring email for notifications](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/configuring-email-for-notifications).

### During the migration

During the migration, the CPU and memory usage for your instance will increase. To ensure the performance of the instance for your users, GitHub recommends that you begin a migration during a period of reduced activity.

> \[!WARNING] Do not modify settings for your enterprise or run `ghe-config-apply` from an administrative SSH session. These actions will trigger a configuration run, which can restart services and may interrupt the migration.

### After the migration

After the migration, storage pressure on your instance will increase due to the duplication of image files in the Docker registry and the Container registry. A future release of GitHub Enterprise Server will remove the duplicated files when all migrations are complete.

For more information about monitoring the performance and storage of your GitHub Enterprise Server instance, see [About the monitor dashboards](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/about-the-monitor-dashboards).

### Starting a migration

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. In the left sidebar, click **Packages**.
4. To the right of the number of packages to migrate, click **Start migration**. During the migration, GitHub Enterprise Server will display progress on this page.

After the migration completes, the page will display the results. If a migration fails, the page will show the organizations that own the package that caused the failure.

## Re-running a failed organization migration

Prior to migration, if a user has created a package in the Container registry that has an identical name to an existing package in the Docker registry, the migration will fail.

1. Delete the affected container in the Container registry. For more information, see [Deleting and restoring a package](/en/enterprise-server@3.20/packages/learn-github-packages/deleting-and-restoring-a-package#deleting-a-version-of-an-organization-scoped-package-on-github).

2. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.

3. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.

4. In the left sidebar, click **Packages**.

5. To the right of the number of packages to migrate, click **Re-run migration**. During the migration, GitHub Enterprise Server will display progress on this page.

6. If the migration fails again, start from step 1 and re-run the migration.