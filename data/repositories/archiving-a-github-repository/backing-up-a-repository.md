# Backing up a repository

You can use Git or the API to back up your repository.

You may want to take backups of repositories for archiving or disaster recovery purposes.

Depending on the GitHub features you use and your requirements (for example whether you need to be able to restore the backup), there are different backup options which include different data.

You may want to store your backups on an external hard drive and/or upload them to a cloud-based backup or storage service such as [Azure Blob Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blobs-overview/), [Google Drive](https://www.google.com/drive/), or [Dropbox](https://www.dropbox.com/dropbox).

## Backing up a Git repository with the Git CLI

A Git repository includes all of the files and folders associated with a project, along with each file's revision history. For more information, see [About Git](/en/get-started/using-git/about-git#about-repositories).

You can take a backup of a Git repository, including the revision history, by performing a mirror clone with the Git CLI.

To perform a mirror clone, use the `git clone` command with the `--mirror` option.

```bash
git clone --mirror https://github.com/EXAMPLE-USER/REPOSITORY.git
```

If the repository includes Git Large File Storage objects, pull in the objects. For more details on Git Large File Storage and how to install it, see [About Git Large File Storage](/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage).

```bash
git lfs fetch --all
```

Once you have cloned the Git repository, you can compress it into an archive (for example a `.zip` or `.tar.gz` file) and move it to a location for safe-keeping.

You can restore your backup by decompressing the archive and then pushing the Git repository to a Git remote.

## Backing up a wiki with the Git CLI

Wikis in GitHub are stored as Git repositories. This means that you can back up a wiki by cloning it. For more details on how to clone a wiki using Git, see [Adding or editing wiki pages](/en/communities/documenting-your-project-with-wikis/adding-or-editing-wiki-pages#cloning-wikis-to-your-computer).

Once you have cloned the wiki, you can compress it into an archive (for example a `.zip` or `.tar.gz` file) and move it to a location for safe-keeping.

You can restore your backup by decompressing the archive and then pushing the wiki repository to a Git remote.

## Backing up a Git repository and selected metadata with migration archives

You can use the REST API to generate a migration archive for a repository. For more information, see [REST API endpoints for organization migrations](/en/rest/migrations/orgs).

These archives are designed for moving data between GitHub products, but they can also be used to back up a repository for archiving purposes

> \[!WARNING]
> Migration archives do not include all data related to a repository. For example, Git Large File Storage objects, discussions, or packages are not included. For more information on what is included in migration archives, see [About migrations between GitHub products](/en/migrations/using-github-enterprise-importer/migrating-between-github-products/about-migrations-between-github-products).

Once you have generated an archive, you can move it to a location of your choice for safe-keeping.

There is no supported, documented way to restore migration archives on GitHub, so these backups are only suitable for archiving purposes.

## Third-party backup tools

A number of self-service tools exist that automate backups of repositories. Backup tools will download data from *specific* repositories and organize it within a new branch or directory.

For more information about self-service backup tools, see the [Backup Utilities category on GitHub Marketplace](https://github.com/marketplace?type=apps\&category=backup-utilities).