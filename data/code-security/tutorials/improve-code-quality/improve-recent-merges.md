# Improving the quality of recently merged code with AI

Explore GitHub Code Quality findings for recently merged code and fix with Copilot Autofix or delegate remediation work to Copilot cloud agent.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.
> During public preview, Code Quality will not be billed, although Code Quality scans will consume GitHub Actions minutes.

## Introduction

This tutorial shows you how to explore and remediate quality issues that have been detected by Code Quality's AI-powered analysis of code that was recently merged into your default branch.

When you improve quality of recently merged files, you reduce technical debt in the repository and make it easier for other developers to work on files that are under active development.

### Code Quality has two lines of defense

Code Quality scans pull requests and comments on quality concerns, **then runs a second AI scan** after the pull request is merged. The two types of scan use complementary technologies:

* **Pull request scans** use CodeQL rules to identify problems. This analysis is thoroughly tested, good at identifying where code doesn't match the quality rules, and can analyze many files. However, it supports a subset of coding languages and cannot identify problems where there is no rule.

* **Recently merged file scans** use a large language model to analyze your most recently changed files and report findings for up to 5 files. This analysis examines your code across all languages, without being limited by rules, and provides contextual insights and suggestions that can go beyond what CodeQL rules offer.

### Prerequisites

* Code Quality is enabled, see [Enabling GitHub Code Quality](/en/code-security/code-quality/how-tos/enable-code-quality).
* At least one pull request has been merged since Code Quality was enabled.

## 1. View the AI suggestions for your repository

After a Code Quality scan of the recently merged files on your default branch, you can see the results under the **AI findings** view, which displays findings for up to 5 files.

1. Navigate to the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of your repository.
2. Click to expand **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code-review" aria-label="code review" role="img"><path d="M1.75 1h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 13H8.061l-2.574 2.573A1.458 1.458 0 0 1 3 14.543V13H1.75A1.75 1.75 0 0 1 0 11.25v-8.5C0 1.784.784 1 1.75 1ZM1.5 2.75v8.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h6.5a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25Zm5.28 1.72a.75.75 0 0 1 0 1.06L5.31 7l1.47 1.47a.751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018l-2-2a.75.75 0 0 1 0-1.06l2-2a.75.75 0 0 1 1.06 0Zm2.44 0a.75.75 0 0 1 1.06 0l2 2a.75.75 0 0 1 0 1.06l-2 2a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L10.69 7 9.22 5.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code quality**, then click **AI findings**.

> \[!NOTE]
> This view is empty if the repository is inactive or if LLM analysis could not suggest ways to improve code quality in recent pushes to the default branch.

## 2. Explore suggested improvements for your repository

On the **AI findings** page, each file is listed with the number of quality problems identified and when the file was pushed to the default branch.

* Click a file name to view details of the quality problems detected and the suggested fixes.

![Screenshot of the "AI findings" view for code quality.](/assets/images/help/code-quality/ai-suggestions-repo.png)

## 3. Delegate remediation work or open pull requests yourself

You can open a pull request to apply the suggested autofixes to a file or delegate the remediation work to Copilot cloud agent. You need a Copilot license to assign work to Copilot cloud agent. <br><a href="https://github.com/features/copilot/plans?ref_product=copilot&ref_type=purchase&ref_style=button" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Sign up for Copilot</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

### Delegate work to Copilot cloud agent

You can ask cloud agent to open pull requests to make improvements to files using the suggested changes as a prompt. This is the best option if the suggested changes look good to you and you want to open a pull request that applies fixes to more than one file.

To delegate pull request creation:

* **Multiple files:** Select the files you want to include, then click **Assign selected to Copilot** in the header for the list of files.
* **One file:** Click **Assign to Copilot** for the file.

There is a delay while the cloud agent sets up the work. When the pull request is open and work is in progress, a banner is displayed with a link to the pull request.

You can track Copilot cloud agent's work:

* In the pull request, the summary is updated as work progresses.
* Using the [agents page](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text) or session logs. See [Tracking GitHub Copilot's sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/track-copilot-sessions).

### Open your own pull requests

You can open pull requests yourself to apply autofix suggestions. This is the best option if:

* You want to work on the changes locally or in GitHub Desktop before opening a pull request
* You do not have access to Copilot cloud agent

> \[!NOTE]
> When you open a pull request yourself, you can only commit fixes to one file at a time. To fix multiple files at once, you must use Copilot cloud agent.

#### Opening a pull request

1. Click the file name to view details of the quality problems detected.

2. Review the problems and suggested fixes.

3. Expand the **Assign to Copilot** drop-down and then click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="Pull request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> **Open pull request** to change the default option to "Open pull request". Your preference is remembered.

   ![Screenshot of the "AI findings" view for code quality.](/assets/images/help/code-quality/ai-suggestions-repo-fixes.png)

4. Click **Open pull request** to open a dialog of commit options.

5. Click **Commit change** to create a pull request with the fixes.

## 4. Provide pull request reviewers with context

Providing context on why you are proposing changes to code is the best way to encourage team members to review your pull request. If you used Copilot cloud agent, the pull request summary already includes full details of the problems fixed by the pull request.

If you opened the pull request directly from the GitHub Code Quality view, the pull request summary links to the "AI findings" view. You may want to copy some of the explanations from the AI findings view into the pull request summary.

![Screenshot of a pull request summary created by GitHub Code Quality.](/assets/images/help/code-quality/user-pr-ai-findings.png)

## 5. See your changes make an impact on AI findings

When you return to the "AI findings" view after merging your pull request, the findings you fixed are no longer listed.

## Next steps

* Learn more about how Copilot cloud agent can help expedite development tasks. See [Best practices for using GitHub Copilot to work on tasks](/en/copilot/tutorials/cloud-agent/get-the-best-results).
* Provide feedback on GitHub Code Quality in the [community discussion](https://github.com/orgs/community/discussions/177488).