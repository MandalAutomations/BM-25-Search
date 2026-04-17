# About ticket priority

Support tickets are assigned a priority based on the circumstances of the issue and impact to you and your team.

## About ticket priorities

When you contact GitHub Support, GitHub will choose a priority for the ticket:

* Low
* Normal
* High
* Urgent ([GitHub Premium Support](/en/enterprise-cloud@latest/support/learning-about-github-support/about-github-premium-support) only)

Ticket priority helps to ensure that support requests are handled in order, and according to their circumstances and impact.

GitHub has the sole discretion to modify the priority of a ticket at any time, and may lower the priority of a ticket after determining and mitigating the primary cause of an issue.

## Scope of Support

Please note that GitHub Support can only assist with issues that fall within GitHub's Scope of Support. Requests related to out-of-scope areas, such as third-party integration issues, custom scripts, or unsupported platforms, cannot be prioritized or addressed by GitHub Support.

For more details and examples of what is considered out of scope for GitHub Support, see GitHub's [Scope of Support documentation](/en/enterprise-cloud@latest/support/learning-about-github-support/about-github-support#scope-of-support). If your request falls outside this scope, please refer to the relevant third-party’s support resources, community forums, or consult [GitHub Expert Services](https://github.com/services/).

## Ticket priorities

|                                                                    Priority                                                                   | Description                                                                                                                                                                                                                      | Examples                                                                                                                                                                                                                                                                                                                                                                                                         |
| :-------------------------------------------------------------------------------------------------------------------------------------------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Urgent<br><br>([GitHub Premium Support](/en/enterprise-cloud@latest/support/learning-about-github-support/about-github-premium-support) only) | Production workflows for your organization or enterprise on GitHub Enterprise Cloud are failing due to critical service errors or outages, and the failure directly impacts the operation of your business.                      | <ul><li>Errors or outages on GitHub Enterprise Cloud affect core Git or web application functionality for all members of your organization or enterprise</li><li>Authentication issues impacting the majority of existing users in your enterprise or organization</li></ul>                                                                                                                                     |
|                                                                      High                                                                     | Account or security issues with your organization or enterprise on GitHub Enterprise Cloud are causing limited impact to your business.                                                                                          | <ul><li>An organization or enterprise owner has unintentionally deleted an organization</li><li>An organization or enterprise member has uploaded sensitive data in a commit, issue, pull request, or issue attachment</li><li>Unable to SCIM provision users or groups</li></ul>                                                                                                                                |
|                                                                     Normal                                                                    | Members of your organization or enterprise on GitHub Enterprise Cloud are experiencing limited or moderate issues with GitHub Enterprise Cloud, or you have general concerns or questions about your organization or enterprise. | <ul><li>Questions about using APIs and features for your organization or enterprise, including rate limits</li><li>API request failures due to rate limits</li><li>Issues with tools for organization data migration that GitHub provides</li><li>Features related to your organization or enterprise not working as expected</li><li>General security questions about your organization or enterprise</li></ul> |
|                                                                      Low                                                                      | You have a question or suggestion about your organization or enterprise on GitHub Enterprise Cloud that is not time-sensitive, or does not otherwise block the productivity of your team.                                        | <ul><li>Excessive resource usage for your organization or enterprise</li><li>Requests for health checks</li><li>Help with using Gists, notifications, wikis, GitHub Pages, GitHub Desktop, or other peripheral services or features with your organization or enterprise</li><li>Feature requests</li><li>Product feedback</li></ul>                                                                             |

## Ticket priorities for GitHub Advanced Security features

All tickets regarding security features follow this logic for ticket prioritization.

| Priority | Description                                                                                                                                                           |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|   High   | A feature is not functioning or is stopped or severely impacted such that the end user cannot reasonably continue use of the software and no workaround is available. |
|  Normal  | A feature is functioning inconsistently, causing impaired end user usage and productivity.                                                                            |
|    Low   | A feature is functioning consistently, but the end user requests minor changes in the software, such as documentation updates, cosmetic defects, or enhancements.     |

## Ticket priorities for Actions Runner Controller (ARC)

|                                                                    Priority                                                                   | Description                                                                                                                                                                                                                                                                        | Examples                                                                                                                                           |
| :-------------------------------------------------------------------------------------------------------------------------------------------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Urgent<br><br>([GitHub Premium Support](/en/enterprise-cloud@latest/support/learning-about-github-support/about-github-premium-support) only) | Issues that critically impact the functionality of GitHub-supported ARC in an existing production environment. This excludes disruptions caused by Kubernetes components, missing dependencies, third-party software (such as proxy servers), or other changes made by your teams. | ARC fails to create pods/start job/remove pods, or ARC has a significant bug affecting production and a rollback is not possible.                  |
|                                                                      High                                                                     | Issues that affect the performance of GitHub-supported ARC in an existing production environment but do not result in a complete system failure.                                                                                                                                   | Delays in pod termination or assignment of jobs to pods, where the delay is not in line with expectations but does not entirely halt the workflow. |
|                                                                  Normal / Low                                                                 | Any other minor issues not classified as Urgent or High should be directed to [the open source Actions Runner Controller repository](https://github.com/actions/actions-runner-controller) issues/discussions.                                                                     | Customization, performance analysis, initial setup.                                                                                                |

For more information about what GitHub Support can assist with, see [Support for Actions Runner Controller](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/about-support-for-actions-runner-controller).

## Further reading

* [Creating a support ticket](/en/enterprise-cloud@latest/support/contacting-github-support/creating-a-support-ticket)