# Auditing users across your enterprise

The audit log dashboard shows site administrators the actions performed by all users and organizations across your enterprise within the last 180 days. The audit log includes details such as who performed the action, what the action was, and when the action was performed.

## Accessing the audit log

The audit log dashboard gives you a visual display of audit data across your enterprise.

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. Under "Settings", click **Audit log**.

Within the map, you can pan and zoom to see events around the world. Hover over a country to see a quick count of events from that country.

## Searching for events across your enterprise

The audit log lists the following information about actions made within your enterprise:

* [The repository](#search-based-on-the-repository) an action was performed in
* [The GitHub account](#search-based-on-the-actor) that performed the action
* [Which organization](#search-based-on-the-organization) an action pertained to
* [The action](#search-based-on-the-action-performed) that was performed
* [Which country](#search-based-on-the-location) the action took place in
* [The date and time](#search-based-on-the-time-of-action) the action occurred

> \[!NOTE]
>
> * While you can't use text to search for audit entries, you can construct search queries using a variety of filters. GitHub Enterprise Server supports many operators for searching across your instance. For more information, see [About searching on GitHub](/en/enterprise-server@3.20/search-github/getting-started-with-searching-on-github/about-searching-on-github).
> * Audit records are available for the last 180 days.

### Search based on the repository

The `repo` qualifier limits actions to a specific repository owned by your organization. For example:

* `repo:my-org/our-repo` finds all events that occurred for the `our-repo` repository in the `my-org` organization.
* `repo:my-org/our-repo repo:my-org/another-repo` finds all events that occurred for both the `our-repo` and `another-repo` repositories in the `my-org` organization.
* `-repo:my-org/not-this-repo` excludes all events that occurred for the `not-this-repo` repository in the `my-org` organization.

You must include your organization's name within the `repo` qualifier; searching for just `repo:our-repo` will not work.

### Search based on the actor

The `actor` qualifier scopes events based on the person or agent that performed the action. For example:

* `actor:octocat` finds all events performed by `octocat`.
* `actor:octocat actor:Copilot` finds all events performed by both `octocat` and `Copilot`.
* `-actor:Copilot` excludes all events performed by `Copilot`.

You can only use a GitHub username, not an individual's real name.

### Search based on the organization

The `org` qualifier limits actions to a specific organization. For example:

* `org:my-org` finds all events that occurred for the `my-org` organization.
* `org:my-org action:team` finds all team events performed within the `my-org` organization.
* `-org:my-org` excludes all events that occurred for the `my-org` organization.

### Search based on the action performed

The `action` qualifier searches for specific events, grouped within categories. For information on the events associated with these categories, see [Audit log events for your enterprise](/en/enterprise-server@3.20/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/audit-log-events-for-your-enterprise).

| Category name | Description                                                                     |
| ------------- | ------------------------------------------------------------------------------- |
| `hook`        | Contains all activities related to webhooks.                                    |
| `org`         | Contains all activities related organization membership                         |
| `repo`        | Contains all activities related to the repositories owned by your organization. |
| `team`        | Contains all activities related to teams in your organization.                  |

You can search for specific sets of actions using these terms. For example:

* `action:team` finds all events grouped within the team category.
* `-action:billing` excludes all events in the billing category.

Each category has a set of associated events that you can filter on. For example:

* `action:team.create` finds all events where a team was created.
* `-action:billing.change_email` excludes all events where the billing email was changed.

### Search based on the location

The `country` qualifier filters actions by the originating country.

* You can use a country's two-letter short code or its full name.
* Countries with spaces in their name must be wrapped in quotation marks. For example:
  * `country:de` finds all events that occurred in Germany.
  * `country:Mexico` finds all events that occurred in Mexico.
  * `country:"United States"` all finds events that occurred in the United States.

### Search based on the time of action

The `created` qualifier filters actions by the time they occurred.

* Define dates using the format of `YYYY-MM-DD`--that's year, followed by month, followed by day.
* Dates support [greater than, less than, and range qualifiers](/en/enterprise-server@3.20/search-github/getting-started-with-searching-on-github/understanding-the-search-syntax). For example:
  * `created:2014-07-08` finds all events that occurred on July 8th, 2014.
  * `created:>=2014-07-01` finds all events that occurred on or after July 8th, 2014.
  * `created:<=2014-07-01` finds all events that occurred on or before July 8th, 2014.
  * `created:2014-07-01..2014-07-31` finds all events that occurred in the month of July 2014.