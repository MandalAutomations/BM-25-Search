# "Out of disk" and "Out of memory" errors

If you see one of these errors with GitHub Actions, you can try alternative runners.

<!-- CodeQL CLI depends on a short URL generated from this article's URL. If this article's URL ever changes, make sure to update the short URL https://gh.io/troubleshooting-code-scanning/out-of-disk-or-memory. https://thehub.github.com/it/how-to/url-shortening -->

## About these errors

You may see these errors when running code scanning if the runners you're using don't meet the recommended hardware requirements.

* `Out of disk`
* `Out of memory`

## Confirming the cause of the problem

You can review the recommended hardware resources for running CodeQL to make sure the runners that you use for code scanning meet those requirements. For more information, see [Recommended hardware resources for running CodeQL](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/recommended-hardware-resources-for-running-codeql).

## Fixing the problem

If the runners you're using don't meet the recommended hardware requirements, consider using either larger runners or self-hosted runners.

Larger runners are GitHub-hosted runners with more RAM, CPU, and disk space than standard runners. These runners have the runner application and other tools preinstalled. For more information about larger runners and code scanning, see [Using larger runners](/en/actions/using-github-hosted-runners/about-larger-runners) and [Configuring larger runners for default setup](/en/code-security/code-scanning/managing-your-code-scanning-configuration/configuring-larger-runners-for-default-setup).

Self-hosted runners offer more control of hardware, operating system, and software tools than GitHub-hosted runners can provide. For more information, see [Self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners).