# REST API endpoints for Git LFS

Use the REST API to enable or disable Git Large File Storage (LFS) for a repository.

## About Git LFS

You can use Git LFS to store large files in a Git repository. The REST API allows you to enable or disable the feature for an individual repository. For more information about Git LFS, see [About Git Large File Storage](/en/enterprise-cloud@latest/repositories/working-with-files/managing-large-files/about-git-large-file-storage).

People with admin access to a repository can use these endpoints.

Usage of Git LFS is subject to billing. For more information, see [Git Large File Storage billing](/en/enterprise-cloud@latest/billing/managing-billing-for-your-products/managing-billing-for-git-large-file-storage/about-billing-for-git-large-file-storage).

If you want to use these endpoints for a repository that belongs to an organization, you must have admin access to the repository (which can be inherited as an organization owner), and your role must also provide you with access to the organization's billing.

* If repository is owned by an organization on GitHub Team, you must be an organization owner or billing manager. For more information, see [Roles in an organization](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization#organization-owners).
* If repository is owned by an organization that is on GitHub Enterprise Cloud and is not owned by an enterprise account, you must be an organization owner or billing manager. For more information, see [Roles in an organization](/en/enterprise-cloud@latest/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization#organization-owners).
* If repository is owned by an organization that is owned by an enterprise account, you must be an enterprise owner or billing manager. For more information, see [Abilities of roles in an enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise#enterprise-owners).

> \[!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Enable Git LFS for a repository

```
PUT /repos/{owner}/{repo}/lfs
```

Enables Git LFS for a repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **202** - Accepted

* **403** - We will return a 403 with one of the following messages:

Git LFS support not enabled because Git LFS is globally disabled.
Git LFS support not enabled because Git LFS is disabled for the root repository in the network.
Git LFS support not enabled because Git LFS is disabled for .

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/lfs
```

**Response schema (Status: 202):**

object

## Disable Git LFS for a repository

```
DELETE /repos/{owner}/{repo}/lfs
```

Disables Git LFS for a repository.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

* **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

* **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

* **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

* **204** - No Content

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/lfs
```

**Response schema (Status: 204):**