# GitHub Copilot seat assignment

Learn how seat assignment for GitHub Copilot works in organizations and enterprises, including billing, user eligibility, and assignment management.

This article explains how seat assignment for Copilot works in organizations and enterprises.

## What is a Copilot seat?

A **Copilot seat** is a license to use Copilot, assigned to a unique user account through a Copilot Business or a Copilot Enterprise plan.

Users must be assigned a seat to access Copilot features under an organization or enterprise plan

## Seat assignment management

* **Who assigns seats:** Organization owners. Seats are assigned to specific user accounts. See [Granting access to GitHub Copilot for members of your organization](/en/copilot/how-tos/administer/organizations/managing-access-to-github-copilot-in-your-organization/granting-access-to-copilot-for-members-of-your-organization).
* **Where:** Seat assignment can be managed in the GitHub organization settings or via the REST API.
* **If all assigned seats are removed, the organization's Copilot plan is canceled.**
* **If a user with an active Copilot Pro or Copilot Pro+ plan is assigned a seat in a Copilot Business or Copilot Enterprise plan**, their personal plan is automatically canceled, and a prorated refund for any remaining portion of their personal billing cycle is issued. The user will now use Copilot under the organization's policies.
* **If a single user receives a seat from multiple organizations within the same enterprise**, the enterprise is only billed once per billing cycle for that unique user. One organization that assigned Copilot to the user is chosen at random each month to be billed for the seat.
* **If a user is assigned both a  Copilot Business and a Copilot Enterprise seat from different organizations within the same enterprise**, only the Copilot Enterprise seat is billed. The charge is at the Copilot Enterprise rate from the time the Copilot Enterprise seat is assigned. The user will have access to the all the features and capabilities available under the Copilot Enterprise plan.