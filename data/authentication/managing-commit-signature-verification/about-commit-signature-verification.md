# About commit signature verification

Using GPG, SSH, or S/MIME, you can sign tags and commits locally. These tags or commits are marked as verified on GitHub so other people can be confident that the changes come from a trusted source.

## About commit signature verification

You can sign commits and tags locally, to give other people confidence about the origin of a change you have made. If a commit or tag has a GPG, SSH, or S/MIME signature that is cryptographically verifiable, GitHub marks the commit or tag "Verified" or "Partially verified."

![Screenshot of a commit in the commit list for a repository. "Verified" is highlighted with an orange outline.](/assets/images/help/commits/verified-commit.png)

For most individual users, GPG or SSH will be the best choice for signing commits. S/MIME signatures are usually required in the context of a larger organization. SSH signatures are the simplest to generate. You can even upload your existing authentication key to GitHub to also use as a signing key. Generating a GPG signing key is more involved than generating an SSH key, but GPG has features that SSH does not. A GPG key can expire or be revoked when no longer used. The GPG signature may include the information about it being expired or revoked.

Commits and tags have the following verification statuses, depending on whether you have enabled vigilant mode. By default vigilant mode is not enabled. For information on how to enable vigilant mode, see [Displaying verification statuses for all of your commits](/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits).

Signing commits differs from signing off on a commit. For more information about signing off on commits, see [Managing the commit signoff policy for your repository](/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/managing-the-commit-signoff-policy-for-your-repository).

### Default statuses

| Status                 | Description                                                       |
| ---------------------- | ----------------------------------------------------------------- |
| **Verified**           | The commit is signed and the signature was successfully verified. |
| **Unverified**         | The commit is signed but the signature could not be verified.     |
| No verification status | The commit is not signed.                                         |

### Persistent commit signature verification

Regardless of the signature choice - GPG, SSH, or S/MIME - once a commit signature is verified, it remains verified within its repository's network. See [Understanding connections between repositories](/en/repositories/viewing-activity-and-data-for-your-repository/understanding-connections-between-repositories).

When a commit signature is verified upon being pushed to GitHub, a verification record is stored alongside the commit. This record can't be edited and will persist so that signatures remain verified over time, even if signing keys are rotated, revoked, or if contributors leave the organization.

The verification record includes a timestamp marking when the verification was completed. This persistent record ensures a consistent verified state, providing a stable history of contributions within the repository. You can view this timestamp by hovering over the "Verified" badge on GitHub or by accessing the commit via the REST API, which includes a `verified_at` field. See [REST API endpoints for commits](/en/rest/commits/commits).

Persistent commit signature verification applies to new commits pushed to GitHub. For any commits that predate this feature, a persistent record will be created the next time the commit's signature is verified on GitHub, helping ensure that verified statuses remain stable and reliable across the repository's history.

#### Records persist even after revocation and expiration

Persistent commit signature verification reflects the verified state of a commit at the time of verification. This means that if a signing key is later revoked, expired, or otherwise altered, previously verified commits retain their verified status based on the record created during the initial verification. GitHub will not re-verify previously signed commits or retroactively adjust their verification status in response to changes in the key's state. Organizations may need to manage key states directly to align with their security policies, especially if frequent key rotation or revocation is planned.

#### The verification record is scoped to its repository network

The verification record is persistent across the repository network, meaning that if the same commit is pushed again to the same repository or to any of its forks, the existing verification record is reused. This allows GitHub to maintain a consistent verified status across related repositories without re-verifying the commit each time it appears within the network. This persistence reinforces a unified and reliable view of commit authenticity across all instances of the commit within the repository network.

### Signature verification for rebase and merge

When using the **Rebase and Merge** option on a pull request, it's important to note that the commits in the head branch are added to the base branch without commit signature verification.
When you use this option, GitHub creates a modified commit, using the data and content of the original commit. This means that GitHub didn't truly create this commit, and can't therefore sign it as a generic system user.
GitHub doesn't have access to the committer's private signing keys, so it can't sign the commit on the user's behalf.

A workaround for this is to rebase and merge locally, and then push the changes to the pull request's base branch.

For more information, see [About merge methods on GitHub](/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/about-merge-methods-on-github#rebasing-and-merging-your-commits).

### Statuses with vigilant mode enabled

| Status                 | Description                                                                                                                                                                                                                                                                              |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Verified**           | The commit is signed, the signature was successfully verified, and the committer is the only author who has enabled vigilant mode.                                                                                                                                                       |
| **Partially verified** | The commit is signed, and the signature was successfully verified, but the commit has an author who: a) is not the committer and b) has enabled vigilant mode. In this case, the commit signature doesn't guarantee the consent of the author, so the commit is only partially verified. |
| **Unverified**         | Any of the following is true:<br>- The commit is signed but the signature could not be verified.<br>- The commit is not signed and the committer has enabled vigilant mode.<br>- The commit is not signed and an author has enabled vigilant mode.<br>                                   |

Repository administrators can enforce required commit signing on a branch to block all commits that are not signed and verified. For more information, see [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-signed-commits).

You can check the verification status of your signed commits or tags on GitHub and view why your commit signatures might be unverified. For more information, see [Checking your commit and tag signature verification status](/en/authentication/troubleshooting-commit-signature-verification/checking-your-commit-and-tag-signature-verification-status).

GitHub will automatically use GPG to sign commits you make using the web interface. Commits signed by GitHub will have a verified status. You can verify the signature locally using the public key available at <https://github.com/web-flow.gpg>.

You can optionally choose to have GitHub GPG sign commits you make in GitHub Codespaces. For more information about enabling GPG verification for your codespaces, see [Managing GPG verification for GitHub Codespaces](/en/codespaces/managing-your-codespaces/managing-gpg-verification-for-github-codespaces).

## GPG commit signature verification

You can use GPG to sign commits with a GPG key that you generate yourself.

GitHub uses OpenPGP libraries to confirm that your locally signed commits and tags are cryptographically verifiable against a public key you have added to your account on GitHub.com.

To sign commits using GPG and have those commits verified on GitHub, follow these steps:

1. [Check for existing GPG keys](/en/authentication/managing-commit-signature-verification/checking-for-existing-gpg-keys)
2. [Generate a new GPG key](/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
3. [Add a GPG key to your GitHub account](/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account)
4. [Tell Git about your signing key](/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)
5. [Sign commits](/en/authentication/managing-commit-signature-verification/signing-commits)
6. [Sign tags](/en/authentication/managing-commit-signature-verification/signing-tags)

## SSH commit signature verification

You can use SSH to sign commits with an SSH key that you generate yourself. For more information, see the [Git reference documentation](https://git-scm.com/docs/git-config#Documentation/git-config.txt-usersigningKey) for `user.Signingkey`. If you already use an SSH key to authenticate with GitHub,
you can also upload that same key again for use as a signing key. There's no limit on the number of signing keys you can add to your account.

GitHub uses [ssh\_data](https://github.com/github/ssh_data), an open source Ruby library, to confirm that your locally signed commits and tags are cryptographically verifiable against a public key you have added to your account on GitHub.com.

> \[!NOTE]
> SSH signature verification is available in Git 2.34 or later. To update your version of Git, see the [Git](https://git-scm.com/downloads) website.

To sign commits using SSH and have those commits verified on GitHub, follow these steps:

1. [Check for existing SSH keys](/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys)
2. [Generate a new SSH key](/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
3. [Add a SSH signing key to your GitHub account](/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
4. [Tell Git about your signing key](/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)
5. [Sign commits](/en/authentication/managing-commit-signature-verification/signing-commits)
6. [Sign tags](/en/authentication/managing-commit-signature-verification/signing-tags)

## S/MIME commit signature verification

You can use S/MIME to sign commits with an X.509 key issued by your organization.

GitHub uses [the Debian ca-certificates package](https://packages.debian.org/bullseye/ca-certificates), the same trust store used by Mozilla browsers, to confirm that your locally signed commits and tags are cryptographically verifiable against a public key in a trusted root certificate.

> \[!NOTE]
> S/MIME signature verification is available in Git 2.19 or later. To update your version of Git, see the [Git](https://git-scm.com/downloads) website.

To sign commits using S/MIME and have those commits verified on GitHub, follow these steps:

1. [Tell Git about your signing key](/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)
2. [Sign commits](/en/authentication/managing-commit-signature-verification/signing-commits)
3. [Sign tags](/en/authentication/managing-commit-signature-verification/signing-tags)

You don't need to upload your public key to GitHub.

## Signature verification for bots

Organizations and GitHub Apps that require commit signing can use bots to sign commits. If a commit or tag has a bot signature that is cryptographically verifiable, GitHub marks the commit or tag as verified.

Signature verification for bots will only work if the request is verified and authenticated as the GitHub App or bot and contains no custom author information, custom committer information, and no custom signature information, such as Commits API.

## Further reading

* [Signing commits](/en/authentication/managing-commit-signature-verification/signing-commits)
* [Signing tags](/en/authentication/managing-commit-signature-verification/signing-tags)
* [Troubleshooting commit signature verification](/en/authentication/troubleshooting-commit-signature-verification)