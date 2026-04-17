# Sharing actions and workflows with your enterprise

You can share an action or reusable workflow with your enterprise without publishing the action or workflow publicly.

## Overview

If your organization is owned by an enterprise account, you can share actions and reusable workflows within your enterprise, without publishing them publicly, by allowing GitHub Actions workflows to access an internal or private repository that contains the action or reusable workflow.

Any actions or reusable workflows stored in the internal or private repository can be used in workflows defined in other internal or private repositories owned by the same organization, or by any organization owned by the enterprise. Actions and reusable workflows stored in internal repositories cannot be used in public repositories and actions and reusable workflows stored in private repositories cannot be used in public or internal repositories.

> \[!WARNING]
>
> * If you make a private repository accessible to GitHub Actions workflows in other repositories, outside collaborators on the other repositories can indirectly access the private repository, even though they do not have direct access to these repositories. The outside collaborators can view logs for workflow runs when actions or workflows from the private repository are used.
> * To allow runners to download these actions, GitHub passes a scoped installation token to the runner. This token has read access to the repository, and automatically expires after one hour.

## Sharing actions and workflows with your enterprise

1. Store the action or reusable workflow in an internal or private repository. For more information, see [About repositories](/en/enterprise-cloud@latest/repositories/creating-and-managing-repositories/about-repositories).
2. Configure the repository to allow access to workflows in other internal or private repositories. For more information, see [Managing GitHub Actions settings for a repository](/en/enterprise-cloud@latest/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#allowing-access-to-components-in-a-private-repository) and [Managing GitHub Actions settings for a repository](/en/enterprise-cloud@latest/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#allowing-access-to-components-in-an-internal-repository).

## Further reading

* [Enterprise accounts](/en/enterprise-cloud@latest/admin/overview/about-enterprise-accounts)
* [Reuse workflows](/en/enterprise-cloud@latest/actions/using-workflows/reusing-workflows)