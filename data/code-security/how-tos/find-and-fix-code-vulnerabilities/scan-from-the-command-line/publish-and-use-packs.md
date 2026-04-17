# Publishing and using CodeQL packs

Share or download a CodeQL pack, then analyze your CodeQL database.

## Authenticating to GitHub Container registries

You can publish packs and download private packs by authenticating to the appropriate GitHub Container registry.

You can authenticate to the Container registry in two ways:

1. Pass the `--github-auth-stdin` option to the CodeQL CLI, then supply a GitHub Apps token or personal access token via standard input.
2. Set the `GITHUB_TOKEN` environment variable to a GitHub Apps token or personal access token.

## Publishing your CodeQL pack

To share your CodeQL pack with other people, you can publish it to the Container registry.

### Configuring the `qlpack.yml` file before publishing

You can check and modify the configuration details of your CodeQL pack prior to publishing. Open the `qlpack.yml` file in your preferred text editor.

```yaml
library: # set to true if the pack is a library. Set to false or omit for a query pack
name: <scope>/<pack>
version: <x.x.x>
description: <Description to publish with the package>
defaultSuite: # optional, one or more queries in the pack to run by default
    - query: <relative-path>/query-file>.ql
defaultSuiteFile: default-queries.qls # optional, a pointer to a query-suite in this pack
license: # optional, the license under which the pack is published
dependencies: # map from CodeQL pack name to version range
```

* `name:` must follow the `<scope>/<pack>` format, where `<scope>` is the GitHub organization that you will publish to and `<pack>` is the name for the pack.

* A maximum of one of `defaultSuite` or `defaultSuiteFile` is allowed. These are two different ways to define a default query suite to be run, the first by specifying queries directly in the qlpack.yml file and the second by specifying a query suite in the pack.

### Running `codeql pack publish`

When you are ready to publish a pack to the GitHub Container registry, you can run the following command in the root of the pack directory:

```shell
codeql pack publish
```

The published package will be displayed in the packages section of GitHub organization specified by the scope in the `qlpack.yml` file.

> \[!NOTE]
> If you're publishing model packs to the GitHub Container registry in order to extend coverage to all repositories in an organization as part of a default setup configuration, then you need to ensure that repositories running code scanning can access those model packs. For more information, see [Editing your configuration of default setup](/en/code-security/code-scanning/managing-your-code-scanning-configuration/editing-your-configuration-of-default-setup) and [Configuring a package's access control and visibility](/en/packages/learn-github-packages/configuring-a-packages-access-control-and-visibility).

## Downloading an existing CodeQL pack

To run a pack that someone else has created, you must first download it by running the following command:

```shell
codeql pack download <scope>/<pack>@x.x.x
```

* `<scope>`: the name of the GitHub organization that you will download from.
* `<pack>`: the name for the pack that you want to download.
* `@x.x.x`: an optional version number. If omitted, the latest version will be downloaded.

This command accepts arguments for multiple packs.

If you write scripts that specify a particular version number of a
query pack to download, keep in mind that when you update your version of
CodeQL to a newer one, you may
also need to switch to a newer version of the query pack. Newer
versions of CodeQL *may* provide
degraded performance when used with query packs that have been pinned
to a very old version. For more information, see [CodeQL query packs reference](/en/code-security/reference/code-scanning/codeql/codeql-cli/codeql-query-packs#codeql-pack-compatibility).

## Using a CodeQL pack to analyze a CodeQL database

To analyze a CodeQL database with a CodeQL pack, run the following command:

```shell
codeql database analyze <database> <scope>/<pack>@x.x.x:<path>
```

* `<database>`: the CodeQL database to be analyzed.
* `<scope>`: the name of the GitHub organization that the pack is published to.
* `<pack>`: the name for the pack that you are using.
* `@x.x.x`: an optional version number. If omitted, the latest version will be used.
* `:<path>`: an optional path to a query, directory, or query suite. If omitted, the pack’s default query suite will be used.

The `analyze` command will run the default suite of any specified CodeQL packs. You can specify multiple CodeQL packs to be used for analyzing a CodeQL database. For example:

```shell
codeql <database> analyze <scope>/<pack> <scope>/<other-pack>
```

> \[!NOTE]
> The `codeql pack download` command stores the pack it downloads in an internal location that is not intended for local modification. Unexpected (and hard to troubleshoot) behavior may result if the pack is modified after downloading. For more information about customizing packs, see [Creating and working with CodeQL packs](/en/code-security/codeql-cli/using-the-advanced-functionality-of-the-codeql-cli/creating-and-working-with-codeql-packs).