# Managing GitHub Advanced Security features for your enterprise

You can control GitHub Advanced Security features that secure and analyze code across all organizations owned by your enterprise.

## About management of Advanced Security features

You can use Advanced Security features to harden security for the organizations in your enterprise.

You can quickly enable security features at scale with a security configuration, a collection of security enablement settings you can apply to repositories in an organization. You can customize Advanced Security features at the organization level with global settings. See [About enabling security features at scale](/en/enterprise-server@3.15/code-security/securing-your-organization/introduction-to-securing-your-organization-at-scale/about-enabling-security-features-at-scale).

To manage individual GitHub Advanced Security features, you can enable or disable each feature for all existing and/or new repositories within the organizations owned by your enterprise.

> \[!WARNING]
> You should communicate any changes you plan to make to existing feature enablement settings to organization owners before making them, so as not to impact existing security configurations that have been rolled out by organizations in your enterprise.

You can also enable or disable GitHub Advanced Security features via the API. For more information, see [REST API endpoints for secret scanning](/en/enterprise-server@3.15/rest/secret-scanning#enable-or-disable-security-features-for-an-enterprise) in the REST API documentation.

For information about buying a license for GitHub Advanced Security, see [GitHub Advanced Security license billing](/en/enterprise-server@3.15/billing/managing-billing-for-your-products/managing-billing-for-github-advanced-security/about-billing-for-github-advanced-security).

If you have disallowed GitHub Advanced Security for an organization, that organization will not be affected by enabling a feature for all existing repositories or for all new repositories. For more information about disallowing GitHub Advanced Security for an organization, see [Enforcing policies for code security and analysis for your enterprise](/en/enterprise-server@3.15/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-code-security-and-analysis-for-your-enterprise).

When you enable one or more security and analysis features for existing repositories, you will see any results displayed on GitHub within minutes.

## Managing Advanced Security features

> \[!NOTE]
> If you enable GitHub Advanced Security features, active committers to these repositories will use GitHub Advanced Security licenses. This option is deactivated if you have exceeded your license capacity.

1. In the top-right corner of GitHub Enterprise Server, click your profile picture, then click **Enterprise settings**.
2. On the left side of the page, in the enterprise account sidebar, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Code security**.
4. Optionally, enable or disable a feature for all existing repositories.

   * To the right of the feature, click **Disable all** or **Enable all**. If the control for "GitHub Advanced Security" is disabled, you have no available licenses for GitHub Advanced Security.
   * To confirm the change, click the **Enable/Disable all** or **Enable/Disable for eligible repositories** button in the dialog that is displayed.
5. Optionally, to enable or disable a feature automatically when new private and internal repositories, user namespace repositories, or public repositories and repositories with GitHub Advanced Security enabled are created, select the checkbox below the feature.
6. Optionally, to enable the scanning of non-provider patterns, to the right of "Scan for non-provider patterns", click **Enable all**. To learn more about scanning for non-provider patterns, see [Supported secret scanning patterns](/en/enterprise-server@3.15/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#non-provider-patterns) and [Viewing and filtering alerts from secret scanning](/en/enterprise-server@3.15/code-security/secret-scanning/managing-alerts-from-secret-scanning/viewing-alerts).
7. Optionally, to include a resource link in the message that members will see when they attempt to push a secret, select **Add a resource link in the CLI and web UI when a commit is blocked**, then type a URL, and click **Save link**.

   > \[!NOTE]
   > When a custom link is configured for an organization, the organization-level value overrides the custom link set for the enterprise. See [About push protection](/en/enterprise-server@3.15/code-security/secret-scanning/protecting-pushes-with-secret-scanning).

   ![Screenshot of "Push protection" settings. The checkbox and text field used for enabling a custom link are outlined.](/assets/images/help/organizations/secret-scanning-custom-link.png)