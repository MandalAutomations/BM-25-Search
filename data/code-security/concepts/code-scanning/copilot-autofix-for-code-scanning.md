# About Copilot Autofix for code scanning

Copilot Autofix provides targeted recommendations to help you fix code scanning alerts and avoid introducing new security vulnerabilities.

Copilot Autofix is an expansion of code scanning that provides you with targeted recommendations to help you fix code scanning alerts so you can avoid introducing new security vulnerabilities. The potential fixes are generated automatically by large language models (LLMs) using data from the codebase and from code scanning analysis.

## How Copilot Autofix works

Copilot Autofix translates the description and location of an alert into code changes that may fix the alert. It interfaces with the large language model GPT-5.3-Codex from OpenAI, which has sufficient generative capabilities to produce both suggested fixes in code and explanatory text for those fixes.

## Enabling and managing Copilot Autofix

You do not need a subscription to GitHub Copilot to use GitHub Copilot Autofix. Copilot Autofix is available to all public repositories on GitHub.com, as well as internal or private repositories owned by organizations and enterprises that have a license for GitHub Code Security.

Copilot Autofix is allowed by default and enabled for every repository that uses CodeQL, regardless of whether it uses default or advanced setup for code scanning. There is no separate step to enable Copilot Autofix: enabling code scanning with CodeQL is sufficient. See [Configuring default setup for code scanning](/en/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning).

Administrators at the enterprise, organization, and repository levels can choose to disable Copilot Autofix. If Copilot Autofix has been disabled at your level, you can re-enable it by following the same steps used to disable it and selecting the option to allow Copilot Autofix. To learn how to manage Copilot Autofix at each level, see [Disabling Copilot Autofix for code scanning security alerts](/en/code-security/how-tos/manage-security-alerts/manage-code-scanning-alerts/disabling-autofix-for-code-scanning).