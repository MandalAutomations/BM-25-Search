# Adding organizations to your enterprise

Learn how to add organizations to your enterprise using three different methods.

There are three ways to add organizations to your enterprise.

* **Create** a new organization in your enterprise.
* **Invite** an existing organization to join your enterprise.
* **Transfer** an existing organization between enterprise accounts on GitHub.com.

<!-- expires 2027-01-30 -->

<!-- When this expires, check with the stakeholder for release #4079 on whether or not the content is still needed. See https://github.com/github/releases/issues/4079#issuecomment-3954280272 for context. -->

If you currently use GitHub Enterprise Cloud with a single organization, we encourage you to create an enterprise account.

<!-- end expires 2027-01-30 --> See [AUTOTITLE](/admin/managing-your-enterprise-account/creating-an-enterprise-account).

## Limitations

If you use GitHub Enterprise Cloud with data residency, you cannot transfer organizations between GitHub.com and your enterprise on GHE.com. Instead, you must migrate organizations with the GitHub Enterprise Importer. See [About migrations between GitHub products](/en/enterprise-cloud@latest/migrations/using-github-enterprise-importer/migrating-between-github-products/about-migrations-between-github-products).

If you use Enterprise Managed Users, the following limitations apply:

* Adding existing organizations to your enterprise is not possible.
* Existing organizations from an enterprise with managed users cannot be added to a different enterprise.

## Changes when adding an existing organization

After you add an existing organization to your enterprise, the organization's resources remain accessible to members at the same URLs, and the following changes will apply.

* **Two-factor authentication (2FA):** If required by the enterprise, members without 2FA, or with insecure 2FA, will be unable to access organization resources until they configure 2FA that meets the enterprise's 2FA security requirements.

* **Enterprise licenses:** Members become part of the enterprise, and usage is billed to the enterprise account. You must ensure that the enterprise account has enough licenses to accommodate any new members. See [Billing for GitHub Enterprise](/en/enterprise-cloud@latest/billing/managing-your-billing/about-billing-for-your-enterprise).

* **Enterprise role management:** Enterprise owners can manage their roles within the organization. See [Managing your role in an organization owned by your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-organizations-in-your-enterprise/managing-your-role-in-an-organization-owned-by-your-enterprise).

* **Enterprise policies:** Any policies applied to the enterprise will apply to the organization. If the organization has write permissions for GitHub Actions, you must manually set write permissions for the enterprise. For more information, see [Managing GitHub Actions settings for a repository](/en/enterprise-cloud@latest/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#managing-github-actions-permissions-for-your-repository). For more information about managing organization-level permissions for GitHub Actions, see [Disabling or limiting GitHub Actions for your organization](/en/enterprise-cloud@latest/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#managing-github-actions-permissions-for-your-organization).

* **SAML SSO Configuration:**

  * If SAML SSO is configured **for the destination enterprise**, the enterprise's SAML configuration will apply to the organization.
    * If SAML is currently configured on the organization, the enterprise account's SAML configuration will override the organization's configuration. SCIM is not available at the enterprise level for enterprises that use personal accounts, so SCIM will be disabled for the organization. The new inherited enterprise SAML settings will be displayed on the organization's SAML settings page.
    * If SAML is ever disabled for the enterprise, the organization SAML settings will revert back to their original configuration.
  * If SAML is **not** configured for the destination enterprise, the organization will retain any existing SAML and SCIM settings.
  * If organization members have existing SAML authorizations for personal access tokens or SSH keys to access the organization, these authorizations will remain active.
    * To see these authorizations, SAML must be configured for either the organization or enterprise, and the user must have a linked SAML identity.
    * To access additional organizations owned by the enterprise, members must authorize the personal access token or key. See [Authorizing a personal access token for use with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on/authorizing-a-personal-access-token-for-use-with-saml-single-sign-on) and [Authorizing an SSH key for use with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on/authorizing-an-ssh-key-for-use-with-saml-single-sign-on).

* **Trial enterprise:** Certain features may be disabled if added to a trial enterprise. See [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud#features-not-included-in-the-trial).

* **GitHub Connect:** If the organization was connected to GitHub Enterprise Server using GitHub Connect, adding the organization to an enterprise will not update the connection. GitHub Connect features will no longer function for the organization. To continue using GitHub Connect, you must disable and re-enable the feature. See [Enabling GitHub Connect for GitHub.com](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/managing-github-connect) in the GitHub Enterprise Server documentation.

* **GitHub Marketplace apps:** If you add a standalone organization that uses billed GitHub Marketplace apps, the organization can continue to use the apps, but usage will be billable to the enterprise.
  * If your enterprise is billed via invoice, contact the app vendor and pay directly.
  * If your enterprise is billed via credit card or PayPal, billing continues automatically.
    To transfer an existing organization with billed apps between enterprise accounts, first remove the billed apps and then re-add the apps after the transfer is complete.

* **Sponsorships:** Any sponsorships by the organization will be canceled.

* **Coupons:** Any coupons will be removed from the organization. To reapply the coupon, [contact our sales team](https://github.com/enterprise/contact).

## Handling GitHub Sponsors with Azure billing

If your organization is added to an enterprise account with Azure metered billing, any active GitHub Sponsors sponsorships will be canceled. While your organization remains under enterprise billing through Azure, you will not be able to reactivate these sponsorships, as sponsoring is not currently supported for organizations billed through Azure.

To continue using GitHub Sponsors, create a new, separate "shell" organization that is not linked to your enterprise account or Azure billing. You can use this shell organization to manage sponsorships independently.

> \[!NOTE]
> After you create a shell organization, update any public references or documentation to point sponsors to the new organization.

## Creating a new organization

New organizations you create within your enterprise account settings are included in your enterprise account's GitHub Enterprise Cloud subscription.

Enterprise owners who create an organization owned by the enterprise account automatically become organization owners. See [Roles in an organization](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization).

During a trial of GitHub Enterprise Cloud, you can create up to three new organizations in your enterprise.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. Under the enterprise name, click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> **Organizations** tab.

   ![Screenshot of an enterprise. The "Organizations" tab is highlighted with an orange outline.](/assets/images/help/enterprises/organizations-tab.png)
3. Above the list of organizations, click **New organization**.
4. Under "Organization name," type a name for your organization.
5. Click **Create organization**.
6. Optionally, under "Invite owners," type the username of a person you'd like to invite to become an organization owner, then click **Invite**.
7. Click **Finish**.

## Inviting an existing organization

Enterprise owners can invite existing organizations to join their enterprise account.

During a trial of GitHub Enterprise Cloud, you can invite organizations to join your trial enterprise. You can invite organizations that are not currently owned by another enterprise. If an organization you want to invite is already owned by another enterprise, you cannot invite it to your trial enterprise.

After you invite the organization, and before an owner approves the invitation, you can cancel or resend the invitation at any time.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. Under the enterprise name, click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> **Organizations** tab.

   ![Screenshot of an enterprise. The "Organizations" tab is highlighted with an orange outline.](/assets/images/help/enterprises/organizations-tab.png)
3. Above the list of organizations, click **Invite organization**.
4. Under "Organization name," start typing the name of the organization you want to invite and select it when it appears in the dropdown list.
5. Click **Invite organization**. The organization owners will receive an email inviting them to join the enterprise.
6. After an organization owner has approved the invitation, navigate back to the **Organizations** tab of the enterprise settings.
7. Under "Organizations," click **X pending**.
8. To complete the transfer, next to the organization name, click **Approve**.

## Transferring an existing organization

Enterprise owners can transfer existing organizations between enterprise accounts. You must be an enterprise owner of both enterprise accounts.

You cannot transfer an existing organization to or from an enterprise with managed users or an enterprise account that is currently enrolled in a trial of GitHub Enterprise Cloud.

If the existing organization uses billed apps, make sure to remove the billed apps before transferring. After the transfer is complete, re-add the apps.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. Under the enterprise name, click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> **Organizations** tab.

   ![Screenshot of an enterprise. The "Organizations" tab is highlighted with an orange outline.](/assets/images/help/enterprises/organizations-tab.png)

3. Next to the organization you want to transfer, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Organization settings" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> dropdown menu, then click **Transfer organization**.

   ![Screenshot of the expanded dropdown menu labeled with the kebab icon, for an organization. The "Transfer organization" option is outlined.](/assets/images/help/business-accounts/transfer-organization.png)

4. Select the **Select enterprise** dropdown menu, start typing the name of the destination enterprise, and click the enterprise you want to transfer the organization to.

5. Click **Review transfer**.

6. To confirm the transfer, click **Transfer organization**.