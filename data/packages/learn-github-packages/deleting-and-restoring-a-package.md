# Deleting and restoring a package

Learn how to delete or restore a package.

<!-- 2148AF7B-5FF8-4B28-A808-D692FEE2225A -->

## Package deletion and restoration support on GitHub

On GitHub if you have the required access, you can delete:

* An entire private package
* An entire public package, if there's not more than 5000 downloads of any version of the package
* A specific version of a private package
* A specific version of a public package, if the package version doesn't have more than 5,000 downloads

> \[!NOTE]
>
> * You cannot delete a public package if any version of the package has more than 5,000 downloads. In this scenario, contact us through the [GitHub Support portal](https://support.github.com/) for further assistance.
> * When deleting public packages, be aware that you may break projects that depend on your package.

On GitHub, you can also restore an entire package or package version, if:

* You restore the package within 30 days of its deletion.
* The same package namespace is still available and not used for a new package.

## Packages API support

> \[!NOTE]
> GitHub Packages only supports authentication using a personal access token (classic). For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

You can use the REST API to manage your packages. For more information, see the [REST API endpoints for packages](/en/rest/packages).

> \[!NOTE]
> The ability for GitHub Actions workflows to delete and restore packages using the REST API is currently in public preview and subject to change.

With registries that support granular permissions, you can use a `GITHUB_TOKEN` in a GitHub Actions workflow to delete or restore packages using the REST API. The token must have `admin` permission to the package. If your workflow publishes a package, the `admin` role is granted by default to the repository where the workflow is stored. For existing packages not published by a workflow, you need to grant the repository the `admin` role to be able to use a GitHub Actions workflow to delete or restore packages using the REST API. For more information, see [Configuring a package's access control and visibility](/en/packages/learn-github-packages/configuring-a-packages-access-control-and-visibility#ensuring-workflow-access-to-your-package).

For certain registries, you can use GraphQL to delete a version of a private package.

You cannot use the GitHub Packages GraphQL API with registries that support granular permissions. For the registries that **only** support repository-scoped permissions, and can be used with the GraphQL API, see [About permissions for GitHub Packages](/en/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages).

## Required permissions to delete or restore a package

With registries that support granular permissions, you can choose to allow packages to be scoped to a user or an organization, or linked to a repository.

To delete a package that has granular permissions separate from a repository, such as container images stored at `https://ghcr.io/NAMESPACE/PACKAGE-NAME` or packages stored at `https://npm.pkg.github.com/NAMESPACE/PACKAGE-NAME` (where `NAMESPACE` is the name of the personal account or organization to which the package is scoped), you must have admin access to the package. For more information, see [About permissions for GitHub Packages](/en/packages/learn-github-packages/about-permissions-for-github-packages).

For packages that inherit their access permissions from repositories, you can delete a package if you have admin permissions to the repository.

Some registries **only** support repository-scoped packages. For a list of these registries, see [About permissions for GitHub Packages](/en/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages).

## Deleting a package version

### Deleting a version of a repository-scoped package on GitHub

To delete a version of a repository-scoped package, you must have admin permissions to the repository in which the package is published. For more information, see [Required permissions](#required-permissions-to-delete-or-restore-a-package).

1. On GitHub, navigate to the main page of the repository.

2. In the right sidebar of your repository, click **Packages**.

   ![Screenshot of the sidebar of a repository page. The "Packages" section is outlined in orange.](/assets/images/help/package-registry/packages-from-repo.png)

3. Search for and then click the name of the package that you want to manage.

4. Under the "Recent Versions" list of packages, click **View and manage all versions**.
   ![Screenshot of a package's "Recent Versions" section. Underneath, the "View and manage all versions" link is highlighted with an orange outline.](/assets/images/help/package-registry/packages-recent-versions-manage-link.png)

5. In the list of packages, find the version of the package that you want to delete.
   * *If your package is a container*, to the right of the package version click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="kebab-horizontal" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then select **Delete version** from the dropdown menu.
     ![Screenshot of a package version kebab button, expanded to show the menu. The "Delete version" link in the menu is outlined in orange.](/assets/images/help/package-registry/delete-container-package-version.png)
   * *For types of packages other than containers*, to the right of the package version click **Delete**.
     ![Screenshot of a package version with a "Delete" button. The button is highlighted with an orange outline.](/assets/images/help/package-registry/delete-noncontainer-package-version.png)

6. To confirm deletion, type the package name and click **I understand the consequences, delete this version**.

### Deleting a version of a repository-scoped package with GraphQL

For certain registries, you can use GraphQL to delete a version of a private package.

You cannot use the GitHub Packages GraphQL API with registries that support granular permissions. For the registries that **only** support repository-scoped permissions, and can be used with the GraphQL API, see [About permissions for GitHub Packages](/en/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages). For information on using the REST API instead, see the [REST API endpoints for packages](/en/rest/packages).

Use the `deletePackageVersion` mutation in the GraphQL API. You must use a personal access token (classic) with the `read:packages`, `delete:packages`, and `repo` scopes. For more information about personal access tokens (classic), see [Introduction to GitHub Packages](/en/packages/learn-github-packages/introduction-to-github-packages#authenticating-to-github-packages).

The following example demonstrates how to delete a package version, using a `packageVersionId` of `MDIyOlJlZ2lzdHJ5UGFja2FnZVZlcnNpb243MTExNg`.

```shell
curl -X POST \
-H "Accept: application/vnd.github.package-deletes-preview+json" \
-H "Authorization: bearer TOKEN" \
-d '{"query":"mutation { deletePackageVersion(input:{packageVersionId:\"MDIyOlJlZ2lzdHJ5UGFja2FnZVZlcnNpb243MTExNg==\"}) { success }}"}' \
HOSTNAME/graphql
```

To find all of the private packages you have published to GitHub Packages, along with the version IDs for the packages, you can use the `packages` connection through the `repository` object. You will need a personal access token (classic) with the `read:packages` and `repo` scopes. For more information, see the [`packages`](/en/graphql/reference/objects#repository) connection or the [`PackageOwner`](/en/graphql/reference/interfaces#packageowner) interface.

For more information about the `deletePackageVersion` mutation, see [Mutations](/en/graphql/reference/mutations#deletepackageversion).

You cannot directly delete an entire package using GraphQL, but if you delete every version of a package, the package will no longer show on GitHub.

### Deleting a version of a user-scoped package on GitHub

To delete a specific version of a user-scoped package on GitHub, such as for a Docker image at `ghcr.io`, use these steps. To delete an entire package, see [Deleting an entire user-scoped package on GitHub](#deleting-an-entire-user-scoped-package-on-github).

To review who can delete a package version, see [Required permissions](#required-permissions-to-delete-or-restore-a-package).

1. On GitHub, navigate to the main page of your personal account.

2. In the top right corner of GitHub, click your profile picture, then click **Your profile**.

   ![Screenshot of the dropdown menu under @octocat's profile picture. "Your profile" is outlined in dark orange.](/assets/images/help/profile/profile-button-avatar-menu-global-nav-update.png)

3. On your profile page, in the header, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-package" aria-label="package" role="img"><path d="m8.878.392 5.25 3.045c.54.314.872.89.872 1.514v6.098a1.75 1.75 0 0 1-.872 1.514l-5.25 3.045a1.75 1.75 0 0 1-1.756 0l-5.25-3.045A1.75 1.75 0 0 1 1 11.049V4.951c0-.624.332-1.201.872-1.514L7.122.392a1.75 1.75 0 0 1 1.756 0ZM7.875 1.69l-4.63 2.685L8 7.133l4.755-2.758-4.63-2.685a.248.248 0 0 0-.25 0ZM2.5 5.677v5.372c0 .09.047.171.125.216l4.625 2.683V8.432Zm6.25 8.271 4.625-2.683a.25.25 0 0 0 .125-.216V5.677L8.75 8.432Z"></path></svg> Packages** tab.

4. Search for and then click the name of the package that you want to manage.

5. Under the "Recent Versions" list of packages, click **View and manage all versions**.
   ![Screenshot of a package's "Recent Versions" section. Underneath, the "View and manage all versions" link is highlighted with an orange outline.](/assets/images/help/package-registry/packages-recent-versions-manage-link.png)

6. In the list of packages, find the version of the package that you want to delete.
   * *If your package is a container*, to the right of the package version click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="kebab-horizontal" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then select **Delete version** from the dropdown menu.
     ![Screenshot of a package version kebab button, expanded to show the menu. The "Delete version" link in the menu is outlined in orange.](/assets/images/help/package-registry/delete-container-package-version.png)
   * *For types of packages other than containers*, to the right of the package version click **Delete**.
     ![Screenshot of a package version with a "Delete" button. The button is highlighted with an orange outline.](/assets/images/help/package-registry/delete-noncontainer-package-version.png)

7. In the confirmation box, type the name of the package to confirm you want to delete the chosen version of it.

8. Click **I understand the consequences, delete this version**.

### Deleting a version of an organization-scoped package on GitHub

To delete a specific version of an organization-scoped package on GitHub, such as for a Docker image at `ghcr.io`, use these steps.
To delete an entire package, see [Deleting an entire organization-scoped package on GitHub](#deleting-an-entire-organization-scoped-package-on-github).

To review who can delete a package version, see [Required permissions to delete or restore a package](#required-permissions-to-delete-or-restore-a-package).

1. On GitHub, navigate to the main page of your organization.

2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-package" aria-label="package" role="img"><path d="m8.878.392 5.25 3.045c.54.314.872.89.872 1.514v6.098a1.75 1.75 0 0 1-.872 1.514l-5.25 3.045a1.75 1.75 0 0 1-1.756 0l-5.25-3.045A1.75 1.75 0 0 1 1 11.049V4.951c0-.624.332-1.201.872-1.514L7.122.392a1.75 1.75 0 0 1 1.756 0ZM7.875 1.69l-4.63 2.685L8 7.133l4.755-2.758-4.63-2.685a.248.248 0 0 0-.25 0ZM2.5 5.677v5.372c0 .09.047.171.125.216l4.625 2.683V8.432Zm6.25 8.271 4.625-2.683a.25.25 0 0 0 .125-.216V5.677L8.75 8.432Z"></path></svg> Packages** tab.

   ![Screenshot of @octo-org's profile page. The "Packages" tab is highlighted with an orange outline.](/assets/images/help/package-registry/org-tab-for-packages-with-overview-tab.png)

3. Search for and then click the name of the package that you want to manage.

4. Under the "Recent Versions" list of packages, click **View and manage all versions**.
   ![Screenshot of a package's "Recent Versions" section. Underneath, the "View and manage all versions" link is highlighted with an orange outline.](/assets/images/help/package-registry/packages-recent-versions-manage-link.png)

5. In the list of packages, find the version of the package that you want to delete.
   * *If your package is a container*, to the right of the package version click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="kebab-horizontal" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then select **Delete version** from the dropdown menu.
     ![Screenshot of a package version kebab button, expanded to show the menu. The "Delete version" link in the menu is outlined in orange.](/assets/images/help/package-registry/delete-container-package-version.png)
   * *For types of packages other than containers*, to the right of the package version click **Delete**.
     ![Screenshot of a package version with a "Delete" button. The button is highlighted with an orange outline.](/assets/images/help/package-registry/delete-noncontainer-package-version.png)

6. In the confirmation box, type the name of the package to confirm you want to delete the chosen version of it.

7. Click **I understand the consequences, delete this version**.

## Deleting an entire package

### Deleting an entire repository-scoped package on GitHub

To delete an entire repository-scoped package, you must have admin permissions to the repository that owns the package. For more information, see [Required permissions](#required-permissions-to-delete-or-restore-a-package).

1. On GitHub, navigate to the main page of the repository.
2. In the right sidebar of your repository, click **Packages**.

   ![Screenshot of the sidebar of a repository page. The "Packages" section is outlined in orange.](/assets/images/help/package-registry/packages-from-repo.png)
3. Search for and then click the name of the package that you want to manage.
4. On your package's landing page, on the right-hand side, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Package settings**.

   ![Screenshot of a package's landing page. In the lower right corner, "Package settings" is highlighted with an orange outline.](/assets/images/help/package-registry/package-settings.png)
5. At the bottom of the page, under "Danger Zone", click **Delete this package**.
6. To confirm, review the confirmation message, enter your package name, and click **I understand, delete this package.**

### Deleting an entire user-scoped package on GitHub

To review who can delete a package, see [Required permissions](#required-permissions-to-delete-or-restore-a-package).

1. On GitHub, navigate to the main page of your personal account.

2. In the top right corner of GitHub, click your profile picture, then click **Your profile**.

   ![Screenshot of the dropdown menu under @octocat's profile picture. "Your profile" is outlined in dark orange.](/assets/images/help/profile/profile-button-avatar-menu-global-nav-update.png)

3. On your profile page, in the header, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-package" aria-label="package" role="img"><path d="m8.878.392 5.25 3.045c.54.314.872.89.872 1.514v6.098a1.75 1.75 0 0 1-.872 1.514l-5.25 3.045a1.75 1.75 0 0 1-1.756 0l-5.25-3.045A1.75 1.75 0 0 1 1 11.049V4.951c0-.624.332-1.201.872-1.514L7.122.392a1.75 1.75 0 0 1 1.756 0ZM7.875 1.69l-4.63 2.685L8 7.133l4.755-2.758-4.63-2.685a.248.248 0 0 0-.25 0ZM2.5 5.677v5.372c0 .09.047.171.125.216l4.625 2.683V8.432Zm6.25 8.271 4.625-2.683a.25.25 0 0 0 .125-.216V5.677L8.75 8.432Z"></path></svg> Packages** tab.

4. Search for and then click the name of the package that you want to manage.

5. On your package's landing page, on the right-hand side, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Package settings**.

   ![Screenshot of a package's landing page. In the lower right corner, "Package settings" is highlighted with an orange outline.](/assets/images/help/package-registry/package-settings.png)

6. At the bottom of the page, under "Danger zone", click **Delete this package**.

7. In the confirmation box, type the name of the package to confirm you want to delete it.

8. Click **I understand the consequences, delete this package**.

### Deleting an entire organization-scoped package on GitHub

To review who can delete a package, see [Required permissions](#required-permissions-to-delete-or-restore-a-package).

1. On GitHub, navigate to the main page of your organization.

2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-package" aria-label="package" role="img"><path d="m8.878.392 5.25 3.045c.54.314.872.89.872 1.514v6.098a1.75 1.75 0 0 1-.872 1.514l-5.25 3.045a1.75 1.75 0 0 1-1.756 0l-5.25-3.045A1.75 1.75 0 0 1 1 11.049V4.951c0-.624.332-1.201.872-1.514L7.122.392a1.75 1.75 0 0 1 1.756 0ZM7.875 1.69l-4.63 2.685L8 7.133l4.755-2.758-4.63-2.685a.248.248 0 0 0-.25 0ZM2.5 5.677v5.372c0 .09.047.171.125.216l4.625 2.683V8.432Zm6.25 8.271 4.625-2.683a.25.25 0 0 0 .125-.216V5.677L8.75 8.432Z"></path></svg> Packages** tab.

   ![Screenshot of @octo-org's profile page. The "Packages" tab is highlighted with an orange outline.](/assets/images/help/package-registry/org-tab-for-packages-with-overview-tab.png)

3. Search for and then click the name of the package that you want to manage.

4. On your package's landing page, on the right-hand side, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Package settings**.

   ![Screenshot of a package's landing page. In the lower right corner, "Package settings" is highlighted with an orange outline.](/assets/images/help/package-registry/package-settings.png)

5. At the bottom of the page, under "Danger zone", click **Delete this package**.

6. In the confirmation box, type the name of the package to confirm you want to delete it.

7. Click **I understand the consequences, delete this package**.

## Restoring packages

You can restore a deleted package or version if:

* You restore the package within 30 days of its deletion.
* The same package namespace and version is still available and not reused for a new package.

For example, if you're the user `octocat`, and you have a deleted RubyGems package named `my-package` that was scoped to the repo `octocat/my-repo`, then you can only restore the package if the package namespace `rubygem.pkg.github.com/octocat/my-repo/my-package` is still available, and 30 days have not yet passed.

To restore a deleted package, you must also meet one of these permission requirements:

* For repository-scoped packages: You have admin permissions to the repository in which the deleted package is published.
* For user-account scoped packages: The deleted package is scoped to your personal account.
* For organization-scoped packages: You have admin permissions to the deleted package in the organization to which the package is scoped.

For more information, see [Required permissions](#required-permissions-to-delete-or-restore-a-package).

Once the package is restored, the package will use the same namespace it did before. If the same package namespace is not available, you will not be able to restore your package. In this scenario, to restore the deleted package, you must delete the new package that uses the deleted package's namespace first.

### Restoring a package in an organization

You can restore a deleted package through your organization account settings, as long as the package was in a repository owned by the organization or had granular permissions and was scoped to your organization account.

To review who can restore a package in an organization, see [Required permissions](#required-permissions-to-delete-or-restore-a-package).

1. On GitHub, navigate to the main page of the organization.
2. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)
3. On the left, click **Packages**.
4. Under "Deleted Packages", next to the package you want to restore, click **Restore**.
5. To confirm, type the name of the package and click **I understand the consequences, restore this package**.

### Restoring a user-account scoped package

You can restore a deleted package through your personal account settings, if the package was in one of your repositories or scoped to your personal account. For more information, see [Required permissions](#required-permissions-to-delete-or-restore-a-package).

1. In the upper-right corner of any page on GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**.
2. In the left sidebar, click **Packages**.
3. Under "Deleted Packages", next to the package you want to restore, click **Restore**.
4. To confirm, type the name of the package and click **I understand the consequences, restore this package**.

### Restoring a package version

You can restore a package version from your package's landing page. To review who can restore a package, see [Required permissions](#required-permissions-to-delete-or-restore-a-package).

1. Navigate to your package's landing page.

2. Search for and then click the name of the package that you want to manage.

3. On your package's landing page, on the right-hand side, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Package settings**.

   ![Screenshot of a package's landing page. In the lower right corner, "Package settings" is highlighted with an orange outline.](/assets/images/help/package-registry/package-settings.png)

4. Under the "Recent Versions" list of packages, click **View and manage all versions**.
   ![Screenshot of a package's "Recent Versions" section. Underneath, the "View and manage all versions" link is highlighted with an orange outline.](/assets/images/help/package-registry/packages-recent-versions-manage-link.png)

5. At the top right corner of the list of package versions, use the **Select versions view** dropdown and select **Deleted**.

   ![Screenshot of a list of package versions. The "Deleted" selection in the versions view is highlighted with an orange outline.](/assets/images/help/package-registry/versions-drop-down-menu.png)

6. Next to the deleted package version you want to restore, click **Restore**.

7. To confirm, click **I understand the consequences, restore this version.**