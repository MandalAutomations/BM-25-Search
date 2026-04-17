# Accessing reports for your instance

You can download reports with information about the users, organizations, and repositories on GitHub.com.

## About reports for GitHub Enterprise Server

If you need to get information about the users, organizations, and repositories on your GitHub Enterprise Server instance, you can fetch data using the REST API. For more information, see [About the REST API](/en/enterprise-server@3.20/rest/about-the-rest-api/about-the-rest-api).

The REST API might not provide all of the data that you want, and requires some technical expertise to use. Alternatively, you can reports containing overviews of users, organizations, and repositories on your instance.

## Downloading reports using the web UI

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. In the left sidebar, click **Reports**.
3. Next to the report you want to download, click **Download**.

You can download CSV files that report the following information:

* All users
* All active users
* All [dormant users](/en/enterprise-server@3.20/admin/user-management/managing-users-in-your-enterprise/managing-dormant-users)
* All users who have been suspended
* All organizations
* All repositories

## Downloading reports programmatically

You can also access reports programmatically via standard HTTP authentication and a personal access token (classic). You must use a personal access token (classic) with the `site_admin` scope. For more information, see [Managing your personal access tokens](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

For example, you can download the "all users" report using curl:

```shell
curl --remote-name \
     --location \
     --user 'USERNAME:TOKEN' \
     http(s)://HOSTNAME/stafftools/reports/all_users.csv
```

To access the other reports programmatically, replace `all_users` with `active_users`, `dormant_users`, `suspended_users`, `all_organizations`, or `all_repositories`.

> \[!NOTE]
> The initial curl request will return an HTTP `202` response if there are no cached reports available. Your instance will generate a report in the background. You can send a second request to download the report. You can use a password or an OAuth token with the `site_admin` scope in place of a password.

## User reports

|               Key | Description                                                  |
| ----------------: | ------------------------------------------------------------ |
|      `created_at` | When the user account was created (as an ISO 8601 timestamp) |
|              `id` | Account ID for the user or organization                      |
|           `login` | Account's login name                                         |
|           `email` | Account's primary email address                              |
|            `role` | Whether the account is an admin or an ordinary user          |
|      `suspended?` | Whether the account has been suspended                       |
|  `last_logged_ip` | Most recent IP address to log into the account               |
|           `repos` | Number of repositories owned by the account                  |
|        `ssh_keys` | Number of SSH keys registered to the account                 |
| `org_memberships` | Number of organizations to which the account belongs         |
|        `dormant?` | Whether the account is dormant                               |
|     `last_active` | When the account was last active (as an ISO 8601 timestamp)  |
|       `raw_login` | Raw login information (in JSON format)                       |
|    `2fa_enabled?` | Whether the user has enabled two-factor authentication       |

## Organization reports

|             Key | Description                                                 |
| --------------: | ----------------------------------------------------------- |
|            `id` | Organization ID                                             |
|    `created_at` | When the organization was created                           |
|         `login` | Organization's login name                                   |
|         `email` | Organization's primary email address                        |
|        `owners` | Number of organization owners                               |
|       `members` | Number of organization members                              |
|         `teams` | Number of organization teams                                |
|         `repos` | Number of organization repositories                         |
| `2fa_required?` | Whether the organization requires two-factor authentication |

## Repository reports

|             Key | Description                                                  |
| --------------: | ------------------------------------------------------------ |
|    `created_at` | When the repository was created                              |
|      `owner_id` | ID of the repository's owner                                 |
|    `owner_type` | Whether the repository is owned by a user or an organization |
|    `owner_name` | Name of the repository's owner                               |
|            `id` | Repository ID                                                |
|          `name` | Repository name                                              |
|    `visibility` | Whether the repository is public or private                  |
| `readable_size` | Repository's size in a human-readable format                 |
|      `raw_size` | Repository's size as a number                                |
| `collaborators` | Number of repository collaborators                           |
|         `fork?` | Whether the repository is a fork                             |
|      `deleted?` | Whether the repository has been deleted                      |