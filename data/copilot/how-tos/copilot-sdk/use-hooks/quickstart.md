# Quickstart for hooks

Get started with hooks in Copilot SDK to control tool execution, transform results, add context, handle errors, and audit interactions.

> \[!NOTE]
> Copilot SDK is currently in public preview. Functionality and availability are subject to change.

Hooks allow you to intercept and customize the behavior of Copilot SDK sessions at key points in the conversation lifecycle. Use hooks to:

* **Control tool execution**—approve, deny, or modify tool calls
* **Transform results**—modify tool outputs before they're processed
* **Add context**—inject additional information at session start
* **Handle errors**—implement custom error handling
* **Audit and log**—track all interactions for compliance

## Available hooks

| Hook                                                                                               | Trigger                   | Use case                                |
| -------------------------------------------------------------------------------------------------- | ------------------------- | --------------------------------------- |
| [`onPreToolUse`](/en/copilot/how-tos/copilot-sdk/use-hooks/pre-tool-use)                           | Before a tool executes    | Permission control, argument validation |
| [`onPostToolUse`](/en/copilot/how-tos/copilot-sdk/use-hooks/post-tool-use)                         | After a tool executes     | Result transformation, logging          |
| [`onUserPromptSubmitted`](/en/copilot/how-tos/copilot-sdk/use-hooks/user-prompt-submitted)         | When user sends a message | Prompt modification, filtering          |
| [`onSessionStart`](/en/copilot/how-tos/copilot-sdk/use-hooks/session-lifecycle#session-start-hook) | Session begins            | Add context, configure session          |
| [`onSessionEnd`](/en/copilot/how-tos/copilot-sdk/use-hooks/session-lifecycle#session-end-hook)     | Session ends              | Cleanup, analytics                      |
| [`onErrorOccurred`](/en/copilot/how-tos/copilot-sdk/use-hooks/error-handling)                      | Error happens             | Custom error handling                   |

## Quick start

The following example demonstrates how to register hooks when creating a session in Node.js/TypeScript.

```typescript
import { CopilotClient } from "@github/copilot-sdk";

const client = new CopilotClient();

const session = await client.createSession({
  hooks: {
    onPreToolUse: async (input) => {
      console.log(`Tool called: ${input.toolName}`);
      // Allow all tools
      return { permissionDecision: "allow" };
    },
    onPostToolUse: async (input) => {
      console.log(
        `Tool result: ${JSON.stringify(input.toolResult)}`
      );
      return null; // No modifications
    },
    onSessionStart: async (input) => {
      return {
        additionalContext:
          "User prefers concise answers.",
      };
    },
  },
});
```

For examples in Python, Go, and .NET, see the [`github/copilot-sdk` repository](https://github.com/github/copilot-sdk/blob/main/docs/hooks/index.md#quick-start). For Java, see the [`github/copilot-sdk-java` repository](https://github.com/github/copilot-sdk-java).

## Hook invocation context

Every hook receives an `invocation` parameter with context about the current session.

| Field       | Type   | Description                   |
| ----------- | ------ | ----------------------------- |
| `sessionId` | string | The ID of the current session |

This allows hooks to maintain state or perform session-specific logic.

## Common patterns

### Logging all tool calls

```typescript
const session = await client.createSession({
  hooks: {
    onPreToolUse: async (input) => {
      console.log(
        `[${new Date().toISOString()}] Tool: `
        + `${input.toolName}, `
        + `Args: ${JSON.stringify(input.toolArgs)}`
      );
      return { permissionDecision: "allow" };
    },
    onPostToolUse: async (input) => {
      console.log(
        `[${new Date().toISOString()}] `
        + `Result: ${JSON.stringify(input.toolResult)}`
      );
      return null;
    },
  },
});
```

### Blocking dangerous tools

```typescript
const BLOCKED_TOOLS = ["shell", "bash", "exec"];

const session = await client.createSession({
  hooks: {
    onPreToolUse: async (input) => {
      if (BLOCKED_TOOLS.includes(input.toolName)) {
        return {
          permissionDecision: "deny",
          permissionDecisionReason:
            "Shell access is not permitted",
        };
      }
      return { permissionDecision: "allow" };
    },
  },
});
```

### Adding user context

```typescript
const session = await client.createSession({
  hooks: {
    onSessionStart: async () => {
      const userPrefs = await loadUserPreferences();
      return {
        additionalContext:
          `User preferences: `
          + `${JSON.stringify(userPrefs)}`,
      };
    },
  },
});
```

## Next steps

* [Pre-tool use hook](/en/copilot/how-tos/copilot-sdk/use-hooks/pre-tool-use)
* [Post-tool use hook](/en/copilot/how-tos/copilot-sdk/use-hooks/post-tool-use)
* [User prompt submitted hook](/en/copilot/how-tos/copilot-sdk/use-hooks/user-prompt-submitted)
* [Session lifecycle hooks](/en/copilot/how-tos/copilot-sdk/use-hooks/session-lifecycle)
* [Error handling hook](/en/copilot/how-tos/copilot-sdk/use-hooks/error-handling)