# Reviewing a pull request created by GitHub Copilot

After Copilot creates a pull request, you should review it. You can mention @copilot to ask Copilot to make changes, or push changes yourself.

> \[!NOTE]
> For an introduction to Copilot cloud agent, see [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent).

## Reviewing Copilot's changes

After Copilot has finished working on a coding task, and has requested a pull request review from you, you should review Copilot's work thoroughly before merging the pull request.

> \[!IMPORTANT]
> If you have rules or branch protections that require pull request approvals, and you ask Copilot to create a pull request, you can approve the pull request, but **your approval won't count** toward the required number of approvals. Someone else must approve the pull request for it to be merged.

You can ask Copilot to make changes by mentioning `@copilot` in pull request comments. By default, Copilot pushes commits directly to the pull request's branch. If you prefer, you can ask Copilot to create a separate pull request instead by using natural language in your comment. You can also check out Copilot's branch and make changes yourself.

Optionally, when submitting a pull request comment (not a review or review comment) through the GitHub web interface, you can select a model using the model picker. By default, Copilot will use the model originally used to create the pull request.

> \[!TIP]
> We recommend you batch your review comments instead of submitting them individually.

Copilot only responds to comments from people who have write access to the repository.

When Copilot starts a new agent session in response to your comment, an eyes emoji (👀) is added as a reaction to the comment, and a "Copilot has started work" event is added to the pull request timeline.

![Screenshot of a pull request timeline with a review comment with the eyes reaction and a "Copilot started work" timeline event.](/assets/images/help/copilot/cloud-agent/comment-to-agent-on-pr.png)

When Copilot starts a new session on the same pull request, it remembers context from the previous session, allowing it to work faster and more reliably.

> \[!NOTE]
> If the pull request was created by a custom agent, when you mention `@copilot` in pull request comments, the same custom agent will be used to make further changes. This ensures consistency in the agent's specialized configuration throughout the pull request lifecycle. See [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents).

For more information, see the section "Use comments to iterate on a pull request" in [Best practices for using GitHub Copilot to work on tasks](/en/copilot/tutorials/cloud-agent/get-the-best-results#using-comments-to-iterate-on-a-pull-request).

## Managing GitHub Actions workflow runs

By default, GitHub Actions workflows will not run automatically when Copilot pushes changes to a pull request.

GitHub Actions workflows can be privileged and have access to sensitive secrets. Inspect the proposed changes in the pull request and ensure that you are comfortable running your workflows on the pull request branch. You should be especially alert to any proposed changes in the `.github/workflows/` directory that affect workflow files.

To allow GitHub Actions workflows to run, click the **Approve and run workflows** button in the pull request's merge box.

![Screenshot of the merge box on a pull request from Copilot with the "Approve and run workflows" button.](/assets/images/help/copilot/cloud-agent/approve-and-run-workflows.png)

Optionally, you can configure Copilot cloud agent to allow GitHub Actions workflows to run without human intervention. For more information, see [Configuring settings for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/configuring-agent-settings).

## Giving feedback on Copilot's work

You can provide feedback on Copilot's work using the feedback buttons on  Copilot's pull requests and comments. We use your feedback to improve the product and the quality of Copilot's solutions.

1. On a pull request or comment from Copilot, click the thumbs up (:+1:) or thumbs down (:-1:) button.
2. If you click the thumbs down button, you're asked to provide additional information. You can, optionally, pick the reason for your negative feedback and leave a comment before clicking **Submit feedback**.

## Further reading

* [Best practices for using GitHub Copilot to work on tasks](/en/copilot/tutorials/cloud-agent/get-the-best-results)
* [Tracking GitHub Copilot's sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/track-copilot-sessions)
* [Troubleshooting GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/troubleshoot-cloud-agent)