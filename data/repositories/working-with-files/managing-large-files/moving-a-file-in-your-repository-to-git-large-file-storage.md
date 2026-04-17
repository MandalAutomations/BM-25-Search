# Moving a file in your repository to Git Large File Storage

If you've set up Git LFS, and you have an existing file in your repository that needs to be tracked in Git LFS, you need to first remove it from your repository.

After installing Git LFS and configuring Git LFS tracking, you can move files from Git's regular tracking to Git LFS. For more information, see [Installing Git Large File Storage](/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage) and [Configuring Git Large File Storage](/en/repositories/working-with-files/managing-large-files/configuring-git-large-file-storage).

If there are referenced Git LFS files that did not upload successfully, you will receive an error message. For more information, see [Resolving Git Large File Storage upload failures](/en/repositories/working-with-files/managing-large-files/resolving-git-large-file-storage-upload-failures).

> \[!TIP]
> If you get an error that "this exceeds Git LFS's file size limit of 100 MiB" when you try to push files to Git, you can use `git lfs migrate` instead of `filter-repo`, to move the large file to Git Large File Storage. For more information about the `git lfs migrate` command, see the [Git LFS 2.2.0](https://github.com/blog/2384-git-lfs-2-2-0-released) release announcement.

1. Remove the file from the repository's Git history using the `filter-repo` command. For detailed information on using these, see [Removing sensitive data from a repository](/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository).
2. Configure tracking for your file and push it to Git LFS. For more information on this procedure, see [Configuring Git Large File Storage](/en/repositories/working-with-files/managing-large-files/configuring-git-large-file-storage).

## Further reading

* [About Git Large File Storage](/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage)
* [Collaboration with Git Large File Storage](/en/repositories/working-with-files/managing-large-files/collaboration-with-git-large-file-storage)
* [Installing Git Large File Storage](/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage)