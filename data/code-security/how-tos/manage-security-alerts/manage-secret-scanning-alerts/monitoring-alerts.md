# Monitoring alerts from secret scanning

You can configure how  secret scanning notifies you about secret scanning alerts, and audit how your team responds to these alerts.

When secret scanning detects a potential secret leak in your repository, staying informed about these alerts is crucial for maintaining your code's security. GitHub provides multiple notification channels to ensure you and your team are promptly alerted when secrets are found. You can customize how and when you receive these notifications based on your role and preferences.

You can also audit responses to secret scanning alerts to track how your team manages security issues and maintain compliance with your organization's security policies.

## Configuring notifications for secret scanning alerts

In addition to displaying an alert in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of the repository, GitHub can also send email notifications for alerts. These notifications are different for incremental scans and historical scans.

### Incremental scans

When a new secret is detected, GitHub notifies all users with access to security alerts for the repository according to their notification preferences. These users include:

* Repository administrators
* Security managers
* Users with custom roles with read/write access
* Organization owners and enterprise owners, if they are administrators of repositories where secrets were leaked

> \[!NOTE]
> Commit authors who've accidentally committed secrets will be notified, regardless of their notification preferences.

You will receive an email notification if:

* You are watching the repository.
* You have enabled notifications for "All Activity", or for custom "Security alerts" on the repository.
* In your notification settings, under "Subscriptions", then under "Watching", you have selected to receive notifications by email.

In addition, you will receive a notification if someone assigns a code scanning or a secret scanning alert to you, see [Assigning alerts](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/about-security-campaigns#assigning-alerts).

1. On GitHub, navigate to the main page of the repository.

2. To start watching the repository, select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-eye" aria-label="eye" role="img"><path d="M8 2c1.981 0 3.671.992 4.933 2.078 1.27 1.091 2.187 2.345 2.637 3.023a1.62 1.62 0 0 1 0 1.798c-.45.678-1.367 1.932-2.637 3.023C11.67 13.008 9.981 14 8 14c-1.981 0-3.671-.992-4.933-2.078C1.797 10.83.88 9.576.43 8.898a1.62 1.62 0 0 1 0-1.798c.45-.677 1.367-1.931 2.637-3.022C4.33 2.992 6.019 2 8 2ZM1.679 7.932a.12.12 0 0 0 0 .136c.411.622 1.241 1.75 2.366 2.717C5.176 11.758 6.527 12.5 8 12.5c1.473 0 2.825-.742 3.955-1.715 1.124-.967 1.954-2.096 2.366-2.717a.12.12 0 0 0 0-.136c-.412-.621-1.242-1.75-2.366-2.717C10.824 4.242 9.473 3.5 8 3.5c-1.473 0-2.825.742-3.955 1.715-1.124.967-1.954 2.096-2.366 2.717ZM8 10a2 2 0 1 1-.001-3.999A2 2 0 0 1 8 10Z"></path></svg> Watch**.

   ![Screenshot of the repository's main page. A dropdown menu, titled "Watch", is highlighted with an orange outline.](/assets/images/help/repository/repository-watch-dropdown.png)

3. In the dropdown menu, click **All Activity**. Alternatively, to only subscribe to security alerts, click **Custom**, then click **Security alerts**.

4. Navigate to the notification settings for your personal account. These are available at [https://github.com/settings/notifications](https://github.com/settings/notifications?ref_product=secret-scanning\&ref_type=engagement\&ref_style=text).

5. On your notification settings page, under "Subscriptions", then under "Watching", select the **Notify me** dropdown.

6. Select "Email" as a notification option, then click **Save**.

   ![Screenshot of the notification settings for a user account. Under "Subscriptions" and "Watching" a checkbox, titled "Email", is outlined in orange.](/assets/images/help/notifications/repository-watching-notification-options.png)

For more information about setting up notification preferences, see [Managing security and analysis settings for your repository](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository#granting-access-to-security-alerts) and [Configuring your watch settings for an individual repository](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications#configuring-your-watch-settings-for-an-individual-repository).

### Historical scans

For historical scans, GitHub notifies the following users:

* Organization owners, enterprise owners, and security managers—whenever a historical scan is complete, even if no secrets are found.
* Repository administrators, security managers, and users with custom roles with read/write access—whenever a historical scan detects a secret, and according to their notification preferences.

We do *not* notify commit authors.

For more information about setting up notification preferences, see [Managing security and analysis settings for your repository](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository#granting-access-to-security-alerts) and [Configuring your watch settings for an individual repository](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications#configuring-your-watch-settings-for-an-individual-repository).

## Auditing responses to secret scanning alerts

You can audit the actions taken in response to secret scanning alerts using GitHub tools. For more information, see [Auditing security alerts](/en/code-security/getting-started/auditing-security-alerts).