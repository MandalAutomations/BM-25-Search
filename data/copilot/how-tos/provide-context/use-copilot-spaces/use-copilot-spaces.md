# Using GitHub Copilot Spaces

Use spaces to ground Copilot's responses in the right context for a specific task.

For information on creating Copilot Spaces, see [Creating GitHub Copilot Spaces](/en/copilot/how-tos/provide-context/use-copilot-spaces/create-copilot-spaces).

## Using Copilot Spaces in GitHub

Once you've added context to your space, you can ask Copilot questions in the space's chat interface in GitHub. Your chat will be grounded in the context you've added. You can view all conversations you have had in the space's "Conversations" tab.

You can also change the large language model (LLM) used for your space by selecting the **CURRENT-MODEL** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="chevron-down" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> dropdown menu, then clicking the AI model of your choice. For more information, see [AI model comparison](/en/copilot/reference/ai-models/model-comparison).

To star your favorite spaces so that you can easily find them later, you can click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-star" aria-label="star" role="img"><path d="M8 .25a.75.75 0 0 1 .673.418l1.882 3.815 4.21.612a.75.75 0 0 1 .416 1.279l-3.046 2.97.719 4.192a.751.751 0 0 1-1.088.791L8 12.347l-3.766 1.98a.75.75 0 0 1-1.088-.79l.72-4.194L.818 6.374a.75.75 0 0 1 .416-1.28l4.21-.611L7.327.668A.75.75 0 0 1 8 .25Zm0 2.445L6.615 5.5a.75.75 0 0 1-.564.41l-3.097.45 2.24 2.184a.75.75 0 0 1 .216.664l-.528 3.084 2.769-1.456a.75.75 0 0 1 .698 0l2.77 1.456-.53-3.084a.75.75 0 0 1 .216-.664l2.24-2.183-3.096-.45a.75.75 0 0 1-.564-.41L8 2.694Z"></path></svg>** in the top right corner of the space. To view all spaces available to you, including starred spaces, go to [https://github.com/copilot/spaces](https://github.com/copilot/spaces?ref_product=copilot\&ref_type=engagement\&ref_style=text).

## Using Copilot Spaces in your IDE

You can also access the information and context from Spaces directly in your IDE using the GitHub MCP server. This allows you to leverage your curated context while coding without switching between your IDE and the web interface.

This functionality is available in any IDE that supports the GitHub Copilot extension and the GitHub MCP server.

> \[!NOTE] When using Spaces in your IDE, repository context and uploaded files are not supported. You will have access to all other sources, including text content added via "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-paste" aria-label="Add text content" role="img"><path d="M3.626 3.533a.249.249 0 0 0-.126.217v9.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-9.5a.249.249 0 0 0-.126-.217.75.75 0 0 1 .752-1.298c.541.313.874.89.874 1.515v9.5A1.75 1.75 0 0 1 12.25 15h-8.5A1.75 1.75 0 0 1 2 13.25v-9.5c0-.625.333-1.202.874-1.515a.75.75 0 0 1 .752 1.298ZM5.75 1h4.5a.75.75 0 0 1 .75.75v3a.75.75 0 0 1-.75.75h-4.5A.75.75 0 0 1 5 4.75v-3A.75.75 0 0 1 5.75 1Zm.75 3h3V2.5h-3Z"></path></svg> **Add text content**", GitHub files, issues, pull requests, and instructions from the space.

Once you've accessed space context from your IDE:

* The space's context will inform Copilot's responses
* You can reference the space's content when generating code, getting explanations, or working on development tasks
* Your spaces stay in sync as your project evolves. GitHub files and other GitHub-based sources added to a space are automatically updated as they change, making Copilot an evergreen expert in your project

### Prerequisites

To use Spaces in your IDE, you need to:

* Set up the remote GitHub MCP server for your IDE. For more information, see [Setting up the GitHub MCP Server](/en/copilot/how-tos/provide-context/use-mcp/set-up-the-github-mcp-server) and [Remote GitHub MCP Server](https://github.com/github/github-mcp-server/blob/main/docs/remote-server.md) in the GitHub MCP server documentation.
* Configure the set up of the remote GitHub MCP server so that the Spaces toolset is enabled.

  The Spaces toolset is not included in the default configuration, so you must explicitly enable it using the `X-MCP-Toolsets` header. The following example configuration enables both the default tools and Spaces:

  ```json copy
  {
    "servers": {
      "github": {
        "type": "http",
        "url": "https://api.githubcopilot.com/mcp/",
        "headers": {
          "X-MCP-Toolsets": "default,copilot_spaces"
        }
      }
    }
  }
  ```

  Alternatively, you can use the dedicated Spaces toolset URL: `https://api.githubcopilot.com/mcp/x/copilot_spaces`. Note that this configuration provides *only* Spaces tools, without other default GitHub MCP server functionality.

### Accessing space context from your IDE

For more detailed information on using the GitHub MCP server in a specific IDE, see [Using the GitHub MCP Server in your IDE](/en/copilot/how-tos/provide-context/use-mcp/use-the-github-mcp-server).

Note that Spaces can only be used in agent mode in your IDE, since spaces are accessed via the GitHub MCP server.

1. In your IDE, open Copilot Chat and select **Agent** from the agent dropdown menu.
   * To confirm that the Spaces tools are enabled, in the Copilot Chat box, click the tools icon. In the tools list, expand the GitHub MCP server entry and confirm that the `get_copilot_space` and `list_copilot_spaces` tools are listed and enabled.
   * If you don't see the tools listed, check that you have completed the prerequisites above, including enabling the `copilot_spaces` toolset in your GitHub MCP server configuration.
2. In the Copilot Chat box, enter a prompt that references the space that you want to use as context. If you know the exact name of the space and the name of the user or organization that owns the space, you can provide that. Otherwise, Copilot will automatically use the `list_copilot_spaces` tool to find spaces that match the name or text you provide and access the context from those spaces.

   For example, you could use either of these two prompts:

   * `Using the Copilot space 'Checkout Flow Redesign' owned by myorganization, summarize the implementation plan.`
   * `Summarize the implementation plan from the Copilot space for the checkout flow redesign.`

   Follow-up prompts in the same chat conversation will have access to the same spaces, without you having to reference it explicitly.

## Next steps

* To learn more about how to use Spaces to help you with development work, see [Speeding up development work with GitHub Copilot Spaces](/en/copilot/using-github-copilot/copilot-spaces/speeding-up-development-work-with-copilot-spaces).
* To learn how to share your space with your team, see [Collaborating with others using GitHub Copilot Spaces](/en/copilot/using-github-copilot/copilot-spaces/collaborating-with-your-team-using-copilot-spaces).