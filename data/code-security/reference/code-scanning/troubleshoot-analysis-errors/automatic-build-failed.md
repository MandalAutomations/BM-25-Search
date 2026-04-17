# Automatic build failed for a compiled language

If automatic build fails, you can configure code scanning to use specific build steps for compiled languages.

If an automatic build of code for a compiled language within your project fails, you can try changing to the `manual` build mode or removing the `autobuild` step from your code scanning workflow and adding specific build steps. If you're not already using advanced setup, you'll need to enable it first to create a workflow you can edit.

## Further reading

* [Configuring advanced setup for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning).
* [CodeQL build modes](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/codeql-code-scanning-for-compiled-languages#codeql-build-modes)