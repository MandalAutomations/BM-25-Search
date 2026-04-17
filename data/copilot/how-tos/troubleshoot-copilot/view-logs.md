# Viewing logs for GitHub Copilot in your environment

View logs to troubleshoot GitHub Copilot-related errors in your IDE.

<div class="ghd-tool jetbrains">

## Collecting log files

The location of the log files depends on the JetBrains IDE you are using. For more information, see [Configuring GitHub Copilot in your environment](/en/copilot/configuring-github-copilot/configuring-github-copilot-in-your-environment?tool=jetbrains).

These steps describe how to view and collect the log files for the following JetBrains IDEs:

* IntelliJ IDEA
* Android Studio
* GoLand
* PhpStorm
* PyCharm
* RubyMine
* WebStorm

The GitHub Copilot extension logs to the IDEA log location for IntelliJ plugins.

1. In your JetBrains IDE, open the **Help** menu.
2. Go to **Show Log in Finder**.
3. Open the `idea.log` in your preferred editor and look for any errors related to GitHub or GitHub Copilot.

For more information, see the [Locating IDE log files](https://intellij-support.jetbrains.com/hc/en-us/articles/207241085-Locating-IDE-log-files) in the IntelliJ documentation.

### Collect log files from Rider

1. In Rider, open the **Help** menu.
2. Go to **Diagnostic Tools**.
3. Go to **Show Log in**.
4. Open the `idea.log` in your preferred editor and look for any errors related to GitHub or GitHub Copilot.

## Enabling debug mode

If you find the log file doesn't contain enough information to resolve an issue, it may help to enable debug logging temporarily. This can be especially helpful for debugging network-related issues.

1. In the menu bar, click **Help**, select **Diagnostic Tools**, and click **Debug Log Settings...**.

   ![Screenshot of the menu bar in a JetBrains IDE. The "Help" menu and "Diagnostic Tools" submenu are expanded and "Debug Log Settings" is highlighted.](/assets/images/help/copilot/jetbrains-debug-log.png)

2. In the "Custom Debug Log Configuration" window, add a new line with the following content, then click **OK**.

   ```text copy
   #com.github.copilot:trace
   ```

3. Keep using your IDE until you encounter the issue again, then collect the log file as described in [Collecting log files](#collecting-log-files).

4. When you have the information you need, disable debug mode by removing `#com.github.copilot:trace` from the "Custom Debug Log Configuration" window.

## Viewing network connectivity diagnostics logs

If you encounter problems connecting to GitHub Copilot due to network restrictions, firewalls, or your proxy setup, use the following troubleshooting steps.

1. In the menu bar, click **Tools**, select **GitHub Copilot**, and click **Log Diagnostics**.
2. The `idea.log` file should open in the JetBrains IDE with the diagnostics output. Alternatively, you can open the `idea.log` file in your preferred editor.
3. Check the section on **Reachability** to determine if GitHub Copilot can access the necessary services.

## Troubleshooting certificate-related errors

If you're using a custom certificate, ensure the certificate is installed correctly in the operating system, see [Troubleshooting network errors for GitHub Copilot](/en/copilot/troubleshooting-github-copilot/troubleshooting-network-errors-for-github-copilot). Then use the following troubleshooting steps.

1. In the menu bar, click **Tools**, select **GitHub Copilot**, and click **Log CA Certificates**.
2. The `idea.log` file should open in the JetBrains IDE with the trusted CA certificates logged in PEM format. You may need to refresh the `idea.log` file to view all of the output. Alternatively, you can open the `idea.log` file in your preferred editor.
3. Check to see if the expected custom certificate is included in the certificate list output.

</div>

<div class="ghd-tool visualstudio">

## Viewing logs in Visual Studio

The log files for the GitHub Copilot extension are stored in the standard log location for Visual Studio extensions.

1. Open the **View** menu in Visual Studio.
2. Click **Output**.
3. On the right of the Output view pane, select **GitHub Copilot** from the dropdown menu.

## Further reading

* [Log all activity to the log file for troubleshooting](https://learn.microsoft.com/en-us/visualstudio/ide/reference/log-devenv-exe?view=vs-2022) in the Visual Studio documentation

</div>

<div class="ghd-tool vscode">

## Viewing and collecting log files

The log files for the GitHub Copilot extension are stored in the standard log location for Visual Studio Code extensions. The log files are useful for diagnosing connection issues.

1. Open the **View** menu in Visual Studio Code.
2. Click **Output**.
3. On the right of the Output view pane, select **GitHub Copilot** from the dropdown menu.

Alternatively, you can open the log folder for Visual Studio Code extensions in your system's file explorer. This is useful if you need to forward the log files to the support team.

1. Open the VS Code Command Palette
   * For Mac:
     * Use: <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd>
   * For Windows or Linux:
     * Use: <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>
2. Type "Logs", and then select **Developer: Open Extension Logs Folder** from the list.

## Enabling debug mode

If you find the log file doesn't contain enough information to resolve an issue, it may help to enable debug logging temporarily. This can be especially helpful for debugging network-related issues.

1. Open the VS Code Command Palette
   * For Mac:
     * Use: <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd>
   * For Windows or Linux:
     * Use: <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>
2. Type "Developer", then select **Developer: Set Log Level**.
3. Type "GitHub", then select the GitHub extension you're troubleshooting:
   * **GitHub Copilot Chat** for the Copilot Chat extension.
   * **GitHub** for the GitHub Copilot Extension.
4. Select **Trace** from the dropdown list.
5. When you have the information you need, disable debug mode by repeating steps 1 through 4 and returning the logging level to **Info**.

## Viewing network connectivity diagnostics logs

If you encounter problems connecting to GitHub Copilot due to network restrictions, firewalls, or your proxy setup, use the following troubleshooting steps.

1. Open the VS Code Command Palette
   * For Mac:
     * Use: <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd>
   * For Windows or Linux:
     * Use: <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>
2. Type "Diagnostics", and then select **Developer: Chat Diagnostics** from the list. This opens a new editor with the relevant information that you can inspect yourself or share with the support team.
3. Check the section on **Reachability** to determine if GitHub Copilot can actually access the necessary services.

## Viewing Electron logs

In rare cases, errors might not be propagated to the corresponding error handlers and are not logged in the regular locations. If you encounter errors and there is nothing in the logs, you may try to see the logs from the process running VS Code and the extension.

1. Open the VS Code Command Palette
   * For Mac:
     * Use: <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd>
   * For Windows or Linux:
     * Use <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>
2. Type "Toggle", and then select **Developer: Toggle Developer Tools** from the list.
3. In the Developer Tools window, select the **Console** tab to see any errors or warnings.

   ![Screenshot of the Developer Tools window in Visual Studio Code. The console tab is outlined in dark orange.](/assets/images/help/copilot/vsc-electron-logs.png)

## Further reading

* [Troubleshooting network errors for GitHub Copilot](/en/copilot/troubleshooting-github-copilot/troubleshooting-network-errors-for-github-copilot)
* [Network Connections in Visual Studio Code](https://code.visualstudio.com/docs/setup/network) in the Visual Studio Code documentation

</div>

<div class="ghd-tool vimneovim">

## Checking if GitHub Copilot is operational

To check if GitHub Copilot is operational, run the following command in Vim/Neovim:

```
:Copilot status
```

</div>

<div class="ghd-tool xcode">

## Collecting log files

The log files for the GitHub Copilot extension for Xcode are stored in `~/Library/Logs/GitHubCopilot/`. The most recent file is named `github-copilot-for-xcode.log`.

1. Open the GitHub Copilot for Xcode application.
2. At the top of the application window, click **Advanced**.
3. In the "Logging" section, click **Open Copilot Log Folder**.

## Enabling verbose logs

You can enable verbose logging to help troubleshoot issues with the GitHub Copilot extension for Xcode.

1. Open the GitHub Copilot for Xcode application.
2. At the top of the application window, click **Advanced**.
3. In the "Logging" section, next to "Verbose Logging", toggle the switch to the right.

</div>