# About issue and pull request templates

With issue and pull request templates, you can customize and standardize the information you'd like contributors to include when they open issues and pull requests in your repository.

After you create issue and pull request templates in your repository, contributors can use the templates to open issues or describe the proposed changes in their pull requests according to the repository's contributing guidelines. For more information about adding contributing guidelines to a repository, see [Setting guidelines for repository contributors](/en/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors).

You can create default issue and pull request templates for your organization or personal account. For more information, see [Creating a default community health file](/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file).

## Issue templates

When you create issue templates for your repository using the issue template builder or with issue forms, contributors can select the appropriate template when they open new issues in the repository.

![Screenshot of the new issue page, with multiple templates to choose from.](/assets/images/help/issues/new-issue-page-with-multiple-templates.png)

Issue templates are helpful when you want to provide guidance for opening issues while allowing contributors to specify the content of their issues. If you want contributors to provide specific, structured information when they open issues, issue forms help ensure that you receive your desired information.

Using the template builder, you can specify a title and description for each template, add the template content, and either commit the template to the default branch or open a pull request in the repository. The template builder automatically adds the YAML front matter markup that is required for the template to show on the new issue page. For more information, see [Configuring issue templates for your repository](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository).

With issue forms, you can create templates that have web form fields using the GitHub form schema. When a contributor opens an issue using an issue form, the form inputs are converted to a standard markdown issue comment. You can specify different input types and set inputs as required to help contributors open actionable issues in your repository. For more information, see [Configuring issue templates for your repository](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository#creating-issue-forms) and [Syntax for issue forms](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms).

You can customize the issue template chooser that people see when creating a new issue in your repository by adding a `config.yml` file to the `.github/ISSUE_TEMPLATE` folder. For more information, see [Configuring issue templates for your repository](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository#configuring-the-template-chooser).

Issue templates are stored on the repository's default branch, in a hidden `.github/ISSUE_TEMPLATE` directory. If you create a template in another branch, it will not be available for collaborators to use. Issue template filenames are not case sensitive, and need a *.md* extension. Issue templates created with issue forms need a *.yml* extension. To be displayed with a <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Added" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg> checkmark in the community profile checklist, issue templates must be located in the `.github/ISSUE_TEMPLATE` folder and contain valid `name:` and `about:` keys in the YAML frontmatter (for issue templates defined in `.md` files) or valid `name:` and `description:` keys (for issue forms defined in `.yml` files).

You can create a security policy to give people instructions for reporting security vulnerabilities in your project. For more information, see [Adding a security policy to your repository](/en/code-security/getting-started/adding-a-security-policy-to-your-repository).

## Pull request templates

When you add a pull request template to your repository, project contributors will automatically see the template's contents in the pull request body.

You must create templates on the repository's default branch. Templates created in other branches are not available for collaborators to use. You can store your pull request template in the repository's visible root directory, the `docs` folder, or the hidden `.github` directory. Pull request template filenames are not case sensitive, and can have an extension such as *.md* or *.txt*.

For more information, see [Creating a pull request template for your repository](/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository).