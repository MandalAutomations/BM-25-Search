# Setting up external monitoring with OpenTelemetry

Configure external monitoring systems to collect and analyze OpenTelemetry metrics from your GitHub Enterprise Server instance.

## External monitoring approaches

External monitoring with OpenTelemetry allows you to integrate your GitHub Enterprise Server instance with existing monitoring infrastructure and tools. GitHub Enterprise Server provides two primary approaches for external monitoring:

1. **Prometheus endpoint**: Expose metrics in Prometheus format for external tools to scrape
2. **Custom OpenTelemetry pipelines**: Configure the OpenTelemetry collector to push metrics to external monitoring systems

> \[!NOTE]
> In cluster deployments, each node exposes its own local metrics. This includes node servers, which collect metrics from all servers in the cluster but only expose their own local metrics through monitoring endpoints. To collect metrics from all nodes in a cluster, you must configure your monitoring system to collect from each node individually.

## Prerequisites

* GitHub Enterprise Server 3.18 or later with OpenTelemetry metrics enabled
* Network connectivity between your GitHub Enterprise Server instance and external monitoring systems
* Administrative access to both your GitHub Enterprise Server instance and monitoring systems

## Choosing your monitoring approach

Choose the monitoring approach that best fits your infrastructure and requirements.

### Prometheus endpoint (recommended for most users)

Use the Prometheus endpoint when:

* You have existing Prometheus-based monitoring infrastructure
* You prefer a pull-based monitoring model
* You want to use external tools to scrape GitHub Enterprise Server metrics
* You need simple integration with minimal configuration

### Custom OpenTelemetry pipelines

Use custom OpenTelemetry pipelines when:

* You need to push metrics to multiple monitoring systems simultaneously
* You want to transform, filter, or aggregate metrics before sending them externally
* You're using cloud-native monitoring solutions that prefer OTLP
* You need advanced metric processing capabilities

## Option 1: Using the Prometheus endpoint

The OpenTelemetry monitoring stack includes a Prometheus-compatible endpoint that exposes all collected metrics in Prometheus format, enabling integration with external monitoring tools. See [Text-based format](https://prometheus.io/docs/instrumenting/exposition_formats/#text-based-format) in the documentation for Prometheus.

### Enabling the Prometheus endpoint

You can enable the Prometheus endpoint using either the Management Console or the command line interface.

#### Using the Management Console

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the monitoring settings, select **Enable OpenTelemetry**.

5. Optionally, adjust the **Metrics retention** and **Metrics scrape interval** fields to optimize performance.

6. Select **Enable Prometheus-compatible (/metrics) endpoint**.

7. In the **Endpoint password** field, enter a strong password to control access to the endpoint.

8. Optionally, in the **Trusted IPv4/IPv6 addresses or CIDR blocks in a comma-separated list** field, enter the IP addresses or CIDR blocks that are allowed to access the endpoint.

9. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

10. Wait for the configuration run to complete.

#### Using the command line interface

1. SSH into your GitHub Enterprise Server instance.

2. Enable the Prometheus endpoint:

   ```shell
   ghe-config observability.metrics.prometheus-endpoint-enabled true
   ghe-config-apply
   ```

3. Set up authentication for the endpoint (strongly recommended):

   ```shell
   ghe-config observability.metrics.prometheus-endpoint-password your-secure-password
   ghe-config-apply
   ```

### Accessing the Prometheus endpoint

The Prometheus endpoint will be available at:

```text
https://[hostname]:8010/metrics
```

Authentication uses:

* **Username**: `ghes-metrics`
* **Password**: The value set in your configuration

### Configuring external tools to scrape metrics

You can configure various external monitoring tools to scrape metrics from the Prometheus endpoint.

#### Prometheus

Add the following job configuration to your Prometheus configuration file:

```yaml
scrape_configs:
  - job_name: 'github-enterprise-server'
    static_configs:
      - targets: ['your-ghes-hostname:8010']
    basic_auth:
      username: 'ghes-metrics'
      password: 'your-secure-password'
    scrape_interval: 30s
    metrics_path: '/metrics'
    scheme: https
    tls_config:
      # Set `true` only when testing with self-signed certificates
      insecure_skip_verify: false
```

#### Other monitoring tools

The Prometheus endpoint is compatible with any monitoring tool that can scrape Prometheus-format metrics, including:

* Grafana (using Prometheus data source)
* Datadog (using Prometheus check)
* New Relic (using Prometheus integration)
* Victoria Metrics
* InfluxDB (using Prometheus input plugin)

### Security considerations for the Prometheus endpoint

Additional security measures can be implemented to protect your metrics endpoint.

#### Password protection

The Prometheus endpoint supports using a password to limit access. You can configure this through either the Management Console or the command line interface.

* **Using the Management Console**:

  In the monitoring settings, use the **Endpoint password** field to enter a strong password to control access to the endpoint.

* **Using the command line interface**:

  ```shell
  ghe-config observability.metrics.prometheus-endpoint-password your-secure-password
  ghe-config-apply
  ```

#### IP allowlisting

The Prometheus endpoint supports IP allowlisting for enhanced security. You can configure this through either the Management Console or the command line interface.

* **Using the Management Console**:

  In the monitoring settings, use the **Trusted IPv4/IPv6 addresses or CIDR blocks in a comma-separated list** field to enter IP addresses or CIDR blocks that should have access to the endpoint.

* **Using the command line interface**:

  ```shell
  ghe-config observability.metrics.prometheus-endpoint-trusted-ips "10.0.0.0/8,192.168.0.0/16"
  ghe-config-apply
  ```

### Testing the endpoint

Check that metrics are being exported:

```shell
# Test the Prometheus endpoint
curl -u ghes-metrics:your-password https://your-ghes-hostname:8010/metrics
```

## Option 2: Using custom OpenTelemetry pipelines

GitHub Enterprise Server supports custom OpenTelemetry collector configurations, allowing you to extend the monitoring capabilities by adding custom pipelines, exporters, and processors. This enable you to ship metrics to external monitoring systems while maintaining the default GitHub Enterprise Server observability stack.

### Important considerations for custom configurations

* Custom configurations are additive to the default GitHub Enterprise Server OpenTelemetry configuration
* **Reserved paths**: The paths `/ghes` and `/internal` are reserved for GitHub Enterprise Server internal use and must not be used in custom configuration files
* `otlp/ghes` and `prometheus/ghes` receivers are the built-in sources of GitHub Enterprise Server metrics that you can use in your custom pipelines
* Test your configuration thoroughly in a non-production environment before applying to production
* Monitor resource usage after enabling custom configurations, as additional pipelines may increase CPU and memory consumption

### Enabling custom OpenTelemetry configuration

You can enable custom OpenTelemetry configuration using either the Management Console or the command line interface.

#### Using the Management Console

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the monitoring settings, first select **Enable OpenTelemetry**.

5. Select **Enable custom OpenTelemetry Collector pipelines**.

6. Use the **Browse...** button to upload your custom OpenTelemetry collector config file (\*.yml), see [Example configurations for popular monitoring systems](#example-configurations-for-popular-monitoring-systems).

7. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

8. Wait for the configuration run to complete.

#### Using the command line

1. SSH into your GitHub Enterprise Server instance and run the following command.

   ```shell
   ghe-config observability.metrics.custom-config-enabled true
   ```

2. Create your custom OpenTelemetry configuration file at `/data/user/common/otelcol.yaml`:

   ```shell
   sudo nano /data/user/common/otelcol.yaml
   ```

3. Add your custom configuration (see [Example configurations for popular monitoring systems](#example-configurations-for-popular-monitoring-systems)).

4. Apply the configuration:

   ```shell
   ghe-config-apply
   ```

### Example configurations for popular monitoring systems

The following examples show how to configure custom OpenTelemetry pipelines for popular monitoring platforms. For information on other exporters or to create your own, see the repository of [OpenTelemetry Collectors](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/exporter).

#### Grafana Cloud

```yaml
---
exporters:
  prometheusremotewrite:
    endpoint: "https://prometheus-us-central1.grafana.net/api/prom/push"
    headers:
      Authorization: "Bearer your-grafana-cloud-token"

service:
  pipelines:
    metrics:
      receivers: [otlp/ghes, prometheus/ghes]
      processors: [batch/ghes]
      exporters: [prometheusremotewrite]
```

#### Datadog

```yaml
---
exporters:
  datadog:
    api:
      site: datadoghq.com
      key: your-datadog-api-key
    host_metadata:
      enabled: true

service:
  pipelines:
    metrics:
      receivers: [otlp/ghes, prometheus/ghes]
      processors: [batch/ghes]
      exporters: [datadog]
```

#### New Relic

```yaml
---
exporters:
  otlp:
    endpoint: "https://otlp.nr-data.net:4317"
    headers:
      api-key: "your-new-relic-license-key"

service:
  pipelines:
    metrics:
      receivers: [otlp/ghes, prometheus/ghes]
      processors: [batch/ghes]
      exporters: [otlp]
```

#### Generic OTLP endpoint

```yaml
---
exporters:
  otlp:
    endpoint: "https://your-otel-collector:4317"
    headers:
      api-key: "your-api-key"
    tls:
      insecure: false

service:
  pipelines:
    metrics:
      receivers: [otlp/ghes, prometheus/ghes]
      processors: [batch/ghes]
      exporters: [otlp]
```

## Network and security considerations

Configure your network and security settings based on your chosen monitoring approach.

### TLS and certificates

For secure connections to external monitoring systems:

* Use valid TLS certificates when possible
* Configure appropriate `tls_config` settings in your monitoring system
* Consider using mutual TLS (mTLS) for enhanced security

## Next steps

* To configure OpenTelemetry settings, see [Configuring OpenTelemetry for your instance](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/configuring-opentelemetry-for-your-instance).
* To learn more about available metrics, see [About OpenTelemetry metrics](/en/enterprise-server@3.20/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/about-opentelemetry-metrics).