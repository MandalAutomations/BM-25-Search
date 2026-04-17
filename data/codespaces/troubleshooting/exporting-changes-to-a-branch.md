# Exporting changes to a branch

This article provides steps for exporting your codespace changes to a branch.

## About exporting changes

While using GitHub Codespaces, you may want to export your changes to a branch without launching your codespace. This can be useful when you have hit a [spending limit](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/managing-the-spending-limit-for-github-codespaces) or have a general issue accessing your codespace.

You can export your changes in one of several ways, depending on how you created the codespace. In every case, only the Git branch that is currently checked out in the codespace is exported. Work contained in other branches is not exported.

* If you created the codespace from a repository to which you have write access, you can export your changes to a new branch of the repository.
* If you created the codespace from a repository to which you only have read access, you can export your changes to a fork of the repository. GitHub Codespaces will create a new fork for you, or link your codespace to an existing fork if you already have one for the repository, and export your changes to a new branch of the fork. For more information, see [Using source control in your codespace](/en/codespaces/developing-in-a-codespace/using-source-control-in-your-codespace#about-automatic-forking).
* If you created the codespace from a template, and have not yet published it, you can publish the codespace to a new repository.

> \[!NOTE]
> GitHub blocks pushes containing files larger than 100 MiB. If your codespace contains large files you will not be able to export your changes to a branch or fork. For more information, see [About large files on GitHub](/en/repositories/working-with-files/managing-large-files/about-large-files-on-github).

## Exporting changes to a branch

The following steps describe how to export your changes to a branch or fork. For information on exporting an unpublished codespace to a new repository, see [Creating a codespace from a template](/en/codespaces/developing-in-a-codespace/creating-a-codespace-from-a-template#publishing-from-githubcom).

1. In the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces** to take you to the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces). Or, for an individual repository, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code** menu.

2. Click the ellipsis (**...**) to the right of the codespace you want to export from.

3. Select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> Export changes to a branch** or **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> Export changes to a fork**.

   ![Screenshot of a list of codespaces with the dropdown menu for one of them displayed, showing the "Export changes to a branch" option.](/assets/images/help/codespaces/export-changes-to-a-branch.png)

4. In the dialog box, click **Create branch** or **Create fork**.

The name of the new branch will be the permanent name of your codespace prefixed by the string `codespace-`, for example `codespace-ideal-space-engine-w5vg5ww5p793g7g9`.