# Using GitHub Copilot cloud agent to improve a project

Find and fix problems in a project with Copilot cloud agent.

> \[!NOTE]
> For an introduction to Copilot cloud agent, see [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent).

## Introduction

Modern development often starts with good intentions: a quick script, a prototype, maybe an action to automate one small thing. But as projects evolve, those early efforts can become brittle.

This tutorial shows how you can use Copilot cloud agent to improve a mature project, without slowing down your momentum.

In the following sections we'll:

* Make sure that the project contains custom instructions that Copilot can use to tailor its responses to your project.
* Make sure there's an environment setup file for Copilot cloud agent, so that it can get started on tasks more quickly by pre-installing your project’s dependencies.
* Get Copilot to look for improvements that could be made to the code, and then create issues for that work.
* Delegate the coding work to Copilot by assigning it to an issue.

## 1. Check for custom instructions

1. Go to your repository on GitHub.

2. Check that at least one of the following custom instructions files exists:

   * `.github/copilot-instructions.md`
   * `.github/instructions/**/*-instructions.md`
   * `AGENTS.md`

3. If any of these files exists, view the file and check that the instructions are adequate and up to date.

   For more information, see the section "Writing effective custom instructions" in [About customizing GitHub Copilot responses](/en/copilot/concepts/prompting/response-customization?tool=webui#writing-effective-custom-instructions), and the library of examples at [Custom instructions](/en/copilot/tutorials/customization-library/custom-instructions).

4. If there are no custom instructions files in the repository, use Copilot cloud agent to create a `.github/copilot-instructions.md` file, by following the instructions in [Adding repository custom instructions for GitHub Copilot](/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions#asking-copilot-cloud-agent-to-generate-a-copilot-instructionsmd-file).

5. Review the pull request that Copilot cloud agent creates. Check that the `.github/copilot-instructions.md` file provides Copilot with all of the information it needs to know to work on this project.

   The file should include:

   * A clear summary of the codebase and what the software does.
   * A project structure overview.
   * Contribution guidelines. For example, how to build, format, lint, and test the codebase, and requirements that must be met before pull requests can be merged.
   * Key technical principles.

6. Edit the file as required.

7. Click **Ready for review** at the bottom of the "Conversation" tab of the pull request, then complete your usual process for merging a pull request.

## 2. Check for an environment setup file

A `copilot-setup-steps.yml` GitHub Actions workflow file can help Copilot cloud agent to get started on tasks more quickly by pre-installing the dependencies that are used by the project.

Creating this file is optional but is a good idea if you use Copilot cloud agent regularly in the repository.

1. In your repository on GitHub, check that the following file exists:

   ```text copy
   .github/workflows/copilot-setup-steps.yml
   ```

   > \[!TIP]
   > A quick way to do this is to copy the above path, go to the main page of your repository and paste the path into the "Go to file" field.

2. If the file exists, open it and check that the steps in the workflow install the correct dependencies for your project. After verifying this, you can skip the remaining steps in this section.

3. If you don't already have a `copilot-setup-steps.yml` file, use the following steps to get Copilot cloud agent to create it for you.

4. At the top of any page of your repository on the GitHub website, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="Open agents panel" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg>**.

5. Copy and paste the following prompt into the Agents dialog:

   <!-- markdownlint-disable -->

   ```text copy
   Analyze this repository to understand the dependencies that need to be installed on the development environment to work on the code in this repository. Using this information, and the details about the `copilot-setup-steps.yml` file that are given in https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/customize-the-agent-environment, add a `.github/workflows/copilot-setup-steps.yml` to this repository. This Actions workflow file should install, in the development environment for Copilot cloud agent, all of the dependencies necessary to work on the code in this repository. Make sure that the workflow job is named `copilot-setup-steps`.
   ```

   <!-- markdownlint-enable -->

6. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-paper-airplane" aria-label="Start task" role="img"><path d="M.989 8 .064 2.68a1.342 1.342 0 0 1 1.85-1.462l13.402 5.744a1.13 1.13 0 0 1 0 2.076L1.913 14.782a1.343 1.343 0 0 1-1.85-1.463L.99 8Zm.603-5.288L2.38 7.25h4.87a.75.75 0 0 1 0 1.5H2.38l-.788 4.538L13.929 8Z"></path></svg>** or press <kbd>Enter</kbd>.

7. In the "Recent agent sessions" list, click the new agent session that has started.

   This displays an activity log, as Copilot works on the task. When Copilot finishes it will generate a summary of what it did.

8. Read the summary, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="Pull request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> View pull request**.

9. Optionally, add Copilot as a reviewer. For more information, see [Using GitHub Copilot code review](/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review?tool=webui). Wait for Copilot to add review comments, then make any changes you think are necessary in response to the comments.

10. Review the pull request yourself, making sure that the setup steps in the new `copilot-setup-steps.yml` file are correct.

    The workflow file that Copilot has created should include an `on: workflow_dispatch` trigger, to allow you to run the workflow manually, and the job must be named `copilot-setup-steps` as shown in this extract:

    ```yaml
    on:
      workflow_dispatch:
      push:
        paths:
          - .github/workflows/copilot-setup-steps.yml
      pull_request:
        paths:
          - .github/workflows/copilot-setup-steps.yml

    jobs:
      copilot-setup-steps:
        runs-on: ubuntu-latest
    ```

11. Make any required changes to the `copilot-setup-steps.yml` file in the pull request.

    You can ask Copilot to make changes for you by using `@copilot` in a review comment. For example:

    `@copilot - comment the file more thoroughly`

12. Click **Ready for review** at the bottom of the "Conversation" tab of the pull request, then complete your usual process for merging a pull request.

13. Open the newly added `.github/workflows/copilot-setup-steps.yml` file in your repository on GitHub.

14. Click **View Runs** near the top right of the page.

15. Click **Run workflow** and then **Run workflow** in the dialog, to test the new workflow.

16. Check that the workflow runs correctly and installs the dependencies. Fix any failures by editing the `.github/workflows/copilot-setup-steps.yml` file.

## 3. Let Copilot find technical debt

Now that Copilot has the right context and (optionally) a ready-to-use environment, you can use it to surface and prioritize technical debt in your repository.

1. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Run this prompt in Copilot Chat" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>** button in the following prompt box to send this prompt to Copilot Chat on GitHub.com.

   ```copilot copy prompt
   What technical debt exists in this project? Give me a prioritized list of up to 5 areas we need to focus on. For each, describe the problem and its consequences.
   ```

2. Make sure that **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-comment" aria-label="comment" role="img"><path d="M1 2.75C1 1.784 1.784 1 2.75 1h10.5c.966 0 1.75.784 1.75 1.75v7.5A1.75 1.75 0 0 1 13.25 12H9.06l-2.573 2.573A1.458 1.458 0 0 1 4 13.543V12H2.75A1.75 1.75 0 0 1 1 10.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h4.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> Ask** mode is selected.

3. Use the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-globe" aria-label="globe" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM5.78 8.75a9.64 9.64 0 0 0 1.363 4.177c.255.426.542.832.857 1.215.245-.296.551-.705.857-1.215A9.64 9.64 0 0 0 10.22 8.75Zm4.44-1.5a9.64 9.64 0 0 0-1.363-4.177c-.307-.51-.612-.919-.857-1.215a9.927 9.927 0 0 0-.857 1.215A9.64 9.64 0 0 0 5.78 7.25Zm-5.944 1.5H1.543a6.507 6.507 0 0 0 4.666 5.5c-.123-.181-.24-.365-.352-.552-.715-1.192-1.437-2.874-1.581-4.948Zm-2.733-1.5h2.733c.144-2.074.866-3.756 1.58-4.948.12-.197.237-.381.353-.552a6.507 6.507 0 0 0-4.666 5.5Zm10.181 1.5c-.144 2.074-.866 3.756-1.58 4.948-.12.197-.237.381-.353.552a6.507 6.507 0 0 0 4.666-5.5Zm2.733-1.5a6.507 6.507 0 0 0-4.666-5.5c.123.181.24.365.353.552.714 1.192 1.436 2.874 1.58 4.948Z"></path></svg>  All repositories** dropdown to select your repository.

4. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-paper-airplane" aria-label="Start task" role="img"><path d="M.989 8 .064 2.68a1.342 1.342 0 0 1 1.85-1.462l13.402 5.744a1.13 1.13 0 0 1 0 2.076L1.913 14.782a1.343 1.343 0 0 1-1.85-1.463L.99 8Zm.603-5.288L2.38 7.25h4.87a.75.75 0 0 1 0 1.5H2.38l-.788 4.538L13.929 8Z"></path></svg>** or press <kbd>Enter</kbd>.

5. Review the details in Copilot's response.

6. Assuming Copilot identified at least one area for improvement, copy the following prompt into the same conversation:

   ```copilot copy
   /create-issue

   Create a GitHub issue to address the first of the problem areas that you identified.

   If the problem area requires substantial work, create one main issue for the entire problem area and then sub-issues that allow the work to be split up into manageable chunks, which will be tackled in separate pull requests that can be easily reviewed. For a large body of work, do not create a single issue that attempts to address the entire problem.

   The issue, or each sub-issue if these are created, must include a description of the problem, a set of acceptance criteria, and pointers on what files need to be added/updated.
   ```

7. Edit this prompt as required. For example, depending on the response that Copilot produced, you may want to work on another of the problem areas that Copilot identified, rather than the first.

8. Make sure that Ask mode is still selected (**<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-comment" aria-label="comment icon" role="img"><path d="M1 2.75C1 1.784 1.784 1 2.75 1h10.5c.966 0 1.75.784 1.75 1.75v7.5A1.75 1.75 0 0 1 13.25 12H9.06l-2.573 2.573A1.458 1.458 0 0 1 4 13.543V12H2.75A1.75 1.75 0 0 1 1 10.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h4.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg>**).

9. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-paper-airplane" aria-label="Start task" role="img"><path d="M.989 8 .064 2.68a1.342 1.342 0 0 1 1.85-1.462l13.402 5.744a1.13 1.13 0 0 1 0 2.076L1.913 14.782a1.343 1.343 0 0 1-1.85-1.463L.99 8Zm.603-5.288L2.38 7.25h4.87a.75.75 0 0 1 0 1.5H2.38l-.788 4.538L13.929 8Z"></path></svg>** or press <kbd>Enter</kbd>.

10. Review the draft issue that Copilot generates, editing it as required.

11. If Copilot creates a single draft issue that indicates that sub-issues should be created, prompt Copilot to do this for you:

    ```copilot copy
    Go ahead and create sub-issues that chunk this work into manageable pieces.
    ```

12. Click **Create**, or **Review and Create**, depending on how many issues were drafted.

    Copilot creates one or more new issues on your behalf. You will be shown as the issue author.

## 4. Get Copilot to fix an issue

Now that you have created issues, the next step is to delegate an issue to Copilot and review the resulting pull request.

1. Open one of the issues that Copilot created for you in the previous section.

2. Check that the issue contains acceptance criteria that Copilot can use to verify it has completed the task.

3. Make any changes you feel are necessary to accurately describe the problem that needs to be fixed, and the expected outcome of the work on this issue.

4. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="Open agents panel" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> Assign to Copilot**.

5. In the "Assign Copilot to issue", click **Assign**.

   Copilot will start working on the issue. After a few moments a link to a draft pull request will be added to the issue.

6. Click the link to the draft pull request.

   Once Copilot has finished working on the pull request it will remove "\[WIP]" from the pull request title and will add you as a reviewer.

   You can leave Copilot to work on the pull request asynchronously, and come back to review the pull request once you are added as a reviewer.

7. Optionally, after Copilot has been working for a couple of minutes, you can click **View session** on the pull request to see a log of what Copilot is doing.

8. Optionally, on the "Conversation" tab of the pull request, add Copilot as a reviewer.

9. After you have been added as a reviewer, review the changes yourself and make any required changes.

   You can ask Copilot to make changes for you by using `@copilot` in a review comment.

10. Click **Ready for review** at the bottom of the "Conversation" tab of the pull request, then complete your usual process for merging a pull request.

## 5. Iterate on this process

1. If Copilot created multiple issues, repeat section 4, assigning Copilot to one of the other issues.
2. After closing all of the issues that Copilot created, repeat section 3, choosing another problem area and iterating on section 4 to assign issues to Copilot and review and merge its changes.

## Conclusion

Copilot cloud agent can help you to improve the quality of code in any project, but it's particularly useful for reducing technical debt in a project that has grown organically over many months or years. By using Copilot cloud agent, you can make improvements that you might have struggled to find time for without an AI assistant working on your behalf.

Copilot doesn't replace you as a developer—you still need to be involved at every step of this process, specifying what you want Copilot to do and carefully reviewing the code it changes or adds—but it does allow you to implement improvements at the same time as you work on other important tasks.

## Next steps

Read this case study on the GitHub blog: [How the GitHub billing team uses the cloud agent in GitHub Copilot to continuously burn down technical debt](https://github.blog/ai-and-ml/github-copilot/how-the-github-billing-team-uses-the-cloud-agent-in-github-copilot-to-continuously-burn-down-technical-debt/).