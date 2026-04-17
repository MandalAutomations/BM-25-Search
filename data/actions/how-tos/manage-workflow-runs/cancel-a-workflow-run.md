# Canceling a workflow run

You can cancel a workflow run, including all jobs and steps, that is in progress.

## Canceling a workflow run

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)
3. In the left sidebar, click the workflow you want to see.

   ![Screenshot of the left sidebar of the "Actions" tab. A workflow, "CodeQL," is outlined in dark orange.](/assets/images/help/actions/superlinter-workflow-sidebar.png)
4. From the list of workflow runs, click the name of the `queued` or `in progress` run that you want to cancel.
5. In the upper-right corner of the workflow, click **Cancel workflow**.
   ![Screenshot showing the summary for a workflow that is currently running. The "Cancel workflow" button is highlighted with a dark orange outline.](/assets/images/help/repository/cancel-check-suite-updated.png)

## Next steps

To learn about the process GitHub uses to cancel a workflow run, as well as the ways you can free up related resources, see [Workflow cancellation reference](/en/actions/reference/workflow-cancellation-reference).