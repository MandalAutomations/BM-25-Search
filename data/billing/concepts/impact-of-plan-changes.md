# Impact of changing your plan on billing

Learn how upgrading or downgrading your plan is reflected in billing.

## How plan changes affect billing

When you change your paid plan, the impact on billing depends on the type of change:

| Scenario                   | When is billing affected? | Is proration applied? | When does access change?                     |
| -------------------------- | ------------------------- | --------------------- | -------------------------------------------- |
| Upgrade plan               | Immediate                 | Yes                   | Immediately                                  |
| Downgrade or cancel plan   | End of current cycle      | No                    | End of current cycle                         |
| Add paid seats/licenses    | Immediate (prorated)      | Yes                   | Immediately                                  |
| Remove paid seats/licenses | Next billing cycle        | No                    | End of current cycle (unless access revoked) |

Key takeaways:

* Upgrades are billed and applied immediately.
* Downgrades and cancellations take effect only after the current billing cycle ends.
* Adding seats is prorated and grants immediate access.
* Removing seats takes effect in the next cycle, unless access is manually revoked.

Each account on GitHub is billed separately. Upgrading an organization account enables paid features for the organization's repositories only and does not affect the features available in repositories owned by any associated personal accounts. Similarly, upgrading a personal account enables paid features for the personal account's repositories only and does not affect the repositories of any organization accounts. For more information about account types, see [Types of GitHub accounts](/en/get-started/learning-about-github/types-of-github-accounts).

Making a change to the GitHub plan for your personal account, organization, or enterprise account does not affect billing for use of GitHub features, such as Copilot or paid apps purchased in GitHub Marketplace.

For more information, see [GitHub's plans](/en/get-started/learning-about-github/githubs-plans) and [How GitHub billing works](/en/billing/using-the-billing-platform/about-billing-on-github).

## Examples

The following examples illustrate how billing rules are applied in practice:

* **Canceling a monthly subscription:** Kumiko pays on the 5th of each month. She cancels on October 10th. Her subscription remains active until November 4th, then downgrades on November 5th.
* **Switching from yearly to monthly:** Ravi has a yearly subscription billed October 5th. He switches on December 10th, but the change won’t apply until the next renewal on October 5th the following year.
* **Adding paid seats:** Mada’s organization pays for 25 seats on the 15th. She adds 10 more on June 4th. She’s immediately charged a prorated amount for June 4–14, and billed for 35 seats starting June 15th.
* **Removing paid seats:** Stefan’s organization pays for 50 seats annually on May 20th. On September 30th, he removes 20 seats. The change takes effect on the next renewal (May 20th), when the organization will pay for 30 seats.

## Further reading

* [Managing your plan and GitHub licenses](/en/billing/managing-the-plan-for-your-github-account)
* [Making payments to third-parties through GitHub](/en/billing/managing-billing-for-your-products/managing-billing-for-github-marketplace-apps)
* [View and manage paid use of GitHub products](/en/billing/managing-billing-for-your-products/managing-billing-for-git-large-file-storage)
* [People who consume a license in an organization](/en/billing/managing-the-plan-for-your-github-account/about-per-user-pricing)