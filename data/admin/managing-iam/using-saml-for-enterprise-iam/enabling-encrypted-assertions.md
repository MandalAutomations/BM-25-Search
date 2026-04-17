# Enabling encrypted assertions

You can improve GitHub.com's security with SAML single sign-on (SSO) by encrypting the messages that your SAML identity provider (IdP) sends.

## About encrypted assertions

If your IdP support encryption of assertions, you can configure encrypted assertions on GitHub Enterprise Server for increased security during the authentication process.

## Prerequisites

To enable encrypted assertions for authentication to GitHub Enterprise Server, you must configure SAML authentication, and your IdP must support encrypted assertions.

## Enabling encrypted assertions

To enable encrypted assertions, you must provide your GitHub Enterprise Server instance's public certificate to your IdP, and configure encryption settings that match your IdP.

> \[!NOTE]
> GitHub strongly recommends that you verify any new configuration for authentication in a staging environment. An incorrect configuration could result in downtime for your GitHub Enterprise Server instance. For more information, see [Setting up a staging instance](/en/enterprise-server@3.20/admin/installation/setting-up-a-github-enterprise-server-instance/setting-up-a-staging-instance).

1. Optionally, enable SAML debugging. SAML debugging records verbose entries in GitHub Enterprise Server's authentication log, and may help you troubleshoot failed authentication attempts. For more information, see [Troubleshooting SAML authentication](/en/enterprise-server@3.20/admin/identity-and-access-management/using-saml-for-enterprise-iam/troubleshooting-saml-authentication#configuring-saml-debugging).
2. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
3. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
4. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
5. In the "Settings" sidebar, click **Authentication**.
6. Select **Require encrypted assertions**.
7. To the right of "Encryption Certificate", to save a copy of your GitHub Enterprise Server instance's public certificate on your local machine, click **Download**.
8. Sign into your SAML IdP as an administrator.
9. In the application for your GitHub Enterprise Server instance, enable encrypted assertions.
   * Note the encryption method and key transport method.
   * Provide the public certificate you downloaded in step 7.
10. Return to the management console on your GitHub Enterprise Server instance.
11. To the right of "Encryption Method", select the encryption method for your IdP from step 9.
12. To the right of "Key Transport Method", select the key transport method for your IdP from step 9.
13. Click **Save settings**.
14. Wait for the configuration run to complete.

If you enabled SAML debugging to test authentication with encrypted assertions, disable SAML debugging when you're done testing. For more information, see [Troubleshooting SAML authentication](/en/enterprise-server@3.20/admin/identity-and-access-management/using-saml-for-enterprise-iam/troubleshooting-saml-authentication#configuring-saml-debugging).

## SAML signing certificate for AuthnRequests

With encrypted assertions, GitHub Enterprise Server relies on the SAML signing certificate private key to decrypt assertions. This certificate is automatically generated when GitHub Enterprise Server is set up, and it is valid for 10 years.

You can find more details about the SAML signing certificate, how long it is valid for, and how to regenerate it if needed in [SAML configuration reference](/en/enterprise-server@3.20/admin/managing-iam/iam-configuration-reference/saml-configuration-reference#saml-signing-certificate-for-authnrequests).