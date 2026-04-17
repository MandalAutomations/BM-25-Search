# Research, plan, and iterate on code changes with Copilot cloud agent

Perform deep research on a repository, create an implementation plan, and make iterative code changes on a branch, then create a pull request when you're ready.

## Introduction

You can use Copilot cloud agent (formerly Copilot coding agent) to:

* Perform **deep research** on a repository by asking Copilot questions.
* **Plan** and refine an approach before Copilot makes changes.
* **Iterate** on code changes on a branch, review a diff, and get Copilot to only **create a pull request when you're ready**.

Copilot cloud agent *won't* automatically open a pull request as part of the session. If you *do* want Copilot to open a pull request for your task right away, you can explicitly ask for one in your prompt. For example, by stating **"Create a pull request to ..."**.

> \[!NOTE] Deep research, planning, and iterating on code changes before creating a pull request are only available with Copilot cloud agent on GitHub.com. Cloud agent integrations (such as Azure Boards, JIRA, Linear, Slack, or Teams) only support creating a pull request directly.

## Performing deep research

You can ask Copilot cloud agent questions about a repository to understand how it works, identify where to make a change, or confirm assumptions before planning and implementation. Copilot starts a **deep research** session to examine the repository and return a grounded answer.

1. Open the agents panel or tab:

   * Open the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> Agents** tab in a repository.
   * **Navigate to the agents page**: Go to [github.com/copilot/agents](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text). You can also get here by opening the agents panel, then clicking **View all**.
   * **Open the agents panel**: Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> in the navigation bar at the top right of GitHub.
2. Ask a question about the repository.

   For example: `Investigate performance issues in this app and suggest improvements.`

   > \[!TIP] Alternatively, open Copilot Chat and attach the relevant repository as context, then ask Copilot Chat to do research. You will be prompted to approve a deep research session.
3. Optionally, send additional prompts while Copilot is working to steer the session.
4. Review the response and ask follow-up questions.

## Creating a plan

You can ask Copilot cloud agent to propose a plan before making changes, simply by prompting the agent.

1. Ask the agent to create a plan.

   For example: `Create a plan to implement the most impactful performance improvements for this app.`
2. Review the plan and iterate with Copilot until it matches what you want.

## Iterating on code changes

After research and planning, you can make changes on a branch, review the diff, and then decide whether to iterate more or create a pull request.

1. Ask the agent to implement changes by describing what you want Copilot to do in your prompt.

   For example, you might reference the plan you designed earlier: `Implement the plan we agreed upon.`
2. Copilot starts a session to make the required changes.
3. Once the session completes, click **Diff** to review the changes.
4. Optionally, open the branch (`copilot/BRANCH-NAME`) that Copilot created to inspect the changes in context.
5. If you want refinements, you can continue the conversation and ask the agent to adjust the work. For example: `Rename this to match our existing conventions.`
6. Continue iterating until you’re satisfied with the branch.
7. Once you're happy with the results, and when the session is complete, click **Create pull request**.

## Further reading

* [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent)
* [Asking GitHub Copilot to create a pull request](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-a-pr)
* [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents)