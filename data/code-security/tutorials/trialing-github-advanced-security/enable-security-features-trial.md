# Enabling security features in your trial enterprise

Quickly create an enterprise-level configuration and apply Secret Protection and Code Security features across all repositories in your trial enterprise.

This article assumes that you have planned and then started a trial of GitHub Advanced Security. For more information, see [Planning a trial of GitHub Advanced Security](/en/code-security/trialing-github-advanced-security/planning-a-trial-of-ghas).

The aim is to enable all the security features you want to trial quickly, as a starting point for deeper exploration. You should start getting results soon on the repositories in your trial enterprise and you can fine-tune the configuration later.

## Step 1: Create an enterprise security configuration for your trial goals

When you planned your trial, you identified the features that you want to test and any enforcement needs. You should create one or more security configurations for your enterprise that enable these features and set any enforcement levels you require.

1. In the top-right corner of GitHub, click your profile picture.
2. Depending on your environment, click **Your enterprise**, or click **Your enterprises** then click your trial enterprise.
3. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
4. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced Security**.
5. Click **New configuration** to create a new configuration.
6. To configure groups of security features for your repositories, click **Custom configuration**.
7. Give the configuration a meaningful name and description.
8. You will see that most features are already enabled. Review the features that are **Not set** and enable any that you want to trial, for example: "Automatic dependency submission."
9. In the "Policy" area, set the "Use as default for newly created repositories" option as needed to define whether or not to apply the configuration to new repositories created in the enterprise.
10. In the "Policy" area, notice that the "Enforce configuration" option is set to **Enforce** so that applying the configuration to a repository enforces all settings apart from any left as "Not set".
    > \[!TIP] While you are testing Advanced Security, you may want to change this to **Don't enforce** to allow you to optimize repository settings as needed without modifying security configurations.
11. When you have finished defining the configuration, click **Save configuration**.

The new enterprise security configuration is now available for use at the enterprise level and also within every organization in the enterprise.

## Step 2: Apply your enterprise security configuration to repositories

You can apply an enterprise security configuration either at the enterprise level or at the organization level. The best option for you will depend on whether or not you want to apply the configuration to all repositories in the enterprise, or to a subset of repositories.

> \[!NOTE] Secret Protection and Code Security are free of charge during trials. However, you will be charged for Actions minutes used by the default code scanning setup if you have exhausted your allocation of Actions minutes.

* Enterprise-level application:
  * Add an enterprise configuration to all repositories in the enterprise, or all repositories without an existing configuration in the enterprise.
* Organization-level application:
  * Add an enterprise or an organization configuration to all repositories in the organization, or all repositories without an existing configuration in the organization.
  * Add an enterprise or an organization configuration to a subset of repositories in the organization.

You may find it helpful to apply an enterprise security configuration to all repositories in your enterprise, and then work at the organization-level to select a subset of repositories and apply an alternative security configuration.

### Enterprise-level application

1. Open your trial enterprise.
2. In the sidebar, click **Settings** and then **Advanced Security** to display the security configurations page.
3. For the configuration you want to apply, click **Apply to** and choose whether to apply the configuration to all repositories in the enterprise or just to the repositories without an existing security configuration.

### Organization-level application

1. Open an organization in your trial enterprise.
2. Click the **Settings** tab to display the organization settings.
3. In the sidebar, click **Advanced Security** and then **Configurations** to display the security configurations page.
4. Optionally, select the **Apply to** dropdown menu and click either **All repositories**, to apply any configuration to all repositories in the organization, or **All repositories without configurations**, to configure just the repositories in the organization without an existing security configuration.
5. Optionally, in the "Apply configurations" section use the "Search repositories" field or **Filter** button to filter repositories. Then select one or more repositories and use the **Apply configuration** button to choose a configuration to apply to those repositories.

For more information, see [Applying a custom security configuration](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/applying-a-custom-security-configuration).

## Next steps

Now that you have enabled the security features you want to test, you are ready to look more deeply into how GitHub Secret Protection and GitHub Code Security protect your code.

1. [Exploring your enterprise trial of GitHub Secret Protection](/en/code-security/trialing-github-advanced-security/explore-trial-secret-scanning)
2. [Exploring your enterprise trial of GitHub Code Security](/en/code-security/trialing-github-advanced-security/explore-trial-code-scanning)