# Managing multiple accounts

If you use one workstation to contribute to projects for more than one account, you can modify your Git configuration to simplify the contribution process.

## Contributing to multiple accounts using HTTPS and personal access tokens

Alternatively, if you want to use the HTTPS protocol for both accounts, you can use different personal access tokens for each account by configuring Git to store different credentials for each repository.

<div class="ghd-tool mac">

1. Open Terminal.
2. To confirm your use of a credential manager, enter the following command and note the output.

   ```shell copy
   git config --get credential.helper
   ```
3. If the output confirms that you're using a credential manager, clear the stored credentials for the credential manager.
   * If the output doesn't include the name of a credential manager, there is no credential manager configured, and you can proceed to the next step.

   * If the output is `osxkeychain`, you're using the macOS keychain. To clear the credentials, you can use the credential helper on the command line:

     ```shell
     $ git credential-osxkeychain erase
     host=github.com
     protocol=https
     > [Press Return]
     >
     ```

   * If the output is `manager` (or `manager-core` in previous versions), you're using Git Credential Manager. To clear the credentials, run the following command.

     ```shell copy
     echo "protocol=https\nhost=github.com" | git credential-manager erase
     ```
4. To configure Git to cache credentials for the full remote URL of each repository you access on GitHub, enter the following command.

   ```shell copy
   git config --global credential.https://github.com.useHttpPath true
   ```
5. For each of your accounts, create a dedicated personal access token (classic) with `repo` scope. Or, for each of your accounts and for each organization that you are a member of, create a fine-grained personal access token that can access the desired repositories and that has read and write permissions on repository contents. For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
6. The first time that you use Git to clone a repository or access data in a repository that you've already cloned, Git will request credentials. Provide the personal access token for the account with access to the repository.

   Git will cache the personal access token based on the full remote URL of the repository, and you'll be able to access and write repository data on GitHub.com using the correct account.

</div>

<div class="ghd-tool windows">

1. Open Git Bash.

2. To confirm your use of a credential manager, enter the following command and note the output.

   ```shell copy
   git config --get credential.helper
   ```

3. If the output confirms that you're using a credential manager, clear the stored credentials for the credential manager.

   * If the output doesn't include the name of a credential manager, there is no credential manager configured, and you can proceed to the next step.
   * If the output is `manager` (or `manager-core` in previous versions), you're using Git Credential Manager. To clear the credentials, run the following command.

   ```shell copy
   echo "protocol=https`nhost=github.com" | git credential-manager erase
   ```

   * If the output is `wincred`, you're using the Windows Credential Manager. To clear the credentials, enter the following command.

     ```shell copy
     cmdkey /delete:LegacyGeneric:target=git:https://github.com
     ```

4. To configure Git to cache credentials for the full remote URL of each repository you access on GitHub, enter the following command.

   ```shell copy
   git config --global credential.https://github.com.useHttpPath true
   ```

5. For each of your accounts, create a dedicated personal access token (classic) with `repo` scope. Or, for each of your accounts and for each organization that you are a member of, create a fine-grained personal access token that can access the desired repositories and that has read and write permissions on repository contents. For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

6. The first time that you use Git to clone a repository or access data in a repository that you've already cloned, Git will request credentials. Provide the personal access token for the account with access to the repository.

   Git will cache the personal access token based on the full remote URL of the repository, and you'll be able to access and write repository data on GitHub.com using the correct account.

</div>

<div class="ghd-tool linux">

1. Open Terminal.
2. To confirm your use of a credential manager, enter the following command and note the output.

   ```shell copy
   git config --get credential.helper
   ```
3. If the output confirms that you're using a credential manager, clear the stored credentials for the credential manager.

   * If the output doesn't include the name of a credential manager, there is no credential manager configured, and you can proceed to the next step.
   * If the output is `manager` (or `manager-core` in previous versions), you're using Git Credential Manager. To clear the credentials, run the following command.

   ```shell copy
   echo "protocol=https\nhost=github.com" | git credential-manager erase
   ```
4. To configure Git to cache credentials for the full remote URL of each repository you access on GitHub, enter the following command.

   ```shell copy
   git config --global credential.https://github.com.useHttpPath true
   ```
5. For each of your accounts, create a dedicated personal access token (classic) with `repo` scope. Or, for each of your accounts and for each organization that you are a member of, create a fine-grained personal access token that can access the desired repositories and that has read and write permissions on repository contents. For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
6. The first time that you use Git to clone a repository or access data in a repository that you've already cloned, Git will request credentials. Provide the personal access token for the account with access to the repository.

   Git will cache the personal access token based on the full remote URL of the repository, and you'll be able to access and write repository data on GitHub.com using the correct account.

</div>

## Contributing to multiple accounts using SSH and `GIT_SSH_COMMAND`

If you want to use the SSH protocol for both accounts, you can use different SSH keys for each account. For more information about using SSH, see [Connecting to GitHub with SSH](/en/authentication/connecting-to-github-with-ssh).

To use a different SSH key for different repositories that you clone to your workstation, you must write a shell wrapper function for Git operations. The function should perform the following steps.

1. Determine the repository's full name with owner, using a command such as `git config --get remote.origin.url`.
2. Choose the correct SSH key for authentication.
3. Modify `GIT_SSH_COMMAND` accordingly. For more information about `GIT_SSH_COMMAND`, see [Environment Variables](https://git-scm.com/docs/git#Documentation/git.txt-codeGITSSHCOMMANDcode) in the Git documentation.

For example, the following command sets the `GIT_SSH_COMMAND` environment variable to specify an SSH command that uses the private key file at ***PATH/TO/KEY/FILE*** for authentication to clone the repository named OWNER/REPOSITORY on GitHub.com.

```shell copy
GIT_SSH_COMMAND='ssh -i PATH/TO/KEY/FILE -o IdentitiesOnly=yes' git clone git@github.com:OWNER/REPOSITORY
```

## Contributing to multiple accounts using SSH and multiple keys

If you are a member of an enterprise with managed users, but also want to collaborate outside your enterprise using a personal account, you can use different SSH keys for each account. For more information about using SSH, see [Connecting to GitHub with SSH](/en/authentication/connecting-to-github-with-ssh).

> \[!WARNING]
> You cannot use the same SSH key to contribute to both repositories inside your organization with managed users and outside the enterprise.

1. Generate a different SSH key for the repositories in your organization with managed users. See [Generating a new SSH key and adding it to the ssh-agent](/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key). When you save the key, give it a different filename from your existing key (for instance, add -emu to the suggested name of the file).

2. Add the new ssh key to your managed user account. See [Adding a new SSH key to your GitHub account](/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account#adding-a-new-ssh-key-to-your-account)

3. Configure your SSH Config File `~/.ssh/config` to use the different keys. For example, if your personal SSH key is `~/.ssh/id_ed25519` and your enterprise with managed users SSH key is `~/.ssh/id_ed25519-emu`

   ```text copy
   Host github.com
       IdentityFile ~/.ssh/id_ed25519
       IdentitiesOnly yes

   Host github-emu.com
       Hostname github.com
       IdentityFile ~/.ssh/id_ed25519-emu
       IdentitiesOnly yes
   ```

   > \[!NOTE]
   > The `IdentitiesOnly` line ensures that if the ssh-agent has loaded multiple keys, ssh uses the correct key when connecting.

4. Test your SSH configuration by running the following command to connect using the SSH key associated with your personal account - see [Testing your SSH connection](/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection) for further details

   ```shell copy
   ssh -T git@github.com
   ```

   Test to see if you can connect to (GitHub) using your enterprise with managed users SSH key

   ```shell copy
   ssh -T git@github-emu.com
   ```

5. Tell `git` to use the correct key when downloading or uploading a repository in an organization with managed users.
   To list the organizations in your enterprise with managed users,

   1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
   2. For each organization listed tell `git` to use the `github-emu.com` host.

   For example, if one of your organizations is called `octocat-emu` then to tell `git` to use the host `github-emu.com` for repositories in the `octocat-emu` organization, run the following command

   ```shell copy
   git config --global url."git@github-emu.com:octocat-emu/".insteadOf "git@github.com:octocat-emu/"
   ```

Now, when you clone a repository using SSH, in the `octocat-emu` organization, `git` will use the SSH key associated with your enterprise with managed users instead of your personal key.

## Next steps

For reference information, see [Personal account reference](/en/account-and-profile/reference/personal-account-reference).