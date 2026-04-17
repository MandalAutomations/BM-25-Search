# Troubleshooting required status checks

You can check for common errors and resolve issues with required status checks.

If you have a check and a status with the same name, and you select that name as a required status check, both the check and the status are required. For more information, see [REST API endpoints for checks](/en/rest/checks).

> \[!NOTE]
> To be required, status checks must have completed successfully within the chosen repository during the past seven days.

After you enable required status checks, your branch may need to be up-to-date with the base branch before merging. This ensures that your branch has been tested with the latest code from the base branch. If your branch is out of date, you'll need to merge the base branch into your branch. For more information, see [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-status-checks-before-merging).

> \[!NOTE]
> You can also bring your branch up to date with the base branch using Git rebase. For more information, see [About Git rebase](/en/get-started/using-git/about-git-rebase).

You won't be able to push local changes to a protected branch until all required status checks pass. Instead, you'll receive an error message similar to the following.

```shell
remote: error: GH006: Protected branch update failed for refs/heads/main.
remote: error: Required status check "ci-build" is failing
```

> \[!NOTE]
> Pull requests that are up-to-date and pass required status checks can be merged locally and pushed to the protected branch. This can be done without status checks running on the merge commit itself.

## Required check needs to succeed against the latest commit SHA

In order for a pull request to be merged, all required checks must pass against the latest commit SHA. This ensures that the most recent changes are validated and meet the required standards before merging. Checks that were triggered using a previous commit SHA will not be used as part of required checks. Successful check statuses are: `success`, `skipped`, and `neutral`. For more information, see [About status checks](/en/pull-requests/collaborating-with-pull-requests/collaborating-on-repositories-with-code-quality-features/about-status-checks).

## Conflicts between head commit and test merge commit

Sometimes, the results of the status checks for the test merge commit and head commit will conflict. If the test merge commit has a status, the test merge commit must pass. Otherwise, the status of the head commit must pass before you can merge the branch.

If there is a conflict between the test merge commit and head commit, the checks for the test merge commit are shown in the pull request status checks box. This is indicated in the pull request status box by a line starting with `Showing checks for the merge commit`. For more information about test merge commits, see [REST API endpoints for pull requests](/en/rest/pulls/pulls#get-a-pull-request).

## Handling skipped but required checks

> \[!WARNING]
> If a workflow is skipped due to [path filtering](/en/actions/using-workflows/workflow-syntax-for-github-actions#onpushpull_requestpull_request_targetpathspaths-ignore), [branch filtering](/en/actions/using-workflows/workflow-syntax-for-github-actions#onpull_requestpull_request_targetbranchesbranches-ignore) or a [commit message](/en/actions/managing-workflow-runs/skipping-workflow-runs), then checks associated with that workflow will remain in a "Pending" state. A pull request that requires those checks to be successful will be blocked from merging.
>
> If, however, a job within a workflow is skipped due to a conditional, it will report its status as "Success". For more information, see [Using conditions to control job execution](/en/actions/using-jobs/using-conditions-to-control-job-execution).
>
> When a job fails, any jobs that depend on the failed job are skipped and do not report a failure. A pull request that requires the check may not be blocked. To use a required check on a job that depends on other jobs, use the `always()` conditional expression in addition to `needs`, see [Using jobs in a workflow](/en/actions/using-jobs/using-jobs-in-a-workflow#defining-prerequisite-jobs).

### Example

The following example shows a workflow that requires a "Successful" completion status for the `build` job, but the workflow will be skipped if the pull request does not change any files in the `scripts` directory.

```yaml
name: ci
on:
  pull_request:
    paths:
      - 'scripts/**'
jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [12.x, 14.x, 16.x]
    steps:
    - uses: actions/checkout@v5
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v4
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'npm'
    - run: npm ci
    - run: npm run build --if-present
    - run: npm test
```

Due to [path filtering](/en/actions/using-workflows/workflow-syntax-for-github-actions#onpushpull_requestpull_request_targetpathspaths-ignore), a pull request that only changes a file in the root of the repository will not trigger this workflow and is blocked from merging. On the pull request, you would see "Waiting for status to be reported."

### Status checks with GitHub Actions and a Merge queue

You **must** use the `merge_group` event to trigger your GitHub Actions workflow when a pull request is added to a merge queue.

> \[!NOTE]
> If your repository uses GitHub Actions to perform required checks on pull requests in your repository, you need to update the workflows to include the `merge_group` event as an additional trigger. Otherwise, status checks will not be triggered when you add a pull request to a merge queue. The merge will fail as the required status check will not be reported. The `merge_group` event is separate from the `pull_request` and `push` events.

A workflow that reports a check which is required by the target branch's protections would look like this:

```yaml
on:
  pull_request:
  merge_group:
```

For more information on the `merge_group` event, see [Events that trigger workflows](/en/actions/using-workflows/events-that-trigger-workflows#merge_group).

## Required status checks from unexpected sources

It's also possible for a protected branch to require a status check from a specific GitHub App. If you see a message similar to the following, then you should verify that the check listed in the merge box was set by the expected app.

```text
Required status check "build" was not set by the expected GitHub App.
```