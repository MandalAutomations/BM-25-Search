# GitHub Copilot with data residency

Keep AI-powered coding assistance within your designated region, so you can meet compliance requirements while improving developer productivity.

If your enterprise uses GitHub Enterprise Cloud with data residency, you can enable a policy to ensure that all inference processing and associated data for GitHub Copilot remain **within your designated geographic region**.

## Supported regions

Copilot with data residency is currently available in the following regions:

* United States
* European Union

GitHub plans to add support for more regions in the near future.

## How restrictions are enforced

When you enforce data residency for Copilot, GitHub routes all Copilot requests to model endpoints within your enterprise's designated region. Your code, prompts, and Copilot responses never leave your region during inference processing.

The enforcement happens at multiple levels:

* **Authentication and routing**: Users' authentication tokens only grant access to your region-specific endpoints, ensuring that traffic never leaves the designated geography.
* **Model availability**: Copilot will only surface models that are certified and available in your region. Developers cannot access models hosted outside your region.
* **Logs and telemetry**: All Copilot-related logs and telemetry are stored within region-appropriate, compliant storage.

## Client version requirements

To use Copilot with model enforcement, developers must use compatible client versions. Generally, any Copilot extension or CLI version released in 2025 or later includes the necessary policy enforcement capabilities.

If a user attempts to use Copilot with an older, incompatible client, they will be prompted to update their extension or CLI to continue.

## Supported Copilot features

All generally available Copilot features work with this enforcement. See [GitHub Copilot features](/en/enterprise-cloud@latest/copilot/get-started/features).

Preview features that reach general availability will be supported with compliant model alternatives at the time of their GA release.

## Available AI models by region

The models available for Copilot vary by region. Users will be able to see available models for your region in the model selector in their Copilot interface.

> \[!NOTE]
> Model availability changes over time. New models released on GitHub.com may take additional time to become available as providers deploy regional infrastructure and obtain necessary certifications.

### United States

<!-- Note: US data resident and FedRAMP compliant models are currently the same, but this may not always be the case. However, we should be able to add new models after this reusable reference in the relevant article -->

* GPT-4o mini
* GPT-4o
* GPT-4.1
* GPT-5.2
* GPT-5.2-Codex
* GPT-5.3-Codex
* Claude Haiku 4.5
* Claude Sonnet 4
* Claude Sonnet 4.5
* Claude Opus 4.5
* Claude Sonnet 4.6
* Claude Opus 4.6

### European Union

* GPT-4o mini
* GPT-4.1
* GPT-5 mini
* GPT-5.2
* GPT-5.4
* Claude Haiku 4.5
* Claude Sonnet 4
* Claude Sonnet 4.5
* Claude Opus 4.5
* Claude Sonnet 4.6
* Claude Opus 4.6

## Pricing changes

Copilot requests processed with this enforcement in place include a 10% model multiplier increase. This reflects the additional infrastructure costs that model providers charge for regional and compliance-certified endpoints.

For example, if a model normally counts as 1 premium request, the same model processed with this enforcement enabled counts as 1.1 premium requests. This pricing applies to all compliant model requests across all providers.

See [Requests in GitHub Copilot](/en/enterprise-cloud@latest/copilot/concepts/billing/copilot-requests#model-multipliers).

## Policy controls

To enable this policy, use the **Restrict Copilot to data residency compliant models** policy in the "Features" section of your enterprise's Copilot policies. This policy is disabled by default, and enabling it will affect your pricing for Copilot requests.

For instructions on finding your policies page, see [Managing policies and features for GitHub Copilot in your enterprise](/en/enterprise-cloud@latest/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies).