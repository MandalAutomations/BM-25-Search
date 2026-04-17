# Setting repository visibility

You can choose who can view your repository.

## About repository visibility changes

> \[!NOTE]
> If you can't change a repository's visibility, the organization owner may have restricted the ability to change repository visibility to organization owners only. For more information, see [Restricting repository visibility changes in your organization](/en/organizations/managing-organization-settings/restricting-repository-visibility-changes-in-your-organization).

We recommend reviewing the following caveats before you change the visibility of a repository.

### Making a repository private

* GitHub will detach public forks of the public repository and put them into a new network. Public forks are not made private.
* If you're using GitHub Free for personal accounts or organizations, some features won't be available in the repository after you change the visibility to private. Any published GitHub Pages site will be automatically unpublished. If you added a custom domain to the GitHub Pages site, you should remove or update your DNS records before making the repository private, to avoid the risk of a domain takeover. For more information, see [GitHub's plans](/en/get-started/learning-about-github/githubs-plans) and [Managing a custom domain for your GitHub Pages site](/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).
* GitHub will no longer include the repository in the GitHub Archive Program. For more information, see [About archiving content and data on GitHub](/en/repositories/archiving-a-github-repository/about-archiving-content-and-data-on-github#about-the-github-archive-program).
* GitHub Advanced Security features, such as code scanning, will stop working unless the repository is owned by an organization that has access to the feature in private repositories with a GitHub Advanced Security, GitHub Code Security, or GitHub Secret Protection license and sufficient spare seats. For more information, see [About GitHub Advanced Security](/en/get-started/learning-about-github/about-github-advanced-security).

### Making a repository public

* GitHub will detach private forks and turn them into a standalone private repository. For more information, see [What happens to forks when a repository is deleted or changes visibility?](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/what-happens-to-forks-when-a-repository-is-deleted-or-changes-visibility#changing-a-private-repository-to-a-public-repository)
* If you're converting your private repository to a public repository as part of a move toward creating an open source project, see the [Open Source Guides](http://opensource.guide) for helpful tips and guidelines. You can also take a free course on managing an open source project with [GitHub Skills](https://skills.github.com/). Once your repository is public, you can also view your repository's community profile to see whether your project meets best practices for supporting contributors. For more information, see [About community profiles for public repositories](/en/communities/setting-up-your-project-for-healthy-contributions/about-community-profiles-for-public-repositories).
* The repository will automatically gain access to GitHub Advanced Security features.
* Actions history and logs will be visible to everyone. If your repository had reusable or required workflows that were shared from a different repository in your organization, the workflow file path including the repository name will be visible in the logs. For more information on how to remove workflow runs and artifacts see [Managing workflow runs](/en/actions/managing-workflow-runs#deleting-logs) and [REST API endpoints for workflow runs](/en/rest/actions/workflow-runs).

For information about improving repository security, see [Quickstart for securing your repository](/en/code-security/getting-started/securing-your-repository).

## Consequences of changing a repository's visibility

> \[!CAUTION]Before you change your repository's visibility, understand the consequences of this change.

### Changing from public to private

* Stars and watchers for this repository will be erased, which will affect repository rankings.
* Custom Dependabot alert rules will be disabled unless GitHub Code Security is enabled for this repository. Dependency graph and Dependabot alerts will remain enabled with permission to perform read-only analysis on this repository.

> - Code scanning will become unavailable unless Code Security is enabled for this repository.

* Current forks will remain public and will be detached from this repository.

### Changing from private to public

* The code will be visible to everyone who can visit GitHub.com.
* Anyone can fork your repository.
* All push rulesets will be disabled.
* Your changes will be published as activity.
* Actions history and logs will be visible to everyone.
* Stars and watchers for this repository will be erased.

### Changing from private to internal

* All members of the enterprise will be given read access.
* Outside collaborators can no longer be added to forks unless they're added to the root.
* Stars and watchers for this repository will be erased.

### Changing from internal to private

* Stars and watchers for this repository will be erased, which will affect repository rankings.
* Custom Dependabot alert rules will be disabled unless GitHub Code Security is enabled for this repository. Dependency graph and Dependabot alerts will remain enabled with permission to perform read-only analysis on this repository.

> - Code scanning will become unavailable unless Code Security is enabled for this repository.

* Current forks will remain public and will be detached from this repository.

### Changing from internal to public

* The code will be visible to everyone who can visit GitHub.com.
* Anyone can fork your repository.
* All push rulesets will be disabled.
* Your changes will be published as activity.
* Actions history and logs will be visible to everyone.
* Stars and watchers for this repository will be erased.

### Changing from public to internal

* All members of the enterprise will be given read access.
* Outside collaborators can no longer be added to forks unless they're added to the root.
* Stars and watchers for this repository will be erased.

## Changing a repository's visibility

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)
3. In the "Danger Zone" section, to the right of to "Change repository visibility", click **Change visibility**.
4. Select a visibility.
5. Click to confirm that you are changing the visibility of the correct repository.
6. Click **I have read and understand these effects**.
7. Click **Make this repository public** or **Make this repository private**.

## Further reading

* [About repositories](/en/repositories/creating-and-managing-repositories/about-repositories#about-repository-visibility)