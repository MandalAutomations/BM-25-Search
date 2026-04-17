# Repository properties for code scanning

You can use repository properties to adjust code scanning to suit your needs.

## Prerequisites

For the repository properties described here to have an effect, you need to have set up code scanning. See [About setup types for code scanning](/en/code-security/concepts/code-scanning/setup-types).

Repository properties which affect code scanning must be created manually for your organization. You can then set values for them that apply to your entire organization or allow them to be configured differently for each repository. See [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization).

## Supported repository properties for code scanning

Some code scanning functionality can be configured using repository properties. Organizations can use repository properties to both enforce configurations across all repositories and for individual repositories. If code scanning is customized using repository properties, the customization applies to all setup types.

The following is an overview of repository properties you can set up which affect code scanning analyses when configured:

| Name                                 | Type       |
| ------------------------------------ | ---------- |
| `github-codeql-extra-queries`        | Text       |
| `github-codeql-disable-overlay`      | True/false |
| `github-codeql-file-coverage-on-prs` | True/false |

> \[!NOTE]
> The repository properties which are supported depend on the version of the [github/codeql-action](https://github.com/github/codeql-action/) that is used by your code scanning analyses. For code scanning advanced setup, check that your workflow is referencing the latest major version. Code scanning default setup automatically uses the latest version.

### Analysis customization

The `github-codeql-extra-queries` property allows you to configure additional queries that should be run. This is useful to add queries to all relevant analyses in your organization without needing to modify individual workflows or switch to an advanced setup. This accepts the same values as the `queries` input of the [github/codeql-action](https://github.com/github/codeql-action/). See [Workflow configuration options for code scanning](/en/code-security/reference/code-scanning/workflow-configuration-options).

### Enabling or disabling features

You can disable improved incremental analysis by setting the `github-codeql-disable-overlay` property to `true`. This may be useful if improved incremental analysis is failing because of increased hardware requirements.

File coverage information is not calculated for analyses of pull requests. If you want to enable file coverage information for pull requests, you can set the `github-codeql-file-coverage-on-prs` property to `true`.