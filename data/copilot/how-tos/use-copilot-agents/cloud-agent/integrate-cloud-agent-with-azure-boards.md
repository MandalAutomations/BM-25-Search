# Integrating Copilot cloud agent with Azure Boards

Use the Copilot integration in Azure Boards to send work items directly to Copilot cloud agent and generate pull requests, all from within your Azure DevOps workspace.

The Azure Boards GitHub integration allows you to invoke Copilot cloud agent without leaving your workspace. From within a Azure Boards work item you can initiate cloud agent sessions and open pull requests, using the context of your work item description and comments.

For information about additional Copilot integrations, see [About Copilot integrations](/en/copilot/concepts/tools/about-copilot-integrations).

> \[!NOTE]
>
> * GitHub Copilot uses AI. Check for mistakes. See [Responsible use of GitHub Copilot cloud agent on GitHub.com](/en/copilot/responsible-use/copilot-cloud-agent).
> * When you send a work item to Copilot cloud agent, the agent will capture content from text fields (such as the description and reproduction steps), along with the last 50 comments. This context is stored in the pull request, and is visible to anyone with access to the repository.

## Prerequisites

* You must have a GitHub account with access to Copilot through Copilot Pro, Copilot Pro+, Copilot Business, or Copilot Enterprise.
* The repositories connected to the Azure DevOps project must have Copilot cloud agent enabled.

## Installing the Azure Boards application on GitHub

> \[!NOTE]
> To install the Azure Boards application, you must be an owner or App manager of the organization or enterprise on GitHub.

The Azure Boards app only needs to be installed once in an organization. After the app is installed, any member of the organization can connect their GitHub account to the app and start using it.

1. Go to the [Azure Boards installation page](https://github.com/marketplace/azure-boards).
2. Scroll to the bottom of the page, then use the **Account** dropdown menu to select an account you would like to install the app in.
3. Click **Install**.
4. Select the repositories you would like the Azure Boards app to have access to.
5. Follow the prompts on screen to configure and authorize the app in your Azure DevOps organization and project.

## Approving the Azure Boards application permissions

If you already have the Azure Boards application installed on GitHub, you will need to approve the required permission changes to allow the app to communicate with GitHub Copilot.

1. Navigate to [your installed GitHub Apps](https://github.com/settings/installations).
2. Find the Azure Boards application, then click the **Review request** link.
3. Review the permissions, then click **Accept new permission**.

## Creating a pull request from a work item

1. In Azure Boards, open the work item you want to send to Copilot cloud agent.
2. Click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> icon on the work item.
3. Select **Create a pull request with Copilot**.
4. Under **GitHub repository**, select the repository where Copilot should create the pull request.
5. Optionally, change the base branch that Copilot should use for the pull request.
6. Optionally, add any additional instructions to provide Copilot with more context.
7. Click **Create**.

Copilot cloud agent will begin processing the work item and create a draft pull request linked back to the work item.

## Further reading

* [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent)
* [Managing access to GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/access-management)