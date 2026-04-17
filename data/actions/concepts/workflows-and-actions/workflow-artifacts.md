# Workflow artifacts

Learn about storing and sharing data as artifacts of GitHub Actions workflows.

## About workflow artifacts

An artifact is a file or collection of files produced during a workflow run. Artifacts allow you to persist data after a job has completed, and share that data with another job in the same workflow. For example, you can use artifacts to save your build and test output after a workflow run has ended.

GitHub provides two actions that you can use to upload and download build artifacts, [upload-artifact](https://github.com/actions/upload-artifact) and [download-artifact](https://github.com/actions/download-artifact).

Common artifacts include:

* Log files and core dumps
* Test results, failures, and screenshots
* Binary or compressed files
* Stress test performance output and code coverage results

## Artifacts versus dependency caching

Artifacts and caching are similar because they provide the ability to store files on GitHub, but each feature offers different use cases and cannot be used interchangeably.

* Use caching when you want to reuse files that don't change often between jobs or workflow runs, such as build dependencies from a package management system.
* Use artifacts when you want to save files produced by a job to view after a workflow run has ended, such as built binaries or build logs.

For more information on dependency caching, see [Dependency caching reference](/en/actions/using-workflows/caching-dependencies-to-speed-up-workflows#comparing-artifacts-and-dependency-caching).

## Generating artifact attestations for builds

Artifact attestations enable you to create unfalsifiable provenance and integrity guarantees for the software you build. In turn, people who consume your software can verify where and how your software was built.

When you generate artifact attestations with your software, you create cryptographically signed claims that establish your build's provenance and include the following information:

* A link to the workflow associated with the artifact
* The repository, organization, environment, commit SHA, and triggering event for the artifact
* Other information from the OIDC token used to establish provenance. For more information, see [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect).

You can also generate artifact attestations that include an associated software bill of materials (SBOM). Associating your builds with a list of the open source dependencies used in them provides transparency and enables consumers to comply with data protection standards.

You can access attestations after a build run, underneath the list of the artifacts the build produced.

For more information, see [Using artifact attestations to establish provenance for builds](/en/actions/security-guides/using-artifact-attestations-to-establish-provenance-for-builds).

## Artifacts from deleted workflow runs

When a workflow run is deleted all artifacts associated with the run are also deleted from storage. You can delete a workflow run using the GitHub Actions UI, the REST API, or using the GitHub CLI, see: [Deleting a workflow run](/en/actions/managing-workflow-runs-and-deployments/managing-workflow-runs/deleting-a-workflow-run), [Delete a workflow run](/en/rest/actions/workflow-runs?apiVersion=2022-11-28#delete-a-workflow-run), or [gh run delete](https://cli.github.com/manual/gh_run_delete).