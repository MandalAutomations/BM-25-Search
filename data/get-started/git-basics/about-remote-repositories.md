# About remote repositories

GitHub's collaborative approach to development depends on publishing commits from your local repository to GitHub for other people to view, fetch, and update.

## About remote repositories

A remote URL is Git's fancy way of saying "the place where your code is stored." That URL could be your repository on GitHub, or another user's fork, or even on a completely different server.

You can only push to two types of URL addresses:

* An HTTPS URL like `https://github.com/user/repo.git`
* An SSH URL, like `git@github.com:user/repo.git`

Git associates a remote URL with a name, and your default remote is usually called `origin`.

## Creating remote repositories

You can use the `git remote add` command to match a remote URL with a name.
For example, you'd type the following in the command line:

```shell
git remote add origin <REMOTE_URL>
```

This associates the name `origin` with the `REMOTE_URL`.

You can use the command `git remote set-url` to [change a remote's URL](/en/get-started/git-basics/managing-remote-repositories).

## Choosing a URL for your remote repository

There are several ways to clone repositories available on GitHub.

When you view a repository while signed in to your account, the URLs you can use to clone the project onto your computer are available below the repository details.

For information on setting or changing your remote URL, see [Managing remote repositories](/en/get-started/git-basics/managing-remote-repositories).

## Cloning with HTTPS URLs

The `https://` clone URLs are available on all repositories, regardless of visibility. `https://` clone URLs work even if you are behind a firewall or proxy.

When you `git clone`, `git fetch`, `git pull`, or `git push` to a private remote repository using HTTPS URLs on the command line, Git will ask for your GitHub username and password. When Git prompts you for your password, enter your personal access token. Alternatively, you can use a credential helper like [Git Credential Manager](https://github.com/GitCredentialManager/git-credential-manager/blob/main/README.md). Password-based authentication for Git has been removed in favor of more secure authentication methods. For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

If you are accessing an organization that uses SAML SSO and you are using a personal access token (classic), you must also authorize your personal access token to access the organization before you authenticate. For more information, see [About authentication with single sign-on](/en/authentication/authenticating-with-saml-single-sign-on/about-authentication-with-saml-single-sign-on) and [Authorizing a personal access token for use with single sign-on](/en/authentication/authenticating-with-saml-single-sign-on/authorizing-a-personal-access-token-for-use-with-saml-single-sign-on).

> \[!TIP]
>
> * You can use a credential helper so Git will remember your GitHub credentials every time it talks to GitHub. For more information, see [Caching your GitHub credentials in Git](/en/get-started/git-basics/caching-your-github-credentials-in-git).
> * To clone a repository without authenticating to GitHub on the command line, you can use GitHub Desktop to clone instead. For more information, see [Cloning a repository from GitHub to GitHub Desktop](/en/desktop/adding-and-cloning-repositories/cloning-a-repository-from-github-to-github-desktop).

If you'd rather use SSH but cannot connect over port 22, you might be able to use SSH over the HTTPS port. For more information, see [Using SSH over the HTTPS port](/en/authentication/troubleshooting-ssh/using-ssh-over-the-https-port).

## Cloning with SSH URLs

SSH URLs provide access to a Git repository via SSH, a secure protocol. To use these URLs, you must generate an SSH keypair on your computer and add the **public** key to your account on GitHub. For more information, see [Connecting to GitHub with SSH](/en/authentication/connecting-to-github-with-ssh).

When you `git clone`, `git fetch`, `git pull`, or `git push` to a remote repository using SSH URLs, you'll be prompted for a password and must provide your SSH key passphrase. For more information, see [Working with SSH key passphrases](/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases).

If you are accessing an organization that uses SAML single sign-on (SSO), you must authorize your SSH key to access the organization before you authenticate. For more information, see [About authentication with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on/about-authentication-with-saml-single-sign-on) and [Authorizing an SSH key for use with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on/authorizing-an-ssh-key-for-use-with-saml-single-sign-on)" in the GitHub Enterprise Cloud documentation.

> \[!TIP]
> You can use an SSH URL to clone a repository to your computer, or as a secure way of deploying your code to production servers. You can also use SSH agent forwarding with your deploy script to avoid managing keys on the server. For more information, see [Using SSH agent forwarding](/en/authentication/connecting-to-github-with-ssh/using-ssh-agent-forwarding).

## Cloning with GitHub CLI

You can also install GitHub CLI to use GitHub workflows in your terminal. For more information, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).