# Objects

Objects in GraphQL represent the resources you can access.

## About objects

[Objects](https://spec.graphql.org/June2018/#sec-Objects) in GraphQL represent the resources you can access. An object can contain a list of fields, which are specifically typed.

For example, the [`Repository`](/en/graphql/reference/objects#repository) object has a field called `name`, which is a `String`.

For more information, see [Introduction to GraphQL](/en/graphql/guides/introduction-to-graphql).

## Connection and Edge types

Connection types with only the standard pagination fields (`edges`, `nodes`, `pageInfo`, `totalCount`) and Edge types with only `cursor` and `node` are summarized here. Connection and Edge types with additional fields are documented individually below.

`ActorConnection`, `ActorEdge`, `AssigneeConnection`, `AssigneeEdge`, `BranchProtectionRuleConflictConnection`, `BranchProtectionRuleConflictEdge`, `BranchProtectionRuleConnection`, `BranchProtectionRuleEdge`, `BypassForcePushAllowanceConnection`, `BypassForcePushAllowanceEdge`, `BypassPullRequestAllowanceConnection`, `BypassPullRequestAllowanceEdge`, `CWEConnection`, `CWEEdge`, `CheckAnnotationConnection`, `CheckAnnotationEdge`, `CheckRunConnection`, `CheckRunEdge`, `CheckStepConnection`, `CheckStepEdge`, `CheckSuiteConnection`, `CheckSuiteEdge`, `CommitCommentConnection`, `CommitCommentEdge`, `CommitConnection`, `CommitEdge`, `CommitHistoryConnection`, `CreatedCommitContributionConnection`, `CreatedCommitContributionEdge`, `CreatedIssueContributionConnection`, `CreatedIssueContributionEdge`, `CreatedPullRequestContributionConnection`, `CreatedPullRequestContributionEdge`, `CreatedPullRequestReviewContributionConnection`, `CreatedPullRequestReviewContributionEdge`, `CreatedRepositoryContributionConnection`, `CreatedRepositoryContributionEdge`, `DependencyGraphDependencyConnection`, `DependencyGraphDependencyEdge`, `DependencyGraphManifestConnection`, `DependencyGraphManifestEdge`, `DeployKeyConnection`, `DeployKeyEdge`, `DeploymentConnection`, `DeploymentEdge`, `DeploymentProtectionRuleConnection`, `DeploymentProtectionRuleEdge`, `DeploymentRequestConnection`, `DeploymentRequestEdge`, `DeploymentReviewConnection`, `DeploymentReviewEdge`, `DeploymentReviewerConnection`, `DeploymentReviewerEdge`, `DeploymentStatusConnection`, `DeploymentStatusEdge`, `DiscussionCategoryConnection`, `DiscussionCategoryEdge`, `DiscussionCommentConnection`, `DiscussionCommentEdge`, `DiscussionConnection`, `DiscussionEdge`, `DiscussionPollOptionConnection`, `DiscussionPollOptionEdge`, `EnterpriseAdministratorConnection`, `EnterpriseAdministratorInvitationConnection`, `EnterpriseAdministratorInvitationEdge`, `EnterpriseConnection`, `EnterpriseEdge`, `EnterpriseFailedInvitationEdge`, `EnterpriseMemberConnection`, `EnterpriseMemberEdge`, `EnterpriseMemberInvitationConnection`, `EnterpriseMemberInvitationEdge`, `EnterpriseOrganizationMembershipConnection`, `EnterpriseOutsideCollaboratorConnection`, `EnterprisePendingMemberInvitationEdge`, `EnterpriseRepositoryInfoConnection`, `EnterpriseRepositoryInfoEdge`, `EnterpriseServerInstallationConnection`, `EnterpriseServerInstallationEdge`, `EnterpriseServerInstallationMembershipConnection`, `EnterpriseServerUserAccountConnection`, `EnterpriseServerUserAccountEdge`, `EnterpriseServerUserAccountEmailConnection`, `EnterpriseServerUserAccountEmailEdge`, `EnterpriseServerUserAccountsUploadConnection`, `EnterpriseServerUserAccountsUploadEdge`, `EnvironmentConnection`, `EnvironmentEdge`, `ExternalIdentityConnection`, `ExternalIdentityEdge`, `FollowerConnection`, `FollowingConnection`, `GistCommentConnection`, `GistCommentEdge`, `GistConnection`, `GistEdge`, `GitActorConnection`, `GitActorEdge`, `IpAllowListEntryConnection`, `IpAllowListEntryEdge`, `IssueCommentConnection`, `IssueCommentEdge`, `IssueConnection`, `IssueEdge`, `IssueFieldValueConnection`, `IssueFieldValueEdge`, `IssueFieldsConnection`, `IssueFieldsEdge`, `IssueTimelineConnection`, `IssueTimelineItemEdge`, `IssueTimelineItemsEdge`, `IssueTypeConnection`, `IssueTypeEdge`, `LabelConnection`, `LabelEdge`, `LinkedBranchConnection`, `LinkedBranchEdge`, `MannequinConnection`, `MannequinEdge`, `MarketplaceListingConnection`, `MarketplaceListingEdge`, `MergeQueueEntryConnection`, `MergeQueueEntryEdge`, `MilestoneConnection`, `MilestoneEdge`, `OrganizationAuditEntryConnection`, `OrganizationAuditEntryEdge`, `OrganizationConnection`, `OrganizationEdge`, `OrganizationEnterpriseOwnerConnection`, `OrganizationInvitationConnection`, `OrganizationInvitationEdge`, `OrganizationMemberConnection`, `PackageConnection`, `PackageEdge`, `PackageFileConnection`, `PackageFileEdge`, `PackageVersionConnection`, `PackageVersionEdge`, `PinnableItemConnection`, `PinnableItemEdge`, `PinnedDiscussionConnection`, `PinnedDiscussionEdge`, `PinnedEnvironmentConnection`, `PinnedEnvironmentEdge`, `PinnedIssueConnection`, `PinnedIssueEdge`, `ProjectCardConnection`, `ProjectCardEdge`, `ProjectColumnConnection`, `ProjectColumnEdge`, `ProjectConnection`, `ProjectEdge`, `ProjectV2ActorConnection`, `ProjectV2ActorEdge`, `ProjectV2Connection`, `ProjectV2Edge`, `ProjectV2FieldConfigurationConnection`, `ProjectV2FieldConfigurationEdge`, `ProjectV2FieldConnection`, `ProjectV2FieldEdge`, `ProjectV2ItemConnection`, `ProjectV2ItemEdge`, `ProjectV2ItemFieldValueConnection`, `ProjectV2ItemFieldValueEdge`, `ProjectV2SortByConnection`, `ProjectV2SortByEdge`, `ProjectV2SortByFieldConnection`, `ProjectV2SortByFieldEdge`, `ProjectV2StatusUpdateConnection`, `ProjectV2StatusUpdateEdge`, `ProjectV2ViewConnection`, `ProjectV2ViewEdge`, `ProjectV2WorkflowConnection`, `ProjectV2WorkflowEdge`, `PublicKeyConnection`, `PublicKeyEdge`, `PullRequestChangedFileConnection`, `PullRequestChangedFileEdge`, `PullRequestCommitConnection`, `PullRequestCommitEdge`, `PullRequestConnection`, `PullRequestEdge`, `PullRequestReviewCommentConnection`, `PullRequestReviewCommentEdge`, `PullRequestReviewConnection`, `PullRequestReviewEdge`, `PullRequestReviewThreadConnection`, `PullRequestReviewThreadEdge`, `PullRequestTimelineConnection`, `PullRequestTimelineItemEdge`, `PullRequestTimelineItemsEdge`, `PushAllowanceConnection`, `PushAllowanceEdge`, `ReactingUserConnection`, `ReactionEdge`, `ReactorConnection`, `RefConnection`, `RefEdge`, `ReleaseAssetConnection`, `ReleaseAssetEdge`, `ReleaseConnection`, `ReleaseEdge`, `RepositoryCollaboratorConnection`, `RepositoryCustomPropertyConnection`, `RepositoryCustomPropertyEdge`, `RepositoryCustomPropertyValueConnection`, `RepositoryCustomPropertyValueEdge`, `RepositoryEdge`, `RepositoryInvitationConnection`, `RepositoryInvitationEdge`, `RepositoryMigrationConnection`, `RepositoryMigrationEdge`, `RepositoryRuleConnection`, `RepositoryRuleEdge`, `RepositoryRulesetBypassActorConnection`, `RepositoryRulesetBypassActorEdge`, `RepositoryRulesetConnection`, `RepositoryRulesetEdge`, `RepositoryTopicConnection`, `RepositoryTopicEdge`, `RepositoryVulnerabilityAlertConnection`, `RepositoryVulnerabilityAlertEdge`, `RequestedReviewerConnection`, `RequestedReviewerEdge`, `ReviewDismissalAllowanceConnection`, `ReviewDismissalAllowanceEdge`, `ReviewRequestConnection`, `ReviewRequestEdge`, `SavedReplyConnection`, `SavedReplyEdge`, `SecurityAdvisoryConnection`, `SecurityAdvisoryEdge`, `SecurityVulnerabilityConnection`, `SecurityVulnerabilityEdge`, `SocialAccountConnection`, `SocialAccountEdge`, `SponsorAndLifetimeValueConnection`, `SponsorAndLifetimeValueEdge`, `SponsorConnection`, `SponsorEdge`, `SponsorableItemConnection`, `SponsorableItemEdge`, `SponsorsActivityConnection`, `SponsorsActivityEdge`, `SponsorsTierConnection`, `SponsorsTierEdge`, `SponsorshipEdge`, `SponsorshipNewsletterConnection`, `SponsorshipNewsletterEdge`, `StargazerConnection`, `StatusCheckRollupContextEdge`, `SubmoduleConnection`, `SubmoduleEdge`, `SuggestedReviewerActorConnection`, `SuggestedReviewerActorEdge`, `TeamConnection`, `TeamEdge`, `TeamMemberConnection`, `TeamRepositoryConnection`, `UserConnection`, `UserContentEditConnection`, `UserContentEditEdge`, `UserEdge`, `UserListConnection`, `UserListEdge`, `UserListItemsConnection`, `UserListItemsEdge`, `UserNamespaceRepositoryConnection`, `UserNamespaceRepositoryEdge`, `UserStatusConnection`, `UserStatusEdge`, `VerifiableDomainConnection`, `VerifiableDomainEdge`, `WorkflowRunConnection`, `WorkflowRunEdge`

## ActorLocation

Location information for an actor.

### Fields for `ActorLocation`

* `city` (String): City.
* `country` (String): Country name.
* `countryCode` (String): Country code.
* `region` (String): Region name.
* `regionCode` (String): Region or state code.

## AddedToMergeQueueEvent

Represents anadded\_to\_merge\_queueevent on a given pull request.

**Implements:** Node

### Fields for `AddedToMergeQueueEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `enqueuer` (User): The user who added this Pull Request to the merge queue.
* `id` (ID!): The Node ID of the AddedToMergeQueueEvent object.
* `mergeQueue` (MergeQueue): The merge queue where this pull request was added to.
* `pullRequest` (PullRequest): PullRequest referenced by event.

## AddedToProjectEvent

Represents aadded\_to\_projectevent on a given issue or pull request.

**Implements:** Node

### Fields for `AddedToProjectEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `id` (ID!): The Node ID of the AddedToProjectEvent object.
* `project` (Project): Project referenced by event. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `projectCard` (ProjectCard): Project card referenced by this project event. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `projectColumnName` (String!): Column name referenced by this project event. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

## AddedToProjectV2Event

Represents aadded\_to\_project\_v2event on a given issue or pull request.

**Implements:** Node, ProjectV2Event

### Fields for `AddedToProjectV2Event`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the AddedToProjectV2Event object.
* `project` (ProjectV2): Project referenced by event.
* `wasAutomated` (Boolean!): Did this event result from workflow automation?.

## AnnouncementBanner

An announcement banner for an enterprise or organization.

### Fields for `AnnouncementBanner`

* `createdAt` (DateTime!): The date the announcement was created.
* `expiresAt` (DateTime): The expiration date of the announcement, if any.
* `isUserDismissible` (Boolean!): Whether the announcement can be dismissed by the user.
* `message` (String): The text of the announcement.

## App

A GitHub App.

**Implements:** Node

### Fields for `App`

* `clientId` (String): The client ID of the app.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `description` (String): The description of the app.

* `id` (ID!): The Node ID of the App object.

* `ipAllowListEntries` (IpAllowListEntryConnection!): The IP addresses of the app.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IpAllowListEntryOrder): Ordering options for IP allow list entries returned.

* `logoBackgroundColor` (String!): The hex color code, without the leading '#', for the logo background.

* `logoUrl` (URI!): A URL pointing to the app's logo.
  * `size` (Int): The size of the resulting image.

* `name` (String!): The name of the app.

* `slug` (String!): A slug based on the name of the app for use in URLs.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The URL to the app's homepage.

## AssignedEvent

Represents anassignedevent on any assignable object.

**Implements:** Node

### Fields for `AssignedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `assignable` (Assignable!): Identifies the assignable associated with the event.
* `assignee` (Assignee): Identifies the user or mannequin that was assigned.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the AssignedEvent object.
* `user` (User): Identifies the user who was assigned. **Deprecated:** Assignees can now be mannequins. Use the assignee field instead. Removal on 2020-01-01 UTC.

## AutoMergeDisabledEvent

Represents aauto\_merge\_disabledevent on a given pull request.

**Implements:** Node

### Fields for `AutoMergeDisabledEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `disabler` (User): The user who disabled auto-merge for this Pull Request.
* `id` (ID!): The Node ID of the AutoMergeDisabledEvent object.
* `pullRequest` (PullRequest): PullRequest referenced by event.
* `reason` (String): The reason auto-merge was disabled.
* `reasonCode` (String): The reason\_code relating to why auto-merge was disabled.

## AutoMergeEnabledEvent

Represents aauto\_merge\_enabledevent on a given pull request.

**Implements:** Node

### Fields for `AutoMergeEnabledEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `enabler` (User): The user who enabled auto-merge for this Pull Request.
* `id` (ID!): The Node ID of the AutoMergeEnabledEvent object.
* `pullRequest` (PullRequest): PullRequest referenced by event.

## AutoMergeRequest

Represents an auto-merge request for a pull request.

### Fields for `AutoMergeRequest`

* `authorEmail` (String): The email address of the author of this auto-merge request.
* `commitBody` (String): The commit message of the auto-merge request. If a merge queue is required by
  the base branch, this value will be set by the merge queue when merging.
* `commitHeadline` (String): The commit title of the auto-merge request. If a merge queue is required by
  the base branch, this value will be set by the merge queue when merging.
* `enabledAt` (DateTime): When was this auto-merge request was enabled.
* `enabledBy` (Actor): The actor who created the auto-merge request.
* `mergeMethod` (PullRequestMergeMethod!): The merge method of the auto-merge request. If a merge queue is required by
  the base branch, this value will be set by the merge queue when merging.
* `pullRequest` (PullRequest!): The pull request that this auto-merge request is set against.

## AutoRebaseEnabledEvent

Represents aauto\_rebase\_enabledevent on a given pull request.

**Implements:** Node

### Fields for `AutoRebaseEnabledEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `enabler` (User): The user who enabled auto-merge (rebase) for this Pull Request.
* `id` (ID!): The Node ID of the AutoRebaseEnabledEvent object.
* `pullRequest` (PullRequest): PullRequest referenced by event.

## AutoSquashEnabledEvent

Represents aauto\_squash\_enabledevent on a given pull request.

**Implements:** Node

### Fields for `AutoSquashEnabledEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `enabler` (User): The user who enabled auto-merge (squash) for this Pull Request.
* `id` (ID!): The Node ID of the AutoSquashEnabledEvent object.
* `pullRequest` (PullRequest): PullRequest referenced by event.

## AutomaticBaseChangeFailedEvent

Represents aautomatic\_base\_change\_failedevent on a given pull request.

**Implements:** Node

### Fields for `AutomaticBaseChangeFailedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the AutomaticBaseChangeFailedEvent object.
* `newBase` (String!): The new base for this PR.
* `oldBase` (String!): The old base for this PR.
* `pullRequest` (PullRequest!): PullRequest referenced by event.

## AutomaticBaseChangeSucceededEvent

Represents aautomatic\_base\_change\_succeededevent on a given pull request.

**Implements:** Node

### Fields for `AutomaticBaseChangeSucceededEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the AutomaticBaseChangeSucceededEvent object.
* `newBase` (String!): The new base for this PR.
* `oldBase` (String!): The old base for this PR.
* `pullRequest` (PullRequest!): PullRequest referenced by event.

## BaseRefChangedEvent

Represents abase\_ref\_changedevent on a given issue or pull request.

**Implements:** Node

### Fields for `BaseRefChangedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `currentRefName` (String!): Identifies the name of the base ref for the pull request after it was changed.
* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the BaseRefChangedEvent object.
* `previousRefName` (String!): Identifies the name of the base ref for the pull request before it was changed.
* `pullRequest` (PullRequest!): PullRequest referenced by event.

## BaseRefDeletedEvent

Represents abase\_ref\_deletedevent on a given pull request.

**Implements:** Node

### Fields for `BaseRefDeletedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `baseRefName` (String): Identifies the name of the Ref associated with the base\_ref\_deleted event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the BaseRefDeletedEvent object.
* `pullRequest` (PullRequest): PullRequest referenced by event.

## BaseRefForcePushedEvent

Represents abase\_ref\_force\_pushedevent on a given pull request.

**Implements:** Node

### Fields for `BaseRefForcePushedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `afterCommit` (Commit): Identifies the after commit SHA for thebase\_ref\_force\_pushedevent.
* `beforeCommit` (Commit): Identifies the before commit SHA for thebase\_ref\_force\_pushedevent.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the BaseRefForcePushedEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.
* `ref` (Ref): Identifies the fully qualified ref name for thebase\_ref\_force\_pushedevent.

## Blame

Represents a Git blame.

### Fields for `Blame`

* `ranges` (\[BlameRange!]!): The list of ranges from a Git blame.

## BlameRange

Represents a range of information from a Git blame.

### Fields for `BlameRange`

* `age` (Int!): Identifies the recency of the change, from 1 (new) to 10 (old). This is
  calculated as a 2-quantile and determines the length of distance between the
  median age of all the changes in the file and the recency of the current
  range's change.
* `commit` (Commit!): Identifies the line author.
* `endingLine` (Int!): The ending line for the range.
* `startingLine` (Int!): The starting line for the range.

## Blob

Represents a Git blob.

**Implements:** GitObject, Node

### Fields for `Blob`

* `abbreviatedOid` (String!): An abbreviated version of the Git object ID.
* `byteSize` (Int!): Byte size of Blob object.
* `commitResourcePath` (URI!): The HTTP path for this Git object.
* `commitUrl` (URI!): The HTTP URL for this Git object.
* `id` (ID!): The Node ID of the Blob object.
* `isBinary` (Boolean): Indicates whether the Blob is binary or text. Returns null if unable to determine the encoding.
* `isTruncated` (Boolean!): Indicates whether the contents is truncated.
* `oid` (GitObjectID!): The Git object ID.
* `repository` (Repository!): The Repository the Git object belongs to.
* `text` (String): UTF8 text data or null if the Blob is binary.

## BlockedByAddedEvent

Represents ablocked\_by\_addedevent on a given issue.

**Implements:** Node

### Fields for `BlockedByAddedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `blockingIssue` (Issue): The blocking issue that was added.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the BlockedByAddedEvent object.

## BlockedByRemovedEvent

Represents ablocked\_by\_removedevent on a given issue.

**Implements:** Node

### Fields for `BlockedByRemovedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `blockingIssue` (Issue): The blocking issue that was removed.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the BlockedByRemovedEvent object.

## BlockingAddedEvent

Represents ablocking\_addedevent on a given issue.

**Implements:** Node

### Fields for `BlockingAddedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `blockedIssue` (Issue): The blocked issue that was added.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the BlockingAddedEvent object.

## BlockingRemovedEvent

Represents ablocking\_removedevent on a given issue.

**Implements:** Node

### Fields for `BlockingRemovedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `blockedIssue` (Issue): The blocked issue that was removed.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the BlockingRemovedEvent object.

## Bot

A special type of user which takes actions on behalf of GitHub Apps.

**Implements:** Actor, Node, UniformResourceLocatable

### Fields for `Bot`

* `avatarUrl` (URI!): A URL pointing to the GitHub App's public avatar.
  * `size` (Int): The size of the resulting square image.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `id` (ID!): The Node ID of the Bot object.

* `login` (String!): The username of the actor.

* `resourcePath` (URI!): The HTTP path for this bot.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this bot.

## BranchNamePatternParameters

Parameters to be used for the branch\_name\_pattern rule.

### Fields for `BranchNamePatternParameters`

* `name` (String): How this rule appears when configuring it.
* `negate` (Boolean!): If true, the rule will fail if the pattern matches.
* `operator` (String!): The operator to use for matching.
* `pattern` (String!): The pattern to match with.

## BranchProtectionRule

A branch protection rule.

**Implements:** Node

### Fields for `BranchProtectionRule`

* `allowsDeletions` (Boolean!): Can this branch be deleted.

* `allowsForcePushes` (Boolean!): Are force pushes allowed on this branch.

* `blocksCreations` (Boolean!): Is branch creation a protected operation.

* `branchProtectionRuleConflicts` (BranchProtectionRuleConflictConnection!): A list of conflicts matching branches protection rule and other branch protection rules. *(Pagination: `after`, `before`, `first`, `last`)*

* `bypassForcePushAllowances` (BypassForcePushAllowanceConnection!): A list of actors able to force push for this branch protection rule. *(Pagination: `after`, `before`, `first`, `last`)*

* `bypassPullRequestAllowances` (BypassPullRequestAllowanceConnection!): A list of actors able to bypass PRs for this branch protection rule. *(Pagination: `after`, `before`, `first`, `last`)*

* `creator` (Actor): The actor who created this branch protection rule.

* `databaseId` (Int): Identifies the primary key from the database.

* `dismissesStaleReviews` (Boolean!): Will new commits pushed to matching branches dismiss pull request review approvals.

* `id` (ID!): The Node ID of the BranchProtectionRule object.

* `isAdminEnforced` (Boolean!): Can admins override branch protection.

* `lockAllowsFetchAndMerge` (Boolean!): Whether users can pull changes from upstream when the branch is locked. Set to
  true to allow fork syncing. Set to false to prevent fork syncing.

* `lockBranch` (Boolean!): Whether to set the branch as read-only. If this is true, users will not be able to push to the branch.

* `matchingRefs` (RefConnection!): Repository refs that are protected by this rule.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `query` (String): Filters refs with query on name.

* `pattern` (String!): Identifies the protection rule pattern.

* `pushAllowances` (PushAllowanceConnection!): A list push allowances for this branch protection rule. *(Pagination: `after`, `before`, `first`, `last`)*

* `repository` (Repository): The repository associated with this branch protection rule.

* `requireLastPushApproval` (Boolean!): Whether the most recent push must be approved by someone other than the person who pushed it.

* `requiredApprovingReviewCount` (Int): Number of approving reviews required to update matching branches.

* `requiredDeploymentEnvironments` (\[String]): List of required deployment environments that must be deployed successfully to update matching branches.

* `requiredStatusCheckContexts` (\[String]): List of required status check contexts that must pass for commits to be accepted to matching branches.

* `requiredStatusChecks` (\[RequiredStatusCheckDescription!]): List of required status checks that must pass for commits to be accepted to matching branches.

* `requiresApprovingReviews` (Boolean!): Are approving reviews required to update matching branches.

* `requiresCodeOwnerReviews` (Boolean!): Are reviews from code owners required to update matching branches.

* `requiresCommitSignatures` (Boolean!): Are commits required to be signed.

* `requiresConversationResolution` (Boolean!): Are conversations required to be resolved before merging.

* `requiresDeployments` (Boolean!): Does this branch require deployment to specific environments before merging.

* `requiresLinearHistory` (Boolean!): Are merge commits prohibited from being pushed to this branch.

* `requiresStatusChecks` (Boolean!): Are status checks required to update matching branches.

* `requiresStrictStatusChecks` (Boolean!): Are branches required to be up to date before merging.

* `restrictsPushes` (Boolean!): Is pushing to matching branches restricted.

* `restrictsReviewDismissals` (Boolean!): Is dismissal of pull request reviews restricted.

* `reviewDismissalAllowances` (ReviewDismissalAllowanceConnection!): A list review dismissal allowances for this branch protection rule. *(Pagination: `after`, `before`, `first`, `last`)*

## BranchProtectionRuleConflict

A conflict between two branch protection rules.

### Fields for `BranchProtectionRuleConflict`

* `branchProtectionRule` (BranchProtectionRule): Identifies the branch protection rule.
* `conflictingBranchProtectionRule` (BranchProtectionRule): Identifies the conflicting branch protection rule.
* `ref` (Ref): Identifies the branch ref that has conflicting rules.

## BypassForcePushAllowance

A user, team, or app who has the ability to bypass a force push requirement on a protected branch.

**Implements:** Node

### Fields for `BypassForcePushAllowance`

* `actor` (BranchActorAllowanceActor): The actor that can force push.
* `branchProtectionRule` (BranchProtectionRule): Identifies the branch protection rule associated with the allowed user, team, or app.
* `id` (ID!): The Node ID of the BypassForcePushAllowance object.

## BypassPullRequestAllowance

A user, team, or app who has the ability to bypass a pull request requirement on a protected branch.

**Implements:** Node

### Fields for `BypassPullRequestAllowance`

* `actor` (BranchActorAllowanceActor): The actor that can bypass.
* `branchProtectionRule` (BranchProtectionRule): Identifies the branch protection rule associated with the allowed user, team, or app.
* `id` (ID!): The Node ID of the BypassPullRequestAllowance object.

## CVSS

The Common Vulnerability Scoring System.

### Fields for `CVSS`

* `score` (Float!): The CVSS score associated with this advisory.
* `vectorString` (String): The CVSS vector string associated with this advisory.

## CWE

A common weakness enumeration.

**Implements:** Node

### Fields for `CWE`

* `cweId` (String!): The id of the CWE.
* `description` (String!): A detailed description of this CWE.
* `id` (ID!): The Node ID of the CWE object.
* `name` (String!): The name of this CWE.

## CheckAnnotation

A single check annotation.

### Fields for `CheckAnnotation`

* `annotationLevel` (CheckAnnotationLevel): The annotation's severity level.
* `blobUrl` (URI!): The path to the file that this annotation was made on.
* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** databaseId will be removed because it does not support 64-bit signed integer identifiers. Use fullDatabaseId instead. Removal on 2027-01-01 UTC.
* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.
* `location` (CheckAnnotationSpan!): The position of this annotation.
* `message` (String!): The annotation's message.
* `path` (String!): The path that this annotation was made on.
* `rawDetails` (String): Additional information about the annotation.
* `title` (String): The annotation's title.

## CheckAnnotationPosition

A character position in a check annotation.

### Fields for `CheckAnnotationPosition`

* `column` (Int): Column number (1 indexed).
* `line` (Int!): Line number (1 indexed).

## CheckAnnotationSpan

An inclusive pair of positions for a check annotation.

### Fields for `CheckAnnotationSpan`

* `end` (CheckAnnotationPosition!): End position (inclusive).
* `start` (CheckAnnotationPosition!): Start position (inclusive).

## CheckRun

A check run.

**Implements:** Node, RequirableByPullRequest, UniformResourceLocatable

### Fields for `CheckRun`

* `annotations` (CheckAnnotationConnection): The check run's annotations. *(Pagination: `after`, `before`, `first`, `last`)*

* `checkSuite` (CheckSuite!): The check suite that this run is a part of.

* `completedAt` (DateTime): Identifies the date and time when the check run was completed.

* `conclusion` (CheckConclusionState): The conclusion of the check run.

* `databaseId` (Int): Identifies the primary key from the database.

* `deployment` (Deployment): The corresponding deployment for this job, if any.

* `detailsUrl` (URI): The URL from which to find full details of the check run on the integrator's site.

* `externalId` (String): A reference for the check run on the integrator's system.

* `id` (ID!): The Node ID of the CheckRun object.

* `isRequired` (Boolean!): Whether this is required to pass before merging for a specific pull request.
  * `pullRequestId` (ID): The id of the pull request this is required for.
  * `pullRequestNumber` (Int): The number of the pull request this is required for.

* `name` (String!): The name of the check for this check run.

* `pendingDeploymentRequest` (DeploymentRequest): Information about a pending deployment, if any, in this check run.

* `permalink` (URI!): The permalink to the check run summary.

* `repository` (Repository!): The repository associated with this check run.

* `resourcePath` (URI!): The HTTP path for this check run.

* `startedAt` (DateTime): Identifies the date and time when the check run was started.

* `status` (CheckStatusState!): The current status of the check run.

* `steps` (CheckStepConnection): The check run's steps.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `number` (Int): Step number.

* `summary` (String): A string representing the check run's summary.

* `text` (String): A string representing the check run's text.

* `title` (String): A string representing the check run.

* `url` (URI!): The HTTP URL for this check run.

## CheckRunStateCount

Represents a count of the state of a check run.

### Fields for `CheckRunStateCount`

* `count` (Int!): The number of check runs with this state.
* `state` (CheckRunState!): The state of a check run.

## CheckStep

A single check step.

### Fields for `CheckStep`

* `completedAt` (DateTime): Identifies the date and time when the check step was completed.
* `conclusion` (CheckConclusionState): The conclusion of the check step.
* `externalId` (String): A reference for the check step on the integrator's system.
* `name` (String!): The step's name.
* `number` (Int!): The index of the step in the list of steps of the parent check run.
* `secondsToCompletion` (Int): Number of seconds to completion.
* `startedAt` (DateTime): Identifies the date and time when the check step was started.
* `status` (CheckStatusState!): The current status of the check step.

## CheckSuite

A check suite.

**Implements:** Node

### Fields for `CheckSuite`

* `app` (App): The GitHub App which created this check suite.

* `branch` (Ref): The name of the branch for this check suite.

* `checkRuns` (CheckRunConnection): The check runs associated with a check suite.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `filterBy` (CheckRunFilter): Filters the check runs by this type.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.

* `commit` (Commit!): The commit for this check suite.

* `conclusion` (CheckConclusionState): The conclusion of this check suite.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `creator` (User): The user who triggered the check suite.

* `databaseId` (Int): Identifies the primary key from the database.

* `id` (ID!): The Node ID of the CheckSuite object.

* `matchingPullRequests` (PullRequestConnection): A list of open pull requests matching the check suite.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `baseRefName` (String): The base ref name to filter the pull requests by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `headRefName` (String): The head ref name to filter the pull requests by.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for pull requests returned from the connection.
  * `states` (\[PullRequestState!]): A list of states to filter the pull requests by.

* `push` (Push): The push that triggered this check suite.

* `repository` (Repository!): The repository associated with this check suite.

* `resourcePath` (URI!): The HTTP path for this check suite.

* `status` (CheckStatusState!): The status of this check suite.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this check suite.

* `workflowRun` (WorkflowRun): The workflow run associated with this check suite.

## ClosedEvent

Represents aclosedevent on any Closable.

**Implements:** Node, UniformResourceLocatable

### Fields for `ClosedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `closable` (Closable!): Object that was closed.
* `closer` (Closer): Object which triggered the creation of this event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `duplicateOf` (IssueOrPullRequest): The issue or pull request that this issue was marked as a duplicate of.
* `id` (ID!): The Node ID of the ClosedEvent object.
* `resourcePath` (URI!): The HTTP path for this closed event.
* `stateReason` (IssueStateReason): The reason the issue state was changed to closed.
* `url` (URI!): The HTTP URL for this closed event.

## CodeOfConduct

The Code of Conduct for a repository.

**Implements:** Node

### Fields for `CodeOfConduct`

* `body` (String): The body of the Code of Conduct.
* `id` (ID!): The Node ID of the CodeOfConduct object.
* `key` (String!): The key for the Code of Conduct.
* `name` (String!): The formal name of the Code of Conduct.
* `resourcePath` (URI): The HTTP path for this Code of Conduct.
* `url` (URI): The HTTP URL for this Code of Conduct.

## CodeScanningParameters

Choose which tools must provide code scanning results before the reference is
updated. When configured, code scanning must be enabled and have results for
both the commit and the reference being updated.

### Fields for `CodeScanningParameters`

* `codeScanningTools` (\[CodeScanningTool!]!): Tools that must provide code scanning results for this rule to pass.

## CodeScanningTool

A tool that must provide code scanning results for this rule to pass.

### Fields for `CodeScanningTool`

* `alertsThreshold` (String!): The severity level at which code scanning results that raise alerts block a
  reference update. For more information on alert severity levels, see "About code scanning alerts.".
* `securityAlertsThreshold` (String!): The severity level at which code scanning results that raise security alerts
  block a reference update. For more information on security severity levels,
  see "About code scanning alerts.".
* `tool` (String!): The name of a code scanning tool.

## CommentDeletedEvent

Represents acomment\_deletedevent on a given issue or pull request.

**Implements:** Node

### Fields for `CommentDeletedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `deletedCommentAuthor` (Actor): The user who authored the deleted comment.
* `id` (ID!): The Node ID of the CommentDeletedEvent object.

## Commit

Represents a Git commit.

**Implements:** GitObject, Node, Subscribable, UniformResourceLocatable

### Fields for `Commit`

* `abbreviatedOid` (String!): An abbreviated version of the Git object ID.

* `additions` (Int!): The number of additions in this commit.

* `associatedPullRequests` (PullRequestConnection): The merged Pull Request that introduced the commit to the repository. If the
  commit is not present in the default branch, additionally returns open Pull
  Requests associated with the commit.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (PullRequestOrder): Ordering options for pull requests.

* `author` (GitActor): Authorship details of the commit.

* `authoredByCommitter` (Boolean!): Check if the committer and the author match.

* `authoredDate` (DateTime!): The datetime when this commit was authored.

* `authors` (GitActorConnection!): The list of authors for this commit based on the git author and the Co-authored-by
  message trailer. The git author will always be first. *(Pagination: `after`, `before`, `first`, `last`)*

* `blame` (Blame!): Fetches git blame information.
  * `path` (String!): The file whose Git blame information you want.

* `changedFiles` (Int!): We recommend using the changedFilesIfAvailable field instead of
  changedFiles, as changedFiles will cause your request to return an error
  if GitHub is unable to calculate the number of changed files. **Deprecated:** changedFiles will be removed. Use changedFilesIfAvailable instead. Removal on 2023-01-01 UTC.

* `changedFilesIfAvailable` (Int): The number of changed files in this commit. If GitHub is unable to calculate
  the number of changed files (for example due to a timeout), this will return
  null. We recommend using this field instead of changedFiles.

* `checkSuites` (CheckSuiteConnection): The check suites associated with a commit.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `filterBy` (CheckSuiteFilter): Filters the check suites by this type.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.

* `comments` (CommitCommentConnection!): Comments made on the commit. *(Pagination: `after`, `before`, `first`, `last`)*

* `commitResourcePath` (URI!): The HTTP path for this Git object.

* `commitUrl` (URI!): The HTTP URL for this Git object.

* `committedDate` (DateTime!): The datetime when this commit was committed.

* `committedViaWeb` (Boolean!): Check if committed via GitHub web UI.

* `committer` (GitActor): Committer details of the commit.

* `deletions` (Int!): The number of deletions in this commit.

* `deployments` (DeploymentConnection): The deployments associated with a commit.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `environments` (\[String!]): Environments to list deployments for.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (DeploymentOrder): Ordering options for deployments returned from the connection.

* `file` (TreeEntry): The tree entry representing the file located at the given path.
  * `path` (String!): The path for the file.

* `history` (CommitHistoryConnection!): The linear commit history starting from (and including) this commit, in the same order as git log.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `author` (CommitAuthor): If non-null, filters history to only show commits with matching authorship.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `path` (String): If non-null, filters history to only show commits touching files under this path.
  * `since` (GitTimestamp): Allows specifying a beginning time or date for fetching commits. Unexpected
    results may be returned for dates not between 1970-01-01 and 2099-12-13 (inclusive).
  * `until` (GitTimestamp): Allows specifying an ending time or date for fetching commits. Unexpected
    results may be returned for dates not between 1970-01-01 and 2099-12-13 (inclusive).

* `id` (ID!): The Node ID of the Commit object.

* `message` (String!): The Git commit message.

* `messageBody` (String!): The Git commit message body.

* `messageBodyHTML` (HTML!): The commit message body rendered to HTML.

* `messageHeadline` (String!): The Git commit message headline.

* `messageHeadlineHTML` (HTML!): The commit message headline rendered to HTML.

* `oid` (GitObjectID!): The Git object ID.

* `onBehalfOf` (Organization): The organization this commit was made on behalf of.

* `parents` (CommitConnection!): The parents of a commit. *(Pagination: `after`, `before`, `first`, `last`)*

* `pushedDate` (DateTime): The datetime when this commit was pushed. **Deprecated:** pushedDate is no longer supported. Removal on 2023-07-01 UTC.

* `repository` (Repository!): The Repository this commit belongs to.

* `resourcePath` (URI!): The HTTP path for this commit.

* `signature` (GitSignature): Commit signing information, if present.

* `status` (Status): Status information for this commit.

* `statusCheckRollup` (StatusCheckRollup): Check and Status rollup information for this commit.

* `submodules` (SubmoduleConnection!): Returns a list of all submodules in this repository as of this Commit parsed from the .gitmodules file. *(Pagination: `after`, `before`, `first`, `last`)*

* `tarballUrl` (URI!): Returns a URL to download a tarball archive for a repository.
  Note: For private repositories, these links are temporary and expire after five minutes.

* `tree` (Tree!): Commit's root Tree.

* `treeResourcePath` (URI!): The HTTP path for the tree of this commit.

* `treeUrl` (URI!): The HTTP URL for the tree of this commit.

* `url` (URI!): The HTTP URL for this commit.

* `viewerCanSubscribe` (Boolean!): Check if the viewer is able to change their subscription status for the repository.

* `viewerSubscription` (SubscriptionState): Identifies if the viewer is watching, not watching, or ignoring the subscribable entity.

* `zipballUrl` (URI!): Returns a URL to download a zipball archive for a repository.
  Note: For private repositories, these links are temporary and expire after five minutes.

## CommitAuthorEmailPatternParameters

Parameters to be used for the commit\_author\_email\_pattern rule.

### Fields for `CommitAuthorEmailPatternParameters`

* `name` (String): How this rule appears when configuring it.
* `negate` (Boolean!): If true, the rule will fail if the pattern matches.
* `operator` (String!): The operator to use for matching.
* `pattern` (String!): The pattern to match with.

## CommitComment

Represents a comment on a given Commit.

**Implements:** Comment, Deletable, Minimizable, Node, Reactable, RepositoryNode, Updatable, UpdatableComment

### Fields for `CommitComment`

* `author` (Actor): The actor who authored the comment.

* `authorAssociation` (CommentAuthorAssociation!): Author's association with the subject of the comment.

* `body` (String!): Identifies the comment body.

* `bodyHTML` (HTML!): The body rendered to HTML.

* `bodyText` (String!): The body rendered to text.

* `commit` (Commit): Identifies the commit associated with the comment, if the commit exists.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.

* `databaseId` (Int): Identifies the primary key from the database.

* `editor` (Actor): The actor who edited the comment.

* `id` (ID!): The Node ID of the CommitComment object.

* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.

* `isMinimized` (Boolean!): Returns whether or not a comment has been minimized.

* `lastEditedAt` (DateTime): The moment the editor made the last edit.

* `minimizedReason` (String): Returns why the comment was minimized. One of abuse, off-topic,
  outdated, resolved, duplicate, spam, and low-quality. Note that the
  case and formatting of these values differs from the inputs to the
  MinimizeComment mutation.

* `path` (String): Identifies the file path associated with the comment.

* `position` (Int): Identifies the line position associated with the comment.

* `publishedAt` (DateTime): Identifies when the comment was published at.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `repository` (Repository!): The repository associated with this node.

* `resourcePath` (URI!): The HTTP path permalink for this commit comment.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL permalink for this commit comment.

* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*

* `viewerCanDelete` (Boolean!): Check if the current viewer can delete this object.

* `viewerCanMinimize` (Boolean!): Check if the current viewer can minimize this object.

* `viewerCanReact` (Boolean!): Can user react to this subject.

* `viewerCanUnminimize` (Boolean!): Check if the current viewer can unminimize this object.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

* `viewerCannotUpdateReasons` (\[CommentCannotUpdateReason!]!): Reasons why the current viewer can not update this comment.

* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

## CommitCommentThread

A thread of comments on a commit.

**Implements:** Node, RepositoryNode

### Fields for `CommitCommentThread`

* `comments` (CommitCommentConnection!): The comments that exist in this thread. *(Pagination: `after`, `before`, `first`, `last`)*
* `commit` (Commit): The commit the comments were made on.
* `id` (ID!): The Node ID of the CommitCommentThread object.
* `path` (String): The file the comments were made on.
* `position` (Int): The position in the diff for the commit that the comment was made on.
* `repository` (Repository!): The repository associated with this node.

## CommitContributionsByRepository

This aggregates commits made by a user within one repository.

### Fields for `CommitContributionsByRepository`

* `contributions` (CreatedCommitContributionConnection!): The commit contributions, each representing a day.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (CommitContributionOrder): Ordering options for commit contributions returned from the connection.

* `repository` (Repository!): The repository in which the commits were made.

* `resourcePath` (URI!): The HTTP path for the user's commits to the repository in this time range.

* `url` (URI!): The HTTP URL for the user's commits to the repository in this time range.

## CommitMessagePatternParameters

Parameters to be used for the commit\_message\_pattern rule.

### Fields for `CommitMessagePatternParameters`

* `name` (String): How this rule appears when configuring it.
* `negate` (Boolean!): If true, the rule will fail if the pattern matches.
* `operator` (String!): The operator to use for matching.
* `pattern` (String!): The pattern to match with.

## CommitterEmailPatternParameters

Parameters to be used for the committer\_email\_pattern rule.

### Fields for `CommitterEmailPatternParameters`

* `name` (String): How this rule appears when configuring it.
* `negate` (Boolean!): If true, the rule will fail if the pattern matches.
* `operator` (String!): The operator to use for matching.
* `pattern` (String!): The pattern to match with.

## Comparison

Represents a comparison between two commit revisions.

**Implements:** Node

### Fields for `Comparison`

* `aheadBy` (Int!): The number of commits ahead of the base branch.
* `baseTarget` (GitObject!): The base revision of this comparison.
* `behindBy` (Int!): The number of commits behind the base branch.
* `commits` (ComparisonCommitConnection!): The commits which compose this comparison. *(Pagination: `after`, `before`, `first`, `last`)*
* `headTarget` (GitObject!): The head revision of this comparison.
* `id` (ID!): The Node ID of the Comparison object.
* `status` (ComparisonStatus!): The status of this comparison.

## ComparisonCommitConnection

The connection type for Commit.

### Fields for `ComparisonCommitConnection`

* `authorCount` (Int!): The total count of authors and co-authors across all commits.
* `edges` (\[CommitEdge]): A list of edges.
* `nodes` (\[Commit]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.

## ConnectedEvent

Represents aconnectedevent on a given issue or pull request.

**Implements:** Node

### Fields for `ConnectedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ConnectedEvent object.
* `isCrossRepository` (Boolean!): Reference originated in a different repository.
* `source` (ReferencedSubject!): Issue or pull request that made the reference.
* `subject` (ReferencedSubject!): Issue or pull request which was connected.

## ContributingGuidelines

The Contributing Guidelines for a repository.

### Fields for `ContributingGuidelines`

* `body` (String): The body of the Contributing Guidelines.
* `resourcePath` (URI): The HTTP path for the Contributing Guidelines.
* `url` (URI): The HTTP URL for the Contributing Guidelines.

## ContributionCalendar

A calendar of contributions made on GitHub by a user.

### Fields for `ContributionCalendar`

* `colors` (\[String!]!): A list of hex color codes used in this calendar. The darker the color, the more contributions it represents.
* `isHalloween` (Boolean!): Determine if the color set was chosen because it's currently Halloween.
* `months` (\[ContributionCalendarMonth!]!): A list of the months of contributions in this calendar.
* `totalContributions` (Int!): The count of total contributions in the calendar.
* `weeks` (\[ContributionCalendarWeek!]!): A list of the weeks of contributions in this calendar.

## ContributionCalendarDay

Represents a single day of contributions on GitHub by a user.

### Fields for `ContributionCalendarDay`

* `color` (String!): The hex color code that represents how many contributions were made on this day compared to others in the calendar.
* `contributionCount` (Int!): How many contributions were made by the user on this day.
* `contributionLevel` (ContributionLevel!): Indication of contributions, relative to other days. Can be used to indicate
  which color to represent this day on a calendar.
* `date` (Date!): The day this square represents.
* `weekday` (Int!): A number representing which day of the week this square represents, e.g., 1 is Monday.

## ContributionCalendarMonth

A month of contributions in a user's contribution graph.

### Fields for `ContributionCalendarMonth`

* `firstDay` (Date!): The date of the first day of this month.
* `name` (String!): The name of the month.
* `totalWeeks` (Int!): How many weeks started in this month.
* `year` (Int!): The year the month occurred in.

## ContributionCalendarWeek

A week of contributions in a user's contribution graph.

### Fields for `ContributionCalendarWeek`

* `contributionDays` (\[ContributionCalendarDay!]!): The days of contributions in this week.
* `firstDay` (Date!): The date of the earliest square in this week.

## ContributionsCollection

A collection of contributions made by a user, including opened issues, commits, and pull requests.
Contributions in private and internal repositories are only included with the optional read:user scope.

### Fields for `ContributionsCollection`

* `commitContributionsByRepository` (\[CommitContributionsByRepository!]!): Commit contributions made by the user, grouped by repository.
  * `maxRepositories` (Int): How many repositories should be included. Default: `25`.

* `contributionCalendar` (ContributionCalendar!): A calendar of this user's contributions on GitHub.

* `contributionYears` (\[Int!]!): The years the user has been making contributions with the most recent year first.

* `doesEndInCurrentMonth` (Boolean!): Determine if this collection's time span ends in the current month.

* `earliestRestrictedContributionDate` (Date): The date of the first restricted contribution the user made in this time
  period. Can only be non-null when the user has enabled private contribution counts.

* `endedAt` (DateTime!): The ending date and time of this collection.

* `firstIssueContribution` (CreatedIssueOrRestrictedContribution): The first issue the user opened on GitHub. This will be null if that issue was
  opened outside the collection's time range and ignoreTimeRange is false. If
  the issue is not visible but the user has opted to show private contributions,
  a RestrictedContribution will be returned.

* `firstPullRequestContribution` (CreatedPullRequestOrRestrictedContribution): The first pull request the user opened on GitHub. This will be null if that
  pull request was opened outside the collection's time range and
  ignoreTimeRange is not true. If the pull request is not visible but the user
  has opted to show private contributions, a RestrictedContribution will be returned.

* `firstRepositoryContribution` (CreatedRepositoryOrRestrictedContribution): The first repository the user created on GitHub. This will be null if that
  first repository was created outside the collection's time range and
  ignoreTimeRange is false. If the repository is not visible, then a
  RestrictedContribution is returned.

* `hasActivityInThePast` (Boolean!): Does the user have any more activity in the timeline that occurred prior to the collection's time range?.

* `hasAnyContributions` (Boolean!): Determine if there are any contributions in this collection.

* `hasAnyRestrictedContributions` (Boolean!): Determine if the user made any contributions in this time frame whose details
  are not visible because they were made in a private repository. Can only be
  true if the user enabled private contribution counts.

* `isSingleDay` (Boolean!): Whether or not the collector's time span is all within the same day.

* `issueContributions` (CreatedIssueContributionConnection!): A list of issues the user opened.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `excludeFirst` (Boolean): Should the user's first issue ever be excluded from the result.
  * `excludePopular` (Boolean): Should the user's most commented issue be excluded from the result.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ContributionOrder): Ordering options for contributions returned from the connection.

* `issueContributionsByRepository` (\[IssueContributionsByRepository!]!): Issue contributions made by the user, grouped by repository.
  * `excludeFirst` (Boolean): Should the user's first issue ever be excluded from the result.
  * `excludePopular` (Boolean): Should the user's most commented issue be excluded from the result.
  * `maxRepositories` (Int): How many repositories should be included. Default: `25`.

* `joinedGitHubContribution` (JoinedGitHubContribution): When the user signed up for GitHub. This will be null if that sign up date
  falls outside the collection's time range and ignoreTimeRange is false.

* `latestRestrictedContributionDate` (Date): The date of the most recent restricted contribution the user made in this time
  period. Can only be non-null when the user has enabled private contribution counts.

* `mostRecentCollectionWithActivity` (ContributionsCollection): When this collection's time range does not include any activity from the user, use this
  to get a different collection from an earlier time range that does have activity.

* `mostRecentCollectionWithoutActivity` (ContributionsCollection): Returns a different contributions collection from an earlier time range than this one
  that does not have any contributions.

* `popularIssueContribution` (CreatedIssueContribution): The issue the user opened on GitHub that received the most comments in the specified
  time frame.

* `popularPullRequestContribution` (CreatedPullRequestContribution): The pull request the user opened on GitHub that received the most comments in the
  specified time frame.

* `pullRequestContributions` (CreatedPullRequestContributionConnection!): Pull request contributions made by the user.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `excludeFirst` (Boolean): Should the user's first pull request ever be excluded from the result.
  * `excludePopular` (Boolean): Should the user's most commented pull request be excluded from the result.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ContributionOrder): Ordering options for contributions returned from the connection.

* `pullRequestContributionsByRepository` (\[PullRequestContributionsByRepository!]!): Pull request contributions made by the user, grouped by repository.
  * `excludeFirst` (Boolean): Should the user's first pull request ever be excluded from the result.
  * `excludePopular` (Boolean): Should the user's most commented pull request be excluded from the result.
  * `maxRepositories` (Int): How many repositories should be included. Default: `25`.

* `pullRequestReviewContributions` (CreatedPullRequestReviewContributionConnection!): Pull request review contributions made by the user. Returns the most recently
  submitted review for each PR reviewed by the user.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ContributionOrder): Ordering options for contributions returned from the connection.

* `pullRequestReviewContributionsByRepository` (\[PullRequestReviewContributionsByRepository!]!): Pull request review contributions made by the user, grouped by repository.
  * `maxRepositories` (Int): How many repositories should be included. Default: `25`.

* `repositoryContributions` (CreatedRepositoryContributionConnection!): A list of repositories owned by the user that the user created in this time range.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `excludeFirst` (Boolean): Should the user's first repository ever be excluded from the result.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ContributionOrder): Ordering options for contributions returned from the connection.

* `restrictedContributionsCount` (Int!): A count of contributions made by the user that the viewer cannot access. Only
  non-zero when the user has chosen to share their private contribution counts.

* `startedAt` (DateTime!): The beginning date and time of this collection.

* `totalCommitContributions` (Int!): How many commits were made by the user in this time span.

* `totalIssueContributions` (Int!): How many issues the user opened.
  * `excludeFirst` (Boolean): Should the user's first issue ever be excluded from this count.
  * `excludePopular` (Boolean): Should the user's most commented issue be excluded from this count.

* `totalPullRequestContributions` (Int!): How many pull requests the user opened.
  * `excludeFirst` (Boolean): Should the user's first pull request ever be excluded from this count.
  * `excludePopular` (Boolean): Should the user's most commented pull request be excluded from this count.

* `totalPullRequestReviewContributions` (Int!): How many pull request reviews the user left.

* `totalRepositoriesWithContributedCommits` (Int!): How many different repositories the user committed to.

* `totalRepositoriesWithContributedIssues` (Int!): How many different repositories the user opened issues in.
  * `excludeFirst` (Boolean): Should the user's first issue ever be excluded from this count.
  * `excludePopular` (Boolean): Should the user's most commented issue be excluded from this count.

* `totalRepositoriesWithContributedPullRequestReviews` (Int!): How many different repositories the user left pull request reviews in.

* `totalRepositoriesWithContributedPullRequests` (Int!): How many different repositories the user opened pull requests in.
  * `excludeFirst` (Boolean): Should the user's first pull request ever be excluded from this count.
  * `excludePopular` (Boolean): Should the user's most commented pull request be excluded from this count.

* `totalRepositoryContributions` (Int!): How many repositories the user created.
  * `excludeFirst` (Boolean): Should the user's first repository ever be excluded from this count.

* `user` (User!): The user who made the contributions in this collection.

## ConvertToDraftEvent

Represents aconvert\_to\_draftevent on a given pull request.

**Implements:** Node, UniformResourceLocatable

### Fields for `ConvertToDraftEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ConvertToDraftEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.
* `resourcePath` (URI!): The HTTP path for this convert to draft event.
* `url` (URI!): The HTTP URL for this convert to draft event.

## ConvertedFromDraftEvent

Represents aconverted\_from\_draftevent on a given issue or pull request.

**Implements:** Node, ProjectV2Event

### Fields for `ConvertedFromDraftEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ConvertedFromDraftEvent object.
* `project` (ProjectV2): Project referenced by event.
* `wasAutomated` (Boolean!): Did this event result from workflow automation?.

## ConvertedNoteToIssueEvent

Represents aconverted\_note\_to\_issueevent on a given issue or pull request.

**Implements:** Node

### Fields for `ConvertedNoteToIssueEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the ConvertedNoteToIssueEvent object.
* `project` (Project): Project referenced by event. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `projectCard` (ProjectCard): Project card referenced by this project event. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `projectColumnName` (String!): Column name referenced by this project event.

## ConvertedToDiscussionEvent

Represents aconverted\_to\_discussionevent on a given issue.

**Implements:** Node

### Fields for `ConvertedToDiscussionEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `discussion` (Discussion): The discussion that the issue was converted into.
* `id` (ID!): The Node ID of the ConvertedToDiscussionEvent object.

## CopilotCodeReviewParameters

Request Copilot code review for new pull requests automatically if the author
has access to Copilot code review and their premium requests quota has not
reached the limit.

### Fields for `CopilotCodeReviewParameters`

* `reviewDraftPullRequests` (Boolean!): Copilot automatically reviews draft pull requests before they are marked as ready for review.
* `reviewOnPush` (Boolean!): Copilot automatically reviews each new push to the pull request.

## CopilotEndpoints

Copilot endpoint information.

### Fields for `CopilotEndpoints`

* `api` (String!): Copilot API endpoint.
* `originTracker` (String!): Copilot origin tracker endpoint.
* `proxy` (String!): Copilot proxy endpoint.
* `telemetry` (String!): Copilot telemetry endpoint.

## CreatedCommitContribution

Represents the contribution a user made by committing to a repository.

**Implements:** Contribution

### Fields for `CreatedCommitContribution`

* `commitCount` (Int!): How many commits were made on this day to this repository by the user.
* `isRestricted` (Boolean!): Whether this contribution is associated with a record you do not have access to. For
  example, your own 'first issue' contribution may have been made on a repository you can no
  longer access.
* `occurredAt` (DateTime!): When this contribution was made.
* `repository` (Repository!): The repository the user made a commit in.
* `resourcePath` (URI!): The HTTP path for this contribution.
* `url` (URI!): The HTTP URL for this contribution.
* `user` (User!): The user who made this contribution.

## CreatedIssueContribution

Represents the contribution a user made on GitHub by opening an issue.

**Implements:** Contribution

### Fields for `CreatedIssueContribution`

* `isRestricted` (Boolean!): Whether this contribution is associated with a record you do not have access to. For
  example, your own 'first issue' contribution may have been made on a repository you can no
  longer access.
* `issue` (Issue!): The issue that was opened.
* `occurredAt` (DateTime!): When this contribution was made.
* `resourcePath` (URI!): The HTTP path for this contribution.
* `url` (URI!): The HTTP URL for this contribution.
* `user` (User!): The user who made this contribution.

## CreatedPullRequestContribution

Represents the contribution a user made on GitHub by opening a pull request.

**Implements:** Contribution

### Fields for `CreatedPullRequestContribution`

* `isRestricted` (Boolean!): Whether this contribution is associated with a record you do not have access to. For
  example, your own 'first issue' contribution may have been made on a repository you can no
  longer access.
* `occurredAt` (DateTime!): When this contribution was made.
* `pullRequest` (PullRequest!): The pull request that was opened.
* `resourcePath` (URI!): The HTTP path for this contribution.
* `url` (URI!): The HTTP URL for this contribution.
* `user` (User!): The user who made this contribution.

## CreatedPullRequestReviewContribution

Represents the contribution a user made by leaving a review on a pull request.

**Implements:** Contribution

### Fields for `CreatedPullRequestReviewContribution`

* `isRestricted` (Boolean!): Whether this contribution is associated with a record you do not have access to. For
  example, your own 'first issue' contribution may have been made on a repository you can no
  longer access.
* `occurredAt` (DateTime!): When this contribution was made.
* `pullRequest` (PullRequest!): The pull request the user reviewed.
* `pullRequestReview` (PullRequestReview!): The review the user left on the pull request.
* `repository` (Repository!): The repository containing the pull request that the user reviewed.
* `resourcePath` (URI!): The HTTP path for this contribution.
* `url` (URI!): The HTTP URL for this contribution.
* `user` (User!): The user who made this contribution.

## CreatedRepositoryContribution

Represents the contribution a user made on GitHub by creating a repository.

**Implements:** Contribution

### Fields for `CreatedRepositoryContribution`

* `isRestricted` (Boolean!): Whether this contribution is associated with a record you do not have access to. For
  example, your own 'first issue' contribution may have been made on a repository you can no
  longer access.
* `occurredAt` (DateTime!): When this contribution was made.
* `repository` (Repository!): The repository that was created.
* `resourcePath` (URI!): The HTTP path for this contribution.
* `url` (URI!): The HTTP URL for this contribution.
* `user` (User!): The user who made this contribution.

## CrossReferencedEvent

Represents a mention made by one issue or pull request to another.

**Implements:** Node, UniformResourceLocatable

### Fields for `CrossReferencedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the CrossReferencedEvent object.
* `isCrossRepository` (Boolean!): Reference originated in a different repository.
* `referencedAt` (DateTime!): Identifies when the reference was made.
* `resourcePath` (URI!): The HTTP path for this pull request.
* `source` (ReferencedSubject!): Issue or pull request that made the reference.
* `target` (ReferencedSubject!): Issue or pull request to which the reference was made.
* `url` (URI!): The HTTP URL for this pull request.
* `willCloseTarget` (Boolean!): Checks if the target will be closed when the source is merged.

## CvssSeverities

The Common Vulnerability Scoring System.

### Fields for `CvssSeverities`

* `cvssV3` (CVSS): The CVSS v3 severity associated with this advisory.
* `cvssV4` (CVSS): The CVSS v4 severity associated with this advisory.

## DemilestonedEvent

Represents ademilestonedevent on a given issue or pull request.

**Implements:** Node

### Fields for `DemilestonedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the DemilestonedEvent object.
* `milestoneTitle` (String!): Identifies the milestone title associated with thedemilestonedevent.
* `subject` (MilestoneItem!): Object referenced by event.

## DependabotUpdate

A Dependabot Update for a dependency in a repository.

**Implements:** RepositoryNode

### Fields for `DependabotUpdate`

* `error` (DependabotUpdateError): The error from a dependency update.
* `pullRequest` (PullRequest): The associated pull request.
* `repository` (Repository!): The repository associated with this node.

## DependabotUpdateError

An error produced from a Dependabot Update.

### Fields for `DependabotUpdateError`

* `body` (String!): The body of the error.
* `errorType` (String!): The error code.
* `title` (String!): The title of the error.

## DependencyGraphDependency

A dependency manifest entry.

### Fields for `DependencyGraphDependency`

* `hasDependencies` (Boolean!): Does the dependency itself have dependencies?.
* `packageLabel` (String!): The original name of the package, as it appears in the manifest. **Deprecated:** packageLabel will be removed. Use normalized packageName field instead. Removal on 2022-10-01 UTC.
* `packageManager` (String): The dependency package manager.
* `packageName` (String!): The name of the package in the canonical form used by the package manager.
* `packageUrl` (URI): Public preview: The dependency package URL.
* `relationship` (String!): Public preview: The relationship of the dependency. Can be direct, transitive, or unknown.
* `repository` (Repository): The repository containing the package.
* `requirements` (String!): The dependency version requirements.

## DependencyGraphManifest

Dependency manifest for a repository.

**Implements:** Node

### Fields for `DependencyGraphManifest`

* `blobPath` (String!): Path to view the manifest file blob.
* `dependencies` (DependencyGraphDependencyConnection): A list of manifest dependencies. *(Pagination: `after`, `before`, `first`, `last`)*
* `dependenciesCount` (Int): The number of dependencies listed in the manifest.
* `exceedsMaxSize` (Boolean!): Is the manifest too big to parse?.
* `filename` (String!): Fully qualified manifest filename.
* `id` (ID!): The Node ID of the DependencyGraphManifest object.
* `parseable` (Boolean!): Were we able to parse the manifest?.
* `repository` (Repository!): The repository containing the manifest.

## DeployKey

A repository deploy key.

**Implements:** Node

### Fields for `DeployKey`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `enabled` (Boolean!): Whether or not the deploy key is enabled by policy at the Enterprise or Organization level.
* `id` (ID!): The Node ID of the DeployKey object.
* `key` (String!): The deploy key.
* `readOnly` (Boolean!): Whether or not the deploy key is read only.
* `title` (String!): The deploy key title.
* `verified` (Boolean!): Whether or not the deploy key has been verified.

## DeployedEvent

Represents adeployedevent on a given pull request.

**Implements:** Node

### Fields for `DeployedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `deployment` (Deployment!): The deployment associated with thedeployedevent.
* `id` (ID!): The Node ID of the DeployedEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.
* `ref` (Ref): The ref associated with thedeployedevent.

## Deployment

Represents triggered deployment instance.

**Implements:** Node

### Fields for `Deployment`

* `commit` (Commit): Identifies the commit sha of the deployment.
* `commitOid` (String!): Identifies the oid of the deployment commit, even if the commit has been deleted.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor!): Identifies the actor who triggered the deployment.
* `databaseId` (Int): Identifies the primary key from the database.
* `description` (String): The deployment description.
* `environment` (String): The latest environment to which this deployment was made.
* `id` (ID!): The Node ID of the Deployment object.
* `latestEnvironment` (String): The latest environment to which this deployment was made.
* `latestStatus` (DeploymentStatus): The latest status of this deployment.
* `originalEnvironment` (String): The original environment to which this deployment was made.
* `payload` (String): Extra information that a deployment system might need.
* `ref` (Ref): Identifies the Ref of the deployment, if the deployment was created by ref.
* `repository` (Repository!): Identifies the repository associated with the deployment.
* `state` (DeploymentState): The current state of the deployment.
* `statuses` (DeploymentStatusConnection): A list of statuses associated with the deployment. *(Pagination: `after`, `before`, `first`, `last`)*
* `task` (String): The deployment task.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## DeploymentEnvironmentChangedEvent

Represents adeployment\_environment\_changedevent on a given pull request.

**Implements:** Node

### Fields for `DeploymentEnvironmentChangedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `deploymentStatus` (DeploymentStatus!): The deployment status that updated the deployment environment.
* `id` (ID!): The Node ID of the DeploymentEnvironmentChangedEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.

## DeploymentProtectionRule

A protection rule.

### Fields for `DeploymentProtectionRule`

* `databaseId` (Int): Identifies the primary key from the database.
* `preventSelfReview` (Boolean): Whether deployments to this environment can be approved by the user who created the deployment.
* `reviewers` (DeploymentReviewerConnection!): The teams or users that can review the deployment. *(Pagination: `after`, `before`, `first`, `last`)*
* `timeout` (Int!): The timeout in minutes for this protection rule.
* `type` (DeploymentProtectionRuleType!): The type of protection rule.

## DeploymentRequest

A request to deploy a workflow run to an environment.

### Fields for `DeploymentRequest`

* `currentUserCanApprove` (Boolean!): Whether or not the current user can approve the deployment.
* `environment` (Environment!): The target environment of the deployment.
* `reviewers` (DeploymentReviewerConnection!): The teams or users that can review the deployment. *(Pagination: `after`, `before`, `first`, `last`)*
* `waitTimer` (Int!): The wait timer in minutes configured in the environment.
* `waitTimerStartedAt` (DateTime): The wait timer in minutes configured in the environment.

## DeploymentReview

A deployment review.

**Implements:** Node

### Fields for `DeploymentReview`

* `comment` (String!): The comment the user left.
* `databaseId` (Int): Identifies the primary key from the database.
* `environments` (EnvironmentConnection!): The environments approved or rejected. *(Pagination: `after`, `before`, `first`, `last`)*
* `id` (ID!): The Node ID of the DeploymentReview object.
* `state` (DeploymentReviewState!): The decision of the user.
* `user` (User!): The user that reviewed the deployment.

## DeploymentStatus

Describes the status of a given deployment attempt.

**Implements:** Node

### Fields for `DeploymentStatus`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor!): Identifies the actor who triggered the deployment.
* `deployment` (Deployment!): Identifies the deployment associated with status.
* `description` (String): Identifies the description of the deployment.
* `environment` (String): Identifies the environment of the deployment at the time of this deployment status.
* `environmentUrl` (URI): Identifies the environment URL of the deployment.
* `id` (ID!): The Node ID of the DeploymentStatus object.
* `logUrl` (URI): Identifies the log URL of the deployment.
* `state` (DeploymentStatusState!): Identifies the current state of the deployment.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## DisconnectedEvent

Represents adisconnectedevent on a given issue or pull request.

**Implements:** Node

### Fields for `DisconnectedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the DisconnectedEvent object.
* `isCrossRepository` (Boolean!): Reference originated in a different repository.
* `source` (ReferencedSubject!): Issue or pull request from which the issue was disconnected.
* `subject` (ReferencedSubject!): Issue or pull request which was disconnected.

## Discussion

A discussion in a repository.

**Implements:** Closable, Comment, Deletable, Labelable, Lockable, Node, Reactable, RepositoryNode, Subscribable, Updatable, Votable

### Fields for `Discussion`

* `activeLockReason` (LockReason): Reason that the conversation was locked.

* `answer` (DiscussionComment): The comment chosen as this discussion's answer, if any.

* `answerChosenAt` (DateTime): The time when a user chose this discussion's answer, if answered.

* `answerChosenBy` (Actor): The user who chose this discussion's answer, if answered.

* `author` (Actor): The actor who authored the discussion.

* `authorAssociation` (CommentAuthorAssociation!): Author's association with the subject of the comment.

* `body` (String!): The main text of the discussion post.

* `bodyHTML` (HTML!): The body rendered to HTML.

* `bodyText` (String!): The body rendered to text.

* `category` (DiscussionCategory!): The category for this discussion.

* `closed` (Boolean!): Indicates if the object is closed (definition of closed may depend on type).

* `closedAt` (DateTime): Identifies the date and time when the object was closed.

* `comments` (DiscussionCommentConnection!): The replies to the discussion. *(Pagination: `after`, `before`, `first`, `last`)*

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.

* `databaseId` (Int): Identifies the primary key from the database.

* `editor` (Actor): The actor who edited the comment.

* `id` (ID!): The Node ID of the Discussion object.

* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.

* `isAnswered` (Boolean): Only return answered/unanswered discussions.

* `labels` (LabelConnection): A list of labels associated with the object.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (LabelOrder): Ordering options for labels returned from the connection.

* `lastEditedAt` (DateTime): The moment the editor made the last edit.

* `locked` (Boolean!): true if the object is locked.

* `number` (Int!): The number identifying this discussion within the repository.

* `poll` (DiscussionPoll): The poll associated with this discussion, if one exists.

* `publishedAt` (DateTime): Identifies when the comment was published at.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `repository` (Repository!): The repository associated with this node.

* `resourcePath` (URI!): The path for this discussion.

* `stateReason` (DiscussionStateReason): Identifies the reason for the discussion's state.

* `title` (String!): The title of this discussion.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `upvoteCount` (Int!): Number of upvotes that this subject has received.

* `url` (URI!): The URL for this discussion.

* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*

* `viewerCanClose` (Boolean!): Indicates if the object can be closed by the viewer.

* `viewerCanDelete` (Boolean!): Check if the current viewer can delete this object.

* `viewerCanLabel` (Boolean!): Indicates if the viewer can edit labels for this object.

* `viewerCanReact` (Boolean!): Can user react to this subject.

* `viewerCanReopen` (Boolean!): Indicates if the object can be reopened by the viewer.

* `viewerCanSubscribe` (Boolean!): Check if the viewer is able to change their subscription status for the repository.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

* `viewerCanUpvote` (Boolean!): Whether or not the current user can add or remove an upvote on this subject.

* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

* `viewerHasUpvoted` (Boolean!): Whether or not the current user has already upvoted this subject.

* `viewerSubscription` (SubscriptionState): Identifies if the viewer is watching, not watching, or ignoring the subscribable entity.

## DiscussionCategory

A category for discussions in a repository.

**Implements:** Node, RepositoryNode

### Fields for `DiscussionCategory`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `description` (String): A description of this category.
* `emoji` (String!): An emoji representing this category.
* `emojiHTML` (HTML!): This category's emoji rendered as HTML.
* `id` (ID!): The Node ID of the DiscussionCategory object.
* `isAnswerable` (Boolean!): Whether or not discussions in this category support choosing an answer with the markDiscussionCommentAsAnswer mutation.
* `name` (String!): The name of this category.
* `repository` (Repository!): The repository associated with this node.
* `slug` (String!): The slug of this category.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## DiscussionComment

A comment on a discussion.

**Implements:** Comment, Deletable, Minimizable, Node, Reactable, Updatable, UpdatableComment, Votable

### Fields for `DiscussionComment`

* `author` (Actor): The actor who authored the comment.

* `authorAssociation` (CommentAuthorAssociation!): Author's association with the subject of the comment.

* `body` (String!): The body as Markdown.

* `bodyHTML` (HTML!): The body rendered to HTML.

* `bodyText` (String!): The body rendered to text.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.

* `databaseId` (Int): Identifies the primary key from the database.

* `deletedAt` (DateTime): The time when this replied-to comment was deleted.

* `discussion` (Discussion): The discussion this comment was created in.

* `editor` (Actor): The actor who edited the comment.

* `id` (ID!): The Node ID of the DiscussionComment object.

* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.

* `isAnswer` (Boolean!): Has this comment been chosen as the answer of its discussion?.

* `isMinimized` (Boolean!): Returns whether or not a comment has been minimized.

* `lastEditedAt` (DateTime): The moment the editor made the last edit.

* `minimizedReason` (String): Returns why the comment was minimized. One of abuse, off-topic,
  outdated, resolved, duplicate, spam, and low-quality. Note that the
  case and formatting of these values differs from the inputs to the
  MinimizeComment mutation.

* `publishedAt` (DateTime): Identifies when the comment was published at.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `replies` (DiscussionCommentConnection!): The threaded replies to this comment. *(Pagination: `after`, `before`, `first`, `last`)*

* `replyTo` (DiscussionComment): The discussion comment this comment is a reply to.

* `resourcePath` (URI!): The path for this discussion comment.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `upvoteCount` (Int!): Number of upvotes that this subject has received.

* `url` (URI!): The URL for this discussion comment.

* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*

* `viewerCanDelete` (Boolean!): Check if the current viewer can delete this object.

* `viewerCanMarkAsAnswer` (Boolean!): Can the current user mark this comment as an answer?.

* `viewerCanMinimize` (Boolean!): Check if the current viewer can minimize this object.

* `viewerCanReact` (Boolean!): Can user react to this subject.

* `viewerCanUnmarkAsAnswer` (Boolean!): Can the current user unmark this comment as an answer?.

* `viewerCanUnminimize` (Boolean!): Check if the current viewer can unminimize this object.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

* `viewerCanUpvote` (Boolean!): Whether or not the current user can add or remove an upvote on this subject.

* `viewerCannotUpdateReasons` (\[CommentCannotUpdateReason!]!): Reasons why the current viewer can not update this comment.

* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

* `viewerHasUpvoted` (Boolean!): Whether or not the current user has already upvoted this subject.

## DiscussionPoll

A poll for a discussion.

**Implements:** Node

### Fields for `DiscussionPoll`

* `discussion` (Discussion): The discussion that this poll belongs to.

* `id` (ID!): The Node ID of the DiscussionPoll object.

* `options` (DiscussionPollOptionConnection): The options for this poll.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (DiscussionPollOptionOrder): How to order the options for the discussion poll.

* `question` (String!): The question that is being asked by this poll.

* `totalVoteCount` (Int!): The total number of votes that have been cast for this poll.

* `viewerCanVote` (Boolean!): Indicates if the viewer has permission to vote in this poll.

* `viewerHasVoted` (Boolean!): Indicates if the viewer has voted for any option in this poll.

## DiscussionPollOption

An option for a discussion poll.

**Implements:** Node

### Fields for `DiscussionPollOption`

* `id` (ID!): The Node ID of the DiscussionPollOption object.
* `option` (String!): The text for this option.
* `poll` (DiscussionPoll): The discussion poll that this option belongs to.
* `totalVoteCount` (Int!): The total number of votes that have been cast for this option.
* `viewerHasVoted` (Boolean!): Indicates if the viewer has voted for this option in the poll.

## DraftIssue

A draft issue within a project.

**Implements:** Node

### Fields for `DraftIssue`

* `assignees` (UserConnection!): A list of users to assigned to this draft issue. *(Pagination: `after`, `before`, `first`, `last`)*
* `body` (String!): The body of the draft issue.
* `bodyHTML` (HTML!): The body of the draft issue rendered to HTML.
* `bodyText` (String!): The body of the draft issue rendered to text.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor): The actor who created this draft issue.
* `id` (ID!): The Node ID of the DraftIssue object.
* `projectV2Items` (ProjectV2ItemConnection!): List of items linked with the draft issue (currently draft issue can be linked to only one item). *(Pagination: `after`, `before`, `first`, `last`)*
* `projectsV2` (ProjectV2Connection!): Projects that link to this draft issue (currently draft issue can be linked to only one project). *(Pagination: `after`, `before`, `first`, `last`)*
* `title` (String!): The title of the draft issue.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## EPSS

The Exploit Prediction Scoring System.

### Fields for `EPSS`

* `percentage` (Float): The EPSS percentage represents the likelihood of a CVE being exploited.
* `percentile` (Float): The EPSS percentile represents the relative rank of the CVE's likelihood of being exploited compared to other CVEs.

## Enterprise

An account to manage multiple organizations with consolidated policy and billing.

**Implements:** Node

### Fields for `Enterprise`

* `announcementBanner` (AnnouncementBanner): The announcement banner set on this enterprise, if any. Only visible to members of the enterprise.

* `avatarUrl` (URI!): A URL pointing to the enterprise's public avatar.
  * `size` (Int): The size of the resulting square image.

* `billingEmail` (String): The enterprise's billing email.

* `billingInfo` (EnterpriseBillingInfo): Enterprise billing information visible to enterprise billing managers.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `description` (String): The description of the enterprise.

* `descriptionHTML` (HTML!): The description of the enterprise as HTML.

* `id` (ID!): The Node ID of the Enterprise object.

* `location` (String): The location of the enterprise.

* `members` (EnterpriseMemberConnection!): A list of users who are members of this enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `deployment` (EnterpriseUserDeployment): Only return members within the selected GitHub Enterprise deployment.
  * `first` (Int): Returns the first n elements from the list.
  * `hasTwoFactorEnabled` (Boolean): Only return members with this two-factor authentication status. Does not
    include members who only have an account on a GitHub Enterprise Server instance.
    Upcoming Change on 2025-04-01 UTC
    Description: hasTwoFactorEnabled will be removed. Use two\_factor\_method\_security instead.
    Reason: has\_two\_factor\_enabled will be removed.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseMemberOrder): Ordering options for members returned from the connection.
  * `organizationLogins` (\[String!]): Only return members within the organizations with these logins.
  * `query` (String): The search string to look for.
  * `role` (EnterpriseUserAccountMembershipRole): The role of the user in the enterprise organization or server.
  * `twoFactorMethodSecurity` (TwoFactorCredentialSecurityType): Only return members with this type of two-factor authentication method. Does
    not include members who only have an account on a GitHub Enterprise Server instance.

* `name` (String!): The name of the enterprise.

* `organizations` (OrganizationConnection!): A list of organizations that belong to this enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations returned from the connection.
  * `query` (String): The search string to look for.
  * `viewerOrganizationRole` (RoleInOrganization): The viewer's role in an organization.

* `ownerInfo` (EnterpriseOwnerInfo): Enterprise information visible to enterprise owners or enterprise owners'
  personal access tokens (classic) with read:enterprise or admin:enterprise scope.

* `readme` (String): The raw content of the enterprise README.

* `readmeHTML` (HTML!): The content of the enterprise README as HTML.

* `repositoryCustomProperties` (RepositoryCustomPropertyConnection): A list of repository custom properties for this enterprise. *(Pagination: `after`, `before`, `first`, `last`)*

* `repositoryCustomProperty` (RepositoryCustomProperty): Returns a single repository custom property for the current enterprise by name.
  * `propertyName` (String!): The name of the repository custom property to be returned.

* `resourcePath` (URI!): The HTTP path for this enterprise.

* `ruleset` (RepositoryRuleset): Returns a single ruleset from the current enterprise by ID.
  * `databaseId` (Int!): The ID of the ruleset to be returned.

* `rulesets` (RepositoryRulesetConnection): A list of rulesets for this enterprise. *(Pagination: `after`, `before`, `first`, `last`)*

* `securityContactEmail` (String): The enterprise's security contact email address.

* `slug` (String!): The URL-friendly identifier for the enterprise.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this enterprise.

* `userNamespaceRepositories` (UserNamespaceRepositoryConnection!): A list of repositories that belong to users. Only available for enterprises with Enterprise Managed Users.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder): Ordering options for repositories returned from the connection.
  * `query` (String): The search string to look for.

* `viewerIsAdmin` (Boolean!): Is the current viewer an admin of this enterprise?.

* `websiteUrl` (URI): The URL of the enterprise website.

## EnterpriseAdministratorEdge

A User who is an administrator of an enterprise.

### Fields for `EnterpriseAdministratorEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (User): The item at the end of the edge.
* `role` (EnterpriseAdministratorRole!): The role of the administrator.

## EnterpriseAdministratorInvitation

An invitation for a user to become an owner or billing manager of an enterprise.

**Implements:** Node

### Fields for `EnterpriseAdministratorInvitation`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `email` (String): The email of the person who was invited to the enterprise.
* `enterprise` (Enterprise!): The enterprise the invitation is for.
* `id` (ID!): The Node ID of the EnterpriseAdministratorInvitation object.
* `invitee` (User): The user who was invited to the enterprise.
* `inviter` (User): The user who created the invitation.
* `role` (EnterpriseAdministratorRole!): The invitee's pending role in the enterprise (owner or billing\_manager).

## EnterpriseBillingInfo

Enterprise billing information visible to enterprise billing managers and owners.

### Fields for `EnterpriseBillingInfo`

* `allLicensableUsersCount` (Int!): The number of licenseable users/emails across the enterprise.
* `assetPacks` (Int!): The number of data packs used by all organizations owned by the enterprise.
* `bandwidthQuota` (Float!): The bandwidth quota in GB for all organizations owned by the enterprise.
* `bandwidthUsage` (Float!): The bandwidth usage in GB for all organizations owned by the enterprise.
* `bandwidthUsagePercentage` (Int!): The bandwidth usage as a percentage of the bandwidth quota.
* `storageQuota` (Float!): The storage quota in GB for all organizations owned by the enterprise.
* `storageUsage` (Float!): The storage usage in GB for all organizations owned by the enterprise.
* `storageUsagePercentage` (Int!): The storage usage as a percentage of the storage quota.
* `totalAvailableLicenses` (Int!): The number of available licenses across all owned organizations based on the unique number of billable users.
* `totalLicenses` (Int!): The total number of licenses allocated.

## EnterpriseFailedInvitationConnection

The connection type for OrganizationInvitation.

### Fields for `EnterpriseFailedInvitationConnection`

* `edges` (\[EnterpriseFailedInvitationEdge]): A list of edges.
* `nodes` (\[OrganizationInvitation]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.
* `totalUniqueUserCount` (Int!): Identifies the total count of unique users in the connection.

## EnterpriseIdentityProvider

An identity provider configured to provision identities for an enterprise.
Visible to enterprise owners or enterprise owners' personal access tokens
(classic) with read:enterprise or admin:enterprise scope.

**Implements:** Node

### Fields for `EnterpriseIdentityProvider`

* `digestMethod` (SamlDigestAlgorithm): The digest algorithm used to sign SAML requests for the identity provider.

* `enterprise` (Enterprise): The enterprise this identity provider belongs to.

* `externalIdentities` (ExternalIdentityConnection!): ExternalIdentities provisioned by this identity provider.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `login` (String): Filter to external identities with the users login.
  * `membersOnly` (Boolean): Filter to external identities with valid org membership only.
  * `userName` (String): Filter to external identities with the users userName/NameID attribute.

* `id` (ID!): The Node ID of the EnterpriseIdentityProvider object.

* `idpCertificate` (X509Certificate): The x509 certificate used by the identity provider to sign assertions and responses.

* `issuer` (String): The Issuer Entity ID for the SAML identity provider.

* `recoveryCodes` (\[String!]): Recovery codes that can be used by admins to access the enterprise if the identity provider is unavailable.

* `signatureMethod` (SamlSignatureAlgorithm): The signature algorithm used to sign SAML requests for the identity provider.

* `ssoUrl` (URI): The URL endpoint for the identity provider's SAML SSO.

## EnterpriseMemberInvitation

An invitation for a user to become an unaffiliated member of an enterprise.

**Implements:** Node

### Fields for `EnterpriseMemberInvitation`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `email` (String): The email of the person who was invited to the enterprise.
* `enterprise` (Enterprise!): The enterprise the invitation is for.
* `id` (ID!): The Node ID of the EnterpriseMemberInvitation object.
* `invitee` (User): The user who was invited to the enterprise.
* `inviter` (User): The user who created the invitation.

## EnterpriseOrganizationMembershipEdge

An enterprise organization that a user is a member of.

### Fields for `EnterpriseOrganizationMembershipEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (Organization): The item at the end of the edge.
* `role` (EnterpriseUserAccountMembershipRole!): The role of the user in the enterprise membership.

## EnterpriseOutsideCollaboratorEdge

A User who is an outside collaborator of an enterprise through one or more organizations.

### Fields for `EnterpriseOutsideCollaboratorEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (User): The item at the end of the edge.
* `repositories` (EnterpriseRepositoryInfoConnection!): The enterprise organization repositories this user is a member of.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder): Ordering options for repositories.

## EnterpriseOwnerInfo

Enterprise information visible to enterprise owners or enterprise owners'
personal access tokens (classic) with read:enterprise or admin:enterprise scope.

### Fields for `EnterpriseOwnerInfo`

* `admins` (EnterpriseAdministratorConnection!): A list of all of the administrators for this enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `hasTwoFactorEnabled` (Boolean): Only return administrators with this two-factor authentication status.
    Upcoming Change on 2025-04-01 UTC
    Description: hasTwoFactorEnabled will be removed. Use two\_factor\_method\_security instead.
    Reason: has\_two\_factor\_enabled will be removed.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseMemberOrder): Ordering options for administrators returned from the connection.
  * `organizationLogins` (\[String!]): Only return members within the organizations with these logins.
  * `query` (String): The search string to look for.
  * `role` (EnterpriseAdministratorRole): The role to filter by.
  * `twoFactorMethodSecurity` (TwoFactorCredentialSecurityType): Only return outside collaborators with this type of two-factor authentication method.

* `affiliatedUsersWithTwoFactorDisabled` (UserConnection!): A list of users in the enterprise who currently have two-factor authentication disabled. *(Pagination: `after`, `before`, `first`, `last`)*

* `affiliatedUsersWithTwoFactorDisabledExist` (Boolean!): Whether or not affiliated users with two-factor authentication disabled exist in the enterprise.

* `allowPrivateRepositoryForkingSetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether private repository forking is enabled for repositories in organizations in this enterprise.

* `allowPrivateRepositoryForkingSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided private repository forking setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `allowPrivateRepositoryForkingSettingPolicyValue` (EnterpriseAllowPrivateRepositoryForkingPolicyValue): The value for the allow private repository forking policy on the enterprise.

* `defaultRepositoryPermissionSetting` (EnterpriseDefaultRepositoryPermissionSettingValue!): The setting value for base repository permissions for organizations in this enterprise.

* `defaultRepositoryPermissionSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided base repository permission.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (DefaultRepositoryPermissionField!): The permission to find organizations for.

* `domains` (VerifiableDomainConnection!): A list of domains owned by the enterprise. Visible to enterprise owners or
  enterprise owners' personal access tokens (classic) with admin:enterprise scope.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `isApproved` (Boolean): Filter whether or not the domain is approved.
  * `isVerified` (Boolean): Filter whether or not the domain is verified.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (VerifiableDomainOrder): Ordering options for verifiable domains returned.

* `enterpriseServerInstallations` (EnterpriseServerInstallationConnection!): Enterprise Server installations owned by the enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `connectedOnly` (Boolean): Whether or not to only return installations discovered via GitHub Connect.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseServerInstallationOrder): Ordering options for Enterprise Server installations returned.

* `failedInvitations` (EnterpriseFailedInvitationConnection!): A list of failed invitations in the enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `query` (String): The search string to look for.

* `ipAllowListEnabledSetting` (IpAllowListEnabledSettingValue!): The setting value for whether the enterprise has an IP allow list enabled.

* `ipAllowListEntries` (IpAllowListEntryConnection!): The IP addresses that are allowed to access resources owned by the enterprise.
  Visible to enterprise owners or enterprise owners' personal access tokens
  (classic) with admin:enterprise scope.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IpAllowListEntryOrder): Ordering options for IP allow list entries returned.

* `ipAllowListForInstalledAppsEnabledSetting` (IpAllowListForInstalledAppsEnabledSettingValue!): The setting value for whether the enterprise has IP allow list configuration for installed GitHub Apps enabled.

* `ipAllowListUserLevelEnforcementEnabledSetting` (IpAllowListUserLevelEnforcementEnabledSettingValue!): The setting value for whether the enterprise has IP allow list user-level enforcement enabled.

* `isUpdatingDefaultRepositoryPermission` (Boolean!): Whether or not the base repository permission is currently being updated.

* `isUpdatingTwoFactorRequirement` (Boolean!): Whether the two-factor authentication requirement is currently being enforced.

* `membersCanChangeRepositoryVisibilitySetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether organization members with admin permissions on a
  repository can change repository visibility.

* `membersCanChangeRepositoryVisibilitySettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided can change repository visibility setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `membersCanCreateInternalRepositoriesSetting` (Boolean): The setting value for whether members of organizations in the enterprise can create internal repositories.

* `membersCanCreatePrivateRepositoriesSetting` (Boolean): The setting value for whether members of organizations in the enterprise can create private repositories.

* `membersCanCreatePublicRepositoriesSetting` (Boolean): The setting value for whether members of organizations in the enterprise can create public repositories.

* `membersCanCreateRepositoriesSetting` (EnterpriseMembersCanCreateRepositoriesSettingValue): The setting value for whether members of organizations in the enterprise can create repositories.

* `membersCanCreateRepositoriesSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided repository creation setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (OrganizationMembersCanCreateRepositoriesSettingValue!): The setting to find organizations for.

* `membersCanDeleteIssuesSetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether members with admin permissions for repositories can delete issues.

* `membersCanDeleteIssuesSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided members can delete issues setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `membersCanDeleteRepositoriesSetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether members with admin permissions for repositories can delete or transfer repositories.

* `membersCanDeleteRepositoriesSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided members can delete repositories setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `membersCanInviteCollaboratorsSetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether members of organizations in the enterprise can invite outside collaborators.

* `membersCanInviteCollaboratorsSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided members can invite collaborators setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `membersCanMakePurchasesSetting` (EnterpriseMembersCanMakePurchasesSettingValue!): Indicates whether members of this enterprise's organizations can purchase additional services for those organizations.

* `membersCanUpdateProtectedBranchesSetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether members with admin permissions for repositories can update protected branches.

* `membersCanUpdateProtectedBranchesSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided members can update protected branches setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `membersCanViewDependencyInsightsSetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether members can view dependency insights.

* `membersCanViewDependencyInsightsSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided members can view dependency insights setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `notificationDeliveryRestrictionEnabledSetting` (NotificationRestrictionSettingValue!): Indicates if email notification delivery for this enterprise is restricted to verified or approved domains.

* `oidcProvider` (OIDCProvider): The OIDC Identity Provider for the enterprise.

* `organizationProjectsSetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether organization projects are enabled for organizations in this enterprise.

* `organizationProjectsSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided organization projects setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `outsideCollaborators` (EnterpriseOutsideCollaboratorConnection!): A list of outside collaborators across the repositories in the enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `hasTwoFactorEnabled` (Boolean): Only return outside collaborators with this two-factor authentication status.
    Upcoming Change on 2025-04-01 UTC
    Description: hasTwoFactorEnabled will be removed. Use two\_factor\_method\_security instead.
    Reason: has\_two\_factor\_enabled will be removed.
  * `last` (Int): Returns the last n elements from the list.
  * `login` (String): The login of one specific outside collaborator.
  * `orderBy` (EnterpriseMemberOrder): Ordering options for outside collaborators returned from the connection.
  * `organizationLogins` (\[String!]): Only return outside collaborators within the organizations with these logins.
  * `query` (String): The search string to look for.
  * `twoFactorMethodSecurity` (TwoFactorCredentialSecurityType): Only return outside collaborators with this type of two-factor authentication method.
  * `visibility` (RepositoryVisibility): Only return outside collaborators on repositories with this visibility.

* `pendingAdminInvitations` (EnterpriseAdministratorInvitationConnection!): A list of pending administrator invitations for the enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseAdministratorInvitationOrder): Ordering options for pending enterprise administrator invitations returned from the connection.
  * `query` (String): The search string to look for.
  * `role` (EnterpriseAdministratorRole): The role to filter by.

* `pendingCollaboratorInvitations` (RepositoryInvitationConnection!): A list of pending collaborator invitations across the repositories in the enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryInvitationOrder): Ordering options for pending repository collaborator invitations returned from the connection.
  * `query` (String): The search string to look for.

* `pendingMemberInvitations` (EnterprisePendingMemberInvitationConnection!): A list of pending member invitations for organizations in the enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `invitationSource` (OrganizationInvitationSource): Only return invitations matching this invitation source.
  * `last` (Int): Returns the last n elements from the list.
  * `organizationLogins` (\[String!]): Only return invitations within the organizations with these logins.
  * `query` (String): The search string to look for.

* `pendingUnaffiliatedMemberInvitations` (EnterpriseMemberInvitationConnection!): A list of pending unaffiliated member invitations for the enterprise.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseMemberInvitationOrder): Ordering options for pending enterprise member invitations returned from the connection.
  * `query` (String): The search string to look for.

* `repositoryDeployKeySetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether deploy keys are enabled for repositories in organizations in this enterprise.

* `repositoryDeployKeySettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided deploy keys setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `repositoryProjectsSetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether repository projects are enabled in this enterprise.

* `repositoryProjectsSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the provided repository projects setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

* `samlIdentityProvider` (EnterpriseIdentityProvider): The SAML Identity Provider for the enterprise.

* `samlIdentityProviderSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the SAML single sign-on setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (IdentityProviderConfigurationState!): The setting value to find organizations for.

* `supportEntitlements` (EnterpriseMemberConnection!): A list of members with a support entitlement.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseMemberOrder): Ordering options for support entitlement users returned from the connection.

* `teamDiscussionsSetting` (EnterpriseEnabledDisabledSettingValue!): The setting value for whether team discussions are enabled for organizations in this enterprise. **Deprecated:** The Team Discussions feature is deprecated in favor of Organization Discussions. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Removal on 2024-07-01 UTC.

* `twoFactorDisallowedMethodsSetting` (EnterpriseDisallowedMethodsSettingValue!): The setting value for what methods of two-factor authentication the enterprise prevents its users from having.

* `twoFactorRequiredSetting` (EnterpriseEnabledSettingValue!): The setting value for whether the enterprise requires two-factor authentication for its organizations and users.

* `twoFactorRequiredSettingOrganizations` (OrganizationConnection!): A list of enterprise organizations configured with the two-factor authentication setting value.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations with this setting.
  * `value` (Boolean!): The setting value to find organizations for.

## EnterprisePendingMemberInvitationConnection

The connection type for OrganizationInvitation.

### Fields for `EnterprisePendingMemberInvitationConnection`

* `edges` (\[EnterprisePendingMemberInvitationEdge]): A list of edges.
* `nodes` (\[OrganizationInvitation]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.
* `totalUniqueUserCount` (Int!): Identifies the total count of unique users in the connection.

## EnterpriseRepositoryInfo

A subset of repository information queryable from an enterprise.

**Implements:** Node

### Fields for `EnterpriseRepositoryInfo`

* `id` (ID!): The Node ID of the EnterpriseRepositoryInfo object.
* `isPrivate` (Boolean!): Identifies if the repository is private or internal.
* `name` (String!): The repository's name.
* `nameWithOwner` (String!): The repository's name with owner.

## EnterpriseServerInstallation

An Enterprise Server installation.

**Implements:** Node

### Fields for `EnterpriseServerInstallation`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `customerName` (String!): The customer name to which the Enterprise Server installation belongs.

* `hostName` (String!): The host name of the Enterprise Server installation.

* `id` (ID!): The Node ID of the EnterpriseServerInstallation object.

* `isConnected` (Boolean!): Whether or not the installation is connected to an Enterprise Server installation via GitHub Connect.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `userAccounts` (EnterpriseServerUserAccountConnection!): User accounts on this Enterprise Server installation.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseServerUserAccountOrder): Ordering options for Enterprise Server user accounts returned from the connection.

* `userAccountsUploads` (EnterpriseServerUserAccountsUploadConnection!): User accounts uploads for the Enterprise Server installation.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseServerUserAccountsUploadOrder): Ordering options for Enterprise Server user accounts uploads returned from the connection.

## EnterpriseServerInstallationMembershipEdge

An Enterprise Server installation that a user is a member of.

### Fields for `EnterpriseServerInstallationMembershipEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (EnterpriseServerInstallation): The item at the end of the edge.
* `role` (EnterpriseUserAccountMembershipRole!): The role of the user in the enterprise membership.

## EnterpriseServerUserAccount

A user account on an Enterprise Server installation.

**Implements:** Node

### Fields for `EnterpriseServerUserAccount`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `emails` (EnterpriseServerUserAccountEmailConnection!): User emails belonging to this user account.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseServerUserAccountEmailOrder): Ordering options for Enterprise Server user account emails returned from the connection.

* `enterpriseServerInstallation` (EnterpriseServerInstallation!): The Enterprise Server installation on which this user account exists.

* `id` (ID!): The Node ID of the EnterpriseServerUserAccount object.

* `isSiteAdmin` (Boolean!): Whether the user account is a site administrator on the Enterprise Server installation.

* `login` (String!): The login of the user account on the Enterprise Server installation.

* `profileName` (String): The profile name of the user account on the Enterprise Server installation.

* `remoteCreatedAt` (DateTime!): The date and time when the user account was created on the Enterprise Server installation.

* `remoteUserId` (Int!): The ID of the user account on the Enterprise Server installation.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## EnterpriseServerUserAccountEmail

An email belonging to a user account on an Enterprise Server installation.

**Implements:** Node

### Fields for `EnterpriseServerUserAccountEmail`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `email` (String!): The email address.
* `id` (ID!): The Node ID of the EnterpriseServerUserAccountEmail object.
* `isPrimary` (Boolean!): Indicates whether this is the primary email of the associated user account.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.
* `userAccount` (EnterpriseServerUserAccount!): The user account to which the email belongs.

## EnterpriseServerUserAccountsUpload

A user accounts upload from an Enterprise Server installation.

**Implements:** Node

### Fields for `EnterpriseServerUserAccountsUpload`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `enterprise` (Enterprise!): The enterprise to which this upload belongs.
* `enterpriseServerInstallation` (EnterpriseServerInstallation!): The Enterprise Server installation for which this upload was generated.
* `id` (ID!): The Node ID of the EnterpriseServerUserAccountsUpload object.
* `name` (String!): The name of the file uploaded.
* `syncState` (EnterpriseServerUserAccountsUploadSyncState!): The synchronization state of the upload.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## EnterpriseUserAccount

An account for a user who is an admin of an enterprise or a member of an enterprise through one or more organizations.

**Implements:** Actor, Node

### Fields for `EnterpriseUserAccount`

* `avatarUrl` (URI!): A URL pointing to the enterprise user account's public avatar.
  * `size` (Int): The size of the resulting square image.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `enterprise` (Enterprise!): The enterprise in which this user account exists.

* `enterpriseInstallations` (EnterpriseServerInstallationMembershipConnection!): A list of Enterprise Server installations this user is a member of.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (EnterpriseServerInstallationOrder): Ordering options for installations returned from the connection.
  * `query` (String): The search string to look for.
  * `role` (EnterpriseUserAccountMembershipRole): The role of the user in the installation.

* `id` (ID!): The Node ID of the EnterpriseUserAccount object.

* `login` (String!): An identifier for the enterprise user account, a login or email address.

* `name` (String): The name of the enterprise user account.

* `organizations` (EnterpriseOrganizationMembershipConnection!): A list of enterprise organizations this user is a member of.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for organizations returned from the connection.
  * `query` (String): The search string to look for.
  * `role` (EnterpriseUserAccountMembershipRole): The role of the user in the enterprise organization.

* `resourcePath` (URI!): The HTTP path for this user.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this user.

* `user` (User): The user within the enterprise.

## Environment

An environment.

**Implements:** Node

### Fields for `Environment`

* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the Environment object.
* `isPinned` (Boolean): Indicates whether or not this environment is currently pinned to the repository.
* `latestCompletedDeployment` (Deployment): The latest completed deployment with status success, failure, or error if it exists.
* `name` (String!): The name of the environment.
* `pinnedPosition` (Int): The position of the environment if it is pinned, null if it is not pinned.
* `protectionRules` (DeploymentProtectionRuleConnection!): The protection rules defined for this environment. *(Pagination: `after`, `before`, `first`, `last`)*

## ExternalIdentity

An external identity provisioned by SAML SSO or SCIM. If SAML is configured on
the organization, the external identity is visible to (1) organization owners,
(2) organization owners' personal access tokens (classic) with read:org or
admin:org scope, (3) GitHub App with an installation token with read or write
access to members. If SAML is configured on the enterprise, the external
identity is visible to (1) enterprise owners, (2) enterprise owners' personal
access tokens (classic) with read:enterprise or admin:enterprise scope.

**Implements:** Node

### Fields for `ExternalIdentity`

* `guid` (String!): The GUID for this identity.
* `id` (ID!): The Node ID of the ExternalIdentity object.
* `organizationInvitation` (OrganizationInvitation): Organization invitation for this SCIM-provisioned external identity.
* `samlIdentity` (ExternalIdentitySamlAttributes): SAML Identity attributes.
* `scimIdentity` (ExternalIdentityScimAttributes): SCIM Identity attributes.
* `user` (User): User linked to this external identity. Will be NULL if this identity has not been claimed by an organization member.

## ExternalIdentityAttribute

An attribute for the External Identity attributes collection.

### Fields for `ExternalIdentityAttribute`

* `metadata` (String): The attribute metadata as JSON.
* `name` (String!): The attribute name.
* `value` (String!): The attribute value.

## ExternalIdentitySamlAttributes

SAML attributes for the External Identity.

### Fields for `ExternalIdentitySamlAttributes`

* `attributes` (\[ExternalIdentityAttribute!]!): SAML Identity attributes.
* `emails` (\[UserEmailMetadata!]): The emails associated with the SAML identity.
* `familyName` (String): Family name of the SAML identity.
* `givenName` (String): Given name of the SAML identity.
* `groups` (\[String!]): The groups linked to this identity in IDP.
* `nameId` (String): The NameID of the SAML identity.
* `username` (String): The userName of the SAML identity.

## ExternalIdentityScimAttributes

SCIM attributes for the External Identity.

### Fields for `ExternalIdentityScimAttributes`

* `emails` (\[UserEmailMetadata!]): The emails associated with the SCIM identity.
* `familyName` (String): Family name of the SCIM identity.
* `givenName` (String): Given name of the SCIM identity.
* `groups` (\[String!]): The groups linked to this identity in IDP.
* `username` (String): The userName of the SCIM identity.

## FileExtensionRestrictionParameters

Prevent commits that include files with specified file extensions from being pushed to the commit graph.

### Fields for `FileExtensionRestrictionParameters`

* `restrictedFileExtensions` (\[String!]!): The file extensions that are restricted from being pushed to the commit graph.

## FilePathRestrictionParameters

Prevent commits that include changes in specified file and folder paths from
being pushed to the commit graph. This includes absolute paths that contain file names.

### Fields for `FilePathRestrictionParameters`

* `restrictedFilePaths` (\[String!]!): The file paths that are restricted from being pushed to the commit graph.

## FundingLink

A funding platform link for a repository.

### Fields for `FundingLink`

* `platform` (FundingPlatform!): The funding platform this link is for.
* `url` (URI!): The configured URL for this funding link.

## GenericHovercardContext

A generic hovercard context with a message and icon.

**Implements:** HovercardContext

### Fields for `GenericHovercardContext`

* `message` (String!): A string describing this context.
* `octicon` (String!): An octicon to accompany this context.

## Gist

A Gist.

**Implements:** Node, Starrable, UniformResourceLocatable

### Fields for `Gist`

* `comments` (GistCommentConnection!): A list of comments associated with the gist. *(Pagination: `after`, `before`, `first`, `last`)*

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `description` (String): The gist description.

* `files` (\[GistFile]): The files in this gist.
  * `limit` (Int): The maximum number of files to return. Default: `10`.
  * `oid` (GitObjectID): The oid of the files to return.

* `forks` (GistConnection!): A list of forks associated with the gist.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (GistOrder): Ordering options for gists returned from the connection.

* `id` (ID!): The Node ID of the Gist object.

* `isFork` (Boolean!): Identifies if the gist is a fork.

* `isPublic` (Boolean!): Whether the gist is public or not.

* `name` (String!): The gist name.

* `owner` (RepositoryOwner): The gist owner.

* `pushedAt` (DateTime): Identifies when the gist was last pushed to.

* `resourcePath` (URI!): The HTML path to this resource.

* `stargazerCount` (Int!): Returns a count of how many stargazers there are on this object.

* `stargazers` (StargazerConnection!): A list of users who have starred this starrable.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (StarOrder): Order for connection.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this Gist.

* `viewerHasStarred` (Boolean!): Returns a boolean indicating whether the viewing user has starred this starrable.

## GistComment

Represents a comment on an Gist.

**Implements:** Comment, Deletable, Minimizable, Node, Updatable, UpdatableComment

### Fields for `GistComment`

* `author` (Actor): The actor who authored the comment.
* `authorAssociation` (CommentAuthorAssociation!): Author's association with the gist.
* `body` (String!): Identifies the comment body.
* `bodyHTML` (HTML!): The body rendered to HTML.
* `bodyText` (String!): The body rendered to text.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.
* `databaseId` (Int): Identifies the primary key from the database.
* `editor` (Actor): The actor who edited the comment.
* `gist` (Gist!): The associated gist.
* `id` (ID!): The Node ID of the GistComment object.
* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.
* `isMinimized` (Boolean!): Returns whether or not a comment has been minimized.
* `lastEditedAt` (DateTime): The moment the editor made the last edit.
* `minimizedReason` (String): Returns why the comment was minimized. One of abuse, off-topic,
  outdated, resolved, duplicate, spam, and low-quality. Note that the
  case and formatting of these values differs from the inputs to the
  MinimizeComment mutation.
* `publishedAt` (DateTime): Identifies when the comment was published at.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.
* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*
* `viewerCanDelete` (Boolean!): Check if the current viewer can delete this object.
* `viewerCanMinimize` (Boolean!): Check if the current viewer can minimize this object.
* `viewerCanUnminimize` (Boolean!): Check if the current viewer can unminimize this object.
* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.
* `viewerCannotUpdateReasons` (\[CommentCannotUpdateReason!]!): Reasons why the current viewer can not update this comment.
* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

## GistFile

A file in a gist.

### Fields for `GistFile`

* `encodedName` (String): The file name encoded to remove characters that are invalid in URL paths.
* `encoding` (String): The gist file encoding.
* `extension` (String): The file extension from the file name.
* `isImage` (Boolean!): Indicates if this file is an image.
* `isTruncated` (Boolean!): Whether the file's contents were truncated.
* `language` (Language): The programming language this file is written in.
* `name` (String): The gist file name.
* `size` (Int): The gist file size in bytes.
* `text` (String): UTF8 text data or null if the file is binary.
  * `truncate` (Int): Optionally truncate the returned file to this length.

## GitActor

Represents an actor in a Git commit (ie. an author or committer).

### Fields for `GitActor`

* `avatarUrl` (URI!): A URL pointing to the author's public avatar.
  * `size` (Int): The size of the resulting square image.

* `date` (GitTimestamp): The timestamp of the Git action (authoring or committing).

* `email` (String): The email in the Git commit.

* `name` (String): The name in the Git commit.

* `user` (User): The GitHub user corresponding to the email field. Null if no such user exists.

## GitHubMetadata

Represents information about the GitHub instance.

### Fields for `GitHubMetadata`

* `gitHubServicesSha` (GitObjectID!): Returns a String that's a SHA of github-services.
* `gitIpAddresses` (\[String!]): IP addresses that users connect to for git operations.
* `githubEnterpriseImporterIpAddresses` (\[String!]): IP addresses that GitHub Enterprise Importer uses for outbound connections.
* `hookIpAddresses` (\[String!]): IP addresses that service hooks are sent from.
* `importerIpAddresses` (\[String!]): IP addresses that the importer connects from.
* `isPasswordAuthenticationVerifiable` (Boolean!): Whether or not users are verified.
* `pagesIpAddresses` (\[String!]): IP addresses for GitHub Pages' A records.

## GpgSignature

Represents a GPG signature on a Commit or Tag.

**Implements:** GitSignature

### Fields for `GpgSignature`

* `email` (String!): Email used to sign this object.
* `isValid` (Boolean!): True if the signature is valid and verified by GitHub.
* `keyId` (String): Hex-encoded ID of the key that signed this object.
* `payload` (String!): Payload for GPG signing object. Raw ODB object without the signature header.
* `signature` (String!): ASCII-armored signature header from object.
* `signer` (User): GitHub user corresponding to the email signing this commit.
* `state` (GitSignatureState!): The state of this signature. VALID if signature is valid and verified by
  GitHub, otherwise represents reason why signature is considered invalid.
* `verifiedAt` (DateTime): The date the signature was verified, if valid.
* `wasSignedByGitHub` (Boolean!): True if the signature was made with GitHub's signing key.

## HeadRefDeletedEvent

Represents ahead\_ref\_deletedevent on a given pull request.

**Implements:** Node

### Fields for `HeadRefDeletedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `headRef` (Ref): Identifies the Ref associated with the head\_ref\_deleted event.
* `headRefName` (String!): Identifies the name of the Ref associated with the head\_ref\_deleted event.
* `id` (ID!): The Node ID of the HeadRefDeletedEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.

## HeadRefForcePushedEvent

Represents ahead\_ref\_force\_pushedevent on a given pull request.

**Implements:** Node

### Fields for `HeadRefForcePushedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `afterCommit` (Commit): Identifies the after commit SHA for thehead\_ref\_force\_pushedevent.
* `beforeCommit` (Commit): Identifies the before commit SHA for thehead\_ref\_force\_pushedevent.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the HeadRefForcePushedEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.
* `ref` (Ref): Identifies the fully qualified ref name for thehead\_ref\_force\_pushedevent.

## HeadRefRestoredEvent

Represents ahead\_ref\_restoredevent on a given pull request.

**Implements:** Node

### Fields for `HeadRefRestoredEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the HeadRefRestoredEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.

## Hovercard

Detail needed to display a hovercard for a user.

### Fields for `Hovercard`

* `contexts` (\[HovercardContext!]!): Each of the contexts for this hovercard.

## IpAllowListEntry

An IP address or range of addresses that is allowed to access an owner's resources.

**Implements:** Node

### Fields for `IpAllowListEntry`

* `allowListValue` (String!): A single IP address or range of IP addresses in CIDR notation.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the IpAllowListEntry object.
* `isActive` (Boolean!): Whether the entry is currently active.
* `name` (String): The name of the IP allow list entry.
* `owner` (IpAllowListOwner!): The owner of the IP allow list entry.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## Issue

An Issue is a place to discuss ideas, enhancements, tasks, and bugs for a project.

**Implements:** Assignable, Closable, Comment, Deletable, Labelable, Lockable, Node, ProjectV2Owner, Reactable, RepositoryNode, Subscribable, SubscribableThread, UniformResourceLocatable, Updatable, UpdatableComment

### Fields for `Issue`

* `activeLockReason` (LockReason): Reason that the conversation was locked.

* `assignedActors` (AssigneeConnection!): A list of actors assigned to this object. *(Pagination: `after`, `before`, `first`, `last`)*

* `assignees` (UserConnection!): A list of Users assigned to this object. *(Pagination: `after`, `before`, `first`, `last`)*

* `author` (Actor): The actor who authored the comment.

* `authorAssociation` (CommentAuthorAssociation!): Author's association with the subject of the comment.

* `blockedBy` (IssueConnection!): A list of issues that are blocking this issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueDependencyOrder): Ordering options for dependencies.

* `blocking` (IssueConnection!): A list of issues that this issue is blocking.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueDependencyOrder): Ordering options for dependencies.

* `body` (String!): Identifies the body of the issue.

* `bodyHTML` (HTML!): The body rendered to HTML.

* `bodyResourcePath` (URI!): The http path for this issue body.

* `bodyText` (String!): Identifies the body of the issue rendered to text.

* `bodyUrl` (URI!): The http URL for this issue body.

* `closed` (Boolean!): Indicates if the object is closed (definition of closed may depend on type).

* `closedAt` (DateTime): Identifies the date and time when the object was closed.

* `closedByPullRequestsReferences` (PullRequestConnection): List of open pull requests referenced from this issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includeClosedPrs` (Boolean): Include closed PRs in results.
  * `last` (Int): Returns the last n elements from the list.
  * `orderByState` (Boolean): Return results ordered by state.
  * `userLinkedOnly` (Boolean): Return only manually linked PRs.

* `comments` (IssueCommentConnection!): A list of comments associated with the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueCommentOrder): Ordering options for issue comments returned from the connection.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.

* `databaseId` (Int): Identifies the primary key from the database.

* `duplicateOf` (Issue): A reference to the original issue that this issue has been marked as a duplicate of.

* `editor` (Actor): The actor who edited the comment.

* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.

* `hovercard` (Hovercard!): The hovercard information for this issue.
  * `includeNotificationContexts` (Boolean): Whether or not to include notification contexts. Default: `true`.

* `id` (ID!): The Node ID of the Issue object.

* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.

* `isPinned` (Boolean): Indicates whether or not this issue is currently pinned to the repository issues list.

* `isReadByViewer` (Boolean): Is this issue read by the viewer.

* `issueDependenciesSummary` (IssueDependenciesSummary!): Summary of the state of an issue's dependencies.

* `issueFieldValues` (IssueFieldValueConnection): Fields that are set on this issue. *(Pagination: `after`, `before`, `first`, `last`)*

* `issueType` (IssueType): The issue type for this Issue.

* `labels` (LabelConnection): A list of labels associated with the object.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (LabelOrder): Ordering options for labels returned from the connection.

* `lastEditedAt` (DateTime): The moment the editor made the last edit.

* `linkedBranches` (LinkedBranchConnection!): Branches linked to this issue. *(Pagination: `after`, `before`, `first`, `last`)*

* `locked` (Boolean!): true if the object is locked.

* `milestone` (Milestone): Identifies the milestone associated with the issue.

* `number` (Int!): Identifies the issue number.

* `parent` (Issue): The parent entity of the issue.

* `participants` (UserConnection!): A list of Users that are participating in the Issue conversation. *(Pagination: `after`, `before`, `first`, `last`)*

* `pinnedIssueComment` (PinnedIssueComment): The pinned comment for this issue.

* `projectCards` (ProjectCardConnection!): List of project cards associated with this issue. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `archivedStates` (\[ProjectCardArchivedState]): A list of archived states to filter the cards by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.

* `projectItems` (ProjectV2ItemConnection): List of project items associated with this issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includeArchived` (Boolean): Include archived items. Default: `true`.
  * `last` (Int): Returns the last n elements from the list.

* `projectV2` (ProjectV2): Find a project by number.
  * `number` (Int!): The project number.

* `projectsV2` (ProjectV2Connection!): A list of projects under the owner.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `minPermissionLevel` (ProjectV2PermissionLevel): Filter projects based on user role. Default: `READ`.
  * `orderBy` (ProjectV2Order): How to order the returned projects.
  * `query` (String): A project to search for under the owner.

* `publishedAt` (DateTime): Identifies when the comment was published at.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `repository` (Repository!): The repository associated with this node.

* `resourcePath` (URI!): The HTTP path for this issue.

* `state` (IssueState!): Identifies the state of the issue.

* `stateReason` (IssueStateReason): Identifies the reason for the issue state.
  * `enableDuplicate` (Boolean): Whether or not to return state reason for duplicates
    Upcoming Change on 2025-10-01 UTC
    Description: enableDuplicate will be removed.
    Reason: The state reason for duplicate issue is now returned by default.

* `subIssues` (IssueConnection!): A list of sub-issues associated with the Issue. *(Pagination: `after`, `before`, `first`, `last`)*

* `subIssuesSummary` (SubIssuesSummary!): Summary of the state of an issue's sub-issues.

* `suggestedActors` (AssigneeConnection!): A list of suggested actors to assign to this object.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `query` (String): If provided, searches users by login or profile name.

* `timeline` (IssueTimelineConnection!): A list of events, comments, commits, etc. associated with the issue. **Deprecated:** timeline will be removed Use Issue.timelineItems instead. Removal on 2020-10-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `since` (DateTime): Allows filtering timeline events by a since timestamp.

* `timelineItems` (IssueTimelineItemsConnection!): A list of events, comments, commits, etc. associated with the issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `itemTypes` (\[IssueTimelineItemsItemType!]): Filter timeline items by type.
  * `last` (Int): Returns the last n elements from the list.
  * `since` (DateTime): Filter timeline items by a since timestamp.
  * `skip` (Int): Skips the first n elements in the list.

* `title` (String!): Identifies the issue title.

* `titleHTML` (String!): Identifies the issue title rendered to HTML.

* `trackedInIssues` (IssueConnection!): A list of issues that track this issue. *(Pagination: `after`, `before`, `first`, `last`)*

* `trackedIssues` (IssueConnection!): A list of issues tracked inside the current issue. *(Pagination: `after`, `before`, `first`, `last`)*

* `trackedIssuesCount` (Int!): The number of tracked issues for this issue.
  * `states` (\[TrackedIssueStates]): Limit the count to tracked issues with the specified states.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this issue.

* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*

* `viewerCanClose` (Boolean!): Indicates if the object can be closed by the viewer.

* `viewerCanDelete` (Boolean!): Check if the current viewer can delete this object.

* `viewerCanLabel` (Boolean!): Indicates if the viewer can edit labels for this object.

* `viewerCanReact` (Boolean!): Can user react to this subject.

* `viewerCanReopen` (Boolean!): Indicates if the object can be reopened by the viewer.

* `viewerCanSetFields` (Boolean): Check if the current viewer can set fields on the issue.

* `viewerCanSubscribe` (Boolean!): Check if the viewer is able to change their subscription status for the repository.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

* `viewerCannotUpdateReasons` (\[CommentCannotUpdateReason!]!): Reasons why the current viewer can not update this comment.

* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

* `viewerSubscription` (SubscriptionState): Identifies if the viewer is watching, not watching, or ignoring the subscribable entity.

* `viewerThreadSubscriptionFormAction` (ThreadSubscriptionFormAction): Identifies the viewer's thread subscription form action.

* `viewerThreadSubscriptionStatus` (ThreadSubscriptionState): Identifies the viewer's thread subscription status.

## IssueComment

Represents a comment on an Issue.

**Implements:** Comment, Deletable, Minimizable, Node, Pinnable, Reactable, RepositoryNode, Updatable, UpdatableComment

### Fields for `IssueComment`

* `author` (Actor): The actor who authored the comment.

* `authorAssociation` (CommentAuthorAssociation!): Author's association with the subject of the comment.

* `body` (String!): The body as Markdown.

* `bodyHTML` (HTML!): The body rendered to HTML.

* `bodyText` (String!): The body rendered to text.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.

* `databaseId` (Int): Identifies the primary key from the database.

* `editor` (Actor): The actor who edited the comment.

* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.

* `id` (ID!): The Node ID of the IssueComment object.

* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.

* `isMinimized` (Boolean!): Returns whether or not a comment has been minimized.

* `isPinned` (Boolean): Indicates whether or not this entity is currently pinned.

* `issue` (Issue!): Identifies the issue associated with the comment.

* `lastEditedAt` (DateTime): The moment the editor made the last edit.

* `minimizedReason` (String): Returns why the comment was minimized. One of abuse, off-topic,
  outdated, resolved, duplicate, spam, and low-quality. Note that the
  case and formatting of these values differs from the inputs to the
  MinimizeComment mutation.

* `pinnedAt` (DateTime): Identifies the date and time when this entity was pinned.

* `pinnedBy` (User): The user who pinned this entity.

* `publishedAt` (DateTime): Identifies when the comment was published at.

* `pullRequest` (PullRequest): Returns the pull request associated with the comment, if this comment was made on a
  pull request.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `repository` (Repository!): The repository associated with this node.

* `resourcePath` (URI!): The HTTP path for this issue comment.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this issue comment.

* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*

* `viewerCanDelete` (Boolean!): Check if the current viewer can delete this object.

* `viewerCanMinimize` (Boolean!): Check if the current viewer can minimize this object.

* `viewerCanPin` (Boolean!): Check if the current viewer can pin this entity.

* `viewerCanReact` (Boolean!): Can user react to this subject.

* `viewerCanUnminimize` (Boolean!): Check if the current viewer can unminimize this object.

* `viewerCanUnpin` (Boolean!): Check if the current viewer can unpin this entity.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

* `viewerCannotUpdateReasons` (\[CommentCannotUpdateReason!]!): Reasons why the current viewer can not update this comment.

* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

## IssueCommentPinnedEvent

Represents aissue\_comment\_pinnedevent on a given issue.

**Implements:** Node

### Fields for `IssueCommentPinnedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the IssueCommentPinnedEvent object.
* `issueComment` (IssueComment): Identifies the issue comment associated with theissue\_comment\_pinnedevent.

## IssueCommentUnpinnedEvent

Represents aissue\_comment\_unpinnedevent on a given issue.

**Implements:** Node

### Fields for `IssueCommentUnpinnedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the IssueCommentUnpinnedEvent object.
* `issueComment` (IssueComment): Identifies the issue comment associated with theissue\_comment\_unpinnedevent.

## IssueContributionsByRepository

This aggregates issues opened by a user within one repository.

### Fields for `IssueContributionsByRepository`

* `contributions` (CreatedIssueContributionConnection!): The issue contributions.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ContributionOrder): Ordering options for contributions returned from the connection.

* `repository` (Repository!): The repository in which the issues were opened.

## IssueDependenciesSummary

Summary of the state of an issue's dependencies.

### Fields for `IssueDependenciesSummary`

* `blockedBy` (Int!): Count of issues this issue is blocked by.
* `blocking` (Int!): Count of issues this issue is blocking.
* `totalBlockedBy` (Int!): Total count of issues this issue is blocked by (open and closed).
* `totalBlocking` (Int!): Total count of issues this issue is blocking (open and closed).

## IssueFieldAddedEvent

Represents aissue\_field\_addedevent on a given issue.

**Implements:** Node

### Fields for `IssueFieldAddedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `color` (String): The color if it is a single-select field.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the IssueFieldAddedEvent object.
* `issueField` (IssueFields): The issue field added.
* `value` (String): The value of the added field.

## IssueFieldChangedEvent

Represents aissue\_field\_changedevent on a given issue.

**Implements:** Node

### Fields for `IssueFieldChangedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the IssueFieldChangedEvent object.
* `issueField` (IssueFields): The issue field changed.
* `newColor` (String): The new color if it is a single-select field.
* `newValue` (String): The new value of the field.
* `previousColor` (String): The previous color if it was a single-select field.
* `previousValue` (String): The previous value of the field.

## IssueFieldDate

Represents a date issue field.

**Implements:** IssueFieldCommon, Node

### Fields for `IssueFieldDate`

* `createdAt` (DateTime!): The issue field's creation timestamp.
* `dataType` (IssueFieldDataType!): The issue field's data type.
* `description` (String): The issue field's description.
* `id` (ID!): The Node ID of the IssueFieldDate object.
* `name` (String!): The issue field's name.
* `visibility` (IssueFieldVisibility!): The issue field's visibility.

## IssueFieldDateValue

The value of a date field in an Issue item.

**Implements:** IssueFieldValueCommon, Node

### Fields for `IssueFieldDateValue`

* `field` (IssueFields): The issue field that contains this value.
* `id` (ID!): The Node ID of the IssueFieldDateValue object.
* `value` (String!): Value of the field.

## IssueFieldNumber

Represents a number issue field.

**Implements:** IssueFieldCommon, Node

### Fields for `IssueFieldNumber`

* `createdAt` (DateTime!): The issue field's creation timestamp.
* `dataType` (IssueFieldDataType!): The issue field's data type.
* `description` (String): The issue field's description.
* `id` (ID!): The Node ID of the IssueFieldNumber object.
* `name` (String!): The issue field's name.
* `visibility` (IssueFieldVisibility!): The issue field's visibility.

## IssueFieldNumberValue

The value of a number field in an Issue item.

**Implements:** IssueFieldValueCommon, Node

### Fields for `IssueFieldNumberValue`

* `field` (IssueFields): The issue field that contains this value.
* `id` (ID!): The Node ID of the IssueFieldNumberValue object.
* `value` (Float!): Value of the field.

## IssueFieldRemovedEvent

Represents aissue\_field\_removedevent on a given issue.

**Implements:** Node

### Fields for `IssueFieldRemovedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the IssueFieldRemovedEvent object.
* `issueField` (IssueFields): The issue field removed.

## IssueFieldSingleSelect

Represents a single select issue field.

**Implements:** IssueFieldCommon, Node

### Fields for `IssueFieldSingleSelect`

* `createdAt` (DateTime!): The issue field's creation timestamp.
* `dataType` (IssueFieldDataType!): The issue field's data type.
* `description` (String): The issue field's description.
* `id` (ID!): The Node ID of the IssueFieldSingleSelect object.
* `name` (String!): The issue field's name.
* `options` (\[IssueFieldSingleSelectOption!]!): Options for the single select field.
* `visibility` (IssueFieldVisibility!): The issue field's visibility.

## IssueFieldSingleSelectOption

Represents an option in a single-select issue field.

**Implements:** Node

### Fields for `IssueFieldSingleSelectOption`

* `color` (IssueFieldSingleSelectOptionColor!): The option's display color.
* `description` (String): The option's plain-text description.
* `id` (ID!): The Node ID of the IssueFieldSingleSelectOption object.
* `name` (String!): The option's name.
* `priority` (Int): The option's priority order.

## IssueFieldSingleSelectValue

The value of a single select field in an Issue item.

**Implements:** IssueFieldValueCommon, Node

### Fields for `IssueFieldSingleSelectValue`

* `color` (IssueFieldSingleSelectOptionColor!): The option's display color.
* `description` (String): The option's plain-text description.
* `field` (IssueFields): The issue field that contains this value.
* `id` (ID!): The Node ID of the IssueFieldSingleSelectValue object.
* `name` (String!): The option's name.
* `optionId` (String): The selected option's global relay ID.
* `value` (String!): The option's name text (alias for name, for consistency with other field value types).

## IssueFieldText

Represents a text issue field.

**Implements:** IssueFieldCommon, Node

### Fields for `IssueFieldText`

* `createdAt` (DateTime!): The issue field's creation timestamp.
* `dataType` (IssueFieldDataType!): The issue field's data type.
* `description` (String): The issue field's description.
* `id` (ID!): The Node ID of the IssueFieldText object.
* `name` (String!): The issue field's name.
* `visibility` (IssueFieldVisibility!): The issue field's visibility.

## IssueFieldTextValue

The value of a text field in an Issue item.

**Implements:** IssueFieldValueCommon, Node

### Fields for `IssueFieldTextValue`

* `field` (IssueFields): The issue field that contains this value.
* `id` (ID!): The Node ID of the IssueFieldTextValue object.
* `value` (String!): Value of the field.

## IssueTemplate

A repository issue template.

### Fields for `IssueTemplate`

* `about` (String): The template purpose.

* `assignees` (UserConnection!): The suggested assignees. *(Pagination: `after`, `before`, `first`, `last`)*

* `body` (String): The suggested issue body.

* `filename` (String!): The template filename.

* `labels` (LabelConnection): The suggested issue labels.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (LabelOrder): Ordering options for labels returned from the connection.

* `name` (String!): The template name.

* `title` (String): The suggested issue title.

* `type` (IssueType): The suggested issue type.

## IssueTimelineItemsConnection

The connection type for IssueTimelineItems.

### Fields for `IssueTimelineItemsConnection`

* `edges` (\[IssueTimelineItemsEdge]): A list of edges.
* `filteredCount` (Int!): Identifies the count of items after applying before and after filters.
* `nodes` (\[IssueTimelineItems]): A list of nodes.
* `pageCount` (Int!): Identifies the count of items after applying before/after filters and first/last/skip slicing.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.
* `updatedAt` (DateTime!): Identifies the date and time when the timeline was last updated.

## IssueType

Represents the type of Issue.

**Implements:** Node

### Fields for `IssueType`

* `color` (IssueTypeColor!): The issue type's color.

* `description` (String): The issue type's description.

* `id` (ID!): The Node ID of the IssueType object.

* `isEnabled` (Boolean!): The issue type's enabled state.

* `isPrivate` (Boolean!): Whether the issue type is publicly visible. **Deprecated:** Private issue types are being deprecated and can no longer be created. Removal on 2025-04-01 UTC.

* `issues` (IssueConnection!): The issues with this issue type in the given repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `filterBy` (IssueFilters): Filtering options for issues returned from the connection.
  * `first` (Int): Returns the first n elements from the list.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for issues returned from the connection.
  * `repositoryId` (ID!): Target repository to load the issues from.
  * `states` (\[IssueState!]): A list of states to filter the issues by.

* `name` (String!): The issue type's name.

* `pinnedFields` (\[IssueFields!]): An ordered list of issue fields pinned to this type.

## IssueTypeAddedEvent

Represents aissue\_type\_addedevent on a given issue.

**Implements:** Node

### Fields for `IssueTypeAddedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the IssueTypeAddedEvent object.
* `issueType` (IssueType): The issue type added.

## IssueTypeChangedEvent

Represents aissue\_type\_changedevent on a given issue.

**Implements:** Node

### Fields for `IssueTypeChangedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the IssueTypeChangedEvent object.
* `issueType` (IssueType): The issue type added.
* `prevIssueType` (IssueType): The issue type removed.

## IssueTypeRemovedEvent

Represents aissue\_type\_removedevent on a given issue.

**Implements:** Node

### Fields for `IssueTypeRemovedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the IssueTypeRemovedEvent object.
* `issueType` (IssueType): The issue type removed.

## JoinedGitHubContribution

Represents a user signing up for a GitHub account.

**Implements:** Contribution

### Fields for `JoinedGitHubContribution`

* `isRestricted` (Boolean!): Whether this contribution is associated with a record you do not have access to. For
  example, your own 'first issue' contribution may have been made on a repository you can no
  longer access.
* `occurredAt` (DateTime!): When this contribution was made.
* `resourcePath` (URI!): The HTTP path for this contribution.
* `url` (URI!): The HTTP URL for this contribution.
* `user` (User!): The user who made this contribution.

## Label

A label for categorizing Issues, Pull Requests, Milestones, or Discussions with a given Repository.

**Implements:** Node

### Fields for `Label`

* `color` (String!): Identifies the label color.

* `createdAt` (DateTime): Identifies the date and time when the label was created.

* `description` (String): A brief description of this label.

* `id` (ID!): The Node ID of the Label object.

* `isDefault` (Boolean!): Indicates whether or not this is a default label.

* `issues` (IssueConnection!): A list of issues associated with this label.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `filterBy` (IssueFilters): Filtering options for issues returned from the connection.
  * `first` (Int): Returns the first n elements from the list.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for issues returned from the connection.
  * `states` (\[IssueState!]): A list of states to filter the issues by.

* `name` (String!): Identifies the label name.

* `pullRequests` (PullRequestConnection!): A list of pull requests associated with this label.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `baseRefName` (String): The base ref name to filter the pull requests by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `headRefName` (String): The head ref name to filter the pull requests by.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for pull requests returned from the connection.
  * `states` (\[PullRequestState!]): A list of states to filter the pull requests by.

* `repository` (Repository!): The repository associated with this label.

* `resourcePath` (URI!): The HTTP path for this label.

* `updatedAt` (DateTime): Identifies the date and time when the label was last updated.

* `url` (URI!): The HTTP URL for this label.

## LabeledEvent

Represents alabeledevent on a given issue or pull request.

**Implements:** Node

### Fields for `LabeledEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the LabeledEvent object.
* `label` (Label!): Identifies the label associated with thelabeledevent.
* `labelable` (Labelable!): Identifies the Labelable associated with the event.

## Language

Represents a given language found in repositories.

**Implements:** Node

### Fields for `Language`

* `color` (String): The color defined for the current language.
* `id` (ID!): The Node ID of the Language object.
* `name` (String!): The name of the current language.

## LanguageConnection

A list of languages associated with the parent.

### Fields for `LanguageConnection`

* `edges` (\[LanguageEdge]): A list of edges.
* `nodes` (\[Language]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.
* `totalSize` (Int!): The total size in bytes of files written in that language.

## LanguageEdge

Represents the language of a repository.

### Fields for `LanguageEdge`

* `cursor` (String!):
* `node` (Language!):
* `size` (Int!): The number of bytes of code written in the language.

## License

A repository's open source license.

**Implements:** Node

### Fields for `License`

* `body` (String!): The full text of the license.
* `conditions` (\[LicenseRule]!): The conditions set by the license.
* `description` (String): A human-readable description of the license.
* `featured` (Boolean!): Whether the license should be featured.
* `hidden` (Boolean!): Whether the license should be displayed in license pickers.
* `id` (ID!): The Node ID of the License object.
* `implementation` (String): Instructions on how to implement the license.
* `key` (String!): The lowercased SPDX ID of the license.
* `limitations` (\[LicenseRule]!): The limitations set by the license.
* `name` (String!): The license full name specified by <https://spdx.org/licenses>.
* `nickname` (String): Customary short name if applicable (e.g, GPLv3).
* `permissions` (\[LicenseRule]!): The permissions set by the license.
* `pseudoLicense` (Boolean!): Whether the license is a pseudo-license placeholder (e.g., other, no-license).
* `spdxId` (String): Short identifier specified by <https://spdx.org/licenses>.
* `url` (URI): URL to the license on <https://choosealicense.com>.

## LicenseRule

Describes a License's conditions, permissions, and limitations.

### Fields for `LicenseRule`

* `description` (String!): A description of the rule.
* `key` (String!): The machine-readable rule key.
* `label` (String!): The human-readable rule label.

## LinkedBranch

A branch linked to an issue.

**Implements:** Node

### Fields for `LinkedBranch`

* `id` (ID!): The Node ID of the LinkedBranch object.
* `ref` (Ref): The branch's ref.

## LockedEvent

Represents alockedevent on a given issue or pull request.

**Implements:** Node

### Fields for `LockedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the LockedEvent object.
* `lockReason` (LockReason): Reason that the conversation was locked (optional).
* `lockable` (Lockable!): Object that was locked.

## Mannequin

A placeholder user for attribution of imported data on GitHub.

**Implements:** Actor, Node, UniformResourceLocatable

### Fields for `Mannequin`

* `avatarUrl` (URI!): A URL pointing to the GitHub App's public avatar.
  * `size` (Int): The size of the resulting square image.

* `claimant` (User): The user that has claimed the data attributed to this mannequin.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `email` (String): The mannequin's email on the source instance.

* `id` (ID!): The Node ID of the Mannequin object.

* `login` (String!): The username of the actor.

* `name` (String): The display name of the imported mannequin.

* `resourcePath` (URI!): The HTML path to this resource.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The URL to this resource.

## MarkedAsDuplicateEvent

Represents amarked\_as\_duplicateevent on a given issue or pull request.

**Implements:** Node

### Fields for `MarkedAsDuplicateEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `canonical` (IssueOrPullRequest): The authoritative issue or pull request which has been duplicated by another.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `duplicate` (IssueOrPullRequest): The issue or pull request which has been marked as a duplicate of another.
* `id` (ID!): The Node ID of the MarkedAsDuplicateEvent object.
* `isCrossRepository` (Boolean!): Canonical and duplicate belong to different repositories.

## MarketplaceCategory

A public description of a Marketplace category.

**Implements:** Node

### Fields for `MarketplaceCategory`

* `description` (String): The category's description.
* `howItWorks` (String): The technical description of how apps listed in this category work with GitHub.
* `id` (ID!): The Node ID of the MarketplaceCategory object.
* `name` (String!): The category's name.
* `primaryListingCount` (Int!): How many Marketplace listings have this as their primary category.
* `resourcePath` (URI!): The HTTP path for this Marketplace category.
* `secondaryListingCount` (Int!): How many Marketplace listings have this as their secondary category.
* `slug` (String!): The short name of the category used in its URL.
* `url` (URI!): The HTTP URL for this Marketplace category.

## MarketplaceListing

A listing in the GitHub integration marketplace.

**Implements:** Node

### Fields for `MarketplaceListing`

* `app` (App): The GitHub App this listing represents.

* `companyUrl` (URI): URL to the listing owner's company site.

* `configurationResourcePath` (URI!): The HTTP path for configuring access to the listing's integration or OAuth app.

* `configurationUrl` (URI!): The HTTP URL for configuring access to the listing's integration or OAuth app.

* `documentationUrl` (URI): URL to the listing's documentation.

* `extendedDescription` (String): The listing's detailed description.

* `extendedDescriptionHTML` (HTML!): The listing's detailed description rendered to HTML.

* `fullDescription` (String!): The listing's introductory description.

* `fullDescriptionHTML` (HTML!): The listing's introductory description rendered to HTML.

* `hasPublishedFreeTrialPlans` (Boolean!): Does this listing have any plans with a free trial?.

* `hasTermsOfService` (Boolean!): Does this listing have a terms of service link?.

* `hasVerifiedOwner` (Boolean!): Whether the creator of the app is a verified org.

* `howItWorks` (String): A technical description of how this app works with GitHub.

* `howItWorksHTML` (HTML!): The listing's technical description rendered to HTML.

* `id` (ID!): The Node ID of the MarketplaceListing object.

* `installationUrl` (URI): URL to install the product to the viewer's account or organization.

* `installedForViewer` (Boolean!): Whether this listing's app has been installed for the current viewer.

* `isArchived` (Boolean!): Whether this listing has been removed from the Marketplace.

* `isDraft` (Boolean!): Whether this listing is still an editable draft that has not been submitted
  for review and is not publicly visible in the Marketplace.

* `isPaid` (Boolean!): Whether the product this listing represents is available as part of a paid plan.

* `isPublic` (Boolean!): Whether this listing has been approved for display in the Marketplace.

* `isRejected` (Boolean!): Whether this listing has been rejected by GitHub for display in the Marketplace.

* `isUnverified` (Boolean!): Whether this listing has been approved for unverified display in the Marketplace.

* `isUnverifiedPending` (Boolean!): Whether this draft listing has been submitted for review for approval to be unverified in the Marketplace.

* `isVerificationPendingFromDraft` (Boolean!): Whether this draft listing has been submitted for review from GitHub for approval to be verified in the Marketplace.

* `isVerificationPendingFromUnverified` (Boolean!): Whether this unverified listing has been submitted for review from GitHub for approval to be verified in the Marketplace.

* `isVerified` (Boolean!): Whether this listing has been approved for verified display in the Marketplace.

* `logoBackgroundColor` (String!): The hex color code, without the leading '#', for the logo background.

* `logoUrl` (URI): URL for the listing's logo image.
  * `size` (Int): The size in pixels of the resulting square image. Default: `400`.

* `name` (String!): The listing's full name.

* `normalizedShortDescription` (String!): The listing's very short description without a trailing period or ampersands.

* `pricingUrl` (URI): URL to the listing's detailed pricing.

* `primaryCategory` (MarketplaceCategory!): The category that best describes the listing.

* `privacyPolicyUrl` (URI!): URL to the listing's privacy policy, may return an empty string for listings that do not require a privacy policy URL.

* `resourcePath` (URI!): The HTTP path for the Marketplace listing.

* `screenshotUrls` (\[String]!): The URLs for the listing's screenshots.

* `secondaryCategory` (MarketplaceCategory): An alternate category that describes the listing.

* `shortDescription` (String!): The listing's very short description.

* `slug` (String!): The short name of the listing used in its URL.

* `statusUrl` (URI): URL to the listing's status page.

* `supportEmail` (String): An email address for support for this listing's app.

* `supportUrl` (URI!): Either a URL or an email address for support for this listing's app, may
  return an empty string for listings that do not require a support URL.

* `termsOfServiceUrl` (URI): URL to the listing's terms of service.

* `url` (URI!): The HTTP URL for the Marketplace listing.

* `viewerCanAddPlans` (Boolean!): Can the current viewer add plans for this Marketplace listing.

* `viewerCanApprove` (Boolean!): Can the current viewer approve this Marketplace listing.

* `viewerCanDelist` (Boolean!): Can the current viewer delist this Marketplace listing.

* `viewerCanEdit` (Boolean!): Can the current viewer edit this Marketplace listing.

* `viewerCanEditCategories` (Boolean!): Can the current viewer edit the primary and secondary category of this
  Marketplace listing.

* `viewerCanEditPlans` (Boolean!): Can the current viewer edit the plans for this Marketplace listing.

* `viewerCanRedraft` (Boolean!): Can the current viewer return this Marketplace listing to draft state
  so it becomes editable again.

* `viewerCanReject` (Boolean!): Can the current viewer reject this Marketplace listing by returning it to
  an editable draft state or rejecting it entirely.

* `viewerCanRequestApproval` (Boolean!): Can the current viewer request this listing be reviewed for display in
  the Marketplace as verified.

* `viewerHasPurchased` (Boolean!): Indicates whether the current user has an active subscription to this Marketplace listing.

* `viewerHasPurchasedForAllOrganizations` (Boolean!): Indicates if the current user has purchased a subscription to this Marketplace listing
  for all of the organizations the user owns.

* `viewerIsListingAdmin` (Boolean!): Does the current viewer role allow them to administer this Marketplace listing.

## MaxFilePathLengthParameters

Prevent commits that include file paths that exceed the specified character limit from being pushed to the commit graph.

### Fields for `MaxFilePathLengthParameters`

* `maxFilePathLength` (Int!): The maximum amount of characters allowed in file paths.

## MaxFileSizeParameters

Prevent commits with individual files that exceed the specified limit from being pushed to the commit graph.

### Fields for `MaxFileSizeParameters`

* `maxFileSize` (Int!): The maximum file size allowed in megabytes. This limit does not apply to Git Large File Storage (Git LFS).

## MemberFeatureRequestNotification

Represents a member feature request notification.

**Implements:** Node

### Fields for `MemberFeatureRequestNotification`

* `body` (String!): Represents member feature request body containing entity name and the number of feature requests.
* `id` (ID!): The Node ID of the MemberFeatureRequestNotification object.
* `title` (String!): Represents member feature request notification title.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## MembersCanDeleteReposClearAuditEntry

Audit log entry for a members\_can\_delete\_repos.clear event.

**Implements:** AuditEntry, EnterpriseAuditEntryData, Node, OrganizationAuditEntryData

### Fields for `MembersCanDeleteReposClearAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `enterpriseResourcePath` (URI): The HTTP path for this enterprise.
* `enterpriseSlug` (String): The slug of the enterprise.
* `enterpriseUrl` (URI): The HTTP URL for this enterprise.
* `id` (ID!): The Node ID of the MembersCanDeleteReposClearAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## MembersCanDeleteReposDisableAuditEntry

Audit log entry for a members\_can\_delete\_repos.disable event.

**Implements:** AuditEntry, EnterpriseAuditEntryData, Node, OrganizationAuditEntryData

### Fields for `MembersCanDeleteReposDisableAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `enterpriseResourcePath` (URI): The HTTP path for this enterprise.
* `enterpriseSlug` (String): The slug of the enterprise.
* `enterpriseUrl` (URI): The HTTP URL for this enterprise.
* `id` (ID!): The Node ID of the MembersCanDeleteReposDisableAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## MembersCanDeleteReposEnableAuditEntry

Audit log entry for a members\_can\_delete\_repos.enable event.

**Implements:** AuditEntry, EnterpriseAuditEntryData, Node, OrganizationAuditEntryData

### Fields for `MembersCanDeleteReposEnableAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `enterpriseResourcePath` (URI): The HTTP path for this enterprise.
* `enterpriseSlug` (String): The slug of the enterprise.
* `enterpriseUrl` (URI): The HTTP URL for this enterprise.
* `id` (ID!): The Node ID of the MembersCanDeleteReposEnableAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## MentionedEvent

Represents amentionedevent on a given issue or pull request.

**Implements:** Node

### Fields for `MentionedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the MentionedEvent object.

## MergeQueue

The queue of pull request entries to be merged into a protected branch in a repository.

**Implements:** Node

### Fields for `MergeQueue`

* `configuration` (MergeQueueConfiguration): The configuration for this merge queue.
* `entries` (MergeQueueEntryConnection): The entries in the queue. *(Pagination: `after`, `before`, `first`, `last`)*
* `id` (ID!): The Node ID of the MergeQueue object.
* `nextEntryEstimatedTimeToMerge` (Int): The estimated time in seconds until a newly added entry would be merged.
* `repository` (Repository): The repository this merge queue belongs to.
* `resourcePath` (URI!): The HTTP path for this merge queue.
* `url` (URI!): The HTTP URL for this merge queue.

## MergeQueueConfiguration

Configuration for a MergeQueue.

### Fields for `MergeQueueConfiguration`

* `checkResponseTimeout` (Int): The amount of time in minutes to wait for a check response before considering it a failure.
* `maximumEntriesToBuild` (Int): The maximum number of entries to build at once.
* `maximumEntriesToMerge` (Int): The maximum number of entries to merge at once.
* `mergeMethod` (PullRequestMergeMethod): The merge method to use for this queue.
* `mergingStrategy` (MergeQueueMergingStrategy): The strategy to use when merging entries.
* `minimumEntriesToMerge` (Int): The minimum number of entries required to merge at once.
* `minimumEntriesToMergeWaitTime` (Int): The amount of time in minutes to wait before ignoring the minumum number of
  entries in the queue requirement and merging a collection of entries.

## MergeQueueEntry

Entries in a MergeQueue.

**Implements:** Node

### Fields for `MergeQueueEntry`

* `baseCommit` (Commit): The base commit for this entry.
* `enqueuedAt` (DateTime!): The date and time this entry was added to the merge queue.
* `enqueuer` (Actor!): The actor that enqueued this entry.
* `estimatedTimeToMerge` (Int): The estimated time in seconds until this entry will be merged.
* `headCommit` (Commit): The head commit for this entry.
* `id` (ID!): The Node ID of the MergeQueueEntry object.
* `jump` (Boolean!): Whether this pull request should jump the queue.
* `mergeQueue` (MergeQueue): The merge queue that this entry belongs to.
* `position` (Int!): The position of this entry in the queue.
* `pullRequest` (PullRequest): The pull request that will be added to a merge group.
* `solo` (Boolean!): Does this pull request need to be deployed on its own.
* `state` (MergeQueueEntryState!): The state of this entry in the queue.

## MergeQueueParameters

Merges must be performed via a merge queue.

### Fields for `MergeQueueParameters`

* `checkResponseTimeoutMinutes` (Int!): Maximum time for a required status check to report a conclusion. After this
  much time has elapsed, checks that have not reported a conclusion will be
  assumed to have failed.
* `groupingStrategy` (MergeQueueGroupingStrategy!): When set to ALLGREEN, the merge commit created by merge queue for each PR in
  the group must pass all required checks to merge. When set to HEADGREEN, only
  the commit at the head of the merge group, i.e. the commit containing changes
  from all of the PRs in the group, must pass its required checks to merge.
* `maxEntriesToBuild` (Int!): Limit the number of queued pull requests requesting checks and workflow runs at the same time.
* `maxEntriesToMerge` (Int!): The maximum number of PRs that will be merged together in a group.
* `mergeMethod` (MergeQueueMergeMethod!): Method to use when merging changes from queued pull requests.
* `minEntriesToMerge` (Int!): The minimum number of PRs that will be merged together in a group.
* `minEntriesToMergeWaitMinutes` (Int!): The time merge queue should wait after the first PR is added to the queue for
  the minimum group size to be met. After this time has elapsed, the minimum
  group size will be ignored and a smaller group will be merged.

## MergedEvent

Represents amergedevent on a given pull request.

**Implements:** Node, UniformResourceLocatable

### Fields for `MergedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `commit` (Commit): Identifies the commit associated with the merge event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the MergedEvent object.
* `mergeRef` (Ref): Identifies the Ref associated with the merge event.
* `mergeRefName` (String!): Identifies the name of the Ref associated with the merge event.
* `pullRequest` (PullRequest!): PullRequest referenced by event.
* `resourcePath` (URI!): The HTTP path for this merged event.
* `url` (URI!): The HTTP URL for this merged event.

## MigrationSource

A GitHub Enterprise Importer (GEI) migration source.

**Implements:** Node

### Fields for `MigrationSource`

* `id` (ID!): The Node ID of the MigrationSource object.
* `name` (String!): The migration source name.
* `type` (MigrationSourceType!): The migration source type.
* `url` (URI!): The migration source URL, for example <https://github.com> or <https://monalisa.ghe.com>.

## Milestone

Represents a Milestone object on a given repository.

**Implements:** Closable, Node, UniformResourceLocatable

### Fields for `Milestone`

* `closed` (Boolean!): Indicates if the object is closed (definition of closed may depend on type).

* `closedAt` (DateTime): Identifies the date and time when the object was closed.

* `closedIssueCount` (Int!): Identifies the number of closed issues associated with the milestone.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `creator` (Actor): Identifies the actor who created the milestone.

* `description` (String): Identifies the description of the milestone.

* `descriptionHTML` (String): The HTML rendered description of the milestone using GitHub Flavored Markdown.

* `dueOn` (DateTime): Identifies the due date of the milestone.

* `id` (ID!): The Node ID of the Milestone object.

* `issues` (IssueConnection!): A list of issues associated with the milestone.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `filterBy` (IssueFilters): Filtering options for issues returned from the connection.
  * `first` (Int): Returns the first n elements from the list.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for issues returned from the connection.
  * `states` (\[IssueState!]): A list of states to filter the issues by.

* `number` (Int!): Identifies the number of the milestone.

* `openIssueCount` (Int!): Identifies the number of open issues associated with the milestone.

* `progressPercentage` (Float!): Identifies the percentage complete for the milestone.

* `pullRequests` (PullRequestConnection!): A list of pull requests associated with the milestone.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `baseRefName` (String): The base ref name to filter the pull requests by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `headRefName` (String): The head ref name to filter the pull requests by.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for pull requests returned from the connection.
  * `states` (\[PullRequestState!]): A list of states to filter the pull requests by.

* `repository` (Repository!): The repository associated with this milestone.

* `resourcePath` (URI!): The HTTP path for this milestone.

* `state` (MilestoneState!): Identifies the state of the milestone.

* `title` (String!): Identifies the title of the milestone.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this milestone.

* `viewerCanClose` (Boolean!): Indicates if the object can be closed by the viewer.

* `viewerCanReopen` (Boolean!): Indicates if the object can be reopened by the viewer.

## MilestonedEvent

Represents amilestonedevent on a given issue or pull request.

**Implements:** Node

### Fields for `MilestonedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the MilestonedEvent object.
* `milestoneTitle` (String!): Identifies the milestone title associated with themilestonedevent.
* `subject` (MilestoneItem!): Object referenced by event.

## MovedColumnsInProjectEvent

Represents amoved\_columns\_in\_projectevent on a given issue or pull request.

**Implements:** Node

### Fields for `MovedColumnsInProjectEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `id` (ID!): The Node ID of the MovedColumnsInProjectEvent object.
* `previousProjectColumnName` (String!): Column name the issue or pull request was moved from. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `project` (Project): Project referenced by event. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `projectCard` (ProjectCard): Project card referenced by this project event. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `projectColumnName` (String!): Column name the issue or pull request was moved to. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

## OIDCProvider

An OIDC identity provider configured to provision identities for an enterprise.
Visible to enterprise owners or enterprise owners' personal access tokens
(classic) with read:enterprise or admin:enterprise scope.

**Implements:** Node

### Fields for `OIDCProvider`

* `enterprise` (Enterprise): The enterprise this identity provider belongs to.

* `externalIdentities` (ExternalIdentityConnection!): ExternalIdentities provisioned by this identity provider.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `login` (String): Filter to external identities with the users login.
  * `membersOnly` (Boolean): Filter to external identities with valid org membership only.
  * `userName` (String): Filter to external identities with the users userName/NameID attribute.

* `id` (ID!): The Node ID of the OIDCProvider object.

* `providerType` (OIDCProviderType!): The OIDC identity provider type.

* `tenantId` (String!): The id of the tenant this provider is attached to.

## OauthApplicationCreateAuditEntry

Audit log entry for a oauth\_application.create event.

**Implements:** AuditEntry, Node, OauthApplicationAuditEntryData, OrganizationAuditEntryData

### Fields for `OauthApplicationCreateAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `applicationUrl` (URI): The application URL of the OAuth application. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `callbackUrl` (URI): The callback URL of the OAuth application. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OauthApplicationCreateAuditEntry object.
* `oauthApplicationName` (String): The name of the OAuth application.
* `oauthApplicationResourcePath` (URI): The HTTP path for the OAuth application.
* `oauthApplicationUrl` (URI): The HTTP URL for the OAuth application.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `rateLimit` (Int): The rate limit of the OAuth application. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `state` (OauthApplicationCreateAuditEntryState): The state of the OAuth application. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgAddBillingManagerAuditEntry

Audit log entry for a org.add\_billing\_manager.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgAddBillingManagerAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgAddBillingManagerAuditEntry object.
* `invitationEmail` (String): The email address used to invite a billing manager for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgAddMemberAuditEntry

Audit log entry for a org.add\_member.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgAddMemberAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgAddMemberAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `permission` (OrgAddMemberAuditEntryPermission): The permission level of the member added to the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgBlockUserAuditEntry

Audit log entry for a org.block\_user.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgBlockUserAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `blockedUser` (User): The blocked user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `blockedUserName` (String): The username of the blocked user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `blockedUserResourcePath` (URI): The HTTP path for the blocked user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `blockedUserUrl` (URI): The HTTP URL for the blocked user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgBlockUserAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgConfigDisableCollaboratorsOnlyAuditEntry

Audit log entry for a org.config.disable\_collaborators\_only event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgConfigDisableCollaboratorsOnlyAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgConfigDisableCollaboratorsOnlyAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgConfigEnableCollaboratorsOnlyAuditEntry

Audit log entry for a org.config.enable\_collaborators\_only event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgConfigEnableCollaboratorsOnlyAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgConfigEnableCollaboratorsOnlyAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgCreateAuditEntry

Audit log entry for a org.create event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgCreateAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `billingPlan` (OrgCreateAuditEntryBillingPlan): The billing plan for the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgCreateAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgDisableOauthAppRestrictionsAuditEntry

Audit log entry for a org.disable\_oauth\_app\_restrictions event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgDisableOauthAppRestrictionsAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgDisableOauthAppRestrictionsAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgDisableSamlAuditEntry

Audit log entry for a org.disable\_saml event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgDisableSamlAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `digestMethodUrl` (URI): The SAML provider's digest algorithm URL. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgDisableSamlAuditEntry object.
* `issuerUrl` (URI): The SAML provider's issuer URL. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `signatureMethodUrl` (URI): The SAML provider's signature algorithm URL. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `singleSignOnUrl` (URI): The SAML provider's single sign-on URL. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgDisableTwoFactorRequirementAuditEntry

Audit log entry for a org.disable\_two\_factor\_requirement event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgDisableTwoFactorRequirementAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgDisableTwoFactorRequirementAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgEnableOauthAppRestrictionsAuditEntry

Audit log entry for a org.enable\_oauth\_app\_restrictions event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgEnableOauthAppRestrictionsAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgEnableOauthAppRestrictionsAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgEnableSamlAuditEntry

Audit log entry for a org.enable\_saml event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgEnableSamlAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `digestMethodUrl` (URI): The SAML provider's digest algorithm URL. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgEnableSamlAuditEntry object.
* `issuerUrl` (URI): The SAML provider's issuer URL. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `signatureMethodUrl` (URI): The SAML provider's signature algorithm URL. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `singleSignOnUrl` (URI): The SAML provider's single sign-on URL. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgEnableTwoFactorRequirementAuditEntry

Audit log entry for a org.enable\_two\_factor\_requirement event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgEnableTwoFactorRequirementAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgEnableTwoFactorRequirementAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgInviteMemberAuditEntry

Audit log entry for a org.invite\_member event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgInviteMemberAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `email` (String): The email address of the organization invitation. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgInviteMemberAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationInvitation` (OrganizationInvitation): The organization invitation. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgInviteToBusinessAuditEntry

Audit log entry for a org.invite\_to\_business event.

**Implements:** AuditEntry, EnterpriseAuditEntryData, Node, OrganizationAuditEntryData

### Fields for `OrgInviteToBusinessAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `enterpriseResourcePath` (URI): The HTTP path for this enterprise.
* `enterpriseSlug` (String): The slug of the enterprise.
* `enterpriseUrl` (URI): The HTTP URL for this enterprise.
* `id` (ID!): The Node ID of the OrgInviteToBusinessAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgOauthAppAccessApprovedAuditEntry

Audit log entry for a org.oauth\_app\_access\_approved event.

**Implements:** AuditEntry, Node, OauthApplicationAuditEntryData, OrganizationAuditEntryData

### Fields for `OrgOauthAppAccessApprovedAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgOauthAppAccessApprovedAuditEntry object.
* `oauthApplicationName` (String): The name of the OAuth application.
* `oauthApplicationResourcePath` (URI): The HTTP path for the OAuth application.
* `oauthApplicationUrl` (URI): The HTTP URL for the OAuth application.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgOauthAppAccessBlockedAuditEntry

Audit log entry for a org.oauth\_app\_access\_blocked event.

**Implements:** AuditEntry, Node, OauthApplicationAuditEntryData, OrganizationAuditEntryData

### Fields for `OrgOauthAppAccessBlockedAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgOauthAppAccessBlockedAuditEntry object.
* `oauthApplicationName` (String): The name of the OAuth application.
* `oauthApplicationResourcePath` (URI): The HTTP path for the OAuth application.
* `oauthApplicationUrl` (URI): The HTTP URL for the OAuth application.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgOauthAppAccessDeniedAuditEntry

Audit log entry for a org.oauth\_app\_access\_denied event.

**Implements:** AuditEntry, Node, OauthApplicationAuditEntryData, OrganizationAuditEntryData

### Fields for `OrgOauthAppAccessDeniedAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgOauthAppAccessDeniedAuditEntry object.
* `oauthApplicationName` (String): The name of the OAuth application.
* `oauthApplicationResourcePath` (URI): The HTTP path for the OAuth application.
* `oauthApplicationUrl` (URI): The HTTP URL for the OAuth application.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgOauthAppAccessRequestedAuditEntry

Audit log entry for a org.oauth\_app\_access\_requested event.

**Implements:** AuditEntry, Node, OauthApplicationAuditEntryData, OrganizationAuditEntryData

### Fields for `OrgOauthAppAccessRequestedAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgOauthAppAccessRequestedAuditEntry object.
* `oauthApplicationName` (String): The name of the OAuth application.
* `oauthApplicationResourcePath` (URI): The HTTP path for the OAuth application.
* `oauthApplicationUrl` (URI): The HTTP URL for the OAuth application.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgOauthAppAccessUnblockedAuditEntry

Audit log entry for a org.oauth\_app\_access\_unblocked event.

**Implements:** AuditEntry, Node, OauthApplicationAuditEntryData, OrganizationAuditEntryData

### Fields for `OrgOauthAppAccessUnblockedAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgOauthAppAccessUnblockedAuditEntry object.
* `oauthApplicationName` (String): The name of the OAuth application.
* `oauthApplicationResourcePath` (URI): The HTTP path for the OAuth application.
* `oauthApplicationUrl` (URI): The HTTP URL for the OAuth application.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgRemoveBillingManagerAuditEntry

Audit log entry for a org.remove\_billing\_manager event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgRemoveBillingManagerAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgRemoveBillingManagerAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `reason` (OrgRemoveBillingManagerAuditEntryReason): The reason for the billing manager being removed. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgRemoveMemberAuditEntry

Audit log entry for a org.remove\_member event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgRemoveMemberAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgRemoveMemberAuditEntry object.
* `membershipTypes` (\[OrgRemoveMemberAuditEntryMembershipType!]): The types of membership the member has with the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `reason` (OrgRemoveMemberAuditEntryReason): The reason for the member being removed. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgRemoveOutsideCollaboratorAuditEntry

Audit log entry for a org.remove\_outside\_collaborator event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgRemoveOutsideCollaboratorAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgRemoveOutsideCollaboratorAuditEntry object.
* `membershipTypes` (\[OrgRemoveOutsideCollaboratorAuditEntryMembershipType!]): The types of membership the outside collaborator has with the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `reason` (OrgRemoveOutsideCollaboratorAuditEntryReason): The reason for the outside collaborator being removed from the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgRestoreMemberAuditEntry

Audit log entry for a org.restore\_member event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgRestoreMemberAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgRestoreMemberAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `restoredCustomEmailRoutingsCount` (Int): The number of custom email routings for the restored member. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `restoredIssueAssignmentsCount` (Int): The number of issue assignments for the restored member. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `restoredMemberships` (\[OrgRestoreMemberAuditEntryMembership!]): Restored organization membership objects. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `restoredMembershipsCount` (Int): The number of restored memberships. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `restoredRepositoriesCount` (Int): The number of repositories of the restored member. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `restoredRepositoryStarsCount` (Int): The number of starred repositories for the restored member. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `restoredRepositoryWatchesCount` (Int): The number of watched repositories for the restored member. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgRestoreMemberMembershipOrganizationAuditEntryData

Metadata for an organization membership for org.restore\_member actions.

**Implements:** OrganizationAuditEntryData

### Fields for `OrgRestoreMemberMembershipOrganizationAuditEntryData`

* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgRestoreMemberMembershipRepositoryAuditEntryData

Metadata for a repository membership for org.restore\_member actions.

**Implements:** RepositoryAuditEntryData

### Fields for `OrgRestoreMemberMembershipRepositoryAuditEntryData`

* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.

## OrgRestoreMemberMembershipTeamAuditEntryData

Metadata for a team membership for org.restore\_member actions.

**Implements:** TeamAuditEntryData

### Fields for `OrgRestoreMemberMembershipTeamAuditEntryData`

* `team` (Team): The team associated with the action.
* `teamName` (String): The name of the team.
* `teamResourcePath` (URI): The HTTP path for this team.
* `teamUrl` (URI): The HTTP URL for this team.

## OrgUnblockUserAuditEntry

Audit log entry for a org.unblock\_user.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgUnblockUserAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `blockedUser` (User): The user being unblocked by the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `blockedUserName` (String): The username of the blocked user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `blockedUserResourcePath` (URI): The HTTP path for the blocked user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `blockedUserUrl` (URI): The HTTP URL for the blocked user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgUnblockUserAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgUpdateDefaultRepositoryPermissionAuditEntry

Audit log entry for a org.update\_default\_repository\_permission.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgUpdateDefaultRepositoryPermissionAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgUpdateDefaultRepositoryPermissionAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `permission` (OrgUpdateDefaultRepositoryPermissionAuditEntryPermission): The new base repository permission level for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `permissionWas` (OrgUpdateDefaultRepositoryPermissionAuditEntryPermission): The former base repository permission level for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgUpdateMemberAuditEntry

Audit log entry for a org.update\_member event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgUpdateMemberAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgUpdateMemberAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `permission` (OrgUpdateMemberAuditEntryPermission): The new member permission level for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `permissionWas` (OrgUpdateMemberAuditEntryPermission): The former member permission level for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgUpdateMemberRepositoryCreationPermissionAuditEntry

Audit log entry for a org.update\_member\_repository\_creation\_permission event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgUpdateMemberRepositoryCreationPermissionAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `canCreateRepositories` (Boolean): Can members create repositories in the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgUpdateMemberRepositoryCreationPermissionAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `visibility` (OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility): The permission for visibility level of repositories for this organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## OrgUpdateMemberRepositoryInvitationPermissionAuditEntry

Audit log entry for a org.update\_member\_repository\_invitation\_permission event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData

### Fields for `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `canInviteOutsideCollaboratorsToRepositories` (Boolean): Can outside collaborators be invited to repositories in the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the OrgUpdateMemberRepositoryInvitationPermissionAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## Organization

An account on GitHub, with one or more owners, that has repositories, members and teams.

**Implements:** Actor, MemberStatusable, Node, PackageOwner, ProfileOwner, ProjectOwner, ProjectV2Owner, ProjectV2Recent, RepositoryDiscussionAuthor, RepositoryDiscussionCommentAuthor, RepositoryOwner, Sponsorable, UniformResourceLocatable

### Fields for `Organization`

* `announcementBanner` (AnnouncementBanner): The announcement banner set on this organization, if any. Only visible to members of the organization's enterprise.

* `anyPinnableItems` (Boolean!): Determine if this repository owner has any items that can be pinned to their profile.
  * `type` (PinnableItemType): Filter to only a particular kind of pinnable item.

* `archivedAt` (DateTime): Identifies the date and time when the organization was archived.

* `auditLog` (OrganizationAuditEntryConnection!): Audit log entries of the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (AuditLogOrder): Ordering options for the returned audit log entries.
  * `query` (String): The query string to filter audit entries.

* `avatarUrl` (URI!): A URL pointing to the organization's public avatar.
  * `size` (Int): The size of the resulting square image.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `description` (String): The organization's public profile description.

* `descriptionHTML` (String): The organization's public profile description rendered to HTML.

* `domains` (VerifiableDomainConnection): A list of domains owned by the organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `isApproved` (Boolean): Filter by if the domain is approved.
  * `isVerified` (Boolean): Filter by if the domain is verified.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (VerifiableDomainOrder): Ordering options for verifiable domains returned.

* `email` (String): The organization's public email.

* `enterpriseOwners` (OrganizationEnterpriseOwnerConnection!): A list of owners of the organization's enterprise account.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrgEnterpriseOwnerOrder): Ordering options for enterprise owners returned from the connection.
  * `organizationRole` (RoleInOrganization): The organization role to filter by.
  * `query` (String): The search string to look for.

* `estimatedNextSponsorsPayoutInCents` (Int!): The estimated next GitHub Sponsors payout for this user/organization in cents (USD).

* `hasSponsorsListing` (Boolean!): True if this user/organization has a GitHub Sponsors listing.

* `id` (ID!): The Node ID of the Organization object.

* `interactionAbility` (RepositoryInteractionAbility): The interaction ability settings for this organization.

* `ipAllowListEnabledSetting` (IpAllowListEnabledSettingValue!): The setting value for whether the organization has an IP allow list enabled.

* `ipAllowListEntries` (IpAllowListEntryConnection!): The IP addresses that are allowed to access resources owned by the organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IpAllowListEntryOrder): Ordering options for IP allow list entries returned.

* `ipAllowListForInstalledAppsEnabledSetting` (IpAllowListForInstalledAppsEnabledSettingValue!): The setting value for whether the organization has IP allow list configuration for installed GitHub Apps enabled.

* `isSponsoredBy` (Boolean!): Whether the given account is sponsoring this user/organization.
  * `accountLogin` (String!): The target account's login.

* `isSponsoringViewer` (Boolean!): True if the viewer is sponsored by this user/organization.

* `isVerified` (Boolean!): Whether the organization has verified its profile email and website.

* `issueFields` (IssueFieldsConnection): A list of the organization's issue fields.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueFieldOrder): Ordering options for issue fields returned from the connection.

* `issueTypes` (IssueTypeConnection): A list of the organization's issue types.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueTypeOrder): Ordering options for issue types returned from the connection.

* `itemShowcase` (ProfileItemShowcase!): Showcases a selection of repositories and gists that the profile owner has
  either curated or that have been selected automatically based on popularity.

* `lifetimeReceivedSponsorshipValues` (SponsorAndLifetimeValueConnection!): Calculate how much each sponsor has ever paid total to this maintainer via
  GitHub Sponsors. Does not include sponsorships paid via Patreon.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorAndLifetimeValueOrder): Ordering options for results returned from the connection.

* `location` (String): The organization's public profile location.

* `login` (String!): The organization's login name.

* `mannequins` (MannequinConnection!): A list of all mannequins for this organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `login` (String): Filter mannequins by login.
  * `orderBy` (MannequinOrder): Ordering options for mannequins returned from the connection.

* `memberStatuses` (UserStatusConnection!): Get the status messages members of this entity have set that are either public or visible only to the organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (UserStatusOrder): Ordering options for user statuses returned from the connection.

* `membersCanForkPrivateRepositories` (Boolean!): Members can fork private repositories in this organization.

* `membersWithRole` (OrganizationMemberConnection!): A list of users who are members of this organization. *(Pagination: `after`, `before`, `first`, `last`)*

* `monthlyEstimatedSponsorsIncomeInCents` (Int!): The estimated monthly GitHub Sponsors income for this user/organization in cents (USD).

* `name` (String): The organization's public profile name.

* `newTeamResourcePath` (URI!): The HTTP path creating a new team.

* `newTeamUrl` (URI!): The HTTP URL creating a new team.

* `notificationDeliveryRestrictionEnabledSetting` (NotificationRestrictionSettingValue!): Indicates if email notification delivery for this organization is restricted to verified or approved domains.

* `organizationBillingEmail` (String): The billing email for the organization.

* `packages` (PackageConnection!): A list of packages under the owner.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `names` (\[String]): Find packages by their names.
  * `orderBy` (PackageOrder): Ordering of the returned packages.
  * `packageType` (PackageType): Filter registry package by type.
  * `repositoryId` (ID): Find packages in a repository by ID.

* `pendingMembers` (UserConnection!): A list of users who have been invited to join this organization. *(Pagination: `after`, `before`, `first`, `last`)*

* `pinnableItems` (PinnableItemConnection!): A list of repositories and gists this profile owner can pin to their profile.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `types` (\[PinnableItemType!]): Filter the types of pinnable items that are returned.

* `pinnedItems` (PinnableItemConnection!): A list of repositories and gists this profile owner has pinned to their profile.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `types` (\[PinnableItemType!]): Filter the types of pinned items that are returned.

* `pinnedItemsRemaining` (Int!): Returns how many more items this profile owner can pin to their profile.

* `project` (Project): Find project by number. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `number` (Int!): The project number to find.

* `projectV2` (ProjectV2): Find a project by number.
  * `number` (Int!): The project number.

* `projects` (ProjectConnection!): A list of projects under the owner. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectOrder): Ordering options for projects returned from the connection.
  * `search` (String): Query to search projects by, currently only searching by name.
  * `states` (\[ProjectState!]): A list of states to filter the projects by.

* `projectsResourcePath` (URI!): The HTTP path listing organization's projects.

* `projectsUrl` (URI!): The HTTP URL listing organization's projects.

* `projectsV2` (ProjectV2Connection!): A list of projects under the owner.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `minPermissionLevel` (ProjectV2PermissionLevel): Filter projects based on user role. Default: `READ`.
  * `orderBy` (ProjectV2Order): How to order the returned projects.
  * `query` (String): A project to search for under the owner.

* `recentProjects` (ProjectV2Connection!): Recent projects that this user has modified in the context of the owner. *(Pagination: `after`, `before`, `first`, `last`)*

* `repositories` (RepositoryConnection!): A list of repositories that the user owns.
  * `affiliations` (\[RepositoryAffiliation]): Array of viewer's affiliation options for repositories returned from the
    connection. For example, OWNER will include only repositories that the
    current viewer owns.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `hasIssuesEnabled` (Boolean): If non-null, filters repositories according to whether they have issues enabled.
  * `isArchived` (Boolean): If non-null, filters repositories according to whether they are archived and not maintained.
  * `isFork` (Boolean): If non-null, filters repositories according to whether they are forks of another repository.
  * `isLocked` (Boolean): If non-null, filters repositories according to whether they have been locked.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder): Ordering options for repositories returned from the connection.
  * `ownerAffiliations` (\[RepositoryAffiliation]): Array of owner's affiliation options for repositories returned from the
    connection. For example, OWNER will include only repositories that the
    organization or user being viewed owns.
  * `privacy` (RepositoryPrivacy): If non-null, filters repositories according to privacy. Internal
    repositories are considered private; consider using the visibility argument
    if only internal repositories are needed. Cannot be combined with the
    visibility argument.
  * `visibility` (RepositoryVisibility): If non-null, filters repositories according to visibility. Cannot be combined with the privacy argument.

* `repository` (Repository): Find Repository.
  * `followRenames` (Boolean): Follow repository renames. If disabled, a repository referenced by its old name will return an error. Default: `true`.
  * `name` (String!): Name of Repository to find.

* `repositoryCustomProperties` (RepositoryCustomPropertyConnection): A list of custom properties for this organization. *(Pagination: `after`, `before`, `first`, `last`)*

* `repositoryCustomProperty` (RepositoryCustomProperty): Returns a single custom property from the current organization by name.
  * `propertyName` (String!): The name of the custom property to be returned.

* `repositoryDiscussionComments` (DiscussionCommentConnection!): Discussion comments this user has authored.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `onlyAnswers` (Boolean): Filter discussion comments to only those that were marked as the answer.
  * `repositoryId` (ID): Filter discussion comments to only those in a specific repository.

* `repositoryDiscussions` (DiscussionConnection!): Discussions this user has started.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `answered` (Boolean): Filter discussions to only those that have been answered or not. Defaults to
    including both answered and unanswered discussions.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (DiscussionOrder): Ordering options for discussions returned from the connection.
  * `repositoryId` (ID): Filter discussions to only those in a specific repository.
  * `states` (\[DiscussionState!]): A list of states to filter the discussions by.

* `repositoryMigrations` (RepositoryMigrationConnection!): A list of all repository migrations for this organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryMigrationOrder): Ordering options for repository migrations returned.
  * `repositoryName` (String): Filter repository migrations by repository name.
  * `state` (MigrationState): Filter repository migrations by state.

* `requiresTwoFactorAuthentication` (Boolean): When true the organization requires all members, billing managers, and outside
  collaborators to enable two-factor authentication.

* `resourcePath` (URI!): The HTTP path for this organization.

* `ruleset` (RepositoryRuleset): Returns a single ruleset from the current organization by ID.
  * `databaseId` (Int!): The ID of the ruleset to be returned.
  * `includeParents` (Boolean): Include rulesets configured at higher levels that apply to this organization. Default: `true`.

* `rulesets` (RepositoryRulesetConnection): A list of rulesets for this organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includeParents` (Boolean): Return rulesets configured at higher levels that apply to this organization. Default: `true`.
  * `last` (Int): Returns the last n elements from the list.
  * `targets` (\[RepositoryRulesetTarget!]): Return rulesets that apply to the specified target.

* `samlIdentityProvider` (OrganizationIdentityProvider): The Organization's SAML identity provider. Visible to (1) organization owners,
  (2) organization owners' personal access tokens (classic) with read:org or
  admin:org scope, (3) GitHub App with an installation token with read or write
  access to members.

* `sponsoring` (SponsorConnection!): List of users and organizations this entity is sponsoring.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorOrder): Ordering options for the users and organizations returned from the connection.

* `sponsors` (SponsorConnection!): List of sponsors for this user or organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorOrder): Ordering options for sponsors returned from the connection.
  * `tierId` (ID): If given, will filter for sponsors at the given tier. Will only return
    sponsors whose tier the viewer is permitted to see.

* `sponsorsActivities` (SponsorsActivityConnection!): Events involving this sponsorable, such as new sponsorships.
  * `actions` (\[SponsorsActivityAction!]): Filter activities to only the specified actions.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includeAsSponsor` (Boolean): Whether to include those events where this sponsorable acted as the sponsor.
    Defaults to only including events where this sponsorable was the recipient
    of a sponsorship.
  * `includePrivate` (Boolean): Whether or not to include private activities in the result set. Defaults to including public and private activities. Default: `true`.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorsActivityOrder): Ordering options for activity returned from the connection.
  * `period` (SponsorsActivityPeriod): Filter activities returned to only those that occurred in the most recent
    specified time period. Set to ALL to avoid filtering by when the activity
    occurred. Will be ignored if since or until is given. Default: `MONTH`.
  * `since` (DateTime): Filter activities to those that occurred on or after this time.
  * `until` (DateTime): Filter activities to those that occurred before this time.

* `sponsorsListing` (SponsorsListing): The GitHub Sponsors listing for this user or organization.

* `sponsorshipForViewerAsSponsor` (Sponsorship): The sponsorship from the viewer to this user/organization; that is, the sponsorship where you're the sponsor.
  * `activeOnly` (Boolean): Whether to return the sponsorship only if it's still active. Pass false to
    get the viewer's sponsorship back even if it has been cancelled. Default: `true`.

* `sponsorshipForViewerAsSponsorable` (Sponsorship): The sponsorship from this user/organization to the viewer; that is, the sponsorship you're receiving.
  * `activeOnly` (Boolean): Whether to return the sponsorship only if it's still active. Pass false to
    get the sponsorship back even if it has been cancelled. Default: `true`.

* `sponsorshipNewsletters` (SponsorshipNewsletterConnection!): List of sponsorship updates sent from this sponsorable to sponsors.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorshipNewsletterOrder): Ordering options for sponsorship updates returned from the connection.

* `sponsorshipsAsMaintainer` (SponsorshipConnection!): The sponsorships where this user or organization is the maintainer receiving the funds.
  * `activeOnly` (Boolean): Whether to include only sponsorships that are active right now, versus all
    sponsorships this maintainer has ever received. Default: `true`.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includePrivate` (Boolean): Whether or not to include private sponsorships in the result set.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorshipOrder): Ordering options for sponsorships returned from this connection. If left
    blank, the sponsorships will be ordered based on relevancy to the viewer.

* `sponsorshipsAsSponsor` (SponsorshipConnection!): The sponsorships where this user or organization is the funder.
  * `activeOnly` (Boolean): Whether to include only sponsorships that are active right now, versus all sponsorships this sponsor has ever made. Default: `true`.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `maintainerLogins` (\[String!]): Filter sponsorships returned to those for the specified maintainers. That
    is, the recipient of the sponsorship is a user or organization with one of
    the given logins.
  * `orderBy` (SponsorshipOrder): Ordering options for sponsorships returned from this connection. If left
    blank, the sponsorships will be ordered based on relevancy to the viewer.

* `team` (Team): Find an organization's team by its slug.
  * `slug` (String!): The name or slug of the team to find.

* `teams` (TeamConnection!): A list of teams in this organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `ldapMapped` (Boolean): If true, filters teams that are mapped to an LDAP Group (Enterprise only).
  * `notificationSetting` (TeamNotificationSetting): If non-null, filters teams according to notification setting.
  * `orderBy` (TeamOrder): Ordering options for teams returned from the connection.
  * `privacy` (TeamPrivacy): If non-null, filters teams according to privacy.
  * `query` (String): If non-null, filters teams with query on team name and team slug.
  * `role` (TeamRole): If non-null, filters teams according to whether the viewer is an admin or member on team.
  * `rootTeamsOnly` (Boolean): If true, restrict to only root teams.
  * `userLogins` (\[String!]): User logins to filter by.

* `teamsResourcePath` (URI!): The HTTP path listing organization's teams.

* `teamsUrl` (URI!): The HTTP URL listing organization's teams.

* `totalSponsorshipAmountAsSponsorInCents` (Int): The amount in United States cents (e.g., 500 = $5.00 USD) that this entity has
  spent on GitHub to fund sponsorships. Only returns a value when viewed by the
  user themselves or by a user who can manage sponsorships for the requested organization.
  * `since` (DateTime): Filter payments to those that occurred on or after this time.
  * `sponsorableLogins` (\[String!]): Filter payments to those made to the users or organizations with the specified usernames.
  * `until` (DateTime): Filter payments to those that occurred before this time.

* `twitterUsername` (String): The organization's Twitter username.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this organization.

* `viewerCanAdminister` (Boolean!): Organization is adminable by the viewer.

* `viewerCanChangePinnedItems` (Boolean!): Can the viewer pin repositories and gists to the profile?.

* `viewerCanCreateProjects` (Boolean!): Can the current viewer create new projects on this owner. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `viewerCanCreateRepositories` (Boolean!): Viewer can create repositories on this organization.

* `viewerCanCreateTeams` (Boolean!): Viewer can create teams on this organization.

* `viewerCanSponsor` (Boolean!): Whether or not the viewer is able to sponsor this user/organization.

* `viewerIsAMember` (Boolean!): Viewer is an active member of this organization.

* `viewerIsFollowing` (Boolean!): Whether or not this Organization is followed by the viewer.

* `viewerIsSponsoring` (Boolean!): True if the viewer is sponsoring this user/organization.

* `webCommitSignoffRequired` (Boolean!): Whether contributors are required to sign off on web-based commits for repositories in this organization.

* `websiteUrl` (URI): The organization's public profile URL.

## OrganizationEnterpriseOwnerEdge

An enterprise owner in the context of an organization that is part of the enterprise.

### Fields for `OrganizationEnterpriseOwnerEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (User): The item at the end of the edge.
* `organizationRole` (RoleInOrganization!): The role of the owner with respect to the organization.

## OrganizationIdentityProvider

An Identity Provider configured to provision SAML and SCIM identities for
Organizations. Visible to (1) organization owners, (2) organization owners'
personal access tokens (classic) with read:org or admin:org scope, (3) GitHub
App with an installation token with read or write access to members.

**Implements:** Node

### Fields for `OrganizationIdentityProvider`

* `digestMethod` (URI): The digest algorithm used to sign SAML requests for the Identity Provider.

* `externalIdentities` (ExternalIdentityConnection!): External Identities provisioned by this Identity Provider.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `login` (String): Filter to external identities with the users login.
  * `membersOnly` (Boolean): Filter to external identities with valid org membership only.
  * `userName` (String): Filter to external identities with the users userName/NameID attribute.

* `id` (ID!): The Node ID of the OrganizationIdentityProvider object.

* `idpCertificate` (X509Certificate): The x509 certificate used by the Identity Provider to sign assertions and responses.

* `issuer` (String): The Issuer Entity ID for the SAML Identity Provider.

* `organization` (Organization): Organization this Identity Provider belongs to.

* `signatureMethod` (URI): The signature algorithm used to sign SAML requests for the Identity Provider.

* `ssoUrl` (URI): The URL endpoint for the Identity Provider's SAML SSO.

## OrganizationInvitation

An Invitation for a user to an organization.

**Implements:** Node

### Fields for `OrganizationInvitation`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `email` (String): The email address of the user invited to the organization.
* `id` (ID!): The Node ID of the OrganizationInvitation object.
* `invitationSource` (OrganizationInvitationSource!): The source of the invitation.
* `invitationType` (OrganizationInvitationType!): The type of invitation that was sent (e.g. email, user).
* `invitee` (User): The user who was invited to the organization.
* `inviter` (User!): The user who created the invitation. **Deprecated:** inviter will be removed. inviter will be replaced by inviterActor. Removal on 2024-07-01 UTC.
* `inviterActor` (User): The user who created the invitation.
* `organization` (Organization!): The organization the invite is for.
* `role` (OrganizationInvitationRole!): The user's pending role in the organization (e.g. member, owner).

## OrganizationMemberEdge

Represents a user within an organization.

### Fields for `OrganizationMemberEdge`

* `cursor` (String!): A cursor for use in pagination.
* `hasTwoFactorEnabled` (Boolean): Whether the organization member has two factor enabled or not. Returns null if information is not available to viewer.
* `node` (User): The item at the end of the edge.
* `role` (OrganizationMemberRole): The role this user has in the organization.

## OrganizationMigration

A GitHub Enterprise Importer (GEI) organization migration.

**Implements:** Node

### Fields for `OrganizationMigration`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (String): Identifies the primary key from the database.
* `failureReason` (String): The reason the organization migration failed.
* `id` (ID!): The Node ID of the OrganizationMigration object.
* `remainingRepositoriesCount` (Int): The remaining amount of repos to be migrated.
* `sourceOrgName` (String!): The name of the source organization to be migrated.
* `sourceOrgUrl` (URI!): The URL of the source organization to migrate.
* `state` (OrganizationMigrationState!): The migration state.
* `targetOrgName` (String!): The name of the target organization.
* `totalRepositoriesCount` (Int): The total amount of repositories to be migrated.

## OrganizationPropertyConditionTarget

Parameters to be used for the organization\_property condition.

### Fields for `OrganizationPropertyConditionTarget`

* `exclude` (\[OrganizationPropertyTargetDefinition!]!): Array of organization properties that must not match.
* `include` (\[OrganizationPropertyTargetDefinition!]!): Array of organization properties that must match.

## OrganizationPropertyTargetDefinition

A property that must match.

### Fields for `OrganizationPropertyTargetDefinition`

* `name` (String!): The name of the property.
* `propertyValues` (\[String!]!): The values to match for.

## OrganizationTeamsHovercardContext

An organization teams hovercard context.

**Implements:** HovercardContext

### Fields for `OrganizationTeamsHovercardContext`

* `message` (String!): A string describing this context.
* `octicon` (String!): An octicon to accompany this context.
* `relevantTeams` (TeamConnection!): Teams in this organization the user is a member of that are relevant. *(Pagination: `after`, `before`, `first`, `last`)*
* `teamsResourcePath` (URI!): The path for the full team list for this user.
* `teamsUrl` (URI!): The URL for the full team list for this user.
* `totalTeamCount` (Int!): The total number of teams the user is on in the organization.

## OrganizationsHovercardContext

An organization list hovercard context.

**Implements:** HovercardContext

### Fields for `OrganizationsHovercardContext`

* `message` (String!): A string describing this context.

* `octicon` (String!): An octicon to accompany this context.

* `relevantOrganizations` (OrganizationConnection!): Organizations this user is a member of that are relevant.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for the User's organizations.

* `totalOrganizationCount` (Int!): The total number of organizations this user is in.

## Package

Information for an uploaded package.

**Implements:** Node

### Fields for `Package`

* `id` (ID!): The Node ID of the Package object.

* `latestVersion` (PackageVersion): Find the latest version for the package.

* `name` (String!): Identifies the name of the package.

* `packageType` (PackageType!): Identifies the type of the package.

* `repository` (Repository): The repository this package belongs to.

* `statistics` (PackageStatistics): Statistics about package activity.

* `version` (PackageVersion): Find package version by version string.
  * `version` (String!): The package version.

* `versions` (PackageVersionConnection!): list of versions for this package.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (PackageVersionOrder): Ordering of the returned packages.

## PackageFile

A file in a package version.

**Implements:** Node

### Fields for `PackageFile`

* `id` (ID!): The Node ID of the PackageFile object.
* `md5` (String): MD5 hash of the file.
* `name` (String!): Name of the file.
* `packageVersion` (PackageVersion): The package version this file belongs to.
* `sha1` (String): SHA1 hash of the file.
* `sha256` (String): SHA256 hash of the file.
* `size` (Int): Size of the file in bytes.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.
* `url` (URI): URL to download the asset.

## PackageStatistics

Represents a object that contains package activity statistics such as downloads.

### Fields for `PackageStatistics`

* `downloadsTotalCount` (Int!): Number of times the package was downloaded since it was created.

## PackageTag

A version tag contains the mapping between a tag name and a version.

**Implements:** Node

### Fields for `PackageTag`

* `id` (ID!): The Node ID of the PackageTag object.
* `name` (String!): Identifies the tag name of the version.
* `version` (PackageVersion): Version that the tag is associated with.

## PackageVersion

Information about a specific package version.

**Implements:** Node

### Fields for `PackageVersion`

* `files` (PackageFileConnection!): List of files associated with this package version.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (PackageFileOrder): Ordering of the returned package files.

* `id` (ID!): The Node ID of the PackageVersion object.

* `package` (Package): The package associated with this version.

* `platform` (String): The platform this version was built for.

* `preRelease` (Boolean!): Whether or not this version is a pre-release.

* `readme` (String): The README of this package version.

* `release` (Release): The release associated with this package version.

* `statistics` (PackageVersionStatistics): Statistics about package activity.

* `summary` (String): The package version summary.

* `version` (String!): The version string.

## PackageVersionStatistics

Represents a object that contains package version activity statistics such as downloads.

### Fields for `PackageVersionStatistics`

* `downloadsTotalCount` (Int!): Number of times the package was downloaded since it was created.

## PageInfo

Information about pagination in a connection.

### Fields for `PageInfo`

* `endCursor` (String): When paginating forwards, the cursor to continue.
* `hasNextPage` (Boolean!): When paginating forwards, are there more items?.
* `hasPreviousPage` (Boolean!): When paginating backwards, are there more items?.
* `startCursor` (String): When paginating backwards, the cursor to continue.

## ParentIssueAddedEvent

Represents aparent\_issue\_addedevent on a given issue.

**Implements:** Node

### Fields for `ParentIssueAddedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ParentIssueAddedEvent object.
* `parent` (Issue): The parent issue added.

## ParentIssueRemovedEvent

Represents aparent\_issue\_removedevent on a given issue.

**Implements:** Node

### Fields for `ParentIssueRemovedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ParentIssueRemovedEvent object.
* `parent` (Issue): The parent issue removed.

## PermissionSource

A level of permission and source for a user's access to a repository.

### Fields for `PermissionSource`

* `organization` (Organization!): The organization the repository belongs to.
* `permission` (DefaultRepositoryPermissionField!): The level of access this source has granted to the user.
* `roleName` (String): The name of the role this source has granted to the user.
* `source` (PermissionGranter!): The source of this permission.

## PinnedDiscussion

A Pinned Discussion is a discussion pinned to a repository's index page.

**Implements:** Node, RepositoryNode

### Fields for `PinnedDiscussion`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `discussion` (Discussion!): The discussion that was pinned.
* `gradientStopColors` (\[String!]!): Color stops of the chosen gradient.
* `id` (ID!): The Node ID of the PinnedDiscussion object.
* `pattern` (PinnedDiscussionPattern!): Background texture pattern.
* `pinnedBy` (Actor!): The actor that pinned this discussion.
* `preconfiguredGradient` (PinnedDiscussionGradient): Preconfigured background gradient option.
* `repository` (Repository!): The repository associated with this node.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## PinnedEnvironment

Represents a pinned environment on a given repository.

**Implements:** Node

### Fields for `PinnedEnvironment`

* `createdAt` (DateTime!): Identifies the date and time when the pinned environment was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `environment` (Environment!): Identifies the environment associated.
* `id` (ID!): The Node ID of the PinnedEnvironment object.
* `position` (Int!): Identifies the position of the pinned environment.
* `repository` (Repository!): The repository that this environment was pinned to.

## PinnedEvent

Represents apinnedevent on a given issue or pull request.

**Implements:** Node

### Fields for `PinnedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the PinnedEvent object.
* `issue` (Issue!): Identifies the issue associated with the event.

## PinnedIssue

A Pinned Issue is a issue pinned to a repository's index page.

**Implements:** Node

### Fields for `PinnedIssue`

* `databaseId` (Int): Identifies the primary key from the database.
* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.
* `id` (ID!): The Node ID of the PinnedIssue object.
* `issue` (Issue!): The issue that was pinned.
* `pinnedBy` (Actor!): The actor that pinned this issue.
* `repository` (Repository!): The repository that this issue was pinned to.

## PinnedIssueComment

A comment pinned to an Issue.

**Implements:** Node

### Fields for `PinnedIssueComment`

* `databaseId` (Int): Identifies the primary key from the database.
* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.
* `id` (ID!): The Node ID of the PinnedIssueComment object.
* `issue` (Issue!): The issue that this comment belongs to.
* `issueComment` (IssueComment!): The comment that was pinned.
* `pinnedAt` (DateTime!): Identifies when the comment was pinned.
* `pinnedBy` (Actor!): The actor that pinned this comment.

## PrivateRepositoryForkingDisableAuditEntry

Audit log entry for a private\_repository\_forking.disable event.

**Implements:** AuditEntry, EnterpriseAuditEntryData, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `PrivateRepositoryForkingDisableAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `enterpriseResourcePath` (URI): The HTTP path for this enterprise.
* `enterpriseSlug` (String): The slug of the enterprise.
* `enterpriseUrl` (URI): The HTTP URL for this enterprise.
* `id` (ID!): The Node ID of the PrivateRepositoryForkingDisableAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## PrivateRepositoryForkingEnableAuditEntry

Audit log entry for a private\_repository\_forking.enable event.

**Implements:** AuditEntry, EnterpriseAuditEntryData, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `PrivateRepositoryForkingEnableAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `enterpriseResourcePath` (URI): The HTTP path for this enterprise.
* `enterpriseSlug` (String): The slug of the enterprise.
* `enterpriseUrl` (URI): The HTTP URL for this enterprise.
* `id` (ID!): The Node ID of the PrivateRepositoryForkingEnableAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## ProfileItemShowcase

A curatable list of repositories relating to a repository owner, which defaults
to showing the most popular repositories they own.

### Fields for `ProfileItemShowcase`

* `hasPinnedItems` (Boolean!): Whether or not the owner has pinned any repositories or gists.
* `items` (PinnableItemConnection!): The repositories and gists in the showcase. If the profile owner has any
  pinned items, those will be returned. Otherwise, the profile owner's popular
  repositories will be returned. *(Pagination: `after`, `before`, `first`, `last`)*

## Project

Projects manage issues, pull requests and notes within a project owner.

**Implements:** Closable, Node, Updatable

### Fields for `Project`

* `body` (String): The project's description body. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `bodyHTML` (HTML!): The projects description body rendered to HTML. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `closed` (Boolean!): Indicates if the object is closed (definition of closed may depend on type).

* `closedAt` (DateTime): Identifies the date and time when the object was closed.

* `columns` (ProjectColumnConnection!): List of columns in the project. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC. *(Pagination: `after`, `before`, `first`, `last`)*

* `createdAt` (DateTime!): Identifies the date and time when the object was created. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `creator` (Actor): The actor who originally created the project. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `id` (ID!): The Node ID of the Project object. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `name` (String!): The project's name. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `number` (Int!): The project's number. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `owner` (ProjectOwner!): The project's owner. Currently limited to repositories, organizations, and users. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `pendingCards` (ProjectCardConnection!): List of pending cards in this project. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `archivedStates` (\[ProjectCardArchivedState]): A list of archived states to filter the cards by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.

* `progress` (ProjectProgress!): Project progress details. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `resourcePath` (URI!): The HTTP path for this project. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `state` (ProjectState!): Whether the project is open or closed. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `url` (URI!): The HTTP URL for this project. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `viewerCanClose` (Boolean!): Indicates if the object can be closed by the viewer.

* `viewerCanReopen` (Boolean!): Indicates if the object can be reopened by the viewer.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

## ProjectCard

A card in a project.

**Implements:** Node

### Fields for `ProjectCard`

* `column` (ProjectColumn): The project column this card is associated under. A card may only belong to one
  project column at a time. The column field will be null if the card is created
  in a pending state and has yet to be associated with a column. Once cards are
  associated with a column, they will not become pending in the future. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `content` (ProjectCardItem): The card content item. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `createdAt` (DateTime!): Identifies the date and time when the object was created. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `creator` (Actor): The actor who created this card. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `id` (ID!): The Node ID of the ProjectCard object. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `isArchived` (Boolean!): Whether the card is archived. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `note` (String): The card note. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `project` (Project!): The project that contains this card. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `resourcePath` (URI!): The HTTP path for this card. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `state` (ProjectCardState): The state of ProjectCard. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `url` (URI!): The HTTP URL for this card. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

## ProjectColumn

A column inside a project.

**Implements:** Node

### Fields for `ProjectColumn`

* `cards` (ProjectCardConnection!): List of cards in the column. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `archivedStates` (\[ProjectCardArchivedState]): A list of archived states to filter the cards by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.

* `createdAt` (DateTime!): Identifies the date and time when the object was created. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `id` (ID!): The Node ID of the ProjectColumn object. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `name` (String!): The project column's name. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `project` (Project!): The project that contains this column. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `purpose` (ProjectColumnPurpose): The semantic purpose of the column. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `resourcePath` (URI!): The HTTP path for this project column. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `url` (URI!): The HTTP URL for this project column. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

## ProjectProgress

Project progress stats.

### Fields for `ProjectProgress`

* `doneCount` (Int!): The number of done cards. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `donePercentage` (Float!): The percentage of done cards. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `enabled` (Boolean!): Whether progress tracking is enabled and cards with purpose exist for this project. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `inProgressCount` (Int!): The number of in-progress cards. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `inProgressPercentage` (Float!): The percentage of in-progress cards. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `todoCount` (Int!): The number of to do cards. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `todoPercentage` (Float!): The percentage of to do cards. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

## ProjectV2

New projects that manage issues, pull requests and drafts using tables and boards.

**Implements:** Closable, Node, Updatable

### Fields for `ProjectV2`

* `closed` (Boolean!): Returns true if the project is closed.

* `closedAt` (DateTime): Identifies the date and time when the object was closed.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `creator` (Actor): The actor who originally created the project.

* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** databaseId will be removed because it does not support 64-bit signed integer identifiers. Use fullDatabaseId instead. Removal on 2025-04-01 UTC.

* `field` (ProjectV2FieldConfiguration): A field of the project.
  * `name` (String!): The name of the field.

* `fields` (ProjectV2FieldConfigurationConnection!): List of fields and their constraints in the project.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2FieldOrder): Ordering options for project v2 fields returned from the connection.

* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.

* `id` (ID!): The Node ID of the ProjectV2 object.

* `items` (ProjectV2ItemConnection!): List of items in the project.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2ItemOrder): Ordering options for project v2 items returned from the connection.
  * `query` (String): Search query for filtering items. Default: \`\`.

* `number` (Int!): The project's number.

* `owner` (ProjectV2Owner!): The project's owner. Currently limited to organizations and users.

* `public` (Boolean!): Returns true if the project is public.

* `readme` (String): The project's readme.

* `repositories` (RepositoryConnection!): The repositories the project is linked to.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder): Ordering options for repositories returned from the connection.

* `resourcePath` (URI!): The HTTP path for this project.

* `shortDescription` (String): The project's short description.

* `statusUpdates` (ProjectV2StatusUpdateConnection!): List of the status updates in the project.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2StatusOrder): Order for connection.

* `teams` (TeamConnection!): The teams the project is linked to.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (TeamOrder): Ordering options for teams returned from this connection.

* `template` (Boolean!): Returns true if this project is a template.

* `title` (String!): The project's name.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this project.

* `view` (ProjectV2View): A view of the project.
  * `number` (Int!): The number of a view belonging to the project.

* `viewerCanClose` (Boolean!): Indicates if the object can be closed by the viewer.

* `viewerCanReopen` (Boolean!): Indicates if the object can be reopened by the viewer.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

* `views` (ProjectV2ViewConnection!): List of views in the project.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2ViewOrder): Ordering options for project v2 views returned from the connection.

* `workflow` (ProjectV2Workflow): A workflow of the project.
  * `number` (Int!): The number of a workflow belonging to the project.

* `workflows` (ProjectV2WorkflowConnection!): List of the workflows in the project.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2WorkflowOrder): Ordering options for project v2 workflows returned from the connection.

## ProjectV2Field

A field inside a project.

**Implements:** Node, ProjectV2FieldCommon

### Fields for `ProjectV2Field`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `dataType` (ProjectV2FieldType!): The field's type.
* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the ProjectV2Field object.
* `name` (String!): The project field's name.
* `project` (ProjectV2!): The project that contains this field.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2Item

An item within a Project.

**Implements:** Node

### Fields for `ProjectV2Item`

* `content` (ProjectV2ItemContent): The content of the referenced draft issue, issue, pull request.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `creator` (Actor): The actor who created the item.

* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** databaseId will be removed because it does not support 64-bit signed integer identifiers. Use fullDatabaseId instead. Removal on 2025-04-01 UTC.

* `fieldValueByName` (ProjectV2ItemFieldValue): The field value of the first project field which matches thenameargument that is set on the item.
  * `name` (String!): The name of the field to return the field value of.

* `fieldValues` (ProjectV2ItemFieldValueConnection!): The field values that are set on the item.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2ItemFieldValueOrder): Ordering options for project v2 item field values returned from the connection.

* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.

* `id` (ID!): The Node ID of the ProjectV2Item object.

* `isArchived` (Boolean!): Whether the item is archived.

* `project` (ProjectV2!): The project that contains this item.

* `type` (ProjectV2ItemType!): The type of the item.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2ItemFieldDateValue

The value of a date field in a Project item.

**Implements:** Node, ProjectV2ItemFieldValueCommon

### Fields for `ProjectV2ItemFieldDateValue`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor): The actor who created the item.
* `databaseId` (Int): Identifies the primary key from the database.
* `date` (Date): Date value for the field.
* `field` (ProjectV2FieldConfiguration!): The project field that contains this value.
* `id` (ID!): The Node ID of the ProjectV2ItemFieldDateValue object.
* `item` (ProjectV2Item!): The project item that contains this value.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2ItemFieldIterationValue

The value of an iteration field in a Project item.

**Implements:** Node, ProjectV2ItemFieldValueCommon

### Fields for `ProjectV2ItemFieldIterationValue`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor): The actor who created the item.
* `databaseId` (Int): Identifies the primary key from the database.
* `duration` (Int!): The duration of the iteration in days.
* `field` (ProjectV2FieldConfiguration!): The project field that contains this value.
* `id` (ID!): The Node ID of the ProjectV2ItemFieldIterationValue object.
* `item` (ProjectV2Item!): The project item that contains this value.
* `iterationId` (String!): The ID of the iteration.
* `startDate` (Date!): The start date of the iteration.
* `title` (String!): The title of the iteration.
* `titleHTML` (String!): The title of the iteration, with HTML.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2ItemFieldLabelValue

The value of the labels field in a Project item.

### Fields for `ProjectV2ItemFieldLabelValue`

* `field` (ProjectV2FieldConfiguration!): The field that contains this value.
* `labels` (LabelConnection): Labels value of a field. *(Pagination: `after`, `before`, `first`, `last`)*

## ProjectV2ItemFieldMilestoneValue

The value of a milestone field in a Project item.

### Fields for `ProjectV2ItemFieldMilestoneValue`

* `field` (ProjectV2FieldConfiguration!): The field that contains this value.
* `milestone` (Milestone): Milestone value of a field.

## ProjectV2ItemFieldNumberValue

The value of a number field in a Project item.

**Implements:** Node, ProjectV2ItemFieldValueCommon

### Fields for `ProjectV2ItemFieldNumberValue`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor): The actor who created the item.
* `databaseId` (Int): Identifies the primary key from the database.
* `field` (ProjectV2FieldConfiguration!): The project field that contains this value.
* `id` (ID!): The Node ID of the ProjectV2ItemFieldNumberValue object.
* `item` (ProjectV2Item!): The project item that contains this value.
* `number` (Float): Number as a float(8).
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2ItemFieldPullRequestValue

The value of a pull request field in a Project item.

### Fields for `ProjectV2ItemFieldPullRequestValue`

* `field` (ProjectV2FieldConfiguration!): The field that contains this value.
* `pullRequests` (PullRequestConnection): The pull requests for this field.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (PullRequestOrder): Ordering options for pull requests.

## ProjectV2ItemFieldRepositoryValue

The value of a repository field in a Project item.

### Fields for `ProjectV2ItemFieldRepositoryValue`

* `field` (ProjectV2FieldConfiguration!): The field that contains this value.
* `repository` (Repository): The repository for this field.

## ProjectV2ItemFieldReviewerValue

The value of a reviewers field in a Project item.

### Fields for `ProjectV2ItemFieldReviewerValue`

* `field` (ProjectV2FieldConfiguration!): The field that contains this value.
* `reviewers` (RequestedReviewerConnection): The reviewers for this field. *(Pagination: `after`, `before`, `first`, `last`)*

## ProjectV2ItemFieldSingleSelectValue

The value of a single select field in a Project item.

**Implements:** Node, ProjectV2ItemFieldValueCommon

### Fields for `ProjectV2ItemFieldSingleSelectValue`

* `color` (ProjectV2SingleSelectFieldOptionColor!): The color applied to the selected single-select option.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor): The actor who created the item.
* `databaseId` (Int): Identifies the primary key from the database.
* `description` (String): A plain-text description of the selected single-select option, such as what the option means.
* `descriptionHTML` (String): The description of the selected single-select option, including HTML tags.
* `field` (ProjectV2FieldConfiguration!): The project field that contains this value.
* `id` (ID!): The Node ID of the ProjectV2ItemFieldSingleSelectValue object.
* `item` (ProjectV2Item!): The project item that contains this value.
* `name` (String): The name of the selected single select option.
* `nameHTML` (String): The html name of the selected single select option.
* `optionId` (String): The id of the selected single select option.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2ItemFieldTextValue

The value of a text field in a Project item.

**Implements:** Node, ProjectV2ItemFieldValueCommon

### Fields for `ProjectV2ItemFieldTextValue`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor): The actor who created the item.
* `databaseId` (Int): Identifies the primary key from the database.
* `field` (ProjectV2FieldConfiguration!): The project field that contains this value.
* `id` (ID!): The Node ID of the ProjectV2ItemFieldTextValue object.
* `item` (ProjectV2Item!): The project item that contains this value.
* `text` (String): Text value of a field.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2ItemFieldUserValue

The value of a user field in a Project item.

### Fields for `ProjectV2ItemFieldUserValue`

* `field` (ProjectV2FieldConfiguration!): The field that contains this value.
* `users` (UserConnection): The users for this field. *(Pagination: `after`, `before`, `first`, `last`)*

## ProjectV2ItemIssueFieldValue

The value of an issue field in a Project item.

### Fields for `ProjectV2ItemIssueFieldValue`

* `field` (ProjectV2FieldConfiguration!): Field that contains this value.
* `issueFieldValue` (ProjectV2IssueFieldValues): Value of the Issue Field.

## ProjectV2ItemStatusChangedEvent

Represents aproject\_v2\_item\_status\_changedevent on a given issue or pull request.

**Implements:** Node, ProjectV2Event

### Fields for `ProjectV2ItemStatusChangedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ProjectV2ItemStatusChangedEvent object.
* `previousStatus` (String!): The previous status of the project item.
* `project` (ProjectV2): Project referenced by event.
* `status` (String!): The new status of the project item.
* `wasAutomated` (Boolean!): Did this event result from workflow automation?.

## ProjectV2IterationField

An iteration field inside a project.

**Implements:** Node, ProjectV2FieldCommon

### Fields for `ProjectV2IterationField`

* `configuration` (ProjectV2IterationFieldConfiguration!): Iteration configuration settings.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `dataType` (ProjectV2FieldType!): The field's type.
* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the ProjectV2IterationField object.
* `name` (String!): The project field's name.
* `project` (ProjectV2!): The project that contains this field.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2IterationFieldConfiguration

Iteration field configuration for a project.

### Fields for `ProjectV2IterationFieldConfiguration`

* `completedIterations` (\[ProjectV2IterationFieldIteration!]!): The iteration's completed iterations.
* `duration` (Int!): The iteration's duration in days.
* `iterations` (\[ProjectV2IterationFieldIteration!]!): The iteration's iterations.
* `startDay` (Int!): The iteration's start day of the week.

## ProjectV2IterationFieldIteration

Iteration field iteration settings for a project.

### Fields for `ProjectV2IterationFieldIteration`

* `duration` (Int!): The iteration's duration in days.
* `id` (String!): The iteration's ID.
* `startDate` (Date!): The iteration's start date.
* `title` (String!): The iteration's title.
* `titleHTML` (String!): The iteration's html title.

## ProjectV2SingleSelectField

A single select field inside a project.

**Implements:** Node, ProjectV2FieldCommon

### Fields for `ProjectV2SingleSelectField`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `dataType` (ProjectV2FieldType!): The field's type.

* `databaseId` (Int): Identifies the primary key from the database.

* `id` (ID!): The Node ID of the ProjectV2SingleSelectField object.

* `name` (String!): The project field's name.

* `options` (\[ProjectV2SingleSelectFieldOption!]!): Options for the single select field.
  * `names` (\[String!]): Filter returned options to only those matching these names, case insensitive.

* `project` (ProjectV2!): The project that contains this field.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2SingleSelectFieldOption

Single select field option for a configuration for a project.

### Fields for `ProjectV2SingleSelectFieldOption`

* `color` (ProjectV2SingleSelectFieldOptionColor!): The option's display color.
* `description` (String!): The option's plain-text description.
* `descriptionHTML` (String!): The option's description, possibly containing HTML.
* `id` (String!): The option's ID.
* `name` (String!): The option's name.
* `nameHTML` (String!): The option's html name.

## ProjectV2SortBy

Represents a sort by field and direction.

### Fields for `ProjectV2SortBy`

* `direction` (OrderDirection!): The direction of the sorting. Possible values are ASC and DESC.
* `field` (ProjectV2Field!): The field by which items are sorted.

## ProjectV2SortByField

Represents a sort by field and direction.

### Fields for `ProjectV2SortByField`

* `direction` (OrderDirection!): The direction of the sorting. Possible values are ASC and DESC.
* `field` (ProjectV2FieldConfiguration!): The field by which items are sorted.

## ProjectV2StatusUpdate

A status update within a project.

**Implements:** Node

### Fields for `ProjectV2StatusUpdate`

* `body` (String): The body of the status update.
* `bodyHTML` (HTML): The body of the status update rendered to HTML.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor): The actor who created the status update.
* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** databaseId will be removed because it does not support 64-bit signed integer identifiers. Use fullDatabaseId instead. Removal on 2025-04-01 UTC.
* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.
* `id` (ID!): The Node ID of the ProjectV2StatusUpdate object.
* `project` (ProjectV2!): The project that contains this status update.
* `startDate` (Date): The start date of the status update.
* `status` (ProjectV2StatusUpdateStatus): The status of the status update.
* `targetDate` (Date): The target date of the status update.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2View

A view within a ProjectV2.

**Implements:** Node

### Fields for `ProjectV2View`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** databaseId will be removed because it does not support 64-bit signed integer identifiers. Use fullDatabaseId instead. Removal on 2025-04-01 UTC.

* `fields` (ProjectV2FieldConfigurationConnection): The view's visible fields.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2FieldOrder): Ordering options for the project v2 fields returned from the connection.

* `filter` (String): The project view's filter.

* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.

* `groupBy` (ProjectV2FieldConnection): The view's group-by field. **Deprecated:** The ProjectV2View#order\_by API is deprecated in favour of the more capable ProjectV2View#group\_by\_field API. Check out the ProjectV2View#group\_by\_fields API as an example for the more capable alternative. Removal on 2023-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2FieldOrder): Ordering options for the project v2 fields returned from the connection.

* `groupByFields` (ProjectV2FieldConfigurationConnection): The view's group-by field.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2FieldOrder): Ordering options for the project v2 fields returned from the connection.

* `id` (ID!): The Node ID of the ProjectV2View object.

* `layout` (ProjectV2ViewLayout!): The project view's layout.

* `name` (String!): The project view's name.

* `number` (Int!): The project view's number.

* `project` (ProjectV2!): The project that contains this view.

* `sortBy` (ProjectV2SortByConnection): The view's sort-by config. **Deprecated:** The ProjectV2View#sort\_by API is deprecated in favour of the more capable ProjectV2View#sort\_by\_fields API. Check out the ProjectV2View#sort\_by\_fields API as an example for the more capable alternative. Removal on 2023-04-01 UTC. *(Pagination: `after`, `before`, `first`, `last`)*

* `sortByFields` (ProjectV2SortByFieldConnection): The view's sort-by config. *(Pagination: `after`, `before`, `first`, `last`)*

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `verticalGroupBy` (ProjectV2FieldConnection): The view's vertical-group-by field. **Deprecated:** The ProjectV2View#vertical\_group\_by API is deprecated in favour of the more capable ProjectV2View#vertical\_group\_by\_fields API. Check out the ProjectV2View#vertical\_group\_by\_fields API as an example for the more capable alternative. Removal on 2023-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2FieldOrder): Ordering options for the project v2 fields returned from the connection.

* `verticalGroupByFields` (ProjectV2FieldConfigurationConnection): The view's vertical-group-by field.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2FieldOrder): Ordering options for the project v2 fields returned from the connection.

* `visibleFields` (ProjectV2FieldConnection): The view's visible fields. **Deprecated:** The ProjectV2View#visibleFields API is deprecated in favour of the more capable ProjectV2View#fields API. Check out the ProjectV2View#fields API as an example for the more capable alternative. Removal on 2023-01-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectV2FieldOrder): Ordering options for the project v2 fields returned from the connection.

## ProjectV2Workflow

A workflow inside a project.

**Implements:** Node

### Fields for `ProjectV2Workflow`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** databaseId will be removed because it does not support 64-bit signed integer identifiers. Use fullDatabaseId instead. Removal on 2025-04-01 UTC.
* `enabled` (Boolean!): Whether the workflow is enabled.
* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.
* `id` (ID!): The Node ID of the ProjectV2Workflow object.
* `name` (String!): The name of the workflow.
* `number` (Int!): The number of the workflow.
* `project` (ProjectV2!): The project that contains this workflow.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## PropertyTargetDefinition

A property that must match.

### Fields for `PropertyTargetDefinition`

* `name` (String!): The name of the property.
* `propertyValues` (\[String!]!): The values to match for.
* `source` (String): The source of the property. Choosecustomor 'system'. Defaults to 'custom' if not specified.

## PublicKey

A user's public key.

**Implements:** Node

### Fields for `PublicKey`

* `accessedAt` (DateTime): The last time this authorization was used to perform an action. Values will be null for keys not owned by the user.
* `createdAt` (DateTime): Identifies the date and time when the key was created. Keys created before
  March 5th, 2014 have inaccurate values. Values will be null for keys not owned by the user.
* `fingerprint` (String!): The fingerprint for this PublicKey.
* `id` (ID!): The Node ID of the PublicKey object.
* `isReadOnly` (Boolean): Whether this PublicKey is read-only or not. Values will be null for keys not owned by the user.
* `key` (String!): The public key string.
* `updatedAt` (DateTime): Identifies the date and time when the key was updated. Keys created before
  March 5th, 2014 may have inaccurate values. Values will be null for keys not
  owned by the user.

## PullRequest

A repository pull request.

**Implements:** Assignable, Closable, Comment, Labelable, Lockable, Node, ProjectV2Owner, Reactable, RepositoryNode, Subscribable, UniformResourceLocatable, Updatable, UpdatableComment

### Fields for `PullRequest`

* `activeLockReason` (LockReason): Reason that the conversation was locked.

* `additions` (Int!): The number of additions in this pull request.

* `assignedActors` (AssigneeConnection!): A list of actors assigned to this object. *(Pagination: `after`, `before`, `first`, `last`)*

* `assignees` (UserConnection!): A list of Users assigned to this object. *(Pagination: `after`, `before`, `first`, `last`)*

* `author` (Actor): The actor who authored the comment.

* `authorAssociation` (CommentAuthorAssociation!): Author's association with the subject of the comment.

* `autoMergeRequest` (AutoMergeRequest): Returns the auto-merge request object if one exists for this pull request.

* `baseRef` (Ref): Identifies the base Ref associated with the pull request.

* `baseRefName` (String!): Identifies the name of the base Ref associated with the pull request, even if the ref has been deleted.

* `baseRefOid` (GitObjectID!): Identifies the oid of the base ref associated with the pull request, even if the ref has been deleted.

* `baseRepository` (Repository): The repository associated with this pull request's base Ref.

* `body` (String!): The body as Markdown.

* `bodyHTML` (HTML!): The body rendered to HTML.

* `bodyText` (String!): The body rendered to text.

* `canBeRebased` (Boolean!): Whether or not the pull request is rebaseable.

* `changedFiles` (Int!): The number of changed files in this pull request.

* `checksResourcePath` (URI!): The HTTP path for the checks of this pull request.

* `checksUrl` (URI!): The HTTP URL for the checks of this pull request.

* `closed` (Boolean!): true if the pull request is closed.

* `closedAt` (DateTime): Identifies the date and time when the object was closed.

* `closingIssuesReferences` (IssueConnection): List of issues that may be closed by this pull request.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for issues returned from the connection.
  * `userLinkedOnly` (Boolean): Return only manually linked Issues.

* `comments` (IssueCommentConnection!): A list of comments associated with the pull request.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueCommentOrder): Ordering options for issue comments returned from the connection.

* `commits` (PullRequestCommitConnection!): A list of commits present in this pull request's head branch not present in the base branch. *(Pagination: `after`, `before`, `first`, `last`)*

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.

* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** databaseId will be removed because it does not support 64-bit signed integer identifiers. Use fullDatabaseId instead. Removal on 2024-07-01 UTC.

* `deletions` (Int!): The number of deletions in this pull request.

* `editor` (Actor): The actor who edited this pull request's body.

* `files` (PullRequestChangedFileConnection): Lists the files changed within this pull request. *(Pagination: `after`, `before`, `first`, `last`)*

* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.

* `headRef` (Ref): Identifies the head Ref associated with the pull request.

* `headRefName` (String!): Identifies the name of the head Ref associated with the pull request, even if the ref has been deleted.

* `headRefOid` (GitObjectID!): Identifies the oid of the head ref associated with the pull request, even if the ref has been deleted.

* `headRepository` (Repository): The repository associated with this pull request's head Ref.

* `headRepositoryOwner` (RepositoryOwner): The owner of the repository associated with this pull request's head Ref.

* `hovercard` (Hovercard!): The hovercard information for this issue.
  * `includeNotificationContexts` (Boolean): Whether or not to include notification contexts. Default: `true`.

* `id` (ID!): The Node ID of the PullRequest object.

* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.

* `isCrossRepository` (Boolean!): The head and base repositories are different.

* `isDraft` (Boolean!): Identifies if the pull request is a draft.

* `isInMergeQueue` (Boolean!): Indicates whether the pull request is in a merge queue.

* `isMergeQueueEnabled` (Boolean!): Indicates whether the pull request's base ref has a merge queue enabled.

* `isReadByViewer` (Boolean): Is this pull request read by the viewer.

* `labels` (LabelConnection): A list of labels associated with the object.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (LabelOrder): Ordering options for labels returned from the connection.

* `lastEditedAt` (DateTime): The moment the editor made the last edit.

* `latestOpinionatedReviews` (PullRequestReviewConnection): A list of latest reviews per user associated with the pull request.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `writersOnly` (Boolean): Only return reviews from user who have write access to the repository.

* `latestReviews` (PullRequestReviewConnection): A list of latest reviews per user associated with the pull request that are not also pending review. *(Pagination: `after`, `before`, `first`, `last`)*

* `locked` (Boolean!): true if the pull request is locked.

* `maintainerCanModify` (Boolean!): Indicates whether maintainers can modify the pull request.

* `mergeCommit` (Commit): The commit that was created when this pull request was merged.

* `mergeQueue` (MergeQueue): The merge queue for the pull request's base branch.

* `mergeQueueEntry` (MergeQueueEntry): The merge queue entry of the pull request in the base branch's merge queue.

* `mergeStateStatus` (MergeStateStatus!): Detailed information about the current pull request merge state status.

* `mergeable` (MergeableState!): Whether or not the pull request can be merged based on the existence of merge conflicts.

* `merged` (Boolean!): Whether or not the pull request was merged.

* `mergedAt` (DateTime): The date and time that the pull request was merged.

* `mergedBy` (Actor): The actor who merged the pull request.

* `milestone` (Milestone): Identifies the milestone associated with the pull request.

* `number` (Int!): Identifies the pull request number.

* `participants` (UserConnection!): A list of Users that are participating in the Pull Request conversation. *(Pagination: `after`, `before`, `first`, `last`)*

* `permalink` (URI!): The permalink to the pull request.

* `potentialMergeCommit` (Commit): The commit that GitHub automatically generated to test if this pull request
  could be merged. This field will not return a value if the pull request is
  merged, or if the test merge commit is still being generated. See the
  mergeable field for more details on the mergeability of the pull request.

* `projectCards` (ProjectCardConnection!): List of project cards associated with this pull request. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `archivedStates` (\[ProjectCardArchivedState]): A list of archived states to filter the cards by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.

* `projectItems` (ProjectV2ItemConnection): List of project items associated with this pull request.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includeArchived` (Boolean): Include archived items. Default: `true`.
  * `last` (Int): Returns the last n elements from the list.

* `projectV2` (ProjectV2): Find a project by number.
  * `number` (Int!): The project number.

* `projectsV2` (ProjectV2Connection!): A list of projects under the owner.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `minPermissionLevel` (ProjectV2PermissionLevel): Filter projects based on user role. Default: `READ`.
  * `orderBy` (ProjectV2Order): How to order the returned projects.
  * `query` (String): A project to search for under the owner.

* `publishedAt` (DateTime): Identifies when the comment was published at.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `repository` (Repository!): The repository associated with this node.

* `resourcePath` (URI!): The HTTP path for this pull request.

* `revertResourcePath` (URI!): The HTTP path for reverting this pull request.

* `revertUrl` (URI!): The HTTP URL for reverting this pull request.

* `reviewDecision` (PullRequestReviewDecision): The current status of this pull request with respect to code review.

* `reviewRequests` (ReviewRequestConnection): A list of review requests associated with the pull request. *(Pagination: `after`, `before`, `first`, `last`)*

* `reviewThreads` (PullRequestReviewThreadConnection!): The list of all review threads for this pull request. *(Pagination: `after`, `before`, `first`, `last`)*

* `reviews` (PullRequestReviewConnection): A list of reviews associated with the pull request.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `author` (String): Filter by author of the review.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `states` (\[PullRequestReviewState!]): A list of states to filter the reviews.

* `state` (PullRequestState!): Identifies the state of the pull request.

* `statusCheckRollup` (StatusCheckRollup): Check and Status rollup information for the PR's head ref.

* `suggestedActors` (AssigneeConnection!): A list of suggested actors to assign to this object.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `query` (String): If provided, searches users by login or profile name.

* `suggestedReviewerActors` (SuggestedReviewerActorConnection!): Reviewer actor suggestions based on commit history, past review comments, and integrations.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `query` (String): Search actors with query on user name and login.

* `suggestedReviewers` (\[SuggestedReviewer]!): A list of reviewer suggestions based on commit history and past review comments.

* `timeline` (PullRequestTimelineConnection!): A list of events, comments, commits, etc. associated with the pull request. **Deprecated:** timeline will be removed Use PullRequest.timelineItems instead. Removal on 2020-10-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `since` (DateTime): Allows filtering timeline events by a since timestamp.

* `timelineItems` (PullRequestTimelineItemsConnection!): A list of events, comments, commits, etc. associated with the pull request.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `itemTypes` (\[PullRequestTimelineItemsItemType!]): Filter timeline items by type.
  * `last` (Int): Returns the last n elements from the list.
  * `since` (DateTime): Filter timeline items by a since timestamp.
  * `skip` (Int): Skips the first n elements in the list.

* `title` (String!): Identifies the pull request title.

* `titleHTML` (HTML!): Identifies the pull request title rendered to HTML.

* `totalCommentsCount` (Int): Returns a count of how many comments this pull request has received.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this pull request.

* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*

* `viewerCanApplySuggestion` (Boolean!): Whether or not the viewer can apply suggestion.

* `viewerCanClose` (Boolean!): Indicates if the object can be closed by the viewer.

* `viewerCanDeleteHeadRef` (Boolean!): Check if the viewer can restore the deleted head ref.

* `viewerCanDisableAutoMerge` (Boolean!): Whether or not the viewer can disable auto-merge.

* `viewerCanEditFiles` (Boolean!): Can the viewer edit files within this pull request.

* `viewerCanEnableAutoMerge` (Boolean!): Whether or not the viewer can enable auto-merge.

* `viewerCanLabel` (Boolean!): Indicates if the viewer can edit labels for this object.

* `viewerCanMergeAsAdmin` (Boolean!): Indicates whether the viewer can bypass branch protections and merge the pull request immediately.

* `viewerCanReact` (Boolean!): Can user react to this subject.

* `viewerCanReopen` (Boolean!): Indicates if the object can be reopened by the viewer.

* `viewerCanSubscribe` (Boolean!): Check if the viewer is able to change their subscription status for the repository.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

* `viewerCanUpdateBranch` (Boolean!): Whether or not the viewer can update the head ref of this PR, by merging or rebasing the base ref.
  If the head ref is up to date or unable to be updated by this user, this will return false.

* `viewerCannotUpdateReasons` (\[CommentCannotUpdateReason!]!): Reasons why the current viewer can not update this comment.

* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

* `viewerLatestReview` (PullRequestReview): The latest review given from the viewer.

* `viewerLatestReviewRequest` (ReviewRequest): The person who has requested the viewer for review on this pull request.

* `viewerMergeBodyText` (String!): The merge body text for the viewer and method.
  * `mergeType` (PullRequestMergeMethod): The merge method for the message.

* `viewerMergeHeadlineText` (String!): The merge headline text for the viewer and method.
  * `mergeType` (PullRequestMergeMethod): The merge method for the message.

* `viewerSubscription` (SubscriptionState): Identifies if the viewer is watching, not watching, or ignoring the subscribable entity.

## PullRequestChangedFile

A file changed in a pull request.

### Fields for `PullRequestChangedFile`

* `additions` (Int!): The number of additions to the file.
* `changeType` (PatchStatus!): How the file was changed in this PullRequest.
* `deletions` (Int!): The number of deletions to the file.
* `path` (String!): The path of the file.
* `viewerViewedState` (FileViewedState!): The state of the file for the viewer.

## PullRequestCommit

Represents a Git commit part of a pull request.

**Implements:** Node, UniformResourceLocatable

### Fields for `PullRequestCommit`

* `commit` (Commit!): The Git commit object.
* `id` (ID!): The Node ID of the PullRequestCommit object.
* `pullRequest` (PullRequest!): The pull request this commit belongs to.
* `resourcePath` (URI!): The HTTP path for this pull request commit.
* `url` (URI!): The HTTP URL for this pull request commit.

## PullRequestCommitCommentThread

Represents a commit comment thread part of a pull request.

**Implements:** Node, RepositoryNode

### Fields for `PullRequestCommitCommentThread`

* `comments` (CommitCommentConnection!): The comments that exist in this thread. *(Pagination: `after`, `before`, `first`, `last`)*
* `commit` (Commit!): The commit the comments were made on.
* `id` (ID!): The Node ID of the PullRequestCommitCommentThread object.
* `path` (String): The file the comments were made on.
* `position` (Int): The position in the diff for the commit that the comment was made on.
* `pullRequest` (PullRequest!): The pull request this commit comment thread belongs to.
* `repository` (Repository!): The repository associated with this node.

## PullRequestContributionsByRepository

This aggregates pull requests opened by a user within one repository.

### Fields for `PullRequestContributionsByRepository`

* `contributions` (CreatedPullRequestContributionConnection!): The pull request contributions.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ContributionOrder): Ordering options for contributions returned from the connection.

* `repository` (Repository!): The repository in which the pull requests were opened.

## PullRequestParameters

Require all commits be made to a non-target branch and submitted via a pull request before they can be merged.

### Fields for `PullRequestParameters`

* `allowedMergeMethods` (\[PullRequestAllowedMergeMethods!]): Array of allowed merge methods. Allowed values include merge, squash, and
  rebase. At least one option must be enabled.
* `dismissStaleReviewsOnPush` (Boolean!): New, reviewable commits pushed will dismiss previous pull request review approvals.
* `requireCodeOwnerReview` (Boolean!): Require an approving review in pull requests that modify files that have a designated code owner.
* `requireLastPushApproval` (Boolean!): Whether the most recent reviewable push must be approved by someone other than the person who pushed it.
* `requiredApprovingReviewCount` (Int!): The number of approving reviews that are required before a pull request can be merged.
* `requiredReviewThreadResolution` (Boolean!): All conversations on code must be resolved before a pull request can be merged.
* `requiredReviewers` (\[RequiredReviewerConfiguration!]): This field is in beta and subject to change. A collection of reviewers and
  associated file patterns. Each reviewer has a list of file patterns which
  determine the files that reviewer is required to review.

## PullRequestReview

A review object for a given pull request.

**Implements:** Comment, Deletable, Minimizable, Node, Reactable, RepositoryNode, Updatable, UpdatableComment

### Fields for `PullRequestReview`

* `author` (Actor): The actor who authored the comment.

* `authorAssociation` (CommentAuthorAssociation!): Author's association with the subject of the comment.

* `authorCanPushToRepository` (Boolean!): Indicates whether the author of this review has push access to the repository.

* `body` (String!): Identifies the pull request review body.

* `bodyHTML` (HTML!): The body rendered to HTML.

* `bodyText` (String!): The body of this review rendered as plain text.

* `comments` (PullRequestReviewCommentConnection!): A list of review comments for the current pull request review. *(Pagination: `after`, `before`, `first`, `last`)*

* `commit` (Commit): Identifies the commit associated with this pull request review.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.

* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** databaseId will be removed because it does not support 64-bit signed integer identifiers. Use fullDatabaseId instead. Removal on 2024-07-01 UTC.

* `editor` (Actor): The actor who edited the comment.

* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.

* `id` (ID!): The Node ID of the PullRequestReview object.

* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.

* `isMinimized` (Boolean!): Returns whether or not a comment has been minimized.

* `lastEditedAt` (DateTime): The moment the editor made the last edit.

* `minimizedReason` (String): Returns why the comment was minimized. One of abuse, off-topic,
  outdated, resolved, duplicate, spam, and low-quality. Note that the
  case and formatting of these values differs from the inputs to the
  MinimizeComment mutation.

* `onBehalfOf` (TeamConnection!): A list of teams that this review was made on behalf of. *(Pagination: `after`, `before`, `first`, `last`)*

* `publishedAt` (DateTime): Identifies when the comment was published at.

* `pullRequest` (PullRequest!): Identifies the pull request associated with this pull request review.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `repository` (Repository!): The repository associated with this node.

* `resourcePath` (URI!): The HTTP path permalink for this PullRequestReview.

* `state` (PullRequestReviewState!): Identifies the current state of the pull request review.

* `submittedAt` (DateTime): Identifies when the Pull Request Review was submitted.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL permalink for this PullRequestReview.

* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*

* `viewerCanDelete` (Boolean!): Check if the current viewer can delete this object.

* `viewerCanMinimize` (Boolean!): Check if the current viewer can minimize this object.

* `viewerCanReact` (Boolean!): Can user react to this subject.

* `viewerCanUnminimize` (Boolean!): Check if the current viewer can unminimize this object.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

* `viewerCannotUpdateReasons` (\[CommentCannotUpdateReason!]!): Reasons why the current viewer can not update this comment.

* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

## PullRequestReviewComment

A review comment associated with a given repository pull request.

**Implements:** Comment, Deletable, Minimizable, Node, Reactable, RepositoryNode, Updatable, UpdatableComment

### Fields for `PullRequestReviewComment`

* `author` (Actor): The actor who authored the comment.

* `authorAssociation` (CommentAuthorAssociation!): Author's association with the subject of the comment.

* `body` (String!): The comment body of this review comment.

* `bodyHTML` (HTML!): The body rendered to HTML.

* `bodyText` (String!): The comment body of this review comment rendered as plain text.

* `commit` (Commit): Identifies the commit associated with the comment.

* `createdAt` (DateTime!): Identifies when the comment was created.

* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.

* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** databaseId will be removed because it does not support 64-bit signed integer identifiers. Use fullDatabaseId instead. Removal on 2024-07-01 UTC.

* `diffHunk` (String!): The diff hunk to which the comment applies.

* `draftedAt` (DateTime!): Identifies when the comment was created in a draft state.

* `editor` (Actor): The actor who edited the comment.

* `fullDatabaseId` (BigInt): Identifies the primary key from the database as a BigInt.

* `id` (ID!): The Node ID of the PullRequestReviewComment object.

* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.

* `isMinimized` (Boolean!): Returns whether or not a comment has been minimized.

* `lastEditedAt` (DateTime): The moment the editor made the last edit.

* `line` (Int): The end line number on the file to which the comment applies.

* `minimizedReason` (String): Returns why the comment was minimized. One of abuse, off-topic,
  outdated, resolved, duplicate, spam, and low-quality. Note that the
  case and formatting of these values differs from the inputs to the
  MinimizeComment mutation.

* `originalCommit` (Commit): Identifies the original commit associated with the comment.

* `originalLine` (Int): The end line number on the file to which the comment applied when it was first created.

* `originalPosition` (Int!): The original line index in the diff to which the comment applies. **Deprecated:** We are phasing out diff-relative positioning for PR comments Removal on 2023-10-01 UTC.

* `originalStartLine` (Int): The start line number on the file to which the comment applied when it was first created.

* `outdated` (Boolean!): Identifies when the comment body is outdated.

* `path` (String!): The path to which the comment applies.

* `position` (Int): The line index in the diff to which the comment applies. **Deprecated:** We are phasing out diff-relative positioning for PR comments Use the line and startLine fields instead, which are file line numbers instead of diff line numbers Removal on 2023-10-01 UTC.

* `publishedAt` (DateTime): Identifies when the comment was published at.

* `pullRequest` (PullRequest!): The pull request associated with this review comment.

* `pullRequestReview` (PullRequestReview): The pull request review associated with this review comment.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `replyTo` (PullRequestReviewComment): The comment this is a reply to.

* `repository` (Repository!): The repository associated with this node.

* `resourcePath` (URI!): The HTTP path permalink for this review comment.

* `startLine` (Int): The start line number on the file to which the comment applies.

* `state` (PullRequestReviewCommentState!): Identifies the state of the comment.

* `subjectType` (PullRequestReviewThreadSubjectType!): The level at which the comments in the corresponding thread are targeted, can be a diff line or a file.

* `updatedAt` (DateTime!): Identifies when the comment was last updated.

* `url` (URI!): The HTTP URL permalink for this review comment.

* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*

* `viewerCanDelete` (Boolean!): Check if the current viewer can delete this object.

* `viewerCanMinimize` (Boolean!): Check if the current viewer can minimize this object.

* `viewerCanReact` (Boolean!): Can user react to this subject.

* `viewerCanUnminimize` (Boolean!): Check if the current viewer can unminimize this object.

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

* `viewerCannotUpdateReasons` (\[CommentCannotUpdateReason!]!): Reasons why the current viewer can not update this comment.

* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

## PullRequestReviewContributionsByRepository

This aggregates pull request reviews made by a user within one repository.

### Fields for `PullRequestReviewContributionsByRepository`

* `contributions` (CreatedPullRequestReviewContributionConnection!): The pull request review contributions.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ContributionOrder): Ordering options for contributions returned from the connection.

* `repository` (Repository!): The repository in which the pull request reviews were made.

## PullRequestReviewThread

A threaded list of comments for a given pull request.

**Implements:** Node

### Fields for `PullRequestReviewThread`

* `comments` (PullRequestReviewCommentConnection!): A list of pull request comments associated with the thread.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `skip` (Int): Skips the first n elements in the list.

* `diffSide` (DiffSide!): The side of the diff on which this thread was placed.

* `id` (ID!): The Node ID of the PullRequestReviewThread object.

* `isCollapsed` (Boolean!): Whether or not the thread has been collapsed (resolved).

* `isOutdated` (Boolean!): Indicates whether this thread was outdated by newer changes.

* `isResolved` (Boolean!): Whether this thread has been resolved.

* `line` (Int): The line in the file to which this thread refers.

* `originalLine` (Int): The original line in the file to which this thread refers.

* `originalStartLine` (Int): The original start line in the file to which this thread refers (multi-line only).

* `path` (String!): Identifies the file path of this thread.

* `pullRequest` (PullRequest!): Identifies the pull request associated with this thread.

* `repository` (Repository!): Identifies the repository associated with this thread.

* `resolvedBy` (User): The user who resolved this thread.

* `startDiffSide` (DiffSide): The side of the diff that the first line of the thread starts on (multi-line only).

* `startLine` (Int): The start line in the file to which this thread refers (multi-line only).

* `subjectType` (PullRequestReviewThreadSubjectType!): The level at which the comments in the corresponding thread are targeted, can be a diff line or a file.

* `viewerCanReply` (Boolean!): Indicates whether the current viewer can reply to this thread.

* `viewerCanResolve` (Boolean!): Whether or not the viewer can resolve this thread.

* `viewerCanUnresolve` (Boolean!): Whether or not the viewer can unresolve this thread.

## PullRequestRevisionMarker

Represents the latest point in the pull request timeline for which the viewer has seen the pull request's commits.

### Fields for `PullRequestRevisionMarker`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `lastSeenCommit` (Commit!): The last commit the viewer has seen.
* `pullRequest` (PullRequest!): The pull request to which the marker belongs.

## PullRequestTemplate

A repository pull request template.

### Fields for `PullRequestTemplate`

* `body` (String): The body of the template.
* `filename` (String): The filename of the template.
* `repository` (Repository!): The repository the template belongs to.

## PullRequestThread

A threaded list of comments for a given pull request.

**Implements:** Node

### Fields for `PullRequestThread`

* `comments` (PullRequestReviewCommentConnection!): A list of pull request comments associated with the thread.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `skip` (Int): Skips the first n elements in the list.

* `diffSide` (DiffSide!): The side of the diff on which this thread was placed.

* `id` (ID!): The Node ID of the PullRequestThread object.

* `isCollapsed` (Boolean!): Whether or not the thread has been collapsed (resolved).

* `isOutdated` (Boolean!): Indicates whether this thread was outdated by newer changes.

* `isResolved` (Boolean!): Whether this thread has been resolved.

* `line` (Int): The line in the file to which this thread refers.

* `path` (String!): Identifies the file path of this thread.

* `pullRequest` (PullRequest!): Identifies the pull request associated with this thread.

* `repository` (Repository!): Identifies the repository associated with this thread.

* `resolvedBy` (User): The user who resolved this thread.

* `startDiffSide` (DiffSide): The side of the diff that the first line of the thread starts on (multi-line only).

* `startLine` (Int): The line of the first file diff in the thread.

* `subjectType` (PullRequestReviewThreadSubjectType!): The level at which the comments in the corresponding thread are targeted, can be a diff line or a file.

* `viewerCanReply` (Boolean!): Indicates whether the current viewer can reply to this thread.

* `viewerCanResolve` (Boolean!): Whether or not the viewer can resolve this thread.

* `viewerCanUnresolve` (Boolean!): Whether or not the viewer can unresolve this thread.

## PullRequestTimelineItemsConnection

The connection type for PullRequestTimelineItems.

### Fields for `PullRequestTimelineItemsConnection`

* `edges` (\[PullRequestTimelineItemsEdge]): A list of edges.
* `filteredCount` (Int!): Identifies the count of items after applying before and after filters.
* `nodes` (\[PullRequestTimelineItems]): A list of nodes.
* `pageCount` (Int!): Identifies the count of items after applying before/after filters and first/last/skip slicing.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.
* `updatedAt` (DateTime!): Identifies the date and time when the timeline was last updated.

## Push

A Git push.

**Implements:** Node

### Fields for `Push`

* `id` (ID!): The Node ID of the Push object.
* `nextSha` (GitObjectID): The SHA after the push.
* `permalink` (URI!): The permalink for this push.
* `previousSha` (GitObjectID): The SHA before the push.
* `pusher` (Actor!): The actor who pushed.
* `repository` (Repository!): The repository that was pushed to.

## PushAllowance

A team, user, or app who has the ability to push to a protected branch.

**Implements:** Node

### Fields for `PushAllowance`

* `actor` (PushAllowanceActor): The actor that can push.
* `branchProtectionRule` (BranchProtectionRule): Identifies the branch protection rule associated with the allowed user, team, or app.
* `id` (ID!): The Node ID of the PushAllowance object.

## RateLimit

Represents the client's rate limit.

### Fields for `RateLimit`

* `cost` (Int!): The point cost for the current query counting against the rate limit.
* `limit` (Int!): The maximum number of points the client is permitted to consume in a 60 minute window.
* `nodeCount` (Int!): The maximum number of nodes this query may return.
* `remaining` (Int!): The number of points remaining in the current rate limit window.
* `resetAt` (DateTime!): The time at which the current rate limit window resets in UTC epoch seconds.
* `used` (Int!): The number of points used in the current rate limit window.

## ReactingUserEdge

Represents a user that's made a reaction.

### Fields for `ReactingUserEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (User!):
* `reactedAt` (DateTime!): The moment when the user made the reaction.

## Reaction

An emoji reaction to a particular piece of content.

**Implements:** Node

### Fields for `Reaction`

* `content` (ReactionContent!): Identifies the emoji reaction.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the Reaction object.
* `reactable` (Reactable!): The reactable piece of content.
* `user` (User): Identifies the user who created this reaction.

## ReactionConnection

A list of reactions that have been left on the subject.

### Fields for `ReactionConnection`

* `edges` (\[ReactionEdge]): A list of edges.
* `nodes` (\[Reaction]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.
* `viewerHasReacted` (Boolean!): Whether or not the authenticated user has left a reaction on the subject.

## ReactionGroup

A group of emoji reactions to a particular piece of content.

### Fields for `ReactionGroup`

* `content` (ReactionContent!): Identifies the emoji reaction.
* `createdAt` (DateTime): Identifies when the reaction was created.
* `reactors` (ReactorConnection!): Reactors to the reaction subject with the emotion represented by this reaction group. *(Pagination: `after`, `before`, `first`, `last`)*
* `subject` (Reactable!): The subject that was reacted to.
* `users` (ReactingUserConnection!): Users who have reacted to the reaction subject with the emotion represented by this reaction group. **Deprecated:** Reactors can now be mannequins, bots, and organizations. Use the reactors field instead. Removal on 2021-10-01 UTC. *(Pagination: `after`, `before`, `first`, `last`)*
* `viewerHasReacted` (Boolean!): Whether or not the authenticated user has left a reaction on the subject.

## ReactorEdge

Represents an author of a reaction.

### Fields for `ReactorEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (Reactor!): The author of the reaction.
* `reactedAt` (DateTime!): The moment when the user made the reaction.

## ReadyForReviewEvent

Represents aready\_for\_reviewevent on a given pull request.

**Implements:** Node, UniformResourceLocatable

### Fields for `ReadyForReviewEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ReadyForReviewEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.
* `resourcePath` (URI!): The HTTP path for this ready for review event.
* `url` (URI!): The HTTP URL for this ready for review event.

## Ref

Represents a Git reference.

**Implements:** Node

### Fields for `Ref`

* `associatedPullRequests` (PullRequestConnection!): A list of pull requests with this ref as the head ref.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `baseRefName` (String): The base ref name to filter the pull requests by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `headRefName` (String): The head ref name to filter the pull requests by.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for pull requests returned from the connection.
  * `states` (\[PullRequestState!]): A list of states to filter the pull requests by.

* `branchProtectionRule` (BranchProtectionRule): Branch protection rules for this ref.

* `compare` (Comparison): Compares the current ref as a base ref to another head ref, if the comparison can be made.
  * `headRef` (String!): The head ref to compare against.

* `id` (ID!): The Node ID of the Ref object.

* `name` (String!): The ref name.

* `prefix` (String!): The ref's prefix, such as refs/heads/ or refs/tags/.

* `refUpdateRule` (RefUpdateRule): Branch protection rules that are viewable by non-admins.

* `repository` (Repository!): The repository the ref belongs to.

* `rules` (RepositoryRuleConnection): A list of rules from active Repository and Organization rulesets that apply to this ref.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryRuleOrder): Ordering options for repository rules.

* `target` (GitObject): The object the ref points to. Returns null when object does not exist.

## RefNameConditionTarget

Parameters to be used for the ref\_name condition.

### Fields for `RefNameConditionTarget`

* `exclude` (\[String!]!): Array of ref names or patterns to exclude. The condition will not pass if any of these patterns match.
* `include` (\[String!]!): Array of ref names or patterns to include. One of these patterns must match
  for the condition to pass. Also accepts \~DEFAULT\_BRANCH to include the
  default branch or \~ALL to include all branches.

## RefUpdateRule

Branch protection rules that are enforced on the viewer.

### Fields for `RefUpdateRule`

* `allowsDeletions` (Boolean!): Can this branch be deleted.
* `allowsForcePushes` (Boolean!): Are force pushes allowed on this branch.
* `blocksCreations` (Boolean!): Can matching branches be created.
* `pattern` (String!): Identifies the protection rule pattern.
* `requiredApprovingReviewCount` (Int): Number of approving reviews required to update matching branches.
* `requiredStatusCheckContexts` (\[String]): List of required status check contexts that must pass for commits to be accepted to matching branches.
* `requiresCodeOwnerReviews` (Boolean!): Are reviews from code owners required to update matching branches.
* `requiresConversationResolution` (Boolean!): Are conversations required to be resolved before merging.
* `requiresLinearHistory` (Boolean!): Are merge commits prohibited from being pushed to this branch.
* `requiresSignatures` (Boolean!): Are commits required to be signed.
* `viewerAllowedToDismissReviews` (Boolean!): Is the viewer allowed to dismiss reviews.
* `viewerCanPush` (Boolean!): Can the viewer push to the branch.

## ReferencedEvent

Represents areferencedevent on a given ReferencedSubject.

**Implements:** Node

### Fields for `ReferencedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `commit` (Commit): Identifies the commit associated with thereferencedevent.
* `commitRepository` (Repository!): Identifies the repository associated with thereferencedevent.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ReferencedEvent object.
* `isCrossRepository` (Boolean!): Reference originated in a different repository.
* `isDirectReference` (Boolean!): Checks if the commit message itself references the subject. Can be false in the case of a commit comment reference.
* `subject` (ReferencedSubject!): Object referenced by event.

## Release

A release contains the content for a release.

**Implements:** Node, Reactable, UniformResourceLocatable

### Fields for `Release`

* `author` (User): The author of the release.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `description` (String): The description of the release.

* `descriptionHTML` (HTML): The description of this release rendered to HTML.

* `id` (ID!): The Node ID of the Release object.

* `immutable` (Boolean!): Whether or not the release is immutable.

* `isDraft` (Boolean!): Whether or not the release is a draft.

* `isLatest` (Boolean!): Whether or not the release is the latest releast.

* `isPrerelease` (Boolean!): Whether or not the release is a prerelease.

* `mentions` (UserConnection): A list of users mentioned in the release description. *(Pagination: `after`, `before`, `first`, `last`)*

* `name` (String): The title of the release.

* `publishedAt` (DateTime): Identifies the date and time when the release was created.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `releaseAssets` (ReleaseAssetConnection!): List of releases assets which are dependent on this release.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `name` (String): A name to filter the assets by.

* `repository` (Repository!): The repository that the release belongs to.

* `resourcePath` (URI!): The HTTP path for this issue.

* `shortDescriptionHTML` (HTML): A description of the release, rendered to HTML without any links in it.
  * `limit` (Int): How many characters to return. Default: `200`.

* `tag` (Ref): The Git tag the release points to.

* `tagCommit` (Commit): The tag commit for this release.

* `tagName` (String!): The name of the release's Git tag.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this issue.

* `viewerCanReact` (Boolean!): Can user react to this subject.

## ReleaseAsset

A release asset contains the content for a release asset.

**Implements:** Node

### Fields for `ReleaseAsset`

* `contentType` (String!): The asset's content-type.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `digest` (String): The SHA256 digest of the asset.
* `downloadCount` (Int!): The number of times this asset was downloaded.
* `downloadUrl` (URI!): Identifies the URL where you can download the release asset via the browser.
* `id` (ID!): The Node ID of the ReleaseAsset object.
* `name` (String!): Identifies the title of the release asset.
* `release` (Release): Release that the asset is associated with.
* `size` (Int!): The size (in bytes) of the asset.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.
* `uploadedBy` (User!): The user that performed the upload.
* `url` (URI!): Identifies the URL of the release asset.

## RemovedFromMergeQueueEvent

Represents aremoved\_from\_merge\_queueevent on a given pull request.

**Implements:** Node

### Fields for `RemovedFromMergeQueueEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `beforeCommit` (Commit): Identifies the before commit SHA for theremoved\_from\_merge\_queueevent.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `enqueuer` (User): The user who removed this Pull Request from the merge queue.
* `id` (ID!): The Node ID of the RemovedFromMergeQueueEvent object.
* `mergeQueue` (MergeQueue): The merge queue where this pull request was removed from.
* `pullRequest` (PullRequest): PullRequest referenced by event.
* `reason` (String): The reason this pull request was removed from the queue.

## RemovedFromProjectEvent

Represents aremoved\_from\_projectevent on a given issue or pull request.

**Implements:** Node

### Fields for `RemovedFromProjectEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `id` (ID!): The Node ID of the RemovedFromProjectEvent object.
* `project` (Project): Project referenced by event. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
* `projectColumnName` (String!): Column name referenced by this project event. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

## RemovedFromProjectV2Event

Represents aremoved\_from\_project\_v2event on a given issue or pull request.

**Implements:** Node, ProjectV2Event

### Fields for `RemovedFromProjectV2Event`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the RemovedFromProjectV2Event object.
* `project` (ProjectV2): Project referenced by event.
* `wasAutomated` (Boolean!): Did this event result from workflow automation?.

## RenamedTitleEvent

Represents arenamedevent on a given issue or pull request.

**Implements:** Node

### Fields for `RenamedTitleEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `currentTitle` (String!): Identifies the current title of the issue or pull request.
* `id` (ID!): The Node ID of the RenamedTitleEvent object.
* `previousTitle` (String!): Identifies the previous title of the issue or pull request.
* `subject` (RenamedTitleSubject!): Subject that was renamed.

## ReopenedEvent

Represents areopenedevent on any Closable.

**Implements:** Node

### Fields for `ReopenedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `closable` (Closable!): Object that was reopened.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ReopenedEvent object.
* `stateReason` (IssueStateReason): The reason the issue state was changed to open.

## RepoAccessAuditEntry

Audit log entry for a repo.access event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoAccessAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoAccessAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `visibility` (RepoAccessAuditEntryVisibility): The visibility of the repository. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoAddMemberAuditEntry

Audit log entry for a repo.add\_member event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoAddMemberAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoAddMemberAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `visibility` (RepoAddMemberAuditEntryVisibility): The visibility of the repository. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoAddTopicAuditEntry

Audit log entry for a repo.add\_topic event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData, TopicAuditEntryData

### Fields for `RepoAddTopicAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoAddTopicAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `topic` (Topic): The name of the topic added to the repository.
* `topicName` (String): The name of the topic added to the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoArchivedAuditEntry

Audit log entry for a repo.archived event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoArchivedAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoArchivedAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `visibility` (RepoArchivedAuditEntryVisibility): The visibility of the repository. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoChangeMergeSettingAuditEntry

Audit log entry for a repo.change\_merge\_setting event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoChangeMergeSettingAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoChangeMergeSettingAuditEntry object.
* `isEnabled` (Boolean): Whether the change was to enable (true) or disable (false) the merge type. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `mergeType` (RepoChangeMergeSettingAuditEntryMergeType): The merge method affected by the change. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigDisableAnonymousGitAccessAuditEntry

Audit log entry for a repo.config.disable\_anonymous\_git\_access event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigDisableAnonymousGitAccessAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigDisableAnonymousGitAccessAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigDisableCollaboratorsOnlyAuditEntry

Audit log entry for a repo.config.disable\_collaborators\_only event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigDisableCollaboratorsOnlyAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigDisableCollaboratorsOnlyAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigDisableContributorsOnlyAuditEntry

Audit log entry for a repo.config.disable\_contributors\_only event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigDisableContributorsOnlyAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigDisableContributorsOnlyAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigDisableSockpuppetDisallowedAuditEntry

Audit log entry for a repo.config.disable\_sockpuppet\_disallowed event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigDisableSockpuppetDisallowedAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigDisableSockpuppetDisallowedAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigEnableAnonymousGitAccessAuditEntry

Audit log entry for a repo.config.enable\_anonymous\_git\_access event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigEnableAnonymousGitAccessAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigEnableAnonymousGitAccessAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigEnableCollaboratorsOnlyAuditEntry

Audit log entry for a repo.config.enable\_collaborators\_only event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigEnableCollaboratorsOnlyAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigEnableCollaboratorsOnlyAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigEnableContributorsOnlyAuditEntry

Audit log entry for a repo.config.enable\_contributors\_only event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigEnableContributorsOnlyAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigEnableContributorsOnlyAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigEnableSockpuppetDisallowedAuditEntry

Audit log entry for a repo.config.enable\_sockpuppet\_disallowed event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigEnableSockpuppetDisallowedAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigEnableSockpuppetDisallowedAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigLockAnonymousGitAccessAuditEntry

Audit log entry for a repo.config.lock\_anonymous\_git\_access event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigLockAnonymousGitAccessAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigLockAnonymousGitAccessAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoConfigUnlockAnonymousGitAccessAuditEntry

Audit log entry for a repo.config.unlock\_anonymous\_git\_access event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoConfigUnlockAnonymousGitAccessAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoConfigUnlockAnonymousGitAccessAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoCreateAuditEntry

Audit log entry for a repo.create event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoCreateAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `forkParentName` (String): The name of the parent repository for this forked repository. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `forkSourceName` (String): The name of the root repository for this network. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoCreateAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `visibility` (RepoCreateAuditEntryVisibility): The visibility of the repository. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoDestroyAuditEntry

Audit log entry for a repo.destroy event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoDestroyAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoDestroyAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `visibility` (RepoDestroyAuditEntryVisibility): The visibility of the repository. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoRemoveMemberAuditEntry

Audit log entry for a repo.remove\_member event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData

### Fields for `RepoRemoveMemberAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoRemoveMemberAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `visibility` (RepoRemoveMemberAuditEntryVisibility): The visibility of the repository. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepoRemoveTopicAuditEntry

Audit log entry for a repo.remove\_topic event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData, TopicAuditEntryData

### Fields for `RepoRemoveTopicAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the RepoRemoveTopicAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `topic` (Topic): The name of the topic added to the repository.
* `topicName` (String): The name of the topic added to the repository.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## Repository

A repository contains the content for a project.

**Implements:** Node, PackageOwner, ProjectOwner, ProjectV2Recent, RepositoryInfo, Starrable, Subscribable, UniformResourceLocatable

### Fields for `Repository`

* `allowUpdateBranch` (Boolean!): Whether or not a pull request head branch that is behind its base branch can
  always be updated even if it is not required to be up to date before merging.

* `archivedAt` (DateTime): Identifies the date and time when the repository was archived.

* `assignableUsers` (UserConnection!): A list of users that can be assigned to issues in this repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `query` (String): Filters users with query on user name and login.

* `autoMergeAllowed` (Boolean!): Whether or not Auto-merge can be enabled on pull requests in this repository.

* `branchProtectionRules` (BranchProtectionRuleConnection!): A list of branch protection rules for this repository. *(Pagination: `after`, `before`, `first`, `last`)*

* `codeOfConduct` (CodeOfConduct): Returns the code of conduct for this repository.

* `codeowners` (RepositoryCodeowners): Information extracted from the repository's CODEOWNERS file.
  * `refName` (String): The ref name used to return the associated CODEOWNERS file.

* `collaborators` (RepositoryCollaboratorConnection): A list of collaborators associated with the repository.
  * `affiliation` (CollaboratorAffiliation): Collaborators affiliation level with a repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `login` (String): The login of one specific collaborator.
  * `query` (String): Filters users with query on user name and login.

* `commitComments` (CommitCommentConnection!): A list of commit comments associated with the repository. *(Pagination: `after`, `before`, `first`, `last`)*

* `contactLinks` (\[RepositoryContactLink!]): Returns a list of contact links associated to the repository.

* `contributingGuidelines` (ContributingGuidelines): Returns the contributing guidelines for this repository.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `defaultBranchRef` (Ref): The Ref associated with the repository's default branch.

* `deleteBranchOnMerge` (Boolean!): Whether or not branches are automatically deleted when merged in this repository.

* `dependencyGraphManifests` (DependencyGraphManifestConnection): A list of dependency manifests contained in the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `dependenciesAfter` (String): Cursor to paginate dependencies.
  * `dependenciesFirst` (Int): Number of dependencies to fetch.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `withDependencies` (Boolean): Flag to scope to only manifests with dependencies.

* `deployKeys` (DeployKeyConnection!): A list of deploy keys that are on this repository. *(Pagination: `after`, `before`, `first`, `last`)*

* `deployments` (DeploymentConnection!): Deployments associated with the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `environments` (\[String!]): Environments to list deployments for.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (DeploymentOrder): Ordering options for deployments returned from the connection.

* `description` (String): The description of the repository.

* `descriptionHTML` (HTML!): The description of the repository rendered to HTML.

* `discussion` (Discussion): Returns a single discussion from the current repository by number.
  * `number` (Int!): The number for the discussion to be returned.

* `discussionCategories` (DiscussionCategoryConnection!): A list of discussion categories that are available in the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `filterByAssignable` (Boolean): Filter by categories that are assignable by the viewer.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.

* `discussionCategory` (DiscussionCategory): A discussion category by slug.
  * `slug` (String!): The slug of the discussion category to be returned.

* `discussions` (DiscussionConnection!): A list of discussions that have been opened in the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `answered` (Boolean): Only show answered or unanswered discussions.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `categoryId` (ID): Only include discussions that belong to the category with this ID.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (DiscussionOrder): Ordering options for discussions returned from the connection.
  * `states` (\[DiscussionState!]): A list of states to filter the discussions by.

* `diskUsage` (Int): The number of kilobytes this repository occupies on disk.

* `environment` (Environment): Returns a single active environment from the current repository by name.
  * `name` (String!): The name of the environment to be returned.

* `environments` (EnvironmentConnection!): A list of environments that are in this repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `names` (\[String!]): The names of the environments to be returned.
  * `orderBy` (Environments): Ordering options for the environments.
  * `pinnedEnvironmentFilter` (EnvironmentPinnedFilterField): Filter to control pinned environments return. Default: `ALL`.

* `forkCount` (Int!): Returns how many forks there are of this repository in the whole network.

* `forkingAllowed` (Boolean!): Whether this repository allows forks.

* `forks` (RepositoryConnection!): A list of direct forked repositories.
  * `affiliations` (\[RepositoryAffiliation]): Array of viewer's affiliation options for repositories returned from the
    connection. For example, OWNER will include only repositories that the
    current viewer owns.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `hasIssuesEnabled` (Boolean): If non-null, filters repositories according to whether they have issues enabled.
  * `isLocked` (Boolean): If non-null, filters repositories according to whether they have been locked.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder): Ordering options for repositories returned from the connection.
  * `ownerAffiliations` (\[RepositoryAffiliation]): Array of owner's affiliation options for repositories returned from the
    connection. For example, OWNER will include only repositories that the
    organization or user being viewed owns.
  * `privacy` (RepositoryPrivacy): If non-null, filters repositories according to privacy. Internal
    repositories are considered private; consider using the visibility argument
    if only internal repositories are needed. Cannot be combined with the
    visibility argument.
  * `visibility` (RepositoryVisibility): If non-null, filters repositories according to visibility. Cannot be combined with the privacy argument.

* `fundingLinks` (\[FundingLink!]!): The funding links for this repository.

* `hasDiscussionsEnabled` (Boolean!): Indicates if the repository has the Discussions feature enabled.

* `hasIssuesEnabled` (Boolean!): Indicates if the repository has issues feature enabled.

* `hasProjectsEnabled` (Boolean!): Indicates if the repository has the Projects feature enabled.

* `hasPullRequestsEnabled` (Boolean!): Indicates if the repository has the pull requests feature enabled.

* `hasSponsorshipsEnabled` (Boolean!): Indicates if the repository displays a Sponsor button for financial contributions.

* `hasVulnerabilityAlertsEnabled` (Boolean!): Whether vulnerability alerts are enabled for the repository.

* `hasWikiEnabled` (Boolean!): Indicates if the repository has wiki feature enabled.

* `homepageUrl` (URI): The repository's URL.

* `id` (ID!): The Node ID of the Repository object.

* `interactionAbility` (RepositoryInteractionAbility): The interaction ability settings for this repository.

* `isArchived` (Boolean!): Indicates if the repository is unmaintained.

* `isBlankIssuesEnabled` (Boolean!): Returns true if the viewer can create a blank issue in this repository.

* `isDisabled` (Boolean!): Returns whether or not this repository disabled.

* `isEmpty` (Boolean!): Returns whether or not this repository is empty.

* `isFork` (Boolean!): Identifies if the repository is a fork.

* `isInOrganization` (Boolean!): Indicates if a repository is either owned by an organization, or is a private fork of an organization repository.

* `isLocked` (Boolean!): Indicates if the repository has been locked or not.

* `isMirror` (Boolean!): Identifies if the repository is a mirror.

* `isPrivate` (Boolean!): Identifies if the repository is private or internal.

* `isSecurityPolicyEnabled` (Boolean): Returns true if this repository has a security policy.

* `isTemplate` (Boolean!): Identifies if the repository is a template that can be used to generate new repositories.

* `isUserConfigurationRepository` (Boolean!): Is this repository a user configuration repository?.

* `issue` (Issue): Returns a single issue from the current repository by number.
  * `number` (Int!): The number for the issue to be returned.

* `issueOrPullRequest` (IssueOrPullRequest): Returns a single issue-like object from the current repository by number.
  * `number` (Int!): The number for the issue to be returned.

* `issueTemplates` (\[IssueTemplate!]): Returns a list of issue templates associated to the repository.

* `issueType` (IssueType): Returns a single issue type by name.
  * `name` (String!): Issue type name.

* `issueTypes` (IssueTypeConnection): A list of the repository's issue types.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueTypeOrder): Ordering options for issue types returned from the connection.

* `issues` (IssueConnection!): A list of issues that have been opened in the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `filterBy` (IssueFilters): Filtering options for issues returned from the connection.
  * `first` (Int): Returns the first n elements from the list.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for issues returned from the connection.
  * `states` (\[IssueState!]): A list of states to filter the issues by.

* `label` (Label): Returns a single label by name.
  * `name` (String!): Label name.

* `labels` (LabelConnection): A list of labels associated with the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (LabelOrder): Ordering options for labels returned from the connection.
  * `query` (String): If provided, searches labels by name and description.

* `languages` (LanguageConnection): A list containing a breakdown of the language composition of the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (LanguageOrder): Order for connection.

* `latestRelease` (Release): Get the latest release for the repository if one exists.

* `licenseInfo` (License): The license associated with the repository.

* `lockReason` (RepositoryLockReason): The reason the repository has been locked.

* `mentionableUsers` (UserConnection!): A list of Users that can be mentioned in the context of the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `query` (String): Filters users with query on user name and login.

* `mergeCommitAllowed` (Boolean!): Whether or not PRs are merged with a merge commit on this repository.

* `mergeCommitMessage` (MergeCommitMessage!): How the default commit message will be generated when merging a pull request.

* `mergeCommitTitle` (MergeCommitTitle!): How the default commit title will be generated when merging a pull request.

* `mergeQueue` (MergeQueue): The merge queue for a specified branch, otherwise the default branch if not provided.
  * `branch` (String): The name of the branch to get the merge queue for. Case sensitive.

* `milestone` (Milestone): Returns a single milestone from the current repository by number.
  * `number` (Int!): The number for the milestone to be returned.

* `milestones` (MilestoneConnection): A list of milestones associated with the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (MilestoneOrder): Ordering options for milestones.
  * `query` (String): Filters milestones with a query on the title.
  * `states` (\[MilestoneState!]): Filter by the state of the milestones.

* `mirrorUrl` (URI): The repository's original mirror URL.

* `name` (String!): The name of the repository.

* `nameWithOwner` (String!): The repository's name with owner.

* `object` (GitObject): A Git object in the repository.
  * `expression` (String): A Git revision expression suitable for rev-parse.
  * `oid` (GitObjectID): The Git object ID.

* `openGraphImageUrl` (URI!): The image used to represent this repository in Open Graph data.

* `owner` (RepositoryOwner!): The User owner of the repository.

* `packages` (PackageConnection!): A list of packages under the owner.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `names` (\[String]): Find packages by their names.
  * `orderBy` (PackageOrder): Ordering of the returned packages.
  * `packageType` (PackageType): Filter registry package by type.
  * `repositoryId` (ID): Find packages in a repository by ID.

* `parent` (Repository): The repository parent, if this is a fork.

* `pinnedDiscussions` (PinnedDiscussionConnection!): A list of discussions that have been pinned in this repository. *(Pagination: `after`, `before`, `first`, `last`)*

* `pinnedEnvironments` (PinnedEnvironmentConnection): A list of pinned environments for this repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (PinnedEnvironmentOrder): Ordering options for the environments.

* `pinnedIssues` (PinnedIssueConnection): A list of pinned issues for this repository. *(Pagination: `after`, `before`, `first`, `last`)*

* `planFeatures` (RepositoryPlanFeatures!): Returns information about the availability of certain features and limits based on the repository's billing plan.

* `primaryLanguage` (Language): The primary language of the repository's code.

* `project` (Project): Find project by number. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `number` (Int!): The project number to find.

* `projectV2` (ProjectV2): Finds and returns the Project according to the provided Project number.
  * `number` (Int!): The Project number.

* `projects` (ProjectConnection!): A list of projects under the owner. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectOrder): Ordering options for projects returned from the connection.
  * `search` (String): Query to search projects by, currently only searching by name.
  * `states` (\[ProjectState!]): A list of states to filter the projects by.

* `projectsResourcePath` (URI!): The HTTP path listing the repository's projects.

* `projectsUrl` (URI!): The HTTP URL listing the repository's projects.

* `projectsV2` (ProjectV2Connection!): List of projects linked to this repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `minPermissionLevel` (ProjectV2PermissionLevel): Filter projects based on user role. Default: `READ`.
  * `orderBy` (ProjectV2Order): How to order the returned projects.
  * `query` (String): A project to search for linked to the repo.

* `pullRequest` (PullRequest): Returns a single pull request from the current repository by number.
  * `number` (Int!): The number for the pull request to be returned.

* `pullRequestCreationPolicy` (PullRequestCreationPolicy): The policy controlling who can create pull requests in this repository.

* `pullRequestTemplates` (\[PullRequestTemplate!]): Returns a list of pull request templates associated to the repository.

* `pullRequests` (PullRequestConnection!): A list of pull requests that have been opened in the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `baseRefName` (String): The base ref name to filter the pull requests by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `headRefName` (String): The head ref name to filter the pull requests by.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for pull requests returned from the connection.
  * `states` (\[PullRequestState!]): A list of states to filter the pull requests by.

* `pushedAt` (DateTime): Identifies the date and time when the repository was last pushed to.

* `rebaseMergeAllowed` (Boolean!): Whether or not rebase-merging is enabled on this repository.

* `recentProjects` (ProjectV2Connection!): Recent projects that this user has modified in the context of the owner. *(Pagination: `after`, `before`, `first`, `last`)*

* `ref` (Ref): Fetch a given ref from the repository.
  * `qualifiedName` (String!): The ref to retrieve. Fully qualified matches are checked in order
    (refs/heads/master) before falling back onto checks for short name matches (master).

* `refs` (RefConnection): Fetch a list of refs from the repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `direction` (OrderDirection): DEPRECATED: use orderBy. The ordering direction.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RefOrder): Ordering options for refs returned from the connection.
  * `query` (String): Filters refs with query on name.
  * `refPrefix` (String!): A ref name prefix like refs/heads/, refs/tags/, etc.

* `release` (Release): Lookup a single release given various criteria.
  * `tagName` (String!): The name of the Tag the Release was created from.

* `releases` (ReleaseConnection!): List of releases which are dependent on this repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReleaseOrder): Order for connection.

* `repositoryCustomPropertyValue` (RepositoryCustomPropertyValue): A custom property value for the repository.
  * `propertyName` (String!): The name of the custom property to retrieve the value for.

* `repositoryCustomPropertyValues` (RepositoryCustomPropertyValueConnection): A list of custom properties and their associated values for a repository. *(Pagination: `after`, `before`, `first`, `last`)*

* `repositoryTopics` (RepositoryTopicConnection!): A list of applied repository-topic associations for this repository. *(Pagination: `after`, `before`, `first`, `last`)*

* `resourcePath` (URI!): The HTTP path for this repository.

* `ruleset` (RepositoryRuleset): Returns a single ruleset from the current repository by ID.
  * `databaseId` (Int!): The ID of the ruleset to be returned.
  * `includeParents` (Boolean): Include rulesets configured at higher levels that apply to this repository. Default: `true`.

* `rulesets` (RepositoryRulesetConnection): A list of rulesets for this repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includeParents` (Boolean): Return rulesets configured at higher levels that apply to this repository. Default: `true`.
  * `last` (Int): Returns the last n elements from the list.
  * `targets` (\[RepositoryRulesetTarget!]): Return rulesets that apply to the specified target.

* `securityPolicyUrl` (URI): The security policy URL.

* `shortDescriptionHTML` (HTML!): A description of the repository, rendered to HTML without any links in it.
  * `limit` (Int): How many characters to return. Default: `200`.

* `squashMergeAllowed` (Boolean!): Whether or not squash-merging is enabled on this repository.

* `squashMergeCommitMessage` (SquashMergeCommitMessage!): How the default commit message will be generated when squash merging a pull request.

* `squashMergeCommitTitle` (SquashMergeCommitTitle!): How the default commit title will be generated when squash merging a pull request.

* `squashPrTitleUsedAsDefault` (Boolean!): Whether a squash merge commit can use the pull request title as default. **Deprecated:** squashPrTitleUsedAsDefault will be removed. Use Repository.squashMergeCommitTitle instead. Removal on 2023-04-01 UTC.

* `sshUrl` (GitSSHRemote!): The SSH URL to clone this repository.

* `stargazerCount` (Int!): Returns a count of how many stargazers there are on this object.

* `stargazers` (StargazerConnection!): A list of users who have starred this starrable.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (StarOrder): Order for connection.

* `submodules` (SubmoduleConnection!): Returns a list of all submodules in this repository parsed from the
  .gitmodules file as of the default branch's HEAD commit. *(Pagination: `after`, `before`, `first`, `last`)*

* `suggestedActors` (ActorConnection!): A list of suggested actors that can be attributed to content in this repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `capabilities` (\[RepositorySuggestedActorFilter!]!): A list of capabilities to filter actors by.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `loginNames` (String): A comma separated list of login names to filter actors by. Only the first 10 logins will be used.
  * `query` (String): Search actors with query on user name and login.

* `tempCloneToken` (String): Temporary authentication token for cloning this repository.

* `templateRepository` (Repository): The repository from which this repository was generated, if any.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this repository.

* `usesCustomOpenGraphImage` (Boolean!): Whether this repository has a custom image to use with Open Graph as opposed to being represented by the owner's avatar.

* `viewerCanAdminister` (Boolean!): Indicates whether the viewer has admin permissions on this repository.

* `viewerCanCreateProjects` (Boolean!): Can the current viewer create new projects on this owner. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `viewerCanSeeIssueFields` (Boolean!): Indicates whether the current user can see issue fields in this repository.

* `viewerCanSubscribe` (Boolean!): Check if the viewer is able to change their subscription status for the repository.

* `viewerCanUpdateTopics` (Boolean!): Indicates whether the viewer can update the topics of this repository.

* `viewerDefaultCommitEmail` (String): The last commit email for the viewer.

* `viewerDefaultMergeMethod` (PullRequestMergeMethod!): The last used merge method by the viewer or the default for the repository.

* `viewerHasStarred` (Boolean!): Returns a boolean indicating whether the viewing user has starred this starrable.

* `viewerPermission` (RepositoryPermission): The users permission level on the repository. Will return null if authenticated as an GitHub App.

* `viewerPossibleCommitEmails` (\[String!]): A list of emails this viewer can commit with.

* `viewerSubscription` (SubscriptionState): Identifies if the viewer is watching, not watching, or ignoring the subscribable entity.

* `visibility` (RepositoryVisibility!): Indicates the repository's visibility level.

* `vulnerabilityAlert` (RepositoryVulnerabilityAlert): Returns a single vulnerability alert from the current repository by number.
  * `number` (Int!): The number for the vulnerability alert to be returned.

* `vulnerabilityAlerts` (RepositoryVulnerabilityAlertConnection): A list of vulnerability alerts that are on this repository.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `classifications` (\[SecurityAdvisoryClassification!]): Filter by the classification of the alert's associated security advisory.
  * `dependencyScopes` (\[RepositoryVulnerabilityAlertDependencyScope!]): Filter by the scope of the alert's dependency.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `states` (\[RepositoryVulnerabilityAlertState!]): Filter by the state of the alert.

* `watchers` (UserConnection!): A list of users watching the repository. *(Pagination: `after`, `before`, `first`, `last`)*

* `webCommitSignoffRequired` (Boolean!): Whether contributors are required to sign off on web-based commits in this repository.

## RepositoryCodeowners

Information extracted from a repository's CODEOWNERS file.

### Fields for `RepositoryCodeowners`

* `errors` (\[RepositoryCodeownersError!]!): Any problems that were encountered while parsing the CODEOWNERS file.

## RepositoryCodeownersError

An error in a CODEOWNERS file.

### Fields for `RepositoryCodeownersError`

* `column` (Int!): The column number where the error occurs.
* `kind` (String!): A short string describing the type of error.
* `line` (Int!): The line number where the error occurs.
* `message` (String!): A complete description of the error, combining information from other fields.
* `path` (String!): The path to the file when the error occurs.
* `source` (String!): The content of the line where the error occurs.
* `suggestion` (String): A suggestion of how to fix the error.

## RepositoryCollaboratorEdge

Represents a user who is a collaborator of a repository.

### Fields for `RepositoryCollaboratorEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (User!):
* `permission` (RepositoryPermission!): The permission the user has on the repository.
* `permissionSources` (\[PermissionSource!]): A list of sources for the user's access to the repository.

## RepositoryConnection

A list of repositories owned by the subject.

### Fields for `RepositoryConnection`

* `edges` (\[RepositoryEdge]): A list of edges.
* `nodes` (\[Repository]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.
* `totalDiskUsage` (Int!): The total size in kilobytes of all repositories in the connection. Value will
  never be larger than max 32-bit signed integer.

## RepositoryContactLink

A repository contact link.

### Fields for `RepositoryContactLink`

* `about` (String!): The contact link purpose.
* `name` (String!): The contact link name.
* `url` (URI!): The contact link URL.

## RepositoryCustomProperty

A repository custom property.

**Implements:** Node

### Fields for `RepositoryCustomProperty`

* `allowedValues` (\[String!]): The allowed values for the custom property. Required if value\_type is single\_select or multi\_select.
* `defaultValue` (CustomPropertyValue): The default value of the custom property, if the property is required.
* `description` (String): The description of the custom property.
* `id` (ID!): The Node ID of the RepositoryCustomProperty object.
* `propertyName` (String!): The name of the custom property.
* `regex` (String): The regex pattern that the value of the custom property must match, if the value\_type is string.
* `requireExplicitValues` (Boolean): Whether this repository custom property requires explicit values.
* `required` (Boolean): Whether the custom property is required.
* `source` (CustomPropertySource!): The source type of the custom property.
* `valueType` (CustomPropertyValueType!): The value type of the custom property.
* `valuesEditableBy` (RepositoryCustomPropertyValuesEditableBy!): Who can edit the values of this repository custom property.

## RepositoryCustomPropertyValue

A value associated with a repository custom property.

### Fields for `RepositoryCustomPropertyValue`

* `propertyName` (String!): The name of the custom property.
* `value` (CustomPropertyValue!): The value of the custom property.

## RepositoryIdConditionTarget

Parameters to be used for the repository\_id condition.

### Fields for `RepositoryIdConditionTarget`

* `repositoryIds` (\[ID!]!): One of these repo IDs must match the repo.

## RepositoryInteractionAbility

Repository interaction limit that applies to this object.

### Fields for `RepositoryInteractionAbility`

* `expiresAt` (DateTime): The time the currently active limit expires.
* `limit` (RepositoryInteractionLimit!): The current limit that is enabled on this object.
* `origin` (RepositoryInteractionLimitOrigin!): The origin of the currently active interaction limit.

## RepositoryInvitation

An invitation for a user to be added to a repository.

**Implements:** Node

### Fields for `RepositoryInvitation`

* `email` (String): The email address that received the invitation.
* `id` (ID!): The Node ID of the RepositoryInvitation object.
* `invitee` (User): The user who received the invitation.
* `inviter` (User!): The user who created the invitation.
* `permalink` (URI!): The permalink for this repository invitation.
* `permission` (RepositoryPermission!): The permission granted on this repository by this invitation.
* `repository` (RepositoryInfo): The Repository the user is invited to.

## RepositoryMigration

A GitHub Enterprise Importer (GEI) repository migration.

**Implements:** Migration, Node

### Fields for `RepositoryMigration`

* `continueOnError` (Boolean!): The migration flag to continue on error.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (String): Identifies the primary key from the database.
* `failureReason` (String): The reason the migration failed.
* `id` (ID!): The Node ID of the RepositoryMigration object.
* `migrationLogUrl` (URI): The URL for the migration log (expires 1 day after migration completes).
* `migrationSource` (MigrationSource!): The migration source.
* `repositoryName` (String!): The target repository name.
* `sourceUrl` (URI!): The migration source URL, for example <https://github.com> or <https://monalisa.ghe.com>.
* `state` (MigrationState!): The migration state.
* `warningsCount` (Int!): The number of warnings encountered for this migration. To review the warnings,
  check the Migration Log.

## RepositoryNameConditionTarget

Parameters to be used for the repository\_name condition.

### Fields for `RepositoryNameConditionTarget`

* `exclude` (\[String!]!): Array of repository names or patterns to exclude. The condition will not pass if any of these patterns match.
* `include` (\[String!]!): Array of repository names or patterns to include. One of these patterns must
  match for the condition to pass. Also accepts \~ALL to include all repositories.
* `protected` (Boolean!): Target changes that match these patterns will be prevented except by those with bypass permissions.

## RepositoryPlanFeatures

Information about the availability of features and limits for a repository based on its billing plan.

### Fields for `RepositoryPlanFeatures`

* `codeowners` (Boolean!): Whether reviews can be automatically requested and enforced with a CODEOWNERS file.
* `draftPullRequests` (Boolean!): Whether pull requests can be created as or converted to draft.
* `maximumAssignees` (Int!): Maximum number of users that can be assigned to an issue or pull request.
* `maximumManualReviewRequests` (Int!): Maximum number of manually-requested reviews on a pull request.
* `teamReviewRequests` (Boolean!): Whether teams can be requested to review pull requests.

## RepositoryPropertyConditionTarget

Parameters to be used for the repository\_property condition.

### Fields for `RepositoryPropertyConditionTarget`

* `exclude` (\[PropertyTargetDefinition!]!): Array of repository properties that must not match.
* `include` (\[PropertyTargetDefinition!]!): Array of repository properties that must match.

## RepositoryRule

A repository rule.

**Implements:** Node

### Fields for `RepositoryRule`

* `id` (ID!): The Node ID of the RepositoryRule object.
* `parameters` (RuleParameters): The parameters for this rule.
* `repositoryRuleset` (RepositoryRuleset): The repository ruleset associated with this rule configuration.
* `type` (RepositoryRuleType!): The type of rule.

## RepositoryRuleConditions

Set of conditions that determine if a ruleset will evaluate.

### Fields for `RepositoryRuleConditions`

* `organizationProperty` (OrganizationPropertyConditionTarget): Configuration for the organization\_property condition.
* `refName` (RefNameConditionTarget): Configuration for the ref\_name condition.
* `repositoryId` (RepositoryIdConditionTarget): Configuration for the repository\_id condition.
* `repositoryName` (RepositoryNameConditionTarget): Configuration for the repository\_name condition.
* `repositoryProperty` (RepositoryPropertyConditionTarget): Configuration for the repository\_property condition.

## RepositoryRuleset

A repository ruleset.

**Implements:** Node

### Fields for `RepositoryRuleset`

* `bypassActors` (RepositoryRulesetBypassActorConnection): The actors that can bypass this ruleset. *(Pagination: `after`, `before`, `first`, `last`)*

* `conditions` (RepositoryRuleConditions!): The set of conditions that must evaluate to true for this ruleset to apply.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `enforcement` (RuleEnforcement!): The enforcement level of this ruleset.

* `id` (ID!): The Node ID of the RepositoryRuleset object.

* `name` (String!): Name of the ruleset.

* `rules` (RepositoryRuleConnection): List of rules.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `type` (RepositoryRuleType): The type of rule.

* `source` (RuleSource!): Source of ruleset.

* `target` (RepositoryRulesetTarget): Target of the ruleset.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## RepositoryRulesetBypassActor

A team or app that has the ability to bypass a rules defined on a ruleset.

**Implements:** Node

### Fields for `RepositoryRulesetBypassActor`

* `actor` (BypassActor): The actor that can bypass rules.
* `bypassMode` (RepositoryRulesetBypassActorBypassMode): The mode for the bypass actor.
* `deployKey` (Boolean!): This actor represents the ability for a deploy key to bypass.
* `enterpriseOwner` (Boolean!): This actor represents the ability for an enterprise owner to bypass.
* `id` (ID!): The Node ID of the RepositoryRulesetBypassActor object.
* `organizationAdmin` (Boolean!): This actor represents the ability for an organization owner to bypass.
* `repositoryRoleDatabaseId` (Int): If the actor is a repository role, the repository role's ID that can bypass.
* `repositoryRoleName` (String): If the actor is a repository role, the repository role's name that can bypass.
* `repositoryRuleset` (RepositoryRuleset): Identifies the ruleset associated with the allowed actor.

## RepositoryTopic

A repository-topic connects a repository to a topic.

**Implements:** Node, UniformResourceLocatable

### Fields for `RepositoryTopic`

* `id` (ID!): The Node ID of the RepositoryTopic object.
* `resourcePath` (URI!): The HTTP path for this repository-topic.
* `topic` (Topic!): The topic.
* `url` (URI!): The HTTP URL for this repository-topic.

## RepositoryVisibilityChangeDisableAuditEntry

Audit log entry for a repository\_visibility\_change.disable event.

**Implements:** AuditEntry, EnterpriseAuditEntryData, Node, OrganizationAuditEntryData

### Fields for `RepositoryVisibilityChangeDisableAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `enterpriseResourcePath` (URI): The HTTP path for this enterprise.
* `enterpriseSlug` (String): The slug of the enterprise.
* `enterpriseUrl` (URI): The HTTP URL for this enterprise.
* `id` (ID!): The Node ID of the RepositoryVisibilityChangeDisableAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepositoryVisibilityChangeEnableAuditEntry

Audit log entry for a repository\_visibility\_change.enable event.

**Implements:** AuditEntry, EnterpriseAuditEntryData, Node, OrganizationAuditEntryData

### Fields for `RepositoryVisibilityChangeEnableAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `enterpriseResourcePath` (URI): The HTTP path for this enterprise.
* `enterpriseSlug` (String): The slug of the enterprise.
* `enterpriseUrl` (URI): The HTTP URL for this enterprise.
* `id` (ID!): The Node ID of the RepositoryVisibilityChangeEnableAuditEntry object.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## RepositoryVulnerabilityAlert

A Dependabot alert for a repository with a dependency affected by a security vulnerability.

**Implements:** Node, RepositoryNode

### Fields for `RepositoryVulnerabilityAlert`

* `autoDismissedAt` (DateTime): When was the alert auto-dismissed?.
* `createdAt` (DateTime!): When was the alert created?.
* `dependabotUpdate` (DependabotUpdate): The associated Dependabot update.
* `dependencyRelationship` (RepositoryVulnerabilityAlertDependencyRelationship): The relationship of an alert's dependency.
* `dependencyScope` (RepositoryVulnerabilityAlertDependencyScope): The scope of an alert's dependency.
* `dismissComment` (String): Comment explaining the reason the alert was dismissed.
* `dismissReason` (String): The reason the alert was dismissed.
* `dismissedAt` (DateTime): When was the alert dismissed?.
* `dismisser` (User): The user who dismissed the alert.
* `fixedAt` (DateTime): When was the alert fixed?.
* `id` (ID!): The Node ID of the RepositoryVulnerabilityAlert object.
* `number` (Int!): Identifies the alert number.
* `repository` (Repository!): The associated repository.
* `securityAdvisory` (SecurityAdvisory): The associated security advisory.
* `securityVulnerability` (SecurityVulnerability): The associated security vulnerability.
* `state` (RepositoryVulnerabilityAlertState!): Identifies the state of the alert.
* `vulnerableManifestFilename` (String!): The vulnerable manifest filename.
* `vulnerableManifestPath` (String!): The vulnerable manifest path.
* `vulnerableRequirements` (String): The vulnerable requirements.

## RequiredDeploymentsParameters

Choose which environments must be successfully deployed to before refs can be pushed into a ref that matches this rule.

### Fields for `RequiredDeploymentsParameters`

* `requiredDeploymentEnvironments` (\[String!]!): The environments that must be successfully deployed to before branches can be merged.

## RequiredReviewerConfiguration

A reviewing team, and file patterns describing which files they must approve changes to.

### Fields for `RequiredReviewerConfiguration`

* `filePatterns` (\[String!]!): Array of file patterns. Pull requests which change matching files must be
  approved by the specified team. File patterns use fnmatch syntax.
* `minimumApprovals` (Int!): Minimum number of approvals required from the specified team. If set to zero,
  the team will be added to the pull request but approval is optional.
* `reviewerId` (ID!): Node ID of the team which must review changes to matching files.

## RequiredStatusCheckDescription

Represents a required status check for a protected branch, but not any specific run of that check.

### Fields for `RequiredStatusCheckDescription`

* `app` (App): The App that must provide this status in order for it to be accepted.
* `context` (String!): The name of this status.

## RequiredStatusChecksParameters

Choose which status checks must pass before the ref is updated. When enabled,
commits must first be pushed to another ref where the checks pass.

### Fields for `RequiredStatusChecksParameters`

* `doNotEnforceOnCreate` (Boolean!): Allow repositories and branches to be created if a check would otherwise prohibit it.
* `requiredStatusChecks` (\[StatusCheckConfiguration!]!): Status checks that are required.
* `strictRequiredStatusChecksPolicy` (Boolean!): Whether pull requests targeting a matching branch must be tested with the
  latest code. This setting will not take effect unless at least one status
  check is enabled.

## RestrictedContribution

Represents a private contribution a user made on GitHub.

**Implements:** Contribution

### Fields for `RestrictedContribution`

* `isRestricted` (Boolean!): Whether this contribution is associated with a record you do not have access to. For
  example, your own 'first issue' contribution may have been made on a repository you can no
  longer access.
* `occurredAt` (DateTime!): When this contribution was made.
* `resourcePath` (URI!): The HTTP path for this contribution.
* `url` (URI!): The HTTP URL for this contribution.
* `user` (User!): The user who made this contribution.

## ReviewDismissalAllowance

A user, team, or app who has the ability to dismiss a review on a protected branch.

**Implements:** Node

### Fields for `ReviewDismissalAllowance`

* `actor` (ReviewDismissalAllowanceActor): The actor that can dismiss.
* `branchProtectionRule` (BranchProtectionRule): Identifies the branch protection rule associated with the allowed user, team, or app.
* `id` (ID!): The Node ID of the ReviewDismissalAllowance object.

## ReviewDismissedEvent

Represents areview\_dismissedevent on a given issue or pull request.

**Implements:** Node, UniformResourceLocatable

### Fields for `ReviewDismissedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `dismissalMessage` (String): Identifies the optional message associated with thereview\_dismissedevent.
* `dismissalMessageHTML` (String): Identifies the optional message associated with the event, rendered to HTML.
* `id` (ID!): The Node ID of the ReviewDismissedEvent object.
* `previousReviewState` (PullRequestReviewState!): Identifies the previous state of the review with thereview\_dismissedevent.
* `pullRequest` (PullRequest!): PullRequest referenced by event.
* `pullRequestCommit` (PullRequestCommit): Identifies the commit which caused the review to become stale.
* `resourcePath` (URI!): The HTTP path for this review dismissed event.
* `review` (PullRequestReview): Identifies the review associated with thereview\_dismissedevent.
* `url` (URI!): The HTTP URL for this review dismissed event.

## ReviewRequest

A request for a user to review a pull request.

**Implements:** Node

### Fields for `ReviewRequest`

* `asCodeOwner` (Boolean!): Whether this request was created for a code owner.
* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the ReviewRequest object.
* `pullRequest` (PullRequest!): Identifies the pull request associated with this review request.
* `requestedReviewer` (RequestedReviewer): The reviewer that is requested.

## ReviewRequestRemovedEvent

Represents anreview\_request\_removedevent on a given pull request.

**Implements:** Node

### Fields for `ReviewRequestRemovedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ReviewRequestRemovedEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.
* `requestedReviewer` (RequestedReviewer): Identifies the reviewer whose review request was removed.

## ReviewRequestedEvent

Represents anreview\_requestedevent on a given pull request.

**Implements:** Node

### Fields for `ReviewRequestedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the ReviewRequestedEvent object.
* `pullRequest` (PullRequest!): PullRequest referenced by event.
* `requestedReviewer` (RequestedReviewer): Identifies the reviewer whose review was requested.

## ReviewStatusHovercardContext

A hovercard context with a message describing the current code review state of the pull
request.

**Implements:** HovercardContext

### Fields for `ReviewStatusHovercardContext`

* `message` (String!): A string describing this context.
* `octicon` (String!): An octicon to accompany this context.
* `reviewDecision` (PullRequestReviewDecision): The current status of the pull request with respect to code review.

## SavedReply

A Saved Reply is text a user can use to reply quickly.

**Implements:** Node

### Fields for `SavedReply`

* `body` (String!): The body of the saved reply.
* `bodyHTML` (HTML!): The saved reply body rendered to HTML.
* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the SavedReply object.
* `title` (String!): The title of the saved reply.
* `user` (Actor): The user that saved this reply.

## SearchResultItemConnection

A list of results that matched against a search query. Regardless of the number
of matches, a maximum of 1,000 results will be available across all types,
potentially split across many pages.

### Fields for `SearchResultItemConnection`

* `codeCount` (Int!): The total number of pieces of code that matched the search query. Regardless
  of the total number of matches, a maximum of 1,000 results will be available
  across all types.
* `discussionCount` (Int!): The total number of discussions that matched the search query. Regardless of
  the total number of matches, a maximum of 1,000 results will be available
  across all types.
* `edges` (\[SearchResultItemEdge]): A list of edges.
* `issueCount` (Int!): The total number of issues that matched the search query. Regardless of the
  total number of matches, a maximum of 1,000 results will be available across all types.
* `issueSearchType` (IssueSearchType): The type of search that was performed for issues (lexical, semantic, or hybrid).
* `lexicalFallbackReason` (\[LexicalFallbackReason!]): When a semantic or hybrid search falls back to lexical, the reasons why the fallback occurred.
* `nodes` (\[SearchResultItem]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `repositoryCount` (Int!): The total number of repositories that matched the search query. Regardless of
  the total number of matches, a maximum of 1,000 results will be available
  across all types.
* `userCount` (Int!): The total number of users that matched the search query. Regardless of the
  total number of matches, a maximum of 1,000 results will be available across all types.
* `wikiCount` (Int!): The total number of wiki pages that matched the search query. Regardless of
  the total number of matches, a maximum of 1,000 results will be available
  across all types.

## SearchResultItemEdge

An edge in a connection.

### Fields for `SearchResultItemEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (SearchResultItem): The item at the end of the edge.
* `textMatches` (\[TextMatch]): Text matches on the result found.

## SecurityAdvisory

A GitHub Security Advisory.

**Implements:** Node

### Fields for `SecurityAdvisory`

* `classification` (SecurityAdvisoryClassification!): The classification of the advisory.

* `cvss` (CVSS!): The CVSS associated with this advisory. **Deprecated:** cvss will be removed. New cvss\_severities field will now contain both cvss\_v3 and cvss\_v4 properties. Removal on 2025-10-01 UTC.

* `cvssSeverities` (CvssSeverities!): The CVSS associated with this advisory.

* `cwes` (CWEConnection!): CWEs associated with this Advisory. *(Pagination: `after`, `before`, `first`, `last`)*

* `databaseId` (Int): Identifies the primary key from the database.

* `description` (String!): This is a long plaintext description of the advisory.

* `epss` (EPSS): The Exploit Prediction Scoring System.

* `ghsaId` (String!): The GitHub Security Advisory ID.

* `id` (ID!): The Node ID of the SecurityAdvisory object.

* `identifiers` (\[SecurityAdvisoryIdentifier!]!): A list of identifiers for this advisory.

* `notificationsPermalink` (URI): The permalink for the advisory's dependabot alerts page.

* `origin` (String!): The organization that originated the advisory.

* `permalink` (URI): The permalink for the advisory.

* `publishedAt` (DateTime!): When the advisory was published.

* `references` (\[SecurityAdvisoryReference!]!): A list of references for this advisory.

* `severity` (SecurityAdvisorySeverity!): The severity of the advisory.

* `summary` (String!): A short plaintext summary of the advisory.

* `updatedAt` (DateTime!): When the advisory was last updated.

* `vulnerabilities` (SecurityVulnerabilityConnection!): Vulnerabilities associated with this Advisory.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `classifications` (\[SecurityAdvisoryClassification!]): A list of advisory classifications to filter vulnerabilities by.
  * `ecosystem` (SecurityAdvisoryEcosystem): An ecosystem to filter vulnerabilities by.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SecurityVulnerabilityOrder): Ordering options for the returned topics.
  * `package` (String): A package name to filter vulnerabilities by.
  * `severities` (\[SecurityAdvisorySeverity!]): A list of severities to filter vulnerabilities by.

* `withdrawnAt` (DateTime): When the advisory was withdrawn, if it has been withdrawn.

## SecurityAdvisoryIdentifier

A GitHub Security Advisory Identifier.

### Fields for `SecurityAdvisoryIdentifier`

* `type` (String!): The identifier type, e.g. GHSA, CVE.
* `value` (String!): The identifier.

## SecurityAdvisoryPackage

An individual package.

### Fields for `SecurityAdvisoryPackage`

* `ecosystem` (SecurityAdvisoryEcosystem!): The ecosystem the package belongs to, e.g. RUBYGEMS, NPM.
* `name` (String!): The package name.

## SecurityAdvisoryPackageVersion

An individual package version.

### Fields for `SecurityAdvisoryPackageVersion`

* `identifier` (String!): The package name or version.

## SecurityAdvisoryReference

A GitHub Security Advisory Reference.

### Fields for `SecurityAdvisoryReference`

* `url` (URI!): A publicly accessible reference.

## SecurityVulnerability

An individual vulnerability within an Advisory.

### Fields for `SecurityVulnerability`

* `advisory` (SecurityAdvisory!): The Advisory associated with this Vulnerability.
* `firstPatchedVersion` (SecurityAdvisoryPackageVersion): The first version containing a fix for the vulnerability.
* `package` (SecurityAdvisoryPackage!): A description of the vulnerable package.
* `severity` (SecurityAdvisorySeverity!): The severity of the vulnerability within this package.
* `updatedAt` (DateTime!): When the vulnerability was last updated.
* `vulnerableVersionRange` (String!): A string that describes the vulnerable package versions.
  This string follows a basic syntax with a few forms.

\= 0.2.0 denotes a single vulnerable version.
<= 1.0.8 denotes a version range up to and including the specified version
< 0.1.11 denotes a version range up to, but excluding, the specified version

> \= 4.3.0, < 4.3.5 denotes a version range with a known minimum and maximum version.
> \= 0.0.1 denotes a version range with a known minimum, but no known maximum.

## SmimeSignature

Represents an S/MIME signature on a Commit or Tag.

**Implements:** GitSignature

### Fields for `SmimeSignature`

* `email` (String!): Email used to sign this object.
* `isValid` (Boolean!): True if the signature is valid and verified by GitHub.
* `payload` (String!): Payload for GPG signing object. Raw ODB object without the signature header.
* `signature` (String!): ASCII-armored signature header from object.
* `signer` (User): GitHub user corresponding to the email signing this commit.
* `state` (GitSignatureState!): The state of this signature. VALID if signature is valid and verified by
  GitHub, otherwise represents reason why signature is considered invalid.
* `verifiedAt` (DateTime): The date the signature was verified, if valid.
* `wasSignedByGitHub` (Boolean!): True if the signature was made with GitHub's signing key.

## SocialAccount

Social media profile associated with a user.

### Fields for `SocialAccount`

* `displayName` (String!): Name of the social media account as it appears on the profile.
* `provider` (SocialAccountProvider!): Software or company that hosts the social media account.
* `url` (URI!): URL of the social media account.

## SponsorAndLifetimeValue

A GitHub account and the total amount in USD they've paid for sponsorships to a
particular maintainer. Does not include payments made via Patreon.

### Fields for `SponsorAndLifetimeValue`

* `amountInCents` (Int!): The amount in cents.
* `formattedAmount` (String!): The amount in USD, formatted as a string.
* `sponsor` (Sponsorable!): The sponsor's GitHub account.
* `sponsorable` (Sponsorable!): The maintainer's GitHub account.

## SponsorsActivity

An event related to sponsorship activity.

**Implements:** Node

### Fields for `SponsorsActivity`

* `action` (SponsorsActivityAction!): What action this activity indicates took place.
* `currentPrivacyLevel` (SponsorshipPrivacy): The sponsor's current privacy level.
* `id` (ID!): The Node ID of the SponsorsActivity object.
* `paymentSource` (SponsorshipPaymentSource): The platform that was used to pay for the sponsorship.
* `previousSponsorsTier` (SponsorsTier): The tier that the sponsorship used to use, for tier change events.
* `sponsor` (Sponsor): The user or organization who triggered this activity and was/is sponsoring the sponsorable.
* `sponsorable` (Sponsorable!): The user or organization that is being sponsored, the maintainer.
* `sponsorsTier` (SponsorsTier): The associated sponsorship tier.
* `timestamp` (DateTime): The timestamp of this event.
* `viaBulkSponsorship` (Boolean!): Was this sponsorship made alongside other sponsorships at the same time from the same sponsor?.

## SponsorsGoal

A goal associated with a GitHub Sponsors listing, representing a target the sponsored maintainer would like to attain.

### Fields for `SponsorsGoal`

* `description` (String): A description of the goal from the maintainer.
* `kind` (SponsorsGoalKind!): What the objective of this goal is.
* `percentComplete` (Int!): The percentage representing how complete this goal is, between 0-100.
* `targetValue` (Int!): What the goal amount is. Represents an amount in USD for monthly sponsorship
  amount goals. Represents a count of unique sponsors for total sponsors count goals.
* `title` (String!): A brief summary of the kind and target value of this goal.

## SponsorsListing

A GitHub Sponsors listing.

**Implements:** Node

### Fields for `SponsorsListing`

* `activeGoal` (SponsorsGoal): The current goal the maintainer is trying to reach with GitHub Sponsors, if any.

* `activeStripeConnectAccount` (StripeConnectAccount): The Stripe Connect account currently in use for payouts for this Sponsors
  listing, if any. Will only return a value when queried by the maintainer
  themselves, or by an admin of the sponsorable organization.

* `billingCountryOrRegion` (String): The name of the country or region with the maintainer's bank account or fiscal
  host. Will only return a value when queried by the maintainer themselves, or
  by an admin of the sponsorable organization.

* `contactEmailAddress` (String): The email address used by GitHub to contact the sponsorable about their GitHub
  Sponsors profile. Will only return a value when queried by the maintainer
  themselves, or by an admin of the sponsorable organization.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `dashboardResourcePath` (URI!): The HTTP path for the Sponsors dashboard for this Sponsors listing.

* `dashboardUrl` (URI!): The HTTP URL for the Sponsors dashboard for this Sponsors listing.

* `featuredItems` (\[SponsorsListingFeaturedItem!]!): The records featured on the GitHub Sponsors profile.
  * `featureableTypes` (\[SponsorsListingFeaturedItemFeatureableType!]): The types of featured items to return.

* `fiscalHost` (Organization): The fiscal host used for payments, if any. Will only return a value when
  queried by the maintainer themselves, or by an admin of the sponsorable organization.

* `fullDescription` (String!): The full description of the listing.

* `fullDescriptionHTML` (HTML!): The full description of the listing rendered to HTML.

* `id` (ID!): The Node ID of the SponsorsListing object.

* `isPublic` (Boolean!): Whether this listing is publicly visible.

* `name` (String!): The listing's full name.

* `nextPayoutDate` (Date): A future date on which this listing is eligible to receive a payout.

* `residenceCountryOrRegion` (String): The name of the country or region where the maintainer resides. Will only
  return a value when queried by the maintainer themselves, or by an admin of
  the sponsorable organization.

* `resourcePath` (URI!): The HTTP path for this Sponsors listing.

* `shortDescription` (String!): The short description of the listing.

* `slug` (String!): The short name of the listing.

* `sponsorable` (Sponsorable!): The entity this listing represents who can be sponsored on GitHub Sponsors.

* `tiers` (SponsorsTierConnection): The tiers for this GitHub Sponsors profile.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includeUnpublished` (Boolean): Whether to include tiers that aren't published. Only admins of the Sponsors
    listing can see draft tiers. Only admins of the Sponsors listing and viewers
    who are currently sponsoring on a retired tier can see those retired tiers.
    Defaults to including only published tiers, which are visible to anyone who
    can see the GitHub Sponsors profile.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorsTierOrder): Ordering options for Sponsors tiers returned from the connection.

* `url` (URI!): The HTTP URL for this Sponsors listing.

## SponsorsListingFeaturedItem

A record that is promoted on a GitHub Sponsors profile.

**Implements:** Node

### Fields for `SponsorsListingFeaturedItem`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `description` (String): Will either be a description from the sponsorable maintainer about why they
  featured this item, or the item's description itself, such as a user's bio
  from their GitHub profile page.
* `featureable` (SponsorsListingFeatureableItem!): The record that is featured on the GitHub Sponsors profile.
* `id` (ID!): The Node ID of the SponsorsListingFeaturedItem object.
* `position` (Int!): The position of this featured item on the GitHub Sponsors profile with a lower
  position indicating higher precedence. Starts at 1.
* `sponsorsListing` (SponsorsListing!): The GitHub Sponsors profile that features this record.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## SponsorsTier

A GitHub Sponsors tier associated with a GitHub Sponsors listing.

**Implements:** Node

### Fields for `SponsorsTier`

* `adminInfo` (SponsorsTierAdminInfo): SponsorsTier information only visible to users that can administer the associated Sponsors listing.
* `closestLesserValueTier` (SponsorsTier): Get a different tier for this tier's maintainer that is at the same frequency
  as this tier but with an equal or lesser cost. Returns the published tier with
  the monthly price closest to this tier's without going over.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `description` (String!): The description of the tier.
* `descriptionHTML` (HTML!): The tier description rendered to HTML.
* `id` (ID!): The Node ID of the SponsorsTier object.
* `isCustomAmount` (Boolean!): Whether this tier was chosen at checkout time by the sponsor rather than
  defined ahead of time by the maintainer who manages the Sponsors listing.
* `isOneTime` (Boolean!): Whether this tier is only for use with one-time sponsorships.
* `monthlyPriceInCents` (Int!): How much this tier costs per month in cents.
* `monthlyPriceInDollars` (Int!): How much this tier costs per month in USD.
* `name` (String!): The name of the tier.
* `sponsorsListing` (SponsorsListing!): The sponsors listing that this tier belongs to.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## SponsorsTierAdminInfo

SponsorsTier information only visible to users that can administer the associated Sponsors listing.

### Fields for `SponsorsTierAdminInfo`

* `isDraft` (Boolean!): Indicates whether this tier is still a work in progress by the sponsorable and
  not yet published to the associated GitHub Sponsors profile. Draft tiers
  cannot be used for new sponsorships and will not be in use on existing
  sponsorships. Draft tiers cannot be seen by anyone but the admins of the
  GitHub Sponsors profile.
* `isPublished` (Boolean!): Indicates whether this tier is published to the associated GitHub Sponsors
  profile. Published tiers are visible to anyone who can see the GitHub Sponsors
  profile, and are available for use in sponsorships if the GitHub Sponsors
  profile is publicly visible.
* `isRetired` (Boolean!): Indicates whether this tier has been retired from the associated GitHub
  Sponsors profile. Retired tiers are no longer shown on the GitHub Sponsors
  profile and cannot be chosen for new sponsorships. Existing sponsorships may
  still use retired tiers if the sponsor selected the tier before it was retired.
* `sponsorships` (SponsorshipConnection!): The sponsorships using this tier.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includePrivate` (Boolean): Whether or not to return private sponsorships using this tier. Defaults to
    only returning public sponsorships on this tier.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorshipOrder): Ordering options for sponsorships returned from this connection. If left
    blank, the sponsorships will be ordered based on relevancy to the viewer.

## Sponsorship

A sponsorship relationship between a sponsor and a maintainer.

**Implements:** Node

### Fields for `Sponsorship`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the Sponsorship object.
* `isActive` (Boolean!): Whether the sponsorship is active. False implies the sponsor is a past sponsor
  of the maintainer, while true implies they are a current sponsor.
* `isOneTimePayment` (Boolean!): Whether this sponsorship represents a one-time payment versus a recurring sponsorship.
* `isSponsorOptedIntoEmail` (Boolean): Whether the sponsor has chosen to receive sponsorship update emails sent from
  the sponsorable. Only returns a non-null value when the viewer has permission to know this.
* `maintainer` (User!): The entity that is being sponsored. **Deprecated:** Sponsorship.maintainer will be removed. Use Sponsorship.sponsorable instead. Removal on 2020-04-01 UTC.
* `paymentSource` (SponsorshipPaymentSource): The platform that was most recently used to pay for the sponsorship.
* `privacyLevel` (SponsorshipPrivacy!): The privacy level for this sponsorship.
* `sponsor` (User): The user that is sponsoring. Returns null if the sponsorship is private or if sponsor is not a user. **Deprecated:** Sponsorship.sponsor will be removed. Use Sponsorship.sponsorEntity instead. Removal on 2020-10-01 UTC.
* `sponsorEntity` (Sponsor): The user or organization that is sponsoring, if you have permission to view them.
* `sponsorable` (Sponsorable!): The entity that is being sponsored.
* `tier` (SponsorsTier): The associated sponsorship tier.
* `tierSelectedAt` (DateTime): Identifies the date and time when the current tier was chosen for this sponsorship.

## SponsorshipConnection

A list of sponsorships either from the subject or received by the subject.

### Fields for `SponsorshipConnection`

* `edges` (\[SponsorshipEdge]): A list of edges.
* `nodes` (\[Sponsorship]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.
* `totalRecurringMonthlyPriceInCents` (Int!): The total amount in cents of all recurring sponsorships in the connection
  whose amount you can view. Does not include one-time sponsorships.
* `totalRecurringMonthlyPriceInDollars` (Int!): The total amount in USD of all recurring sponsorships in the connection whose
  amount you can view. Does not include one-time sponsorships.

## SponsorshipNewsletter

An update sent to sponsors of a user or organization on GitHub Sponsors.

**Implements:** Node

### Fields for `SponsorshipNewsletter`

* `author` (User): The author of the newsletter.
* `body` (String!): The contents of the newsletter, the message the sponsorable wanted to give.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the SponsorshipNewsletter object.
* `isPublished` (Boolean!): Indicates if the newsletter has been made available to sponsors.
* `sponsorable` (Sponsorable!): The user or organization this newsletter is from.
* `subject` (String!): The subject of the newsletter, what it's about.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## SshSignature

Represents an SSH signature on a Commit or Tag.

**Implements:** GitSignature

### Fields for `SshSignature`

* `email` (String!): Email used to sign this object.
* `isValid` (Boolean!): True if the signature is valid and verified by GitHub.
* `keyFingerprint` (String): Hex-encoded fingerprint of the key that signed this object.
* `payload` (String!): Payload for GPG signing object. Raw ODB object without the signature header.
* `signature` (String!): ASCII-armored signature header from object.
* `signer` (User): GitHub user corresponding to the email signing this commit.
* `state` (GitSignatureState!): The state of this signature. VALID if signature is valid and verified by
  GitHub, otherwise represents reason why signature is considered invalid.
* `verifiedAt` (DateTime): The date the signature was verified, if valid.
* `wasSignedByGitHub` (Boolean!): True if the signature was made with GitHub's signing key.

## StargazerEdge

Represents a user that's starred a repository.

### Fields for `StargazerEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (User!):
* `starredAt` (DateTime!): Identifies when the item was starred.

## StarredRepositoryConnection

The connection type for Repository.

### Fields for `StarredRepositoryConnection`

* `edges` (\[StarredRepositoryEdge]): A list of edges.
* `isOverLimit` (Boolean!): Is the list of stars for this user truncated? This is true for users that have many stars.
* `nodes` (\[Repository]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `totalCount` (Int!): Identifies the total count of items in the connection.

## StarredRepositoryEdge

Represents a starred repository.

### Fields for `StarredRepositoryEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (Repository!):
* `starredAt` (DateTime!): Identifies when the item was starred.

## Status

Represents a commit status.

**Implements:** Node

### Fields for `Status`

* `combinedContexts` (StatusCheckRollupContextConnection!): A list of status contexts and check runs for this commit. *(Pagination: `after`, `before`, `first`, `last`)*

* `commit` (Commit): The commit this status is attached to.

* `context` (StatusContext): Looks up an individual status context by context name.
  * `name` (String!): The context name.

* `contexts` (\[StatusContext!]!): The individual status contexts for this commit.

* `id` (ID!): The Node ID of the Status object.

* `state` (StatusState!): The combined commit status.

## StatusCheckConfiguration

Required status check.

### Fields for `StatusCheckConfiguration`

* `context` (String!): The status check context name that must be present on the commit.
* `integrationId` (Int): The optional integration ID that this status check must originate from.

## StatusCheckRollup

Represents the rollup for both the check runs and status for a commit.

**Implements:** Node

### Fields for `StatusCheckRollup`

* `commit` (Commit): The commit the status and check runs are attached to.
* `contexts` (StatusCheckRollupContextConnection!): A list of status contexts and check runs for this commit. *(Pagination: `after`, `before`, `first`, `last`)*
* `id` (ID!): The Node ID of the StatusCheckRollup object.
* `state` (StatusState!): The combined status for the commit.

## StatusCheckRollupContextConnection

The connection type for StatusCheckRollupContext.

### Fields for `StatusCheckRollupContextConnection`

* `checkRunCount` (Int!): The number of check runs in this rollup.
* `checkRunCountsByState` (\[CheckRunStateCount!]): Counts of check runs by state.
* `edges` (\[StatusCheckRollupContextEdge]): A list of edges.
* `nodes` (\[StatusCheckRollupContext]): A list of nodes.
* `pageInfo` (PageInfo!): Information to aid in pagination.
* `statusContextCount` (Int!): The number of status contexts in this rollup.
* `statusContextCountsByState` (\[StatusContextStateCount!]): Counts of status contexts by state.
* `totalCount` (Int!): Identifies the total count of items in the connection.

## StatusContext

Represents an individual commit status context.

**Implements:** Node, RequirableByPullRequest

### Fields for `StatusContext`

* `avatarUrl` (URI): The avatar of the OAuth application or the user that created the status.
  * `size` (Int): The size of the resulting square image. Default: `40`.

* `commit` (Commit): This commit this status context is attached to.

* `context` (String!): The name of this status context.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `creator` (Actor): The actor who created this status context.

* `description` (String): The description for this status context.

* `id` (ID!): The Node ID of the StatusContext object.

* `isRequired` (Boolean!): Whether this is required to pass before merging for a specific pull request.
  * `pullRequestId` (ID): The id of the pull request this is required for.
  * `pullRequestNumber` (Int): The number of the pull request this is required for.

* `state` (StatusState!): The state of this status context.

* `targetUrl` (URI): The URL for this status context.

## StatusContextStateCount

Represents a count of the state of a status context.

### Fields for `StatusContextStateCount`

* `count` (Int!): The number of statuses with this state.
* `state` (StatusState!): The state of a status context.

## StripeConnectAccount

A Stripe Connect account for receiving sponsorship funds from GitHub Sponsors.

### Fields for `StripeConnectAccount`

* `accountId` (String!): The account number used to identify this Stripe Connect account.
* `billingCountryOrRegion` (String): The name of the country or region of an external account, such as a bank
  account, tied to the Stripe Connect account. Will only return a value when
  queried by the maintainer of the associated GitHub Sponsors profile
  themselves, or by an admin of the sponsorable organization.
* `countryOrRegion` (String): The name of the country or region of the Stripe Connect account. Will only
  return a value when queried by the maintainer of the associated GitHub
  Sponsors profile themselves, or by an admin of the sponsorable organization.
* `isActive` (Boolean!): Whether this Stripe Connect account is currently in use for the associated GitHub Sponsors profile.
* `sponsorsListing` (SponsorsListing!): The GitHub Sponsors profile associated with this Stripe Connect account.
* `stripeDashboardUrl` (URI!): The URL to access this Stripe Connect account on Stripe's website.

## SubIssueAddedEvent

Represents asub\_issue\_addedevent on a given issue.

**Implements:** Node

### Fields for `SubIssueAddedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the SubIssueAddedEvent object.
* `subIssue` (Issue): The sub-issue added.

## SubIssueRemovedEvent

Represents asub\_issue\_removedevent on a given issue.

**Implements:** Node

### Fields for `SubIssueRemovedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the SubIssueRemovedEvent object.
* `subIssue` (Issue): The sub-issue removed.

## SubIssuesSummary

Summary of the state of an issue's sub-issues.

### Fields for `SubIssuesSummary`

* `completed` (Int!): Count of completed sub-issues.
* `percentCompleted` (Int!): Percent of sub-issues which are completed.
* `total` (Int!): Count of total number of sub-issues.

## Submodule

A pointer to a repository at a specific revision embedded inside another repository.

### Fields for `Submodule`

* `branch` (String): The branch of the upstream submodule for tracking updates.
* `gitUrl` (URI!): The git URL of the submodule repository.
* `name` (String!): The name of the submodule in .gitmodules.
* `nameRaw` (Base64String!): The name of the submodule in .gitmodules (Base64-encoded).
* `path` (String!): The path in the superproject that this submodule is located in.
* `pathRaw` (Base64String!): The path in the superproject that this submodule is located in (Base64-encoded).
* `subprojectCommitOid` (GitObjectID): The commit revision of the subproject repository being tracked by the submodule.

## SubscribedEvent

Represents asubscribedevent on a given Subscribable.

**Implements:** Node

### Fields for `SubscribedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the SubscribedEvent object.
* `subscribable` (Subscribable!): Object referenced by event.

## SuggestedReviewer

A suggestion to review a pull request based on a user's commit history and review comments.

### Fields for `SuggestedReviewer`

* `isAuthor` (Boolean!): Is this suggestion based on past commits?.
* `isCommenter` (Boolean!): Is this suggestion based on past review comments?.
* `reviewer` (User!): Identifies the user suggested to review the pull request.

## SuggestedReviewerActor

A suggestion to review a pull request based on an actor's commit history, review comments, and integrations.

### Fields for `SuggestedReviewerActor`

* `isAuthor` (Boolean!): Is this suggestion based on past commits?.
* `isCommenter` (Boolean!): Is this suggestion based on past review comments?.
* `reviewer` (Actor!): Identifies the actor suggested to review the pull request.

## Tag

Represents a Git tag.

**Implements:** GitObject, Node

### Fields for `Tag`

* `abbreviatedOid` (String!): An abbreviated version of the Git object ID.
* `commitResourcePath` (URI!): The HTTP path for this Git object.
* `commitUrl` (URI!): The HTTP URL for this Git object.
* `id` (ID!): The Node ID of the Tag object.
* `message` (String): The Git tag message.
* `name` (String!): The Git tag name.
* `oid` (GitObjectID!): The Git object ID.
* `repository` (Repository!): The Repository the Git object belongs to.
* `tagger` (GitActor): Details about the tag author.
* `target` (GitObject!): The Git object the tag points to.

## TagNamePatternParameters

Parameters to be used for the tag\_name\_pattern rule.

### Fields for `TagNamePatternParameters`

* `name` (String): How this rule appears when configuring it.
* `negate` (Boolean!): If true, the rule will fail if the pattern matches.
* `operator` (String!): The operator to use for matching.
* `pattern` (String!): The pattern to match with.

## Team

A team of users in an organization.

**Implements:** MemberStatusable, Node, Subscribable

### Fields for `Team`

* `ancestors` (TeamConnection!): A list of teams that are ancestors of this team. *(Pagination: `after`, `before`, `first`, `last`)*

* `avatarUrl` (URI): A URL pointing to the team's avatar.
  * `size` (Int): The size in pixels of the resulting square image. Default: `400`.

* `childTeams` (TeamConnection!): List of child teams belonging to this team.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `immediateOnly` (Boolean): Whether to list immediate child teams or all descendant child teams. Default: `true`.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (TeamOrder): Order for connection.
  * `userLogins` (\[String!]): User logins to filter by.

* `combinedSlug` (String!): The slug corresponding to the organization and team.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `description` (String): The description of the team.

* `editTeamResourcePath` (URI!): The HTTP path for editing this team.

* `editTeamUrl` (URI!): The HTTP URL for editing this team.

* `id` (ID!): The Node ID of the Team object.

* `invitations` (OrganizationInvitationConnection): A list of pending invitations for users to this team. *(Pagination: `after`, `before`, `first`, `last`)*

* `memberStatuses` (UserStatusConnection!): Get the status messages members of this entity have set that are either public or visible only to the organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (UserStatusOrder): Ordering options for user statuses returned from the connection.

* `members` (TeamMemberConnection!): A list of users who are members of this team.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `membership` (TeamMembershipType): Filter by membership type. Default: `ALL`.
  * `orderBy` (TeamMemberOrder): Order for the connection.
  * `query` (String): The search string to look for.
  * `role` (TeamMemberRole): Filter by team member role.

* `membersResourcePath` (URI!): The HTTP path for the team' members.

* `membersUrl` (URI!): The HTTP URL for the team' members.

* `name` (String!): The name of the team.

* `newTeamResourcePath` (URI!): The HTTP path creating a new team.

* `newTeamUrl` (URI!): The HTTP URL creating a new team.

* `notificationSetting` (TeamNotificationSetting!): The notification setting that the team has set.

* `organization` (Organization!): The organization that owns this team.

* `parentTeam` (Team): The parent team of the team.

* `privacy` (TeamPrivacy!): The level of privacy the team has.

* `projectV2` (ProjectV2): Finds and returns the project according to the provided project number.
  * `number` (Int!): The Project number.

* `projectsV2` (ProjectV2Connection!): List of projects this team has collaborator access to.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `filterBy` (ProjectV2Filters): Filtering options for projects returned from this connection.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `minPermissionLevel` (ProjectV2PermissionLevel): Filter projects based on user role. Default: `READ`.
  * `orderBy` (ProjectV2Order): How to order the returned projects.
  * `query` (String): The query to search projects by. Default: \`\`.

* `repositories` (TeamRepositoryConnection!): A list of repositories this team has access to.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (TeamRepositoryOrder): Order for the connection.
  * `query` (String): The search string to look for. Repositories will be returned where the name contains your search string.

* `repositoriesResourcePath` (URI!): The HTTP path for this team's repositories.

* `repositoriesUrl` (URI!): The HTTP URL for this team's repositories.

* `resourcePath` (URI!): The HTTP path for this team.

* `reviewRequestDelegationAlgorithm` (TeamReviewAssignmentAlgorithm): What algorithm is used for review assignment for this team.

* `reviewRequestDelegationEnabled` (Boolean!): True if review assignment is enabled for this team.

* `reviewRequestDelegationMemberCount` (Int): How many team members are required for review assignment for this team.

* `reviewRequestDelegationNotifyTeam` (Boolean!): When assigning team members via delegation, whether the entire team should be notified as well.

* `slug` (String!): The slug corresponding to the team.

* `teamsResourcePath` (URI!): The HTTP path for this team's teams.

* `teamsUrl` (URI!): The HTTP URL for this team's teams.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this team.

* `viewerCanAdminister` (Boolean!): Team is adminable by the viewer.

* `viewerCanSubscribe` (Boolean!): Check if the viewer is able to change their subscription status for the subscribable entity. **Deprecated:** Team.viewerCanSubscribe will be removed. Team notifications subscriptions are being deprecated. Removal on 2026-07-01 UTC.

* `viewerSubscription` (SubscriptionState): Identifies if the viewer is watching, not watching, or ignoring the subscribable entity. **Deprecated:** Team.viewerSubscription will be removed. Team notifications subscriptions are being deprecated. Removal on 2026-07-01 UTC.

## TeamAddMemberAuditEntry

Audit log entry for a team.add\_member event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, TeamAuditEntryData

### Fields for `TeamAddMemberAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the TeamAddMemberAuditEntry object.
* `isLdapMapped` (Boolean): Whether the team was mapped to an LDAP Group. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `team` (Team): The team associated with the action.
* `teamName` (String): The name of the team.
* `teamResourcePath` (URI): The HTTP path for this team.
* `teamUrl` (URI): The HTTP URL for this team.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## TeamAddRepositoryAuditEntry

Audit log entry for a team.add\_repository event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData, TeamAuditEntryData

### Fields for `TeamAddRepositoryAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the TeamAddRepositoryAuditEntry object.
* `isLdapMapped` (Boolean): Whether the team was mapped to an LDAP Group. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `team` (Team): The team associated with the action.
* `teamName` (String): The name of the team.
* `teamResourcePath` (URI): The HTTP path for this team.
* `teamUrl` (URI): The HTTP URL for this team.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## TeamChangeParentTeamAuditEntry

Audit log entry for a team.change\_parent\_team event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, TeamAuditEntryData

### Fields for `TeamChangeParentTeamAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the TeamChangeParentTeamAuditEntry object.
* `isLdapMapped` (Boolean): Whether the team was mapped to an LDAP Group. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `parentTeam` (Team): The new parent team. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `parentTeamName` (String): The name of the new parent team. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `parentTeamNameWas` (String): The name of the former parent team. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `parentTeamResourcePath` (URI): The HTTP path for the parent team. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `parentTeamUrl` (URI): The HTTP URL for the parent team. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `parentTeamWas` (Team): The former parent team. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `parentTeamWasResourcePath` (URI): The HTTP path for the previous parent team. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `parentTeamWasUrl` (URI): The HTTP URL for the previous parent team. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `team` (Team): The team associated with the action.
* `teamName` (String): The name of the team.
* `teamResourcePath` (URI): The HTTP path for this team.
* `teamUrl` (URI): The HTTP URL for this team.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## TeamMemberEdge

Represents a user who is a member of a team.

### Fields for `TeamMemberEdge`

* `cursor` (String!): A cursor for use in pagination.
* `memberAccessResourcePath` (URI!): The HTTP path to the organization's member access page.
* `memberAccessUrl` (URI!): The HTTP URL to the organization's member access page.
* `node` (User!):
* `role` (TeamMemberRole!): The role the member has on the team.

## TeamRemoveMemberAuditEntry

Audit log entry for a team.remove\_member event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, TeamAuditEntryData

### Fields for `TeamRemoveMemberAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the TeamRemoveMemberAuditEntry object.
* `isLdapMapped` (Boolean): Whether the team was mapped to an LDAP Group. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `team` (Team): The team associated with the action.
* `teamName` (String): The name of the team.
* `teamResourcePath` (URI): The HTTP path for this team.
* `teamUrl` (URI): The HTTP URL for this team.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## TeamRemoveRepositoryAuditEntry

Audit log entry for a team.remove\_repository event.

**Implements:** AuditEntry, Node, OrganizationAuditEntryData, RepositoryAuditEntryData, TeamAuditEntryData

### Fields for `TeamRemoveRepositoryAuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `id` (ID!): The Node ID of the TeamRemoveRepositoryAuditEntry object.
* `isLdapMapped` (Boolean): Whether the team was mapped to an LDAP Group. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.
* `team` (Team): The team associated with the action.
* `teamName` (String): The name of the team.
* `teamResourcePath` (URI): The HTTP path for this team.
* `teamUrl` (URI): The HTTP URL for this team.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## TeamRepositoryEdge

Represents a team repository.

### Fields for `TeamRepositoryEdge`

* `cursor` (String!): A cursor for use in pagination.
* `node` (Repository!):
* `permission` (RepositoryPermission!): The permission level the team has on the repository.

## TextMatch

A text match within a search result.

### Fields for `TextMatch`

* `fragment` (String!): The specific text fragment within the property matched on.
* `highlights` (\[TextMatchHighlight!]!): Highlights within the matched fragment.
* `property` (String!): The property matched on.

## TextMatchHighlight

Represents a single highlight in a search result match.

### Fields for `TextMatchHighlight`

* `beginIndice` (Int!): The indice in the fragment where the matched text begins.
* `endIndice` (Int!): The indice in the fragment where the matched text ends.
* `text` (String!): The text matched.

## Topic

A topic aggregates entities that are related to a subject.

**Implements:** Node, Starrable

### Fields for `Topic`

* `id` (ID!): The Node ID of the Topic object.

* `name` (String!): The topic's name.

* `relatedTopics` (\[Topic!]!): A list of related topics, including aliases of this topic, sorted with the most relevant
  first. Returns up to 10 Topics.
  * `first` (Int): How many topics to return. Default: `3`.

* `repositories` (RepositoryConnection!): A list of repositories.
  * `affiliations` (\[RepositoryAffiliation]): Array of viewer's affiliation options for repositories returned from the
    connection. For example, OWNER will include only repositories that the
    current viewer owns.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `hasIssuesEnabled` (Boolean): If non-null, filters repositories according to whether they have issues enabled.
  * `isLocked` (Boolean): If non-null, filters repositories according to whether they have been locked.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder): Ordering options for repositories returned from the connection.
  * `ownerAffiliations` (\[RepositoryAffiliation]): Array of owner's affiliation options for repositories returned from the
    connection. For example, OWNER will include only repositories that the
    organization or user being viewed owns.
  * `privacy` (RepositoryPrivacy): If non-null, filters repositories according to privacy. Internal
    repositories are considered private; consider using the visibility argument
    if only internal repositories are needed. Cannot be combined with the
    visibility argument.
  * `sponsorableOnly` (Boolean): If true, only repositories whose owner can be sponsored via GitHub Sponsors will be returned.
  * `visibility` (RepositoryVisibility): If non-null, filters repositories according to visibility. Cannot be combined with the privacy argument.

* `stargazerCount` (Int!): Returns a count of how many stargazers there are on this object.

* `stargazers` (StargazerConnection!): A list of users who have starred this starrable.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (StarOrder): Order for connection.

* `viewerHasStarred` (Boolean!): Returns a boolean indicating whether the viewing user has starred this starrable.

## TransferredEvent

Represents atransferredevent on a given issue or pull request.

**Implements:** Node

### Fields for `TransferredEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `fromRepository` (Repository): The repository this came from.
* `id` (ID!): The Node ID of the TransferredEvent object.
* `issue` (Issue!): Identifies the issue associated with the event.

## Tree

Represents a Git tree.

**Implements:** GitObject, Node

### Fields for `Tree`

* `abbreviatedOid` (String!): An abbreviated version of the Git object ID.
* `commitResourcePath` (URI!): The HTTP path for this Git object.
* `commitUrl` (URI!): The HTTP URL for this Git object.
* `entries` (\[TreeEntry!]): A list of tree entries.
* `id` (ID!): The Node ID of the Tree object.
* `oid` (GitObjectID!): The Git object ID.
* `repository` (Repository!): The Repository the Git object belongs to.

## TreeEntry

Represents a Git tree entry.

### Fields for `TreeEntry`

* `extension` (String): The extension of the file.
* `isGenerated` (Boolean!): Whether or not this tree entry is generated.
* `language` (Language): The programming language this file is written in.
* `lineCount` (Int): Number of lines in the file.
* `mode` (Int!): Entry file mode.
* `name` (String!): Entry file name.
* `nameRaw` (Base64String!): Entry file name. (Base64-encoded).
* `object` (GitObject): Entry file object.
* `oid` (GitObjectID!): Entry file Git object ID.
* `path` (String): The full path of the file.
* `pathRaw` (Base64String): The full path of the file. (Base64-encoded).
* `repository` (Repository!): The Repository the tree entry belongs to.
* `size` (Int!): Entry byte size.
* `submodule` (Submodule): If the TreeEntry is for a directory occupied by a submodule project, this returns the corresponding submodule.
* `type` (String!): Entry file type.

## UnassignedEvent

Represents anunassignedevent on any assignable object.

**Implements:** Node

### Fields for `UnassignedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `assignable` (Assignable!): Identifies the assignable associated with the event.
* `assignee` (Assignee): Identifies the user or mannequin that was unassigned.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the UnassignedEvent object.
* `user` (User): Identifies the subject (user) who was unassigned. **Deprecated:** Assignees can now be mannequins. Use the assignee field instead. Removal on 2020-01-01 UTC.

## UnknownSignature

Represents an unknown signature on a Commit or Tag.

**Implements:** GitSignature

### Fields for `UnknownSignature`

* `email` (String!): Email used to sign this object.
* `isValid` (Boolean!): True if the signature is valid and verified by GitHub.
* `payload` (String!): Payload for GPG signing object. Raw ODB object without the signature header.
* `signature` (String!): ASCII-armored signature header from object.
* `signer` (User): GitHub user corresponding to the email signing this commit.
* `state` (GitSignatureState!): The state of this signature. VALID if signature is valid and verified by
  GitHub, otherwise represents reason why signature is considered invalid.
* `verifiedAt` (DateTime): The date the signature was verified, if valid.
* `wasSignedByGitHub` (Boolean!): True if the signature was made with GitHub's signing key.

## UnlabeledEvent

Represents anunlabeledevent on a given issue or pull request.

**Implements:** Node

### Fields for `UnlabeledEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the UnlabeledEvent object.
* `label` (Label!): Identifies the label associated with theunlabeledevent.
* `labelable` (Labelable!): Identifies the Labelable associated with the event.

## UnlockedEvent

Represents anunlockedevent on a given issue or pull request.

**Implements:** Node

### Fields for `UnlockedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the UnlockedEvent object.
* `lockable` (Lockable!): Object that was unlocked.

## UnmarkedAsDuplicateEvent

Represents anunmarked\_as\_duplicateevent on a given issue or pull request.

**Implements:** Node

### Fields for `UnmarkedAsDuplicateEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `canonical` (IssueOrPullRequest): The authoritative issue or pull request which has been duplicated by another.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `duplicate` (IssueOrPullRequest): The issue or pull request which has been marked as a duplicate of another.
* `id` (ID!): The Node ID of the UnmarkedAsDuplicateEvent object.
* `isCrossRepository` (Boolean!): Canonical and duplicate belong to different repositories.

## UnpinnedEvent

Represents anunpinnedevent on a given issue or pull request.

**Implements:** Node

### Fields for `UnpinnedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the UnpinnedEvent object.
* `issue` (Issue!): Identifies the issue associated with the event.

## UnsubscribedEvent

Represents anunsubscribedevent on a given Subscribable.

**Implements:** Node

### Fields for `UnsubscribedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the UnsubscribedEvent object.
* `subscribable` (Subscribable!): Object referenced by event.

## UpdateParameters

Only allow users with bypass permission to update matching refs.

### Fields for `UpdateParameters`

* `updateAllowsFetchAndMerge` (Boolean!): Branch can pull changes from its upstream repository.

## User

A user is an individual's account on GitHub that owns repositories and can make new content.

**Implements:** Actor, Agentic, Node, PackageOwner, ProfileOwner, ProjectOwner, ProjectV2Owner, ProjectV2Recent, RepositoryDiscussionAuthor, RepositoryDiscussionCommentAuthor, RepositoryOwner, Sponsorable, UniformResourceLocatable

### Fields for `User`

* `anyPinnableItems` (Boolean!): Determine if this repository owner has any items that can be pinned to their profile.
  * `type` (PinnableItemType): Filter to only a particular kind of pinnable item.

* `avatarUrl` (URI!): A URL pointing to the user's public avatar.
  * `size` (Int): The size of the resulting square image.

* `bio` (String): The user's public profile bio.

* `bioHTML` (HTML!): The user's public profile bio as HTML.

* `canReceiveOrganizationEmailsWhenNotificationsRestricted` (Boolean!): Could this user receive email notifications, if the organization had notification restrictions enabled?.
  * `login` (String!): The login of the organization to check.

* `commitComments` (CommitCommentConnection!): A list of commit comments made by this user. *(Pagination: `after`, `before`, `first`, `last`)*

* `company` (String): The user's public profile company.

* `companyHTML` (HTML!): The user's public profile company as HTML.

* `contributionsCollection` (ContributionsCollection!): The collection of contributions this user has made to different repositories.
  * `from` (DateTime): Only contributions made at this time or later will be counted. If omitted, defaults to a year ago.
  * `organizationID` (ID): The ID of the organization used to filter contributions.
  * `to` (DateTime): Only contributions made before and up to (including) this time will be
    counted. If omitted, defaults to the current time or one year from the
    provided from argument.

* `copilotEndpoints` (CopilotEndpoints): The user's Copilot endpoint information.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `email` (String!): The user's publicly visible profile email.

* `enterprises` (EnterpriseConnection): A list of enterprises that the user belongs to.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `membershipType` (EnterpriseMembershipType): Filter enterprises returned based on the user's membership type. Default: `ALL`.
  * `orderBy` (EnterpriseOrder): Ordering options for the User's enterprises.

* `estimatedNextSponsorsPayoutInCents` (Int!): The estimated next GitHub Sponsors payout for this user/organization in cents (USD).

* `followers` (FollowerConnection!): A list of users the given user is followed by. *(Pagination: `after`, `before`, `first`, `last`)*

* `following` (FollowingConnection!): A list of users the given user is following. *(Pagination: `after`, `before`, `first`, `last`)*

* `gist` (Gist): Find gist by repo name.
  * `name` (String!): The gist name to find.

* `gistComments` (GistCommentConnection!): A list of gist comments made by this user. *(Pagination: `after`, `before`, `first`, `last`)*

* `gists` (GistConnection!): A list of the Gists the user has created.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (GistOrder): Ordering options for gists returned from the connection.
  * `privacy` (GistPrivacy): Filters Gists according to privacy.

* `hasSponsorsListing` (Boolean!): True if this user/organization has a GitHub Sponsors listing.

* `hovercard` (Hovercard!): The hovercard information for this user in a given context.
  * `primarySubjectId` (ID): The ID of the subject to get the hovercard in the context of.

* `id` (ID!): The Node ID of the User object.

* `interactionAbility` (RepositoryInteractionAbility): The interaction ability settings for this user.

* `isBountyHunter` (Boolean!): Whether or not this user is a participant in the GitHub Security Bug Bounty.

* `isCampusExpert` (Boolean!): Whether or not this user is a participant in the GitHub Campus Experts Program.

* `isDeveloperProgramMember` (Boolean!): Whether or not this user is a GitHub Developer Program member.

* `isEmployee` (Boolean!): Whether or not this user is a GitHub employee.

* `isFollowingViewer` (Boolean!): Whether or not this user is following the viewer. Inverse of viewerIsFollowing.

* `isGitHubStar` (Boolean!): Whether or not this user is a member of the GitHub Stars Program.

* `isHireable` (Boolean!): Whether or not the user has marked themselves as for hire.

* `isSiteAdmin` (Boolean!): Whether or not this user is a site administrator.

* `isSponsoredBy` (Boolean!): Whether the given account is sponsoring this user/organization.
  * `accountLogin` (String!): The target account's login.

* `isSponsoringViewer` (Boolean!): True if the viewer is sponsored by this user/organization.

* `isViewer` (Boolean!): Whether or not this user is the viewing user.

* `issueComments` (IssueCommentConnection!): A list of issue comments made by this user.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueCommentOrder): Ordering options for issue comments returned from the connection.

* `issues` (IssueConnection!): A list of issues associated with this user.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `filterBy` (IssueFilters): Filtering options for issues returned from the connection.
  * `first` (Int): Returns the first n elements from the list.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for issues returned from the connection.
  * `states` (\[IssueState!]): A list of states to filter the issues by.

* `itemShowcase` (ProfileItemShowcase!): Showcases a selection of repositories and gists that the profile owner has
  either curated or that have been selected automatically based on popularity.

* `lifetimeReceivedSponsorshipValues` (SponsorAndLifetimeValueConnection!): Calculate how much each sponsor has ever paid total to this maintainer via
  GitHub Sponsors. Does not include sponsorships paid via Patreon.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorAndLifetimeValueOrder): Ordering options for results returned from the connection.

* `lists` (UserListConnection!): A user-curated list of repositories. *(Pagination: `after`, `before`, `first`, `last`)*

* `location` (String): The user's public profile location.

* `login` (String!): The username used to login.

* `monthlyEstimatedSponsorsIncomeInCents` (Int!): The estimated monthly GitHub Sponsors income for this user/organization in cents (USD).

* `name` (String): The user's public profile name.

* `organization` (Organization): Find an organization by its login that the user belongs to.
  * `login` (String!): The login of the organization to find.

* `organizationVerifiedDomainEmails` (\[String!]!): Verified email addresses that match verified domains for a specified organization the user is a member of.
  * `login` (String!): The login of the organization to match verified domains from.

* `organizations` (OrganizationConnection!): A list of organizations the user belongs to.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (OrganizationOrder): Ordering options for the User's organizations.

* `packages` (PackageConnection!): A list of packages under the owner.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `names` (\[String]): Find packages by their names.
  * `orderBy` (PackageOrder): Ordering of the returned packages.
  * `packageType` (PackageType): Filter registry package by type.
  * `repositoryId` (ID): Find packages in a repository by ID.

* `pinnableItems` (PinnableItemConnection!): A list of repositories and gists this profile owner can pin to their profile.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `types` (\[PinnableItemType!]): Filter the types of pinnable items that are returned.

* `pinnedItems` (PinnableItemConnection!): A list of repositories and gists this profile owner has pinned to their profile.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `types` (\[PinnableItemType!]): Filter the types of pinned items that are returned.

* `pinnedItemsRemaining` (Int!): Returns how many more items this profile owner can pin to their profile.

* `project` (Project): Find project by number. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `number` (Int!): The project number to find.

* `projectV2` (ProjectV2): Find a project by number.
  * `number` (Int!): The project number.

* `projects` (ProjectConnection!): A list of projects under the owner. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectOrder): Ordering options for projects returned from the connection.
  * `search` (String): Query to search projects by, currently only searching by name.
  * `states` (\[ProjectState!]): A list of states to filter the projects by.

* `projectsResourcePath` (URI!): The HTTP path listing user's projects.

* `projectsUrl` (URI!): The HTTP URL listing user's projects.

* `projectsV2` (ProjectV2Connection!): A list of projects under the owner.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `minPermissionLevel` (ProjectV2PermissionLevel): Filter projects based on user role. Default: `READ`.
  * `orderBy` (ProjectV2Order): How to order the returned projects.
  * `query` (String): A project to search for under the owner.

* `pronouns` (String): The user's profile pronouns.

* `publicKeys` (PublicKeyConnection!): A list of public keys associated with this user. *(Pagination: `after`, `before`, `first`, `last`)*

* `pullRequests` (PullRequestConnection!): A list of pull requests associated with this user.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `baseRefName` (String): The base ref name to filter the pull requests by.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `headRefName` (String): The head ref name to filter the pull requests by.
  * `labels` (\[String!]): A list of label names to filter the pull requests by.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (IssueOrder): Ordering options for pull requests returned from the connection.
  * `states` (\[PullRequestState!]): A list of states to filter the pull requests by.

* `recentProjects` (ProjectV2Connection!): Recent projects that this user has modified in the context of the owner. *(Pagination: `after`, `before`, `first`, `last`)*

* `repositories` (RepositoryConnection!): A list of repositories that the user owns.
  * `affiliations` (\[RepositoryAffiliation]): Array of viewer's affiliation options for repositories returned from the
    connection. For example, OWNER will include only repositories that the
    current viewer owns.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `hasIssuesEnabled` (Boolean): If non-null, filters repositories according to whether they have issues enabled.
  * `isArchived` (Boolean): If non-null, filters repositories according to whether they are archived and not maintained.
  * `isFork` (Boolean): If non-null, filters repositories according to whether they are forks of another repository.
  * `isLocked` (Boolean): If non-null, filters repositories according to whether they have been locked.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder): Ordering options for repositories returned from the connection.
  * `ownerAffiliations` (\[RepositoryAffiliation]): Array of owner's affiliation options for repositories returned from the
    connection. For example, OWNER will include only repositories that the
    organization or user being viewed owns.
  * `privacy` (RepositoryPrivacy): If non-null, filters repositories according to privacy. Internal
    repositories are considered private; consider using the visibility argument
    if only internal repositories are needed. Cannot be combined with the
    visibility argument.
  * `visibility` (RepositoryVisibility): If non-null, filters repositories according to visibility. Cannot be combined with the privacy argument.

* `repositoriesContributedTo` (RepositoryConnection!): A list of repositories that the user recently contributed to.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `contributionTypes` (\[RepositoryContributionType]): If non-null, include only the specified types of contributions. The
    GitHub.com UI uses \[COMMIT, ISSUE, PULL\_REQUEST, REPOSITORY].
  * `first` (Int): Returns the first n elements from the list.
  * `hasIssues` (Boolean): If non-null, filters repositories according to whether they have issues enabled.
  * `includeUserRepositories` (Boolean): If true, include user repositories.
  * `isLocked` (Boolean): If non-null, filters repositories according to whether they have been locked.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder): Ordering options for repositories returned from the connection.
  * `privacy` (RepositoryPrivacy): If non-null, filters repositories according to privacy.

* `repository` (Repository): Find Repository.
  * `followRenames` (Boolean): Follow repository renames. If disabled, a repository referenced by its old name will return an error. Default: `true`.
  * `name` (String!): Name of Repository to find.

* `repositoryDiscussionComments` (DiscussionCommentConnection!): Discussion comments this user has authored.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `onlyAnswers` (Boolean): Filter discussion comments to only those that were marked as the answer.
  * `repositoryId` (ID): Filter discussion comments to only those in a specific repository.

* `repositoryDiscussions` (DiscussionConnection!): Discussions this user has started.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `answered` (Boolean): Filter discussions to only those that have been answered or not. Defaults to
    including both answered and unanswered discussions.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (DiscussionOrder): Ordering options for discussions returned from the connection.
  * `repositoryId` (ID): Filter discussions to only those in a specific repository.
  * `states` (\[DiscussionState!]): A list of states to filter the discussions by.

* `resourcePath` (URI!): The HTTP path for this user.

* `savedReplies` (SavedReplyConnection): Replies this user has saved.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SavedReplyOrder): The field to order saved replies by.

* `socialAccounts` (SocialAccountConnection!): The user's social media accounts, ordered as they appear on the user's profile. *(Pagination: `after`, `before`, `first`, `last`)*

* `sponsoring` (SponsorConnection!): List of users and organizations this entity is sponsoring.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorOrder): Ordering options for the users and organizations returned from the connection.

* `sponsors` (SponsorConnection!): List of sponsors for this user or organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorOrder): Ordering options for sponsors returned from the connection.
  * `tierId` (ID): If given, will filter for sponsors at the given tier. Will only return
    sponsors whose tier the viewer is permitted to see.

* `sponsorsActivities` (SponsorsActivityConnection!): Events involving this sponsorable, such as new sponsorships.
  * `actions` (\[SponsorsActivityAction!]): Filter activities to only the specified actions.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includeAsSponsor` (Boolean): Whether to include those events where this sponsorable acted as the sponsor.
    Defaults to only including events where this sponsorable was the recipient
    of a sponsorship.
  * `includePrivate` (Boolean): Whether or not to include private activities in the result set. Defaults to including public and private activities. Default: `true`.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorsActivityOrder): Ordering options for activity returned from the connection.
  * `period` (SponsorsActivityPeriod): Filter activities returned to only those that occurred in the most recent
    specified time period. Set to ALL to avoid filtering by when the activity
    occurred. Will be ignored if since or until is given. Default: `MONTH`.
  * `since` (DateTime): Filter activities to those that occurred on or after this time.
  * `until` (DateTime): Filter activities to those that occurred before this time.

* `sponsorsListing` (SponsorsListing): The GitHub Sponsors listing for this user or organization.

* `sponsorshipForViewerAsSponsor` (Sponsorship): The sponsorship from the viewer to this user/organization; that is, the sponsorship where you're the sponsor.
  * `activeOnly` (Boolean): Whether to return the sponsorship only if it's still active. Pass false to
    get the viewer's sponsorship back even if it has been cancelled. Default: `true`.

* `sponsorshipForViewerAsSponsorable` (Sponsorship): The sponsorship from this user/organization to the viewer; that is, the sponsorship you're receiving.
  * `activeOnly` (Boolean): Whether to return the sponsorship only if it's still active. Pass false to
    get the sponsorship back even if it has been cancelled. Default: `true`.

* `sponsorshipNewsletters` (SponsorshipNewsletterConnection!): List of sponsorship updates sent from this sponsorable to sponsors.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorshipNewsletterOrder): Ordering options for sponsorship updates returned from the connection.

* `sponsorshipsAsMaintainer` (SponsorshipConnection!): The sponsorships where this user or organization is the maintainer receiving the funds.
  * `activeOnly` (Boolean): Whether to include only sponsorships that are active right now, versus all
    sponsorships this maintainer has ever received. Default: `true`.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `includePrivate` (Boolean): Whether or not to include private sponsorships in the result set.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorshipOrder): Ordering options for sponsorships returned from this connection. If left
    blank, the sponsorships will be ordered based on relevancy to the viewer.

* `sponsorshipsAsSponsor` (SponsorshipConnection!): The sponsorships where this user or organization is the funder.
  * `activeOnly` (Boolean): Whether to include only sponsorships that are active right now, versus all sponsorships this sponsor has ever made. Default: `true`.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `maintainerLogins` (\[String!]): Filter sponsorships returned to those for the specified maintainers. That
    is, the recipient of the sponsorship is a user or organization with one of
    the given logins.
  * `orderBy` (SponsorshipOrder): Ordering options for sponsorships returned from this connection. If left
    blank, the sponsorships will be ordered based on relevancy to the viewer.

* `starredRepositories` (StarredRepositoryConnection!): Repositories the user has starred.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (StarOrder): Order for connection.
  * `ownedByViewer` (Boolean): Filters starred repositories to only return repositories owned by the viewer.

* `status` (UserStatus): The user's description of what they're currently doing.

* `suggestedListNames` (\[UserListSuggestion!]!): Suggested names for user lists.

* `topRepositories` (RepositoryConnection!): Repositories the user has contributed to, ordered by contribution rank, plus repositories the user has created.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder!): Ordering options for repositories returned from the connection.
  * `since` (DateTime): How far back in time to fetch contributed repositories.

* `totalSponsorshipAmountAsSponsorInCents` (Int): The amount in United States cents (e.g., 500 = $5.00 USD) that this entity has
  spent on GitHub to fund sponsorships. Only returns a value when viewed by the
  user themselves or by a user who can manage sponsorships for the requested organization.
  * `since` (DateTime): Filter payments to those that occurred on or after this time.
  * `sponsorableLogins` (\[String!]): Filter payments to those made to the users or organizations with the specified usernames.
  * `until` (DateTime): Filter payments to those that occurred before this time.

* `twitterUsername` (String): The user's Twitter username.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this user.

* `userViewType` (UserViewType!): Whether the request returns publicly visible information or privately visible information about the user.

* `viewerCanChangePinnedItems` (Boolean!): Can the viewer pin repositories and gists to the profile?.

* `viewerCanCreateProjects` (Boolean!): Can the current viewer create new projects on this owner. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `viewerCanFollow` (Boolean!): Whether or not the viewer is able to follow the user.

* `viewerCanSponsor` (Boolean!): Whether or not the viewer is able to sponsor this user/organization.

* `viewerCopilotAgentCreatesChannel` (String): Channel value for subscribing to live updates for session creations.

* `viewerCopilotAgentLogUpdatesChannel` (String): Channel value for subscribing to live updates for session log updates.

* `viewerCopilotAgentTaskUpdatesChannel` (String): Channel value for subscribing to live updates for task updates.

* `viewerCopilotAgentUpdatesChannel` (String): Channel value for subscribing to live updates for session updates.

* `viewerIsFollowing` (Boolean!): Whether or not this user is followed by the viewer. Inverse of isFollowingViewer.

* `viewerIsSponsoring` (Boolean!): True if the viewer is sponsoring this user/organization.

* `watching` (RepositoryConnection!): A list of repositories the given user is watching.
  * `affiliations` (\[RepositoryAffiliation]): Affiliation options for repositories returned from the connection. If none
    specified, the results will include repositories for which the current
    viewer is an owner or collaborator, or member.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `hasIssuesEnabled` (Boolean): If non-null, filters repositories according to whether they have issues enabled.
  * `isLocked` (Boolean): If non-null, filters repositories according to whether they have been locked.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (RepositoryOrder): Ordering options for repositories returned from the connection.
  * `ownerAffiliations` (\[RepositoryAffiliation]): Array of owner's affiliation options for repositories returned from the
    connection. For example, OWNER will include only repositories that the
    organization or user being viewed owns.
  * `privacy` (RepositoryPrivacy): If non-null, filters repositories according to privacy. Internal
    repositories are considered private; consider using the visibility argument
    if only internal repositories are needed. Cannot be combined with the
    visibility argument.
  * `visibility` (RepositoryVisibility): If non-null, filters repositories according to visibility. Cannot be combined with the privacy argument.

* `websiteUrl` (URI): A URL pointing to the user's public website/blog.

## UserBlockedEvent

Represents auser\_blockedevent on a given user.

**Implements:** Node

### Fields for `UserBlockedEvent`

* `actor` (Actor): Identifies the actor who performed the event.
* `blockDuration` (UserBlockDuration!): Number of days that the user was blocked for.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `id` (ID!): The Node ID of the UserBlockedEvent object.
* `subject` (User): The user who was blocked.

## UserContentEdit

An edit on user content.

**Implements:** Node

### Fields for `UserContentEdit`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `deletedAt` (DateTime): Identifies the date and time when the object was deleted.
* `deletedBy` (Actor): The actor who deleted this content.
* `diff` (String): A summary of the changes for this edit.
* `editedAt` (DateTime!): When this content was edited.
* `editor` (Actor): The actor who edited this content.
* `id` (ID!): The Node ID of the UserContentEdit object.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## UserEmailMetadata

Email attributes from External Identity.

### Fields for `UserEmailMetadata`

* `primary` (Boolean): Boolean to identify primary emails.
* `type` (String): Type of email.
* `value` (String!): Email id.

## UserList

A user-curated list of repositories.

**Implements:** Node

### Fields for `UserList`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `description` (String): The description of this list.
* `id` (ID!): The Node ID of the UserList object.
* `isPrivate` (Boolean!): Whether or not this list is private.
* `items` (UserListItemsConnection!): The items associated with this list. *(Pagination: `after`, `before`, `first`, `last`)*
* `lastAddedAt` (DateTime!): The date and time at which this list was created or last had items added to it.
* `name` (String!): The name of this list.
* `slug` (String!): The slug of this list.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.
* `user` (User!): The user to which this list belongs.

## UserListSuggestion

Represents a suggested user list.

### Fields for `UserListSuggestion`

* `id` (ID): The ID of the suggested user list.
* `name` (String): The name of the suggested user list.

## UserNamespaceRepository

A repository owned by an Enterprise Managed user.

**Implements:** Node

### Fields for `UserNamespaceRepository`

* `id` (ID!): The Node ID of the UserNamespaceRepository object.
* `name` (String!): The name of the repository.
* `nameWithOwner` (String!): The repository's name with owner.
* `owner` (RepositoryOwner!): The user owner of the repository.

## UserStatus

The user's description of what they're currently doing.

**Implements:** Node

### Fields for `UserStatus`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `emoji` (String): An emoji summarizing the user's status.
* `emojiHTML` (HTML): The status emoji as HTML.
* `expiresAt` (DateTime): If set, the status will not be shown after this date.
* `id` (ID!): The Node ID of the UserStatus object.
* `indicatesLimitedAvailability` (Boolean!): Whether this status indicates the user is not fully available on GitHub.
* `message` (String): A brief message describing what the user is doing.
* `organization` (Organization): The organization whose members can see this status. If null, this status is publicly visible.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.
* `user` (User!): The user who has this status.

## VerifiableDomain

A domain that can be verified or approved for an organization or an enterprise.

**Implements:** Node

### Fields for `VerifiableDomain`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `dnsHostName` (URI): The DNS host name that should be used for verification.
* `domain` (URI!): The unicode encoded domain.
* `hasFoundHostName` (Boolean!): Whether a TXT record for verification with the expected host name was found.
* `hasFoundVerificationToken` (Boolean!): Whether a TXT record for verification with the expected verification token was found.
* `id` (ID!): The Node ID of the VerifiableDomain object.
* `isApproved` (Boolean!): Whether or not the domain is approved.
* `isRequiredForPolicyEnforcement` (Boolean!): Whether this domain is required to exist for an organization or enterprise policy to be enforced.
* `isVerified` (Boolean!): Whether or not the domain is verified.
* `owner` (VerifiableDomainOwner!): The owner of the domain.
* `punycodeEncodedDomain` (URI!): The punycode encoded domain.
* `tokenExpirationTime` (DateTime): The time that the current verification token will expire.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.
* `verificationToken` (String): The current verification token for the domain.

## ViewerHovercardContext

A hovercard context with a message describing how the viewer is related.

**Implements:** HovercardContext

### Fields for `ViewerHovercardContext`

* `message` (String!): A string describing this context.
* `octicon` (String!): An octicon to accompany this context.
* `viewer` (User!): Identifies the user who is related to this context.

## Workflow

A workflow contains meta information about an Actions workflow file.

**Implements:** Node, UniformResourceLocatable

### Fields for `Workflow`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `databaseId` (Int): Identifies the primary key from the database.

* `id` (ID!): The Node ID of the Workflow object.

* `name` (String!): The name of the workflow.

* `resourcePath` (URI!): The HTTP path for this workflow.

* `runs` (WorkflowRunConnection!): The runs of the workflow.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (WorkflowRunOrder): Ordering options for the connection.

* `state` (WorkflowState!): The state of the workflow.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this workflow.

## WorkflowFileReference

A workflow that must run for this rule to pass.

### Fields for `WorkflowFileReference`

* `path` (String!): The path to the workflow file.
* `ref` (String): The ref (branch or tag) of the workflow file to use.
* `repositoryId` (Int!): The ID of the repository where the workflow is defined.
* `sha` (String): The commit SHA of the workflow file to use.

## WorkflowRun

A workflow run.

**Implements:** Node, UniformResourceLocatable

### Fields for `WorkflowRun`

* `checkSuite` (CheckSuite!): The check suite this workflow run belongs to.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (Int): Identifies the primary key from the database.
* `deploymentReviews` (DeploymentReviewConnection!): The log of deployment reviews. *(Pagination: `after`, `before`, `first`, `last`)*
* `event` (String!): The event that triggered the workflow run.
* `file` (WorkflowRunFile): The workflow file.
* `id` (ID!): The Node ID of the WorkflowRun object.
* `pendingDeploymentRequests` (DeploymentRequestConnection!): The pending deployment requests of all check runs in this workflow run. *(Pagination: `after`, `before`, `first`, `last`)*
* `resourcePath` (URI!): The HTTP path for this workflow run.
* `runNumber` (Int!): A number that uniquely identifies this workflow run in its parent workflow.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.
* `url` (URI!): The HTTP URL for this workflow run.
* `workflow` (Workflow!): The workflow executed in this workflow run.

## WorkflowRunFile

An executed workflow file for a workflow run.

**Implements:** Node, UniformResourceLocatable

### Fields for `WorkflowRunFile`

* `id` (ID!): The Node ID of the WorkflowRunFile object.
* `path` (String!): The path of the workflow file relative to its repository.
* `repositoryFileUrl` (URI!): The direct link to the file in the repository which stores the workflow file.
* `repositoryName` (URI!): The repository name and owner which stores the workflow file.
* `resourcePath` (URI!): The HTTP path for this workflow run file.
* `run` (WorkflowRun!): The parent workflow run execution for this file.
* `url` (URI!): The HTTP URL for this workflow run file.
* `viewerCanPushRepository` (Boolean!): If the viewer has permissions to push to the repository which stores the workflow.
* `viewerCanReadRepository` (Boolean!): If the viewer has permissions to read the repository which stores the workflow.

## WorkflowsParameters

Require all changes made to a targeted branch to pass the specified workflows before they can be merged.

### Fields for `WorkflowsParameters`

* `doNotEnforceOnCreate` (Boolean!): Allow repositories and branches to be created if a check would otherwise prohibit it.
* `workflows` (\[WorkflowFileReference!]!): Workflows that must pass for this rule to pass.