# Choosing who owns and pays for codespaces in your organization

You can choose whether codespaces are paid for and owned by your organization or by your members.

## Overview

If you're the owner of an organization on a GitHub Team or GitHub Enterprise Cloud plan, you can pay for your members' and collaborators' usage of GitHub Codespaces. Paying for usage will allow people to use GitHub Codespaces to work in your repositories without having to do so at their own expense and will give your organization more control over the codespaces created from your repositories.

To pay for usage, you must do all of the following things:

* Allow at least some of your members and collaborators to use GitHub Codespaces in your organization's private repositories. See [Enabling or disabling GitHub Codespaces for your organization](/en/codespaces/managing-codespaces-for-your-organization/enabling-or-disabling-github-codespaces-for-your-organization#enabling-or-disabling-github-codespaces).
* Choose for codespaces created from your organization's repositories to be **organization-owned**. See [Choosing who owns and pays for codespaces](#choosing-who-owns-and-pays-for-codespaces).
* Set a non-zero spending limit for GitHub Codespaces. See [Setting up budgets to control spending on metered products](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/managing-the-spending-limit-for-github-codespaces#managing-the-github-codespaces-spending-limit-for-your-organization-account).

## About choosing who pays for codespaces

Paying for a codespace means paying for the storage and compute costs of the codespace over the codespace's lifetime. See [GitHub Codespaces billing](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/about-billing-for-github-codespaces).

Organizations on a GitHub Free plan cannot pay for GitHub Codespaces, so the user who creates the codespace always pays.

For organizations on a GitHub Team or GitHub Enterprise Cloud plan, when a user creates a codespace from a repository in the organization, either the user or the organization can pay for the codespace. The user who creates a codespace can't choose who pays for it, but the organization can choose to pay for certain users. In an organization's settings, you can choose for codespaces to be **user-owned** or **organization-owned**.

If an organization chooses for codespaces to be **user-owned**, a user who creates a codespace from a repository in the organization always pays for the codespace. The user's access to create codespaces depends on the visibility of the repository and your organization's access settings.

If an organization chooses for codespaces to be **organization-owned**, the organization will pay for a codespace if all the following things are true:

* The organization has no budget defined for GitHub Codespaces or has set a non-zero budget.
* The codespace is created from one of the organization's repositories, or from a fork of one of the organization's repositories. This includes both public and private repositories.
* The user creating the codespace is a member or collaborator of the organization, and the organization has enabled GitHub Codespaces for this user. This can include all members and collaborators if the organization has chosen to enable Codespaces for all users. If Codespaces isn't enabled for a user, they can still create codespaces from public repositories in the organization, but the user will pay for these codespaces.

For more information about enabling GitHub Codespaces for members and collaborators, see [Enabling or disabling GitHub Codespaces for your organization](/en/codespaces/managing-codespaces-for-your-organization/enabling-or-disabling-github-codespaces-for-your-organization).

## About ownership of codespaces

A codespace is paid for by the account that owns it. The codespace owner can be the user who created the codespace, or it can be an organization.

If your organization owns a codespace, your organization has control over that codespace. For example, for codespaces owned by your organization, you can:

* Use the [REST API](/en/rest/codespaces/organizations) to manage codespaces, such as stopping or deleting a codespace
* Access audit logs to review actions related to GitHub Codespaces
* Set policies to manage constraints, such as restricting the dev container image or machine type that can be used in codespaces, or setting a default timeout and retention period

If a user owns a codespace, your organization does not have any of these options for managing the codespace, even if the codespace was created from one of your organization's repositories.

When a user creates a codespace, they're told who will pay for it, and therefore who owns it. From a user's point of view, apart from the policies your organization can use to set constraints on codespaces, the experience with GitHub Codespaces will be similar regardless of who owns a codespace. For example, most of a user's personal settings for GitHub Codespaces, such as dotfiles, secrets, and GPG verification, apply regardless of who owns the codespace.

## About changing your settings

When you change your ownership settings, existing codespaces can transfer to a new owner.

If you change from **organization ownership** to **user ownership**, codespaces that are currently owned by your organization will be transferred to the ownership of the user who created the codespace. Before you make this change, you should ask each user to review the codespaces that will be transferred to their ownership. These codespaces will now incur usage on the user's personal account.

If you change from **user ownership** to **organization ownership**, existing codespaces may be transferred to your organization's ownership. A codespace will be transferred if the user who currently owns the codespace is a member or collaborator, and you have enabled GitHub Codespaces for this user. Otherwise, a codespace will remain under the ownership of the user.

## Choosing who owns and pays for codespaces

> \[!NOTE]
> If you cannot access the option to make codespaces **organization-owned**, this may be because you have disabled GitHub Codespaces for all users in your organization's private repositories. See [About choosing who pays for codespaces](#about-choosing-who-pays-for-codespaces).

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.

2. Select an organization by clicking on it.

3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)

4. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces**.

5. Under **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codespaces" aria-label="codespaces" role="img"><path d="M0 11.25c0-.966.784-1.75 1.75-1.75h12.5c.966 0 1.75.784 1.75 1.75v3A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm2-9.5C2 .784 2.784 0 3.75 0h8.5C13.216 0 14 .784 14 1.75v5a1.75 1.75 0 0 1-1.75 1.75h-8.5A1.75 1.75 0 0 1 2 6.75Zm1.75-.25a.25.25 0 0 0-.25.25v5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5a.25.25 0 0 0-.25-.25Zm-2 9.5a.25.25 0 0 0-.25.25v3c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-3a.25.25 0 0 0-.25-.25Z"></path><path d="M7 12.75a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Zm-4 0a.75.75 0 0 1 .75-.75h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1-.75-.75Z"></path></svg> Codespaces**, in the left sidebar, click **General**.

6. On the Codespaces settings page, under "Codespace ownership," select the setting you want for your organization:
   * **Organization ownership:** Codespaces can be owned and paid for by your organization.
   * **User ownership:** Codespaces are always owned and paid for by the user who creates the codespace.

7. Optionally, under "Codespaces access," review the members and collaborators for whom you have enabled Codespaces. These are the only users who can create codespaces that your organization pays for. See [Enabling or disabling GitHub Codespaces for your organization](/en/codespaces/managing-codespaces-for-your-organization/enabling-or-disabling-github-codespaces-for-your-organization).

## Setting a spending limit

Accounts may have spending limits that prevent new codespaces being created, or existing codespaces being opened, if doing so would incur a billable cost to your personal, organization, or enterprise account. Check your account's budgets to ensure they are appropriate for your usage needs. See [Setting up budgets to control spending on metered products](/en/billing/managing-your-billing/using-budgets-control-spending).

For information on managing and changing your account's spending limit, see [Setting up budgets to control spending on metered products](/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/managing-the-spending-limit-for-github-codespaces#managing-the-github-codespaces-spending-limit-for-your-organization-account).