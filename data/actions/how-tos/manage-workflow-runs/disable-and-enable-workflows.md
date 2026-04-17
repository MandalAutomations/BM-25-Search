# Disabling and enabling a workflow

You can disable and re-enable a workflow using the GitHub UI, the REST API, or GitHub CLI.

Disabling a workflow allows you to stop a workflow from being triggered without having to delete the file from the repo. You can easily re-enable the workflow again on GitHub.

Temporarily disabling a workflow can be useful in many scenarios. These are a few examples where disabling a workflow might be helpful:

* A workflow error that produces too many or wrong requests, impacting external services negatively.
* A workflow that is not critical and is consuming too many minutes on your account.
* A workflow that sends requests to a service that is down.
* Workflows on a forked repository that aren't needed (for example, scheduled workflows).

> \[!WARNING]
> To prevent unnecessary workflow runs, scheduled workflows may be disabled automatically. When a public repository is forked, scheduled workflows are disabled by default. In a public repository, scheduled workflows are automatically disabled when no repository activity has occurred in 60 days.

You can also disable and enable a workflow using the REST API. For more information, see [REST API endpoints for workflows](/en/rest/actions/workflows).

## Disabling a workflow

<div class="ghd-tool webui">

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)
3. In the left sidebar, click the workflow you want to disable.
4. Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Show workflow options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> to display a dropdown menu and click **Disable workflow**.

   ![Screenshot of a workflow. The "Show workflow options" button, shown with a kebab icon, and the "Disable workflow" menu item are outlined in orange.](/assets/images/help/repository/actions-disable-workflow-2022.png)

</div>

<div class="ghd-tool cli">

> \[!NOTE]
> To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

To disable a workflow, use the `workflow disable` subcommand. Replace `workflow` with either the name, ID, or file name of the workflow you want to disable. For example, `"Link Checker"`, `1234567`, or `"link-check-test.yml"`. If you don't specify a workflow, GitHub CLI returns an interactive menu for you to choose a workflow.

```shell
gh workflow disable WORKFLOW
```

</div>

## Enabling a workflow

<div class="ghd-tool webui">

You can re-enable a workflow that was previously disabled.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)

3. In the left sidebar, click the workflow you want to enable.

   ![Screenshot of the "Actions" page. In the left sidebar, a workflow name is highlighted with an outline in dark orange.](/assets/images/help/repository/actions-select-disabled-workflow-2022.png)

4. Click **Enable workflow**.

</div>

<div class="ghd-tool cli">

To enable a workflow, use the `workflow enable` subcommand. Replace `workflow` with either the name, ID, or file name of the workflow you want to enable. For example, `"Link Checker"`, `1234567`, or `"link-check-test.yml"`. If you don't specify a workflow, GitHub CLI returns an interactive menu for you to choose a workflow.

```shell
gh workflow enable WORKFLOW
```

</div>