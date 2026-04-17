# Authenticating with Copilot SDK

Choose the authentication method in GitHub Copilot SDK that best fits your deployment scenario.

> \[!NOTE]
> Copilot SDK is currently in public preview. Functionality and availability are subject to change.

## Authentication methods overview

GitHub Copilot SDK supports multiple authentication methods to fit different use cases.

| Method                                                | Use case                                                | Copilot subscription required |
| ----------------------------------------------------- | ------------------------------------------------------- | ----------------------------- |
| [GitHub signed-in user](#github-signed-in-user)       | Interactive apps where users sign in with GitHub        | Yes                           |
| [OAuth GitHub App](#oauth-github-app)                 | Apps acting on behalf of users via OAuth                | Yes                           |
| [Environment variables](#environment-variables)       | CI/CD, automation, server-to-server                     | Yes                           |
| [BYOK (bring your own key)](#byok-bring-your-own-key) | Using your own API keys (Azure AI Foundry, OpenAI, etc) | No                            |

## GitHub signed-in user

This is the default authentication method when running the GitHub Copilot CLI interactively, see [Authenticating GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/set-up-copilot-cli/authenticate-copilot-cli). Users authenticate via the GitHub OAuth device flow, and the SDK uses their stored credentials.

**How it works:**

1. User runs the `copilot` CLI and signs in via GitHub OAuth.
2. Credentials are stored securely in the system keychain.
3. The SDK automatically uses stored credentials.

**SDK configuration:**

```typescript
import { CopilotClient } from "@github/copilot-sdk";

// Default: uses signed-in user credentials
const client = new CopilotClient();
```

For examples in other languages, see [Authentication](https://github.com/github/copilot-sdk/blob/main/docs/auth/index.md#github-signed-in-user) in the `github/copilot-sdk` repository.

**When to use this method:**

* Desktop applications where users interact directly
* Development and testing environments
* Any scenario where a user can sign in interactively

## OAuth GitHub App

Use an OAuth GitHub App to authenticate users through your application and pass their credentials to the SDK. This lets your application make GitHub Copilot API requests on behalf of users who authorize your app.

**How it works:**

1. User authorizes your OAuth GitHub App.
2. Your app receives a user access token (`gho_` or `ghu_` prefix).
3. Pass the token to the SDK via the `githubToken` option.

**SDK configuration:**

```typescript
import { CopilotClient } from "@github/copilot-sdk";

const client = new CopilotClient({
    githubToken: userAccessToken,  // Token from OAuth flow
    useLoggedInUser: false,        // Don't use stored CLI credentials
});
```

For examples in other languages, see [Authentication](https://github.com/github/copilot-sdk/blob/main/docs/auth/index.md#oauth-github-app) in the `github/copilot-sdk` repository.

**Supported token types:**

* `gho_` — OAuth user access tokens
* `ghu_` — GitHub App user access tokens
* `github_pat_` — Fine-grained personal access tokens

**Not supported:**

* `ghp_` — Personal access tokens (classic) (closing down)

**When to use this method:**

* Web applications where users sign in via GitHub
* Software-as-a-service (SaaS) applications building on top of GitHub Copilot
* Any multi-user application where you need to make requests on behalf of different users

## Environment variables

For automation, CI/CD pipelines, and server-to-server scenarios, you can authenticate using environment variables.

**Supported environment variables (in priority order):**

1. `COPILOT_GITHUB_TOKEN` — Recommended for explicit Copilot usage
2. `GH_TOKEN` — GitHub CLI compatible
3. `GITHUB_TOKEN` — GitHub Actions compatible

The SDK automatically detects and uses these environment variables without any code changes required:

```typescript
import { CopilotClient } from "@github/copilot-sdk";

// Token is read from environment variable automatically
const client = new CopilotClient();
```

**When to use this method:**

* CI/CD pipelines (GitHub Actions, Jenkins, etc)
* Automated testing
* Server-side applications with service accounts
* Development when you don't want to use interactive sign-in

## BYOK (bring your own key)

BYOK lets you use your own API keys from model providers like Azure AI Foundry, OpenAI, or Anthropic. This bypasses GitHub Copilot authentication entirely.

**Key benefits:**

* No GitHub Copilot subscription required
* Use enterprise model deployments
* Direct billing with your model provider
* Support for Azure AI Foundry, OpenAI, Anthropic, and OpenAI-compatible endpoints

For complete setup instructions, including provider configuration options, limitations, and code examples, see [Bring your own key (BYOK)](/en/copilot/how-tos/copilot-sdk/authenticate-copilot-sdk/bring-your-own-key).

## Authentication priority

When multiple authentication methods are available, the SDK uses them in this priority order:

1. **Explicit `githubToken`** — Token passed directly to the SDK constructor
2. **HMAC key** — `CAPI_HMAC_KEY` or `COPILOT_HMAC_KEY` environment variables
3. **Direct API token** — `GITHUB_COPILOT_API_TOKEN` with `COPILOT_API_URL`
4. **Environment variable tokens** — `COPILOT_GITHUB_TOKEN` → `GH_TOKEN` → `GITHUB_TOKEN`
5. **Stored OAuth credentials** — From previous `copilot` CLI sign-in
6. **GitHub CLI** — `gh auth` credentials

## Disabling auto sign-in

To prevent the SDK from automatically using stored credentials or GitHub CLI authentication, set the `useLoggedInUser` option to `false`:

```typescript
const client = new CopilotClient({
    useLoggedInUser: false,  // Only use explicit tokens
});
```

For examples in other languages, see [Authentication](https://github.com/github/copilot-sdk/blob/main/docs/auth/index.md#disabling-auto-login) in the `github/copilot-sdk` repository.

## Next steps

* [Bring your own key (BYOK)](/en/copilot/how-tos/copilot-sdk/authenticate-copilot-sdk/bring-your-own-key)
* [MCP servers documentation](https://github.com/github/copilot-sdk/blob/main/docs/features/mcp.md)—Connect to external tools using the SDK