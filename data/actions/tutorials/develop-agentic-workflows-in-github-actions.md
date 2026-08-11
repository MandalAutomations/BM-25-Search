# Develop agentic workflows in GitHub Actions

Use GitHub Agentic Workflows to turn Markdown instructions into automations powered by third-party coding agents.

> \[!NOTE]
> GitHub Agentic Workflows are in public preview and subject to change.

## Introduction

GitHub Agentic Workflows let you define repository automations in Markdown and choose the AI coding agent that runs them. The `gh aw` extension compiles each agentic workflow into a GitHub Actions workflow.

The entire workflow lifecycle—authoring, debugging, and optimization—is itself agentic. You describe what you want in natural language and a coding agent creates, refines, and troubleshoots the workflow for you.

This tutorial uses a coding agent to create an automated pull request reviewer that checks whether changes are adequately tested.

## Prerequisites

Before you begin, make sure you have:

* A repository where GitHub Actions is enabled and you have write access
* GitHub CLI version 2.0.0 or later installed and authenticated
* Access to a supported coding agent, such as Claude Code, OpenAI Codex, or Google Gemini CLI, or Copilot CLI, and its required credential

To authenticate GitHub CLI, run:

```shell
gh auth login --scopes repo,workflow
```

## Installing the `gh aw` extension

Install the GitHub Agentic Workflows extension for GitHub CLI:

```shell
gh extension install github/gh-aw
```

## Choosing an agent and configuring authentication

Choose the agent CLI that best fits your workflow. Claude Code, OpenAI Codex, or Google Gemini CLI, and Copilot CLI can all run GitHub Agentic Workflows.

This article walks through a simple setup that adds the agent's credential as a repository secret. If you use Claude Code, OpenAI Codex, or Google Gemini CLI, store the agent's API key as a repository secret.

| Agent CLI             | `engine` value | Repository secret                                                                                                                                                                                        |
| --------------------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Claude Code           | `claude`       | `ANTHROPIC_API_KEY` containing an Anthropic API key                                                                                                                                                      |
| OpenAI Codex          | `codex`        | `OPENAI_API_KEY` containing an OpenAI API key                                                                                                                                                            |
| Google Gemini CLI     | `gemini`       | `GEMINI_API_KEY` containing a Google AI Studio API key                                                                                                                                                   |
| Copilot CLI (default) | `copilot`      | No secret needed for organization repositories (see below). For personal repositories, `COPILOT_GITHUB_TOKEN` containing a fine-grained personal access token with **Copilot Requests** set to **Read**. |

Other engines such as Pi (experimental) are also supported. For the full list, see the [GitHub Agentic Workflows authentication reference](https://github.github.com/gh-aw/reference/auth/).

### Organization billing for GitHub Copilot

If you use GitHub Copilot in an organization-owned repository, you can use GitHub Actions' built-in `GITHUB_TOKEN` instead of a personal access token. Add `copilot-requests: write` to your workflow frontmatter `permissions` and no separate secret is required. For setup steps, see [Creating GitHub Agentic Workflows](/en/copilot/how-tos/github-agentic-workflows/creating-github-agentic-workflows#using-the-built-in-github_token).

### Storing a secret in the GitHub UI

To add a secret for Claude Code, OpenAI Codex, or Google Gemini CLI, or GitHub Copilot personal repositories:

1. On GitHub, navigate to your repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**.
3. In the sidebar, click **Secrets and variables**, then click **Actions**.
4. Click **New repository secret**.
5. In the **Name** field, enter the secret name from the table above.
6. In the **Secret** field, enter the value.
7. Click **Add secret**.

## Creating the workflow

Use a coding agent to create the workflow from a natural language description.

1. From your repository root, initialize the repository for agentic authoring. This adds skills and instructions that help the coding agent create and edit workflows:

   ```shell
   gh aw init
   ```

2. Start a coding agent session in the context of your repository—for example, using Claude Code, OpenAI Codex, or Google Gemini CLI, Copilot CLI, or VS Code agent mode.

3. Use the `agentic-workflows` skill and describe the workflow you want:

   ```copilot copy
   /agentic-workflows create a pr reviewer that ensure the changes are tested.
   ```

   The agent creates a workflow Markdown file in `.github/workflows/`, compiles the corresponding `.lock.yml` GitHub Actions workflow file, and asks you to review and commit both files.

4. Review the generated workflow, then ask the agent to commit and push the files.

> \[!TIP]
> You can use the same agentic approach to update and improve the workflow after it runs. Ask the agent to refine the review criteria, add more checks, or debug a failed run—all in natural language. If you edit the workflow frontmatter later, run `gh aw compile` before committing your changes.

## Running the workflow

The generated workflow triggers automatically on pull requests, so it runs the next time you open or update a pull request in your repository.

1. Open a pull request in your repository.
2. On GitHub, navigate to your repository and click the **Actions** tab.
3. In the left sidebar, select the workflow that the agent created.
4. Once the run completes, the workflow leaves a pull request review noting whether the changes include enough tests.

## Next steps

* To create a workflow that produces a weekly issue activity report, see [Creating GitHub Agentic Workflows](/en/copilot/how-tos/github-agentic-workflows/creating-github-agentic-workflows).
* For advanced engine configuration, safe outputs, and more workflow examples, see the [GitHub Agentic Workflows documentation site](https://github.github.com/gh-aw/).