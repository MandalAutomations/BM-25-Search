# Helping others review your changes

You can use pull requests to provide clear context for your changes and keep your team informed, improving collaboration and the quality of reviews.

When you create a pull request, you’re asking your team to review your changes and provide feedback. This guide provides best practices for creating pull requests that are easy to review and keep your team informed, so that you can improve collaboration and the quality of reviews.

## Making your changes easy to review

Clear context in your pull requests helps reviewers quickly see what you’ve changed and why it matters. This makes the review process faster and smoother, with less back-and-forth, and helps your team give better feedback and make confident decisions. For information on creating a pull request, see [Creating a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request).

### Write small pull requests

Aim to create small, focused pull requests that fulfill a single purpose. Smaller pull requests are easier and faster to review and merge, leave less room to introduce bugs, and provide a clearer history of changes.

### Provide context and guidance

Write clear titles and descriptions for your pull requests so that reviewers can quickly understand what the pull request does. In the pull request body, include:

* The purpose of the pull request
* An overview of what changed
* Links to any additional context such as tracking issues or previous conversations

To help reviewers, share the type of feedback you need. For example, do you need a quick look or a deeper critique? Additionally, you can use GitHub Copilot to generate a summary of your pull request. See [Use GitHub Copilot to generate pull request summaries](#use-github-copilot-to-generate-pull-request-summaries), later in this article.

If your pull request consists of changes to multiple files, provide guidance to reviewers about the order in which to review the files. Recommend where to start and how to proceed with the review.

### Review your own pull request first

Review, build, and test your own pull request before submitting it. This will allow you to catch errors or typos that you may have missed, before others start reviewing.

### Review for security

There are various tools available that can help you review your pull request for potential security issues before others review it. Reviewing for security helps to catch and resolve security issues early, and lets you highlight unresolved risks for others to review and advise on. For example, you can:

* Check the dependency diff to see if your pull request is introducing vulnerable dependencies. See [Reviewing dependency changes in a pull request](/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-dependency-changes-in-a-pull-request).
* Check the GitHub Advisory Database to find additional context and information on vulnerable dependencies.
* Investigate and resolve any failing security checks or workflows, such as the dependency review action or the code scanning results check. See [About dependency review](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review#about-the-dependency-review-action) and [Triaging code scanning alerts in pull requests](/en/code-security/code-scanning/managing-code-scanning-alerts/triaging-code-scanning-alerts-in-pull-requests#about-code-scanning-as-a-pull-request-check).
* If your repository has set up code scanning as a pull request check, use GitHub Copilot Autofix to suggest fixes for security vulnerabilities in your code. See [Triaging code scanning alerts in pull requests](/en/code-security/code-scanning/managing-code-scanning-alerts/triaging-code-scanning-alerts-in-pull-requests#working-with-copilot-autofix-suggestions-for-alerts-on-a-pull-request).

## Keeping your team informed

Pull requests can do more than just document code changes—they’re also a powerful way to keep your team and manager informed about the status of your work. By making your progress visible in your pull requests, you can reduce the need for separate updates and ensure everyone stays aligned.

### Use GitHub Copilot to generate pull request summaries

> \[!NOTE] You'll need access to GitHub Copilot. For more information, see [What is GitHub Copilot?](/en/copilot/about-github-copilot/what-is-github-copilot#getting-access-to-copilot).

You can use Copilot to generate a summary of a pull request on GitHub. You can use the summary to help reviewers understand your changes.

1. On GitHub, create a pull request or navigate to an existing pull request.

   > \[!NOTE] Copilot does not take into account any existing content in the pull request description, so it is best to start with a blank description.

2. Navigate to the text field where you want to add the pull request summary.

   * If you're creating a new pull request, use the "Add a description" field.
   * If you're adding a description to an existing pull request, edit the opening comment.
   * If you're adding a summary as a comment, navigate to the "Add a comment" section at the bottom of the pull request page.

3. In the header of the text field, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Copilot actions" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>, then click **Summary**.

   ![Screenshot of the form for creating a pull request. A Copilot icon is highlighted, and a box appears with the "Summary" command.](/assets/images/help/copilot/copilot-description-suggestion.png)

4. Wait for Copilot to produce the summary, then check over the results carefully.

5. Add any additional context that will help people viewing your pull request.

6. When you're happy with the description, click **Create pull request** on a new pull request, or **Update comment** if you're editing an existing description.

> \[!TIP] You can also use Copilot Chat to turn your work into a discussion or blog post. See [Writing discussions or blog posts](/en/copilot/copilot-chat-cookbook/documenting-code/writing-discussions-or-blog-posts).

### Link to related issues or projects

Connect your pull request to relevant issues or project boards to show how your work fits into the larger project.

* Add keywords like `Closes ISSUE-LINK` in your description to automatically link and close the issue when the pull request is merged.
* Use Projects to track your work and link to the project from your pull request, making progress easy to track in one place. See [About Projects](/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).

### Highlight the status with labels

Add a status label to your pull request to show whether it’s ready for review, blocked, or in progress. This helps reviewers understand the state of your work at a glance. For more information, see [Managing labels](/en/issues/using-labels-and-milestones-to-track-work/managing-labels).