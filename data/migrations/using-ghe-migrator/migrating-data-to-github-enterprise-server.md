# Migrating data to GitHub Enterprise Server

After generating a migration archive, you can import the data to your target GitHub Enterprise Server instance. You'll be able to review changes for potential conflicts before permanently applying the changes to your target instance.

## Preparing the migrated data

1. Using the [`scp`](https://acloudguru.com/blog/engineering/ssh-and-scp-howto-tips-tricks#scp) command, copy the migration archive generated from your source instance or organization to your GitHub Enterprise Server target:

   ```shell
   scp -P 122 PATH-TO-MIGRATION-GUID.tar.gz admin@HOSTNAME:/home/admin/
   ```

2. SSH into your target GitHub Enterprise Server instance. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell
   ssh -p 122 admin@HOSTNAME
   ```

3. Ensure the migration archive has sufficient read permissions.

   ```shell
   chmod 644 /home/admin/MIGRATION-GUID.tar.gz
   ```

4. Use the `ghe-migrator prepare` command to prepare the archive for import on the target instance and generate a new Migration GUID for you to use in subsequent steps:

   ```shell
   ghe-migrator prepare /home/admin/MIGRATION-GUID.tar.gz
   ```

   * To start a new import attempt, run `ghe-migrator prepare` again and get a new Migration GUID.
   * To specify where migration files should be staged append the command with `--staging-path=/full/staging/path`. Defaults to `/data/user/tmp`.

## Generating a list of migration conflicts

1. Using the `ghe-migrator conflicts` command with the Migration GUID, generate a *conflicts.csv* file:

   ```shell
   ghe-migrator conflicts -g MIGRATION-GUID > conflicts.csv
   ```

   * If no conflicts are reported, you can safely import the data.

2. If there are conflicts, using the [`scp`](https://acloudguru.com/blog/engineering/ssh-and-scp-howto-tips-tricks#scp) command, copy *conflicts.csv* to your local computer:

   ```shell
   scp -P 122 admin@HOSTNAME:conflicts.csv ~/Desktop
   ```

3. Continue to [Resolving migration conflicts or setting up custom mappings](#resolving-migration-conflicts-or-setting-up-custom-mappings).

## Reviewing migration conflicts

1. Using a text editor or [CSV-compatible spreadsheet software](https://en.wikipedia.org/wiki/Comma-separated_values#Application_support), open *conflicts.csv*.
2. With guidance from the examples and reference tables below, review the *conflicts.csv* file to ensure that the proper actions will be taken upon import.

The *conflicts.csv* file contains a *migration map* of conflicts and recommended actions. A migration map lists out both what data is being migrated from the source, and how the data will be applied to the target.

| `model_name`   | `source_url`                                           | `target_url`                                           | `recommended_action` |
| -------------- | ------------------------------------------------------ | ------------------------------------------------------ | -------------------- |
| `user`         | `https://example-gh.source/octocat`                    | `https://example-gh.target/octocat`                    | `map`                |
| `organization` | `https://example-gh.source/octo-org`                   | `https://example-gh.target/octo-org`                   | `map`                |
| `repository`   | `https://example-gh.source/octo-org/widgets`           | `https://example-gh.target/octo-org/widgets`           | `rename`             |
| `team`         | `https://example-gh.source/orgs/octo-org/teams/admins` | `https://example-gh.target/orgs/octo-org/teams/admins` | `merge`              |
|                |                                                        |                                                        |                      |

Each row in *conflicts.csv* provides the following information:

| Name                 | Description                                                            |
| -------------------- | ---------------------------------------------------------------------- |
| `model_name`         | The type of data being changed.                                        |
| `source_url`         | The source URL of the data.                                            |
| `target_url`         | The expected target URL of the data.                                   |
| `recommended_action` | The preferred action `ghe-migrator` will take when importing the data. |

### Possible mappings for each record type

There are several different mapping actions that `ghe-migrator` can take when transferring data:

| `action`        | Description                                                                                                                                                                                                                                    | Applicable models                  |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| `import`        | (default) Data from the source is imported to the target.                                                                                                                                                                                      | All record types                   |
|                 |                                                                                                                                                                                                                                                |                                    |
| `map`           | Instead of creating a new model based on the source data, an existing record in the target is used. Useful for importing a repository into an existing organization or mapping user identities in the target to user identities in the source. | Users, organizations               |
|                 |                                                                                                                                                                                                                                                |                                    |
|                 |                                                                                                                                                                                                                                                |                                    |
| `rename`        | Data from the source is renamed, then copied over to the target.                                                                                                                                                                               | Users, organizations, repositories |
|                 |                                                                                                                                                                                                                                                |                                    |
| `map_or_rename` | If the target exists, map to that target. Otherwise, rename the imported model.                                                                                                                                                                | Users                              |
|                 |                                                                                                                                                                                                                                                |                                    |
| `merge`         | Data from the source is combined with existing data on the target.                                                                                                                                                                             | Teams                              |
|                 |                                                                                                                                                                                                                                                |                                    |

**We strongly suggest you review the *conflicts.csv* file and use `ghe-migrator audit` to ensure that the proper actions are being taken.** If everything looks good, you can continue.

## Resolving migration conflicts or setting up custom mappings

If you believe that `ghe-migrator` will perform an incorrect change, you can make corrections by changing the data in *conflicts.csv*. You can make changes to any of the rows in *conflicts.csv*.

For example, let's say you notice that the `octocat` user from the source is being mapped to `octocat` on the target.

| `model_name` | `source_url`                        | `target_url`                        | `recommended_action` |
| ------------ | ----------------------------------- | ----------------------------------- | -------------------- |
| `user`       | `https://example-gh.source/octocat` | `https://example-gh.target/octocat` | `map`                |

You can choose to map the user to a different user on the target. Suppose you know that `octocat` should actually be `monalisa` on the target. You can change the `target_url` column in *conflicts.csv* to refer to `monalisa`.

| `model_name` | `source_url`                        | `target_url`                         | `recommended_action` |
| ------------ | ----------------------------------- | ------------------------------------ | -------------------- |
| `user`       | `https://example-gh.source/octocat` | `https://example-gh.target/monalisa` | `map`                |

As another example, if you want to rename the `octo-org/widgets` repository to `octo-org/amazing-widgets` on the target instance, change the `target_url` to `octo-org/amazing-widgets` and the `recommend_action` to `rename`.

| `model_name` | `source_url`                                 | `target_url`                                         | `recommended_action` |
| ------------ | -------------------------------------------- | ---------------------------------------------------- | -------------------- |
| `repository` | `https://example-gh.source/octo-org/widgets` | `https://example-gh.target/octo-org/amazing-widgets` | `rename`             |

### Adding custom mappings

A common scenario during a migration is for migrated users to have different usernames on the target than they have on the source.

Given a list of usernames from the source and a list of usernames on the target, you can build a CSV file with custom mappings and then apply it to ensure each user's username and content is correctly attributed to them at the end of a migration.

You can quickly generate a CSV of users being migrated in the CSV format needed to apply custom mappings by using the `ghe-migrator audit` command:

```shell
ghe-migrator audit -m user -g MIGRATION-GUID > users.csv
```

Now, you can edit that CSV and enter the new URL for each user you would like to map or rename, and then update the fourth column to have `map` or `rename` as appropriate.

For example, to rename the user `octocat` to `monalisa` on the target `https://example-gh.target` you would create a row with the following content:

| `model_name` | `source_url`                        | `target_url`                         | `state`  |
| ------------ | ----------------------------------- | ------------------------------------ | -------- |
| `user`       | `https://example-gh.source/octocat` | `https://example-gh.target/monalisa` | `rename` |

The same process can be used to create mappings for each record that supports custom mappings. For more information, see [our table on the possible mappings for records](#possible-mappings-for-each-record-type).

### Applying modified migration data

1. After making changes, use the [`scp`](https://acloudguru.com/blog/engineering/ssh-and-scp-howto-tips-tricks#scp) command to apply your modified *conflicts.csv* (or any other mapping *.csv* file in the correct format) to the target instance:

   ```shell
   scp -P 122 ~/Desktop/conflicts.csv admin@HOSTNAME:/home/admin/
   ```

2. Re-map the migration data using the `ghe-migrator map` command, passing in the path to your modified *.csv* file and the Migration GUID:

   ```shell
   ghe-migrator map -i conflicts.csv -g MIGRATION-GUID
   ```

3. If the `ghe-migrator map -i conflicts.csv -g MIGRATION-GUID` command reports that conflicts still exist, run through the migration conflict resolution process again.

## Applying the imported data on GitHub Enterprise Server

1. SSH into your target GitHub Enterprise Server instance. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell
   ssh -p 122 admin@HOSTNAME
   ```

2. Using the `ghe-migrator import` command, start the import process. You'll need:

   * Your Migration GUID. For more information, see [Preparing the migrated data for import to GitHub Enterprise Server](#preparing-the-migrated-data).
   * Your personal access token for authentication. The personal access token that you use is only for authentication as a site administrator, and does not require any specific scope or permissions. For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

   ```shell
   $ ghe-migrator import /home/admin/MIGRATION-GUID.tar.gz -g MIGRATION-GUID -u USERNAME -p TOKEN

   > Starting GitHub::Migrator
   > Import 100% complete /
   ```

   * To specify where migration files should be staged append the command with `--staging-path=/full/staging/path`. Defaults to `/data/user/tmp`.

## Reviewing migration data

By default, `ghe-migrator audit` returns every record. It also allows you to filter records by:

* The types of records.
* The state of the records.

The record types match those found in the [migrated data](/en/migrations/using-ghe-migrator/about-ghe-migrator#migrated-data).

## Record type filters

| Record type                              | Filter name                   |
| ---------------------------------------- | ----------------------------- |
| Users                                    | `user`                        |
| Organizations                            | `organization`                |
| Repositories                             | `repository`                  |
| Teams                                    | `team`                        |
| Milestones                               | `milestone`                   |
|                                          |                               |
| Issues                                   | `issue`                       |
| Issue comments                           | `issue_comment`               |
| Pull requests                            | `pull_request`                |
| Pull request reviews                     | `pull_request_review`         |
| Commit comments                          | `commit_comment`              |
| Pull request review comments             | `pull_request_review_comment` |
| Releases                                 | `release`                     |
| Actions taken on pull requests or issues | `issue_event`                 |
| Protected branches                       | `protected_branch`            |

## Record state filters

| Record state    | Description                           |
| --------------- | ------------------------------------- |
| `export`        | The record will be exported.          |
| `import`        | The record will be imported.          |
| `map`           | The record will be mapped.            |
| `rename`        | The record will be renamed.           |
| `merge`         | The record will be merged.            |
| `exported`      | The record was successfully exported. |
| `imported`      | The record was successfully imported. |
| `mapped`        | The record was successfully mapped.   |
| `renamed`       | The record was successfully renamed.  |
| `merged`        | The record was successfully merged.   |
| `failed_export` | The record failed to export.          |
| `failed_import` | The record failed to be imported.     |
| `failed_map`    | The record failed to be mapped.       |
| `failed_rename` | The record failed to be renamed.      |
| `failed_merge`  | The record failed to be merged.       |

## Filtering audited records

With the `ghe-migrator audit` command, you can filter based on the record type using the `-m` flag. Similarly, you can filter on the import state using the `-s` flag. The command looks like this:

```shell
ghe-migrator audit -m RECORD_TYPE -s STATE -g MIGRATION-GUID
```

For example, to view every successfully imported organization and team, you would enter:

```shell
$ ghe-migrator audit -m organization,team -s mapped,renamed -g MIGRATION-GUID
> model_name,source_url,target_url,state
> organization,https://gh.source/octo-org/,https://ghe.target/octo-org/,renamed
```

**We strongly recommend auditing every import that failed.** To do that, you will enter:

```shell
$ ghe-migrator audit -s failed_import,failed_map,failed_rename,failed_merge -g MIGRATION-GUID
> model_name,source_url,target_url,state
> user,https://gh.source/octocat,https://gh.target/octocat,failed
> repository,https://gh.source/octo-org/octo-project,https://ghe.target/octo-org/octo-project,failed
```

If you have any concerns about failed imports, you can contact us by visiting [GitHub Enterprise Support](https://support.github.com).

## Completing the import on GitHub Enterprise Server

After your migration is applied to your target instance and you have reviewed the migration, you''ll unlock the repositories and delete them off the source. Before deleting your source data we recommend waiting around two weeks to ensure that everything is functioning as expected.

## Unlocking repositories on the target instance

1. SSH into GitHub.com. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```
2. Unlock all the imported repositories with the `ghe-migrator unlock` command. You'll need your Migration GUID:

```shell
$ ghe-migrator unlock -g MIGRATION-GUID
> Unlocked octo-org/octo-project
```

> \[!WARNING]
> If your repository contains GitHub Actions workflows using the `schedule` trigger, the workflows will not run automatically after an import. To start the scheduled workflows once again, push a commit to the repository. For more information, see [Events that trigger workflows](/en/actions/using-workflows/events-that-trigger-workflows#schedule).

## Unlocking repositories on the source

After your migration is complete, you should unlock the repositories on the source.

### Unlocking repositories from an organization on GitHub.com

To unlock the repositories on a GitHub.com organization, you'll send a `DELETE` request to [the migration unlock endpoint](/en/rest/migrations#unlock-an-organization-repository). You'll need:

* Your access token for authentication
* The unique `id` of the migration
* The name of the repository to unlock

```shell
curl -H "Authorization: Bearer GITHUB_ACCESS_TOKEN" -X DELETE \
  -H "Accept: application/vnd.github.wyandotte-preview+json" \
  https://api.github.com/orgs/ORG-NAME/migrations/ID/repos/REPO_NAME/lock
```

### Deleting repositories from an organization on GitHub.com

After unlocking the GitHub.com organization's repositories, you should delete every repository you previously migrated using [the repository delete endpoint](/en/rest/repos/repos#delete-a-repository). You'll need your access token for authentication:

```shell
curl -H "Authorization: Bearer GITHUB_ACCESS_TOKEN" -X DELETE \
  https://api.github.com/repos/ORG-NAME/REPO_NAME
```

### Unlocking repositories from a GitHub Enterprise Server instance

1. SSH into GitHub.com. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```
2. Unlock all the imported repositories with the `ghe-migrator unlock` command. You'll need your Migration GUID:

```shell
$ ghe-migrator unlock -g MIGRATION-GUID
> Unlocked octo-org/octo-project
```