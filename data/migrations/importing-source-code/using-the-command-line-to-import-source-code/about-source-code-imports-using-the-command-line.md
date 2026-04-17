# About source code imports using the command line

You can use command line tools to import source code and its revision history to GitHub.

Importing your source code to GitHub makes it easier for you and others to work together on projects and manage code. GitHub helps you collaborate, track changes, and organize tasks, making it simpler to build and manage projects. For more information, see [About GitHub and Git](/en/get-started/start-your-journey/about-github-and-git).

If you want to import a Git repository to GitHub.com, and the repository is stored on a code hosting service that is publicly available on the internet, we recommend using GitHub Importer. For more information, see [Using GitHub Importer](/en/migrations/importing-source-code/using-github-importer).

If your source code is not tracked by Git or is not publicly available, you can use the command line instead.

* To import a Git repository that is stored on a code hosting service that is not accessible from the public internet, see [Importing an external Git repository using the command line](/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/importing-an-external-git-repository-using-the-command-line).
* To import code that is only stored locally, and is either tracked by Git or not tracked by any version control system, see [Adding locally hosted code to GitHub](/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github).
* To import code that is tracked by any version control system other than Git, first convert the repository to Git, then push the Git repository to GitHub.

  * [Importing a Subversion repository](/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/importing-a-subversion-repository)
  * [Importing a Mercurial repository](/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/importing-a-mercurial-repository)
  * [Importing a Team Foundation Version Control repository](/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/importing-a-team-foundation-version-control-repository)

All of these tools import source code and revision history, only. If you also want to import your settings and your collaboration history, such as issues and pull requests, you'll need to use more advanced tools. To determine the best tool to use for your migration, see [Planning your migration to GitHub](/en/migrations/overview/planning-your-migration-to-github).

## Further reading

* [Troubleshooting the 2 GiB push limit](/en/get-started/using-git/troubleshooting-the-2-gb-push-limit)