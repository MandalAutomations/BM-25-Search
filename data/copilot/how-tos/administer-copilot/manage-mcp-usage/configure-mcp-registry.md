# Configure an MCP registry for your organization or enterprise

Create and host a list of MCP servers that your developers can access.

## Prerequisites

Before you create your Model Context Protocol (MCP) registry, you should understand the functionality and benefits of MCP management for your company. See [MCP server usage in your company](/en/copilot/concepts/mcp-management).

## Option 1: Self-hosting an MCP registry

At its core, an MCP registry is a set of HTTPS endpoints that serve details about the included MCP servers. You can create your registry with any of the following options:

* Fork and self-host the open-source MCP Registry. To get started, see the [MCP Registry Quickstart](https://github.com/modelcontextprotocol/registry/tree/main?tab=readme-ov-file#quick-start) in the `modelcontextprotocol/registry` repository.
* Run the open-source registry locally using Docker.
* Publish your own custom implementation.

> \[!NOTE]
> If you want your developers to have access to local MCP servers, include those servers in your registry with the correct server ID. For more information, see [MCP allowlist enforcement](/en/copilot/reference/mcp-allowlist-enforcement).

To create a valid MCP registry that is reachable by GitHub Copilot, the registry must meet the following requirements:

* [Endpoint and specification requirements](#endpoint-and-specification-requirements)
* [Cross-Origin Resource Sharing requirements](#cross-origin-resource-sharing-requirements)

### Endpoint and specification requirements

A valid registry must support URL routing and follow the v0.1 MCP registry specification, including the following endpoints:

* `GET /v0.1/servers`: Returns a list of all included MCP servers
* `GET /v0.1/servers/{serverName}/versions/latest`: Returns the latest version of a specific server
* `GET /v0.1/servers/{serverName}/versions/{version}`: Returns the details for a specific version of a server

For more details and example JSON responses to requests, see the [Official MCP Registry documentation](https://registry.modelcontextprotocol.io/docs).

#### Support for the v0.1 specification

While the MCP registry launched using the v0 specification, that version is now considered unstable and should not be implemented. Instead, create your registry according to the v0.1 specification, which is supported in the following IDEs:

| IDE              | v0.1 support                                                                                                                                                                                                                                                                                                             |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| VS Code Insiders | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| VS Code          | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Visual Studio    | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Eclipse          | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| JetBrains IDEs   | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |
| Xcode            | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Supported" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> |

### Cross-Origin Resource Sharing requirements

To ensure Copilot can successfully make cross-origin requests when fetching your registry, the registry or reverse proxy must include Cross-Origin Resource Sharing (CORS) headers. Add the following headers to all `/v0.1/servers` endpoints:

```http copy
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET, OPTIONS
Access-Control-Allow-Headers: Authorization, Content-Type
```

## Option 2: Using Azure API Center as an MCP registry

Azure API Center provides a fully managed MCP registry with automatic CORS configuration, built-in governance features, and no additional web server setup.

1. To complete the initial setup for your registry, see [Register and discover remote MCP servers in your API inventory](https://learn.microsoft.com/azure/api-center/register-discover-mcp-server) in the Azure documentation.
2. If you want your developers to have access to local MCP servers, include those servers in your registry with the correct server ID. For more information, see [MCP allowlist enforcement](/en/copilot/reference/mcp-allowlist-enforcement).
3. To ensure GitHub Copilot can fetch your registry, in the visibility settings of your API Center, allow anonymous access.
4. Copy your API Center endpoint URL. In the next article, you will use this URL to make your registry available across your company.

### Pricing and limits

Azure API Center offers a **free tier** for basic API cataloging and discovery, including MCP registry management. If you need higher limits than those included with the free tier, you can upgrade to the Standard plan. For detailed limits and pricing, see [Azure API Center limits](https://learn.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits#azure-api-center-limits) in the Azure documentation.

## Next steps

Now that you have created your MCP registry, you can set MCP policies for your company. See [Configure MCP server access for your organization or enterprise](/en/copilot/how-tos/administer-copilot/manage-mcp-usage/configure-mcp-server-access).