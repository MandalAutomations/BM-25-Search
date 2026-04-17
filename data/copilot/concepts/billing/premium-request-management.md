# Management methods for premium request usage in an enterprise

Learn about organization and user-based control of premium requests for enterprises.

## Management methods

The best way to control budgets for premium requests in an enterprise is to create cost centers and scope one or more budgets to each center.

When you want to set different limits on additional premium requests for different subsets of users, there are two possible budget management approaches.

* **Organization-based:** Each cost center is assigned one or more organizations.
* **User-based:** Each cost center is assigned one or more users.

These options provide flexibility for managing the cost of premium requests, but involve tradeoffs and careful decision making.

<div class="ghd-tool rowheaders">

| Considerations                | Organization-based       | User-based   |
| ----------------------------- | ------------------------ | ------------ |
| Identity provider integration | SCIM supported           | No support   |
| Copilot license assignment    | Single organization only | Not relevant |
| REST API automation           | Supported                | Supported    |

</div>

See [Using cost centers to allocate costs to business units](/en/billing/tutorials/use-cost-centers#creating-a-cost-center) and [REST API endpoints for billing](/en/rest/enterprise-admin/billing) or [open source utilities for automating cost center administration](https://github.com/github/cost-center-automation) in the `/github/cost-center-automation` repository on GitHub.com..
With organization-based management, the costs of Copilot and GitHub Enterprise licenses are allocated to the cost center. With user-based management, the costs of all paid licenses are allocated to the cost center. See [Cost center allocation for different products](/en/billing/reference/cost-center-allocation).

## Organization-based management example

An enterprise with the following properties would be a good candidate for organization-based management:

* Uses System for Cross-domain Identity Management (SCIM) to provision organization and team membership from the identity provider, which facilitates centralized management of Copilot licenses.
* Users are already grouped into organizations that match the differential budgets planned.
* Most users are assigned a Copilot license through a single organization.
* Any users who are currently assigned licenses through multiple organizations will be identified and their license assignment revised.

For example, there are a total of 25 Copilot users, and you want to permit additional premium requests for only 10 users. All 10 of those users must be assigned Copilot licenses through a single organization, separate from the organization that assigns licenses to the remaining 15 users.

For information about preparing your enterprise for organization-based management, see:

* [GitHub Copilot seat assignment](/en/copilot/reference/copilot-billing/seat-assignment)
* [Disabling Copilot for organizations in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-access/disable-for-organizations)
* [Using cost centers to allocate costs to business units](/en/billing/tutorials/use-cost-centers)

## User-based management example

An enterprise with the following properties would be a good candidate for user-based management:

* Organization membership does not align with the differential budgets planned.
* Many users are assigned a Copilot license through multiple organizations.
* You want to allocate costs for GitHub Enterprise, GitHub Secret Protection and GitHub Code Security licenses using the same grouping of users.

For example, organizations in your company represent workstreams and not users in different roles. You want to make additional premium requests available to a small subset of users across different organizations. There are a total of 25 Copilot users, and you want to permit additional premium requests for only 10 users. You assign the 10 users directly to one cost center and the remaining 15 to a second cost center. You set a budget of $0 for premium requests to the second cost center, and a higher budget for the first cost center.

## Next steps

* [Managing the premium request allowance for your organization or enterprise](/en/copilot/how-tos/manage-and-track-spending/manage-request-allowances)