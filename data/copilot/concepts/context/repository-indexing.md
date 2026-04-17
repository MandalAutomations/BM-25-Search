# Indexing repositories for GitHub Copilot

Copilot improves responses by indexing your repositories.

## Benefit of indexing repositories

Copilot's ability to answer natural language questions and complete tasks in a repository context is optimized when the semantic code search index for the repository is up to date.

**Copilot will not use your indexed repository for model training.**

## Semantic code search in Copilot Chat

When you start a conversation with Copilot Chat that has a repository context, the repository is automatically indexed to improve context-enriched answers to your questions about the code's structure and logic in GitHub and Visual Studio Code. For example, you can ask **“How does this repo manage HTTP requests and responses?”** and Copilot Chat will reference relevant sections of your code to deliver an informed answer.

For more information on how to ask questions, see [Asking GitHub Copilot questions in GitHub](/en/copilot/using-github-copilot/asking-github-copilot-questions-in-github).

## Semantic code search in Copilot cloud agent

Copilot cloud agent uses semantic code search to find relevant code based on meaning, rather than relying solely on exact text matches with tools like `grep`. When the agent doesn't know the precise names or patterns to search for, semantic code search helps it locate the right code faster. No configuration is required—the agent automatically uses semantic code search when appropriate.

For more information about Copilot cloud agent, see [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent).

## About index creation and use

Indexing runs in the background and initial indexing can take up to 60 seconds for a large repository. Once a repository has been indexed for the first time, re-indexing is much quicker and the index will typically be automatically updated to include the latest changes within seconds of you starting a new conversation.

Once an index has been created for a repository, it can be used by:

* Copilot Chat in GitHub and Visual Studio Code
* Copilot cloud agent

> \[!TIP] There is no limit to how many repositories you can index.

## Excluding content from Copilot Chat answers

Enterprise or organization owners with a Copilot Enterprise or Copilot Business plan can define content exclusions to control the behavior of GitHub Copilot for the Copilot seats they manage. For more information, see [Excluding content from GitHub Copilot](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/setting-policies-for-copilot-in-your-organization/excluding-content-from-github-copilot).

If a semantic code search index is created for a repository that is included in a content exclusion policy, data is filtered according to the policy before being passed to Copilot Chat.