# Configuring automatic deletion of your codespaces

Inactive codespaces are automatically deleted. You can choose how long your stopped codespaces are retained, up to a maximum of 30 days.

By default, GitHub Codespaces are automatically deleted after they have been stopped and have remained inactive for 30 days.

However, because GitHub Codespaces incurs storage charges, you may prefer to reduce the retention period by changing your default period in your personal settings for GitHub Codespaces. For more information about storage charges, see [GitHub Codespaces billing](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/about-billing-for-github-codespaces#codespaces-pricing).

> \[!NOTE]
> Whether or not you have set a personal codespace retention period, it's a good idea to get into the habit of deleting codespaces that you no longer need. See [Deleting a codespace](/en/codespaces/developing-in-a-codespace/deleting-a-codespace).

Automatic deletion happens irrespective of whether a codespace contains unpushed changes. To prevent automatic deletion of a codespace, just open the codespace again. The retention period is reset every time you connect to a codespace, and the retention countdown restarts when the codespace is stopped.

If a repository belongs to an organization, the organization owner may have set a retention period for the whole organization. If this period is less than the default retention period in your personal settings then the organization retention period will apply to codespaces you create for this repository. See [Restricting the retention period for codespaces](/en/codespaces/managing-codespaces-for-your-organization/restricting-the-retention-period-for-codespaces).

Each codespace has its own retention period. You may, therefore, have codespaces with different retention periods. For example, if:

* You created a codespace, changed your default retention period, then created another codespace.
* You created a codespace using GitHub CLI and specified a different retention period.
* You created a codespace for an organization-owned repository that has a retention period configured in the organization settings. The ownership of the codespaces you create is shown on the [Your codespaces](https://github.com/settings/codespaces) page.

> \[!NOTE]
> The retention period is specified in days. A day represents a 24-hour period, beginning at the time of day when you stop a codespace.

<div class="ghd-tool webui">

## Setting a default retention period for your codespaces

1. In the upper-right corner of any page on GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**.

2. In the "Code, planning, and automation" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces**.

3. Under "Default retention period", enter the number of days for which you want your codespaces to be retained, by default, after they have been stopped.

   ![Screenshot of the "Default retention period" setting, currently set to 1 day. Next to the number of days is the "Save" button.](/assets/images/help/codespaces/setting-default-retention.png)

   You can set your default retention period between `0` and `30` days.

   > \[!WARNING]
   > Setting the period to `0` will result in your codespaces being immediately deleted when you stop them, or when they timeout due to inactivity. See [Setting your timeout period for GitHub Codespaces](/en/codespaces/setting-your-user-preferences/setting-your-timeout-period-for-github-codespaces).

4. Click **Save**.

When you create a codespace using GitHub CLI you can override this default. If you create a codespace in an organization that specifies a shorter retention period, the organization-level value overrides your personal setting.

If you set a retention period of more than a day, you'll be sent an email notification one day prior to its deletion.

## Checking the remaining time until autodeletion

You can check whether a codespace is due to be automatically deleted soon.

When an inactive codespace is approaching the end of its retention period, this is indicated in your list of codespaces on GitHub at <https://github.com/codespaces>.

![Screenshot of a list of three codespaces. The third of these is labeled "Expiring in 4 days" which is highlighted with a dark orange outline.](/assets/images/help/codespaces/retention-deletion-message.png)

## Avoiding automatic deletion of codespaces

You may have a codespace that you want to keep for longer than the retention period defined in your personal settings. You can do this by using the "Keep codespace" option. When you select this option, your codespace will be retained indefinitely, until you delete it manually.

> \[!NOTE]
> The "Keep codespace" option is not available for organization-owned codespaces affected by an organization retention policy.

Codespaces incur storage costs, or consume your included storage allowance if the codespace is owned by your personal GitHub account. You should therefore be aware of the cost implications of storing codespaces indefinitely. See [GitHub Codespaces billing](/en/billing/concepts/product-billing/github-codespaces).

1. In the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces** to take you to the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces).
2. To the right of the codespace you want to exempt from automatic deletion, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Codespace configuration" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-bookmark" aria-label="bookmark" role="img"><path d="M3 2.75C3 1.784 3.784 1 4.75 1h6.5c.966 0 1.75.784 1.75 1.75v11.5a.75.75 0 0 1-1.227.579L8 11.722l-3.773 3.107A.751.751 0 0 1 3 14.25Zm1.75-.25a.25.25 0 0 0-.25.25v9.91l3.023-2.489a.75.75 0 0 1 .954 0l3.023 2.49V2.75a.25.25 0 0 0-.25-.25Z"></path></svg> Keep codespace**.

   ![Screenshot of the dropdown menu for an active codespace. The "Keep codespace" option has a tooltip saying "Expires 10 days after shutdown."](/assets/images/help/codespaces/keep-codespace.png)

Codespaces that you have exempted from automatic deletion are indicated in your list of codespaces with the bookmark icon (<svg version="1.1" width="24" height="24" viewBox="0 0 24 24" class="octicon octicon-bookmark-fill" aria-label="bookmark-fill" role="img"><path d="M6.69 2h10.56c.966 0 1.75.784 1.75 1.75v17.5a.75.75 0 0 1-1.218.585L12 17.21l-5.781 4.626A.75.75 0 0 1 5 21.253L4.94 3.756A1.748 1.748 0 0 1 6.69 2Z"></path></svg>).

![Screenshot of a section of the codespaces list, showing a codespace labeled with the bookmark icon.](/assets/images/help/codespaces/keep-codespace-bookmarked.png)

</div>

<div class="ghd-tool cli">

## Setting a retention period for a codespace

If you have installed GitHub CLI, you can use it to work with GitHub Codespaces. For installation instructions for GitHub CLI, see the [GitHub CLI repository](https://github.com/cli/cli#installation).

To set the codespace retention period when you create a codespace, use the `--retention-period` flag with the `codespace create` subcommand. Specify the period in days. The period must be between 0 and 30 days.

```shell
gh codespace create --retention-period DAYS
```

If you don't specify a retention period when you create a codespace, then either your default retention period, or an organization retention period, will be used, depending on which is lower. For information about setting your default retention period, click the "Web browser" tab on this page.

> \[!NOTE]
> To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

</div>

<div class="ghd-tool vscode">

## Setting the retention period

You can set your default retention period in your web browser, on GitHub. Alternatively, if you use GitHub CLI to create a codespace you can set a retention period for that particular codespace. For more information, click the appropriate tab above.

## Checking whether codespaces will be autodeleted soon

You can check, in the Visual Studio Code desktop application, whether a codespace is due to be automatically deleted soon.

1. In VS Code, in the Activity Bar, click the Remote Explorer icon.

   ![Screenshot of the Activity Bar. The icon for the "Remote Explorer" side bar (a rectangle overlaid by a circle) is highlighted with an orange outline.](/assets/images/help/codespaces/click-remote-explorer-icon-vscode.png)

   > \[!NOTE]
   > If the Remote Explorer is not displayed in the Activity Bar:
   >
   > 1. Access the Command Palette. For example, by pressing <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd> (Mac) / <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux).
   > 2. Type: `details`.
   > 3. Click **Codespaces: Details**.
2. Choose **GitHub Codespaces** from the dropdown menu at the top right of the Remote Explorer, if it is not already selected.
3. Under "GITHUB CODESPACES," position the mouse pointer over the codespace that you're interested in. A pop-up box is displayed showing you information about the codespace.

   If the codespace is nearing the end of its retention period, a line is included telling when this period is due to expire.

   ![Screenshot of the "Remote Explorer" side bar. In the right-click menu for a codespace, "Expiring in 19 days" is highlighted with an orange outline.](/assets/images/help/codespaces/vscode-deleting-in-5-days.png)

</div>

## Further reading

* [Customizing your codespace](/en/codespaces/customizing-your-codespace)
* [Managing your codespaces](/en/codespaces/managing-your-codespaces)