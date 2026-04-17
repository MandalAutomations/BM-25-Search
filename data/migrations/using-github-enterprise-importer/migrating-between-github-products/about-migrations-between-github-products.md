# About migrations between GitHub products

Learn which data GitHub Enterprise Importer can migrate between GitHub products.

## About migrations between GitHub products

With GitHub Enterprise Importer, you can migrate data from GitHub Enterprise Server to GitHub Enterprise Cloud, or migrate data from GitHub.com to another account on GitHub Enterprise Cloud.

For example, GitHub Enterprise Importer can help your company to:

* Adopt GitHub Enterprise Cloud with data residency by migrating your enterprise to GHE.com
* Adopt certain features on GitHub.com, such as Enterprise Managed Users or new billing models, by migrating between enterprises on GitHub.com
* Benefit from simplified administration and new features by migrating from GitHub Enterprise Server to GitHub Enterprise Cloud

If your migration source is an account on GitHub.com, you can migrate individual repositories between organizations, or migrate entire organizations between enterprises. If your migration source is GitHub Enterprise Server, you can migrate individual repositories.

The data that GitHub Enterprise Importer migrates depends on the source of the migration and whether you are migrating a repository or organization.

## Considerations for migrations to GitHub Enterprise Cloud

Before you use GitHub Enterprise Importer, understand the following considerations:

* If you **already use GitHub Enterprise Cloud**: A GitHub Enterprise plan entitles you to one deployment of GitHub Enterprise Cloud.

  For example, if you already use GitHub.com, and you also want to migrate from GitHub Enterprise Server to GHE.com, your usage for both won't be covered under a single plan.
* If you're **migrating to Enterprise Managed Users**: You will need to integrate with an identity provider to manage user accounts. Check the level of support for your identity provider before you start. See [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/about-enterprise-managed-users#identity-management-systems).
* If you're **migrating from GitHub Enterprise Server**: Be aware that GitHub applies rate limits to certain actions, which are disabled by default on GitHub Enterprise Server. See [Rate limits for the REST API](/en/enterprise-cloud@latest/rest/using-the-rest-api/rate-limits-for-the-rest-api).
* If you're **migrating to GitHub Enterprise Cloud with data residency**: Be aware that certain features are unavailable, and some features require different or additional configuration. See [Feature overview for GitHub Enterprise Cloud with data residency](/en/enterprise-cloud@latest/admin/data-residency/feature-overview-for-github-enterprise-cloud-with-data-residency).

## Data that is migrated from GitHub Enterprise Server

To migrate from GitHub Enterprise Server (GHES), you must have GHES version 3.4.1 or higher. The data that is migrated depends on the version you're using.

| Item                                                                                                                                                                                                                             | GHES 3.4.1+                                                                                                                                                                                                                                                                                                                                                                                                                              | GHES 3.5.0+                                                                                                                                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Git source (including commit history)                                                                                                                                                                                            | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Pull requests                                                                                                                                                                                                                    | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Issues                                                                                                                                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Milestones                                                                                                                                                                                                                       | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Wikis                                                                                                                                                                                                                            | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| GitHub Actions workflows                                                                                                                                                                                                         | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Commit comments                                                                                                                                                                                                                  | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Webhooks (must be re-enabled after your migration, see [Enabling webhooks](/en/migrations/using-github-enterprise-importer/migrating-between-github-products/overview-of-a-migration-between-github-products#enabling-webhooks)) | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Branch protections                                                                                                                                                                                                               | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| GitHub Pages settings                                                                                                                                                                                                            | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| User history for the above data                                                                                                                                                                                                  | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Attachments (see [Attaching files](/en/get-started/writing-on-github/working-with-advanced-formatting/attaching-files))                                                                                                          | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Releases                                                                                                                                                                                                                         | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Cannot be migrated" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Can be migrated" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |

Different size limits per repository apply to the compressed archive, depending on your GHES version.

| Limit      | GHES <3.8.0 | GHES 3.8.x-3.11.x | GHES 3.12.x | GHES 3.13.0+           |
| ---------- | ----------- | ----------------- | ----------- | ---------------------- |
| Git source | 2GiB        | 10GiB             | 20GiB       | 40GiB (public preview) |
| Metadata   | 2GiB        | 10GiB             | 20GiB       | 40GiB (public preview) |

### Data that is not migrated

Currently, the following data is **not** migrated.

* Audit logs
* Code scanning results
* Codespaces secrets
* Commit status checks
* Dependabot alerts
* Dependabot secrets
* Discussions at the repository level
* Edit history of issue comments and pull request comments
* Fork relationships between repositories (see [About forks](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks))
* GitHub Actions secrets, variables, environments, self-hosted runners, larger runners, workflow artifacts, or workflow run history
* GitHub Apps and GitHub App installations
* Git LFS objects and large binaries (repositories using Git LFS are still supported, see [Limitations of GitHub Enterprise Importer](#limitations-of-github-enterprise-importer))
* Links from commits to pull requests that were rebase merged
* Mentions of users, teams, and organizations in pull request, issue, release, and comment bodies (the username originally mentioned is retained)
* Packages in GitHub Packages
* Projects (the new projects experience)
* References between pull requests and issues in different repositories (see [Autolinked references and URLs](/en/get-started/writing-on-github/working-with-advanced-formatting/autolinked-references-and-urls))
* Remediation states of secret scanning results
* Repositories owned by user accounts
* Repository activity feed
* Repository properties and custom properties (see [Custom properties](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/custom-properties))
* Repository stars
* Repository watchers
* Rulesets
* Sub-issues (see [About issues](/en/issues/tracking-your-work-with-issues/learning-about-issues/about-issues#about-sub-issues))
* Tag protection rules
* User access to the repository
* Users' profiles, SSH keys, signing keys, or personal access tokens
* Webhook secrets
* Teams
* User or team access to the repository
* Repository settings for pull requests

### Branch protections

Branch protections apply a specified set of rules to a specific branch name or branch name pattern. For more information, see [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

Branch protections will always be migrated, but certain rules will not be migrated. The following branch protection rules are not migrated.

* Allow specific actors to bypass required pull requests
* Require approval of the most recent push
* Require deployments to succeed before merging
* Lock branch
* Restrict pushes that create matching branches
* Allow force pushes

The following limitations also apply:

* If a branch protection rule optionally allows you to specify people, teams, or apps that are exempt from the rule, such as "Restrict who can dismiss pull request reviews," the exceptions will not be migrated.
* If the "Allow force pushes" rule is enabled in "Specify who can force push" mode, the rule will not be migrated.

## Data that is migrated from GitHub.com

If your migration source is an account on GitHub.com, you can migrate individual repositories between organizations, or migrate entire organizations between enterprises.

### Migrated data for an organization

When you migrate an organization, a new organization is created within the destination enterprise account. Then, the following data is migrated to the new organization.

* Teams
* Repositories
* Team access to repositories
* Member privileges
* Organization-level webhooks (must be re-enabled after your migration, see [Enabling webhooks](/en/migrations/using-github-enterprise-importer/migrating-between-github-products/overview-of-a-migration-between-github-products#enabling-webhooks))
* Default branch name for new repositories created in the organization

All repositories are migrated with private visibility. If you want to set a repository's visibility to public or internal, you can do this after the migration using the UI or API.

Team membership is **not** migrated. After the migration, you'll need to add members to migrated teams. For more information, see [Overview of a migration between GitHub products](/en/migrations/using-github-enterprise-importer/migrating-between-github-products/overview-of-a-migration-between-github-products#recreating-teams).

> \[!NOTE]
> References to teams, such as `@octo-org/octo-team`, are **not** updated as part of an organization migration. This might cause problems in the destination organization, such as `CODEOWNERS` files not working as expected. For more information about how to prevent and resolve these issues, see [Troubleshooting your migration with GitHub Enterprise Importer](/en/migrations/using-github-enterprise-importer/completing-your-migration-with-github-enterprise-importer/troubleshooting-your-migration-with-github-enterprise-importer#team-references-are-broken-after-an-organization-migration).

### Migrated data for a repository

When you migrate a repository, either directly or as part of an organization migration, only the following data is migrated.

* Git source (including commit history)
* Pull requests
* Issues
* Milestones
* Wikis (excluding attachments)
* GitHub Actions workflows
* Commit comments
* Active webhooks (must be re-enabled after your migration, see [Enabling webhooks](/en/migrations/using-github-enterprise-importer/migrating-between-github-products/overview-of-a-migration-between-github-products#enabling-webhooks))
* Repository topics
* Repository settings
  * Branch protections (see [Branch protections](#branch-protections) for more details)
  * GitHub Pages settings
  * Autolink references
  * Pull request settings
    * Automatically delete head branches
    * Allow auto-merge
    * Allow merge commits (commit message setting is reset to the default message)
    * Allow squash merging (commit message setting is reset to the default message)
    * Allow rebase merging
* Releases (up to 10 GiB per repository)
* User history for the above data
* Attachments (see [Attaching files](/en/get-started/writing-on-github/working-with-advanced-formatting/attaching-files))

### Data that is not migrated

Currently, the following data is **not** migrated.

* Audit logs
* Code scanning results
* Codespaces secrets
* Commit status checks
* Dependabot alerts
* Dependabot secrets
* Discussions at the repository level
* Edit history of issue comments and pull request comments
* Fork relationships between repositories (see [About forks](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks))
* GitHub Actions secrets, variables, environments, self-hosted runners, larger runners, workflow artifacts, or workflow run history
* GitHub Apps and GitHub App installations
* Git LFS objects and large binaries (repositories using Git LFS are still supported, see [Limitations of GitHub Enterprise Importer](#limitations-of-github-enterprise-importer))
* Links from commits to pull requests that were rebase merged
* Mentions of users, teams, and organizations in pull request, issue, release, and comment bodies (the username originally mentioned is retained)
* Packages in GitHub Packages
* Projects (the new projects experience)
* References between pull requests and issues in different repositories (see [Autolinked references and URLs](/en/get-started/writing-on-github/working-with-advanced-formatting/autolinked-references-and-urls))
* Remediation states of secret scanning results
* Repositories owned by user accounts
* Repository activity feed
* Repository properties and custom properties (see [Custom properties](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/custom-properties))
* Repository stars
* Repository watchers
* Rulesets
* Sub-issues (see [About issues](/en/issues/tracking-your-work-with-issues/learning-about-issues/about-issues#about-sub-issues))
* Tag protection rules
* User access to the repository
* Users' profiles, SSH keys, signing keys, or personal access tokens
* Webhook secrets

When you migrate a repository directly, teams and team access to repositories are not migrated.

#### Branch protections

Branch protections apply a specified set of rules to a specific branch name or branch name pattern. For more information, see [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

Branch protections will always be migrated, but certain rules will not be migrated. The following branch protection rules are not migrated.

* Allow specific actors to bypass required pull requests
* Require approval of the most recent push
* Require deployments to succeed before merging
* Lock branch
* Restrict pushes that create matching branches
* Allow force pushes

The following limitations also apply:

* If a branch protection rule optionally allows you to specify people, teams, or apps that are exempt from the rule, such as "Restrict who can dismiss pull request reviews," the exceptions will not be migrated.
* If the "Allow force pushes" rule is enabled in "Specify who can force push" mode, the rule will not be migrated.

## Limitations on migrated data

There are limits to what GitHub Enterprise Importer can migrate. Some are due to limitations of GitHub, while others are limitations of GitHub Enterprise Importer itself.

### Limitations of GitHub

* **2 GiB size limit for a single Git commit:** No single commit in your Git repository can be larger than 2 GiB. If any of your commits are larger than 2 GiB, you will need to split the commit into smaller commits that are each 2 GiB or smaller.
* **255 byte limit for Git references:** No single [Git reference](https://git-scm.com/book/en/v2/Git-Internals-Git-References), commonly known as a "ref", can have a name larger than 255 bytes. Usually, this means that your references cannot be more than 255 characters long, but any non-[ASCII](https://en.wikipedia.org/wiki/ASCII) characters, such as emojis, may consume more than one byte. If any of your Git references are too large, we'll return a clear error message.
* **100 MiB file size limit:** After you complete your migration, no single file in your Git repository can be larger than 100 MiB. During repository migration this limit is increased to 400 MiB. Consider using Git LFS to store large files. For more information, see [Managing large files](/en/repositories/working-with-files/managing-large-files).

### Limitations of GitHub Enterprise Importer

* **40 GiB size limit for a Git repository (public preview):** This limit applies only to the source code. To check if the repository archive is over the limit, use the [git-sizer](https://github.com/github/git-sizer) tool and review the total blob size in the output. The git-sizer tool also helps to identify potential issues related to large files, blob size, commit size, and tree counts that could impact migrations.
* **40 GiB limit for metadata (public preview):** The Importer cannot migrate repositories with more than 40 GiB of metadata. Metadata includes issues, pull requests, releases, and attachments. In most cases, large metadata is caused by binary assets attached to releases. You can exclude releases from the migration with the `migrate-repo` command's `--skip-releases` flag, and then move your releases manually after the migration.
* **400 MiB file size limit:** When migrating a repository with GitHub Enterprise Importer, no single file in your Git repository can be larger than 400 MiB. Consider using Git LFS for storing large files. For more information, see [Managing large files](/en/repositories/working-with-files/managing-large-files).
* **Git LFS objects not migrated:** The Importer can migrate repositories that use Git LFS, but the LFS objects themselves will not be migrated. They can be pushed to your migration destination as a follow-up task after the migration is complete. For more information, see [Duplicating a repository](/en/repositories/creating-and-managing-repositories/duplicating-a-repository#mirroring-a-repository-that-contains-git-large-file-storage-objects).
* **Follow-up tasks required:** When migrating between GitHub products, certain settings are not migrated and must be reconfigured in the new repository. For a list of follow-up tasks you'll need to complete after each migration, see [Overview of a migration between GitHub products](/en/migrations/using-github-enterprise-importer/migrating-between-github-products/overview-of-a-migration-between-github-products#completing-follow-up-tasks).
* **Delayed code search functionality:** Re-indexing the search index can take a few hours after a repository is migrated, and code searches may return unexpected results until re-indexing is complete.
* **Rulesets configured for your organization can cause migrations to fail:** For example, if you configured a rule that requires email addresses for commit authors to end with `@monalisa.cat`, and the repository you're migrating contains commits that don't comply with this rule, your migration will fail. For more information about rulesets, see [About rulesets](/en/enterprise-cloud@latest/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).
* **Mannequin content might not be searchable:** Mannequins are placeholder users to which imported content (such as issues, pull requests, comments, etc.) is associated. When you search for content associated with a mannequin, such as assigned issues, the issues may not be found. Once a mannequin is reclaimed, the content should be found via the new owner. For more information, see [Reclaiming mannequins for GitHub Enterprise Importer](/en/migrations/using-github-enterprise-importer/completing-your-migration-with-github-enterprise-importer/reclaiming-mannequins-for-github-enterprise-importer).

## Getting started

Before you migrate between GitHub products, you should plan out how you will run your migration. Before migrating any data, you will need to choose someone to run the migration. You must grant that person the necessary access for both the source and the destination of the migration. We also recommend you run a trial migration first.

For an overview of the migration process from beginning to end, see [Overview of a migration between GitHub products](/en/migrations/using-github-enterprise-importer/migrating-between-github-products/overview-of-a-migration-between-github-products).