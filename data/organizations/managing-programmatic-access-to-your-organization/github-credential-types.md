# GitHub credential types reference

Reference documentation for all programmatic credential types that can access GitHub, including token formats, lifespan, SSO authorization capabilities, and revocation options.

This article provides a consolidated reference for all programmatic credential types that can access GitHub. Use this reference to audit activity and manage credential revocation, especially during security incidents.

## Credential types overview

The following table lists all credential types that can programmatically access GitHub.

| Credential type                                                                | Credential prefix | Lifespan                                      | Revocation                 | Associated with  |
| ------------------------------------------------------------------------------ | ----------------- | --------------------------------------------- | -------------------------- | ---------------- |
| [Personal access token (classic)](#personal-access-token-classic)              | `ghp_`            | Long-lived                                    | Manual                     | User account     |
| [Fine-grained personal access token](#fine-grained-personal-access-token)      | `github_pat_`     | Configurable (up to 1 year, or no expiration) | Manual                     | User account     |
| [OAuth app access token](#oauth-app-access-tokens)                             | `gho_`            | Long-lived                                    | Manual                     | User account     |
| [GitHub App user access token](#github-app-user-access-tokens)                 | `ghu_`            | Short-lived (8 hours)                         | Automatic expiry or manual | User account     |
| [GitHub App installation access token](#github-app-installation-access-tokens) | `ghs_`            | Short-lived (1 hour)                          | Automatic expiry           | App installation |
| [GitHub App refresh token](#github-app-refresh-tokens)                         | `ghr_`            | Long-lived (6 months)                         | Manual                     | User account     |
| [User SSH key](#user-ssh-keys)                                                 | Not applicable    | Long-lived                                    | Manual                     | User account     |
| [Deploy key](#deploy-keys)                                                     | Not applicable    | Long-lived                                    | Manual                     | Repository       |
| [`GITHUB_TOKEN`](#github_token-github-actions) (GitHub Actions)                | Not applicable    | Short-lived (job duration)                    | Automatic expiry           | Workflow run     |

## Credential revocation

The following sections describe revocation options for each credential type based on your role. See also [Token expiration and revocation](/en/authentication/keeping-your-account-and-data-secure/token-expiration-and-revocation).

> \[!NOTE] Enterprise owners have options for **bulk actions** in major incidents. See [Bulk actions for security incidents](#bulk-actions-for-security-incidents).

### Personal access token (classic)

* If the token **belongs to you**, you can delete it via your personal account settings. See [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#deleting-a-personal-access-token).

* If the token is owned by someone else, and the actual token value is known, **anyone** can submit a request to revoke it using the REST API. The API doesn't require authentication - anyone with the token value can submit it for revocation. See [Revocation](/en/rest/credentials/revoke?apiVersion=2022-11-28#revoke-a-list-of-credentials) in the REST API documentation.

* **Organization owners** and **enterprise owners** do not have direct visibility into or control over individual tokens. However, they can:
  * Revoke them using the REST API, if the actual token value is known. See [Revocation](/en/rest/credentials/revoke?apiVersion=2022-11-28#revoke-a-list-of-credentials).
  * Restrict the access of personal access tokens to the organization or enterprise entirely. See [Setting a personal access token policy for your organization](/en/organizations/managing-programmatic-access-to-your-organization/setting-a-personal-access-token-policy-for-your-organization) and [Enforcing policies for personal access tokens in your enterprise](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-personal-access-tokens-in-your-enterprise).

* **Organization owners and enterprise owners** on GitHub Enterprise Cloud with SSO enforced can revoke the SSO authorization for a specific personal access token (classic). See [Revoking SSO authorization](#revoking-sso-authorization) for details.

* **Revoked automatically** if pushed to a public repository or gist, or if unused for one year. See [Token expiration and revocation](/en/authentication/keeping-your-account-and-data-secure/token-expiration-and-revocation).

### Fine-grained personal access token

* If the token **belongs to you**, you can delete it via your personal account settings. See [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#deleting-a-personal-access-token).

* If the token is owned by someone else, and the actual token value is known, **anyone** can submit a request to revoke it using the REST API. The API doesn't require authentication - anyone with the token value can submit it for revocation. See [Revocation](/en/rest/credentials/revoke?apiVersion=2022-11-28#revoke-a-list-of-credentials) in the REST API documentation.

* **Organization owners**: Can view and revoke individual tokens. Note, however, that when an organization owner revokes a fine-grained personal access token, any SSH keys created by the token will continue to work and the token will still be able to read public resources within the organization. The revocation changes the resource owner from the organization to the user, and the user can reassign it back. See [Reviewing and revoking personal access tokens in your organization](/en/organizations/managing-programmatic-access-to-your-organization/reviewing-and-revoking-personal-access-tokens-in-your-organization).

* **Organization owners** and **enterprise owners** can:
  * Revoke the token using the REST API. See [Revocation](/en/rest/credentials/revoke?apiVersion=2022-11-28#revoke-a-list-of-credentials).
  * Restrict the access of personal access tokens to the organization or enterprise entirely. See [Setting a personal access token policy for your organization](/en/organizations/managing-programmatic-access-to-your-organization/setting-a-personal-access-token-policy-for-your-organization) and [Enforcing policies for personal access tokens in your enterprise](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-personal-access-tokens-in-your-enterprise).

* **Revoked automatically** if pushed to a public repository or gist, or if unused for one year. See [Token expiration and revocation](/en/authentication/keeping-your-account-and-data-secure/token-expiration-and-revocation).

### OAuth app access tokens

* **Users** can revoke their authorization to an OAuth app in their personal account settings, which will revoke any tokens associated with the app. See [Reviewing your authorized OAuth apps](/en/apps/oauth-apps/using-oauth-apps/reviewing-your-authorized-oauth-apps).

* If the token is owned by someone else, and the actual token value is known, **anyone** can submit a request to revoke it using the REST API. The API doesn't require authentication - anyone with the token value can submit it for revocation. See [Revocation](/en/rest/credentials/revoke?apiVersion=2022-11-28#revoke-a-list-of-credentials) in the REST API documentation.

* **Organization owners** can deny a previously approved OAuth app's access to the organization. See [Denying access to a previously approved OAuth app for your organization](/en/enterprise-cloud@latest/organizations/managing-oauth-access-to-your-organizations-data/denying-access-to-a-previously-approved-oauth-app-for-your-organization).

* Enterprise and organization owners cannot directly revoke SSO authorization for individual OAuth app tokens.

* **Revoked automatically** if pushed to a public repository or gist, or if unused for one year. See [Token expiration and revocation](/en/authentication/keeping-your-account-and-data-secure/token-expiration-and-revocation).

### GitHub App user access tokens

* **Users** can revoke their authorization to an GitHub App in their personal account settings. Note that this revokes authorization for **all** organizations, not just a specific one. See [Reviewing and revoking authorization of GitHub Apps](/en/apps/using-github-apps/reviewing-and-revoking-authorization-of-github-apps).

* If the token is owned by someone else, and the actual token value is known, **anyone** can submit a request to revoke it using the REST API. The API doesn't require authentication - anyone with the token value can submit it for revocation. See [Revocation](/en/rest/credentials/revoke?apiVersion=2022-11-28#revoke-a-list-of-credentials) in the REST API documentation.

* **Organization owners** can't revoke user authorizations directly, but can suspend or uninstall the app to prevent access to organization resources. See [Reviewing and modifying installed GitHub Apps](/en/apps/using-github-apps/reviewing-and-modifying-installed-github-apps).

* Enterprise and organization owners cannot directly revoke SSO authorization for individual GitHub App user access tokens.

* **Automatically expires** after 8 hours by default. See [Token expiration and revocation](/en/authentication/keeping-your-account-and-data-secure/token-expiration-and-revocation#user-token-expired-due-to-github-app-configuration).

### GitHub App refresh tokens

* **Users** can revoke the GitHub App authorization, which also invalidates associated refresh tokens. See [Reviewing and revoking authorization of GitHub Apps](/en/apps/using-github-apps/reviewing-and-revoking-authorization-of-github-apps).

* If the token is owned by someone else, and the actual token value is known, **anyone** can submit a request to revoke it using the REST API. The API doesn't require authentication - anyone with the token value can submit it for revocation. See [Revocation](/en/rest/credentials/revoke?apiVersion=2022-11-28#revoke-a-list-of-credentials) in the REST API documentation.

* **Automatically expires** after 6 months.

### GitHub App installation access tokens

* **App owners** can revoke via `DELETE /installation/token`. See [REST API endpoints for GitHub App installations](/en/rest/apps/installations?apiVersion=2022-11-28#revoke-an-installation-access-token).
* **Organization owners and enterprise owners**: Can uninstall the app from the organization, which deactivates all associated installation tokens. See [Reviewing and modifying installed GitHub Apps](/en/apps/using-github-apps/reviewing-and-modifying-installed-github-apps).
* **Automatically expires** after 1 hour.

### User SSH keys

* **Users** can delete the credential via **Settings > SSH and GPG keys**. See [Reviewing your SSH keys](/en/authentication/keeping-your-account-and-data-secure/reviewing-your-ssh-keys).
* **Organization owners and enterprise owners** on GitHub Enterprise Cloud with SSO enforced can revoke the SSO authorization for a specific SSH key. Once revoked, the same key cannot be re-authorized—the user must create a new SSH key. See [Revoking SSO authorization](#revoking-sso-authorization) for details.
* **Automatically deleted** if unused for one year. See [Deleted or missing SSH keys](/en/enterprise-cloud@latest/authentication/troubleshooting-ssh/deleted-or-missing-ssh-keys).

For more information on SSH keys, see [Adding a new SSH key to your GitHub account](/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

### Deploy keys

* **Repository admins** can delete keys via **Repository settings > Security > Deploy keys**. Also available via the Deploy keys REST API. See [Reviewing your deploy keys](/en/authentication/keeping-your-account-and-data-secure/reviewing-your-deploy-keys).
* **Organization owners** can disable deploy keys entirely across the organization, which disables all existing deploy keys. See [Restricting deploy keys in your organization](/en/organizations/managing-organization-settings/restricting-deploy-keys-in-your-organization).
* **Enterprise owners** can enforce a policy to disable deploy keys across all repositories. See [Enforcing repository management policies in your enterprise](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise).

For more information on deploy keys, see [Managing deploy keys](/en/authentication/connecting-to-github-with-ssh/managing-deploy-keys).

### `GITHUB_TOKEN` (GitHub Actions)

* **Automatically expires**: The `GITHUB_TOKEN` is created at the start of each workflow job and expires when the job completes. There is no manual revocation mechanism. During an incident, you can disable GitHub Actions on the repository to prevent new tokens from being issued.

For more information on `GITHUB_TOKEN`, see [GITHUB\_TOKEN](/en/actions/concepts/security/github_token).

## SSO authorization

When single sign-on (SSO) is required at the enterprise level, enforced at the organization level, or enabled for an organization and a member has linked an identity, certain credential types must be authorized for an organization before they can access organization resources. The following table indicates which credential types can be authorized for an organization.

| Token type                           | Supports SSO authorization                                                                                                                                                                                                                                                                                                                                                                                                                   | Admins can revoke SSO authorization                                                                                                                                                                                                                                                                                                                                                                                      |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Personal access token (classic)      | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                       |
| Fine-grained personal access token   | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="No" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> |
| OAuth app access token               | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>[^1]                                                                                                                       | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="No" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> |
| GitHub App user access token         | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>[^1]                                                                                                                       | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="No" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> |
| GitHub App installation access token | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="No" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> (not required)      | Not applicable                                                                                                                                                                                                                                                                                                                                                                                                           |
| GitHub App refresh token             | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="No" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg>                     | Not applicable                                                                                                                                                                                                                                                                                                                                                                                                           |
| User SSH key                         | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Yes" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                       |
| Deploy key                           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="No" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> (repository-scoped) | Not applicable                                                                                                                                                                                                                                                                                                                                                                                                           |
| `GITHUB_TOKEN` (GitHub Actions)      | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="No" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> (repository-scoped) | Not applicable                                                                                                                                                                                                                                                                                                                                                                                                           |

[^1]: SSO authorization is granted automatically when the user authorizes the app during an active SAML or OIDC session. These authorizations are not visible to users or admins in the GitHub UI, and are not returned by the [List SAML SSO authorizations for an organization](/en/rest/orgs/orgs#list-saml-sso-authorizations-for-an-organization) REST API endpoint.

For information on how to authorize a credential for SSO, see [Authorizing a personal access token for use with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-single-sign-on/authorizing-a-personal-access-token-for-use-with-single-sign-on), [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token), and [Authorizing an SSH key for use with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-single-sign-on/authorizing-an-ssh-key-for-use-with-single-sign-on).

### Revoking SSO authorization

On GitHub Enterprise Cloud with SSO enforced, when a credential supports SSO authorization, there are two independent containment options:

* **Delete or revoke the credential itself**: Permanently removes all access associated with the credential. See the individual credential type sections above for who can perform this action.
* **Revoke the credential's SSO authorization**: Blocks the credential from accessing a specific organization's resources without deleting it. Once revoked, the user cannot re-authorize the same credential; they must create a new one.

Enterprise administrators and organization owners can revoke SSO authorization for the credential types marked in the table above:

* **Organization owners** can manage SSO authorizations for organizations with organization-level SSO via the GitHub UI. See [Viewing and managing a member's SAML access to your organization](/en/enterprise-cloud@latest/organizations/granting-access-to-your-organization-with-saml-single-sign-on/viewing-and-managing-a-members-saml-access-to-your-organization).
* **Enterprise owners** can manage SSO authorizations for enterprises with enterprise-level SSO (including Enterprise Managed Users) via the GitHub UI. See [Viewing and managing a user's SAML access to your enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/viewing-and-managing-a-users-saml-access-to-your-enterprise#viewing-and-revoking-authorized-credentials).

You can also manage SSO authorizations via the REST API. See [REST API endpoints for organizations](/en/rest/orgs/orgs?apiVersion=2022-11-28#list-saml-sso-authorizations-for-an-organization).

During a security incident, enterprise owners can revoke SSO authorizations in bulk. See [Bulk actions for security incidents](#bulk-actions-for-security-incidents).

## Bulk actions for security incidents

During a major security incident, there are some enterprise-level bulk actions that enterprise owners on GitHub Enterprise Cloud can take to respond quickly. These actions affect user SSH keys, OAuth app user access tokens, GitHub App user access tokens, personal access tokens (classic), and fine-grained personal access tokens. They do **not** affect GitHub App installation access tokens, deploy keys, or `GITHUB_TOKEN`.

> \[!WARNING] These are high-impact actions that should be reserved for major security incidents. They are likely to break automations, and it could take months of work to restore your original state.

* **Lock down SSO**: Temporarily block SSO for all users except enterprise owners, preventing access to SSO-protected resources. Available for Enterprise Managed Users or enterprises that use SSO. See [Locking down single sign-on in your enterprise](/en/enterprise-cloud@latest/admin/managing-iam/respond-to-incidents/lock-down-sso).
* **Revoke all SSO authorizations**: Remove SSO authorizations for user credentials across all organizations in the enterprise. Credentials are not deleted, but lose access to SSO-protected organization resources. Once revoked, credentials cannot be re-authorized—users must create new credentials. Available for Enterprise Managed Users or enterprises that use SSO. See [Revoking SSO authorizations or deleting credentials in your enterprise](/en/enterprise-cloud@latest/admin/managing-iam/respond-to-incidents/revoke-authorizations-or-tokens).
* **Delete all user tokens and keys**: Delete user credentials entirely, removing all access. Available for Enterprise Managed Users **only**. See [Revoking SSO authorizations or deleting credentials in your enterprise](/en/enterprise-cloud@latest/admin/managing-iam/respond-to-incidents/revoke-authorizations-or-tokens).

> \[!NOTE]
> For enterprises with personal accounts (non-EMU) that use SSO, the "delete all tokens and keys" option is **not available**. The "revoke SSO authorizations" action blocks access to SSO-protected organization resources, but does not block credentials from accessing enterprise-level endpoints or resources in organizations that do not enforce SSO. For enterprises without SSO, neither bulk action is available.