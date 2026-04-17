# Managing your role in an organization owned by your enterprise

You can manage your membership in any organization owned by your enterprise and change your role within the organization.

## About role management

You can choose to join an organization owned by your enterprise as a member or as an organization owner, change your role within the organization, or leave the organization. Your organization role determines your level of access to organization resources as follows:

* **Unaffiliated or no official organization role:** you cannot access organization content or repositories, but you can manage enterprise settings and policies that impact your organization
* **Organization member:** you can access organization resources and content, such as repositories, but you cannot access the organization's settings
* **Organization owner:** you can configure organization settings and manage access to the organization's resources through teams, etc.

> \[!WARNING]
> If an organization uses SCIM to provision users, joining the organization this way could have unintended consequences. For more information, see [About SCIM for organizations](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization/about-scim-for-organizations).

For information about managing other people's roles in an organization, see [Managing membership in your organization](/en/enterprise-cloud@latest/organizations/managing-membership-in-your-organization) and [Managing people's access to your organization with roles](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles).

## Managing your role with the enterprise settings

You can join an organization owned by your enterprise and manage your role within the organization, directly from the settings for your enterprise account.

If an organization enforces SAML single sign-on (SSO), you cannot use the enterprise settings to join the organization. Instead, you must join the organization using that organization's identity provider (IdP). Then, you can manage your role in your enterprise settings. For more information, see [Joining an organization that enforces SAML SSO](#joining-an-organization-that-enforces-saml-sso).

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. Next to the organization you want to manage your role in, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="Organization settings" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> dropdown menu and click **Join as an organization owner** or **Join as an organization member**.

   ![Screenshot of an organization in the organization list. A dropdown menu, labeled with the gear icon, is highlighted with an orange outline.](/assets/images/help/business-accounts/organization-settings-button.png)

## Joining an organization that enforces SAML SSO

If an organization enforces SAML SSO, you cannot use the enterprise settings to join the organization. Instead, you must join the organization using that organization's identity provider (IdP).

1. You must be assigned access in your IdP to the application for GitHub Enterprise Cloud that is used by the organization. If you're unable to configure your IdP yourself, contact your IdP administrator.
2. Authenticate to the organization using SAML SSO.

   * If the organization uses SCIM, accept the organization invitation that will be generated by the SCIM integration.
   * If the organization does not use SCIM, visit the following URL, replacing ORGANIZATION with the name of the organization, then follow the prompts to authenticate.

     `https://github.com/orgs/ORGANIZATION/sso`

After you've joined the organization, you can use the enterprise settings to manage your role in the organization, such as becoming an organization owner. For more information, see [Managing your role with the enterprise settings](#managing-your-role-with-the-enterprise-settings).