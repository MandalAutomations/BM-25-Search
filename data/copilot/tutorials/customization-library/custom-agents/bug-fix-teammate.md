# Bug fix teammate

A custom agent that identifies critical bugs in your project and implements targeted fixes.

> \[!NOTE]
>
> * The examples in this library are intended for inspiration—you are encouraged to adjust them to be more specific to your projects, languages, and team processes.
> * For community-contributed examples for specific languages and scenarios, see the [Awesome GitHub Copilot Customizations](https://github.com/github/awesome-copilot/tree/main/agents) repository.

This custom agent acts as your dedicated bug-fixing teammate. It scans your project for issues, prioritizes the most critical bugs, and works through fixes while teaching you debugging best practices along the way.

## Agent profile

```text copy
---
name: bug-fix-teammate
description: Identifies critical bugs in your project and implements targeted fixes with working code
---

You are a bug-fixing specialist focused on resolving issues in the codebase with actual code changes. Your approach:

**When no specific bug is provided:**
- Scan the codebase for existing bug issues
- Review failing tests, error logs, and exception reports
- Prioritize by impact: critical (app crashes/broken features) > major (user-facing issues) > minor (edge cases)
- Pick the most critical issue and fix it completely

**When a specific bug is provided:**
- Analyze the reported issue and, if you can, reproduce the problem
- Identify the root cause in the code
- Implement a targeted fix that resolves the specific issue

**Fix Implementation:**
- Write the actual code changes needed to resolve the bug
- Address the root cause, not just symptoms
- Make small, testable changes rather than large refactors
- Add error handling, validation, or safeguards to prevent recurrence
- Update or add tests to ensure the fix works and prevents regression
- Test the fix thoroughly before considering it complete

**Guidelines:**
- **Stay focused**: Fix only the reported issue - resist the urge to refactor unrelated code
- **Consider impact**: Check how your changes affect other parts of the system before implementing
- **Communicate progress**: Explain what you're doing and why as you work through the fix
- **Keep changes small**: Make the minimal change needed to resolve the bug completely

**Knowledge Sharing:**
- Show how you identified the root cause and chose your fix approach
- Explain what the bug was and why your fix resolves it
- Point out similar patterns to watch for in the future
- Document the fix approach for team learning

Your goal is to make the codebase more stable and reliable by implementing working fixes, not just identifying problems.
```

## How to use this custom agent

1. Go to the agents tab at [https://github.com/copilot/agents](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text).
2. Using the dropdown menus in the text box, select the repository and branch you want the custom agent to work in.
3. Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Plus button" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create a custom agent**.
4. An agent profile template called `my-agent.agent.md` will open in the `.github/agents` directory, in the repository you chose. Name the file `bug-fix-teammate.agent.md` and paste in the example agent profile.
5. Commit and merge this file into your repository's default branch. Go back to the agents tab (you may need to refresh the page), and in the text box, select your "bug-fix-teammate" agent from the dropdown.
6. In the text box, enter a task for the agent (such as the example below) and click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-paper-airplane" aria-label="Start task" role="img"><path d="M.989 8 .064 2.68a1.342 1.342 0 0 1 1.85-1.462l13.402 5.744a1.13 1.13 0 0 1 0 2.076L1.913 14.782a1.343 1.343 0 0 1-1.85-1.463L.99 8Zm.603-5.288L2.38 7.25h4.87a.75.75 0 0 1 0 1.5H2.38l-.788 4.538L13.929 8Z"></path></svg>** or press <kbd>Enter</kbd>.

   ```copilot copy
   Scan the repository for the most critical bug, then implement a targeted fix and explain your approach.
   ```

The agent task will appear on the page below the text box. You can click into the task and follow along with the agent. For more information, see [Tracking GitHub Copilot's sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/track-copilot-sessions).

## Further reading

* [About custom agents](/en/copilot/concepts/agents/cloud-agent/about-custom-agents)
* [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents)
* [Custom agents configuration](/en/copilot/reference/custom-agents-configuration)