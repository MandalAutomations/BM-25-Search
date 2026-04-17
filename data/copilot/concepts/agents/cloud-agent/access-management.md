# Managing access to GitHub Copilot cloud agent

Find out about Copilot cloud agent policies available for GitHub Copilot Enterprise and GitHub Copilot Business, and about disabling the agent for specific repositories.

> \[!NOTE]
> For an introduction to Copilot cloud agent, see [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent).

## Overview

Copilot cloud agent is an AI-powered software development agent that can work autonomously on issues or developer requests. It raises draft pull requests to propose a fix and iterates on the changes in response to feedback.

If you are a GitHub Copilot Enterprise or GitHub Copilot Business subscriber, Copilot cloud agent is disabled by default and must be enabled by an administrator before it is available for use.

If you are a GitHub Copilot Pro or Pro+ subscriber, Copilot cloud agent is enabled by default.

Once enabled, you can use Copilot cloud agent in any repository, provided that an administrator hasn't opted the repository out.

## Copilot cloud agent policies for Copilot Business and Copilot Enterprise

For GitHub Copilot Business and GitHub Copilot Enterprise subscribers, the ability to use Copilot cloud agent is controlled by policy settings defined at the organization level. See [Adding GitHub Copilot cloud agent to your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/add-copilot-cloud-agent).

If the organization is owned by an enterprise, enablement may be controlled at the enterprise level. See [Enabling GitHub Copilot cloud agent in your enterprise](/en/enterprise-cloud@latest/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/manage-copilot-cloud-agent).

## Opting repositories out of Copilot cloud agent

By default, users with Copilot cloud agent enabled can use it in all repositories.

Enterprise administrators and organization owners (for organization-owned repositories) and users (for user-owned repositories) can opt out repositories and prevent Copilot cloud agent from being used in those repositories.

For information on disabling Copilot cloud agent in some or all repositories owned by an organization, see [Adding GitHub Copilot cloud agent to your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/add-copilot-cloud-agent).

For information on disabling Copilot cloud agent in all repositories owned by an enterprise, see [Blocking GitHub Copilot cloud agent in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/block-copilot-cloud-agent).

For information on disabling Copilot cloud agent in repositories owned by your personal user account, see [Managing GitHub Copilot policies as an individual subscriber](/en/copilot/managing-copilot/managing-copilot-as-an-individual-subscriber/managing-your-copilot-plan/managing-copilot-policies-as-an-individual-subscriber#enabling-or-disabling-copilot-cloud-agent).

## Further reading

* [GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent)
* [Customizing the development environment for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/customize-the-agent-environment)
* [Customizing or disabling the firewall for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/customize-the-agent-firewall)
* [Extending GitHub Copilot cloud agent with the Model Context Protocol (MCP)](/en/copilot/how-tos/use-copilot-agents/cloud-agent/extend-cloud-agent-with-mcp)
* [Piloting GitHub Copilot cloud agent in your organization](/en/copilot/tutorials/cloud-agent/pilot-cloud-agent)