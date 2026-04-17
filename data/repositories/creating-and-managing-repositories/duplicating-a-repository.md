# Duplicating a repository

To maintain a mirror of a repository without forking it, you can run a special clone command, then mirror-push to the new repository.

> \[!NOTE]
> If you have a project hosted on another Git-based hosting service, you can automatically import your project to GitHub using the GitHub Importer tool. For more information, see [About GitHub Importer](/en/migrations/importing-source-code/using-github-importer/about-github-importer).

Before you can push the original repository to your new copy, or *mirror*, of the repository, you must [create the new repository](/en/repositories/creating-and-managing-repositories/creating-a-new-repository) on GitHub.com. In these examples, `exampleuser/new-repository` or `exampleuser/mirrored` are the mirrors.

## Mirroring a repository

1. Open <span class="platform-mac">Terminal</span><span class="platform-linux">Terminal</span><span class="platform-windows">Git Bash</span>.

2. Create a bare clone of the repository.

   ```shell
   git clone --bare https://github.com/EXAMPLE-USER/OLD-REPOSITORY.git
   ```

3. Mirror-push to the new repository.

   ```shell
   cd OLD-REPOSITORY
   git push --mirror https://github.com/EXAMPLE-USER/NEW-REPOSITORY.git
   ```

4. Remove the temporary local repository you created earlier.

   ```shell
   cd ..
   rm -rf OLD-REPOSITORY
   ```

## Mirroring a repository that contains Git Large File Storage objects

1. Open <span class="platform-mac">Terminal</span><span class="platform-linux">Terminal</span><span class="platform-windows">Git Bash</span>.

2. Create a bare clone of the repository. Replace the example username with the name of the person or organization who owns the repository, and replace the example repository name with the name of the repository you'd like to duplicate.

   ```shell
   git clone --bare https://github.com/EXAMPLE-USER/OLD-REPOSITORY.git
   ```

3. Navigate to the repository you just cloned.

   ```shell
   cd OLD-REPOSITORY
   ```

4. Pull in the repository's Git Large File Storage objects.

   ```shell
   git lfs fetch --all
   ```

5. Mirror-push to the new repository.

   ```shell
   git push --mirror https://github.com/EXAMPLE-USER/NEW-REPOSITORY.git
   ```

6. Push the repository's Git Large File Storage objects to your mirror.

   ```shell
   git lfs push --all https://github.com/EXAMPLE-USER/NEW-REPOSITORY.git
   ```

7. Remove the temporary local repository you created earlier.

   ```shell
   cd ..
   rm -rf OLD-REPOSITORY
   ```

## Mirroring a repository in another location

If you want to mirror a repository in another location, including getting updates from the original, you can clone a mirror and periodically push the changes.

1. Open <span class="platform-mac">Terminal</span><span class="platform-linux">Terminal</span><span class="platform-windows">Git Bash</span>.

2. Create a bare mirrored clone of the repository.

   ```shell
   git clone --mirror https://github.com/EXAMPLE-USER/REPOSITORY-TO-MIRROR.git
   ```

3. Set the push location to your mirror.

   ```shell
   cd REPOSITORY-TO-MIRROR
   git remote set-url --push origin https://github.com/EXAMPLE-USER/MIRRORED
   ```

   As with a bare clone, a mirrored clone includes all remote branches and tags, but all local references will be overwritten each time you fetch, so it will always be the same as the original repository. Setting the URL for pushes simplifies pushing to your mirror.

4. To update your mirror, fetch updates and push.

   ```shell
   git fetch -p origin
   git push --mirror
   ```

## Further reading

* [Pushing changes to GitHub from GitHub Desktop](/en/desktop/making-changes-in-a-branch/pushing-changes-to-github-from-github-desktop#pushing-changes-to-github)
* [About Git Large File Storage and GitHub Desktop](/en/desktop/configuring-and-customizing-github-desktop/about-git-large-file-storage-and-github-desktop)