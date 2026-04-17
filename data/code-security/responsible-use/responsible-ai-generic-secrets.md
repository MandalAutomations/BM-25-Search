# Responsible detection of generic secrets with Copilot secret scanning

Learn how Copilot secret scanning uses AI responsibly to scan and create alerts for unstructured secrets, such as passwords.

<!--Note on the versioning above ^. This article is visible to free, pro, team users for transparency. They cannot use the feature so `fpt` is not included in the feature definition.-->

## About generic secret detection with Copilot secret scanning

Copilot secret scanning's generic secret detection is an AI-powered expansion of secret scanning that identifies unstructured secrets (passwords) in your source code and then generates an alert.

> \[!NOTE]
> You do not need a subscription to GitHub Copilot to use Copilot secret scanning's generic secret detection. Copilot secret scanning features are available to repositories owned by organizations and enterprises that have a license for GitHub Secret Protection.

GitHub Secret Protection users can already receive secret scanning alerts for partner or custom patterns found in their source code, but unstructured secrets are not easily discoverable. Copilot secret scanning uses large language models (LLMs) to identify this type of secret.

When a password is detected, an alert is displayed in the "Generic" list of secret scanning alerts (under the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of the repository, organization, or enterprise), so that maintainers and security managers can review the alert and, where necessary, remove the credential or implement a fix.

For users with GitHub Enterprise Cloud, an enterprise owner must first set a policy at the enterprise level that controls whether generic secret detection can be enabled and disabled for repositories in an organization. This policy is set to "allowed" by default. The feature must then be enabled for repositories and organizations.

### Input processing

Input is limited to text (typically code) that a user has checked into a repository. The system provides this text to the LLM along with a meta prompt asking the LLM to find passwords within the scope of the input. The user does not interact with the LLM directly.

The system scans for passwords using the LLM. No additional data is collected by the system, other than what is already collected by the existing secret scanning feature.

### Output and display

The LLM scans for strings that resemble passwords and verifies that the identified strings included in the response actually exist in the input.

These detected strings are surfaced as alerts on the secret scanning alerts page, but they are displayed in an additional list that is separate from regular secret scanning alerts. The intent is that this separate list is triaged with more scrutiny to verify the validity of the findings. Each alert notes that it was detected using AI. For information on how to view alerts for generic secrets, see [Viewing and filtering alerts from secret scanning](/en/code-security/secret-scanning/managing-alerts-from-secret-scanning/viewing-alerts).

## Improving the performance of generic secret detection

To improve the performance of generic secret detection, we recommend closing false positive alerts appropriately.

### Verify the accuracy of alerts and close as appropriate

Since Copilot secret scanning's generic secret detection may generate more false positives than the existing secret scanning feature for partner patterns, it's important that you review the accuracy of these alerts. When you verify an alert to be a false positive, be sure to close the alert and mark the reason as "False positive" in the GitHub UI. The GitHub development team will use information on false positive volume and detection locations to improve the model. GitHub does not have access to the secret literals themselves.

## Limitations of generic secret detection

When using Copilot secret scanning's generic secret detection, you should consider the following limitations.

### Limited scope

Generic secret detection currently only looks for instances of passwords in git content. The feature does not look for other types of generic secrets, and it does not look for secrets in non-git content, such as GitHub Issues.

### Potential for false positive alerts

Generic secret detection may generate more false positive alerts when compared to the existing secret scanning feature (which detects partner patterns, and which has a very low false positive rate). To mitigate this excess noise, alerts are grouped in a separate list from partner pattern alerts, and security managers and maintainers should triage each alert to verify its accuracy.

### Potential for incomplete reporting

Generic secret detection may miss instances of credentials checked into a repository. The LLM will improve over time. You retain ultimate responsibility for ensuring the security of your code.

### Limitations by design

Generic secret detection has the following limitations by design:

* Copilot secret scanning will not detect secrets that are obviously fake or test passwords, or passwords with low entropy.
* Copilot secret scanning will only detect a maximum of 100 passwords per push.
* If five or more detected secrets within a single file are marked as false positive, Copilot secret scanning will stop generating new alerts for that file.
* Copilot secret scanning does not detect secrets in generated or vendored files.
* Copilot secret scanning does not detect secrets in encrypted files.
* Copilot secret scanning does not detect secrets in file types: SVG, PNG, JPEG, CSV, TXT, SQL, or ITEM.
* Copilot secret scanning does not detect secrets in test code. Copilot secret scanning skips detections when both conditions are met:
  * The file path contains "test", "mock", or "spec", AND
  * The file extension is `.cs`, `.go`, `.java`, `.js`, `.kt`, `.php`, `.py`, `.rb`, `.scala`, `.swift`, or `.ts`.

## Evaluation of generic secret detection

Generic secret detection has been subject to Responsible AI Red Teaming and GitHub will continue to monitor the efficacy and safety of the feature over time.

## Next steps

* [Enabling Copilot secret scanning's generic secret detection](/en/code-security/secret-scanning/copilot-secret-scanning/enabling-ai-powered-generic-secret-detection)
* [Manage secret scanning alerts](/en/code-security/secret-scanning/managing-alerts-from-secret-scanning)

## Further reading

* [About secret scanning](/en/code-security/secret-scanning/introduction/about-secret-scanning)