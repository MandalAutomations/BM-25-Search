# Token expiration and revocation

Your tokens can expire and can also be revoked by you, applications you have authorized, and GitHub itself.

When a token has expired or has been revoked, it can no longer be used to authenticate Git and API requests. It is not possible to restore an expired or revoked token, you or the application will need to create a new token.

This article explains the possible reasons your GitHub token might be revoked or expire.

> \[!NOTE]
> When a personal access token, OAuth app token, or GitHub App token expires or is revoked, you may see an `oauth_authorization.destroy` action in your security log. For more information, see [Reviewing your security log](/en/authentication/keeping-your-account-and-data-secure/reviewing-your-security-log).

## Token revoked after reaching its expiration date

When you create a personal access token, we recommend that you set an expiration for your token. Upon reaching your token's expiration date, the token is automatically revoked. For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

## Token revoked when pushed to a public repository or public gist

If a valid OAuth token, GitHub App token, or personal access token is pushed to a public repository or public gist, the token will be automatically revoked.

## Token expired due to lack of use

GitHub will automatically revoke an OAuth token or personal access token when the token hasn't been used in one year.

## Token revoked by the user

You can revoke your authorization of a GitHub App or OAuth app from your account settings which will revoke any tokens associated with the app. For more information, see [Reviewing and revoking authorization of GitHub Apps](/en/apps/using-github-apps/reviewing-your-authorized-integrations) and [Reviewing your authorized OAuth apps](/en/apps/oauth-apps/using-oauth-apps/reviewing-your-authorized-applications-oauth).

Once an authorization is revoked, any tokens associated with the authorization will be revoked as well. To reauthorize an application, follow the instructions from the third-party application or website to connect your account on GitHub again.

## Token revoked by a third party

To prevent unauthorized access using exposed tokens, GitHub recommends token revocation to ensure that a token can no longer be used to authenticate to GitHub. The credential revocation API supports revoking the following token types:

* Personal access tokens (classic) with the `ghp_` prefix
* Fine-grained personal access tokens with the `github_pat_` prefix
* OAuth app tokens with the `gho_` prefix
* GitHub App user-to-server tokens with the `ghu_` prefix
* GitHub App refresh tokens with the `ghr_` prefix

If you find any of these tokens leaked on GitHub or elsewhere, you can submit a revocation request through the REST API. See [Revocation](/en/rest/credentials/revoke#revoke-a-list-of-credentials) for the complete and authoritative list of supported token types.

When a valid token is submitted to GitHub's credential revocation API, the token will be automatically revoked. This API allows a third party to revoke a token they do not own and helps protect the data associated with this token from unauthorized access, limiting the impact of exposed tokens.

To encourage reports and ensure that exposed tokens can be quickly and easily revoked, we do not require authentication for the revocation requests submitted through the API. As a result, GitHub is unable to provide further information about the source of the reported token.

## Token revoked by the OAuth app

The owner of an OAuth app can revoke an account's authorization of their app, this will also revoke any tokens associated with the authorization. For more information about revoking authorizations of your OAuth app, see [REST API endpoints for OAuth authorizations](/en/rest/apps/oauth-applications#delete-an-app-authorization).

OAuth app owners can also revoke individual tokens associated with an authorization. For more information about revoking individual tokens for your OAuth app, see [REST API endpoints for OAuth authorizations](/en/rest/apps/oauth-applications#delete-an-app-token).

## Token revoked due to excess of tokens for an OAuth app with the same scope

There is a limit of ten tokens that are issued per user/application/scope combination, and a rate limit of ten tokens created per hour. If an application creates more than ten tokens for the same user and the same scopes, the oldest tokens with the same user/application/scope combination are revoked. However, hitting the hourly rate limit will not revoke your oldest token. Instead, it will trigger a re-authorization prompt within the browser, asking the user to double check the permissions they're granting your app. This prompt is intended to give a break to any potential infinite loop the app is stuck in, since there's little to no reason for an app to request ten tokens from the user within an hour.

## User token expired due to GitHub App configuration

User access tokens created by a GitHub App will expire after eight hours by default, and then must be regenerated using the included refresh token. Owners of GitHub Apps can optionally configure these tokens to never expire instead, but this is not recommended due to the security implications. For more information about configuring your GitHub App's user access tokens, see [Activating optional features for GitHub Apps](/en/apps/maintaining-github-apps/activating-optional-features-for-github-apps).