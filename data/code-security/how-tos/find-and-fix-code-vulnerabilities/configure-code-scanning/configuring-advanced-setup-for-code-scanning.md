# Configuring advanced setup for code scanning

You can configure advanced setup for a repository to find security vulnerabilities in your code using a highly customizable code scanning configuration.

If you do not need a highly customizable code scanning configuration, consider using default setup for code scanning. For more information, see [About setup types for code scanning](/en/code-security/concepts/code-scanning/setup-types).

## Prerequisites

Your repository is eligible for advanced setup if it meets these requirements.

* It uses CodeQL-supported languages or you plan to generate code scanning results with a third-party tool.
* GitHub Actions is enabled.
* It is publicly visible, or GitHub Code Security is enabled.

## Configuring advanced setup for code scanning with CodeQL

You can customize your CodeQL analysis by creating and editing a workflow file. Selecting advanced setup generates a basic workflow file for you to customize using standard workflow syntax and specifying options for the CodeQL action. See [Workflows](/en/actions/using-workflows/about-workflows) and [Workflow configuration options for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning).

Using actions to run code scanning will use minutes. For more information, see [GitHub Actions billing](/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions).

> \[!NOTE]
> You can configure code scanning for any public repository where you have write access.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)

3. In the "Security" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced Security**.

4. Scroll down to "Code Security", in the "CodeQL analysis" row select **Set up** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg>, then click **Advanced**.

   > \[!NOTE]
   > If you are switching from default setup to advanced setup, in the "CodeQL analysis" row, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Menu" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-workflow" aria-label="workflow" role="img"><path d="M0 1.75C0 .784.784 0 1.75 0h3.5C6.216 0 7 .784 7 1.75v3.5A1.75 1.75 0 0 1 5.25 7H4v4a1 1 0 0 0 1 1h4v-1.25C9 9.784 9.784 9 10.75 9h3.5c.966 0 1.75.784 1.75 1.75v3.5A1.75 1.75 0 0 1 14.25 16h-3.5A1.75 1.75 0 0 1 9 14.25v-.75H5A2.5 2.5 0 0 1 2.5 11V7h-.75A1.75 1.75 0 0 1 0 5.25Zm1.75-.25a.25.25 0 0 0-.25.25v3.5c0 .138.112.25.25.25h3.5a.25.25 0 0 0 .25-.25v-3.5a.25.25 0 0 0-.25-.25Zm9 9a.25.25 0 0 0-.25.25v3.5c0 .138.112.25.25.25h3.5a.25.25 0 0 0 .25-.25v-3.5a.25.25 0 0 0-.25-.25Z"></path></svg> Switch to advanced**. In the pop-up window that appears, click **Disable CodeQL**.

   ![Screenshot of the "Code Security" section of "Advanced Security" settings. The "Advanced setup" button is highlighted with an orange outline.](/assets/images/help/security/advanced-code-scanning-setup-ghas.png)

5. To customize how code scanning scans your code, edit the workflow.

   Generally, you can commit the CodeQL analysis workflow without making any changes to it. However, many of the third-party workflows require additional configuration, so read the comments in the workflow before committing.

   For more information, see [Workflow configuration options for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning) and [CodeQL code scanning for compiled languages](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/codeql-code-scanning-for-compiled-languages).

6. Click **Commit changes...** to display the commit changes form.

   ![Screenshot of the form to create a new file. To the right of the file name, a green button, labeled "Commit changes...", is outlined in dark orange.](/assets/images/help/repository/start-commit-commit-new-file.png)

7. In the commit message field, type a commit message.

8. Choose whether you'd like to commit directly to the default branch, or create a new branch and start a pull request.

9. Click **Commit new file** to commit the workflow file to the default branch or click **Propose new file** to commit the file to a new branch.

10. If you created a new branch, click **Create pull request** and open a pull request to merge your change into the default branch.

In the suggested CodeQL analysis workflow, code scanning is configured to analyze your code each time you either push a change to the default branch or any protected branches, or raise a pull request against the default branch. As a result, code scanning will now commence.

The `on:pull_request` and `on:push` triggers for code scanning are each useful for different purposes. See [Workflow configuration options for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning#scan-frequency) and [Triggering a workflow](/en/actions/using-workflows/triggering-a-workflow).

For information on bulk enablement, see [Configuring advanced setup for code scanning with CodeQL at scale](/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/configuring-advanced-setup-for-code-scanning-with-codeql-at-scale).

## Configuring code scanning using third-party actions

GitHub includes workflow templates for third-party actions, as well as the CodeQL action. Using a workflow template is much easier than writing a workflow unaided.

Using actions to run code scanning will use minutes. For more information, see [GitHub Actions billing](/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions).

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)

3. If the repository has already at least one workflow configured and running, click **New workflow** to display workflow templates. If there are currently no workflows configured for the repository, go to the next step.

   ![Screenshot of the Actions tab for a repository. The "New workflow" button is outlined in dark orange.](/assets/images/help/security/actions-new-workflow-button.png)

4. In the "Choose a workflow" or "Get started with GitHub Actions" view, scroll down to the "Security" category and click **Configure** under the workflow you want to configure. You may need to click **View all** to find the security workflow you want to configure.

   ![Screenshot of the Security category of workflow templates. The Configure button and "View all" link are highlighted with an orange outline.](/assets/images/help/security/actions-workflows-security-section.png)

5. Follow any instructions in the workflow to customize it to your needs. For more general assistance about workflows, click **Documentation** on the right pane of the workflow page.

   ![Screenshot showing a workflow template file open for editing. The "Documentation" button is highlighted with an orange outline.](/assets/images/help/security/actions-workflows-documentation.png)

6. When you have finished defining your configuration, add the new workflow to your default branch.

   For more information, see [Using workflow templates](/en/actions/learn-github-actions/using-starter-workflows#choosing-and-using-a-starter-workflow) and [Workflow configuration options for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning).

## Next steps

After your workflow runs successfully at least once, you are ready to start examining and resolving code scanning alerts. For more information on code scanning alerts, see [About code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/about-code-scanning-alerts) and [Assessing code scanning alerts for your repository](/en/code-security/code-scanning/managing-code-scanning-alerts/assessing-code-scanning-alerts-for-your-repository).

Learn how code scanning runs behave as checks on pull requests, see [Triaging code scanning alerts in pull requests](/en/code-security/code-scanning/managing-code-scanning-alerts/triaging-code-scanning-alerts-in-pull-requests#about-code-scanning-as-a-pull-request-check).

You can find detailed information about your code scanning configuration, including timestamps for each scan and the percentage of files scanned, on the tool status page. For more information, see [Use the tool status page for code scanning](/en/code-security/code-scanning/managing-your-code-scanning-configuration/about-the-tool-status-page).

### Further reading

* [Triaging code scanning alerts in pull requests](/en/code-security/code-scanning/managing-code-scanning-alerts/triaging-code-scanning-alerts-in-pull-requests).
* [Configuring notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications#github-actions-notification-options).
* [Workflow configuration options for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning).
* [Viewing code scanning logs from GitHub Actions](/en/code-security/code-scanning/managing-your-code-scanning-configuration/viewing-code-scanning-logs).