# Webhook events for the GitHub Marketplace API

A GitHub Marketplace app receives information about changes to a user's plan from the Marketplace purchase event webhook. A Marketplace purchase event is triggered when a user purchases, cancels, or changes their payment plan.

> \[!NOTE]
> This article applies to publishing apps in GitHub Marketplace only. For more information about publishing GitHub Actions in GitHub Marketplace, see [Publishing actions in GitHub Marketplace](/en/actions/creating-actions/publishing-actions-in-github-marketplace).

For more information about the GitHub Marketplace webhook payload, see [Webhook events and payloads](/en/webhooks/webhook-events-and-payloads#marketplace_purchase).

Webhooks `POST` requests have special headers. See [Webhook events and payloads](/en/webhooks/webhook-events-and-payloads#delivery-headers) for more details. GitHub doesn't resend failed delivery attempts. Ensure your app can receive all webhook payloads sent by GitHub. For information about how to create and disable GitHub Marketplace webhooks, see [Creating webhooks](/en/webhooks/using-webhooks/creating-webhooks) and [Disabling webhooks](/en/webhooks/using-webhooks/disabling-webhooks).

Cancellations and downgrades take effect on the first day of the next billing cycle. Events for downgrades and cancellations are sent when the new plan takes effect at the beginning of the next billing cycle. Events for new purchases and upgrades begin immediately. Use the `effective_date` in the webhook payload to determine when a change will begin.

> \[!NOTE]
> If you notice any spammy GitHub Marketplace purchases or other malicious behavior, please complete the [report abuse](https://github.com/contact/report-abuse) form with more information on the user.