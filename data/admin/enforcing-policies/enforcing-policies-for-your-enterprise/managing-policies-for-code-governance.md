# Managing code rulesets for repositories in your enterprise

You can edit, monitor, and delete existing rulesets to alter how people can interact with repositories in your enterprise.

After creating a ruleset at the enterprise level, you can make changes to the ruleset to alter how people can interact with the targeted repositories. For example, you can:

* Add rules to better protect the branches or tags in those repositories
* Switch your ruleset from "Evaluate" mode to "Active" after testing its effects on the contributor experience

> \[!NOTE]
> Anyone with read access to a repository can view the active rulesets operating on that repository.

## About delegated bypass

Delegated bypass for push rulesets lets you control who can bypass push protection and which blocked pushes should be allowed.

With delegated bypass, contributors to a repository must request "bypass privileges" when pushing commits that contain restricted content. The request is sent to a designated group of reviewers, who either approve or deny the request to bypass push rules.

If the request to bypass push rules is approved, the contributor can push the commit containing restricted content. If the request is denied, the contributor must remove the content from the commit (or commits) containing the restricted content before pushing again.

To configure delegated bypass, organization owners or repository administrators first create a "bypass list". The bypass list includes specific roles and teams, such as team or repository administrators, who oversee requests to bypass push protection. For more information, see [Managing rulesets for repositories in your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/managing-rulesets-for-repositories-in-your-organization) and [About rulesets](/en/enterprise-cloud@latest/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

## Editing a ruleset

You can edit a ruleset to change parts of the ruleset, such as the name, bypass permissions, or rules. You can also edit a ruleset to change its status, such as if you want to enable or temporarily disable a ruleset.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. In the left sidebar, in the "Policies" section, click  **Code**, then click **Rulesets**.

3. On the "Rulesets" page, click the name of the ruleset you want to edit.

4. Change the ruleset as required.

   For information on the available rules, see [Available rules for rulesets](/en/enterprise-cloud@latest/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets)

5. At the bottom of the page, click **Save changes**.

## Deleting a ruleset

> \[!NOTE]
> Anyone with read access to a repository can view the active rulesets operating on that repository.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. In the left sidebar, in the "Policies" section, click **Code**, then click **Rulesets**.
3. To the right of the ruleset's name, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Open additional options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-trash" aria-label="trash" role="img"><path d="M11 1.75V3h2.25a.75.75 0 0 1 0 1.5H2.75a.75.75 0 0 1 0-1.5H5V1.75C5 .784 5.784 0 6.75 0h2.5C10.216 0 11 .784 11 1.75ZM4.496 6.675l.66 6.6a.25.25 0 0 0 .249.225h5.19a.25.25 0 0 0 .249-.225l.66-6.6a.75.75 0 0 1 1.492.149l-.66 6.6A1.748 1.748 0 0 1 10.595 15h-5.19a1.75 1.75 0 0 1-1.741-1.575l-.66-6.6a.75.75 0 1 1 1.492-.15ZM6.5 1.75V3h3V1.75a.25.25 0 0 0-.25-.25h-2.5a.25.25 0 0 0-.25.25Z"></path></svg> Delete ruleset**.

## Using ruleset history

>

Ruleset history lists events triggered by changes that affect your rulesets within the last 180 days.

You can view all the changes to a ruleset and revert back to a specific iteration. You can also download a JSON file containing the ruleset's configuration at a specific iteration. The bypass list of a ruleset is excluded from the exported JSON file.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. In the left sidebar, in the "Policies" section, click **Code**, then click **Rulesets**.
3. To view the history of changes to the ruleset, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Open additional options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> to the right of the ruleset's name, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-history" aria-label="history" role="img"><path d="m.427 1.927 1.215 1.215a8.002 8.002 0 1 1-1.6 5.685.75.75 0 1 1 1.493-.154 6.5 6.5 0 1 0 1.18-4.458l1.358 1.358A.25.25 0 0 1 3.896 6H.25A.25.25 0 0 1 0 5.75V2.104a.25.25 0 0 1 .427-.177ZM7.75 4a.75.75 0 0 1 .75.75v2.992l2.028.812a.75.75 0 0 1-.557 1.392l-2.5-1A.751.751 0 0 1 7 8.25v-3.5A.75.75 0 0 1 7.75 4Z"></path></svg> History**.
4. To the right of the specific iteration, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Open additional options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **Compare changes**, **Restore**, or **Download**.

## Importing a ruleset

You can import a ruleset from another repository, organization or enterprise using the exported JSON file from the previous section. This can be useful if you want to apply the same ruleset to multiple repositories, organizations or enterprises.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. In the left sidebar, in the "Policies" section, click **Code**, then click **Rulesets**.
3. Select the **New ruleset** dropdown, then click **Import a ruleset**.
4. Open the exported JSON file.
5. Review the imported ruleset and click **Create**.

## Viewing insights for rulesets

You can view insights for rulesets to see how rulesets are affecting the repositories in your enterprise. On the "Rule Insights" page, you will see a timeline of the following user actions. You can use filters to find what you're looking for.

* Actions that have been checked against one or more rulesets and passed.
* Actions that have been checked against one or more rulesets and failed.
* Actions where someone has bypassed one or more rulesets.

If a ruleset is running in "Evaluate" mode, you can see actions that would have passed or failed if the ruleset had been active.

Additionally, these insights are available via the rule suites [REST API](/en/enterprise-cloud@latest/rest/repos/rule-suites).

![Screenshot of the "Rule Insights" page. Three actions are listed marked: "Pass," "Bypass," and "Fail". The failed action has with an "evaluate" label.](/assets/images/help/repository/rule-insights.png)

If a ruleset is running in "Evaluate" mode, you can see actions that would have passed or failed if the ruleset had been active.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. In the left sidebar, in the "Policies" section, click **Code**, then click **Rulesets**.
3. On the "Rule insights" page, use the dropdown menus at the top of the page to filter the actions by ruleset, repository, actor, and time period.
4. To see which specific rules failed or required a bypass, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="View rule runs" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then expand the name of the ruleset.

## Managing requests to bypass push rules

You can view and manage all requests for bypass privileges on the “Bypass Requests" page, located under the **Rules** settings of the repository.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)
3. Click **Bypass Requests**.

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