# Deleting a codespace

You can delete a codespace you no longer need.

## Overview

GitHub Codespaces are automatically deleted after they have been stopped and have remained inactive for a defined number of days. The retention period for each codespace is set when the codespace is created and does not change. The default retention period is 30 days. See [Configuring automatic deletion of your codespaces](/en/codespaces/setting-your-user-preferences/configuring-automatic-deletion-of-your-codespaces?tool=webui).

You can manually delete a codespace in a variety of ways:

* In the terminal by using GitHub CLI
* In Visual Studio Code
* In your web browser

Use the tabs at the top of this article to display instructions for each of these ways of deleting a codespace.

> \[!NOTE]
> You can't delete a codespace from within JupyterLab.

## Why you should delete unused codespaces

There are costs associated with storing codespaces. You should therefore delete any codespaces you no longer need. See [GitHub Codespaces billing](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/about-billing-for-github-codespaces).

There are limits to the number of codespaces you can create, and the number of codespaces you can run at the same time. These limits vary based on a number of factors. If you reach the maximum number of codespaces and try to create another, a message is displayed telling you that you must remove an existing codespace before you can create a new one.

## Deleting a codespace

<div class="ghd-tool webui">

1. In the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces** to take you to the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces).
2. To the right of the codespace you want to delete, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Codespace configuration" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-trash" aria-label="trash" role="img"><path d="M11 1.75V3h2.25a.75.75 0 0 1 0 1.5H2.75a.75.75 0 0 1 0-1.5H5V1.75C5 .784 5.784 0 6.75 0h2.5C10.216 0 11 .784 11 1.75ZM4.496 6.675l.66 6.6a.25.25 0 0 0 .249.225h5.19a.25.25 0 0 0 .249-.225l.66-6.6a.75.75 0 0 1 1.492.149l-.66 6.6A1.748 1.748 0 0 1 10.595 15h-5.19a1.75 1.75 0 0 1-1.741-1.575l-.66-6.6a.75.75 0 1 1 1.492-.15ZM6.5 1.75V3h3V1.75a.25.25 0 0 0-.25-.25h-2.5a.25.25 0 0 0-.25.25Z"></path></svg> Delete**.

   ![Screenshot of a list of codespaces with the dropdown menu for one of them displayed, showing the "Delete" option.](/assets/images/help/codespaces/delete-codespace.png)

</div>

> \[!NOTE]
> You may have prebuild codespaces that are consuming additional storage which are not displayed on this dashboard. To delete them, follow the steps for “[Deleting a prebuild configuration](/en/codespaces/prebuilding-your-codespaces/managing-prebuilds#deleting-a-prebuild-configuration).”

<div class="ghd-tool vscode">

You can delete codespaces from within VS Code when you are not currently working in a codespace.

1. In VS Code, in the Activity Bar, click the Remote Explorer icon.

   ![Screenshot of the Activity Bar. The icon for the "Remote Explorer" side bar (a rectangle overlaid by a circle) is highlighted with an orange outline.](/assets/images/help/codespaces/click-remote-explorer-icon-vscode.png)

   > \[!NOTE]
   > If the Remote Explorer is not displayed in the Activity Bar:
   >
   > 1. Access the Command Palette. For example, by pressing <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd> (Mac) / <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux).
   > 2. Type: `details`.
   > 3. Click **Codespaces: Details**.
2. Under "GitHub Codespaces," right-click the codespace you want to delete.
3. Click **Delete Codespace**.

</div>

<div class="ghd-tool cli">

> \[!NOTE]
> To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

To delete a codespace use the `gh codespace delete` subcommand and then choose a codespace from the list that's displayed.

```shell
gh codespace delete
```

If you have unsaved changes, you'll be prompted to confirm deletion. You can use the `--force` flag to force deletion, avoiding this prompt.

For more information about this command, see [the GitHub CLI manual](https://cli.github.com/manual/gh_codespace_delete).

</div>

## Bulk deleting codespaces

<div class="ghd-tool webui">

You can use GitHub CLI to delete several or all of your codespaces with a single command. For more information, click the "GitHub CLI" tab near the top of this page.

</div>

<div class="ghd-tool vscode">

You can use GitHub CLI to delete several or all of your codespaces with a single command. For more information, click the "GitHub CLI" tab near the top of this page.

</div>

<div class="ghd-tool cli">

You can delete several or all of your codespaces with a single command, using `gh codespace delete` followed by one of these flags:

`--all` - Delete all of your codespaces.

`--repo REPOSITORY` - Delete all of your codespaces for this repository. Or use together with the `--days` flag to filter by age of the codespace.

`--days NUMBER` - Delete all of your codespaces that are older than the specified number of days. Can be used together with the `--repo` flag.

By default you are prompted to confirm deletion of any codespaces that contain unsaved changes. You can use the `--force` flag to skip this confirmation.

### Example

Delete all of the codespaces for the `octo-org/octo-repo` repository that you created more than 7 days ago.

```shell
gh codespace delete --repo octo-org/octo-repo --days 7
```

</div>

## Deleting codespaces in your organization

As an organization owner, you can use GitHub CLI to delete any codespace in your organization.

<div class="ghd-tool webui">

For more information, click the "GitHub CLI" tab near the top of this page.

</div>

<div class="ghd-tool vscode">

For more information, click the "GitHub CLI" tab near the top of this page.

</div>

<div class="ghd-tool cli">

1. Enter one of these commands to display a list of codespaces.
   * `gh codespace delete --org ORGANIZATION` - Lists the current codespaces in the specified organization.
   * `gh codespace delete --org ORGANIZATION --user USER` - Lists only those codespaces created by the specified user.
     You must be an owner of the specified organization.
2. In the list of codespaces, navigate to the codespace you want to delete.
3. To delete the selected codespace press <kbd>Enter</kbd>.

   If the codespace contains unsaved changes you will be prompted to confirm deletion.

</div>

You can also use the REST API to delete codespaces for your organization. See [REST API endpoints for Codespaces organizations](/en/rest/codespaces/organizations#delete-a-codespace-from-the-organization).

## Further reading

* [Understanding the codespace lifecycle](/en/codespaces/about-codespaces/understanding-the-codespace-lifecycle)
* [Configuring automatic deletion of your codespaces](/en/codespaces/setting-your-user-preferences/configuring-automatic-deletion-of-your-codespaces)
* [Restricting the retention period for codespaces](/en/codespaces/managing-codespaces-for-your-organization/restricting-the-retention-period-for-codespaces)