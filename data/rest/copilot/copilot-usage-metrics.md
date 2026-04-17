# REST API endpoints for Copilot usage metrics

Use the REST API to view Copilot usage metrics.

To enable these endpoints, the "Copilot usage metrics" policy must be set to **Enabled everywhere** for the enterprise. See [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies#defining-policies-for-your-enterprise).

For more information on the metrics returned by these endpoints, see [GitHub Copilot usage metrics](/en/copilot/reference/copilot-usage-metrics).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get Copilot enterprise usage metrics for a specific day

```
GET /enterprises/{enterprise}/copilot/metrics/reports/enterprise-1-day
```

Use this endpoint to retrieve download links for the Copilot enterprise usage metrics report for a specific day. The report provides comprehensive usage data for Copilot features across the enterprise.
The report contains aggregated metrics for the specified day, including usage statistics for various Copilot features, user engagement data, and feature adoption metrics. Reports are generated daily and made available for download through signed URLs with a limited expiration time.
The response includes download links to the report files, along with the specific date of the report. The report covers a complete day for which data has been processed. Reports are available starting from October 10, 2025, and historical data can be accessed for up to 1 year from the current date.
Enterprise owners, billing managers, and authorized users with fine-grained "View Enterprise Copilot Metrics" permission can retrieve Copilot metrics reports for the enterprise. OAuth app tokens and personal access tokens (classic) need either the manage\_billing:copilot or read:enterprise scopes to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`day`** (string) (required)
  The day to request data for, in YYYY-MM-DD format.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/copilot/metrics/reports/enterprise-1-day
```

**Response schema (Status: 200):**

* `download_links`: required, array of string, format: uri
* `report_day`: required, string, format: date

## Get Copilot enterprise usage metrics

```
GET /enterprises/{enterprise}/copilot/metrics/reports/enterprise-28-day/latest
```

Use this endpoint to retrieve download links for the latest 28-day enterprise Copilot usage metrics report. The report provides comprehensive usage data for Copilot features across the enterprise.
The report contains aggregated metrics for the previous 28 days, including usage statistics for various Copilot features, user engagement data, and feature adoption metrics. Reports are generated daily and made available for download through signed URLs with a limited expiration time.
The response includes download links to the report files, along with the specific date range covered by the report. The report covers a complete 28-day period ending on the most recent day for which data has been processed.
Enterprise owners, billing managers, and authorized users with fine-grained "View Enterprise Copilot Metrics" permission can retrieve Copilot metrics reports for the enterprise. OAuth app tokens and personal access tokens (classic) need either the manage\_billing:copilot or read:enterprise scopes to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/copilot/metrics/reports/enterprise-28-day/latest
```

**Response schema (Status: 200):**

* `download_links`: required, array of string, format: uri
* `report_start_day`: required, string, format: date
* `report_end_day`: required, string, format: date

## Get Copilot users usage metrics for a specific day

```
GET /enterprises/{enterprise}/copilot/metrics/reports/users-1-day
```

Use this endpoint to retrieve download links for the Copilot user usage metrics report for a specific day. The report provides detailed user-level usage data and engagement metrics for Copilot features across the enterprise.
The report contains user-specific metrics for the specified day, including individual user engagement statistics, feature usage patterns, and adoption metrics broken down by user. This report allows authorized users to analyze Copilot usage at the user level to understand adoption patterns and identify opportunities for increased engagement.
Reports are generated daily and made available for download through signed URLs with a limited expiration time. The response includes download links to the report files, along with the specific date of the report. The report covers a complete day for which data has been processed. Reports are available starting from October 10, 2025, and historical data can be accessed for up to 1 year from the current date.
Enterprise owners, billing managers, and authorized users with fine-grained "View Enterprise Copilot Metrics" permission can retrieve Copilot metrics reports for the enterprise. OAuth app tokens and personal access tokens (classic) need either the manage\_billing:copilot or read:enterprise scopes to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

* **`day`** (string) (required)
  The day to request data for, in YYYY-MM-DD format.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/copilot/metrics/reports/users-1-day
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot enterprise usage metrics for a specific day](#get-copilot-enterprise-usage-metrics-for-a-specific-day).

## Get Copilot users usage metrics

```
GET /enterprises/{enterprise}/copilot/metrics/reports/users-28-day/latest
```

Use this endpoint to retrieve download links for the latest 28-day enterprise users Copilot usage metrics report. The report provides detailed user-level usage data and engagement metrics for Copilot features across the enterprise.
The report contains user-specific metrics for the previous 28 days, including individual user engagement statistics, feature usage patterns, and adoption metrics broken down by user. This report allows authorized users to analyze Copilot usage at the user level to understand adoption patterns and identify opportunities for increased engagement.
Reports are generated daily and made available for download through signed URLs with a limited expiration time. The response includes download links to the report files, along with the specific date range covered by the report. The report covers a complete 28-day period ending on the most recent day for which data has been processed.
Enterprise owners, billing managers, and authorized users with fine-grained "View Enterprise Copilot Metrics" permission can retrieve Copilot metrics reports for the enterprise. OAuth app tokens and personal access tokens (classic) need either the manage\_billing:copilot or read:enterprise scopes to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/copilot/metrics/reports/users-28-day/latest
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot enterprise usage metrics](#get-copilot-enterprise-usage-metrics).

## Get Copilot organization usage metrics for a specific day

```
GET /orgs/{org}/copilot/metrics/reports/organization-1-day
```

Use this endpoint to retrieve download links for the Copilot organization usage metrics report for a specific day. The report provides comprehensive usage data for Copilot features across the organization.
The report contains aggregated metrics for the specified day, including usage statistics for various Copilot features, user engagement data, and feature adoption metrics. Reports are generated daily and made available for download through signed URLs with a limited expiration time.
The response includes download links to the report files, along with the specific date of the report. The report covers a complete day for which data has been processed.
Organization owners and authorized users with fine-grained "View Organization Copilot Metrics" permission can retrieve Copilot metrics reports for the organization. OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.
For more information about organization metrics attribution, see How are metrics attributed across organizations.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`day`** (string) (required)
  The day to request data for, in YYYY-MM-DD format.

### HTTP response status codes

* **200** - OK

* **204** - A header with no content is returned.

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/metrics/reports/organization-1-day
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot enterprise usage metrics for a specific day](#get-copilot-enterprise-usage-metrics-for-a-specific-day).

## Get Copilot organization usage metrics

```
GET /orgs/{org}/copilot/metrics/reports/organization-28-day/latest
```

Use this endpoint to retrieve download links for the latest 28-day organization Copilot usage metrics report. The report provides comprehensive usage data for Copilot features across the organization.
The report contains aggregated metrics for the previous 28 days, including usage statistics for various Copilot features, user engagement data, and feature adoption metrics. Reports are generated daily and made available for download through signed URLs with a limited expiration time.
The response includes download links to the report files, along with the specific date range covered by the report. The report covers a complete 28-day period ending on the most recent day for which data has been processed.
Organization owners and authorized users with fine-grained "View Organization Copilot Metrics" permission can retrieve Copilot metrics reports for the organization. OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.
For more information about organization metrics attribution, see How are metrics attributed across organizations.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/metrics/reports/organization-28-day/latest
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot enterprise usage metrics](#get-copilot-enterprise-usage-metrics).

## Get Copilot organization users usage metrics for a specific day

```
GET /orgs/{org}/copilot/metrics/reports/users-1-day
```

Use this endpoint to retrieve download links for the Copilot organization user usage metrics report for a specific day. The report provides detailed user-level usage data and engagement metrics for Copilot features across the organization.
The report contains user-specific metrics for the specified day, including individual user engagement statistics, feature usage patterns, and adoption metrics broken down by user. This report allows authorized users to analyze Copilot usage at the user level to understand adoption patterns and identify opportunities for increased engagement.
Reports are generated daily and made available for download through signed URLs with a limited expiration time. The response includes download links to the report files, along with the specific date of the report. The report covers a complete day for which data has been processed.
Organization owners and authorized users with fine-grained "View Organization Copilot Metrics" permission can retrieve Copilot metrics reports for the organization. OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.
For more information about organization metrics attribution, see How are metrics attributed across organizations.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

* **`day`** (string) (required)
  The day to request data for, in YYYY-MM-DD format.

### HTTP response status codes

* **200** - OK

* **204** - A header with no content is returned.

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/metrics/reports/users-1-day
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot enterprise usage metrics for a specific day](#get-copilot-enterprise-usage-metrics-for-a-specific-day).

## Get Copilot organization users usage metrics

```
GET /orgs/{org}/copilot/metrics/reports/users-28-day/latest
```

Use this endpoint to retrieve download links for the latest 28-day organization users Copilot usage metrics report. The report provides detailed user-level usage data and engagement metrics for Copilot features across the organization.
The report contains user-specific metrics for the previous 28 days, including individual user engagement statistics, feature usage patterns, and adoption metrics broken down by user. This report allows authorized users to analyze Copilot usage at the user level to understand adoption patterns and identify opportunities for increased engagement.
Reports are generated daily and made available for download through signed URLs with a limited expiration time. The response includes download links to the report files, along with the specific date range covered by the report. The report covers a complete 28-day period ending on the most recent day for which data has been processed.
Organization owners and authorized users with fine-grained "View Organization Copilot Metrics" permission can retrieve Copilot metrics reports for the organization. OAuth app tokens and personal access tokens (classic) need the read:org scope to use this endpoint.
For more information about organization metrics attribution, see How are metrics attributed across organizations.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

* **200** - OK

* **403** - Forbidden

* **404** - Resource not found

* **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/metrics/reports/users-28-day/latest
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot enterprise usage metrics](#get-copilot-enterprise-usage-metrics).