# Viewing people in your enterprise

To audit access to enterprise-owned resources or user license usage, enterprise owners can view every administrator and member of the enterprise.

> \[!NOTE] If your enterprise uses managed user accounts, the outside collaborator role is called "repository collaborator." Generally, the documentation for outside collaborators also applies to repository collaborators. For the distinctions that apply, see [Roles in an organization](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization#outside-collaborators-or-repository-collaborators).

## About the list of people in your enterprise

To audit access to your enterprise's resources and manage license usage, you can see a list of all the people who have access to your enterprise.

You can see all current enterprise members and enterprise administrators, as well as pending invitations to become members and administrators. To make it easier to consume this information, you can search and filter the lists. You can also view an overview of the number of members in your enterprise, grouped by role, type of license, or type of deployment.

If GitHub Connect is configured for your enterprise, when you filter a list of people in your enterprise, the following limitations apply.

* The filter for two-factor authentication (2FA) status does not show people who only have an account on a GitHub Enterprise Server instance.
* If you combine the filter for accounts on GitHub Enterprise Server instances with either the filter for organizations or 2FA status, you will not see any results.

For more information about GitHub Connect, see [About GitHub Connect](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/about-github-connect) in the GitHub Enterprise Server documentation.

You can also export membership information for your enterprise. For more information, see [Exporting membership information for your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/exporting-membership-information-for-your-enterprise).

## Viewing enterprise administrators

You can view all the current enterprise owners and billing managers for your enterprise. You can see useful information about each administrator and filter the list by role. You can find a specific person by searching for their username or display name.

You can also remove an administrator. For more information. see [Inviting people to manage your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/inviting-people-to-manage-your-enterprise#removing-an-enterprise-administrator-from-your-enterprise-account).

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Under "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People", click **Administrators**.

## Viewing members

You can see all the current members for your enterprise. You can see useful information about each account and filter the list in useful ways, such as by role. In addition to the list of members, you will see an overview of the number of members in your enterprise, grouped by role, type of license, and type of deployment.

You can find a specific person by searching for the person's username or display name. To view more information about the person's access to your enterprise, such as the organizations the person belongs to, you can select the person's name.

You can also remove any enterprise member from all organizations owned by the enterprise. For more information, see [Removing a member from your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/removing-a-member-from-your-enterprise).

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.

3. Optionally, to export the list of members as a CSV report, select **CSV report**. For more information about the information included in the report, see [Exporting membership information for your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/exporting-membership-information-for-your-enterprise).

### About the membership overview

On the "Members" page, you will find an overview of the number of members in your enterprise, grouped by role, type of license consumed, and the type of deployment the member is on. The following sections explain how the numbers in this overview are calculated.

If your enterprise uses both GitHub Enterprise Cloud and GitHub Enterprise Server, to get accurate data about your members and licenses across your deployments, you will need to enable GitHub Connect and synchronize license usage. For more information, see [About GitHub Connect](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/about-github-connect) in the GitHub Enterprise Server documentation.

#### Roles

The "Roles" column groups members by their role in the enterprise. For more information, see [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/roles-in-an-enterprise).

If a user has multiple roles in an enterprise, the user is counted once for each role. For example, if the same user is a member of three organizations and an owner of two organizations, the user counts once towards "Organization member" and once towards "Organization owner."

An "outside collaborator" is a user who has access to a repository in an organization, but is not a member of the organization. The user might be an outside collaborator in one organization in your enterprise and a member of another organization. In this case, the user counts towards each total. For more information, see [Adding outside collaborators to repositories in your organization](/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-outside-collaborators/adding-outside-collaborators-to-repositories-in-your-organization).

#### User licenses consumed

The "User licenses consumed" column shows you how licenses are consumed in your enterprise. For more information, see [Combined GitHub Enterprise cloud and server use](/en/enterprise-cloud@latest/billing/managing-your-license-for-github-enterprise/about-licenses-for-github-enterprise).

If there are outside collaborators in your enterprise, the "total consumed" number of licenses may be larger than the number of people listed for your enterprise. An outside collaborator consumes a license, but is not counted in the total member count displayed next to "people in YOUR-ENTERPRISE". A pending invitation to an outside collaborator also consumes a license, but is not counted in the "By invitations" count in the overview.

For more information about how license usage is calculated across deployments, see [Troubleshooting license usage for GitHub Enterprise](/en/enterprise-cloud@latest/billing/managing-your-license-for-github-enterprise/troubleshooting-license-usage-for-github-enterprise#about-the-calculation-of-consumed-licenses).

#### Deployment

The "Deployment" column groups users by the type of deployment they are using. For more information, see [About GitHub for enterprises](/en/enterprise-cloud@latest/admin/overview/about-github-for-enterprises#about-deployment-options).

"Cloud members" are a member or owner of any organization in your enterprise on GitHub Enterprise Cloud. "Server members" have an account on a GitHub Enterprise Server instance owned by your enterprise. "Members on cloud and server" are users who match both these criteria.

## Viewing members' email addresses

You may be able to view the email addresses for members of your enterprise on either GitHub or an external identity system. The visibility of the email addresses depends on your enterprise's authentication method, domains, and potentially the member's user profile configuration.

* If you use Enterprise Managed Users and the `NameID` for your SAML configuration is an email address, you can view the `NameID` for each of your enterprise members.

* If you verify a domain for your enterprise, you can view members' email addresses for the verified domain. For more information, see [Verifying or approving a domain for your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-your-enterprise/verifying-or-approving-a-domain-for-your-enterprise).

* If you don't use Enterprise Managed Users, and you also don't configure SAML single sign-on (SSO), members access your enterprise's resources on GitHub solely using a personal account. The owner of a personal account can choose whether or not to publicly display an email address. If a user chooses not to display the email address, you cannot view the email address. Without SAML, GitHub cannot display external identity information, like the `NameID`, which is typically an email address.

If you use Enterprise Managed Users, verify a domain, or configure SAML SSO for your enterprise, you may be able to view the email addresses in one or more of the following ways.

1. On your SAML Identity Provider (IdP), review the email addresses of users with access to your enterprise. For more information, see [About SAML for enterprise IAM](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/about-saml-for-enterprise-iam).
2. Export the membership report for your enterprise on GitHub. The report may contain the user's email address, stored as the following values.

   * `GitHub com saml name`: The `NameID` from the user's linked SAML identity, which is typically the user's email address (for more information, see [SAML configuration reference](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/saml-configuration-reference))
   * `GitHub com verified domain emails`: Email addresses for any verified domains (for more information, see [Verifying or approving a domain for your enterprise](/en/enterprise-cloud@latest/admin/configuration/configuring-your-enterprise/verifying-or-approving-a-domain-for-your-enterprise))

   For more information, see [Exporting membership information for your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/exporting-membership-information-for-your-enterprise).
3. Use the GraphQL API to retrieve the `ExternalIdentity` for each member. For more information, see [About the GraphQL API](/en/enterprise-cloud@latest/graphql/overview/about-the-graphql-api) and [Objects](/en/enterprise-cloud@latest/graphql/reference/objects#externalidentity) in the GraphQL API documentation.

## Viewing outside collaborators

You can see all the current outside collaborators for your enterprise. You can see useful information about each collaborator and filter the list in useful ways, such as by organization. You can find a specific collaborator by searching for their username or display name.

You can view more information about the person's access to your enterprise, such as a list of all the repositories the collaborator has access to, by selecting the person's name.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Under "People", select **Outside collaborators**.

## Viewing pending invitations

You can see all the pending invitations to become members, administrators, or outside collaborators in your enterprise. You can filter the list in useful ways, such as by license, by organization, or by source. You can find a specific person by searching for their username or display name.

In the list of pending members, for any individual account, you can cancel all invitations to join organizations owned by your enterprise. This does not cancel any invitations for that same person to become an enterprise administrator or outside collaborator.

> \[!NOTE]
> If an invitation was provisioned via SCIM, you must cancel the invitation via your identity provider (IdP) instead of on GitHub.

If you use Visual Studio subscriptions with GitHub Enterprise, the list of pending invitations includes all Visual Studio subscribers that haven't joined any of your organizations on GitHub, even if the subscriber does not have a pending invitation to join an organization. For more information about how to get Visual Studio subscribers access to GitHub Enterprise, see [Setting up Visual Studio subscriptions with GitHub Enterprise](/en/enterprise-cloud@latest/billing/managing-billing-for-your-products/managing-licenses-for-visual-studio-subscriptions-with-github-enterprise/setting-up-visual-studio-subscriptions-with-github-enterprise).

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Under "People", select **Invitations**.
4. Optionally, you can cancel all invitations for an account to join organizations owned by your enterprise. To the right of the account, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Show actions" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then select **Cancel invitation**.

   ![Screenshot of a single invitation on the "Invitations" page. A button, titled "Cancel invitation", is highlighted with an orange outline.](/assets/images/help/enterprises/cancel-enterprise-member-invitation.png)
5. Optionally, you can view pending invitations for enterprise administrators or outside collaborators. Under "Invitations", select **Administrators** or **Outside collaborators**.
6. Optionally, to filter the list of pending invitations by license, by organization, or by source, use the dropdown menus at the top of the list.

   ![Screenshot of the "Invitations" page. Three dropdown menus, titled "License", "Organizations", and "Source" are highlighted with an orange outline.](/assets/images/help/enterprises/enterprise-filter-pending-invitations.png)

## Viewing suspended members

If your enterprise uses Enterprise Managed Users, you can view suspended users. Suspended users are members who have been deprovisioned after being unassigned from the application or deleted on the identity provider. Currently, it is not possible to remove suspended users from an enterprise that uses Enterprise Managed Users.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. Under "People", select **Suspended**.

## Viewing dormant users

You can view a list of all dormant users who are not site administrators. A user account is considered to be dormant if it has not been active for 30 days.  For more information, see [Managing dormant users](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/managing-dormant-users).

## Filtering by member type in an enterprise with managed users

If your enterprise uses Enterprise Managed Users, you can filter the member list of an organization by type to determine if memberships are managed through an IdP or managed directly. Memberships managed through an IdP were added through an IdP group, and the IdP group was connected to a team within the organization. Memberships managed directly were added to the organization manually. The way a membership is managed in an organization determines how it must be removed. You can use this filter to determine how members were added to an organization, so you know how to remove them. For more information, see [About Enterprise Managed Users](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/about-enterprise-managed-users#about-organization-membership-management).

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. Under "Organizations", in the search bar, begin typing the organization's name until it appears in the search results.
3. Select the name of the organization.
4. Above the organization name, select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.

   ![Screenshot of the tabs above an organization name. The "People" tab is highlighted with an orange outline.](/assets/images/help/enterprises/emu-organization-people-tab.png)
5. Above the list of members, select **Type**, then select the type of members you want to view.
   ![Screenshot of the list of members. A dropdown menu labeled "Type" is outlined and expanded.](/assets/images/help/enterprises/filter-by-member-type.png)

## Viewing members without an email address from a verified domain

You can view a list of members in your enterprise who don't have an email address from a verified domain associated with their user account.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. Under "Settings", click **Verified & approved domains**.
4. Under "Notification preferences", select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-eye" aria-label="eye" role="img"><path d="M8 2c1.981 0 3.671.992 4.933 2.078 1.27 1.091 2.187 2.345 2.637 3.023a1.62 1.62 0 0 1 0 1.798c-.45.678-1.367 1.932-2.637 3.023C11.67 13.008 9.981 14 8 14c-1.981 0-3.671-.992-4.933-2.078C1.797 10.83.88 9.576.43 8.898a1.62 1.62 0 0 1 0-1.798c.45-.677 1.367-1.931 2.637-3.022C4.33 2.992 6.019 2 8 2ZM1.679 7.932a.12.12 0 0 0 0 .136c.411.622 1.241 1.75 2.366 2.717C5.176 11.758 6.527 12.5 8 12.5c1.473 0 2.825-.742 3.955-1.715 1.124-.967 1.954-2.096 2.366-2.717a.12.12 0 0 0 0-.136c-.412-.621-1.242-1.75-2.366-2.717C10.824 4.242 9.473 3.5 8 3.5c-1.473 0-2.825.742-3.955 1.715-1.124.967-1.954 2.096-2.366 2.717ZM8 10a2 2 0 1 1-.001-3.999A2 2 0 0 1 8 10Z"></path></svg> View enterprise members without an approved or verified domain email** link.

## Viewing whether members in your enterprise have 2FA enabled

You can see which people in your enterprise have enabled two-factor authentication.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. To view the two-factor authentication security levels of enterprise members, on the right, select **Two-factor authentication**, then select **Secure**, **Insecure**, or **Disabled**.

   ![Screenshot of the list of enterprise members. A dropdown menu, labeled "Two-factor authentication", is expanded and outlined in orange.](/assets/images/help/2fa/filter-enterprise-members-by-2fa.png)

## Further reading

* [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise)