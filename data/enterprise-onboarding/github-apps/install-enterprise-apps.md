# Installing enterprise apps

Install GitHub Apps to build automations for the enterprise account.

> \[!NOTE]
> Enterprise-installed GitHub Apps are in public preview and subject to change.

## About installing GitHub Apps on your enterprise

Enterprise-installed GitHub Apps are apps that request enterprise-level permissions and can perform operations on your enterprise account. Unlike organization or user installations, they do not have access to any organization or repository permissions—they only manage the enterprise itself.

When an enterprise owner installs a GitHub App on your enterprise, the app will be granted the enterprise permissions it requested. These permissions allow the app to perform operations such as creating organizations in the enterprise, installing applications across organizations, and managing SCIM provisioning.

## Requirements to install a GitHub App on your enterprise

The GitHub App must request enterprise-level permissions. It can request other permissions as well, but only the enterprise permissions will be granted during installation.

The app must be owned by your enterprise or an organization within your enterprise. You cannot install apps owned by an account outside your enterprise.

## Installing a GitHub App on your enterprise

To install an app on your enterprise, navigate to the GitHub App installation page. This may be provided by the app developer as an installation link, or you can find it in the app's registration. The URL will look something like `https://github.com/apps/APP-NAME/installations/new`, where `APP-NAME` is the name of the GitHub App.

If the app can be installed, the list of available installation locations will include your enterprise. You can select your enterprise to install the app.

After installation, the app will be able to create an installation token for your enterprise or sign in enterprise members in order to act on their behalf at the enterprise level. Acting on a user's behalf requires the user to be able to perform the desired operations within the enterprise. For example, if the app needs to invite a user to an enterprise, the user must have permission to invite members to the enterprise as well.

## What enterprise-installed apps can do

Enterprise-installed GitHub Apps cannot call every enterprise API, but several APIs have already been updated to support GitHub Apps. These APIs and GraphQL mutations include:

* [List and create organizations in your enterprise](/en/enterprise-cloud@latest/graphql/reference/mutations#createenterpriseorganization)
* [Manage users in your enterprise](/en/enterprise-cloud@latest/graphql/reference/objects#enterprise)
* Create and manage GitHub App installations in your organizations
* Manage enterprise custom repository properties
* Call the enterprise SCIM APIs

Check the [changelog](https://github.blog/changelog/) for updates on new APIs and permissions for GitHub Apps.

For more information about available permissions and API endpoints, see [Permissions required for GitHub Apps](/en/enterprise-cloud@latest/rest/authentication/permissions-required-for-github-apps).

## Rate limits for enterprise-installed GitHub Apps

The installation token for an enterprise-installed GitHub Apps has the same rate limit as a GitHub Enterprise Cloud organization. Rate limits are per installation. For example, if an app is installed on an enterprise and two organizations, it will require 3 installation tokens to access them and have a full, independent rate limit budget for each installation. For more information, see [Rate limits for the REST API](/en/enterprise-cloud@latest/rest/overview/rate-limits-for-the-rest-api) and [Rate limits and query limits for the GraphQL API](/en/enterprise-cloud@latest/graphql/overview/resource-limitations).

## Current limitations

Enterprise-installed GitHub Apps are currently in public preview with the following limitations.

### API support

Not all APIs support enterprise-installed GitHub Apps yet. As more permissions are built and APIs updated, support will become broader. For more information about the APIs and permissions that support enterprise-installed GitHub Apps, see [Permissions required for GitHub Apps](/en/enterprise-cloud@latest/rest/authentication/permissions-required-for-github-apps).

### Webhook support

Enterprise installations do not currently support webhooks. Apps installed at the enterprise level cannot receive webhook events for enterprise-level activities. Install them on organizations or repositories to receive webhook events for those resources.

### Organization access

Enterprise installations are not granted access to organizations or repositories within your enterprise, with the exception of the organization installations API. To access organization or repository resources, you must install the app separately on each organization where access is needed.

## Next steps

Now that you're automating processes with GitHub Apps, learn about GitHub Support so you can get help when you need it. See [Understanding enterprise support](/en/enterprise-cloud@latest/enterprise-onboarding/support-for-your-enterprise/understanding-support).