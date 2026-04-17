# Downloading files from GitHub

Learn how to download files from GitHub, and understand the difference between downloading, cloning, and forking.

## Introduction

GitHub.com is home to millions of open-source software projects, that you can copy, customize, and use for your own purposes.

There are different ways to get a copy of a repository's files on GitHub. You can:

* **Download** a snapshot of a repository's files as a zip file to your own (local) computer.
* **Clone** a repository to your local computer using Git.
* **Fork** a repository to create a new repository on GitHub.

Each of these methods has its own use case, which we'll explain in the next section.

This tutorial focuses on downloading a repository's files to your local computer. For example, if you've found some interesting content in a repository on GitHub, downloading is a simple way to get a copy of the content, without using Git or applying version control.

### Understanding the differences between downloading, cloning, and forking

| Term     | Definition                                                                                                                                                 | Use case                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Download | To save a snapshot of a repository's files to your local computer.                                                                                         | You want to use or customize the content of the files, but you're not interested in applying version control.                                                                                                                                                                                                                                                                                                                                                |
| Clone    | To make a full copy of a repository's data, including all versions of every file and folder.                                                               | You want to work on a full copy of the repository on your local computer, using Git to track and manage your changes. You likely intend to sync these locally-made changes with the GitHub-hosted repository. For more information, see [Cloning a repository](/en/repositories/creating-and-managing-repositories/cloning-a-repository).                                                                                                                    |
| Fork     | To create a new repository on GitHub, linked to your personal account, that shares code and visibility settings with the original ("upstream") repository. | You want to use the original repository's data as a basis for your own project on GitHub. Or, you want to use the fork to propose changes to the original ("upstream") repository. After forking the repository, you still might want to clone the repository, so that you can work on the changes on your local computer. For more information, see [Fork a repository](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo). |

## Prerequisites

* You must have a GitHub account.

## Downloading a repository's files

For the tutorial, we'll use a demo repository ([octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife)).

1. Navigate to [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife).
2. Above the list of files, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code**.

   ![Screenshot of the list of files on the landing page of a repository. The "Code" button is highlighted with a dark orange outline.](/assets/images/help/repository/code-button.png)
3. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-file-zip" aria-label="file-zip" role="img"><path d="M3.5 1.75v11.5c0 .09.048.173.126.217a.75.75 0 0 1-.752 1.298A1.748 1.748 0 0 1 2 13.25V1.75C2 .784 2.784 0 3.75 0h5.586c.464 0 .909.185 1.237.513l2.914 2.914c.329.328.513.773.513 1.237v8.586A1.75 1.75 0 0 1 12.25 15h-.5a.75.75 0 0 1 0-1.5h.5a.25.25 0 0 0 .25-.25V4.664a.25.25 0 0 0-.073-.177L9.513 1.573a.25.25 0 0 0-.177-.073H7.25a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5h-3a.25.25 0 0 0-.25.25Zm3.75 8.75h.5c.966 0 1.75.784 1.75 1.75v3a.75.75 0 0 1-.75.75h-2.5a.75.75 0 0 1-.75-.75v-3c0-.966.784-1.75 1.75-1.75ZM6 5.25a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 6 5.25Zm.75 2.25h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM8 6.75A.75.75 0 0 1 8.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 8 6.75ZM8.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM8 9.75A.75.75 0 0 1 8.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 8 9.75Zm-1 2.5v2.25h1v-2.25a.25.25 0 0 0-.25-.25h-.5a.25.25 0 0 0-.25.25Z"></path></svg> Download ZIP**.

## Conclusion

You now have a copy of the repository's files saved as a zip file on your local computer. You can edit and customize the files for your own purposes.

## Next steps

* In the next tutorial, [Uploading a project to GitHub](/en/get-started/start-your-journey/uploading-a-project-to-github), you'll learn how to upload your own files to a remote repository on GitHub.

## Further reading

* [Downloading source code archives](/en/repositories/working-with-files/using-files/downloading-source-code-archives)