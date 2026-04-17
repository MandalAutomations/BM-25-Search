# Uploading a project to GitHub

Learn how to upload the files for your project to GitHub.

## Introduction

This tutorial will show you how to upload a group of files to a GitHub repository.

Uploading your files to a GitHub repository lets you:

* **Apply version control** when you make edits to the files, so your project's history is protected and manageable.
* **Back up** your work, because your files are now stored in the cloud.
* **Pin** the repository to your personal profile, so that others can see your work.
* **Share** and discuss your work with others, either publicly or privately.

If you're already familiar with Git, and you're looking for information on how to upload a locally-stored Git repository to GitHub, see [Adding locally hosted code to GitHub](/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-using-git).

## Prerequisites

* You must have a GitHub account. For more information, see [Creating an account on GitHub](/en/get-started/start-your-journey/creating-an-account-on-github).
* You should have a group of files you'd like to upload.

## Step 1: Create a new repository for your project

It's a good idea to create a new repository for each individual project you're working on. If you're writing a software project, grouping all the related files in a new repository makes it easier to maintain and manage the codebase over time.

1. In the upper-right corner of any page, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Create something new" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>, then click **New repository**.

   ![Screenshot of a GitHub dropdown menu showing options to create new items. The menu item "New repository" is outlined in dark orange.](/assets/images/help/repository/repo-create-global-nav-update.png)
2. In the "Repository name" box, type a name for your project. For example, type "my-first-project."
3. In the "Description" box, type a short description. For example, type "This is my first project on GitHub."
4. Select whether your repository will be **Public** or **Private**. Select "Public" if you want others to be able to see your project.
5. Select **Add a README file**. You will edit this file in a later step.
6. Click **Create repository**.

## Step 2: Upload files to your project's repository

So far, you should only see one file listed in the repository, the `README.md` file you created when you initialized the repository. Now, we'll upload some of your own files.

1. To the right of the page, select the **Add file** dropdown menu.
2. From the dropdown menu, click **Upload files**.
3. On your computer, open the folder containing your work, then drag and drop all files and folders into the browser.
4. At the bottom of the page, under "Commit changes", select "Commit directly to the `main` branch, then click **Commit changes**.

## Step 3: Edit the README file for your project's repository

Your repository's README file is typically the first item someone will see when visiting your repository. It usually contains information on what your project is about and why your project is useful.

As we learned in the [Hello World](/en/get-started/start-your-journey/hello-world) tutorial, the README file (`README.md`) is written in Markdown syntax. Markdown is an easy-to-read, easy-to-write language for formatting plain text.

In this step, we'll edit your project's `README.md` using Markdown so that it includes some basic information about your project.

1. From the list of files, click `README.md` to view the file.

2. In the upper right corner of the file view, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit file" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> to open the file editor.
   * You will see that some information about your project has been pre-filled for you. For example, you should see the repository name and repository description you completed in Step 1 displayed on line 1 and line 2.

3. Delete the existing text apart from `#`, then type a proper title for your project.
   * Example: `# About my first project on GitHub`.

4. Next, add some information about your project, such as a description of the project's purpose or its main features.

   > \[!NOTE]
   > If you're not sure what to write, take a look at other repositories on GitHub to see how other people describe their projects.
   >
   > To apply more sophisticated formatting, such as adding images, links, and footnotes, see [Basic writing and formatting syntax](/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

5. Above the new content, click **Preview**.

   ![Screenshot of a file in edit mode. Above the file's contents, a tab labeled "Preview" is outlined in dark orange.](/assets/images/help/repository/edit-readme-preview-changes.png)

6. Take a look at how the file will render once we save our changes, then toggle back to "Edit".

7. Continue to edit and preview the text until you're happy with the content of your README.

8. In the top right, click **Commit changes**.

9. In the dialog box that opens, a commit message has been pre-filled for you ("Update README.md") and, by default, the option to "Commit directly to the `main` branch" has been selected. Leave these options as they are and go ahead and click **Commit changes**.

## Conclusion

You have now created a new repository, uploaded some files to it, and added a project README.

If you set your repository visibility to "Public," the repository will be displayed on your personal profile and you can share the URL of your repository with others.

As you add, edit or delete files directly in the browser on GitHub, GitHub will track these changes ("commits"), so you can start to manage your project's history and evolution.

When making changes, remember that you can create a new branch from the `main` branch of your repository, so that you can experiment without affecting the main copy of files. Then, when you're happy with a set of a changes, open a pull request to merge the changes into your `main` branch. For a reminder of how to do this, see [Hello World](/en/get-started/start-your-journey/hello-world).

## Next steps

* Most people want to keep working on their files locally (i.e. on their own computer), and then continually sync these locally-made changes with this "remote" (in the cloud) repository on GitHub. There are plenty of tools that let you do this, such as GitHub Desktop. To get started, you'd need to:
  * **Install** GitHub Desktop. For more information, see [Getting started with GitHub Desktop](/en/desktop/overview/getting-started-with-github-desktop).
  * **Clone** the remote repository, so you have a copy of it on your own computer. For more information, see [Cloning and forking repositories from GitHub Desktop](/en/desktop/adding-and-cloning-repositories/cloning-and-forking-repositories-from-github-desktop).
  * Continually **sync** your local changes with this remote repository. For more information, see [Syncing your branch in GitHub Desktop](/en/desktop/working-with-your-remote-repository-on-github-or-github-enterprise/syncing-your-branch-in-github-desktop).

* To learn more about other tools available for working with repositories hosted on GitHub, see [Connecting to GitHub](/en/get-started/using-github/connecting-to-github).

## Further reading

* [About the repository README file](/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)
* [Managing files](/en/repositories/working-with-files/managing-files)
* [Cloning a repository](/en/repositories/creating-and-managing-repositories/cloning-a-repository)