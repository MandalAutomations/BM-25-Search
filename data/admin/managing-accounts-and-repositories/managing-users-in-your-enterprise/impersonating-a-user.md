# Impersonating a user

You can impersonate users and perform actions on their behalf, for troubleshooting, unblocking, and other legitimate reasons.

## About user impersonation

If you need to temporarily take over a user account, for example when troubleshooting a user problem, or when the user is unavailable and urgent action is required, you can start an impersonation session to act on their behalf.

For each impersonation session, you need to provide a reason for the impersonation. A session is limited to one hour, and you will have the same access as the user being impersonated.

Actions you perform during an impersonation session are recorded as events in the enterprise audit log, as well as the impersonated user's security log. The person being impersonated is sent an email notification when the impersonation session starts. You cannot deactivate these emails. For more information, see [Audit log events for your enterprise](/en/enterprise-server@3.20/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/audit-log-events-for-your-enterprise) and [Reviewing your security log](/en/enterprise-server@3.20/authentication/keeping-your-account-and-data-secure/reviewing-your-security-log).

## Impersonating a user

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. Under "Search users, organizations, teams, repositories, gists, and applications", type the name of the user in the text field.
4. To the right of text field, click **Search**.
   ![Screenshot of the "Search" page of the "Site admin" settings. The button to search users, labeled "Search," is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/search-for-things.png)
   * If an exact account name match isn't found, under "Search results – Accounts", in the "Fuzzy matches" section, click the name of the user you want to manage.
     ![Screenshot of search results in the "Site admin" settings. In the "Fuzzy matches" section, an example user name is highlighted with an orange outline.](/assets/images/enterprise/site-admin-settings/click-user.png)
5. Review the user details in the site admin page to confirm you have identified the correct user.
   ![Screenshot of the Site admin account overview page.](/assets/images/enterprise/site-admin-settings/site-admin-account-overview.png)
6. In the top left of the page, click **User info**.

   ![Screenshot of the "User info" section for a user. The "User info" heading is outlined. Under the heading, the user is marked as active.](/assets/images/enterprise/stafftools/user-info.png)
7. Under "Danger Zone", click **Sign in to GitHub as @username**
8. Select a reason from the dropdown list. If you select **Other** you will need to provide additional context in the text field below **Notes**. Click **Begin impersonation** to begin the session.
9. When you are ready to end the impersonation session, click **Return to your mundane life as username** in the banner at the top of the page.