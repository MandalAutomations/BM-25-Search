# Filtering alerts in security overview

Find the security alerts that matter most by filtering your security overview data.

Security overview can show alerts across many repositories in your organization or enterprise. Filtering helps you focus on specific alerts based on severity, alert type, repository characteristics, and other factors.

You can combine multiple filters to narrow your results. For example, you can show only critical Dependabot alerts in public repositories owned by a specific team.

For a complete list of available filters, see [Available filters for security overview](/en/code-security/reference/security-alert-management/available-filters-for-security-overview).

> \[!NOTE]
> The information shown by security overview varies according to your access to repositories and organizations, and according to whether Advanced Security features are used by those repositories and organizations. For more information, see [About security overview](/en/code-security/security-overview/about-security-overview#permission-to-view-data-in-security-overview).

## Filter methods

All security views have features to help you define filters. These provide an easy way to set up filters and understand the options available.

* **Interactive search text box.** When you click in the search box and press the keyboard "Space" key, a pop-up text box shows the filter options available in that view. You can use the mouse or keyboard arrow keys to select the options you want in the text box before pressing the keyboard "Return" key to add the filter. Supported for all views.
* **Dropdown selectors and toggles.** Shown at the end of the "Search text box" or in the header of the data table. As you choose the data to view, the filters shown in the search text box are updated accordingly. Supported on the alert views.
* **Advanced filters dialog.** When you click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-filter" aria-label="filter" role="img"><path d="M.75 3h14.5a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1 0-1.5ZM3 7.75A.75.75 0 0 1 3.75 7h8.5a.75.75 0 0 1 0 1.5h-8.5A.75.75 0 0 1 3 7.75Zm3 4a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 0 1.5h-2.5a.75.75 0 0 1-.75-.75Z"></path></svg> Filter** button, you can use dropdown lists to select the "Qualifier," "Operator," and "Values" for each filter. Supported on the "Overview" and "Insights" views.

## Accessing security overview for your organization

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. In the "Organizations" section, select the organization you want to look at.
3. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.

## Accessing security overview for your enterprise

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab. The "Overview" dashboard of security overview is displayed.

## Applying simple filters

1. In security overview, select the view of your choice on the left navigation panel. For instructions about how to access security overview, see [Accessing security overview for your organization](#accessing-security-overview-for-your-organization) or [Accessing security overview for your enterprise](#accessing-security-overview-for-your-enterprise).
2. Click in the box adjacent to the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-filter" aria-label="filter" role="img"><path d="M.75 3h14.5a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1 0-1.5ZM3 7.75A.75.75 0 0 1 3.75 7h8.5a.75.75 0 0 1 0 1.5h-8.5A.75.75 0 0 1 3 7.75Zm3 4a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 0 1.5h-2.5a.75.75 0 0 1-.75-.75Z"></path></svg> Filter** control. If there is text in the box, delete it. A popup shows available filters for the current view.
3. Select a filter and a value for the filter.
4. Press <kbd>Enter</kbd>.

## Using the advanced filters dialog

The advanced filters dialog is available in "Overview" and "Insights" views and helps you build filters.

1. In the desired view of security overview, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-filter" aria-label="filter" role="img"><path d="M.75 3h14.5a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1 0-1.5ZM3 7.75A.75.75 0 0 1 3.75 7h8.5a.75.75 0 0 1 0 1.5h-8.5A.75.75 0 0 1 3 7.75Zm3 4a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 0 1.5h-2.5a.75.75 0 0 1-.75-.75Z"></path></svg> Filter**.
2. In the "Advanced filters" dialog, use the dropdown lists to build your filter:
   * **Qualifier**: Select the filter type (for example, "Severity" or "Tool")
   * **Operator**: Select how to match values (for example, "is one of" and "is not one of")
   * **Value**: Select what to filter for (for example, "Critical" or "CodeQL")
3. Optionally, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus icon" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add a filter** to add a custom filter.
4. Click **Apply**.

## Combining filters

* **AND logic (default):** Multiple filters show results matching all filters.

  `severity:critical visibility:public`

* **OR logic:** Use commas between values for a single filter.

  `severity:critical,high`

* **NOT logic:** Use a minus sign to exclude results.

  `-repo:my-org/archived-repo`

## Common filter examples

* Show critical alerts in public repositories:

  `severity:critical visibility:public`

* Show repositories with more than N code scanning alerts:

  `code-scanning-alerts:>100`

* Show alerts for a specific team's repositories:

  `team:security-team`

* Show Dependabot alerts with available fixes:

  `has:patch`

* Show active secrets from a specific provider:

  `provider:amazon_aws validity:active`