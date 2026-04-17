# Configuring multi-ecosystem updates for Dependabot

Reduce the number of Dependabot pull requests you receive by grouping updates across multiple ecosystems into a single, consolidated pull request.

Multi-ecosystem updates allow you to consolidate Dependabot pull requests across different package ecosystems into a single PR per group. See [Multi-ecosystem updates](/en/code-security/concepts/supply-chain-security/multi-ecosystem-updates).

## Prerequisites

* A repository with dependencies in multiple package ecosystems
* An existing `.github/dependabot.yml` file. See [Configuring Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates).

## 1. Define your multi-ecosystem group in your `.github/dependabot.yml` file

Start by defining a group with a schedule in the top-level `multi-ecosystem-groups` section:

```yaml copy
version: 2

multi-ecosystem-groups:
  infrastructure:
    schedule:
      interval: "weekly"

updates:
  # Your existing package ecosystems will go here
```

## 2. Assign ecosystems to the group

Add the `multi-ecosystem-groups` key and patterns to your package ecosystem configurations.

```yaml copy
version: 2

multi-ecosystem-groups:
  infrastructure:
    schedule:
      interval: "weekly"

updates:
  - package-ecosystem: "docker"
    directory: "/"
    patterns: ["nginx", "redis", "postgres"]
    multi-ecosystem-group: "infrastructure"

  - package-ecosystem: "terraform"
    directory: "/"
    patterns: ["aws", "terraform-*"]
    multi-ecosystem-group: "infrastructure"
```

> \[!NOTE]
> Use `["*"]` to include all dependencies.

## 3. Commit your changes

Commit the changes to your `dependabot.yml` file.

## 4. Customize with additional keys (optional)

You can add assignees, labels, or other configuration options to your multi-ecosystem groups. See [`assignees`](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#assignees--) and [`labels`](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#labels--).

```yaml copy
multi-ecosystem-groups:
  infrastructure:
    schedule:
      interval: "weekly"
    assignees: ["@platform-team"]
    labels: ["infrastructure", "dependencies"]

updates:
  - package-ecosystem: "docker"
    directory: "/"
    patterns: ["nginx", "redis", "postgres"]
    multi-ecosystem-group: "infrastructure"

  - package-ecosystem: "terraform"
    directory: "/"
    patterns: ["aws", "terraform-*"]
    multi-ecosystem-group: "infrastructure"
```

For a complete list of available options, see [Dependabot options reference](/en/code-security/reference/supply-chain-security/dependabot-options-reference#multi-ecosystem-groups).

## 5. Verify your configuration

After committing your changes, you can verify the configuration:

1. Navigate to your repository's **Insights** tab.
2. Select **Dependency graph**, then **Dependabot**.
3. Confirm your multi-ecosystem group appears in the list.

The next time the scheduled update runs, you'll receive a single pull request with updates from all ecosystems in the group.

## Troubleshooting

If you're not seeing consolidated pull requests, ensure that:

* The `patterns` key is defined for each ecosystem (required when using `multi-ecosystem-group`).
* All ecosystems use the same group name in the `multi-ecosystem-group` field.

## Further reading

* [Dependabot options reference](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference)