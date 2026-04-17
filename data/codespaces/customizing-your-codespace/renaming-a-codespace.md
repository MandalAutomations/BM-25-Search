# Renaming a codespace

You can change the codespace display name to one of your choice on GitHub or using the GitHub CLI.

## About renaming a codespace

When you create a codespace it's assigned an auto-generated display name. If you have multiple codespaces, the display name helps you to differentiate between codespaces. For example: `literate space parakeet`. You can change the display name for your codespace.

To find the display name of a codespace:

* On GitHub, view your list of codespaces at <https://github.com/codespaces>.

  ![Screenshot of a list of three codespaces on the https://github.com/codespaces page."](/assets/images/help/codespaces/your-codespaces-list.png)

* In the Visual Studio Code desktop application, or the VS Code web client, click the Remote Explorer. The display name is the second item in the list. For example: `psychic chainsaw` in the screenshot below.

  ![Screenshot of the "Remote Explorer" in VS Code. The codespace display name, "psychic chainsaw," is highlighted with a dark orange outline.](/assets/images/help/codespaces/codespaces-remote-explorer.png)

  > \[!NOTE]
  > If the Remote Explorer is not displayed in the Activity Bar:
  >
  > 1. Access the Command Palette. For example, by pressing <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd> (Mac) / <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux).
  > 2. Type: `details`.
  > 3. Click **Codespaces: Details**.

* In a terminal window on your local machine, use this GitHub CLI command: `gh codespace list`.

### Permanent codespace names

In addition to a display name, every codespace also has a unique, permanent name. The permanent name is a combination of the initial display name, followed by some random characters - for example, `literate-space-parakeet-w5vg5ww5p793g7g9`. You can't change the permanent name.

You will occasionally need to know the permanent name of a codespace. For example, when you use some GitHub CLI commands, or when you discuss a particular codespace with GitHub support.

To find the permanent name of a codespace, do one of the following:

* Open the codespace in the browser. The subdomain of the URL is the name of the codespace. For example: `https://obscure-space-engine-grx7rgg6qp43v9j5.github.dev` is the URL for the `obscure-space-engine-grx7rgg6qp43v9j5` codespace.
* If you cannot open a codespace, you can access the name from your list of codespaces at <https://github.com/codespaces>. Right-click the display name of the codespace and select your browser's option for copying the link address. The final part of the URL you copy is the permanent name of the codespace.
* In a codespace, use this command in the terminal: `echo $CODESPACE_NAME`.
* If GitHub CLI is installed, either locally or in a codespace, use this command in the terminal to list all of your codespaces: `gh codespace list`.

The permanent name the codespace is also included in many of the log files. For example, in the GitHub Codespaces extension log, after `fetching codespace` or `Connecting to codespace`, and in the browser console log after `clientUrl`. For more information, see [GitHub Codespaces logs](/en/codespaces/troubleshooting/github-codespaces-logs).

## Renaming a codespace

Changing the display name of a codespace can be useful if you have multiple codespaces that you will be using for an extended period. An appropriate name helps you identify a codespace that you use for a particular purpose.

<div class="ghd-tool cli">

If you have installed GitHub CLI, you can use it to work with GitHub Codespaces. For installation instructions for GitHub CLI, see the [GitHub CLI repository](https://github.com/cli/cli#installation).

To change the display name of a codespace, use the `gh codespace edit` subcommand:

```shell
gh codespace edit -c PERMANENT-CODESPACE-NAME -d 'NEW-DISPLAY-NAME'
```

In this example, replace `PERMANENT-CODESPACE-NAME` with the permanent name of the codespace whose display name you want to change. Replace `NEW-DISPLAY-NAME` with the display name you want to use for this codespace.

Display names can be up to 48 characters in length. The display name can contain any combination of characters, including spaces, provided you enclose it in single quotes.

For more information, see [Using GitHub Codespaces with GitHub CLI](/en/codespaces/developing-in-a-codespace/using-github-codespaces-with-github-cli#rename-a-codespace).

</div>

<div class="ghd-tool webui">

You can change the display name for your codespace on GitHub.

1. In the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces** to take you to the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces).

   The current display name for each of your codespaces is displayed.

2. Click the ellipsis (**...**) to the right of the codespace you want to modify.

3. Click **Rename**.

4. In the prompt, under "Change display name to..." type your desired display name and click **OK**.

</div>

## Further reading

* [Setting your user preferences](/en/codespaces/setting-your-user-preferences)
* [Managing your codespaces](/en/codespaces/managing-your-codespaces)