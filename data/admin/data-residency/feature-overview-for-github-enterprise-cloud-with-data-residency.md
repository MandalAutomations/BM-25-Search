# Feature overview for GitHub Enterprise Cloud with data residency

Learn about the available features on GHE.com, plus features that work differently from GitHub.com.

The features available with data residency on GHE.com are similar to the features available to managed user accounts on GitHub.com, with some additions and exceptions. Some features work differently or require additional configuration compared to the equivalent feature on GitHub.com.

## Available features

GitHub Enterprise Cloud is a developer platform that supports the entire software development lifecycle, including planning work, automating tests and deployments, and keeping code secure. To learn about available features, see [GitHub's plans page](https://github.com/pricing).

## Currently unavailable features

The following features are currently unavailable on GHE.com, but may be planned for future development.

| Feature                                                      | Details                                                                                                                                                                                                                                                          | More information                                                                                                                                                                                             |
| :----------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| macOS runners for GitHub Actions                             | Currently unavailable.                                                                                                                                                                                                                                           | [GitHub-hosted runners](/en/enterprise-cloud@latest/actions/using-github-hosted-runners/about-github-hosted-runners/about-github-hosted-runners)                                                             |
| Maven and Gradle support for GitHub Packages                 | Currently unavailable.                                                                                                                                                                                                                                           | [Working with the Apache Maven registry](/en/enterprise-cloud@latest/packages/working-with-a-github-packages-registry/working-with-the-apache-maven-registry)                                                |
| Repository traffic metrics                                   | Currently unavailable through both the UI and REST API.                                                                                                                                                                                                          | [Viewing traffic to a repository](/en/enterprise-cloud@latest/repositories/viewing-activity-and-data-for-your-repository/viewing-traffic-to-a-repository)                                                    |
| Spark                                                        | Currently unavailable.                                                                                                                                                                                                                                           | [About GitHub Spark](/en/enterprise-cloud@latest/copilot/concepts/spark)                                                                                                                                     |
| GitHub Marketplace                                           | GitHub Marketplace, as a means of searching for, purchasing, and directly installing apps and actions, is unavailable. Ecosystem apps and actions can still be discovered and installed from their source, but they may require modification to work on GHE.com. | [GitHub Actions workflows from GitHub Marketplace](#github-actions-workflows-from-github-marketplace)                                                                                                        |
| Certain features of GitHub Connect                           | Although you can connect an enterprise on GHE.com to a GitHub Enterprise Server instance, certain features of GitHub Connect are not available.                                                                                                                  | [GitHub Connect](#github-connect)                                                                                                                                                                            |
| Some features currently in public preview or private preview | Certain features that are in a preview phase on GitHub.com may not be available on GHE.com until GA.                                                                                                                                                             |                                                                                                                                                                                                              |
| Migrations REST API                                          | Currently unavailable.                                                                                                                                                                                                                                           | [REST API endpoints for migrations](/en/enterprise-cloud@latest/rest/migrations)                                                                                                                             |
| Streaming audit logs to Amazon S3 with OpenID Connect (OIDC) | Currently unavailable.                                                                                                                                                                                                                                           | [Streaming the audit log for your enterprise](/en/enterprise-cloud@latest/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/streaming-the-audit-log-for-your-enterprise) |

## Permanently unavailable features

By design, the following features are permanently unavailable on GHE.com. This is generally because they are not intended for large enterprises with strict compliance requirements.

| Feature                                                        | Details                                                                                                                                                                                                                                                              | More information                                                                                                                                                                            |
| :------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Features unavailable with Enterprise Managed Users             | Because Enterprise Managed Users is the only option for identity management on GHE.com, features that are unavailable with Enterprise Managed Users on GitHub.com are also unavailable on GHE.com. Notably, these include gists and public repositories.             | [Abilities and restrictions of managed user accounts](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/abilities-and-restrictions-of-managed-user-accounts) |
| GitHub Importer (the "Import repository" button on GitHub.com) | Instead, the **GitHub Enterprise Importer** is available to migrate data. See [About GitHub Enterprise Importer](/en/enterprise-cloud@latest/migrations/using-github-enterprise-importer/understanding-github-enterprise-importer/about-github-enterprise-importer). | [About GitHub Importer](/en/enterprise-cloud@latest/migrations/importing-source-code/using-github-importer/about-github-importer)                                                           |

## Features that work differently

The following features are either specific to GHE.com or work differently compared to GitHub.com.

* [API access](#api-access)
* [URL differences](#url-differences)
* [Organization names and usernames](#organization-names-and-usernames)
* [GitHub Actions workflows from GitHub Marketplace](#github-actions-workflows-from-github-marketplace)
* [Retirement of namespaces for actions accessed on GitHub.com](#retirement-of-namespaces-for-actions-accessed-on-githubcom)
* [GitHub Connect](#github-connect)
* [GitHub Codespaces](#github-codespaces)

### API access

Integrators with the REST and GraphQL APIs must send requests to your enterprise's dedicated URL on GHE.com. For more information, see [About GitHub Enterprise Cloud with data residency](/en/enterprise-cloud@latest/admin/data-residency/about-github-enterprise-cloud-with-data-residency#api-access).

### URL differences

The URL formats for certain features and services vary between GitHub.com and GHE.com. If you're migrating to GHE.com and have automations or integrations that depend on URL values for GitHub.com, you will need to updates these values.

The following examples are not exhaustive.

<div class="ghd-tool rowheaders">

| Feature                                    | Example on GitHub.com                                                                              | Example on GHE.com                                                                                       |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| GitHub Packages                            | The Container registry is located at `ghcr.io`.                                                    | The Container registry is located at `https://containers.SUBDOMAIN.ghe.com`.                             |
| User provisioning                          | The "tenant URL" for Microsoft Entra ID is `https://api.github.com/scim/v2/enterprises/ENTERPRISE` | The "tenant URL" for Microsoft Entra ID is `https://api.SUBDOMAIN.ghe.com/scim/v2/enterprises/SUBDOMAIN` |
| OIDC trusts for GitHub Actions deployments | The OIDC token is issued from `https://token.actions.githubusercontent.com`.                       | The OIDC token is issued from `https://token.actions.SUBDOMAIN.ghe.com`                                  |
| Raw URLs                                   | `https://raw.githubusercontent.com/`                                                               | `https://raw.SUBDOMAIN.ghe.com/`                                                                         |
| Anonymized URLs for images and videos      | `https://private-user-images.githubusercontent.com/`                                               | `https://SUBDOMAIN.ghe.com/user-attachments/assets/`                                                     |
| Cloning repositories using SSH             | `git clone git@github.com:OWNER/REPOSITORY.git`                                                    | `git clone SUBDOMAIN@SUBDOMAIN.ghe.com:OWNER/REPOSITORY.git`                                             |

</div>

### Organization names and usernames

GHE.com reserves certain usernames and organization names for internal use. If you try to create a user or organization with one of these names, you'll get an error stating the name is unavailable.

### GitHub Actions workflows from GitHub Marketplace

GitHub Actions workflows from the GitHub Marketplace may not work as users expect.

* Some actions hard-code API calls to api.github.com, which don't currently work for enterprises on GHE.com.
* Some actions make requests to resources on GitHub.com, and these actions will **not** work for enterprises on GHE.com unless the author has built a mechanism to inject a secondary token for API calls. A `GITHUB_TOKEN` within a workflow run for your enterprise on GHE.com does not grant access to resources on GitHub.com.

### Retirement of namespaces for actions accessed on GitHub.com

To ensure workflows use their intended actions and to block the potential for abuse, once an action on GitHub.com is used for the first time, the namespace associated with that action is retired in your enterprise. This blocks users from creating an organization and repository in your enterprise that match the action's namespace on GitHub.com.

To allow people to use namespaces that match actions you have used from GitHub.com, you can make a retired namespace available. See [Making retired namespaces available on GHE.com](/en/enterprise-cloud@latest/actions/administering-github-actions/making-retired-namespaces-available-on-ghecom).

### GitHub Connect

You can use GitHub Connect to connect to GHE.com from GitHub Enterprise Server.

* Server Statistics is not available.
* GitHub.com actions are not available.
* Automatic user license sync requires GitHub Enterprise Server version 3.15 or later.

To enable GitHub Connect, you must configure your GitHub Enterprise Server instance to connect to your GHE.com subdomain. See [Enabling GitHub Connect for GHE.com](/en/enterprise-server@3.20/admin/configuring-settings/configuring-github-connect/enabling-github-connect-for-ghecom).

## Features in public preview

Some features on GHE.com are currently in public preview.

### GitHub Codespaces

GitHub Codespaces on GHE.com are in public preview and are available in all GitHub Enterprise Cloud with data residency regions.

To use GitHub Codespaces from VS Code desktop with an enterprise on GHE.com, you must configure the `Github-enterprise: Uri` and `Github > Codespaces: Auth Provider` settings. For more information, see [Using GitHub Codespaces in Visual Studio Code](/en/enterprise-cloud@latest/codespaces/developing-in-a-codespace/using-github-codespaces-in-visual-studio-code#connecting-to-an-enterprise-on-ghecom).