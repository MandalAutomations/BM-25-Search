# Deploying runner scale sets with Actions Runner Controller

Deploy runner scale sets with Actions Runner Controller, and use advanced configuration options to tailor Actions Runner Controller to your needs.

## Deploying a runner scale set

To deploy a runner scale set, you must have ARC up and running. For more information, see [Get started with Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/quickstart-for-actions-runner-controller).

You can deploy runner scale sets with ARC's Helm charts or by deploying the necessary manifests. Using ARC's Helm charts is the preferred method, especially if you do not have prior experience using ARC.

> \[!NOTE]
>
> * As a security best practice, create your runner pods in a different namespace than the namespace containing your operator pods.
> * As a security best practice, create Kubernetes secrets and pass the secret references. Passing your secrets in plain text via the CLI can pose a security risk.
> * We recommend running production workloads in isolation. GitHub Actions workflows are designed to run arbitrary code, and using a shared Kubernetes cluster for production workloads could pose a security risk.
> * Ensure you have implemented a way to collect and retain logs from the controller, listeners, and ephemeral runners.

1. To configure your runner scale set, run the following command in your terminal, using values from your ARC configuration.

   When you run the command, keep the following in mind.

   * Update the `INSTALLATION_NAME` value carefully. You can use the installation name as the value of [`runs-on`](/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idruns-on) in your workflows.
   * Update the `NAMESPACE` value to the location you want the runner pods to be created.
   * Set the `GITHUB_CONFIG_URL` value to the URL of your repository, organization, or enterprise. This is the entity that the runners will belong to.
   * This example command installs the latest version of the Helm chart. To install a specific version, you can pass the `--version` argument with the version of the chart you want to install. You can find the list of releases in the [`actions-runner-controller`](https://github.com/actions/actions-runner-controller/pkgs/container/actions-runner-controller-charts%2Fgha-runner-scale-set) repository.

     ```bash copy
     INSTALLATION_NAME="arc-runner-set"
     NAMESPACE="arc-runners"
     GITHUB_CONFIG_URL="https://github.com/<your_enterprise/org/repo>"
     GITHUB_PAT="<PAT>"
     helm install "${INSTALLATION_NAME}" \
         --namespace "${NAMESPACE}" \
         --create-namespace \
         --set githubConfigUrl="${GITHUB_CONFIG_URL}" \
         --set githubConfigSecret.github_token="${GITHUB_PAT}" \
         oci://ghcr.io/actions/actions-runner-controller-charts/gha-runner-scale-set
     ```

     For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

2. To check your installation, run the following command in your terminal.

   ```bash copy
   helm list -A
   ```

   You should see an output similar to the following.

   ```bash
   NAME            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                                       APP VERSION
   arc             arc-systems     1               2023-04-12 11:45:59.152090536 +0000 UTC deployed        gha-runner-scale-set-controller-0.4.0       0.4.0
   arc-runner-set  arc-systems     1               2023-04-12 11:46:13.451041354 +0000 UTC deployed        gha-runner-scale-set-0.4.0                  0.4.0
   ```

3. To check the manager pod, run the following command in your terminal.

   ```bash copy
   kubectl get pods -n arc-systems
   ```

   If the installation was successful, the pods will show the `Running` status.

   ```bash
   NAME                                                   READY   STATUS    RESTARTS   AGE
   arc-gha-runner-scale-set-controller-594cdc976f-m7cjs   1/1     Running   0          64s
   arc-runner-set-754b578d-listener                       1/1     Running   0          12s
   ```

If your installation was not successful, see [Troubleshooting Actions Runner Controller errors](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/troubleshooting-actions-runner-controller-errors) for troubleshooting information.

## Using advanced configuration options

ARC offers several advanced configuration options.

### Configuring the runner scale set name

> \[!NOTE]
> Runner scale set names are unique within the runner group they belong to. If you want to deploy multiple runner scale sets with the same name, they must belong to different runner groups.

To configure the runner scale set name, you can define an `INSTALLATION_NAME` or set the value of `runnerScaleSetName` in your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file.

```yaml
## The name of the runner scale set to create, which defaults to the Helm release name
runnerScaleSetName: "my-runners"
```

Make sure to pass the `values.yaml` file in your `helm install` command. See the [Helm Install](https://helm.sh/docs/helm/helm_install/) documentation for more details.

### Choosing runner destinations

Runner scale sets can be deployed at the repository, organization, or enterprise levels.

To deploy runner scale sets to a specific level, set the value of `githubConfigUrl` in your copy of the `values.yaml` to the URL of your repository, organization, or enterprise.

The following example shows how to configure ARC to add runners to `octo-org/octo-repo`.

```yaml
githubConfigUrl: "https://github.com/octo-ent/octo-org/octo-repo"
```

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

### Using a GitHub App for authentication

If you are not using enterprise-level runners, you can use GitHub Apps to authenticate with the GitHub API. For more information, see [Authenticating ARC to the GitHub API](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/authenticating-to-the-github-api).

> \[!NOTE]
> Given the security risk associated with exposing your private key in plain text in a file on disk, we recommend creating a Kubernetes secret and passing the reference instead.

You can either create a Kubernetes secret, or specify values in your [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file.

#### Option 1: Create a Kubernetes secret (recommended)

Once you have created your GitHub App, create a Kubernetes secret and pass the reference to that secret in your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file.

> \[!NOTE]
> Create the secret in the same namespace where the `gha-runner-scale-set` chart is installed. In this example, the namespace is `arc-runners` to match the quickstart documentation. For more information, see [Get started with Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/quickstart-for-actions-runner-controller#configuring-a-runner-scale-set).

```bash
kubectl create secret generic pre-defined-secret \
  --namespace=arc-runners \
  --from-literal=github_app_id=123456 \
  --from-literal=github_app_installation_id=654321 \
  --from-file=github_app_private_key=private-key.pem
```

In your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) pass the secret name as a reference.

```yaml
githubConfigSecret: pre-defined-secret
```

#### Option 2: Specify values in your `values.yaml` file

Alternatively, you can specify the values of `app_id`, `installation_id` and `private_key` in your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file.

```yaml
## githubConfigSecret is the Kubernetes secret to use when authenticating with GitHub API.
## You can choose to use a GitHub App or a personal access token (classic)
githubConfigSecret:
  ## GitHub Apps Configuration
  ## IDs must be strings, use quotes
  github_app_id: "123456"
  github_app_installation_id: "654321"
  github_app_private_key: |
    -----BEGIN RSA PRIVATE KEY-----
    ...
    HkVN9...
    ...
    -----END RSA PRIVATE KEY-----
```

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

### Managing access with runner groups

You can use runner groups to control which organizations or repositories have access to your runner scale sets. For more information on runner groups, see [Managing access to self-hosted runners using groups](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups).

To add a runner scale set to a runner group, you must already have a runner group created. Then set the `runnerGroup` property in your copy of the `values.yaml` file. The following example adds a runner scale set to the Octo-Group runner group.

```yaml
runnerGroup: "Octo-Group"
```

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

### Configuring an outbound proxy

To force HTTP traffic for the controller and runners to go through your outbound proxy, set the following properties in your Helm chart.

```yaml
proxy:
  http:
    url: http://proxy.com:1234
    credentialSecretRef: proxy-auth # a Kubernetes secret with `username` and `password` keys
  https:
    url: http://proxy.com:1234
    credentialSecretRef: proxy-auth # a Kubernetes secret with `username` and `password` keys
  noProxy:
    - example.com
    - example.org
```

ARC supports using anonymous or authenticated proxies. If you use authenticated proxies, you will need to set the `credentialSecretRef` value to reference a Kubernetes secret. You can create a secret with your proxy credentials with the following command.

> \[!NOTE]
> Create the secret in the same namespace where the `gha-runner-scale-set` chart is installed. In this example, the namespace is `arc-runners` to match the quickstart documentation. For more information, see [Get started with Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/quickstart-for-actions-runner-controller#configuring-a-runner-scale-set).

```bash copy
  kubectl create secret generic proxy-auth \
    --namespace=arc-runners \
    --from-literal=username=proxyUsername \
    --from-literal=password=proxyPassword \
```

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

### Setting the maximum and minimum number of runners

The `maxRunners` and `minRunners` properties provide you with a range of options to customize your ARC setup.

> \[!NOTE]
> ARC does not support scheduled maximum and minimum configurations. You can use a cron job or any other scheduling solution to update the configuration on a schedule.

#### Example: Unbounded number of runners

If you comment out both the `maxRunners` and `minRunners` properties, ARC will scale up to the number of jobs assigned to the runner scale set and will scale down to 0 if there aren't any active jobs.

```yaml
## maxRunners is the max number of runners the auto scaling runner set will scale up to.
# maxRunners: 0

## minRunners is the min number of idle runners. The target number of runners created will be
## calculated as a sum of minRunners and the number of jobs assigned to the scale set.
# minRunners: 0
```

#### Example: Minimum number of runners

You can set the `minRunners` property to any number and ARC will make sure there is always the specified number of runners active and available to take jobs assigned to the runner scale set at all times.

```yaml
## maxRunners is the max number of runners the auto scaling runner set will scale up to.
# maxRunners: 0

## minRunners is the min number of idle runners. The target number of runners created will be
## calculated as a sum of minRunners and the number of jobs assigned to the scale set.
minRunners: 20
```

#### Example: Set maximum and minimum number of runners

In this configuration, Actions Runner Controller will scale up to a maximum of `30` runners and will scale down to `20` runners when the jobs are complete.

> \[!NOTE]
> The value of `minRunners` can never exceed that of `maxRunners`, unless `maxRunners` is commented out.

```yaml
## maxRunners is the max number of runners the auto scaling runner set will scale up to.
maxRunners: 30

## minRunners is the min number of idle runners. The target number of runners created will be
## calculated as a sum of minRunners and the number of jobs assigned to the scale set.
minRunners: 20
```

#### Example: Jobs queue draining

In certain scenarios you might want to drain the jobs queue to troubleshoot a problem or to perform maintenance on your cluster. If you set both properties to `0`, Actions Runner Controller will not create new runner pods when new jobs are available and assigned.

```yaml
## maxRunners is the max number of runners the auto scaling runner set will scale up to.
maxRunners: 0

## minRunners is the min number of idle runners. The target number of runners created will be
## calculated as a sum of minRunners and the number of jobs assigned to the scale set.
minRunners: 0
```

### Custom TLS certificates

> \[!NOTE]
> If you are using a custom runner image that is not based on the `Debian` distribution, the following instructions will not work.

Some environments require TLS certificates that are signed by a custom certificate authority (CA). Since the custom certificate authority certificates are not bundled with the controller or runner containers, you must inject them into their respective trust stores.

```yaml
githubServerTLS:
  certificateFrom:
    configMapKeyRef:
      name: config-map-name
      key: ca.crt
  runnerMountPath: /usr/local/share/ca-certificates/
```

When you do this, ensure you are using the Privacy Enhanced Mail (PEM) format and that the extension of your certificate is `.crt`. Anything else will be ignored.

The controller executes the following actions.

* Creates a `github-server-tls-cert` volume containing the certificate specified in `certificateFrom`.
* Mounts that volume on path `runnerMountPath/<certificate name>`.
* Sets the `NODE_EXTRA_CA_CERTS` environment variable to that same path.
* Sets the `RUNNER_UPDATE_CA_CERTS` environment variable to `1` (as of version `2.303.0`, this will instruct the runner to reload certificates on the host).

ARC observes values set in the runner pod template and does not overwrite them.

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

### Using a private container registry

> \[!WARNING]
> This Actions Runner Controller customization option may be outside the scope of what GitHub Support can assist with and may cause unexpected behavior when configured incorrectly.
>
> For more information about what GitHub Support can assist with, see [Support for Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/about-support-for-actions-runner-controller).

To use a private container registry, you can copy the controller image and runner image to your private container registry. Then configure the links to those images and set the `imagePullPolicy` and `imagePullSecrets` values.

#### Configuring the controller image

You can update your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set-controller/values.yaml) file and set the `image` properties as follows.

```yaml
image:
  repository: "custom-registry.io/gha-runner-scale-set-controller"
  pullPolicy: IfNotPresent
  # Overrides the image tag whose default is the chart appVersion.
  tag: "0.4.0"

imagePullSecrets:
  - name: <registry-secret-name>
```

The listener container inherits the `imagePullPolicy` defined for the controller.

#### Configuring the runner image

You can update your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file and set the `template.spec` properties to configure the runner pod for your specific use case.

> \[!NOTE]
> The runner container must be named `runner`. Otherwise, it will not be configured properly to connect to GitHub.

The following is a sample configuration:

```yaml
template:
  spec:
    containers:
      - name: runner
        image: "custom-registry.io/actions-runner:latest"
        imagePullPolicy: Always
        command: ["/home/runner/run.sh"]
    imagePullSecrets:
      - name: <registry-secret-name>
```

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

### Updating the pod specification for the runner pod

> \[!WARNING]
> This Actions Runner Controller customization option may be outside the scope of what GitHub Support can assist with and may cause unexpected behavior when configured incorrectly.
>
> For more information about what GitHub Support can assist with, see [Support for Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/about-support-for-actions-runner-controller).

You can fully customize the PodSpec of the runner pod and the controller will apply the configuration you specify. The following is an example pod specification.

```yaml
template:
  spec:
    containers:
      - name: runner
        image: ghcr.io/actions/actions-runner:latest
        command: ["/home/runner/run.sh"]
        resources:
          limits:
            cpu: 500m
            memory: 512Mi
        securityContext:
          readOnlyRootFilesystem: true
          allowPrivilegeEscalation: false
          capabilities:
            add:
              - NET_ADMIN
```

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

### Updating the pod specification for the listener pod

> \[!WARNING]
> This Actions Runner Controller customization option may be outside the scope of what GitHub Support can assist with and may cause unexpected behavior when configured incorrectly.
>
> For more information about what GitHub Support can assist with, see [Support for Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/about-support-for-actions-runner-controller).

You can customize the PodSpec of the listener pod and the controller will apply the configuration you specify. The following is an example pod specification.

> \[!NOTE]
> It's important to not change the `listenerTemplate.spec.containers.name` value of the listener container. Otherwise, the configuration you specify will be applied to a new sidecar container.

```yaml
listenerTemplate:
  spec:
    containers:
    # If you change the name of the container, the configuration will not be applied to the listener,
    # and it will be treated as a sidecar container.
    - name: listener
      securityContext:
        runAsUser: 1000
      resources:
        limits:
          cpu: "1"
          memory: 1Gi
        requests:
          cpu: "1"
          memory: 1Gi
```

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

## Using Docker-in-Docker or Kubernetes mode for containers

> \[!WARNING]
> This Actions Runner Controller customization option may be outside the scope of what GitHub Support can assist with and may cause unexpected behavior when configured incorrectly.
>
> For more information about what GitHub Support can assist with, see [Support for Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/about-support-for-actions-runner-controller).

If you are using container jobs and services or container actions, you must set the `containerMode` value to `dind` or `kubernetes`. To use a custom container mode, comment out or remove `containerMode`, and add your desired configuration to the `template` section. See [Customizing container modes](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/deploying-runner-scale-sets-with-actions-runner-controller#customizing-container-modes).

* For more information on container jobs and services, see [Running jobs in a container](/en/actions/using-jobs/running-jobs-in-a-container).
* For more information on container actions, see [Creating a Docker container action](/en/actions/creating-actions/creating-a-docker-container-action).

### Using Docker-in-Docker mode

> \[!NOTE]
> The Docker-in-Docker container requires privileged mode. For more information, see [Configure a Security Context for a Pod or Container](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/) in the Kubernetes documentation.
>
> By default, the `dind` container uses the `docker:dind` image, which runs the Docker daemon as root. You can replace this image with `docker:dind-rootless` as long as you are aware of the [known limitations](https://docs.docker.com/engine/security/rootless/#known-limitations) and run the pods with `--privileged` mode. To learn how to customize the Docker-in-Docker configuration, see [Customizing container modes](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/deploying-runner-scale-sets-with-actions-runner-controller#customizing-container-modes).

Docker-in-Docker mode is a configuration that allows you to run Docker inside a Docker container. In this configuration, for each runner pod created, ARC creates the following containers.

* An `init` container
* A `runner` container
* A `dind` container

To enable Docker-in-Docker mode, set the `containerMode.type` to `dind` as follows.

```yaml
containerMode:
  type: "dind"
```

The `template.spec` will be updated to the following default configuration.

For versions of Kubernetes `>= v1.29`, sidecar container will be used to run docker daemon.

```yaml
template:
  spec:
    initContainers:
      - name: init-dind-externals
        image: ghcr.io/actions/actions-runner:latest
        command: ["cp", "-r", "/home/runner/externals/.", "/home/runner/tmpDir/"]
        volumeMounts:
          - name: dind-externals
            mountPath: /home/runner/tmpDir
      - name: dind
        image: docker:dind
        args:
          - dockerd
          - --host=unix:///var/run/docker.sock
          - --group=$(DOCKER_GROUP_GID)
        env:
          - name: DOCKER_GROUP_GID
            value: "123"
        securityContext:
          privileged: true
        restartPolicy: Always
        startupProbe:
          exec:
            command:
              - docker
              - info
          initialDelaySeconds: 0
          failureThreshold: 24
          periodSeconds: 5
        volumeMounts:
          - name: work
            mountPath: /home/runner/_work
          - name: dind-sock
            mountPath: /var/run
          - name: dind-externals
            mountPath: /home/runner/externals
    containers:
      - name: runner
        image: ghcr.io/actions/actions-runner:latest
        command: ["/home/runner/run.sh"]
        env:
          - name: DOCKER_HOST
            value: unix:///var/run/docker.sock
          - name: RUNNER_WAIT_FOR_DOCKER_IN_SECONDS
            value: "120"
        volumeMounts:
          - name: work
            mountPath: /home/runner/_work
          - name: dind-sock
            mountPath: /var/run
    volumes:
      - name: work
        emptyDir: {}
      - name: dind-sock
        emptyDir: {}
      - name: dind-externals
        emptyDir: {}
```

For versions of Kubernetes `< v1.29`, the following configuration will be applied:

```yaml
template:
  spec:
    initContainers:
      - name: init-dind-externals
        image: ghcr.io/actions/actions-runner:latest
        command:
          ["cp", "-r", "/home/runner/externals/.", "/home/runner/tmpDir/"]
        volumeMounts:
          - name: dind-externals
            mountPath: /home/runner/tmpDir
    containers:
      - name: runner
        image: ghcr.io/actions/actions-runner:latest
        command: ["/home/runner/run.sh"]
        env:
          - name: DOCKER_HOST
            value: unix:///var/run/docker.sock
        volumeMounts:
          - name: work
            mountPath: /home/runner/_work
          - name: dind-sock
            mountPath: /var/run
      - name: dind
        image: docker:dind
        args:
          - dockerd
          - --host=unix:///var/run/docker.sock
          - --group=$(DOCKER_GROUP_GID)
        env:
          - name: DOCKER_GROUP_GID
            value: "123"
        securityContext:
          privileged: true
        volumeMounts:
          - name: work
            mountPath: /home/runner/_work
          - name: dind-sock
            mountPath: /var/run
          - name: dind-externals
            mountPath: /home/runner/externals
    volumes:
      - name: work
        emptyDir: {}
      - name: dind-sock
        emptyDir: {}
      - name: dind-externals
        emptyDir: {}
```

The values in `template.spec` are automatically injected and cannot be overridden. If you want to customize this setup, you must unset `containerMode.type`, then copy this configuration and apply it directly in your copy of the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file.

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

### Using Kubernetes mode

In Kubernetes mode, ARC uses runner container hooks to create a new pod in the same namespace to run the service, container job, or action.

#### Prerequisites

Kubernetes mode supports two approaches for sharing job data between the runner pod and the container job pod. You can use persistent volumes, which remain the recommended option for scenarios requiring concurrent write access, or you can use container lifecycle hooks to restore and export job filesystems between pods without relying on RWX volumes. The lifecycle hook approach improves portability and performance by leveraging local storage and is ideal for clusters without shared storage.

#### Configuring Kubernetes mode with persistent volumes

To use Kubernetes mode, you must create persistent volumes that the runner pods can claim and use a solution that automatically provisions these volumes on demand. For testing, you can use a solution like [OpenEBS](https://github.com/openebs/openebs).

To enable Kubernetes mode, set the `containerMode.type` to `kubernetes` in your [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) file.

```yaml
containerMode:
  type: "kubernetes"
  kubernetesModeWorkVolumeClaim:
    accessModes: ["ReadWriteOnce"]
    storageClassName: "dynamic-blob-storage"
    resources:
      requests:
        storage: 1Gi
```

For additional Helm configuration options, see [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/values.yaml) in the ARC repository.

#### Configuring Kubernetes mode with container lifecycle hooks

To enable Kubernetes mode using container lifecycle hooks, set the `containerMode.type` to `kubernetes-novolume` in your `values.yaml` file:

```yaml
containerMode:
  type: "kubernetes-novolume"
```

> \[!NOTE]
> When using `kubernetes-novolume` mode, the container must run as `root` to support lifecycle hook operations.

#### Troubleshooting Kubernetes mode

When Kubernetes mode is enabled, workflows that are not configured with a container job will fail with an error similar to:

```bash
Jobs without a job container are forbidden on this runner, please add a 'container:' to your job or contact your self-hosted runner administrator.
```

To allow jobs without a job container to run, set `ACTIONS_RUNNER_REQUIRE_JOB_CONTAINER` to `false` on your runner container. This instructs the runner to disable this check.

> \[!WARNING]
> Allowing jobs to run without a container in `kubernetes` or `kubernetes-novolume` mode can give the >runner pod elevated privileges with the Kubernetes API server, including the ability to create pods and access secrets. Before changing this default, we recommend carefully reviewing the potential security implications.

```yaml
  template:
    spec:
      containers:
        - name: runner
          image: ghcr.io/actions/actions-runner:latest
          command: ["/home/runner/run.sh"]
          env:
            - name: ACTIONS_RUNNER_REQUIRE_JOB_CONTAINER
              value: "false"
```

### Customizing container modes

When you set the `containerMode` in the `values.yaml` file for the [`gha-runner-scale-set` helm chart](https://github.com/actions/actions-runner-controller/blob/5347e2c2c80fbc45be7390eab117e861d30776d1/charts/gha-runner-scale-set/values.yaml#L77), you can use either of the following values:

* `dind` or
* `kubernetes`

Depending on which value you set for the `containerMode`, a configuration will automatically be injected into the `template` section of the `values.yaml` file for the `gha-runner-scale-set` helm chart.

* See the [`dind` configuration](https://github.com/actions/actions-runner-controller/blob/5347e2c2c80fbc45be7390eab117e861d30776d1/charts/gha-runner-scale-set/values.yaml#L110).
* See the [`kubernetes` configuration](https://github.com/actions/actions-runner-controller/blob/5347e2c2c80fbc45be7390eab117e861d30776d1/charts/gha-runner-scale-set/values.yaml#L160).

To customize the spec, comment out or remove `containerMode`, and append the configuration you want in the `template` section.

#### Example: running `dind-rootless`

Before deciding to run `dind-rootless`, make sure you are aware of [known limitations](https://docs.docker.com/engine/security/rootless/#known-limitations).

For versions of Kubernetes >= v1.29, sidecar container will be used to run docker daemon.

```yaml
## githubConfigUrl is the GitHub url for where you want to configure runners
## ex: https://github.com/myorg/myrepo or https://github.com/myorg
githubConfigUrl: "https://github.com/actions/actions-runner-controller"

## githubConfigSecret is the k8s secrets to use when auth with GitHub API.
## You can choose to use GitHub App or a PAT token
githubConfigSecret: my-super-safe-secret

## maxRunners is the max number of runners the autoscaling runner set will scale up to.
maxRunners: 5

## minRunners is the min number of idle runners. The target number of runners created will be
## calculated as a sum of minRunners and the number of jobs assigned to the scale set.
minRunners: 0

runnerGroup: "my-custom-runner-group"

## name of the runner scale set to create. Defaults to the helm release name
runnerScaleSetName: "my-awesome-scale-set"

## template is the PodSpec for each runner Pod
## For reference: https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/pod-v1/#PodSpec
template:
  spec:
    initContainers:
    - name: init-dind-externals
      image: ghcr.io/actions/actions-runner:latest
      command: ["cp", "-r", "/home/runner/externals/.", "/home/runner/tmpDir/"]
      volumeMounts:
        - name: dind-externals
          mountPath: /home/runner/tmpDir
    - name: init-dind-rootless
      image: docker:dind-rootless
      command:
        - sh
        - -c
        - |
          set -x
          cp -a /etc/. /dind-etc/
          echo 'runner:x:1001:1001:runner:/home/runner:/bin/ash' >> /dind-etc/passwd
          echo 'runner:x:1001:' >> /dind-etc/group
          echo 'runner:100000:65536' >> /dind-etc/subgid
          echo 'runner:100000:65536' >> /dind-etc/subuid
          chmod 755 /dind-etc;
          chmod u=rwx,g=rx+s,o=rx /dind-home
          chown 1001:1001 /dind-home
      securityContext:
        runAsUser: 0
      volumeMounts:
        - mountPath: /dind-etc
          name: dind-etc
        - mountPath: /dind-home
          name: dind-home
    - name: dind
      image: docker:dind-rootless
      args:
        - dockerd
        - --host=unix:///run/user/1001/docker.sock
      securityContext:
        privileged: true
        runAsUser: 1001
        runAsGroup: 1001
      restartPolicy: Always
      startupProbe:
        exec:
          command:
            - docker
            - info
        initialDelaySeconds: 0
        failureThreshold: 24
        periodSeconds: 5
      volumeMounts:
        - name: work
          mountPath: /home/runner/_work
        - name: dind-sock
          mountPath: /run/user/1001
        - name: dind-externals
          mountPath: /home/runner/externals
        - name: dind-etc
          mountPath: /etc
        - name: dind-home
          mountPath: /home/runner
    containers:
    - name: runner
      image: ghcr.io/actions/actions-runner:latest
      command: ["/home/runner/run.sh"]
      env:
        - name: DOCKER_HOST
          value: unix:///run/user/1001/docker.sock
      securityContext:
        privileged: true
        runAsUser: 1001
        runAsGroup: 1001
      volumeMounts:
        - name: work
          mountPath: /home/runner/_work
        - name: dind-sock
          mountPath: /run/user/1001
    volumes:
    - name: work
      emptyDir: {}
    - name: dind-externals
      emptyDir: {}
    - name: dind-sock
      emptyDir: {}
    - name: dind-etc
      emptyDir: {}
    - name: dind-home
      emptyDir: {}
```

For versions of Kubernetes `< v1.29`, the following configuration will be applied:

```yaml
## githubConfigUrl is the GitHub url for where you want to configure runners
## ex: https://github.com/myorg/myrepo or https://github.com/myorg
githubConfigUrl: "https://github.com/actions/actions-runner-controller"

## githubConfigSecret is the k8s secrets to use when auth with GitHub API.
## You can choose to use GitHub App or a PAT token
githubConfigSecret: my-super-safe-secret

## maxRunners is the max number of runners the autoscaling runner set will scale up to.
maxRunners: 5

## minRunners is the min number of idle runners. The target number of runners created will be
## calculated as a sum of minRunners and the number of jobs assigned to the scale set.
minRunners: 0

runnerGroup: "my-custom-runner-group"

## name of the runner scale set to create. Defaults to the helm release name
runnerScaleSetName: "my-awesome-scale-set"

## template is the PodSpec for each runner Pod
## For reference: https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/pod-v1/#PodSpec
template:
  spec:
    initContainers:
    - name: init-dind-externals
      image: ghcr.io/actions/actions-runner:latest
      command: ["cp", "-r", "/home/runner/externals/.", "/home/runner/tmpDir/"]
      volumeMounts:
        - name: dind-externals
          mountPath: /home/runner/tmpDir
    - name: init-dind-rootless
      image: docker:dind-rootless
      command:
        - sh
        - -c
        - |
          set -x
          cp -a /etc/. /dind-etc/
          echo 'runner:x:1001:1001:runner:/home/runner:/bin/ash' >> /dind-etc/passwd
          echo 'runner:x:1001:' >> /dind-etc/group
          echo 'runner:100000:65536' >> /dind-etc/subgid
          echo 'runner:100000:65536' >> /dind-etc/subuid
          chmod 755 /dind-etc;
          chmod u=rwx,g=rx+s,o=rx /dind-home
          chown 1001:1001 /dind-home
      securityContext:
        runAsUser: 0
      volumeMounts:
        - mountPath: /dind-etc
          name: dind-etc
        - mountPath: /dind-home
          name: dind-home
    containers:
    - name: runner
      image: ghcr.io/actions/actions-runner:latest
      command: ["/home/runner/run.sh"]
      env:
        - name: DOCKER_HOST
          value: unix:///run/user/1001/docker.sock
      securityContext:
        privileged: true
        runAsUser: 1001
        runAsGroup: 1001
      volumeMounts:
        - name: work
          mountPath: /home/runner/_work
        - name: dind-sock
          mountPath: /run/user/1001
    - name: dind
      image: docker:dind-rootless
      args:
        - dockerd
        - --host=unix:///run/user/1001/docker.sock
      securityContext:
        privileged: true
        runAsUser: 1001
        runAsGroup: 1001
      volumeMounts:
        - name: work
          mountPath: /home/runner/_work
        - name: dind-sock
          mountPath: /run/user/1001
        - name: dind-externals
          mountPath: /home/runner/externals
        - name: dind-etc
          mountPath: /etc
        - name: dind-home
          mountPath: /home/runner
    volumes:
    - name: work
      emptyDir: {}
    - name: dind-externals
      emptyDir: {}
    - name: dind-sock
      emptyDir: {}
    - name: dind-etc
      emptyDir: {}
    - name: dind-home
      emptyDir: {}
```

#### Understanding runner-container-hooks

When the runner detects a workflow run that uses a container job, service container, or Docker action, it will call runner-container-hooks to create a new pod. The runner relies on runner-container-hooks to call the Kubernetes APIs and create a new pod in the same namespace as the runner pod. This newly created pod will be used to run the container job, service container, or Docker action. For more information, see the [`runner-container-hooks`](https://github.com/actions/runner-container-hooks) repository.

#### Configuring hook extensions

As of ARC version 0.4.0, runner-container-hooks support hook extensions. You can use these to configure the pod created by runner-container-hooks. For example, you could use a hook extension to set a security context on the pod. Hook extensions allow you to specify a YAML file that is used to update the [PodSpec](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.26/#podspec-v1-core) of the pod created by runner-container-hooks.

There are two options to configure hook extensions.

* Store in your **custom runner image**. You can store the PodSpec in a YAML file anywhere in your custom runner image. For more information, see [Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/about-actions-runner-controller#creating-your-own-runner-image).
* Store in a **ConfigMap**. You can create a config map with the PodSpec and mount that config map in the runner container. For more information, see [ConfigMaps](https://kubernetes.io/docs/concepts/configuration/configmap/) in the Kubernetes documentation.

> \[!NOTE]
> With both options, you must set the `ACTIONS_RUNNER_CONTAINER_HOOK_TEMPLATE` environment variable in the runner container spec to point to the path of the YAML file mounted in the runner container.

##### Example: Using config map to set securityContext

Create a config map in the same namespace as the runner pods. For example:

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: hook-extension
  namespace: arc-runners
data:
  content: |
    metadata:
      annotations:
        example: "extension"
    spec:
      containers:
        - name: "$job" # Target the job container
          securityContext:
            runAsUser: 1000
```

* The `.metadata.labels` and `metadata.annotations` fields will be appended as is, unless their keys are reserved. You cannot override the `.metadata.name` and `metadata.namespace` fields.
* The majority of the PodSpec fields are applied from the specified template, and will override the values passed from your Helm chart `values.yaml` file.
* If you specify additional volumes they will be appended to the default volumes specified by the runner.
* The `spec.containers` are merged based on the names assigned to them.
  * If the name of the container is `$job`:
    * The `spec.containers.name` and `spec.containers.image` fields are ignored.
    * The `spec.containers.env`, `spec.containers.volumeMounts`, and `spec.containers.ports` fields are appended to the default container spec created by the hook.
    * The rest of the fields are applied as provided.
  * If the name of the container is not `$job`, the fields will be added to the pod definition as they are.

## Enabling metrics

> \[!NOTE]
> Metrics for ARC are available as of version gha-runner-scale-set-0.5.0.

ARC can emit metrics about your runners, your jobs, and time spent on executing your workflows. Metrics can be used to identify congestion, monitor the health of your ARC deployment, visualize usage trends, optimize resource consumption, among many other use cases. Metrics are emitted by the controller-manager and listener pods in Prometheus format. For more information, see [Exposition formats](https://prometheus.io/docs/instrumenting/exposition_formats/) in the Prometheus documentation.

To enable metrics for ARC, configure the `metrics` property in the [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set-controller/values.yaml) file of the `gha-runner-scale-set-controller` chart.

The following is an example configuration.

```yaml
metrics:
  controllerManagerAddr: ":8080"
  listenerAddr: ":8080"
  listenerEndpoint: "/metrics"
```

> \[!NOTE]
> If the `metrics:` object is not provided or is commented out, the following flags will be applied to the controller-manager and listener pods with empty values: `--metrics-addr`, `--listener-metrics-addr`, `--listener-metrics-endpoint`. This will disable metrics for ARC.

Once these properties are configured, your controller-manager and listener pods emit metrics via the listenerEndpoint bound to the ports that you specify in your [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set-controller/values.yaml) file. In the above example, the endpoint is `/metrics` and the port is `:8080`. You can use this endpoint to scrape metrics from your controller-manager and listener pods.

To turn off metrics, update your [`values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set-controller/values.yaml) file by removing or commenting out the `metrics:` object and its properties.

### Available metrics for ARC

The following table shows the metrics emitted by the controller-manager and listener pods.

> \[!NOTE]
> The metrics that the controller-manager emits pertain to the controller runtime and are not owned by GitHub.

| Owner              | Metric                                       | Type      | Description                                                                                                 |
| ------------------ | -------------------------------------------- | --------- | ----------------------------------------------------------------------------------------------------------- |
| controller-manager | gha\_controller\_pending\_ephemeral\_runners | gauge     | Number of ephemeral runners in a pending state                                                              |
| controller-manager | gha\_controller\_running\_ephemeral\_runners | gauge     | Number of ephemeral runners in a running state                                                              |
| controller-manager | gha\_controller\_failed\_ephemeral\_runners  | gauge     | Number of ephemeral runners in a failed state                                                               |
| controller-manager | gha\_controller\_running\_listeners          | gauge     | Number of listeners in a running state                                                                      |
| listener           | gha\_assigned\_jobs                          | gauge     | Number of jobs assigned to the runner scale set                                                             |
| listener           | gha\_running\_jobs                           | gauge     | Number of jobs running or queued to run                                                                     |
| listener           | gha\_registered\_runners                     | gauge     | Number of runners registered by the runner scale set                                                        |
| listener           | gha\_busy\_runners                           | gauge     | Number of registered runners currently running a job                                                        |
| listener           | gha\_min\_runners                            | gauge     | Minimum number of runners configured for the runner scale set                                               |
| listener           | gha\_max\_runners                            | gauge     | Maximum number of runners configured for the runner scale set                                               |
| listener           | gha\_desired\_runners                        | gauge     | Number of runners desired (scale up / down target) by the runner scale set                                  |
| listener           | gha\_idle\_runners                           | gauge     | Number of registered runners not running a job                                                              |
| listener           | gha\_started\_jobs\_total                    | counter   | Total number of jobs started since the listener became ready \[1]                                           |
| listener           | gha\_completed\_jobs\_total                  | counter   | Total number of jobs completed since the listener became ready \[1]                                         |
| listener           | gha\_job\_startup\_duration\_seconds         | histogram | Number of seconds spent waiting for workflow job to get started on the runner owned by the runner scale set |
| listener           | gha\_job\_execution\_duration\_seconds       | histogram | Number of seconds spent executing workflow jobs by the runner scale set                                     |

\[1]: Listener metrics that have the counter type are reset when the listener pod restarts.

## Upgrading ARC

Because there is no support for upgrading or deleting CRDs with Helm, it is not possible to use Helm to upgrade ARC. For more information, see [Custom Resource Definitions](https://helm.sh/docs/chart_best_practices/custom_resource_definitions/#some-caveats-and-explanations) in the Helm documentation. To upgrade ARC to a newer version, you must complete the following steps.

1. Uninstall all installations of `gha-runner-scale-set`.
2. Wait for resources cleanup.
3. Uninstall ARC.
4. If there is a change in CRDs from the version you currently have installed, to the upgraded version, remove all CRDs associated with `actions.github.com` API group.
5. Reinstall ARC again.

For more information, see [Deploying a runner scale set](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/deploying-runner-scale-sets-with-actions-runner-controller#deploying-a-runner-scale-set).

If you would like to upgrade ARC but are concerned about downtime, you can deploy ARC in a high availability configuration to ensure runners are always available. For more information, see [High availability and automatic failover](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/deploying-runner-scale-sets-with-actions-runner-controller#high-availability-and-automatic-failover).

> \[!NOTE]
> Transitioning from the [community supported version of ARC](https://github.com/actions/actions-runner-controller/discussions/2775) to the GitHub supported version is a substantial architectural change. The GitHub supported version involves a redesign of many components of ARC. It is not a minor software upgrade. For these reasons, we recommend testing the new versions in a staging environment that matches your production environment first. This will ensure stability and reliability of the setup before deploying in production.

### Deploying a canary image

You can test features before they are released by using canary releases of the controller-manager container image. Canary images are published with tag format `canary-SHORT_SHA`. For more information, see [`gha-runner-scale-set-controller`](https://github.com/actions/actions-runner-controller/pkgs/container/gha-runner-scale-set-controller) on the Container registry.

> \[!NOTE]
>
> * You must use Helm charts on your local file system.
> * You cannot use the released Helm charts.

1. Update the `tag` in the [gha-runner-scale-set-controller `values.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set-controller/values.yaml) file to: `canary-SHORT_SHA`
2. Update the field `appVersion` in the [`Chart.yaml`](https://github.com/actions/actions-runner-controller/blob/master/charts/gha-runner-scale-set/Chart.yaml) file for `gha-runner-scale-set` to: `canary-SHORT_SHA`
3. Re-install ARC using the updated Helm chart and `values.yaml` files.

## High availability and automatic failover

ARC can be deployed in a high availability (active-active) configuration. If you have two distinct Kubernetes clusters deployed in separate regions, you can deploy ARC in both clusters and configure runner scale sets to use the same `runnerScaleSetName`. In order to do this, each runner scale set must be assigned to a distinct runner group. For example, you can have two runner scale sets each named `arc-runner-set`, as long as one runner scale set belongs to `runner-group-A` and the other runner scale set belongs to `runner-group-B`. For information on assigning runner scale sets to runner groups, see [Managing access to self-hosted runners using groups](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups).

If both runner scale sets are online, jobs assigned to them will be distributed arbitrarily (assignment race). You cannot configure the job assignment algorithm. If one of the clusters goes down, the runner scale set in the other cluster will continue to acquire jobs normally without any intervention or configuration change.

## Using ARC across organizations

A single installation of Actions Runner Controller allows you to configure one or more runner scale sets. These runner scale sets can be registered to a repository, organization, or enterprise. You can also use runner groups to control the permissions boundaries of these runner scale sets.

As a best practice, create a unique namespace for each organization. You could also create a namespace for each runner group or each runner scale set. You can install as many runner scale sets as needed in each namespace. This will provide you the highest levels of isolation and improve your security. You can use GitHub Apps for authentication and define granular permissions for each runner scale set.

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