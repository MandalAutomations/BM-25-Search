# Integrating Copilot cloud agent with Slack

Provide context to the Copilot cloud agent and open pull requests, all from within your Slack workspace.

> \[!NOTE]
>
> * This feature is in public preview and subject to change.
> * GitHub Copilot uses AI. Check for mistakes. See [Responsible use of GitHub Copilot cloud agent on GitHub.com](/en/copilot/responsible-use/copilot-cloud-agent)

## Introduction

The Copilot cloud agent integration in Slack allows you to interact with Copilot cloud agent from your Slack workspace and is included in the GitHub App for Slack. From within a Slack thread or direct message, you can initiate cloud agent sessions using the context of your conversation.

For information about additional Copilot integrations, see [About Copilot integrations](/en/copilot/concepts/tools/about-copilot-integrations).

## Security considerations

When you @mention Copilot in Slack, consider the following.

* Copilot may perform write actions on your behalf, such as creating pull requests or issues, in addition to answering questions. Copilot uses the permissions of your linked GitHub account for any actions it takes.
* Copilot cloud agent will capture the entire thread as context for your request, understanding and implementing solutions based on the discussion. This context is stored in the pull request. If you want to limit the context, you can send a direct message to the GitHub App for Slack instead.

## Prerequisites

* You must have a GitHub account with access to Copilot through Copilot Pro, Copilot Pro+, Copilot Business, or Copilot Enterprise.
* You must have a Slack account and be a member of a workspace.
* You must have the GitHub App for Slack installed. See [Integrating GitHub with Slack](/en/integrations/how-tos/slack/integrate-github-with-slack).

## Connecting the GitHub App to your GitHub account

The first time you use the GitHub App in Slack, the app will prompt you to connect it to your GitHub account and set a default repository. The default repository is where pull requests created by Copilot cloud agent sessions will be opened.

1. In Slack, open a direct message with the GitHub App or mention Copilot in a thread by typing `@GitHub Copilot`.
2. Send a prompt to Copilot cloud agent. This can be a request to perform a task, or simply `login`.
3. If asked to connect your GitHub account, follow the instructions in Copilot's reply and authorize the app to access your GitHub account.
4. In the Slack message thread, click **Configure settings** to set a default repository for pull requests. You can change this repository later using the `settings` command.
5. In the "Settings" dialog, type the name of a repository where you'll be using the cloud agent, then click **Save changes**.

## Using the GitHub App in Slack

You can send the GitHub App direct messages or mention it in a thread. The bot will respond to your messages and perform tasks based on your requests.

You must have write access to the default repository – or the repository specified in your prompt – in order to trigger Copilot cloud agent to work. If you do not have write access to the relevant repository, you can still help guide Copilot by providing input in the Slack thread, which will be used as context when Copilot cloud agent makes changes in the pull request.

Users can invoke Copilot cloud agent on any repository where they have `write` access. For enterprise-owned repositories, administrators must install and configure the [Slack GitHub App](https://github.com/marketplace/slack-github?ref_product=copilot\&ref_type=engagement\&ref_style=text\&ref_plan=enterprise) and specify which repositories the Slack app can access. For more information about configuring GitHub Apps, see [Installing a GitHub App from GitHub Marketplace for your organizations](/en/apps/using-github-apps/installing-a-github-app-from-github-marketplace-for-your-organizations).

1. In Slack, open a direct message with the GitHub App or mention the app in a thread by typing `@GitHub Copilot`.

2. Type your prompt, then send it. Optionally, you can specify a repository or branch using the following syntax:

   `@GitHub Add "Hello World" to the README in repo=REPO_OWNER/REPO_NAME branch=BRANCH_NAME`

   > \[!NOTE] The repo parameter tells Copilot cloud agent which repository to use for the request, and the branch parameter specifies an existing branch of the repository that should be used as the base branch for a pull request. By default, Copilot uses your configured default repository and the repository’s default branch.

3. Copilot cloud agent will initiate a cloud agent session and, once the cloud agent has finished, respond with a summary of the changes it plans to make and a link to the pull request it has created in the default repository.

### Creating an issue with Copilot

You can ask Copilot to draft GitHub issues directly from Slack, turning conversations into actionable tasks. When you mention Copilot, it uses the full thread history as context for the issue it drafts. To keep the context focused, consider starting a new thread or sending a direct message.

1. In Slack, ask Copilot to create an issue, specifying the target repository.

   For example:

   ```text
   @GitHub In octo-org/octo-repo, create a feature request to add fuzzy matching to search.
   ```

   ```text
   @GitHub Log a bug for a 500 error in octo-org/octo-repo and assign @USER to it. This happens consistently when I try to log into the site.
   ```

   ```text
   @GitHub In octo-org/octo-repo, create an issue and add relevant code snippets to improve the API response format.
   ```

   > \[!NOTE] You can only use Copilot to create issues in repositories where you already have permission to create issues. This feature doesn't change your access or bypass repository permissions.

2. Click **Review draft** to open the issue draft. Copilot drafts an issue that includes:

   * A suggested title.
   * Details of the required changes.

   Based on your prompt, Copilot can also suggest metadata such as labels, assignees, and issue type.

3. Review the draft, and once the issue looks good, click **Create**.

## Further reading

* [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent) - Learn more about Copilot cloud agent and how it can support you.