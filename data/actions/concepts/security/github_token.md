# GITHUB_TOKEN

Learn what GITHUB_TOKEN is, how it works, and why it matters for secure automation in GitHub Actions workflows.

## About the `GITHUB_TOKEN`

At the start of each workflow job, GitHub automatically creates a unique `GITHUB_TOKEN` secret to use in your workflow. You can use the `GITHUB_TOKEN` to authenticate in the workflow job.

When you enable GitHub Actions, GitHub installs a GitHub App on your repository. The `GITHUB_TOKEN` secret is a GitHub App installation access token. You can use the installation access token to authenticate on behalf of the GitHub App installed on your repository. The token's permissions are limited to the repository that contains your workflow. For more information, see [Workflow syntax for GitHub Actions](/en/actions/reference/workflow-syntax-for-github-actions#permissions).

Before each job begins, GitHub fetches an installation access token for the job. The `GITHUB_TOKEN` expires when the job finishes or after its effective maximum lifetime.

The effective maximum lifetime of the token depends on the type of runner:

* **GitHub-hosted runners** The maximum job execution time is 6 hours, so the `GITHUB_TOKEN` can live for a maximum of 6 hours.
* **Self-hosted runners** The maximum job execution time is 5 days. However, because the `GITHUB_TOKEN` is an installation access token, it can only be refreshed for up to 24 hours. If your job runs longer than 24 hours, use a personal access token or other authentication method instead.

The token is also available in the `github.token` context. For more information, see [Contexts reference](/en/actions/learn-github-actions/contexts#github-context).

## When `GITHUB_TOKEN` triggers workflow runs

When you use the repository's `GITHUB_TOKEN` to perform tasks, events triggered by the `GITHUB_TOKEN`, with the exception of `workflow_dispatch` and `repository_dispatch`, will not create a new workflow run. This prevents you from accidentally creating recursive workflow runs. For example, if a workflow run pushes code using the repository's `GITHUB_TOKEN`, a new workflow will not run even when the repository contains a workflow configured to run when `push` events occur.

Commits pushed by a GitHub Actions workflow that uses the `GITHUB_TOKEN` do not trigger a GitHub Pages build.

## Next steps

* [Use GITHUB\_TOKEN for authentication in workflows](/en/actions/how-tos/security-for-github-actions/security-guides/use-github_token-in-workflows)
* [Workflow syntax for GitHub Actions](/en/actions/reference/workflow-syntax-for-github-actions#permissions)