# Updating your GitHub access credentials

GitHub credentials include your password, access tokens, SSH keys, and application API tokens used to communicate with GitHub. You can reset all of these access credentials yourself.

## Requesting a new password

1. To request a new password, visit <https://github.com/password_reset>.

2. Enter the email address associated with your account, then click **Send password reset email.**
   > \[!NOTE]
   > Only primary and backup email addresses can be used to request a new password. Unless you have previously chosen a specific backup email address, all verified emails are considered backup email addresses.

3. GitHub will email you a link that will allow you to reset your password. You must click on this link within 3 hours of receiving the email. If you didn't receive an email from us, make sure to check your spam folder.

4. If you have enabled two-factor authentication, you will be prompted for your 2FA credentials:
   * If you have added a passkey or a security key to your account, click **Use passkey or security key**.

   * If you have set up [GitHub Mobile](https://github.com/mobile), you will be sent a push notification to verify your identity. If you didn't receive a notification, click "More options", then **Authenticate with GitHub Mobile**.

   * Alternatively, type your TOTP or SMS authentication code, or one of your recovery codes, and click **Verify**.
   > \[!NOTE]
   > If you've lost access to your two-factor authentication credentials and your recovery codes, you can start account recovery request. See [Recovering your account if you lose your 2FA credentials](/en/authentication/securing-your-account-with-two-factor-authentication-2fa/recovering-your-account-if-you-lose-your-2fa-credentials#recovering-without-your-password-or-two-factor-authentication-credentials).

5. In the text field under **Password**, type a new password. Then, in the text field under **Confirm password**, type the password again.

6. Click **Change password**. For help creating a strong password, see [Creating a strong password](/en/authentication/keeping-your-account-and-data-secure/creating-a-strong-password).

> \[!TIP]
> To avoid losing your password in the future, we suggest using a secure password manager.

## Changing an existing password

When you type a password to sign in, create an account, or change your password, GitHub will check if the password you entered is considered weak according to datasets like HaveIBeenPwned. The password may be identified as weak even if you have never used that password before.

GitHub only inspects the password at the time you type it, and never stores the password you entered in plaintext. For more information, see [HaveIBeenPwned](https://haveibeenpwned.com/).

1. Sign in to GitHub.
2. In the upper-right corner of any page on GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**.
3. In the "Access" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield-lock" aria-label="shield-lock" role="img"><path d="m8.533.133 5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667l5.25-1.68a1.748 1.748 0 0 1 1.066 0Zm-.61 1.429.001.001-5.25 1.68a.251.251 0 0 0-.174.237V7c0 1.36.275 2.666 1.057 3.859.784 1.194 2.121 2.342 4.366 3.298a.196.196 0 0 0 .154 0c2.245-.957 3.582-2.103 4.366-3.297C13.225 9.666 13.5 8.358 13.5 7V3.48a.25.25 0 0 0-.174-.238l-5.25-1.68a.25.25 0 0 0-.153 0ZM9.5 6.5c0 .536-.286 1.032-.75 1.3v2.45a.75.75 0 0 1-1.5 0V7.8A1.5 1.5 0 1 1 9.5 6.5Z"></path></svg> Password and authentication**.
4. Under "Change password", type your old password, a strong new password, and confirm your new password. For help creating a strong password, see [Creating a strong password](/en/authentication/keeping-your-account-and-data-secure/creating-a-strong-password).
5. Click **Update password**.

> \[!TIP]
> For greater security, enable two-factor authentication in addition to changing your password. See [About two-factor authentication](/en/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) for more details.

## Updating your access tokens

See [Reviewing and revoking authorization of GitHub Apps](/en/apps/using-github-apps/reviewing-your-authorized-integrations) for instructions on reviewing and deleting access tokens. To generate new access tokens, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

If you have reset your account password and would also like to trigger a sign-out from the GitHub Mobile app, you can revoke your authorization of the "GitHub iOS" or "GitHub Android" OAuth app. This will sign out all instances of the GitHub Mobile app associated with your account. For additional information, see [Reviewing and revoking authorization of GitHub Apps](/en/apps/using-github-apps/reviewing-your-authorized-integrations).

## Updating your SSH keys

See [Reviewing your SSH keys](/en/authentication/keeping-your-account-and-data-secure/reviewing-your-ssh-keys) for instructions on reviewing and deleting SSH keys. To generate and add new SSH keys, see [Connecting to GitHub with SSH](/en/authentication/connecting-to-github-with-ssh).

## Resetting API tokens

If you have any applications registered with GitHub, you'll want to reset their OAuth tokens. For more information, see the `PATCH /applications/{client_id}/token` endpoint in [REST API endpoints for OAuth authorizations](/en/rest/apps/oauth-applications#reset-a-token).

## Preventing unauthorized access

For more tips on securing your account and preventing unauthorized access, see [Preventing unauthorized access](/en/authentication/keeping-your-account-and-data-secure/preventing-unauthorized-access).