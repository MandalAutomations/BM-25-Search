# Using Grafana to analyze OpenTelemetry metrics

Monitor the health and performance of your instance using dashboards and metrics provided by the OpenTelemetry metrics stack.

## Prerequisites

OpenTelemetry metrics must be enabled on the instance. For configuration instructions, see [Configuring OpenTelemetry for your instance](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/configuring-opentelemetry-for-your-instance).

## Navigating to the monitor dashboards

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
4. If you have created multiple Management Console user accounts, select **Root site admin** or **Management Console user**. For more information about Management Console user accounts see, [Managing access to the Management Console](/en/enterprise-server@3.20/admin/configuration/administering-your-instance-from-the-management-console/managing-access-to-the-management-console).
5. Type your Management Console credentials. Then click **Continue**.
6. Click the **Monitor** tab.

### Metric labels

The OpenTelemetry stack exporters automatically attach labels to metrics. Common labels are:

* `job` — the name of the exporter that produced the metric
* `instance` — the instance name from which the metric originated

For some exporters (like `node_exporter` or `haproxy_exporter`), open-source documentation may be available by searching for the `job` label value.

Label availability varies by exporter and metric. Some GitHub application-level metrics may provide fewer labels than infrastructure/exporter metrics, and labels are subject to change from version to version.

## Inspecting panel queries

> \[!IMPORTANT] Pre-built dashboards can be opened and edited for inspection, but changes cannot be saved. Create a copy of a dashboard to apply and retain any customizations.

To understand which metrics and queries power a given panel, use the graph panel menu *(3 vertical dots)* when viewing a Grafana dashboard:

* **Edit**: Opens the panel editor. This is the most direct way to review and adjust the queries that power the visualization.
* **Explore**: Opens Grafana Explore with the panel’s queries pre-populated, allowing interactive analysis.
* **Metrics Drilldown**: Opens a side panel for discovering related metrics and breaking down the metric by label values.

## Exploring metrics in Grafana

Grafana provides multiple ways to discover and analyze the metrics available on your instance.

### Grafana Drilldown

Grafana Drilldown provides a guided workflow to discover metrics by filtering on metric prefixes, labels, and label values. After selecting a metric, Grafana can break down the series by available label values. For example, `haproxy_backend_response_errors_total` can be grouped by proxy/back-end label values.

### Grafana Explore

Grafana Explore enables interactive analysis using PromQL (Prometheus Query Language), including a query builder that can help users discover available metrics and labels.

Tips for working in Grafana Explore:

* Use **Code mode's Metric browser** to discover metrics and labels. Selecting labels and label values can reveal associated metrics, and selecting a metric can reveal associated labels and label values.
* After selecting a metric, switch to **Builder mode** for suggestions to refine the query.
* Access additional operations via the **+ Operations** button.
* Customize legend labels in the **Options** panel using the **Legend** setting, for example `false`. By default, Grafana assigns legend labels based on unique label sets.

## Further reading

* [Advanced dashboards of OpenTelemetry metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/advanced-dashboards)
* [About the monitor dashboards](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/about-the-monitor-dashboards#creating-new-dashboards)
* [Get Started with Explore](https://grafana.com/docs/grafana/latest/visualizations/explore/get-started-with-explore/) in the Grafana documentation
* [Promql - Querying Basics](https://prometheus.io/docs/prometheus/latest/querying/basics/) in the Prometheus documentation