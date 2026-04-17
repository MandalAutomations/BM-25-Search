# Asking GitHub Copilot to create a pull request

You can ask Copilot to create a pull request from many places, including GitHub Issues, the agents panel, Copilot Chat, the GitHub CLI, and agentic coding tools and IDEs with Model Context Protocol (MCP) support.

> \[!NOTE]
> For an overview of Copilot cloud agent, see [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent).

## Introduction

You can ask Copilot to create a new pull request from:

* GitHub Issues, by [assigning an issue to Copilot](#assigning-an-issue-to-copilot)
* The [agents tab or panel](#asking-copilot-to-create-a-pull-request-from-the-agents-tab-or-panel) on GitHub
* The [dashboard](#asking-copilot-to-create-a-pull-request-from-the-dashboard) on GitHub
* Copilot Chat in [Visual Studio Code](#asking-copilot-to-create-a-pull-request-from-copilot-chat-in-visual-studio-code), [JetBrains IDEs](#asking-copilot-to-create-a-pull-request-from-copilot-chat-in-jetbrains-ides), [Eclipse](#asking-copilot-to-create-a-pull-request-from-copilot-chat-in-eclipse) and [Visual Studio 2026](#asking-copilot-to-create-a-pull-request-from-copilot-chat-in-visual-studio-2026)
* Copilot Chat on [GitHub.com](#asking-copilot-to-create-a-pull-request-from-copilot-chat-in-githubcom)
* The [GitHub CLI](#asking-copilot-to-create-a-pull-request-from-the-github-cli)
* On [GitHub Mobile](#asking-copilot-to-create-a-pull-request-from-github-mobile)
* Your preferred IDE or agentic coding tool with [Model Context Protocol (MCP)](#asking-copilot-to-create-a-pull-request-from-the-github-mcp-server) support
* The [Raycast](#asking-copilot-to-create-a-pull-request-from-raycast) launcher
* The ["New repository" form](#asking-copilot-to-create-a-pull-request-from-the-new-repository-page) on GitHub

Copilot will start working on the task, raise a pull request, then request a review from you when it's finished working. For more information, see [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent).

## Assigning an issue to Copilot

You can ask Copilot to start working on an issue by assigning the issue to Copilot.

You can assign an issue to Copilot:

* On GitHub.com (see the [next section](#assigning-an-issue-to-copilot-on-githubcom))
* On [GitHub Mobile](#assigning-an-issue-to-copilot-on-github-mobile)
* Via the GitHub API (see [later in this article](#assigning-an-issue-to-copilot-via-the-github-api))
* Using the [Raycast launcher](#assigning-an-issue-to-copilot-from-raycast)
* Using GitHub CLI (see [`gh issue edit`](https://cli.github.com/manual/gh_issue_edit))

### Assigning an issue to Copilot on GitHub.com

> \[!NOTE]
> This feature is in public preview and subject to change.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Issues," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-issues-global-nav-update.png)

3. Open the issue that you want to assign to Copilot.

4. In the right side menu, click **Assignees**.

   ![Screenshot of the right sidebar of an issue. A header, labeled "Assignees", is outlined in dark orange.](/assets/images/help/issues/assignee-menu.png)

5. Click **Copilot** from assignees list.

   ![Screenshot of "Assignees" window on an issue. Copilot is available in the list.](/assets/images/help/copilot/cloud-agent/assign-to-copilot.png)

   Additional options are displayed.

   ![Screenshot of "Assign to Copilot" dialog showing options for target repository, starting branch, custom agent, and additional instructions.](/assets/images/help/copilot/cloud-agent/assign-to-copilot-dialog.png)

6. In the **Optional prompt** field you can add specific guidance for Copilot. Add any context, constraints, or specific requirements that will help Copilot to understand and complete the task.

   For example, you might include instructions about specific coding patterns or frameworks to use, testing requirements, code style preferences, files or directories that should or shouldn't be modified.

   In addition to the details you supply here, Copilot will use any custom instructions that have been configured for the target repository. See [Adding repository custom instructions for GitHub Copilot](/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions).

7. You can use the dropdown menus in the dialog to change the repository that Copilot will work in and the branch that it will branch off from.

   All repositories where you have **at least** read access will be displayed in the repository dropdown menu. However, you can only select a repository if you have write access to it, **and** if Copilot cloud agent is enabled for that repository.

   If you select a repository in a different organization than the issue's source organization, or if you select a public repository when the issue is in a private repository, a warning will be displayed.

   If you don't specify a repository, Copilot will work in the same repository as the issue. If you don't specify a branch, Copilot will work from the default branch of the selected repository.

   > \[!TIP]
   > When you assign an issue to Copilot, it gets sent the issue title, description, any comments that currently exist, and any additional instructions you provide. After assigning the issue, Copilot will not be aware of, and therefore won't react to, any further comments that are added to the issue. If you have more information, or changes to the original requirement, add this as a comment in the pull request that Copilot raises.

8. Optionally, you can click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> to open the agent dropdown menu, if you want to assign an agent or a custom agent with specialized behavior and tools. You can select an existing custom agent from your repository, organization, or enterprise. You can also click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Plus button" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create an agent** to create a new agent profile in your selected repository and branch. For more information, see [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents).
   > \[!NOTE] Third-party coding agents are available in the GitHub Copilot Pro+ and Copilot Enterprise plans.

9. Optionally, if you are a GitHub Copilot Pro or GitHub Copilot Pro+ user, you can use the dropdown menu to select the model that Copilot will use. For more information, see [Changing the AI model for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/changing-the-ai-model).

You can also assign issues to Copilot from other places on GitHub.com:

* From the list of issues on a repository's **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues** page.
* When viewing an issue in GitHub Projects.

### Assigning an issue to Copilot on GitHub Mobile

1. In GitHub Mobile, navigate to the repository that contains the issue you want to assign to Copilot.
2. Click **Issues**.
3. Open the issue that you want to assign to Copilot.
4. Tap the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-info" aria-label="information" role="img"><path d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8Zm8-6.5a6.5 6.5 0 1 0 0 13 6.5 6.5 0 0 0 0-13ZM6.5 7.75A.75.75 0 0 1 7.25 7h1a.75.75 0 0 1 .75.75v2.75h.25a.75.75 0 0 1 0 1.5h-2a.75.75 0 0 1 0-1.5h.25v-2h-.25a.75.75 0 0 1-.75-.75ZM8 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg>** icon.
5. Beside "Assignees", tap **Edit**.
6. Beside "Copilot", click the plus sign.
7. Click **Done**.

### Assigning an issue to Copilot via the GitHub API

> \[!NOTE]
> This feature is in public preview and subject to change.

You can assign issues to Copilot using either the GraphQL API or the REST API. Both APIs support an optional Agent Assignment input to customize the task:

| GraphQL parameter    | REST parameter        | Description                              |
| -------------------- | --------------------- | ---------------------------------------- |
| `targetRepositoryId` | `target_repo`         | The repository where Copilot will work   |
| `baseRef`            | `base_branch`         | The branch that Copilot will branch from |
| `customInstructions` | `custom_instructions` | Additional instructions for Copilot      |
| `customAgent`        | `custom_agent`        | A custom agent to use for the task       |
| `model`              | `model`               | The model for Copilot to use             |

#### Using the GraphQL API

> \[!NOTE]
> You must include the `GraphQL-Features` header with the values `issues_copilot_assignment_api_support` and `coding_agent_model_selection`.

You can use the following GraphQL mutations to assign issues to Copilot:

* [`updateIssue`](/en/graphql/reference/mutations#updateissue)
* [`createIssue`](/en/graphql/reference/mutations#createissue)
* [`addAssigneesToAssignable`](/en/graphql/reference/mutations#addassigneestoassignable)
* [`replaceActorsForAssignable`](/en/graphql/reference/mutations#replaceactorsforassignable)

##### Creating and assigning a new issue

1. Make sure you're authenticating with the API using a user token, for example a personal access token or a GitHub App user-to-server token.

   > \[!NOTE]
   > If using a fine-grained personal access token, it needs the following permissions to assign Copilot to an issue:
   >
   > * Read access to metadata
   > * Read and write access to actions, contents, issues and pull requests
   >
   > If using a personal access token (classic), it needs the `repo` scope to assign Copilot to an issue.

2. Verify that Copilot cloud agent is enabled in the repository by checking if the repository's `suggestedActors` in the GraphQL API includes Copilot. Replace `octo-org` with the repository owner, and `octo-repo` with the repository name.

   ```graphql copy
   query {
     repository(owner: "octo-org", name: "octo-repo") {
       suggestedActors(capabilities: [CAN_BE_ASSIGNED], first: 100) {
         nodes {
           login
           __typename

           ... on Bot {
             id
           }

           ... on User {
             id
           }
         }
       }
     }
   }
   ```

   If Copilot cloud agent is enabled for the user and in the repository, the first node returned from the query will have the `login` value `copilot-swe-agent`.

3. Make a note of the `id` value of this login.

4. Fetch the GraphQL global ID of the repository you want to create the issue in, replacing `octo-org` with the repository owner, and `octo-repo` with the repository name.

   ```graphql copy
   query {
     repository(owner: "octo-org", name: "octo-repo") {
       id
     }
   }
   ```

5. Create the issue with the `createIssue` mutation. Replace `REPOSITORY_ID` with the ID returned from the previous step, and `BOT_ID` with the ID returned from the step before that. You can optionally include the `agentAssignment` input to customize the task.

   ```shell copy
   gh api graphql -f query='mutation {
     createIssue(input: {
       repositoryId: "REPOSITORY_ID",
       title: "Implement comprehensive unit tests",
       body: "DETAILS",
       assigneeIds: ["BOT_ID"],
       agentAssignment: {
         targetRepositoryId: "REPOSITORY_ID",
         baseRef: "main",
         customInstructions: "Add comprehensive test coverage",
         customAgent: "",
         model: ""
       }
     }) {
       issue {
         id
         title
         assignees(first: 10) {
           nodes {
             login
           }
         }
       }
     }
   }' -H 'GraphQL-Features: issues_copilot_assignment_api_support,coding_agent_model_selection'
   ```

##### Assigning an existing issue

1. Make sure you're authenticating with the API using a user token, for example a personal access token or a GitHub App user-to-server token.

2. Verify that Copilot cloud agent is enabled in the repository by checking if the repository's `suggestedActors` in the GraphQL API includes Copilot. Replace `octo-org` with the repository owner, and `octo-repo` with the repository name.

   ```graphql copy
   query {
     repository(owner: "monalisa", name: "octocat") {
       suggestedActors(capabilities: [CAN_BE_ASSIGNED], first: 100) {
         nodes {
           login
           __typename

           ... on Bot {
             id
           }

           ... on User {
             id
           }
         }
       }
     }
   }
   ```

   If Copilot cloud agent is enabled for the user and in the repository, the first node returned from the query will have the `login` value `copilot-swe-agent`.

3. Fetch the GraphQL global ID of the issue you want to assign to Copilot, replacing `monalisa` with the repository owner, `octocat` with the name and `9000` with the issue number.

   ```graphql copy
   query {
     repository(owner: "monalisa", name: "octocat") {
       issue(number: 9000) {
         id
         title
       }
     }
   }
   ```

4. Assign the existing issue to Copilot using the `replaceActorsForAssignable` mutation. Replace `ISSUE_ID` with the ID returned from the previous step, `BOT_ID` with the ID returned from the step before that, and `REPOSITORY_ID` with the repository ID. You can optionally include the `agentAssignment` input to customize the task.

   ```shell copy
   gh api graphql -f query='mutation {
     replaceActorsForAssignable(input: {
       assignableId: "ISSUE_ID",
       actorIds: ["BOT_ID"],
       agentAssignment: {
         targetRepositoryId: "REPOSITORY_ID",
         baseRef: "main",
         customInstructions: "Fix the reported bug",
         customAgent: "",
         model: ""
       }
     }) {
       assignable {
         ... on Issue {
           id
           title
           assignees(first: 10) {
             nodes {
               login
             }
           }
         }
       }
     }
   }' -H 'GraphQL-Features: issues_copilot_assignment_api_support,coding_agent_model_selection'
   ```

5. Alternatively, you can use the `updateIssue` mutation to update an existing issue and assign it to Copilot. Replace `ISSUE_ID` with the issue ID and `BOT_ID` with the bot ID.

   ```shell copy
   gh api graphql -f query='mutation {
     updateIssue(input: {
       id: "ISSUE_ID",
       assigneeIds: ["BOT_ID"],
       agentAssignment: {
         targetRepositoryId: "REPOSITORY_ID",
         baseRef: "main",
         customInstructions: "Update feature implementation",
         customAgent: "",
         model: ""
       }
     }) {
       issue {
         id
         title
         assignees(first: 10) {
           nodes {
             login
           }
         }
       }
     }
   }' -H 'GraphQL-Features: issues_copilot_assignment_api_support,coding_agent_model_selection'
   ```

6. You can also use the `addAssigneesToAssignable` mutation to add Copilot to an existing issue while keeping other assignees. Replace `ISSUE_ID` with the issue ID and `BOT_ID` with the bot ID.

   ```shell copy
   gh api graphql -f query='mutation {
     addAssigneesToAssignable(input: {
       assignableId: "ISSUE_ID",
       assigneeIds: ["BOT_ID"],
       agentAssignment: {
         targetRepositoryId: "REPOSITORY_ID",
         baseRef: "main",
         customInstructions: "Collaborate on this task",
         customAgent: "",
         model: ""
       }
     }) {
       assignable {
         ... on Issue {
           id
           title
           assignees(first: 10) {
             nodes {
               login
             }
           }
         }
       }
     }
   }' -H 'GraphQL-Features: issues_copilot_assignment_api_support,coding_agent_model_selection'
   ```

#### Using the REST API

You can use the following REST API endpoints to assign issues to Copilot:

* [Add assignees to an issue](/en/rest/issues/assignees#add-assignees-to-an-issue)
* [Create an issue](/en/rest/issues/issues#create-an-issue)
* [Update an issue](/en/rest/issues/issues#update-an-issue)

##### Adding assignees to an existing issue

```shell copy
gh api \
  --method POST \
  -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  /repos/OWNER/REPO/issues/ISSUE_NUMBER/assignees \
  --input - <<< '{
  "assignees": ["copilot-swe-agent[bot]"],
  "agent_assignment": {
    "target_repo": "OWNER/REPO",
    "base_branch": "main",
    "custom_instructions": "",
    "custom_agent": "",
    "model": ""
  }
}'
```

##### Creating a new issue

```shell copy
gh api \
  --method POST \
  -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  /repos/OWNER/REPO/issues \
  --input - <<< '{
  "title": "Issue title",
  "body": "Issue description.",
  "assignees": ["copilot-swe-agent[bot]"],
  "agent_assignment": {
    "target_repo": "OWNER/REPO",
    "base_branch": "main",
    "custom_instructions": "",
    "custom_agent": "",
    "model": ""
  }
}'
```

##### Updating an existing issue

```shell copy
gh api \
  --method PATCH \
  -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  /repos/OWNER/REPO/issues/ISSUE_NUMBER \
  --input - <<< '{
  "assignees": ["copilot-swe-agent[bot]"],
  "agent_assignment": {
    "target_repo": "OWNER/REPO",
    "base_branch": "main",
    "custom_instructions": "",
    "custom_agent": "",
    "model": ""
  }
}'
```

### Assigning an issue to Copilot from Raycast

[Raycast](https://www.raycast.com/) is an extensible launcher for Windows and macOS. With the GitHub Copilot extension for Raycast, you can start and track Copilot cloud agent tasks and watch session logs live wherever you are on your computer.

1. Install Raycast from the [Raycast website](https://www.raycast.com).
2. Install the GitHub Copilot extension for Raycast by clicking the **Install Extension** button on the [extension's page](https://www.raycast.com/github/github-copilot).
3. Open Raycast, search for "Copilot," find the **Assign Issues to Copilot** command, then press <kbd>Enter</kbd>.
4. Click **Sign in with GitHub**, then complete the authentication flow. Raycast will re-open.
5. Select the repository you want Copilot to work in.
6. Select the issue you want to assign to Copilot.
7. Optionally, select a base branch for Copilot's pull request. Copilot will create a new branch based on this branch, then push the changes to a pull request targeting that branch.
8. Optionally, select a custom agent with specialized behavior and tools from the dropdown menu. For more information, see [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents).
9. Optionally, if you are a GitHub Copilot Pro or GitHub Copilot Pro+ user, you can use the dropdown menu to select the model that Copilot will use. For more information, see [Changing the AI model for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/changing-the-ai-model).
10. Optionally, provide additional instructions. These will be passed to Copilot alongside your issue contents.
11. Press <kbd>Command</kbd>+<kbd>Enter</kbd> (macOS) or <kbd>Ctrl</kbd>+<kbd>Enter</kbd> (Windows) to assign the issue.

    Copilot will start a new session. Copilot will work on the task and push changes to its pull request, then add you as a reviewer when it has finished, triggering a notification.

> \[!NOTE]
>
> If you are unable to select a specific repository when starting a task, the organization that owns the repository may have enabled OAuth app access restrictions. To learn how to request approval for the "GitHub Copilot for Raycast" OAuth app, see [Requesting organization approval for OAuth apps](/en/account-and-profile/how-tos/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/requesting-organization-approval-for-oauth-apps).

## Asking Copilot to create a pull request from the agents tab or panel

You can ask Copilot to open a pull request from either the agents tab or the agents panel. The only difference is the entry point - once you see the "New agent task" form, the steps are the same.

1. Open the agents panel or tab:

   * Open the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> Agents** tab in a repository.
   * **Navigate to the agents page**: Go to [github.com/copilot/agents](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text). You can also get here by opening the agents panel, then clicking **View all**.
   * **Open the agents panel**: Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> in the navigation bar at the top right of GitHub.

2. Using the dropdown menu in the prompt field, select the repository you want Copilot to work in.

3. Type a prompt describing your request. You can also add visual inputs like screenshots or UI mockups by pasting, dragging, or uploading an image. Files supported: image/png, image/jpeg, image/gif, image/webp.

   For example, `Create a pull request to implement a user friendly message for common errors.`

4. Optionally, select a base branch for Copilot's pull request. Copilot will create a new branch based on this branch, then push the changes to a pull request targeting that branch.

5. Optionally, you can click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> to open the agent dropdown menu, if you want to assign an agent or a custom agent with specialized behavior and tools. You can select an existing custom agent from your repository, organization, or enterprise. You can also click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Plus button" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create an agent** to create a new agent profile in your selected repository and branch. For more information, see [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents).
   > \[!NOTE] Third-party coding agents are available in the GitHub Copilot Pro+ and Copilot Enterprise plans.

6. Optionally, if you are a GitHub Copilot Pro or GitHub Copilot Pro+ user, you can use the dropdown menu to select the model that Copilot will use. For more information, see [Changing the AI model for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/changing-the-ai-model).

7. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-paper-airplane" aria-label="Start task" role="img"><path d="M.989 8 .064 2.68a1.342 1.342 0 0 1 1.85-1.462l13.402 5.744a1.13 1.13 0 0 1 0 2.076L1.913 14.782a1.343 1.343 0 0 1-1.85-1.463L.99 8Zm.603-5.288L2.38 7.25h4.87a.75.75 0 0 1 0 1.5H2.38l-.788 4.538L13.929 8Z"></path></svg>** or press <kbd>Enter</kbd>.

   Copilot will start a new session, which will appear in the list below the prompt box. Copilot will work on the task and push changes to its pull request, then add you as a reviewer when it has finished, triggering a notification.

## Asking Copilot to create a pull request from the dashboard

You can ask Copilot to open a pull request from the Copilot prompt box in the dashboard. The dashboard is your personalized overview of your activity on GitHub, seen when you visit <https://github.com> while logged in.

1. Navigate to the dashboard at [https://github.com](https://github.com/?ref_product=desktop\&ref_type=engagement\&ref_style=text).

2. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> Task** button.

3. Using the dropdown menu in the prompt field, select the repository you want Copilot to work in.

4. Type a prompt describing your request.

   For example, `Create a pull request to implement a user friendly message for common errors.`

5. Optionally, select a base branch for Copilot's pull request. Copilot will create a new branch based on this branch, then push the changes to a pull request.

6. Optionally, you can click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> to open the agent dropdown menu, if you want to assign an agent or a custom agent with specialized behavior and tools. You can select an existing custom agent from your repository, organization, or enterprise. You can also click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Plus button" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create an agent** to create a new agent profile in your selected repository and branch. For more information, see [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents).
   > \[!NOTE] Third-party coding agents are available in the GitHub Copilot Pro+ and Copilot Enterprise plans.

7. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-paper-airplane" aria-label="Send now" role="img"><path d="M.989 8 .064 2.68a1.342 1.342 0 0 1 1.85-1.462l13.402 5.744a1.13 1.13 0 0 1 0 2.076L1.913 14.782a1.343 1.343 0 0 1-1.85-1.463L.99 8Zm.603-5.288L2.38 7.25h4.87a.75.75 0 0 1 0 1.5H2.38l-.788 4.538L13.929 8Z"></path></svg> Send now** or press <kbd>Return</kbd>.

   You will be taken to the agents tab, and Copilot will start a new session, which will appear in the "Recent sessions" list below the prompt box. Copilot will work on the task and push changes to its pull request, then add you as a reviewer when it has finished, triggering a notification.

   > \[!NOTE]
   > If you have enabled the **New Dashboard Experience** in feature preview, the new session will appear in "Agent sessions" under the prompt box in your dashboard. For more information, see [Personal dashboard](/en/account-and-profile/reference/personal-dashboard#home-dashboard-view).

## Asking Copilot to create a pull request from Copilot Chat in Visual Studio Code

1. Install the [GitHub Pull Requests extension](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github) for Visual Studio Code.

2. Open GitHub Copilot Chat in Visual Studio Code.

3. Type a prompt explaining what you want Copilot to do.

   For example, `Put backticks around file names and variables in output`

   > \[!TIP]
   > To help Copilot, you can select the relevant line(s) of code before submitting your prompt.

4. Submit your prompt by clicking the <svg class="octicon" width="16" height="16" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg" fill="currentColor"><path d="M15.724 11.053V11.948L7.724 15.948L7.026 15.343L8.14 12.001H13V11.001H8.14L7.026 7.659L7.724 7.054L15.724 11.053ZM1 8C1 6.46 2.15 5.18 3.67 5.02L4.02 4.98L4.11 4.64C4.5 3.09 5.89 2 7.5 2C9.43 2 11 3.57 11 5.5V6H11.5C12.88 6 14 7.12 14 8.5V8.52L14.95 8.99C14.98 8.83 15 8.67 15 8.5C15 6.73 13.68 5.26 11.98 5.03C11.74 2.77 9.82 1 7.5 1C5.55 1 3.84 2.25 3.23 4.07C1.37 4.43 0 6.07 0 8C0 10.21 1.79 12 4 12H7V11H4C2.35 11 1 9.65 1 8Z"/></svg> **Delegate this task to the GitHub Copilot cloud agent** button, next to the <svg class="octicon" width="16" height="16" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg" fill="currentColor"><path d="M1 1.91L1.78 1.5L15 7.44899V8.3999L1.78 14.33L1 13.91L2.58311 8L1 1.91ZM3.6118 8.5L2.33037 13.1295L13.5 7.8999L2.33037 2.83859L3.6118 7.43874L9 7.5V8.5H3.6118Z"/></svg> **Send** button

5. If you have local changes, a dialog will be displayed asking if you want to push those changes so Copilot can start from your current state. Click **Include changes** to push your changes, or **Ignore changes** to ask Copilot to start its work from your repository's default branch.

   Copilot will start a new session and respond with a link to the pull request it creates. It will work on the task and push changes to the pull request, and then add you as a reviewer when it has finished, triggering a notification.

## Asking Copilot to create a pull request from Copilot Chat in JetBrains IDEs

> \[!NOTE]
> Copilot cloud agent in JetBrains IDEs is in public preview, and subject to change.

1. Open GitHub Copilot Chat in your JetBrains IDE.

2. Type a prompt explaining what you want Copilot to do

   For example, `Put backticks around file names and variables in output`

3. Click the **Delegate to Cloud Agent** button next to the **Send** button.

   Copilot will start a new session and respond with a link to the pull request it creates. It will work on the task and push changes to the pull request, and then add you as a reviewer when it has finished, triggering a notification from GitHub and in the IDE.

## Asking Copilot to create a pull request from Copilot Chat in Eclipse

> \[!NOTE]
> Copilot cloud agent in Eclipse is in public preview, and subject to change.

1. Open GitHub Copilot Chat in Eclipse.

2. Type a prompt explaining what you want Copilot to do.

   For example, `Put backticks around file names and variables in output`

3. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg>** next to the **Send** button.

4. In the dialog box that opens, select the repository you want Copilot to work in, then click **Continue**.

   Copilot will start a new session and respond with a link to the pull request it creates. It will work on the task and push changes to the pull request, and then add you as a reviewer when it has finished, triggering a notification from GitHub and in the IDE.

## Asking Copilot to create a pull request from Copilot Chat in Visual Studio 2026

> \[!NOTE] To use Copilot cloud agent in Visual Studio, you'll need to be running at least [December Update 18.1.0](https://learn.microsoft.com/en-us/visualstudio/releases/2026/release-notes#github-copilot-1) of Visual Studio 2026.

1. Enable Copilot cloud agent support in Visual Studio.
   1. Open the **Tools** menu, then click **Options**.
   2. In the sidebar, select **GitHub**.
   3. Check the **Enable Copilot Cloud agent (preview)** box.
   4. Restart Visual Studio.

2. Open GitHub Copilot Chat in Visual Studio.

3. Enter a prompt, giving details of what you want Copilot to change.

   For example, `Put backticks around file names and variables in log output.`

4. Submit your prompt by clicking the <svg class="octicon" width="16" height="16" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg" fill="currentColor"><path d="M15.724 11.053V11.948L7.724 15.948L7.026 15.343L8.14 12.001H13V11.001H8.14L7.026 7.659L7.724 7.054L15.724 11.053ZM1 8C1 6.46 2.15 5.18 3.67 5.02L4.02 4.98L4.11 4.64C4.5 3.09 5.89 2 7.5 2C9.43 2 11 3.57 11 5.5V6H11.5C12.88 6 14 7.12 14 8.5V8.52L14.95 8.99C14.98 8.83 15 8.67 15 8.5C15 6.73 13.68 5.26 11.98 5.03C11.74 2.77 9.82 1 7.5 1C5.55 1 3.84 2.25 3.23 4.07C1.37 4.43 0 6.07 0 8C0 10.21 1.79 12 4 12H7V11H4C2.35 11 1 9.65 1 8Z"/></svg> **Delegate this task to the GitHub Copilot cloud agent** button, next to the <svg class="octicon" width="16" height="16" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg" fill="currentColor"><path d="M1 1.91L1.78 1.5L15 7.44899V8.3999L1.78 14.33L1 13.91L2.58311 8L1 1.91ZM3.6118 8.5L2.33037 13.1295L13.5 7.8999L2.33037 2.83859L3.6118 7.43874L9 7.5V8.5H3.6118Z"/></svg> **Send** button.

   Copilot asks you to confirm that you want to use the cloud agent to create a pull request.

5. Click **Confirm**.

   Copilot will start a new session and respond with a link to the pull request it creates. It will work on the task and push changes to the pull request, and then add you as a reviewer when it has finished, triggering a notification.

## Asking Copilot to create a pull request from Copilot Chat in GitHub.com

1. Open GitHub Copilot Chat on GitHub.com.

2. Type `/task` to ask Copilot to create a pull request, and give details of what you want Copilot to change.

   For example, `/task Create a pull request to put backticks around file names and variables in output.`

3. Optionally, select a base branch for Copilot's pull request. Copilot will create a new branch based on this branch, then push the changes to a pull request targeting that branch.

4. Optionally, you can click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> to open the agent dropdown menu, if you want to assign an agent or a custom agent with specialized behavior and tools. You can select an existing custom agent from your repository, organization, or enterprise. You can also click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Plus button" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create an agent** to create a new agent profile in your selected repository and branch. For more information, see [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents).
   > \[!NOTE] Third-party coding agents are available in the GitHub Copilot Pro+ and Copilot Enterprise plans.

5. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-paper-airplane" aria-label="Start task" role="img"><path d="M.989 8 .064 2.68a1.342 1.342 0 0 1 1.85-1.462l13.402 5.744a1.13 1.13 0 0 1 0 2.076L1.913 14.782a1.343 1.343 0 0 1-1.85-1.463L.99 8Zm.603-5.288L2.38 7.25h4.87a.75.75 0 0 1 0 1.5H2.38l-.788 4.538L13.929 8Z"></path></svg>** or press <kbd>Enter</kbd>.

   Copilot will start a new session, which will appear in the list below the prompt box. Copilot will work on the task and push changes to its pull request, then add you as a reviewer when it has finished, triggering a notification.

## Asking Copilot to create a pull request from GitHub Mobile

1. In GitHub Mobile, navigate to the repository where you want to create a pull request.

2. Tap the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>** icon in the bottom right corner of the screen.

3. Enter a prompt to ask Copilot to create a pull request.

   For example: `Create a pull request to ...`.

   Copilot responds with a brief summary of the task it will perform, asking for your confirmation before it proceeds.

4. Check that Copilot has interpreted your prompt correctly, then tap **Accept** or **Dismiss**.

   Copilot creates a pull request and gives you a link to it. It will work on the task and push changes to the pull request, and then add you as a reviewer when it has finished, triggering a notification.

## Asking Copilot to create a pull request from the GitHub CLI

> \[!NOTE]
> The `agent-task` command set is only available in v2.80.0 or later of the GitHub CLI. This command set is a public preview and is subject to change.

You can start a new Copilot cloud agent session with the `gh agent-task create` command in the GitHub CLI.

When you run the command without any arguments, you are asked to enter a prompt. Copilot cloud agent acts on the prompt and opens a pull request in the current repository.

You can use command line options to:

* Provide the prompt (`gh agent-task create "Example prompt"`)
* Choose a base branch, instead of using the repository's default branch (`--base`)
* Select a repository, instead of targeting the current repository (`--repo`)
* Follow the session log in real time (`--follow`)

To see all of the available options, run `gh agent-task create --help`.

## Asking Copilot to create a pull request from the GitHub MCP server

> \[!NOTE]
>
> * This capability is only available on the remote GitHub MCP server and host applications where remote MCP servers are supported.

1. Install the GitHub MCP server in your preferred IDE or agentic coding tool. See [Using the GitHub MCP Server in your IDE](/en/copilot/how-tos/context/model-context-protocol/using-the-github-mcp-server).

2. Ensure the `create_pull_request_with_copilot` tool is enabled.

3. Open chat.

4. Type a prompt asking Copilot to create a pull request, with the details of what you want to change.

   For example, `Open a PR in my repository to expand unit test coverage.`

   > \[!TIP]
   >
   > * You can ask Copilot to open a pull request using a specific branch as the base branch by including it in your prompt.

5. Submit your prompt.

   Copilot will start a new session, open a draft pull request and work on the task in the background. As it works, it will push changes to the pull request, and once it has finished, it will add you as a reviewer. In most cases, the MCP host will show you the URL of the created pull request.

## Asking Copilot to create a pull request from Raycast

[Raycast](https://www.raycast.com/) is an extensible launcher for Windows and macOS. With the GitHub Copilot extension for Raycast, you can start and track Copilot cloud agent tasks and watch session logs live wherever you are on your computer.

1. Install Raycast from the [Raycast website](https://www.raycast.com).
2. Install the GitHub Copilot extension for Raycast by clicking the **Install Extension** button on the [extension's page](https://www.raycast.com/github/github-copilot).
3. Open Raycast, search for "Copilot," find the **Create Task** command, then press <kbd>Enter</kbd>.
4. Click **Sign in with GitHub**, then complete the authentication flow. Raycast will re-open.
5. Type a prompt describing what you want Copilot to do.

   For example, `Implement a user friendly message for common errors.`
6. Select the repository you want Copilot to work in.
7. Optionally, select a base branch for Copilot's pull request. Copilot will create a new branch based on this branch, then push the changes to a pull request targeting that branch.
8. Optionally, select a custom agent with specialized behavior and tools from the dropdown menu. For more information, see [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents).
9. Optionally, if you are a GitHub Copilot Pro or GitHub Copilot Pro+ user, you can use the dropdown menu to select the model that Copilot will use. For more information, see [Changing the AI model for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/changing-the-ai-model).
10. Press <kbd>Command</kbd>+<kbd>Enter</kbd> (macOS) or <kbd>Ctrl</kbd>+<kbd>Enter</kbd> (Windows) to start the task.

    Copilot will start a new session. Copilot will work on the task and push changes to its pull request, then add you as a reviewer when it has finished, triggering a notification.

> \[!NOTE]
>
> If you are unable to select a specific repository when starting a task, the organization that owns the repository may have enabled OAuth app access restrictions. To learn how to request approval for the "GitHub Copilot for Raycast" OAuth app, see [Requesting organization approval for OAuth apps](/en/account-and-profile/how-tos/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/requesting-organization-approval-for-oauth-apps).

## Asking Copilot to create a pull request from the "New repository" page

When creating a new repository, you can ask Copilot to seed the new repository by entering a prompt.

1. In the upper-right corner of any page, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Create something new" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>, then click **New repository**.

   ![Screenshot of a GitHub dropdown menu showing options to create new items. The menu item "New repository" is outlined in dark orange.](/assets/images/help/repository/repo-create-global-nav-update.png)
2. Use the **Owner** dropdown menu to select the account you want to own the repository.
   ![Screenshot of the owner menu for a new GitHub repository. The menu shows two options, octocat and github.](/assets/images/help/repository/create-repository-owner.png)
3. In the **Prompt** field, enter a prompt describing what you want Copilot to build.

   For example, `Create a Rust CLI for converting CSV spreadsheets to Markdown`
4. Click **Create repository**.

   Copilot will immediately open a draft pull request. Copilot will work on the task and push changes to its pull request, then add you as a reviewer when it has finished, triggering a notification.

## Monitoring progress

You can view your current and past Copilot sessions from the agents panel, [agents page](https://github.com/copilot/agents), Visual Studio Code, and more. See [Tracking GitHub Copilot's sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/track-copilot-sessions).

## Further reading

* [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent)
* [Best practices for using GitHub Copilot to work on tasks](/en/copilot/tutorials/cloud-agent/get-the-best-results)
* [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents)
* [Troubleshooting GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/troubleshoot-cloud-agent#copilot-cant-create-a-pull-request-from-copilot-chat)