# About GitHub Actions for enterprises

GitHub Actions can improve developer productivity by automating your enterprise's software development cycle.

## About GitHub Actions for enterprises

GitHub Actions allows users in your enterprise to improve productivity by automating every phase of the software development workflow.

| Task                                                                  | More information                                                                                                                        |
| --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Automatically test and build your application                         | [Continuous integration](/en/enterprise-cloud@latest/actions/automating-builds-and-tests/about-continuous-integration)                  |
| Deploy your application                                               | [Continuous deployment](/en/enterprise-cloud@latest/actions/deployment/about-deployments/about-continuous-deployment)                   |
| Automatically and securely package code into artifacts and containers | [About GitHub Packages and GitHub Actions](/en/enterprise-cloud@latest/actions/publishing-packages/about-packaging-with-github-actions) |

GitHub Actions helps your team work faster at scale. When large repositories start using GitHub Actions, pull requests are typically merged faster, allowing teams to merge more pull requests per day.

You can create your own unique automations, or you can use and adapt workflows from our ecosystem of over 10,000 actions built by industry leaders and the open source community. For more information, see [Using pre-written building blocks in your workflow](/en/enterprise-cloud@latest/actions/learn-github-actions/finding-and-customizing-actions).

GitHub Actions is developer friendly, because it's integrated directly into the familiar GitHub experience.

You can enjoy the convenience of GitHub-hosted runners, which are maintained and upgraded by GitHub, or you can control your own private CI/CD infrastructure by using self-hosted runners. Self-hosted runners allow you to determine the exact environment and resources that complete your builds, testing, and deployments, without exposing your software development cycle to the internet. For more information, see [GitHub-hosted runners](/en/enterprise-cloud@latest/actions/using-github-hosted-runners/about-github-hosted-runners) and [Self-hosted runners](/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners).

GitHub Actions provides greater control over deployments. For example, you can use environments to require approval for a job to proceed, restrict which branches can trigger a workflow, or limit access to secrets. If your workflows need to access resources from a cloud provider that supports OpenID Connect (OIDC), you can configure your workflows to authenticate directly to the cloud provider. OIDC provides security benefits such as eliminating the need to store credentials as long-lived secrets. For more information, see [OpenID Connect](/en/enterprise-cloud@latest/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect).

GitHub Actions also includes tools to govern your enterprise's software development cycle and meet compliance obligations. For more information, see [Enforcing policies for GitHub Actions in your enterprise](/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise).

## About getting started with GitHub Actions

Before you get started, you should make a plan for how you'll introduce GitHub Actions to your enterprise. For more information, see [Introducing GitHub Actions to your enterprise](/en/enterprise-cloud@latest/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/introducing-github-actions-to-your-enterprise).

If you're migrating your enterprise to GitHub Actions from another provider, there are additional considerations. For more information, see [Migrating your enterprise to GitHub Actions](/en/enterprise-cloud@latest/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/migrating-your-enterprise-to-github-actions).

After you finish planning, you can follow the instructions for getting started with GitHub Actions. For more information, see [Getting started with GitHub Actions for GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/github-actions/getting-started-with-github-actions-for-your-enterprise/getting-started-with-github-actions-for-github-enterprise-cloud).

## Further reading

* [Understanding GitHub Actions](/en/enterprise-cloud@latest/actions/learn-github-actions/understanding-github-actions)
* [GitHub Actions billing](/en/enterprise-cloud@latest/billing/managing-billing-for-github-actions/about-billing-for-github-actions)