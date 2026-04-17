# Managing dormant users

A user account is considered to be dormant if it has not been active for 30 days.

## About dormant users

A user is considered active if the user has performed any of the following activities on your enterprise.

* Authenticating to access your enterprise's resources via SAML SSO
* Creating a repository
* Pushing to an internal repository via HTTPS
* Being added to a repository
* Changing the visibility of a repository
* Creating an issue or pull request
* Commenting on an issue or pull request
* Closing or reopening an issue or pull request
* Applying a label to an issue or pull request, or removing a label
* Assigning or unassigning an issue or pull request
* Requesting a review of a pull request, or removing a review request
* Creating or editing a comment in a pull request review
* Dismissing a comment in a pull request
* Synchronizing a pull request
* Commenting on a commit
* Publishing a release
* Pushing to a wiki
* Starring a repository
* Deleting a repository
* Joining an organization

GitHub **does not consider the following activities as active**:

* Accessing resources by using a personal access token, SSH key, or GitHub App.
* Git operations (such as pushes, pulls, repository cloning) on private repositories.


> [!NOTE] You cannot mark a dormant user as active. To become active, a user must perform one of the activities listed above.

When assessing user dormancy, we only consider organizations, repositories, or sign-on events that are associated with the enterprise. For example, a user who has recently commented on an issue in a public repository outside of the enterprise may be considered dormant, while a user who has commented on an issue in a public repository within the enterprise will not be considered dormant.

A user account is considered to be dormant if the user  hasn't performed any of the previous activities in the past 30 days.

Dormancy applies to both enterprise members and outside collaborators.



## Downloading the dormant users report from your enterprise account

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec&ref_type=engagement&ref_style=text) page on GitHub.com.
1. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-checklist" aria-label="checklist" role="img"><path d="M2.5 1.75v11.5c0 .138.112.25.25.25h3.17a.75.75 0 0 1 0 1.5H2.75A1.75 1.75 0 0 1 1 13.25V1.75C1 .784 1.784 0 2.75 0h8.5C12.216 0 13 .784 13 1.75v7.736a.75.75 0 0 1-1.5 0V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25Zm13.274 9.537v-.001l-4.557 4.45a.75.75 0 0 1-1.055-.008l-1.943-1.95a.75.75 0 0 1 1.062-1.058l1.419 1.425 4.026-3.932a.75.75 0 1 1 1.048 1.074ZM4.75 4h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1 0-1.5ZM4 7.75A.75.75 0 0 1 4.75 7h2a.75.75 0 0 1 0 1.5h-2A.75.75 0 0 1 4 7.75Z"></path></svg> Compliance**.
1. Scroll to "Reports".
1. Optionally, to generate a new report, next to "Dormant Users", click **New report**.
1. Under "Recent reports", next to the report you want to download, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-download" aria-label="download" role="img"><path d="M2.75 14A1.75 1.75 0 0 1 1 12.25v-2.5a.75.75 0 0 1 1.5 0v2.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25v-2.5a.75.75 0 0 1 1.5 0v2.5A1.75 1.75 0 0 1 13.25 14Z"></path><path d="M7.25 7.689V2a.75.75 0 0 1 1.5 0v5.689l1.97-1.969a.749.749 0 1 1 1.06 1.06l-3.25 3.25a.749.749 0 0 1-1.06 0L4.22 6.78a.749.749 0 1 1 1.06-1.06l1.97 1.969Z"></path></svg> Download**.