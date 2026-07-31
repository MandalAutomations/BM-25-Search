# Creating stacked pull requests

Create a stack of dependent pull requests using the gh stack extension in GitHub CLI or directly on GitHub.

> \[!NOTE] This feature is in public preview and subject to change.

Create stacked pull requests with the `gh stack` extension in GitHub CLI or on the GitHub website.

> \[!NOTE]
> Stacked pull requests require all branches to be in the same repository. Cross-fork stacks are not supported.

## Creating a stack with GitHub CLI

1. Initialize a stack. This creates and checks out the first branch on top of your trunk branch.

   ```shell copy
   gh stack init auth-layer
   ```

2. Write code for the first layer, then stage and commit your changes.

   ```shell copy
   git add .
   git commit -m "helpful-commit-message"
   ```

3. Add a branch for the next logical unit of work. The new branch is created on top of the current one.

   ```shell copy
   gh stack add BRANCH-NAME
   ```

4. Write code and commit on the new branch. Repeat for each additional layer.

5. Push all branches to the remote repository and create the stacked pull requests on GitHub.

   ```shell copy
   gh stack submit
   ```

   Each pull request is created with the correct base branch, so reviewers see only the diff for that layer, and the pull requests are automatically linked together as a stack.

## Creating a stack from the GitHub website

You can create a stack without the CLI by setting the base branch of each pull request to the branch below it.

1. Create the first pull request as you normally would. Typically your base would target `main`.

2. Create the next pull request and set its base branch to the first pull request's branch. Select the **Create stack** option to link the two pull requests together as a stack.

   Once created, the stack shows the pull requests linked together.

   * A stack icon <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-stack" aria-label="The stack icon" role="img"><path d="M7.122.392a1.75 1.75 0 0 1 1.756 0l5.003 2.902c.83.481.83 1.68 0 2.162L8.878 8.358a1.75 1.75 0 0 1-1.756 0L2.119 5.456a1.251 1.251 0 0 1 0-2.162ZM8.125 1.69a.248.248 0 0 0-.25 0l-4.63 2.685 4.63 2.685a.248.248 0 0 0 .25 0l4.63-2.685ZM1.601 7.789a.75.75 0 0 1 1.025-.273l5.249 3.044a.248.248 0 0 0 .25 0l5.249-3.044a.75.75 0 0 1 .752 1.298l-5.248 3.044a1.75 1.75 0 0 1-1.756 0L1.874 8.814A.75.75 0 0 1 1.6 7.789Zm0 3.5a.75.75 0 0 1 1.025-.273l5.249 3.044a.248.248 0 0 0 .25 0l5.249-3.044a.75.75 0 0 1 .752 1.298l-5.248 3.044a1.75 1.75 0 0 1-1.756 0l-5.248-3.044a.75.75 0 0 1-.273-1.025Z"></path></svg> at the top of the pull request shows a number indicating which layer you're viewing.
   * A stack map appears in the merge box. It shows every pull request in the stack and its status, and lets you navigate to any layer with one click.

3. Repeat for each additional pull request, targeting the branch of the pull request before it.

## Turning existing pull requests into a stack

If you already have open pull requests whose branches line up, where each pull request's base branch is the head branch of the pull request below it, GitHub recognizes the chain and shows a **recommendation banner** offering to turn them into a stack.

1. On any of the eligible pull requests, select the banner to open a dialog that previews the stack, listing each pull request in order from top to bottom.

2. Review the preview and confirm to link the pull requests together into a stack.

Once you confirm, the stack map appears in each pull request's header.

## Add to an existing stack from the GitHub website

To add a new pull request to a stack that already exists:

1. Open any pull request in the stack, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-stack" aria-label="The stack icon" role="img"><path d="M7.122.392a1.75 1.75 0 0 1 1.756 0l5.003 2.902c.83.481.83 1.68 0 2.162L8.878 8.358a1.75 1.75 0 0 1-1.756 0L2.119 5.456a1.251 1.251 0 0 1 0-2.162ZM8.125 1.69a.248.248 0 0 0-.25 0l-4.63 2.685 4.63 2.685a.248.248 0 0 0 .25 0l4.63-2.685ZM1.601 7.789a.75.75 0 0 1 1.025-.273l5.249 3.044a.248.248 0 0 0 .25 0l5.249-3.044a.75.75 0 0 1 .752 1.298l-5.248 3.044a1.75 1.75 0 0 1-1.756 0L1.874 8.814A.75.75 0 0 1 1.6 7.789Zm0 3.5a.75.75 0 0 1 1.025-.273l5.249 3.044a.248.248 0 0 0 .25 0l5.249-3.044a.75.75 0 0 1 .752 1.298l-5.248 3.044a1.75 1.75 0 0 1-1.756 0l-5.248-3.044a.75.75 0 0 1-.273-1.025Z"></path></svg>** in the header, and then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Add button" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add to stack**.

2. The base branch is automatically set to the head of the top pull request. Select the head branch for your new pull request and select **Create pull request**.

3. Select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Add button" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add to stack**, to create the pull request.

The new pull request is added to the top of the stack.

## Further reading

* [Stacked pull requests CLI commands](/en/pull-requests/reference/stacked-prs-cli-commands)