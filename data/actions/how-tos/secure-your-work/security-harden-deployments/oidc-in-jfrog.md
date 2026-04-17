# Configuring OpenID Connect in JFrog

Use OpenID Connect within your workflows to authenticate with JFrog.

## Overview

OpenID Connect (OIDC) allows your GitHub Actions workflows to authenticate with [JFrog](https://jfrog.com/) to download and publish artifacts without storing JFrog passwords, tokens, or API keys in GitHub.

This guide gives an overview of how to configure JFrog to trust GitHub's OIDC as a federated identity, and demonstrates how to use this configuration in a GitHub Actions workflow.

For an example GitHub Actions workflow, see [Sample GitHub Actions Integration](https://jfrog.com/help/r/jfrog-platform-administration-documentation/sample-github-actions-integration) in the JFrog documentation.

For an example GitHub Actions workflow using the JFrog CLI, see [`build-publish.yml`](https://github.com/jfrog/jfrog-github-oidc-example/blob/main/.github/workflows/build-publish.yml) in the `jfrog-github-oidc-example` repository.

## Prerequisites

* To learn the basic concepts of how GitHub uses OpenID Connect (OIDC), and its architecture and benefits, see [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect).

* Before proceeding, you must plan your security strategy to ensure that access tokens are only allocated in a predictable way. To control how your cloud provider issues access tokens, you **must** define at least one condition, so that untrusted repositories can’t request access tokens for your cloud resources. For more information, see [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect#configuring-the-oidc-trust-with-the-cloud).

* To be secure, you need to set a Claims JSON in JFrog when configuring identity mappings. For more information, see [AUTOTITLE](https://jfrog.com/help/r/jfrog-platform-administration-documentation/configure-identity-mappings) and [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect#customizing-the-token-claims).

  For example, you can set `iss` to `https://token.actions.githubusercontent.com`, and the `repository` to something like "octo-org/octo-repo"\`. This will ensure only Actions workflows from the specified repository will have access to your JFrog platform. The following is an example Claims JSON when configuring identity mappings.

  ```json copy
  {
      "iss": "https://token.actions.githubusercontent.com",
      "repository": "octo-org/octo-repo"
  }
  ```

## Adding the identity provider to JFrog

To use OIDC with JFrog, establish a trust relationship between GitHub Actions and the JFrog platform. For more information about this process, see [OpenID Connect Integration](https://jfrog.com/help/r/jfrog-platform-administration-documentation/openid-connect-integration) in the JFrog documentation.

1. Sign in to your JFrog Platform.
2. Configure trust between JFrog and your GitHub Actions workflows.
3. Configure identity mappings.

## Updating your GitHub Actions workflow

### Authenticating with JFrog using OIDC

In your GitHub Actions workflow file, ensure you are using the provider name and audience you configured in the JFrog Platform.

The following example uses the placeholders `YOUR_PROVIDER_NAME` and `YOUR_AUDIENCE`.

```yaml
# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.
permissions:
  id-token: write
  contents: read

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Set up JFrog CLI with OIDC
        id: setup-jfrog-cli
        uses: jfrog/setup-jfrog-cli@29fa5190a4123350e81e2a2e8d803b2a27fed15e
        with:
          JF_URL: ${{ env.JF_URL }}
          oidc-provider-name: 'YOUR_PROVIDER_NAME'
          oidc-audience: 'YOUR_AUDIENCE' # This is optional

      - name: Upload artifact
        run: jf rt upload "dist/*.zip" my-repo/

```

> \[!TIP]
> When OIDC authentication is used, the `setup-jfrog-cli` action automatically provides `oidc-user` and `oidc-token` as step outputs.
> These can be used for other integrations that require authentication with JFrog.
> To reference these outputs, ensure the step has an explicit `id` defined (for example `id: setup-jfrog-cli`).

### Using OIDC Credentials in other steps

```yaml
# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.
      - name: Sign in to Artifactory Docker registry
        uses: docker/login-action@v3
        with:
          registry: ${{ env.JF_URL }}
          username: ${{ steps.setup-jfrog-cli.outputs.oidc-user }}
          password: ${{ steps.setup-jfrog-cli.outputs.oidc-token }}
```

## Further reading

* [OpenID Connect Integration](https://jfrog.com/help/r/jfrog-platform-administration-documentation/openid-connect-integration) in the JFrog documentation
* [Identity Mappings](https://jfrog.com/help/r/jfrog-platform-administration-documentation/identity-mappings) in the JFrog documentation
* [OpenID Connect](/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect)