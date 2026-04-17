# Changing the machine type for your codespace

You can change the type of machine that's running your codespace, so that you're using resources appropriate for the work you're doing.

## About machine types

Typically, you can run your codespace on a choice of remote machine types. These machine types offer a choice of hardware specifications ranging from 2 cores to 32 cores, although the full range of machine types may not always be available. Each machine type has a different level of resources and a different billing tier. For information, see [GitHub Codespaces billing](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/about-billing-for-github-codespaces).

By default the machine type with the lowest valid resources is used when you create a codespace. You can choose an alternative machine type either when you create a codespace or at any time after you've created a codespace.

For information on choosing a machine type when you create a codespace, see [Creating a codespace for a repository](/en/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository#creating-a-codespace-for-a-repository).

Unpublished codespaces (codespaces created from a template that are not linked to a repository on GitHub) always run on a virtual machine with the same specifications. You can't change the machine type of an unpublished codespace. For more information, see [Creating a codespace from a template](/en/codespaces/developing-in-a-codespace/creating-a-codespace-from-a-template).

## Changing the machine type

> \[!NOTE]
> Your choice of available machine types may be limited by a number of factors. These can include a policy configured for your organization, or a minimum machine type specification for your repository. For more information, see [Restricting access to machine types](/en/codespaces/managing-codespaces-for-your-organization/restricting-access-to-machine-types) and [Setting a minimum specification for codespace machines](/en/codespaces/setting-up-your-project-for-codespaces/configuring-dev-containers/setting-a-minimum-specification-for-codespace-machines).

<div class="ghd-tool webui">

1. In the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces** to take you to the "Your codespaces" page at [github.com/codespaces](https://github.com/codespaces).

   The number of cores, memory, storage capacity, and currently used storage are displayed for each codespace. Some details are omitted if you are using a narrow browser window.

   ![Screenshot of a list of three codespaces on the https://github.com/codespaces page."](/assets/images/help/codespaces/your-codespaces-list.png)

2. Click the ellipsis (**...**) to the right of the codespace you want to modify.

3. Click **Change machine type**.

   ![Screenshot of the dropdown menu for a codespace. The "Change machine type" option is highlighted.](/assets/images/help/codespaces/change-machine-type-menu-option.png)

4. If multiple machine types are available for your codespace, choose the type of machine you want to use.

   ![Screenshot of a dialog showing two available machine types: 2-core and 4-core.](/assets/images/help/codespaces/change-machine-type-choice.png)

5. Click **Update codespace**.

</div>

<div class="ghd-tool vscode">

1. In VS Code, open the Command Palette with <kbd>Command</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Mac) or <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux).

2. Search for and select "Codespaces: Change Machine Type."

   ![Screenshot of "change machine" entered as a search string and "Codespaces: Change Machine Type" in the dropdown list.](/assets/images/help/codespaces/vscode-change-machine-type-option.png)

3. If you're not following these instructions within a codespace, click the codespace that you want to change.

   ![Screenshot of a dropdown list of four codespaces.](/assets/images/help/codespaces/vscode-change-machine-choose-repo.png)

   If you are following these instructions in a codespace, the change will apply to the codespace you're working in.

4. Select the machine type you want to use.

5. If you're changing to a machine type with a different storage capacity, a prompt will appear asking if you would like to continue. Read the prompt and click **Yes** to accept.

</div>

<div class="ghd-tool cli">

If you have installed GitHub CLI, you can use it to work with GitHub Codespaces. For installation instructions for GitHub CLI, see the [GitHub CLI repository](https://github.com/cli/cli#installation).

You can use the `gh codespace edit --machine MACHINE-TYPE-NAME` GitHub CLI command to change the machine type of a codespace. To use this command, you'll first need to find out the available machine types for your codespace.

1. To view your list of codespaces, in a terminal, enter the following command.

   ```shell
   gh codespace list
   ```

2. Optionally, to find the current machine type for a codespace, enter the following command.

   ```shell
   gh api /user/codespaces/CODESPACE-NAME
   ```

   Replace `CODESPACE-NAME` with the permanent name of the codespace, for example `literate-space-parakeet-w5vg5ww5p793g7g9`. The permanent names are listed under the **NAME** column in the list returned by `gh codespace list`.

   If you're prompted to request the `codespace` scope, follow the instructions in the terminal.

   Details for the current machine are listed under the `machine` field.

3. To find the available machine types for a codespace, enter the following command.

   ```shell
   gh api /user/codespaces/CODESPACE-NAME/machines
   ```

   Replace `CODESPACE-NAME` with the permanent name of the codespace, for example `literate-space-parakeet-w5vg5ww5p793g7g9`.

4. To change the machine type for a codespace, enter the following command.

   ```shell
   gh codespace edit --machine MACHINE-TYPE-NAME
   ```

   Replace `MACHINE-TYPE-NAME` with the name of an available machine type for your codespace, for example `standardLinux32gb`.

5. Using the arrow keys, navigate to the codespace you want to change, then press <kbd>Enter</kbd>.

</div>

If you changed to a virtual machine with a different storage capacity (for example, from 32 GB to 64 GB), your codespace will be unavailable for a short time while the machine type is changed. If the codespace is currently active, it will automatically be stopped. When the change is complete, you'll be able to restart the codespace running on the new machine type.

If you changed to a virtual machine with the same storage capacity, the change will be applied the next time you restart the codespace. An active codespace will not be stopped automatically. For more information on restarting a codespace, see [Stopping and starting a codespace](/en/codespaces/developing-in-codespaces/stopping-and-starting-a-codespace#restarting-a-codespace).

<div class="ghd-tool cli">

## Further reading

* [REST API endpoints for Codespaces machines](/en/rest/codespaces/machines)
* [`gh codespace edit`](https://cli.github.com/manual/gh_codespace_edit) in the GitHub CLI manual
* [Setting your user preferences](/en/codespaces/setting-your-user-preferences)
* [Managing your codespaces](/en/codespaces/managing-your-codespaces)

</div>