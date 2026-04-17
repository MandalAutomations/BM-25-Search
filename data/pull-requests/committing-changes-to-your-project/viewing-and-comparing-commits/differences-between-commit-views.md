# Differences between commit views

You might observe differences in commit history depending on the chosen viewing method.

On GitHub, you can see the commit history of a repository by:

* Navigating to [the commits page](https://github.com/rust-lang/rust/commits/main) of a repository by clicking the clock icon with the number of commits at the top of the main repository view.
* Navigating to [the commit history for a specific file](https://github.com/rust-lang/rust/commits/main/README.md) by clicking on a file, then clicking **History**, to get.

These two commit views may show *different* information at times. The history for a single file may omit commits found on the repository's commit history.

Git has several different ways of showing the history of a repository. When Git shows the history of a single file, it simplifies history by omitting
commits that did not change the file. Instead of looking at every commit to
decide whether it touched the file, Git will omit a whole branch if that branch,
when merged, did not impact the final contents of the file. Any commits on the
branch that touched the file will not be shown.

For a file's commit history, GitHub explicitly follows this simple strategy. It makes the history simpler by removing commits that didn't contribute to the final result. For example, if a side branch made a change and then reverted it, that commit would not show up in the branch history. This makes reviewing branches more efficient, since you only see the commits that affect the file.

This truncated view might not always contain the information you're
after. If you want to see the entire history, GitHub provides a view with more
information on a repository's commits page.

For more information on how Git considers commit history, see [the "History Simplification"](https://git-scm.com/docs/git-log#_history_simplification) section of the `git log` help article.

## Further reading

* [Signing commits](/en/authentication/managing-commit-signature-verification/signing-commits)
* [Searching commits](/en/search-github/searching-on-github/searching-commits)