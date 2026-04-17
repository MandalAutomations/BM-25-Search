# Setting up a trial of GitHub Enterprise Cloud

Learn how to set up a trial of GitHub Enterprise Cloud, what is included in the trial, and what happens when the trial ends.

GitHub Enterprise Cloud is designed for large businesses or teams who collaborate on GitHub. See [About GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/about-github-enterprise-cloud).

To set up a trial, you must be signed in to a personal account. If you don't have a personal account, see [Creating an account on GitHub](/en/get-started/start-your-journey/creating-an-account-on-github).

<a href="https://github.com/account/enterprises/new?ref_product=ghec&ref_type=trial&ref_style=button&ref_plan=enterprise" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Set up a trial of GitHub Enterprise Cloud</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

## About enterprise types

While setting up your trial of GitHub Enterprise Cloud, you'll choose an enterprise type.

* Enterprise with personal accounts
* Enterprise with managed users

To help you decide which choice is best for your enterprise, see [Choosing an enterprise type for GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/identity-and-access-management/understanding-iam-for-enterprises/choosing-an-enterprise-type-for-github-enterprise-cloud).

### Enterprises with managed users

If you choose an enterprise with managed users, you will also choose whether to create an enterprise on GitHub.com or in a specific data residency region on GHE.com.

* Trials on **GitHub.com** include free access to GitHub Advanced Security features. Your enterprise will be hosted in the US.
* Trials on **GHE.com** allow you to meet specific regulatory requirements and choose a unique subdomain for your enterprise. However, there are some features that are not included in the trial. See [Feature overview for GitHub Enterprise Cloud with data residency](/en/enterprise-cloud@latest/admin/data-residency/feature-overview-for-github-enterprise-cloud-with-data-residency#currently-unavailable-features).

## What is included in the trial?

The trial lasts for **30 days** and includes the following features.

* Access to **most** GitHub Enterprise Cloud features.
* GitHub Secret Protection and GitHub Code Security (GitHub.com trials only)
* Access to the **new billing platform**. See [Introduction to billing and licensing](/en/enterprise-cloud@latest/billing/using-the-new-billing-platform/about-the-new-billing-platform-for-enterprises).
* An **enterprise account**, which allows you to manage multiple organizations. See [Types of GitHub accounts](/en/enterprise-cloud@latest/get-started/learning-about-github/types-of-github-accounts).
* Up to **50 licenses** to grant access to users.
* Up to 3,000 minutes of standard GitHub-hosted runners.

Your trial **won't** include access to GitHub Enterprise Server. To test this, contact [GitHub's Sales team](https://github.com/enterprise/contact).

## Features not included in the trial

* GitHub Codespaces
* GitHub Copilot Enterprise
* GitHub Copilot Business
* GitHub Sponsors
* Paid GitHub Marketplace apps
* GitHub Connect
* Git Large File Storage
* For GitHub Actions, increased minutes, job concurrency, and larger runners

If you invite an existing organization into your trial enterprise, **all of these features will be disabled**. If you remove the organization from the enterprise, the features will be re-enabled.

## Do I need to provide a payment method?

You do not need to provide a payment method to start a trial.

## During the trial

After you set up your trial, you can explore GitHub Enterprise Cloud by following the suggested tasks on the "Getting started" tab of your enterprise account.

You can create up to **three new organizations** in the trial enterprise, or transfer any number of existing organizations.

* You cannot transfer organizations if you selected an enterprise with managed users.
* You cannot transfer organizations that have free or paid GitHub Marketplace apps. Free apps are supported for new organizations in the trial.
* You cannot transfer organizations that are already owned by another enterprise.
* Billing for transferred organizations is paused during the trial and any coupons are removed. To reapply a coupon, contact [GitHub Support](https://support.github.com).
* Organizations created during the trial cannot be removed from the enterprise account until you purchase GitHub Enterprise.

For help setting up the included features, once you've started your trial, see [Getting started with the GitHub Enterprise Cloud trial](/en/enterprise-cloud@latest/get-started/onboarding/getting-started-with-the-github-enterprise-cloud-trial).

## What happens when the trial ends?

You can end your trial at any time by purchasing GitHub Enterprise or canceling the trial. Otherwise, after 30 days, your trial will expire.

GitHub Enterprise trial accounts are automatically deleted 90 days after the trial period ends if the account has not been converted to a paid account.

If you **purchase GitHub Enterprise**:

* You can use usage-based billing for GitHub Enterprise Cloud and GitHub Advanced Security products, which means you pay monthly for the number of licenses you use. You will not need to buy a predefined number of licenses in advance. See [Usage-based billing for enterprise licenses](/en/enterprise-cloud@latest/billing/using-the-new-billing-platform/about-usage-based-billing-for-licenses).

  If you did not set up a free trial and you want to use usage-based billing to pay for GitHub Advanced Security products after the GitHub Enterprise Cloud trial ends, contact [GitHub's Sales team](https://enterprise.github.com/contact).

* You can generate a GitHub Enterprise Server license file for the same quantity of users who are consuming a GitHub Enterprise Cloud license.

If you **cancel your trial**:

* Organizations that you transferred into the enterprise are removed and reverted to their previous plans and settings.
* Enterprise owners and members lose access to the enterprise account and any organizations that you created during the trial.

If your **trial expires**:

* Organizations that you transferred into the enterprise are removed and reverted to their previous plans and settings.
* Enterprise owners and members retain access to the enterprise account and organizations created during the trial in a downgraded state, allowing you to either upgrade to GitHub Enterprise or move assets elsewhere.
* You can delete an expired trial to remove people's access to the enterprise and organizations created during the trial.

For more information about the effects of downgrading an organization, see [Downgrading your account's plan](/en/enterprise-cloud@latest/billing/managing-the-plan-for-your-github-account/downgrading-your-accounts-plan#downgrading-your-organizations-plan).

## Ending your trial

You can end a trial by purchasing GitHub Enterprise or by canceling the trial. If a trial has expired, you can delete the trial.

### Purchasing GitHub Enterprise

You can purchase GitHub Enterprise at any time during the trial.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. To end the trial period and purchase GitHub Enterprise, click **Activate Enterprise** in the blue banner at the top of the page.

### Canceling or deleting a trial

You can cancel a trial at any time. Once the trial has expired, you can delete the trial.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.
3. Under **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**, click **General**.
4. At the bottom of the page, in the "Danger zone" section, click **Cancel trial** or **Delete trial**.

## Further reading

* [Best practices for organizing work in your enterprise](/en/enterprise-cloud@latest/admin/overview/best-practices-for-enterprises)
* [GitHub public roadmap](https://github.com/github/roadmap#github-public-roadmap)