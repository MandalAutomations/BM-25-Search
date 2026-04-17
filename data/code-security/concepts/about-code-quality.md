# About GitHub Code Quality

Use GitHub Code Quality to flag code quality issues in pull requests and repository scans, apply Copilot-powered autofixes, and enforce standards with rulesets.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.
> During public preview, Code Quality will not be billed, although Code Quality scans will consume GitHub Actions minutes.

## Overview

GitHub Code Quality helps you ensure your codebase is reliable, maintainable, and efficient. Whether you're building a new feature, reducing technical debt, or reporting on repository health, Code Quality provides actionable insights and automated fixes so you can improve and maintain the code health of your repository efficiently.

## Key features and benefits

With Code Quality, you can:

* Identify code quality risks and opportunities in **pull requests** and through **repository scans**.
* Review clear explanations for findings and apply one-click **Copilot-powered autofixes**.
* Use **repository dashboards** to track reliability and maintainability scores, identify areas needing attention, and prioritize remediation.
* Monitor **organization dashboards** to understand the code health of your repositories at a glance and determine which repositories to investigate further.
* Set up **rulesets** for pull requests to enforce code quality standards and block changes that do not meet your criteria.
* Easily assign remediation work to **Copilot cloud agent**, if you have a Copilot license.

## Availability and usage costs

GitHub Code Quality is available for organization-owned repositories on GitHub Team and GitHub Enterprise Cloud plans.

GitHub Code Quality won't be billed during public preview. However, Code Quality scans will consume GitHub Actions minutes. See [GitHub Code Quality billing](/en/billing/concepts/product-billing/github-code-quality).

> \[!NOTE]
>
> * You **don't** need a Copilot or a Code Security license to use Code Quality or apply Copilot-powered autofixes.

## Supported languages

Code Quality performs rule-based analysis of the following languages using CodeQL:

* C#
* Go
* Java
* JavaScript
* Python
* Ruby
* TypeScript

Code Quality also performs AI-powered analysis with results displayed separately on the "**AI findings**" repository dashboard. Unlike the rule-based CodeQL analysis that scans the entire codebase and pull requests, this AI-powered analysis only examines files recently pushed to the default branch and may identify issues in languages beyond those listed above. For more information, see [Responsible use of GitHub Code Quality](/en/code-security/code-quality/responsible-use/code-quality).

## Where will findings appear?

Once you enable Code Quality for a repository, you'll see CodeQL scans for:

* Every new pull request opened against the default branch
* All existing pull requests to the default branch when they are updated, triggering a new run of CI tests
* The whole codebase on the default branch at the time and date shown on the "Code quality" settings page

In addition, you'll see an AI-powered analysis of all recent pushes to the default branch.

### Pull request results

When CodeQL finds rule-based problems on pull requests, you'll see comments from the `github-code-quality[bot]`. Where possible, each comment will include a Copilot Autofix suggestion on how to fix the problem. See [Fixing code quality findings before merging your pull request](/en/code-security/code-quality/tutorials/fix-findings-in-prs).

### Default branch results

Code Quality findings on the default branch are reported on "Code quality" pages on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for the repository:

* **Standard findings** shows the results of CodeQL quality analysis. See [Improving the quality of your repository's code](/en/code-security/code-quality/tutorials/improve-your-codebase).
* **AI findings** shows the results of AI-powered analysis of the files most recently pushed to the default branch. See [Improving the quality of recently merged code with AI](/en/code-security/code-quality/tutorials/improve-recent-merges).

### Scan information

Each CodeQL analysis will use GitHub Actions minutes and can be seen on the **Actions** tab of the repository as a run of the dynamic "Code Quality" workflow.

## Next steps

* **For your repository:** Turn on Code Quality to start generating results. See [Enabling GitHub Code Quality](/en/code-security/how-tos/maintain-quality-code/enable-code-quality).
* **For your enterprise:** Ensure repositories in your enterprise can enable Code Quality. See [Allowing use of GitHub Code Quality in your enterprise](/en/code-security/how-tos/secure-at-scale/configure-enterprise-security/configure-specific-tools/allow-github-code-quality-in-enterprise).