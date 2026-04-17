# Viewing code scanning logs from GitHub Actions

View the output from a code scanning analysis in GitHub Actions.

After configuring code scanning using default setup or a custom GitHub Actions workflow, you can watch the output of the actions as they run. For information about logs for other code scanning setups, see [Code scanning logs](/en/code-security/reference/code-scanning/code-scanning-logs).

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)

   You'll see a list that includes an entry for running the code scanning workflow. The text of the entry is the title you gave your commit message.

   ![Screenshot of the "All workflows" page. In the list of workflow runs is a run labeled "Create .github/workflows/codeql.yml."](/assets/images/help/repository/code-scanning-actions-list.png)

2. Click the entry for the code scanning workflow.

   > \[!NOTE]
   > If you are looking for the CodeQL workflow run triggered by enabling default setup, the text of the entry is "CodeQL."

3. Click the job name on the left. For example, **Analyze (LANGUAGE)**.

   ![Screenshot of the log output for the "Analyze (go)" job. In the left sidebar, under the "Jobs" heading, "Analyze (go)" is listed.](/assets/images/help/repository/code-scanning-logging-analyze-action.png)

4. Review the logging output from the actions in this workflow as they run.

5. Optionally, to see more detail about the commit that triggered the workflow run, click the short commit hash. The short commit hash is 7 lowercase characters immediately following the commit author's username.

6. Once all jobs are complete, you can view the details of any code scanning alerts that were identified. For more information, see [Assessing code scanning alerts for your repository](/en/code-security/code-scanning/managing-code-scanning-alerts/assessing-code-scanning-alerts-for-your-repository#viewing-the-alerts-for-a-repository).

## Further reading

If you're looking for diagnostic information about whether code scanning accessed any private registries, see [Viewing code scanning logs from GitHub Actions](/en/code-security/how-tos/view-and-interpret-data/viewing-code-scanning-logs).