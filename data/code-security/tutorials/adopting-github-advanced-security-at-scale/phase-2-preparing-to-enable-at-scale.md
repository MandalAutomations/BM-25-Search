# Phase 2: Preparing to enable at scale

In this phase you will prepare developers and collect data about your repositories to ensure your teams are ready and you have everything you need for pilot programs and rolling out code scanning and secret scanning.

> \[!TIP]
> This article is part of a series on adopting GitHub Advanced Security at scale. For the previous article in this series, see [Phase 1: Align on your rollout strategy and goals](/en/enterprise-cloud@latest/code-security/adopting-github-advanced-security-at-scale/phase-1-align-on-your-rollout-strategy-and-goals).

## Preparing to enable code scanning

Code scanning is a feature that you use to analyze the code in a GitHub repository to find security vulnerabilities and coding errors. Any problems identified by the analysis are shown in your repository. For more information, see [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning).

Rolling code scanning out across hundreds of repositories can be difficult, especially when done inefficiently. Following these steps will ensure your rollout is both efficient and successful.

Code scanning is also available for all public repositories on GitHub.com without a license for prodname\_GH\_code\_security.

### Preparing teams for code scanning

First, prepare your teams to use code scanning. The more teams that use code scanning, the more data you'll have to drive remediation plans and monitor progress on your rollout.

For an introduction to code scanning, see:

* [About code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)
* [About code scanning alerts](/en/enterprise-cloud@latest/code-security/code-scanning/managing-code-scanning-alerts/about-code-scanning-alerts)
* [Assessing code scanning alerts for your repository](/en/enterprise-cloud@latest/code-security/code-scanning/managing-code-scanning-alerts/assessing-code-scanning-alerts-for-your-repository)

Your core focus should be preparing as many teams to use code scanning as possible. You can also encourage teams to remediate appropriately, but we recommend prioritizing enablement and use of code scanning over fixing issues during this phase.

## Preparing to enable secret scanning

> \[!NOTE]
> When a secret is detected in a repository that has enabled secret scanning, GitHub alerts all users with access to security alerts for the repository.
>
> Secrets found in public repositories using secret scanning alerts for partners are reported directly to the partner, without creating an alert on GitHub. For details about the supported partner patterns, see [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#supported-secrets).

If a project communicates with an external service, it might use a token or private key for authentication. If you check a secret into a repository, anyone who has read access to the repository can use the secret to access the external service with your privileges. Secret scanning will scan your entire Git history on all branches present in your GitHub repositories for secrets and alert you or block the push containing the secret. For more information, see [About secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/introduction/about-secret-scanning).

Secret scanning alerts for partners runs automatically on public repositories and public npm packages to notify service providers about leaked secrets on GitHub.

Secret scanning alerts for users are available for free on all public repositories.

### Considerations when enabling secret scanning

Enabling secret scanning at the organizational level can be easy, but clicking **Enable All** at the organization level and selecting the option **Automatically enable secret scanning for every new repository** has some downstream effects that you should be aware of:

#### License consumption

Enabling secret scanning for all repositories will maximize your use of GitHub Secret Protection licenses. This is fine if you have enough licenses for the current committers to all those repositories. If the number of active developers is likely to increase in the coming months, you may exceed your license limit and then be unable to use secret scanning on newly created repositories.

#### Initial high volume of detected secrets

If you are enabling secret scanning on a large organization, be prepared to see a high number of secrets found. Sometimes this comes as a shock to organizations and the alarm is raised. If you would like to turn on secret scanning across all repositories at once, plan for how you will respond to multiple alerts across the organization.

Secret scanning can be enabled for individual repositories. For more information, see [Enabling secret scanning for your repository](/en/enterprise-cloud@latest/code-security/secret-scanning/enabling-secret-scanning-features/enabling-secret-scanning-for-your-repository). Secret scanning can also be enabled for all repositories in your organization, as described above. For more information on enabling for all repositories, see [Managing security and analysis settings for your organization](/en/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization).

### Custom patterns for secret scanning

Secret scanning detects a large number of default patterns but can also be configured to detect custom patterns, such as secret formats unique to your infrastructure or used by integrators that GitHub's secret scanning does not currently detect. For more information about supported secrets for partner patterns, see [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/introduction/supported-secret-scanning-patterns).

As you audit your repositories and speak to security and developer teams, build a list of the secret types that you will later use to configure custom patterns for secret scanning. For more information, see [Defining custom patterns for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/custom-patterns/defining-custom-patterns-for-secret-scanning).

### Push protection for secret scanning

Push protection for organizations and repositories instructs secret scanning to check pushes for supported secrets *before* secrets are committed to the codebase. For information on which secrets are supported, see [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#supported-secrets).

If a secret is detected in a push, that push is blocked. Secret scanning lists any secrets it detects so the author can review the secrets and remove them or, if needed, allow those secrets to be pushed. Secret scanning can also check pushes for custom patterns.

Developers have the option to bypass push protection by reporting that a secret is a false positive, that it is used in tests, or that it will be fixed later.

When a contributor bypasses a push protection block, GitHub:

* Creates an alert in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of the repository, organization, and enterprise
* Adds the bypass event to the audit log
* Sends an email alert to personal account, organization, and enterprise owners, security managers, and repository administrators who are watching the repository, with a link to the secret and the reason it was allowed

Before enabling push protection, consider whether you need to create guidance for developer teams on the acceptable conditions for bypassing push protection. You can configure a link to this resource in the message that's displayed when a developer attempts to push a blocked secret.

Next, familiarize yourself with the different options for managing and monitoring alerts that are the result of a contributor bypassing push protection.

For more information, see [About push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/introduction/about-push-protection).

## Next steps

For the next article in this series, see [Phase 3: Pilot programs](/en/enterprise-cloud@latest/code-security/adopting-github-advanced-security-at-scale/phase-3-pilot-programs).