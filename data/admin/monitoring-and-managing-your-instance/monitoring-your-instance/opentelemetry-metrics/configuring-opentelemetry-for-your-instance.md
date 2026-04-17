# Configuring OpenTelemetry for your instance

Learn how to configure OpenTelemetry metrics collection on your GitHub Enterprise Server instance for enhanced monitoring and observability.

OpenTelemetry metrics are the future foundation for monitoring, available from GitHub Enterprise Server 3.18 onward. This new monitoring stack provides enhanced observability and management capabilities compared to the legacy collectd system.

Collectd metrics continue to be gathered by default and remain fully supported in this release.

## Prerequisites

* GitHub Enterprise Server 3.18 or later
* Administrative access to the Management Console
* SSH access to your GitHub Enterprise Server appliance

## Enabling OpenTelemetry metrics

OpenTelemetry metrics are enabled by default for **new installations** of GitHub Enterprise Server 3.19 and later. Upgrades to GitHub Enterprise Server 3.19 will still have `collectd` metrics enabled by default, but you can choose to switch to OpenTelemetry metrics.

## Performance considerations

When configuring OpenTelemetry metrics, consider the following performance factors:

* **Collection frequency**: More frequent collection increases system load
* **Data retention**: Longer retention periods require more storage
* **Custom exporters**: Additional exporters may increase CPU and memory usage
* **Network bandwidth**: External metric shipping affects network usage

## Configuring metrics collection

After enabling OpenTelemetry metrics, you can customize various aspects of the metrics collection process.

### Setting collection intervals

The default metrics collection interval is 30 seconds. You can adjust this based on your monitoring needs.

> \[!IMPORTANT]
> Setting shorter intervals increases the precision of metrics but also increases storage requirements and system load. Consider your system resources and monitoring requirements before adjusting this setting.

#### Using the Management Console to set intervals

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the monitoring settings, under **Metrics scrape interval**, enter the desired interval in seconds (for example, `60`).

5. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

6. Wait for the configuration run to complete.

#### Using the command line to set intervals

SSH into your GitHub Enterprise Server appliance and run the following commands:

```shell
# Set scrape interval to 60 seconds
ghe-config observability.metrics.interval 60
ghe-config-apply
```

### Configuring data retention

By default, metrics data is retained for 30 days. You can modify this setting using either the Management Console or command line.

#### Using the Management Console to configure retention

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the monitoring settings, under **Metrics retention**, enter the desired retention period in days (for example, `15`).

5. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

6. Wait for the configuration run to complete.

#### Using the command line to configure retention

SSH into your GitHub Enterprise Server appliance and run the following commands:

```shell
# Set retention to 15 days
ghe-config observability.metrics.retention 15
ghe-config-apply
```

### Configuring the verbosity level for internal telemetry

The OpenTelemetry collector generates its own internal telemetry data for monitoring the health and performance of the collector itself. You can configure the verbosity of this internal telemetry using the command line.

The available telemetry levels are:

* `none`: Disables internal telemetry
* `basic`: Provides essential telemetry data (default)
* `normal`: Provides standard telemetry data
* `detailed`: Provides verbose telemetry data for debugging

SSH into your GitHub Enterprise Server appliance and run the following commands:

```shell
# Set internal telemetry level to normal
ghe-config observability.metrics.internal-otel-telemetry-level normal
ghe-config-apply
```

> \[!NOTE]
> Higher telemetry levels provide more detailed information about the collector's internal operations but also increase resource usage. The `basic` level is recommended for production environments unless you need to troubleshoot collector issues.

## Troubleshooting configuration issues

If you encounter problems with OpenTelemetry configuration, the following information can help you identify and resolve common issues.

### Common configuration problems

* **Service startup failures**: Check system logs for error messages
* **Resource constraints**: Monitor system resources when adjusting collection intervals

### Viewing local logs

SSH into the node you want to debug and run the following commands:

View OpenTelemetry collector logs:

```shell
sudo journalctl -u otelcol-contrib -f
```

View VictoriaMetrics logs:

```shell
sudo journalctl -u victoriametrics -f
```

## Next steps

* To enable advanced monitoring dashboards, see [Advanced dashboards of OpenTelemetry metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/advanced-dashboards)
* Exploring OpenTelemetry metrics, see [Using Grafana to analyze OpenTelemetry metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/using-grafana-to-analyze-opentelemetry-metrics).
* To set up external monitoring, see [Setting up external monitoring with OpenTelemetry](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/setting-up-external-monitoring-with-opentelemetry).