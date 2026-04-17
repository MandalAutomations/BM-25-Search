# Transferring an issue to another repository

To move an issue to a better fitting repository, you can transfer open issues to other repositories.

To transfer an open issue to another repository, you must have write access to the repository the issue is in and the repository you're transferring the issue to. For more information, see [Repository roles for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).

> \[!NOTE]
> You can only transfer issues between repositories owned by the same user or organization account. A private repository issue cannot be transferred to a public repository.

When you transfer an issue, comments and assignees are retained. Labels and milestones are also retained if they're present in the target repository, with labels matching by name and milestones matching by both name and due date.

People or teams who are mentioned in the issue will receive a notification letting them know that the issue has been transferred to a new repository. The original URL redirects to the new issue's URL. People who don't have read permissions in the new repository will see a banner letting them know that the issue has been transferred to a new repository that they can't access.

## Transferring an open issue to another repository

<div class="ghd-tool webui">

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Issues," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-issues-global-nav-update.png)
3. In the list of issues, click the issue you'd like to transfer.
4. In the right sidebar, click **Transfer issue**.
5. Select the **Choose a repository** dropdown menu, and click the repository you want to transfer the issue to.
6. Click **Transfer issue**.

</div>

<div class="ghd-tool cli">

> \[!NOTE]
> To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

To transfer an issue, use the `gh issue transfer` subcommand. Replace the `issue` parameter with the number or URL of the issue. Replace the `owner/repo` parameter with the name of the repository that you want to transfer the issue to, such as `octocat/octo-repo`.

```shell
gh issue transfer ISSUE OWNER/REPO
```

</div>

## Further reading

* [About issues](/en/issues/tracking-your-work-with-issues/about-issues)