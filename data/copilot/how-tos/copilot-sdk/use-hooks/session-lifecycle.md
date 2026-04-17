# Session lifecycle hooks

Use the onSessionStart and onSessionEnd hooks to initialize context, clean up resources, and track session metrics in Copilot SDK.

> \[!NOTE]
> Copilot SDK is currently in public preview. Functionality and availability are subject to change.

Session lifecycle hooks let you respond to session start and end events. Use them to:

* Initialize context when sessions begin
* Clean up resources when sessions end
* Track session metrics and analytics
* Configure session behavior dynamically

## Session start hook

The `onSessionStart` hook is called when a session begins—whether new or resumed.

### Hook signature

```typescript
import type { SessionStartHookInput, HookInvocation, SessionStartHookOutput } from "@github/copilot-sdk";
type SessionStartHandler = (
  input: SessionStartHookInput,
  invocation: HookInvocation
) => Promise<
  SessionStartHookOutput | null | undefined
>;
```

For hook signatures in Python, Go, and .NET, see the [`github/copilot-sdk` repository](https://github.com/github/copilot-sdk/blob/main/docs/hooks/session-lifecycle.md#hook-signature). For Java, see the [`github/copilot-sdk-java` repository](https://github.com/github/copilot-sdk-java).

### Input

| Field           | Type                                 | Description                                |
| --------------- | ------------------------------------ | ------------------------------------------ |
| `timestamp`     | number                               | Unix timestamp when the hook was triggered |
| `cwd`           | string                               | Current working directory                  |
| `source`        | `"startup"` \| `"resume"` \| `"new"` | How the session was started                |
| `initialPrompt` | string \| undefined                  | The initial prompt if provided             |

### Output

| Field               | Type   | Description                     |
| ------------------- | ------ | ------------------------------- |
| `additionalContext` | string | Context to add at session start |
| `modifiedConfig`    | object | Override session configuration  |

### Examples

#### Add project context at start

```typescript
const session = await client.createSession({
  hooks: {
    onSessionStart: async (
      input, invocation
    ) => {
      console.log(
        `Session ${invocation.sessionId} `
        + `started (${input.source})`
      );

      const projectInfo =
        await detectProjectType(input.cwd);

      return {
        additionalContext:
          `This is a ${projectInfo.type} project.\n`
          + `Main language: `
          + `${projectInfo.language}\n`
          + `Package manager: `
          + `${projectInfo.packageManager}`,
      };
    },
  },
});
```

For examples in Python, see the [`github/copilot-sdk` repository](https://github.com/github/copilot-sdk/blob/main/docs/hooks/session-lifecycle.md#add-project-context-at-start). For Java, see the [`github/copilot-sdk-java` repository](https://github.com/github/copilot-sdk-java).

#### Handle session resume

```typescript
const session = await client.createSession({
  hooks: {
    onSessionStart: async (
      input, invocation
    ) => {
      if (input.source === "resume") {
        const previousState =
          await loadSessionState(
            invocation.sessionId
          );

        return {
          additionalContext:
            `Session resumed. Previous context:\n`
            + `- Last topic: `
            + `${previousState.lastTopic}\n`
            + `- Open files: `
            + previousState.openFiles.join(", "),
        };
      }
      return null;
    },
  },
});
```

#### Load user preferences

```typescript
const session = await client.createSession({
  hooks: {
    onSessionStart: async () => {
      const preferences =
        await loadUserPreferences();

      const contextParts = [];

      if (preferences.language) {
        contextParts.push(
          `Preferred language: `
          + `${preferences.language}`
        );
      }
      if (preferences.codeStyle) {
        contextParts.push(
          `Code style: ${preferences.codeStyle}`
        );
      }
      if (preferences.verbosity === "concise") {
        contextParts.push(
          "Keep responses brief and "
          + "to the point."
        );
      }

      return {
        additionalContext:
          contextParts.join("\n"),
      };
    },
  },
});
```

## Session end hook

The `onSessionEnd` hook is called when a session ends.

### Hook signature

```typescript
import {
  HookInvocation,
  SessionEndHookInput,
  SessionEndHookOutput,
} from "@github/copilot-sdk";

type SessionEndHandler = (
  input: SessionEndHookInput,
  invocation: HookInvocation
) => Promise<
  SessionEndHookOutput | null | undefined
>;
```

For hook signatures in Python, Go, and .NET, see the [`github/copilot-sdk` repository](https://github.com/github/copilot-sdk/blob/main/docs/hooks/session-lifecycle.md#hook-signature-1). For Java, see the [`github/copilot-sdk-java` repository](https://github.com/github/copilot-sdk-java).

### Input

| Field          | Type                | Description                                     |
| -------------- | ------------------- | ----------------------------------------------- |
| `timestamp`    | number              | Unix timestamp when the hook was triggered      |
| `cwd`          | string              | Current working directory                       |
| `reason`       | string              | Why the session ended (see the following table) |
| `finalMessage` | string \| undefined | The last message from the session               |
| `error`        | string \| undefined | Error message if session ended due to error     |

#### End reasons

| Reason        | Description                         |
| ------------- | ----------------------------------- |
| `"complete"`  | Session completed normally          |
| `"error"`     | Session ended due to an error       |
| `"abort"`     | Session was aborted by user or code |
| `"timeout"`   | Session timed out                   |
| `"user_exit"` | User explicitly ended the session   |

### Output

| Field            | Type      | Description                                  |
| ---------------- | --------- | -------------------------------------------- |
| `suppressOutput` | boolean   | Suppress the final session output            |
| `cleanupActions` | string\[] | List of cleanup actions to perform           |
| `sessionSummary` | string    | Summary of the session for logging/analytics |

### Examples

#### Track session metrics

```typescript
const sessionStartTimes =
  new Map<string, number>();

const session = await client.createSession({
  hooks: {
    onSessionStart: async (
      input, invocation
    ) => {
      sessionStartTimes.set(
        invocation.sessionId, input.timestamp
      );
      return null;
    },
    onSessionEnd: async (
      input, invocation
    ) => {
      const startTime = sessionStartTimes.get(
        invocation.sessionId
      );
      const duration = startTime
        ? input.timestamp - startTime
        : 0;

      await recordMetrics({
        sessionId: invocation.sessionId,
        duration,
        endReason: input.reason,
      });

      sessionStartTimes.delete(
        invocation.sessionId
      );
      return null;
    },
  },
});
```

For examples in Python, see the [`github/copilot-sdk` repository](https://github.com/github/copilot-sdk/blob/main/docs/hooks/session-lifecycle.md#track-session-metrics). For Java, see the [`github/copilot-sdk-java` repository](https://github.com/github/copilot-sdk-java).

#### Clean up resources

```typescript
const sessionResources =
  new Map<string, { tempFiles: string[] }>();

const session = await client.createSession({
  hooks: {
    onSessionStart: async (
      input, invocation
    ) => {
      sessionResources.set(
        invocation.sessionId,
        { tempFiles: [] }
      );
      return null;
    },
    onSessionEnd: async (
      input, invocation
    ) => {
      const resources =
        sessionResources.get(
          invocation.sessionId
        );

      if (resources) {
        for (const file
          of resources.tempFiles) {
          await fs.unlink(file).catch(() => {});
        }
        sessionResources.delete(
          invocation.sessionId
        );
      }

      console.log(
        `Session ${invocation.sessionId} `
        + `ended: ${input.reason}`
      );
      return null;
    },
  },
});
```

#### Save session state for resume

```typescript
const session = await client.createSession({
  hooks: {
    onSessionEnd: async (input, invocation) => {
      if (input.reason !== "error") {
        // Save state for potential resume
        await saveSessionState(invocation.sessionId, {
          endTime: input.timestamp,
          cwd: input.cwd,
          reason: input.reason,
        });
      }
      return null;
    },
  },
});
```

#### Log session summary

```typescript
const sessionData: Record<
  string,
  { prompts: number; tools: number;
    startTime: number }
> = {};

const session = await client.createSession({
  hooks: {
    onSessionStart: async (
      input, invocation
    ) => {
      sessionData[invocation.sessionId] = {
        prompts: 0,
        tools: 0,
        startTime: input.timestamp,
      };
      return null;
    },
    onUserPromptSubmitted: async (
      _, invocation
    ) => {
      sessionData[
        invocation.sessionId
      ].prompts++;
      return null;
    },
    onPreToolUse: async (_, invocation) => {
      sessionData[
        invocation.sessionId
      ].tools++;
      return { permissionDecision: "allow" };
    },
    onSessionEnd: async (
      input, invocation
    ) => {
      const data =
        sessionData[invocation.sessionId];
      const durationSec =
        (input.timestamp - data.startTime)
        / 1000;
      console.log(
        `Session Summary:\n`
        + `  ID: ${invocation.sessionId}\n`
        + `  Duration: ${durationSec}s\n`
        + `  Prompts: ${data.prompts}\n`
        + `  Tool calls: ${data.tools}\n`
        + `  End reason: ${input.reason}`
      );

      delete sessionData[
        invocation.sessionId
      ];
      return null;
    },
  },
});
```

## Best practices

* **Keep `onSessionStart` fast.** Users are waiting for the session to be ready.
* **Handle all end reasons.** Don't assume sessions end cleanly; handle errors and aborts.
* **Clean up resources.** Use `onSessionEnd` to free any resources allocated during the session.
* **Store minimal state.** If tracking session data, keep it lightweight.
* **Make cleanup idempotent.** `onSessionEnd` might not be called if the process crashes.

## Further reading

* [Quickstart for hooks](/en/copilot/how-tos/copilot-sdk/use-hooks/quickstart)
* [Error handling hook](/en/copilot/how-tos/copilot-sdk/use-hooks/error-handling)
* [User prompt submitted hook](/en/copilot/how-tos/copilot-sdk/use-hooks/user-prompt-submitted)