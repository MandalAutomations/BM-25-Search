# Promoting or demoting a site administrator

Site administrators can promote any normal user account to a site administrator, as well as demote other site administrators to regular users.

> \[!NOTE] For information about promoting a user to an organization owner, see the `ghe-org-admin-promote` section of [Command-line utilities](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-org-admin-promote).

## Considerations with external authentication

If you use certain external authentication features, you may not be able to manage promotion and demotion from the enterprise settings or command line:

* If you use SAML authentication, and have *not* selected **Disable administrator demotion/promotion** in the SAML settings in the site admin dashboard, administrator rights will be determined by your SAML provider.
* If you have enabled SCIM provisioning, for SCIM-provisioned users, you must manage roles from your identity provider.
* If LDAP Sync is enabled, and the `Administrators group` attribute is set when configuring LDAP access for users, those users will automatically have site administrator access to your instance. To promote users, you must add them to the LDAP `Administrators group`.

## Promoting a user from the enterprise settings

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Under "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People", click **Administrators**.
4. In the upper-right corner of the page, click **Add owner**.
5. In the search field, type the name of the user, then click **Add**.

## Demoting a site administrator from the enterprise settings

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Under "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People", click **Administrators**.
4. In the upper-left corner of the page, in the "Find an administrator" search field, type the username of the person you want to demote.
5. In the search results, find the username of the person you want to demote, then select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Administrator settings" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg> dropdown menu and click **Convert to member**.

   ![Screenshot of a user in the enterprise administrators list. A dropdown menu, labeled with a kebab icon, is highlighted with an orange outline.](/assets/images/help/business-accounts/administrator-settings.png)

## Promoting a user from the command line

1. [SSH](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh) into your appliance.
2. Run [ghe-user-promote](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-user-promote) with the username to promote.

   ```shell
   ghe-user-promote USERNAME
   ```

## Demoting a site administrator from the command line

1. [SSH](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh) into your appliance.
2. Run [ghe-user-demote](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-user-demote) with the username to demote.

   ```shell
   ghe-user-demote USERNAME
   ```