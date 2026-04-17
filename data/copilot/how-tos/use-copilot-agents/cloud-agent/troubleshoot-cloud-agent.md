# Troubleshooting GitHub Copilot cloud agent

Learn how to resolve problems that may occur when you assign tasks to Copilot.

## Copilot is not available in the "Assignees" list on my issue

You can only assign issues to Copilot if you have access to Copilot through either the **GitHub Copilot Pro** plan, **GitHub Copilot Pro+** plan, the **GitHub Copilot Business**  plan, or the **GitHub Copilot Enterprise** plan.

If you do not already have a subscription for one of these plans, click this button for more information:<br> <a href="https://github.com/features/copilot/plans?ref_product=copilot&ref_type=engagement&ref_style=button" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Sign up for Copilot</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

If you *do* have GitHub Copilot Pro, GitHub Copilot Pro+, GitHub Copilot Business, or GitHub Copilot Enterprise, check that Copilot cloud agent  has not been manually disabled for the repository:

* For organization-owned repositories, the availability of Copilot cloud agent in the repository is managed by the organization and/or enterprise administrators. See [Adding GitHub Copilot cloud agent to your organization](/en/enterprise-cloud@latest/copilot/how-tos/administer-copilot/manage-for-organization/add-copilot-cloud-agent).

* For personal repositories, the availability of Copilot cloud agent in the repository is configured in your account settings. See [Managing GitHub Copilot policies as an individual subscriber](/en/copilot/managing-copilot/managing-copilot-as-an-individual-subscriber/managing-your-copilot-plan/managing-copilot-policies-as-an-individual-subscriber#enabling-or-disabling-copilot-cloud-agent).

> \[!NOTE]
> You can check whether Copilot cloud agent has been enabled for you in the features page of your Copilot settings: [github.com/settings/copilot/features](https://github.com/settings/copilot/features).

## I have an Enterprise Managed User account and Copilot won't work in my personal repository

Copilot cloud agent is not available in personal repositories owned by managed user accounts. This is because Copilot cloud agent runs on GitHub-hosted runners, which are not available to personal repositories owned by managed user accounts. For more information, see [GitHub-hosted runners](/en/actions/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners).

<!--If you update this text, you may also need to update "Limitations in Copilot's compatibility with other features" in https://docs.github.com/en/copilot/using-github-copilot/cloud-agent/about-assigning-tasks-to-copilot  -->

If you have an managed user account and try to assign Copilot to an issue in a personal repository, you may see an error message reporting that GitHub Actions are not available for your repository.

To use Copilot cloud agent, you'll need to work with repositories owned by your organization instead of personal repositories.

## Copilot can't create a pull request from Copilot Chat

If you asked Copilot to create a pull request and it responds that it cannot directly create a pull request, check that Copilot cloud agent is available.

> \[!IMPORTANT]
> In VS Code, Visual Studio, and JetBrains IDEs, you must mention the `@github` chat participant in your prompt. You can omit this in Copilot Chat on GitHub.com.

## I assigned an issue to Copilot, but nothing is happening

Wait a while, then refresh the page. You should see Copilot leave an 👀 reaction on the issue. Shortly after this, Copilot will open a draft pull request linked to the issue, which will be shown in the issue timeline.

## Copilot has opened a pull request, but nothing is happening

If there is a "Copilot started work" event in the pull request timeline, click **View session** to see the session logs. These will stream live, and you will be able to see what Copilot is doing.

## Copilot won't respond to my pull request comments

Copilot only responds to comments from people who have write access to the repository.

If you do have write access, and you mention `@copilot` on a pull request that is assigned to Copilot, the comment is passed to Copilot cloud agent. An eyes emoji (👀) is added to your comment to indicate that Copilot cloud agent has seen your comment. Shortly after, a "Copilot started work" event is added to the pull request timeline.

If this doesn't happen, Copilot may have been unassigned from the pull request, or you may not have write access. Note that Copilot only responds to mentions in open pull requests. Once a pull request is merged or closed, Copilot cloud agent will not respond to new mentions or comments to better focus on active development work.

## Based on the agent session logs, Copilot appears to be stuck

Copilot can appear to be stuck for a while, and then get moving again.

If the session remains stuck, it will time out after an hour. You can retry by unassigning the issue and then reassigning it to Copilot.

If Copilot got stuck while responding to a comment, try adding the same comment to the pull request again.

## My GitHub Actions workflows are not running when Copilot pushes

GitHub Actions workflows will not run automatically when Copilot pushes changes to a pull request.

To allow GitHub Actions workflows to run, click the **Approve and run workflows** button in the pull request's merge box. See [Reviewing a pull request created by GitHub Copilot](/en/copilot/how-tos/use-copilot-agents/cloud-agent/review-copilot-prs).

## Copilot is pushing changes which don't pass my CI checks

While working on an issue, Copilot has access to its own ephemeral development environment, powered by GitHub Actions, where it can execute automated tests and linters to validate its work before it pushes.

It is most likely to do this if given clear instructions on what to do. The best way to do this is with a `.github/copilot-instructions.md` file. See [Best practices for using GitHub Copilot to work on tasks](/en/copilot/tutorials/cloud-agent/get-the-best-results#adding-custom-instructions-to-your-repository).

## There is a warning from GitHub Copilot about the firewall

By default, Copilot's access to the internet is limited by a firewall.

Limiting access to the internet helps to manage data exfiltration risks, where surprising behavior from Copilot or malicious instructions given to it could lead to code or other sensitive information being leaked to remote locations.

If Copilot tries to make a request which is blocked by the firewall, a warning is added to the pull request body (if Copilot is responding to an issue assignment) or to a comment (if Copilot is responding to a comment). The warning shows the blocked address and the command that tried to make the request.

![Screenshot of a warning from Copilot about being blocked by the firewall.](/assets/images/help/copilot/cloud-agent/firewall-warning.png)

For more information, see [Customizing or disabling the firewall for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/customize-the-agent-firewall).

## Copilot is not picking up attached screenshots

The maximum image size allowed by Copilot cloud agent is 3.00 MiB. Images larger than this will be removed from the request.

## Further reading

* [Best practices for using GitHub Copilot to work on tasks](/en/copilot/tutorials/cloud-agent/get-the-best-results)
* [Customizing the development environment for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/customize-the-agent-environment)