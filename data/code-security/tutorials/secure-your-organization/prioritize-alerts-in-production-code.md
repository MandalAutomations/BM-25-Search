# Prioritizing Dependabot and code scanning alerts using production context

Focus remediation on real risk by targeting Dependabot and code scanning alerts in artifacts deployed to production, using metadata from external systems and integrations like Dynatrace, JFrog Artifactory, Microsoft Defender for Cloud, or your own CI/CD workflows.

Application Security (AppSec) managers are often overwhelmed by a high volume of alerts, many of which may not represent real risk because the affected code never makes it to production. By associating production context with your alerts, you can filter and prioritize vulnerabilities that impact artifacts actually approved for production environments. This enables your team to focus remediation efforts on the vulnerabilities that matter most, reducing noise and improving your security posture.

## 1. Associate artifacts with production context

GitHub's linked artifacts page allows you to provide production context for your company's builds using the REST API or a partner integration. Teams can then use this context to prioritize Dependabot and code scanning alerts. For more information, see [About linked artifacts](/en/code-security/concepts/supply-chain-security/linked-artifacts).

To provide production context, you should configure your system to:

* Update **storage records** in the linked artifacts page whenever an artifact is promoted to a production-approved package repository.
* Update **deployment records** when an artifact is deployed to a production environment.

GitHub processes this metadata and uses it to power alert filters, such as `artifact-registry-url` and `artifact-registry` from storage records, and `has:deployment` and `runtime-risk` from deployment records. Runtime risks from deployment records are also visible as properties on individual code scanning and Dependabot alert pages.

For more information on updating records, see [Uploading storage and deployment data to the linked artifacts page](/en/code-security/how-tos/secure-your-supply-chain/establish-provenance-and-integrity/upload-linked-artifacts).

## 2. Use production context filters

Production context filters are made available in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.

* **Dependabot view**: See [Viewing and updating Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/viewing-and-updating-dependabot-alerts#viewing-dependabot-alerts).
* **Code scanning view**: See [Assessing code scanning alerts for your repository](/en/code-security/code-scanning/managing-code-scanning-alerts/assessing-code-scanning-alerts-for-your-repository).
* **Security campaign view**: See [Creating and managing security campaigns](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/creating-managing-security-campaigns).

Once the alert list is displayed, use the `artifact-registry-url` or `artifact-registry` filters in organization views to focus on vulnerabilities affecting artifacts present in production.

* For your own artifact repository that is hosted at `my-registry.example.com`, you would use:

  ```text copy
  artifact-registry-url:my-registry.example.com
  ```

* If you use JFrog Artifactory, you can use `artifact-registry` with no further setup in GitHub:

  ```text copy
  artifact-registry:jfrog-artifactory
  ```

You can also use the `has:deployment` and `runtime-risk` filters to focus on vulnerabilites that deployment metadata shows as in deployment or at risk of runtime vulnerabilities. This data is populated automatically if you have connected MDC. For example:

* To focus on alerts in deployed code that is exposed to the internet, you would use:

  ```text copy
  has:deployment AND runtime-risk:internet-exposed
  ```

You can also combine these production context filters with other filters, such as EPSS:

```text copy
epss > 0.5 AND artifact-registry-url:my-registry.example.com
```

## 3. Remediate alerts in production code

Now you have identified the alerts that put your production code at risk of exploitation, you need to remediate them as a matter of urgency. Where possible use automation to lower the barrier to remediation.

* **Dependabot alerts:** Use automated pull requests for security fixes. See [Configuring Dependabot security updates](/en/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates).
* **Code scanning alerts:** Create targeted campaigns with Copilot Autofix. See [Creating and managing security campaigns](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/creating-managing-security-campaigns).

## Further reading

* [Prioritizing Dependabot alerts using metrics](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-vulnerabilities/prioritizing-dependabot-alerts-using-metrics)