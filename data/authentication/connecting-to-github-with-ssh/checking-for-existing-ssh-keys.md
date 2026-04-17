# Checking for existing SSH keys

Before you generate an SSH key, you can check to see if you have any existing SSH keys.

## About SSH keys

You can use SSH to perform Git operations in repositories. For more information, see [About SSH](/en/authentication/connecting-to-github-with-ssh/about-ssh).

If you have an existing SSH key, you can use the key to authenticate Git operations over SSH.

## Checking for existing SSH keys

Before you generate a new SSH key, you should check your local machine for existing keys.

> \[!NOTE]
> GitHub improved security by dropping older, insecure key types on March 15, 2022.
>
> As of that date, DSA keys (`ssh-dss`) are no longer supported. You cannot add new DSA keys to your personal account on GitHub.
>
> RSA keys (`ssh-rsa`) with a `valid_after` before November 2, 2021 may continue to use any signature algorithm. RSA keys generated after that date must use a SHA-2 signature algorithm. Some older clients may need to be upgraded in order to use SHA-2 signatures.

1. Open <span class="platform-mac">Terminal</span><span class="platform-linux">Terminal</span><span class="platform-windows">Git Bash</span>.

2. Enter `ls -al ~/.ssh` to see if existing SSH keys are present.

   ```shell
   $ ls -al ~/.ssh
   # Lists the files in your .ssh directory, if they exist
   ```

3. Check the directory listing to see if you already have a public SSH key. By default, the filenames of supported public keys for GitHub are one of the following.
   * *id\_rsa.pub*

   * *id\_ecdsa.pub*

   * *id\_ed25519.pub*
   > \[!TIP]
   > If you receive an error that *\~/.ssh* doesn't exist, you do not have an existing SSH key pair in the default location. You can create a new SSH key pair in the next step.

4. Either generate a new SSH key or upload an existing key.
   * If you don't have a supported public and private key pair, or don't wish to use any that are available, generate a new SSH key.
   * If you see an existing public and private key pair listed (for example, *id\_rsa.pub* and *id\_rsa*) that you would like to use to connect to GitHub, you can add the key to the ssh-agent.

     For more information about generation of a new SSH key or addition of an existing key to the ssh-agent, see [Generating a new SSH key and adding it to the ssh-agent](/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).