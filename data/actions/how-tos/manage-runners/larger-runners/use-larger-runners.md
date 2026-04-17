# Running jobs on larger runners

You can speed up your workflows by configuring them to run on larger runners.

## Running jobs on your runner

<div class="ghd-tool linux">

Once your runner type has been defined, you can update your workflow YAML files to send jobs to your newly created runner instances for processing. You can use runner groups or labels to define where your jobs run.

> \[!NOTE]
> Larger runners are automatically assigned a default label that corresponds to the runner name. You cannot add custom labels to larger runners, but you can use the default labels or the runner's group to send jobs to specific types of runners.

Only owner or administrator accounts can see the runner settings. Non-administrative users can contact the organization owner to find out which runners are enabled. Your organization owner can create new runners and runner groups, as well as configure permissions to specify which repositories can access a runner group. For more information, see [Managing larger runners](/en/actions/using-github-hosted-runners/managing-larger-runners#allowing-repositories-to-access-a-runner-group).

</div>

<div class="ghd-tool windows">

Once your runner type has been defined, you can update your workflow YAML files to send jobs to your newly created runner instances for processing. You can use runner groups or labels to define where your jobs run.

> \[!NOTE]
> Larger runners are automatically assigned a default label that corresponds to the runner name. You cannot add custom labels to larger runners, but you can use the default labels or the runner's group to send jobs to specific types of runners.

Only owner or administrator accounts can see the runner settings. Non-administrative users can contact the organization owner to find out which runners are enabled. Your organization owner can create new runners and runner groups, as well as configure permissions to specify which repositories can access a runner group. For more information, see [Managing larger runners](/en/actions/using-github-hosted-runners/managing-larger-runners#allowing-repositories-to-access-a-runner-group).

</div>

<div class="ghd-tool mac">

Once your runner type has been defined, you can update your workflow YAML files to send jobs to runner instances for processing. To run jobs on macOS larger runners, update the `runs-on` key in your workflow YAML files to use one of the GitHub-defined labels for macOS runners. For more information, see [Available macOS larger runners](#available-macos-larger-runners).

</div>

<div class="ghd-tool mac">

## Available macOS larger runners

Use the labels in the table below to run your workflows on the corresponding macOS larger runner.

| Runner Size | Architecture | Processor (CPU)                   | Memory (RAM) | Storage (SSD) | Workflow label                                                                                                                      |
| ----------- | ------------ | --------------------------------- | ------------ | ------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Large       | Intel        | 12                                | 30 GB        | 14 GB         | <code>macos-latest-large</code>, <code>macos-14-large</code>, <code>macos-15-large</code> (latest), <code>macos-26-large</code>     |
| XLarge      | arm64 (M2)   | 5 (+ 8 GPU hardware acceleration) | 14 GB        | 14 GB         | <code>macos-latest-xlarge</code>, <code>macos-14-xlarge</code>, <code>macos-15-xlarge</code> (latest), <code>macos-26-xlarge</code> |

</div>

## Viewing available runners for a repository

If you have `repo: write` access to a repository, you can view a list of the runners available to the repository.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)
3. In the left sidebar, under the "Management" section, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-server" aria-label="server" role="img"><path d="M1.75 1h12.5c.966 0 1.75.784 1.75 1.75v4c0 .372-.116.717-.314 1 .198.283.314.628.314 1v4a1.75 1.75 0 0 1-1.75 1.75H1.75A1.75 1.75 0 0 1 0 12.75v-4c0-.358.109-.707.314-1a1.739 1.739 0 0 1-.314-1v-4C0 1.784.784 1 1.75 1ZM1.5 2.75v4c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-4a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25Zm.25 5.75a.25.25 0 0 0-.25.25v4c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-4a.25.25 0 0 0-.25-.25ZM7 4.75A.75.75 0 0 1 7.75 4h4.5a.75.75 0 0 1 0 1.5h-4.5A.75.75 0 0 1 7 4.75ZM7.75 10h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1 0-1.5ZM3 4.75A.75.75 0 0 1 3.75 4h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 4.75ZM3.75 10h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Runners**.
4. Review the list of available runners for the repository.
5. Optionally, to copy a runner's label to use it in a workflow, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> to the right of the runner, then click **Copy label**.

> \[!NOTE]
> Enterprise and organization owners can create runners from this page. To create a new runner, click **New runner** at the top right of the list of runners to add runners to the repository.
>
> For more information, see [Managing larger runners](/en/actions/using-github-hosted-runners/managing-larger-runners) and [Adding self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners).

<div class="ghd-tool linux">

## Using groups to control where jobs are run

In this example, Ubuntu runners have been added to a group called `ubuntu-runners`. The `runs-on` key sends the job to any available runner in the `ubuntu-runners` group:

```yaml
name: learn-github-actions
on: [push]
jobs:
  check-bats-version:
    runs-on: 
      group: ubuntu-runners
    steps:
      - uses: actions/checkout@v5
      - uses: actions/setup-node@v4
        with:
          node-version: '14'
      - run: npm install -g bats
      - run: bats -v
```

</div>

<div class="ghd-tool windows">

## Using groups to control where jobs are run

In this example, Ubuntu runners have been added to a group called `ubuntu-runners`. The `runs-on` key sends the job to any available runner in the `ubuntu-runners` group:

```yaml
name: learn-github-actions
on: [push]
jobs:
  check-bats-version:
    runs-on: 
      group: ubuntu-runners
    steps:
      - uses: actions/checkout@v5
      - uses: actions/setup-node@v4
        with:
          node-version: '14'
      - run: npm install -g bats
      - run: bats -v
```

</div>

<div class="ghd-tool linux">

## Using labels to control where jobs are run

You can implicitly pass a label to the `runs-on` key by using the syntax `runs-on: LABEL`. Alternatively, you can use the `labels` key, as shown in the example below.

In this example, the `runs-on` key sends the job to any available runner that has been assigned the `ubuntu-24.04-16core` label:

```yaml
name: learn-github-actions
on: [push]
jobs:
  check-bats-version:
    runs-on:
      labels: ubuntu-24.04-16core
    steps:
      - uses: actions/checkout@v5
      - uses: actions/setup-node@v4
        with:
          node-version: '14'
      - run: npm install -g bats
      - run: bats -v
```

Anyone with write access to an Actions-enabled repository can find out the labels for the runners that are available in that repository. See [Running jobs on larger runners](/en/actions/using-github-hosted-runners/about-larger-runners/running-jobs-on-larger-runners#viewing-available-runners-for-a-repository).

</div>

<div class="ghd-tool windows">

## Using labels to control where jobs are run

You can implicitly pass a label to the `runs-on` key by using the syntax `runs-on: LABEL`. Alternatively, you can use the `labels` key, as shown in the example below.

In this example, the `runs-on` key sends the job to any available runner that has been assigned the `windows-2022-16core` label:

```yaml
name: learn-github-actions
on: [push]
jobs:
  check-bats-version:
    runs-on:
      labels: windows-2022-16core
    steps:
      - uses: actions/checkout@v5
      - uses: actions/setup-node@v4
        with:
          node-version: '14'
      - run: npm install -g bats
      - run: bats -v
```

Anyone with write access to an Actions-enabled repository can find out the labels for the runners that are available in that repository. See [Running jobs on larger runners](/en/actions/using-github-hosted-runners/about-larger-runners/running-jobs-on-larger-runners#viewing-available-runners-for-a-repository).

</div>

<div class="ghd-tool mac">

## Targeting macOS larger runners in a workflow

To run your workflows on macOS larger runners, set the value of the `runs-on` key to a label associated with a macOS larger runner. For a list of macOS larger runner labels, see [Available macOS larger runners](#available-macos-larger-runners).

In this example, the workflow uses a label that is associated with macOS XL runners. The `runs-on` key sends the job to any available runner with a matching label:

```yaml
name: learn-github-actions-testing
on: [push]
jobs:
  build:
    runs-on: macos-26-xlarge
    steps:
      - uses: actions/checkout@v5
      - name: Build
        run: swift build
      - name: Run tests
        run: swift test
```

</div>

<div class="ghd-tool linux">

## Using labels and groups to control where jobs are run

When you combine groups and labels, the runner must meet both requirements to be eligible to run the job.

In this example, a runner group called `ubuntu-runners` is populated with Ubuntu runners, which have also been assigned the label `ubuntu-24.04-16core`. The `runs-on` key combines `group` and `labels` so that the job is routed to any available runner within the group that also has a matching label:

```yaml
name: learn-github-actions
on: [push]
jobs:
  check-bats-version:
    runs-on:
      group: ubuntu-runners
      labels: ubuntu-24.04-16core
    steps:
      - uses: actions/checkout@v5
      - uses: actions/setup-node@v4
        with:
          node-version: '14'
      - run: npm install -g bats
      - run: bats -v
```

</div>

<div class="ghd-tool windows">

## Using labels and groups to control where jobs are run

When you combine groups and labels, the runner must meet both requirements to be eligible to run the job.

In this example, a runner group called `ubuntu-runners` is populated with Ubuntu runners, which have also been assigned the label `ubuntu-24.04-16core`. The `runs-on` key combines `group` and `labels` so that the job is routed to any available runner within the group that also has a matching label:

```yaml
name: learn-github-actions
on: [push]
jobs:
  check-bats-version:
    runs-on:
      group: ubuntu-runners
      labels: ubuntu-24.04-16core
    steps:
      - uses: actions/checkout@v5
      - uses: actions/setup-node@v4
        with:
          node-version: '14'
      - run: npm install -g bats
      - run: bats -v
```

</div>

## Troubleshooting larger runners

<div class="ghd-tool linux">

If you notice the jobs that target your larger runners are delayed or not running, there are several factors that may be causing this.

* **Concurrency settings:** You may have reached your maximum concurrency limit. If you would like to enable more jobs to run in parallel, you can update your autoscaling settings to a larger number. For more information, see [Managing larger runners](/en/actions/using-github-hosted-runners/managing-larger-runners#configuring-autoscaling-for-larger-runners).
* **Repository permissions:** Ensure you have the appropriate repository permissions enabled for your larger runners. By default, enterprise runners are not available at the repository level and must be manually enabled by an organization administrator. For more information, see [Managing larger runners](/en/actions/using-github-hosted-runners/managing-larger-runners#allowing-repositories-to-access-larger-runners).
* **Billing information:** You must have a valid credit card on file in order to use larger runners. After adding a credit card to your account, it can take up to 10 minutes to enable the use of your larger runners. For more information, see [Managing your payment and billing information](/en/billing/managing-your-billing/managing-your-payment-and-billing-information).
* **Spending limit:** Your GitHub Actions spending limit must be set to a value greater than zero. For more information, see [Setting up budgets to control spending on metered products](/en/billing/managing-billing-for-github-actions/managing-your-spending-limit-for-github-actions).
* **Fair use policy:** GitHub has a fair use policy that begins to throttle jobs based on several factors, such as how many jobs you are running or how many jobs are running across the entirety of GitHub Actions.
* **Job queue to assign time:** Job queue to assign time refers to the time between a job request and GitHub assigning a VM to execute the job. Standard GitHub-hosted runners utilizing prescribed YAML workflow labels (such as `ubuntu-latest`) are always in a "warm" state. With larger runners, a warm VM may not be ready to pick up a job on first request as the pools for these machines are smaller. As a result, GitHub may need to create a new VM, which increases the queue to assign time. Once a runner is in use, VMs are ready for subsequent workflow runs within 5 minutes. If not used again within that time, a subset of those machines remains warm, reducing the queue to assign time for future workflow runs over the next 24 hours. The higher the volume of jobs you run, the more VMs will remain in the warm pool.

</div>

<div class="ghd-tool windows">

If you notice the jobs that target your larger runners are delayed or not running, there are several factors that may be causing this.

* **Concurrency settings:** You may have reached your maximum concurrency limit. If you would like to enable more jobs to run in parallel, you can update your autoscaling settings to a larger number. For more information, see [Managing larger runners](/en/actions/using-github-hosted-runners/managing-larger-runners#configuring-autoscaling-for-larger-runners).
* **Repository permissions:** Ensure you have the appropriate repository permissions enabled for your larger runners. By default, enterprise runners are not available at the repository level and must be manually enabled by an organization administrator. For more information, see [Managing larger runners](/en/actions/using-github-hosted-runners/managing-larger-runners#allowing-repositories-to-access-larger-runners).
* **Billing information:** You must have a valid credit card on file in order to use larger runners. After adding a credit card to your account, it can take up to 10 minutes to enable the use of your larger runners. For more information, see [Managing your payment and billing information](/en/billing/managing-your-billing/managing-your-payment-and-billing-information).
* **Spending limit:** Your GitHub Actions spending limit must be set to a value greater than zero. For more information, see [Setting up budgets to control spending on metered products](/en/billing/managing-billing-for-github-actions/managing-your-spending-limit-for-github-actions).
* **Fair use policy:** GitHub has a fair use policy that begins to throttle jobs based on several factors, such as how many jobs you are running or how many jobs are running across the entirety of GitHub Actions.
* **Job queue to assign time:** Job queue to assign time refers to the time between a job request and GitHub assigning a VM to execute the job. Standard GitHub-hosted runners utilizing prescribed YAML workflow labels (such as `ubuntu-latest`) are always in a "warm" state. With larger runners, a warm VM may not be ready to pick up a job on first request as the pools for these machines are smaller. As a result, GitHub may need to create a new VM, which increases the queue to assign time. Once a runner is in use, VMs are ready for subsequent workflow runs within 5 minutes. If not used again within that time, a subset of those machines remains warm, reducing the queue to assign time for future workflow runs over the next 24 hours. The higher the volume of jobs you run, the more VMs will remain in the warm pool.

</div>

<div class="ghd-tool mac">

Because macOS arm64 does not support Node 12, macOS larger runners automatically use Node 16 to execute any JavaScript action written for Node 12. Some community actions may not be compatible with Node 16. If you use an action that requires a different Node version, you may need to manually install a specific version at runtime.

> \[!NOTE]
> ARM-powered runners are currently in public preview and are subject to change.

</div>