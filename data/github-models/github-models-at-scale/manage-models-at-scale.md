# Managing your team's model usage

Control and secure AI models in your organization with GitHub Models.

> \[!NOTE]
> GitHub Models for organizations and repositories is in public preview and subject to change.

## Why restrict model usage in your organization?

Limiting the models available to your developers can help **control spend on models and meet your governance, data security, and compliance requirements**.

If you don't manage access, your teams may inadvertently use models that do not meet your organization’s standards, leading to potential risks such as:

* Unexpected costs from high-priced models
* Security or compliance issues caused by unauthorized AI services
* Time wasted integrating unapproved or suboptimal models

For more information about using models at scale, see [Using GitHub Models to develop AI-powered applications in your enterprise](/en/github-models/github-models-at-scale/use-models-at-scale).

## Exceptions to your organization's model settings

While GitHub Models for organizations and repositories is in public preview, some of your organization's model settings are not applied in certain circumstances. Your teams will be able to use AI models without limitation in the following places:

* Enterprise Managed Users organizations
* GitHub Models extension for GitHub CLI
* GitHub Models extension for GitHub Copilot Chat
* GitHub Models VS Code extension
* Playground for GitHub Models in the GitHub Marketplace at <https://github.com/marketplace/models>.

## Enabling GitHub Models for an enterprise

For GitHub Models to be available to your organization, an enterprise owner must first enable the feature for the enterprise.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Policies**.
3. Under <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> "Policies", click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-ai-model" aria-label="ai-model" role="img"><path d="M10.628 7.25a2.25 2.25 0 1 1 0 1.5H8.622a2.25 2.25 0 0 1-2.513 1.466L5.03 12.124a2.25 2.25 0 1 1-1.262-.814l1.035-1.832A2.245 2.245 0 0 1 4.25 8c0-.566.209-1.082.553-1.478L3.768 4.69a2.25 2.25 0 1 1 1.262-.814l1.079 1.908A2.25 2.25 0 0 1 8.622 7.25ZM2.5 2.5a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm4 4.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm6.25 0a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm-9.5 5.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> Models**.
4. Under "Models", in the "Models in your enterprise" section, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="the down arrow" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> beside **Disabled** and select one of the following options:
   * **Enabled**: Enable GitHub Models for all organizations in your enterprise.
   * **No policy**: Allow each organization in your enterprise to manage the enablement of GitHub Models independently.

## Controlling model usage in your organization

> \[!NOTE]
> You can only change your organization's Models settings if your enterprise policies allow access to GitHub Models.

You can choose to enable or disable GitHub Models for your organization. You can also choose to only allow the use of selected models or model publishers. For more information, see the instructions below.

You can also integrate your preferred external LLM models by bringing your own keys (BYOK) to GitHub Models. See [Using your own API keys in GitHub Models](/en/github-models/github-models-at-scale/set-up-custom-model-integration-models-byok)

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.

2. Select an organization by clicking on it.

3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)

4. In the "Code, planning, and automation" section of the sidebar, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-ai-model" aria-label="ai-model" role="img"><path d="M10.628 7.25a2.25 2.25 0 1 1 0 1.5H8.622a2.25 2.25 0 0 1-2.513 1.466L5.03 12.124a2.25 2.25 0 1 1-1.262-.814l1.035-1.832A2.245 2.245 0 0 1 4.25 8c0-.566.209-1.082.553-1.478L3.768 4.69a2.25 2.25 0 1 1 1.262-.814l1.079 1.908A2.25 2.25 0 0 1 8.622 7.25ZM2.5 2.5a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm4 4.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm6.25 0a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm-9.5 5.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> Models** dropdown. Then click **Development**.

5. Under "Models", in the "Models in your organization" section, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="the down arrow" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> beside **Disabled** and select **Enabled** from the dropdown.

   > \[!NOTE]
   > If GitHub Models is already enabled for the organization, the dropdown will show **Enabled**, and you can skip the step above.

6. Under "Models permissions", select one or more options.

   * **All publishers** is the default option and indicates that models from all the current and future publishers available on the GitHub Models catalog from the GitHub Marketplace can be used in the organization.
   * **Only select models** allows you to define a list of models and publishers:
     * Available to the organization (**Enabled list**)
     * Restricted for use in the organization (**Disabled list**)

   Depending on your requirements, you can specify an enabled list, a disabled list, or both.
   Once you've added a publisher to a list, you can fine-tune the list by removing individual models from it.