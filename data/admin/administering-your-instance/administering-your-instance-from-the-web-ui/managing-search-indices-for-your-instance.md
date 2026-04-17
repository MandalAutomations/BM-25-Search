# Managing search indices for your instance

GitHub Enterprise Server uses Elasticsearch to power search features, and provides tools for managing search and index behavior.

## About search for GitHub Enterprise Server

Users can search your instance to find, navigate, and understand issues, pull requests, code, and other content on GitHub Enterprise Server. Elasticsearch powers the search functionality on your instance. You can view the current status of Elasticsearch, and you can control search and index behavior.

For more information about search for GitHub Enterprise Server, see [Search on GitHub documentation](/en/enterprise-server@3.20/search-github). For more information about Elasticsearch, see the [Elasticsearch website](https://elastic.co).

## About index management

GitHub Enterprise Server reconciles the state of the search index with data on the instance automatically and regularly, including:

* Issues, projects, pull requests, repositories, and users in the database
* Git repositories (source code) on disk

In normal use, enterprise owners do not need to create new indices or schedule repair jobs. For troubleshooting or other support purposes, GitHub Support may instruct you to run a repair job.

## Viewing search indices

1. In the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. In the left sidebar, click **Search indexes**.
3. Under "Index management", click the search index you want to view.

## Creating a new search index

1. In the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. In the left sidebar, click **Search indexes**.
3. Next to "Index management", click **Create new index**.
4. Select the **Select the index to create** dropdown, then click the search index you want to create.
5. If you want the index to be searchable, select the **Make this index searchable** checkbox.
6. If you want the index to be writable, select the **Make this index writable** checkbox.
7. Click **Create index**.
8. If your instance uses a high availability or cluster configuration, you will need to run a script to ensure the number of search indices is correctly configured across the instance. This step does not apply to those using the new HA configuration released in GitHub Enterprise Server 3.19.

   Access the administrative shell for your primary appliance via SSH, then run one of the following commands.

   For high availability configurations:

   ```shell copy
   /usr/local/share/enterprise/ghe-es-auto-expand -v 0-all
   ```

   For cluster configurations:

   ```shell copy
   /usr/local/share/enterprise/ghe-es-auto-expand -v 0-1
   ```

   See [Accessing the administrative shell (SSH)](/en/enterprise-server@3.20/admin/administering-your-instance/administering-your-instance-from-the-command-line/accessing-the-administrative-shell-ssh).

## Managing search indices

When you view an existing search index in the site admin dashboard, you can perform the following actions:

* Make the index searchable.
* Make the index writable.
* Update the index.
* Delete the index.
* Reset the index repair state.
* Start a new index repair job.
* Enable or disable index repair jobs.

## Managing code search

You can enable or disable both search and index operations for source code. For more information about code search, see [Searching code](/en/enterprise-server@3.20/search-github/searching-on-github/searching-code).

1. In the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. In the left sidebar, click **Search indexes**.
3. In the "Code search" section, next to "Searching" or "Indexing", click **Enable** or **Disable**.

## Repairing search indices

Your instance uses repair jobs to reconcile the data, and schedules a repair job in the background when the following events occur:

* A new search index is created.
* Missing data needs to be backfilled.
* Old search data needs to be updated.

In the "Repair" section of the search index, a progress bar shows the current status of a repair job across background workers. You can ignore the value shown in the progress bar after a repair job has completed. The progress bar shows the difference between the repair offset and the highest record ID in the database, and will decrease as more repositories are added to your GitHub Enterprise Server instance even though those repositories are actually indexed.

To minimize the effects on I/O performance and reduce the chances of operations timing out, run the repair job during off-peak hours. As the job reconciles the search index with database and Git repository data, one CPU will be used. Monitor your system's load averages and CPU usage with a utility like `top`. If you don't notice any significant increase in resource consumption, it should also be safe to run an index repair job during peak hours.

Repair jobs use a "repair offset" for parallelization. This is an offset into the database table for the record being reconciled. Multiple background jobs can synchronize work based on this offset.