# About monitoring your instance

You can configure monitoring and alerting so that you're aware of potential issues before they negatively impact application performance or availability.

## Metrics

OpenTelemetry metrics were introduced in GitHub Enterprise Server 3.18 and are the future foundation for monitoring your GitHub Enterprise Server instance.
Collectd metrics will continue to be gathered by default, but we expect collectd metrics to be discontinued in a future release.

For more information about OpenTelemetry metrics, see [About OpenTelemetry metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/about-opentelemetry-metrics).

For more information about Collectd metrics, see [About Collectd metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/collectd-metrics/about-collectd-metrics).

## Dashboards

The Management Console provides built-in dashboards that visualize metrics to help you troubleshoot performance issues and better understand how your GitHub Enterprise Server appliance is being used. The data behind the graphs is gathered by the monitoring services and sampled regularly.

For more information about the monitor dashboards, see [About the monitor dashboards](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/about-the-monitor-dashboards).

## System Logs

GitHub Enterprise Server maintains system logs that can be used to monitor system events and troubleshoot issues. These logs provide detailed information about various system processes and can be valuable for debugging and monitoring purposes.

For more information about system logs, see [About system logs](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/about-system-logs).

## Troubleshooting resource allocation problems

Resource allocation problems can impact the performance and availability of your GitHub Enterprise Server instance. Understanding how to identify and resolve these issues is crucial for maintaining optimal system performance.

For more information about troubleshooting resource allocation problems, see [Troubleshooting resource allocation problems](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/troubleshooting-resource-allocation-problems).

## Generating a Health Check for your enterprise

A health check provides a comprehensive overview of your GitHub Enterprise Server instance's current state and can help identify potential issues before they become critical.

For more information about generating a health check, see [Generating a Health Check for your enterprise](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/generating-a-health-check-for-your-enterprise).