# Reminding inactive users to use their GitHub Copilot license

Use the GitHub API to identify inactive users and help them get started.

When you're rolling out GitHub Copilot in a business, it's important to keep track of which users are using their Copilot license, so you can respond effectively by reassigning unused licenses or helping people to get started with Copilot.

You can use the [List all Copilot seat assignments for an organization](/en/rest/copilot/copilot-user-management#list-all-copilot-seat-assignments-for-an-organization) API endpoint to find the last activity date for each user who is assigned a license in an organization. Then, you can respond automatically by filtering for users who haven't used their license for a certain amount of time and sending a reminder to those users.

## Writing the reminder message

Your reminder to inactive users should help users to get past common adoption blockers for Copilot. We recommend identifying specific blockers for your company by running surveys or interviewing developers.

For example, the message could include information and links to help users:

* Install Copilot in their environment.
* Set up Copilot to work with your company's proxy or firewall.
* Get the most out of Copilot in their day-to-day work.

You should also clearly communicate any further action you will take if the license continues to go unused, such as revoking the user's license.

### Example reminder

In the next section, we'll use this message in an automation that creates an issue assigned to each inactive user.

> We noticed you haven't used your assigned license for GitHub Copilot in 30 days. Here are some resources that might help you get started:
>
> * If you haven't yet set up Copilot in your environment, see [Setting up GitHub Copilot for yourself](/en/copilot/setting-up-github-copilot/setting-up-github-copilot-for-yourself) or [Troubleshooting common issues with GitHub Copilot](/en/copilot/troubleshooting-github-copilot/troubleshooting-common-issues-with-github-copilot).
> * For best practices and advice on getting started, see [Best practices for using GitHub Copilot](/en/copilot/using-github-copilot/best-practices-for-using-github-copilot) or [Prompt engineering for GitHub Copilot Chat](/en/copilot/using-github-copilot/copilot-chat/prompt-engineering-for-copilot-chat).
> * For examples related to specific tasks, see [GitHub Copilot Chat Cookbook](/en/copilot/example-prompts-for-github-copilot-chat).
>
> If you no longer need access to Copilot, please let us know in this issue. If your license remains inactive for a further 30 days, we'll revoke it to free up access for another user.

#### Example reminder in Markdown

<!-- markdownlint-disable search-replace -->

```markdown copy
We noticed you haven't used your assigned license for GitHub Copilot in 30 days. Here are some resources that might help you get started:

* If you haven't yet set up Copilot in your environment, see [Setting up GitHub Copilot for yourself](https://docs.github.com/en/copilot/setting-up-github-copilot/setting-up-github-copilot-for-yourself) or [Troubleshooting common issues with GitHub Copilot](https://docs.github.com/en/copilot/troubleshooting-github-copilot/troubleshooting-common-issues-with-github-copilot).
* For best practices and advice on getting started, see [Best practices for using GitHub Copilot](https://docs.github.com/en/copilot/using-github-copilot/best-practices-for-using-github-copilot) or [Prompt engineering for GitHub Copilot](https://docs.github.com/en/copilot/using-github-copilot/prompt-engineering-for-github-copilot).
* For examples related to specific tasks, see [Copilot Chat Cookbook](https://docs.github.com/en/copilot/example-prompts-for-github-copilot-chat).

If you no longer need access to Copilot, please let us know in this issue. If your license remains inactive for a further 30 days, we'll revoke it to free up access for another user.
```

<!-- markdownlint-enable search-replace -->

## Automating the reminder with GitHub Actions

The following example workflow uses the API to identify users in an organization who haven't used their license for 30 days or haven't used it at all since the seat was assigned, then creates an issue assigned to each user. This is a simple example that you can adapt to meet your needs.

To use this workflow:

1. Create a label in the repository where reminder issues will be created. Call the label `copilot-reminder`. We'll use this label to check whether a reminder issue is already open for each inactive user.

   To create a label, see [Managing labels](/en/issues/using-labels-and-milestones-to-track-work/managing-labels#creating-a-label).
2. Save your reminder message, such as the one provided in [Example reminder in Markdown](#example-reminder-in-markdown), as an GitHub Actions variable in your repository or organization. Call the variable `COPILOT_REMINDER_MESSAGE`.

   To create a variable, see [Store information in variables](/en/actions/writing-workflows/choosing-what-your-workflow-does/store-information-in-variables#creating-configuration-variables-for-a-repository).
3. Create a personal access token with permission to call the [List all Copilot seat assignments for an organization](/en/rest/copilot/copilot-user-management#list-all-copilot-seat-assignments-for-an-organization) API endpoint. For example, create a fine-grained token with the following details:

   * **Resource owner**: The organization where you're looking for inactive users.
   * **Organization permissions**: GitHub Copilot Business (read-only).

   To create a token, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token).
4. Save the access token as a GitHub Actions secret in your repository or organization. Call the secret `COPILOT_LICENSE_READ`.

   To create a secret, see [Using secrets in GitHub Actions](/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository).
5. Using the example below, create the workflow in the repository where you want the reminder issues to be created.

   If you're new to GitHub Actions, see [Quickstart for GitHub Actions](/en/actions/writing-workflows/quickstart).
6. If you want to create the issues in a repository other than the one in which the workflow is located, replace `${{ github.repository }}` in the `gh` commands with the name of the repository where you want the reminder issues to be created. For example: `octo-org/octo-repo`.

### Example workflow

> \[!NOTE] This example assumes you assign licenses through an organization. Similar API endpoints exist for enterprise accounts and enterprise teams. See [REST API endpoints for Copilot user management](/en/rest/copilot/copilot-user-management).

<!-- markdownlint-disable GHD021 -->

```yaml annotate
# Name your workflow
name: Remind inactive users about GitHub Copilot license

on:
  # Run on demand (enables `Run workflow` button on the Actions tab to easily trigger a run manually)
  workflow_dispatch:
  # Run the workflow every day at 8am UTC
  schedule:
    - cron: '0 8 * * *'

jobs:
  context-log:
    runs-on: ubuntu-latest

    # Modify the default permissions granted to GITHUB_TOKEN
    permissions:
      contents: read
      issues: write

    steps:
      - name: Check last GitHub Copilot activity
        id: check-last-activity
        run: |
          # List all GitHub Copilot seat assignments for an organization
          RESPONSE=$(gh api \
            -H "Accept: application/vnd.github+json" \
            -H "X-GitHub-Api-Version: 2022-11-28" \
            -H "Authorization: Bearer ${{ secrets.COPILOT_LICENSE_READ }}" \
            /orgs/${{ github.repository_owner }}/copilot/billing/seats)
          echo "Raw Response from gh api:"
          echo "$RESPONSE"

          # Parse and check each user's `last_activity_at` and `created_at`
          echo "$RESPONSE" | jq -c '.seats[]' | while read -r seat; do
            LOGIN=$(echo "$seat" | jq -r '.assignee.login')
            LAST_ACTIVITY=$(echo "$seat" | jq -r '.last_activity_at')
            CREATED_AT=$(echo "$seat" | jq -r '.created_at')

            # List all open issues with label `copilot-reminder`
            EXISTING_ISSUES=$(gh issue list --repo ${{ github.repository }} --assignee $LOGIN --label 'copilot-reminder' --json id)

            # Get last activity date and convert dates to seconds since epoch for comparison
            if [ "$LAST_ACTIVITY" = "null" ]; then
              LAST_ACTIVITY_DATE=$(date -d "$CREATED_AT" +%s)
            else
              LAST_ACTIVITY_DATE=$(date -d "$LAST_ACTIVITY" +%s)
            fi
            THIRTY_DAYS_AGO=$(date -d "30 days ago" +%s)

            # Create issues for inactive users who don't have an existing open issue
            if [ "$LAST_ACTIVITY_DATE" -lt "$THIRTY_DAYS_AGO" ] && [ "$EXISTING_ISSUES" = "[]" ]; then
              echo "User $LOGIN has not been active in the last 30 days. Last activity: $LAST_ACTIVITY"

              NEW_ISSUE_URL="$(gh issue create --title "Reminder about your GitHub Copilot license" --body "${{ vars.COPILOT_REMINDER_MESSAGE }}" --repo ${{ github.repository }} --assignee $LOGIN --label 'copilot-reminder')"
            else
              echo "User $LOGIN is active or already has an assigned reminder issue. Last activity: $LAST_ACTIVITY"
            fi
          done

        # Set the GH_TOKEN, required for the 'gh issue' commands
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

<!-- markdownlint-enable GHD021 -->

## Further reading

* [Metrics data properties for GitHub Copilot](/en/copilot/reference/metrics-data#last_activity_at)
* [Driving GitHub Copilot adoption in your company](/en/copilot/rolling-out-github-copilot-at-scale/driving-copilot-adoption-in-your-company)
* [Tracking license activation and initial usage with Copilot usage metrics](/en/copilot/rolling-out-github-copilot-at-scale/analyzing-usage-over-time-with-the-copilot-metrics-api)