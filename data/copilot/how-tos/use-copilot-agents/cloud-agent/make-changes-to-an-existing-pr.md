# Asking GitHub Copilot to make changes to an existing pull request

You can ask Copilot to make changes to an existing pull request by mentioning @copilot.

> \[!NOTE]
> For an overview of Copilot cloud agent, see [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent).

## Introduction

You can ask Copilot to make changes to an existing pull request by mentioning `@copilot` in a comment.

By default, Copilot pushes commits directly to the pull request's branch. Once it has finished work on the changes you requested, it requests your review.

If you prefer Copilot to create a separate pull request instead, you can ask for this using natural language in your comment—for example, "open a PR to fix the tests."

## Resolving merge conflicts

You can ask Copilot to resolve merge conflicts on a pull request in two ways:

* **Using the "Fix with Copilot" button**: If a pull request has merge conflicts, click the **Fix with Copilot** button that appears in the merge box. This button is available if you have access to Copilot cloud agent and it is enabled for the repository.
* **Using an @copilot mention**: Mention `@copilot` in a comment on the pull request and ask it to fix the conflicts using natural language, such as "@copilot resolve the merge conflicts on this PR."

Copilot will analyze the conflicting changes, resolve the conflicts, and ensure the build, tests, and linter still pass. Once it has finished, Copilot will request your review so you can verify the conflict resolution before merging.

## Asking Copilot to make changes

1. Navigate to the pull request that you want Copilot to make changes to.
2. Write a comment or review mentioning Copilot with `@copilot`.
3. Optionally, when leaving a pull request comment (not a review or review comment) through the GitHub web interface, select a model using the model picker.
4. Submit your comment or review.

If you prefer not to use this default behavior, you can ask Copilot to create a new branch and a new pull request targeting your branch instead. Once the agent finishes work, it will request a review from you.

## Monitoring progress

You can view your current and past Copilot sessions from the agents panel, [agents page](https://github.com/copilot/agents), Visual Studio Code, and more. See [Tracking GitHub Copilot's sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/track-copilot-sessions).

## Further reading

* [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent)
* [Best practices for using GitHub Copilot to work on tasks](/en/copilot/tutorials/cloud-agent/get-the-best-results)
* [Troubleshooting GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/troubleshoot-cloud-agent#copilot-cant-create-a-pull-request-from-copilot-chat)