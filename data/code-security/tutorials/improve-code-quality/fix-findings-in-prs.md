# Fixing code quality findings before merging your pull request

Catch quality issues before they reach your default branch and fix them with Copilot Autofix and Copilot cloud agent.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.
> During public preview, Code Quality will not be billed, although Code Quality scans will consume GitHub Actions minutes.

## Introduction

This tutorial shows you how to work with GitHub Code Quality on pull requests to identify code quality issues that your changes may otherwise inadvertently introduce, and how to address and resolve code quality findings with Copilot Autofix and Copilot cloud agent.

### Benefits of catching issues early

Catching code quality issues early keeps your team's codebase in shape. GitHub Code Quality checks your code for:

* **Reliability**: For example, logic errors, unsafe error handling, or race conditions that could cause your app to crash or behave unpredictably. By addressing this type of issue early, you make your software more robust and dependable for users.
* **Maintainability**: For example, duplicated code, overly complex logic, unused variables, or violations of coding best practices. Fixing these issues makes your code cleaner and easier to read, so future changes are faster and less risky.

## 1. Understand how GitHub Code Quality works on pull requests

When you open a pull request, GitHub Code Quality uses CodeQL to automatically scan your changes for quality issues like those described above.

The results of the CodeQL scan are reported as comments on your pull request, left by the `github-code-quality[bot]`. Each comment corresponds to a specific code quality problem that was detected in your changes, and comes with a suggested autofix.

Comments are labeled by severity (**Error**, **Warning**, **Note**), so you can see which findings are the most critical to address.

## 2. Prioritize fixes based on severity

Scan through the comments and identify the findings that have the highest severity level ("Error") first.

If there are no "Error" findings, look for findings of the next severity level ("Warning"), and so on.

High severity findings indicate more serious code quality issues that are more likely to introduce reliability or maintainability problems in your codebase. By resolving high severity findings, you're doing the most impactful work to maintain the quality of your team's code.

> \[!NOTE]
> A repository administrator may have set a code quality gate that **blocks** merging on your pull request, if the pull request contains Code Quality findings of a particular severity level or above. See [Resolving a block on your pull request](/en/code-security/code-quality/how-tos/unblock-your-pr).

## 3. Leverage Copilot Autofix or Copilot cloud agent to fix findings

### Copilot Autofix

Comments on the pull request include a suggested **autofix** that you can commit directly to your pull request. Carefully review the suggested autofix for logic, security, and style, then click **Commit suggestion**.

You don't need a Copilot license to apply these suggestions.

### Copilot cloud agent

Alternatively, if you have a Copilot license, you can delegate the remediation work to Copilot cloud agent. Comment on the pull request mentioning `@Copilot` and request that Copilot fix the detected issues.

![Screenshot showing a PR comment that invoked Copilot cloud agent.](/assets/images/help/code-quality/invoke-cloud-agent.png)

Copilot responds with an eyes emoji (👀) to your comment, starts a new agent session, and opens a pull request with the necessary fixes.

You can track Copilot cloud agent's work:

* In the pull request, the summary is updated as work progresses.
* Using the [agents page](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text) or session logs, see [Tracking GitHub Copilot's sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/track-copilot-sessions).

You need a Copilot license to invoke Copilot cloud agent. <br><a href="https://github.com/features/copilot/plans?ref_product=copilot&ref_type=purchase&ref_style=button" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Sign up for Copilot</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

## 4. Dismiss irrelevant findings

You can dismiss a finding if it isn’t relevant or actionable in the context of your codebase. Common reasons to dismiss a finding include:

* The finding is in legacy code that’s no longer maintained.
* It’s a known exception to your team’s coding standards.
* It’s a false positive that doesn’t pose a real quality risk.

Dismissing irrelevant alerts keeps your quality checks focused on meaningful issues.

## 5. Push changes and wait for the scan

After fixing or dismissing findings, push your changes to the branch associated with your pull request. GitHub Code Quality will automatically re-scan your changes and update the comments on your pull request accordingly.

## 6. Check your repository's code quality ratings

Anyone with write access can view the overall code quality ratings for a repository, which summarize the state of the code's reliability and maintainability across the default branch.

To view your repository's ratings, navigate to the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of your repository, expand **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code-review" aria-label="code review" role="img"><path d="M1.75 1h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 13H8.061l-2.574 2.573A1.458 1.458 0 0 1 3 14.543V13H1.75A1.75 1.75 0 0 1 0 11.25v-8.5C0 1.784.784 1 1.75 1ZM1.5 2.75v8.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h6.5a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25Zm5.28 1.72a.75.75 0 0 1 0 1.06L5.31 7l1.47 1.47a.751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018l-2-2a.75.75 0 0 1 0-1.06l2-2a.75.75 0 0 1 1.06 0Zm2.44 0a.75.75 0 0 1 1.06 0l2 2a.75.75 0 0 1 0 1.06l-2 2a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L10.69 7 9.22 5.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code quality** in the sidebar, then click **Standard findings**.

By resolving issues before merging your pull request, you've directly contributed to maintaining these ratings.

## Next steps

* Address code quality findings in your default branch and understand your repository’s reliability and maintainability ratings. See [Improving the quality of your repository's code](/en/code-security/code-quality/tutorials/improve-your-codebase).
* Provide feedback on GitHub Code Quality in the [community discussion](https://github.com/orgs/community/discussions/177488).