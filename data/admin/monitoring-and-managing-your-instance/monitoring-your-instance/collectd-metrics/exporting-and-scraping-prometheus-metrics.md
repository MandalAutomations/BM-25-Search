# Exporting and scraping Prometheus metrics

GitHub Enterprise Server provides Prometheus-compatible metrics by transforming collectd data. These metrics can be scraped from a dedicated endpoint, allowing integration with observability and monitoring tools for performance insights.

Collectd metrics are gathered by default and are fully supported in this release. OpenTelemetry metrics are the future foundation for monitoring, available from GitHub Enterprise Server 3.18 onward.

> \[!NOTE]
> Collectd metrics are expected to be closing down and then retired in a future release of GitHub Enterprise Server. We recommend that your long-term monitoring strategy includes a migration to OpenTelemetry metrics. See [About OpenTelemetry metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/about-opentelemetry-metrics).

GitHub Enterprise Server includes a Prometheus metrics exporter to simplify observability and monitoring. This feature allows metrics to be scraped directly from the appliance, eliminating the need to forward `collectd` metrics to an external `collectd` server for transformation before sending them to a Prometheus system. By supporting Prometheus-compatible metrics natively, the exporter enables seamless integration with external monitoring dashboards and alerting systems.

## Enabling Prometheus metrics exporter and scraping metrics

By default, the Prometheus metrics exporter and scraping are disabled. Enabling the exporter for `collectd` metrics opens the metrics endpoint (also knows as `scrape endpoint`) at `http(s)://HOSTNAME:9103`. Ensure that firewall rules allow traffic on port 9103.

You can enable the Prometheus metrics exporter using the Management Console, the command line interface within the appliance, or the API.

### Enabling using the Management Console

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the monitoring settings, select **Enable prometheus**.

5. In the **Trusted IPv4/IPv6 addresses or CIDR blocks in a comma-separated list** field, type the comma-separated list of ip addresses or CIDR blocks. An example: `10.0.0.1, 192.168.1.0/8`. If this field is left empty, then scraping requests from any source IP will be accepted.

6. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

7. Wait for the configuration run to complete.

### Enabling via the command line interface

To enable the Prometheus metrics exporter, SSH into the GitHub Enterprise Server appliance and run the following commands:

```shell
ghe-config app.prometheus.enabled true
# Specify a comma-separated list of 
# trusted IPv4/IPv6 addresses or CIDR blocks.
ghe-config app.prometheus.trusted-ips \
  "10.0.0.1, 192.168.1.0/8"
ghe-config-apply
```

### Enabling using the API

You can enable the Prometheus metrics exporter using the API by sending a `PUT` request to update the configuration settings.

```shell
curl -L -H "Content-Type: application/json" \
  -X PUT -u "api_key:xxxxxxx" \
  https://<hostname>/manage/v1/config/settings \
  -d '{"prometheus": {"enabled": true, "trusted_ips": "10.0.0.1, 192.168.1.0/8"}}'
```

## Verifying the Prometheus metrics exporter is enabled

To verify that the Prometheus metrics exporter is enabled, use `curl` to query the `/metrics` endpoint on port 9103. For more information about the administrative ports, see [Network ports](/en/enterprise-server@3.20/admin/configuring-settings/configuring-network-settings/network-ports#administrative-ports).

```shell
curl 127.0.0.1:9103/metrics
```

If successful, the response will include metrics with the `collectd_` prefix.

## Configuring your external Prometheus server

To scrape exported metrics from  GitHub Enterprise Server, add a scraping configuration to the `prometheus.yaml` file on your external Prometheus server.

```yaml
- job_name: "ghes-prom-agent"
  scrape_interval: 10s
  static_configs:
    - targets: ["http(s)://HOSTNAME:9103/metrics"]
```

## Support for the darkshipped Prometheus metrics exporter

If you have been using the Prometheus metrics exporter since it was darkshipped in GitHub Enterprise Server 3.12, it will continue to work after upgrading to 3.16. In this version, you now have the option to specify trusted IPs for scraping requests.

## Sharing feedback

You can share your feedback on the Prometheus metrics exporter and scraping functionality with GitHub. For help with questions or issues, visit [GitHub Enterprise Support](https://support.github.com).