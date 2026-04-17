# Creating a pull request from a fork

You can create a pull request to propose changes you've made to a fork of an upstream repository.

If your pull request compares your topic branch with a branch in the upstream repository as the base branch, then your topic branch is also called the "compare branch" of the pull request.

For example:

* Your topic branch (also known as “feature branch”) is the branch where you’re making your changes in your forked repository (e.g. `my-topic-branch`).
* The base branch is the branch in the upstream (central) repository that you want to merge your changes into (e.g. `main`).
* The pull request compares the changes proposed by the topic branch (`my-topic-branch`) with the base branch (`main`), so `my-topic-branch` is known as the “compare branch”.

For more information about pull request branches, including examples, see [Creating a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request#changing-the-branch-range-and-destination-repository).

> \[!NOTE]
> To open a pull request in a public repository, you must have write access to the head or the source branch or, for organization-owned repositories, you must be a member of the organization that owns the repository to open a pull request.

1. Navigate to the original repository where you created your fork.

2. Above the list of files, in the yellow banner, click **Compare & pull request** to create a pull request for the associated branch.

   ![Screenshot of the banner above the list of files.](/assets/images/help/pull_requests/pull-request-compare-pull-request.png)

3. On the page to create a new pull request, click **compare across forks**.

   ![Screenshot of the page to open a pull request. The "compare across forks" link is outlined in dark orange.](/assets/images/help/pull_requests/compare-across-forks-link.png)

4. In the "base branch" dropdown menu, select the branch of the upstream repository you'd like to merge changes into.

   ![Screenshot of the page to open a new pull request. The dropdown menus for choosing the base repository and branch are outlined in dark orange.](/assets/images/help/pull_requests/choose-base-fork-and-branch.png)

5. In the "head fork" dropdown menu, select your fork, then use the "compare branch" drop-down menu to select the branch you made your changes in.

   ![Screenshot of the page to open a new pull request. The dropdown menus for choosing the head repository and compare branch are outlined in dark orange.](/assets/images/help/pull_requests/choose-head-fork-compare-branch.png)

6. Type a title and description for your pull request.

7. On user-owned forks, if you want to allow anyone with push access to the upstream repository to make changes to your pull request, select **Allow edits from maintainers**.

   > \[!WARNING]
   > If your fork contains GitHub Actions workflows, the option is **Allow edits and access to secrets by maintainers**. Allowing edits on a fork's branch that contains GitHub Actions workflows also allows a maintainer to edit the forked repository's workflows, which can potentially reveal values of secrets and grant access to other branches.

8. To create a pull request that is ready for review, click **Create Pull Request**.
   To create a draft pull request, use the drop-down and select **Create Draft Pull Request**, then click **Draft Pull Request**. If you are the member of an organization, you may need to request access to draft pull requests from an organization owner. See [About pull requests](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#draft-pull-requests).

> \[!TIP]
> After you create a pull request, you can ask a specific person to [review your proposed changes](/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request). For more information, see [Requesting a pull request review](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/requesting-a-pull-request-review).

## Further reading

* [Working with forks](/en/pull-requests/collaborating-with-pull-requests/working-with-forks)
* [Allowing changes to a pull request branch created from a fork](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/allowing-changes-to-a-pull-request-branch-created-from-a-fork)