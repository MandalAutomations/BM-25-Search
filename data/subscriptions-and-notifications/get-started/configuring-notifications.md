# Configuring notifications

Choose the type of activity on GitHub that you want to receive notifications for and how you want these updates delivered.

## Notification delivery options

You can receive notifications for activity on GitHub in the following locations.

* The notifications inbox in the GitHub web interface
* The notifications inbox on GitHub Mobile, which syncs with the inbox in the web interface
* An email client that uses a verified email address, which can also sync with the notifications inbox in the web interface and GitHub Mobile

To use the notifications inbox on GitHub and GitHub Mobile, you must enable notifications for both **Email** and **On GitHub** in your notification settings. For more information, see [Choosing your notification settings](#choosing-your-notification-settings).

> \[!TIP]
> If you receive notifications both via email and on GitHub, you can automatically sync the read or unread status of the notification so that notifications on GitHub are automatically marked as read once you've read the corresponding email notification. To enable this sync, your email client must be able to view images from `notifications@github.com`.

### Benefits of the notifications inbox

The notifications inbox includes triaging options designed specifically for your GitHub notifications flow, including options to:

* Triage multiple notifications at once.
* Mark completed notifications as **Done** and remove them from your inbox. To view all of your notifications marked as **Done**, use the `is:done` query.
* Save a notification to review later. Saved notifications are flagged in your inbox and kept indefinitely. To view all of your saved notifications, use the `is:saved` query.
* Unsubscribe and remove a notification from your inbox.
* Preview the issue or pull request where the notification originates on GitHub from within the notifications inbox.
* See one of the latest reasons you're receiving a notification from your inbox with a `reasons` label.
* Create custom filters to focus on different notifications when you want.
* Group notifications in your inbox by repository or date to get a quick overview with less context switching.

In addition, you can receive and triage notifications on your mobile device with GitHub Mobile. For more information, see [Managing your notification settings with GitHub Mobile](#managing-your-notification-settings-with-github-mobile) or [GitHub Mobile](/en/get-started/using-github/github-mobile).

### Benefits of using an email client for notifications

One benefit of using an email client is that all of your notifications can be kept indefinitely depending on your email client's storage capacity. Your inbox notifications are only kept for 5 months on GitHub unless you've marked them as **Saved**. **Saved** notifications are kept indefinitely. For more information about your inbox's retention policy, see [About notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/about-notifications#notification-retention-policy).

Sending notifications to your email client also allows you to customize your inbox according to your email client's settings, which can include custom or color-coded labels.

Email notifications also allow flexibility with the types of notifications you receive and allow you to choose different email addresses for updates. For example, you can send certain notifications for a repository to a verified personal email address. For more information, about your email customization options, see [Customizing your email notifications](#customizing-your-email-notifications).

## About participating and watching notifications

When you watch a repository, you're subscribing to updates for activity in that repository.

To see repositories that you're watching, go to your [watching page](https://github.com/watching). For more information, see [Managing subscriptions for activity on GitHub](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/managing-subscriptions-for-activity-on-github).

You can configure notifications for a repository on the repository page, or on your watching page.

> \[!NOTE]
> You can watch a maximum of 10,000 repositories.

### About custom notifications

You can customize notifications for a repository. For example, you can choose to only be notified when updates to one or more types of events (issues, pull requests, releases, security alerts, or discussions) happen within a repository, or ignore all notifications for a repository. For more information, see [Configuring your watch settings for an individual repository](#configuring-your-watch-settings-for-an-individual-repository) below.

### Participating in conversations

Anytime you comment in a conversation or when someone @mentions your username, you are participating in a conversation. By default, you are automatically subscribed to a conversation when you participate in it. You can unsubscribe from a conversation you've participated in manually by clicking **Unsubscribe** on the issue or pull request or through the **Unsubscribe** option in the notifications inbox.

For conversations you're watching or participating in, you can choose whether you want to receive notifications on GitHub or by email in your notification settings. For more information, see [Choosing your notification settings](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications#choosing-your-notification-settings).

For example, on your "Notification settings" page:

* If you don't want notifications to be sent to your email, deselect **email** for participating and watching notifications.
* If you want to receive notifications by email when you've participated in a conversation, then select **email** under "Participating".

If you do not enable "Notify me: On GitHub" for watching or participating notifications, then your notifications inbox will not have any updates.

## Customizing your email notifications

After enabling email notifications, GitHub will send notifications to you as multipart emails that contain both HTML and plain text copies of the content. Email notification content includes any Markdown, @mentions, emojis, hash-links, and more, that appear in the original content on GitHub. If you only want to see the text in the email, you can configure your email client to display the plain text copy only.

> \[!TIP]
> If you receive notifications both via email and on GitHub, you can automatically sync the read or unread status of the notification so that notifications on GitHub are automatically marked as read once you've read the corresponding email notification. To enable this sync, your email client must be able to view images from `notifications@github.com`.

If you're using Gmail, you can click a button beside the notification email to visit the original issue or pull request that generated the notification.

Choose a default email address where you want to send updates for conversations you're participating in or watching. You can also specify which activity on GitHub you want to receive updates for using your default email address. For example, choose whether you want updates sent to your default email from:

* Comments on issues and pull requests
* Pull request reviews
* Pull request pushes
* Your own updates, such as when you open, comment on, or close an issue or pull request

Depending on the organization that owns the repository, you can also send notifications to different email addresses. Your organization may require the email address to be verified for a specific domain. For more information, see [Configuring notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications#choosing-where-your-organizations-email-notifications-are-sent).

You can also send notifications for a specific repository to an email address. For more information, see [About email notifications for pushes to your repository](/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/about-email-notifications-for-pushes-to-your-repository).

You'll only receive notification emails if you've chosen to receive email notifications in your notification settings.

If an organization you're a member of restricts email notifications to an approved email domain, you'll need to verify an email address in that domain to receive email notifications about activity in the organization. For more information, see [Restricting email notifications for your organization](/en/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/restricting-email-notifications-for-your-organization).

Each email notification that GitHub sends contains header information that you can use to filter notifications in your email client. For information about the headers included, see [Email notification headers](/en/subscriptions-and-notifications/reference/email-notification-headers).

## Replying to email notifications

You can reply to email notifications from GitHub and your reply will be posted to the issue, pull request, or discussion.

The `reply-to` address on each email notification identifies the thread and the account that the comment will be posted from. This email address remains valid until you reset your password.

GitHub will not always include the full email contents and will attempt to strip some personally identifiable information from comments created via an email reply:

* Email addresses in a standard format, such as `octocat@github.com`, are transformed to `***@***.***`.
* Signatures and quoted reply chains, when the email client has used a `>` to mark those sections, are stripped.
* While the unsubscribe link from your email notification is sometimes quoted, the link will only work when signed in to your account.
* Email attachments are not included in the resulting comment.
* The maximum length of a comment created via an email reply is 65530 characters.

## Choosing your notification settings

1. In the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-inbox" aria-label="You have " role="img"><path d="M2.8 2.06A1.75 1.75 0 0 1 4.41 1h7.18c.7 0 1.333.417 1.61 1.06l2.74 6.395c.04.093.06.194.06.295v4.5A1.75 1.75 0 0 1 14.25 15H1.75A1.75 1.75 0 0 1 0 13.25v-4.5c0-.101.02-.202.06-.295Zm1.61.44a.25.25 0 0 0-.23.152L1.887 8H4.75a.75.75 0 0 1 .6.3L6.625 10h2.75l1.275-1.7a.75.75 0 0 1 .6-.3h2.863L11.82 2.652a.25.25 0 0 0-.23-.152Zm10.09 7h-2.875l-1.275 1.7a.75.75 0 0 1-.6.3h-3.5a.75.75 0 0 1-.6-.3L4.375 9.5H1.5v3.75c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25Z"></path></svg>.

   ![Screenshot of the right corner of the header of GitHub. An inbox icon has a blue dot, indicating that there are unread notifications.](/assets/images/help/notifications/notifications-general-existence-indicator.png)
2. In the left sidebar, under the list of repositories, use the "Manage notifications" drop-down to click **Notification settings**.

   ![Screenshot of the "Notifications" page. A dropdown menu, titled "Manage notifications", is highlighted with an orange outline.](/assets/images/help/notifications-v2/manage-notifications-options.png)
3. On the notifications settings page, choose how you receive notifications when:
   * There are updates in repositories you're watching or in a conversation you're participating in. For more information, see [About participating and watching notifications](#about-participating-and-watching-notifications).
   * There are new Dependabot alerts in your repository. For more information, see [Managing security notifications](/en/subscriptions-and-notifications/how-tos/managing-security-notifications).
   * There are workflow runs updates on repositories set up with GitHub Actions. For more information, see [Managing GitHub Actions notifications](/en/subscriptions-and-notifications/how-tos/managing-github-actions-notifications).
   * There are new deploy keys added to repositories that belong to organizations that you're an owner of. For more information, see [Managing organization notifications](/en/subscriptions-and-notifications/how-tos/managing-organization-notifications).

## Configuring your watch settings for an individual repository

You can choose whether to watch or unwatch an individual repository. You can also choose to only be notified of certain event types such as issues, pull requests, releases, security alerts, or discussions (if enabled for the repository), or completely ignore an individual repository.

1. On GitHub, navigate to the main page of the repository.
2. In the upper-right corner, select the "Watch" drop-down menu, then click a watch option.

   If you want to further customize notifications, click **Custom**, then select specific events that you want to be notified of, such as Issues or Pull Requests, in addition to participating and @mentions.

   For example, if you select "Issues", you will be notified about, and subscribed to, updates on every issue (including those that existed prior to you selecting this option) in the repository. If you're @mentioned in a pull request in this repository, you'll receive notifications for that too, and you'll be subscribed to updates on that specific pull request, in addition to being notified about issues.

## Managing your notification settings with GitHub Mobile

When you install GitHub Mobile, you will automatically be opted into web notifications. Within the app, you can enable push notifications for the following events.

* Direct mentions
* Assignments to issues or pull requests
* Requests to review a pull request
* Requests to approve a deployment

You can also schedule when GitHub Mobile will send push notifications to your mobile device.

GitHub Enterprise Server uses background fetch to support push notifications, so you may experience a delay in receiving push notifications.

### Managing your notification settings with GitHub for iOS

1. In the bottom menu, tap **Profile**.
2. To view your settings, tap <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="The Gear icon" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg>.
3. To update your notification settings, tap **Notifications** and then use the toggles to enable or disable your preferred types of push notifications.
4. Optionally, to schedule when GitHub Mobile will send push notifications to your mobile device, tap **Working Hours**, use the **Custom working hours** toggle, and then choose when you would like to receive push notifications.

### Managing your notification settings with GitHub for Android

1. In the bottom menu, tap **Profile**.
2. To view your settings, tap <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="The Gear icon" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg>.
3. To update your notification settings, tap **Configure Notifications** and then use the toggles to enable or disable your preferred types of push notifications.
4. Optionally, to schedule when GitHub Mobile will send push notifications to your mobile device, tap **Working Hours**, use the **Custom working hours** toggle, and then choose when you would like to receive push notifications.

## Configuring your watch settings for an individual repository with GitHub Mobile

You can choose whether to watch or unwatch an individual repository. You can also choose to only be notified of certain event types such as issues, pull requests, discussions (if enabled for the repository) and new releases, or completely ignore an individual repository.

1. On GitHub Mobile, navigate to the main page of the repository.
2. Tap **Watch**.
3. To choose what activities you receive notifications for, tap your preferred watch settings. For example, choose to only be notified when you are participating or @mentioned, or use the "Custom" option to select specific events that you want to be notified of.