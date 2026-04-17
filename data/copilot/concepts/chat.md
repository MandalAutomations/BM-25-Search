# About GitHub Copilot Chat

Learn how you can use GitHub Copilot Chat to enhance your coding experience.

# Overview

GitHub Copilot Chat is the AI-powered chat interface for GitHub Copilot. It allows you to interact with AI models to get coding assistance, explanations, and suggestions in a conversational format.

Copilot Chat can help you with a variety of coding-related tasks, like offering you code suggestions, providing natural language descriptions of a piece of code's functionality and purpose, generating unit tests for your code, and proposing fixes for bugs in your code.

GitHub Copilot Chat is available in various environments:

* GitHub (the website)
* A range of IDEs such as Visual Studio Code, Xcode, and JetBrains IDEs
* GitHub Mobile
* GitHub Copilot CLI

Different environments may have different features and capabilities, but the core functionality remains consistent across platforms. To explore the functionality available in each environment, see the [GitHub Copilot Chat](/en/copilot/how-tos/chat) how-to guides and the [Tutorials for GitHub Copilot](/en/copilot/tutorials).

## Limitations

Copilot Chat is designed to assist with coding tasks, but you remain responsible for reviewing and validating the code it generates. It may not always produce correct or optimal solutions, and it can sometimes generate code that contains security vulnerabilities or other issues. Always test and review the code before using it in production.

## Customizing Copilot Chat responses

GitHub Copilot in GitHub, Visual Studio Code, and Visual Studio can provide chat responses that are tailored to the way your team works, the tools you use, the specifics of your project, or your personal preferences, if you provide it with enough context to do so. Instead of repeating instructions in each prompt, you can create and save instructions for Copilot Chat to customize what responses you receive.

There are various ways you can create custom instructions for Copilot Chat. These fall into three main categories:

* **Personal instructions**: You can add personal instructions so that all the chat responses you, as a user, receive are tailored to your preferences.
* **Repository instructions**: You can store instructions files in a repository, so that all prompts asked in the context of the repository automatically include the instructions you've defined.
* **Organization instructions**: If you are an organization owner, you can create a custom instructions file for an organization, so that all prompts asked in the context of any repository owned by the organization automatically include the instructions you've defined.

For more information, see [Adding personal custom instructions for GitHub Copilot](/en/copilot/customizing-copilot/adding-personal-custom-instructions-for-github-copilot), [Adding repository custom instructions for GitHub Copilot](/en/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot) and [Adding organization custom instructions for GitHub Copilot](/en/copilot/customizing-copilot/adding-organization-custom-instructions-for-github-copilot).

## AI models for Copilot Chat

You can change the model Copilot uses to generate responses to chat prompts. You may find that different models perform better, or provide more useful responses, depending on the type of questions you ask. Options include premium models with advanced capabilities.  See [Changing the AI model for GitHub Copilot Chat](/en/copilot/using-github-copilot/ai-models/changing-the-ai-model-for-copilot-chat).

## Extending Copilot Chat

Copilot Chat can be extended in a variety of ways to enhance its functionality and integrate it with other tools and services. This can include using the Model Context Protocol (MCP) to provide context-aware AI assistance, or connecting third-party tools to leverage GitHub’s AI capabilities.

### Extending Copilot Chat with MCP

MCP is an open standard that defines how applications share context with large language models (LLMs). MCP provides a standardized way to connect AI models to different data sources and tools, enabling them to work together more effectively.

You can configure MCP servers to provide context to Copilot Chat in various IDEs, such as Visual Studio Code and JetBrains IDEs. For Copilot Chat in GitHub, the GitHub MCP server is automatically configured, enabling Copilot Chat to perform a limited set of tasks, at your request, such as creating branches or merging pull requests. For more information, see [Extending GitHub Copilot Chat with Model Context Protocol (MCP) servers](/en/copilot/how-tos/context/model-context-protocol/extending-copilot-chat-with-mcp) and [Using the GitHub MCP Server in your IDE](/en/copilot/how-tos/context/model-context-protocol/using-the-github-mcp-server).

### Further reading

* [GitHub Copilot Chat](/en/copilot/how-tos/chat-with-copilot) how-to guides
* [Using GitHub Copilot CLI](/en/copilot/how-tos/use-copilot-agents/use-copilot-cli)
* [GitHub Copilot Chat Cookbook](/en/copilot/tutorials/copilot-chat-cookbook)