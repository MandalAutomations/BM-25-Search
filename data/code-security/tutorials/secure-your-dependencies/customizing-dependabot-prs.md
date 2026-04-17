# Customizing Dependabot pull requests to fit your processes

Learn how to tailor your Dependabot pull requests to better suit your own internal workflows.

There are various ways to customize your Dependabot pull requests so that they better suit your own internal processes.

For example, to integrate Dependabot's pull requests into your CI/CD pipelines, it can apply **custom labels** to pull requests, which you can then use to trigger action workflows.

There are several different customization options which can all be used in combination, and tailored per package ecosystem.

## Automatically adding assignees

By default, Dependabot raises pull requests without any assignees.

To automatically assign pull requests to a designated security team, you can use `assignees` to set these values per package ecosystem.

The example `dependabot.yml` file below changes the npm configuration so that all pull requests opened with version and security updates for npm have:

* An individual ("`user-name`") automatically assigned to the pull requests.

```yaml copy
# `dependabot.yml` file with
#  assignee for all npm pull requests

version: 2
updates:
  # Keep npm dependencies up to date
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
    # Raise all npm pull requests with assignees
    assignees:
      - "user-name"
```

## Automatically adding reviewers

By default, Dependabot raises pull requests without any reviewers.

To ensure your project's security updates get addressed promptly by the appropriate team, you can automatically add reviewers to Dependabot pull requests using a CODEOWNERS file. See [About code owners](/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners).

## Labeling pull requests with custom labels

By default, Dependabot raises pull requests with the `dependencies` label.

Dependabot also applies an ecosystem label, such as `java`, `npm`, or `github-actions`, to pull requests. Dependabot adds both the `dependencies` label and the ecosystem label to all pull requests, including single-ecosystem updates, to improve filtering and triaging.

Dependabot creates the default labels it applies to pull requests if they do not already exist in the repository. If you want to use custom labels instead of the defaults, you can set the `labels` option in your `dependabot.yml` file per package ecosystem; this overrides the defaults. For more information, see [Managing labels](/en/issues/using-labels-and-milestones-to-track-work/managing-labels) and [`labels`](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#labels--).

If semantic version (SemVer) labels are present in the repository, Dependabot will also automatically apply them to indicate the type of version update (`major`, `minor`, or `patch`). These labels are applied in addition to any custom labels you define.

You can use `labels` to override the default labels and specify your own custom labels per package ecosystem. This is useful if, for example, you want to:

* Use labels to assign a priority to certain pull requests.
* Use labels to trigger another workflow, such as automatically adding the pull request onto a project board.

The example `dependabot.yml` file below changes the npm configuration so that all pull requests opened with version and security updates for npm have custom labels.

```yaml copy
# `dependabot.yml` file with
# customized npm configuration

version: 2
updates:
  # Keep npm dependencies up to date
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
    # Raise all npm pull requests with custom labels
    labels:
      - "npm dependencies"
      - "triage-board"
```

Setting this option will also affect pull requests for security updates to the manifest files of this package manager, unless you use `target-branch` to check for version updates on a non-default branch.

See also [`labels`](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#labels--).

## Adding a prefix to commit messages

By default, Dependabot attempts to detect your commit message preferences and use similar patterns. In addition, Dependabot populates the titles of pull requests based on the commit messages.

You can specify your own prefix for Dependabot's commit messages (and pull request titles) for a specific package ecosystem. This can be useful if, for example, you're running automations that process commit messages or pull requests titles.

To specify your preferences explicitly, use `commit-message` together with the following supported options:

* `prefix`:
  * Specifies a prefix for all commit messages.
  * Prefix is also added to the start of the pull request title.
* `prefix-development`:
  * Specifies a separate prefix for all commit messages that update development dependencies, as defined by the package manager or ecosystem.
  * Supported for `bundler`, `composer`, `mix`, `maven`, `npm`, and `pip`.
* `include: "scope"`:
  * Specifies that any prefix is followed by the dependency types (`deps` or `deps-dev`) updated in the commit.

The example below shows several different options, tailored per package ecosystem:

```yaml copy
# Customize commit messages

version: 2
updates:
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
    commit-message:
      # Prefix all commit messages with "npm: "
      prefix: "npm"

  - package-ecosystem: "docker"
    directory: "/"
    schedule:
      interval: "weekly"
    commit-message:
      # Prefix all commit messages with "[docker] " (no colon, but a trailing whitespace)
      prefix: "[docker] "

  - package-ecosystem: "composer"
    directory: "/"
    schedule:
      interval: "weekly"
    # Prefix all commit messages with "Composer" plus its scope, that is, a
    # list of updated dependencies
    commit-message:
      prefix: "Composer"
      include: "scope"

  - package-ecosystem: "pip"
    directory: "/"
    schedule:
      interval: "weekly"
    # Include a list of updated dependencies
    # with a prefix determined by the dependency group
    commit-message:
      prefix: "pip prod"
      prefix-development: "pip dev"
```

Setting this option will also affect pull requests for security updates to the manifest files of this package manager, unless you use `target-branch` to check for version updates on a non-default branch.

See also [`commit-message`](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#commit-message--).

## Associating pull requests with a milestone

Milestones help you track the progress of groups of pull requests (or issues) towards a project goal or release. With Dependabot, you can use the `milestone` option to associate pull requests for dependency updates with a specific milestone.

You must specify the numeric identifier of the milestone and not its label. To find the numeric identifier, check the final part of the page URL, after `milestone`. For example, for `https://github.com/<org>/<repo>/milestone/3`, "`3`" is the numeric identifier of the milestone.

```yaml copy
# Specify a milestone for pull requests

version: 2
updates:
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
    # Associate pull requests with milestone "4"
    milestone: 4
```

Setting this option will also affect pull requests for security updates to the manifest files of this package manager, unless you use `target-branch` to check for version updates on a non-default branch.

See also [`milestone`](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#milestone--) and [About milestones](/en/issues/using-labels-and-milestones-to-track-work/about-milestones).

## Changing the separator in the pull request branch name

Dependabot generates a branch for each pull request. Each branch name includes `dependabot`, as well as the name of the package manager and the dependency to be updated. By default, these parts of the branch name are separated by a `/` symbol, for example:

* `dependabot/npm_and_yarn/next_js/acorn-6.4.1`

To maintain supportability or consistency with your existing processes, you may need to ensure your branch names align with your team's existing conventions. In this case, you can use `pull-request-branch-name.separator` to specify a different separator, choosing either `_`, `/`, or `"-"`.

In the below example, the npm configuration changes the default separator from `/` to `"-"`, so that it would appear as such:

* Default (`/`): `dependabot/npm_and_yarn/next_js/acorn-6.4.1`
* Customized (`"-"`): `dependabot-npm_and_yarn-next_js-acorn-6.4.1`

Note that the hyphen symbol (`"-"`) must be surrounded by quotation marks so that it's not interpreted as starting an empty YAML list.

```yaml copy
# Specify a different separator for branch names

version: 2
updates:
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
    pull-request-branch-name:
      # Change the default separator (/) to a hyphen (-)
      separator: "-"
```

Setting this option will also affect pull requests for security updates to the manifest files of this package manager, unless you use `target-branch` to check for version updates on a non-default branch.

See also [`pull-request-branch-name.separator`](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#pull-request-branch-nameseparator--).

## Targeting pull requests against a non-default branch

By default, Dependabot checks for manifest files on the default branch and raises pull requests for updates against the default branch.

Generally, it makes most sense to keep Dependabot's checks and updates on the default branch. However, there may be some cases where you may need to specify a different target branch. If, for example, your team's processes require you to first test and validate updates on a non-production branch, you can use `target-branch` to specify a different branch for Dependabot to raise pull requests against.

> \[!NOTE]
> Dependabot raises pull requests for security updates against the **default branch only**. If you use `target-branch`, then as a result, all configuration settings for that package manager will then *only* apply to version updates, and not security updates.

```yaml copy
# Specify a non-default branch for pull requests for pip

version: 2
updates:
  - package-ecosystem: "pip"
    directory: "/"
    schedule:
      interval: "weekly"
    # Raise pull requests for version updates
    # to pip against the `develop` branch
    target-branch: "develop"
    # Labels on pull requests for version updates only
    labels:
      - "pip dependencies"

  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
      # Check for npm updates on Sundays
      day: "sunday"
    # Labels on pull requests for security and version updates
    labels:
      - "npm dependencies"
```

See also [`target-branch`](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#target-branch-).