# Configuring built-in authentication

When you use the default authentication method, all authentication details are stored on GitHub.com.

## About built-in authentication

By default, GitHub Enterprise Server uses built-in authentication. Each person creates a user account on your GitHub Enterprise Server instance from an invitation or by signing up, and then authenticates with the credentials for the account to access your instance. Your GitHub Enterprise Server instance stores the authentication information for the account.

By default, users can use passkeys for built-in authentication, but you can disable passkeys for your instance. See [Disabling passkeys for your instance](/en/enterprise-server@3.20/admin/managing-iam/using-built-in-authentication/disabling-passkeys-for-your-instance).

You can prevent unauthenticated people from creating new user accounts on your instance. For more information, see [Disabling unauthenticated sign-ups](/en/enterprise-server@3.20/admin/identity-and-access-management/using-built-in-authentication/disabling-unauthenticated-sign-ups).

Alternatively, you can configure external authentication for your GitHub Enterprise Server instance. If you use external authentication, you must invite people to use your instance through your authentication provider. For more information, see [Identity and access management fundamentals](/en/enterprise-server@3.20/admin/identity-and-access-management/managing-iam-for-your-enterprise/about-authentication-for-your-enterprise#external-authentication).

## Configuring built-in authentication

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
4. In the "Settings" sidebar, click **Authentication**.
5. Under "Authentication," select **Built in authentication**.

### Two-factor authentication

When using LDAP or built-in authentication, two-factor authentication is supported. Organization owners can require members to have two-factor authentication enabled.

## Creating your account

Once your instance has been created, you'll need to create your own admin account.

1. On the "Create Admin Account" page at `http(s)://[hostname]/join`, type your username, password, and email address, then click **Create an account**.
2. Sign in to your GitHub Enterprise Server instance at `http(s)://HOSTNAME/login`.

## Next steps

<a name="inviting-users"></a>

After you configure built-in authentication and create your administrative account, you can invite people to create accounts and use your instance. For more information, see [Inviting people to use your instance](/en/enterprise-server@3.20/admin/identity-and-access-management/using-built-in-authentication/inviting-people-to-use-your-instance).

## Further reading

* [Configuring email for notifications](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/configuring-email-for-notifications)