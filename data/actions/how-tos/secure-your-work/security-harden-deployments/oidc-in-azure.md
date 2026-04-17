# Configuring OpenID Connect in Azure

Use OpenID Connect within your workflows to authenticate with Azure.

## Overview

OpenID Connect (OIDC) allows your GitHub Actions workflows to access resources in Azure, without needing to store the Azure credentials as long-lived GitHub secrets.

This guide gives an overview of how to configure Azure to trust GitHub's OIDC as a federated identity, and includes a workflow example for the [`azure/login`](https://github.com/Azure/login) action that uses tokens to authenticate to Azure and access resources.

## Prerequisites

* To learn the basic concepts of how GitHub uses OpenID Connect (OIDC), and its architecture and benefits, see [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect).

* Before proceeding, you must plan your security strategy to ensure that access tokens are only allocated in a predictable way. To control how your cloud provider issues access tokens, you **must** define at least one condition, so that untrusted repositories can’t request access tokens for your cloud resources. For more information, see [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect#configuring-the-oidc-trust-with-the-cloud).

## Adding the federated credentials to Azure

GitHub's OIDC provider works with Azure's workload identity federation. For an overview, see Microsoft's documentation at [Workload identity federation](https://docs.microsoft.com/en-us/azure/active-directory/develop/workload-identity-federation).

To configure the OIDC identity provider in Azure, you will need to perform the following configuration. For instructions on making these changes, refer to [the Azure documentation](https://docs.microsoft.com/en-us/azure/developer/github/connect-from-azure).

In the following procedure, you will create an application for Microsoft Entra ID (previously known as Azure AD).

1. Create an Entra ID application and a service principal.
2. Add federated credentials for the Entra ID application.
3. Create GitHub secrets for storing Azure configuration.

Additional guidance for configuring the identity provider:

* For security hardening, make sure you've reviewed [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect#configuring-the-oidc-trust-with-the-cloud). For an example, see [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect#configuring-the-subject-in-your-cloud-provider).
* For the `audience` setting, `api://AzureADTokenExchange` is the recommended value, but you can also specify other values here.

## Updating your GitHub Actions workflow

To update your workflows for OIDC, you will need to make two changes to your YAML:

1. Add permissions settings for the token.
2. Use the [`azure/login`](https://github.com/Azure/login) action to exchange the OIDC token (JWT) for a cloud access token.

> \[!NOTE]
> When environments are used in workflows or in OIDC policies, we recommend adding protection rules to the environment for additional security. For example, you can configure deployment rules on an environment to restrict which branches and tags can deploy to the environment or access environment secrets. For more information, see [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/managing-environments-for-deployment#deployment-protection-rules).

### Adding permissions settings

The job or workflow run requires a `permissions` setting with [`id-token: write`](/en/actions/security-guides/automatic-token-authentication#modifying-the-permissions-for-the-github_token) to allow GitHub's OIDC provider to create a JSON Web Token for every run.

> \[!NOTE] Setting `id-token: write` in the workflow’s permissions does not give the workflow permission to modify or write to any resources. Instead, it only allows the workflow to request (fetch) and use (set) an OIDC token for an action or step. This token is then used to authenticate with external services using a short-lived access token.

For detailed information on required permissions, configuration examples, and advanced scenarios, see [OpenID Connect reference](/en/actions/reference/openid-connect-reference##workflow-permissions-for-the-requesting-the-oidc-token).

### Requesting the access token

The [`azure/login`](https://github.com/Azure/login) action receives a JWT from the GitHub OIDC provider, and then requests an access token from Azure. For more information, see the [`azure/login`](https://github.com/Azure/login) documentation.

The following example exchanges an OIDC ID token with Azure to receive an access token, which can then be used to access cloud resources.

```yaml copy
# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.
name: Run Azure Login with OIDC
on: [push]

permissions:
  id-token: write
  contents: read
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: 'Az CLI login'
        uses: azure/login@8c334a195cbb38e46038007b304988d888bf676a
        with:
          client-id: ${{ secrets.AZURE_CLIENT_ID }}
          tenant-id: ${{ secrets.AZURE_TENANT_ID }}
          subscription-id: ${{ secrets.AZURE_SUBSCRIPTION_ID }}

      - name: 'Run az commands'
        run: |
          az account show
          az group list
```

## Further reading

* [Using OpenID Connect with reusable workflows](/en/actions/deployment/security-hardening-your-deployments/using-openid-connect-with-reusable-workflows)
* [Self-hosted runners reference](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/communicating-with-self-hosted-runners)