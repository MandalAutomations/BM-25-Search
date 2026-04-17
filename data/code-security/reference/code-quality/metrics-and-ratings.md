# Metrics and ratings reference

Understand the terminology used by GitHub to assess the quality of your repository's code.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.
> During public preview, Code Quality will not be billed, although Code Quality scans will consume GitHub Actions minutes.

This article provides definitions for the metrics and ratings used by Code Quality.

You can see the rule-based results for your repository on your **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab, in the **Standard findings** tab under "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code-review" aria-label="code review" role="img"><path d="M1.75 1h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 13H8.061l-2.574 2.573A1.458 1.458 0 0 1 3 14.543V13H1.75A1.75 1.75 0 0 1 0 11.25v-8.5C0 1.784.784 1 1.75 1ZM1.5 2.75v8.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h6.5a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25Zm5.28 1.72a.75.75 0 0 1 0 1.06L5.31 7l1.47 1.47a.751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018l-2-2a.75.75 0 0 1 0-1.06l2-2a.75.75 0 0 1 1.06 0Zm2.44 0a.75.75 0 0 1 1.06 0l2 2a.75.75 0 0 1 0 1.06l-2 2a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L10.69 7 9.22 5.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code quality".

## Metric definitions

The following table provides definitions for each metric that is reported for your repository.

| Metric              | Definition                                                                                                                                                                                                               | Example findings                                                                                                                          |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **Reliability**     | Assess whether the code performs its intended function correctly, predictably, and consistently. Reliable code is free from bugs, handles errors safely, and operates as expected under normal and edge-case conditions. | Issues with performance, concurrency, error handling, correctness, API design, accessibility, internationalization, or security           |
| **Maintainability** | Assess how easy it is to understand, modify, and extend the code over time. Maintainable code follows best practices, avoids unnecessary complexity, and is organized for ease of future changes and collaboration.      | Not using best practices, unused/dead code, duplicate code, complexity, logical redundancies, inadequate documentation, dependency issues |

## Severity levels

Severity levels are used to indicate the potential impact or urgency of a code quality finding. They help users prioritize remediation efforts and communicate risks to stakeholders. Severity is determined by the rule that detected the issue, following conventions from CodeQL and industry standards.

| Severity    | Definition                                                                                                                                   |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Error**   | Indicates a high-severity issue that is likely to cause bugs, failures, or major maintainability risks.                                      |
| **Warning** | Indicates a moderate-severity issue that may impact code quality or reliability, but is not immediately critical.                            |
| **Note**    | Indicates a low-severity issue, minor improvement, or recommendation. These findings are useful for ongoing code health and maintainability. |

## Ratings definitions

These ratings are used to summarize the overall reliability and maintainability of a repository based on the severity of rule-based results found by CodeQL scans of the full default branch:

| Rating                | Definition                                                                           | Criteria (based on findings)      |
| --------------------- | ------------------------------------------------------------------------------------ | --------------------------------- |
| **Excellent**         | Codebase demonstrates best practices for reliability and maintainability.            | No code quality findings detected |
| **Good**              | Codebase has low-severity issues or minor improvements are suggested.                | ≥1 "Note" level finding           |
| **Fair**              | Codebase has moderate-severity issues that may impact quality, but are not critical. | ≥1 "Warning" level finding        |
| **Needs Improvement** | Codebase has high-severity issues, including bugs or major maintainability risks.    | ≥1 "Error" level finding          |

## Further reading

* [About GitHub Code Quality](/en/code-security/code-quality/concepts/about-code-quality)
* [Interpreting the code quality results for your repository](/en/code-security/code-quality/how-tos/interpret-results)