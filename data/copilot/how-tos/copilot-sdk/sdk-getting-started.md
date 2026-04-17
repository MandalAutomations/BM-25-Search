# Getting started with Copilot SDK

Learn how to install Copilot SDK and send your first message.

> \[!NOTE]
> Copilot SDK is currently in public preview. Functionality and availability are subject to change.

GitHub Copilot SDK lets you build applications powered by GitHub Copilot in your preferred programming language. In this guide, you'll install the SDK using `npm`, send your first message, and add streaming responses.

For more information and steps for other languages, see [Install the SDK](https://github.com/github/copilot-sdk/blob/main/docs/getting-started.md) in the `github/copilot-sdk` repository.

## Prerequisites

Before you begin, make sure you have **Node.js 18** or later installed.

## Authentication

Follow the instructions at [Installing GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/install-copilot-cli) to install and authenticate with GitHub Copilot CLI. This will allow the SDK to access your GitHub account and use Copilot.

1. Verify that Copilot CLI is installed and working:

   ```bash copy
   copilot --version
   ```

## Installation

1. Create a new directory and initialize your project:

   ```bash copy
   mkdir copilot-demo && cd copilot-demo
   npm init -y --init-type module
   ```

2. Install the SDK and TypeScript runner:

   ```bash copy
   npm install @github/copilot-sdk tsx
   ```

## Send your first message

1. Create a new file `index.ts` and add the following code. This sends a single prompt to Copilot and prints the response.

   ```typescript copy
   import { CopilotClient } from "@github/copilot-sdk";

   const client = new CopilotClient();
   const session = await client.createSession({ model: "gpt-4.1" });

   const response = await session.sendAndWait({ prompt: "What is 2 + 2?" });
   console.log(response?.data.content);

   await client.stop();
   process.exit(0);
   ```

2. Run the code:

   ```bash copy
   npx tsx index.ts
   ```

In this example:

* **`CopilotClient()`** creates a new client that manages the connection to Copilot CLI.
* **`createSession()`** starts a new conversation session with the specified model.
* **`sendAndWait()`** sends a prompt and waits for the complete response before returning.

## Add streaming responses

Instead of waiting for the full response, you can stream it as it's generated. This is useful for long responses or interactive applications where you want to display output in real time.

1. Update `index.ts` with the following code to listen and print response chunks as they arrive:

   ```typescript copy
   import { CopilotClient } from "@github/copilot-sdk";

   const client = new CopilotClient();
   const session = await client.createSession({
       model: "gpt-4.1",
       streaming: true,
   });

   // Listen for response chunks
   session.on("assistant.message_delta", (event) => {
       process.stdout.write(event.data.deltaContent);
   });
   session.on("session.idle", () => {
       console.log(); // New line when done
   });

   await session.sendAndWait({ prompt: "Tell me a short joke" });

   await client.stop();
   process.exit(0);
   ```

2. Run the code:

   ```bash copy
   npx tsx index.ts
   ```

With streaming enabled, the response appears incrementally as it's generated.
You can subscribe to events to process each chunk in real time:

* **`assistant.message_delta`** fires for each chunk of the response as it's generated.
* **`session.idle`** fires when the response is complete and the session is ready for the next message.

### Event subscription methods

The SDK provides the following methods to subscribe to events:

* **on(handler)**: Subscribe to all events. Returns the unsubscribe function.
* **on(eventType, handler)**: Subscribe to a specific event type. Returns the unsubscribe function.

Add the following code to `index.ts` to subscribe to events and unsubscribe when you no longer need them:

```typescript copy
// Subscribe to all events
const unsubscribeAll = session.on((event) => {
    console.log("Event:", event.type);
});

// Subscribe to specific event type
const unsubscribeIdle = session.on("session.idle", (event) => {
    console.log("Session is idle");
});

// Later, to unsubscribe:
unsubscribeAll();
unsubscribeIdle();
```

## Next steps

To continue getting started with Copilot SDK, see [Build Your First Copilot-Powered App](https://github.com/github/copilot-sdk/blob/main/docs/getting-started.md#step-4-add-a-custom-tool) in the `github/copilot-sdk` repository.