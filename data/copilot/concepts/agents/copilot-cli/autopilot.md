# Allowing GitHub Copilot CLI to work autonomously

The CLI's autopilot mode lets Copilot CLI work autonomously on a task, carrying out multiple steps until the task is complete.

## Overview

Typically, when you use Copilot CLI interactively, you submit a prompt and then wait for Copilot CLI to respond before giving the next instruction. This back-and-forth interaction continues until the task is done.

Autopilot mode allows Copilot CLI to work through a task without waiting for your input after each step. Once you give the initial instruction, Copilot CLI works through each step autonomously until it determines the task is complete.

The difference between the CLI's standard interactive mode and autopilot mode is like the difference between working on a task with a coworker, where they do most of the work, but check back with you periodically, versus handing the task over to your colleague, saying "Here's what I need—let me know when you're finished."

In autopilot mode, Copilot keeps on going until one of these happens:

* The agent determines that the task is complete.
* A problem occurs that prevents further progress.
* You press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the agent from continuing.
* The maximum continuation limit is reached (if set).

To switch into autopilot mode during an interactive session, press <kbd>Shift</kbd>+<kbd>Tab</kbd> and cycle through the available modes until you reach autopilot mode, then enter your prompt. Use the same keypress to switch from autopilot mode back to the standard interactive mode.

## Benefits of autopilot mode

* **Hands-off automation:** Copilot completes tasks without needing your input after the initial instruction.
* **Efficiency:** Ideal for well-defined tasks like writing tests, refactoring files, or fixing CI failures. Autopilot is particularly suited for large tasks that require long-running, multi-step sessions.
* **Batch operations:** Useful for scripting and CI workflows where you want Copilot to run to completion.
* **Safety:** Autopilot mode allows Copilot to take multiple self-directed steps to finish your task. `--max-autopilot-continues` limits how many steps it can take before stopping, to avoid infinite loops. Also, in autopilot mode, Copilot cannot carry out any actions that require permission unless you explicitly grant it full permissions.

## Things to consider

* **Task suitability:** Autopilot mode is best for well-defined tasks. It is not ideal for open-ended exploration, feature development without a clear goal, or tasks where you want to guide the ongoing work.

  Copilot will do its best to complete any task, but it may struggle with vague or ambiguous instructions or tasks that require nuanced judgment calls along the way. This may result in a set of code changes that aren't what you expected and can't be used without remedial work.

* **Trust:** You need to trust Copilot to make reasonable decisions. Autopilot mode works best when you grant it approval for all permissions. This is equivalent to running Copilot CLI with the `--allow-all` option. You should be aware that this gives the CLI permission to make any changes it deems necessary to complete the task, including altering and deleting files.

* **Cost:** Autopilot mode uses premium requests in the same way that these are used when you are working in the standard interactive interface. In the standard mode, one premium request is used when you submit your initial prompt, and then an additional premium request is used each time you reply to a question in the CLI and the agent uses your response to interact with the AI model. The same applies in autopilot mode, except that you are not involved in initiating the next step, so the use of additional premium requests happens without your direct involvement.

  The billable premium request usage is determined using a multiplier. The multiplier varies depending on which model you use. Use the `/model` slash command to see the currently selected model and its multiplier, and change the model if required. For more information, see [Requests in GitHub Copilot](/en/copilot/concepts/billing/copilot-requests) and [About billing for individual GitHub Copilot plans](/en/copilot/concepts/billing/billing-for-individuals#about-premium-requests).

  Each time the agent continues autonomously it will display a message in the CLI telling you how many premium requests have been used by that continuation step—taking account of the model multiplier—for example: `Continuing autonomously (3 premium requests)`.

## Permissions

When entering autopilot mode, if you have not already granted Copilot all permissions, a message is displayed prompting you to choose between three options:

```text
1. Enable all permissions (recommended)
2. Continue with limited permissions
3. Cancel (Esc)
```

You will get the best results from autopilot mode if you enable all permissions. If you choose to continue with limited permissions, Copilot will automatically deny any tool requests that require approval, which may prevent it from completing certain tasks. You can change your mind later and grant full permissions, during an autopilot session, by using the `/allow-all` command (or its alias `/yolo`).

## Comparing autopilot mode, `--allow-all`, and `--no-ask-user`

`--allow-all`, and its alias `--yolo`, are permissions-related options that you can pass to the `copilot` command when you start an interactive session. For a full list of available options, see [GitHub Copilot CLI command reference](/en/copilot/reference/copilot-cli-reference/cli-command-reference#command-line-options).

The `--allow-all` and `--yolo` options allow the CLI agent to use all tools, paths, and URLs. You can also set these permissions during an interactive session, by using the `/allow-all` or `/yolo` slash commands.

> \[!NOTE]
> Entering `/allow-all` and `/yolo` enables permissions for the current session. Entering these slash commands again does not disable permissions—in other words, these commands don't toggle permissions on and off.

With `--allow-all`, you are still in the normal interactive flow. Copilot will still stop and ask you what you want it to do when it reaches a decision point. However, when Copilot CLI needs to do something that would normally require approval, such as using tools, paths, or URLs, it will go ahead without asking for permission.

The `--no-ask-user` option suppresses clarifying questions that Copilot would normally ask. Instead the agent must make decisions on its own, rather than asking for your input. This provides a degree of autonomy. However, unlike autopilot mode, `--no-ask-user` does not allow the agent to continue working on a task through successive steps where interaction with the AI model is required. With this option, the CLI won't use additional premium requests, after your initial prompt, without your involvement.

## Typical workflow for using autopilot mode

Autopilot mode is ideal for implementing a large, detailed plan of work. Often you will find it useful to switch to autopilot mode after working with Copilot in plan mode to create an implementation plan. For more information about plan mode, see [Best practices for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/cli-best-practices#2-plan-before-you-code).

For example:

* Start an interactive Copilot CLI session.

  Optionally, you can include the `--allow-all` option to grant permissions, and the `--max-autopilot-continues` option to set a maximum continuation limit for autopilot mode during the session. For example, you could start the session with `copilot --allow-all --max-autopilot-continues 10` to give the agent permission to use all tools, paths, and URLs, and set a maximum continuation limit for autopilot to 10.

* When the interactive session starts, if you're prompted to trust the files in the current folder, accept this option.

* Press <kbd>Shift</kbd>+<kbd>Tab</kbd> to switch to plan mode, enter a prompt describing what you want to achieve, then work with Copilot to create a detailed plan.

* Once you have a plan that you are happy with, use the option that the CLI presents to "Accept plan and build on autopilot".

* If you're prompted about permissions, choose the option to enable all permissions.

* Leave Copilot to implement the plan. You can check in on its progress periodically.

## Using autopilot mode programmatically

You can use autopilot mode when you run Copilot CLI programmatically, for example when you pass Copilot a prompt on the command line, or when you use the CLI as part of a script or CI workflow. Doing so allows you to automate tasks end-to-end without needing to interact with the CLI after the initial command.

Use the `--allow-all` (or `--yolo`) option to grant Copilot permission to use all tools, paths, and URLs. You can include the `--max-autopilot-continues` option to set a maximum continuation limit to prevent runaway loops. This is especially important in programmatic contexts where you won't be there to intervene if something goes wrong.

Example usage:

```shell
copilot --autopilot --yolo --max-autopilot-continues 10 -p "YOUR PROMPT HERE"
```

## Summary

Use autopilot mode when you want Copilot to take over a task and work to completion without your involvement. It's best for clear, well-defined tasks where you trust Copilot to make reasonable decisions.

## Further reading

* [Using GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/use-copilot-cli#get-copilot-to-work-autonomously)
* [Running tasks in parallel with the \`/fleet\` command](/en/copilot/concepts/agents/copilot-cli/fleet)
* [GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli)