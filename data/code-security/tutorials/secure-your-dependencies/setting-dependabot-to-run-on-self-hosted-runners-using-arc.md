# Setting up Dependabot to run on self-hosted action runners using the Actions Runner Controller

You can configure the Actions Runner Controller to run Dependabot on self-hosted runners.

## Working with the Actions Runner Controller (ARC)

This article provides step-by-step instructions for setting up ARC on a Kubernetes cluster and configuring Dependabot to run on self-hosted action runners. The article:

* Contains an overview of the ARC and Dependabot integration.
* Provides detailed installation and configuration steps using helm scripts.

## What is ARC?

The Actions Runner Controller is a Kubernetes controller that manages self-hosted GitHub Actions as Kubernetes pods. It allows you to dynamically scale and orchestrate runners based on your workflows, providing better resource utilization and integration with Kubernetes environments. See [Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/about-actions-runner-controller).

## Dependabot on ARC

You can run Dependabot on self-hosted GitHub Actions runners managed within a Kubernetes cluster via ARC. This enables auto-scaling, workload isolation, and better resource management for Dependabot jobs, ensuring that dependency updates can run efficiently within an organization's controlled infrastructure while integrating seamlessly with GitHub Actions.

## Setting up ARC for Dependabot on your Local environment

### Prerequisites

* A Kubernetes cluster
  * For a managed cloud environment, you can use Azure Kubernetes Service (AKS).
  * For a local setup, you can use minikube.
* Helm
  * A package manager for Kubernetes.

### Setting up ARC

1. Install ARC. For more information, see [Get started with Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/quickstart-for-actions-runner-controller).

2. Create a work directory for the ARC setup and create a shell script file (for example, `helm_install_arc.sh`) to install the latest ARC version.

   ```bash copy
       mkdir ARC
       touch helm_install_arc.sh
       chmod 755 helm_install_arc.sh
   ```

3. Edit `helm_install_arc.sh` with this bash script for installing ARC.

   ```text copy
   NAMESPACE="arc-systems"
   helm install arc \
       --namespace "${NAMESPACE}" \
       --create-namespace \
       oci://ghcr.io/actions/actions-runner-controller-charts/gha-runner-scale-set-controller
   ```

4. Execute the `helm_install_arc.sh` script file.

   ```bash
   ./helm_install_arc.sh
   ```

5. Now, you need to configure the runner scale set. For this, let's start by creating and editing a file with the following bash script.

   ```bash copy
   touch arc-runner-set.sh
   chmod 755 arc-runner-set.sh
   ```

   ```text copy
   INSTALLATION_NAME="dependabot"
   NAMESPACE="arc-runners"
   GITHUB_CONFIG_URL=REPO_URL
   GITHUB_PAT=PAT
   helm install "${INSTALLATION_NAME}" \
       --namespace "${NAMESPACE}" \
       --create-namespace \
       --set githubConfigUrl="${GITHUB_CONFIG_URL}" \
       --set githubConfigSecret.github_token="${GITHUB_PAT}" \
       --set containerMode.type="dind" \
       oci://ghcr.io/actions/actions-runner-controller-charts/gha-runner-scale-set
   ```

6. Execute the `arc-runner-set.sh` script file.

   ```bash copy
   ./arc-runner-set.sh
   ```

> \[!NOTE]
>
> * The installation name of the runner scale set has to be `dependabot` in order to target the dependabot job to the runner.
> * The `containerMode.type="dind"` configuration is required to allow the runner to connect to the Docker daemon.
> * If an organization-level or enterprise-level runner is created, then the appropriate scopes should be provided to the Personal Access Token (PAT).
> * A personal access token (classic) (PAT) can be created. The token should have the following scopes based on whether you are creating a repository, organization or enterprise level runner scale set.
>   * Repository level: **repo**
>   * Organization level: **admin:org**
>   * Enterprise level: **admin:enterprise**\
>     For information about creating a personal access token (classic), see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

### Adding runner groups

Runner groups are used to control which organizations or repositories have access to runner scale sets. To add a runner scale set to a runner group, you must already have a runner group created.

For information about creating runner groups, see [Managing access to self-hosted runners using groups](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/managing-access-to-self-hosted-runners-using-groups#creating-a-self-hosted-runner-group-for-an-organization).

Don't forget to add the following setting to the runner scale set configuration in the helm chart.

```text copy
--set runnerGroup="<Runner group name>" \
```

### Checking your installation

1. Check your installation.

   ```bash copy
   helm list -A
   ```

   Output:

   ```text
   ➜  ARC git:(master) ✗ helm list -A
       NAME           NAMESPACE   REVISION UPDATED                              STATUS   CHART                                  APP VERSION
       arc            arc-systems 1        2025-04-11 14:41:53.70893 -0500 CDT  deployed gha-runner-scale-set-controller-0.11.0 0.11.0
       arc-runner-set arc-runners 1        2025-04-11 15:08:12.58119 -0500 CDT  deployed gha-runner-scale-set-0.11.0            0.11.0
       dependabot     arc-runners 1        2025-04-16 21:53:40.080772 -0500 CDT deployed gha-runner-scale-set-0.11.0
   ```

2. Check the manager pod using this command.

   ```bash copy
   kubectl get pods -n arc-systems
   ```

   Output:

   ```text
   ➜  ARC git:(master) ✗ kubectl get pods -n arc-systems

   NAME                                    READY   STATUS    RESTARTS      AGE
   arc-gha-rs-controller-57c67d4c7-zjmw2   1/1     Running   8 (36h ago)   6d9h
   arc-runner-set-754b578d-listener        1/1     Running   0             11h
   dependabot-754b578d-listener            1/1     Running   0             14h
   ```

### Setting up Dependabot

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)

3. In the "Security" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced Security**.

4. Under "Dependabot", scroll to "Dependabot on Action Runners", and select **Enable** for "Dependabot on self-hosted runners".

## Triggering a Dependabot run

Now that you've set up ARC, you can start a Dependabot run.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights** tab.

3. In the left sidebar, click **Dependency graph**.
   ![Screenshot of the "Dependency graph" tab. The tab is highlighted with an orange outline.](/assets/images/help/graphs/graphs-sidebar-dependency-graph.png)

4. Under "Dependency graph", click **Dependabot**.

5. To the right of the name of manifest file you're interested in, click **Recent update jobs**.

6. If there are no recent update jobs for the manifest file, click **Check for updates** to re-run a Dependabot version updates'job and check for new updates to dependencies for that ecosystem.

## Viewing the generated ARC runners

You can view the ARC runners that have been created for the Dependabot job.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)

3. On the left sidebar, click **Runners**.

4. Under "Runners", click **Self-hosted runners** to view the list of all the runners available in the repository. You can see the ephemeral dependabot runner that has been created.
   ![Screenshot showing a dependabot runner in the list of available runners. The runner is highlighted with an orange outline.](/assets/images/help/dependabot/dependabot-self-hosted-runner.png)

   You can also view the same dependabot runner pod created in your kubernetes cluster from the terminal by executing this command.

   ```text copy
   ➜  ARC git:(master) ✗ kubectl get pods -n arc-runners
       NAME                            READY   STATUS    RESTARTS   AGE
       dependabot-sw8zn-runner-4mbc7   2/2     Running   0          46s
   ```

Additionally, you can verify:

* The logs, by checking the runner and machine name. See [Viewing Dependabot job logs](/en/code-security/dependabot/troubleshooting-dependabot/viewing-dependabot-job-logs).

  ![Example of log for a dependabot self hosted runner.](/assets/images/help/dependabot/dependabot-self-hosted-runner-log.png)

* The version update pull requests created by the dependabot job in the **Pull requests** tab of the repository.