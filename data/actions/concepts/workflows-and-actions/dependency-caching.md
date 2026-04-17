# Dependency caching

Learn about dependency caching for workflow speed and efficiency.

## About workflow dependency caching

Workflow runs often reuse the same outputs or downloaded dependencies from one run to another. For example, package and dependency management tools such as Maven, Gradle, npm, and Yarn keep a local cache of downloaded dependencies.

Jobs on GitHub-hosted runners start in a clean runner image and must download dependencies each time, causing increased network utilization, longer runtime, and increased cost. To help speed up the time it takes to recreate files like dependencies, GitHub can cache files you frequently use in workflows.

> \[!NOTE]
> When using self-hosted runners, caches from workflow runs are stored on GitHub-owned cloud storage. A customer-owned storage solution is only available with GitHub Enterprise Server.

## Artifacts versus dependency caching

Artifacts and caching are similar because they provide the ability to store files on GitHub, but each feature offers different use cases and cannot be used interchangeably.

* Use caching when you want to reuse files that don't change often between jobs or workflow runs, such as build dependencies from a package management system.
* Use artifacts when you want to save files produced by a job to view after a workflow run has ended, such as built binaries or build logs.

For more information on workflow run artifacts, see [Store and share data with workflow artifacts](/en/actions/using-workflows/storing-workflow-data-as-artifacts).

## Next steps

To implement dependency caching in your workflows, see [Dependency caching reference](/en/actions/reference/dependency-caching-reference).