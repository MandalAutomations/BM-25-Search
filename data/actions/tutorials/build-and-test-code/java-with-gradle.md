# Building and testing Java with Gradle

Learn how to create a continuous integration (CI) workflow in GitHub Actions to build and test your Java project with Gradle.

## Introduction

This guide shows you how to create a workflow that performs continuous integration (CI) for your Java project using the Gradle build system. The workflow you create will allow you to see when commits to a pull request cause build or test failures against your default branch; this approach can help ensure that your code is always healthy. You can extend your CI workflow to cache files and upload artifacts from a workflow run.

GitHub-hosted runners have a tools cache with pre-installed software, which includes Java Development Kits (JDKs) and Gradle. For a list of software and the pre-installed versions for JDK and Gradle, see [GitHub-hosted runners](/en/actions/using-github-hosted-runners/about-github-hosted-runners#supported-software).

## Prerequisites

You should be familiar with YAML and the syntax for GitHub Actions. For more information, see:

* [Workflow syntax for GitHub Actions](/en/actions/using-workflows/workflow-syntax-for-github-actions)
* [Writing workflows](/en/actions/learn-github-actions)

We recommend that you have a basic understanding of Java and the Gradle framework. For more information, see the [Gradle User Manual](https://docs.gradle.org/current/userguide/userguide.html).

## Using a Gradle workflow template

To get started quickly, add a workflow template to the `.github/workflows` directory of your repository.

GitHub provides a workflow template for Gradle that should work for most Java with Gradle projects. The subsequent sections of this guide give examples of how you can customize this workflow template.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)

3. If you already have a workflow in your repository, click **New workflow**.

4. The "Choose a workflow" page shows a selection of recommended workflow templates. Search for "Java with Gradle".

5. On the "Java with Gradle" workflow, click **Configure**.
   This workflow performs the following steps:

6. Checks out a copy of project's repository.

7. Sets up the Java JDK.

8. Sets up the Gradle environment. The [`gradle/actions/setup-gradle`](https://github.com/gradle/actions) action takes care of caching state between workflow runs, and provides a detailed summary of all Gradle executions.

9. The "Build with Gradle" step executes the `build` task using the [Gradle Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html).

10. Edit the workflow as required. For example, change the Java version.

    > \[!NOTE]
    >
    > * This workflow template contains an action that is not certified by GitHub. Actions provided by third parties are governed by separate terms of service, privacy policy, and support documentation.
    > * If you use actions from third parties you should use a version specified by a commit SHA. If the action is revised and you want to use the newer version, you will need to update the SHA. You can specify a version by referencing a tag or a branch, however the action may change without warning. For more information, see [Secure use reference](/en/actions/security-guides/security-hardening-for-github-actions#using-third-party-actions).

11. Click **Commit changes**.

    The `gradle.yml` workflow file is added to the `.github/workflows` directory of your repository.

### Specifying the Java version and architecture

The workflow template sets up the `PATH` to contain OpenJDK 8 for the x64 platform. If you want to use a different version of Java, or target a different architecture (`x64` or `x86`), you can use the `setup-java` action to choose a different Java runtime environment.

For example, to use version 11 of the JDK provided by Adoptium for the x64 platform, you can use the `setup-java` action and configure the `java-version`, `distribution` and `architecture` parameters to `'11'`, `'temurin'` and `x64`.

```yaml copy
steps:
  - uses: actions/checkout@v5
  - name: Set up JDK 11 for x64
    uses: actions/setup-java@v4
    with:
      java-version: '11'
      distribution: 'temurin'
      architecture: x64
```

For more information, see the [`setup-java`](https://github.com/actions/setup-java) action.

## Building and testing your code

You can use the same commands that you use locally to build and test your code.

The workflow template will run the `build` task by default. In the default Gradle configuration, this command will download dependencies, build classes, run tests, and package classes into their distributable format, for example, a JAR file.

If you use different commands to build your project, or you want to use a different task, you can specify those. For example, you may want to run the `package` task that's configured in your `ci.gradle` file.

```yaml copy
# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.
steps:
  - uses: actions/checkout@v5
  - uses: actions/setup-java@v4
    with:
      java-version: '17'
      distribution: 'temurin'

  - name: Setup Gradle
    uses: gradle/actions/setup-gradle@017a9effdb900e5b5b2fddfb590a105619dca3c3 # v4.4.2

  - name: Build with Gradle
    run: ./gradlew -b ci.gradle package
```

## Caching dependencies

Your build dependencies can be cached to speed up your workflow runs. After a successful run, `gradle/actions/setup-gradle` caches important parts of the Gradle user home directory. In future jobs, the cache will be restored so that build scripts won't need to be recompiled and dependencies won't need to be downloaded from remote package repositories.

Caching is enabled by default when using the `gradle/actions/setup-gradle` action. For more information, see [`gradle/actions/setup-gradle`](https://github.com/gradle/actions/blob/main/setup-gradle/README.md#caching-build-state-between-jobs).

## Packaging workflow data as artifacts

After your build has succeeded and your tests have passed, you may want to upload the resulting Java packages as a build artifact. This will store the built packages as part of the workflow run, and allow you to download them. Artifacts can help you test and debug pull requests in your local environment before they're merged. For more information, see [Store and share data with workflow artifacts](/en/actions/using-workflows/storing-workflow-data-as-artifacts).

Gradle will usually create output files like JARs, EARs, or WARs in the `build/libs` directory. You can upload the contents of that directory using the `upload-artifact` action.

```yaml copy
# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.
steps:
  - uses: actions/checkout@v5
  - uses: actions/setup-java@v4
    with:
      java-version: '17'
      distribution: 'temurin'

  - name: Setup Gradle
    uses: gradle/actions/setup-gradle@017a9effdb900e5b5b2fddfb590a105619dca3c3 # v4.4.2

  - name: Build with Gradle
    run: ./gradlew build

  - name: Upload build artifacts
    uses: actions/upload-artifact@v4
    with:
      name: Package
      path: build/libs
```