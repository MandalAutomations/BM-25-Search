# Recovering your SSH key passphrase

If you've lost your SSH key passphrase, depending on the operating system you use, you may either recover it or you may need to generate a new SSH key passphrase.

<div class="ghd-tool mac">

If you [configured your SSH passphrase with the macOS keychain](/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases#saving-your-passphrase-in-the-keychain), you may be able to recover it.

1. In Finder, search for the **Keychain Access** app.
2. In Keychain Access, search for **SSH**.
3. Double click on the entry for your SSH key to open a new dialog box.
4. In the lower-left corner, select **Show password**.
5. You'll be prompted for your administrative password. Type it into the "Keychain Access" dialog box.
6. Your password will be revealed.

</div>

<div class="ghd-tool windows">

If you lose your SSH key passphrase, there's no way to recover it. You'll need to [generate a brand new SSH keypair](/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) or [switch to HTTPS cloning](/en/get-started/git-basics/about-remote-repositories#cloning-with-https-urls) so you can use a personal access token instead.

</div>

<div class="ghd-tool linux">

If you lose your SSH key passphrase, there's no way to recover it. You'll need to [generate a brand new SSH keypair](/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) or [switch to HTTPS cloning](/en/get-started/git-basics/about-remote-repositories#cloning-with-https-urls) so you can use a personal access token instead.

</div>