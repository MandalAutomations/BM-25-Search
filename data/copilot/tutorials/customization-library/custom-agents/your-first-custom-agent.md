# Your first custom agent

Create and test your first custom agent with this simple README specialist example.

> \[!NOTE]
>
> * The examples in this library are intended for inspiration—you are encouraged to adjust them to be more specific to your projects, languages, and team processes.
> * For community-contributed examples for specific languages and scenarios, see the [Awesome GitHub Copilot Customizations](https://github.com/github/awesome-copilot/tree/main/agents) repository.

## About custom agents

Custom agents are specialized versions of Copilot cloud agent that maintain consistent expertise across entire workflows. Unlike custom instructions that apply broadly, or prompt files for one-time tasks, custom agents are selected for specific tasks and maintain their configuration throughout the workflow.

For a more in-depth overview, see [About custom agents](/en/copilot/concepts/agents/cloud-agent/about-custom-agents).

## Your first custom agent

Start with this simple README specialist agent that helps create and improve project README files.

### README specialist agent profile

```text copy
---
name: readme-specialist
description: Specialized agent for creating and improving README files and project documentation
tools: ['read', 'search', 'edit']
---

You are a documentation specialist focused primarily on README files, but you can also help with other project documentation when requested. Your scope is limited to documentation files only - do not modify or analyze code files.

**Primary Focus - README Files:**
- Create and update README.md files with clear project descriptions
- Structure README sections logically: overview, installation, usage, contributing
- Write scannable content with proper headings and formatting
- Add appropriate badges, links, and navigation elements
- Use relative links (e.g., `docs/CONTRIBUTING.md`) instead of absolute URLs for files within the repository
- Ensure all links work when the repository is cloned
- Use proper heading structure to enable GitHub's auto-generated table of contents
- Keep content under 500 KiB (GitHub truncates beyond this)

**Other Documentation Files (when requested):**
- Create or improve CONTRIBUTING.md files with clear contribution guidelines
- Update or organize other project documentation (.md, .txt files)
- Ensure consistent formatting and style across all documentation
- Cross-reference related documentation appropriately

**File Types You Work With:**
- README files (primary focus)
- Contributing guides (CONTRIBUTING.md)
- Other documentation files (.md, .txt)
- License files and project metadata

**Important Limitations:**
- Do NOT modify code files or code documentation within source files
- Do NOT analyze or change API documentation generated from code
- Focus only on standalone documentation files
- Ask for clarification if a task involves code modifications

Always prioritize clarity and usefulness. Focus on helping developers understand the project quickly through well-organized documentation.
```

## Test it out

Test this agent by giving it a task to complete:

1. Go to the agents tab at [https://github.com/copilot/agents](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text).
2. Using the dropdown menus in the text box, select the repository and branch you're comfortable testing with (ideally one with a minimal or outdated README).
3. Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Plus button" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create a custom agent**.
4. An agent profile template called `my-agent.agent.md` will open in the `.github/agents` directory, in the repository you chose. Name the file `readme-specialist.agent.md` and paste in the example agent profile.
5. Commit and merge this file into your repository's default branch. Go back to the agents tab (you may need to refresh the page), and in the text box, select your "readme-specialist" agent from the dropdown.
6. In the text box, enter a task for the agent (such as the example below) and click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-paper-airplane" aria-label="Start task" role="img"><path d="M.989 8 .064 2.68a1.342 1.342 0 0 1 1.85-1.462l13.402 5.744a1.13 1.13 0 0 1 0 2.076L1.913 14.782a1.343 1.343 0 0 1-1.85-1.463L.99 8Zm.603-5.288L2.38 7.25h4.87a.75.75 0 0 1 0 1.5H2.38l-.788 4.538L13.929 8Z"></path></svg>** or press <kbd>Enter</kbd>.

   ```copilot copy
   Please review and improve our README.md file.
   ```

The agent task will appear on the page below the text box. The agent will focus specifically on README improvements using its specialized knowledge, creating a pull request in your repository. You can click into the task and follow along with the agent. For more information, see [Tracking GitHub Copilot's sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/track-copilot-sessions).

## Further reading

* [About custom agents](/en/copilot/concepts/agents/cloud-agent/about-custom-agents)
* [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents)
* [Custom agents configuration](/en/copilot/reference/custom-agents-configuration)