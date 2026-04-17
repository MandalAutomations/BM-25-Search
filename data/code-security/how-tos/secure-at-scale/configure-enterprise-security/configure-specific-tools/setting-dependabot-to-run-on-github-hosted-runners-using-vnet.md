# Setting up Dependabot to run on github-hosted action runners using the Azure Private Network

You can configure an Azure Virtual Network (VNET) to run Dependabot on GitHub-hosted runners.

## Configuring VNET for Dependabot updates

This article provides step-by-step instructions for running Dependabot on GitHub-hosted runners configured with VNET. The article explains:

* How to create runner groups for your enterprise or organization with a VNET configuration.
* How to create GitHub-hosted runners for Dependabot in the runner group.
* How to enable Dependabot on large runners.
* How to configure Azure VNET firewall IP rules.

To use GitHub-hosted runners with Azure VNET, you first need to configure your Azure resources, then create a private network configuration in GitHub.

## Configuring Azure resources

To learn how to use GitHub-hosted runners with an Azure private network, see [Configuring your Azure resources](/en/enterprise-cloud@latest/admin/configuring-settings/configuring-private-networking-for-hosted-compute-products/configuring-private-networking-for-github-hosted-runners-in-your-enterprise#configuring-your-azure-resources) in the GitHub Enterprise Cloud documentation.

> \[!NOTE]
>
> * The `databaseId` which is required in the script for configuring the Azure resources can refer to any of the following depending on whether you are configuring the resources for an enterprise or an organization:
> * The enterprise slug, which you can identify by looking at the URL for your enterprise, `https://github.com/enterprises/SLUG`, or
> * The login for the organization account, which you can identify by looking at the URL for your organization, `https://github.com/organizations/ORGANIZATION_LOGIN`.
> * The script will return the full payload for the created resource. The `GitHubId` hash value returned in the payload for the created resource is the network settings resource ID you will use in the next steps while setting up a network configuration in  GitHub

## Configuring a VNET-injected runner for Dependabot updates in your enterprise

After configuring your Azure resources, you can use an Azure Virtual Network (VNET) for private networking by creating a network configuration at the organization level. Then, you can associate that network configuration to runner groups.

1. Add a new network configuration for your enterprise. See [Add a new network configuration for your enterprise](/en/enterprise-cloud@latest/admin/configuring-settings/configuring-private-networking-for-hosted-compute-products/configuring-private-networking-for-github-hosted-runners-in-your-enterprise#1-add-a-new-network-configuration-for-your-enterprise) in the GitHub Enterprise Cloud documentation.
2. Create a runner group for the enterprise and select the organizations that you want to run Dependabot updates for. See [Create a runner group for your enterprise](/en/enterprise-cloud@latest/admin/configuring-settings/configuring-private-networking-for-hosted-compute-products/configuring-private-networking-for-github-hosted-runners-in-your-enterprise#2-create-a-runner-group-for-your-enterprise) in the GitHub Enterprise Cloud documentation.
3. Create and add a GitHub-hosted runner to the enterprise runner group. See [Adding a larger runner to an enterprise](/en/enterprise-cloud@latest/actions/using-github-hosted-runners/using-larger-runners/managing-larger-runners#adding-a-larger-runner-to-an-enterprise) in the GitHub Enterprise Cloud documentation. Important points are as follows:
   * The runner name must be **dependabot**

   * Choose a Linux x64 platform.

   * Select the suitable Ubuntu version.

   * When adding your GitHub-hosted runner to a runner group, select the runner group you created in the previous step.
   > \[!NOTE]
   > Naming the GitHub-hosted runner **dependabot** assigns the **dependabot** label to the runner, which enables it to pick up jobs triggered by Dependabot on actions.

<!-- This section is currently only valid for dotcom. It'll need reviewing for GHES 3.18 -->

## Enabling Dependabot for the organization

You now need to enable Dependabot on *self-hosted runners* for your organization in order to enable Dependabot on large runners. See [Enabling or disabling Dependabot on larger runners](/en/code-security/dependabot/working-with-dependabot/about-dependabot-on-github-actions-runners#enabling-or-disabling-dependabot-on-larger-runners).

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)
3. In the "Security" section of the sidebar, select the **Advanced Security** dropdown menu, then click **Global settings**.
4. Under **Dependabot**, select **Dependabot on self-hosted runners**. This step is required, as it ensures that future Dependabot jobs will run on the larger GitHub-hosted runner that has the `dependabot` name.

## Triggering a Dependabot run

Now that you've set up private networking with VNET, you can start a Dependabot run.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights** tab.

3. In the left sidebar, click **Dependency graph**.
   ![Screenshot of the "Dependency graph" tab. The tab is highlighted with an orange outline.](/assets/images/help/graphs/graphs-sidebar-dependency-graph.png)

4. Under "Dependency graph", click **Dependabot**.

5. To the right of the name of manifest file you're interested in, click **Recent update jobs**.

6. If there are no recent update jobs for the manifest file, click **Check for updates** to re-run a Dependabot version updates'job and check for new updates to dependencies for that ecosystem.

## Checking logs and active jobs for Dependabot updates

* You can view the logs of the Dependabot workflow in the **Actions** tab of your repository. Ensure you select the Dependabot job on the left sidebar of the Actions page.

  ![Example of log for a "Dependabot in vnet" workflow. The Dependabot job is highlighted with an orange outline. ](/assets/images/help/dependabot/dependabot-vnet-logs.png)

* You can view the active jobs in the page containing informatuon about the runner. To access that page, click the **Policies** tab for the enterprise, select **Actions** on the left sidebar, click the **Runner group** tab, and select your runner.

  ![Screenshot showing a Dependabot runner's active jobs.](/assets/images/help/dependabot/dependabot-vnet-active-jobs.png)

## Configuring Azure VNET firewall IP rules

If your Azure VNET environment is configured with a firewall with an IP allowlist, you may need to update your list of allowed IP addresses to use the GitHub-hosted runners IP addresses sourced from the meta API endpoint.

* GitHub provides the following public endpoint for its IP ranges:
  > GET <https://api.github.com/meta>

* Copy and paste the following curl command in your terminal or command prompt and replace the placeholder bearer token value with your actual value.

  ```bash copy
        curl -L \
        -H "Accept: application/vnd.github+json" \
        -H "Authorization: Bearer YOUR-TOKEN" \
        -H "X-GitHub-Api-Version: 2022-11-28" \
        https://api.github.com/meta
  ```

* From the response, look for the **actions** key.

  ```bash
      "actions": [ ... ]
  ```

  These are the IP ranges used by GitHub Actions runners, including Dependabot and hosted runners.

* Add these IPs to your firewall allowlist.