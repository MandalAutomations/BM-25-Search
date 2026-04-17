# Storing your secrets safely

Learn about secrets in software development and how you can manage them safely.

## What is a secret?

In software development, a secret is a piece of sensitive information that is used to authenticate or authorize access to systems, services, data, and APIs. Examples include:

* **API keys** and **access tokens** that allow you to interact with external services such as GitHub's REST API. Access tokens also allow services, such as GitHub Actions, to perform tasks that need authentication, as we will experiment with later.
* **Database credentials** that grant access to local and external databases and storage.
* **Private keys**, such as private SSH and PGP keys, that can be used to access other servers and encrypt data.

Since secrets provide so much access, including to critical systems, we can understand why it's so important to keep your **secrets secure**.

### What can happen when a secret is exposed?

* Attackers can gain **unauthorized access** to everything the secret allows access to.
* Hackers can **steal data**, including sensitive user data. This may have privacy and legal ramifications and harm trust in you and your application.
* Exposed secrets can **cost you money** if hackers run unauthorized workloads on your cloud provider accounts.
* Hackers can use an exposed secret to delete, modify, and disrupt servers which can cause **downtime and data loss**.

Consider all the access and abilities a secret grants you and what a hacker could do with it. For example, if a personal access token for your GitHub account was exposed, a hacker could post and make changes on GitHub as you.

## Best practices for managing your secrets

To avoid these types of issues, follow best practices to prevent leaks and limit damage if a secret is ever exposed.

### Follow the **Principle of Least Privilege (PoLP)**

Whenever possible, restrict what a secret can do and can access to only what is necessary. For example:

* If a secret will only be used to read data and not make changes to data, opt to make it **read only**.
* If the API you're using allows you to limit a secret to only particular scopes or permissions, only select **the ones that you need**. For example, if you only need to create issues with a GitHub secret, there's no reason for the secret to have access to repository contents or anything else.
* If a secret will give an attacker full access to the user account that owns it, **consider creating service accounts** that can take ownership of the secret.

### Protect secrets in your application

* **Never hardcode a secret**. Always use **environment variables** or your platform's secret management tools (such as GitHub's repository secrets).
* If you have to share a secret with someone, use a dedicated tool like a **password manager**. Never send secrets via email or instant message.
* If possible, set **expiration dates** and **rotate your secrets** regularly; this reduces the risk of old secrets being exploited.
* If your application produces a log, ensure that **secrets are redacted before being logged**. Otherwise, active secrets could be saved to plaintext files.

### Limit damage if a secret is exposed

* Consider the secret compromised, even if only exposed for a second, and **revoke the secret immediately**. Then, generate a new secret and store it safely.
* Check any **activity logs** that might show any suspicious activity performed with the compromised secret.
* Consider how the secret was exposed and make changes to your processes so this can't happen again.

## How GitHub helps keep your secrets secure

There's a lot that you can do to keep your secrets safe, but there's also a lot that GitHub does to help keep your secrets secret. Everyone makes mistakes, and we're here to help with features that will catch any secrets you accidentally expose:

* **Push protection**, which we'll experiment with later, blocks pushing secrets to your repositories on GitHub.
* **Secret scanning** scans repositories and creates alerts when it discovers a secret. For some secrets, we also notify the provider so they can take action, such as revoking the secret automatically.

## Practicing safely storing a secret

In this exercise, we'll create a personal access token and store it safely so we can use it with GitHub Actions. The action we'll create is a straightforward workflow that responds to an issue.

### 1. Creating a practice repository

We'll start by creating a repository to work from. The `new2code` account has a template repository we can use to quickly get started.

1. Navigate to the [new repository page](https://github.com/new?template_owner=new2code\&template_name=secret-action). Following this link will pre-select the template on the `new2code` account.
2. Under "Owner", make sure your user account is selected.
3. In the "Repository name" field, type `secret-action`.
4. Beneath the description field, select **Public** to set the repository visibility.
5. Click **Create repository**.

### 2. Committing a dummy token

Everyone makes mistakes, and it's possible that you'll accidentally commit a secret at some point in your coding journey. In this exercise, we'll intentionally commit a **fake token** so that we can become familiar and comfortable with the alert that gets triggered.

1. Navigate to the repository you just created.

2. Navigate to the YAML workflow file by clicking `.github/workflows` in the list of files.

3. Open the workflow file by clicking `comment.yml` in the list of files.

4. To edit the workflow file, at the top-right, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit this file" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>.

5. On line 13, `GH_TOKEN: ""`, insert this dummy token between the quotes:

   ```text
   secret_scanning_ab85fc6f8d7638cf1c11da812da308d43_abcde
   ```

   The end result should look like this:

   ```yaml
   GH_TOKEN: "secret_scanning_ab85fc6f8d7638cf1c11da812da308d43_abcde"
   ```

6. To attempt to commit the change, at the top right, click **Commit changes...** and then click **Commit changes** again in the dialog.

7. You should now see the push protection alert, telling you that "Secret scanning found a GitHub Secret Scanning secret on line 13".

   ![Screenshot of a push protection alert for Line 13 of the file we attempted to commit. The "Cancel" button is highlighted in an orange outline.](/assets/images/help/security/push-protection-example.png)

   If we weren't experimenting with a dummy token, this would alert us that we were one step away from exposing a token. Review the options you can select on the alert.

8. To stop your commit and avoid exposing the secret, click **Cancel**. In the top right, click **Cancel changes**, then discard your unsaved changes if prompted.

### 3. Creating a real token

Now, let's try following our best practices. First, we'll create a personal access token which will allow the action to act on your behalf (the comment it creates will appear to come from your user account).

> \[!NOTE] Notice how we follow the Principle of Least Privilege for each configuration step. Your token will have the shortest expiration necessary, only have access to the repository it needs, and have the minimum permissions needed to work.

1. Navigate to the [new personal access token page](https://github.com/settings/personal-access-tokens/new).
2. Under "Token name", give your new token a name. You can use something like "Action token".
3. Under "Expiration", select "7 days".
4. Under "Repository access", select **Only select repositories**.
5. In the "Select repositories" dropdown, select **just** the practice repository you created earlier.
6. To the right of "Repository permissions" in the "Permissions" section, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-unfold" aria-label="Expand" role="img"><path d="m8.177.677 2.896 2.896a.25.25 0 0 1-.177.427H8.75v1.25a.75.75 0 0 1-1.5 0V4H5.104a.25.25 0 0 1-.177-.427L7.823.677a.25.25 0 0 1 .354 0ZM7.25 10.75a.75.75 0 0 1 1.5 0V12h2.146a.25.25 0 0 1 .177.427l-2.896 2.896a.25.25 0 0 1-.354 0l-2.896-2.896A.25.25 0 0 1 5.104 12H7.25v-1.25Zm-5-2a.75.75 0 0 0 0-1.5h-.5a.75.75 0 0 0 0 1.5h.5ZM6 8a.75.75 0 0 1-.75.75h-.5a.75.75 0 0 1 0-1.5h.5A.75.75 0 0 1 6 8Zm2.25.75a.75.75 0 0 0 0-1.5h-.5a.75.75 0 0 0 0 1.5h.5ZM12 8a.75.75 0 0 1-.75.75h-.5a.75.75 0 0 1 0-1.5h.5A.75.75 0 0 1 12 8Zm2.25.75a.75.75 0 0 0 0-1.5h-.5a.75.75 0 0 0 0 1.5h.5Z"></path></svg> to view all the possible permissions.
7. Scroll down to "Issues" and, in the dropdown on the right, select "Read and write".
8. At the bottom of the page, click **Generate token**. If prompted, confirm by clicking **Generate token** again.

It's crucial to handle the resulting token securely from this moment forward. As we'll be using the token shortly, you can copy it to your clipboard briefly.

### 4. Storing the token safely

We can now store our new token safely in our repository.

1. Navigate to the repository you created at the beginning of the exercise.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)
3. In the "Security" section of the sidebar, select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key-asterisk" aria-label="key-asterisk" role="img"><path d="M0 2.75A2.75 2.75 0 0 1 2.75 0h10.5A2.75 2.75 0 0 1 16 2.75v10.5A2.75 2.75 0 0 1 13.25 16H2.75A2.75 2.75 0 0 1 0 13.25ZM2.75 1.5c-.69 0-1.25.56-1.25 1.25v10.5c0 .69.56 1.25 1.25 1.25h10.5c.69 0 1.25-.56 1.25-1.25V2.75c0-.69-.56-1.25-1.25-1.25Z"></path><path d="M8 4a.75.75 0 0 1 .75.75V6.7l1.69-.975a.75.75 0 0 1 .75 1.3L9.5 8l1.69.976a.75.75 0 0 1-.75 1.298L8.75 9.3v1.951a.75.75 0 0 1-1.5 0V9.299l-1.69.976a.75.75 0 0 1-.75-1.3L6.5 8l-1.69-.975a.75.75 0 0 1 .75-1.3l1.69.976V4.75A.75.75 0 0 1 8 4Z"></path></svg> Secrets and variables**, then click **Actions**.
4. Under "Repository secrets," click **New repository secret**.
5. In the **Name** field, type the name for your secret. For this exercise, we'll use `MY_TOKEN`.
6. In the **Secret** field, paste the personal access token you generated previously.
7. Click **Add secret**.

Your secret is now safely encrypted and ready to use!

### 5. Referencing the token in our action

Now we can update the YAML workflow file to use the token and test it works.

1. Navigate back to your repository. If you're in your repository's settings, you can click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code** under the repository name.

2. Navigate to the YAML workflow file by clicking `.github/workflows` in the list of files.

3. Open the workflow file by clicking `comment.yml` in the list of files.

4. To start editing the workflow file, at the top-right, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit this file" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>.

5. On line 13, `GH_TOKEN: ""`, replace the empty quotes with `${{ secrets.MY_TOKEN }}`. This will reference the repository secret we added previously.

   ```yaml
   GH_TOKEN: ${{ secrets.MY_TOKEN }}
   ```

6. To commit the change, at the top-right, click **Commit changes...**

7. In the "Commit changes" dialog, edit "Commit message" to reflect the change we're making. For example, you could enter "Updating workflow to use repository secret".

8. Make sure "Commit directly to the `main` branch" is selected.

9. Click **Commit changes**.

### 6. Testing out the token and workflow

We should be all set now! Let's go ahead and test the workflow.

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Issues," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-issues-global-nav-update.png)
2. Click **New issue**.
3. Under "Add a title", you can type any title you like.
4. Under "Add a description", in the text area, type `Hello`.
5. Beneath the text area, click **Create**.

Once the workflow has had time to complete, you should see a new comment appear. The comment will be authored by yourself, as we're using your token, and contain a greeting in return.

## Next steps

For a more in-depth dive into secret scanning and push protection, you can complete the [Introduction to secret scanning](https://github.com/skills/introduction-to-secret-scanning/tree/main) course in GitHub Skills.

Another important part of code security is learning how to identify and patch code vulnerabilities in your projects. See [Finding and fixing your first code vulnerability](/en/get-started/learning-to-code/finding-and-fixing-your-first-code-vulnerability).