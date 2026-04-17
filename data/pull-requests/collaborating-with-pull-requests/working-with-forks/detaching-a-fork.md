# Detaching a fork

You can disconnect a repository from its fork network by leaving the network or manually deleting the fork and recreating it without any connection to the original.

## Manually Leaving the fork network

To turn your fork into a standalone repository, you can clone the fork, use the clone to create a new repository, and then delete the fork removing the connection to the original network.

1. Open <span class="platform-mac">Terminal</span><span class="platform-linux">Terminal</span><span class="platform-windows">Git Bash</span>.

2. Create a bare clone of the fork.

   ```shell
   git clone --bare https://github.com/EXAMPLE-USER/FORK.git
   ```

3. Delete the forked repository. For more information, see [Deleting a repository](/en/repositories/creating-and-managing-repositories/deleting-a-repository).<br><br>

   > \[!WARNING]
   > Deleting a fork will **permanently** delete any associated pull requests and configurations. This action **cannot** be undone.

4. Create a new repository with the same name in the same location. For more information, see [Creating a new repository](/en/repositories/creating-and-managing-repositories/creating-a-new-repository).

5. Mirror-push the repository back to the same remote URL.

   ```shell
   git --git-dir FORK.git push --mirror https://github.com/EXAMPLE-USER/FORK.git
   ```

6. Remove temporary local clone you created earlier.

   ```shell
   rm -rf FORK.git
   ```

For more information, see [our support page](https://support.github.com/request/fork) on forks.