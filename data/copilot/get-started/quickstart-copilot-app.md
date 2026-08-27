# Getting started with the GitHub Copilot app

Sign in to the GitHub Copilot app, connect a repository or local folder, and create your first agent session to make code changes.

For a conceptual overview of the GitHub Copilot app, see [About the GitHub Copilot app](/en/copilot/concepts/agents/github-copilot-app).

In this quickstart, you will:

1. Install and sign in to the GitHub Copilot app.
2. Connect a repository or local folder.
3. Make code changes in an agent session.

## Prerequisites

* A GitHub account.
* A Copilot plan, or you can configure your own model provider.
  * If you use your own model provider, you will need provider credentials such as an API key. For setup steps, see [Using your own LLM models in the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/use-byok-models).
* [Git](https://github.com/git-guides/install-git) installed on your computer.

> \[!NOTE]
> For Copilot Business and Copilot Enterprise users, the GitHub Copilot app policy must remain enabled. This policy is enabled by default and is separate from the Copilot CLI policy. See [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies) or [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies).

## Installing the GitHub Copilot app

1. Visit the [download page for GitHub Copilot app](https://github.com/features/ai/github-app).
2. Download the app for your platform.

## Opening the GitHub Copilot app for the first time

1. Open the GitHub Copilot app.
2. Click **Sign in to GitHub** and follow the prompts to authenticate. If you use GitHub Enterprise Server, choose **Use GitHub Enterprise** and enter your server address when prompted.
3. If you do not have a Copilot plan, choose whether to sign up for a plan or continue with your own model provider.
   * If you choose to use your own model provider, select a provider, enter any required credentials, then click **Save and continue**.
4. When prompted, select one or more repositories based on your recent GitHub activity. You can also add a local folder or repository, or skip this step and add projects later.
5. Choose a theme, then complete onboarding to open the app.

## Connecting a repository or folder

To work on code, you need at least one project connected to the app. A project can be a folder already on your machine, including a repository you've already cloned locally, or a repository you clone from GitHub or another remote Git host such as Azure DevOps. Connecting a project unlocks the core app workflow: reading code, making edits, and opening pull requests from agent sessions. If you skipped project setup during onboarding, or want to add more projects later:

1. Click the **+** button in the sidebar next to "Sessions".
2. Under **Add project from**, choose one of the following:

* **Local folder or repository** — Select a folder already on your machine, including one that contains a repository you've already cloned locally.
* **GitHub repository** — Browse and clone a repository from GitHub.
* **Repository URL** — Clone from a Git URL for repositories hosted outside GitHub (for example, on Azure DevOps) or for private repositories without app access.

## Making your first code changes

1. Click **+** next to **Sessions**, then choose a connected folder or repository under **Start session in**.

2. Select a session mode from the dropdown below the prompt field—for example, **Interactive** to work collaboratively with the agent.

3. In the prompt box, paste this prompt:

   ```copilot copy
   Suggest a small low-risk code change in this repository, implement it, and explain the diff.
   ```

4. Respond to any requests for input from the agent. After the agent makes changes, click **Changes** above the prompt box to view the diff.

5. Continue iterating in the same session until you are happy with the result.

6. If you want to keep the change, click **Create PR** to open a pull request for review.

7. If you create a pull request, click **PR** above the prompt box to view it directly in the app.

**Optional:** If you already have tasks you want to complete in your repository, you can start a session from an issue in **[My work](https://github.com/copilot/app/launch?open=ghapp%3A%2F%2Fmywork)**. For more information, see [Managing issues and pull requests with the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/managing-issues-and-pull-requests).

## Orienting yourself

The sidebar gives you access to the main areas of the app:

* **[My work](https://github.com/copilot/app/launch?open=ghapp%3A%2F%2Fmywork)** — Browse and filter issues and pull requests from your repositories, check CI status, and leave reviews.
* **[Automations](https://github.com/copilot/app/launch?open=ghapp%3A%2F%2Fautomations)** — Saved agent tasks that run on a schedule or on demand.
* **Customize** — Discover and manage plugins, skills, MCP servers, and canvases.
* **Search** — Search across your repositories directly from the app.
* **Sessions** — Active agent sessions, grouped by project.
* **Chats** — General conversations that do not require a dedicated branch or workspace.

## Next steps

Find out more about using the GitHub Copilot app:

* [Working with agent sessions in the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/agent-sessions)
* [Working with canvas extensions in the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/working-with-canvas-extensions)
* [Managing issues and pull requests with the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/managing-issues-and-pull-requests)
* [Using automations in the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/using-automations)
* [Slash commands for the GitHub Copilot app](/en/copilot/reference/github-copilot-app-reference/slash-commands)
* [Built-in skills for the GitHub Copilot app](/en/copilot/reference/github-copilot-app-reference/built-in-skills)