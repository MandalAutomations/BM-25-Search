# Managing and standardizing pull requests

Use these steps to manage and standardize the pull requests that contributors create in your repository.

If you are a repository maintainer, there are several ways that you can manage and standardize the pull requests that contributors create in your repository. These steps can help you ensure that pull requests are reviewed by the right people, and that they meet your repository's standards.

## Using pull request templates

Pull request templates let you customize and standardize the information you'd like to be included when someone creates a pull request in your repository. When you add a pull request template to your repository, project contributors will automatically see the template's contents in the pull request body. For more information, see [Creating a pull request template for your repository](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository).

You can use pull request templates to standardize the review process for your repository. For example, you can include a list of tasks that you would like authors to complete before merging their pull requests, by adding a task list to the template. For more information, see [About tasklists](/en/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists).

You can request that contributors include an issue reference in their pull request body, so that merging the pull request will automatically close the issue. For more information, see [Linking a pull request to an issue](/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue).

## Defining code owners

You may want to make sure that specific individuals always review changes to certain code or files in your repository. For example, you may want to ensure that a member of the security team always reviews changes to your `SECURITY.md` file or `dependabot.yml` file.

You can define individuals or teams that you consider responsible for code or files in a repository to be code owners. Code owners will automatically be requested for review when someone opens a pull request that modifies the files that they own. You can define code owners for specific types of files or directories, as well as for different branches in a repository. For more information, see [About code owners](/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners).

## Using protected branches

You can use protected branches to prevent pull requests from being merged into important branches, such as `main`, until certain conditions are met. For example, you can require an approving review, or require that all status checks are passing. See [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

## Using rulesets

Working alongside protected branches, rulesets let you enforce policies across your repository, such as requiring status checks or workflows to pass before a pull request can be merged.

Rulesets are especially useful for maintaining repository security when combined with other automated security checks. For example:

* You can use rulesets to enforce the dependency review action, a workflow that blocks pull requests that are introducing vulnerable dependencies into your codebase. See [Enforcing dependency review across an organization](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/enforcing-dependency-review-across-an-organization).
* If your repository is configured with code scanning, you can use rulesets to set code scanning merge protection, which prevents pull requests from being merged if there is a code scanning alert of a certain severity, or if a code scanning analysis is still in progress. See [Set code scanning merge protection](/en/code-security/code-scanning/managing-your-code-scanning-configuration/set-code-scanning-merge-protection).

## Using push rulesets

With push rulesets, you can block pushes to a private or internal repository and that repository's entire fork network based on file extensions, file path lengths, file and folder paths, and file sizes.

Push rules do not require any branch targeting because they apply to every push to the repository.

Push rulesets allow you to:

* **Restrict file paths:** Prevent commits that include changes in specified file paths from being pushed.

  You can use `fnmatch` syntax for this. For example, a restriction targeting `test/demo/**/*` prevents any pushes to files or folders in the `test/demo/` directory. A restriction targeting `test/docs/pushrules.md` prevents pushes specifically to the `pushrules.md` file in the `test/docs/` directory. For more information, see [Creating rulesets for a repository](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/creating-rulesets-for-a-repository#using-fnmatch-syntax).
* **Restrict file path length:** Prevent commits that include file paths that exceed a specified character limit from being pushed.
* **Restrict file extensions:** Prevent commits that include files with specified file extensions from being pushed.
* **Restrict file size:** Prevent commits that exceed a specified file size limit from being pushed.

### About push rulesets for forked repositories

Push rules apply to the entire fork network for a repository, ensuring every entry point to the repository is protected. For example, if you fork a repository that has push rulesets enabled, the same push rulesets will also apply to your forked repository.

For a forked repository, the only people who have bypass permissions for a push rule are the people who have bypass permissions in the root repository.

For more information, see [About rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets#push-rulesets).

## Using automated tools to review code styling

Use automated tools, such as linters, in your repository's pull requests to maintain consistent styling and make code more understandable. Using automated tools to catch smaller problems like typos or styling leaves more time for reviewers to focus on the substance of a pull request.

For example, you can use GitHub Actions to set up code linters that can run on pull requests as part of your continuous integration (CI) workflow. For more information, see [Continuous integration](/en/actions/automating-builds-and-tests/about-continuous-integration).