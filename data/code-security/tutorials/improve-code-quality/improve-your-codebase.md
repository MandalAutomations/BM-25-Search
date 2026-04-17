# Improving the quality of your repository's code

Assess and remediate code quality issues detected on your default branch so you can improve the quality of your codebase. As you progress, you'll see your repository's code quality rating rise as a result.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.
> During public preview, Code Quality will not be billed, although Code Quality scans will consume GitHub Actions minutes.

## Introduction

This tutorial guides you through using GitHub Code Quality to review, prioritize, and remediate code health issues across your repository — helping you systematically reduce technical debt, improve reliability and maintainability, and communicate your impact to stakeholders.

### Prerequisites

* Code Quality is enabled for your repository. See [Enabling GitHub Code Quality](/en/code-security/code-quality/how-tos/enable-code-quality).
* If you're enabling GitHub Code Quality for the first time, ensure you've waited a few minutes after enablement for a full CodeQL scan of the default branch to complete.

## 1. Assess your repository's overall code health

1. Navigate to the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of your repository, then under "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code-review" aria-label="code review" role="img"><path d="M1.75 1h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 13H8.061l-2.574 2.573A1.458 1.458 0 0 1 3 14.543V13H1.75A1.75 1.75 0 0 1 0 11.25v-8.5C0 1.784.784 1 1.75 1ZM1.5 2.75v8.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h6.5a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25Zm5.28 1.72a.75.75 0 0 1 0 1.06L5.31 7l1.47 1.47a.751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018l-2-2a.75.75 0 0 1 0-1.06l2-2a.75.75 0 0 1 1.06 0Zm2.44 0a.75.75 0 0 1 1.06 0l2 2a.75.75 0 0 1 0 1.06l-2 2a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L10.69 7 9.22 5.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code quality", click **Standard findings**.
2. The overview on the "Standard findings" dashboard gives you an immediate assessment of the state of your default branch today:

   * **Maintainability rating** reflects the presence and severity of findings for dead code, duplication, complexity, missing documentation, and failure to follow best practices.
   * **Reliability rating** reflects the presence and severity of findings for correctness, performance, error handling, concurrency, and accessibility of your code.

   ![Screenshot of code quality ratings in the "Standard findings" view for Code Quality.](/assets/images/help/code-quality/all-findings-overview-repo.png)

## 2. Identify and prioritize the most impactful findings

On the "Standard findings" view, you'll see the list of results from Code Quality's last scan of the default branch of the repository. These findings are:

* Grouped by **rule**, so you can see which types of problem most affect your codebase.
* Assigned a **severity** level ("Error", "Warning", "Note").

### Focus on high severity findings

Use the dashboard **filters** to focus on the highest-severity results first ("Errors"), and review which rules generate the most issues.

![Screenshot showing the dashboard filters for the "Standard findings" view.](/assets/images/help/code-quality/standard-findings-filters.png)

To improve your repository's maintainability or reliability rating, you must resolve (fix or dismiss) all findings with the highest severity level for that metric.

For example, to improve your repository's "Reliability" metric from **Needs improvement** to **Fair**, you would need to address and resolve all **error-level findings** that impact reliability. If you have one or more error-level findings, your rating cannot be higher than "Needs improvement". See [Metrics and ratings reference](/en/code-security/code-quality/reference/metrics-and-ratings).

## 3. Investigate a group of findings and understand context

Once you've identified a rule with multiple results that you want to address, you can investigate further to understand the underlying problems.

1. Click the rule name to be taken to a detailed view of all findings for that rule.

   ![Screenshot showing a rule in the "Standard findings" view. The rule name is highlighted in dark orange.](/assets/images/help/code-quality/click-rule-name.png)

2. Click **Show more**, then review the explanation of the rule, what the recommended fix is, supporting code examples and references.

   ![Screenshot showing the results for a code quality rule. The text "Show more" is highlighted in dark orange.](/assets/images/help/code-quality/click-show-more.png)

## 4. Choose remediation options

Evaluate all the highlighted findings for validity, impact, and risk. To improve your quality rating, you need to resolve each finding by either choosing to fix or dismiss it.

### Generate an autofix

If the finding looks valid and relevant for your codebase, you can generate a suggested fix.

1. To the right of an individual finding, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> Generate fix**.

2. Review carefully the diff of the proposed change, and if you agree with it, click **Open pull request**.

3. In the "Commit autofix to branch" dialog box, select "Open a pull request", then click **Commit change**.

   > \[!TIP]
   > It's not currently possible to generate autofixes for a group of findings in bulk.
   >
   > If you want to address multiple findings with a single pull request, repeat steps 1 and 2 above, then in the "Commit autofix to branch" dialog box, use the branch name you already created for the first autofix, then select "Open pull request" and **Commit change**.
   >
   > The fix will be added to the existing draft pull request for your branch.

4. When you're ready, change the pull request status from "Draft" to "Ready for review", and carefully review the proposed changes. Wait for any CI checks and automated tests to complete and pass before merging the pull request.

### Dismiss a finding

You can dismiss a finding if it isn’t relevant or actionable in the context of your codebase. Common reasons to dismiss a finding include:

* The finding is in legacy code that’s no longer maintained.
* It’s a known exception to your team’s coding standards.
* It’s a false positive that doesn’t pose a real quality risk.

Dismissing irrelevant alerts keeps your quality checks focused on meaningful issues.

1. To dismiss a finding, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield-slash" aria-label="Dismiss" role="img"><path d="M8.533.133a1.75 1.75 0 0 0-1.066 0l-2.091.67a.75.75 0 0 0 .457 1.428l2.09-.67a.25.25 0 0 1 .153 0l5.25 1.68a.25.25 0 0 1 .174.239V7c0 .233-.008.464-.025.694a.75.75 0 1 0 1.495.112c.02-.27.03-.538.03-.806V3.48a1.75 1.75 0 0 0-1.217-1.667L8.533.133ZM1 2.857l-.69-.5a.75.75 0 1 1 .88-1.214l14.5 10.5a.75.75 0 1 1-.88 1.214l-1.282-.928c-.995 1.397-2.553 2.624-4.864 3.608-.425.181-.905.18-1.329 0-2.447-1.042-4.049-2.356-5.032-3.855C1.32 10.182 1 8.566 1 7Zm1.5 1.086V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297.05.02.106.02.153 0 2.127-.905 3.439-1.982 4.237-3.108Z"></path></svg>**.
2. The finding will disappear from the list of open findings. You can still review and reopen dismissed findings from under the "Dismissed" tab at the top of the page.

## 5. Measure improvement and communicate impact

After remediation work is complete, return to the "Standard findings" dashboard to review the updated reliability and maintainability metrics.

When communicating your impact to stakeholders, highlight:

* Any **reduction** in the number of findings for "Reliability" or "Maintainability".
* Any **change in rating** for the Reliability or Maintainability ratings.
* The requirement(s) that has been met to achieve the change in rating. For example, the remediation of all "Warning"-level findings caused the rating to change from "Fair" to "Good".

Use the improvements in quality ratings and reduction in number of findings to demonstrate progress.

## 6. Enforce code quality standards for pull requests

If you haven't already, set up quality thresholds for pull requests, to block any changes to the codebase that will reduce the health of your codebase. See [Setting code quality thresholds for pull requests](/en/code-security/code-quality/how-tos/set-pr-thresholds).

## Next steps

* Reduce technical debt further by fixing findings in recently changed files. See [Improving the quality of recently merged code with AI](/en/code-security/code-quality/tutorials/improve-recent-merges).
* Provide feedback on GitHub Code Quality in the [community discussion](https://github.com/orgs/community/discussions/177488).