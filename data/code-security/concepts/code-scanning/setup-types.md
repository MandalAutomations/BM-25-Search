# About setup types for code scanning

Depending on your needs, GitHub offers a default or advanced setup for code scanning.

## About default setup

Default setup for code scanning is the quickest, easiest, most low-maintenance way to enable code scanning for your repository. Based on the code in your repository, default setup will automatically create a custom code scanning configuration. After enabling default setup, the code written in CodeQL-supported languages in your repository will be scanned using CodeQL:

* On each push to the repository's default branch, or any protected branch. For more information on protected branches, see [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).
* When creating or committing to a pull request based against the repository's default branch, or any protected branch, excluding pull requests from forks.
* On a weekly schedule.

### Supported languages

We recommend enabling default setup for eligible repositories if there is any chance the repositories will include at least one CodeQL-supported language in the future. If you enable default setup on a repository that does not include any CodeQL-supported languages, default setup will not run any scans or use any GitHub Actions minutes. If CodeQL-supported languages are added to the repository's default branch, default setup will automatically begin scanning CodeQL-supported languages and using GitHub Actions minutes. For more information on CodeQL-supported languages, see [About code scanning with CodeQL](/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning-with-codeql#about-codeql).

If the code in a repository changes to include any CodeQL-supported languages, GitHub will automatically update the code scanning configuration to include the new language. If code scanning fails with the new configuration, GitHub will resume the previous configuration automatically so the repository does not lose code scanning coverage.

## Customization of default setup

After running an initial analysis of your code with default setup, you can make changes to your configuration to better meet your needs.

### Configuration options

For existing configurations of default setup, you can edit:

* Which languages default setup will analyze.
* The query suite run during analysis. For more information on the available query suites, see [CodeQL query suites](/en/code-security/code-scanning/managing-your-code-scanning-configuration/codeql-query-suites).
* The threat models (public preview) to use for analysis. Your choice of threat model determines which sources of tainted data are treated as a risk to your application. During the public preview, threat models are supported only for analysis of Java/Kotlin and C#. For more information about threat models, see [Including local sources of tainted data in default setup](/en/code-security/how-tos/scan-code-for-vulnerabilities/manage-your-configuration/editing-your-configuration-of-default-setup#including-local-sources-of-tainted-data-in-default-setup).

If your codebase depends on a library or framework that is not recognized by the standard libraries included with CodeQL, you can also extend the CodeQL coverage in default setup using CodeQL model packs. For more information, see [Extending CodeQL coverage with CodeQL model packs in default setup](/en/code-security/how-tos/scan-code-for-vulnerabilities/manage-your-configuration/editing-your-configuration-of-default-setup#extending-codeql-coverage-with-codeql-model-packs-in-default-setup).

Additional configuration options that are shared between all code scanning setup types are available. See [Repository properties for code scanning](/en/code-security/concepts/code-scanning/repository-properties).

### Available runners

You can use default setup for all CodeQL-supported languages on self-hosted runners or GitHub-hosted runners.

You can assign self-hosted runners for default setup by giving the runners the default `code-scanning` label, or you can optionally give them custom labels so that individual repositories can use different runners.

Unless you have a specific use case, we recommend that you only assign runners with the default `code-scanning` label. However, you may want to use custom labels to:

* Assign more powerful self-hosted runners to critical repositories for faster code scanning analysis.
* Run your code scanning analyses on a particular platform (for example, macOS).
* Have granular control over the workload for your GitHub-hosted runners and self-hosted runners.

## About advanced setup

If you need more granular control over your code scanning configuration, you should instead configure advanced setup. Advanced setup for code scanning is helpful when you need to customize your code scanning. You can set up code scanning with GitHub Actions or an external continuous integration or continuous delivery/deployment (CI/CD) system.

If you run code scanning using multiple configurations, an alert will sometimes have multiple analysis origins. If an alert has multiple analysis origins, you can view the status of the alert for each analysis origin on the alert page. For more information, see [About code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/about-code-scanning-alerts#about-analysis-origins).

### With GitHub Actions

By creating and editing a GitHub Actions workflow file, you can define how to build compiled languages, choose which queries to run, select the languages to scan, use a matrix build, and more. You also have access to all the options for controlling workflows, for example: changing the scan schedule, defining workflow triggers, specifying specialist runners to use.

### With a third-party CI/CD system

As an alternative to running code scanning within GitHub using GitHub Actions, you can analyze code in an external CI/CD system, then upload the results to GitHub.

The CodeQL CLI is a standalone, command-line tool that you can use to analyze code. You can add the CodeQL CLI to your third-party system, or use another third-party static analysis tool that can produce results as Static Analysis Results Interchange Format (SARIF) 2.1.0 data. For more information, see [About the CodeQL CLI](/en/code-security/codeql-cli/getting-started-with-the-codeql-cli/about-the-codeql-cli) and [SARIF support for code scanning](/en/code-security/code-scanning/integrating-with-code-scanning/sarif-support-for-code-scanning).

Alerts for code scanning that you generate externally are displayed in the same way as those for code scanning that you generate within GitHub.

## Next steps

You can enable default setup for a single repository, multiple repositories, or all repositories in an organization at the same time.

* For a single repository, see [Configuring default setup for code scanning](/en/code-security/how-tos/scan-code-for-vulnerabilities/configure-code-scanning/configuring-default-setup-for-code-scanning).
* For bulk enablement, see [Configuring default setup for code scanning at scale](/en/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning-at-scale).

To configure advanced setup instead, see [Configuring advanced setup for code scanning](/en/code-security/how-tos/scan-code-for-vulnerabilities/configure-code-scanning/configuring-advanced-setup-for-code-scanning).