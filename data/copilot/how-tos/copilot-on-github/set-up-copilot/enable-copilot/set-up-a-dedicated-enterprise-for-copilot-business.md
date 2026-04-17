# Setting up a dedicated enterprise for GitHub Copilot Business

Create an enterprise account for managing Copilot Business licenses without adopting GitHub Enterprise.

With a dedicated enterprise account, you get enterprise-grade identity provider integrations for authentication and provisioning without paying for GitHub Enterprise licenses. See [About enterprise accounts for Copilot Business](/en/copilot/concepts/about-enterprise-accounts-for-copilot-business).

## Create an enterprise account

> \[!IMPORTANT]
> If you purchased Copilot Business through GitHub's sales team, your enterprise account is already created. Skip to the next section.

Start a trial of GitHub Enterprise Cloud to create your enterprise account.

<a href="https://github.com/account/enterprises/new?ref_product=ghec&ref_type=trial&ref_style=button&ref_plan=enterprise" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Set up a trial of GitHub Enterprise Cloud</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

Do not create any organizations during setup. Adding users to organizations assigns GitHub Enterprise licenses, while adding users directly to the enterprise keeps your setup limited to Copilot Business.

## Add users to your enterprise

Once you have an enterprise account, add the people who will receive Copilot Business licenses. How you add users depends on your enterprise type.

### Enterprise with personal accounts

Invite users directly to your enterprise. For detailed steps, see [Inviting users to your enterprise directly](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/invite-users-directly).

### Enterprise with managed users

If your enterprise uses Enterprise Managed Users, provision user accounts from your identity provider (IdP) through SCIM.
For setup and provisioning guidance, see [Getting started with Enterprise Managed Users](/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users).

Provisioned users appear automatically in your enterprise's **People** list. You can then assign Copilot Business licenses directly to these users or to enterprise teams synced with your IdP.

## Create teams (optional)

Group users to scale license assignment by creating enterprise teams. See [Creating enterprise teams](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/create-enterprise-teams).

## Enable Copilot for the enterprise

Before you can assign licenses, an **enterprise owner** must enable Copilot for the enterprise.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-credit-card" aria-label="credit-card" role="img"><path d="M10.75 9a.75.75 0 0 0 0 1.5h1.5a.75.75 0 0 0 0-1.5h-1.5Z"></path><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25ZM14.5 6.5h-13v5.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Zm0-2.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25V5h13Z"></path></svg> Billing and licensing**.
3. In the left sidebar, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> **Licensing**.
4. Next to "Copilot", click **Enable**.

## Assign Copilot licenses

Give people access to Copilot by assigning Copilot Business licenses to users or enterprise teams.

For detailed steps, see [Granting users access to GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-access/grant-access#assigning-licenses-to-users-or-teams).

## Convert your trial to a paid enterprise account

To continue using Copilot Business after your trial, convert to a paid enterprise account. See [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud#purchasing-github-enterprise).

## Next steps

Help your developers start using Copilot and measure its impact. See [Driving GitHub Copilot adoption in your company](/en/copilot/tutorials/roll-out-at-scale/enable-developers/drive-adoption).