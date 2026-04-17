# Setting your timeout period for GitHub Codespaces

You can set your default timeout for GitHub Codespaces in your personal settings page.

## About the idle timeout

A codespace will stop running after a period of inactivity. By default this period is 30 minutes, but you can specify a longer or shorter default timeout period in your personal settings on GitHub. The updated setting will apply to any new codespaces you create. You can also specify a timeout when you use GitHub CLI to create a codespace.

> \[!WARNING]
> Codespaces compute usage is billed for the duration for which a codespace is active. If you're not using a codespace but it remains running, and hasn't yet timed out, you are billed for the total time that the codespace was active, irrespective of whether you were using it. For more information, see [GitHub Codespaces billing](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/about-billing-for-github-codespaces#codespaces-pricing).

### Inactivity defined

In the context of the Codespaces idle timeout, inactivity is defined as the absence of activity indicative of a user's presence. Personal interaction with a codespace, such as typing or using the mouse, resets the idle timeout period. Terminal activity, either input or output, also resets the idle timeout period. For example, if you publish a web app on a port from a codespace and page requests generate output in a terminal on the codespace, then each time terminal output occurs the timeout will be reset. However, if you share a port, and then don't interact with the codespace, and no terminal output is generated, the codespace will time out after the configured period.

### Timeout periods for organization-owned repositories

Organizations can set a maximum idle timeout policy for codespaces created from some or all of their repositories. If an organization policy sets a maximum timeout which is less than the default timeout you have set, the organization's timeout will be used instead of your setting. You will be notified of this after the codespace is created. For more information, see [Restricting the idle timeout period](/en/codespaces/managing-codespaces-for-your-organization/restricting-the-idle-timeout-period).

<div class="ghd-tool webui">

## Setting your default timeout period

1. In the upper-right corner of any page on GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**.
2. In the "Code, planning, and automation" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces**.
3. Under "Default idle timeout", enter the time that you want, then click **Save**. The time must be between 5 minutes and 240 minutes (4 hours).

   ![Screenshot of the "Default idle timeout" section of the Codespaces settings, with "90 minutes" entered.](/assets/images/help/codespaces/setting-default-timeout.png)

</div>

<div class="ghd-tool cli">

## Setting the timeout period for a codespace

> \[!NOTE]
> To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

To set the timeout period when you create a codespace, use the `idle-timeout` argument with the `codespace create` subcommand. Specify the time in minutes, followed by `m`. The time must be between 5 minutes and 240 minutes (4 hours).

```shell
gh codespace create --idle-timeout 90m
```

If you don't specify a timeout period when you create a codespace, then the default timeout period will be used. For information about setting a default timeout period, click the "Web browser" tab on this page. You can't currently specify a default timeout period through GitHub CLI.

</div>

<div class="ghd-tool vscode">

## Setting a timeout period

You can set your default timeout period in your web browser, on GitHub. Alternatively, if you use GitHub CLI to create a codespace you can set a timeout period for that particular codespace. For more information, click the appropriate tab above.

</div>

## Further reading

* [Customizing your codespace](/en/codespaces/customizing-your-codespace)
* [Managing your codespaces](/en/codespaces/managing-your-codespaces)