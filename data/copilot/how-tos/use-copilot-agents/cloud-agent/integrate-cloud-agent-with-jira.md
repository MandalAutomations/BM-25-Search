# Integrating Copilot cloud agent with Jira

You can use the GitHub integration in Jira to provide context and open pull requests, all from within your Jira workspace.

> \[!NOTE]
>
> * This feature is currently in public preview and subject to change.
> * GitHub Copilot uses AI. Check for mistakes. See [Responsible use of GitHub Copilot cloud agent on GitHub.com](/en/copilot/responsible-use/copilot-cloud-agent).
> * You can provide feedback about the GitHub Copilot for Jira integration in the [GitHub survey](https://www.surveymonkey.com/r/CCAforJira).

The GitHub Copilot integration in Jira allows you to invoke Copilot cloud agent without leaving your Jira workspace. From within a Jira work item you can initiate cloud agent sessions and open pull requests, using the context of the work item's title, description, labels, and comments.

## Prerequisites

* You must have a GitHub account with access to Copilot through Copilot Pro, Copilot Pro+, Copilot Business, or Copilot Enterprise.
* You must have a Jira Cloud account with the following AI features enabled for your organization:
  * **Jira must be an AI-enabled app** and Rovo must be activated. See [Activate AI for apps](https://support.atlassian.com/organization-administration/docs/activate-atlassian-intelligence-for-products) in the Atlassian documentation.
  * **Beta AI features** must be turned on. See [Control access to beta AI features](https://support.atlassian.com/organization-administration/docs/control-access-to-beta-ai-features/) in the Atlassian documentation.<!-- markdownlint-disable-line GHD046 -->
* Installation and authentication must be completed for both Jira and GitHub.

> \[!NOTE]
> If your Jira site is on release tracks, you should contact Atlassian Support and ask for agents to be enabled in Jira before proceeding with the installation. For more information, see [What are release tracks?](https://support.atlassian.com/organization-administration/docs/what-are-release-tracks/) in the Atlassian documentation.

## Installation

To install the GitHub Copilot for Jira app and authorize it for your GitHub organization or enterprise account, you need:

* Administrator permission for your Jira site.
* Owner or GitHub App manager permissions for your GitHub organization.

This integration relies on an Atlassian Forge application and a GitHub application. Both are required for the integration. Once successfully installed, authorized users of the Jira workspace with **write** access to a GitHub repository will be able to trigger the agent from Jira.

### Installing the GitHub Copilot for Jira app for GitHub.com

1. Navigate to the [GitHub Copilot for Jira installation page](https://marketplace.atlassian.com/apps/1582455624?ref_product=copilot\&ref_type=engagement\&ref_style=text) on the Atlassian Marketplace.
2. Click **Get app**.
3. Select the Atlassian instance you want to install the GitHub application in.
4. Click **Install**.
5. If you are not automatically redirected, go to the [GitHub Copilot for Jira installation page](https://github.com/apps/github-copilot-for-jira?ref_product=copilot\&ref_type=engagement\&ref_style=text) on the GitHub Marketplace and click **Install**.
6. In the **Install GitHub Copilot for Jira** page, select the organization and repositories you would like to give the application access to.
   * You can add additional organizations after the app is installed, see [Adding an organization to the GitHub Copilot for Jira app](#adding-an-organization).
7. Click **Install**.

### Installing the GitHub Copilot for Jira app for GHE.com

1. Navigate to the [GitHub Copilot for Jira (GHEC with Data Residency) installation page](https://marketplace.atlassian.com/apps/3637796809?ref_product=copilot\&ref_type=engagement\&ref_style=text) on the Atlassian Marketplace.
2. To the right of the app name, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Configure" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, and enter your `SUBDOMAIN.ghe.com` in the text box. Replace SUBDOMAIN with your enterprise's subdomain of GHE.com.
3. Click **Save configuration**.
4. Click **Get app**.
5. Select the Atlassian instance you want to install the GitHub application in.
6. Click **Install**.
7. If you are not automatically redirected, find the GitHub Copilot for Jira app in the list of apps available to your enterprise at `SUBDOMAIN.ghe.com/apps/external-app/github-copilot-for-jira`.
8. Click **Install**.
9. In the **Install GitHub Copilot for Jira** page, select the organization and repositories you would like to give the application access to.
   * You can add additional organizations after the app is installed, see [Adding an organization to the GitHub Copilot for Jira app](#adding-an-organization).
10. Click **Install**.

## Adding an organization to the GitHub Copilot for Jira app

Once the GitHub Copilot for Jira app has been installed, a Jira administrator and GitHub organization owner can enable additional organizations to use the app. This allows any member of the organization to connect their GitHub account to the app and start using it in Jira.

To enable the GitHub Copilot for Jira app for an organization:

1. In Jira, go to the settings page for your space.
2. Go to the applications setting page for the GitHub Copilot app.
3. Optionally, click **Connect More GitHub Organizations** to add new organizations to the list.
4. Enable the Copilot app for one or more of the listed organizations.

## Using the GitHub Copilot app in Jira

The Copilot app must be enabled for a GitHub organization you are a member of, before you can start using it.

The first time you use Copilot cloud agent in Jira, you will need to connect it to your GitHub account.

Only users with **write** access to a repository can trigger Copilot cloud agent to work in that repository.

You can trigger Copilot cloud agent in three ways:

* **Assign** GitHub Copilot to a work item using the Assignee field.
* **Mention** `@GitHub Copilot` in a comment on a work item.
* **Add Copilot to a workflow transition** so it is triggered automatically when a work item moves to a specific status. See [Collaborate on work items with AI agents](https://support.atlassian.com/jira-software-cloud/docs/collaborate-on-work-items-with-ai-agents/#Add-an-agent-to-workflow-transitions) for setup instructions.

To change the model used by Copilot cloud agent for a specific task, include the model name in your instructions to Copilot. For example, you can say `@GitHub Copilot use Claude Sonnet 4.5 to create a new API endpoint for user authentication in octo-org/octorepo`. If you do not specify a model, Copilot cloud agent will use the default model for coding tasks, see [Changing the AI model for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/changing-the-ai-model).

> \[!NOTE]
> When you assign Copilot to a Jira work item, the context the agent captures from Jira will be added to the pull request and **visible to everyone** if the repository is public.

### Example: Triggering Copilot cloud agent from a Jira work item

1. In Jira, open or create a work item that contains clear requirements you want to delegate to Copilot cloud agent.

2. To specify a repository you want Copilot to work in, mention it in the work item description or in a comment.

3. Assign `GitHub Copilot` to the work item, or mention `@GitHub Copilot` in a comment. For example:

   ```text
   @GitHub Copilot create a new API endpoint for user authentication in octo-org/octorepo
   ```

4. If you have not previously connected the GitHub application in Jira to your GitHub account, follow the prompts to authorize the application for both GitHub and Atlassian.

5. Once Copilot cloud agent has started working on the pull request, a comment will appear in the Jira work item. The user who initiated the agent session can view progress updates for the agent.

6. You can follow up with further instructions for Copilot in a work item:
   * Mention `@GitHub Copilot` in a comment.
   * Use the **Continue in Chat** button under the **Agents** heading to chat directly with Copilot.

> \[!TIP]
> If you have not received confirmation of triggering Copilot cloud agent after 1 minute, refresh the Jira work item page.

## Usage costs

Copilot cloud agent uses GitHub Actions minutes and Copilot premium requests.

Within your monthly usage allowance for GitHub Actions and premium requests, you can ask Copilot cloud agent to work on coding tasks without incurring any additional costs.

For more information, see [GitHub Copilot premium requests](/en/billing/concepts/product-billing/github-copilot-premium-requests#usage-by-copilot-cloud-agent).

## Troubleshooting

If you run into problems, try the following solutions.

### You can't see the Copilot cloud agent and it is not possible to assign it to a Jira work item

In Jira, check your Atlassian Administration settings for your organization are set as follows.

1. Jira is an AI-enabled app, see [Activate AI for apps](https://support.atlassian.com/organization-administration/docs/activate-atlassian-intelligence-for-products) in the Atlassian documentation.
2. Beta AI features are enabled, see [Control access to beta AI features](https://support.atlassian.com/organization-administration/docs/control-access-to-beta-ai-features/) in the Atlassian documentation.<!-- markdownlint-disable-line GHD046 -->

### You can see the Copilot cloud agent but it is not possible to assign it to a Jira work item

Check that you have connected your personal account on GitHub to the GitHub Copilot for Jira app.

1. In Jira, go to the settings page for your personal account.
2. Under your general settings, select the **GitHub Copilot for Jira** app.
3. If you are not already signed in with GitHub, follow the prompts to sign in and authorize the application.

### When chatting with GitHub Copilot, you are prompted to sign in

To sign in to GitHub Copilot for Jira app, follow the steps above in [You can see the Copilot cloud agent but it is not possible to assign it to a Jira work item](#you-can-see-the-copilot-cloud-agent-but-it-is-not-possible-to-assign-it-to-a-jira-work-item)

### GitHub Copilot is not responding

* Check GitHub's [Status page](https://githubstatus.com) for any active incidents.
* Verify that Copilot cloud agent has access to the repository by testing if you can assign Copilot to an issue on GitHub. See [Managing access to GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/access-management).
* Verify that the GitHub Copilot for Jira application has access to the repository. See [Reviewing and modifying installed GitHub Apps](/en/apps/using-github-apps/reviewing-and-modifying-installed-github-apps#modifying-repository-access).

## Further reading

* [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent)
* [Managing access to GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/access-management)
* [Extending GitHub Copilot cloud agent with the Model Context Protocol (MCP)](/en/copilot/how-tos/use-copilot-agents/cloud-agent/extend-cloud-agent-with-mcp#example-atlassian)
* [Collaborate on work items with AI agents](https://support.atlassian.com/jira-software-cloud/docs/collaborate-on-work-items-with-ai-agents/) in the Atlassian documentation