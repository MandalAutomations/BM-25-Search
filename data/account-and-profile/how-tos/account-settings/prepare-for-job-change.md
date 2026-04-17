# Prepare for job change

If you use your GitHub account for both personal and work purposes, there are steps to follow when you leave your company or organization.

## Update your personal account information

1. Unverify your company email address by deleting it in your Email settings.

   After removal, you can re-add this email without verifying to keep any associated commits linked to your account.

   For more information, see [Changing your primary email address](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/changing-your-primary-email-address).

2. Change your primary email address from your company email to your personal email.

   For more information, see [Changing your primary email address](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/changing-your-primary-email-address).

3. Verify your new primary email address.

   For more information, see [Verifying your email address](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/verifying-your-email-address).

4. Update your GitHub username if it contains references to your company or organization.

   For more information, see [Username changes](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-user-account-settings/changing-your-github-username).

5. Review and update your two-factor authentication (2FA) methods to ensure they aren't linked to company resources:

   * If you use a TOTP app on a company phone, transfer it to your personal device.
   * If you've registered company-owned security keys, remove them and add personal ones instead.
   * If you're using GitHub Mobile on a company device, install it on your personal device.
   * Download fresh recovery codes and store them in a personal secure location.

   For more information, see [Configuring two-factor authentication](/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication).

## Leave organization memberships

> \[!NOTE] Unless you're using a managed user account, you'll still be able to access your personal account after leaving an organization.

1. If you're the organization owner, transfer ownership to another person before removing yourself.

   For more information, see [Transferring organization ownership](/en/organizations/managing-organization-settings/transferring-organization-ownership).

2. Remove yourself from the organization.

   For more information, see [Removing yourself from an organization](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/removing-yourself-from-an-organization).

## Clean up professional repository associations

1. Remove yourself as a collaborator from repositories owned by others.

   For more information, see [Removing yourself from a collaborator's repository](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/removing-yourself-from-a-collaborators-repository).

2. Stop watching work-related repositories to avoid unnecessary notifications.

   To manage your watched repositories, visit <https://github.com/watching>.

3. Transfer repositories that you own that others may need to continue working on.

   For more information, see [Transferring a repository](/en/repositories/creating-and-managing-repositories/transferring-a-repository).

4. Delete any work-related forks that belong to you.

   Deleting a fork doesn't delete the upstream repository.

   For more information, see [Deleting a repository](/en/repositories/creating-and-managing-repositories/deleting-a-repository).

5. Delete local copies of your work repositories from your computer by running the following command:

   ```shell
   rm -rf --one-file-system -- WORK_DIRECTORY
   ```

   Replace `WORK_DIRECTORY` with the path to your work repository.