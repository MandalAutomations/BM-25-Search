# Agent management for enterprises

Maintain your enterprise's security and compliance standards and supercharge your developers by managing agents with AI Controls.

## Overview

The AI Controls view provides a centralized platform where you can manage and monitor AI policies and agents across your enterprise. From the "Agents" page, you can:

* Manage the enterprise-level availability of agents like Copilot cloud agent, Copilot code review, and Copilot custom agents
* Control who can manage your enterprise-level custom agents
* View and filter a list of agent sessions in your enterprise over the last 24 hours
* Find a detailed record of agentic audit log events

## Copilot cloud agent

Copilot policies are also managed at the enterprise level. If your enterprise owner has selected a specific policy, such as enabling a feature everywhere, disabling it everywhere, or enabling it for selected organizations only, you cannot override that setting at the organization level. For information on how policies combine, see [GitHub Copilot policies to control availability of features and models](/en/copilot/concepts/policies).

Enterprise owners and AI managers can control how Copilot cloud agent is adopted across the enterprise by choosing one of four policy states. This allows you to pilot adoption progressively and manage risk.

If you choose the **Enabled for selected organizations** policy, you can select organizations individually or based on organization custom properties. This lets you define dynamic groups of organizations that align with your existing organizational structure—for example, by region, compliance tier, or department. You can manage this policy setting using the REST API endpoints or directly in the AI Controls page.  See [REST API endpoints for Copilot coding agent management](/en/rest/copilot/copilot-coding-agent-management#copilot-coding-agent-policy-states). Please note that using custom properties to enable CCA is evaluated once at the time of configuration. Organizations will not be automatically enabled or disabled for CCA if the custom property is added, removed, or modified later.

## Copilot custom agents

Copilot custom agents are specialized versions of Copilot cloud agent that you can configure with tailored prompts, tools, and context, making them excel at specific tasks. Custom agents can be defined and managed at the enterprise level for greater control and compliance, or at the organization and repository levels to allow teams the flexibility to build for their specific needs.

You can manage your enterprise-level custom agents:

* From the AI Controls view
* Using the REST API. See [REST API endpoints for Copilot custom agents](/en/rest/copilot/copilot-custom-agents).

For more detailed information on custom agents, see [About custom agents](/en/copilot/concepts/agents/cloud-agent/about-custom-agents).

## Agent sessions

An agent session encompasses an entire interaction with Copilot cloud agent, or any individual custom agent, on a specific task. These tasks include:

* Prompting the agent to create or edit a pull request
* Assigning the agent to an issue

For billing information on agent sessions, see [GitHub Copilot premium requests](/en/billing/concepts/product-billing/github-copilot-premium-requests#usage-by-copilot-cloud-agent).

## Agent mode in the IDE

Enterprise and organization owners can separately control whether their users have access to agent mode in IDE chat, independently from the "Chat in IDE" policy. This gives you finer-grained control over agentic capabilities in your developers' IDEs.

To manage this policy, enable or disable **Copilot Agent Mode in IDE chat** in your AI Controls settings. For more information, see [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies).

## Next steps

To get started with custom agents, see [Preparing to use custom agents in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/prepare-for-custom-agents).

## Further reading

* [About third-party agents](/en/copilot/concepts/agents/about-third-party-agents)