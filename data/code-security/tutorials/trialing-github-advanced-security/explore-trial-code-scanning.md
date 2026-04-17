# Exploring your enterprise trial of GitHub Code Security

Introduction to the features of code and dependency scanning available with GitHub Code Security in GitHub Enterprise Cloud so you can assess their fit to your business needs.

This guide assumes that you have planned and started a trial of GitHub Advanced Security for an existing or trial GitHub enterprise account, see [Planning a trial of GitHub Advanced Security](/en/code-security/trialing-github-advanced-security/planning-a-trial-of-ghas).

## Introduction

Code scanning and dependency analysis work in the same way in public repositories and in private and internal repositories with Code Security enabled. In addition, Code Security enables you to create security campaigns where security specialists and developers can collaborate to effectively reduce technical debt.

This article focuses on how you can combine these features with enterprise-level controls to standardize and enforce your development process.

### Refine your security configurations

In contrast to Secret Protection, where a single security configuration is typically applied to all repositories, you probably want to fine-tune the configuration of code scanning for different types of repositories. For example, you might need to create additional configurations so that:

* Code scanning uses runners with a specific label to apply to repositories that require a specialized environment or that use private registries.
* Code scanning is "Not set" to apply to repositories that need to use advanced setup or that require a third-party tool.

For your trial, it's simplest to create a primary enterprise-level security configuration and apply it to your test repositories. Then you can create any additional security configurations you need and apply them to a subset of repositories selected using code language, custom property, visibility, and  other filter options. For more information, see [Enabling security features in your trial enterprise](/en/code-security/trialing-github-advanced-security/enable-security-features-trial) and [Applying a custom security configuration](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/applying-a-custom-security-configuration).

### Provide access to view results of code scanning

By default, only the repository administrator and the organization owner can view all code scanning alerts in their area. You should assign the predefined security manager role to all organization teams and users who you want to access the alerts found during the trial. You may also want to give the enterprise account owner this role for each organization in the trial. For more information, see [Managing security managers in your organization](/en/organizations/managing-peoples-access-to-your-organization-with-roles/managing-security-managers-in-your-organization) and [Using organization roles](/en/organizations/managing-peoples-access-to-your-organization-with-roles/using-organization-roles#assigning-an-organization-role).

## Evaluate and refine results from the default setup

The default setup for code scanning runs a set of high confidence queries. These are chosen to ensure that, when you roll out code scanning across your whole codebase, developers see a limited set of high quality results, with few false positive results.

You can see a summary of any results found in the organizations in your trial enterprise in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for the enterprise. There are also separate views for each type of security alert. See [Viewing security insights](/en/code-security/security-overview/viewing-security-insights).

If you don't see the results you expect for code scanning, you can update default setup to run an extended query suite for repositories where you expected to find more results. This is controlled at the repository level, see [Editing your configuration of default setup](/en/code-security/code-scanning/managing-your-code-scanning-configuration/editing-your-configuration-of-default-setup).

> \[!TIP]
> If you are blocked from editing the repository settings for code scanning, edit the security configuration used by the repository so that settings are not enforced.

If the extended suite still fails to find the results you expect, you may need to enable advanced setup so you can customize the analysis fully. For more information, see [Use the tool status page for code scanning](/en/code-security/code-scanning/managing-your-code-scanning-configuration/about-the-tool-status-page) and [Configuring advanced setup for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/configuring-advanced-setup-for-code-scanning).

## Enforce automated analysis of pull requests

There are three different types of automated analysis of pull requests built into GitHub:

* **Code scanning analysis** uses queries to highlight known bad coding patterns and security vulnerabilities. Copilot Autofix suggests fixes to problems identified by code scanning.
* **Dependency review** summarizes the dependency changes made by the pull request and highlights any dependencies with known vulnerabilities or that do not meet your development standards.
* **Copilot code review** uses AI to provide feedback on your changes with suggested fixes where possible.

These automated reviews are a valuable extension to self-review and make it easier for developers to present a more complete and secure pull request for peer review. In addition, code scanning and dependency reviews can be enforced to protect the security and compliance of your code.

> \[!NOTE]
> GitHub Copilot Autofix is included in the license for GitHub Code Security. Copilot code review requires a paid Copilot plan.

### Code scanning analysis

When code scanning is enabled, you can then block merges into important branches unless the pull request meets your requirements by creating a code ruleset for the enterprise or organization. Typically, you would require that results from code scanning are present and that any important alerts are resolved.

* **Type of ruleset:** Branch.
* **Require code scanning results:** Enable to block merging until results are successfully generated for the commit and the reference the pull request targets.
* **Required tools and alert thresholds:** Define the level of alerts that must be resolved before a pull request can be merged for each code scanning tool you use.

As with all rulesets, you can control exactly which organizations (enterprise-level), repositories, and branches it acts on and also define roles or teams who can bypass the rule. For more information, see [About rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

### Dependency review

When Code Security and dependency graph are enabled for a repository, manifest files have a rich diff view which shows a summary of the dependencies that it adds or updates. This is a useful summary for human reviewers of the pull request but does not provide any control of which dependencies are added to the codebase.

Most enterprises put automatic checks in place to block the use of dependencies with known vulnerabilities or unsupported license terms.

1. Create a private repository to serve as a central home where you can store reusable workflows for the enterprise.
2. Edit the actions settings for the repository to allow all private repositories in the enterprise to access workflows in this central repository, see [Allowing access to components in a private repository](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#allowing-access-to-components-in-a-private-repository).
3. In the central repository, create a reusable workflow to run the dependency review action, configuring the action to meet your business needs, see [Configuring the dependency review action](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/configuring-the-dependency-review-action).
4. In each organization, create or update branch rulesets to add the new workflow to the required status checks, see [Enforcing dependency review across an organization](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/enforcing-dependency-review-across-an-organization).

This allows you to update the configuration in a single location, but use the workflow in many repositories. You may want to use this central repository to maintain other workflows. For more information, see [Reuse workflows](/en/actions/sharing-automations/reusing-workflows).

### Copilot code review

> \[!NOTE]
>
> * If you get a Copilot subscription from an organization, you will only be able to participate in the public preview on the GitHub website if an owner of your organization or enterprise has enabled Copilot code review. See [Managing policies and features for GitHub Copilot in your organization](/en/enterprise-cloud@latest/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies#opting-in-to-previews-or-feedback) and [Managing policies and features for GitHub Copilot in your enterprise](/en/enterprise-cloud@latest/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies) in the GitHub Enterprise Cloud documentation.

By default, users request a review from Copilot in the same way as they do from human reviewers. However, you can update or create an organization-level branch ruleset to automatically add Copilot as a reviewer to all pull requests made to selected branches in all or selected repositories. See [Configuring automatic code review by GitHub Copilot](/en/enterprise-cloud@latest/copilot/how-tos/agents/copilot-code-review/automatic-code-review) in the GitHub Enterprise Cloud documentation.

Copilot leaves a review comment on each pull request it reviews, without approving the pull request or requesting changes. This ensures that its review is advisory and will not block development work. Similarly, you should not enforce the resolution of suggestions made by Copilot because AI suggestions have known limitations, see [Responsible use of GitHub Copilot code review](/en/enterprise-cloud@latest/copilot/responsible-use-of-github-copilot-features/responsible-use-of-github-copilot-code-review#limitations-of-github-copilot-code-review) in the GitHub Enterprise Cloud documentation.

## Define where Copilot Autofix is allowed and enabled

Copilot Autofix helps developers understand and fix code scanning alerts found in their pull requests. We recommend that you enable this feature for all repositories with Code Security enabled to help developers resolve alerts efficiently and increase their understanding of secure coding.

There are two levels of control:

* Enterprises can allow or block use of Copilot Autofix throughout the enterprise using an "Advanced Security" policy, see: [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-code-security-and-analysis-for-your-enterprise).
* Organizations can enable or disable Copilot Autofix for all organization-owned repositories in the "Global settings" for the organization, see [Configuring global security settings for your organization](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/configuring-global-security-settings-for-your-organization).

## Engage developers in security remediation

Security campaigns provide a way for security teams to engage with developers to remediate security technical debt. They also provide a practical way to combine education in secure coding with examples of vulnerable code in code that your developers are familiar with. For more information, see [About security campaigns](/en/enterprise-cloud@latest/code-security/securing-your-organization/fixing-security-alerts-at-scale/about-security-campaigns) and [Running a security campaign to fix alerts at scale](/en/enterprise-cloud@latest/code-security/securing-your-organization/fixing-security-alerts-at-scale/best-practice-fix-alerts-at-scale) in the GitHub Enterprise Cloud documentation.

## Provide a secure development environment

The development environment has many components. Some of the most useful features for scaling and standardizing a secure development environment in GitHub are:

* **Security configurations:** define the setup of security features for the enterprise, an organization, a subset of organization repositories, or new repositories, see [Refine your security configurations](#refine-your-security-configurations).
* **Policies:** protect and control use of resources for the enterprise or an organization, see [Enforcing policies for your enterprise](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise).
* **Rulesets:** protect and control branches, tags, and pushes for an organization, a subset of organization repositories, or a repository, see [Creating rulesets for repositories in your organization](/en/organizations/managing-organization-settings/creating-rulesets-for-repositories-in-your-organization).
* **Repository templates:** define the security workflows and processes needed for each type of environment, see [Creating a template repository](/en/repositories/creating-and-managing-repositories/creating-a-template-repository). For example, each template might contain a specialized:
  * Security policy file defining the company's security stance and how to report any security concerns.
  * Workflow to enable Dependabot version updates for package managers used by the company.
  * Workflow defining advanced setup for code scanning for supported development languages where the default setup results are not enough.

In addition, when a developer creates a repository from a template they must define the value of any required custom properties. Custom properties are very useful for selecting a subset of repositories that you want to apply configurations, policies, or rulesets to, see [Managing custom properties for repositories in your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-repositories-in-your-enterprise/managing-custom-properties-for-repositories-in-your-enterprise) in the GitHub Enterprise Cloud documentation.

## Next steps

When you have finished exploring these options and secret scanning features, you are ready to test your discoveries so far against your business needs, and then explore further.

## Further reading

* [Secure use reference](/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions)
* [Enforcing policies for your enterprise](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise)
* [Governing how people use repositories in your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-repositories-in-your-enterprise/governing-how-people-use-repositories-in-your-enterprise) in the GitHub Enterprise Cloud documentation
* [Enforce GitHub Advanced Security at Scale](https://wellarchitected.github.com/library/application-security/recommendations/enforce-ghas-at-scale/)