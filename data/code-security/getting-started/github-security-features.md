# GitHub security features

An overview of GitHub's security features.

## About GitHub's security features

GitHub's security features help keep your code and secrets secure in repositories and across organizations.

* Some features are available for all GitHub plans.
* Additional features are available to organizations  on GitHub Team and GitHub Enterprise Cloud that purchase a GitHub Advanced Security product:
  * [GitHub Secret Protection](#available-with-github-secret-protection)
  * [GitHub Code Security](#available-with-github-code-security)
* In addition, a number of GitHub Secret Protection and GitHub Code Security features can be run on public repositories for free.

## Available for all GitHub plans

The following security features are available for you to use, regardless of the GitHub plan you are on. You don't need to purchase GitHub Secret Protection or GitHub Code Security to use these features.

Most of these features are available for public and private repositories.
Some features are *only* available for public repositories.

### Security policy

Make it easy for your users to confidentially report security vulnerabilities they've found in your repository. For more information, see [Adding a security policy to your repository](/en/code-security/getting-started/adding-a-security-policy-to-your-repository).

### Dependency graph

The dependency graph allows you to explore the ecosystems and packages that your repository depends on and the repositories and packages that depend on your repository.

You can find the dependency graph on the **Insights** tab for your repository. For more information, see [About the dependency graph](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph).

### Software Bill of Materials (SBOM)

You can export the dependency graph of your repository as an SPDX-compatible, Software Bill of Materials (SBOM). For more information, see [Exporting a software bill of materials for your repository](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/exporting-a-software-bill-of-materials-for-your-repository).

### GitHub Advisory Database

The GitHub Advisory Database contains a curated list of security vulnerabilities that you can view, search, and filter. For more information, see [Browsing security advisories in the GitHub Advisory Database](/en/code-security/security-advisories/working-with-global-security-advisories-from-the-github-advisory-database/browsing-security-advisories-in-the-github-advisory-database).

### Dependabot alerts and security updates

View alerts about dependencies that are known to contain security vulnerabilities, and choose whether to have pull requests generated automatically to update these dependencies. For more information, see [About Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)
and [About Dependabot security updates](/en/code-security/dependabot/dependabot-security-updates/about-dependabot-security-updates).

You can also use default Dependabot auto-triage rules curated by GitHub to automatically filter out a substantial amount of false positives.

For an overview of the different features offered by Dependabot and instructions on how to get started, see [Dependabot quickstart guide](/en/code-security/getting-started/dependabot-quickstart-guide).

#### Dependabot malware alerts

On GitHub.com and GitHub Enterprise Server 3.22+, you can view alerts for malicious dependencies in your repository. See [Dependabot malware alerts](/en/code-security/concepts/supply-chain-security/dependabot-malware-alerts).

### Dependabot version updates

Use Dependabot to automatically raise pull requests to keep your dependencies up-to-date. This helps reduce your exposure to older versions of dependencies. Using newer versions makes it easier to apply patches if security vulnerabilities are discovered, and also makes it easier for Dependabot security updates to successfully raise pull requests to upgrade vulnerable dependencies. You can also customize Dependabot version updates to streamline their integration into your repositories. For more information, see [About Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/about-dependabot-version-updates).

### Security advisories

Privately discuss and fix security vulnerabilities in your public repository's code. You can then publish a security advisory to alert your community to the vulnerability and encourage community members to upgrade. For more information, see [About repository security advisories](/en/code-security/security-advisories/working-with-repository-security-advisories/about-repository-security-advisories).

### Repository rulesets

Enforce consistent code standards, security, and compliance across branches and tags. For more information, see [About rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

### Artifact attestations

Create unfalsifiable provenance and integrity guarantees for the software you build. For more information, see [Using artifact attestations to establish provenance for builds](/en/actions/security-for-github-actions/using-artifact-attestations/using-artifact-attestations-to-establish-provenance-for-builds).

> \[!NOTE]
> If you are on a GitHub Free, GitHub Pro, or GitHub Team plan, artifact attestations are only available for public repositories. To use artifact attestations in private or internal repositories, you must be on a GitHub Enterprise Cloud plan.

### Secret scanning alerts for partners

When GitHub detects a leaked secret in a public repository, or a public npm packages, GitHub informs the relevant service provider that the secret may be compromised. For details of the supported secrets and service providers, see [Supported secret scanning patterns](/en/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#supported-secrets).

### Push protection for users

Push protection for users automatically protects you from accidentally committing secrets to public repositories, regardless of whether the repository itself has secret scanning enabled. Push protection for users is on by default, but you can disable the feature at any time through your personal account settings. For more information, see [Managing push protection for users](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/push-protection-for-users).

## Available with GitHub Secret Protection

For accounts on GitHub Team and GitHub Enterprise Cloud, you can access additional security features when you purchase **GitHub Secret Protection**.

GitHub Secret Protection includes features that help you detect and prevent credential leaks and secret sprawl, such as secret scanning for detecting hardcoded credentials and push protection for blocking them before they reach your repository.

These features are available for all repository types. Some of these features are available for public repositories free of charge, meaning that you don't need to purchase GitHub Secret Protection to enable the feature on a public repository.

<!--Hiding information on setting up a trial for now, as there is no available link for fpt yet. Needs versioning for fpt, ghec and ghes.
For information about how you can try GitHub Secret Protection for free, see [AUTOTITLE](/billing/managing-billing-for-your-products/managing-billing-for-github-advanced-security/setting-up-a-trial-of-github-advanced-security).
-->

### Secret scanning alerts for users

Automatically detect hardcoded credentials that have been checked into a repository. You can view alerts for any secrets that GitHub finds in your code, in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of your repository, so you can respond to credential leaks quickly. For more information, see [About secret scanning](/en/code-security/secret-scanning/introduction/about-secret-scanning).

Available for public repositories by default.

### Copilot secret scanning

Copilot secret scanning's generic secret detection is an AI-powered expansion of secret scanning that identifies unstructured secrets (passwords) in your source code and then generates an alert. For more information, see [Responsible detection of generic secrets with Copilot secret scanning](/en/code-security/secret-scanning/copilot-secret-scanning/responsible-ai-generic-secrets).

### Push protection

Push protection proactively scans your code, and any repository contributors' code, for hardcoded secrets during the push process and blocks the push if any credential leaks are detected. If a contributor bypasses the block, an alert is generated. For more information, see [About push protection](/en/code-security/secret-scanning/introduction/about-push-protection).

Available for public repositories by default.

### Delegated bypass for push protection

Delegated bypass for push protection lets you control which individuals, roles, and teams:

* Can bypass push protection
* Are exempt from push protection
* Can review bypass requests from other contributors

For more information, see [About delegated bypass for push protection](/en/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/delegated-bypass-for-push-protection/about-delegated-bypass-for-push-protection).

### Custom patterns

You can define custom patterns to identify secrets that are not detected by the default patterns supported by secret scanning, such as patterns that are internal to your organization. For more information, see [Defining custom patterns for secret scanning](/en/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/custom-patterns/defining-custom-patterns-for-secret-scanning).

<!--Hiding security overview for earlier GHES versions, so it isn't duplicated below-->

### Security overview

Security overview allows you to review the overall security landscape of your organization, view trends and other insights, and manage security configurations, making it easy to monitor your organization's security status and identify the repositories and organizations at greatest risk. For more information, see [About security overview](/en/code-security/security-overview/about-security-overview).

## Available with GitHub Code Security

For accounts on GitHub Team and GitHub Enterprise Cloud, you can access additional security features when you purchase **GitHub Code Security**.

GitHub Code Security includes features that help you find and fix vulnerabilities, like code scanning, premium Dependabot features, and dependency review.

These features are available for all repository types. Some of these features are available for public repositories free of charge, meaning that you don't need to purchase GitHub Code Security to enable the feature on a public repository.

<!--Hiding information on setting up a trial for now, as there is no available link for fpt yet. Needs versioning for fpt, ghec & ghes.

For information about how you can try GitHub Code Security for free, see [AUTOTITLE](/billing/managing-billing-for-your-products/managing-billing-for-github-advanced-security/setting-up-a-trial-of-github-advanced-security).

-->

### Code scanning

Automatically detect security vulnerabilities and coding errors in new or modified code. Potential problems are highlighted, with detailed information, allowing you to fix the code before it's merged into your default branch. For more information, see [About code scanning](/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning).

Available for public repositories by default.

### CodeQL CLI

Run CodeQL processes locally on software projects or to generate code scanning results for upload to GitHub. For more information, see [About the CodeQL CLI](/en/code-security/codeql-cli/getting-started-with-the-codeql-cli/about-the-codeql-cli).

Available for public repositories by default.

### Copilot Autofix

Get automatically generated fixes for code scanning alerts. For more information, see [Responsible use of Copilot Autofix for code scanning](/en/code-security/code-scanning/managing-code-scanning-alerts/responsible-use-autofix-code-scanning).

Available for public repositories by default.

### Custom auto-triage rules for Dependabot

Help you manage your Dependabot alerts at scale. With custom auto-triage rules you have control over the alerts you want to ignore, snooze, or trigger a Dependabot security update for. For more information, see [About Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts) and [Customizing auto-triage rules to prioritize Dependabot alerts](/en/code-security/dependabot/dependabot-auto-triage-rules/customizing-auto-triage-rules-to-prioritize-dependabot-alerts).

### Dependency review

Show the full impact of changes to dependencies and see details of any vulnerable versions before you merge a pull request. For more information, see [About dependency review](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review).

Available for public repositories by default.

### Security campaigns

Fix security alerts at scale by creating security campaigns and collaborating with developers to reduce your security backlog. For more information, see [About security campaigns](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/about-security-campaigns).

### Security overview

Security overview allows you to review the overall security landscape of your organization, view trends and other insights, and manage security configurations, making it easy to monitor your organization's security status and identify the repositories and organizations at greatest risk. For more information, see [About security overview](/en/code-security/security-overview/about-security-overview).

## Further reading

* [GitHub's plans](/en/get-started/learning-about-github/githubs-plans)
* [About GitHub Advanced Security](/en/get-started/learning-about-github/about-github-advanced-security)
* [GitHub language support](/en/get-started/learning-about-github/github-language-support)