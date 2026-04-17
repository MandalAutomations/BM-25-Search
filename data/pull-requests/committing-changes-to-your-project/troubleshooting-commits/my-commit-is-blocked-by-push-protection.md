# My commit is blocked by push protection

To keep your repository secure, push protection prevents you from accidentally committing secrets to the repository.

## Understanding why push protection has blocked your commit

Leaked secrets can pose serious security risks to your repository and your supply chain. Push protection prevents you from accidentally introducing secrets to your codebase where they could be exploited by malicious actors.

If the repository you're contributing to on GitHub is secured by push protection, you'll encounter a push protection block whenever you:

* **Push commits** containing recognized secrets **from the command line** to the remote repository.
* **Commit changes** or upload files containing recognized secrets to a repository in the **GitHub UI**.
* **Make certain requests** containing recognized secrets in **the REST API**.

## Resolving a push protection block

In order to resolve the block, you should remove the secret from the commit (or request). If you believe the secret is safe to push, you may be able to bypass the block. For more information on how to remove the secret or, if necessary, bypass the block, see:

* [Working with push protection from the command line](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line)
* [Working with push protection in the GitHub UI](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-in-the-github-ui)
* [Working with push protection from the REST API](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-rest-api)

## Further reading

* [About push protection](/en/code-security/secret-scanning/introduction/about-push-protection)
* [Supported secret scanning patterns](/en/code-security/secret-scanning/introduction/supported-secret-scanning-patterns)