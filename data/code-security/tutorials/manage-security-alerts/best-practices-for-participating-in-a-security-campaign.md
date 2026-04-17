# Participating in a code security campaign

If you've been assigned alerts as part of a security campaign, this guide explains what campaigns are, what to expect, and how to resolve alerts effectively.

## What is a code security campaign?

A code security campaign is a focused effort to remediate a defined group of code scanning alerts across one or more repositories.

Campaigns are created by organization owners or security managers and typically target alerts detected in the default branches of repositories. If you’re participating in a campaign, you’ve been asked to help resolve some of these alerts.

## What are the benefits of participating in a campaign?

In addition to reducing risk in your organization’s codebase, alerts in a security campaign have several other benefits compared with fixing another alert in your repository.

* You have a campaign manager on the security team to collaborate with and a specific contact link for discussing campaign activities.
* You know that you are fixing a security alert that is important to the company.
* Potentially, you may have access to targeted training materials.
* You don't need to request a GitHub Copilot Autofix suggestion, it is already available as a starting point.
* If you have access to GitHub Copilot Chat, you can ask questions about the alert and the suggested fix.
* You are improving and demonstrating your knowledge of secure coding.

Participating in a campaign helps reduce risk in your organization’s codebase while strengthening your secure coding skills.

## 1. Learn about campaigns

Start by reviewing campaign updates and deadlines so you can plan your work effectively.

### Notification settings

You'll automatically receive email updates about security campaigns for any repositories you have **write** access to, so you can stay informed about relevant updates.

In addition, you will receive a notification if someone assigns a code scanning or a secret scanning alert to you, see [Assigning alerts](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/about-security-campaigns#assigning-alerts).

### View campaign details

When you open the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for a repository with one or more campaign alerts, you can see the campaign name in the sidebar of the view. Click the campaign name to see the list of alerts included in the campaign and summary information on how the campaign is progressing.

### Campaign-generated GitHub Issues

Some campaigns automatically create GitHub Issues for each repository that detail the campaign managers, contact URL, and due date.

Use this issue to coordinate work, track progress, and keep stakeholders aligned. For example, you might use the issue to:

* Add the issue to project boards
* Add assignees
* Create sub-issues or tasklists

## 2. Build context before applying fixes

Your security team may provide you with specific training ahead of participating in a campaign, so that you feel equipped to address the alerts included in the campaign.

If no formal training program is available, you can request that the campaign manager shares information on:

* Types of security vulnerabilities included in the campaign
* Examples of how to fix them
* How to test the fixes

In addition, there are external resources for understanding common security issues:

* The **OWASP Foundation** provides many resources for learning about the most common vulnerabilities, see [About the OWASP Foundation](https://owasp.org/about/).
* The **MITRE Corporation** maintains a detailed list of common weaknesses, see [About CWE](https://cwe.mitre.org/about/index.html).

## 3. Collaborate early and often

A security campaign will generally include a contact URL, which might link you to the campaign manager, an open forum (such as a GitHub Discussion), or a website of resources. You should use this space to ask questions about the campaign or specific alerts, find useful resources, and share knowledge.

To find the contact URL:

1. Open the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for your repository.
2. On the left sidebar, click the name of the campaign you are participating in.
3. On the campaign tracking page, to the right of the campaign manager's name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-comment" aria-label="comment" role="img"><path d="M1 2.75C1 1.784 1.784 1 2.75 1h10.5c.966 0 1.75.784 1.75 1.75v7.5A1.75 1.75 0 0 1 13.25 12H9.06l-2.573 2.573A1.458 1.458 0 0 1 4 13.543V12H2.75A1.75 1.75 0 0 1 1 10.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h4.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg>**.

## 4. Group alerts strategically

Tackle similar alerts together to build momentum, reduce context switching, and develop a deeper understanding of the underlying issue. As you gain confidence and efficiency in resolving a specific type of alert, it makes it easier and faster for you to resolve subsequent alerts.

## 5. Resolve alerts with the help of Copilot

You can leverage Copilot to help resolve alerts in a security campaign. Depending on the features enabled in your repository, you may have access to Copilot Autofix suggestions and Copilot Chat.

### Copilot Autofix

Copilot Autofix is automatically triggered for alerts that are included in a campaign, meaning that where possible, fixes are automatically generated for you. You can commit the suggested fix to resolve the alert and then verify that continuous integration testing (CI) for the codebase is still passing. See [Fixing alerts in a security campaign](/en/code-security/code-scanning/managing-code-scanning-alerts/fixing-alerts-in-security-campaign).

If Copilot cloud agent is enabled in the repository, you can also assign alerts to Copilot. See [Fixing alerts in a security campaign](/en/code-security/code-scanning/managing-code-scanning-alerts/fixing-alerts-in-security-campaign#assigning-alerts-to-copilot-cloud-agent).

By assigning multiple alerts, Copilot cloud agent will apply the fixes and iterate on the code to validate the changes, check for any new security issues, and ensure there are no merge conflicts.

### Copilot Chat

You can ask Copilot Chat for help in understanding the vulnerability, the suggested fix, and how to test that the fix is comprehensive. To access Copilot Chat, navigate to [https://github.com/copilot](https://github.com/copilot?ref_product=copilot\&ref_type=engagement\&ref_style=text).

Alternatively, when viewing a specific alert, in the top right corner of the page, click the Copilot Chat icon (<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>) to open a chat window, and ask Copilot questions about the alert.

For example:

```text copy

Explain how this alert introduces a vulnerability into the code.

```

If you don't already have access to Copilot Chat through your organization, you can sign up to GitHub Copilot Free. See [Getting started with a GitHub Copilot plan](/en/copilot/managing-copilot/managing-copilot-as-an-individual-subscriber/managing-copilot-free/accessing-github-copilot-free).

## Next steps

* [Fixing alerts in a security campaign](/en/code-security/code-scanning/managing-code-scanning-alerts/fixing-alerts-in-security-campaign)