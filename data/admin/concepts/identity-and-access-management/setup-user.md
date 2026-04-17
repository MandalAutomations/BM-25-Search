# Setup user

The setup user is used only to configure authentication and provisioning for Enterprise Managed Users.

## How should I use the setup user?

The setup user is an administrative account. It is **only** intended to be used for:

* Configuring authentication and provisioning
* SCIM provisioning via its personal access token
* Regaining access to your enterprise in the event of an issue with your identity provider

For other enterprise administration tasks, such as creating organizations, use a **provisioned managed user account** with the appropriate administrative role.

## What is the setup user's username?

If you use **GitHub.com**, the username is your enterprise's shortcode, suffixed with `_admin`. For example: `fabrikam_admin`.

If you use **GHE.com**, the username is a randomly generated shortcode, suffixed with `_admin`.

## How do I sign in as the setup user?

After we create your enterprise, you will receive an **email** inviting you to choose a password for the setup user.

When you create the password, we strongly recommend that you **enable two-factor authentication (2FA)** for the account and **save your recovery codes**.

Unlike provisioned managed users, the setup user cannot sign in via SSO.

* **Without 2FA enabled**, you must provide an enterprise recovery code **every** time you sign in.
* If **2FA is enabled**, you must sign in with a successful 2FA challenge response. You only need to enter an enterprise recovery code to access enterprise settings.

If you need to reset the password for your setup user, contact GitHub Support through the [GitHub Support portal](https://support.github.com). The usual password reset option by providing your email address will not work.

## Can I delete the setup user?

The setup user **cannot** be deleted, because it is essential for maintaining authentication and provisioning. The only way to remove the setup user is to delete your enterprise account. See [Deleting an enterprise account](/en/enterprise-cloud@latest/admin/managing-your-enterprise-account/deleting-an-enterprise-account).

## Further reading

* [Downloading your enterprise account's single sign-on recovery codes](/en/enterprise-cloud@latest/admin/managing-iam/managing-recovery-codes-for-your-enterprise/downloading-your-enterprise-accounts-single-sign-on-recovery-codes#downloading-codes-for-an-enterprise-with-enterprise-managed-users)