# Personalizing GitHub Codespaces for your account

You can personalize GitHub Codespaces by using a dotfiles repository on GitHub or by using Settings Sync.

## About personalizing Codespaces

When using any development environment, customizing the settings and tools to your preferences and workflows is an important step. GitHub Codespaces allows for two main ways of personalizing your codespaces.

* [Settings Sync](#settings-sync) - You can synchronize your Visual Studio Code settings between the desktop application and the VS Code web client.
* [Dotfiles](#dotfiles) – You can use a `dotfiles` repository to specify scripts, shell preferences, and other configurations.

GitHub Codespaces personalization applies to any codespace you create.

Project maintainers can also define a default configuration that applies to every codespace for a repository, created by anyone. For more information, see [Introduction to dev containers](/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers).

## Settings Sync

Settings Sync allows you to synchronize configurations such as settings, keyboard shortcuts, snippets, extensions, and UI state across machines and instances of VS Code. For more information, see [Settings Sync](https://code.visualstudio.com/docs/editor/settings-sync) in the VS Code documentation.

Your synced settings are cached in the cloud. If Settings Sync is turned on in a codespace, any updates you make to your settings in the codespace are pushed to the cloud, and any updates you push to the cloud from elsewhere are pulled into your codespace.

For example, a common use of Settings Sync would be to sync your settings from your VS Code desktop application, which you use for local work, to codespaces you open in the browser. To do this, you would need to do the following things.

* Turn on Settings Sync in the desktop application. For more information, see [Settings Sync](https://code.visualstudio.com/docs/editor/settings-sync#_turning-on-settings-sync) in the VS Code documentation.
* Enable Settings Sync in your user preferences for GitHub Codespaces. For more information, see [Managing your preferences for Settings Sync](#managing-your-preferences-for-settings-sync).
* Optionally, if you want to sync settings changes back to your desktop application from a codespace, turn on Settings Sync in the codespace and add the repository from which you created the codespace to your list of trusted repositories. For more information, see [Turning on Settings Sync in a codespace](#turning-on-settings-sync-in-a-codespace).

Alternatively, you may want to use the same settings across all codespaces you open in the web client, while leaving your local VS Code application unaffected. To do this, you would need to do the following things.

* In a codespace, configure your settings as you want them, then turn on Settings Sync in the codespace to push the settings to the cloud. When you do this, Settings Sync is enabled automatically in your user preferences for GitHub Codespaces, so your settings will be pulled into all new codespaces. For more information, see [Turning on Settings Sync in a codespace](#turning-on-settings-sync-in-a-codespace).
* In the desktop application, leave Settings Sync turned off, or sync your settings to a different account.

### About Settings Sync in codespaces

Whether Settings Sync is turned on by default in a codespace, and the relationship between your cached settings and the settings in a codespace, depend on several factors. These factors include the editor in which you open the codespace, your user preferences on GitHub, and your list of trusted repositories.

For codespaces opened in the VS Code desktop application, Settings Sync remains on if you have previously turned on Settings Sync in the application. If Settings Sync is on, your settings are synced both to and from the cloud.

For codespaces opened in the VS Code web client, Settings Sync is disabled by default. This means the VS Code instance in the codespace uses the default theme and settings.

If you use the web client and want your codespaces to use your cached synced settings, you can enable Settings Sync in your user preferences on GitHub. For more information, see [Managing your preferences for Settings Sync](#managing-your-preferences-for-settings-sync). Settings Sync is enabled in your user preferences automatically if you open a codespace in the web client and turn on Settings Sync in the codespace.

When Settings Sync is enabled in your user preferences, for codespaces opened in the web client, the behavior of Settings Sync depends on your list of trusted repositories.

* If you create a codespace from a repository you trust, Settings Sync is turned on in the codespace by default, so your settings are synced both to and from the cloud.
* If you create a codespace from a repository you haven't added to your list of trusted repositories, the sync takes place in one direction and at one time only. When you create the codespace, your settings are pulled into the codespace from your cached settings in the cloud, but from then on, Settings Sync is turned off in the codespace. This means updates you make to your settings in the codespace are not pushed back to the cloud, and any updates you make to your cached settings from elsewhere are not reflected in the codespace after you have created it.

  If you turn on Settings Sync in a codespace, you will be prompted to add the repository to your list of trusted repositories. For more information, see [Turning on Settings Sync in a codespace](#turning-on-settings-sync-in-a-codespace).

Your list of trusted repositories for GitHub Codespaces is shared between the GPG verification and Settings Sync features. Assuming you have both features enabled, if you have added a selected list of trusted repositories for GPG verification, Settings Sync is turned on in codespaces created from these repositories. If you trust a new repository for Settings Sync, GPG verification is enabled for the same repository. Although the features share the same list of trusted repositories, you can enable or disable GPG verification and Settings Sync independently.

> \[!NOTE]
> If you have previously enabled GPG verification for all repositories, we recommend changing your preferences to use a selected list of trusted repositories. For more information, see [Security in GitHub Codespaces](/en/codespaces/codespaces-reference/security-in-github-codespaces#using-settings-sync).

For more information on managing your preferences for GPG verification, see [Managing GPG verification for GitHub Codespaces](/en/codespaces/managing-your-codespaces/managing-gpg-verification-for-github-codespaces).

### Managing your preferences for Settings Sync

If you enable Settings Sync in your user preferences, codespaces opened in the VS Code web client will pull in your cached settings from the cloud, and codespaces created from trusted repositories will sync with your cached settings in both directions.

1. In the upper-right corner of any page on GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**.
2. In the "Code, planning, and automation" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces**.
3. To enable or disable Settings Sync, under "Settings Sync," select or deselect **Enable**.
4. To change your trusted repositories for GPG verification and Settings Sync, under "Trusted repositories," either select **All repositories**, or select **Selected repositories** and use the "Select repositories" dropdown to add repositories you trust.

   > \[!NOTE]
   > We recommend using a selected list of trusted repositories. For more information, see [Security in GitHub Codespaces](/en/codespaces/codespaces-reference/security-in-github-codespaces#using-settings-sync).

Your updates will take effect in new codespaces. However, you can turn on Settings Sync in an existing codespace. For more information, see [Turning on Settings Sync in a codespace](#turning-on-settings-sync-in-a-codespace).

### Turning on Settings Sync in a codespace

> \[!NOTE]
> You should only turn on Settings Sync in codespaces created from repositories you trust. For more information, see [Security in GitHub Codespaces](/en/codespaces/reference/security-in-github-codespaces#using-settings-sync).

The following procedure describes how to turn on Settings Sync in a codespace opened in the web client. For information about turning on Settings Sync in the VS Code desktop application, see [Settings Sync](https://code.visualstudio.com/docs/editor/settings-sync#_turning-on-settings-sync) in the VS Code documentation.

1. In VS Code, at the bottom of the Activity Bar, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="Manage" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg>, then click **Sign in to Sync Settings**.

2. If the repository from which you created the codespace is not in your list of trusted repositories, a browser window will open asking you to authorize additional permissions for Settings Sync. If you trust the repository, click **Authorize**, then close the browser window. The codespace will reload and display your latest synced settings.

   > \[!NOTE]
   > If you have Settings Sync disabled in your user preferences, and have set your trusted repositories to all repositories, you will see a warning about enabling Settings Sync for all repositories. Review the warning and choose whether to enable Settings Sync for all repositories or revise your list of trusted repositories.

3. To configure which settings you want to sync, open the Command Palette with <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd> (Mac) / <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux), then start typing "Settings Sync". Click **Settings Sync: Configure...**.

4. Select the settings you want to sync, then click **OK**.

   ![Screenshot of the "Setting Sync" options. There are seven options, each with a checkbox. The "OK" button is shown top right.](/assets/images/help/codespaces/settings-sync-config-ok.png)

### Turning off Settings Sync in a codespace

You can turn off Settings Sync to stop syncing settings to and from an instance of VS Code.

When you turn off Settings Sync in a codespace, new codespaces continue to use the settings cached from the last time your settings were pushed to the cloud. If you use the VS Code web client for codespaces, and want codespaces to use the default settings instead of your cached settings, you can disable Settings Sync. For more information, see [Managing your preferences for Settings Sync](/en/codespaces/setting-your-user-preferences/personalizing-github-codespaces-for-your-account#managing-your-preferences-for-settings-sync).

If you want to return to using the default VS Code settings in all instances of VS Code, including the desktop application, you can clear the cache in the cloud when you turn off Settings Sync.

1. If Settings Sync is currently turned off in your instance of VS Code, and you want to clear your cached settings, you must first turn it on. For instructions, see [Personalizing GitHub Codespaces for your account](/en/codespaces/setting-your-user-preferences/personalizing-github-codespaces-for-your-account#turning-on-settings-sync-in-a-codespace).

2. At the bottom of the Activity Bar, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="The gear icon" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> and click **Settings Sync is On**.

3. In the dropdown, click **Settings Sync: Turn Off**.

   ![Screenshot of the dropdown menu with the "Settings Sync: Turn Off" option highlighted with a dark orange outline.](/assets/images/help/codespaces/settings-sync-turn-off.png)

4. To clear your cached settings, in the dialog, select **Turn off sync on all your devices and clear the data from the cloud**.

   ![Screenshot of the "Do you want to turn off sync?" dialog, with the option to clear data from the cloud selected.](/assets/images/help/codespaces/turn-off-sync-dialog.png)

5. Click **Turn off**.

## Dotfiles

Dotfiles are files and folders on Unix-like systems starting with `.` that control the configuration of applications and shells on your system. You can store and manage your dotfiles in a repository on GitHub. For advice and tutorials about what to include in your dotfiles repository, see [GitHub does dotfiles](https://dotfiles.github.io/).

Your dotfiles repository might include your shell aliases and preferences, any tools you want to install, or any other codespace personalization you want to make.

You can configure GitHub Codespaces to use dotfiles from any repository you own by selecting that repository in your [personal GitHub Codespaces settings](https://github.com/settings/codespaces).

When you create a new codespace, GitHub clones your selected dotfiles repository to the codespace environment, and looks for one of the following files to set up the environment.

* `install.sh`
* `install`
* `bootstrap.sh`
* `bootstrap`
* `script/bootstrap`
* `setup.sh`
* `setup`
* `script/setup`

If none of these files are found, then any files or folders in your selected dotfiles repository starting with `.` are symlinked to the codespace's `~` or `$HOME` directory.

Any changes to your selected dotfiles repository will apply only to each new codespace, and do not affect any existing codespace.

> \[!NOTE]
> Currently, Codespaces does not support personalizing the User-scoped settings for VS Code with your `dotfiles` repository. You can set default Workspace and Remote \[Codespaces] settings for a specific project in the project's repository. For more information, see [Introduction to dev containers](/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers#creating-a-custom-dev-container-configuration).

### Enabling your dotfiles repository for Codespaces

You can use your selected dotfiles repository to personalize your GitHub Codespaces environment. Once you choose your dotfiles repository, you can add your scripts, preferences, and configurations to it. You then need to enable your dotfiles from your personal GitHub Codespaces settings page.

> \[!WARNING]
> Dotfiles have the ability to run arbitrary scripts, which may contain unexpected or malicious code. Before installing a dotfiles repo, we recommend checking scripts to ensure they don't perform any unexpected actions.

1. In the upper-right corner of any page on GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**.

2. In the "Code, planning, and automation" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces**.

3. Under "Dotfiles", select **Automatically install dotfiles** so that GitHub Codespaces automatically installs your dotfiles into every new codespace you create.

   ![Screenshot of the "Dotfiles" section of the codespace settings, with the "Automatically install dotfiles" option cleared.](/assets/images/help/codespaces/install-custom-dotfiles.png)

4. Use the dropdown to choose the repository you want to install dotfiles from.

   ![Screenshot of the "Automatically install dotfiles" option selected and "monalisa/dotfiles" selected from a dropdown list of repositories.](/assets/images/help/codespaces/select-dotfiles-repo.png)

You can add further script, preferences, configuration files to your dotfiles repository or edit existing files whenever you want. Changes to settings will only be picked up by new codespaces.

If your codespace fails to pick up configuration settings from dotfiles, see [Troubleshooting personalization options for GitHub Codespaces](/en/codespaces/troubleshooting/troubleshooting-personalization-for-codespaces#troubleshooting-dotfiles).

## Other available settings

You can also personalize GitHub Codespaces using additional options in [your personal settings](https://github.com/settings/codespaces):

* To enable GPG verification, see [Managing GPG verification for GitHub Codespaces](/en/codespaces/managing-your-codespaces/managing-gpg-verification-for-github-codespaces).
* To set your editor, see [Setting your default editor for GitHub Codespaces](/en/codespaces/setting-your-user-preferences/setting-your-default-editor-for-github-codespaces).
* To set how long a codespace can remain unused before it is automatically stopped, see [Setting your timeout period for GitHub Codespaces](/en/codespaces/setting-your-user-preferences/setting-your-timeout-period-for-github-codespaces).
* To set the period for which your unused codespaces are retained, see [Configuring automatic deletion of your codespaces](/en/codespaces/setting-your-user-preferences/configuring-automatic-deletion-of-your-codespaces).
* To set your default region, see [Setting your default region for GitHub Codespaces](/en/codespaces/setting-your-user-preferences/setting-your-default-region-for-github-codespaces).

## Further reading

* [Creating a new repository](/en/repositories/creating-and-managing-repositories/creating-a-new-repository)
* [Deep dive into GitHub Codespaces](/en/codespaces/about-codespaces/deep-dive#personalizing-your-codespace-with-extensions-or-plugins)
* [Customizing your codespace](/en/codespaces/customizing-your-codespace)
* [Managing your codespaces](/en/codespaces/managing-your-codespaces)