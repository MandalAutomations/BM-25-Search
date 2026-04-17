# Exporting membership information for your enterprise

You can export information about all of your enterprise's members from GitHub's web UI.

## About export of membership information

You can export aggregated information about your enterprise's members as a membership information report. For example, you may want to perform an audit of your enterprise's current members. You can generate a file containing the report from GitHub's web UI.

The membership information report includes the following information.

* Username and display name details
* Whether the user has two-factor authentication enabled and how secure their 2FA configuration is
* Whether the user is an organization owner or member
* Organizations with pending invitations
* Optionally, additional information that depends on the enterprise's configuration:
  * The user's email addresses for a verified domain
  * The user's SAML `NameID`
  * Username and primary email addresses on any GitHub Enterprise Server instances where GitHub Connect is configured
  * User, subscription email address, and license status for Visual Studio subscriptions with GitHub Enterprise

You can also use GitHub's APIs to retrieve information about your enterprise's members. For more information, see the [GraphQL API](/en/enterprise-cloud@latest/graphql/reference/objects#user) and [REST API](/en/enterprise-cloud@latest/rest/users) documentation.

Organization owners can also export membership information for an organization. For more information, see [Exporting member information for your organization](/en/enterprise-cloud@latest/organizations/managing-membership-in-your-organization/exporting-member-information-for-your-organization).

The membership information report includes everyone associated with the enterprise, regardless of whether they consume a license. This report is useful for reviewing current enterprise membership, permissions, and roles for all individuals currently associated with the enterprise. For information about current and billable licenses, see [Viewing usage for your GitHub Enterprise plan](/en/enterprise-cloud@latest/billing/managing-your-license-for-github-enterprise/viewing-license-usage-for-github-enterprise).

## Exporting a membership information report

You can download a CSV file containing the membership information report for your enterprise.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> People**.
3. To the right of "Members", click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-download" aria-label="download" role="img"><path d="M2.75 14A1.75 1.75 0 0 1 1 12.25v-2.5a.75.75 0 0 1 1.5 0v2.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25v-2.5a.75.75 0 0 1 1.5 0v2.5A1.75 1.75 0 0 1 13.25 14Z"></path><path d="M7.25 7.689V2a.75.75 0 0 1 1.5 0v5.689l1.97-1.969a.749.749 0 1 1 1.06 1.06l-3.25 3.25a.749.749 0 0 1-1.06 0L4.22 6.78a.749.749 0 1 1 1.06-1.06l1.97 1.969Z"></path></svg> CSV Report**.

   * If your enterprise has less than 1,000 members, the report will download immediately.
   * If your enterprise has 1,000 or more members, you'll soon receive an email with a link to download the report.