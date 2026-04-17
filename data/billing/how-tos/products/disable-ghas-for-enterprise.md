# Disabling GitHub Advanced Security for your enterprise

Disable GitHub Advanced Security and prevent accidental re-enablement across your enterprise.

If you want to immediately disable GitHub Advanced Security in all repositories, prevent organizations from re-enabling it and avoid unexpected billing charges, you can use the **Disable Advanced Security** option available in the enterprise licensing page. This is different from canceling your Advanced Security subscription:

* **Canceling your subscription** stops future billing but does not disable GitHub Advanced Security in repositories or prevent re-enablement.
* **Disabling Advanced Security** immediately disables GitHub Advanced Security in all private and internal repositories and sets a policy to prevent future paid adoption.

## Disabling GitHub Advanced Security across your enterprise

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec&ref_type=engagement&ref_style=text) page on GitHub.com.
1. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-credit-card" aria-label="credit-card" role="img"><path d="M10.75 9a.75.75 0 0 0 0 1.5h1.5a.75.75 0 0 0 0-1.5h-1.5Z"></path><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25ZM14.5 6.5h-13v5.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Zm0-2.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25V5h13Z"></path></svg> Billing and licensing**.
1. From the list of "Billing & licensing" pages, click **Licensing**.
1. To the right of "Advanced Security," click **Manage** and select the **Disable Advanced Security** option.
1. In the modal dialog that is displayed, click **Disable Advanced Security** to confirm.

   To re-enable GitHub Advanced Security, you'll need to update the policies for this feature in the **Policies** tab of your enterprise.

## What happens to my bill?

Once you have disabled GitHub Advanced Security:

* If you use **volume billing**, you agreed to a number of licenses and billing period upfront. You'll continue to pay for the rest of this period.
* If you use **metered billing**, you pay based on usage, and your billing will stop from next month. However, you _will_ continue paying for any licenses you've already consumed this month until the end of the month.

  For example, if you had 10 licenses in use and disabled GitHub Advanced Security on the second day of the month, you will still be billed for your 10 licenses for the full month instead of just for the two days.