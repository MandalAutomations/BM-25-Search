# REST API endpoints for rules

Use the REST API to manage rulesets for an enterprise. Rulesets control how people can interact with repositories and code.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Create an enterprise repository ruleset

```
POST /enterprises/{enterprise}/rulesets
```

Create a repository ruleset for an enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`name`** (string) (required)
  The name of the ruleset.

- **`target`** (string)
  The target of the ruleset
  Default: `branch`
  Can be one of: `branch`, `tag`, `push`, `repository`

- **`enforcement`** (string) (required)
  The enforcement level of the ruleset. evaluate allows admins to test rules before enforcing them. Admins can view insights on the Rule Insights page. evaluate is not available for the repository target.
  Can be one of: `disabled`, `active`, `evaluate`

- **`bypass_actors`** (array of objects)
  The actors that can bypass the rules in this ruleset
  - **`actor_id`** (integer or null)
    The ID of the actor that can bypass a ruleset. Required for Integration, RepositoryRole, and Team actor types. If actor_type is OrganizationAdmin, actor_id is ignored. If actor_type is DeployKey, this should be null. If actor_type is EnterpriseOwner, actor_id is ignored. OrganizationAdmin and EnterpriseOwner are not applicable for personal repositories.
  - **`actor_type`** (string) (required)
    The type of actor that can bypass a ruleset
    Can be one of: `Integration`, `OrganizationAdmin`, `RepositoryRole`, `Team`, `DeployKey`, `EnterpriseOwner`
  - **`bypass_mode`** (string)
    When the specified actor can bypass the ruleset. pull_request means that an actor can only bypass rules on pull requests. pull_request is not applicable for the DeployKey actor type. Also, pull_request is only applicable to branch rulesets. When bypass_mode is exempt, rules will not be run for that actor and a bypass audit entry will not be created.
    Default: `always`
    Can be one of: `always`, `pull_request`, `exempt`

- **`conditions`** (object)
  Conditions for an enterprise ruleset.
The conditions object supports either of the following combinations: - organization_id and repository_name - organization_id and repository_property - organization_name and repository_name - organization_name and repository_property - organization_property and repository_name - organization_property and repository_property
For branch and tag rulesets, the conditions object should also contain the ref_name property.
  - **`organization_name_and_repository_name`** (object)
    Conditions to target organizations by name and all repositories
    - **`organization_name`** (object) (required)
      - **`include`** (array of strings)
        Array of organization names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all organizations and ~EMUS to target all enterprise managed user accounts.
      - **`exclude`** (array of strings)
        Array of organization names or patterns to exclude. The condition will not pass if any of these patterns match.
    - **`repository_name`** (object) (required)
      - **`include`** (array of strings)
        Array of repository names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all repositories.
      - **`exclude`** (array of strings)
        Array of repository names or patterns to exclude. The condition will not pass if any of these patterns match.
      - **`protected`** (boolean)
        Whether renaming of target repositories is prevented.
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_name_and_repository_property`** (object)
    Conditions to target organizations by name and repositories by property
    - **`organization_name`** (object) (required)
      - **`include`** (array of strings)
        Array of organization names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all organizations and ~EMUS to target all enterprise managed user accounts.
      - **`exclude`** (array of strings)
        Array of organization names or patterns to exclude. The condition will not pass if any of these patterns match.
    - **`repository_property`** (object) (required)
      - **`include`** (array of objects)
        The repository properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
      - **`exclude`** (array of objects)
        The repository properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_id_and_repository_name`** (object)
    Conditions to target organizations by id and all repositories
    - **`organization_id`** (object) (required)
      - **`organization_ids`** (array of integers)
        The organization IDs that the ruleset applies to. One of these IDs must match for the condition to pass.
    - **`repository_name`** (object) (required)
      - **`include`** (array of strings)
        Array of repository names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all repositories.
      - **`exclude`** (array of strings)
        Array of repository names or patterns to exclude. The condition will not pass if any of these patterns match.
      - **`protected`** (boolean)
        Whether renaming of target repositories is prevented.
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_id_and_repository_property`** (object)
    Conditions to target organization by id and repositories by property
    - **`organization_id`** (object) (required)
      - **`organization_ids`** (array of integers)
        The organization IDs that the ruleset applies to. One of these IDs must match for the condition to pass.
    - **`repository_property`** (object) (required)
      - **`include`** (array of objects)
        The repository properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
      - **`exclude`** (array of objects)
        The repository properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_property_and_repository_name`** (object)
    Conditions to target organizations by property and all repositories
    - **`organization_property`** (object) (required)
      - **`include`** (array of objects)
        The organization properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the organization property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the organization property
      - **`exclude`** (array of objects)
        The organization properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the organization property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the organization property
    - **`repository_name`** (object) (required)
      - **`include`** (array of strings)
        Array of repository names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all repositories.
      - **`exclude`** (array of strings)
        Array of repository names or patterns to exclude. The condition will not pass if any of these patterns match.
      - **`protected`** (boolean)
        Whether renaming of target repositories is prevented.
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_property_and_repository_property`** (object)
    Conditions to target organizations by property and repositories by property
    - **`organization_property`** (object) (required)
      - **`include`** (array of objects)
        The organization properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the organization property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the organization property
      - **`exclude`** (array of objects)
        The organization properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the organization property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the organization property
    - **`repository_property`** (object) (required)
      - **`include`** (array of objects)
        The repository properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
      - **`exclude`** (array of objects)
        The repository properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.

- **`rules`** (array of objects)
  An array of rules within the ruleset.
  - **`creation`** (object)
    Only allow users with bypass permission to create matching refs.
    - **`type`** (string) (required)
      Can be one of: `creation`
  - **`update`** (object)
    Only allow users with bypass permission to update matching refs.
    - **`type`** (string) (required)
      Can be one of: `update`
    - **`parameters`** (object)
      - **`update_allows_fetch_and_merge`** (boolean) (required)
        Branch can pull changes from its upstream repository
  - **`deletion`** (object)
    Only allow users with bypass permissions to delete matching refs.
    - **`type`** (string) (required)
      Can be one of: `deletion`
  - **`required_linear_history`** (object)
    Prevent merge commits from being pushed to matching refs.
    - **`type`** (string) (required)
      Can be one of: `required_linear_history`
  - **`required_deployments`** (object)
    Choose which environments must be successfully deployed to before refs can be pushed into a ref that matches this rule.
    - **`type`** (string) (required)
      Can be one of: `required_deployments`
    - **`parameters`** (object)
      - **`required_deployment_environments`** (array of strings) (required)
        The environments that must be successfully deployed to before branches can be merged.
  - **`required_signatures`** (object)
    Commits pushed to matching refs must have verified signatures.
    - **`type`** (string) (required)
      Can be one of: `required_signatures`
  - **`pull_request`** (object)
    Require all commits be made to a non-target branch and submitted via a pull request before they can be merged.
    - **`type`** (string) (required)
      Can be one of: `pull_request`
    - **`parameters`** (object)
      - **`allowed_merge_methods`** (array of strings)
        Array of allowed merge methods. Allowed values include merge, squash, and rebase. At least one option must be enabled.
Supported values are: merge, squash, rebase
      - **`dismiss_stale_reviews_on_push`** (boolean) (required)
        New, reviewable commits pushed will dismiss previous pull request review approvals.
      - **`require_code_owner_review`** (boolean) (required)
        Require an approving review in pull requests that modify files that have a designated code owner.
      - **`require_last_push_approval`** (boolean) (required)
        Whether the most recent reviewable push must be approved by someone other than the person who pushed it.
      - **`required_approving_review_count`** (integer) (required)
        The number of approving reviews that are required before a pull request can be merged.
      - **`required_review_thread_resolution`** (boolean) (required)
        All conversations on code must be resolved before a pull request can be merged.
      - **`required_reviewers`** (array of objects)
        Note

required_reviewers is in beta and subject to change.

A collection of reviewers and associated file patterns. Each reviewer has a list of file patterns which determine the files that reviewer is required to review.
        - **`file_patterns`** (array of strings) (required)
          Array of file patterns. Pull requests which change matching files must be approved by the specified team. File patterns use fnmatch syntax.
        - **`minimum_approvals`** (integer) (required)
          Minimum number of approvals required from the specified team. If set to zero, the team will be added to the pull request but approval is optional.
        - **`reviewer`** (object) (required)
          A required reviewing team
          - **`id`** (integer) (required)
            ID of the reviewer which must review changes to matching files.
          - **`type`** (string) (required)
            The type of the reviewer
            Can be one of: `Team`
  - **`required_status_checks`** (object)
    Choose which status checks must pass before the ref is updated. When enabled, commits must first be pushed to another ref where the checks pass.
    - **`type`** (string) (required)
      Can be one of: `required_status_checks`
    - **`parameters`** (object)
      - **`do_not_enforce_on_create`** (boolean)
        Allow repositories and branches to be created if a check would otherwise prohibit it.
      - **`required_status_checks`** (array of objects) (required)
        Status checks that are required.
        - **`context`** (string) (required)
          The status check context name that must be present on the commit.
        - **`integration_id`** (integer)
          The optional integration ID that this status check must originate from.
      - **`strict_required_status_checks_policy`** (boolean) (required)
        Whether pull requests targeting a matching branch must be tested with the latest code. This setting will not take effect unless at least one status check is enabled.
  - **`non_fast_forward`** (object)
    Prevent users with push access from force pushing to refs.
    - **`type`** (string) (required)
      Can be one of: `non_fast_forward`
  - **`commit_message_pattern`** (object)
    Parameters to be used for the commit_message_pattern rule
    - **`type`** (string) (required)
      Can be one of: `commit_message_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`commit_author_email_pattern`** (object)
    Parameters to be used for the commit_author_email_pattern rule
    - **`type`** (string) (required)
      Can be one of: `commit_author_email_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`committer_email_pattern`** (object)
    Parameters to be used for the committer_email_pattern rule
    - **`type`** (string) (required)
      Can be one of: `committer_email_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`branch_name_pattern`** (object)
    Parameters to be used for the branch_name_pattern rule
    - **`type`** (string) (required)
      Can be one of: `branch_name_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`tag_name_pattern`** (object)
    Parameters to be used for the tag_name_pattern rule
    - **`type`** (string) (required)
      Can be one of: `tag_name_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`file_path_restriction`** (object)
    Prevent commits that include changes in specified file and folder paths from being pushed to the commit graph. This includes absolute paths that contain file names.
    - **`type`** (string) (required)
      Can be one of: `file_path_restriction`
    - **`parameters`** (object)
      - **`restricted_file_paths`** (array of strings) (required)
        The file paths that are restricted from being pushed to the commit graph.
  - **`max_file_path_length`** (object)
    Prevent commits that include file paths that exceed the specified character limit from being pushed to the commit graph.
    - **`type`** (string) (required)
      Can be one of: `max_file_path_length`
    - **`parameters`** (object)
      - **`max_file_path_length`** (integer) (required)
        The maximum amount of characters allowed in file paths.
  - **`file_extension_restriction`** (object)
    Prevent commits that include files with specified file extensions from being pushed to the commit graph.
    - **`type`** (string) (required)
      Can be one of: `file_extension_restriction`
    - **`parameters`** (object)
      - **`restricted_file_extensions`** (array of strings) (required)
        The file extensions that are restricted from being pushed to the commit graph.
  - **`max_file_size`** (object)
    Prevent commits with individual files that exceed the specified limit from being pushed to the commit graph.
    - **`type`** (string) (required)
      Can be one of: `max_file_size`
    - **`parameters`** (object)
      - **`max_file_size`** (integer) (required)
        The maximum file size allowed in megabytes. This limit does not apply to Git Large File Storage (Git LFS).
  - **`workflows`** (object)
    Require all changes made to a targeted branch to pass the specified workflows before they can be merged.
    - **`type`** (string) (required)
      Can be one of: `workflows`
    - **`parameters`** (object)
      - **`do_not_enforce_on_create`** (boolean)
        Allow repositories and branches to be created if a check would otherwise prohibit it.
      - **`workflows`** (array of objects) (required)
        Workflows that must pass for this rule to pass.
        - **`path`** (string) (required)
          The path to the workflow file
        - **`ref`** (string)
          The ref (branch or tag) of the workflow file to use
        - **`repository_id`** (integer) (required)
          The ID of the repository where the workflow is defined
        - **`sha`** (string)
          The commit SHA of the workflow file to use
  - **`code_scanning`** (object)
    Choose which tools must provide code scanning results before the reference is updated. When configured, code scanning must be enabled and have results for both the commit and the reference being updated.
    - **`type`** (string) (required)
      Can be one of: `code_scanning`
    - **`parameters`** (object)
      - **`code_scanning_tools`** (array of objects) (required)
        Tools that must provide code scanning results for this rule to pass.
        - **`alerts_threshold`** (string) (required)
          The severity level at which code scanning results that raise alerts block a reference update. For more information on alert severity levels, see "About code scanning alerts."
          Can be one of: `none`, `errors`, `errors_and_warnings`, `all`
        - **`security_alerts_threshold`** (string) (required)
          The severity level at which code scanning results that raise security alerts block a reference update. For more information on security severity levels, see "About code scanning alerts."
          Can be one of: `none`, `critical`, `high_or_higher`, `medium_or_higher`, `all`
        - **`tool`** (string) (required)
          The name of a code scanning tool
  - **`copilot_code_review`** (object)
    Request Copilot code review for new pull requests automatically if the author has access to Copilot code review and their premium requests quota has not reached the limit.
    - **`type`** (string) (required)
      Can be one of: `copilot_code_review`
    - **`parameters`** (object)
      - **`review_draft_pull_requests`** (boolean)
        Copilot automatically reviews draft pull requests before they are marked as ready for review.
      - **`review_on_push`** (boolean)
        Copilot automatically reviews each new push to the pull request.





### HTTP response status codes


- **201** - Created


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/rulesets \
  -d '{
  "name": "super cool ruleset",
  "target": "branch",
  "enforcement": "active",
  "bypass_actors": [
    {
      "actor_id": 234,
      "actor_type": "Team",
      "bypass_mode": "always"
    }
  ],
  "conditions": {
    "org_name": {
      "include": [
        "important_org"
      ],
      "exclude": [
        "unimportant_org"
      ]
    }
  },
  "rules": [
    {
      "type": "deletion"
    }
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `name`: required, string
* `target`: string, enum: `branch`, `tag`, `push`, `repository`
* `source_type`: string, enum: `Repository`, `Organization`, `Enterprise`
* `source`: required, string
* `enforcement`: required, string, enum: `disabled`, `active`, `evaluate`
* `bypass_actors`: array of `Repository Ruleset Bypass Actor`:
  * `actor_id`: integer or null
  * `actor_type`: required, string, enum: `Integration`, `OrganizationAdmin`, `RepositoryRole`, `Team`, `DeployKey`, `EnterpriseOwner`
  * `bypass_mode`: string, enum: `always`, `pull_request`, `exempt`, default: `"always"`
* `current_user_can_bypass`: string, enum: `always`, `pull_requests_only`, `never`, `exempt`
* `node_id`: string
* `_links`: object:
  * `self`: object:
    * `href`: string
  * `html`: object or null:
    * `href`: string
* `conditions`: any of:
  * **Repository ruleset conditions for ref names**
    * `ref_name`: object:
      * `include`: array of string
      * `exclude`: array of string
  * **Organization ruleset conditions**
* `rules`: array of object
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time





## Get an enterprise repository ruleset

```
GET /enterprises/{enterprise}/rulesets/{ruleset_id}
```

Get a repository ruleset for an enterprise.
Note: To prevent leaking sensitive information, the bypass_actors property is only returned if the user
making the API request has write access to the ruleset.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`ruleset_id`** (integer) (required)
  The ID of the ruleset.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/rulesets/RULESET_ID
```

**Response schema (Status: 200):**

Same response schema as [Create an enterprise repository ruleset](#create-an-enterprise-repository-ruleset).





## Update an enterprise repository ruleset

```
PUT /enterprises/{enterprise}/rulesets/{ruleset_id}
```

Update a ruleset for an enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`ruleset_id`** (integer) (required)
  The ID of the ruleset.




#### Body parameters

- **`name`** (string)
  The name of the ruleset.

- **`target`** (string)
  The target of the ruleset
  Can be one of: `branch`, `tag`, `push`, `repository`

- **`enforcement`** (string)
  The enforcement level of the ruleset. evaluate allows admins to test rules before enforcing them. Admins can view insights on the Rule Insights page. evaluate is not available for the repository target.
  Can be one of: `disabled`, `active`, `evaluate`

- **`bypass_actors`** (array of objects)
  The actors that can bypass the rules in this ruleset
  - **`actor_id`** (integer or null)
    The ID of the actor that can bypass a ruleset. Required for Integration, RepositoryRole, and Team actor types. If actor_type is OrganizationAdmin, actor_id is ignored. If actor_type is DeployKey, this should be null. If actor_type is EnterpriseOwner, actor_id is ignored. OrganizationAdmin and EnterpriseOwner are not applicable for personal repositories.
  - **`actor_type`** (string) (required)
    The type of actor that can bypass a ruleset
    Can be one of: `Integration`, `OrganizationAdmin`, `RepositoryRole`, `Team`, `DeployKey`, `EnterpriseOwner`
  - **`bypass_mode`** (string)
    When the specified actor can bypass the ruleset. pull_request means that an actor can only bypass rules on pull requests. pull_request is not applicable for the DeployKey actor type. Also, pull_request is only applicable to branch rulesets. When bypass_mode is exempt, rules will not be run for that actor and a bypass audit entry will not be created.
    Default: `always`
    Can be one of: `always`, `pull_request`, `exempt`

- **`conditions`** (object)
  Conditions for an enterprise ruleset.
The conditions object supports either of the following combinations: - organization_id and repository_name - organization_id and repository_property - organization_name and repository_name - organization_name and repository_property - organization_property and repository_name - organization_property and repository_property
For branch and tag rulesets, the conditions object should also contain the ref_name property.
  - **`organization_name_and_repository_name`** (object)
    Conditions to target organizations by name and all repositories
    - **`organization_name`** (object) (required)
      - **`include`** (array of strings)
        Array of organization names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all organizations and ~EMUS to target all enterprise managed user accounts.
      - **`exclude`** (array of strings)
        Array of organization names or patterns to exclude. The condition will not pass if any of these patterns match.
    - **`repository_name`** (object) (required)
      - **`include`** (array of strings)
        Array of repository names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all repositories.
      - **`exclude`** (array of strings)
        Array of repository names or patterns to exclude. The condition will not pass if any of these patterns match.
      - **`protected`** (boolean)
        Whether renaming of target repositories is prevented.
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_name_and_repository_property`** (object)
    Conditions to target organizations by name and repositories by property
    - **`organization_name`** (object) (required)
      - **`include`** (array of strings)
        Array of organization names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all organizations and ~EMUS to target all enterprise managed user accounts.
      - **`exclude`** (array of strings)
        Array of organization names or patterns to exclude. The condition will not pass if any of these patterns match.
    - **`repository_property`** (object) (required)
      - **`include`** (array of objects)
        The repository properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
      - **`exclude`** (array of objects)
        The repository properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_id_and_repository_name`** (object)
    Conditions to target organizations by id and all repositories
    - **`organization_id`** (object) (required)
      - **`organization_ids`** (array of integers)
        The organization IDs that the ruleset applies to. One of these IDs must match for the condition to pass.
    - **`repository_name`** (object) (required)
      - **`include`** (array of strings)
        Array of repository names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all repositories.
      - **`exclude`** (array of strings)
        Array of repository names or patterns to exclude. The condition will not pass if any of these patterns match.
      - **`protected`** (boolean)
        Whether renaming of target repositories is prevented.
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_id_and_repository_property`** (object)
    Conditions to target organization by id and repositories by property
    - **`organization_id`** (object) (required)
      - **`organization_ids`** (array of integers)
        The organization IDs that the ruleset applies to. One of these IDs must match for the condition to pass.
    - **`repository_property`** (object) (required)
      - **`include`** (array of objects)
        The repository properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
      - **`exclude`** (array of objects)
        The repository properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_property_and_repository_name`** (object)
    Conditions to target organizations by property and all repositories
    - **`organization_property`** (object) (required)
      - **`include`** (array of objects)
        The organization properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the organization property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the organization property
      - **`exclude`** (array of objects)
        The organization properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the organization property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the organization property
    - **`repository_name`** (object) (required)
      - **`include`** (array of strings)
        Array of repository names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all repositories.
      - **`exclude`** (array of strings)
        Array of repository names or patterns to exclude. The condition will not pass if any of these patterns match.
      - **`protected`** (boolean)
        Whether renaming of target repositories is prevented.
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
  - **`organization_property_and_repository_property`** (object)
    Conditions to target organizations by property and repositories by property
    - **`organization_property`** (object) (required)
      - **`include`** (array of objects)
        The organization properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the organization property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the organization property
      - **`exclude`** (array of objects)
        The organization properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the organization property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the organization property
    - **`repository_property`** (object) (required)
      - **`include`** (array of objects)
        The repository properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
      - **`exclude`** (array of objects)
        The repository properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
    - **`ref_name`** (object)
      - **`include`** (array of strings)
        Array of ref names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~DEFAULT_BRANCH to include the default branch or ~ALL to include all branches.
      - **`exclude`** (array of strings)
        Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.

- **`rules`** (array of objects)
  An array of rules within the ruleset.
  - **`creation`** (object)
    Only allow users with bypass permission to create matching refs.
    - **`type`** (string) (required)
      Can be one of: `creation`
  - **`update`** (object)
    Only allow users with bypass permission to update matching refs.
    - **`type`** (string) (required)
      Can be one of: `update`
    - **`parameters`** (object)
      - **`update_allows_fetch_and_merge`** (boolean) (required)
        Branch can pull changes from its upstream repository
  - **`deletion`** (object)
    Only allow users with bypass permissions to delete matching refs.
    - **`type`** (string) (required)
      Can be one of: `deletion`
  - **`required_linear_history`** (object)
    Prevent merge commits from being pushed to matching refs.
    - **`type`** (string) (required)
      Can be one of: `required_linear_history`
  - **`required_deployments`** (object)
    Choose which environments must be successfully deployed to before refs can be pushed into a ref that matches this rule.
    - **`type`** (string) (required)
      Can be one of: `required_deployments`
    - **`parameters`** (object)
      - **`required_deployment_environments`** (array of strings) (required)
        The environments that must be successfully deployed to before branches can be merged.
  - **`required_signatures`** (object)
    Commits pushed to matching refs must have verified signatures.
    - **`type`** (string) (required)
      Can be one of: `required_signatures`
  - **`pull_request`** (object)
    Require all commits be made to a non-target branch and submitted via a pull request before they can be merged.
    - **`type`** (string) (required)
      Can be one of: `pull_request`
    - **`parameters`** (object)
      - **`allowed_merge_methods`** (array of strings)
        Array of allowed merge methods. Allowed values include merge, squash, and rebase. At least one option must be enabled.
Supported values are: merge, squash, rebase
      - **`dismiss_stale_reviews_on_push`** (boolean) (required)
        New, reviewable commits pushed will dismiss previous pull request review approvals.
      - **`require_code_owner_review`** (boolean) (required)
        Require an approving review in pull requests that modify files that have a designated code owner.
      - **`require_last_push_approval`** (boolean) (required)
        Whether the most recent reviewable push must be approved by someone other than the person who pushed it.
      - **`required_approving_review_count`** (integer) (required)
        The number of approving reviews that are required before a pull request can be merged.
      - **`required_review_thread_resolution`** (boolean) (required)
        All conversations on code must be resolved before a pull request can be merged.
      - **`required_reviewers`** (array of objects)
        Note

required_reviewers is in beta and subject to change.

A collection of reviewers and associated file patterns. Each reviewer has a list of file patterns which determine the files that reviewer is required to review.
        - **`file_patterns`** (array of strings) (required)
          Array of file patterns. Pull requests which change matching files must be approved by the specified team. File patterns use fnmatch syntax.
        - **`minimum_approvals`** (integer) (required)
          Minimum number of approvals required from the specified team. If set to zero, the team will be added to the pull request but approval is optional.
        - **`reviewer`** (object) (required)
          A required reviewing team
          - **`id`** (integer) (required)
            ID of the reviewer which must review changes to matching files.
          - **`type`** (string) (required)
            The type of the reviewer
            Can be one of: `Team`
  - **`required_status_checks`** (object)
    Choose which status checks must pass before the ref is updated. When enabled, commits must first be pushed to another ref where the checks pass.
    - **`type`** (string) (required)
      Can be one of: `required_status_checks`
    - **`parameters`** (object)
      - **`do_not_enforce_on_create`** (boolean)
        Allow repositories and branches to be created if a check would otherwise prohibit it.
      - **`required_status_checks`** (array of objects) (required)
        Status checks that are required.
        - **`context`** (string) (required)
          The status check context name that must be present on the commit.
        - **`integration_id`** (integer)
          The optional integration ID that this status check must originate from.
      - **`strict_required_status_checks_policy`** (boolean) (required)
        Whether pull requests targeting a matching branch must be tested with the latest code. This setting will not take effect unless at least one status check is enabled.
  - **`non_fast_forward`** (object)
    Prevent users with push access from force pushing to refs.
    - **`type`** (string) (required)
      Can be one of: `non_fast_forward`
  - **`commit_message_pattern`** (object)
    Parameters to be used for the commit_message_pattern rule
    - **`type`** (string) (required)
      Can be one of: `commit_message_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`commit_author_email_pattern`** (object)
    Parameters to be used for the commit_author_email_pattern rule
    - **`type`** (string) (required)
      Can be one of: `commit_author_email_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`committer_email_pattern`** (object)
    Parameters to be used for the committer_email_pattern rule
    - **`type`** (string) (required)
      Can be one of: `committer_email_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`branch_name_pattern`** (object)
    Parameters to be used for the branch_name_pattern rule
    - **`type`** (string) (required)
      Can be one of: `branch_name_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`tag_name_pattern`** (object)
    Parameters to be used for the tag_name_pattern rule
    - **`type`** (string) (required)
      Can be one of: `tag_name_pattern`
    - **`parameters`** (object)
      - **`name`** (string)
        How this rule appears when configuring it.
      - **`negate`** (boolean)
        If true, the rule will fail if the pattern matches.
      - **`operator`** (string) (required)
        The operator to use for matching.
        Can be one of: `starts_with`, `ends_with`, `contains`, `regex`
      - **`pattern`** (string) (required)
        The pattern to match with.
  - **`file_path_restriction`** (object)
    Prevent commits that include changes in specified file and folder paths from being pushed to the commit graph. This includes absolute paths that contain file names.
    - **`type`** (string) (required)
      Can be one of: `file_path_restriction`
    - **`parameters`** (object)
      - **`restricted_file_paths`** (array of strings) (required)
        The file paths that are restricted from being pushed to the commit graph.
  - **`max_file_path_length`** (object)
    Prevent commits that include file paths that exceed the specified character limit from being pushed to the commit graph.
    - **`type`** (string) (required)
      Can be one of: `max_file_path_length`
    - **`parameters`** (object)
      - **`max_file_path_length`** (integer) (required)
        The maximum amount of characters allowed in file paths.
  - **`file_extension_restriction`** (object)
    Prevent commits that include files with specified file extensions from being pushed to the commit graph.
    - **`type`** (string) (required)
      Can be one of: `file_extension_restriction`
    - **`parameters`** (object)
      - **`restricted_file_extensions`** (array of strings) (required)
        The file extensions that are restricted from being pushed to the commit graph.
  - **`max_file_size`** (object)
    Prevent commits with individual files that exceed the specified limit from being pushed to the commit graph.
    - **`type`** (string) (required)
      Can be one of: `max_file_size`
    - **`parameters`** (object)
      - **`max_file_size`** (integer) (required)
        The maximum file size allowed in megabytes. This limit does not apply to Git Large File Storage (Git LFS).
  - **`workflows`** (object)
    Require all changes made to a targeted branch to pass the specified workflows before they can be merged.
    - **`type`** (string) (required)
      Can be one of: `workflows`
    - **`parameters`** (object)
      - **`do_not_enforce_on_create`** (boolean)
        Allow repositories and branches to be created if a check would otherwise prohibit it.
      - **`workflows`** (array of objects) (required)
        Workflows that must pass for this rule to pass.
        - **`path`** (string) (required)
          The path to the workflow file
        - **`ref`** (string)
          The ref (branch or tag) of the workflow file to use
        - **`repository_id`** (integer) (required)
          The ID of the repository where the workflow is defined
        - **`sha`** (string)
          The commit SHA of the workflow file to use
  - **`code_scanning`** (object)
    Choose which tools must provide code scanning results before the reference is updated. When configured, code scanning must be enabled and have results for both the commit and the reference being updated.
    - **`type`** (string) (required)
      Can be one of: `code_scanning`
    - **`parameters`** (object)
      - **`code_scanning_tools`** (array of objects) (required)
        Tools that must provide code scanning results for this rule to pass.
        - **`alerts_threshold`** (string) (required)
          The severity level at which code scanning results that raise alerts block a reference update. For more information on alert severity levels, see "About code scanning alerts."
          Can be one of: `none`, `errors`, `errors_and_warnings`, `all`
        - **`security_alerts_threshold`** (string) (required)
          The severity level at which code scanning results that raise security alerts block a reference update. For more information on security severity levels, see "About code scanning alerts."
          Can be one of: `none`, `critical`, `high_or_higher`, `medium_or_higher`, `all`
        - **`tool`** (string) (required)
          The name of a code scanning tool
  - **`copilot_code_review`** (object)
    Request Copilot code review for new pull requests automatically if the author has access to Copilot code review and their premium requests quota has not reached the limit.
    - **`type`** (string) (required)
      Can be one of: `copilot_code_review`
    - **`parameters`** (object)
      - **`review_draft_pull_requests`** (boolean)
        Copilot automatically reviews draft pull requests before they are marked as ready for review.
      - **`review_on_push`** (boolean)
        Copilot automatically reviews each new push to the pull request.





### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/rulesets/RULESET_ID \
  -d '{
  "name": "super cool ruleset",
  "target": "branch",
  "enforcement": "active",
  "bypass_actors": [
    {
      "actor_id": 234,
      "actor_type": "Team",
      "bypass_mode": "always"
    }
  ],
  "conditions": {
    "org_name": {
      "include": [
        "important_org"
      ],
      "exclude": [
        "unimportant_org"
      ]
    }
  },
  "rules": [
    {
      "type": "deletion"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an enterprise repository ruleset](#create-an-enterprise-repository-ruleset).





## Delete an enterprise repository ruleset

```
DELETE /enterprises/{enterprise}/rulesets/{ruleset_id}
```

Delete a ruleset for an enterprise.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`ruleset_id`** (integer) (required)
  The ID of the ruleset.






### HTTP response status codes


- **204** - No Content


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/enterprises/ENTERPRISE/rulesets/RULESET_ID
```

**Response schema (Status: 204):**





## Get enterprise ruleset history

```
GET /enterprises/{enterprise}/rulesets/{ruleset_id}/history
```

Get the history of an enterprise ruleset.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`ruleset_id`** (integer) (required)
  The ID of the ruleset.






### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/rulesets/RULESET_ID/history
```

**Response schema (Status: 200):**

Array of `Ruleset version`:
  * `version_id`: required, integer
  * `actor`: required, object:
    * `id`: integer
    * `type`: string
  * `updated_at`: required, string, format: date-time





## Get enterprise ruleset version

```
GET /enterprises/{enterprise}/rulesets/{ruleset_id}/history/{version_id}
```

Get a version of an enterprise ruleset.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`ruleset_id`** (integer) (required)
  The ID of the ruleset.

- **`version_id`** (integer) (required)
  The ID of the version






### HTTP response status codes


- **200** - OK


- **404** - Resource not found


- **500** - Internal Error




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/rulesets/RULESET_ID/history/VERSION_ID
```

**Response schema (Status: 200):**

* all of:
  * **Ruleset version**
    * `version_id`: required, integer
    * `actor`: required, object:
      * `id`: integer
      * `type`: string
    * `updated_at`: required, string, format: date-time
  * **object**
    * `state`: required, object