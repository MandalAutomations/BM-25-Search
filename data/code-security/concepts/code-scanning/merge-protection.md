# Code scanning merge protection

Code scanning rules prevent pull requests with potential vulnerabilities from being merged.

## Rulesets for code scanning merge protection

A ruleset is a named list of rules that control how people can interact with branches and tags in your repositories. You can add code scanning rules to rulesets to prevent pull requests from being merged when any of the following conditions are met:

* A required tool finds a code scanning alert of a severity that is defined in the ruleset.
* A required tool's analysis is still in progress.
* A required tool is not configured for the repository.

Typically, you should use code scanning merge protection on long-lived feature branches, where you want to guarantee code has been analyzed before pull requests can be merged.

Configuring a code scanning rule will not automatically enable code scanning. To learn how to enable code scanning, see [Configuring default setup for code scanning](/en/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning).

> \[!NOTE]
>
> * Merge protection with rulesets is not related to status checks. For more information about status checks, see [About status checks](/en/pull-requests/collaborating-with-pull-requests/collaborating-on-repositories-with-code-quality-features/about-status-checks).

## Availability

You can set code scanning merge protection with rulesets:

* At the repository level
* At the organization level (GitHub Enterprise plans only)

## Exceptions and limitations

Merge protection with rulesets will **not apply** to:

* Merge queue groups
* Dependabot pull requests analyzed by default setup

Additionally, all the lines of code identified by an alert must exist in the pull request diff. For more information, see [SARIF support for code scanning](/en/code-security/code-scanning/integrating-with-code-scanning/sarif-support-for-code-scanning#source-file-locations).

## Next steps

To configure a ruleset that requires code scanning results, see [Set code scanning merge protection](/en/code-security/how-tos/scan-code-for-vulnerabilities/manage-your-configuration/set-code-scanning-merge-protection).