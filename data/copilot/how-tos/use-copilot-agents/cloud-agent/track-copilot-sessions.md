# Tracking GitHub Copilot's sessions

You can use the agents panel or page, Visual Studio Code, JetBrains IDEs, Eclipse, the GitHub CLI, Raycast and session logs to track Copilot's progress and understand its approach.

## Introduction

After you give Copilot a task, it works autonomously in the background to complete it. See [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent).

The agents panel, [agents tab](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text), the GitHub CLI, and GitHub Copilot extension for Raycast provide an overview of your agent sessions across repositories. You can use them to kick off new tasks and track Copilot's progress.

You can also track Copilot's sessions in a specific repository from Visual Studio Code.

During or after an agent session, you can inspect the session logs to understand Copilot's approach to your problem.

## Tracking agent sessions from the agents tab

You can see a list of your running and past agent sessions in the agents panel, available from every page on GitHub, or on the dedicated agents tab. Agent sessions appear in your sessions list if you started the session or prompted Copilot to work on another user's session.

To open the [agents tab](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text), click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> to open the agents panel in the navigation bar on any page, then click **View all**.

Each session displays its status. Click on a session to open the session log and overview, where you can monitor the agent's progress, token usage, session count, and session length.

You can start new agent sessions from the tab. See [Asking GitHub Copilot to create a pull request](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-a-pr).

## Tracking agent sessions from the GitHub CLI

> \[!NOTE]
> The `agent-task` command set is only available in v2.80.0 or later of the GitHub CLI. This command set is a public preview and is subject to change.

You can see a list of your running and past agent sessions from the GitHub CLI with the `gh agent-task list` command. The output will show a list of your recent sessions.

To see more information on a specific session, use the `gh agent-task view` command. For example, to view information about the session associated with pull request #123 in the `monalisa/bookstore` repository, run `gh agent-task view --repo monalisa/bookstore 123`.

To view the session logs, add the `--log` option. Optionally, use the `--follow` option to stream live logs as the agent works.

To see all of the available options, run `gh agent-task list --help` or `gh agent-task view --help`.

## Tracking agent sessions from Raycast

[Raycast](https://www.raycast.com/) is an extensible launcher for Windows and macOS. With the GitHub Copilot extension for Raycast, you can start and track Copilot cloud agent tasks and watch session logs live wherever you are on your computer.

1. Install Raycast from the [Raycast website](https://www.raycast.com).
2. Install the GitHub Copilot extension for Raycast by clicking the **Install Extension** button on the [extension's page](https://www.raycast.com/github/github-copilot).
3. Open Raycast, search for "Copilot," find the **View Tasks** command, then press <kbd>Enter</kbd>.
4. Click **Sign in with GitHub**, then complete the authentication flow. Raycast will re-open.
5. You'll see a list of your tasks. Select a task, then use the following keyboard shortcuts:
   * To watch the session logs live, press <kbd>Enter</kbd>. The logs update in real time, so you can monitor Copilot's progress without leaving Raycast.
   * To open the session logs in the browser, press <kbd>Command</kbd>+<kbd>Enter</kbd> (macOS) or <kbd>Ctrl</kbd>+<kbd>Enter</kbd> (Windows).
   * To open the linked pull request, press <kbd>Command</kbd>+<kbd>P</kbd> (macOS) or <kbd>Ctrl</kbd>+<kbd>P</kbd> (Windows).

> \[!NOTE]
> If you are unable to see some tasks in Raycast, the organization that owns the repository may have enabled OAuth app access restrictions. To learn how to request approval for the "GitHub Copilot for Raycast" OAuth app, see [Requesting organization approval for OAuth apps](/en/account-and-profile/how-tos/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/requesting-organization-approval-for-oauth-apps).

You can also start new agent sessions from Raycast. See [Asking GitHub Copilot to create a pull request](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-a-pr#asking-copilot-to-create-a-pull-request-from-raycast).

## Tracking sessions from Visual Studio Code

You can see a list of your running and past agent sessions for a specific repository in Visual Studio Code with the [GitHub Pull Requests extension](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github).

Once you've installed the extension, you can see Copilot's sessions by clicking the **GitHub** button in the sidebar.

For each session listed, you can see its status at a glance, or click on it to navigate to the pull request within Visual Studio Code.

To view the session logs, click on the pull request in the list, then click **View Session**.

You can also start new agent sessions from Visual Studio Code. See [Asking GitHub Copilot to create a pull request](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-a-pr#asking-copilot-to-create-a-pull-request-from-copilot-chat-in-visual-studio-code).

To directly open agent sessions in VS Code, click the **Open in VS Code** option on the agents tab.

> \[!NOTE]
> Opening a session in VS Code is currently only available in VS Code Insiders.

## Tracking sessions from JetBrains IDEs

> \[!NOTE]
> Copilot cloud agent in JetBrains IDEs is in public preview, and subject to change.

You can see a list of your running and past agent sessions for a project in JetBrains IDEs with the GitHub Copilot Chat extension. See [Installing the GitHub Copilot extension in your environment](/en/copilot/how-tos/set-up/install-copilot-extension?tool=jetbrains).

You can see all of Copilot's sessions by clicking the **GitHub Cloud Agent Jobs** button in the sidebar or by clicking the **Open Job List** button after delegating a task to Copilot from GitHub Copilot Chat.

For each session listed, you can see its status at a glance. Click **Open in Browser** to open the pull request in your browser, or right-click on a running job then click **Cancel Job** to cancel.

Copilot will also notify you when an agent job has started and finished.

## Tracking sessions from Eclipse

> \[!NOTE]
> Copilot cloud agent in Eclipse is in public preview, and subject to change.

You can see a list of your running and past agent sessions for a project in Eclipse with the GitHub Copilot Chat extension. See [Installing the GitHub Copilot extension in your environment](/en/copilot/how-tos/set-up/install-copilot-extension?tool=eclipse).

You can see all of Copilot's sessions by clicking **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg>** at the top right of the chat window, or by clicking the **Open Job List** button after delegating a task to Copilot from GitHub Copilot Chat.

For each session listed, you can see its status at a glance. Click **Open in Browser** to open the pull request in your browser, or right-click on a running job then click **Cancel Job** to cancel.

Copilot will also notify you when an agent job has started and finished.

## Tracking sessions from GitHub Mobile

You can see a list of your running and past pull requests generated by agents in GitHub Mobile.

1. In the "Agents" section on the GitHub Mobile Home page, tap **Agent Tasks**.

   A list of the currently open pull requests, that you asked Copilot to generate, is displayed.

2. Use the buttons at the top of the list to filter the list of pull requests.

   For example, to show only merged tasks, tap **Open** and then, in the dropdown, tap **Merged**.

   <img width=350rem src="/assets/images/help/copilot/cloud-agent/mobile-status-dropdown.png" alt="Screenshot of the status dropdown list with a check mark against 'Open'." />

## Tracing commits to session logs

Commits from Copilot cloud agent have the following characteristics:

* Every commit is authored by Copilot, with the human who started the task marked as the co-author.
* Each commit message includes a link to the session logs for that commit, so you can understand why Copilot made a change during code review or trace it later for auditing purposes.
* Commits from Copilot cloud agent are signed and appear as "Verified" on GitHub.

## Using the session logs to understand Copilot's approach

You can dive into Copilot's session logs in GitHub, Visual Studio Code, or Raycast to understand how it approached your task.

In the session logs, you can see Copilot's internal monologue and the tools it used to understand your repository, make changes and validate its work.

> \[!NOTE]
> Copilot has its own development environment, including the ability to run automated tests and linters, to validate its changes before it pushes.

## Steering a Copilot session from the agents tab

You can steer Copilot while it is working to complete a task. Reasons you might want to steer a session include:

* Copilot appears to be going in a wrong direction, and you want to give it more clarity.
* You made a mistake in your description of the required work, and you've decided to start over.

Follow these steps to steer Copilot:

1. Open the [agents tab](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text).
2. In the **Agent sessions** list, select the task that you want to provide further input for.
3. In the prompt box, prompt Copilot as it is working on a task.

For example, `Use our existing ErrorHandler utility class instead of writing custom try-catch blocks for each endpoint.`

Copilot will start implementing your input after it has finished its current tool call.

> \[!NOTE]
> Steering uses **one premium request** per message.

## Stopping a Copilot session

You can stop Copilot from continuing to work on a task by clicking **Stop session** in the session log viewer.

![Screenshot of the log viewer with the 'Stop session' button highlighted.](/assets/images/help/copilot/cloud-agent/log-stop-session.png)

Reasons you might want to stop a session include:

* You made a mistake in your description of the required work, and you've decided to start over.
* You've realized that the change you asked for doesn't need to be made, so you want to stop Copilot from doing any more work on it.

## Further reading

* [Best practices for using GitHub Copilot to work on tasks](/en/copilot/tutorials/cloud-agent/get-the-best-results)
* [Troubleshooting GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/troubleshoot-cloud-agent)