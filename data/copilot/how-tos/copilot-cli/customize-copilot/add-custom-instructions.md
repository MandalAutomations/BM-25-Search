# Adding custom instructions for GitHub Copilot CLI

Give Copilot additional context on how to understand your project and how to build, test and validate its changes.

GitHub Copilot can provide responses that are tailored to your personal preferences, the way your team works, the tools you use, or the specifics of your project, if you provide it with enough context to do so. Instead of repeatedly adding this contextual detail to your prompts, you can create custom instructions that automatically add this information for you. The additional information is not displayed, but is available to Copilot to allow it to generate higher quality responses.

## Types of custom instructions

GitHub Copilot CLI supports the following types of custom instructions.

### Repository-wide custom instructions

These apply to all requests made in the context of a repository.

These are specified in a `copilot-instructions.md` file in the `.github` directory at the root of the repository. See [Creating repository-wide custom instructions](#creating-repository-wide-custom-instructions).

### Path-specific custom instructions

These apply to requests made in the context of files that match a specified path.

These are specified in one or more `NAME.instructions.md` files within or below the `.github/instructions` directory at the root of the repository, or within or below a `.github/instructions` directory in the current working directory. See [Creating path-specific custom instructions](#creating-path-specific-custom-instructions).

If the path you specify in these instructions matches a file that Copilot is working on, and a repository-wide custom instructions file also exists, then the instructions from both files are used. You should avoid potential conflicts between instructions as Copilot's choice between conflicting instructions is non-deterministic.

### Agent instructions

These are used by various AI agents.

You can create one or more `AGENTS.md` files. These can be located in the repository's root directory, in the current working directory, or in any of the directories specified by a comma-separated list of paths in the `COPILOT_CUSTOM_INSTRUCTIONS_DIRS` environment variable.

Instructions in the `AGENTS.md` file in the root directory, if found, are treated as primary instructions. If an `AGENTS.md` file and a `.github/copilot-instructions.md` file are both found at the root of the repository, the instructions in both files are used.

Instructions found in other `AGENTS.md` files are treated as additional instructions. Any primary instructions that are found are likely to have more effect on Copilot's responses than additional instructions.

For more information, see the [agentsmd/agents.md repository](https://github.com/agentsmd/agents.md).

Alternatively, you can use `CLAUDE.md` and `GEMINI.md` files. These must be located at the root of the repository.

### Local instructions

These apply within a specific local environment.

You can specify instructions within your own home directory, by creating a file at `$HOME/.copilot/copilot-instructions.md`.

You can also set the `COPILOT_CUSTOM_INSTRUCTIONS_DIRS` environment variable to a comma-separated list of directories. Copilot CLI will look for an `AGENTS.md` file, and any `.github/instructions/**/*.instructions.md` files, in each of these directories.

## Creating repository-wide custom instructions

1. In the root of your repository, create a file named `.github/copilot-instructions.md`.

   Create the `.github` directory if it does not already exist.

2. Add natural language instructions to the file, in Markdown format.

   Whitespace between instructions is ignored, so the instructions can be written as a single paragraph, each on a new line, or separated by blank lines for legibility.

   For help on writing effective custom instructions, see [About customizing GitHub Copilot responses](/en/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions).

## Creating path-specific custom instructions

1. Create the `.github/instructions` directory if it does not already exist.

2. Optionally, create subdirectories of `.github/instructions` to organize your instruction files.

3. Create one or more `NAME.instructions.md` files, where `NAME` indicates the purpose of the instructions. The file name must end with `.instructions.md`.

4. At the start of the file, create a frontmatter block containing the `applyTo` keyword. Use glob syntax to specify what files or directories the instructions apply to.

   For example:

   ```markdown
   ---
   applyTo: "app/models/**/*.rb"
   ---
   ```

   You can specify multiple patterns by separating them with commas. For example, to apply the instructions to all TypeScript files in the repository, you could use the following frontmatter block:

   ```markdown
   ---
   applyTo: "**/*.ts,**/*.tsx"
   ---
   ```

   Glob examples:

   * `*` - will all match all files in the current directory.
   * `**` or `**/*` - will all match all files in all directories.
   * `*.py` - will match all `.py` files in the current directory.
   * `**/*.py` - will recursively match all `.py` files in all directories.
   * `src/*.py` - will match all `.py` files in the `src` directory. For example, `src/foo.py` and `src/bar.py` but *not* `src/foo/bar.py`.
   * `src/**/*.py` - will recursively match all `.py` files in the `src` directory. For example, `src/foo.py`, `src/foo/bar.py`, and `src/foo/bar/baz.py`.
   * `**/subdir/**/*.py` - will recursively match all `.py` files in any `subdir` directory at any depth. For example, `subdir/foo.py`, `subdir/nested/bar.py`, `parent/subdir/baz.py`, and `deep/parent/subdir/nested/qux.py`, but *not* `foo.py` at a path that does not contain a `subdir` directory.

5. Optionally, to prevent the file from being used by either Copilot cloud agent or Copilot code review, add the `excludeAgent` keyword to the frontmatter block. Use either `"code-review"` or `"cloud-agent"`.

   For example, the following file will only be read by Copilot cloud agent.

   ```markdown
   ---
   applyTo: "**"
   excludeAgent: "code-review"
   ---
   ```

   If the `excludeAgent` keyword is not included in the front matterblock, both Copilot code review and Copilot cloud agent will use your instructions.

6. Add your custom instructions in natural language, using Markdown format. Whitespace between instructions is ignored, so the instructions can be written as a single paragraph, each on a new line, or separated by blank lines for legibility.

<div class="ghd-alert ghd-alert-accent ghd-spotlight-accent">

Did you successfully add a custom instructions file to your repository?

<a href="https://docs.github.io/success-test/yes.html" target="_blank" class="btn btn-outline mt-3 mr-3 no-underline"><span>Yes</span></a>  <a href="https://docs.github.io/success-test/no.html" target="_blank" class="btn btn-outline mt-3 mr-3 no-underline"><span>No</span></a>

</div>

## Custom instructions in use

The instructions in the file(s) are available for use by Copilot as soon as you save the file(s). Instructions are automatically added to requests that you submit to Copilot.

If you make changes to your custom instructions during a CLI session, your changes are available for use by Copilot the next time you submit a prompt in the current, or future, sessions.

## Further reading

* [Support for different types of custom instructions](/en/copilot/reference/custom-instructions-support)
* [Custom instructions](/en/copilot/tutorials/customization-library/custom-instructions)—a curated collection of examples
* [Using custom instructions to unlock the power of Copilot code review](/en/copilot/tutorials/use-custom-instructions)