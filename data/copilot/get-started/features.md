# GitHub Copilot features

GitHub Copilot offers a suite of features. Copilot also offers a suite of features for administrators.

## GitHub Copilot features

### Copilot Chat

A chat interface that lets you ask coding-related questions. GitHub Copilot Chat is available on the GitHub website, in GitHub Mobile, in supported IDEs *(Visual Studio Code, Visual Studio, JetBrains IDEs, Eclipse IDE, and Xcode)*, and in Windows Terminal. Users can also use skills with Copilot Chat. See [Asking GitHub Copilot questions in GitHub](/en/copilot/using-github-copilot/asking-github-copilot-questions-in-github) and [Asking GitHub Copilot questions in your IDE](/en/copilot/using-github-copilot/asking-github-copilot-questions-in-your-ide).

### Copilot cloud agent (formerly Copilot coding agent)

An autonomous AI agent that can research a repository, create an implementation plan, and make code changes on a branch. You can review the diff, iterate, and create a pull request when you're ready. You can also assign a GitHub issue to Copilot or ask it to open a pull request directly to complete a task. See [GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent).

### Third-party coding agents (public preview)

You can use third-party coding agents alongside Copilot cloud agent. See [About third-party agents](/en/copilot/concepts/agents/about-third-party-agents).

### Copilot CLI

A command line interface that lets you use Copilot from within the terminal. You can get answers to questions, or you can ask Copilot to make changes to your local files. You can also use Copilot CLI to interact with GitHub.com—for example, listing your open pull requests, or asking Copilot to create an issue. See [About GitHub Copilot CLI](/en/copilot/concepts/agents/about-copilot-cli).

### Copilot code review

AI-generated code review suggestions to help you write better code. See [Using GitHub Copilot code review](/en/copilot/using-github-copilot/code-review/using-copilot-code-review).

Several tools in Copilot code review are in public preview and subject to change. See [About GitHub Copilot code review](/en/copilot/concepts/agents/code-review).

### Copilot pull request summaries

AI-generated summaries of the changes that were made in a pull request, which files they impact, and what a reviewer should focus on when they conduct their review. See [Creating a pull request summary with GitHub Copilot](/en/copilot/using-github-copilot/creating-a-pull-request-summary-with-github-copilot).

### Inline suggestions

Autocomplete-style suggestions from Copilot in supported IDEs (Visual Studio Code, Visual Studio, JetBrains IDEs, Azure Data Studio, Xcode, Vim/Neovim, and Eclipse). See [Getting code suggestions in your IDE with GitHub Copilot](/en/copilot/using-github-copilot/getting-code-suggestions-in-your-ide-with-github-copilot).

If you use VS Code, Xcode, and Eclipse, you can also use next edit suggestions, which will predict the location of the next edit you are likely to make and suggest a completion for it.

### Copilot Edits

Copilot Edits is available in Visual Studio Code, Visual Studio, and JetBrains IDEs. Use Copilot Edits to make changes across multiple files directly from a single Copilot Chat prompt. Copilot Edits has the following modes:

#### Edit mode

Edit mode is only available in Visual Studio Code and JetBrains IDEs.

Use edit mode when you want more granular control over the edits that Copilot proposes. In edit mode, you choose which files Copilot can make changes to, provide context to Copilot with each iteration, and decide whether or not to accept the suggested edits after each turn.

Edit mode is best suited to use cases where:

* You want to make a quick, specific update to a defined set of files.
* You want full control over the number of LLM requests Copilot uses.

#### Agent mode

Use agent mode when you have a specific task in mind and want to enable Copilot to autonomously edit your code. In agent mode, Copilot determines which files to make changes to, offers code changes and terminal commands to complete the task, and iterates to remediate issues until the original task is complete.

Agent mode is best suited to use cases where:

* Your task is complex, and involves multiple steps, iterations, and error handling.
* You want Copilot to determine the necessary steps to take to complete the task.
* The task requires Copilot to integrate with external applications, such as an MCP server.

### Copilot custom instructions

Enhance Copilot Chat responses by providing contextual details on your preferences, tools, and requirements. See [About customizing GitHub Copilot responses](/en/copilot/concepts/about-customizing-github-copilot-chat-responses).

### Copilot Memory (public preview)

Copilot can deduce and store useful information about a repository, which Copilot cloud agent and Copilot code review can use to improve the quality of their output when working in that repository. For more information, see [About agentic memory for GitHub Copilot](/en/copilot/concepts/agents/copilot-memory).

### Copilot in GitHub Desktop

Automatically generate commit messages and descriptions with Copilot in GitHub Desktop based on the changes you make to your project.

### Copilot Spaces

Organize and centralize relevant content—like code, docs, specs, and more—into Spaces that ground Copilot’s responses in the right context for a specific task. See [About GitHub Copilot Spaces](/en/copilot/using-github-copilot/copilot-spaces/about-organizing-and-sharing-context-with-copilot-spaces).

### GitHub Spark (public preview)

Build and deploy full-stack applications using natural-language prompts that seamlessly integrate with the GitHub platform for advanced development. See [Building and deploying AI-powered apps with GitHub Spark](/en/copilot/tutorials/spark/build-apps-with-spark).

## GitHub Copilot features for administrators

The following features are available to organization and enterprise owners with a Copilot Business or Copilot Enterprise plan.

### Policy management

Manage policies for Copilot in your organization or enterprise. See [Managing policies and features for GitHub Copilot in your organization](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/setting-policies-for-copilot-in-your-organization/managing-policies-for-copilot-in-your-organization) and [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-policies-and-features-for-copilot-in-your-enterprise).

### Access management

Enterprise owners can specify which organizations in the enterprise can use Copilot, and organization owners can specify which organization members can use Copilot. See [Managing access to GitHub Copilot in your organization](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-access-to-github-copilot-in-your-organization) and [Managing access to Copilot in your enterprise](/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-access-to-copilot-in-your-enterprise).

### Usage data

Review Copilot usage data within your organization or enterprise to inform how to manage access and drive adoption of Copilot. See [Reviewing user activity data for GitHub Copilot in your organization](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/reviewing-activity-related-to-github-copilot-in-your-organization/reviewing-user-activity-data-for-copilot-in-your-organization) and [Viewing Copilot license usage in your enterprise](/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-access-to-copilot-in-your-enterprise/viewing-copilot-license-usage-in-your-enterprise).

### Audit logs

Review audit logs for Copilot in your organization to understand what actions have been taken and by which users. See [Reviewing audit logs for GitHub Copilot](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/reviewing-activity-related-to-github-copilot-in-your-organization/reviewing-audit-logs-for-copilot-business).

### Exclude files

Configure Copilot to ignore certain files. This can be useful if you have files that you don't want to be available to Copilot. See [Excluding content from GitHub Copilot](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/setting-policies-for-copilot-in-your-organization/excluding-content-from-github-copilot).

## Next steps

* To learn more about the plans available for GitHub Copilot, see [Plans for GitHub Copilot](/en/copilot/about-github-copilot/subscription-plans-for-github-copilot).
* To start using Copilot, see [Setting up GitHub Copilot](/en/copilot/setting-up-github-copilot).