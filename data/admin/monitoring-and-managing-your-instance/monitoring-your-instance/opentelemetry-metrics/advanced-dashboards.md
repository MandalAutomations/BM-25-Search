# Advanced dashboards of OpenTelemetry metrics

After enabling OpenTelemetry metrics collection on your GitHub Enterprise Server instance, you have access to additional dashboards with enhanced visualization and monitoring capabilities.

OpenTelemetry metrics are the future foundation for monitoring, available from GitHub Enterprise Server 3.18 onward. This new monitoring stack provides enhanced observability and management capabilities compared to the legacy collectd system.

Collectd metrics continue to be gathered by default and remain fully supported in this release.



## Prerequisites

* OpenTelemetry metrics are enabled for your GitHub Enterprise Server instance

## Additional dashboards

When OpenTelemetry metrics are enabled, you will have access to advanced Grafana dashboards with enhanced visualization and monitoring capabilities.

* **Elasticsearch** - Detailed metrics for search performance, indexing operations, and cluster health
* **Nomad** - In-depth monitoring of job scheduling, resource allocation, and service orchestration
* **HAProxy** - Load balancer performance metrics, connection statistics, and request routing information
* **Node Exporter** - System-level metrics including CPU, memory, disk, and network statistics for each node
* **Process Exporter** - Detailed process-level metrics for monitoring individual service performance

These dashboards provide more granular insights into your GitHub Enterprise Server instance's performance and can help with advanced troubleshooting and capacity planning.