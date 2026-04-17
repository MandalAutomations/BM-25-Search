# Your first spark

Learn how to build your first GitHub Spark app in minutes, without writing any code.

Have you ever had a great idea for an app, but you didn't have the tools to build it? With the help of AI, you can now bring your app ideas to life in minutes using only natural language. In this article, we'll use GitHub Spark to build, improve, and share a word search app without writing a single line of code ourselves.

> \[!NOTE]
> GitHub Spark is in public preview with [data protection](https://gh.io/dpa) and subject to change.

## Creating a prototype of your app

Let's start by generating an initial, basic version of our app that we can build on later.

1. Navigate to <https://github.com/spark>.

2. Send the following prompt to generate the first iteration of your app:

   ```copilot copy
   Please create a word search game. The game should take in a set of words from the user, then create a word search puzzle containing those words, as well as a word bank listing the words. Words in the puzzle can be horizontal, vertical, diagonal, forwards, and backwards, and are "found" when the user clicks and drags their mouse across them. Once all words are found, give the user the option to create a new puzzle.
   ```

3. Watch as Spark builds your app in real time! You'll know the app is done generating when the preview appears.

4. To test your app, create and solve a puzzle using the preview.

## Improving your app

Just like that, we have a working app! However, it still needs some tweaks. Let's give Spark some additional prompts to polish our project.

1. At the left side of the page, in the **Iterate** tab, send the following prompt:

   ```copilot copy
   Please add a leaderboard and a timer to the game. The timer should start when the user generates a new puzzle, then stop when all words are found. The user should then be able to enter their name, and their name, time, and the number of words in their puzzle should be displayed on the leaderboard. The leaderboard should be sortable in ascending and descending order by each of the three categories.
   ```

2. Once the app is updated, create and solve another puzzle to see the new features in action.

3. Get creative and make your own improvements to the app! If you're feeling stuck, pick one of the suggestions Spark provides above the prompt text box. You can also make changes using the visual editing controls in the "Theme", "Data", and "Prompts" tabs, without ever having to touch code.

## Debugging your app

While you're building your app, you may encounter some errors. Often, Spark will identify these issues and list them in an "Errors" pop up above the prompt text box. To fix the errors, click **Fix all**.

![Screenshot of errors identified by GitHub Spark. The "Fix all" button is outlined in orange.](/assets/images/help/copilot/spark-fix-all-errors.png)

If you find an error that Spark itself didn't flag, write a prompt to fix it. For best results, provide a detailed description of the error, as well as the ideal fixed state. For example, if you notice that adding words over a certain number of characters causes the puzzle to render incorrectly, send the following prompt:

```copilot copy
Please prevent users from entering words longer than the number of rows or columns in the puzzle. Additionally, add an option to change the size of a puzzle. If the user tries to enter a word that's longer than the current size of the puzzle, display an error message telling them that provided words must be less than or equal to the size of the puzzle.
```

## Sharing your app

Now that you're happy with your app, let's publish it so you can share it with others. You can also choose to share your spark as **read-only** so that other users can view your app's content, but they cannot edit content, delete files or records, or create new items.

> \[!NOTE]
>
> * If you make your spark accessible to all GitHub users, all users will be able to access and edit the data stored in your spark. Make sure to delete any private or sensitive data from your app prior to making it visible to other users. **This option is not available for managed user accounts**

1. In the top-right corner of the page, click **Publish**.

2. By default, your spark is published as private and only accessible to you. To let other GitHub users access your app, in the **Visibility** section of the publish dropdown, choose **Organization** to make your spark accessible to all members of your selected organization, or <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-id-badge" aria-label="id-badge" role="img"><path d="M3 7.5a.5.5 0 0 1 .5-.5h2a.5.5 0 0 1 .5.5v3a.5.5 0 0 1-.5.5h-2a.5.5 0 0 1-.5-.5v-3Zm10 .25a.75.75 0 0 1-.75.75h-4.5a.75.75 0 0 1 0-1.5h4.5a.75.75 0 0 1 .75.75ZM10.25 11a.75.75 0 0 0 0-1.5h-2.5a.75.75 0 0 0 0 1.5h2.5Z"></path><path d="M7.25 0h1.5c.966 0 1.75.784 1.75 1.75V3h3.75c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 15H1.75A1.75 1.75 0 0 1 0 13.25v-8.5C0 3.784.784 3 1.75 3H5.5V1.75C5.5.784 6.284 0 7.25 0Zm3.232 4.5A1.75 1.75 0 0 1 8.75 6h-1.5a1.75 1.75 0 0 1-1.732-1.5H1.75a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25ZM7 1.75v2.5c0 .138.112.25.25.25h1.5A.25.25 0 0 0 9 4.25v-2.5a.25.25 0 0 0-.25-.25h-1.5a.25.25 0 0 0-.25.25Z"></path></svg> **All GitHub users**. This allows anyone with a GitHub account to access your spark.

   ![Screenshot of the GitHub Spark publication menu. The "All GitHub users" visibility option is outlined in orange.](/assets/images/help/copilot/spark-github-user-visibility.png)

3. If you make your spark visible to other users (i.e. any setting besides private), a "Data Access" option appears in the publication dropdown. This gives you the option to control who has access to edit the content and data in your spark.

   ![Screenshot of the GitHub Spark publication menu. The "Data Access" visibility option is outlined in orange.](/assets/images/help/copilot/spark-data-access.png)

   Choose **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-eye" aria-label="eye" role="img"><path d="M8 2c1.981 0 3.671.992 4.933 2.078 1.27 1.091 2.187 2.345 2.637 3.023a1.62 1.62 0 0 1 0 1.798c-.45.678-1.367 1.932-2.637 3.023C11.67 13.008 9.981 14 8 14c-1.981 0-3.671-.992-4.933-2.078C1.797 10.83.88 9.576.43 8.898a1.62 1.62 0 0 1 0-1.798c.45-.677 1.367-1.931 2.637-3.022C4.33 2.992 6.019 2 8 2ZM1.679 7.932a.12.12 0 0 0 0 .136c.411.622 1.241 1.75 2.366 2.717C5.176 11.758 6.527 12.5 8 12.5c1.473 0 2.825-.742 3.955-1.715 1.124-.967 1.954-2.096 2.366-2.717a.12.12 0 0 0 0-.136c-.412-.621-1.242-1.75-2.366-2.717C10.824 4.242 9.473 3.5 8 3.5c-1.473 0-2.825.742-3.955 1.715-1.124.967-1.954 2.096-2.366 2.717ZM8 10a2 2 0 1 1-.001-3.999A2 2 0 0 1 8 10Z"></path></svg> Read-Only** to let others view your app, without allowing them to create, edit or delete content or data. Choose **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="pencil" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> Write Access** to allow users to both edit and view content and data in your spark.

   For example, if you've created a family calendar app and you want to showcase the app, but you don't want users to be able to create, edit or delete events in the calendar yet, choose "Read-Only".

4. Click **View site** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link-external" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg> to see your deployed app, then copy and share your app's URL.

## Next steps

We just created a word search app, but Spark can make all kinds of web apps! Try [creating a new app](https://github.com/spark) on your own. If you need some inspiration, here are a few ideas to get you started:

* Try building a **news aggregator app** or an **intelligent recipe generator**.
* Build a **budget tracker** that lets you set a budget, takes in a list of expenses, and displays your total remaining budget. You can give each expense a category and date, then sort the expenses by the many different categories.

## Further reading

* [Responsible use of GitHub Spark](/en/copilot/responsible-use-of-github-copilot-features/responsible-use-of-github-spark)
* [GitHub Spark billing](/en/copilot/concepts/copilot-billing/about-billing-for-github-spark)