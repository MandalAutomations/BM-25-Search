# Troubleshooting rules

Learn how to troubleshoot rulesets when you're contributing to a repository.

## Troubleshooting rulesets

If you cannot perform an action in a repository and want to know why, you can view the active rulesets targeting the branch or tag you're working with. For more information, see [Managing rulesets for a repository](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository#viewing-rulesets-for-a-repository).

Depending on which rules are active, you may need to edit your commit history locally before you can push your commits to the remote branch. For example, if a branch requires commits to be signed, you can update your signing settings, then use an interactive rebase on your local branch to rewrite your Git history with signed commits. For more information, see [Available rules for rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets#require-signed-commits) and [Using Git rebase on the command line](/en/get-started/using-git/using-git-rebase-on-the-command-line).

If a branch or tag is targeted by rules restricting the metadata of commits, your commits may be rejected if part of the commit's metadata does not match a certain pattern. For example, you might need to add an issue number to the start of your commit message, or change the name of a new branch or tag you're trying to push to the repository. If your commits are rejected, you will see a message telling you the pattern the relevant metadata needs to match. As with signed commits, you may need to perform a rebase to squash the commits or rewrite each commit individually. For more information, see [Available rules for rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets#metadata-restrictions).

When utilizing push rulesets, a maximum of 1000 reference updates are allowed per push. If your push exceeds this limit, it will be rejected. For more information see [Creating rulesets for a repository](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/creating-rulesets-for-a-repository#creating-a-push-ruleset).

Additionally, push rulesets apply to the "Create a blob", "Create a tree", and "Create or update file contents" endpoints in the REST API. See [REST API endpoints for Git blobs](/en/rest/git/blobs?apiVersion=2022-11-28#create-a-blob), [REST API endpoints for Git trees](/en/rest/git/trees?apiVersion=2022-11-28#create-a-tree), and [REST API endpoints for repository contents](/en/rest/repos/contents?apiVersion=2022-11-28#create-or-update-file-contents).

## Troubleshooting required status checks

When defining status checks, the name format depends on the type of check:

* **Workflow**: The name format is `<job name>`.
* **Reusable workflow**: The name format is `<job name> / <reusable job name>`.
* **Other checks**: The name format is `<check name>`.

Required status checks do not take workflow, matrix, or event trigger types into account.