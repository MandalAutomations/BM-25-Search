# Configuring an MCP server allowlist for your enterprise

Define which MCP servers your users can and cannot use without the need for a private registry.

## About allowlists

You can define an allowlist and denylist to control which MCP servers users in your enterprise can run in Copilot clients. These lists are defined in your enterprise's `managed-settings.json`, which you can store on GitHub.

For more information, see [MCP server usage in your company](/en/copilot/concepts/mcp-management).

## Prerequisites

* For any MCP servers to run, the **MCP servers in Copilot** policy must be enabled for your enterprise or for organizations where MCP servers should be allowed.
* If you currently restrict MCP servers to a custom registry, we recommend turning off this restriction to avoid conflicts with your new allowlist and maintain a single source of truth. Set the **Restrict MCP access to registry servers** policy to **Allow all**, and optionally clear the value for **MCP Registry URL**.

You can find these settings in the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-mcp" aria-label="MCP" role="img"><path d="M5.52 1.12a3.578 3.578 0 0 1 6.078 2.98 3.578 3.578 0 0 1 2.982 6.08l-3.292 3.293a.252.252 0 0 0 0 .354l.843.843a.749.749 0 1 1-1.06 1.06l-.844-.843a1.75 1.75 0 0 1 0-2.474L13.52 9.12a2.08 2.08 0 0 0 0-2.94 2.08 2.08 0 0 0-2.94 0L7.731 9.03A.75.75 0 0 1 6.67 7.97l2.85-2.85a2.08 2.08 0 0 0 0-2.94 2.08 2.08 0 0 0-2.94 0l-4.799 4.8A.75.75 0 0 1 .72 5.92Z"></path><path d="M7.52 3.12a.749.749 0 1 1 1.06 1.06L5.731 7.03A2.079 2.079 0 0 0 8.67 9.97l2.85-2.85a.749.749 0 1 1 1.06 1.06l-2.849 2.85A3.578 3.578 0 0 1 4.67 5.97Z"></path></svg> **MCP** section of your Copilot policies. See [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies).

## Defining an allowlist or denylist

1. Create a `managed-settings.json` file for your enterprise. Most enterprises store this file in a `.github-private` repository. You can also install it directly on users' machines using mobile device management. See [Configuring enterprise-managed settings](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/configure-enterprise-managed-settings#deploying-server-managed-settings).
2. Edit the file to define an allowlist and denylist for MCP servers. You can match by name, server URL, or specific commands. For syntax details, see [allowedMcpServers](/en/copilot/reference/enterprise-managed-settings-reference#allowedMcpServers), and [deniedMcpServers](/en/copilot/reference/enterprise-managed-settings-reference#deniedMcpServers) in "Enterprise managed settings reference."

   The following example allows servers that match any of the three allowlist entries. The server at `learn.microsoft.com` is always blocked, even if it also matches an allowlist entry.

   ```json copy
   {
     "allowedMcpServers": [
       { "serverUrl": "https://api.githubcopilot.com/*" },
       { "serverCommand": ["npx", "@playwright/mcp@latest"] },
       { "serverCommand": ["cmd", "/c", "uvx", "markitdown-mcp"] }
     ],
     "deniedMcpServers": [
       { "serverUrl": "https://learn.microsoft.com/*" }
     ]
   }
   ```

## Evaluation rules

Copilot clients evaluate MCP servers in this order:

1. Always allow built-in default servers, such as the built-in GitHub MCP server.
2. Block the server if it matches any entry in `deniedMcpServers`.
3. If `allowedMcpServers` is present, block the server if it does not match an entry.
4. Block the server if its URL or command contains an unresolved variable, such as `${VARIABLE}` or `$VARIABLE`, because the client cannot verify the server.

If a client receives settings from multiple `managed-settings.json` deployment methods, all the settings apply. A deny rule from any source blocks the server, and a server must match an allowlist entry at every layer that defines one.

If an allowlist or denylist is malformed (for example, has invalid JSON), the client treats the policy as an empty `allowedMcpServers` list. This blocks all servers except built-in default servers.

If the client cannot determine a policy layer because of a retrieval or device-discovery error, it retains the previously enforced policy. The effective policy can become more restrictive, but not less restrictive.