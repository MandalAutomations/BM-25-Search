# Planning a trial of GitHub Advanced Security

Learn how to prepare for a successful trial of Advanced Security.

## Is a self-serve trial right for you?

This article is for organizations that want to begin a trial of GitHub Advanced Security independently, without the help of an expert or partner. Typically, that means you're a small or medium-sized organization.

This article helps you plan for a **self-serve** trial of GitHub Advanced Security. A self-serve trial is right for you if both of the following are true:

* You want to conduct your trial independently, without the help of an expert or partner. Typically, this works best for small or medium-sized organizations.
* You're an existing GitHub Enterprise Cloud customer who pays by credit card or PayPal.

Otherwise, contact us for help with your trial.

* If you want expert help: [Contact our team](https://github.com/enterprise/contact).
* If you pay by invoice: Contact your sales representative.

## 1. Define your company goals

Before you start a trial, you should define the purpose of the trial and identify the key questions you need to answer. Maintaining a strong focus on these goals will enable you to plan a trial that maximizes discovery and ensures that you have the information needed to decide whether or not to upgrade.

If your company already uses GitHub, consider what needs are currently unmet that Secret Protection or Code Security might address. You should also consider your current application security posture and longer term aims. For inspiration, see [Design Principles for Application security](https://wellarchitected.github.com/library/application-security/design-principles/) in the GitHub well-architected documentation.

<div class="ghd-tool rowheaders">

| Example need                               | Features to explore during the trial                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Enforce use of security features           | Enterprise-level security configurations and policies. See [About enabling security features at scale](/en/enterprise-cloud@latest/admin/managing-code-security/securing-your-enterprise/about-security-configurations) and [Enterprise policies](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/about-enterprise-policies)                                                                                                                                                                                                                                            |
| Protect custom access tokens               | Custom patterns for secret scanning, delegated bypass for push protection, and validity checks. See [Exploring your enterprise trial of GitHub Secret Protection](/en/code-security/trialing-github-advanced-security/explore-trial-secret-scanning)                                                                                                                                                                                                                                                                                                                                                                |
| Define and enforce a development process   | Dependency review, auto-triage rules, rulesets, and policies. See [About dependency review](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review), [About Dependabot auto-triage rules](/en/code-security/dependabot/dependabot-auto-triage-rules/about-dependabot-auto-triage-rules), [About rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets), and [Enterprise policies](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/about-enterprise-policies) |
| Reduce technical debt at scale             | Security campaigns. See [About security campaigns](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/about-security-campaigns).                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Monitor and track trends in security risks | Security overview. See [Viewing security insights](/en/code-security/security-overview/viewing-security-insights)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

</div>

If your company doesn't use GitHub yet, you are likely to have additional questions including how the platform handles data residency, secure account management, and repository migration. For more information, see [Getting started with GitHub Enterprise Cloud](/en/enterprise-cloud@latest/get-started/onboarding/getting-started-with-github-enterprise-cloud).

## 2. Identify the members of your trial team

GitHub Advanced Security enables you to integrate security measures throughout the software development life cycle, so it's important to ensure that you include representatives from all areas of your development cycle. Otherwise, you risk making a decision without having all the data you need. A trial includes 50 licenses which provides scope for representation from a wide range of people.

You may also find it helpful to identify a champion for each company need that you want to investigate.

## 3. Determine whether preliminary research is needed

Decide whether your team would benefit from hands-on experience with our free security features **before** you begin your trial. Testing code scanning and secret scanning on public repositories can help new users get familiar with the core features of GitHub Advanced Security. This will allow you to focus your trial period on private repositories and the advanced features and controls available in Secret Protection and Code Security.

For more information, see:

* [Enabling secret scanning for your repository](/en/code-security/secret-scanning/enabling-secret-scanning-features/enabling-secret-scanning-for-your-repository)
* [Configuring default setup for code scanning](/en/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning)
* [Enabling the dependency graph](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/configuring-the-dependency-graph)

Organizations on GitHub Team and GitHub Enterprise can run a free report to scan their code for leaked secrets. This helps you assess your repositories' current exposure to leaked secrets and shows how many existing secret leaks could have been prevented by Secret Protection. See [About secret security with GitHub](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/about-secret-risk-assessment).

## 4. Decide which organizations and repositories to test

It is generally best to start your trial with an **existing** organization. This ensures that you can experience the features in repositories you know well and within a familiar coding environment.

If you want, you can add test organizations or code later. However, be aware that deliberately insecure applications, such as WebGoat, are not the best test. They may contain coding patterns that appear to be insecure but which code scanning determines cannot be exploited. As a result, code scanning may report fewer issues in these artificial codebases than other security scanners.

## 5. Define the assessment criteria for the trial

For each company need or goal you set for the trial, decide how you will measure success. For example, if you want to enforce the use of security features, create test cases for security configurations and policies to confirm they work as expected.

## 6. Start your trial

If you already use GitHub Enterprise Cloud (as a paying customer or as part of a free trial), see [Setting up a trial of GitHub Advanced Security](/en/code-security/trialing-github-advanced-security/trial-advanced-security).

Otherwise, you can trial GitHub Advanced Security as part of a trial of GitHub Enterprise Cloud. See [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud) in the GitHub Enterprise Cloud documentation.

> \[!NOTE]
> GitHub Advanced Security is free of charge during trials, but you will be charged for any Actions minutes used by code scanning or any other workflows.