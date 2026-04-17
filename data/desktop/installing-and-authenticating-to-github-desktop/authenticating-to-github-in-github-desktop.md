# Authenticating to GitHub in GitHub Desktop

You can securely access your account's resources on GitHub Desktop by authenticating to GitHub.

## About authentication

To keep your account secure, you must authenticate before you can use GitHub Desktop to access resources on GitHub.

Before you authenticate, you must already have an account on GitHub. For more information, see [Creating an account on GitHub](/en/get-started/start-your-journey/creating-an-account-on-github).

<div class="ghd-tool mac">

## Authenticating to your GitHub account

1. In the menu bar, select **GitHub Desktop**, then click **Settings**.

   ![Screenshot of the menu bar on a Mac. Under the open "GitHub Desktop" dropdown menu, the cursor hovers over "Settings", which is highlighted in blue.](/assets/images/help/desktop/mac-choose-settings.png)
2. In the "Settings" window, on the **Accounts** pane, click the appropriate "Sign Into" button. Use **Sign Into GitHub Enterprise** to sign into GitHub Enterprise Server or GitHub Enterprise Cloud with data residency.

   ![Screenshot of the "Accounts" pane in the "Settings" window. Blue buttons labeled "Sign Into GitHub.com" and "Sign Into GitHub Enterprise" are shown.](/assets/images/help/desktop/sign-in-github.png)
3. If you are signing into an account on GitHub Enterprise, in the "Sign in" modal window, type the URL where you access GitHub, then click **Continue**.
4. In the "Sign in Using Your Browser" modal window, click **Continue With Browser**. GitHub Desktop will open your default browser.
5. To authenticate to GitHub, in the browser, type your credentials and click **Sign in**.

   Alternatively, if you were already signed in to GitHub, follow the prompts to return to GitHub Desktop to finish authenticating.
6. If you have configured two-factor authentication (2FA) for GitHub, do one of the following:

   * If you set up 2FA via SMS, retrieve your 2FA code from an SMS message.
   * If you set up 2FA with a TOTP application, generate a 2FA code.

   Then enter your 2FA code in the prompt on GitHub and click **Verify**.
7. After GitHub authenticates your account, follow the prompts to return to GitHub Desktop.

</div>

<div class="ghd-tool windows">

## Authenticating to your GitHub account

1. Use the **File** menu, then click **Options**.

   ![Screenshot of the "GitHub Desktop" menu bar on Windows. In the expanded "File" dropdown menu, the "Options" item is outlined in orange.](/assets/images/help/desktop/windows-choose-options.png)

2. In the "Options" window, on the **Accounts** pane, click the appropriate "Sign Into" button. Use **Sign Into GitHub Enterprise** to sign into GitHub Enterprise Server or GitHub Enterprise Cloud with data residency.

   ![Screenshot of the "Accounts" pane in the "Options" window. Blue buttons labeled "Sign Into GitHub.com" and "Sign Into GitHub Enterprise" are shown.](/assets/images/help/desktop/windows-sign-in-github.png)

3. If you are signing into an account on GitHub Enterprise, in the "Sign in" modal window, type the URL where you access GitHub, then click **Continue**.

4. In the "Sign in Using Your Browser" modal window, click **Continue With Browser**. GitHub Desktop will open your default browser.

   > \[!WARNING]
   > Authenticating to GitHub using your username and password is not supported. We require authenticating using the browser instead.

5. To authenticate to GitHub, in the browser, type your credentials and click **Sign in**.

   Alternatively, if you were already signed in to GitHub, follow the prompts to return to GitHub Desktop to finish authenticating.

6. If you have configured two-factor authentication (2FA) for GitHub, do one of the following:

   * If you set up 2FA via SMS, retrieve your 2FA code from an SMS message.
   * If you set up 2FA with a TOTP application, generate a 2FA code.

   Then enter your 2FA code in the prompt on GitHub and click **Verify**.

7. After GitHub authenticates your account, follow the prompts to return to GitHub Desktop.

</div>

## Troubleshooting authentication issues

If GitHub Desktop encounters an authentication error, you can use error messages to troubleshoot.

If you encounter an authentication error, first try signing out and signing back in to your account on GitHub Desktop.

For some errors, GitHub Desktop will prompt you with an error message. If you are not prompted, or to find more information about any error, view the GitHub Desktop log files by using the following steps.

<div class="ghd-tool mac">

1. In the menu bar, select **Help**, then click **Show Logs in Finder**.

   ![Screenshot of the "GitHub Desktop" menu bar on a Mac. Under the expanded "Help" dropdown menu, "Show Logs in Finder" is highlighted blue.](/assets/images/help/desktop/mac-show-logs.png)

2. Select the log file from the date when you encountered the authentication error.

</div>

<div class="ghd-tool windows">

1. Use the **Help** drop-down menu and click **Show Logs in Explorer**.

   ![Screenshot of the "GitHub Desktop" menu bar on Windows. In the expanded "Help" dropdown menu, "Show Logs in Explorer" is outlined in orange.](/assets/images/help/desktop/windows-show-logs.png)

2. Select the log file from the date when you encountered the authentication error.

</div>

Review the troubleshooting information below for the error message that you encounter.

### Bad credentials

```shell
Error: Bad credentials
```

This error means that there is an issue with your stored account credentials.

To troubleshoot, sign out of your account on GitHub Desktop and then sign back in.

### Empty token

```shell
info: [ui] [AppStore.withAuthenticatingUser] account found for repository: node - USERNAME (empty token)
```

This error means that GitHub Desktop is unable to find the access token that it created in the system keychain.

To troubleshoot, sign out of your account on GitHub Desktop and then sign back in.

### Repository not found

```shell
fatal: repository 'https://github.com/<user>/<repo>.git' not found

(The error was parsed as 8: The repository does not seem to exist anymore. You may not have access, or it may have been deleted or renamed.)
```

This error means that you do not have permission to access the repository that you are trying to clone.

To troubleshoot, contact the person in your organization who administers permissions.

### Could not read from remote repository

```shell
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights and the repository exists.
```

This error means that you do not have a valid SSH key set up.

To troubleshoot, see [Generating a new SSH key and adding it to the ssh-agent](/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

### Failed to clone

```shell
fatal: clone of 'git@github.com:<user>/<repo>' into submodule path '<path>' failed
Failed to clone 'src/github.com/<user>/<repo>'. Retry scheduled
Cloning into '<path>'...
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.
```

This error means that either the repository that you are trying to clone has submodules that you do not have access to or you do not have a valid SSH key set up.

If you do not have access to the submodules, troubleshoot by contacting the person who administers permissions for the repository.

If you do not have a valid SSH key set up, see [Generating a new SSH key and adding it to the ssh-agent](/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

<div class="ghd-tool windows">

### Unable to read AskPass response

```shell
error: unable to read askpass response from '/Users/<path>/GitHub Desktop.app/Contents/Resources/app/static/ask-pass-trampoline.sh'
fatal: could not read Username for 'https://github.com': terminal prompts disabled
```

This error can be caused by multiple events.

If the `Command Processor` registry entries are modified, GitHub Desktop will respond with an `Authentication failed` error. To check if these registry entries have been modified, follow these steps.

1. Open the Registry Editor (`regedit.exe`) and navigate to the following locations.
   `HKEY_CURRENT_USER\Software\Microsoft\Command Processor\`
   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Command Processor\`
2. Check to see if there is an `Autorun` value in either location.
3. If there is an `Autorun` value, delete it.

If your Windows username has extended Unicode characters, it may cause an AskPass response error. To troubleshoot, create a new Windows user account and migrate your files to that account. For more information, see [Create a user account in Windows](https://support.microsoft.com/en-us/help/13951/windows-create-user-account) in the Microsoft documentation.

</div>

## Further reading

* [About authentication to GitHub](/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)