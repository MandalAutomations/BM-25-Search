# About secret scanning alerts

Learn about the different types of secret scanning alerts.

## About types of alerts

There are three types of secret scanning alerts:

* **User alerts:** Reported to users in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of the repository, when a supported secret is detected in the repository.
* **Push protection alerts:** Reported to users in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of the repository, when a contributor bypasses push protection.
* **Partner alerts:** Reported directly to secret providers that are part of secret scanning's partner program. These alerts are not reported in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of the repository.

## About user alerts

When you enable secret scanning for a repository or push commits to a repository with secret scanning enabled, GitHub scans the contents for secrets that match patterns defined by service providers.

When secret scanning detects a secret, GitHub generates an alert. GitHub displays an alert in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of the repository.

To help you triage alerts more effectively, GitHub separates alerts into two lists:

* **Default** alerts
* **Generic** alerts

### Default alerts list

The default alerts list displays alerts that relate to supported patterns and specified custom patterns. This is the main view for alerts.

### Generic alerts list

The generic alerts list displays alerts that relate to non-provider patterns (such as private keys), or generic secrets detected using AI (such as passwords). These types of alerts can have a higher rate of false positives or secrets used in tests. You can toggle to the generic alerts list from the default alerts list.

GitHub will continue to release new patterns and secret types to the generic alerts list and will promote them to the default list when feature-complete (that is, when they have an appropriately low volume and false positive rate).

In addition, alerts that fall into this category:

* Are limited in quantity to 5000 alerts per repository (this includes open and closed alerts).
* Are not shown in the summary views for security overview, only in the "Secret scanning" view.
* Only have the first five detected locations shown on GitHub for non-provider patterns, and only the first detected location shown for AI-detected generic secrets.

For GitHub to scan for non-provider patterns and generic secrets, you must first enable the features for your repository or organization. For more information, see [Enabling secret scanning for non-provider patterns](/en/code-security/how-tos/secure-your-secrets/detect-secret-leaks/enabling-secret-scanning-for-non-provider-patterns) and [Enabling Copilot secret scanning's generic secret detection](/en/code-security/secret-scanning/copilot-secret-scanning/enabling-ai-powered-generic-secret-detection).

If access to a resource requires paired credentials, then secret scanning will create an alert only when both parts of the pair are detected in the same file. This ensures that the most critical leaks are not hidden behind information about partial leaks. Pair matching also helps reduce false positives since both elements of a pair must be used together to access the provider's resource.

## About push protection alerts

Push protection scans pushes for supported secrets. If push protection detects a supported secret, it will block the push. When a contributor bypasses push protection to push a secret to the repository, a push protection alert is generated and displayed in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of the repository. To see all push protection alerts for a repository, you must filter by `bypassed: true` on the alerts page. For more information, see [Viewing and filtering alerts from secret scanning](/en/code-security/how-tos/manage-security-alerts/manage-secret-scanning-alerts/viewing-alerts#filtering-alerts).

If access to a resource requires paired credentials, then secret scanning will create an alert only when both parts of the pair are detected in the same file. This ensures that the most critical leaks are not hidden behind information about partial leaks. Pair matching also helps reduce false positives since both elements of a pair must be used together to access the provider's resource.

> \[!NOTE]
> You can also enable push protection for your personal account, called "push protection for users", which prevents you from accidentally pushing supported secrets to *any* public repository. Alerts are *not* created if you choose to bypass your user-based push protection only. Alerts are only created if the repository itself has push protection enabled. For more information, see [Managing push protection for users](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/push-protection-for-users).
>
> Older versions of certain tokens may not be supported by push protection as these tokens may generate a higher number of false positives than their most recent version. Push protection may also not apply to legacy tokens. For tokens such as Azure Storage Keys, GitHub only supports *recently created* tokens, not tokens that match the legacy patterns. For more information about push protection limitations, see [Secret scanning detection scope](/en/code-security/how-tos/secure-your-secrets/troubleshooting-secret-scanning#push-protection-and-pattern-versions).

## About partner alerts

When GitHub detects a leaked secret in a public repository or npm package, an alert is sent directly to the secret provider, if they are part of GitHub's secret scanning partner program. For more information about secret scanning alerts for partners, see [Secret scanning partner program](/en/code-security/secret-scanning/secret-scanning-partnership-program/secret-scanning-partner-program) and [Supported secret scanning patterns](/en/code-security/reference/secret-security/supported-secret-scanning-patterns).

Partner alerts are not sent to repository administrators, so you do not need to take any action for this type of alert.

## Further reading

* [Supported secret scanning patterns](/en/code-security/reference/secret-security/supported-secret-scanning-patterns)
* [Enabling secret scanning for non-provider patterns](/en/code-security/how-tos/secure-your-secrets/detect-secret-leaks/enabling-secret-scanning-for-non-provider-patterns)