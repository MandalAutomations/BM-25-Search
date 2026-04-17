# Adding labels to issues

You can use GitHub Actions to automatically label issues.

## Introduction

This tutorial demonstrates how to use the GitHub CLI in a workflow to label newly opened or reopened issues. For example, you can add the `triage` label every time an issue is opened or reopened. Then, you can see all issues that need to be triaged by filtering for issues with the `triage` label.

The GitHub CLI allows you to easily use the GitHub API in a workflow.

In the tutorial, you will first make a workflow file that uses the GitHub CLI. Then, you will customize the workflow to suit your needs.

## Creating the workflow

1. Choose a repository where you want to apply this project management workflow. You can use an existing repository that you have write access to, or you can create a new repository. For more information about creating a repository, see [Creating a new repository](/en/repositories/creating-and-managing-repositories/creating-a-new-repository).

2. In your repository, create a file called `.github/workflows/YOUR_WORKFLOW.yml`, replacing `YOUR_WORKFLOW` with a name of your choice. This is a workflow file. For more information about creating new files on GitHub, see [Creating new files](/en/repositories/working-with-files/managing-files/creating-new-files).

3. Copy the following YAML contents into your workflow file.

   ```yaml copy
   name: Label issues
   on:
     issues:
       types:
         - reopened
         - opened
   jobs:
     label_issues:
       runs-on: ubuntu-latest
       permissions:
         issues: write
       steps:
         - run: gh issue edit "$NUMBER" --add-label "$LABELS"
           env:
             GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
             GH_REPO: ${{ github.repository }}
             NUMBER: ${{ github.event.issue.number }}
             LABELS: triage
   ```

4. Customize the `env` values in your workflow file:
   * The `GH_TOKEN`, `GH_REPO`, and `NUMBER` values are automatically set using the `github` and `secrets` contexts. You do not need to change these.
   * Change the value for `LABELS` to the list of labels that you want to add to the issue. The label(s) must exist for your repository. Separate multiple labels with commas. For example, `help wanted,good first issue`. For more information about labels, see [Managing labels](/en/issues/using-labels-and-milestones-to-track-work/managing-labels#applying-labels-to-issues-and-pull-requests).

5. Commit your workflow file to the default branch of your repository. For more information, see [Creating new files](/en/repositories/working-with-files/managing-files/creating-new-files).

## Testing the workflow

Every time an issue in your repository is opened or reopened, this workflow will add the labels that you specified to the issue.

Test out your workflow by creating an issue in your repository.

1. Create an issue in your repository. For more information, see [Creating an issue](/en/issues/tracking-your-work-with-issues/creating-an-issue).
2. To see the workflow run that was triggered by creating the issue, view the history of your workflow runs. For more information, see [Viewing workflow run history](/en/actions/monitoring-and-troubleshooting-workflows/viewing-workflow-run-history).
3. When the workflow completes, the issue that you created should have the specified labels added.

## Next steps

* To learn more about additional things you can do with the GitHub CLI, see the [GitHub CLI manual](https://cli.github.com/manual/).
* To learn more about different events that can trigger your workflow, see [Events that trigger workflows](/en/actions/using-workflows/events-that-trigger-workflows#issues).
* [Search GitHub](https://github.com/search?q=path%3A.github%2Fworkflows+gh+issue+edit\&type=code) for examples of workflows using `gh issue edit`.