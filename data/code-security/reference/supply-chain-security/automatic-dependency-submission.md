# Automatic dependency submission

Network access requirements, troubleshooting, and ecosystem-specific behavior for automatic dependency submission.

## Configure network access for self-hosted runners

If your self-hosted runners operate behind a firewall with restricted outbound internet access, you must add certain URLs to the allowlist for automatic dependency submission. The required URLs depend on the ecosystems your repositories use.

### Required URLs for all ecosystems

These URLs are required for all automatic dependency submission workflows:

* `https://github.com`—Required for accessing GitHub and downloading actions.
* `https://api.github.com`—Required for GitHub API access.
* `https://*.githubusercontent.com`—Required for downloading action source code and releases (including `raw.githubusercontent.com`, `github-releases.githubusercontent.com`, and `objects.githubusercontent.com`).

### Ecosystem-specific URLs

Depending on the ecosystems you use, you may need to allowlist additional URLs.

#### Go

* `https://go.dev`—For downloading the Go toolchain.
* `https://golang.org`—Alternate domain for Go downloads.
* `https://proxy.golang.org`—Official Go module proxy for downloading Go modules during dependency detection.

> \[!NOTE]
> The `actions/go-versions` repository is accessed via `https://raw.githubusercontent.com`, which is already covered in the general requirements.

#### Java (Maven and Gradle)

* `https://repo.maven.apache.org`—Maven Central repository for downloading dependencies.
* `https://api.adoptium.net`—For downloading Adoptium/Temurin JDK distributions (default distribution used by `actions/setup-java`).

If you use a different JDK distribution, you may also need:

* `https://aka.ms` and `https://download.microsoft.com`—For Microsoft Build of OpenJDK (note: `aka.ms` is also used for .NET downloads).
* `https://download.oracle.com`—For Oracle JDK.
* `https://api.azul.com`—For Azul Zulu OpenJDK.

#### .NET (C#, F#, Visual Basic)

* `https://aka.ms`—Microsoft URL shortener that redirects to .NET download locations.
* `https://builds.dotnet.microsoft.com`—Primary feed for .NET SDK and runtime downloads.
* `https://ci.dot.net`—Secondary feed for .NET builds.

> \[!NOTE]
> The `microsoft/component-detection` tool used by .NET autosubmission is downloaded from GitHub releases, which is already covered in the general requirements (`https://github.com` and `https://*.githubusercontent.com`).

#### Python

* `https://python.org`—For downloading Python interpreters.

> \[!NOTE]
> The `actions/python-versions` repository and `microsoft/component-detection` releases are accessed via URLs already covered in the general requirements (`https://*.githubusercontent.com` and `https://github.com`).

## Use GitHub-hosted larger runners for automatic dependency submission

GitHub Team or GitHub Enterprise Cloud users can use larger runners to run automatic dependency submissions jobs.

1. Provision a larger runner at the organization level with the name `dependency-submission`. For more information, see [Adding a larger runner to an organization](/en/actions/using-github-hosted-runners/about-larger-runners/managing-larger-runners#adding-a-larger-runner-to-an-organization).
2. Give your repository access to the runner. For more information, see [Allowing repositories to access larger runners](/en/actions/using-github-hosted-runners/about-larger-runners/managing-larger-runners#allowing-repositories-to-access-larger-runners).
3. Under "Dependency graph", click the dropdown menu next to “Automatic dependency submission”, then select **Enabled for labeled runners**.

## Troubleshoot automatic dependency submission

Automatic dependency submission makes a best effort to cache package downloads between runs using the [Cache](https://github.com/marketplace/actions/cache) action to speed up workflows. For self-hosted runners, you may want to manage this cache within your own infrastructure. To do this, you can disable the built-in caching by setting an environment variable of `GH_DEPENDENCY_SUBMISSION_SKIP_CACHE` to `true`. For more information, see [Store information in variables](/en/actions/learn-github-actions/variables).

### Manifest deduplication

A repository can use multiple methods for dependency submission, which can cause the same package manifest to be scanned multiple times, potentially with different outputs from each scan. Dependency graph uses deduplication logic to parse the outputs, prioritizing the most accurate information for each manifest file.

Dependency graph displays only one instance of each manifest file using the following precedence rules.

1. **User submissions** take the highest priority, because they are usually created during artifact builds they have the most complete information.
   * If there are multiple manual snapshots from different detectors, they are sorted alphabetically by correlator and the first one used.
   * If there are two correlators with the same detector, the resolved dependencies are merged. For more information about correlators and detectors, see [REST API endpoints for dependency submission](/en/rest/dependency-graph/dependency-submission).
2. **Automatic submissions** have the second-highest priority since they are also created during artifact builds, but are not submitted by users.
3. **Static analysis results** are used when no other data is available.

## Package ecosystem-specific information

### Maven projects

For Maven projects, automatic dependency submission runs an open source fork of the [Maven Dependency Tree Dependency Submission](https://github.com/marketplace/actions/maven-dependency-tree-dependency-submission). The fork allows GitHub to stay in sync with the upstream repository plus maintain some changes that are only applicable to automatic submission. The fork's source is available at [advanced-security/maven-dependency-submission-action](https://github.com/advanced-security/maven-dependency-submission-action).

If your repository's dependencies seem inaccurate, check that the timestamp of the last dependency graph build matches the last change to your `pom.xml` file. The timestamp is visible on the table of alerts in the repository's Dependabot tab. Pushing a commit which updates `pom.xml` will trigger a new run of the Dependency Tree Submission action and force a rebuild of that repository's dependency graph.

### Gradle projects

For Gradle projects, automatic dependency submission runs a fork of the open source Gradle actions from [gradle/actions](https://github.com/gradle/actions). The fork is available at [actions/gradle-build-tools-actions](https://github.com/actions/gradle-build-tools-actions). You can view the results of the autosubmission action under your repository's **Actions** tab. Each run will be labeled "Automatic Dependency Submission (Gradle)" and its output will contain the JSON payload which the action submitted to the API.

### .NET projects

The .NET autosubmission action uses the open source [component-detection](https://github.com/microsoft/component-detection/) project as the engine for its dependency detection. It supports .NET 8.x, 9.x, and 10.x. .NET autosubmission runs if the repository's `dependabot.yml` defines `nuget` as a [`package-ecosystem`](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#package-ecosystem-) or when there is a supported manifest file in the root directory of the repository. Supported manifest files include `.sln`, `.csproj`, `packages.config`, `.vbproj`, `.vcxproj`, and `.fsproj`.

### Python projects

Python uses the open source [component-detection](https://github.com/microsoft/component-detection/) project as its underlying graph generation engine. The autosubmission action for Python will only run if there is a `requirements.txt` file in the root directory of the repository. Python autosubmission does not currently support private packages; packages referenced in `requirements.txt` which are not publicly available will cause the autosubmission action to fail.

> \[!NOTE]
> This action uses [actions/setup-python](https://github.com/actions/setup-python) to install Python. You must include a .python-version file in your repository to specify the Python version to be installed.