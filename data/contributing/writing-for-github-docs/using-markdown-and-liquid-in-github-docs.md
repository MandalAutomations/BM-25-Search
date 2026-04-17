# Using Markdown and Liquid in GitHub Docs

You can use Markdown and Liquid to format content, create reusable content, and write content for different versions on GitHub Docs.

## About using Markdown and Liquid in GitHub Docs

GitHub Docs are written using Markdown, which is a human-friendly syntax for formatting plain text. We use the variant of Markdown called GitHub Flavored Markdown and ensure that it is compliant with CommonMark. For more information, see [About writing and formatting on GitHub](/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/about-writing-and-formatting-on-github).

We use Liquid syntax to expand the functionality to provide accessible tables, maintainable links, versioning, variables, and chunks of reusable content. For more information about Liquid, see the [Liquid documentation](https://shopify.github.io/liquid/basics/introduction/).

The content on this site uses Markdown rendering powered by [`/src/content-render`](https://github.com/github/docs/blob/main/src/content-render/README.md), which is in turn built on the [`remark`](https://remark.js.org/) Markdown processor.

## Lists

In a list item, the general rules for additional content after the first paragraph are:

* Images and subsequent paragraphs should each be on their own line and separated by a blank line.
* All subsequent lines in a list item must match up with the first text after the list marker.

### Example usage of a list

This example shows the correct way to align list items with multiple paragraphs or objects.

```markdown
1. Under your repository name, click **Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)

   This is another paragraph in the list.

1. This is the next item.
```

This content is displayed on the GitHub Docs site with the content under the first list item correctly aligned.

### Example list rendered on GitHub Docs

1. Under your repository name, click **Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)

   This is another paragraph in the list.
2. This is the next item.

## Alerts

Alerts highlight important information that users need to know. For details about supported alert types, how to format them in Markdown, and information on when to use alerts, see [Style guide](/en/contributing/style-guide-and-content-model/style-guide#alerts).

### Examples of alerts

```markdown
> [!TIP]
> Try this out!
```

```markdown
> [!NOTE]
> Generally alerts should be short.
>
> But occasionally may require more than one paragraph
```

### Example alerts rendered on GitHub Docs

> \[!TIP]
> Try this out!

> \[!NOTE]
> Generally alerts should be short.
>
> But occasionally may require more than one paragraph

## Code sample syntax highlighting

To render syntax highlighting in command line instructions and code samples, we use triple backticks followed by the language of the sample. For a list of all supported languages, see [`code-languages.yml`](https://github.com/github/docs/blob/main/data/code-languages.yml).

### Example usage of code syntax highlighting

````
```bash
git init YOUR-REPOSITORY
```
````

Within the code sample syntax, use all uppercase text to indicate placeholder text or content that varies for each user, such as a user or repository name. By default, codeblocks will escape the content within the triple backticks. If you need to write sample code that parses the content (for example, to italicize text within `<em>` tags instead of passing the tags through literally), wrap the codeblock in `<pre>` tags.

### Code blocks with a copy button

You can also add a header that includes the name of the language and a button to copy the contents of the code block.

For example, the following code adds syntax highlighting for JavaScript and a copy button for the code sample.

#### Example usage of a copy button

````
```javascript copy
const copyMe = true
```
````

#### Example code rendered on GitHub Docs

```javascript copy
const copyMe = true
```

## Code sample annotations

Code sample annotations help explain longer code examples by rendering comments as annotations next to the sample code. This lets us write longer explanations of code without cluttering the code itself. Code samples with annotations are rendered in a two pane layout with the code sample on the left and the annotations on the right. The annotations are visually emphasized when someone hovers their cursor over the code example.

Code annotations only work in articles with the `layout: inline` frontmatter property. For more information on how to write and style code annotations, see [Annotating code examples](/en/contributing/syntax-and-versioning-for-github-docs/annotating-code-examples).

### Example of an annotated code sample

````
```yaml annotate
# The name of the workflow as it will appear in the "Actions" tab of the GitHub repository.
name: Post welcome comment
# The `on` keyword lets you define the events that trigger when the workflow is run.
on:
  # Add the `pull_request` event, so that the workflow runs automatically
  # every time a pull request is created.
  pull_request:
    types: [opened]
# Modifies the default permissions granted to `GITHUB_TOKEN`.
permissions:
  pull-requests: write
# Defines a job with the ID `build` that is stored within the `jobs` key.
jobs:
  build:
    name: Post welcome comment
    # Configures the operating system the job runs on.
    runs-on: ubuntu-latest
    # The `run` keyword tells the job to execute the [`gh pr comment`](https://cli.github.com/manual/gh_pr_comment) command on the runner.
    steps:
      - run: gh pr comment $PR_URL --body "Welcome to the repository!"
        env:
          GH_TOKEN: $
          PR_URL: $
```
````

For an example of an article that uses code annotations on GitHub Docs, see [Publishing and installing a package with GitHub Actions](/en/packages/managing-github-packages-using-github-actions-workflows/publishing-and-installing-a-package-with-github-actions).

## Copilot prompts

Prompts for Copilot can either be displayed in blocks or included inline within text.

### Prompt blocks

These are very similar to code blocks, but use the `copilot` keyword rather than the name of a programming language.

Prompt blocks should always have a copy button, added using the `copy` option, and may also have a Copilot button, added using the `prompt` option. The Copilot button gives the reader a quick way to run the prompt in Copilot Chat on GitHub.com. The `copy` and `prompt` options can be used in any order.

#### Example prompt block with Copilot and copy buttons

````markdown
```copilot prompt copy
What is git?
```
````

This is rendered as:

```copilot prompt copy
What is git?
```

You should only add a Copilot button to a prompt block if:

* The prompt can be run without any further context (as shown in the example above).
* There is a code block in the same article that provides the required context for the prompt.

#### Including context with a prompt

If you use a Copilot button, you can add context to the prompt that is sent to Copilot Chat by referencing a code block in the same article. You do this by adding `id=STRING-OF-YOUR-CHOICE` to the code block and `ref=STRING-OF-YOUR-CHOICE` to the prompt block.

#### Example code block used as context within a prompt block

````markdown
Add an id to the code block whose code you want to add to the prompt as context:

```javascript id=js-age
function logPersonsAge(a, b, c) {
  if (c) {
    console.log(a + " is " + b + " years old.");
  } else {
    console.log(a + " does not want to reveal their age.");
  }
}
```

Then, elsewhere in the same article, reference the id in the prompt block:

```copilot copy prompt ref=js-age
Improve the variable names in this function
```
````

There are many examples of prompt blocks with context in the Copilot Cookbook. For example, see [Improving code readability and maintainability](/en/copilot/tutorials/copilot-chat-cookbook/refactor-code/improve-code-readability).

### Inline prompts

For most inline prompts, mark these by using backticks, just like inline code.

If the prompt does not require any context, you can add a clickable Copilot icon after the prompt. This allows the reader to run the prompt in Copilot Chat on GitHub.com. To add the clickable icon, surround the prompt with Liquid syntax tags:

```markdown
... you can click {% prompt %}what is git{% endprompt %} to run this ...
```

This is rendered as:

... you can click <code id="2939823852">what is git</code><a href="https://github.com/copilot?prompt=what%20is%20git" target="_blank" class="tooltipped tooltipped-n ml-1 copilot-prompt-long" aria-label="Run this prompt in Copilot Chat" aria-describedby="2939823852" style="text-decoration:none;"><svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-hidden="true"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg></a><a href="https://github.com/copilot?prompt=what%20is%20git" target="_blank" class="tooltipped tooltipped-n ml-1 copilot-prompt-short" aria-label="Run prompt" aria-describedby="2939823852" style="text-decoration:none;"><svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-hidden="true"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg></a> to run this ...

## Octicons

Octicons are icons used across GitHub’s interface. We reference Octicons when documenting the user interface and to indicate binary values in tables. Find the name of specific Octicons on the [Octicons site](https://primer.style/octicons).

If you're referencing an Octicon that appears in the UI, identify whether the Octicon is the entire label of the UI element (for example, a button that is labeled only with "+") or whether it's only decorative, in addition to another label (for example, a button is labeled "+ Add message").

* If the Octicon is the entire label, use your browser's developer tools to inspect the Octicon and determine what screen reader users will hear instead. Then, use that text for the `aria-label` (for example, `{% octicon "plus" aria-label="Add file" %}`). Occasionally, in the UI, the Octicon itself will not have an `aria-label`, but a surrounding element such as a `<summary>` or `<div>` tag will.
  * Some Octicons used as labels have dynamic `aria-label` elements that change based on the state of the UI element or a user input. For example, when someone has two security policies-`Policy A` and `Policy B`-their UI will show two trash Octicons labeled `{% octicon "trash" aria-label="Delete Policy A" %}` and `{% octicon "trash" aria-label="Delete Policy B" %}`. For dynamic `aria-label` elements, since we can't document the exact `aria-label` that people will encounter, describe the Octicon and a placeholder example of the label (for example, `"{% octicon "trash" aria-label="The trash icon, labeled 'Delete YOUR-POLICY-NAME'." %}"`). This will help people identify both the Octicon and how it is labeled, and give context for collaborating with people who are visually describing the Octicon.
* If the Octicon is decorative, it's likely hidden to screen readers with the `aria-hidden=true` attribute. If so, for consistency with the product, use `aria-hidden="true"` in the Liquid syntax for the Octicon in the docs as well (for example, `"{% octicon "plus" aria-hidden="true" %} Add message"`).

If you're using the Octicon in another way, such as using the "check" and "x" icons to reflect binary values in tables, use the `aria-label` to describe the meaning of the Octicon, not its visual characteristics. For example, if you're using a "x" icon in the "Supported" column of a table, use "Not supported" as the `aria-label`. For more information, see [Style guide](/en/contributing/style-guide-and-content-model/style-guide#tables).

### Example usage of Octicons

```text
{% octicon "<name of Octicon>" %}
{% octicon "plus" %}
{% octicon "plus" aria-label="Add file" %}
"{% octicon "plus" aria-hidden="true" %} Add file"
```

## Operating system tags

We occasionally need to write documentation for different operating systems. Each operating system may require a different set of instructions. We use operating system tags to demarcate information for each operating system.

### Example usage of operating system tags

```text
{% mac %}

These instructions are pertinent to Mac users.

{% endmac %}
```

```text
{% linux %}

 These instructions are pertinent to Linux users.

{% endlinux %}
```

```text
{% windows %}

These instructions are pertinent to Windows users.

{% endwindows %}
```

You can define a default platform in an article's YAML frontmatter. For more information, see [Using YAML frontmatter](/en/contributing/syntax-and-versioning-for-github-docs/using-yaml-frontmatter#defaultplatform).

## Tool tags

We occasionally need to write documentation that has different instructions for different tools. For example, the GitHub UI, GitHub CLI, GitHub Desktop, GitHub Codespaces, and Visual Studio Code might be able to accomplish the same task using different steps. We use tool tags to control what information is displayed for each tool.

GitHub Docs maintains tool tags for GitHub products and selected third-party extensions. See the [`all-tools.ts`](https://github.com/github/docs/blob/main/src/tools/lib/all-tools.ts) object in the `github/docs` repository for a list of all supported tools.

On rare occasions, we will add new tools. Before adding a new tool, read [Creating tool switchers in articles](/en/contributing/syntax-and-versioning-for-github-docs/creating-tool-switchers-in-articles). To add a new tool, add an entry to the `allTools` object in [`lib/all-tools.ts`](https://github.com/github/docs/blob/main/src/tools/lib/all-tools.ts) as a key-value pair. The key is the tag you'll use to refer to the tool in the article, and the value is how the tool will be identified on the tool picker at the top of the article.

You can define a default tool for an article in the YAML frontmatter. For more information, see [Using YAML frontmatter](/en/contributing/syntax-and-versioning-for-github-docs/using-yaml-frontmatter#defaulttool).

### Example usage of tool tags

```text
{% api %}

These instructions are pertinent to API users.

{% endapi %}
```

```text
{% bash %}

These instructions are pertinent to Bash shell commands.

{% endbash %}
```

```text
{% cli %}

These instructions are pertinent to GitHub CLI users.

{% endcli %}
```

```text
{% codespaces %}

These instructions are pertinent to Codespaces users. They are mostly used outside the Codespaces docset, when we want to refer to how to do something inside Codespaces. Otherwise `webui` or `vscode` may be used.

{% endcodespaces %}
```

```text
{% curl %}

These instructions are pertinent to curl commands.

{% endcurl %}
```

```text
{% desktop %}

 These instructions are pertinent to GitHub Desktop.

{% enddesktop %}
```

```text
{% importer_cli %}

These instructions are pertinent to GitHub Enterprise Importer CLI users.

{% endimporter_cli %}
```

```text
{% javascript %}

These instructions are pertinent to javascript users.

{% endjavascript %}
```

```text
{% jetbrains %}

These instructions are pertinent to users of JetBrains IDEs.

{% endjetbrains %}
```

```text
{% powershell %}

These instructions are pertinent to `pwsh` and `powershell` commands.

{% endpowershell %}
```

```text
{% vscode %}

These instructions are pertinent to VS Code users.

{% endvscode %}
```

```text
{% webui %}

These instructions are pertinent to GitHub UI users.

{% endwebui %}
```

## Reusable and variable strings of text

Reusable strings (commonly called content references or conrefs) contain content that is used in more than one place in our documentation. Creating these allows us to update the content in a single location rather than every place the string appears.

For longer strings, we use reusables, and for shorter strings, we use variables. For more information about reusables and variables, see [Creating reusable content](/en/contributing/writing-for-github-docs/creating-reusable-content).

## Table pipes

Every row of a table in the GitHub Docs must start and end with a pipe, `|`, even rows that contain only Liquid versioning.

```markdown
| Where is the table located? | Does every row end with a pipe? |
| --- | --- |
| {% ifversion some-cool-feature %} |
| GitHub Docs | Yes |
| {% endif %} |
```

## Table row headers

If you create a table where the first column contains headers for the table rows, wrap your table in the Liquid tag `{% rowheaders %} {% endrowheaders %}`. For more information on using markup for tables, see [Style guide](/en/contributing/style-guide-and-content-model/style-guide#use-proper-markup-for-row-and-column-headers).

### Example table with row headers

```markdown
{% rowheaders %}

|             | Mona | Tom    | Hobbes |
|-------------|------|--------|--------|
|Type of cat  | Octo | Tuxedo | Tiger  |
|Likes to swim| Yes  | No     | No     |

{% endrowheaders %}
```

### Example table without row headers

```markdown
| Name   | Vocation         |
| ------ | ---------------- |
| Mona   | GitHub mascot    |
| Tom    | Mouse antagonist |
| Hobbes | Best friend      |
```

## Tables with codeblocks

Although using tables to contain block items, such as code blocks, is generally discouraged, occasionally it may be appropriate.

Because [tables in GitHub Flavored Markdown](https://github.github.com/gfm/#tables-extension-) cannot contain any line breaks or block-level structures, you must use HTML tags to write the table structure.

When HTML tables contain code blocks, the width of the table might exceed the regular width of page content, and then overflow into the area normally containing the mini table of contents.

If this happens, add the following CSS style to the `<table>` HTML tag:

```html
<table style="table-layout: fixed;">
```

For a current example of this usage, see [Managing your work with GitHub Actions](/en/actions/examples).

## Links

Links to docs in the `docs` repository must start with a product ID (like `/actions` or `/admin`) and contain the entire filepath, but not the file extension. For example, `/actions/creating-actions/about-custom-actions`.

Image paths must start with `/assets` and contain the entire filepath including the file extension. For example, `/assets/images/help/settings/settings-account-delete.png`.

The links to Markdown pages undergo some transformations on the server side to match the current page's language and version. The handling for these transformations lives in [`lib/render-content/plugins/rewrite-local-links`](https://github.com/github/docs/blob/main/src/content-render/unified/rewrite-local-links.ts).

For example, if you include the following link in a content file:

```text
/github/writing-on-github/creating-a-saved-reply
```

When viewed on GitHub Docs, the link gets rendered with the language code:

```text
/en/github/writing-on-github/creating-a-saved-reply
```

and when viewed on GitHub Enterprise Server docs, the version is included as well:

```text
/en/enterprise-server@2.20/github/writing-on-github/creating-a-saved-reply
```

For more information about links, see [Style guide](/en/contributing/style-guide-and-content-model/style-guide#links).

### Permalinks

Because the site is dynamic, it does not build HTML files for each different version of an article. Instead it generates a "permalink" for every version of the article. It does this based on the article's [`versions` frontmatter](/en/contributing/syntax-and-versioning-for-github-docs/using-yaml-frontmatter#versions).

> \[!NOTE]
> As of early 2021, the `free-pro-team@latest` version is not included in URLs. A helper function called `lib/remove-fpt-from-path.ts` removes the version from URLs.

For example, an article that is available in currently supported versions will have permalink URLs like the following:

* `/en/get-started/git-basics/set-up-git`
* `/en/enterprise-cloud@latest/get-started/git-basics/set-up-git`
* `/en/enterprise-server@3.10/get-started/git-basics/set-up-git`
* `/en/enterprise-server@3.9/get-started/git-basics/set-up-git`
* `/en/enterprise-server@3.8/get-started/git-basics/set-up-git`
* `/en/enterprise-server@3.7/get-started/git-basics/set-up-git`
* `/en/enterprise-server@3.6/get-started/git-basics/set-up-git`

An article that is not available in GitHub Enterprise Server will have just one permalink:

* `/en/get-started/git-basics/set-up-git`

> \[!NOTE]
> If you are a content contributor, you don't need to worry about supported versions when adding a link to a document. Following the examples above, if you want to reference an article, you can just use its relative location: `/github/getting-started-with-github/set-up-git`.

### Internal links with AUTOTITLE

When linking to another GitHub Docs page, use standard Markdown syntax like `[]()`, but type `AUTOTITLE` instead of the page title. The GitHub Docs application will replace `AUTOTITLE` with the title of the linked page during rendering. This special keyword is case-sensitive, so take care with your typing or the replacement will not work.

#### Example usage of internal links with AUTOTITLE

* `For more information, see [AUTOTITLE](/path/to/page).`
* `For more information, see [AUTOTITLE](/path/to/page#section-link).`
* `For more information, see the TOOLNAME documentation in [AUTOTITLE](/path/to/page?tool=TOOLNAME).`

> \[!NOTE]
> Same-page section links do not work with this keyword. Type out the full header text instead.

### Linking to the current article in a different version of the docs

Sometimes you may want to link from an article to the same article in a different product version. For example:

* You mention some functionality that is not available for free, pro, or team plans and you want to link to the GitHub Enterprise Cloud version of the same page.
* The GitHub Enterprise Server version of an article describes a feature that shipped with that version, but site administrators can upgrade to the latest version of the feature that's in use on GitHub Enterprise Cloud.

You can link directly to a different version of the page using the `currentArticle` property. This means that the link will continue to work directly even if the article URL changes.

```markdown
{% ifversion fpt %}For more information, see the [{% data variables.product.prodname_ghe_cloud %} documentation](/enterprise-cloud@latest{{ currentArticle }}).{% endif %}
```

### Preventing transformations

Sometimes you want to link to a Dotcom-only article in Enterprise content and you don't want the link to be Enterprise-ified. To prevent the transformation, you should include the preferred version in the path.

```markdown
[GitHub's Terms of Service](/free-pro-team@latest/github/site-policy/github-terms-of-service)
```

Sometimes the canonical home of content moves outside the docs site. None of the links included in [`src/redirects/lib/external-sites.json`](https://github.com/github/docs/blob/main/src/redirects/lib/external-sites.json) get rewritten. See [`contributing/redirects.md`](https://github.com/github/docs/blob/main/contributing/redirects.md) for more info about this type of redirect.

### Legacy filepaths and redirects for links

Our docs contain links that use legacy filepaths such as `/article/article-name` or `/github/article-name`. Our docs also contain links that refer to articles by past names. Both of these link types function properly because of redirects, but they are bugs.

When you add a link to an article, use the current filepath and article name.