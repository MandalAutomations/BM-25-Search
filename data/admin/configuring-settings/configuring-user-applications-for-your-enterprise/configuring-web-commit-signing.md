# Configuring web commit signing

You can enable auto-signing of commits made in the web interface of GitHub Enterprise Server.

## About web commit signing

If you enable web commit signing, GitHub Enterprise Server will automatically use GPG to sign commits users make on the web interface of your GitHub Enterprise Server instance. Commits signed by GitHub Enterprise Server will have a verified status. For more information, see [About commit signature verification](/en/enterprise-server@3.20/authentication/managing-commit-signature-verification/about-commit-signature-verification).

You can enable web commit signing, rotate the private key used for web commit signing, and disable web commit signing.

### About persistent commit signature verification

Persistent commit signature verification is related but separate from web commit signing. This feature ensures that the verified status of commits is retained, even if signing keys are changed or revoked.

Persistent commit signature verification helps maintain long-term integrity and trust in your repository’s commit history. However, you may choose to disable it in environments where minimizing disk usage is a priority, especially for large installations with a high number of verified commits.

For information about disabling persistent commit signature verification, see [Disabling persistent commit verification](/en/enterprise-server@3.20/admin/configuring-settings/configuring-user-applications-for-your-enterprise/disabling-persistent-commit-verification).

## Enabling web commit signing

1. In the administrative shell, create a PGP key. Make note of the email address and key ID.

   ```bash copy
   gpg --full-generate-key --pinentry-mode=loopback
   ```

   * Use the default key type and at least `4096` bits with no expiry.
   * Use `web-flow` as the username. If `web-flow` is unavailable or unusable, use any new unique username. Use this username throughout the following steps in this article.
   * If you have a no-reply email address defined in the Management Console, use that email address. If not, use any email address, such as `web-flow@my-company.com`. The email address does not need to be valid.
   * The PGP key **cannot** be protected by a passphrase.

2. Define the key as an environment variable for GitHub Enterprise Server, replacing `<YOUR-KEY-ID>` with the GPG key ID.

   ```bash copy
   ghe-config "secrets.gpgverify.web-signing-key" "$(gpg --export-secret-keys -a <YOUR-KEY-ID> | awk '{printf "%s\\n", $0}')"
   ```

3. Update the settings for GitHub's commit signing service.

   ```bash copy
   sudo consul-template -once -template /etc/consul-templates/etc/nomad-jobs/gpgverify/gpgverify.hcl.ctmpl:/etc/nomad-jobs/gpgverify/gpgverify.hcl
    
   sudo nomad job run /etc/nomad-jobs/gpgverify/gpgverify.hcl
   ```

4. Enable web commit signing.

   ```bash copy
   ghe-config app.github.web-commit-signing-enabled true
   ```

5. Create a new user on your GitHub Enterprise Server instance via built-in authentication or external authentication. For more information, see [Identity and access management fundamentals](/en/enterprise-server@3.20/admin/identity-and-access-management/managing-iam-for-your-enterprise/about-authentication-for-your-enterprise).
   * The user's username must be the same username you used when creating the PGP key in step 1 above, for example, `web-flow`.
   * The user's email address must be the same address you used when creating the PGP key.

6. Run the following command, replacing KEY-ID with your PGP key ID.

   ```bash copy
   gpg --armor --export KEY-ID
   ```

7. Copy your PGP key, beginning with `-----BEGIN PGP PUBLIC KEY BLOCK-----` and ending with `-----END PGP PUBLIC KEY BLOCK-----`.

8. Sign into GitHub Enterprise Server as the user created for web commit signing, for example, `web-flow`.

9. Add the public PGP key to the user's profile. For more information, see [Adding a GPG key to your GitHub account](/en/enterprise-server@3.20/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account).

   > \[!NOTE]
   > Do not remove other public keys from the list of GPG keys. If a public key is deleted, any commits signed with the corresponding private key will no longer be marked as verified.

10. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

11. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

12. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

13. In the "Settings" sidebar, click **Email**.

14. Under "No-reply email address", type the same email address you used when creating the PGP key.

    > \[!NOTE]
    > The "No-reply email address" field will only be displayed if you've enabled email for your GitHub Enterprise Server instance. For more information, see [Configuring email for notifications](/en/enterprise-server@3.20/admin/configuration/configuring-your-enterprise/configuring-email-for-notifications#configuring-smtp-for-your-enterprise).

15. Under the "Settings" sidebar, click **Save settings**.

    > \[!NOTE]
    > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

16. Wait for the configuration run to complete.

## Rotating the private key used for web commit signing

1. In the administrative shell, create a PGP key. Make note of the email address and key ID.

   ```bash copy
   gpg --full-generate-key --pinentry-mode=loopback
   ```

   * Use the default key type and at least `4096` bits with no expiry.
   * Use the web commit signing user's username, for example, `web-flow`.
   * Use the no-reply email address defined in the Management Console, which should be the same as the email address of the web commit signing user, for example, `web-flow`.
   * The PGP key **cannot** be protected by a passphrase.

2. Define the key as an environment variable for GitHub Enterprise Server, replacing `<YOUR-KEY-ID>` with the GPG key ID.

   ```bash copy
   ghe-config "secrets.gpgverify.web-signing-key" "$(gpg --export-secret-keys -a <YOUR-KEY-ID> | awk '{printf "%s\\n", $0}')"
   ```

3. Update the settings for GitHub's commit signing service.

   ```bash copy
   sudo consul-template -once -template /etc/consul-templates/etc/nomad-jobs/gpgverify/gpgverify.hcl.ctmpl:/etc/nomad-jobs/gpgverify/gpgverify.hcl
    
   sudo nomad job run /etc/nomad-jobs/gpgverify/gpgverify.hcl
   ```

4. Run the following command, replacing KEY-ID with your PGP key ID.

   ```bash copy
   gpg --armor --export KEY-ID
   ```

5. Copy your PGP key, beginning with `-----BEGIN PGP PUBLIC KEY BLOCK-----` and ending with `-----END PGP PUBLIC KEY BLOCK-----`.

6. Sign into GitHub Enterprise Server as the user created for web commit signing, for example, `web-flow`.

7. Add the public PGP key to the user's profile. For more information, see [Adding a GPG key to your GitHub account](/en/enterprise-server@3.20/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account).

   > \[!NOTE]
   > Do not remove other public keys from the list of GPG keys. If a public key is deleted, any commits signed with the corresponding private key will no longer be marked as verified.

## Disabling web commit signing

You can disable web commit signing for your GitHub Enterprise Server instance.

1. In the administrative shell, run the following command.

   ```bash copy
   ghe-config app.github.web-commit-signing-enabled false
   ```

2. Apply the configuration.

   ```bash copy
   ghe-config-apply
   ```