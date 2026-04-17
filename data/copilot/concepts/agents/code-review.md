# About GitHub Copilot code review

Find out how Copilot can review pull requests for you.

## Introduction

Copilot code review reviews code written in any language, and provides feedback. It reviews your code from multiple angles to identify issues and suggest fixes. You can apply suggested changes with a couple of clicks.

This article provides an overview of Copilot code review. To learn how to request a code review from Copilot, see [Using GitHub Copilot code review](/en/copilot/how-tos/agents/copilot-code-review/using-copilot-code-review).

## Availability

Copilot code review is supported in:

* GitHub.com
* GitHub CLI
* GitHub Mobile
* VS Code
* Visual Studio
* Xcode
* JetBrains IDEs

Copilot code review is a premium feature available with these plans:

* Copilot Pro
* Copilot Pro+
* Copilot Business
* Copilot Enterprise

See [Copilot plans](https://github.com/features/copilot/plans?ref_product=copilot\&ref_type=purchase\&ref_style=text).

If you receive Copilot from an organization, your organization must enable the **Copilot code review** option in the Copilot policy settings. This applies to reviews on GitHub.com or in GitHub Mobile. See [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer/organizations/managing-policies-for-copilot-in-your-organization).

## Copilot code review without a Copilot license

Organization members **without a Copilot license** can use Copilot code review on GitHub.com. An enterprise administrator or organization owner must enable it. This capability is available to organizations on **Copilot Business** and **Copilot Enterprise** plans.

### Enabling code review for users without a license

To allow organization members without a Copilot license to use Copilot code review, you must enable two policies:

1. **Premium request paid usage**. Enable this policy first. It allows the enterprise or organization to incur charges for Copilot code review premium request usage.
2. **Allow members without a Copilot license to use Copilot code review in GitHub.com**. This sub-policy enables Copilot code review for users without a license.

The second policy has these characteristics:

* It is disabled by default.
* Once this policy is set it at the enterprise level, it becomes **visible, but not editable** at the organization level.
* The policy is **most restrictive**. Copilot code review is only available in repositories where you explicitly enable the policy.

### How it works for users without a license

When both policies are enabled, users without a Copilot license can request a review from Copilot code review on their pull requests in the organization's repositories.

In repositories where automatic code review is enabled, Copilot automatically reviews all pull requests. This happens regardless of whether the author has a Copilot license.

Copilot code review for users without a license is not available in IDEs.

## Excluded files

Some file types are excluded from Copilot code review:

* Dependency management files, such as package.json and Gemfile.lock
* Log files
* SVG files

If you include these file types in a pull request, Copilot code review will not review the file.

For more information, see [Files excluded from GitHub Copilot code review](/en/copilot/reference/review-excluded-files).

## Agentic capabilities for Copilot code review

> \[!NOTE]
>
> * Copilot code review has capabilities that are in public preview and subject to change. The [GitHub Pre-release License Terms](/en/site-policy/github-terms/github-pre-release-license-terms) apply to your use of preview features.

Copilot code review utilizes agentic capabilities to extend its functionality.

* **Full project context gathering**. This provides more specific, accurate, and contextually aware code reviews. This capability analyzes your entire repository to better understand the context of code changes. Full project context gathering is generally available.
* **The ability to pass suggestions to Copilot cloud agent**. This automates creating a new pull request against your branch with the suggested fixes applied. Passing suggestions to Copilot cloud agent is in public preview and subject to change.

These capabilities are enabled automatically for Copilot Pro or Copilot Pro+ plans.

If GitHub Actions is unavailable or if Actions workflows used by Copilot code review fail, reviews will still be generated. However, they will not include the additional features provided by the agentic capabilities.

### Usage of GitHub Actions runners for agentic capabilities in code review

Copilot code review uses free minutes for GitHub Actions to run the agentic capabilities, including full project context gathering and any capabilities in public preview. By default, Copilot code review uses GitHub-hosted runners. You can also upgrade to larger GitHub-hosted runners for better performance.

> \[!NOTE]
> Usage of larger GitHub-hosted runners is billed per-minute and may incur additional GitHub Actions charges.

You do not need to have GitHub Actions enabled in your organization or enterprise to use the agentic capabilities in code review.

If your organization has disabled GitHub-hosted runners, the agentic capabilities will not be available. In this case, code reviews will fall back to a more limited review. Organizations in this situation can use self-hosted runners.

For more information on configuring runners, see [Configuring runners for GitHub Copilot code review](/en/copilot/how-tos/copilot-on-github/set-up-copilot/configure-runners).

## Code review monthly quota

Each time Copilot reviews a pull request or reviews code in your IDE, your monthly quota of Copilot premium requests is reduced by one.

If a repository is configured to automatically request a code review from Copilot for all new pull requests, the premium request usage is applied to the pull request author's quota. If a review is manually requested by another user, the usage is applied to that user's quota instead.

If a pull request is created by GitHub Actions or by a bot, the usage will apply to:

* The user who triggered the workflow, if that user can be identified.
* A designated billing owner.

### What happens when you reach your quota

When you reach your monthly quota, you will not be able to get a code review from Copilot until your quota resets. To continue to use code reviews before your quota resets, you will need to upgrade your Copilot plan or enable additional premium requests.

### Users without a Copilot license or plan that includes Copilot code review

Users without access to Copilot code review do not have a monthly premium request quota. This includes users who have no Copilot license and users on the Copilot Free plan, which does not include Copilot code review.

When Copilot code review is enabled for these users, any premium requests they generate are billed directly to the organization or enterprise as paid overage usage. This applies to both manually requested reviews and automatic code reviews.

Premium requests generated by these users are not attributed to any Copilot plan quota. They appear as overage usage in billing reports and premium request analytics. Users with a Copilot license that includes code review continue to consume premium requests from their assigned plan quota.

## Model usage

Copilot code review is a purpose-built product that uses a carefully tuned mix of models, prompts, and system behaviors to deliver consistent, high-quality feedback across a wide range of codebases. Model switching is not supported, as changing the model is likely to compromise reliability, user experience, and the quality of review comments.

> \[!NOTE]
> Copilot code review may use models that are not enabled on your organization's "Models" settings page. The "Models" settings page only controls Copilot Chat.
>
> Since Copilot code review is generally available, all model usage will be subject to the generally available terms. See [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies).

## Validating Copilot code reviews

Copilot is not guaranteed to spot all problems or issues in a pull request. Sometimes it will make mistakes. Always validate Copilot's feedback carefully. Supplement Copilot's feedback with a human review.

For more information, see [Responsible use of GitHub Copilot code review](/en/copilot/responsible-use-of-github-copilot-features/responsible-use-of-github-copilot-code-review).

## Enhancing Copilot's knowledge of a repository

The more Copilot knows about the code in your repository, the tools you use, and your coding standards and practices, the more accurate and useful its reviews will become. You can enhance Copilot's knowledge of your repositories in two ways.

### Custom instructions

These are short, natural-language statements that you write and store as one or more files in a repository. If you are the owner of an organization on GitHub, you can also define custom instructions in the settings for your organization. For more information, see [About customizing GitHub Copilot responses](/en/copilot/concepts/prompting/response-customization?tool=webui#about-repository-custom-instructions).

### Copilot Memory (public preview)

If you have a Copilot Pro or Copilot Pro+ plan, you can enable Copilot Memory. This allows Copilot to store useful details it has learned about a repository. Copilot can then use this information when it reviews pull requests in that repository. For more information, see [About agentic memory for GitHub Copilot](/en/copilot/concepts/agents/copilot-memory).

## About automatic pull request reviews

By default, Copilot only reviews a pull request if you assign it to the pull request. However, you can configure automatic reviews.

* **Individual users** on the Copilot Pro or Copilot Pro+ plan can configure Copilot to automatically review all pull requests they create.
* **Repository owners** can configure Copilot to automatically review all pull requests in the repository that are created by people with access to Copilot.
* **Organization owners** can configure Copilot to automatically review all pull requests in some or all of the repositories in the organization where the pull request is created by a Copilot user.

### Triggering an automatic pull request review

The triggers for automatic code review depend on the configuration settings.

* Basic setting:
  * When you create a pull request as an "Open" pull request.
  * The first time you switch a "Draft" pull request to "Open".
* Review new pushes:
  * Every time you push a new commit to the pull request.
* Review draft pull requests:
  * Pull requests are automatically reviewed while they are still drafts, before you switch them to "Open".

For full instructions, see [Configuring automatic code review by GitHub Copilot](/en/copilot/how-tos/agents/copilot-code-review/configuring-automatic-code-review-by-copilot).

> \[!NOTE]
> Unless Copilot has been configured to review each push to a pull request, it will only review a pull request once. If you make changes to the pull request after it has been automatically reviewed and you want Copilot to re-review it, you can request this manually. Click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-sync" aria-label="Re-request review" role="img"><path d="M1.705 8.005a.75.75 0 0 1 .834.656 5.5 5.5 0 0 0 9.592 2.97l-1.204-1.204a.25.25 0 0 1 .177-.427h3.646a.25.25 0 0 1 .25.25v3.646a.25.25 0 0 1-.427.177l-1.38-1.38A7.002 7.002 0 0 1 1.05 8.84a.75.75 0 0 1 .656-.834ZM8 2.5a5.487 5.487 0 0 0-4.131 1.869l1.204 1.204A.25.25 0 0 1 4.896 6H1.25A.25.25 0 0 1 1 5.75V2.104a.25.25 0 0 1 .427-.177l1.38 1.38A7.002 7.002 0 0 1 14.95 7.16a.75.75 0 0 1-1.49.178A5.5 5.5 0 0 0 8 2.5Z"></path></svg> button next to Copilot's name in the **Reviewers** menu.

## Getting detailed code quality feedback for your whole repository

GitHub Copilot code review reviews your code in pull requests and provides feedback. If you want actionable feedback on the reliability and maintainability of your whole repository, enable GitHub Code Quality. See [About GitHub Code Quality](/en/code-security/code-quality/concepts/about-code-quality).

## Further reading

* [Using GitHub Copilot code review](/en/copilot/how-tos/agents/copilot-code-review/using-copilot-code-review)