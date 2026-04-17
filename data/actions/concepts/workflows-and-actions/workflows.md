# Workflows

Get a high-level overview of GitHub Actions workflows, including triggers, syntax, and advanced features.

## About workflows

A **workflow** is a configurable automated process that will run one or more jobs. Workflows are defined by a YAML file checked in to your repository and will run when triggered by an event in your repository, or they can be triggered manually, or at a defined schedule.

Workflows are defined in the `.github/workflows` directory in a repository. A repository can have multiple workflows, each of which can perform a different set of tasks such as:

* Building and testing pull requests
* Deploying your application every time a release is created
* Adding a label whenever a new issue is opened

## Workflow basics

A workflow must contain the following basic components:

1. One or more *events* that will trigger the workflow.
2. One or more *jobs*, each of which will execute on a *runner* machine and run a series of one or more *steps*.
3. Each step can either run a script that you define or run an action, which is a reusable extension that can simplify your workflow.

For more information on these basic components, see [Understanding GitHub Actions](/en/actions/learn-github-actions/understanding-github-actions#the-components-of-github-actions).

![Diagram of an event triggering Runner 1 to run Job 1, which triggers Runner 2 to run Job 2. Each of the jobs is broken into multiple steps.](/assets/images/help/actions/overview-actions-simple.png)

## Workflow triggers

Workflow triggers are events that cause a workflow to run. These events can be:

* Events that occur in your workflow's repository
* Events that occur outside of GitHub and trigger a `repository_dispatch` event on GitHub
* Scheduled times
* Manual

For example, you can configure your workflow to run when a push is made to the default branch of your repository, when a release is created, or when an issue is opened.

Workflow triggers are defined with the `on` key. For more information, see [Workflow syntax for GitHub Actions](/en/actions/using-workflows/workflow-syntax-for-github-actions#on).

The following steps occur to trigger a workflow run:

1. An event occurs on your repository. The event has an associated commit SHA and Git ref.
2. GitHub searches the `.github/workflows` directory in the root of your repository for workflow files that are present in the associated commit SHA or Git ref of the event.
3. A workflow run is triggered for any workflows that have `on:` values that match the triggering event. Some events also require the workflow file to be present on the default branch of the repository in order to run.

Each workflow run will use the version of the workflow that is present in the associated commit SHA or Git ref of the event. When a workflow runs, GitHub sets the `GITHUB_SHA` (commit SHA) and `GITHUB_REF` (Git ref) environment variables in the runner environment. For more information, see [Store information in variables](/en/actions/learn-github-actions/variables).

For more information, see [Triggering a workflow](/en/actions/using-workflows/triggering-a-workflow).

## Next steps

To build your first workflow, see [Creating an example workflow](/en/actions/tutorials/creating-an-example-workflow).