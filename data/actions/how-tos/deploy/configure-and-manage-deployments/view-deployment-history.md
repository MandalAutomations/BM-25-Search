# Viewing deployment history

View current and previous deployments for your repository.

## Viewing your repository's deployment history

On the deployments page of your repository, you can view the following aspects of your deployments.

* Currently active deployments across various environments
* Deployments filtered by environment
* Your repository's full deployment history
* Associated commits that triggered the deployment
* Connected GitHub Actions workflow logs
* The deployment URL (if one exists)
* The source pull request and branch related to each deployment
* Deployment statuses. For more information about deployment statuses, see [REST API endpoints for deployments](/en/rest/deployments/deployments#about-deployments).

By default, the deployments page shows currently active deployments from select environments and a timeline of the latest deployments for all environments.

1. In the right-hand sidebar of the home page of your repository, click **Deployments**.
2. Once you are on the "Deployments" page, you can view the following information about your deployment history.
   * **To view recent deployments for a specific environment**, in the "Environments" section of the left sidebar, click an environment.
   * **To pin an environment to the top of the deployment history list**, repository administrators can click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pin" aria-label="Pin environment" role="img"><path d="m11.294.984 3.722 3.722a1.75 1.75 0 0 1-.504 2.826l-1.327.613a3.089 3.089 0 0 0-1.707 2.084l-.584 2.454c-.317 1.332-1.972 1.8-2.94.832L5.75 11.311 1.78 15.28a.749.749 0 1 1-1.06-1.06l3.969-3.97-2.204-2.204c-.968-.968-.5-2.623.832-2.94l2.454-.584a3.08 3.08 0 0 0 2.084-1.707l.613-1.327a1.75 1.75 0 0 1 2.826-.504ZM6.283 9.723l2.732 2.731a.25.25 0 0 0 .42-.119l.584-2.454a4.586 4.586 0 0 1 2.537-3.098l1.328-.613a.25.25 0 0 0 .072-.404l-3.722-3.722a.25.25 0 0 0-.404.072l-.613 1.328a4.584 4.584 0 0 1-3.098 2.537l-2.454.584a.25.25 0 0 0-.119.42l2.731 2.732Z"></path></svg> to the right of the environment. You can pin up to ten environments.
   * **To view the commit that triggered a deployment**, in the deployment history list, click the commit message for the deployment you want to view.
     > \[!NOTE]Deployments from commits that originate from a fork outside of the repository will not show links to the source pull request and branch related to each deployment. For more information about forks, see [About forks](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks).
   * **To view the URL for a deployment**, to the right of the commit message in the deployment history list, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="Navigate to deployment URL" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg>.
   * **To navigate to the workflow run logs associated with a deployment**, to the right of the commit message in the deployment history list, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="View logs" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **View logs**.
3. Optionally, to filter the deployment history list, create a filter.
   1. Click on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-filter" aria-label="filter" role="img"><path d="M.75 3h14.5a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1 0-1.5ZM3 7.75A.75.75 0 0 1 3.75 7h8.5a.75.75 0 0 1 0 1.5h-8.5A.75.75 0 0 1 3 7.75Zm3 4a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 0 1.5h-2.5a.75.75 0 0 1-.75-.75Z"></path></svg> Filter** button.
   2. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add a filter**.
   3. Choose a qualifier you would like to filter the deployment history by.
   4. Depending on the qualifier you chose, fill out information in the "Operator" and "Value" columns.
   5. Optionally, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Add a filter** to add another filter.
   6. Click **Apply**.