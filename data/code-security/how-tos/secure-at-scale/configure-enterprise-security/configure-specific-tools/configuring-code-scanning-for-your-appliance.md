# Configuring self-hosted runners for code scanning in your enterprise

You can enable, configure, and disable code scanning for your enterprise without GitHub-hosted runners. Code scanning allows users to scan code for vulnerabilities and errors.

<!--The CodeQL CLI man pages include a link to a section in this article. If you rename this article,
make sure that you also update the MS short link: https://aka.ms/code-scanning-docs/configuring-ghes.-->

## Provisioning a self-hosted runner

> \[!NOTE]
>
> * If your enterprise uses GitHub-hosted runners with GitHub Actions, proceed directly to configuring code scanning through GitHub.com. See [Configuring default setup for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning) and [Configuring default setup for code scanning at scale](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning-at-scale).
> * With the exception of Swift analysis, default setup can now run on larger runners. See [Larger runners](/en/enterprise-cloud@latest/actions/using-github-hosted-runners/about-larger-runners/about-larger-runners) and [Configuring larger runners for default setup](/en/enterprise-cloud@latest/code-security/code-scanning/managing-your-code-scanning-configuration/configuring-larger-runners-for-default-setup).

GitHub can run code scanning using a GitHub Actions workflow. First, you need to provision one or more self-hosted GitHub Actions runners in your environment. You can provision self-hosted runners at the repository, organization, or enterprise account level. See [Self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners) and [Adding self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners).

If you are provisioning a self-hosted runner for CodeQL analysis, your runner must use a CodeQL-supported operating system version and CPU architecture. See the [CodeQL system requirements](https://codeql.github.com/docs/codeql-overview/system-requirements/).

If you are using default setup for code scanning, you can assign self-hosted runners with the default `code-scanning` label, or you can optionally give them custom labels so that individual repositories can use different runners. See [Configuring default setup for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning#assigning-labels-to-runners).

For information about using default setup for code scanning analysis of compiled languages, see [CodeQL code scanning for compiled languages](/en/enterprise-cloud@latest/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/codeql-code-scanning-for-compiled-languages).

You must ensure that Git is in the PATH variable on any self-hosted runners you use to run CodeQL actions.

> \[!NOTE]
> If you use CodeQL code scanning to analyze code written in Python in your enterprise, you must make sure that your self-hosted runner has Python 3 installed.