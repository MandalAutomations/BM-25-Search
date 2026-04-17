# Resolving a block on your pull request

Identify and resolve a code quality block on your pull request so you can merge your changes.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.
> During public preview, Code Quality will not be billed, although Code Quality scans will consume GitHub Actions minutes.

## Understanding why your pull request is blocked

Repository administrators can set code quality gates for maintainability and reliability using GitHub Code Quality. When you open a pull request, a scan automatically runs to check your changes against these standards.

If your pull request introduces code that falls below the required quality threshold, you’ll see a merge block banner at the bottom of the pull request in the Checks section:
"Merging is blocked: Code quality findings were detected."

![Screenshot of the merge block banner in the Checks section of a pull request.](/assets/images/help/code-quality/code-quality-merge-block.png)

These checks help maintain a healthy, maintainable codebase and prevent technical debt from accumulating.

## Viewing scan results and their severity levels

The results of the scan are reported as comments on your pull request, left by the `github-code-quality[bot]`. Each comment corresponds to a specific code quality problem that was detected in your changes.

Comments are labeled by severity (**Error**, **Warning**, **Note**). To learn more about what the severity levels mean, see [Severity levels](/en/code-security/code-quality/reference/metrics-and-ratings#severity-levels).

## Determining which findings are blocking your pull request

The quality gate set by repository administrators defines the **minimum severity level** that will block merging.

The merge block banner may specify the minimum severity level. All findings at that severity level or higher must be addressed before you can merge your pull request.

![Screenshot of the merge block banner in the Checks section of a pull request.](/assets/images/help/code-quality/merge-block-warnings.png)

> \[!NOTE]
> If you don't see a severity level defined in the merge block banner, it means that your repository is using the most stringent code quality thresholds, which require **all findings** to be addressed before merging.

## Fixing or dismissing each finding

In order to unblock your pull request, you need to resolve each required finding by deciding whether to **fix** the issue in your code or **dismiss** the comment.

### Leveraging Copilot Autofix and Copilot cloud agent to fix findings

#### Copilot Autofix

Comments on the pull request include a suggested **autofix** that you can commit directly to your pull request. Carefully review the suggested autofix for logic, security, and style, then click **Commit suggestion**.

You don't need a Copilot license to apply these suggestions.

#### Copilot cloud agent

Alternatively, if you have a Copilot license, you can delegate the remediation work to Copilot cloud agent. Comment on the pull request mentioning `@Copilot` and request that Copilot fix the detected issues.

![Screenshot showing a PR comment that invoked Copilot cloud agent.](/assets/images/help/code-quality/invoke-cloud-agent.png)

Copilot responds with an eyes emoji (👀) to your comment, starts a new agent session, and opens a pull request with the necessary fixes.

You can track Copilot cloud agent's work:

* In the pull request, the summary is updated as work progresses.
* Using the [agents page](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text) or session logs, see [Tracking GitHub Copilot's sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/track-copilot-sessions).

You need a Copilot license to invoke Copilot cloud agent. <br><a href="https://github.com/features/copilot/plans?ref_product=copilot&ref_type=purchase&ref_style=button" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Sign up for Copilot</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

### Dismissing the finding

You can dismiss a finding if it isn’t relevant or actionable in the context of your codebase. Common reasons to dismiss a finding include:

* The finding is in legacy code that’s no longer maintained.
* It’s a known exception to your team’s coding standards.
* It’s a false positive that doesn’t pose a real quality risk.

Dismissing irrelevant alerts keeps your quality checks focused on meaningful issues.

## Verifying that you've met the requirements

To see if you've met the code quality requirements, look at the "Checks" section at the bottom of your pull request. The merge block banner should no longer be present, and you should be able to merge your changes as usual.

## Next steps

Reduce technical debt by fixing findings in recently changed files. See [Improving the quality of recently merged code with AI](/en/code-security/code-quality/tutorials/improve-recent-merges).