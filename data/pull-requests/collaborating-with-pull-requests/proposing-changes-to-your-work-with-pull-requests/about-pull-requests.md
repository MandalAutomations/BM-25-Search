# About pull requests

Pull requests let you propose, review, and merge code changes.

Pull requests are proposals to merge code changes into a project. A pull request is GitHub's foundational **collaboration feature**, letting you discuss and review changes before merging them. This helps teams work together, catch issues early, and maintain code quality.

<a href="https://github.com/pulls?ref_product=github&ref_type=engagement&ref_style=button" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>View your pull requests</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

## Working with pull requests

The **Conversation** tab of a pull request displays a description of the changes, a timeline of events, and comments and reviews from collaborators. This central hub lets you track the discussion and progress of the proposed changes.

The **Commits** tab shows all commits made to the pull request branch in chronological order. This helps you understand the development history and see how the changes evolved over time.

The **Checks** tab displays the status of any automated tests, builds, or other continuous integration workflows that run when you push commits. These checks help ensure your changes meet quality standards before merging.

The **Files changed** tab shows the differences between the proposed changes and the existing code, making it easy to see what will change when the pull request merges.

## Draft pull requests

When you create a pull request, you can choose to make it a draft pull request. Draft pull requests cannot be merged, and code owners are not automatically requested to review them. This is useful when you want to share work-in-progress without formally requesting reviews.

When you're ready to get feedback on your pull request, you can mark your draft pull request as ready for review. Marking a pull request as ready for review will request reviews from any code owners. You can convert a pull request to a draft at any time. See [Changing the stage of a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/changing-the-stage-of-a-pull-request).

## Pull request refs and merge branches

When you open a pull request, GitHub creates up to two temporary, read-only Git references for it:

| Ref                                   | Description                                                                                                                                                                                                     |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `refs/pull/PULL_REQUEST_NUMBER/head`  | Points to the latest commit on the pull request's head branch.                                                                                                                                                  |
| `refs/pull/PULL_REQUEST_NUMBER/merge` | A merge branch—a simulated merge commit that represents what the repository would look like if the pull request were merged right now. This ref is only available when the pull request has no merge conflicts. |

The merge branch automatically updates when the head branch or base branch changes. To fetch it locally:

```shell
git fetch origin refs/pull/PULL_REQUEST_NUMBER/merge
git checkout FETCH_HEAD
```

Replace `PULL_REQUEST_NUMBER` with the number of your pull request.

For information about how GitHub Actions uses the merge branch, see [Events that trigger workflows](/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#how-the-merge-branch-affects-your-workflow).

## Differences between commits on compare and pull request pages

The compare and pull request pages use different methods to calculate the diff for changed files:

* Compare pages show the diff between the tip of the head ref and the current common ancestor (that is, the merge base) of the head and base ref.
* Pull request pages show the diff between the tip of the head ref and the common ancestor of the head and base ref at the time when the pull request was created. As a result, the merge base used for the comparison might be different.

## Further reading

* [Creating a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)
* [About branches](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)
* [Commenting on a pull request](/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/commenting-on-a-pull-request)