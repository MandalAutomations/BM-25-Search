# Larger runners

Learn about the types and uses of GitHub-hosted larger runners.

## About larger runners

Customers on GitHub Team and GitHub Enterprise Cloud plans can choose from a range of managed virtual machines that have more resources than the [standard GitHub-hosted runners](/en/actions/how-tos/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners#supported-runners-and-hardware-resources). These machines are referred to as "larger runners." They offer the following advanced features:

* More RAM, CPU, and disk space
* Static IP addresses
* Azure private networking
* The ability to group runners
* Autoscaling to support concurrent workflows
* GPU-powered runners

These larger runners are hosted by GitHub and have the runner application and other tools preinstalled.

GitHub offers larger runners with macOS, Ubuntu, or Windows operating systems, and different features and sizes are available depending on which operating system you use.

## About larger runners for code scanning default setup

Consider configuring larger runners for code scanning default setup if:

* Your scans with standard GitHub-hosted runners are taking too long.
* Your scans with standard GitHub-hosted runners are returning memory or disk errors.
* You want to customize aspects of your code scanning runner, such as the runner size, runner image, and job concurrency, without using self-hosted runners.

For more information on configuring larger runners for code scanning default setup, see [Configuring larger runners for default setup](/en/code-security/how-tos/scan-code-for-vulnerabilities/manage-your-configuration/configuring-larger-runners-for-default-setup).

## About Ubuntu and Windows larger runners

Larger runners with Ubuntu or Windows operating systems are configured in your organization or enterprise. When you add a larger runner, you are defining a type of machine from a selection of available hardware specifications and operating system images.

With Ubuntu and Windows larger runners, you can:

* Assign runners static IP addresses from a specific range, allowing you to use this range to configure a firewall allowlist
* Control access to your resources by assigning runners to runner groups
* Use autoscaling to simplify runner management and control your costs
* Use your runners with Azure private networking

## About macOS larger runners

Larger runners with a macOS operating system are not manually added to your organization or enterprise, but are instead used by updating the `runs-on` key of a workflow file to one of the GitHub-defined macOS larger runner labels.

Since macOS larger runners are not preconfigured, they have limitations that Ubuntu and Windows larger runners do not. For more information, see [Larger runners reference](/en/actions/reference/larger-runners-reference#limitations-for-macos-larger-runners).

## Billing

> \[!NOTE]
> Larger runners are not eligible for the use of included minutes on private repositories. For both private and public repositories, when larger runners are in use, they will always be billed at the per-minute rate.

Compared to standard GitHub-hosted runners, larger runners are billed differently. Larger runners are only billed at the per-minute rate for the amount of time workflows are executed on them. There is no cost associated with creating a larger runner that is not being used by a workflow. For more information, see [Actions runner pricing](/en/billing/reference/actions-minute-multipliers).

## Next steps

To start using Windows or Ubuntu larger runners, see [Managing larger runners](/en/actions/how-tos/using-github-hosted-runners/using-larger-runners/managing-larger-runners).

To start using macOS larger runners, see [Running jobs on larger runners](/en/actions/how-tos/using-github-hosted-runners/using-larger-runners/running-jobs-on-larger-runners?platform=mac).

To find reference information about using larger runners, see [Larger runners reference](/en/actions/reference/larger-runners-reference).