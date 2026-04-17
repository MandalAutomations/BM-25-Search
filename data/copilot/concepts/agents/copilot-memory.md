# About agentic memory for GitHub Copilot

Find out how Copilot can store details it has learned about a codebase and use that knowledge for future work in a repository.

> \[!NOTE]
> This feature is currently in public preview and is subject to change.

## Introduction

As a developer, when you start working on an existing codebase—perhaps as a new member of the development team—you can read the README for the repository, the coding conventions documentation, and other information to help you understand the repository and how you should work when updating or adding code. This will help you submit good quality pull requests. However, the quality of work you're able to deliver will steadily improve as you work on the codebase and learn more about it. In the same way, by allowing Copilot to build its own understanding of your repository, you can enable it to become increasingly effective over time.

Copilot can develop a persistent understanding of a repository by storing "memories."

Memories are tightly scoped pieces of information about a repository, that are deduced by Copilot as it works on the repository. Memories are:

* Repository-specific.
* Only created in response to Copilot activity initiated by users who have had Copilot Memory enabled.

Memories created by one part of Copilot can be used by another part of Copilot. So, for example, if Copilot cloud agent discovers how your repository handles database connections, Copilot code review can later apply that knowledge to spot inconsistent patterns in a pull request it is reviewing. Similarly, if Copilot code review learns about settings that must stay synchronized in two separate files, then Copilot cloud agent will know that if it alters the settings in one of those files it must update the other file accordingly.

## Benefits of using Copilot Memory

AI that is stateless and doesn't retain an understanding of a codebase between separate human/AI interactions, requires you either to repeatedly explain coding conventions and important details about specific code in your prompts, or to create detailed custom instructions files, which you must then maintain.

Copilot Memory:

* Reduces the burden of repeatedly providing the same details in your prompts.
* Reduces the need for regular, manual maintenance of custom instruction files.

By building and maintaining a persistent, repository-level memory, Copilot develops its own knowledge of your codebase, adapts to your coding requirements, and increases the value it can deliver over time.

## Where is Copilot Memory used?

Currently Copilot Memory is used by Copilot cloud agent and Copilot code review when these features are working on pull requests on the GitHub website, and by Copilot CLI. Memories are only created and used by Copilot when Copilot Memory has been enabled for the user initiating the Copilot operation.

Agentic memory will be extended to other parts of Copilot, and for personal and organizational scopes, in future releases.

## How memories are stored, retained and used

Each memory that Copilot generates is stored with citations. These are references to specific code locations that support the memory. When Copilot finds a memory that relates to the work it is doing, it checks the citations against the current codebase to validate that the information is still accurate and is relevant to the current branch. The memory is only used if it is successfully validated.

To avoid stale memories being retained, resulting in outdated information adversely affecting Copilot's decision making, memories are automatically deleted after 28 days.

If a memory is validated and used by Copilot, then a new memory with the same details may be stored, which increases the longevity of that memory.

Memories can be created from code in pull requests that were closed without being merged. However, the validation mechanism ensures that such memories will not affect Copilot's behavior if there is no substantiating evidence in the current codebase.

Copilot only creates memories in a repository in response to actions taken within that repository by people who have write permission for the repository, and for whom Copilot Memory has been enabled. Memories are repository scoped, not user scoped, so all memories stored for a repository are available for use in Copilot operations initiated by any user who has access to Copilot Memory for that repository. The memories stored for a repository can only be used in Copilot operations on that same repository. In this way, what Copilot learns about a repository stays within that repository, ensuring privacy and security.

If you are the owner of a repository where Copilot Memory is being used, you can review and manually delete the memories for that repository. See [Managing and curating Copilot Memory](/en/copilot/how-tos/use-copilot-agents/copilot-memory).

## About enabling Copilot Memory

The ability to use Copilot Memory is granted to users, rather than being enabled for repositories. After Copilot Memory has been enabled for a user, Copilot will be able to use agentic memory in any repository in which that person uses GitHub Copilot.

For users who have an individual Copilot subscription to a Copilot Pro or Copilot Pro+ plan, Copilot Memory is enabled by default. These users can disable Copilot Memory in their personal Copilot settings on GitHub.

For enterprise and organization-managed Copilot subscriptions, Copilot Memory is turned off by default and can be enabled in the enterprise or organization settings. When enabled at the enterprise or organization level, Copilot Memory will be available to all organization members who receive a Copilot subscription from that organization.

For more information, see [Managing and curating Copilot Memory](/en/copilot/how-tos/use-copilot-agents/copilot-memory).