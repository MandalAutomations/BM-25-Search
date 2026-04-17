# Deleting users from your instance

You can delete a user's account to permanently remove their data from GitHub.com.

## What happens when I delete a user account?

Deleting a user account removes all repositories, forks of private repositories, wikis, issues, pull requests, pages, and packages and container images owned by the user account. By deleting a user account, **you may break software projects and workflows that depend on these things.**

Issues and pull requests the user has created and comments they've made in repositories owned by other users or organizations will not be deleted and will instead be associated with a `ghost` user account.

Once a user account has been deleted, the username will be available for use with a different account on your GitHub Enterprise Server instance.

## When can I delete a user account?

You cannot delete a user that is currently an **organization owner**.

* **If the user is the only owner:** Transfer ownership to another person, or delete the organization. See [Transferring organization ownership](/en/enterprise-server@3.20/organizations/managing-organization-settings/transferring-organization-ownership) and [Deleting an organization account](/en/enterprise-server@3.20/organizations/managing-organization-settings/deleting-an-organization-account).
* **If there are other owners:** Remove the user from the organization. See [Removing yourself from an organization](/en/enterprise-server@3.20/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/removing-yourself-from-an-organization).

You cannot delete **your own user account**. If you need to delete your own user account, ask another site administrator to delete your account for you.

If you have enabled SCIM provisioning on your instance, you cannot delete **users who have been provisioned by SCIM**.

## Should I delete or suspend a user account?

GitHub recommends suspending users where possible, rather than deleting their accounts. Suspending user accounts on GitHub Enterprise Server preserves the history of resources owned by the user account, such as repositories and pull requests, and releases the license previously consumed by the user. See [Suspending and unsuspending users](/en/enterprise-server@3.20/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/suspending-and-unsuspending-users).

As an alternative to deleting or suspending a user account, to stop a user's repositories being permanently removed from your enterprise you can place a legal hold on the user account. See [Placing a legal hold on a user or organization](/en/enterprise-server@3.20/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/placing-a-legal-hold-on-a-user-or-organization).

## Deleting a user from the site admin dashboard

Before deleting a user account, you should consider if a backup or copy of the repositories, private forks, wikis, issues, and pull requests owned by the user account is required. See [Configuring backups on your instance using Backup Utilities](/en/enterprise-server@3.20/admin/backing-up-and-restoring-your-instance/configuring-backups-on-your-instance) and [Backing up a repository](/en/enterprise-server@3.20/repositories/archiving-a-github-repository/backing-up-a-repository).

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. Under "Search users, organizations, teams, repositories, gists, and applications", type the name of the user in the text field.
4. To the right of text field, click **Search**.
   ![Screenshot of the "Search" page of the "Site admin" settings. The button to search users, labeled "Search," is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/search-for-things.png)
   * If an exact account name match isn't found, under "Search results – Accounts", in the "Fuzzy matches" section, click the name of the user you want to manage.
     ![Screenshot of search results in the "Site admin" settings. In the "Fuzzy matches" section, an example user name is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/click-user.png)
5. Review the user details in the site admin page to confirm you have identified the correct user.
   ![Screenshot of the Site admin account overview page.](/assets/images/enterprise/site-admin-settings/site-admin-account-overview.png)
6. In the upper-right corner of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Admin**.
   ![Screenshot of the header of the "Site admin" page for a user or repository. The "Admin" tab is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/user/user-admin-tab-top.png)
7. Under "Delete account," in the "Danger Zone" section, click **Delete this account**.
8. In the "Delete account" dialog box, under "Make sure you want to do this", review the changes. To confirm, enter the username of the account to be deleted.
9. Click **Delete this account**.

## Further reading

* [REST API endpoints for enterprise users](/en/enterprise-server@3.20/rest/enterprise-admin/users#delete-a-user)