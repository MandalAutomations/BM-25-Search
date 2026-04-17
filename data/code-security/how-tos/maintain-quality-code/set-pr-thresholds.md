# Setting code quality thresholds for pull requests

Create a Code Quality gate for pull requests to increase the quality of code merged into your repository.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.
> During public preview, Code Quality will not be billed, although Code Quality scans will consume GitHub Actions minutes.

## Introduction

You can block pull requests that don't meet your code quality standards by adding the **Require code quality results** branch rule to a ruleset and specifying the severity level you require. If a pull request doesn't reach this threshold, it can't be merged.

## Prerequisites

* Code Quality is enabled. See [Enabling GitHub Code Quality](/en/code-security/code-quality/how-tos/enable-code-quality)
* Code in a supported language. See [Supported languages](/en/code-security/code-quality/concepts/about-code-quality#supported-languages).

> \[!NOTE]
> The threshold will have an impact only if the repository has code in one or more of the supported languages, see [Enabling GitHub Code Quality](/en/code-security/code-quality/how-tos/enable-code-quality).

## Confirming Code Quality runs successfully on pull requests

Before you add or update a ruleset to include a threshold for Code Quality, confirm that the Code Quality workflow is running and reporting results back to pull requests. Otherwise, the ruleset could block the merging of **all** pull requests.

1. Open a recent pull request and scroll to the "Checks" summary at the bottom of the pull request.
2. Confirm that the "CodeQL - Code Quality" check ran successfully and reported its status.

For more information, see [CodeQL-powered analysis for Code Quality](/en/code-security/code-quality/reference/codeql-detection).

## Adding or updating a ruleset to include Code Quality

1. Navigate to the "Settings" tab of your repository.
2. In the left sidebar, under "Code and automation", expand <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-repo-push" aria-label="repo-push" role="img"><path d="M2 2.5A2.5 2.5 0 0 1 4.5 0h8.75a.75.75 0 0 1 .75.75v3.5a.75.75 0 0 1-1.5 0V1.5h-8a1 1 0 0 0-1 1v6.708A2.493 2.493 0 0 1 4.5 9h2.25a.75.75 0 0 1 0 1.5H4.5a1 1 0 0 0 0 2h4.75a.75.75 0 0 1 0 1.5H4.5A2.5 2.5 0 0 1 2 11.5Zm12.23 7.79h-.001l-1.224-1.224v6.184a.75.75 0 0 1-1.5 0V9.066L10.28 10.29a.75.75 0 0 1-1.06-1.061l2.505-2.504a.75.75 0 0 1 1.06 0L15.29 9.23a.751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018Z"></path></svg> **Rules**, then click **Rulesets**.
3. If you don't already have a ruleset to protect your default branch, expand **New ruleset** and click **New branch ruleset**. Alternatively, open your existing ruleset for the default branch and move to step 5.
4. If you are creating a new ruleset:
   * Define a name for the ruleset.
   * Set the "Enforcement status" to "Active."
   * Under "Target branches" add a target of "Include default branch."
5. Under "Branch rules", enable "Require code quality results".
6. Set "Severity" to define the lowest severity of code quality results that must be resolved before a pull request can be merged into the default branch. For example:
   * Set "Errors" to block pull requests with unresolved code quality **errors** being merged.
   * Set "Warnings and higher" to block pull requests with unresolved code quality **warnings** or **errors** being merged.
   * Set "Notes and higher" to block pull requests with unresolved code quality **notes**, **warnings** or **errors** being merged.
   * Set "All" to block pull requests with **any** unresolved code quality results being merged.
7. When you have finished defining or editing the ruleset, click **Create** or **Save changes**.

## Next steps

Learn how GitHub Code Quality works on pull requests to prevent code quality issues from reaching your default branch. See [Fixing code quality findings before merging your pull request](/en/code-security/code-quality/tutorials/fix-findings-in-prs).