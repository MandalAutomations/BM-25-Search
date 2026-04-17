# Responsible use of Copilot Autofix for code scanning

Learn how GitHub uses AI to suggest potential fixes for code scanning alerts and find out how best to mitigate limitations in the AI suggestions.

## About Copilot Autofix for code scanning

GitHub Copilot Autofix is an expansion of code scanning that provides users with targeted recommendations to help them fix code scanning alerts so they can avoid introducing new security vulnerabilities. The potential fixes are generated automatically by large language models (LLMs) using data from the codebase and from code scanning analysis. GitHub Copilot Autofix is available for CodeQL analysis.

> \[!NOTE]
> You do not need a subscription to GitHub Copilot to use GitHub Copilot Autofix. Copilot Autofix is available to all public repositories on GitHub.com, as well as internal or private repositories owned by organizations and enterprises that have a license for GitHub Code Security.

Copilot Autofix generates potential fixes that are relevant to the existing source code and translates the description and location of an alert into code changes that may fix the alert. Copilot Autofix uses internal GitHub Copilot APIs interfacing with the large language model GPT-5.3-Codex from OpenAI, which has sufficient generative capabilities to produce both suggested fixes in code and explanatory text for those fixes.

Copilot Autofix is allowed by default and enabled for every repository using CodeQL, but you can choose to opt out and disable Copilot Autofix. To learn how to disable Copilot Autofix at the enterprise, organization and repository levels, see [Disabling Copilot Autofix for code scanning security alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/disabling-autofix-for-code-scanning).

In an organization's security overview dashboard, you can view the total number of code suggestions generated on open and closed pull requests in the organization for a given time period. For more information, see [Viewing security insights](/en/code-security/security-overview/viewing-security-insights#autofix-suggestions).

## Developer experience

Code scanning users can already see security alerts to analyze their pull requests. However, developers often have little training in secure coding so fixing these alerts requires substantial effort. They must first read and understand the alert location and description, and then use that understanding to edit the source code to fix the vulnerability.

Copilot Autofix lowers the barrier of entry to developers by combining information on best practices with details of the codebase and alert to suggest a potential fix to the developer. Instead of starting with a search for information about the vulnerability, the developer starts with a code suggestion that demonstrates a potential solution for their codebase. The developer evaluates the potential fix to determine whether it is the best solution for their codebase and to ensure that it maintains the intended behavior.

After committing a suggested fix or modified fix, the developer should always verify that continuous integration testing (CI) for the codebase continues to pass and that the alert is shown as resolved before they merge their pull request.

## Supported languages for CodeQL code scanning

Copilot Autofix supports fix generation for a subset of queries included in the default and security-extended CodeQL query suites for C#, C/C++, Go, Java/Kotlin, Swift, JavaScript/TypeScript, Python, Ruby, and Rust. For more information on these query suites, see [CodeQL query suites](/en/code-security/code-scanning/managing-your-code-scanning-configuration/codeql-query-suites#built-in-codeql-query-suites).

## Suggestion generation process

When Copilot Autofix is enabled for a repository, code scanning alerts that are identified send input to the LLM. If the LLM can generate a potential fix, the fix is shown as a suggestion.

GitHub sends the LLM a variety of data from the code scanning analysis. For example:

* CodeQL alert data in SARIF format. For more information, see [SARIF support for code scanning](/en/code-security/code-scanning/integrating-with-code-scanning/sarif-support-for-code-scanning).
* Code from the current version of the branch.
  * Short snippets of code around each source location, sink location, and any location referenced in the alert message or included on the flow path.
  * First \~10 lines from each file involved in any of those locations.
* Help text for the CodeQL query that identified the problem. For examples, see [CodeQL query help](https://codeql.github.com/codeql-query-help/).

Any Copilot Autofix suggestions are generated and stored within the code scanning backend. They are displayed as suggestions. No user interaction is needed beyond enabling code scanning on the codebase and creating a pull request.

The process of generating fixes does not gather or utilize any customer data beyond the scope outlined above. Therefore, the use of this feature is governed by the existing terms and conditions associated with Advanced Security. Moreover, data handled by Copilot Autofix is strictly not employed for LLM training purposes. For more information on Advanced Security terms and conditions, see [GitHub Terms for Additional Products and Features](/en/site-policy/github-terms/github-terms-for-additional-products-and-features#advanced-security).

## Limitations and non-determinism of Copilot Autofix

Copilot Autofix for code scanning alerts won't be able to generate a fix for every alert in every situation. The feature operates on a best-effort basis and is not guaranteed to succeed 100% of the time.

### When a Copilot Autofix suggestion may not be generated

Several factors can prevent Copilot Autofix from successfully generating a suggested fix.

* *Non-determinism:* The underlying large language model is a generative model and is therefore non-deterministic. This means that even with the same alert and code, it might fail to produce a viable suggestion, or the suggestion might vary across attempts.
* *Problem complexity and context:* Some security alerts, such as those that require tracing data flow across a complex, multi-file codebase or those that represent subtle logic flaws, could be difficult for the model to resolve.
* *File size:* If the affected code is within a very large file or repository, the context provided to the LLM may be truncated. The model needs sufficient context to understand the surrounding code logic and safely apply a fix; when this context is limited, the feature will not attempt a fix.
* *Language and framework coverage:* While Copilot Autofix supports a growing list of languages and CodeQL alerts, it doesn't cover every possible alert type or language.

## Quality of suggestions

GitHub uses an automated test harness to continuously monitor the quality of suggestions from Copilot Autofix. This allows us to understand how the suggestions generated by the LLM change as the model develops.

The test harness includes a set of over 2,300 alerts from a diverse set of public repositories where the highlighted code has test coverage. Suggestions for these alerts are tested to see how good they are, that is, how much a developer would need to edit them before committing them to the codebase. For many of the test alerts, suggestions generated by the LLM could be committed as-is to fix the alert while continuing to successfully pass all the existing CI tests.

In addition, the system is stress-tested to check for any potential harm (often referred to as red teaming), and a filtering system on the LLM helps prevent potentially harmful suggestions being displayed to users.

### How GitHub tests suggestions

We test the effectiveness of suggestions by merging all suggested changes, unedited, before running code scanning and the repository's unit tests on the resulting code.

1. Was the code scanning alert fixed by the suggestion?
2. Did the fix introduce any new code scanning alerts?
3. Did the fix introduce any syntax errors that code scanning can detect?
4. Has the fix changed the output of any of the repository tests?

In addition, we spot check many of the successful suggestions and verify that they fix the alert without introducing new problems. When one or more of these checks failed, our manual triage showed that in many cases the proposed fix was nearly correct but needed some minor modifications that a user could identify and manually perform.

### Effectiveness on other projects

The test set contains a broad range of different types of projects and alerts. We predict that suggestions for other projects using languages supported by Copilot Autofix should follow a similar pattern.

* Copilot Autofix is likely to add a code suggestion to the majority of alerts.
* When developers evaluate the suggestions we expect that the majority of fixes can be committed without editing or with minor updates to reflect the wider context of the code.
* A small percentage of suggested fixes will reflect a significant misunderstanding of the codebase or the vulnerability.

However, each project and codebase is unique, so developers may need to edit a larger percentage of suggested fixes before committing them. Copilot Autofix provides valuable information to help you resolve code scanning alerts, but ultimately it remains your responsibility to evaluate the proposed change and ensure the security and accuracy of your code.

> \[!NOTE]
> Fix generation for supported languages is subject to LLM operational capacity. In addition, each suggested fix is tested before it is added to a pull request. If no suggestion is available, or if the suggested fix fails internal testing, then no suggestion is displayed.

## Limitations of suggestions

When you review a suggestion from Copilot Autofix, you must always consider the limitations of AI and edit the changes as needed before you accept the changes. You should also consider updating the CI testing and dependency management for a repository before enabling Copilot Autofix for code scanning. For more information, see [Mitigating the limitations of suggestions](#mitigating-the-limitations-of-suggestions).

### Limitations of code suggestions

* *Human languages:* The system primarily uses English data, including the prompts sent to the system, the code seen by the LLMs in their datasets, and the test cases used for internal evaluation. Suggestions generated by the LLM may have a lower success rate for source code and comments written in other languages and using other character sets.
* *Syntax errors:* The system may suggest fixes that are not syntactically correct code changes, so it is important to run syntax checks on pull requests.
* *Location errors:* The system may suggest fixes that are syntactically correct code but are suggested at the incorrect location, which means that if a user accepts a fix without editing the location they will introduce a syntax error.
* *Semantic errors*: The system may suggest fixes that are syntactically valid but that change the semantics of the program. The system has no understanding of the programmer or codebase’s intent in how the code should behave. Having good test coverage helps developers verify that a fix does not change the behavior of the codebase.
* *Security vulnerabilities and misleading fixes:* The system may suggest fixes that fail to remediate the underlying security vulnerability and/or introduce new security vulnerabilities.
* *Partial fixes:* The system may suggest fixes that only partially address the security vulnerability, or only partially preserve the intended code functionality. The system sees only a small subset of the code in the codebase and does not always produce globally optimal or correct solutions.

### Limitations of dependency suggestions

Sometimes a suggested fix includes a change in the dependencies of the codebase. If you use a dependency management system, any changes will be highlighted automatically for the developer to review. Before merging a pull request always verify that any dependency changes are secure and maintain the intended behavior of the codebase.

* *New or updated dependencies:* The system may suggest adding or updating software dependencies as part of a suggested fix. For example, by suggesting changing the `package.json` file for JavaScript projects to add dependencies from npm.
* *Unsupported or insecure dependencies:* The system does not know which versions of an existing dependency are supported or secure.
* *Fabricated dependencies:* The system has incomplete knowledge of the dependencies published in the wider ecosystem. This can lead to suggestions that add a new dependency on malicious software that attackers have published under a statistically probable dependency name.

## Mitigating the limitations of suggestions

The best way to mitigate the limitations of suggestions from Copilot Autofix is to follow best practices. For example, using CI testing of pull requests to verify functional requirements are unaffected and using dependency management solutions, such as the dependency review API and action. For more information, see [About dependency review](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review).

It is important to remember that the author of a pull request retains responsibility for how they respond to review comments and suggested code changes, whether proposed by colleagues or automated tools. Developers should always look at suggestions for code changes critically. If needed, they should edit the suggested changes to ensure that the resulting code and application are correct, secure, meet performance criteria, and satisfy all other functional and non-functional requirements for the application.

## Next steps

* [About code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/about-code-scanning-alerts)
* [Triaging code scanning alerts in pull requests](/en/code-security/code-scanning/managing-code-scanning-alerts/triaging-code-scanning-alerts-in-pull-requests#working-with-autofix-suggestions-for-alerts-on-a-pull-request)
* [Resolving code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/resolving-code-scanning-alerts#generating-suggested-fixes-for-code-scanning-alerts)
* [Disabling Copilot Autofix for code scanning security alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/disabling-autofix-for-code-scanning)