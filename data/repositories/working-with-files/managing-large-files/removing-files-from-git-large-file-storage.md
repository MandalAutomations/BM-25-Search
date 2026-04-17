# Removing files from Git Large File Storage

If you've set up Git LFS for your repository, you can remove all files or a subset of files from Git LFS.

## Removing a single file

1. Remove the file from the repository's Git history using the `filter-repo` command. For detailed information on using these, see [Removing sensitive data from a repository](/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository).

2. Navigate to your *.gitattributes* file.

   > \[!NOTE]
   > Your *.gitattributes* file is generally saved within your local repository. In some cases, you may have created a global *.gitattributes* file that contains all of your Git LFS associations.

3. Find and remove the associated Git LFS tracking rule within the *.gitattributes* file.

4. Save and exit the *.gitattributes* file.

## Removing all files within a Git LFS repository

1. Remove the files from the repository's Git history using the `filter-repo` command. For detailed information on using these, see [Removing sensitive data from a repository](/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository).
2. Optionally, to uninstall Git LFS in the repository, run:

   ```shell
   git lfs uninstall
   ```

   For Git LFS versions below 1.1.0, run:

   ```shell
   git lfs uninit
   ```

## Git LFS objects in your repository

After you remove files from Git LFS, the Git LFS objects still exist on the remote storage and will continue to count toward your Git LFS storage quota.

To remove Git LFS objects from a repository, delete and recreate the repository. When you delete a repository, any associated issues, stars, and forks are also deleted. For more information, see [Deleting a repository](/en/repositories/creating-and-managing-repositories/deleting-a-repository). If you need to purge a removed object and you are unable to delete the repository, please [contact support](/en/support) for help.

> \[!NOTE]
> If you removed a single file and have other Git LFS objects that you'd like to keep in your repository, after deleting and recreating your repository, reconfigure your Git LFS-associated files. For more information, see [Removing a single file](#removing-a-single-file) and [Configuring Git Large File Storage](/en/repositories/working-with-files/managing-large-files/configuring-git-large-file-storage).

## Further reading

* [About Git Large File Storage](/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage)
* [Collaboration with Git Large File Storage](/en/repositories/working-with-files/managing-large-files/collaboration-with-git-large-file-storage)
* [Installing Git Large File Storage](/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage)