# Integrating Copilot cloud agent with Linear

Use the Copilot integration in Linear to provide context and open pull requests, all from within your Linear workspace.

> \[!NOTE]
>
> * This feature is currently in public preview and subject to change.
> * GitHub Copilot uses AI. Check for mistakes. See [Responsible use of GitHub Copilot cloud agent on GitHub.com](/en/copilot/responsible-use/copilot-cloud-agent).

The Copilot integration in Linear allows you to invoke Copilot cloud agent without leaving your Linear workspace. From within a Linear issue you can initiate cloud agent sessions and open pull requests, using the context of your issue description and comments.

For information about additional Copilot integrations, see [About Copilot integrations](/en/copilot/concepts/tools/about-copilot-integrations).

> \[!NOTE]
> When you mention @GitHub in, or assign Copilot to, a Linear issue, the agent will capture the entire issue description and comments as context for your request. This helps the agent to understand the issue, and implement an appropriate solution, based on all of the information in the issue. This context is stored in the pull request.

## Prerequisites

* You must have a GitHub account with access to Copilot through Copilot Pro, Copilot Pro+, Copilot Business, or Copilot Enterprise.
* You must have a Linear account and be a member of a team.

## Installing the Copilot app in Linear

> \[!NOTE] In order to install the Copilot app in Linear, be an owner of the organization or enterprise where you want to install the app. You must also be a workspace admin in Linear.

The Copilot app only needs to be installed once in an organization. After the app is installed, any member of the organization can connect their Copilot account to the app and start using it.

1. Go to the [Copilot for Linear page](https://github.com/apps/github-copilot-for-linear?ref_product=copilot\&ref_type=engagement\&ref_style=text) and click **Configure**.
2. Follow the prompts on screen to configure and authorize the app in the organization or enterprise where you want to use it.

## Using the Copilot app in Linear

The first time you use the Copilot app in Linear, you will need to connect it to your GitHub account. You will also need to specify a repository for Copilot cloud agent to use. Only users with **write** access to the specified repository can trigger Copilot cloud agent to work in that repository. Contributors to the issue without repository **write** access can help guide Copilot by providing input to the issue conversation, which will be used as context when creating the pull request.

1. In Linear, create an issue where you want to use Copilot cloud agent.
2. Click the **Assign** dropdown, then select **GitHub Copilot**.
3. If you haven't yet specified a repository for Copilot cloud agent to use, you will be prompted to do so now. This is where Copilot cloud agent will open the pull request related to this issue.
4. If this is your first time using the app, you will be prompted to sign in to your GitHub account and authorize the app. Follow the prompts to complete the authorization.
5. In the "Links" section of your Linear issue, you will now see a linked "\[WIP]" pull request created by Copilot cloud agent. Click the link to view the pull request on GitHub.
6. Once Copilot cloud agent has finished working on the pull request, a notification will be added to the "Activity" section of your Linear issue.

## Further reading

* [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent)
* [Managing access to GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/access-management)