# Rate limits for GitHub Copilot

Learn about GitHub Copilot rate limits and what to do if you are rate limited.

Rate limiting is a mechanism used to control the number of requests a user or application can make in a given time period. GitHub uses rate limits to ensure everyone has fair access to GitHub Copilot and to protect against abuse.

When you hit a rate limit, you may temporarily lose access to certain GitHub Copilot features or models, and you’ll see an error message informing you that you’ve been rate limited.

## Why does GitHub use rate limits?

GitHub enforces rate limits for several reasons.

* **Capacity:** There is a limited amount of computing power available to serve all Copilot users. Rate limiting helps prevent the system from being overloaded.
* **High usage:** Popular features and models may receive bursts of requests. Rate limits ensure no single user or group can monopolize these resources.
* **Fairness:** Rate limits ensure that all users have equitable access to Copilot.
* **Abuse mitigation:** Without rate limits, malicious actors could exploit Copilot, leading to degraded service for everyone or even denial of service.

## Types of rate limits
* **Limits for overall service reliability:** Temporary protections that GitHub applies to keep GitHub Copilot reliable and fair for everyone. You may see these represented as **global** or **weekly** rate limits.
* **Limits for specific models or model family capacity:** Plan-based limits that reflect the GitHub Copilot usage you've consumed for a particular model or model family.

## What to do if you are rate limited

If you receive a rate limit error when using Copilot, you should:

* **Wait and try again.** Rate limits are temporary. Often, waiting a short period and trying again resolves the issue.
* **Check your usage.** If you’re making frequent or automated requests (for example, rapid-fire completions or large-scale usage), consider adjusting your usage pattern.
* **Change your model.** Select models may have stricter rate limits due to limited capacity.
* **Upgrade your plan.** If you are on an individual Copilot plan, upgrading your plan will allow for additional usage. 
* **Contact Support.** If you’re repeatedly rate limited and believe it’s impacting legitimate use, contact [GitHub Support](https://support.github.com) for assistance.

>[!NOTE] Service-level rate limits should not affect typical Copilot usage. However, if you’re heavily using select models, you may encounter rate limits more frequently.