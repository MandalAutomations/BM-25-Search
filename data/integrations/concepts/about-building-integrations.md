# About building integrations

You can build integrations to extend GitHub's functionality.

Integrations are tools that extend GitHub's functionality. Integrations can do things on GitHub like open issues, comment on pull requests, and manage projects. They can also do things outside of GitHub based on events that happen on GitHub. For example, an integration can post on Slack when an issue is opened on GitHub.

Many integrations are GitHub Apps, GitHub Actions workflows, or custom actions for GitHub Actions workflows.

* GitHub Apps are integrations that run on the app owner's server or on a user device. For more information, see [About creating GitHub Apps](/en/apps/creating-github-apps/about-creating-github-apps/about-creating-github-apps).
* GitHub Actions workflows are workflows that run when specific events occur on GitHub. For more information, see [Understanding GitHub Actions](/en/actions/learn-github-actions/understanding-github-actions).
* Custom actions are code that can be executed by a GitHub Actions workflow. For more information, see [About custom actions](/en/actions/creating-actions/about-custom-actions).

Your integration can use GitHub's API to fetch data and make changes to data on GitHub. GitHub has a REST API and a GraphQL API. For more information, see:

* [Comparing GitHub's REST API and GraphQL API](/en/rest/about-the-rest-api/comparing-githubs-rest-api-and-graphql-api)
* [GitHub REST API documentation](/en/rest)
* [GitHub GraphQL API documentation](/en/graphql)

Your integration can use webhooks to learn when specific events happen on GitHub. For more information, see [About webhooks](/en/webhooks/about-webhooks).

If your integration is a GitHub App or custom action, you can publish your integration on GitHub Marketplace. For more information, see [About GitHub Marketplace for apps](/en/apps/github-marketplace/github-marketplace-overview/about-github-marketplace-for-apps) and [Publishing actions in GitHub Marketplace](/en/actions/creating-actions/publishing-actions-in-github-marketplace).

If your integration uses generative AI, you can find and experiment with AI models for free on GitHub. See [Prototyping with AI models](/en/github-models/prototyping-with-ai-models).