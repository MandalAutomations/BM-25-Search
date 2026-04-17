# Managing labels

You can classify issues and pull requests by creating, editing, applying, and deleting labels.

## About labels

You can manage your work on GitHub by creating labels to categorize issues, pull requests, and discussions. You can apply labels in the repository the label was created in. Once a label exists, you can use the label on any issue, pull request, or discussion within that repository. Addition, modification, or deletion of labels in one repository has no effect on labels belonging to other repositories.

## About default labels

GitHub provides default labels in every new repository. You can use these default labels to help create a standard workflow in a repository.

| Label              | Description                                                                 |
| ------------------ | --------------------------------------------------------------------------- |
| `bug`              | Indicates an unexpected problem or unintended behavior                      |
| `documentation`    | Indicates a need for improvements or additions to documentation             |
| `duplicate`        | Indicates similar issues, pull requests, or discussions                     |
| `enhancement`      | Indicates new feature requests                                              |
| `good first issue` | Indicates a good issue for first-time contributors                          |
| `help wanted`      | Indicates that a maintainer wants help on an issue or pull request          |
| `invalid`          | Indicates that an issue, pull request, or discussion is no longer relevant  |
| `question`         | Indicates that an issue, pull request, or discussion needs more information |
| `wontfix`          | Indicates that work won't continue on an issue, pull request, or discussion |

Default labels are included in every new repository when the repository is created, but you can edit or delete the labels later.

Issues with the `good first issue` label are used to populate the repository's `contribute` page. For an example of a `contribute` page, see [github/docs/contribute](https://github.com/github/docs/contribute).

Organization owners can customize the default labels for repositories in their organization. For more information, see [Managing default labels for repositories in your organization](/en/organizations/managing-organization-settings/managing-default-labels-for-repositories-in-your-organization).

## Creating a label

Anyone with write access to a repository can create a label.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues** or **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, the "Issues" and "Pull requests" tabs are outlined in orange.](/assets/images/help/repository/repo-settings-issues-pull-requests-global-nav-update.png)
3. Above the list of issues or pull requests, click **Labels**.

   ![Screenshot of the list of issues for a repository. Above the list, a button, labeled with a label icon and "Labels", is outlined in dark orange.](/assets/images/help/issues/issues-labels-button.png)
4. To the right of the search field, click **New label**.
5. Under "Label name", type a name for your label.
6. Under "Description", type a description to help others understand and use your label.
7. Optionally, to customize the color of your label, edit the hexadecimal number, or, for another random selection, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-sync" aria-label="Get a new color" role="img"><path d="M1.705 8.005a.75.75 0 0 1 .834.656 5.5 5.5 0 0 0 9.592 2.97l-1.204-1.204a.25.25 0 0 1 .177-.427h3.646a.25.25 0 0 1 .25.25v3.646a.25.25 0 0 1-.427.177l-1.38-1.38A7.002 7.002 0 0 1 1.05 8.84a.75.75 0 0 1 .656-.834ZM8 2.5a5.487 5.487 0 0 0-4.131 1.869l1.204 1.204A.25.25 0 0 1 4.896 6H1.25A.25.25 0 0 1 1 5.75V2.104a.25.25 0 0 1 .427-.177l1.38 1.38A7.002 7.002 0 0 1 14.95 7.16a.75.75 0 0 1-1.49.178A5.5 5.5 0 0 0 8 2.5Z"></path></svg>.
8. To save the new label, click **Create label**.

## Applying a label

Anyone with triage access to a repository can apply and dismiss labels.

1. Navigate to the issue, pull request, or discussion.
2. In the right sidebar, click **Labels**, then click a label.

## Editing a label

Anyone with write access to a repository can edit existing labels.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues** or **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, the "Issues" and "Pull requests" tabs are outlined in orange.](/assets/images/help/repository/repo-settings-issues-pull-requests-global-nav-update.png)
3. Above the list of issues or pull requests, click **Labels**.

   ![Screenshot of the list of issues for a repository. Above the list, a button, labeled with a label icon and "Labels", is outlined in dark orange.](/assets/images/help/issues/issues-labels-button.png)
4. In the labels list, to the right of the label you want to edit, click **Edit**.
5. Under "Label name", type a name for your label.
6. Under "Description", type a description to help others understand and use your label.
7. Optionally, to customize the color of your label, edit the hexadecimal number, or, for another random selection, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-sync" aria-label="Get a new color" role="img"><path d="M1.705 8.005a.75.75 0 0 1 .834.656 5.5 5.5 0 0 0 9.592 2.97l-1.204-1.204a.25.25 0 0 1 .177-.427h3.646a.25.25 0 0 1 .25.25v3.646a.25.25 0 0 1-.427.177l-1.38-1.38A7.002 7.002 0 0 1 1.05 8.84a.75.75 0 0 1 .656-.834ZM8 2.5a5.487 5.487 0 0 0-4.131 1.869l1.204 1.204A.25.25 0 0 1 4.896 6H1.25A.25.25 0 0 1 1 5.75V2.104a.25.25 0 0 1 .427-.177l1.38 1.38A7.002 7.002 0 0 1 14.95 7.16a.75.75 0 0 1-1.49.178A5.5 5.5 0 0 0 8 2.5Z"></path></svg>.
8. Click **Save changes**.

## Deleting a label

Anyone with write access to a repository can delete existing labels.

Deleting a label will remove the label from issues and pull requests.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues** or **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, the "Issues" and "Pull requests" tabs are outlined in orange.](/assets/images/help/repository/repo-settings-issues-pull-requests-global-nav-update.png)
3. Above the list of issues or pull requests, click **Labels**.

   ![Screenshot of the list of issues for a repository. Above the list, a button, labeled with a label icon and "Labels", is outlined in dark orange.](/assets/images/help/issues/issues-labels-button.png)
4. In the labels list, to the right of the label you want to delete, click **Delete**.

## Further reading

* [Filtering and searching issues and pull requests](/en/issues/tracking-your-work-with-issues/filtering-and-searching-issues-and-pull-requests)
* [Managing default labels for repositories in your organization](/en/organizations/managing-organization-settings/managing-default-labels-for-repositories-in-your-organization)
* [Encouraging helpful contributions to your project with labels](/en/communities/setting-up-your-project-for-healthy-contributions/encouraging-helpful-contributions-to-your-project-with-labels)
* [Basic writing and formatting syntax](/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#using-emoji)