# Setting up your profile

Your profile tells people who you are and what you're interested in.

## About your profile

Your profile page on GitHub is a place where people can find out more about you. You can use your profile to:

* **Share** your interests and skills.
* **Showcase** your projects and contributions.
* **Express** your identity and show the GitHub community who you are.

In this tutorial, you'll learn how to personalize your profile by adding a profile picture, bio, and a profile README.

You'll also learn the basics of Markdown syntax, which is what you'll use to format any writing you do on GitHub.

### Prerequisites

* You must have a GitHub account. For more information, see [Creating an account on GitHub](/en/get-started/start-your-journey/creating-an-account-on-github).

## Adding a profile picture and bio

First, we'll add a picture to your profile. Your profile picture helps identify you across GitHub.

### Adding a profile picture

1. In the upper-right corner of any page, click your existing profile avatar, then, from the dropdown menu, click **Settings**.
2. Under "Profile Picture", select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="pencil" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> Edit**, then click **Upload a photo...**.

   ![Screenshot of the "Public profile" section of a user account's settings. A button, labeled with a pencil icon and "Edit", is outlined in dark orange.](/assets/images/help/profile/edit-profile-photo.png)
3. Select an image, then click **Upload**.
4. Crop your picture.
5. Click **Set new profile picture**.

Next, we'll add some basic information about yourself to share with other GitHub users. This information will display below your profile picture on your profile page.

### Adding a bio

1. On your profile page, under your profile picture, click **Edit profile**.

2. Under "Bio", write one or two sentences about yourself, such as who you are and what you do.

   > \[!NOTE]
   > Keep the bio short; we'll add a longer description of your interests in your profile README in the section below.

3. To add an emoji to your bio, visit [Emoji cheat sheet](https://www.webfx.com/tools/emoji-cheat-sheet/) and copy and paste an emoji into the "Bio" dialog box.

4. Optionally, add your preferred pronouns, workplace, location and timezone, and any links to your personal website and social accounts. Your pronouns will only be visible to users that are signed in to GitHub.

5. Click **Save**.

## Adding a profile README

Next, we'll create a special repository and README file that will be displayed directly on your profile page.

Your profile README contains information such as your interests, skills, and background, and it can be a great way to introduce yourself to other people on GitHub and showcase your work.

As we learned in the [Hello World](/en/get-started/start-your-journey/hello-world) tutorial, `README.md` files are written using Markdown syntax (note the `.md` file extension), which is just a way to format plain text.

In the following steps, we'll create and edit your profile README.

### Step 1: Create a new repository for your profile README

1. In the upper-right corner of any page, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Create something new" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>, then click **New repository**.

   ![Screenshot of a GitHub dropdown menu showing options to create new items. The menu item "New repository" is outlined in dark orange.](/assets/images/help/repository/repo-create-global-nav-update.png)
2. Under "Repository name", type a repository name that matches your GitHub username. For example, if your username is "octocat", the repository name must be "octocat."
3. Optionally, in the "Description" field, type a description of your repository. For example, "My personal repository."
4. Select **Public**.
5. Toggle **Add README** to **On**.
6. Click **Create repository**.

### Step 2: Edit the `README.md` file

1. Click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit this file" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> next to your profile README.

   ![Screenshot of @octocat's profile README. A pencil icon is outlined in dark orange.](/assets/images/help/profile/edit-profile-readme.png)
2. In the "Edit" view, you'll see some pre-populated text to get you started. On line 1, delete the text that says `### Hi there` and type `# About me`.
   * In Markdown syntax, `###` renders the plain text as a small ("third-level") heading, while `##` or `#` renders a second- and first-level heading respectively.
3. Toggle to "Preview" to see how the plain text now renders. You should see the new text displayed as a much larger heading.
4. Toggle back to the "Edit" view.
5. Delete line 3 and line 16.
   * This HTML syntax (e.g. `<!--`) is keeping the other lines hidden when you toggle to "Preview".
6. Complete some of the prompts on lines 8 to 15, and delete any lines you don't want. For example, add your interests, skills, hobbies, or a fun fact about yourself.
7. Now, toggle to "Preview". You should see your completed prompts render as a bulleted list.
8. Toggle back to "Edit" and remove any other lines of text that you don't want displayed on your profile.
9. Keep customizing and editing your profile README.
   * Use the [Emoji cheat sheet](https://www.webfx.com/tools/emoji-cheat-sheet/) to add emojis.
   * Use the [Markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/) to experiment with additional Markdown formatting.

### Step 3: Publish your changes to your profile

1. When you're happy with how your profile README looks in "Preview", and you're ready to publish it, click **Commit changes..**.
2. In the open dialog box, simply click again **Commit changes**.
3. Navigate back to your profile page. You will see your new profile README displayed on your profile.

## Next steps

* If you want to learn more Markdown syntax and add more sophisticated formatting to your profile README, see [Quickstart for writing on GitHub](/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github).
* Alternatively, try the [GitHub Skills](https://skills.github.com/) "Communicate using Markdown" course.
* In the next tutorial, [Finding inspiration on GitHub](/en/get-started/start-your-journey/finding-inspiration-on-github), we'll look at ways you can explore GitHub to find projects and people that interest you.

## Further reading

* [About your profile](/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/about-your-profile)
* [Personalize your profile](/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile)
* [Basic writing and formatting syntax](/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)