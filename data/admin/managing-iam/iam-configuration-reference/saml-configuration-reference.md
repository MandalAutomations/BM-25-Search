# SAML configuration reference

You can see SAML metadata for , and you can learn more about available SAML attributes and response requirements.

## About SAML configuration

To use SAML single sign-on (SSO) for authentication to GitHub, you must configure both your external SAML identity provider (IdP) and your enterprise or organization on GitHub. In a SAML configuration, GitHub functions as a SAML service provider (SP). For more information about authentication for your enterprise, see [Identity and access management fundamentals](/en/enterprise-cloud@latest/admin/identity-and-access-management/understanding-iam-for-enterprises/about-identity-and-access-management#authentication-methods).

GitHub provides integration according to the SAML 2.0 specification. For more information, see the [SAML Wiki](https://wiki.oasis-open.org/security) on the OASIS website.

You must enter unique values from your SAML IdP when configuring SAML SSO for GitHub, and you must also enter unique values from GitHub on your IdP.

## SAML metadata

The SP metadata for GitHub Enterprise Cloud is available for either organizations or enterprises with SAML SSO. GitHub uses the `urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST` binding.

If you use Enterprise Managed Users, you can only enable SAML SSO at the enterprise level.

### Organizations

You can configure SAML SSO for an individual organization in your enterprise. You can also configure SAML SSO for an organization if you use an individual organization on GitHub Enterprise Cloud and do not use an enterprise account. For more information, see [Managing SAML single sign-on for your organization](/en/enterprise-cloud@latest/organizations/managing-saml-single-sign-on-for-your-organization).

The SP metadata for an organization on GitHub is available at `https://github.com/orgs/ORGANIZATION/saml/metadata`, where **ORGANIZATION** is the name of your organization on GitHub.

| Value                                   | Other names                          | Description                                           | Example                                             |
| :-------------------------------------- | :----------------------------------- | :---------------------------------------------------- | :-------------------------------------------------- |
| SP Entity ID                            | SP URL, audience restriction         | The top-level URL for your organization on GitHub.com | `https://github.com/orgs/ORGANIZATION`              |
| SP Assertion Consumer Service (ACS) URL | Reply, recipient, or destination URL | URL where IdP sends SAML responses                    | `https://github.com/orgs/ORGANIZATION/saml/consume` |
| SP Single Sign-On (SSO) URL             |                                      | URL where IdP begins SSO                              | `https://github.com/orgs/ORGANIZATION/sso`          |

### Enterprises

Depending on your environment, the SP metadata for an enterprise on GitHub Enterprise Cloud is available at either:

* `https://github.com/enterprises/ENTERPRISE/saml/metadata`, where **ENTERPRISE** is the name of your enterprise
* `https://SUBDOMAIN.ghe.com/enterprises/SUBDOMAIN/saml/metadata`, where **SUBDOMAIN** is the subdomain for your enterprise

| Value                                   | Other names                          | Description                                         | Example                                                  |
| :-------------------------------------- | :----------------------------------- | :-------------------------------------------------- | :------------------------------------------------------- |
| SP Entity ID                            | SP URL, audience restriction         | The top-level URL for your enterprise on GitHub.com | `https://github.com/enterprises/ENTERPRISE`              |
| SP Assertion Consumer Service (ACS) URL | Reply, recipient, or destination URL | URL where IdP sends SAML responses                  | `https://github.com/enterprises/ENTERPRISE/saml/consume` |
| SP Single Sign-On (SSO) URL             |                                      | URL where IdP begins SSO                            | `https://github.com/enterprises/ENTERPRISE/sso`          |

## SAML attributes

The following SAML attributes are available for GitHub.

| Name                  | Required                                                                                                                                                                                                                                                                                                                                                                                                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| :-------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `NameID`              | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Required" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                                                                        | A persistent user identifier. Any persistent name identifier format may be used. If you use an enterprise with Enterprise Managed Users, GitHub will normalize the `NameID` element to use as a username unless one of the alternative assertions is provided. For more information, see [Username considerations for external authentication](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-iam-for-your-enterprise/username-considerations-for-external-authentication).<br><br> > \[!NOTE] It's important to use a human-readable, persistent identifier. Using a transient identifier format like `urn:oasis:names:tc:SAML:2.0:nameid-format:transient` will result in re-linking of accounts on every sign-in, which can be detrimental to authorization management. |
| `SessionNotOnOrAfter` | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Optional" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> | The date that GitHub invalidates the associated session. After invalidation, the person must authenticate once again to access your enterprise's resources. For more information, see [Session duration and timeout](#session-duration-and-timeout).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|                       |                                                                                                                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `full_name`           | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Optional" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> | If you configure SAML SSO for an enterprise and you use Enterprise Managed Users, the full name of the user to display on the user's profile page.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `emails`              | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Optional" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> | The email addresses for the user. If you sync license usage between GitHub Enterprise Server and GitHub Enterprise Cloud, GitHub Connect uses `emails` to identify unique users across products. For more information, see [Syncing license usage from GitHub Enterprise Server to Cloud](/en/enterprise-cloud@latest/billing/managing-your-license-for-github-enterprise/syncing-license-usage-between-github-enterprise-server-and-github-enterprise-cloud).                                                                                                                                                                                                                                                                                                                                        |
| `public_keys`         | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Optional" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> | If you configure SAML SSO for an enterprise and you use Enterprise Managed Users, the public SSH keys for the user. You can specify more than one key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `gpg_keys`            | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Optional" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> | If you configure SAML SSO for an enterprise and you use Enterprise Managed Users, the GPG keys for the user. You can specify more than one key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

To specify more than one value for an attribute, use multiple `<saml2:AttributeValue>` elements.

```xml
<saml2:Attribute FriendlyName="public_keys" Name="urn:oid:1.2.840.113549.1.1.1" NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri">
    <saml2:AttributeValue>ssh-rsa LONG KEY</saml2:AttributeValue>
    <saml2:AttributeValue>ssh-rsa LONG KEY 2</saml2:AttributeValue>
</saml2:Attribute>
```

## SAML response requirements

GitHub requires that the response message from your IdP fulfill the following requirements.

* Your IdP must provide the `<Destination>` element on the root response document and match the ACS URL only when the root response document is signed. If your IdP signs the assertion, GitHub will ignore the assertion.
* Your IdP must always provide the `<Audience>` element as part of the `<AudienceRestriction>` element. The value must match your `EntityId` for GitHub.
  * If you configure SAML for an organization, this value is `https://github.com/orgs/ORGANIZATION`.
  * If you configure SAML for an enterprise, this URL is `https://github.com/enterprises/ENTERPRISE` or `https://SUBDOMAIN.ghe.com/enterprises/SUBDOMAIN`.
* Your IdP must provide a single assertion in the response with a digital signature. You can accomplish this by signing the `<Assertion>` element or by signing the `<Response>` element.
* Your IdP must provide a `<NameID>` element as part of the `<Subject>` element. You may use any persistent name identifier format.
* Your IdP must include the `Recipient` attribute, which must be set to the ACS URL. The following example demonstrates the attribute.

  ```xml
  <samlp:Response ...>
    <saml:Assertion ...>
      <saml:Subject>
        <saml:NameID ...>...</saml:NameID>
        <saml:SubjectConfirmation ...>
          <saml:SubjectConfirmationData Recipient="https://github.com/enterprises/ENTERPRISE/saml/consume" .../>
        </saml:SubjectConfirmation>
      </saml:Subject>
      <saml:AttributeStatement>
        <saml:Attribute FriendlyName="USERNAME-ATTRIBUTE" ...>
          <saml:AttributeValue>monalisa</saml:AttributeValue>
        </saml:Attribute>
      </saml:AttributeStatement>
    </saml:Assertion>
  </samlp:Response>
  ```

## Session duration and timeout

To prevent a person from authenticating with your IdP and staying authorized indefinitely, GitHub periodically invalidates the session for each user account with access to your enterprise's resources. After invalidation, the person must authenticate with your IdP once again.

By default, if your IdP does not assert a value for the `SessionNotOnOrAfter` attribute, GitHub invalidates a session 24 hours after successful authentication with your IdP.

GitHub will support a customized session duration if your IdP provides the option to configure a `SessionNotOnOrAfter` attribute and value.

If you define a customized session duration value less than 24 hours, GitHub may prompt people to authenticate every time GitHub initiates a redirect.

To prevent authentication errors, we recommend a minimum session duration of 4 hours. For more information, see [Troubleshooting SAML authentication](/en/enterprise-cloud@latest/admin/identity-and-access-management/using-saml-for-enterprise-iam/troubleshooting-saml-authentication#users-are-repeatedly-redirected-to-authenticate).

> \[!NOTE] Microsoft Entra ID (previously known as Azure AD) **does not support the `SessionNotOnOrAfter` attribute**. Additionally, the configurable lifetime policy for SAML tokens issued by Entra ID **does not control session timeout** for GitHub.