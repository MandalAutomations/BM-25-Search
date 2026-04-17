# Troubleshooting missing contributions

Learn common reasons that contributions may be missing from your contributions graph.

## Commit was made less than 24 hours ago

After making a commit that meets the requirements to count as a contribution, you may need to wait for up to 24 hours to see the contribution appear on your contributions graph. For more information, see [Viewing commit details from your timeline](/en/account-and-profile/how-tos/setting-up-and-managing-your-github-profile/managing-contribution-settings-on-your-profile/troubleshooting-commits-on-your-timeline).

## Your local Git commit email isn't connected to your account

Commits must be made with an email address that is connected to your account on GitHub, or the GitHub-provided `noreply` email address provided to you in your email settings, in order to appear on your contributions graph. For more information about `noreply` email addresses, see [Setting your commit email address](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address#about-commit-email-addresses).

You can check the email address used for a commit by adding `.patch` to the end of a commit URL. For example, the following commit URL includes `.patch`.

<https://github.com/octocat/octocat.github.io/commit/67c0afc1da354d8571f51b6f0af8f2794117fd10.patch>

```text
From 67c0afc1da354d8571f51b6f0af8f2794117fd10 Mon Sep 17 00:00:00 2001
From: The Octocat <octocat@nowhere.com>
Date: Sun, 27 Apr 2014 15:36:39 +0530
Subject: [PATCH] updated index for better welcome message
```

The email address in the `From:` field is the address that was set in the [local git config settings](/en/get-started/git-basics/set-up-git). In this example, the email address used for the commit is `octocat@nowhere.com`.

If the email address used for the commit is not connected to your account on GitHub, you must [add the email address](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/adding-an-email-address-to-your-github-account) to your account on GitHub. Your contributions graph will be rebuilt automatically when you add the new address.

> \[!NOTE]
> If you use a managed user account, you cannot add additional email addresses to the account, even if multiple email addresses are registered with your identity provider (IdP). Therefore, only commits that are authored by the primary email address registered with your IdP can be associated with your managed user account.

Generic email addresses, such as `jane@computer.local`, cannot be added to GitHub accounts and linked to commits. If you've authored any commits using a generic email address, the commits will not be linked to your GitHub profile and will not show up in your contribution graph.

## Commit was not made in the default or `gh-pages` branch

Commits are only counted if they are made in the default branch or the `gh-pages` branch (for repositories with project sites). For more information, see [What is GitHub Pages?](/en/pages/getting-started-with-github-pages/what-is-github-pages#types-of-github-pages-sites).

If your commits are in a non-default or non-`gh-pages` branch and you'd like them to count toward your contributions, you will need to do one of the following:

* [Open a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) to have your changes merged into the default branch or the `gh-pages` branch.
* [Change the default branch](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/changing-the-default-branch) of the repository.

> \[!WARNING]
> Changing the default branch of the repository will change it for all repository collaborators. Only do this if you want the new branch to become the base against which all future pull requests and commits will be made.

## Commit was made in a fork

Commits made in a fork will not count toward your contributions. To make them count, you must open a pull request to have your changes merged into the parent repository. For more information, see [Creating a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request).

## Next steps

* [Profile contributions reference](/en/account-and-profile/reference/profile-contributions-reference)
* [Viewing contributions on your profile](/en/account-and-profile/setting-up-and-managing-your-github-profile/managing-contribution-settings-on-your-profile/viewing-contributions-on-your-profile)