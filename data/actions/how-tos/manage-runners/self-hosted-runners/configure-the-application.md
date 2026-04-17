# Configuring the self-hosted runner application as a service

You can configure the self-hosted runner application as a service to automatically start the runner application when the machine starts.

<div class="ghd-tool linux">

> \[!NOTE]
> You must add a runner to GitHub before you can configure the self-hosted runner application as a service.
> For more information, see [Adding self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners).

For Linux systems that use `systemd`, you can use the `svc.sh` script that is created after successfully adding the runner to install and manage using the application as a service.

On the runner machine, open a shell in the directory where you installed the self-hosted runner application. Use the commands below to install and manage the self-hosted runner service.

</div>

<div class="ghd-tool windows">

> \[!NOTE]
> Configuring the self-hosted runner application as a service on Windows is part of the application configuration process. If you have already configured the self-hosted runner application but did not choose to configure it as a service, you must remove the runner from GitHub and re-configure the application. When you re-configure the application, choose the option to configure the application as a service.
>
> For more information, see [Removing self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/removing-self-hosted-runners) and [Adding self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners).

You can manage the runner service in the Windows **Services** application, or you can use PowerShell to run the commands below.

</div>

<div class="ghd-tool mac">

> \[!NOTE]
> You must add a runner to GitHub before you can configure the self-hosted runner application as a service.
> For more information, see [Adding self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners).

On the runner machine, open a shell in the directory where you installed the self-hosted runner application. Use the commands below to install and manage the self-hosted runner service.

</div>

<div class="ghd-tool linux">

## Installing the service

1. Stop the self-hosted runner application if it is currently running.

2. Install the service with the following command:

   ```shell
   sudo ./svc.sh install
   ```

3. Alternatively, the command takes an optional `user` argument to install the service as a different user.

   ```shell
   ./svc.sh install USERNAME
   ```

</div>

<div class="ghd-tool mac">

## Installing the service

1. Stop the self-hosted runner application if it is currently running.
2. Install the service with the following command:

   ```shell
   ./svc.sh install
   ```

</div>

## Starting the service

Start the service with the following command:

<div class="ghd-tool linux">

```shell
sudo ./svc.sh start
```

> \[!NOTE]
> On Debian-based Linux systems (such as Debian or Ubuntu) with `needrestart` enabled, you can prevent `needrestart` from restarting the runner service during a workflow job by configuring it to ignore the runner service. Run the following command:
>
> ```bash
> echo '$nrconf{override_rc}{qr(^actions\.runner\..+\.service$)} = 0;' | sudo tee /etc/needrestart/conf.d/actions_runner_services.conf
> ```

</div>

<div class="ghd-tool windows">

```shell
Start-Service "actions.runner.*"
```

</div>

<div class="ghd-tool mac">

```shell
./svc.sh start
```

</div>

## Checking the status of the service

Check the status of the service with the following command:

<div class="ghd-tool linux">

```shell
sudo ./svc.sh status
```

</div>

<div class="ghd-tool windows">

```shell
Get-Service "actions.runner.*"
```

</div>

<div class="ghd-tool mac">

```shell
./svc.sh status
```

</div>

For more information on viewing the status of your self-hosted runner, see [Monitoring and troubleshooting self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/monitoring-and-troubleshooting-self-hosted-runners).

## Stopping the service

Stop the service with the following command:

<div class="ghd-tool linux">

```shell
sudo ./svc.sh stop
```

</div>

<div class="ghd-tool windows">

```shell
Stop-Service "actions.runner.*"
```

</div>

<div class="ghd-tool mac">

```shell
./svc.sh stop
```

</div>

## Uninstalling the service

1. Stop the service if it is currently running.
2. Uninstall the service with the following command:

    <div class="ghd-tool linux">

   ```shell
   sudo ./svc.sh uninstall
   ```

    </div>

    <div class="ghd-tool windows">

   ```shell
   Remove-Service "actions.runner.*"
   ```

    </div>

    <div class="ghd-tool mac">

   ```shell
   ./svc.sh uninstall
   ```

    </div>

<div class="ghd-tool linux">

## Customizing the self-hosted runner service

If you don't want to use the above default `systemd` service configuration, you can create a customized service or use whichever service mechanism you prefer. Consider using the `serviced` template at `actions-runner/bin/actions.runner.service.template` as a reference. If you use a customized service, the self-hosted runner service must always be invoked using the `runsvc.sh` entry point.

</div>

<div class="ghd-tool mac">

## Customizing the self-hosted runner service

If you don't want to use the above default launchd service configuration, you can create a customized service or use whichever service mechanism you prefer. Consider using the `plist` template at `actions-runner/bin/actions.runner.plist.template` as a reference. If you use a customized service, the self-hosted runner service must always be invoked using the `runsvc.sh` entry point.

</div>