# Authenticating ARC to the GitHub API

Authenticate Actions Runner Controller to the GitHub API.

You can authenticate Actions Runner Controller (ARC) to the GitHub API by using a GitHub App or by using a personal access token (classic).

> \[!NOTE]
> You cannot authenticate using a GitHub App for runners at the enterprise level. For more information, see [Managing access to self-hosted runners using groups](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#about-runner-groups).

## Authenticating ARC with a GitHub App

1. Create a GitHub App that is owned by an organization. For more information, see [Registering a GitHub App](/en/apps/creating-github-apps/creating-github-apps/creating-a-github-app). Configure the GitHub App as follows.

   1. For "Homepage URL," enter `https://github.com/actions/actions-runner-controller`.

   2. Under "Permissions," click **Repository permissions**. Then use the dropdown menus to select the following access permissions.
      * **Administration:** Read and write

        > \[!NOTE]
        > `Administration: Read and write` is only required when configuring Actions Runner Controller to register at the repository scope. It is not required to register at the organization scope.

      * **Metadata:** Read-only

   3. Under "Permissions," click **Organization permissions**. Then use the dropdown menus to select the following access permissions.
      * **Self-hosted runners:** Read and write

2. After creating the GitHub App, on the GitHub App's page, note the value for "App ID". You will use this value later.

3. Under "Private keys", click **Generate a private key**, and save the `.pem` file. You will use this key later.

4. In the menu at the top-left corner of the page, click **Install app**, and next to your organization, click **Install** to install the app on your organization.

5. After confirming the installation permissions on your organization, note the app installation ID. You will use it later. You can find the app installation ID on the app installation page, which has the following URL format:

   `https://github.com/organizations/ORGANIZATION/settings/installations/INSTALLATION_ID`

6. Register the app ID, installation ID, and the downloaded `.pem` private key file from the previous steps to Kubernetes as a secret.

   To create a Kubernetes secret with the values of your GitHub App, run the following command.

   > \[!NOTE]
   > Create the secret in the same namespace where the `gha-runner-scale-set` chart is installed. In this example, the namespace is `arc-runners` to match the quickstart documentation. For more information, see [Get started with Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/quickstart-for-actions-runner-controller#configuring-a-runner-scale-set).

   ```bash copy
   kubectl create secret generic pre-defined-secret \
      --namespace=arc-runners \
      --from-literal=github_app_id=123456 \
      --from-literal=github_app_installation_id=654321 \
      --from-literal=github_app_private_key='-----BEGIN RSA PRIVATE KEY-----********'
   ```

   Then using the `githubConfigSecret` property in your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file, pass the secret name as a reference.

   ```yaml
   githubConfigSecret: pre-defined-secret
   ```

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

## Authenticating ARC with a personal access token (classic)

ARC can use personal access tokens (classic) to register self-hosted runners.

1. Create a personal access token (classic) with the required scopes. The required scopes are different depending on whether you are registering runners at the repository or organization level. For more information on how to create a personal access token (classic), see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-personal-access-token-classic).

   The following is the list of required personal access token scopes for ARC runners.

   * Repository runners: `repo`
   * Organization runners: `admin:org`

2. To create a Kubernetes secret with the value of your personal access token (classic), use the following command.

   > \[!NOTE]
   > Create the secret in the same namespace where the `gha-runner-scale-set` chart is installed. In this example, the namespace is `arc-runners` to match the quickstart documentation. For more information, see [Get started with Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/quickstart-for-actions-runner-controller#configuring-a-runner-scale-set).

   ```bash copy
   kubectl create secret generic pre-defined-secret \
      --namespace=arc-runners \
      --from-literal=github_token='YOUR-PAT'
   ```

3. In your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file, pass the secret name as a reference.

   ```yaml
   githubConfigSecret: pre-defined-secret
   ```

   For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

## Authenticating ARC with a fine-grained personal access token

ARC can use fine-grained personal access tokens to register self-hosted runners.

1. Create a fine-grained personal access token with the required scopes. The required scopes are different depending on whether you are registering runners at the repository or organization level. For more information on how to create a fine-grained personal access token, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-fine-grained-personal-access-token).

   The following is the list of required personal access token scopes for ARC runners.

   * Repository runners:
     * **Administration:** Read and write

   * Organization runners:
     * **Administration:** Read
     * **Self-hosted runners:** Read and write

2. To create a Kubernetes secret with the value of your fine-grained personal access token, use the following command.

   > \[!NOTE]
   > Create the secret in the same namespace where the `gha-runner-scale-set` chart is installed. In this example, the namespace is `arc-runners` to match the quickstart documentation. For more information, see [Get started with Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/quickstart-for-actions-runner-controller#configuring-a-runner-scale-set).

   ```bash copy
   kubectl create secret generic pre-defined-secret \
      --namespace=arc-runners \
      --from-literal=github_token='YOUR-PAT'
   ```

3. In your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file, pass the secret name as a reference.

   ```yaml
   githubConfigSecret: pre-defined-secret
   ```

   For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

## Authenticating ARC with vault secrets

> \[!NOTE]
> Vault integration is currently available in public preview with support for Azure Key Vault.

Starting with gha-runner-scale-set version 0.12.0, ARC supports retrieving GitHub credentials from an external vault. Vault integration is configured per runner scale set. This means you can run some scale sets using Kubernetes secrets while others use vault-based secrets, depending on your security and operational requirements.

### Enabling Vault Integration

To enable vault integration for a runner scale set:

1. **Set the `githubConfigSecret` field** in your `values.yaml` file to the name of the secret key stored in your vault. This value must be a string.
2. **Uncomment and configure the `keyVault` section** in your `values.yaml` file with the appropriate provider and access details.
3. **Provide the required certificate** (`.pfx`) to both the controller and the listener. You can do this by:
   \*Rebuilding the controller image with the certificate included, or
   \*Mounting the certificate as a volume in both the controller and the listener using the `listenerTemplate` and `controllerManager` fields.

### Secret Format

The secret stored in Azure Key Vault must be in JSON format. The structure depends on the type of authentication you are using:

#### Example: GitHub Token

```json
{
  "github_token": "TOKEN"
}
```

#### Example: GitHub App

```json
{
  "github_app_id": "APP_ID_OR_CLIENT_ID",
  "github_app_installation_id": "INSTALLATION_ID",
  "github_app_private_key": "PRIVATE_KEY"
}
```

### Configuring `values.yaml` for Vault Integration

The certificate is stored as a .pfx file and mounted to the container at /akv/cert.pfx. Below is an example of how to configure the keyVault section to use this certificate for authentication:

```yaml
keyVault:
  type: "azure_key_vault"
  proxy:
    https:
      url: "PROXY_URL"
      credentialSecretRef: "PROXY_CREDENTIALS_SECRET_NAME"
    http: {}
    noProxy: []
  azureKeyVault:
    clientId: <AZURE_CLIENT_ID>
    tenantId: <AZURE_TENANT_ID>
    url: <AZURE_VAULT_URL>
    certificatePath: "/akv/cert.pfx"
```

### Providing the Certificate to the Controller and Listener

ARC requires a `.pfx` certificate to authenticate with the vault. This certificate must be made available to both the controller and the listener components during controller installation.
You can do this by mounting the certificate as a volume using the `controllerManager` and `listenerTemplate` fields in your `values.yaml` file:

```yaml
volumes:
  - name: cert-volume
    secret:
      secretName: my-cert-secret
volumeMounts:
  - mountPath: /akv
    name: cert-volume
    readOnly: true

listenerTemplate:
  volumeMounts:
    - name: cert-volume
      mountPath: /akv/certs
      readOnly: true
  volumes:
    - name: cert-volume
      secret:
        secretName: my-cert-secret
```

The code below is an example of a scale set `values.yml` file.

```yaml
listenerTemplate:
  spec:
    containers:
      - name: listener
        volumeMounts:
          - name: cert-volume
            mountPath: /akv
            readOnly: true
    volumes:
      - name: cert-volume
        secret:
          secretName: my-cert-secret
```

## Legal notice

Portions have been adapted from <https://github.com/actions/actions-runner-controller/> under the Apache-2.0 license:

```text
Copyright 2019 Moto Ishizawa

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```