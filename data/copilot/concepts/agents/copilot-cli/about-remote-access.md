# About remote access to GitHub Copilot CLI sessions

Access a running Copilot CLI session from GitHub.com or GitHub Mobile to monitor and steer the session when you are away from the machine where the session is running.

This article explains the concepts around remote access to Copilot CLI sessions. For instructions on how to enable remote access, see [Steering a GitHub Copilot CLI session from another device](/en/copilot/how-tos/copilot-cli/steer-remotely).

## Introduction

When you start a GitHub Copilot CLI session on your local machine, the session is normally only accessible from the terminal where you started it. However, you can enable remote access to the session from GitHub.com and GitHub Mobile, allowing you to view the progress of a task that Copilot is working on, and respond to prompts for more information, or requests for permissions.

This is useful in scenarios such as:

* **Leaving your workstation**: You started a session on your laptop and were then called away, or you finished work for the day, but you want to continue interacting with Copilot without having to return to the machine.

* **Monitoring a long-running task**: You started a complex task that will take time to complete, but didn't give Copilot full permission to carry out every action. You need to periodically assess and respond to permission requests to allow a task to continue.

  To ensure the stability of the remote access feature there is a 60 MB limit on size of session output that is passed to the remote interface. As a result, very long-running sessions that generate large amounts of output may experience reduced performance in the remote interface. The local terminal session is unaffected.

* **Quick access from a mobile device**: You're working on something else now but you're using GitHub Mobile to provide an at-a-glance view of progress on a task you started in Copilot CLI.

> \[!NOTE]
>
> * Remote access to Copilot CLI sessions is in public preview and subject to change.
> * Mobile access is currently only available in the latest beta release of GitHub Mobile. You can join the test program for GitHub Mobile via [Apple TestFlight for iOS](https://testflight.apple.com/join/NLskzwi5) and [Google Play for Android](https://play.google.com/apps/testing/com.github.android). <!-- markdownlint-disable-line GHD046 -->

## Prerequisites

Remote access requires:

* **Policy enablement**: For users who have a Copilot seat from an organization, remote access access is governed by policies set at the organization and enterprise level. The "Remote Control" policy is off by default but can be enabled by an enterprise or organization owner. See [Administering remote access](#administering-remote-access).
* **A GitHub repository**: The working directory where you started the CLI must contain a Git repository hosted on GitHub.com. If you attempt to enable remote access outside of a GitHub repository, the CLI displays the message: "Remote session disabled: not in a GitHub repository"
* **The machine must be online**: The CLI session must be actively running in a terminal on a machine with an internet connection. If the machine goes to sleep or loses its connection, remote access is unavailable until the machine is back online. See [Reconnection](#reconnection) later in this article.
* **An interactive session**: Remote access is only available for interactive sessions. It is not available when you use the CLI programmatically with the `--prompt` command-line option, for example when you use the CLI in a script.

## Accessing a session remotely

When you enable remote access for a Copilot CLI session, you can go to GitHub.com or GitHub Mobile and find the session in the list of your recent agent sessions. The remote interface is updated in real time, allowing you to monitor ongoing output from the session and respond to prompts and permission requests as they come in.

Both the local terminal and the remote interface are active at the same time. You can enter commands in either interface. Copilot CLI uses the first response it receives to any prompt or permission request.

Your session continues to run on your local machine. The remote interface provides a way to interact with the session, but the CLI itself—and all the tools, shell commands, and file operations it runs—remain on the machine where you started the session.

## What you can do remotely

When connected to a session remotely from GitHub.com or GitHub Mobile, you can:

* **Respond to permission requests**: Approve or deny tool, file path, and URL permission requests.
* **Respond to questions**: Answer when Copilot asks you to supply more information or make a decision.
* **Approve or reject plans**: Respond to plan approval prompts when Copilot is in plan mode.
* **Submit new prompts**: Enter questions or instructions, just as you would in the terminal.
* **Switch modes**: Change the session mode—for example, between interactive and plan mode.
* **End the current operation**: Cancel the agent's current work.

> \[!NOTE]
> Slash commands—such as `/allow-all`—are not currently available from the remote interface.

## Reconnection

If the connection between your local machine and GitHub is temporarily lost—for example, due to a network interruption—you can continue using the session remotely as soon as the connection is restored.

You can use the `/keep-alive` slash command to prevent your machine from going to sleep. See [Preventing your machine from going to sleep](/en/copilot/how-tos/copilot-cli/steer-remotely#preventing-your-machine-from-going-to-sleep).

If you closed a session that had remote access enabled, when you resume the session—either using `copilot --continue` or `copilot --resume=ID`—you must re-enable remote access. For more information, see [Steering a GitHub Copilot CLI session from another device](/en/copilot/how-tos/copilot-cli/steer-remotely#resuming-a-session-with-remote-access).

## Visibility of remote access sessions

Remote access is only available to you—the person who is signed in to GitHub with the same account that started the CLI session. No one else can view or interact with your session remotely.

### Points to note

When you enable remote access:

* Session events are sent from your local machine to GitHub. This includes conversation messages, tool execution events, and permission requests.
* Remote commands are polled by Copilot CLI from GitHub and injected into your local session.
* The CLI itself continues to run locally. All shell commands, file operations, and tool executions happen on your machine—remote access does not grant any direct access to your local machine beyond what the CLI agent can do within the session.

The remote session link (displayed in the CLI when you enable remote access) points to a session-specific URL on GitHub.com. Only authenticated users with the correct account can access this URL.

## Administering remote access

The ability for users enable remote access to their Copilot CLI sessions can be controlled by policies in the enterprise or organization settings. Users who get Copilot from an organization will not be able to use remote access if it has been disabled at the organization or enterprise level.

The "Remote Control" policy is off by default, so it must be enabled by an enterprise or organization owner before users can start monitoring and steering their CLI sessions remotely.

For more information about setting policies for your enterprise or organization, see [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies) and [Administering Copilot CLI for your enterprise](/en/copilot/how-tos/copilot-cli/administer-copilot-cli-for-your-enterprise).