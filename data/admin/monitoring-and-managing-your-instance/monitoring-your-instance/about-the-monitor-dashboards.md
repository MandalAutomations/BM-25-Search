# About the monitor dashboards

View historical data for details like CPU and storage usage, application and authentication response times, and general system health.

## Accessing the monitor dashboards

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the top navigation bar, click **Monitor**.

   ![Screenshot of the header of the Management Console. A tab, labeled "Monitor", is highlighted with an orange outline.](/assets/images/enterprise/management-console/monitor-dash-link.png)

5. In HA and cluster environments you can switch between nodes using the dropdown and clicking on a different hostname.

## Using the monitor dashboards

The dashboards visualize metrics which can be useful for troubleshooting performance issues and better understanding how your GitHub Enterprise Server appliance is being used. The data behind the graphs is gathered by the monitoring services and sampled regularly.

Within the pre-built dashboards you can find various sections grouping graphs of different types of system resources. Use the links on the page to navigate between the dashboards.

![Screenshot of the Management Console header. The dashboard navigation links provided at the top right are highlighted in orange.](/assets/images/enterprise/management-console/monitor-dash-navigation.png)

If you have enabled metrics for OpenTelemetry, then additional dashboards are available, see: [Advanced dashboards of OpenTelemetry metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/advanced-dashboards).

### "Operational Health" dashboard

This is the default dashboard displayed on the "Monitor" page. It visualizes key metrics that help you to get a quick overview of the health of your GitHub Enterprise Server appliance.

### "System & Application Insights" dashboard

On this more detailed dashboard you can get further insights into all aspects of the services that are running on your appliance.

## Creating new dashboards

Starting with GitHub Enterprise Server 3.18, you can create custom Grafana dashboards and alerts directly inside the Management Console. These custom dashboards and alerts will persist over upgrades, making it easier to maintain your monitoring configuration.

> \[!IMPORTANT] Pre-built dashboards can be opened and edited for inspection, but changes cannot be saved. Create a copy of a dashboard to apply and retain any customizations.

You can use OpenTelemetry and collectd metrics concurrently for external monitoring. During the public preview, collectd remains enabled and cannot be disabled.

For more information about OpenTelemetry metrics, see [About OpenTelemetry metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/about-opentelemetry-metrics).

For more information about collectd metrics, see [About Collectd metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/collectd-metrics/about-collectd-metrics).

## About the metrics on the monitor dashboards

The monitor dashboards provide a comprehensive view of various metrics that help in understanding the performance and health of your GitHub Enterprise Server instance. These metrics are categorized into different sections to make it easier to analyze specific aspects of the system.

### System Health

The system health graphs provide a general overview of services and system resource utilization. The CPU, memory, and load average graphs are useful for identifying trends or times where provisioned resource saturation has occurred. For more information, see [Recommended alert thresholds](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/recommended-alert-thresholds).

### Application Health

These graphs include key metrics for the resource utilization of services that power  GitHub Enterprise Server. They help visualize ongoing issues while processing requests.

* **Nomad jobs:** The CPU and memory usage of individual services. GitHub Enterprise Server utilizes Nomad internally as the workload orchestrator.
* **Response code:** The number of responses by status code returned across GitHub Enterprise Server services.
* **Response time:** The speed of web requests at the 90th percentile in milliseconds.
* **Active workers:** The number of web workers busy per GitHub Enterprise Server application.
* **Queued requests:** The number of web requests queued per GitHub Enterprise Server application. It is expected for this panel to display 'No data' when no requests are queued up.
* **ElasticSearch Cluster Health:** The health status of the ElasticSearch cluster, based on the state of its primary and replica shards. This cluster powers GitHub Enterprise Server search.

### Processes

The processes graph section looks deeper into the major individual services which make up the GitHub Enterprise Server appliance. Looking at these services individually can show how usage trends impact system resources over time.

### Authentication

The authentication graphs break down the rates at which users and applications are authenticating to the GitHub Enterprise Server appliance. We also track the protocol or service type such as Git or API for the authentications, which is useful in identifying broad user activity trends. The authentication graphs can help you find interesting trends or timeframes to look at when diving deeper into authentication and API request logs.

### LDAP

LDAP graphs will only display data if LDAP authentication is enabled on the GitHub Enterprise Server appliance. For more information, see [Using LDAP](/en/enterprise-server@3.20/admin/managing-iam/using-ldap-for-enterprise-iam/using-ldap). These graphs can help you to identify slow responses from your LDAP server, as well as the overall volume of LDAP password based authentications.

### App servers

The application servers section provides insight into the activity of GitHub Enterprise Server services which provide data to users and integrations.

### App request/response

The **App request/response** section looks at the rate of requests, how quickly those requests are responded to, and with what status they returned.

### Actions

The graphs break down different metrics about GitHub Actions on your GitHub Enterprise Server instance including an overview of GitHub Actions services web requests  and MSSQL database transaction log size.

### Background jobs

Number of tasks queued for background processing on the GitHub Enterprise Server appliance.

### Git Maintenance

Monitoring Git maintenance failures can help customers with large and active repositories proactively manage repository health. Occasional "spurious failures" and "retries" are expected, but if a repository consistently shows Git maintenance marked as "failed", we recommend contacting [GitHub Support](https://support.github.com/).

### Network

The network interface graphs can be useful in profiling user activity, and throughput of traffic in and out of the GitHub Enterprise Server appliance.

### Storage

GitHub Enterprise Server repository performance is very dependent on the underlying storage system. Low latency, local SSD disks provide the highest performance. For more information on the GitHub Enterprise storage architecture, see [System overview](/en/enterprise-server@3.14/admin/overview/system-overview).

### Appliance-specific system services

System services graphs contain data related to the major databases on GitHub Enterprise Server. These are MySQL, and Elasticseach persistent databases, as well as Redis and Memcached which contain ephemeral data.

* Memcached: Provides a layer of in-memory caching for web and API operations. Memcached helps to provide quicker response times for users and integrations interacting with the system.
* MySQL: The primary database in GitHub Enterprise Server. User, issue, and other non-git or search related metadata is stored within MySQL.
* Nomad Jobs: GitHub Enterprise Server utilizes Nomad internally as the workload orchestrator, where the CPU and memory usage of individual services can be seen.
* Redis: The database mainly contains background job queue, as well as session state information.
* Kafka-Lite: Kafka broker service for job processing.
* Elasticsearch: Powers the built-in search features in GitHub Enterprise Server.
* Custom hooks: Graphs related to pre-receive hook execution.
* Git fetch caching: GitHub Enterprise Server will attempt to cache intensive operations, such as Git pack-objects, when multiple identical requests arrive in quick succession.
* MinIO: Storage used by some GitHub Enterprise Server services.
* Packages: Requests powering GitHub Packages.
* SecretScanning: Services powering Secret scanning features.
* CodeScanning: Services powering Code scanning features.
* Cluster: Graphs related to GitHub Enterprise Server high availability or clustering.
* Babeld: Git proxy.
* Alive: Service powering live updates.
* Ghes-manage: Service powering GHES Manage API.