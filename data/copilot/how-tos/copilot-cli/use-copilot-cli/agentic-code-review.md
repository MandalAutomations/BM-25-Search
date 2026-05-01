# Requesting a code review with GitHub Copilot CLI

Use Copilot CLI to review your code changes directly from the terminal.

## About agentic code review

You can use the `/review` slash command to have Copilot analyze code changes without leaving the CLI. This lets you get quick feedback on your changes prior to committing.

1. Type `/review` and optionally specify a prompt, path, or file pattern to narrow the review scope, then press <kbd>Enter</kbd>.
2. If Copilot proposes running a command (for example, to inspect a diff or verify a file), review the command, then use the arrow keys to choose an option and press <kbd>Enter</kbd>.
   * Select **Yes** to run the command.
   * Select **No** to skip the command and tell Copilot what to do differently.
3. Read the feedback that Copilot provides about your changes and apply any suggested improvements in your code editor.

## Further reading

* [Automating tasks with Copilot CLI and GitHub Actions](/en/copilot/how-tos/copilot-cli/automate-with-actions)
* [Adding custom instructions for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/add-custom-instructions)