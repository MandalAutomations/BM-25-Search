# GitHub Actions helper

Generate and improve GitHub Actions workflows.

> \[!NOTE]
>
> * The examples in this library are intended for inspiration—you are encouraged to adjust them to be more specific to your projects, languages, and team processes.
> * For community-contributed examples of custom instructions for specific languages and scenarios, see the [Awesome GitHub Copilot Customizations](https://github.com/github/awesome-copilot/blob/main/docs/README.instructions.md) repository.
> * You can apply custom instructions across different scopes, depending on the platform or IDE where you are creating them. For more information, see "[About customizing GitHub Copilot responses](/en/copilot/concepts/response-customization)."

The following example shows a path-specific `actions.instructions.md` file that applies only to GitHub Actions workflow files in your repository, using the `applyTo` field. For more information about path-specific instructions files, see [Adding repository custom instructions for GitHub Copilot](/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions#using-one-or-more-instructionsmd-files).

````text copy
---
applyTo: ".github/workflows/**/*.yml"
---

When generating or improving GitHub Actions workflows:

## Security First
- Use GitHub secrets for sensitive data, never hardcode credentials
- Pin third-party actions to specific commits by using the SHA value (e.g., `- uses: owner/some-action@a824008085750b8e136effc585c3cd6082bd575f`)
- Configure minimal permissions for GITHUB_TOKEN required for the workflow

## Performance Essentials
- Cache dependencies with `actions/cache` or built-in cache options
- Add `timeout-minutes` to prevent hung workflows
- Use matrix strategies for multi-environment testing

## Best Practices
- Use descriptive names for workflows, jobs, and steps
- Include appropriate triggers: `push`, `pull_request`, `workflow_dispatch`
- Add `if: always()` for cleanup steps that must run regardless of failure

## Example Pattern
```yaml
name: CI
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - uses: actions/checkout@v5
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
      - run: npm ci
      - run: npm test
```
````

## Further reading

* [About customizing GitHub Copilot responses](/en/copilot/concepts/response-customization) - Overview of response customization in GitHub Copilot
* [Configure custom instructions for GitHub Copilot](/en/copilot/how-tos/configure-custom-instructions) - How to configure custom instructions
* [Awesome GitHub Copilot Customizations](https://github.com/github/awesome-copilot/blob/main/README.md) - Repository of community-contributed custom instructions and other customizations for specific languages and scenarios