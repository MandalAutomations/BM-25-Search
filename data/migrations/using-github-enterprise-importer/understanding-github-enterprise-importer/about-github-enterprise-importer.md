# About GitHub Enterprise Importer

With GitHub Enterprise Importer, you can migrate your enterprise to GitHub Enterprise Cloud from various sources.

## About GitHub Enterprise Importer

GitHub Enterprise Importer is a highly customizable migration tool designed to help you move your enterprise to GitHub Enterprise Cloud.

You can migrate on a repository-by-repository basis or, if your migration source is GitHub.com, on an organization-by-organization basis.

GitHub Enterprise Importer allows you to customize your migration to meet your enterprise's unique needs with:

* **A distinct migration permissions role** for repository migrations, which allows you to designate teams and/or individual users to run a migration and removes the need for organization owners to complete the migration.
* **High fidelity migration**, which allows you to migrate a single repository, a series of repositories, or an entire organization.
* **Support for custom trial run migrations**, which allow you to run a migration as many times as you desire before running the production migration.
* **Clear and unblocking error logging**, so that migrations are allowed to continue with non-critical migration errors, such as not being able to move a single pull request comment. After the migration, you can review a log file that opens automatically.
* **Users retain ownership of their history**, to ensure that their Git history or GitHub metadata is maintained across the migration.

You can run your migration with either the GitHub CLI or the API.

The GitHub CLI simplifies the migration process and is recommended for most customers. Advanced customers with heavy customization needs can use the API to build their own integrations with GitHub Enterprise Importer.

## Supported migration paths

GitHub Enterprise Importer supports migrations **to** GitHub Enterprise Cloud (GitHub.com or GHE.com) **from** the following sources.

* Azure DevOps (ADO) Cloud
* Bitbucket Server and Bitbucket Data Center 5.14+
* GitHub.com
* GitHub Enterprise Server (GHES) 3.4.1+

> \[!NOTE]
> GitHub Enterprise Importer does not currently support migrations **from GHE.com.**

## Getting started

To learn more about the migration path you require, and the data that GitHub Enterprise Importer migrates, see the following articles.

* [Understand migrations from Azure DevOps to GitHub](/en/migrations/using-github-enterprise-importer/migrating-from-azure-devops-to-github-enterprise-cloud/about-migrations-from-azure-devops-to-github-enterprise-cloud)

* [About migrations from Bitbucket Server to GitHub Enterprise Cloud](/en/migrations/using-github-enterprise-importer/migrating-from-bitbucket-server-to-github-enterprise-cloud/about-migrations-from-bitbucket-server-to-github-enterprise-cloud)

* [About migrations between GitHub products](/en/migrations/using-github-enterprise-importer/migrating-between-github-products/about-migrations-between-github-products)