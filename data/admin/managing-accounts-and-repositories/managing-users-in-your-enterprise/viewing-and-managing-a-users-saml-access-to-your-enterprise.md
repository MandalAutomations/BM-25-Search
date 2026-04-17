# Viewing and managing a user's SAML access to your enterprise

You can view and revoke an enterprise member's active SAML sessions.

## About SAML access to your enterprise account

When you enable SAML single sign-on for your enterprise account, each enterprise member can link their external identity on your identity provider (IdP) to their existing account on GitHub.com. To access each organization's resources on GitHub, the member must have an active SAML session in their browser. To access each organization's protected resources using the API and Git, the member must use a personal access token or SSH key that the member has authorized for use with the organization. Enterprise owners can view and revoke a member's linked identity, active sessions, or authorized credentials at any time.

If your enterprise is uses Enterprise Managed Users, your members will use accounts provisioned through your IdP. Managed user accounts will not use their existing user account on GitHub. For more information, see [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/about-enterprise-managed-users).

## Viewing and revoking a linked identity

You can view the single sign-on identity that a member has linked to their account on GitHub.

If a member links the wrong identity to their account on GitHub, you can revoke the linked identity to allow the member to try again.

If your enterprise uses Enterprise Managed Users, you will not be able to deprovision or remove user accounts from the enterprise via GitHub. Any changes you need to make to your enterprise's managed user accounts should be made through your IdP.

> \[!WARNING]
> If your organization uses team synchronization, revoking a person's SSO identity will remove that person from any teams mapped to IdP groups. For more information, see [Synchronizing a team with an identity provider group](/en/enterprise-cloud@latest/organizations/organizing-members-into-teams/synchronizing-a-team-with-an-identity-provider-group).

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Click on the name of the member whose linked identity you'd like to view or revoke.
4. In the left sidebar, click **SAML identity linked**.

   ![Screenshot of the people summary for @octocat. A link, labeled "SAML identity linked", is highlighted with an orange outline.](/assets/images/help/saml/saml-identity-linked.png)
5. Under "Linked SSO identity", view the linked SSO identity for the member.
6. To revoke the linked identity, to the right of the identity, click **Revoke**.
7. Read the information, then click **Revoke external identity**.

## Viewing and revoking an active SAML session

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Click on the name of the member whose SAML session you'd like to view or revoke.
4. In the left sidebar, click **SAML identity linked**.

   ![Screenshot of the people summary for @octocat. A link, labeled "SAML identity linked", is highlighted with an orange outline.](/assets/images/help/saml/saml-identity-linked.png)
5. Under "Active SAML sessions", view the active SAML sessions for the member.
6. To revoke a session, to the right of the session you'd like to revoke, click **Revoke**.

## Viewing and revoking authorized credentials

You can see each personal access token and SSH key that a member has authorized for API and Git access. Only the last several characters of each token or key are visible. If necessary, work with the member to determine which credentials you should revoke. Be aware that revoking a credential only removes the SAML authorization. It does not delete the underlying token or SSH key.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Click on the name of the member whose authorized credentials you'd like to view or revoke.
4. In the left sidebar, click **SAML identity linked**.

   ![Screenshot of the people summary for @octocat. A link, labeled "SAML identity linked", is highlighted with an orange outline.](/assets/images/help/saml/saml-identity-linked.png)
5. Under "Authorized credentials", view the authorized credentials for the member.
6. To revoke credentials, to the right of the credentials you'd like to revoke, click **Revoke**.
7. Read the information, then click **I understand, revoke access for this token.**

## Further reading

* [Viewing and managing a member's SAML access to your organization](/en/enterprise-cloud@latest/organizations/granting-access-to-your-organization-with-saml-single-sign-on/viewing-and-managing-a-members-saml-access-to-your-organization)