# Interfaces

Interfaces serve as parent objects from which other objects can inherit.

## About interfaces

[Interfaces](https://spec.graphql.org/June2018/#sec-Interfaces) serve as parent objects from which other objects can inherit.

For example, [`Lockable`](/en/graphql/reference/interfaces#lockable) is an interface because both [`Issue`](/en/graphql/reference/objects#issue) and [`PullRequest`](/en/graphql/reference/objects#pullrequest) objects can be locked. An interface has its own list of named fields that are shared by implementing objects.

For more information, see [Introduction to GraphQL](/en/graphql/guides/introduction-to-graphql#implementation).

## Actor

Represents an object which can take actions on GitHub. Typically a User or Bot.

### Fields for `Actor`

* `avatarUrl` (URI!): A URL pointing to the actor's public avatar.
  * `size` (Int): The size of the resulting square image.

* `login` (String!): The username of the actor.

* `resourcePath` (URI!): The HTTP path for this actor.

* `url` (URI!): The HTTP URL for this actor.

## Agentic

Copilot Agentic fields in context of the current viewer.

### Fields for `Agentic`

* `viewerCopilotAgentCreatesChannel` (String): Channel value for subscribing to live updates for session creations.
* `viewerCopilotAgentLogUpdatesChannel` (String): Channel value for subscribing to live updates for session log updates.
* `viewerCopilotAgentTaskUpdatesChannel` (String): Channel value for subscribing to live updates for task updates.
* `viewerCopilotAgentUpdatesChannel` (String): Channel value for subscribing to live updates for session updates.

## Assignable

An object that can have users assigned to it.

### Fields for `Assignable`

* `assignedActors` (AssigneeConnection!): A list of actors assigned to this object. *(Pagination: `after`, `before`, `first`, `last`)*
* `assignees` (UserConnection!): A list of Users assigned to this object. *(Pagination: `after`, `before`, `first`, `last`)*
* `suggestedActors` (AssigneeConnection!): A list of suggested actors to assign to this object.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `query` (String): If provided, searches users by login or profile name.

## AuditEntry

An entry in the audit log.

### Fields for `AuditEntry`

* `action` (String!): The action name. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actor` (AuditEntryActor): The user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorIp` (String): The IP address of the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLocation` (ActorLocation): A readable representation of the actor's location. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorLogin` (String): The username of the user who initiated the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorResourcePath` (URI): The HTTP path for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `actorUrl` (URI): The HTTP URL for the actor. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `createdAt` (PreciseDateTime!): The time the action was initiated. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `operationType` (OperationType): The corresponding operation type for the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `user` (User): The user affected by the action. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userLogin` (String): For actions involving two users, the actor is the initiator and the user is the affected user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userResourcePath` (URI): The HTTP path for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `userUrl` (URI): The HTTP URL for the user. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## Closable

An object that can be closed.

### Fields for `Closable`

* `closed` (Boolean!): Indicates if the object is closed (definition of closed may depend on type).
* `closedAt` (DateTime): Identifies the date and time when the object was closed.
* `viewerCanClose` (Boolean!): Indicates if the object can be closed by the viewer.
* `viewerCanReopen` (Boolean!): Indicates if the object can be reopened by the viewer.

## Comment

Represents a comment.

### Fields for `Comment`

* `author` (Actor): The actor who authored the comment.
* `authorAssociation` (CommentAuthorAssociation!): Author's association with the subject of the comment.
* `body` (String!): The body as Markdown.
* `bodyHTML` (HTML!): The body rendered to HTML.
* `bodyText` (String!): The body rendered to text.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `createdViaEmail` (Boolean!): Check if this comment was created via an email reply.
* `editor` (Actor): The actor who edited the comment.
* `id` (ID!): The Node ID of the Comment object.
* `includesCreatedEdit` (Boolean!): Check if this comment was edited and includes an edit with the creation data.
* `lastEditedAt` (DateTime): The moment the editor made the last edit.
* `publishedAt` (DateTime): Identifies when the comment was published at.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.
* `userContentEdits` (UserContentEditConnection): A list of edits to this content. *(Pagination: `after`, `before`, `first`, `last`)*
* `viewerDidAuthor` (Boolean!): Did the viewer author this comment.

## Contribution

Represents a contribution a user made on GitHub, such as opening an issue.

### Fields for `Contribution`

* `isRestricted` (Boolean!): Whether this contribution is associated with a record you do not have access to. For
  example, your own 'first issue' contribution may have been made on a repository you can no
  longer access.
* `occurredAt` (DateTime!): When this contribution was made.
* `resourcePath` (URI!): The HTTP path for this contribution.
* `url` (URI!): The HTTP URL for this contribution.
* `user` (User!): The user who made this contribution.

## Deletable

Entities that can be deleted.

### Fields for `Deletable`

* `viewerCanDelete` (Boolean!): Check if the current viewer can delete this object.

## EnterpriseAuditEntryData

Metadata for an audit entry containing enterprise account information.

### Fields for `EnterpriseAuditEntryData`

* `enterpriseResourcePath` (URI): The HTTP path for this enterprise.
* `enterpriseSlug` (String): The slug of the enterprise.
* `enterpriseUrl` (URI): The HTTP URL for this enterprise.

## GitObject

Represents a Git object.

### Fields for `GitObject`

* `abbreviatedOid` (String!): An abbreviated version of the Git object ID.
* `commitResourcePath` (URI!): The HTTP path for this Git object.
* `commitUrl` (URI!): The HTTP URL for this Git object.
* `id` (ID!): The Node ID of the GitObject object.
* `oid` (GitObjectID!): The Git object ID.
* `repository` (Repository!): The Repository the Git object belongs to.

## GitSignature

Information about a signature (GPG or S/MIME) on a Commit or Tag.

### Fields for `GitSignature`

* `email` (String!): Email used to sign this object.
* `isValid` (Boolean!): True if the signature is valid and verified by GitHub.
* `payload` (String!): Payload for GPG signing object. Raw ODB object without the signature header.
* `signature` (String!): ASCII-armored signature header from object.
* `signer` (User): GitHub user corresponding to the email signing this commit.
* `state` (GitSignatureState!): The state of this signature. VALID if signature is valid and verified by
  GitHub, otherwise represents reason why signature is considered invalid.
* `verifiedAt` (DateTime): The date the signature was verified, if valid.
* `wasSignedByGitHub` (Boolean!): True if the signature was made with GitHub's signing key.

## HovercardContext

An individual line of a hovercard.

### Fields for `HovercardContext`

* `message` (String!): A string describing this context.
* `octicon` (String!): An octicon to accompany this context.

## IssueFieldCommon

Common fields across different issue field types.

### Fields for `IssueFieldCommon`

* `createdAt` (DateTime!): The issue field's creation timestamp.
* `dataType` (IssueFieldDataType!): The issue field's data type.
* `description` (String): The issue field's description.
* `name` (String!): The issue field's name.
* `visibility` (IssueFieldVisibility!): The issue field's visibility.

## IssueFieldValueCommon

Common fields across different issue field value types.

### Fields for `IssueFieldValueCommon`

* `field` (IssueFields): The issue field that contains this value.

## Labelable

An object that can have labels assigned to it.

### Fields for `Labelable`

* `labels` (LabelConnection): A list of labels associated with the object.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (LabelOrder): Ordering options for labels returned from the connection.

* `viewerCanLabel` (Boolean!): Indicates if the viewer can edit labels for this object.

## Lockable

An object that can be locked.

### Fields for `Lockable`

* `activeLockReason` (LockReason): Reason that the conversation was locked.
* `locked` (Boolean!): true if the object is locked.

## MemberStatusable

Entities that have members who can set status messages.

### Fields for `MemberStatusable`

* `memberStatuses` (UserStatusConnection!): Get the status messages members of this entity have set that are either public or visible only to the organization.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (UserStatusOrder): Ordering options for user statuses returned from the connection.

## Migration

Represents a GitHub Enterprise Importer (GEI) migration.

### Fields for `Migration`

* `continueOnError` (Boolean!): The migration flag to continue on error.
* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `databaseId` (String): Identifies the primary key from the database.
* `failureReason` (String): The reason the migration failed.
* `id` (ID!): The Node ID of the Migration object.
* `migrationLogUrl` (URI): The URL for the migration log (expires 1 day after migration completes).
* `migrationSource` (MigrationSource!): The migration source.
* `repositoryName` (String!): The target repository name.
* `sourceUrl` (URI!): The migration source URL, for example <https://github.com> or <https://monalisa.ghe.com>.
* `state` (MigrationState!): The migration state.
* `warningsCount` (Int!): The number of warnings encountered for this migration. To review the warnings,
  check the Migration Log.

## Minimizable

Entities that can be minimized.

### Fields for `Minimizable`

* `isMinimized` (Boolean!): Returns whether or not a comment has been minimized.
* `minimizedReason` (String): Returns why the comment was minimized. One of abuse, off-topic,
  outdated, resolved, duplicate, spam, and low-quality. Note that the
  case and formatting of these values differs from the inputs to the
  MinimizeComment mutation.
* `viewerCanMinimize` (Boolean!): Check if the current viewer can minimize this object.
* `viewerCanUnminimize` (Boolean!): Check if the current viewer can unminimize this object.

## Node

An object with an ID.

### Fields for `Node`

* `id` (ID!): ID of the object.

## OauthApplicationAuditEntryData

Metadata for an audit entry with action oauth\_application.\*.

### Fields for `OauthApplicationAuditEntryData`

* `oauthApplicationName` (String): The name of the OAuth application.
* `oauthApplicationResourcePath` (URI): The HTTP path for the OAuth application.
* `oauthApplicationUrl` (URI): The HTTP URL for the OAuth application.

## OrganizationAuditEntryData

Metadata for an audit entry with action org.\*.

### Fields for `OrganizationAuditEntryData`

* `organization` (Organization): The Organization associated with the Audit Entry. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationName` (String): The name of the Organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationResourcePath` (URI): The HTTP path for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.
* `organizationUrl` (URI): The HTTP URL for the organization. **Deprecated:** The GraphQL audit-log is deprecated. Please use the REST API instead. Removal on 2026-04-01 UTC.

## PackageOwner

Represents an owner of a package.

### Fields for `PackageOwner`

* `id` (ID!): The Node ID of the PackageOwner object.
* `packages` (PackageConnection!): A list of packages under the owner.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `names` (\[String]): Find packages by their names.
  * `orderBy` (PackageOrder): Ordering of the returned packages.
  * `packageType` (PackageType): Filter registry package by type.
  * `repositoryId` (ID): Find packages in a repository by ID.

## Pinnable

Entities that can be pinned.

### Fields for `Pinnable`

* `isPinned` (Boolean): Indicates whether or not this entity is currently pinned.
* `pinnedAt` (DateTime): Identifies the date and time when this entity was pinned.
* `pinnedBy` (User): The user who pinned this entity.
* `viewerCanPin` (Boolean!): Check if the current viewer can pin this entity.
* `viewerCanUnpin` (Boolean!): Check if the current viewer can unpin this entity.

## ProfileOwner

Represents any entity on GitHub that has a profile page.

### Fields for `ProfileOwner`

* `anyPinnableItems` (Boolean!): Determine if this repository owner has any items that can be pinned to their profile.
  * `type` (PinnableItemType): Filter to only a particular kind of pinnable item.

* `email` (String): The public profile email.

* `id` (ID!): The Node ID of the ProfileOwner object.

* `itemShowcase` (ProfileItemShowcase!): Showcases a selection of repositories and gists that the profile owner has
  either curated or that have been selected automatically based on popularity.

* `location` (String): The public profile location.

* `login` (String!): The username used to login.

* `name` (String): The public profile name.

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

* `viewerCanChangePinnedItems` (Boolean!): Can the viewer pin repositories and gists to the profile?.

* `websiteUrl` (URI): The public profile website URL.

## ProjectOwner

Represents an owner of a Project.

### Fields for `ProjectOwner`

* `id` (ID!): The Node ID of the ProjectOwner object. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `project` (Project): Find project by number. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `number` (Int!): The project number to find.

* `projects` (ProjectConnection!): A list of projects under the owner. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ProjectOrder): Ordering options for projects returned from the connection.
  * `search` (String): Query to search projects by, currently only searching by name.
  * `states` (\[ProjectState!]): A list of states to filter the projects by.

* `projectsResourcePath` (URI!): The HTTP path listing owners projects. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `projectsUrl` (URI!): The HTTP URL listing owners projects. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

* `viewerCanCreateProjects` (Boolean!): Can the current viewer create new projects on this owner. **Deprecated:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

## ProjectV2Event

Represents an event related to a project on the timeline of an issue or pull request.

### Fields for `ProjectV2Event`

* `project` (ProjectV2): Project referenced by event.
* `wasAutomated` (Boolean!): Did this event result from workflow automation?.

## ProjectV2FieldCommon

Common fields across different project field types.

### Fields for `ProjectV2FieldCommon`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `dataType` (ProjectV2FieldType!): The field's type.
* `databaseId` (Int): Identifies the primary key from the database.
* `id` (ID!): The Node ID of the ProjectV2FieldCommon object.
* `name` (String!): The project field's name.
* `project` (ProjectV2!): The project that contains this field.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2ItemFieldValueCommon

Common fields across different project field value types.

### Fields for `ProjectV2ItemFieldValueCommon`

* `createdAt` (DateTime!): Identifies the date and time when the object was created.
* `creator` (Actor): The actor who created the item.
* `databaseId` (Int): Identifies the primary key from the database.
* `field` (ProjectV2FieldConfiguration!): The project field that contains this value.
* `id` (ID!): The Node ID of the ProjectV2ItemFieldValueCommon object.
* `item` (ProjectV2Item!): The project item that contains this value.
* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

## ProjectV2Owner

Represents an owner of a project.

### Fields for `ProjectV2Owner`

* `id` (ID!): The Node ID of the ProjectV2Owner object.

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

## ProjectV2Recent

Recent projects for the owner.

### Fields for `ProjectV2Recent`

* `recentProjects` (ProjectV2Connection!): Recent projects that this user has modified in the context of the owner. *(Pagination: `after`, `before`, `first`, `last`)*

## Reactable

Represents a subject that can be reacted on.

### Fields for `Reactable`

* `databaseId` (Int): Identifies the primary key from the database.

* `id` (ID!): The Node ID of the Reactable object.

* `reactionGroups` (\[ReactionGroup!]): A list of reactions grouped by content left on the subject.

* `reactions` (ReactionConnection!): A list of Reactions left on the Issue.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `content` (ReactionContent): Allows filtering Reactions by emoji.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (ReactionOrder): Allows specifying the order in which reactions are returned.

* `viewerCanReact` (Boolean!): Can user react to this subject.

## RepositoryAuditEntryData

Metadata for an audit entry with action repo.\*.

### Fields for `RepositoryAuditEntryData`

* `repository` (Repository): The repository associated with the action.
* `repositoryName` (String): The name of the repository.
* `repositoryResourcePath` (URI): The HTTP path for the repository.
* `repositoryUrl` (URI): The HTTP URL for the repository.

## RepositoryDiscussionAuthor

Represents an author of discussions in repositories.

### Fields for `RepositoryDiscussionAuthor`

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

## RepositoryDiscussionCommentAuthor

Represents an author of discussion comments in repositories.

### Fields for `RepositoryDiscussionCommentAuthor`

* `repositoryDiscussionComments` (DiscussionCommentConnection!): Discussion comments this user has authored.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `onlyAnswers` (Boolean): Filter discussion comments to only those that were marked as the answer.
  * `repositoryId` (ID): Filter discussion comments to only those in a specific repository.

## RepositoryInfo

A subset of repository info.

### Fields for `RepositoryInfo`

* `archivedAt` (DateTime): Identifies the date and time when the repository was archived.

* `createdAt` (DateTime!): Identifies the date and time when the object was created.

* `description` (String): The description of the repository.

* `descriptionHTML` (HTML!): The description of the repository rendered to HTML.

* `forkCount` (Int!): Returns how many forks there are of this repository in the whole network.

* `hasDiscussionsEnabled` (Boolean!): Indicates if the repository has the Discussions feature enabled.

* `hasIssuesEnabled` (Boolean!): Indicates if the repository has issues feature enabled.

* `hasProjectsEnabled` (Boolean!): Indicates if the repository has the Projects feature enabled.

* `hasPullRequestsEnabled` (Boolean!): Indicates if the repository has the pull requests feature enabled.

* `hasSponsorshipsEnabled` (Boolean!): Indicates if the repository displays a Sponsor button for financial contributions.

* `hasWikiEnabled` (Boolean!): Indicates if the repository has wiki feature enabled.

* `homepageUrl` (URI): The repository's URL.

* `isArchived` (Boolean!): Indicates if the repository is unmaintained.

* `isFork` (Boolean!): Identifies if the repository is a fork.

* `isInOrganization` (Boolean!): Indicates if a repository is either owned by an organization, or is a private fork of an organization repository.

* `isLocked` (Boolean!): Indicates if the repository has been locked or not.

* `isMirror` (Boolean!): Identifies if the repository is a mirror.

* `isPrivate` (Boolean!): Identifies if the repository is private or internal.

* `isTemplate` (Boolean!): Identifies if the repository is a template that can be used to generate new repositories.

* `licenseInfo` (License): The license associated with the repository.

* `lockReason` (RepositoryLockReason): The reason the repository has been locked.

* `mirrorUrl` (URI): The repository's original mirror URL.

* `name` (String!): The name of the repository.

* `nameWithOwner` (String!): The repository's name with owner.

* `openGraphImageUrl` (URI!): The image used to represent this repository in Open Graph data.

* `owner` (RepositoryOwner!): The User owner of the repository.

* `pullRequestCreationPolicy` (PullRequestCreationPolicy): The policy controlling who can create pull requests in this repository.

* `pushedAt` (DateTime): Identifies the date and time when the repository was last pushed to.

* `resourcePath` (URI!): The HTTP path for this repository.

* `shortDescriptionHTML` (HTML!): A description of the repository, rendered to HTML without any links in it.
  * `limit` (Int): How many characters to return. Default: `200`.

* `updatedAt` (DateTime!): Identifies the date and time when the object was last updated.

* `url` (URI!): The HTTP URL for this repository.

* `usesCustomOpenGraphImage` (Boolean!): Whether this repository has a custom image to use with Open Graph as opposed to being represented by the owner's avatar.

* `visibility` (RepositoryVisibility!): Indicates the repository's visibility level.

## RepositoryNode

Represents a object that belongs to a repository.

### Fields for `RepositoryNode`

* `repository` (Repository!): The repository associated with this node.

## RepositoryOwner

Represents an owner of a Repository.

### Fields for `RepositoryOwner`

* `avatarUrl` (URI!): A URL pointing to the owner's public avatar.
  * `size` (Int): The size of the resulting square image.

* `id` (ID!): The Node ID of the RepositoryOwner object.

* `login` (String!): The username used to login.

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

* `resourcePath` (URI!): The HTTP URL for the owner.

* `url` (URI!): The HTTP URL for the owner.

## RequirableByPullRequest

Represents a type that can be required by a pull request for merging.

### Fields for `RequirableByPullRequest`

* `isRequired` (Boolean!): Whether this is required to pass before merging for a specific pull request.
  * `pullRequestId` (ID): The id of the pull request this is required for.
  * `pullRequestNumber` (Int): The number of the pull request this is required for.

## Sponsorable

Entities that can sponsor or be sponsored through GitHub Sponsors.

### Fields for `Sponsorable`

* `estimatedNextSponsorsPayoutInCents` (Int!): The estimated next GitHub Sponsors payout for this user/organization in cents (USD).

* `hasSponsorsListing` (Boolean!): True if this user/organization has a GitHub Sponsors listing.

* `isSponsoredBy` (Boolean!): Whether the given account is sponsoring this user/organization.
  * `accountLogin` (String!): The target account's login.

* `isSponsoringViewer` (Boolean!): True if the viewer is sponsored by this user/organization.

* `lifetimeReceivedSponsorshipValues` (SponsorAndLifetimeValueConnection!): Calculate how much each sponsor has ever paid total to this maintainer via
  GitHub Sponsors. Does not include sponsorships paid via Patreon.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (SponsorAndLifetimeValueOrder): Ordering options for results returned from the connection.

* `monthlyEstimatedSponsorsIncomeInCents` (Int!): The estimated monthly GitHub Sponsors income for this user/organization in cents (USD).

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

* `totalSponsorshipAmountAsSponsorInCents` (Int): The amount in United States cents (e.g., 500 = $5.00 USD) that this entity has
  spent on GitHub to fund sponsorships. Only returns a value when viewed by the
  user themselves or by a user who can manage sponsorships for the requested organization.
  * `since` (DateTime): Filter payments to those that occurred on or after this time.
  * `sponsorableLogins` (\[String!]): Filter payments to those made to the users or organizations with the specified usernames.
  * `until` (DateTime): Filter payments to those that occurred before this time.

* `viewerCanSponsor` (Boolean!): Whether or not the viewer is able to sponsor this user/organization.

* `viewerIsSponsoring` (Boolean!): True if the viewer is sponsoring this user/organization.

## Starrable

Things that can be starred.

### Fields for `Starrable`

* `id` (ID!): The Node ID of the Starrable object.

* `stargazerCount` (Int!): Returns a count of how many stargazers there are on this object.

* `stargazers` (StargazerConnection!): A list of users who have starred this starrable.
  * `after` (String): Returns the elements in the list that come after the specified cursor.
  * `before` (String): Returns the elements in the list that come before the specified cursor.
  * `first` (Int): Returns the first n elements from the list.
  * `last` (Int): Returns the last n elements from the list.
  * `orderBy` (StarOrder): Order for connection.

* `viewerHasStarred` (Boolean!): Returns a boolean indicating whether the viewing user has starred this starrable.

## Subscribable

Entities that can be subscribed to for web and email notifications.

### Fields for `Subscribable`

* `id` (ID!): The Node ID of the Subscribable object.
* `viewerCanSubscribe` (Boolean!): Check if the viewer is able to change their subscription status for the repository.
* `viewerSubscription` (SubscriptionState): Identifies if the viewer is watching, not watching, or ignoring the subscribable entity.

## SubscribableThread

Entities that can be subscribed to for web and email notifications.

### Fields for `SubscribableThread`

* `id` (ID!): The Node ID of the SubscribableThread object.
* `viewerThreadSubscriptionFormAction` (ThreadSubscriptionFormAction): Identifies the viewer's thread subscription form action.
* `viewerThreadSubscriptionStatus` (ThreadSubscriptionState): Identifies the viewer's thread subscription status.

## TeamAuditEntryData

Metadata for an audit entry with action team.\*.

### Fields for `TeamAuditEntryData`

* `team` (Team): The team associated with the action.
* `teamName` (String): The name of the team.
* `teamResourcePath` (URI): The HTTP path for this team.
* `teamUrl` (URI): The HTTP URL for this team.

## TopicAuditEntryData

Metadata for an audit entry with a topic.

### Fields for `TopicAuditEntryData`

* `topic` (Topic): The name of the topic added to the repository.
* `topicName` (String): The name of the topic added to the repository.

## UniformResourceLocatable

Represents a type that can be retrieved by a URL.

### Fields for `UniformResourceLocatable`

* `resourcePath` (URI!): The HTML path to this resource.
* `url` (URI!): The URL to this resource.

## Updatable

Entities that can be updated.

### Fields for `Updatable`

* `viewerCanUpdate` (Boolean!): Check if the current viewer can update this object.

## UpdatableComment

Comments that can be updated.

### Fields for `UpdatableComment`

* `viewerCannotUpdateReasons` (\[CommentCannotUpdateReason!]!): Reasons why the current viewer can not update this comment.

## Votable

A subject that may be upvoted.

### Fields for `Votable`

* `upvoteCount` (Int!): Number of upvotes that this subject has received.
* `viewerCanUpvote` (Boolean!): Whether or not the current user can add or remove an upvote on this subject.
* `viewerHasUpvoted` (Boolean!): Whether or not the current user has already upvoted this subject.