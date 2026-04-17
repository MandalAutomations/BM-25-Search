# Managing context in GitHub Copilot CLI

Understand how Copilot manages conversation context, what happens during long sessions, and how to stay in control of your context window.

## About the context window

When you use GitHub Copilot CLI, every message you send, every response from Copilot, every tool call and its result, and the system instructions that define Copilot's behavior are all held in a **context window**. The context window is the total amount of information that the AI model can consider at one time when generating a response.

The context window has a fixed size, measured in tokens, that varies by model. Tokens typically consist of short, commonly used words, and fragments of multi-syllable words. As your conversation progresses, the context window fills up with:

* **System instructions and tool definitions**: The built-in instructions that tell Copilot how to behave, plus the schemas of all available tools. These are always present and take up a fixed portion of the context window.
* **Your messages**: Every prompt you send.
* **Copilot's responses**: Everything Copilot says back to you.
* **Tool calls and results**: When Copilot reads files, runs commands, or searches your codebase, both the request and the output are added to the context. Tool results can be especially large—for example, if a tool reads a long file or runs a command that produces extensive output.

All of this accumulates in the context window. In a long or complex session, the context window can fill up.

### Why the context window matters

The context window is what gives Copilot its "memory" of your conversation. Everything inside the context window is available for Copilot to reference when responding to you.

This means that in a very long session, Copilot might not be able to hold the entire conversation history at once. Copilot CLI therefore has context management features that effectively allow you to continue a conversation with Copilot for as long as you need.

## Checking your context usage

You can check how much of the context window is currently in use by entering the `/context` slash command. This displays a visual breakdown of your token usage, showing:

* **System/Tools**: The fixed overhead of system instructions and tool definitions.
* **Messages**: The space used by your conversation history.
* **Free Space**: How much room is left for new messages.
* **Buffer**: A reserved portion that triggers automatic context management.

![Screenshot of the output of the '/context' CLI command.](/assets/images/help/copilot/copilot-cli-context-usage.png)

You might want to use the `/context` slash command when:

* You're in a long session and want to know how much space is left.
* Copilot seems to be forgetting earlier parts of the conversation.
* You want to understand whether compaction has occurred, or is likely to occur soon.

## Compaction

Compaction is the process that allows GitHub Copilot CLI to support long-running sessions without hitting the limits of the context window.

### When compaction happens

When your conversation reaches approximately 80% of the context window's capacity, Copilot CLI automatically starts compacting the context in the background. This leaves a buffer of approximately 20% so that tool calls can continue to run while compaction is in progress. If the context fills to approximately 95% before compaction finishes, Copilot CLI pauses briefly to wait for compaction to complete before continuing.

You can also trigger compaction manually at any time by entering the `/compact` command. This is useful if you're about to start a new phase of work and want to free up context space proactively. Press <kbd>Esc</kbd> to cancel a manual compaction if you change your mind.

### What compaction does

When compaction runs, Copilot CLI:

1. Takes a snapshot of the current conversation history.
2. Sends the full conversation to the AI model with a special prompt that asks it to generate a structured summary. The summary captures the goals of the conversation, what was done, key technical details, important files, and planned next steps.
3. Replaces the old conversation history with the summary, along with any original user instructions and the current state of any plans or to-do lists.
4. Keeps any messages that were added while compaction was running in the background.

The result is that the conversation history is compressed into a much smaller summary, freeing up the majority of the context window for new work. Copilot uses this summary to maintain continuity—it knows what was discussed, what was decided, and what to do next—even though the original messages have been replaced.

### What compaction does not preserve

Compaction is a summarization process, so some detail is inevitably lost. The summary captures the key points, but fine-grained details—such as the exact wording of every message, the full output of every command, or minor decisions made early in a long conversation—may not be included. If you need Copilot to recall a very specific detail from much earlier in the session, it may not have that information after compaction.

### What would happen without compaction

Without compaction, once the context window filled up, Copilot would have to fall back to simply dropping old messages from the conversation history—removing them without any summary or record. This would mean losing context abruptly, with no way for Copilot to know what was in the deleted messages. Compaction avoids this by replacing the history with an intelligent summary rather than discarding it.

## Checkpoints

Every time compaction happens—whether automatically or manually—a **checkpoint** is created. A checkpoint is a saved copy of the compaction summary, stored as a numbered, titled file in your session's workspace.

### Viewing checkpoints

To see all checkpoints in your current session, enter:

```copilot copy
/session checkpoints
```

This lists every checkpoint with its number and title:

```text
Checkpoint History (3 total):
  3. Refactoring authentication module
  2. Implementing user dashboard
  1. Initial planning and setup
```

Use the checkpoint number to view the full content of any checkpoint. For example, to view checkpoint 2, enter:

```copilot copy
/session checkpoints 2
```

### When checkpoints are useful

* **Reviewing what happened**: After a long session with multiple compactions, earlier phases of the conversation are no longer in the active context. Checkpoints let you read back through what Copilot did at each compaction.
* **Verifying continuity**: If you want to check that Copilot's summary accurately captured your earlier work before continuing, you can review the most recent checkpoint.
* **Debugging confusion**: If Copilot seems to have forgotten a decision or is going in a direction that contradicts earlier work, checking checkpoints can reveal what was preserved during compaction and what might have been summarized differently than you expected.

> \[!NOTE]
>
> * Checkpoints are created automatically. You don't need to manage them—they're there if you need them. For most sessions, you won't need to look at checkpoints at all.
> * You can't reverse a compaction once it has completed.

## Using long-running sessions

Automatic compaction allows you to continue working in a long-running session without worrying about hitting the limits of the context window. There are times when this is very useful, and other times when you might prefer to start a fresh session.

### When long sessions are useful

Long-running sessions work well when:

* You're working on a multi-phase task, such as building a feature that requires scaffolding, implementation, testing, and then creating a pull request.
* You're iterating on a problem and want Copilot to retain the context of what's been tried and what hasn't worked.
* You're doing exploratory work across a codebase and building up shared understanding with Copilot over time.

### When to start a fresh session

Starting a new session is better when:

* You're switching to an unrelated task. Copilot doesn't need the context of your previous work, and a clean context window means more space for the new task.
* The conversation has gone through many compactions, and you feel that important context is being lost in the summarization process.
* You want a clean slate—for example, if work went in a wrong direction and you'd rather start over than have Copilot try to reconcile earlier decisions with a new approach.

> \[!TIP]
> You can resume previous sessions at any time using the `/resume` command. This lets you pick up where you left off, including any checkpoints that were created during that session.

## Further reading

* [GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli)
* [Using GitHub Copilot CLI](/en/copilot/how-tos/use-copilot-agents/use-copilot-cli)
* [GitHub Copilot CLI command reference](/en/copilot/reference/copilot-cli-reference/cli-command-reference)