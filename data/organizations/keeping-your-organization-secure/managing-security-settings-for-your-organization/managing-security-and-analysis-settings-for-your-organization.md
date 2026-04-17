# Managing security and analysis settings for your organization

You can control features that secure and analyze the code in your organization's projects on GitHub.

## About management of security and analysis settings

GitHub can help you to secure the repositories in your organization. You can manage the security and analysis features for all existing or new repositories that members create in your organization. If you have a license for GitHub Secret Protection or GitHub Code Security then you can also manage access to these features. For more information, see [About GitHub Advanced Security](/en/get-started/learning-about-github/about-github-advanced-security).

You can't disable some security and analysis features that are enabled by default for public repositories.

You can quickly enable security features at scale with a security configuration, a collection of security enablement settings you can apply to repositories in an organization. You can customize Advanced Security features at the organization level with global settings. See [About enabling security features at scale](/en/code-security/securing-your-organization/introduction-to-securing-your-organization-at-scale/about-enabling-security-features-at-scale).

If you enable security and analysis features, GitHub performs read-only analysis on your repository.

## Allowing Dependabot to access private dependencies

Dependabot can check for outdated dependency references in a project and automatically generate a pull request to update them. To do this, Dependabot must have access to all of the targeted dependency files. Typically, version updates will fail if one or more dependencies are inaccessible. For more information, see [About Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/about-dependabot-version-updates).

By default, Dependabot can't update dependencies that are located in private repositories, or private package registries. However, if a dependency is in a private GitHub repository within the same organization as the project that uses that dependency, you can allow Dependabot to update the version successfully by giving it access to the host repository.

If your code depends on packages in a private registry, you can allow Dependabot to update the versions of these dependencies by configuring this at the repository level. You do this by adding authentication details to the `dependabot.yml` file for the repository. For more information, see [Top-level `registries` key](/en/code-security/reference/supply-chain-security/dependabot-options-reference#top-level-registries-key).

For more information on how to grant Dependabot access to private dependencies, see [Configuring global security settings for your organization](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/configuring-global-security-settings-for-your-organization#granting-dependabot-access-to-private-and-internal-repositories).

## Removing access to GitHub Advanced Security features from individual repositories in an organization

You can use security configurations to remove access to GitHub Advanced Security features from individual repositories in an organization. For more information, see [Managing your paid use of Advanced Security](/en/code-security/securing-your-organization/managing-the-security-of-your-organization/managing-your-github-advanced-security-license-usage#turning-off-github-advanced-security-features-on-select-repositories-in-your-organization).

## Further reading

* [Quickstart for securing your repository](/en/code-security/getting-started/securing-your-repository)
* [About secret scanning](/en/code-security/secret-scanning/introduction/about-secret-scanning)
* [About the dependency graph](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph)
* [About supply chain security](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-supply-chain-security)