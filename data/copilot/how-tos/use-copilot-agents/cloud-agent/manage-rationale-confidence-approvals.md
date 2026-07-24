# Managing rationale, confidence, and approvals for issues

Set up and manage rationale, confidence, and approvals for issues handled by automation.

Rationale and confidence need no extra configuration. When an automation's agent changes a supported issue attribute, it attaches a rationale and a confidence level automatically. Whether that change applies directly or waits for review depends on your repository's automation level, or on an explicit request to suggest rather than apply the change.

## Setting your repository's automation level

> \[!NOTE]
> Configuring an automation level is rolling out gradually and might not be available in your repository yet.

Your repository's automation level sets the confidence threshold used to route every supported change. Changes rated below the threshold are held as suggestions; changes at or above it apply automatically. The default level is **Cautious**, so only high-confidence changes apply automatically until you change it.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)
3. In the "Planning" section of the sidebar, click **Agent suggestions for issues**.
4. Under "Automation level," select the level that fits your repository:
   * **Full control**: Every change is held for review. Nothing is applied automatically.
   * **Cautious** (default): Only high-confidence changes are applied automatically. Everything else is held for your review.
   * **Balanced**: Routine, clear-cut changes are applied automatically. Anything with ambiguity is held for review.
   * **Full automation**: Every change is applied automatically. The agent only holds a change back if it's flagged as uncertain.
5. Click **Save**.

## With Copilot cloud agent

1. Create an automation that triages issues, following [Creating automations with Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-automations). Use the **When an issue is created** trigger, or run the automation on a schedule.
2. Grant the automation the issue tools for the attributes you want it to change, such as updating labels, setting the type, editing fields, assigning users, or closing issues.
3. In the prompt, describe the triage task, for example: `Triage this issue by setting a type, labels, and priority, and explain your reasoning for each.` You don't need to mention rationale, confidence, or suggestions explicitly. To hold specific changes for review regardless of confidence, ask the agent to suggest those changes rather than apply them.
4. Save the automation. When it runs, its changes carry a rationale and a confidence level. Changes below your repository's automation level, and any changes you asked the agent to suggest, wait in the approvals panel on the issue.

## With GitHub Agentic Workflows

Issue intents, the rationale and confidence metadata attached to a workflow's issue changes, are optional and enabled by default. Existing workflows keep working without changes.

1. Update to the latest version of the GitHub Agentic Workflows extension by running `gh aw upgrade`.
2. Add a workflow that triages issues to your repository's `.github/workflows` directory. You can start from an issue triage sample or author your own. See the [GitHub Agentic Workflows](https://gh.io/gh-aw) documentation.
3. Give the workflow the outputs for the attributes you want it to change by listing them under `safe-outputs` in the workflow's frontmatter. For example, `add-labels` to apply labels, `set-issue-type` to set the issue type, `set-issue-field` to edit fields, `assign-to-user` or `assign-to-agent` to assign issues, and `close-issue` to close them. Adding these outputs is enough for the workflow to make the corresponding issue changes with a rationale and confidence level.
4. Optionally, control whether a safe output requires issue intent metadata by setting `issue-intent` on it:

   ```yaml
   safe-outputs:
     add-labels:
       issue-intent: true
   ```

   * Omit `issue-intent`, or leave it unset, to keep it optional: the agent is encouraged to provide a rationale and confidence level, but the output still works without them.
   * Set `issue-intent: true` to require a rationale and confidence level for that output. The workflow fails if the agent omits them.
   * Set `issue-intent: false` to opt out entirely: the output never carries rationale or confidence metadata.
5. In the workflow prompt, describe the triage task. To hold specific changes for review regardless of confidence, ask the agent to suggest those changes rather than apply them.
6. Compile the workflow by running `gh aw compile`, then commit the workflow file and its generated lock file.
7. When the workflow runs, its changes carry a rationale and a confidence level (unless you opted out). Changes below your repository's automation level, and any changes the agent suggested, wait in the approvals panel on the issue.

## With the REST or GraphQL API

If you build your own integration instead of using an automation, you can use the same issue-writing REST and GraphQL APIs to include a rationale and confidence level with a change, or mark a change as a suggestion to hold it for review. The change is routed the same way as a change from an automation or a GitHub Agentic Workflows workflow: subject to your repository's automation level, or held for review if you marked it as a suggestion.

## Finding issues with pending suggestions

To find issues that have suggestions waiting for review, search using the `has:suggestions` qualifier, for example `is:issue is:open has:suggestions`.

## Reviewing suggestions in the approvals panel

When a change is held for review, it waits in an approvals panel on the issue instead of taking effect. Use the panel to inspect each suggestion and decide what to apply.

1. Open the issue. Suggested changes appear in the approvals panel.
2. Inspect each suggestion. It shows the proposed change, such as a label, type, field, assignee, or close, along with the rationale and confidence level.
3. Act on the suggestions:
   * Select **Accept** to apply a suggestion, or **Decline** to dismiss it.
   * Select **Accept all** or **Decline all** to act on every pending suggestion at once.

Accepted changes take effect on the issue immediately. Declined suggestions are dismissed without changing the issue.

Ready to put this into practice? See [Creating automations with Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-automations) to create an automation that triages issues for you.