# Communicating on GitHub

You can discuss specific projects and changes, as well as broader ideas or team goals, using different types of discussions on GitHub.

## Introduction

GitHub provides built-in collaborative communication tools allowing you to interact closely with your community. This quickstart guide will show you how to pick the right tool for your needs.

You can create and participate in issues, pull requests, and team discussions, depending on the type of conversation you'd like to have.

> \[!TIP] You can also use Copilot Chat to generate ideas, outlines, or drafts for discussions, based on your pull requests and issues. See [Writing discussions or blog posts](/en/copilot/copilot-chat-cookbook/documenting-code/writing-discussions-or-blog-posts).

### GitHub Issues

* Are useful for discussing specific details of a project such as bug reports, planned improvements and feedback
* Are specific to a repository, and usually have a clear owner
* Are often referred to as GitHub's bug-tracking system

### Pull requests

* Allow you to propose specific changes
* Allow you to comment directly on proposed changes suggested by others
* Are specific to a repository

### GitHub Discussions

* Are like a forum, and are best used for open-form ideas and discussions where collaboration is important
* May span many repositories
* Provide a collaborative experience outside the codebase, allowing the brainstorming of ideas, and the creation of a community knowledge base
* Often don’t have a clear owner
* Often do not result in an actionable task

## Which discussion tool should I use?

### Scenarios for issues

* I want to keep track of tasks, enhancements and bugs.
* I want to file a bug report.
* I want to share feedback about a specific feature.
* I want to ask a question about files in the repository.

#### Issue example

This example illustrates how a GitHub user created an issue in our documentation open source repository to make us aware of a bug, and discuss a fix.

![Screenshot of an issue, with the title "Blue link text in notices is unreadable due to blue background."](/assets/images/help/issues/issue-example.png)

* A user noticed that the blue color of the banner at the top of the page in the Chinese version of the GitHub Docs makes the text in the banner unreadable.
* The user created an issue in the repository, stating the problem and suggesting a fix (which is, use a different background color for the banner).
* A discussion ensues, and eventually, a consensus will be reached about the fix to apply.
* A contributor can then create a pull request with the fix.

### Scenarios for pull requests

* I want to fix a typo in a repository.
* I want to make changes to a repository.
* I want to make changes to fix an issue.
* I want to comment on changes suggested by others.

#### Pull request example

This example illustrates how a GitHub user created a pull request in our documentation open source repository to fix a typo.

In the **Conversation** tab of the pull request, the author explains why they created the pull request.

![Screenshot of the "Conversation" tab of a pull request.](/assets/images/help/pull_requests/pr-conversation-example.png)

The **Files changed** tab of the pull request shows the implemented fix.

![Screenshot of the "Files changed" tab of a pull request.](/assets/images/help/pull_requests/pr-files-changed-example.png)

* This contributor notices a typo in the repository.
* The user creates a pull request with the fix.
* A repository maintainer reviews the pull request, comments on it, and merges it.

### Scenarios for GitHub Discussions

* I have a question that's not necessarily related to specific files in the repository.
* I want to share news with my collaborators, or my team.
* I want to start or participate in an open-ended conversation.
* I want to make an announcement to my community.

#### GitHub Discussions example

This example shows the GitHub Discussions welcome post for the GitHub Docs open source repository, and illustrates how the team wants to collaborate with their community.

![Screenshot of an example of a discussion, with the title "Welcome to GitHub Docs Discussions."](/assets/images/help/discussions/github-discussions-example.png)

This community maintainer started a discussion to welcome the community, and to ask members to introduce themselves. This post fosters an inviting atmosphere for visitors and contributors. The post also clarifies that the team's happy to help with contributions to the repository.

## Using Copilot to gain context

> \[!NOTE] You'll need access to GitHub Copilot. For more information, see [What is GitHub Copilot?](/en/copilot/about-github-copilot/what-is-github-copilot#getting-access-to-copilot).

If you need more context or clarity on a specific issue or discussion, you can use GitHub Copilot to help answer your questions. This enables you to quickly gain insights, understand complex threads, and stay aligned with the project’s goals, fostering collaboration and knowledge sharing within the community.

To ask a question about an issue or discussion:

1. From anywhere on GitHub,  click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>** icon next to the search bar in the top right of the page.

   ![Screenshot of the new conversation button, highlighted with a dark orange outline.](/assets/images/help/copilot/copilot-icon-top-right.png)

2. In the "Ask Copilot" box, type a question and include the relevant URL in your message. For example, you could ask:

   * `Explain https://github.com/monalisa/octokit/issues/1`
   * `Summarize https://github.com/monalisa/octokit/discussions/4`
   * `Recommend next steps for https://github.com/monalisa/octokit/issues/2`
   * `What are the acceptance criteria for ISSUE URL?`
   * `What are the main points made by PERSON in DISCUSSION URL?`

   If you chat with GitHub Copilot from a specific issue or discussion, you don't need to include the URL in your question.

3. Optionally, after submitting a question, you can click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-square-fill" aria-label="Stop" role="img"><path d="M5.75 4h4.5c.966 0 1.75.784 1.75 1.75v4.5A1.75 1.75 0 0 1 10.25 12h-4.5A1.75 1.75 0 0 1 4 10.25v-4.5C4 4.784 4.784 4 5.75 4Z"></path></svg> in the text box to stop the response.

## Next steps

These examples showed you how to decide which is the best tool for your conversations on GitHub. But this is only the beginning; there is so much more you can do to tailor these tools to your needs.

For issues, for example, you can tag issues with labels for quicker searching and create issue templates to help contributors open meaningful issues. For more information, see [About issues](/en/issues/tracking-your-work-with-issues/about-issues#working-with-issues) and [About issue and pull request templates](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/about-issue-and-pull-request-templates).

For pull requests, you can create draft pull requests if your proposed changes are still a work in progress. Draft pull requests cannot be merged until they're marked as ready for review. For more information, see [About pull requests](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#draft-pull-requests).

For GitHub Discussions, you can set up a code of conduct and pin discussions that contain important information for your community. For more information, see [About discussions](/en/discussions/collaborating-with-your-community-using-discussions/about-discussions).

To learn some advanced formatting features that will help you communicate, see [Quickstart for writing on GitHub](/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github).