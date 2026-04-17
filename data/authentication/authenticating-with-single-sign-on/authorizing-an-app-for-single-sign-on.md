# Authorizing an app for single sign-on

To use an OAuth app or GitHub App with an organization that uses single sign-on (SSO), you must first set up your SSO sessions and then authorize the application.

## About authorizing apps with SSO

If your organization or enterprise uses single sign-on (SSO) and you want to access the organization or enterprise's resources through an OAuth app or GitHub App, you must set up an active SSO session and then authorize the app.

If you do not have an SSO session with an organization's identity provider when you go through the app authentication flow, you will not be able to request or install the application for that organization.

When you sign in to an application (also known as authorizing it), the token that the app receives can be used against any of the organizations where the app is allowed (via installation or approval) *and* you meet the SSO provider requirements.

If you want to sign in to an application but do not want the resulting token to have access to a specific SSO-protected organization, you must first sign out of your SSO session with the organization.

## Authorizing an app for  SSO

Apps are automatically authorized for all of the organizations you have an SSO session for at the time of sign in, as long as the app itself is allowed in that organization.

If you sign into an app but it is unable to access an organization you belong to, first check that the app is approved or installed for the organization. If it is, you then need to sign into that organization's SSO providers using the following steps:

1. Go to your [organization settings](https://github.com/settings/organizations).

2. Under "Single sign-on", find the organization you need to authenticate to, and click **Sign in**.
   If your enterprise manages SSO for your organization, signing in to one organization in the enterprise works as an SSO session for all organizations in the enterprise.

3. Try to sign into the the app again. When you are authorizing the app you will see the organizations you've signed into and be able to request or install the app for those organizations.

For more information, see [Installing a GitHub App from a third party](/en/enterprise-cloud@latest/apps/using-github-apps/installing-a-github-app-from-a-third-party), [Installing a GitHub App from GitHub Marketplace for your organizations](/en/enterprise-cloud@latest/apps/using-github-apps/installing-a-github-app-from-github-marketplace-for-your-organizations), and [Requesting a GitHub App from your organization owner](/en/enterprise-cloud@latest/apps/using-github-apps/requesting-a-github-app-from-your-organization-owner).

For more information about authorizing apps with SSO, see [Authorizing OAuth apps](/en/enterprise-cloud@latest/apps/oauth-apps/using-oauth-apps/authorizing-oauth-apps) or [SAML and GitHub Apps](/en/enterprise-cloud@latest/apps/using-github-apps/saml-and-github-apps).