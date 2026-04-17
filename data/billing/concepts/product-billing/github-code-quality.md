# GitHub Code Quality billing

Learn how usage of Code Quality is measured.

> \[!NOTE]
> GitHub Code Quality is currently in public preview and subject to change.

## How use of GitHub Code Quality is measured

### For general availability

When Code Quality is generally available, scanning repositories will incur two types of costs for an organization:

* Premium requests
* GitHub Actions minutes needed to run the scans unless you use self-hosted runners

### For the public preview

When you scan private repositories during the public preview, you **will not be billed** for premium request usage, but GitHub Actions minutes **will be consumed**.

To view consumption of actions by the `dynamic/github-code-scanning/codeql` workflow, download a detailed usage report from the "Billing and licensing" tab. See [Viewing your usage of metered products and licenses](/en/billing/how-tos/products/view-productlicense-use).

> \[!NOTE]
> During the public preview, Code Quality uses the `dynamic/github-code-scanning/codeql` workflow that is also used by code scanning.

## Further reading

* [Quickstart for GitHub Code Quality](/en/code-security/code-quality/get-started/quickstart)
* [Enabling GitHub Code Quality](/en/code-security/code-quality/how-tos/enable-code-quality)