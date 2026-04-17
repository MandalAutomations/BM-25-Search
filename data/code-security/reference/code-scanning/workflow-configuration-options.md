# Workflow configuration options for code scanning

Edit your workflow file to configure how advanced setup scans the code in your project for vulnerabilities and errors.

<!--The CodeQL CLI man pages include a link to a section of the article. If you rename this article,
make sure that you also update the MS short link: https://aka.ms/code-scanning-docs/config-file.-->

## Prerequisites

You must use advanced setup for code scanning and be able to edit the workflow file where your configuration is defined.

The examples provided in this article relate to the CodeQL analysis workflow file. By default, this file is defined at `.github/workflows/codeql-analysis.yml`.

## Scan frequency

You can configure the CodeQL analysis workflow to scan code on a schedule or when specific events occur in a repository.

Scanning code when someone pushes a change, and whenever a pull request is created, prevents developers from introducing new vulnerabilities and errors into the code. Scanning code on a schedule informs you about the latest vulnerabilities and errors that GitHub, security researchers, and the community discover, even when developers aren't actively maintaining the repository.

### Scanning on push

By default, the CodeQL analysis workflow uses the `on:push` event to trigger a code scan on every push to the default branch of the repository and any protected branches. For code scanning to be triggered on a specified branch, the workflow must exist in that branch. For more information, see [Workflow syntax for GitHub Actions](/en/actions/using-workflows/workflow-syntax-for-github-actions#on).

If you scan on push, then the results appear in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for your repository. For more information, see [Assessing code scanning alerts for your repository](/en/code-security/code-scanning/managing-code-scanning-alerts/assessing-code-scanning-alerts-for-your-repository#viewing-the-alerts-for-a-repository).

Additionally, when an `on:push` scan returns results that can be mapped to an open pull request, these alerts will automatically appear on the pull request in the same places as other pull request alerts. The alerts are identified by comparing the existing analysis of the head of the branch to the analysis for the target branch. For more information on code scanning alerts in pull requests, see [Triaging code scanning alerts in pull requests](/en/code-security/code-scanning/managing-code-scanning-alerts/triaging-code-scanning-alerts-in-pull-requests).

### Scanning pull requests

The default CodeQL analysis workflow uses the `pull_request` event to trigger a code scan on pull requests targeted against the default branch. If a pull request is from a private fork, the `pull_request` event will only be triggered if you've selected the "Run workflows from fork pull requests" option in the repository settings. For more information, see [Managing GitHub Actions settings for a repository](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#enabling-workflows-for-private-repository-forks).

For more information about the `pull_request` event, see [Events that trigger workflows](/en/actions/using-workflows/events-that-trigger-workflows#pull_request).

If you scan pull requests, then the results appear as alerts in a pull request check. For more information, see [Triaging code scanning alerts in pull requests](/en/code-security/code-scanning/managing-code-scanning-alerts/triaging-code-scanning-alerts-in-pull-requests).

Using the `pull_request` trigger, configured to scan the pull request's merge commit rather than the head commit, will produce more efficient and accurate results than scanning the head of the branch on each push. However, if you use a CI/CD system that cannot be configured to trigger on pull requests, you can still use the `on:push` trigger and code scanning will map the results to open pull requests on the branch and add the alerts as annotations on the pull request. For more information, see [Scanning on push](#scanning-on-push).

> \[!NOTE]
> If your repository is configured with a merge queue, you need to include the `merge_group` event as an additional trigger for code scanning. This will ensure that pull requests are also scanned when they are added to a merge queue. For more information, see [Managing a merge queue](/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue).

### Avoiding unnecessary scans of pull requests

You might want to avoid a code scan being triggered on specific pull requests targeted against the default branch, irrespective of which files have been changed. You can configure this by specifying `on:pull_request:paths-ignore` or `on:pull_request:paths` in the code scanning workflow. For example, if the only changes in a pull request are to files with the file extensions `.md` or `.txt` you can use the following `paths-ignore` array.

```yaml copy
on:
  push:
    branches: [main, protected]
  pull_request:
    branches: [main]
    paths-ignore:
      - '**/*.md'
      - '**/*.txt'
```

> \[!NOTE]
> `on:pull_request:paths-ignore` and `on:pull_request:paths` set conditions that determine whether the actions in the workflow will run on a pull request. They don't determine what files will be analyzed when the actions *are* run. When a pull request contains any files that are not matched by `on:pull_request:paths-ignore` or `on:pull_request:paths`, the workflow runs the actions and scans all of the files changed in the pull request, including those matched by `on:pull_request:paths-ignore` or `on:pull_request:paths`, unless the files have been excluded. For information on how to exclude files from analysis, see [Specifying directories to scan](#specifying-directories-to-scan).

For more information about using `on:pull_request:paths-ignore` and `on:pull_request:paths` to determine when a workflow will run for a pull request, see [Workflow syntax for GitHub Actions](/en/actions/using-workflows/workflow-syntax-for-github-actions#onpushpull_requestpull_request_targetpathspaths-ignore).

### Scanning on a schedule

If you use the default CodeQL analysis workflow, the workflow will scan the code in your repository once a week, in addition to the scans triggered by events. To adjust this schedule, edit the `cron` value for the `on.schedule` event in the workflow. For more information, see [Workflow syntax for GitHub Actions](/en/actions/reference/workflows-and-actions/workflow-syntax#onschedule).

> \[!NOTE]
> This event will only trigger a workflow run if the workflow file exists on the default branch.

### Example

The following example shows a CodeQL analysis workflow for a particular repository that has a default branch called `main` and one protected branch called `protected`.

```yaml copy
on:
  push:
    branches: [main, protected]
  pull_request:
    branches: [main]
  schedule:
    - cron: '20 14 * * 1'
```

This workflow scans:

* Every push to the default branch and the protected branch
* Every pull request to the default branch
* The default branch every Monday at 14:20 UTC

## Operating system

> \[!NOTE]
>
> * Code scanning of Swift code uses macOS runners by default. GitHub-hosted macOS runners are more expensive than Linux and Windows runners, so you should consider only scanning the build step. For more information about configuring code scanning for Swift, see [CodeQL code scanning for compiled languages](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/codeql-code-scanning-for-compiled-languages#considerations-for-building-swift). For more information about pricing for GitHub-hosted runners, see [GitHub Actions billing](/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions).
>
> * Code scanning of Swift code is not supported for runners that are part of an Actions Runner Controller (ARC), because ARC runners only use Linux and Swift requires macOS runners. However, you can have a mixture of both ARC runners and self-hosted macOS runners. For more information, see [Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/about-actions-runner-controller).

If your code requires a specific operating system to compile, you can configure the operating system in your CodeQL analysis workflow. Edit the value of `jobs.analyze.runs-on` to specify the operating system for the machine that runs your code scanning actions.

```yaml copy
jobs:
  analyze:
    name: Analyze
    runs-on: [ubuntu-latest]
```

If you choose to use a self-hosted runner for code scanning, you can specify an operating system by using an appropriate label as the second element in a two-element array, after `self-hosted`.

```yaml copy
jobs:
  analyze:
    name: Analyze
    runs-on: [self-hosted, ubuntu-latest]
```

CodeQL code scanning supports the latest versions of Ubuntu, Windows, and macOS. Typical values for this setting are therefore: `ubuntu-latest`, `windows-latest`, and `macos-latest`. For more information, see [Choosing the runner for a job](/en/actions/using-jobs/choosing-the-runner-for-a-job) and [Using labels with self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/using-labels-with-self-hosted-runners).

If you use a self-hosted runner, you must ensure that Git is in the PATH variable. For more information, see [Self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners) and [Adding self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners).

For recommended specifications (RAM, CPU cores, and disk) for running CodeQL analysis on self-hosted machines, see [Recommended hardware resources for running CodeQL](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/recommended-hardware-resources-for-running-codeql).

## CodeQL database location

In general, you do not need to worry about where the CodeQL analysis workflow places CodeQL databases since later steps will automatically find databases created by previous steps. However, if you are writing a custom workflow step that requires the CodeQL database to be in a specific disk location, for example to upload the database as a workflow artifact, you can specify that location using the `db-location` parameter under the `init` action.

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    db-location: '${{ github.runner_temp }}/my_location'
```

The CodeQL analysis workflow will expect the path provided in `db-location` to be writable, and either not exist, or be an empty directory. When using this parameter in a job running on a self-hosted runner or using a Docker container, it's the responsibility of the user to ensure that the chosen directory is cleared between runs, or that the databases are removed once they are no longer needed. This is not necessary for jobs running on GitHub-hosted runners, which obtain a fresh instance and a clean filesystem each time they run. For more information, see [GitHub-hosted runners](/en/actions/using-github-hosted-runners/about-github-hosted-runners).

If this parameter is not used, the CodeQL analysis workflow will create databases in a temporary location of its own choice. Currently the default value is `${{ github.runner_temp }}/codeql_databases`.

## Languages to be analyzed

CodeQL code scanning supports code written in the following languages:

<!-- If you update the list of supported languages for CodeQL, update docs-internal/content/get-started/learning-about-github/github-language-support.md to reflect the changes. -->

* C/C++
* C#
* Go
* Java/Kotlin
* JavaScript/TypeScript
* Python
* Ruby
* Rust
* Swift
* GitHub Actions workflows

> \[!NOTE]
>
> * Use `java-kotlin` to analyze code written in Java, Kotlin or both.
> * Use `javascript-typescript` to analyze code written in JavaScript, TypeScript or both.

For more information, see the documentation on the CodeQL website: [Supported languages and frameworks](https://codeql.github.com/docs/codeql-overview/supported-languages-and-frameworks/).

CodeQL uses the following language identifiers:

| Language                 | Identifier              | Optional alternative identifiers (if any) |
| ------------------------ | ----------------------- | ----------------------------------------- |
| C/C++                    | `c-cpp`                 | `c` or `cpp`                              |
| C#                       | `csharp`                |                                           |
|                          |                         |                                           |
| GitHub Actions workflows | `actions`               |                                           |
|                          |                         |                                           |
| Go                       | `go`                    |                                           |
| Java/Kotlin              | `java-kotlin`           | `java` or `kotlin`                        |
| JavaScript/TypeScript    | `javascript-typescript` | `javascript` or `typescript`              |
| Python                   | `python`                |                                           |
| Ruby                     | `ruby`                  |                                           |
|                          |                         |                                           |
| Rust                     | `rust`                  |                                           |
|                          |                         |                                           |
| Swift                    | `swift`                 |                                           |

> \[!NOTE]
> If you specify one of the alternative identifiers, this is equivalent to using the standard language identifier. For example, specifying `javascript` instead of `javascript-typescript` will not exclude analysis of TypeScript code. Instead, you can use a custom configuration file to exclude files from analysis using the `paths-ignore` setting. For more information, see [Using a custom configuration file](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning#custom-configuration-files) and [Specifying directories to scan](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning#specifying-directories-to-scan).

These language identifiers can be used as arguments to the `languages` input of the `init` action. We recommend that only one language is provided as an argument:

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    languages: javascript-typescript
```

The default CodeQL analysis workflow file created after [configuring advanced setup for code scanning with CodeQL](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/configuring-advanced-setup-for-code-scanning#configuring-advanced-setup-for-code-scanning-with-codeql) defines a matrix containing a property named `language` which lists the languages in your repository that will be analyzed. This matrix has been automatically pre-populated with supported languages detected in your repository. Using the `language` matrix allows CodeQL to run each language analysis in parallel and to customize analysis for each language. In an individual analysis, the name of the language from the matrix is provided to the `init` action as the argument for the `languages` input. We recommend that all workflows adopt this configuration. For more information about matrices, see [Running variations of jobs in a workflow](/en/actions/using-jobs/using-a-matrix-for-your-jobs).

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    languages: ${{ matrix.language }}
```

If your workflow uses the `language` matrix, then CodeQL will only analyze the languages in the matrix. To change the languages you want to analyze, edit the matrix configuration. You can remove a language to prevent it from being analyzed. There are several reasons you might want to prevent a language being analyzed. For example, the project might have dependencies in a different language to the main body of your code, and you might prefer not to see alerts for those dependencies. You can also add a language that was not present in the repository when code scanning was configured. For example, if the repository initially only contained JavaScript when code scanning was configured, and you later added Python code, you will need to add `python` to the matrix.

```yaml copy
jobs:
  analyze:
    name: Analyze
    ...
    strategy:
      fail-fast: false
      matrix:
        include:
          - language: javascript-typescript
            build-mode: none
          - language: python
            build-mode: none
```

For compiled languages, the matrix can also be used to configure which build mode should be used for analysis by changing the value of the `build-mode` property. For more information about build modes, see [CodeQL code scanning for compiled languages](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/codeql-code-scanning-for-compiled-languages#about-build-mode-none-for-codeql).

If your workflow does not provide an argument to the `languages` input of the `init` action, then CodeQL is configured to run analyses sequentially. In this case, CodeQL automatically detects, and attempts to analyze, any supported languages in the repository. Depending on the size of the repository and the number of languages, this may take a long time. If analysis for one language fails in this mode, then the analysis for all languages fails. Therefore, we do not recommend this configuration.

> \[!NOTE]
> When analyzing languages sequentially, the default build-mode for every language will be used. Alternatively, if you provide an explicit `autobuild` step, then every language that supports the `autobuild` mode will use it while other languages use their default mode. If a more complex build-mode configuration than this is required, then you will need to configure a matrix.

## Alert severities for check failures

You can use rulesets to prevent pull requests from being merged when one of the following conditions is met:

* A required tool finds a code scanning alert of a severity that is defined in the ruleset.
* A required tool's analysis is still in progress.
* A required tool is not configured for the repository.

For more information, see [Set code scanning merge protection](/en/code-security/code-scanning/managing-your-code-scanning-configuration/set-code-scanning-merge-protection). For more general information about rulesets, see [About rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

## Analysis category

Use `category` to distinguish between multiple analyses for the same tool and commit, but performed on different languages or different parts of the code. The category you specify in your workflow will be included in the SARIF results file.

This parameter is particularly useful if you work with monorepos and have multiple SARIF files for different components of the monorepo.

```yaml copy
    - name: Perform CodeQL Analysis
      uses: github/codeql-action/analyze@v4
      with:
        # Optional. Specify a category to distinguish between multiple analyses
        # for the same tool and ref. If you don't use `category` in your workflow,
        # GitHub will generate a default category name for you
        category: "my_category"
```

If you don't specify a `category` parameter in your workflow, GitHub will generate a category name for you, based on the name of the workflow file triggering the action, the action name, and any matrix variables. For example:

* The `.github/workflows/codeql-analysis.yml` workflow and the `analyze` action will produce the category `.github/workflows/codeql.yml:analyze`.
* The `.github/workflows/codeql-analysis.yml` workflow, the `analyze` action, and the `{language: javascript-typescript, os: linux}` matrix variables will produce the category `.github/workflows/codeql-analysis.yml:analyze/language:javascript-typescript/os:linux`.

The `category` value will appear as the `<run>.automationDetails.id` property in SARIF v2.1.0. For more information, see [SARIF support for code scanning](/en/code-security/code-scanning/integrating-with-code-scanning/sarif-support-for-code-scanning#runautomationdetails-object).

Your specified category will not overwrite the details of the `runAutomationDetails` object in the SARIF file, if included.

## CodeQL model packs

If your codebase depends on a library or framework that is not recognized by the standard queries in CodeQL, you can extend the CodeQL coverage in your code scanning workflow by specifying published CodeQL model packs. For more information about creating your own model packs, see [Creating and working with CodeQL packs](/en/code-security/codeql-cli/using-the-advanced-functionality-of-the-codeql-cli/creating-and-working-with-codeql-packs#creating-a-model-pack).

> \[!NOTE]
> CodeQL model packs are currently in public preview and subject to change. Model packs are supported for C/C++, C#, Java/Kotlin, Python, Ruby, and Rust analysis.
>
> The CodeQL model editor in the CodeQL extension for Visual Studio Code supports modeling dependencies for  C#, Java/Kotlin, Python, and Ruby.

### Using CodeQL model packs

To add one or more published CodeQL model packs, specify them inside the `with: packs:` entry within the `uses: github/codeql-action/init@v4` section of the workflow. Within `packs` you specify one or more packages to use and, optionally, which version to download. Where you don't specify a version, the latest version is downloaded. If you want to use packages that are not publicly available, you need to set the `GITHUB_TOKEN` environment variable to a secret that has access to the packages. For more information, see [Use GITHUB\_TOKEN for authentication in workflows](/en/actions/security-guides/automatic-token-authentication) and [Using secrets in GitHub Actions](/en/actions/security-guides/encrypted-secrets).

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    config-file: ./.github/codeql/codeql-config.yml
    queries: security-extended
    packs: my-company/my-java-queries@~7.8.9,my-repo/my-java-model-pack
```

In this example, the default queries will be run for Java, as well as the queries from a version greater than or equal to `7.8.9` and less than `7.9.0` of the query pack `my-company/my-java-queries`. The dependencies modeled in the latest version of the model pack `my-repo/my-java-model-pack` will be available to both the default queries and those in `my-company/my-java-queries`.

## Non-default queries

When you use CodeQL to scan code, the CodeQL analysis engine generates a database from the code and runs queries on it. CodeQL analysis uses a default set of queries, but you can specify more queries to run, in addition to the default queries.

> \[!TIP]
> You can also specify the queries you want to exclude from analysis, or include in the analysis. This requires the use of a custom configuration file. For more information, see [Custom configuration files](#custom-configuration-files) and [Excluding specific queries from analysis](#excluding-specific-queries-from-analysis) below.

You can run extra queries if they are part of a CodeQL pack published to the GitHub Container registry or a CodeQL pack stored in a repository. For more information, see [About code scanning with CodeQL](/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning-with-codeql#about-codeql-queries).

The options available to specify the additional queries you want to run are:

* `packs` to install one or more CodeQL query packs and run the default query suite or queries for those packs.
* `queries` to specify a single *.ql* file, a directory containing multiple *.ql* files, a *.qls* query suite definition file, or any combination. For more information about query suite definitions, see [Creating CodeQL query suites](https://codeql.github.com/docs/codeql-cli/creating-codeql-query-suites/).

You can use both `packs` and `queries` in the same workflow.

We don't recommend referencing query suites directly from the `github/codeql` repository, for example, `github/codeql/cpp/ql/src@main`. Such queries would have to be recompiled, and may not be compatible with the version of CodeQL currently active on GitHub Actions, which could lead to errors during analysis.

### Using query packs

To add one or more CodeQL query packs, add a `with: packs:` entry within the `uses: github/codeql-action/init@v4` section of the workflow. Within `packs` you specify one or more packages to use and, optionally, which version to download. Where you don't specify a version, the latest version is downloaded. If you want to use packages that are not publicly available, you need to set the `GITHUB_TOKEN` environment variable to a secret that has access to the packages. For more information, see [Use GITHUB\_TOKEN for authentication in workflows](/en/actions/security-guides/automatic-token-authentication) and [Using secrets in GitHub Actions](/en/actions/security-guides/encrypted-secrets).

> \[!NOTE]
> For workflows that generate CodeQL databases for multiple languages, you must instead specify the CodeQL query packs in a configuration file. For more information, see [Specifying CodeQL query packs](#specifying-codeql-query-packs) below.

In the example below, `scope` is the organization or personal account that published the package. When the workflow runs, the four CodeQL query packs are downloaded from GitHub and the default queries or query suite for each pack run:

* The latest version of `pack1` is downloaded and all default queries are run.
* Version 1.2.3 of `pack2` is downloaded and all default queries are run.
* The latest version of `pack3` that is compatible with version 3.2.1 is downloaded and all queries are run.
* Version 4.5.6 of `pack4` is downloaded and only the queries found in `path/to/queries` are run.

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    # Comma-separated list of packs to download
    packs: scope/pack1,scope/pack2@1.2.3,scope/pack3@~3.2.1,scope/pack4@4.5.6:path/to/queries
```

> \[!NOTE]
> If you specify a particular version of a query pack to use, beware that the version you specify may eventually become too old to be used efficiently by the default CodeQL engine used by the CodeQL action. To ensure optimal performance, if you need to specify exact query pack versions, you should consider reviewing periodically whether the pinned version of the query pack needs to be moved forward.
>
> For more information about pack compatibility, see [CodeQL query packs reference](/en/code-security/reference/code-scanning/codeql/codeql-cli/codeql-query-packs#codeql-pack-compatibility).

### Downloading CodeQL packs from GitHub Enterprise Server

If your workflow uses packs that are published on a GitHub Enterprise Server installation, you need to tell your workflow where to find them. You can do this by using the `registries` input of the github/codeql-action/init\@v4 action. This input accepts a list of `url`, `packages`, and `token` properties as shown below.

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    registries: |
      # URL to the container registry, usually in this format
      - url: https://containers.GHEHOSTNAME1/v2/

        # List of package glob patterns to be found at this registry
        packages:
          - my-company/*
          - my-company2/*

        # Token, which should be stored as a secret
        token: ${{ secrets.GHEHOSTNAME1_TOKEN }}

      # URL to the default container registry
      - url: https://ghcr.io/v2/
        # Packages can also be a string
        packages: "*/*"
        token: ${{ secrets.GHCR_TOKEN }}

    
```

The package patterns in the registries list are examined in order, so you should generally place the most specific package patterns first. The values for `token` must be a personal access token (classic) generated by the GitHub instance you are downloading from with the `read:packages` permission.

Notice the `|` after the `registries` property name. This is important since GitHub Actions inputs can only accept strings. Using the `|` converts the subsequent text to a string, which is parsed later by the github/codeql-action/init\@v4 action.

### Using queries in QL packs

To add one or more queries, add a `with: queries:` entry within the `uses: github/codeql-action/init@v4` section of the workflow. If the queries are in a private repository, use the `external-repository-token` parameter to specify a token that has access to checkout the private repository.

You can also specify query suites in the value of `queries`. Query suites are collections of queries, usually grouped by purpose or language.

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    # Comma-separated list of queries / packs / suites to run.
    # This may include paths or a built in suite, for example:
    # security-extended or security-and-quality.
    queries: security-extended
    # Optional. Provide a token to access queries stored in private repositories.
    external-repository-token: ${{ secrets.ACCESS_TOKEN }}
```

The following query suites are built into CodeQL code scanning and are available for use.

| Query suite            | Description                                                                    |
| :--------------------- | :----------------------------------------------------------------------------- |
| `security-extended`    | Queries from the default suite, plus lower severity and precision queries      |
| `security-and-quality` | Queries from `security-extended`, plus maintainability and reliability queries |

For more information, see: [CodeQL query suites](/en/code-security/code-scanning/managing-your-code-scanning-configuration/built-in-codeql-query-suites).

Each of these query suites contains a different subset of the queries included in the built-in CodeQL query pack for that language. The query suites are automatically generated using the metadata for each query. For more information, see [Metadata for CodeQL queries](https://codeql.github.com/docs/writing-codeql-queries/metadata-for-codeql-queries/).

<!--See lists of query tables linked in the reusable above.-->

When you specify a query suite, the CodeQL analysis engine will run the default set of queries and any extra queries defined in the additional query suite.

### Working with custom configuration files

If you also use a configuration file for custom settings, any additional packs or queries specified in your workflow are used instead of those specified in the configuration file. If you want to run the combined set of additional packs or queries, prefix the value of `packs` or `queries` in the workflow with the `+` symbol. For more information, see [Custom configuration files](#custom-configuration-files).

In the following example, the `+` symbol ensures that the specified additional packs and queries are used together with any specified in the referenced configuration file.

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    config-file: ./.github/codeql/codeql-config.yml
    queries: +security-and-quality,octo-org/python-qlpack/show_ifs.ql@main
    packs: +scope/pack1,scope/pack2@1.2.3,scope/pack3@4.5.6:path/to/queries
```

<!-- Anchor to maintain the current CodeQL CLI manual pages link: https://aka.ms/code-scanning-docs/config-file -->

## Custom configuration files

A custom configuration file is an alternative way to specify additional packs and queries to run. You can also use the file to disable the default queries, exclude or include specific queries, and to specify which directories to scan during analysis.

In the workflow file, use the `config-file` parameter of the `init` action to specify the path to the configuration file you want to use. This example loads the configuration file *./.github/codeql/codeql-config.yml*.

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    config-file: ./.github/codeql/codeql-config.yml
```

The configuration file can be located within the repository you are analyzing, or in an external repository. Using an external repository allows you to specify configuration options for multiple repositories in a single place. When you reference a configuration file located in an external repository, you can use the *OWNER/REPOSITORY/FILENAME\@BRANCH* syntax. For example, *octo-org/shared/codeql-config.yml\@main*.

If the configuration file is located in an external private repository, use the `external-repository-token` parameter of the `init` action to specify a token that has access to the private repository.

```yaml copy
- uses: github/codeql-action/init@v4
  with:
    external-repository-token: ${{ secrets.ACCESS_TOKEN }}
```

The settings in the configuration file are written in YAML format.

### Specifying CodeQL query packs

You specify CodeQL query packs in an array. Note that the format is different from the format used by the workflow file.

```yaml copy
packs:
  # Use the latest version of 'pack1' published by 'scope'
  - scope/pack1
  # Use version 1.2.3 of 'pack2'
  - scope/pack2@1.2.3
  # Use the latest version of 'pack3' compatible with 3.2.1
  - scope/pack3@~3.2.1
  # Use pack4 and restrict it to queries found in the 'path/to/queries' directory
  - scope/pack4:path/to/queries
  # Use pack5 and restrict it to the query 'path/to/single/query.ql'
  - scope/pack5:path/to/single/query.ql
  # Use pack6 and restrict it to the query suite 'path/to/suite.qls'
  - scope/pack6:path/to/suite.qls
```

The full format for specifying a query pack is `scope/name[@version][:path]`. Both `version` and `path` are optional. `version` is semver version range. If it is missing, the latest version is used. For more information about semver ranges, see the [semver docs on npm](https://docs.npmjs.com/cli/v6/using-npm/semver#ranges).

If you have a workflow that generates more than one CodeQL database, you can specify any CodeQL query packs to run in a custom configuration file using a nested map of packs.

```yaml copy
packs:
  # Use these packs for JavaScript and TypeScript analysis
  javascript:
    - scope/js-pack1
    - scope/js-pack2
  # Use these packs for Java and Kotlin analysis
  java:
    - scope/java-pack1
    - scope/java-pack2@v1.0.0
```

### Extending CodeQL coverage with threat models

> \[!NOTE]
> Threat models are currently in public preview and subject to change. During the public preview, threat models are supported only by analysis for Java/Kotlin and C#.

The default threat model includes remote sources of untrusted data. You can extend the CodeQL threat model to include local sources of untrusted data (for example: command-line arguments, environment variables, file systems, and databases) by specifying `threat-models: local` in a custom configuration file. If you extend the threat model, the default threat model will also be used.

### Specifying additional queries

You specify additional queries in a `queries` array. Each element of the array contains a `uses` parameter with a value that identifies a single query file, a directory containing query files, or a query suite definition file.

```yaml copy
queries:
  - uses: ./my-basic-queries/example-query.ql
  - uses: ./my-advanced-queries
  - uses: ./query-suites/my-security-queries.qls
```

Optionally, you can give each array element a name, as shown in the example configuration files below. For more information about additional queries, see [Non-default queries](#non-default-queries) above.

### Disabling the default queries

If you only want to run custom queries, you can disable the default security queries by using `disable-default-queries: true`.

### Excluding specific queries from analysis

You can add `exclude` and `include` filters to your custom configuration file, to specify the queries you want to exclude or include in the analysis.

This is useful if you want to exclude, for example:

* Specific queries from the default suites (`security`, `security-extended` and `security-and-quality`).
* Specific queries whose results do not interest you.
* All the queries that generate warnings and recommendations.

You can use `exclude` filters similar to those in the configuration file below to exclude queries that you want to remove from the default analysis. In the example of configuration file below, both the `js/redundant-assignment` and the `js/useless-assignment-to-local` queries are excluded from analysis.

```yaml copy
query-filters:
  - exclude:
      id: js/redundant-assignment
  - exclude:
      id: js/useless-assignment-to-local
```

To find the id of a query, you can click the alert in the list of alerts in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab. This opens the alert details page. The `Rule ID` field contains the query id. For more information about the alert details page, see [About code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/about-code-scanning-alerts#about-alert-details).

> \[!TIP]
>
> * The order of the filters is important. The first filter instruction that appears after the instructions about the queries and query packs determines whether the queries are included or excluded by default.
> * Subsequent instructions are executed in order and the instructions that appear later in the file take precedence over the earlier instructions.

You can find another example illustrating the use of these filters in the [Example configuration files](#example-configuration-files) section.

For more information about using `exclude` and `include` filters in your custom configuration file, see [Creating CodeQL query suites](/en/code-security/codeql-cli/using-the-advanced-functionality-of-the-codeql-cli/creating-codeql-query-suites#filtering-the-queries-in-a-query-suite). For information on the query metadata you can filter on, see [Metadata for CodeQL queries](https://codeql.github.com/docs/writing-codeql-queries/metadata-for-codeql-queries/).

### Specifying directories to scan

When codebases are analyzed without building the code, you can restrict code scanning to files in specific directories by adding a `paths` array to the configuration file. You can also exclude the files in specific directories from analysis by adding a `paths-ignore` array. You can use this option when you run the CodeQL actions on an interpreted language (Python, Ruby, and JavaScript/TypeScript) or when you analyze a compiled language without building the code (currently supported for C/C++, C#, Java and Rust).

```yaml copy
paths:
  - src
paths-ignore:
  - src/node_modules
  - '**/*.test.js'
```

> \[!NOTE]
>
> * The `paths` and `paths-ignore` keywords, used in the context of the code scanning configuration file, should not be confused with the same keywords when used for `on.<push|pull_request>.paths` in a workflow. When they are used to modify `on.<push|pull_request>` in a workflow, they determine whether the actions will be run when someone modifies code in the specified directories. For more information, see [Workflow syntax for GitHub Actions](/en/actions/using-workflows/workflow-syntax-for-github-actions#onpushpull_requestpull_request_targetpathspaths-ignore).
> * The filter pattern characters `?`, `+`, `[`, `]`, and `!` are not supported and will be matched literally.
> * `**` characters can only be at the start or end of a line, or surrounded by slashes, and you can't mix `**` and other characters. For example, `foo/**`, `**/foo`, and `foo/**/bar` are all allowed syntax, but `**foo` isn't. However you can use single stars along with other characters, as shown in the example. You'll need to quote anything that contains a `*` character.

For analysis where code is built, if you want to limit code scanning to specific directories in your project, you must specify appropriate build steps in the workflow. The commands you need to use to exclude a directory from the build will depend on your build system. For more information, see [CodeQL code scanning for compiled languages](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/codeql-code-scanning-for-compiled-languages#adding-build-steps-for-a-compiled-language).

You can quickly analyze small portions of a monorepo when you modify code in specific directories. You'll need to both exclude directories in your build steps and use the `paths-ignore` and `paths` keywords for [`on.<push|pull_request>`](/en/actions/using-workflows/workflow-syntax-for-github-actions#onpushpull_requestpull_request_targetpathspaths-ignore) in your workflow.

<!-- Anchor to maintain the old CodeQL CLI manual pages link: https://aka.ms/docs-config-file -->

### Example configuration files

This configuration file adds the `security-and-quality` query suite to the list of queries run by CodeQL when scanning your code. For more information about the query suites available for use, see [Non-default queries](#non-default-queries).

```yaml
name: "My CodeQL config"

queries:
  - uses: security-and-quality
```

The following configuration file disables the default queries and specifies a set of custom queries to run instead. It also configures CodeQL to scan files in the *src* directory (relative to the root), except for the *src/node\_modules* directory, and except for files whose name ends in *.test.js*. Files in *src/node\_modules* and files with names ending *.test.js* are therefore excluded from analysis.

```yaml
name: "My CodeQL config"

disable-default-queries: true

queries:
  - name: Use an in-repository CodeQL pack (run queries in the my-queries directory)
    uses: ./my-queries
  - name: Use an external JavaScript CodeQL pack (run queries from an external repo)
    uses: octo-org/javascript-codeql-pack@main
  - name: Use an external query (run a single query from an external CodeQL pack)
    uses: octo-org/python-codeql-pack/show_ifs.ql@main
  - name: Use a query suite file (run queries from a query suite in this repo)
    uses: ./codeql-packs/complex-python-codeql-pack/rootAndBar.qls

paths:
  - src
paths-ignore:
  - src/node_modules
  - '**/*.test.js'
```

The following configuration file only runs queries that generate alerts of severity error. The configuration first selects all the default queries, all queries in `./my-queries`, and the default suite in `codeql/java-queries`, then excludes all the queries that generate warnings or recommendations.

```yaml
queries:
  - name: Use an in-repository CodeQL query pack (run queries in the my-queries directory)
    uses: ./my-queries
packs:
  - codeql/java-queries
query-filters:
- exclude:
    problem.severity:
      - warning
      - recommendation
```

## Configuration details

If you'd prefer to specify additional configuration details in the workflow file, you can use the `config` input of the `init` command of the CodeQL action. The value of this input must be a YAML string that follows the configuration file format documented at [Custom configuration files](#custom-configuration-files) above.

### Example configuration

This step in a GitHub Actions workflow file uses a `config` input to disable the default queries, add the `security-extended` query suite, and exclude queries that are tagged with `cwe-020`.

```yaml
- uses: github/codeql-action/init@v4
  with:
    languages: ${{ matrix.language }}
    config: |
      disable-default-queries: true
      threat-models: local
      queries:
        - uses: security-extended
      query-filters:
        - exclude:
            tags: /cwe-020/
```

You can use the same approach to specify any valid configuration options in the workflow file.

> \[!TIP]
> You can share one configuration across multiple repositories using GitHub Actions variables. One benefit of this approach is that you can update the configuration in a single place without editing the workflow file.
>
> In the following example, `vars.CODEQL_CONF` is a GitHub Actions variable. Its value can be the contents of any valid configuration file. For more information, see [Store information in variables](/en/actions/learn-github-actions/variables#defining-configuration-variables-for-multiple-workflows).
>
> ```yaml
> - uses: github/codeql-action/init@v4
>   with:
>     languages: ${{ matrix.language }}
>     config: ${{ vars.CODEQL_CONF }}
> ```

## Compiled languages

For compiled languages, you can decide how the CodeQL action creates a CodeQL database for analysis. For information about the build options available, see [CodeQL code scanning for compiled languages](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/codeql-code-scanning-for-compiled-languages).

## Data upload

GitHub can display code analysis data generated externally by a third-party tool. You can upload code analysis data with the `upload-sarif` action. For more information, see [Uploading a SARIF file to GitHub](/en/code-security/code-scanning/integrating-with-code-scanning/uploading-a-sarif-file-to-github).