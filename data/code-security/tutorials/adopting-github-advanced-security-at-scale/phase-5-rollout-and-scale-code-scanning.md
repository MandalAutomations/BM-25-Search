# Phase 5: Rollout and scale code scanning

You can use security configurations to rollout code scanning across your enterprise.

> \[!TIP]
> This article is part of a series on adopting GitHub Advanced Security at scale. For the previous article in this series, see [Phase 4: Create internal documentation](/en/enterprise-cloud@latest/code-security/adopting-github-advanced-security-at-scale/phase-4-create-internal-documentation).

You can quickly enable security features at scale with a security configuration, a collection of security enablement settings you can apply to repositories in an organization. You can customize Advanced Security features at the organization level with global settings. See [About enabling security features at scale](/en/enterprise-cloud@latest/code-security/securing-your-organization/introduction-to-securing-your-organization-at-scale/about-enabling-security-features-at-scale).

## Enabling code scanning

After piloting code scanning and creating internal documentation for best practices, you can enable code scanning across your company. You can configure code scanning default setup for all repositories in an organization from security overview. For more information, see [Configuring default setup for code scanning at scale](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning-at-scale#configuring-default-setup-for-all-eligible-repositories-in-an-organization).

For some languages or build systems, you may need to instead configure advanced setup for code scanning to get full coverage of your codebase. However, advanced setup requires significantly more effort to configure, customize, and maintain, so we recommend enabling default setup first.

## Building subject matter expertise

To successfully manage and use code scanning across your company, you should build internal subject matter expertise. For default setup for code scanning, one of the most important areas for subject matter experts (SMEs) to understand is interpreting and fixing code scanning alerts. For more information about code scanning alerts, see:

* [About code scanning alerts](/en/enterprise-cloud@latest/code-security/code-scanning/managing-code-scanning-alerts/about-code-scanning-alerts)
* [Assessing code scanning alerts for your repository](/en/enterprise-cloud@latest/code-security/code-scanning/managing-code-scanning-alerts/assessing-code-scanning-alerts-for-your-repository)
* [Resolving code scanning alerts](/en/enterprise-cloud@latest/code-security/code-scanning/managing-code-scanning-alerts/resolving-code-scanning-alerts)

You'll also need SMEs if you need to use advanced setup for code scanning. These SMEs will need knowledge of code scanning alerts, as well as topics like GitHub Actions and customizing code scanning workflows for particular frameworks. For custom configurations of advanced setup, consider running meetings on complicated topics to scale the knowledge of several SMEs at once.

For code scanning alerts from CodeQL analysis, you can use security overview to see how CodeQL is performing in pull requests in repositories across your organization, and to identify repositories where you may need to take action. For more information, see [CodeQL pull request alert metrics](/en/enterprise-cloud@latest/code-security/concepts/code-scanning/pull-request-alert-metrics).

With a GitHub Copilot Enterprise license, you can also ask GitHub Copilot Chat for help to better understand code scanning alerts in repositories in your organization. For more information, see [Asking GitHub Copilot questions in GitHub](/en/enterprise-cloud@latest/copilot/using-github-copilot/asking-github-copilot-questions-in-githubcom#asking-questions-about-alerts-from-github-advanced-security-features).

> \[!TIP]
> For the next article in this series, see [Phase 6: Rollout and scale secret scanning](/en/enterprise-cloud@latest/code-security/adopting-github-advanced-security-at-scale/phase-6-rollout-and-scale-secret-scanning).