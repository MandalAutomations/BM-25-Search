# Revoking SSO authorizations or deleting credentials in your enterprise

Respond to a security incident by taking bulk action on credentials with access to your enterprise.

When your enterprise is affected by a major security incident, you can respond by preventing programmatic access to your enterprise or its organizations.

In the  "Authentication security" section of your enterprise settings, you can review counts for user tokens and keys that are authorized for single sign-on (SSO). Then, if needed, you can use one of the following bulk actions in the "Danger zone":

* **Revoke SSO authorizations** to remove access to SSO-protected organization resources for user credentials in your enterprise.
* **Delete keys and tokens** to remove user tokens and SSH keys in your enterprise, even if they don't have an SSO authorization (Enterprise Managed Users only).

> \[!WARNING] These are high-impact actions that should be reserved for major security incidents. They are likely to break automations, and it could take months of work to restore your original state. For alternative options for responding to individual compromised tokens on a smaller scale, see the [Resources for smaller-scale responses](#resources-for-smaller-scale-responses) section.

## Accessing the authentication security page

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. In the left sidebar, click **Authentication security**.

## Reviewing credentials

In the "Credentials" section, you can view how many credentials of each type have **at least one SSO authorization** for an organization in your enterprise. For more information, see [About authentication with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-single-sign-on/about-authentication-with-single-sign-on).

The counts include:

* Fine-grained personal access tokens
* Personal access tokens (classic)
* User SSH keys
* GitHub App and OAuth app user access tokens

An exact count is displayed if there are 10,000 or fewer of a token type. Above that figure, the description `10k+ tokens` is displayed.

## Taking bulk action (danger zone)

Use the **Danger zone** bulk action buttons to respond to a security incident as needed. The following sections describe each action, which SSO authorizations or credentials are impacted, and related audit log events.

> \[!NOTE] If your enterprise does **not** use Enterprise Managed Users and has **not** enabled SAML SSO, neither of these actions is available. As an alternative, if you need users to replace personal access tokens as part of your incident response, you can configure an enterprise policy to expire all personal access tokens. See [Enforcing policies for personal access tokens in your enterprise](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-personal-access-tokens-in-your-enterprise).

### Revoke SSO authorizations

This action is available for Enterprise Managed Users or enterprises that use SAML SSO.

Revoking authorizations removes SSO authorizations for user tokens and SSH keys across all organizations in your enterprise.

* Credentials that have had SSO authorizations revoked **cannot be re-authorized** for the affected organizations. To restore access, users must create new credentials and authorize them.
* The credentials themselves are not deleted, and their permissions for the user and enterprise scopes, and for non-SSO-protected organizations, **remain active**.
* Credentials that have not been authorized for SSO are **not affected**.

Authorization for **fine-grained personal access tokens** works differently, so this action has a different effect on this token type. For fine-grained PATs where an organization is the "resource owner," the resource owner is removed, removing access to organization resources. Users can change the resource owner back to the organization account, which may require approval (see [Enforcing policies for personal access tokens in your enterprise](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-personal-access-tokens-in-your-enterprise#enforcing-an-approval-policy-for-fine-grained-personal-access-tokens)).

### Delete keys and tokens

This action is available for Enterprise Managed Users only.

Deleting keys and tokens removes credentials that have access to your enterprise, regardless of whether they are authorized for SSO. The credentials stop working and are no longer visible in the UI.

To restore programmatic access, users must create new credentials, authorize them with organizations if required, and update affected processes to use the new credentials.

### Included credentials

Both actions include the following credential types:

* User SSH keys
* OAuth apps user access tokens (`ghu_`)
* GitHub App user access tokens
* Personal access tokens (classic)
* Fine-grained personal access tokens

Note that the "revoke authorizations" action works differently for fine-grained personal access tokens, as explained above.

The following credential types are **not** affected:

* GitHub App installation tokens (`ghs_`)
* Fine-grained personal access tokens
* Deploy keys
* GitHub Actions `GITHUB_TOKEN` access

### Audit and security log events

The "revoke authorizations" action generates the following events:

* `org_credential_authorization.deauthorize`
* `org_credential_authorization.revoke`
* `personal_access_token.access_revoked`

The "delete tokens" action also generates those events, and additionally generates the following events:

* `oauth_access.destroy`
* `personal_access_token.destroy`

## Resources for smaller-scale responses

The following articles describe alternative actions for managing incidents that are smaller in scope, where you can identify specific compromised tokens or user accounts.

* [Identifying audit log events performed by an access token](/en/enterprise-cloud@latest/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/identifying-audit-log-events-performed-by-an-access-token)
* [Remediating a leaked secret in your repository](/en/enterprise-cloud@latest/code-security/tutorials/remediate-leaked-secrets/remediating-a-leaked-secret)
* [Revocation](/en/enterprise-cloud@latest/rest/credentials/revoke) in the REST API documentation