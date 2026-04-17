# Managing allowed IP addresses for a GitHub App

You can add an IP allow list to your GitHub App registration to prevent your app from being blocked by an enterprise or organization's own allow list.

## About IP address allow lists for GitHub Apps

Enterprise and organization owners can restrict access to assets by configuring an IP address allow list. This list specifies the IP addresses that actors can use to access their resources. For more information, see [Enforcing policies for security settings in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-security-settings-in-your-enterprise#managing-allowed-ip-addresses-for-organizations-in-your-enterprise).

When an organization or enterprise has an allow list, third-party applications that connect via a GitHub App will be denied access unless either of the following condition sets are true:

* The creator of the GitHub App has configured an allow list for the application that specifies the IP addresses at which their application runs. See below for details of how to do this, **and**
* The organization or enterprise owner has chosen to permit the addresses in the GitHub App's allow list to be added to their own allow list. For more information, see [Managing allowed IP addresses for your organization](/en/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-allowed-ip-addresses-for-your-organization#allowing-access-by-github-apps) in the GitHub Enterprise Cloud documentation.

or

* The organization or enterprise owner has added an IP allow list entry for the IP addresses from which the application runs. See [Adding an allowed IP address](/en/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-allowed-ip-addresses-for-your-organization#adding-an-allowed-ip-address) in the GitHub Enterprise Cloud documentation.

> \[!NOTE]
> The addresses in the IP allow list of a GitHub App only affect requests made by installations of the GitHub App. The automatic addition of a GitHub App's IP address to an organization's allow list does not allow access to a GitHub user who connects from that IP address.

## Adding an IP address allow list to a GitHub App registration

> \[!NOTE]
> GitHub is gradually rolling out support for IPv6. As GitHub services continue to add IPv6 support, we will start recognizing IPv6 addresses of GitHub users. To prevent possible access interruptions, please ensure you have added any necessary IPv6 addresses to your IP allow list.

> \[!NOTE]
> Due to caching, adding or removing IP addresses can take a few minutes to fully take effect.

1. In the upper-right corner of any page on GitHub, click your profile picture.

2. Navigate to your account settings.
   * For an app owned by a personal account, click **Settings**.
   * For an app owned by an organization:
     1. Click **Your organizations**.
     2. To the right of the organization, click **Settings**.

3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Developer settings**.

4. In the left sidebar, click **GitHub Apps**.

5. To the right of the GitHub App you want to modify, click **Edit**.

6. At the bottom of the "IP allow list" section, in the "IP address or range in CIDR notation" field, type an IP address, or a range of addresses in CIDR notation.

   ![Screenshot of the IP allow list settings. A text field, labeled "IP address or range in CIDR notation", is highlighted with an orange outline.](/assets/images/help/security/ip-address-field.png)

7. Optionally, in the "Short description of IP address or range" field, enter a description of the allowed IP address or range.
   The description is for your reference and is not used in the allow list of organizations where the GitHub App is installed. Instead, organization allow lists will include "Managed by the NAME GitHub App" as the description.

8. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add**.