# GitHub Copilot policies to control availability of features and models

Learn about the policies that control the availability of GitHub Copilot features and models for users granted a license through your organization or an organization in your enterprise.

## About policies for Copilot

When you assign a Copilot license to a member of your organization or enterprise, you can control the features they can use under that license with Copilot policies.

Policies are grouped into different types.

* **Feature policy:** Defines the availability of a Copilot feature. Shown on the "Policies" page.
* **Privacy policy:** Defines whether a potentially sensitive action is allowed or not. Shown at the end of the "Policies" page.
* **Models policy:** Defines the availability of models beyond the basic models provided with Copilot, which may incur additional costs. Shown on the "Models" page.

Each policy controls availability for members who receive a Copilot license from your enterprise or organization.

## Organization-level control of policies

Organization owners set policies to control the availability of features and models for users granted a Copilot license by the organization. For example, an organization owner can enable or disable using Copilot in the IDE (unless an enterprise owner has defined availability for the feature at the enterprise level).

The enforcement options for feature and model policies in an organization are:

* **Unconfigured** - A placeholder, which is removed once you have defined a setting. The policy is treated as disabled for this organization until you select an option.
* **Enabled** - The feature is **available** to all members who are assigned Copilot by the organization.
* **Disabled** - The feature is **blocked** for all members who are assigned Copilot by the organization.

For privacy policies, the options are called "Allowed" and "Blocked" in preference to enabled and disabled. This provides a clearer message of the impact of a privacy policy.

## Enterprise-level control of policies

Enterprise owners can choose to set policies for Copilot at the enterprise level or to delegate the decision to organization owners.

### Policy defined

If a policy is defined at the enterprise level, the policy applies to all users and control of the policy is disabled at the organization level.

### Granular organization selection

**For the Copilot cloud agent policy**, enterprise owners can choose to enable the feature for specific organizations rather than applying a blanket enterprise-wide setting. When **Enabled for selected organizations** is selected by an enterprise owner or an AI manager, only the selected organizations can enable the feature. Organizations can be selected individually or by using organization custom properties.

### No policy

If an enterprise owner selects **No policy**, the impact depends on whether a user has access to Copilot through an organization or directly from the enterprise.

For members who receive a Copilot license from the organization, organization owners can choose their policy. If a member receives access to Copilot through multiple organizations with conflicting policies, either the least or most permissive policy may apply, depending on the policy. For more information, see [Feature availability when GitHub Copilot policies conflict in organizations](/en/copilot/reference/feature-availability-enterprise).

For users who receive access to Copilot directly from the enterprise rather than from an organization, the **Policies for enterprise-assigned users** setting determines whether "No policy" defaults to enabled or disabled.

## Next steps

* [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer/organizations/managing-policies-for-copilot-in-your-organization)
* [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer/enterprises/managing-policies-and-features-for-copilot-in-your-enterprise)