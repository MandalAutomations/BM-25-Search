# Using GitHub Copilot to explore a codebase

GitHub Copilot Chat can help you gain an understanding of the content, structure, and functionality of a codebase.

## Introduction

If you've been assigned to work on a project that you're not familiar with—or you've found an interesting open source project that you want to contribute to—you'll need some understanding of the codebase before you can start making changes. This guide will show you how to use GitHub Copilot Chat to explore a codebase and quickly learn about the project.

## Working with Copilot Chat

Throughout this guide, we'll work with Copilot Chat on GitHub.com, which you can find at [github.com/copilot](https://github.com/copilot?ref_product=copilot\&ref_type=engagement\&ref_style=text).

## Attaching a codebase

Before Copilot Chat can help you, you need to attach the codebase you want to explore.

1. On GitHub, navigate to [github.com/copilot](https://github.com/copilot?ref_product=copilot\&ref_type=engagement\&ref_style=text).
2. In the text box, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Add attachments" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add repositories, files, and spaces**, then click **Repositories**.
3. Search for and select the repository you want to explore.

Copilot Chat now has access to the code in that repository, and you can start asking questions about it.

## Example prompts

The following prompts are examples of the kind of questions you can ask Copilot to help you find out about a codebase.

### General questions

<!-- Blank lines left between list items to space out the output slightly. -->

* `Based on the code in this repository, give me an overview of the architecture of the codebase. Provide evidence.`

* `Which languages are used in this repo? Show the percentages for each language.`

* `What are the core algorithms implemented in this repo?`

* `What design patterns are used in this repository? Give a brief explanation of each pattern that you find, and an example of code from this repository that uses the pattern, with a link to the file.`

### Specific questions

Whether these questions are useful will depend on the codebase you're exploring.

* `How do I build this project?`

* `Where is authentication handled in this codebase?`

* `Analyze the code in this repository and tell me about the entry points for this application.`

* `Describe the data flow in this application.`

* `Analyze the code in this repository and tell me what application-level security mechanisms are employed. Provide references.`

## Understanding the files in a directory

Use Copilot to help you understand the purpose of the files in a directory, or individual files.

To find out about the files in a directory:

1. Navigate to the directory on GitHub.com.
2. In the top right corner of the page, click the Copilot icon (**<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Copilot icon" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>**) to open Copilot Chat.

   Copilot will use the directory contents as context for your question.
3. Ask Copilot: `Explain the files in this directory`.

To find out about a specific file:

1. Open the file on GitHub.com.
2. In the top right corner of the page, click the Copilot icon (**<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Copilot icon" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>**) to open Copilot Chat.

   Copilot will use the file contents as context for your question.
3. For a small file, ask Copilot: `Explain this file`.
4. For a large file, ask: `Explain what this file does. Start with an overview of the purpose of the file. Then, in appropriately headed sections, go through each part of the file and explain what it does in detail.`

## Understanding specific lines of code

Use Copilot to help you understand specific lines of code in a file.

To find out about a specific line of code:

1. On GitHub, navigate to a repository and open a file.

2. Select the lines by clicking the line number for the first line you want to select, holding down <kbd>Shift</kbd> and clicking the line number for the last line you want to select.

3. To ask your own question about the selected lines, click the Copilot icon (<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>) to the right of your selection.
   This displays the GitHub Copilot Chat panel with the selected lines indicated as the context of your question.

4. To ask a predefined question, click the downward-pointing button beside the Copilot icon, then choose one of the options.

   ![Screenshot of the Copilot buttons, highlighted with a dark orange outline, to the right of some selected code.](/assets/images/help/copilot/copilot-buttons-inline-code.png)

5. If you clicked the Copilot icon, type a question in the prompt box at the bottom of the chat panel and press <kbd>Enter</kbd>.

## Understanding a specific file or symbol

Use Copilot to help you understand the purpose of a specific file or symbol in the codebase. A symbol is a named entity in the code, such as a function, class, or variable.

1. On GitHub, navigate to a repository and open a file.

2. At the top of the file, click the Copilot icon (**<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Copilot icon" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>**) to open Copilot Chat.

   Copilot will display the file contents in a split screen as context for your question.

3. If you want to ask about a specific symbol, highlight the symbol in the file.

4. In the prompt box, type a question about the file or highlighted symbol, and press <kbd>Enter</kbd>.

   Copilot replies in the chat panel.

   > \[!TIP]
   >
   > Copilot's ability to answer natural language questions like these in a repository context is optimized when the semantic code search index for the repository is up to date. For more information, see [Indexing repositories for GitHub Copilot](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/indexing-repositories-for-copilot-chat).

## Finding out about commits

One good way to familiarize yourself with a project is to look at the recent work that's been happening. You can do this by browsing the recent commits.

1. On GitHub, navigate to the main page of the repository.
2. On the main page of the repository, above the file list, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-history" aria-label="history" role="img"><path d="m.427 1.927 1.215 1.215a8.002 8.002 0 1 1-1.6 5.685.75.75 0 1 1 1.493-.154 6.5 6.5 0 1 0 1.18-4.458l1.358 1.358A.25.25 0 0 1 3.896 6H.25A.25.25 0 0 1 0 5.75V2.104a.25.25 0 0 1 .427-.177ZM7.75 4a.75.75 0 0 1 .75.75v2.992l2.028.812a.75.75 0 0 1-.557 1.392l-2.5-1A.751.751 0 0 1 7 8.25v-3.5A.75.75 0 0 1 7.75 4Z"></path></svg> commits**.

   ![Screenshot of the main page for a repository. A clock icon and "178 commits" is highlighted with an orange outline.](/assets/images/help/commits/commits-page.png)
3. Click a commit message to display a diff view for that commit.
4. In the Copilot Chat panel, enter: `What does this commit do?`.
5. If necessary, you can follow up by entering: `Explain in more detail`.

## Using the Insights tab

In addition to using Copilot to help you become familiar with a project, you can also use the **Insights** tab on GitHub.com. This gives you a high-level overview of the repository.

For more information, see [Using Pulse to view a summary of repository activity](/en/repositories/viewing-activity-and-data-for-your-repository/using-pulse-to-view-a-summary-of-repository-activity) and [Viewing a project's contributors](/en/repositories/viewing-activity-and-data-for-your-repository/viewing-a-projects-contributors).

## Further reading

* [Asking GitHub Copilot questions in GitHub](/en/copilot/using-github-copilot/copilot-chat/asking-github-copilot-questions-in-github)