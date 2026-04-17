# Supported secret scanning patterns


Lists of supported secrets and the partners that GitHub works with to prevent fraudulent use of secrets that were committed accidentally.


## About secret scanning patterns

There are three types of secret scanning alerts:

* **User alerts:** Reported to users in the ** Security and quality** tab of the repository, when a supported secret is detected in the repository.
* **Push protection alerts:** Reported to users in the ** Security and quality** tab of the repository, when a contributor bypasses push protection.
* **Partner alerts:** Reported directly to secret providers that are part of secret scanning's partner program. These alerts are not reported in the ** Security and quality** tab of the repository.

For in-depth information about each alert type, see [About secret scanning alerts](/en/code-security/secret-scanning/managing-alerts-from-secret-scanning/about-alerts).

For details about all the supported patterns, see the [Supported secrets](#supported-secrets) section below.

If you use the REST API for secret scanning, you can use the `Secret type` to report on secrets from specific issuers. For more information, see [REST API endpoints for secret scanning](/en/enterprise-cloud@latest/rest/secret-scanning).

If you believe that secret scanning should have detected a secret committed to your repository, and it has not, you first need to check that GitHub supports your secret. For more information, refer to the following sections. For more advanced troubleshooting information, see [Secret scanning detection scope](/en/code-security/secret-scanning/troubleshooting-secret-scanning-and-push-protection/troubleshooting-secret-scanning).

## Supported secrets

The tables list the secrets supported by secret scanning for each secret type. Information in the tables may include this data:

* **Provider:** Name of the token provider.
* **Partner:** Token for which leaks are reported to the relevant token partner. Applies to public repositories and all gists, including secret gists. Secret gists are not private and can be accessed by anyone with the URL. See [About gists](/en/get-started/writing-on-github/editing-and-sharing-content-with-gists/creating-gists#about-gists).
* **User:** Token for which leaks are reported to users on GitHub.
  * Applies to public repositories, and to private repositories where GitHub Secret Protection and secret scanning are enabled.
  * Includes default tokens, which relate to supported patterns and specified custom patterns, as well as non-provider tokens such as private keys, which usually have a higher ratio of false positives.
  * For secret scanning to scan for non-provider patterns, the detection of non-provider patterns must be enabled for the repository or the organization. For more information, see [Enabling secret scanning for your repository](/en/code-security/secret-scanning/enabling-secret-scanning-features/enabling-secret-scanning-for-your-repository).
* **Push protection:** Token for which leaks are reported to users on GitHub. Applies to repositories with secret scanning and push protection enabled.
* **Validity check:** Token for which a validity check is implemented. For partner tokens, GitHub sends the token to the relevant partner. Note that not all partners are based in the United States. For more information, see [Advanced Security](/en/site-policy/github-terms/github-terms-for-additional-products-and-features#advanced-security) in the Site Policy documentation.
* **Metadata check:** Token for which extended metadata is available, providing additional context about the detected secret.
* **Base64:** Token for which Base64-encoded versions are supported.

### Non-provider patterns

Precision levels are estimated based on the pattern type's typical false positive rates.

| Provider | Token                                | Description                                                            | Precision |
| :------- | :----------------------------------- | :--------------------------------------------------------------------- | :-------- |
| Generic  | ec\_private\_key                     | Elliptic Curve (EC) private keys used for cryptographic operations     | High      |
| Generic  | generic\_private\_key                | Cryptographic private keys with `-----BEGIN PRIVATE KEY-----` header   | High      |
| Generic  | http\_basic\_authentication\_header  | HTTP Basic Authentication credentials in request headers               | Medium    |
| Generic  | http\_bearer\_authentication\_header | HTTP Bearer tokens used for API authentication                         | Medium    |
| Generic  | mongodb\_connection\_string          | Connection strings for MongoDB databases containing credentials        | High      |
| Generic  | mysql\_connection\_url               | Connection strings for MySQL databases containing credentials          | High      |
| Generic  | openssh\_private\_key                | OpenSSH format private keys used for SSH authentication                | High      |
| Generic  | pgp\_private\_key                    | PGP (Pretty Good Privacy) private keys used for encryption and signing | High      |
| Generic  | postgres\_connection\_string         | Connection strings for PostgreSQL databases containing credentials     | High      |
| Generic  | rsa\_private\_key                    | RSA private keys used for cryptographic operations                     | High      |

> \[!NOTE]
> Validity checks are **not supported** for non-provider patterns.

### Copilot secret scanning

Secret scanning uses Copilot to detect generic passwords. See [Responsible detection of generic secrets with Copilot secret scanning](/en/code-security/secret-scanning/copilot-secret-scanning/responsible-ai-generic-secrets).

| Provider | Token    |
| -------- | :------- |
| Generic  | password |

> \[!NOTE] Push protection and validity checks are not supported for passwords.

### Default patterns

> \[!NOTE]
> Validity and extended metadata checks are only available to users with GitHub Team or GitHub Enterprise who enable the feature as part of GitHub Secret Protection.

| Provider                       | Token                                                                                                           |                                  Partner                                  |                                    User                                   |                              Push protection                              |                               Validity check                              |                               Metadata check                              |                                   Base64                                  |
| ------------------------------ | :-------------------------------------------------------------------------------------------------------------- | :-----------------------------------------------------------------------: | :-----------------------------------------------------------------------: | :-----------------------------------------------------------------------: | :-----------------------------------------------------------------------: | :-----------------------------------------------------------------------: | :-----------------------------------------------------------------------: |
| 1Password                      | 1password\_service\_account\_token                                                                              |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Adafruit                       | adafruit\_io\_key                                                                                               | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Adobe                          | adobe\_client\_secret                                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Adobe                          | adobe\_device\_token                                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Adobe                          | adobe\_pac\_token                                                                                               | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Adobe                          | adobe\_refresh\_token                                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Adobe                          | adobe\_service\_token                                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Adobe                          | adobe\_short\_lived\_access\_token                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Aikido                         | aikido\_api\_client\_secret                                                                                     |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Aikido                         | aikido\_ci\_scanning\_token                                                                                     |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Airtable                       | airtable\_api\_key                                                                                              |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Airtable                       | airtable\_personal\_access\_token                                                                               |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Aiven                          | aiven\_auth\_token                                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Aiven                          | aiven\_service\_password                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Alibaba                        | alibaba\_cloud\_access\_key\_id, alibaba\_cloud\_access\_key\_secret                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Amazon AWS                     | aws\_access\_key\_id, aws\_secret\_access\_key 
[Token versions](#token-versions)           | ✓ | ✓ | ✓ | ✓ |  ✗  | ✓ |
| Amazon AWS                     | aws\_api\_key                                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Amazon AWS                     | aws\_secret\_access\_key, aws\_session\_token, aws\_temporary\_access\_key\_id                        |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Anthropic                      | anthropic\_admin\_api\_key                                                                                      | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Anthropic                      | anthropic\_api\_key 
[Token versions](#token-versions)                                           | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Anthropic                      | anthropic\_session\_id                                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Apify                          | apify\_actor\_run\_api\_token                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Apify                          | apify\_actor\_run\_proxy\_password                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Apify                          | apify\_api\_token                                                                                               | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Apify                          | apify\_integration\_api\_token                                                                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Apify                          | apify\_proxy\_password                                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Apify                          | apify\_ui\_token                                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Apify                          | apify\_webhook\_dispatch\_api\_token                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Asaas                          | asaas\_api\_token                                                                                               | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Asana                          | asana\_legacy\_format\_personal\_access\_token                                                                  |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Asana                          | asana\_personal\_access\_token 
[Token versions](#token-versions)                                |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Atlassian                      | atlassian\_api\_token 
[Token versions](#token-versions)                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Atlassian                      | atlassian\_jwt                                                                                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Authress                       | authress\_service\_client\_access\_key                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_active\_directory\_application\_id, azure\_active\_directory\_application\_secret                   |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_active\_directory\_application\_secret 
[Token versions](#token-versions)                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_active\_directory\_user\_credential                                                                      | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_ai\_services\_key                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_anomaly\_detector\_ee\_key                                                                               | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_anomaly\_detector\_key                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_apim\_direct\_management\_key                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_apim\_gateway\_key                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_apim\_repository\_key                                                                                    | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Azure                          | azure\_apim\_subscription\_key                                                                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_app\_configuration\_connection\_string                                                                   |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Azure                          | azure\_app\_configuration\_key                                                                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_batch\_key\_identifiable 
[Token versions](#token-versions)                               | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_cache\_for\_redis\_access\_key 
[Token versions](#token-versions)                         | ✓ | ✓ | ✓ |  ✗  |  ✗  | ✓ |
| Azure                          | azure\_cognitive\_services\_key                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_communication\_services\_connection\_string                                                              |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Azure                          | azure\_communication\_services\_key                                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_computer\_vision\_key                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_container\_registry\_key\_identifiable                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_content\_moderator\_key                                                                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_content\_safety\_key                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_cosmosdb\_key\_identifiable 
[Token versions](#token-versions)                            | ✓ | ✓ | ✓ | ✓ |  ✗  | ✓ |
| Azure                          | azure\_custom\_vision\_prediction\_key                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_custom\_vision\_training\_key                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_devops\_personal\_access\_token 
[Token versions](#token-versions)                        | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Azure                          | azure\_event\_grid\_key\_identifiable 
[Token versions](#token-versions)                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_event\_hub\_key\_identifiable                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_face\_key                                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_fluid\_relay\_key                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_form\_recognizer\_key                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_function\_key 
[Token versions](#token-versions)                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  | ✓ |
| Azure                          | azure\_health\_decision\_support\_key                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_health\_insights\_key                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_immersive\_reader\_key                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_internal\_all\_in\_one\_key                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_iot\_device\_connection\_string                                                                          |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Azure                          | azure\_iot\_device\_key                                                                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_iot\_device\_provisioning\_key                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_iot\_hub\_connection\_string                                                                             |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Azure                          | azure\_iot\_hub\_key                                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_iot\_provisioning\_connection\_string                                                                    |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Azure                          | azure\_knowledge\_key                                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_logic\_apps\_url 
[Token versions](#token-versions)                                       | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_luis\_authoring\_key                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_luis\_key                                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_management\_certificate                                                                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_maps\_key                                                                                                | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Azure                          | azure\_metrics\_advisor\_key                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_mixed\_reality\_key                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_ml\_inference\_identifiable\_key                                                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_ml\_internal\_service\_principal\_identifiable\_key                                                      | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_ml\_web\_service\_classic\_identifiable\_key                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_openai\_key 
[Token versions](#token-versions)                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  | ✓ |
| Azure                          | azure\_personalizer\_key                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_qna\_maker\_key                                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_qna\_maker\_v2\_key                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_quantum\_key                                                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_relay\_key\_identifiable                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_sas\_token                                                                                               | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_search\_admin\_key                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_search\_query\_key                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_service\_bus\_identifiable                                                                               | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_signalr\_connection\_string                                                                              |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_signalr\_key 
[Token versions](#token-versions)                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_speech\_services\_key                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_speech\_translation\_key                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_sql\_connection\_string                                                                                  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_sql\_internal\_default\_cloudsa\_key                                                                     | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_sql\_password                                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_storage\_account\_key 
[Token versions](#token-versions)                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  | ✓ |
| Azure                          | azure\_text\_analytics\_key                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_text\_translation\_key                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_video\_intelligence\_key                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_web\_app\_bot\_key                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_web\_pub\_sub\_connection\_string                                                                        |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | azure\_web\_pub\_sub\_key 
[Token versions](#token-versions)                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Azure                          | microsoft\_azure\_entra\_id\_token                                                                              |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Azure                          | microsoft\_corporate\_network\_user\_credential                                                                 | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Baidu                          | baiduai\_api\_key                                                                                               | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Baidu                          | baiducloud\_api\_accesskey                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Beamer                         | beamer\_api\_key                                                                                                |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Bitbucket                      | bitbucket\_server\_personal\_access\_token                                                                      |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Bitrise                        | bitrise\_personal\_access\_token                                                                                | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Bitrise                        | bitrise\_workspace\_api\_token                                                                                  | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Block Protocol                 | block\_protocol\_api\_key                                                                                       |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Brevo                          | sendinblue\_api\_key 
[Token versions](#token-versions)                                          | ✓ | ✓ | ✓ | ✓ |  ✗  | ✓ |
| Brevo                          | sendinblue\_smtp\_key                                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_agent\_access\_token                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_agent\_job\_token                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_agent\_registration\_token                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_cluster\_queue\_token                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_cluster\_token                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_packages\_registry\_token                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_packages\_temporary\_token                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_portal\_secret                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_portal\_token                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Buildkite                      | buildkite\_user\_access\_token                                                                                  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Canadian Digital Service       | cds\_canada\_notify\_api\_key                                                                                   | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Canva                          | canva\_app\_secret                                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Canva                          | canva\_connect\_api\_secret                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Canva                          | canva\_secret                                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Cashfree                       | cashfree\_api\_key                                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Cfx.re                         | cfxre\_server\_key                                                                                              | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Checkout.com                   | checkout\_production\_secret\_key 
[Token versions](#token-versions)                             | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Checkout.com                   | checkout\_test\_secret\_key 
[Token versions](#token-versions)                                   | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Chief Tools                    | chief\_tools\_token                                                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| CircleCI                       | circleci\_bot\_access\_token                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| CircleCI                       | circleci\_personal\_access\_token                                                                               | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| CircleCI                       | circleci\_project\_access\_token                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| CircleCI                       | circleci\_release\_integration\_token                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Clojars                        | clojars\_deploy\_token                                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Cloudflare                     | cloudflare\_account\_api\_token                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Cloudflare                     | cloudflare\_global\_user\_api\_key                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Cloudflare                     | cloudflare\_user\_api\_token                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Cockroach Labs                 | ccdb\_api\_key                                                                                                  | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Cohere                         | cohere\_api\_key                                                                                                |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Contentful                     | contentful\_personal\_access\_token                                                                             | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Contentful                     | contentful\_web\_token                                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Contributed Systems            | contributed\_systems\_credentials                                                                               | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Coveo                          | coveo\_access\_token                                                                                            | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Coveo                          | coveo\_api\_key                                                                                                 | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| crates.io                      | cratesio\_api\_token 
[Token versions](#token-versions)                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Databento                      | databento\_api\_key                                                                                             | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Databricks                     | databricks\_access\_token 
[Token versions](#token-versions)                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  | ✓ |
| Databricks                     | databricks\_account\_session\_token                                                                             | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_federated\_account\_session\_token                                                                  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_oauth\_code                                                                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_oauth\_refresh\_token                                                                               | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_oauth\_secret\_token                                                                                | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_oauth\_single\_use\_refresh\_token\_child                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_oauth\_single\_use\_refresh\_token\_parent                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_scoped\_api\_token                                                                                  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_scoped\_internal\_token                                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_token                                                                                               | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Databricks                     | databricks\_workspace\_session\_token                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Datadog                        | datadog\_api\_key                                                                                               | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Datadog                        | datadog\_app\_key                                                                                               | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Datadog                        | datadog\_rcm                                                                                                    |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Datastax                       | datastax\_astracs\_token                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| DeepSeek                       | deepseek\_api\_key                                                                                              |  ✗  | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Defined Networking             | defined\_networking\_nebula\_api\_key                                                                           | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| DevCycle                       | devcycle\_client\_api\_key                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| DevCycle                       | devcycle\_mobile\_api\_key                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| DevCycle                       | devcycle\_server\_api\_key                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| DigitalOcean                   | digitalocean\_oauth\_token                                                                                      | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| DigitalOcean                   | digitalocean\_personal\_access\_token                                                                           | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| DigitalOcean                   | digitalocean\_refresh\_token                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| DigitalOcean                   | digitalocean\_system\_token                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Discord                        | discord\_bot\_token 
[Token versions](#token-versions)                                           | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Docker                         | docker\_organization\_access\_token                                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Docker                         | docker\_personal\_access\_token                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Docker                         | docker\_swarm\_join\_token                                                                                      |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Docker                         | docker\_swarm\_unlock\_key                                                                                      |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Doppler                        | doppler\_audit\_token                                                                                           | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Doppler                        | doppler\_cli\_token                                                                                             | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Doppler                        | doppler\_personal\_token                                                                                        | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Doppler                        | doppler\_scim\_token                                                                                            | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Doppler                        | doppler\_service\_account\_token                                                                                | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Doppler                        | doppler\_service\_token                                                                                         | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Dropbox                        | dropbox\_access\_token                                                                                          | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Dropbox                        | dropbox\_short\_lived\_access\_token                                                                            | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Duffel                         | duffel\_live\_access\_token                                                                                     |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Duffel                         | duffel\_test\_access\_token                                                                                     |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Dynatrace                      | dynatrace\_api\_token                                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Dynatrace                      | dynatrace\_internal\_token                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| EasyPost                       | easypost\_production\_api\_key                                                                                  |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| EasyPost                       | easypost\_test\_api\_key                                                                                        |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| eBay                           | ebay\_production\_client\_id, ebay\_production\_client\_secret                                             |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| eBay                           | ebay\_sandbox\_client\_id, ebay\_sandbox\_client\_secret                                                   |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Elastic                        | elastic\_cloud\_api\_key                                                                                        |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Facebook                       | facebook\_access\_token                                                                                         | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Fastly                         | fastly\_api\_token 
[Token versions](#token-versions)                                            | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Fieldguide                     | fieldguide\_api\_token                                                                                          | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Figma                          | figma\_pat                                                                                                      | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Figma                          | figma\_scim\_token                                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Finicity                       | finicity\_app\_key                                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Firebase                       | firebase\_cloud\_messaging\_server\_key                                                                         |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Flickr                         | flickr\_api\_key                                                                                                |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Flutterwave                    | flutterwave\_live\_api\_secret\_key                                                                             |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Flutterwave                    | flutterwave\_test\_api\_secret\_key                                                                             |  ✗  | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Frame.io                       | frameio\_developer\_token                                                                                       | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Frame.io                       | frameio\_jwt                                                                                                    | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| FullStory                      | fullstory\_api\_key 
[Token versions](#token-versions)                                           | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| GitHub                         | github\_app\_installation\_access\_token 
[Token versions](#token-versions)                      | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GitHub                         | github\_oauth\_access\_token 
[Token versions](#token-versions)                                  | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GitHub                         | github\_personal\_access\_token 
[Token versions](#token-versions)                               | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GitHub                         | github\_refresh\_token 
[Token versions](#token-versions)                                        | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GitHub                         | github\_ssh\_private\_key                                                                                       | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| GitHub                         | github\_test\_token                                                                                             | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| GitLab                         | gitlab\_access\_token 
[Token versions](#token-versions)                                         |  ✗  | ✓ | ✓ | ✓ | ✓ | ✓ |
| GoCardless                     | gocardless\_live\_access\_token                                                                                 | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| GoCardless                     | gocardless\_sandbox\_access\_token                                                                              | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Google                         | google\_api\_key                                                                                                | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Google                         | google\_cloud\_service\_account\_credentials                                                                    | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Google                         | google\_cloud\_storage\_access\_key\_secret, google\_cloud\_storage\_service\_account\_access\_key\_id     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Google                         | google\_cloud\_storage\_access\_key\_secret, google\_cloud\_storage\_user\_access\_key\_id                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Google                         | google\_gcp\_api\_key\_bound\_service\_account                                                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Google                         | google\_gemini\_api\_key                                                                                        |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Google                         | google\_oauth\_access\_token                                                                                    | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Google                         | google\_oauth\_client\_id, google\_oauth\_client\_secret 
[Token versions](#token-versions) | ✓ | ✓ | ✓ |  ✗  |  ✗  | ✓ |
| Google                         | google\_oauth\_refresh\_token 
[Token versions](#token-versions)                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  | ✓ |
| Grafana                        | grafana\_cloud\_api\_key                                                                                        | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Grafana                        | grafana\_cloud\_api\_token                                                                                      | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Grafana                        | grafana\_project\_api\_key                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Grafana                        | grafana\_project\_service\_account\_token                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Groq                           | groq\_api\_key 
[Token versions](#token-versions)                                                | ✓ | ✓ | ✓ | ✓ |  ✗  | ✓ |
| GuardSquare                    | guardsquare\_appsweep\_api\_key                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| GuardSquare                    | guardsquare\_cli\_access\_token                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| GuardSquare                    | guardsquare\_maven\_token                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Hack Club                      | hackclub\_ai\_api\_key                                                                                          |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| HashiCorp                      | hashicorp\_vault\_batch\_token 
[Token versions](#token-versions)                                |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| HashiCorp                      | hashicorp\_vault\_root\_service\_token                                                                          |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| HashiCorp                      | hashicorp\_vault\_service\_token 
[Token versions](#token-versions)                              |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| HashiCorp                      | terraform\_api\_token                                                                                           | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| hCaptcha                       | hcaptcha\_siteverify\_secret                                                                                    |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Heroku                         | heroku\_platform\_api\_oauth2\_token                                                                            |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Heroku                         | heroku\_postgres\_connection\_url                                                                               |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Highnote                       | highnote\_rk\_live\_key                                                                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Highnote                       | highnote\_rk\_test\_key                                                                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Highnote                       | highnote\_sk\_live\_key                                                                                         | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Highnote                       | highnote\_sk\_test\_key                                                                                         | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| HOP                            | hop\_bearer                                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| HOP                            | hop\_pat                                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| HOP                            | hop\_ptk                                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Hubspot                        | hubspot\_api\_key 
[Token versions](#token-versions)                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Hubspot                        | hubspot\_personal\_access\_key                                                                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Hubspot                        | hubspot\_private\_apps\_user\_token                                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Hubspot                        | hubspot\_smtp\_credential 
[Token versions](#token-versions)                                     | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Hugging Face                   | hf\_org\_api\_key                                                                                               | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Hugging Face                   | hf\_user\_access\_token 
[Token versions](#token-versions)                                       | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| IBM                            | ibm\_cloud\_iam\_key                                                                                            | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Intercom                       | intercom\_access\_token                                                                                         |  ✗  | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Ionic                          | ionic\_personal\_access\_token 
[Token versions](#token-versions)                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Ionic                          | ionic\_refresh\_token 
[Token versions](#token-versions)                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Iterative                      | iterative\_dvc\_studio\_access\_token                                                                           | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| JFrog                          | jfrog\_platform\_access\_token                                                                                  |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| JFrog                          | jfrog\_platform\_api\_key                                                                                       |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| JFrog                          | jfrog\_platform\_reference\_token 
[Token versions](#token-versions)                             |  ✗  | ✓ | ✓ |  ✗  |  ✗  | ✓ |
| Langchain                      | langchain\_api\_personal\_key                                                                                   |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Langchain                      | langchain\_api\_server\_key                                                                                     |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Langchain                      | langsmith\_license\_key                                                                                         |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Langchain                      | langsmith\_scim\_bearer\_token                                                                                  |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Lark                           | lark\_apaas\_client\_id, lark\_apaas\_client\_secret                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Lark                           | lark\_app\_id, lark\_app\_secret                                                                           | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Lark                           | lark\_mcp\_grant\_token                                                                                         | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Lark                           | lark\_meego\_plugin\_id, lark\_meego\_plugin\_secret                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Lark                           | lark\_user\_session                                                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| LaunchDarkly                   | launchdarkly\_access\_token                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Lichess                        | lichess\_oauth\_access\_token                                                                                   | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Lichess                        | lichess\_personal\_access\_token                                                                                | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Lightspeed                     | lightspeed\_xs\_pat                                                                                             |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Limbar                         | limbar\_token                                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Linear                         | linear\_api\_key                                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Linear                         | linear\_oauth\_access\_token                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| LinkedIn                       | linkedin\_client\_secret                                                                                        |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Lob                            | lob\_live\_api\_key                                                                                             |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Lob                            | lob\_test\_api\_key                                                                                             |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Localstack                     | localstack\_api\_key                                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| LogicMonitor                   | logicmonitor\_bearer\_token                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| LogicMonitor                   | logicmonitor\_lmv1\_access\_key                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Login with Amazon              | amazon\_oauth\_client\_id, amazon\_oauth\_client\_secret                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Mailchimp                      | mailchimp\_api\_key                                                                                             | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Mailchimp                      | mandrill\_api\_key                                                                                              | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Mailersend                     | mailersend\_api\_token                                                                                          | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Mailersend                     | mailersend\_smtp\_password                                                                                      | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Mailersend                     | mailersend\_smtp\_username                                                                                      | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Mailgun                        | mailgun\_api\_key 
[Token versions](#token-versions)                                             | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Mailgun                        | mailgun\_smtp\_credential                                                                                       | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Mapbox                         | mapbox\_secret\_access\_token                                                                                   | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| MaxMind                        | maxmind\_license\_key                                                                                           | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Mercury                        | mercury\_non\_production\_api\_token                                                                            | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Mercury                        | mercury\_production\_api\_token                                                                                 | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Mergify                        | mergify\_application\_key                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| MessageBird                    | messagebird\_api\_key                                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Microsoft                      | power\_automate\_webhook\_sas                                                                                   | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Midtrans                       | midtrans\_production\_server\_key                                                                               |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Midtrans                       | midtrans\_sandbox\_server\_key                                                                                  |  ✗  | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Mistral AI                     | mistral\_ai\_api\_key                                                                                           |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| MongoDB                        | mongodb\_atlas\_db\_uri\_with\_credentials                                                                      | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| MongoDB                        | mongodb\_atlas\_service\_account\_secret                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Naver Cloud                    | navercloud\_gov\_access\_key                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Naver Cloud                    | navercloud\_gov\_access\_key\_secret                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Naver Cloud                    | navercloud\_gov\_sts                                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Naver Cloud                    | navercloud\_gov\_sts\_secret                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Naver Cloud                    | navercloud\_pub\_access\_key                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Naver Cloud                    | navercloud\_pub\_access\_key\_secret                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Naver Cloud                    | navercloud\_pub\_sts                                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Naver Cloud                    | navercloud\_pub\_sts\_secret                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Neon                           | neon\_api\_key                                                                                                  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Neon                           | neon\_connection\_uri                                                                                           | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Netflix                        | netflix\_netkey                                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| New Relic                      | new\_relic\_insights\_query\_key                                                                                |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| New Relic                      | new\_relic\_license\_key                                                                                        |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| New Relic                      | new\_relic\_personal\_api\_key                                                                                  |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| New Relic                      | new\_relic\_rest\_api\_key                                                                                      |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Notion                         | notion\_api\_token                                                                                              | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Notion                         | notion\_integration\_token                                                                                      |  ✗  | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Notion                         | notion\_oauth\_client\_secret                                                                                   |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| npm                            | npm\_access\_token 
[Token versions](#token-versions)                                            | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| NuGet                          | nuget\_api\_key 
[Token versions](#token-versions)                                               | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Octopus Deploy                 | octopus\_deploy\_api\_key                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Oculus                         | oculus\_access\_token                                                                                           |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| OneChronos                     | onechronos\_api\_key                                                                                            |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| OneChronos                     | onechronos\_eb\_api\_key                                                                                        |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| OneChronos                     | onechronos\_eb\_encryption\_key                                                                                 |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| OneChronos                     | onechronos\_oauth\_token                                                                                        |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| OneChronos                     | onechronos\_refresh\_token                                                                                      |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| OneSignal                      | onesignal\_rich\_authentication\_token                                                                          | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Onfido                         | onfido\_live\_api\_token                                                                                        | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Onfido                         | onfido\_sandbox\_api\_token                                                                                     | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| OpenAI                         | openai\_api\_key 
[Token versions](#token-versions)                                              | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| OpenRouter                     | openrouter\_api\_key                                                                                            | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| OpenVSX                        | openvsx\_access\_token 
[Token versions](#token-versions)                                        |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Openweather                    | openweather\_api\_key                                                                                           |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Oracle                         | oracle\_api\_key                                                                                                | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Orbit                          | orbit\_api\_token                                                                                               |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Paddle                         | paddle\_api\_key                                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Paddle                         | paddle\_sandbox\_api\_key                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| PagerDuty                      | pagerduty\_oauth\_secret                                                                                        |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| PagerDuty                      | pagerduty\_oauth\_token                                                                                         |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Palantir                       | palantir\_jwt                                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Pangea                         | pangea\_token                                                                                                   |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Perplexity                     | perplexity\_api\_key                                                                                            |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Persona  Identities            | persona\_production\_api\_key                                                                                   | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Persona  Identities            | persona\_sandbox\_api\_key                                                                                      | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Pineapple Technologies Limited | pineapple\_technologies\_incident\_api\_key                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Pinecone                       | pinecone\_api\_key, pinecone\_environment                                                                  |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Pinterest                      | pinterest\_access\_token                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Pinterest                      | pinterest\_refresh\_token                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| PlanetScale                    | planetscale\_database\_password                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| PlanetScale                    | planetscale\_oauth\_token                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| PlanetScale                    | planetscale\_service\_token                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Planning Center                | planning\_center\_oauth\_access\_token                                                                          | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Planning Center                | planning\_center\_oauth\_app\_secret                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Planning Center                | planning\_center\_personal\_access\_token                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Plivo                          | plivo\_auth\_id, plivo\_auth\_token                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Polar                          | polar\_access\_token 
[Token versions](#token-versions)                                          | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Polar                          | polar\_authorization\_code 
[Token versions](#token-versions)                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Polar                          | polar\_client\_registration\_token 
[Token versions](#token-versions)                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Polar                          | polar\_client\_secret 
[Token versions](#token-versions)                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Polar                          | polar\_customer\_session\_token                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Polar                          | polar\_personal\_access\_token 
[Token versions](#token-versions)                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Polar                          | polar\_refresh\_token 
[Token versions](#token-versions)                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Polar                          | polar\_user\_session\_token                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| PostHog                        | posthog\_feature\_flags\_secure\_api\_key                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| PostHog                        | posthog\_oauth\_access\_token                                                                                   | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| PostHog                        | posthog\_oauth\_refresh\_token                                                                                  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| PostHog                        | posthog\_personal\_api\_key                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Postman                        | postman\_api\_key                                                                                               | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Postman                        | postman\_collection\_key                                                                                        | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Prefect                        | prefect\_server\_api\_key                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Prefect                        | prefect\_user\_api\_key                                                                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Proctorio                      | proctorio\_consumer\_key                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Proctorio                      | proctorio\_linkage\_key                                                                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Proctorio                      | proctorio\_registration\_key                                                                                    | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Proctorio                      | proctorio\_secret\_key 
[Token versions](#token-versions)                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Proof                          | proof\_full\_access\_api\_key                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Pulumi                         | pulumi\_access\_token                                                                                           | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| PyPI                           | pypi\_api\_token                                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Rainforest Pay                 | rainforest\_api\_key                                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Rainforest Pay                 | rainforest\_sandbox\_api\_key                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Ramp                           | ramp\_client\_id                                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Ramp                           | ramp\_client\_secret                                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Ramp                           | ramp\_oauth\_token                                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Raycast                        | raycast\_access\_token                                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| ReadMe                         | readmeio\_api\_access\_token                                                                                    | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| redirect.pizza                 | redirect\_pizza\_api\_token                                                                                     | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Replicate                      | replicate\_api\_token                                                                                           | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Rootly                         | rootly\_api\_key                                                                                                |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| RubyGems                       | rubygems\_api\_key                                                                                              | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| RunPod                         | runpod\_api\_key                                                                                                | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Salesforce                     | salesforce\_access\_token                                                                                       |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Salesforce                     | salesforce\_marketing\_cloud\_api\_oauth2\_token                                                                |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Salesforce                     | salesforce\_oauth2\_consumer\_key, salesforce\_oauth2\_consumer\_secret                                    |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Salesforce                     | salesforce\_refresh\_token                                                                                      |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Samsara                        | samsara\_api\_token                                                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Samsara                        | samsara\_oauth\_access\_token                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Scalr                          | scalr\_api\_token                                                                                               | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Segment                        | segment\_public\_api\_token                                                                                     | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| SendGrid                       | sendgrid\_api\_key                                                                                              | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Sentry                         | sentry\_integration\_token                                                                                      |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Sentry                         | sentry\_organization\_token                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Sentry                         | sentry\_personal\_token                                                                                         | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Sentry                         | sentry\_user\_app\_auth\_token                                                                                  |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shippo                         | shippo\_live\_api\_token                                                                                        |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shippo                         | shippo\_test\_api\_token                                                                                        |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shopee                         | shopee\_open\_platform\_partner\_key                                                                            | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shopify                        | shopify\_access\_token                                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shopify                        | shopify\_app\_client\_credentials                                                                               | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shopify                        | shopify\_app\_client\_secret                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shopify                        | shopify\_app\_shared\_secret                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shopify                        | shopify\_custom\_app\_access\_token                                                                             | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shopify                        | shopify\_marketplace\_token                                                                                     | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Shopify                        | shopify\_merchant\_token                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shopify                        | shopify\_partner\_api\_token                                                                                    | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Shopify                        | shopify\_private\_app\_password                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Siemens                        | siemens\_api\_token                                                                                             | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Siemens                        | siemens\_code\_token                                                                                            | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Sindri                         | sindri\_api\_key 
[Token versions](#token-versions)                                              | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Slack                          | slack\_api\_token 
[Token versions](#token-versions)                                             | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Slack                          | slack\_incoming\_webhook\_url                                                                                   | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Slack                          | slack\_workflow\_webhook\_url                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Snowflake                      | snowflake\_postgres\_connection\_string                                                                         | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Snowflake                      | snowflake\_postgres\_host, snowflake\_postgres\_password                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Snowflake                      | snowflake\_programmatic\_access\_token                                                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Sourcegraph                    | sourcegraph\_access\_token                                                                                      | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Sourcegraph                    | sourcegraph\_dotcom\_user\_gateway                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Sourcegraph                    | sourcegraph\_instance\_identifier\_access\_token                                                                | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Sourcegraph                    | sourcegraph\_license\_key\_token                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Sourcegraph                    | sourcegraph\_product\_subscription\_token                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Square                         | square\_access\_token 
[Token versions](#token-versions)                                         |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Square                         | square\_production\_application\_secret                                                                         |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Square                         | square\_sandbox\_application\_secret                                                                            |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| SSLMate                        | sslmate\_api\_key 
[Token versions](#token-versions)                                             | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| SSLMate                        | sslmate\_cluster\_secret                                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Stripe                         | stripe\_api\_key                                                                                                | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Stripe                         | stripe\_legacy\_api\_key                                                                                        | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |  ✗  |
| Stripe                         | stripe\_live\_restricted\_key                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Stripe                         | stripe\_test\_restricted\_key                                                                                   | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Stripe                         | stripe\_test\_secret\_key                                                                                       | ✓ | ✓ | ✓ | ✓ | ✓ |  ✗  |
| Stripe                         | stripe\_webhook\_signing\_secret                                                                                | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Supabase                       | supabase\_personal\_access\_token                                                                               | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Supabase                       | supabase\_secret\_key                                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Supabase                       | supabase\_service\_key 
[Token versions](#token-versions)                                        | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Tableau                        | tableau\_personal\_access\_token                                                                                |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Tailscale                      | tailscale\_api\_key                                                                                             | ✓ | ✓ |  ✗  | ✓ | ✓ |  ✗  |
| Telegram                       | telegram\_bot\_token                                                                                            |  ✗  | ✓ |  ✗  | ✓ | ✓ |  ✗  |
| Telnyx                         | telnyx\_api\_v2\_key                                                                                            | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Temporal                       | temporal\_cloud\_api\_key                                                                                       | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Tencent                        | tencent\_cloud\_intl\_access\_token                                                                             | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Tencent                        | tencent\_cloud\_secret\_id                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Tencent                        | tencent\_wechat\_api\_app\_id                                                                                   | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Tencent                        | tencent\_wechat\_pay\_token                                                                                     |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Thunderstore                   | thunderstore\_io\_api\_token                                                                                    |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Twilio                         | twilio\_access\_token                                                                                           |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Twilio                         | twilio\_account\_sid 
[Token versions](#token-versions)                                          | ✓ | ✓ | ✓ |  ✗  |  ✗  | ✓ |
| Twilio                         | twilio\_api\_key                                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Typeform                       | typeform\_personal\_access\_token                                                                               | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Uniwise                        | wiseflow\_api\_key                                                                                              | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Unkey                          | unkey\_root\_key                                                                                                | ✓ | ✓ |  ✗  | ✓ |  ✗  |  ✗  |
| Val Town                       | val\_town\_api\_token                                                                                           | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Vercel                         | vercel\_api\_key                                                                                                | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Vercel                         | vercel\_app\_refresh\_token                                                                                     | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Vercel                         | vercel\_app\_user\_access\_token                                                                                | ✓ | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Vercel                         | vercel\_integration\_access\_token                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Vercel                         | vercel\_personal\_access\_token                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Vercel                         | vercel\_support\_access\_token                                                                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| VolcEngine                     | volcengine\_access\_key\_id                                                                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Wakatime                       | wakatime\_api\_key                                                                                              | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Wakatime                       | wakatime\_app\_secret                                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Wakatime                       | wakatime\_oauth\_access\_token                                                                                  | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Wakatime                       | wakatime\_oauth\_refresh\_token                                                                                 | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Weatherstack                   | weatherstack\_api\_key                                                                                          |  ✗  | ✓ |  ✗  |  ✗  |  ✗  |  ✗  |
| Weights & Biases               | wandb\_api\_key                                                                                                 |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Workato                        | workato\_developer\_api\_token 
[Token versions](#token-versions)                                | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| WorkOS                         | workos\_production\_api\_key 
[Token versions](#token-versions)                                  | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| WorkOS                         | workos\_staging\_api\_key 
[Token versions](#token-versions)                                     | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| WSO2                           | wso2\_choreo\_personal\_access\_token                                                                           | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| xAI                            | xai\_api\_key                                                                                                   | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Yandex                         | yandex\_cloud\_api\_key                                                                                         | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Yandex                         | yandex\_cloud\_iam\_access\_secret                                                                              | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Yandex                         | yandex\_cloud\_iam\_cookie                                                                                      | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Yandex                         | yandex\_cloud\_iam\_token                                                                                       | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Yandex                         | yandex\_cloud\_smartcaptcha\_server\_key                                                                        | ✓ | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Yandex                         | yandex\_dictionary\_api\_key                                                                                    |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Yandex                         | yandex\_passport\_oauth\_token                                                                                  | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| Yandex                         | yandex\_predictor\_api\_key                                                                                     |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Yandex                         | yandex\_translate\_api\_key                                                                                     |  ✗  | ✓ | ✓ | ✓ |  ✗  |  ✗  |
| ZenHub                         | zenhub\_personal\_api\_key                                                                                      |  ✗  | ✓ | ✓ |  ✗  |  ✗  |  ✗  |
| Zuplo                          | zuplo\_consumer\_api\_key                                                                                       | ✓ | ✓ | ✓ | ✓ |  ✗  |  ✗  |

#### Token versions

Service providers update the patterns used to generate tokens periodically and may support more than one version of a token. Push protection only supports the most recent token versions that secret scanning can identify with confidence. This avoids push protection blocking commits unnecessarily when a result may be a false positive, which is more likely to happen with legacy tokens.

## Further reading

* [About secret scanning alerts](/en/code-security/secret-scanning/managing-alerts-from-secret-scanning/about-alerts)
* [Secret scanning partner program](/en/code-security/secret-scanning/secret-scanning-partnership-program/secret-scanning-partner-program)
* [Quickstart for securing your repository](/en/code-security/getting-started/securing-your-repository)
* [Keeping your account and data secure](/en/authentication/keeping-your-account-and-data-secure)
