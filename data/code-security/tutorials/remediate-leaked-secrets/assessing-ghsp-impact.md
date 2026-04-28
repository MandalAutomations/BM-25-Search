# Assessing the impact of GitHub Secret Protection

Measure how GitHub Secret Protection reduces secret exposure across your organization, so you can demonstrate value and identify areas to strengthen your security posture.

## Introduction

After enabling GitHub Secret Protection (GHSP) for your organization, you'll want to assess its impact and understand how it's protecting your organization. This tutorial walks you through accessing secret-related data and interpreting the results to measure GHSP performance.

In this tutorial, you'll learn how to:

* Access your organization's security overview to view secret scanning data
* Review the secret risk assessment (SRA) report
* Compare and analyze the data to assess GHSP's impact

If you don't have a historic SRA report from before your GHSP rollout, you can still assess GHSP's effectiveness. Skip ahead to [Step 4: Analyze security overview data trends](#step-4-analyze-security-overview-data-trends).

## Prerequisites

* You need to have the organization owner or security manager role.
* Secret Protection must be enabled for your organization.

## Step 1: Access the organization-level security overview

The security overview provides real-time data about secret scanning alerts across your organization.

1. On GitHub, navigate to the main page of the organization.
2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
3. On the security overview page, click the **Risk** tab to view secret scanning data.
   The overview shows:
   * Total number of open secret scanning alerts
   * Alert trends over time
   * Breakdown by repository
   * Alert severity distribution

## Step 2: View your secret risk assessment report

If you previously ran a SRA report, you can access the report to establish a baseline.

1. On GitHub, navigate to the main page of the organization.
2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
3. In the sidebar, under "Security", click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key" aria-label="key" role="img"><path d="M10.5 0a5.499 5.499 0 1 1-1.288 10.848l-.932.932a.749.749 0 0 1-.53.22H7v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22H5v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22h-2A1.75 1.75 0 0 1 0 14.25v-2c0-.199.079-.389.22-.53l4.932-4.932A5.5 5.5 0 0 1 10.5 0Zm-4 5.5c-.001.431.069.86.205 1.269a.75.75 0 0 1-.181.768L1.5 12.56v1.69c0 .138.112.25.25.25h1.69l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l1.023-1.025a.75.75 0 0 1 .768-.18A4 4 0 1 0 6.5 5.5ZM11 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg> Assessments**.
4. Review the key metrics from the assessment, including:
   * Number of exposed secrets detected
   * Types of secrets found
   * Repositories with the highest risk
   * Recommended remediation actions

> \[!NOTE] The SRA report represents a point-in-time snapshot of your secret exposure before or during your GHSP implementation.

## Step 3: Compare SRA data with current security overview

The SRA report is a **point-in-time** snapshot taken before or during your GHSP rollout, while the security overview shows **real-time** data that updates as alerts are opened and resolved. To make a meaningful comparison, you need to ensure both datasets cover the same secret types.

### Filter to comparable pattern types

The SRA report only detects **provider patterns** and **generic patterns**. The security overview, however, may also include results from custom patterns you've configured since enabling GHSP. To ensure an accurate comparison, filter the security overview to the same pattern types the SRA covers.

#### Using the UI

In the security overview **Risk** tab, use the filter bar to narrow results to provider and generic patterns only, excluding any custom patterns.

#### Using the API

Alternatively, you can use the REST API to programmatically retrieve alerts filtered by secret type. For example, to list only default (provider) secret scanning alerts for a repository:

```shell copy
gh api \
  -H "Accept: application/vnd.github+json" \
  /orgs/ORG/secret-scanning/alerts --paginate
```

This returns alerts for default patterns only. To also include generic patterns in your results, pass the specific token names using the `secret_type` parameter.

For more information, see [REST API endpoints for secret scanning](/en/rest/secret-scanning/secret-scanning).

### Build your comparison

1. Using the filtered data, create a comparison table with these key metrics:

   | Metric                | SRA report (Baseline) | Current security overview (Filtered) | Change        |
   | --------------------- | --------------------- | ------------------------------------ | ------------- |
   | Total exposed secrets | \[SRA number]         | \[Current number]                    | \[Difference] |
   | Critical alerts       | \[SRA number]         | \[Current number]                    | \[Difference] |
   | Affected repositories | \[SRA number]         | \[Current number]                    | \[Difference] |

2. Calculate the percentage change for each metric:
   * **Positive impact indicators:** Reduction in total exposed secrets, fewer critical alerts
   * **Areas for improvement:** New alerts appearing, specific repositories with increasing trends

3. Note any significant differences in:
   * Secret types being detected
   * Repository coverage
   * Alert resolution rates

## Step 4: Analyze security overview data trends

Even without an SRA report, you can assess GHSP effectiveness by analyzing trends in the security overview.

1. On GitHub, navigate to the main page of the organization.

2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.

3. In the security overview **Risk** tab, look at the trend graph showing secret scanning alerts over time.

4. Identify patterns:
   * **Declining trend:** Indicates successful remediation and prevention
   * **Plateau:** May suggest steady state or need for increased awareness
   * **Rising trend:** May indicate increased detection coverage or new secret introduction

5. Click on individual repositories to drill down into specific alert details.

6. Review the alert resolution rate:
   * Navigate to the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for your organization.
   * Under "Findings", Click **Secret scanning**.
   * Check how many alerts have been closed versus the number of alerts that remain open.
   * Select the alert type you're interested in.
   * Assess average time to resolution.

## Step 5: Interpret the results and take action

Based on your analysis, determine the next steps.

### If you're seeing positive trends

* Document the improvement to demonstrate GHSP value
* Identify successful practices to replicate across other repositories
* Consider expanding GHSP coverage to additional repositories or organizations

### If you're seeing areas for improvement

* Review repositories with increasing alerts or slow resolution times
* Provide additional training to development teams
* Assess whether custom patterns need to be configured
* Check if push protection is enabled to prevent new secrets from being introduced

### Ongoing monitoring

* Schedule regular reviews (weekly or monthly) of the security overview
* Set up notifications for new secret scanning alerts
* Track metrics over time to demonstrate continuous improvement

## Further reading

* To understand secret scanning metrics in detail, see [Viewing security insights](/en/code-security/security-overview/viewing-security-insights).