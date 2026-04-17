# Governing how people use repositories in your enterprise

Create a repository policy to control who can do things like create and delete repositories.

> \[!NOTE] Repository policies are currently in public preview and subject to change.
> You can have up to 75 total policies and rulesets per organization, and up to 75 total policies and rulesets per enterprise.

To govern key events in the lifecycle of your repositories, such as who can create or delete repositories, you can create a repository policy. A repository policy is a collection of restrictions that gives you flexible control over which users are affected and which repositories are targeted.

In a repository policy, you can restrict:

* Which **visibilities** are permitted for new repositories and visibility changes.
* Who can **create** repositories.
* Who can **delete** repositories.
* Who can **transfer** repositories out of an organization.
* How people can **name** repositories.

> \[!TIP] If you're an **organization owner**, you can create a repository policy for a specific organization. See [Governing how people use repositories in your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/governing-how-people-use-repositories-in-your-organization).

## Examples

You can use a repository policy to do things like:

* Ensure all new repositories use a certain naming convention, such as `kebab-case`.
* Prevent repository deletions except by organization admins.
* Allow public repositories to be created only in the "open source" organization in your enterprise.
* Prevent public repositories from being changed to private to avoid potential loss of metadata.

## How will I target repositories?

First, you'll target organizations in your enterprise. You can select all organizations, choose from a list, or create a dynamic rule using `fnmatch` syntax. If you use Enterprise Managed Users, you can also choose to target all repositories owned by users in your enterprise.

Then, you'll target repositories in the selected organizations. We recommend using repository policies alongside **custom repository properties**. By adding custom properties to repositories, you will be able to flexibly target those repositories in a policy.

For example, you can add a property to mark repositories that contain production data or other sensitive information, then prevent anyone from making those repositories public.

To create and set custom properties, see [Managing custom properties for repositories in your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization).

## Interaction with other policies

Some of the available restrictions are duplicates of policies you may have set on the "Member privileges" page in your organization or enterprise settings.

Creating a repository policy does **not** override your existing "member privilege" policies. Instead, the policies are additive, so that the most restrictive version of a policy applies. This applies both to **member privilege policies** and to other **repository policies** that people have created at the enterprise or organization level.

Compared to member privilege policies, repository policies have several advantages:

* They offer more flexible targeting of organizations and repositories.
* They allow you to give certain actors the option to bypass the policies.
* They're visible to organization owners, so there is more transparency around what is permitted.
* They allow you to target repositories owned by Enterprise Managed Users.

## Creating a repository policy

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Policies**.
3. Under "Policies", click **Repository**.
4. Click **New policy**.
5. Configure your new policy, then click **Create**. For help, consult the following subsections.

### Policy name

Use something descriptive to communicate the purpose of the policy. Organization owners can view the policy, so good names help add clarity. For example: `Prevent public repos on production`.

### Enforcement status

If you don't want the policy to be enforced when it's created, set to "Disabled". Otherwise, set to "Active".

### Allow list

Choose which roles can **bypass** the restrictions in this policy.

### Targets

Choose which organizations and repositories the policy applies to.

#### Target organizations

Select all organizations, choose a selection of existing organizations, or set a dynamic list by name. If you use Enterprise Managed Users, you can also choose to target all repositories owned by users in your enterprise.

If you set a dynamic list, you'll add one or more naming patterns using `fnmatch` syntax. For example, the string `*open-source` would match any organization with a name that ends with `open-source`. For syntax details, see [Creating rulesets for a repository](/en/enterprise-cloud@latest/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/creating-rulesets-for-a-repository#using-fnmatch-syntax).

#### Target repositories

Choose which repositories (current or future) to target in the selected organizations. You can select all repositories or set a dynamic list by custom property.

### Policies

Choose which restrictions are included. When the policy is active, the restrictions apply across all targeted repositories, but can be bypassed by users or teams on the allow list.

If you choose the "Restrict names" policy, you must use **regular expression** syntax to set a pattern that repository names must or must not match. For example, a pattern to enforce `kebab-case` naming would look like `^([a-z][a-z0-9]*)(-[a-z0-9]+)*$`.

* Patterns support RE2 syntax. See Google's [syntax guide](https://github.com/google/re2/wiki/Syntax).
* To validate your expressions, click **Test pattern**, then enter a pattern and test value.

### Delegating bypass of policies

> \[!NOTE] Repository policy delegated bypass is in public preview and subject to change.

Delegated bypass for repository policies lets you control who can bypass repository policies for repository deletions and visibility changes.

With delegated bypass, repository administrators must submit a request to change the visibility of the repository or delete the repository. The request is sent to a designated group of reviewers, who either approve or deny the request to bypass repository policies.

If the request to bypass repository policies is approved, the request change is completed immediately. If the request is denied, the requested change will not be made but may be re-requested.

To configure delegated bypass, enterprise owners or organization owners first create a "bypass list". The bypass list includes specific roles and teams, such as team or repository administrators, who oversee requests to bypass repository policies.

#### Managing bypass requests

## Managing requests to bypass push rules

> \[!NOTE] Repository policy delegated bypass is in public preview and subject to change.

You can view and manage all requests for bypass privileges on the “Bypass Requests" page, located under the **Policy** settings.

You can filter requests by approver (member of the bypass list), requester (contributor making the request), timeframe, and status. The following statuses are assigned to a request:

| Status      | Description                                                                                                                  |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `Cancelled` | The request has been cancelled by the contributor.                                                                           |
| `Completed` | The request has been approved and the commit(s) have been pushed to the repository.                                          |
| `Denied`    | The request has been reviewed and denied.                                                                                    |
| `Expired`   | The request has expired. Requests are valid for 7 days.                                                                      |
| `Open`      | The request has either not yet been reviewed, or has been approved but the commit(s) have not been pushed to the repository. |

When a contributor requests bypass privileges to push a commit containing restricted content, members of the bypass list all receive an email notification containing a link to the request. Members of the bypass list then have 7 days to review and either approve or deny the request before the request expires.

The contributor is notified of the decision by email and must take the required action. If the request is approved, the contributor can push the commit containing the restricted content to the repository. If the request is denied, the contributor must remove the restricted content from the commit in order to successfully push the commit to the repository.

## Further reading

To set additional policies for repository management, see [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise).