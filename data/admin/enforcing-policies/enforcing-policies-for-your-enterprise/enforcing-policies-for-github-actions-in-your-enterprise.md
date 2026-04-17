# Enforcing policies for GitHub Actions in your enterprise

You can enforce policies to manage how GitHub Actions can be used within your enterprise.

## What are policies for GitHub Actions?

Enterprise policies control the options that are available to enterprise members when they use GitHub Actions.

If you don't enforce enterprise policies, organization owners and users with the "Manage organization Actions policies" permission have full control over GitHub Actions for their organizations.

> \[!NOTE] GitHub Actions must be enabled for repositories in an organization for the CodeQL code scanning default setup and GitHub Code Quality workflows to run. However, the CodeQL default setup for code scanning is not affected by other GitHub Actions policies (such as restricting access to public actions or reusable workflows).

## Enforcing policies

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Policies**.
3. Under "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Policies", click **Actions**.
4. After you configure each policy, click **Save**.

For more information about each section of the "Policies" page, continue reading.

## Policies

In the "Policies" section, you can control which organizations within your enterprise can use GitHub Actions, with the following options:

* Enable GitHub Actions for all organizations
* Enable GitHub Actions for specific organizations
* Disable GitHub Actions for all organizations

> \[!NOTE]
> If you disable GitHub Actions, or do not enable the feature for one or more organizations, this blocks affected organizations from using code scanning and GitHub Code Quality analysis.

### Controlling access to public actions and reusable workflows

Enterprises often want to limit access to only a well-tested group of public actions and reusable workflows as part of their supply chain governance. The policies available in GitHub allow you to control access without blocking the dynamic workflows used by code scanning and GitHub Code Quality.

You can enforce strict controls without defining exceptions or additional configuration for code scanning and GitHub Code Quality, with the following options:

* **Allow all actions and reusable workflows:** Any action or reusable workflow can be used, regardless of who authored it or where it is defined.
* **Allow enterprise actions and reusable workflows:** Only actions and reusable workflows defined in a repository within the enterprise can be used. Blocks all access to actions authored by GitHub, such as the [`actions/checkout`](https://github.com/actions/checkout) action.
* **Allow enterprise, and select non-enterprise, actions and reusable workflows**: Any action or reusable workflow defined in a repository within the enterprise can be used, plus any action or reusable workflow that matches criteria you specify.
* **Require actions to be pinned to a full-length commit SHA**: All actions must be pinned to a full-length commit SHA to be used. This includes actions from your enterprise and actions authored by GitHub. Reusable workflows can still be referenced by tag. For more information, see [Secure use reference](/en/enterprise-cloud@latest/actions/reference/security/secure-use#using-third-party-actions).

<span id="allowing-select-actions-and-reusable-workflows-to-run" ></span>

### **Allow enterprise, and select non-enterprise, actions and reusable workflows**

If you choose this option, actions and reusable workflows within your enterprise are allowed, and you'll have the following options for allowing other actions and reusable workflows:

* **Allow actions created by GitHub:** Allows all actions created by GitHub, located in the [`actions`](https://github.com/actions) and [`github`](https://github.com/github) organizations.
* **Allow Marketplace actions by verified creators:** Allows all GitHub Marketplace actions created by verified creators, labeled with <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-verified" aria-label="The verified badge" role="img"><path d="m9.585.52.929.68c.153.112.331.186.518.215l1.138.175a2.678 2.678 0 0 1 2.24 2.24l.174 1.139c.029.187.103.365.215.518l.68.928a2.677 2.677 0 0 1 0 3.17l-.68.928a1.174 1.174 0 0 0-.215.518l-.175 1.138a2.678 2.678 0 0 1-2.241 2.241l-1.138.175a1.17 1.17 0 0 0-.518.215l-.928.68a2.677 2.677 0 0 1-3.17 0l-.928-.68a1.174 1.174 0 0 0-.518-.215L3.83 14.41a2.678 2.678 0 0 1-2.24-2.24l-.175-1.138a1.17 1.17 0 0 0-.215-.518l-.68-.928a2.677 2.677 0 0 1 0-3.17l.68-.928c.112-.153.186-.331.215-.518l.175-1.14a2.678 2.678 0 0 1 2.24-2.24l1.139-.175c.187-.029.365-.103.518-.215l.928-.68a2.677 2.677 0 0 1 3.17 0ZM7.303 1.728l-.927.68a2.67 2.67 0 0 1-1.18.489l-1.137.174a1.179 1.179 0 0 0-.987.987l-.174 1.136a2.677 2.677 0 0 1-.489 1.18l-.68.928a1.18 1.18 0 0 0 0 1.394l.68.927c.256.348.424.753.489 1.18l.174 1.137c.078.509.478.909.987.987l1.136.174a2.67 2.67 0 0 1 1.18.489l.928.68c.414.305.979.305 1.394 0l.927-.68a2.67 2.67 0 0 1 1.18-.489l1.137-.174a1.18 1.18 0 0 0 .987-.987l.174-1.136a2.67 2.67 0 0 1 .489-1.18l.68-.928a1.176 1.176 0 0 0 0-1.394l-.68-.927a2.686 2.686 0 0 1-.489-1.18l-.174-1.137a1.179 1.179 0 0 0-.987-.987l-1.136-.174a2.677 2.677 0 0 1-1.18-.489l-.928-.68a1.176 1.176 0 0 0-1.394 0ZM11.28 6.78l-3.75 3.75a.75.75 0 0 1-1.06 0L4.72 8.78a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L7 8.94l3.22-3.22a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg>.
* **Allow or block specified actions and reusable workflows:** Allows actions and reusable workflows that you specify. You can specify individual actions and reusable workflows or entire organizations and repositories.

When specifying actions and reusable workflows, use the following syntax:

* To restrict access to specific tags or commit SHAs of an action or reusable workflow, use the same syntax used in the workflow to select the action or reusable workflow.
  * For an action, the syntax is `OWNER/REPOSITORY@TAG-OR-SHA`. For example, use `actions/javascript-action@v1.0.1` to select a tag or `actions/javascript-action@a824008085750b8e136effc585c3cd6082bd575f` to select a SHA.
  * For a reusable workflow, the syntax is `OWNER/REPOSITORY/PATH/FILENAME@TAG-OR-SHA`. For example, `octo-org/another-repo/.github/workflows/workflow.yml@v1`.
* To specify a pattern, use the wildcard character, `*`.
  * To allow all actions and reusable workflows in organizations that start with `space-org`, use `space-org*/*`.
  * To allow all actions and reusable workflows in repositories that start with octocat, use `*/octocat**@*`.
* To specify multiple patterns, use `,` to separate patterns.
  * To allow all actions and reusable workflows from the `octocat` and `octokit` organizations, use `octocat/*, octokit/*`.
* To block specific patterns, use the `!` prefix.
  * To allow all actions and reusable workflows from the `space-org` organization, but block a specific action like `space-org/action`, use `space-org/*, !space-org/action@*`.
  * By default, only actions and reusable workflows specified in the list will be allowed. To allow all actions and reusable workflows while also blocking specific actions, use `*, !space-org/action@*`.

Policies never restrict access to local actions on the runner filesystem (where the `uses:` path start with `./`).

## Runners

By default, anyone with admin access to a repository can add a self-hosted runner for the repository, and self-hosted runners come with risks:

* There is no guarantee that self-hosted runners will be hosted on ephemeral, clean virtual machines. As a result, they may be compromised by untrusted code in a workflow.
* Anyone who can fork the repository and open a pull request can compromise the self-hosted runner environment, potentially gaining access to secrets and the `GITHUB_TOKEN`, which may have write access to the repository.

In the "Runners" section, you can mediate these risks by disabling the use of repository-level self-hosted runners.

* **Disable for all organizations:** Prevents the creation of runners at the repository level.
* **Disable in all Enterprise Managed User (EMU) repositories:** Prevents the creation of runners for repositories owned by managed user accounts.

> \[!NOTE] When creation of repository-level self-hosted runners is disabled, workflows can still access self-hosted runners at the enterprise or organization level.

## Custom images

In the "Custom images" section, you can control which organizations in your enterprise are allowed to create and manage custom images with the following access policy:

* **Enable for all organizations**: All organizations, including any created in the future, may use or create custom images.
* **Enable for specific organizations**: Only selected organizations may use or create custom images.
* **Disable for all organizations**: No organization may use or create custom images.

### Custom images retention policies

You can define how long custom image versions are retained and when they become inactive.

* **Maximum versions per image**: Limits how many versions of each image are retained. When this limit is exceeded, the oldest unused image versions are automatically deleted.
  * **Default**: 20 versions
  * **Configurable range**: 1–100 versions
* **Unused version retention**: Deletes image versions that have not been used for a specified number of days. Image versions that are assigned to a runner pool but not actively used are also considered unused.
  * **Default**: 30 days
  * **Configurable range**: 1–90 days
* **Maximum version age**: Disables image versions that were created earlier than the specified number of days. Disabled image versions cannot be used by runners until the policy limit is increased.
  * **Default**: 60 days
  * **Configurable range**: 7–90 days

## Artifact and log retention

By default, artifacts and log files generated by workflows are retained for 90 days. You can change the retention period.

* For public repositories, you can configure a period between 1 and 90 days.
* For private and internal repositories, you can configure a period between 1 and 400 days.

Changes only apply to new artifacts and log files.

### Cache settings

You can configure maximum cache retention and size limits that will apply across your entire enterprise. If you increase the "Cache size eviction limit" beyond the 10 GB included in your plan, you will be charged for any additional storage of cached entries.

By default:

* Caches are retained for 7 days before automatic deletion.
* The total cache storage limit is 10 GB per repository.

You can customize these settings to set maximum limits for cache retention and cache storage size across your enterprise:

* **Cache retention**: Configure up to 90 days for public repositories or 365 days for private and internal repositories.
* **Cache size eviction limit**: Configure up to 10,000 GB per repository.

The settings you configure at the enterprise level act as maximum limits. Organization owners can opt in to configure limits for their organization, but cannot exceed the limits set at the enterprise level. Repository administrators can opt in to configure limits for their repositories, but cannot exceed the limits set at the organization level.

For more information about cache eviction, see [Dependency caching reference](/en/enterprise-cloud@latest/actions/reference/workflows-and-actions/dependency-caching#usage-limits-and-eviction-policy).

## Fork pull request workflows from outside collaborators

Anyone can fork a public repository, then submit a pull request to propose changes to the repository's workflows. To prevent abuse, workflows will not run automatically on pull requests created by some contributors.

You can configure which pull requests require approval before they are run.

> \[!WARNING] When requiring approvals only for first-time contributors (the first two settings), a user that has had any commit or pull request merged into the repository will not require approval. A malicious user could meet this requirement by getting a simple typo or other innocuous change accepted by a maintainer, either as part of a pull request they have authored or as part of another user's pull request.

* **Require approval for first-time contributors who are new to GitHub**. Requires approval for users who have never committed to the repository and have new GitHub accounts.
* **Require approval for first-time contributors**. Requires approval for users who have never committed to the repository.
* **Require approval for all outside collaborators**. Requires approval for all users who are not organization members.

> \[!NOTE] Workflows on the base branch triggered by `pull_request_target` events will always run, regardless of approval settings.

## Fork pull request workflows in private repositories

You can control how users can run workflows on `pull_request` events in private and internal repositories.

* **Run workflows from fork pull requests**. Users can run workflows from fork pull requests. By default, workflows will use a `GITHUB_TOKEN` with read-only permission, with no access to secrets.
* **Send write tokens to workflows from pull requests**. Workflows will use a `GITHUB_TOKEN` with write permission.
* **Send secrets to workflows from pull requests**. All secrets are available to the pull request.
* **Require approval for fork pull request workflows**. Workflows on pull requests from collaborators without write permission will require approval from someone with write permission before they will run.

If a policy is enabled for an enterprise, the policy can be selectively disabled in individual organizations or repositories. If a policy is disabled for an enterprise, individual organizations or repositories cannot enable it.

## Workflow permissions

In the "Workflow permissions" section, you can set the **default** permissions granted to the `GITHUB_TOKEN`.

* **Read and write permissions:** The default permissions for the `GITHUB_TOKEN` depend on when the enterprise or organization was created:

  * **Created on or after February 2, 2023** – Defaults to **read-only** access for all scopes.
  * **Created before February 2, 2023** – Defaults to **read and write** access for all scopes.

* **Read repository contents and packages permissions:** By default, `GITHUB_TOKEN` has only read access for the `contents` and `packages` scopes. The more permissive setting cannot be chosen as the default for individual organizations or repositories.

Anyone with write access to a repository can still modify the permissions granted to the `GITHUB_TOKEN` for a specific workflow, by editing the `permissions` key in the workflow file.

**Allow GitHub Actions to create and approve pull requests** is disabled by default. If you enable this setting, `GITHUB_TOKEN` can create and approve pull requests.