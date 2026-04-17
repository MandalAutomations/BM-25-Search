# CodeQL-powered analysis for Code Quality

Information on how CodeQL-powered analysis for Code Quality works, the workflow used, and the status checks reported on pull requests.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.
> During public preview, Code Quality will not be billed, although Code Quality scans will consume GitHub Actions minutes.

## CodeQL-powered analysis

Code Quality uses CodeQL to perform rule-based analysis of pull requests and your default branch.

* Findings for your **default branch** appear under the "Standard findings" dashboard under your repository's **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.

* Findings **on pull requests** appear as comments made by `github-code-quality[bot]`.

Copilot Autofix suggestions are provided for findings where possible.

### Query lists for supported languages

Each Code Quality rule is written as a query in CodeQL and then run using GitHub Actions.

The rules are continually refined by both GitHub and open source developers.

* [C# CodeQL queries for Code Quality](/en/code-security/code-quality/reference/codeql-queries/csharp-queries)
* [Go CodeQL queries for Code Quality](/en/code-security/code-quality/reference/codeql-queries/go-queries)
* [Java CodeQL queries for Code Quality](/en/code-security/code-quality/reference/codeql-queries/java-queries)
* [JavaScript CodeQL queries for Code Quality](/en/code-security/code-quality/reference/codeql-queries/javascript-queries)
* [Python CodeQL queries for Code Quality](/en/code-security/code-quality/reference/codeql-queries/python-queries)
* [Ruby CodeQL queries for Code Quality](/en/code-security/code-quality/reference/codeql-queries/ruby-queries)

For more information about the CodeQL project, see <https://codeql.github.com/>.

## Workflow used for code quality analysis

You can see all the workflow runs for Code Quality on the **Actions** tab for your repository. The dynamic workflow is called "Code Quality".

By default, the Code Quality workflow runs on standard GitHub runners but you can configure Code Quality to use runners with a specific label. These may be hosted by GitHub or self-hosted.

If your organization has configured caching of private registries, these will be available for code quality analysis to use to resolve dependencies.

For more information, see:

* [Enabling GitHub Code Quality](/en/code-security/code-quality/how-tos/enable-code-quality)
* [Giving security features access to private registries](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/giving-org-access-private-registries#code-quality-access-to-private-registries)

## Pull request status checks

When code quality analysis runs on a pull request, the "CodeQL - Code Quality / Analyze" check is shown in the "Checks" section at the bottom of the pull request.

Any code problems identified by the scan are reported in comments on the pull request. The comment is made by the `github-code-quality[bot]` and includes a Copilot Autofix suggestion.

### Status check failures

The workflow failed to run. For example, your budget for actions minutes is exhausted. See [Viewing logs to diagnose failures](/en/actions/how-tos/monitor-workflows/use-workflow-run-logs#viewing-logs-to-diagnose-failures).

### Merging is blocked: Code quality findings were detected

The scan found problems in the code that exceed the quality gate set by a code quality branch rule for the repository. You need to resolve these problems before you can merge the pull request. See [Resolving a block on your pull request](/en/code-security/code-quality/how-tos/unblock-your-pr).