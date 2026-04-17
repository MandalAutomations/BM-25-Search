# Setting a Markdown processor for your GitHub Pages site using Jekyll

You can choose a Markdown processor to determine how Markdown is rendered on your GitHub Pages site.

> \[!NOTE] While the `github-pages` gem remains supported for some workflows, GitHub Actions is now the recommended approach for deploying and automating GitHub Pages sites.

People with write permissions for a repository can set the Markdown processor for a GitHub Pages site.

GitHub Pages supports two Markdown processors: [kramdown](http://kramdown.gettalong.org/) and GitHub's own Markdown processor, which is used to render [GitHub Flavored Markdown (GFM)](https://github.github.com/gfm/) throughout GitHub. For more information, see [About writing and formatting on GitHub](/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/about-writing-and-formatting-on-github).

You can use GitHub Flavored Markdown with either processor.

1. On GitHub, navigate to your site's repository.

2. In your repository, browse to the \_*config.yml* file.

3. In the upper right corner of the file view, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit file" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> to open the file editor.
   ![Screenshot of a file. In the header, a button, labeled with a pencil icon, is outlined in dark orange.](/assets/images/help/repository/edit-file-edit-button.png)

   > \[!NOTE]
   > Instead of editing and committing the file using the default file editor, you can optionally choose to use the [github.dev code editor](/en/codespaces/the-githubdev-web-based-editor) by selecting the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="More edit options" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu and clicking **github.dev**. You can also clone the repository and edit the file locally via GitHub Desktop by clicking **GitHub Desktop**.
   >
   > ![Screenshot of a file. In the header, a downwards-facing triangle icon is outlined in dark orange.](/assets/images/help/repository/edit-file-edit-dropdown.png)

4. Find the line that starts with `markdown:` and change the value to `kramdown` or `GFM`. The full line should read `markdown: kramdown` or `markdown: GFM`.

5. Click **Commit changes...**

6. In the "Commit message" field, type a short, meaningful commit message that describes the change you made to the file. You can attribute the commit to more than one author in the commit message. For more information, see [Creating a commit with multiple authors](/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/creating-a-commit-with-multiple-authors).

7. If you have more than one email address associated with your account on GitHub, click the email address drop-down menu and select the email address to use as the Git author email address. Only verified email addresses appear in this drop-down menu. If you enabled email address privacy, then a no-reply will be the default commit author email address. For more information about the exact form the no-reply email address can take, see [Setting your commit email address](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address).

   ![Screenshot of a GitHub pull request showing a dropdown menu with options to choose the commit author email address. octocat@github.com is selected.](/assets/images/help/repository/choose-commit-email-address.png)

8. Below the commit message fields, decide whether to add your commit to the current branch or to a new branch. If your current branch is the default branch, you should choose to create a new branch for your commit and then create a pull request. For more information, see [Creating a pull request](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request).

   ![Screenshot of a GitHub pull request showing a radio button to commit directly to the main branch or to create a new branch. New branch is selected.](/assets/images/help/repository/choose-commit-branch.png)

9. Click **Commit changes** or **Propose changes**.

## Further reading

* [kramdown Documentation](https://kramdown.gettalong.org/documentation.html)
* [GitHub Flavored Markdown Spec](https://github.github.com/gfm/)