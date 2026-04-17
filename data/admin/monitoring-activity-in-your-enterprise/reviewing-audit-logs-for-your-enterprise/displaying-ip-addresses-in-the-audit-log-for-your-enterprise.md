# Displaying IP addresses in the audit log for your enterprise

You can display the source IP address for events in your enterprise's audit log.

## About display of IP addresses in the audit log

By default, GitHub does not display the source IP address for events in your enterprise's audit log. Optionally, to ensure compliance and respond to threats, you can display the full IP address associated with the actor responsible for each event. Actors are typically users, but can also be apps or integrations.

You are responsible for meeting any legal obligations that accompany the viewing or storage of IP addresses displayed within your enterprise's audit log.

If you choose to display IP addresses for your enterprise account, IP addresses for **new and existing events** will appear in both your enterprise's audit log and the audit log of every organization owned by your enterprise. Alternatively, you can enable the display of IP addresses in the audit log for individual organizations. For more information, see [Displaying IP addresses in the audit log for your organization](/en/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/displaying-ip-addresses-in-the-audit-log-for-your-organization).

You can display IP addresses in the audit log regardless of which authentication method you use for your enterprise on GitHub. For more information, see [Identity and access management fundamentals](/en/enterprise-cloud@latest/admin/identity-and-access-management/managing-iam-for-your-enterprise/about-authentication-for-your-enterprise).

When anyone creates an account on GitHub, the person agrees to GitHub's collection of basic information about connections to GitHub's services, including source IP address. For more information, see [GitHub General Privacy Statement](/en/site-policy/privacy-policies/github-privacy-statement#usage-information).

## Events that display IP addresses in the audit log

GitHub displays an IP address in the audit log when a member of the enterprise interacts with a resource owned by your enterprise or an organization in your enterprise. For example, you will see an IP address for audited events involving an internal or private repository owned by an organization in your enterprise, or resources associated with those repositories, such as an issue, pull request, action, or project.

If members of your enterprise access GitHub.com with personal accounts that they manage, because you do not use Enterprise Managed Users, GitHub does not display an event or IP address in the audit log for the following actions.

* Authentication to GitHub.com
* Interactions with a resource owned by the personal account, including a repository, gist, or project
* Interactions with a public repository owned by an organization in your enterprise

GitHub does not display IP addresses in the audit log for `api.request` events that do not have repository context, such as requests triggered by GraphQL or requests to endpoints that reference only a user or organization.

GitHub does not display IP addresses in the audit log for certain events where the actor recorded in the audit log differs from the person or system that performed the action. GitHub also does not display IP addresses when a bot or automated system performs the action.

## Enabling display of IP addresses in the audit log

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. Under "Settings", click **Audit log**.
4. On the **Settings** tab, under "Disclose actor IP addresses in audit logs", select **Enable source IP disclosure**.
5. Click **Save**.

After you enable the feature, you can access the audit log to view events that include IP addresses. For more information, see [Accessing the audit log for your enterprise](/en/enterprise-cloud@latest/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/accessing-the-audit-log-for-your-enterprise).