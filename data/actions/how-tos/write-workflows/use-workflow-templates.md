# Using workflow templates

GitHub provides workflow templates for a variety of languages and tooling.

## Choosing and using a workflow template

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)

3. If you already have a workflow in your repository, click **New workflow**.

4. The "Choose a workflow" page shows a selection of recommended workflow templates. Find the workflow template that you want to use, then click **Configure**. To help you find the workflow template that you want, you can search for keywords or filter by category.

5. If the workflow template contains comments detailing additional setup steps, follow these steps.

   There are guides to accompany many of the workflow templates for building and testing projects. For more information, see [Building and testing your code](/en/actions/automating-builds-and-tests).

6. Some workflow templates use secrets. For example, `${{ secrets.npm_token }}`. If the workflow template uses a secret, store the value described in the secret name as a secret in your repository. For more information, see [Using secrets in GitHub Actions](/en/actions/security-guides/using-secrets-in-github-actions).

7. Optionally, make additional changes. For example, you might want to change the value of `on` when the workflow runs.

8. Click **Start commit**.

9. Write a commit message and decide whether to commit directly to the default branch or to open a pull request.

## Further reading

* [Continuous integration](/en/actions/automating-builds-and-tests/about-continuous-integration)

* [Managing workflow runs](/en/actions/managing-workflow-runs)

* [Monitor workflows](/en/actions/monitoring-and-troubleshooting-workflows/about-monitoring-and-troubleshooting)

* [GitHub Actions billing](/en/billing/managing-billing-for-github-actions)