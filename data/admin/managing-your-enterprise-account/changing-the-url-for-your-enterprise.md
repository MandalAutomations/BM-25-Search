# Changing the URL for your enterprise

If you want to change the URL where your enterprise is accessed, you can change your enterprise slug.

## About changes to enterprise slugs

When you create an enterprise, you choose a "slug" for the enterprise, which is a string used in the URL for your enterprise. For example, if you chose `octo-enterprise` as the slug, the URL for your enterprise on GitHub.com would be `https://github.com/enterprises/octo-enterprise`.

If your company pays for GitHub Enterprise Cloud by credit card or PayPal, you can change the slug in the settings for your enterprise. When you change the slug, GitHub does not set up any redirects from the old URL. Your old enterprise slug will immediately become available for another customer to use.

> \[!NOTE]
> If you pay for GitHub Enterprise Cloud via invoice, or if your enterprise uses Enterprise Managed Users, you must contact [GitHub's Sales team](https://github.com/enterprise/contact) to change your enterprise slug.
> For enterprises hosted on GHE.com, changing the enterprise slug is not currently supported.

## Considerations when changing your enterprise slug

Before changing the slug for an enterprise, ensure you have considered any parts of your enterprise's configuration, automations, or processes that may depend on the old enterprise slug. To minimize disruption, you should address these points either immediately before or immediately after changing the slug.

Parts of your system that may be affected by changing the slug include, but are not limited to, the following.

### SAML single sign-on (SSO)

If you have enabled SAML single sign-on (SSO) at the enterprise level, you will need to reconfigure the settings in your identity provider (IdP) to use the new enterprise slug. When you change your slug, existing IdP sessions are not revoked, but your members won't be able to use SSO to access resources in your enterprise until you update the IdP settings. If you have enabled SAML or SCIM at the organization level, changing the slug will not affect SSO. For more information, see [Configuring SAML single sign-on for your enterprise](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/configuring-saml-single-sign-on-for-your-enterprise).

Before changing the slug, to ensure you will have access to your enterprise even if SSO is not working, we recommend you download the recovery codes for your enterprise. For more information, see [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes).

### API endpoints

Many GitHub API endpoints for managing an enterprise take the enterprise slug as a parameter. If you use these endpoints in automations, you will need to update the API calls to use the new slug. API calls that use the old slug will stop working immediately. The enterprise ID, which can be used as an alternative to the slug in many cases, is not affected by a slug change.

### OpenID Connect with GitHub Actions workflows

If you use OpenID Connect (OIDC) in GitHub Actions workflows, and have configured your cloud provider to only accept tokens from a unique URL that includes your enterprise slug, you will need to update the settings in your cloud provider. To prevent workflows from failing, the most robust option is to configure your provider to accept tokens from both the old and new slug just before you change the slug. For more information, see [OpenID Connect](/en/enterprise-cloud@latest/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect#customizing-the-issuer-value-for-an-enterprise).

### GitHub Connect

If your enterprise is linked to one or more GitHub Enterprise Server instances via GitHub Connect, after changing the slug, you'll need to reset the connection by disabling and then reenabling GitHub Connect. For more information, see [Enabling GitHub Connect for GitHub.com](/en/enterprise-server@3.20/admin/configuration/configuring-github-connect/managing-github-connect) in the GitHub Enterprise Server documentation.

## Changing the enterprise slug

> \[!NOTE]
> Before changing the slug for an enterprise, make sure you have understood the potential consequences. For more information, see [Considerations when changing your enterprise slug](#considerations-when-changing-your-enterprise-slug).

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.

3. At the bottom of the page, in the "Danger zone" section, click **Change enterprise URL slug**.

4. In the "Change enterprise URL slug" dialog, follow the instructions, then click **Change enterprise slug URL**.