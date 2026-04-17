# Creating rulesets for repositories in your organization

You can create a ruleset to target multiple repositories in your organization.

## Introduction

For customers on GitHub Team or GitHub Enterprise plans you can create rulesets in your organization to control how users can interact with repositories in your organization. You can control things like who can push commits to a certain branch and how the commits must be formatted, or who can delete or rename a tag. You can also prevent people from renaming repositories.

You can also create push rulesets to block pushes to a private or internal repository and the repository's entire fork network. Push rulesets allow you to block pushes based on file extensions, file path lengths, file and folder paths, and file sizes.

Forks do not inherit branch or tag rulesets from their upstream repositories. However, forks owned by your organization are subject to the rulesets you create, like any other repository.

Forks *do* inherit push rulesets from their root repository. Push rules apply to the entire fork network for a repository, ensuring every entry point to the repository is protected. For example, if you fork a repository that has push rulesets enabled, the same push rulesets will also apply to your forked repository.

For a forked repository, the only people who have bypass permissions for a push rule are the people who have bypass permissions in the root repository.

## Importing prebuilt rulesets

To import one of the prebuilt rulesets by GitHub, see [`github/ruleset-recipes`](https://github.com/github/ruleset-recipes).

You can import an existing ruleset using a JSON file. This can be useful if you want to apply the same ruleset to multiple repositories or organizations. For more information, see [Managing rulesets for repositories in your organization](/en/organizations/managing-organization-settings/managing-rulesets-for-repositories-in-your-organization#importing-a-ruleset).

## Using `fnmatch` syntax

You can use `fnmatch` syntax to define patterns to target when you create a ruleset.

You can use the `*` wildcard to match any string of characters. Because GitHub uses the `File::FNM_PATHNAME` flag for the `File.fnmatch` syntax, the `*` wildcard does not match directory separators (`/`). For example, `qa/*` will match all branches beginning with `qa/` and containing a single slash, but will not match `qa/foo/bar`. You can include any number of slashes after `qa` with `qa/**/*`, which would match, for example, `qa/foo/bar/foobar/hello-world`. You can also extend the `qa` string with `qa**/**/*` to make the rule more inclusive.

For more information about syntax options, see the [fnmatch documentation](https://ruby-doc.org/core-2.5.1/File.html#method-c-fnmatch).

## Using ruleset enforcement statuses

While creating or editing your ruleset, you can use enforcement statuses to configure how your ruleset will be enforced.

You can select any of the following enforcement statuses for your ruleset.

* **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Active:** your ruleset will be enforced upon creation.
* **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-skip" aria-label="skip" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm9.78-2.22-5.5 5.5a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734l5.5-5.5a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Disabled:** your ruleset will not be enforced.

## Creating a branch or tag ruleset

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.

2. Select an organization by clicking on it.

3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)

4. In the left sidebar, in the "Code, planning, and automation" section, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-repo" aria-label="repo" role="img"><path d="M2 2.5A2.5 2.5 0 0 1 4.5 0h8.75a.75.75 0 0 1 .75.75v12.5a.75.75 0 0 1-.75.75h-2.5a.75.75 0 0 1 0-1.5h1.75v-2h-8a1 1 0 0 0-.714 1.7.75.75 0 1 1-1.072 1.05A2.495 2.495 0 0 1 2 11.5Zm10.5-1h-8a1 1 0 0 0-1 1v6.708A2.486 2.486 0 0 1 4.5 9h8ZM5 12.25a.25.25 0 0 1 .25-.25h3.5a.25.25 0 0 1 .25.25v3.25a.25.25 0 0 1-.4.2l-1.45-1.087a.249.249 0 0 0-.3 0L5.4 15.7a.25.25 0 0 1-.4-.2Z"></path></svg> Repository**, then click **Rulesets**.

   ![Screenshot of an organization's settings page. In the sidebar, a link labeled "Rulesets" is outlined in orange.](/assets/images/help/organizations/sidebar-repository-rulesets.png)

5. Click **New ruleset**.

6. To create a ruleset targeting branches, click **New branch ruleset**. Alternatively, to create a ruleset targeting tags, click **New tag ruleset**.

7. Under "Ruleset name," type a name for the ruleset.

8. Optionally, to change the default enforcement status, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-skip" aria-label="skip" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm9.78-2.22-5.5 5.5a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734l5.5-5.5a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Disabled** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> and select an enforcement status.

### Choosing which repositories to target in your organization

With your ruleset, you can choose to target all repositories in your organization or a list of manually selected repositories. You can also filter by naming convention, deployment context, or custom properties.

For more information about custom properties, see [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization).

If a repository is targeted by a ruleset created at the organization level, only owners of the organization can edit the ruleset. However, people with admin access to the repository, or with a custom role including the "edit repository rules" permission, can create additional rulesets at the repository level. The rules in these rulesets will be aggregated with the rules defined at the organization level. The result is that creating a new ruleset can make the rules targeting a branch or tag more restrictive, but never less restrictive. For more information on creating rulesets, see [About rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

#### Targeting repositories by properties in your organization

You can target repositories in your organization by custom properties. See [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization).

1. To target a dynamic list of repositories in your organization by properties, in the "Target repositories" section, next to "Repository targeting criteria" select **Repositories matching a filter**.
2. To add a target, in the filter section, **enter a query** for example, `visibility:private props.team:infra -language:java` or **Select by filter**.
3. In the modal dialog that appears, select custom or system properties from the dropdown menu, then select a value for each property.
4. Click **Apply**.

#### Targeting all repositories in your organization

To target all repositories in your organization, in the "Target repositories" section, next to "Repository targeting criteria", select **All repositories**.

#### Targeting select repositories in your organization

1. To target a static, manually selected list of repositories in your organization, in the "Target repositories" section, next to "Repository targeting criteria", select  **Only selected repositories**.
2. To select repositories to target, in the "Targeting criteria" section, select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-repo" aria-label="repo" role="img"><path d="M2 2.5A2.5 2.5 0 0 1 4.5 0h8.75a.75.75 0 0 1 .75.75v12.5a.75.75 0 0 1-.75.75h-2.5a.75.75 0 0 1 0-1.5h1.75v-2h-8a1 1 0 0 0-.714 1.7.75.75 0 1 1-1.072 1.05A2.495 2.495 0 0 1 2 11.5Zm10.5-1h-8a1 1 0 0 0-1 1v6.708A2.486 2.486 0 0 1 4.5 9h8ZM5 12.25a.25.25 0 0 1 .25-.25h3.5a.25.25 0 0 1 .25.25v3.25a.25.25 0 0 1-.4.2l-1.45-1.087a.249.249 0 0 0-.3 0L5.4 15.7a.25.25 0 0 1-.4-.2Z"></path></svg> Select repositories**, then search for the name of each repository you would like to target. Select each repository from the search results.

#### Targeting repositories by naming convention in your organization

1. To target a dynamic list of repositories in your organization by naming convention, in the "Target repositories" section, next to "Repository targeting criteria", select **Repositories matching a name**.

2. To begin defining a targeting pattern, in the "Targeting criteria" section, select **Add a target** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg>, then click **Include by pattern** or **Exclude by pattern**.

3. In the modal dialog that appears, enter a repository naming pattern using `fnmatch` syntax, then click **Add Inclusion pattern** or **Add Exclusion pattern**. For more information on `fnmatch` syntax, see [Using `fnmatch` syntax](#using-fnmatch-syntax).

   > \[!NOTE]
   > You can add multiple targeting criteria to the same ruleset. For example, you could include any repositories matching the pattern `*cat*`, then specifically exclude a repository matching the pattern `not-a-cat`.

4. Optionally, on the ruleset configuration page, select **Prevent renaming of target repositories**.

#### Targeting repositories by deployment context

If your organization has added records to the linked artifacts page, you can target repositories that are **deployable** (have an active storage record) or **deployed** (have an active deployment record). See [About linked artifacts](/en/code-security/concepts/supply-chain-security/linked-artifacts).

1. In the "Target repositories" section, next to "Repository targeting criteria" select **Repositories matching a filter**.
2. Next to "Repositories matching a filter", click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Open filter dialog" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> icon.
3. Use the `deployed:true` or `deployable:true` filters to target repositories.
4. Click **Apply**.

### Choosing which branches or tags to target

To target branches or tags, in the "Target branches" or "Target tags" section, select **Add a target**, then select how you want to include or exclude branches or tags. You can use `fnmatch` syntax to include or exclude branches or tags based on a pattern. For more information, see [Using `fnmatch` syntax](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/creating-rulesets-for-a-repository#using-fnmatch-syntax).

You can add multiple targeting criteria to the same ruleset. For example, you could include the default branch, include any branches matching the pattern `*feature*`, and then specifically exclude a branch matching the pattern `not-a-feature`.

### Selecting branch or tag protections

In the "Branch protections" or "Tag protections" section, select the rules you want to include in the ruleset. When you select a rule, you may be able to enter additional settings for the rule. For more information on the rules, see [Available rules for rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets).

> \[!NOTE]
> If you select **Require status checks before merging**, in the "Additional settings" section:
>
> * You can enter the name of each status check you would like to require. To finish adding the status check as a requirement, you must click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Add selected status checks" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>.
> * If you select **Require branches to be up to date before merging**, you must define a check for the protection to take effect.

### Finalizing your branch or tag ruleset and next steps

To finish creating your ruleset, click **Create**. If the enforcement status of the ruleset is set to "Active", the ruleset takes effect immediately.

## Creating a push ruleset

> \[!NOTE]
> This ruleset will enforce push restrictions for a repository's entire fork network.

You can create a push ruleset for private or internal repositories in your organization.

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. Select an organization by clicking on it.
3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)
4. In the left sidebar, in the "Code, planning, and automation" section, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-repo" aria-label="repo" role="img"><path d="M2 2.5A2.5 2.5 0 0 1 4.5 0h8.75a.75.75 0 0 1 .75.75v12.5a.75.75 0 0 1-.75.75h-2.5a.75.75 0 0 1 0-1.5h1.75v-2h-8a1 1 0 0 0-.714 1.7.75.75 0 1 1-1.072 1.05A2.495 2.495 0 0 1 2 11.5Zm10.5-1h-8a1 1 0 0 0-1 1v6.708A2.486 2.486 0 0 1 4.5 9h8ZM5 12.25a.25.25 0 0 1 .25-.25h3.5a.25.25 0 0 1 .25.25v3.25a.25.25 0 0 1-.4.2l-1.45-1.087a.249.249 0 0 0-.3 0L5.4 15.7a.25.25 0 0 1-.4-.2Z"></path></svg> Repository**, then click **Rulesets**.

   ![Screenshot of an organization's settings page. In the sidebar, a link labeled "Rulesets" is outlined in orange.](/assets/images/help/organizations/sidebar-repository-rulesets.png)
5. Click **New ruleset**.
6. To create a ruleset targeting branches, click **New push ruleset**.
7. Under "Ruleset name," type a name for the ruleset.
8. Optionally, to change the default enforcement status, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-skip" aria-label="skip" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm9.78-2.22-5.5 5.5a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734l5.5-5.5a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Disabled** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> and select an enforcement status.

### Granting bypass permissions for your push ruleset

> \[!NOTE] Bypass permissions for push rulesets that target a repository will be inherited by the entire fork network for this repository. This means that the only users who can bypass this ruleset for any repository in this repository's entire fork network are the users who can bypass this ruleset in the root repository.

You can grant certain roles, teams, or apps bypass permissions  for your ruleset. The following are eligible for bypass access:

* Repository admins, organization owners, and enterprise owners
* The maintain or write role, or custom repository roles based on the write role
* Teams, excluding secret teams. See [About organization teams](/en/organizations/organizing-members-into-teams/about-teams#team-visibility).
* GitHub Apps
* Dependabot. For more information about Dependabot, see [Dependabot quickstart guide](/en/code-security/getting-started/dependabot-quickstart-guide).

1. To grant bypass permissions for the ruleset, in the "Bypass list" section, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add bypass**.
2. In the "Add bypass" modal dialog that appears, search for the role, team, or app you would like to grant bypass permissions, then select the role, team, or app from the "Suggestions" section and click **Add Selected**.

### Choosing which repositories to target in your organization

With your ruleset, you can choose to target all repositories in your organization or a list of manually selected repositories. You can also filter by naming convention, deployment context, or custom properties.

For more information about custom properties, see [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization).

If a repository is targeted by a ruleset created at the organization level, only owners of the organization can edit the ruleset. However, people with admin access to the repository, or with a custom role including the "edit repository rules" permission, can create additional rulesets at the repository level. The rules in these rulesets will be aggregated with the rules defined at the organization level. The result is that creating a new ruleset can make the rules targeting a branch or tag more restrictive, but never less restrictive. For more information on creating rulesets, see [About rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

#### Targeting repositories by properties in your organization

You can target repositories in your organization by custom properties. See [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization).

1. To target a dynamic list of repositories in your organization by properties, in the "Target repositories" section, next to "Repository targeting criteria" select **Repositories matching a filter**.
2. To add a target, in the filter section, **enter a query** for example, `visibility:private props.team:infra -language:java` or **Select by filter**.
3. In the modal dialog that appears, select custom or system properties from the dropdown menu, then select a value for each property.
4. Click **Apply**.

#### Targeting all repositories in your organization

To target all repositories in your organization, in the "Target repositories" section, next to "Repository targeting criteria", select **All repositories**.

#### Targeting select repositories in your organization

1. To target a static, manually selected list of repositories in your organization, in the "Target repositories" section, next to "Repository targeting criteria", select  **Only selected repositories**.
2. To select repositories to target, in the "Targeting criteria" section, select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-repo" aria-label="repo" role="img"><path d="M2 2.5A2.5 2.5 0 0 1 4.5 0h8.75a.75.75 0 0 1 .75.75v12.5a.75.75 0 0 1-.75.75h-2.5a.75.75 0 0 1 0-1.5h1.75v-2h-8a1 1 0 0 0-.714 1.7.75.75 0 1 1-1.072 1.05A2.495 2.495 0 0 1 2 11.5Zm10.5-1h-8a1 1 0 0 0-1 1v6.708A2.486 2.486 0 0 1 4.5 9h8ZM5 12.25a.25.25 0 0 1 .25-.25h3.5a.25.25 0 0 1 .25.25v3.25a.25.25 0 0 1-.4.2l-1.45-1.087a.249.249 0 0 0-.3 0L5.4 15.7a.25.25 0 0 1-.4-.2Z"></path></svg> Select repositories**, then search for the name of each repository you would like to target. Select each repository from the search results.

#### Targeting repositories by naming convention in your organization

1. To target a dynamic list of repositories in your organization by naming convention, in the "Target repositories" section, next to "Repository targeting criteria", select **Repositories matching a name**.

2. To begin defining a targeting pattern, in the "Targeting criteria" section, select **Add a target** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg>, then click **Include by pattern** or **Exclude by pattern**.

3. In the modal dialog that appears, enter a repository naming pattern using `fnmatch` syntax, then click **Add Inclusion pattern** or **Add Exclusion pattern**. For more information on `fnmatch` syntax, see [Using `fnmatch` syntax](#using-fnmatch-syntax).

   > \[!NOTE]
   > You can add multiple targeting criteria to the same ruleset. For example, you could include any repositories matching the pattern `*cat*`, then specifically exclude a repository matching the pattern `not-a-cat`.

4. Optionally, on the ruleset configuration page, select **Prevent renaming of target repositories**.

#### Targeting repositories by deployment context

If your organization has added records to the linked artifacts page, you can target repositories that are **deployable** (have an active storage record) or **deployed** (have an active deployment record). See [About linked artifacts](/en/code-security/concepts/supply-chain-security/linked-artifacts).

1. In the "Target repositories" section, next to "Repository targeting criteria" select **Repositories matching a filter**.
2. Next to "Repositories matching a filter", click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Open filter dialog" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> icon.
3. Use the `deployed:true` or `deployable:true` filters to target repositories.
4. Click **Apply**.

### Selecting push protections

You can block pushes to this repository and this repository's entire fork network based on file extensions, file path lengths, file and folder paths, and file sizes.

Any push protections you configure will block pushes in this repository and throughout this repository's entire fork network.

1. Under "Push protections," click the restrictions you want to apply. Then fill in the details for the restrictions you select.

   For file path restrictions, you can use partial or full paths. You can use `fnmatch` syntax for this. For example, a restriction targeting `test/demo/**/*` prevents any pushes to files or folders in the `test/demo/` directory. A restriction targeting `test/docs/pushrules.md` prevents pushes specifically to the `pushrules.md` file in the `test/docs/` directory. For more information, see [Creating rulesets for a repository](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/creating-rulesets-for-a-repository#using-fnmatch-syntax).

### Finalizing your push ruleset and next steps

To finish creating your ruleset, click **Create**. If the enforcement status of the ruleset is set to "Active", the ruleset takes effect immediately.