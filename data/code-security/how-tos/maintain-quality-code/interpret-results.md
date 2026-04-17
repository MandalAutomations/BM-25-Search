# Interpreting the code quality results for your repository

View GitHub Code Quality findings for your default branch.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.
> During public preview, Code Quality will not be billed, although Code Quality scans will consume GitHub Actions minutes.

## Prerequisites

* Code Quality is enabled, see [Enabling GitHub Code Quality](/en/code-security/code-quality/how-tos/enable-code-quality).

## Viewing the full backlog of code quality results

1. Navigate to the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of your repository.
2. Click to expand **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code-review" aria-label="code review" role="img"><path d="M1.75 1h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 13H8.061l-2.574 2.573A1.458 1.458 0 0 1 3 14.543V13H1.75A1.75 1.75 0 0 1 0 11.25v-8.5C0 1.784.784 1 1.75 1ZM1.5 2.75v8.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h6.5a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25Zm5.28 1.72a.75.75 0 0 1 0 1.06L5.31 7l1.47 1.47a.751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018l-2-2a.75.75 0 0 1 0-1.06l2-2a.75.75 0 0 1 1.06 0Zm2.44 0a.75.75 0 0 1 1.06 0l2 2a.75.75 0 0 1 0 1.06l-2 2a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L10.69 7 9.22 5.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code quality**, then click **Standard findings**.

Alternatively, if you want to view AI-powered findings for the most recently changed files, see [Improving the quality of recently merged code with AI](/en/code-security/code-quality/tutorials/improve-recent-merges).

## Exploring the backlog for your repository

The "Standard findings" dashboard shows all the results found by CodeQL analysis on the default branch of your repository. This view helps you visualize the full backlog of quality results and prioritize work to fix specific types of problems.

The overview, at the top of the page, summarizes the maintainability and reliability of the codebase.

![Screenshot of the "Standard findings" dashboard for code quality results. The summary is outlined in dark orange.](/assets/images/help/code-quality/all-findings-overview-repo.png)

Underneath the overview, the full list of results is shown with a header with filters that you can use to focus on a specific set of findings. The results are:

* Grouped by the rule that detected each finding
* Within each rule, ordered by file path alphabetically

Explore the results by expanding a rule to list the affected files and clicking on the name of a rule to see full details of the findings.

![Screenshot of the Rules table on the "Standard findings" dashboard for code quality. The "Overwritten property" rule name is outlined in dark orange.](/assets/images/help/code-quality/all-findings-rules-repo.png)

## Interpreting ratings and metrics

Code quality results should always be interpreted in the context of your repository. For example:

* Small repositories, or repositories with only a small amount of code written in supported languages, tend to have few results and good ratings.
* Repositories with a lot of generated code may have many maintenance results, lowering the rating for maintainability. This is not a problem if the source code itself is maintainable.
* Large repositories with a lot of code in a fully supported language often have many results even if the majority of the code has good maintainability and reliability standards.

To learn more about the metrics and how the ratings are calculated, see [Metrics and ratings reference](/en/code-security/code-quality/reference/metrics-and-ratings).

## Next steps

* Remediate quality findings in your default branch and improve the maintainability and reliability rating for your repository. See [Improving the quality of your repository's code](/en/code-security/code-quality/tutorials/improve-your-codebase).
* Stop your repository from accumulating more code quality problems by setting a quality threshold for pull requests using rulesets. See [Setting code quality thresholds for pull requests](/en/code-security/code-quality/how-tos/set-pr-thresholds).