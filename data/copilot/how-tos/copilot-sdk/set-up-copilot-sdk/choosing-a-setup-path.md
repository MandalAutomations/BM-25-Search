# Choosing a setup path for Copilot SDK

Find the right setup guide that matches how you plan to use Copilot SDK.

> \[!NOTE]
> Copilot SDK is currently in technical preview. Functionality and availability are subject to change.

## Architecture overview

Every GitHub Copilot SDK integration follows the same core pattern: your application talks to the SDK, which communicates with Copilot CLI over JSON-RPC. What changes across setups is where the CLI runs, how users authenticate, and how sessions are managed.

## Who are you?

### Hobbyist

You're building a personal assistant, side project, or experimental app. You want the simplest path to getting Copilot in your code.

**Start with:**

1. [Using a local CLI with Copilot SDK](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/local-cli)—use the CLI already signed in on your machine.
2. [Using a bundled CLI with Copilot SDK](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/bundled-cli)—package everything into a standalone app.

### Internal app developer

You're building tools for your team or company. Users are employees who need to authenticate with their enterprise GitHub accounts or org memberships.

**Start with:**

1. [Using GitHub OAuth with Copilot SDK](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/github-oauth)—let employees sign in with their GitHub accounts.
2. [Setting up Copilot SDK for backend services](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/backend-services)—run the SDK in your internal services.

**If scaling beyond a single server:**

1. [Scaling Copilot SDK deployments](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/scaling)—handle multiple users and services.

### App developer (ISV)

You're building a product for customers. You need to handle authentication for your users—either through GitHub or by managing identity yourself.

**Start with:**

1. [Using GitHub OAuth with Copilot SDK](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/github-oauth)—let customers sign in with GitHub.
2. [BYOK](https://github.com/github/copilot-sdk/blob/main/docs/auth/byok.md) in the `github/copilot-sdk` repository—manage identity with your own model keys.
3. [Setting up Copilot SDK for backend services](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/backend-services)—power your product from server-side code.

**For production:**

1. [Scaling Copilot SDK deployments](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/scaling)—serve many customers reliably.

### Platform developer

You're embedding Copilot into a platform—APIs, developer tools, or infrastructure that other developers build on. You need fine-grained control over sessions, scaling, and multi-tenancy.

**Start with:**

1. [Setting up Copilot SDK for backend services](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/backend-services)—core server-side integration.
2. [Scaling Copilot SDK deployments](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/scaling)—session isolation, horizontal scaling, persistence.

**Depending on your authentication model:**

1. [Using GitHub OAuth with Copilot SDK](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/github-oauth)—for GitHub-authenticated users.
2. [BYOK](https://github.com/github/copilot-sdk/blob/main/docs/auth/byok.md) in the `github/copilot-sdk` repository—for self-managed identity and model access.

## Decision matrix

Use this table to find the right guide based on what you need to do.

| What you need                                  | Guide                                                                                                                      |
| ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Simplest possible setup                        | [Using a local CLI with Copilot SDK](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/local-cli)                         |
| Ship a standalone app with Copilot             | [Using a bundled CLI with Copilot SDK](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/bundled-cli)                     |
| Users sign in with GitHub                      | [Using GitHub OAuth with Copilot SDK](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/github-oauth)                     |
| Use your own model keys (OpenAI, Azure, etc.)  | [BYOK](https://github.com/github/copilot-sdk/blob/main/docs/auth/byok.md) in the `github/copilot-sdk` repository           |
| Azure BYOK with Managed Identity (no API keys) | [Using Azure Managed Identity with Copilot SDK](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/azure-managed-identity) |
| Run the SDK on a server                        | [Setting up Copilot SDK for backend services](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/backend-services)         |
| Serve multiple users or scale horizontally     | [Scaling Copilot SDK deployments](/en/copilot/how-tos/copilot-sdk/set-up-copilot-sdk/scaling)                              |

## Prerequisites

All guides assume you have:

* **Copilot CLI** installed. For more information, see [Installing GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/set-up-copilot-cli/install-copilot-cli).
* **One of the SDKs** installed:
  * Node.js: `npm install @github/copilot-sdk`
  * Python: `pip install github-copilot-sdk`
  * Go: `go get github.com/github/copilot-sdk/go`
  * .NET: `dotnet add package GitHub.Copilot.SDK`
  * Java: See the [`github/copilot-sdk-java`](https://github.com/github/copilot-sdk-java) repository for Maven/Gradle setup

If you're new to the GitHub Copilot SDK, start with [Getting started with Copilot SDK](/en/copilot/how-tos/copilot-sdk/sdk-getting-started) first, then return here for production configuration.

## Next steps

Pick the guide that matches your situation from the [decision matrix](#decision-matrix) above, or start with the persona description closest to your role.