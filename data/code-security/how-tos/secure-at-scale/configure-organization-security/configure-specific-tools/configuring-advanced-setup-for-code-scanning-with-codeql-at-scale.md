# Configuring advanced setup for code scanning with CodeQL at scale

Establish a highly customizable code scanning setup at scale with a script.

## Using a script to enable advanced setup

For repositories that are not eligible for default setup, you can use a bulk configuration script to enable advanced setup across multiple repositories.

> \[!NOTE] To successfully execute the script, GitHub Actions must be enabled for the organization.

1. Identify a group of repositories that can be analyzed using the same code scanning configuration. For example, all repositories that build Java artifacts using the production environment.
2. Create and test a GitHub Actions workflow to call the CodeQL action with the appropriate configuration. For more information, see [Configuring advanced setup for code scanning](/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/configuring-advanced-setup-for-code-scanning#configuring-advanced-setup-for-code-scanning-with-codeql).
3. Use one of the example scripts or create a custom script to add the workflow to each repository in the group.
   * GitHub CLI extension: [`advanced-security/gh-add-files`](https://github.com/advanced-security/gh-add-files?ref_product=code-scanning\&ref_type=engagement\&ref_style=text)
   * Python example: [`Malwarebytes/ghas-cli`](https://github.com/Malwarebytes/ghas-cli?ref_product=code-scanning\&ref_type=engagement\&ref_style=text) repository
   * NodeJS example: [`nickliffen/ghas-enablement`](https://github.com/NickLiffen/ghas-enablement?ref_product=code-scanning\&ref_type=engagement\&ref_style=text) repository
   * PowerShell example: [`jhutchings1/Create-ActionsPRs`](https://github.com/jhutchings1/Create-ActionsPRs?ref_product=code-scanning\&ref_type=engagement\&ref_style=text) repository

## Next steps

> \[!NOTE]
> CodeQL model packs are currently in public preview and subject to change. Model packs are supported for C/C++, C#, Java/Kotlin, Python, Ruby, and Rust analysis.
>
> The CodeQL model editor in the CodeQL extension for Visual Studio Code supports modeling dependencies for  C#, Java/Kotlin, Python, and Ruby.

If your codebase depends on a library or framework that is not recognized by the standard queries in CodeQL, you can extend the CodeQL coverage in your bulk configuration script by specifying published CodeQL model packs. For more information, see [Workflow configuration options for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning#codeql-model-packs).