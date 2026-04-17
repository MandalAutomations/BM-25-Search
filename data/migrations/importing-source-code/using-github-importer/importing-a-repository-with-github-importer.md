# Importing a repository with GitHub Importer

If you have a project hosted on another Git-based hosting service, you can quickly import it to GitHub using the GitHub Importer tool.

## About repository imports with GitHub Importer

GitHub Importer imports the source code and commit history of Git repositories hosted on external hosting services. For more information about the capabilities and limitations of GitHub Importer, see [About GitHub Importer](/en/migrations/importing-source-code/using-github-importer/about-github-importer#capabilities-and-limitations-of-github-importer).

GitHub uses the email address in the commit header to link a commit to a GitHub user. To correctly attribute commits in an imported repository, users will need to add the email address associated with their commits to their GitHub account. For more information, see [Adding an email address to your GitHub account](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/adding-an-email-address-to-your-github-account).

## Importing a repository with GitHub Importer

When you import a repository using the GitHub Importer, a new repository will be created. If you already have an existing repository you want to use, you can instead add your local repository to GitHub using Git. For more information, see [Adding locally hosted code to GitHub](/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#importing-a-git-repository-with-the-command-line).

1. In the upper-right corner of any page on GitHub.com, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Create new" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>, and then click **Import repository**.

   ![Screenshot of the top-right corner of any page on GitHub. A plus icon is highlighted with an orange outline.](/assets/images/help/importer/import-repository.png)

2. On the "Import your project to GitHub" page, enter the URL for the remote repository hosted on another platform.

3. If the source repository is private, enter credentials for authentication. GitHub Importer will use the credentials to perform a `git clone` operation on the source repository.

4. Choose an owner and a name for the new repository on GitHub.

5. Choose the visibility of the new repository. For more information, see [About repositories](/en/repositories/creating-and-managing-repositories/about-repositories#about-repository-visibility).

6. Click **Begin import**.

You'll be redirected to a "Preparing your new repository" page, where you can track the status of your import. You'll receive an email when the repository has been completely imported.