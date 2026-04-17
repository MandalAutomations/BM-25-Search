# Mutations

The mutation type defines GraphQL operations that change data on the server.

## About mutations

Every GraphQL schema has a root type for both queries and mutations. The [mutation type](https://spec.graphql.org/June2018/#sec-Type-System) defines GraphQL operations that change data on the server. It is analogous to performing HTTP verbs such as `POST`, `PATCH`, and `DELETE`.

For more information, see [Forming calls with GraphQL](/en/graphql/guides/forming-calls-with-graphql#about-mutations).

## abortQueuedMigrations

Clear all of a customer's queued migrations.

### Input fields for `abortQueuedMigrations`

* `input` (AbortQueuedMigrationsInput!):

### Return fields for `abortQueuedMigrations`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `success` (Boolean): Did the operation succeed?.

## abortRepositoryMigration

Abort a repository migration queued or in progress.

### Input fields for `abortRepositoryMigration`

* `input` (AbortRepositoryMigrationInput!):

### Return fields for `abortRepositoryMigration`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `success` (Boolean): Did the operation succeed?.

## acceptEnterpriseAdministratorInvitation

Accepts a pending invitation for a user to become an administrator of an enterprise.

### Input fields for `acceptEnterpriseAdministratorInvitation`

* `input` (AcceptEnterpriseAdministratorInvitationInput!):

### Return fields for `acceptEnterpriseAdministratorInvitation`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `invitation` (EnterpriseAdministratorInvitation): The invitation that was accepted.
* `message` (String): A message confirming the result of accepting an administrator invitation.

## acceptEnterpriseMemberInvitation

Accepts a pending invitation for a user to become an unaffiliated member of an enterprise.

### Input fields for `acceptEnterpriseMemberInvitation`

* `input` (AcceptEnterpriseMemberInvitationInput!):

### Return fields for `acceptEnterpriseMemberInvitation`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `invitation` (EnterpriseMemberInvitation): The invitation that was accepted.
* `message` (String): A message confirming the result of accepting an unaffiliated member invitation.

## acceptTopicSuggestion

Applies a suggested topic to the repository.

### Input fields for `acceptTopicSuggestion`

* `input` (AcceptTopicSuggestionInput!):

### Return fields for `acceptTopicSuggestion`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `topic` (Topic): The accepted topic. **Deprecated:** Suggested topics are no longer supported Removal on 2024-04-01 UTC.

## accessUserNamespaceRepository

Access user namespace repository for a temporary duration.

### Input fields for `accessUserNamespaceRepository`

* `input` (AccessUserNamespaceRepositoryInput!):

### Return fields for `accessUserNamespaceRepository`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `expiresAt` (DateTime): The time that repository access expires at.
* `repository` (Repository): The repository that is temporarily accessible.

## addAssigneesToAssignable

Adds assignees to an assignable object.

### Input fields for `addAssigneesToAssignable`

* `input` (AddAssigneesToAssignableInput!):

### Return fields for `addAssigneesToAssignable`

* `assignable` (Assignable): The item that was assigned.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## addBlockedBy

Adds a 'blocked by' relationship to an issue.

### Input fields for `addBlockedBy`

* `input` (AddBlockedByInput!):

### Return fields for `addBlockedBy`

* `blockingIssue` (Issue): The issue that is blocking the given issue.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue that is blocked.

## addComment

Adds a comment to an Issue or Pull Request.

### Input fields for `addComment`

* `input` (AddCommentInput!):

### Return fields for `addComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `commentEdge` (IssueCommentEdge): The edge from the subject's comment connection.
* `subject` (Node): The subject.
* `timelineEdge` (IssueTimelineItemEdge): The edge from the subject's timeline connection.

## addDiscussionComment

Adds a comment to a Discussion, possibly as a reply to another comment.

### Input fields for `addDiscussionComment`

* `input` (AddDiscussionCommentInput!):

### Return fields for `addDiscussionComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `comment` (DiscussionComment): The newly created discussion comment.

## addDiscussionPollVote

Vote for an option in a discussion poll.

### Input fields for `addDiscussionPollVote`

* `input` (AddDiscussionPollVoteInput!):

### Return fields for `addDiscussionPollVote`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pollOption` (DiscussionPollOption): The poll option that a vote was added to.

## addEnterpriseOrganizationMember

Adds enterprise members to an organization within the enterprise.

### Input fields for `addEnterpriseOrganizationMember`

* `input` (AddEnterpriseOrganizationMemberInput!):

### Return fields for `addEnterpriseOrganizationMember`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `users` (\[User!]): The users who were added to the organization.

## addEnterpriseSupportEntitlement

Adds a support entitlement to an enterprise member.

### Input fields for `addEnterpriseSupportEntitlement`

* `input` (AddEnterpriseSupportEntitlementInput!):

### Return fields for `addEnterpriseSupportEntitlement`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `message` (String): A message confirming the result of adding the support entitlement.

## addLabelsToLabelable

Adds labels to a labelable object.

### Input fields for `addLabelsToLabelable`

* `input` (AddLabelsToLabelableInput!):

### Return fields for `addLabelsToLabelable`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `labelable` (Labelable): The item that was labeled.

## addProjectCard

Adds a card to a ProjectColumn. Either contentId or note must be provided but not both.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `addProjectCard`

* `input` (AddProjectCardInput!):

### Return fields for `addProjectCard`

* `cardEdge` (ProjectCardEdge): The edge from the ProjectColumn's card connection.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectColumn` (ProjectColumn): The ProjectColumn.

## addProjectColumn

Adds a column to a Project.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `addProjectColumn`

* `input` (AddProjectColumnInput!):

### Return fields for `addProjectColumn`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `columnEdge` (ProjectColumnEdge): The edge from the project's column connection.
* `project` (Project): The project.

## addProjectV2DraftIssue

Creates a new draft issue and add it to a Project.

### Input fields for `addProjectV2DraftIssue`

* `input` (AddProjectV2DraftIssueInput!):

### Return fields for `addProjectV2DraftIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectItem` (ProjectV2Item): The draft issue added to the project.

## addProjectV2ItemById

Links an existing content instance to a Project.

### Input fields for `addProjectV2ItemById`

* `input` (AddProjectV2ItemByIdInput!):

### Return fields for `addProjectV2ItemById`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `item` (ProjectV2Item): The item added to the project.

## addPullRequestReview

Adds a review to a Pull Request.

### Input fields for `addPullRequestReview`

* `input` (AddPullRequestReviewInput!):

### Return fields for `addPullRequestReview`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequestReview` (PullRequestReview): The newly created pull request review.
* `reviewEdge` (PullRequestReviewEdge): The edge from the pull request's review connection.

## addPullRequestReviewComment

Adds a comment to a review.

### Input fields for `addPullRequestReviewComment`

* `input` (AddPullRequestReviewCommentInput!):

### Return fields for `addPullRequestReviewComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `comment` (PullRequestReviewComment): The newly created comment.
* `commentEdge` (PullRequestReviewCommentEdge): The edge from the review's comment connection.

## addPullRequestReviewThread

Adds a new thread to a pending Pull Request Review.

### Input fields for `addPullRequestReviewThread`

* `input` (AddPullRequestReviewThreadInput!):

### Return fields for `addPullRequestReviewThread`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `thread` (PullRequestReviewThread): The newly created thread.

## addPullRequestReviewThreadReply

Adds a reply to an existing Pull Request Review Thread.

### Input fields for `addPullRequestReviewThreadReply`

* `input` (AddPullRequestReviewThreadReplyInput!):

### Return fields for `addPullRequestReviewThreadReply`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `comment` (PullRequestReviewComment): The newly created reply.

## addReaction

Adds a reaction to a subject.

### Input fields for `addReaction`

* `input` (AddReactionInput!):

### Return fields for `addReaction`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `reaction` (Reaction): The reaction object.
* `reactionGroups` (\[ReactionGroup!]): The reaction groups for the subject.
* `subject` (Reactable): The reactable subject.

## addStar

Adds a star to a Starrable.

### Input fields for `addStar`

* `input` (AddStarInput!):

### Return fields for `addStar`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `starrable` (Starrable): The starrable.

## addSubIssue

Adds a sub-issue to a given issue.

### Input fields for `addSubIssue`

* `input` (AddSubIssueInput!):

### Return fields for `addSubIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The parent issue that the sub-issue was added to.
* `subIssue` (Issue): The sub-issue of the parent.

## addUpvote

Add an upvote to a discussion or discussion comment.

### Input fields for `addUpvote`

* `input` (AddUpvoteInput!):

### Return fields for `addUpvote`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `subject` (Votable): The votable subject.

## addVerifiableDomain

Adds a verifiable domain to an owning account.

### Input fields for `addVerifiableDomain`

* `input` (AddVerifiableDomainInput!):

### Return fields for `addVerifiableDomain`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `domain` (VerifiableDomain): The verifiable domain that was added.

## approveDeployments

Approve all pending deployments under one or more environments.

### Input fields for `approveDeployments`

* `input` (ApproveDeploymentsInput!):

### Return fields for `approveDeployments`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `deployments` (\[Deployment!]): The affected deployments.

## approveVerifiableDomain

Approve a verifiable domain for notification delivery.

### Input fields for `approveVerifiableDomain`

* `input` (ApproveVerifiableDomainInput!):

### Return fields for `approveVerifiableDomain`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `domain` (VerifiableDomain): The verifiable domain that was approved.

## archiveProjectV2Item

Archives a ProjectV2Item.

### Input fields for `archiveProjectV2Item`

* `input` (ArchiveProjectV2ItemInput!):

### Return fields for `archiveProjectV2Item`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `item` (ProjectV2Item): The item archived from the project.

## archivePullRequest

Archive a pull request. Closes, locks, and marks the pull request as archived.
Only repository admins can archive pull requests.

### Input fields for `archivePullRequest`

* `input` (ArchivePullRequestInput!):

### Return fields for `archivePullRequest`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that was archived.

## archiveRepository

Marks a repository as archived.

### Input fields for `archiveRepository`

* `input` (ArchiveRepositoryInput!):

### Return fields for `archiveRepository`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The repository that was marked as archived.

## cancelEnterpriseAdminInvitation

Cancels a pending invitation for an administrator to join an enterprise.

### Input fields for `cancelEnterpriseAdminInvitation`

* `input` (CancelEnterpriseAdminInvitationInput!):

### Return fields for `cancelEnterpriseAdminInvitation`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `invitation` (EnterpriseAdministratorInvitation): The invitation that was canceled.
* `message` (String): A message confirming the result of canceling an administrator invitation.

## cancelEnterpriseMemberInvitation

Cancels a pending invitation for an unaffiliated member to join an enterprise.

### Input fields for `cancelEnterpriseMemberInvitation`

* `input` (CancelEnterpriseMemberInvitationInput!):

### Return fields for `cancelEnterpriseMemberInvitation`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `invitation` (EnterpriseMemberInvitation): The invitation that was canceled.
* `message` (String): A message confirming the result of canceling an member invitation.

## cancelSponsorship

Cancel an active sponsorship.

### Input fields for `cancelSponsorship`

* `input` (CancelSponsorshipInput!):

### Return fields for `cancelSponsorship`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `sponsorsTier` (SponsorsTier): The tier that was being used at the time of cancellation.

## changeUserStatus

Update your status on GitHub.

### Input fields for `changeUserStatus`

* `input` (ChangeUserStatusInput!):

### Return fields for `changeUserStatus`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `status` (UserStatus): Your updated status.

## clearLabelsFromLabelable

Clears all labels from a labelable object.

### Input fields for `clearLabelsFromLabelable`

* `input` (ClearLabelsFromLabelableInput!):

### Return fields for `clearLabelsFromLabelable`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `labelable` (Labelable): The item that was unlabeled.

## clearProjectV2ItemFieldValue

This mutation clears the value of a field for an item in a Project. Currently
only text, number, date, assignees, labels, single-select, iteration and
milestone fields are supported.

### Input fields for `clearProjectV2ItemFieldValue`

* `input` (ClearProjectV2ItemFieldValueInput!):

### Return fields for `clearProjectV2ItemFieldValue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2Item` (ProjectV2Item): The updated item.

## cloneProject

Creates a new project by cloning configuration from an existing project.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `cloneProject`

* `input` (CloneProjectInput!):

### Return fields for `cloneProject`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `jobStatusId` (String): The id of the JobStatus for populating cloned fields.
* `project` (Project): The new cloned project.

## cloneTemplateRepository

Create a new repository with the same files and directory structure as a template repository.

### Input fields for `cloneTemplateRepository`

* `input` (CloneTemplateRepositoryInput!):

### Return fields for `cloneTemplateRepository`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The new repository.

## closeDiscussion

Close a discussion.

### Input fields for `closeDiscussion`

* `input` (CloseDiscussionInput!):

### Return fields for `closeDiscussion`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `discussion` (Discussion): The discussion that was closed.

## closeIssue

Close an issue.

### Input fields for `closeIssue`

* `input` (CloseIssueInput!):

### Return fields for `closeIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue that was closed.

## closePullRequest

Close a pull request.

### Input fields for `closePullRequest`

* `input` (ClosePullRequestInput!):

### Return fields for `closePullRequest`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that was closed.

## convertProjectCardNoteToIssue

Convert a project note card to one associated with a newly created issue.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `convertProjectCardNoteToIssue`

* `input` (ConvertProjectCardNoteToIssueInput!):

### Return fields for `convertProjectCardNoteToIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectCard` (ProjectCard): The updated ProjectCard.

## convertProjectV2DraftIssueItemToIssue

Converts a projectV2 draft issue item to an issue.

### Input fields for `convertProjectV2DraftIssueItemToIssue`

* `input` (ConvertProjectV2DraftIssueItemToIssueInput!):

### Return fields for `convertProjectV2DraftIssueItemToIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `item` (ProjectV2Item): The updated project item.

## convertPullRequestToDraft

Converts a pull request to draft.

### Input fields for `convertPullRequestToDraft`

* `input` (ConvertPullRequestToDraftInput!):

### Return fields for `convertPullRequestToDraft`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that is now a draft.

## copyProjectV2

Copy a project.

### Input fields for `copyProjectV2`

* `input` (CopyProjectV2Input!):

### Return fields for `copyProjectV2`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2` (ProjectV2): The copied project.

## createAttributionInvitation

Invites a user to claim reattributable data.

### Input fields for `createAttributionInvitation`

* `input` (CreateAttributionInvitationInput!):

### Return fields for `createAttributionInvitation`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `owner` (Organization): The owner scoping the reattributable data.
* `source` (Claimable): The account owning the data to reattribute.
* `target` (Claimable): The account which may claim the data.

## createBranchProtectionRule

Create a new branch protection rule.

### Input fields for `createBranchProtectionRule`

* `input` (CreateBranchProtectionRuleInput!):

### Return fields for `createBranchProtectionRule`

* `branchProtectionRule` (BranchProtectionRule): The newly created BranchProtectionRule.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## createCheckRun

Create a check run.

### Input fields for `createCheckRun`

* `input` (CreateCheckRunInput!):

### Return fields for `createCheckRun`

* `checkRun` (CheckRun): The newly created check run.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## createCheckSuite

Create a check suite.

### Input fields for `createCheckSuite`

* `input` (CreateCheckSuiteInput!):

### Return fields for `createCheckSuite`

* `checkSuite` (CheckSuite): The newly created check suite.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## createCommitOnBranch

Appends a commit to the given branch as the authenticated user.
This mutation creates a commit whose parent is the HEAD of the provided
branch and also updates that branch to point to the new commit.
It can be thought of as similar to git commit.
Locating a Branch
Commits are appended to a branch of type Ref.
This must refer to a git branch (i.e.  the fully qualified path must
begin with refs/heads/, although including this prefix is optional.
Callers may specify the branch to commit to either by its global node
ID or by passing both of repositoryNameWithOwner and refName.  For
more details see the documentation for CommittableBranch.
Describing Changes
fileChanges are specified as a FilesChanges object describing
FileAdditions and FileDeletions.
Please see the documentation for FileChanges for more information on
how to use this argument to describe any set of file changes.
Authorship
Similar to the web commit interface, this mutation does not support
specifying the author or committer of the commit and will not add
support for this in the future.
A commit created by a successful execution of this mutation will be
authored by the owner of the credential which authenticates the API
request.  The committer will be identical to that of commits authored
using the web interface.
If you need full control over author and committer information, please
use the Git Database REST API instead.
Commit Signing
Commits made using this mutation are automatically signed by GitHub if
supported and will be marked as verified in the user interface.

### Input fields for `createCommitOnBranch`

* `input` (CreateCommitOnBranchInput!):

### Return fields for `createCommitOnBranch`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `commit` (Commit): The new commit.
* `ref` (Ref): The ref which has been updated to point to the new commit.

## createDeployment

Creates a new deployment event.

### Input fields for `createDeployment`

* `input` (CreateDeploymentInput!):

### Return fields for `createDeployment`

* `autoMerged` (Boolean): True if the default branch has been auto-merged into the deployment ref.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `deployment` (Deployment): The new deployment.

## createDeploymentStatus

Create a deployment status.

### Input fields for `createDeploymentStatus`

* `input` (CreateDeploymentStatusInput!):

### Return fields for `createDeploymentStatus`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `deploymentStatus` (DeploymentStatus): The new deployment status.

## createDiscussion

Create a discussion.

### Input fields for `createDiscussion`

* `input` (CreateDiscussionInput!):

### Return fields for `createDiscussion`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `discussion` (Discussion): The discussion that was just created.

## createEnterpriseOrganization

Creates an organization as part of an enterprise account. A personal access
token used to create an organization is implicitly permitted to update the
organization it created, if the organization is part of an enterprise that has
SAML enabled or uses Enterprise Managed Users. If the organization is not part
of such an enterprise, and instead has SAML enabled for it individually, the
token will then require SAML authorization to continue working against that organization.

### Input fields for `createEnterpriseOrganization`

* `input` (CreateEnterpriseOrganizationInput!):

### Return fields for `createEnterpriseOrganization`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise that owns the created organization.
* `organization` (Organization): The organization that was created.

## createEnvironment

Creates an environment or simply returns it if already exists.

### Input fields for `createEnvironment`

* `input` (CreateEnvironmentInput!):

### Return fields for `createEnvironment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `environment` (Environment): The new or existing environment.

## createIpAllowListEntry

Creates a new IP allow list entry.

### Input fields for `createIpAllowListEntry`

* `input` (CreateIpAllowListEntryInput!):

### Return fields for `createIpAllowListEntry`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `ipAllowListEntry` (IpAllowListEntry): The IP allow list entry that was created.

## createIssue

Creates a new issue.

### Input fields for `createIssue`

* `input` (CreateIssueInput!):

### Return fields for `createIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The new issue.

## createIssueField

Creates a new issue field.

### Input fields for `createIssueField`

* `input` (CreateIssueFieldInput!):

### Return fields for `createIssueField`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issueField` (IssueFields): The newly created issue field.

## createIssueFieldValue

Creates a new issue field value for an issue.

### Input fields for `createIssueFieldValue`

* `input` (CreateIssueFieldValueInput!):

### Return fields for `createIssueFieldValue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue object.
* `issueFieldValue` (IssueFieldValue): The newly created issue field value.

## createIssueType

Creates a new issue type.

### Input fields for `createIssueType`

* `input` (CreateIssueTypeInput!):

### Return fields for `createIssueType`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issueType` (IssueType): The newly created issue type.

## createLabel

Creates a new label.

### Input fields for `createLabel`

* `input` (CreateLabelInput!):

### Return fields for `createLabel`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `label` (Label): The new label.

## createLinkedBranch

Create a branch linked to an issue.

### Input fields for `createLinkedBranch`

* `input` (CreateLinkedBranchInput!):

### Return fields for `createLinkedBranch`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue that was linked to.
* `linkedBranch` (LinkedBranch): The new branch issue reference.

## createMigrationSource

Creates a GitHub Enterprise Importer (GEI) migration source.

### Input fields for `createMigrationSource`

* `input` (CreateMigrationSourceInput!):

### Return fields for `createMigrationSource`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `migrationSource` (MigrationSource): The created migration source.

## createProject

Creates a new project.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `createProject`

* `input` (CreateProjectInput!):

### Return fields for `createProject`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `project` (Project): The new project.

## createProjectV2

Creates a new project.

### Input fields for `createProjectV2`

* `input` (CreateProjectV2Input!):

### Return fields for `createProjectV2`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2` (ProjectV2): The new project.

## createProjectV2Field

Create a new project field.

### Input fields for `createProjectV2Field`

* `input` (CreateProjectV2FieldInput!):

### Return fields for `createProjectV2Field`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2Field` (ProjectV2FieldConfiguration): The new field.

## createProjectV2IssueField

Create a new project issue field.

### Input fields for `createProjectV2IssueField`

* `input` (CreateProjectV2IssueFieldInput!):

### Return fields for `createProjectV2IssueField`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2Field` (ProjectV2FieldConfiguration): The new field.

## createProjectV2StatusUpdate

Creates a status update within a Project.

### Input fields for `createProjectV2StatusUpdate`

* `input` (CreateProjectV2StatusUpdateInput!):

### Return fields for `createProjectV2StatusUpdate`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `statusUpdate` (ProjectV2StatusUpdate): The status update updated in the project.

## createPullRequest

Create a new pull request.

### Input fields for `createPullRequest`

* `input` (CreatePullRequestInput!):

### Return fields for `createPullRequest`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The new pull request.

## createRef

Create a new Git Ref.

### Input fields for `createRef`

* `input` (CreateRefInput!):

### Return fields for `createRef`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `ref` (Ref): The newly created ref.

## createRepository

Create a new repository.

### Input fields for `createRepository`

* `input` (CreateRepositoryInput!):

### Return fields for `createRepository`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The new repository.

## createRepositoryCustomProperty

Create a repository custom property.

### Input fields for `createRepositoryCustomProperty`

* `input` (CreateRepositoryCustomPropertyInput!):

### Return fields for `createRepositoryCustomProperty`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repositoryCustomProperty` (RepositoryCustomProperty): The newly created repository custom property.

## createRepositoryRuleset

Create a repository ruleset.

### Input fields for `createRepositoryRuleset`

* `input` (CreateRepositoryRulesetInput!):

### Return fields for `createRepositoryRuleset`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `ruleset` (RepositoryRuleset): The newly created Ruleset.

## createSponsorsListing

Create a GitHub Sponsors profile to allow others to sponsor you or your organization.

### Input fields for `createSponsorsListing`

* `input` (CreateSponsorsListingInput!):

### Return fields for `createSponsorsListing`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `sponsorsListing` (SponsorsListing): The new GitHub Sponsors profile.

## createSponsorsTier

Create a new payment tier for your GitHub Sponsors profile.

### Input fields for `createSponsorsTier`

* `input` (CreateSponsorsTierInput!):

### Return fields for `createSponsorsTier`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `sponsorsTier` (SponsorsTier): The new tier.

## createSponsorship

Start a new sponsorship of a maintainer in GitHub Sponsors, or reactivate a past sponsorship.

### Input fields for `createSponsorship`

* `input` (CreateSponsorshipInput!):

### Return fields for `createSponsorship`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `sponsorship` (Sponsorship): The sponsorship that was started.

## createSponsorships

Make many sponsorships for different sponsorable users or organizations at
once. Can only sponsor those who have a public GitHub Sponsors profile.

### Input fields for `createSponsorships`

* `input` (CreateSponsorshipsInput!):

### Return fields for `createSponsorships`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `sponsorables` (\[Sponsorable!]): The users and organizations who received a sponsorship.

## createUserList

Creates a new user list.

### Input fields for `createUserList`

* `input` (CreateUserListInput!):

### Return fields for `createUserList`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `list` (UserList): The list that was just created.
* `viewer` (User): The user who created the list.

## declineTopicSuggestion

Rejects a suggested topic for the repository.

### Input fields for `declineTopicSuggestion`

* `input` (DeclineTopicSuggestionInput!):

### Return fields for `declineTopicSuggestion`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `topic` (Topic): The declined topic. **Deprecated:** Suggested topics are no longer supported Removal on 2024-04-01 UTC.

## deleteBranchProtectionRule

Delete a branch protection rule.

### Input fields for `deleteBranchProtectionRule`

* `input` (DeleteBranchProtectionRuleInput!):

### Return fields for `deleteBranchProtectionRule`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## deleteDeployment

Deletes a deployment.

### Input fields for `deleteDeployment`

* `input` (DeleteDeploymentInput!):

### Return fields for `deleteDeployment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## deleteDiscussion

Delete a discussion and all of its replies.

### Input fields for `deleteDiscussion`

* `input` (DeleteDiscussionInput!):

### Return fields for `deleteDiscussion`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `discussion` (Discussion): The discussion that was just deleted.

## deleteDiscussionComment

Delete a discussion comment. If it has replies, wipe it instead.

### Input fields for `deleteDiscussionComment`

* `input` (DeleteDiscussionCommentInput!):

### Return fields for `deleteDiscussionComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `comment` (DiscussionComment): The discussion comment that was just deleted.

## deleteEnvironment

Deletes an environment.

### Input fields for `deleteEnvironment`

* `input` (DeleteEnvironmentInput!):

### Return fields for `deleteEnvironment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## deleteIpAllowListEntry

Deletes an IP allow list entry.

### Input fields for `deleteIpAllowListEntry`

* `input` (DeleteIpAllowListEntryInput!):

### Return fields for `deleteIpAllowListEntry`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `ipAllowListEntry` (IpAllowListEntry): The IP allow list entry that was deleted.

## deleteIssue

Deletes an Issue object.

### Input fields for `deleteIssue`

* `input` (DeleteIssueInput!):

### Return fields for `deleteIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The repository the issue belonged to.

## deleteIssueComment

Deletes an IssueComment object.

### Input fields for `deleteIssueComment`

* `input` (DeleteIssueCommentInput!):

### Return fields for `deleteIssueComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## deleteIssueField

Deletes an issue field.

### Input fields for `deleteIssueField`

* `input` (DeleteIssueFieldInput!):

### Return fields for `deleteIssueField`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issueField` (IssueFields): The deleted issue field.

## deleteIssueFieldValue

Deletes an issue field value from an issue.

### Input fields for `deleteIssueFieldValue`

* `input` (DeleteIssueFieldValueInput!):

### Return fields for `deleteIssueFieldValue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue object.
* `success` (Boolean): Whether the field value was successfully deleted.

## deleteIssueType

Delete an issue type.

### Input fields for `deleteIssueType`

* `input` (DeleteIssueTypeInput!):

### Return fields for `deleteIssueType`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `deletedIssueTypeId` (ID): The ID of the deleted issue type.

## deleteLabel

Deletes a label.

### Input fields for `deleteLabel`

* `input` (DeleteLabelInput!):

### Return fields for `deleteLabel`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## deleteLinkedBranch

Unlink a branch from an issue.

### Input fields for `deleteLinkedBranch`

* `input` (DeleteLinkedBranchInput!):

### Return fields for `deleteLinkedBranch`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue the linked branch was unlinked from.

## deletePackageVersion

Delete a package version.

### Input fields for `deletePackageVersion`

* `input` (DeletePackageVersionInput!):

### Return fields for `deletePackageVersion`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `success` (Boolean): Whether or not the operation succeeded.

## deleteProject

Deletes a project.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `deleteProject`

* `input` (DeleteProjectInput!):

### Return fields for `deleteProject`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `owner` (ProjectOwner): The repository or organization the project was removed from.

## deleteProjectCard

Deletes a project card.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `deleteProjectCard`

* `input` (DeleteProjectCardInput!):

### Return fields for `deleteProjectCard`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `column` (ProjectColumn): The column the deleted card was in.
* `deletedCardId` (ID): The deleted card ID.

## deleteProjectColumn

Deletes a project column.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `deleteProjectColumn`

* `input` (DeleteProjectColumnInput!):

### Return fields for `deleteProjectColumn`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `deletedColumnId` (ID): The deleted column ID.
* `project` (Project): The project the deleted column was in.

## deleteProjectV2

Delete a project.

### Input fields for `deleteProjectV2`

* `input` (DeleteProjectV2Input!):

### Return fields for `deleteProjectV2`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2` (ProjectV2): The deleted Project.

## deleteProjectV2Field

Delete a project field.

### Input fields for `deleteProjectV2Field`

* `input` (DeleteProjectV2FieldInput!):

### Return fields for `deleteProjectV2Field`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2Field` (ProjectV2FieldConfiguration): The deleted field.

## deleteProjectV2Item

Deletes an item from a Project.

### Input fields for `deleteProjectV2Item`

* `input` (DeleteProjectV2ItemInput!):

### Return fields for `deleteProjectV2Item`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `deletedItemId` (ID): The ID of the deleted item.

## deleteProjectV2StatusUpdate

Deletes a project status update.

### Input fields for `deleteProjectV2StatusUpdate`

* `input` (DeleteProjectV2StatusUpdateInput!):

### Return fields for `deleteProjectV2StatusUpdate`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `deletedStatusUpdateId` (ID): The ID of the deleted status update.
* `projectV2` (ProjectV2): The project the deleted status update was in.

## deleteProjectV2Workflow

Deletes a project workflow.

### Input fields for `deleteProjectV2Workflow`

* `input` (DeleteProjectV2WorkflowInput!):

### Return fields for `deleteProjectV2Workflow`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `deletedWorkflowId` (ID): The ID of the deleted workflow.
* `projectV2` (ProjectV2): The project the deleted workflow was in.

## deletePullRequestReview

Deletes a pull request review.

### Input fields for `deletePullRequestReview`

* `input` (DeletePullRequestReviewInput!):

### Return fields for `deletePullRequestReview`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequestReview` (PullRequestReview): The deleted pull request review.

## deletePullRequestReviewComment

Deletes a pull request review comment.

### Input fields for `deletePullRequestReviewComment`

* `input` (DeletePullRequestReviewCommentInput!):

### Return fields for `deletePullRequestReviewComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequestReview` (PullRequestReview): The pull request review the deleted comment belonged to.
* `pullRequestReviewComment` (PullRequestReviewComment): The deleted pull request review comment.

## deleteRef

Delete a Git Ref.

### Input fields for `deleteRef`

* `input` (DeleteRefInput!):

### Return fields for `deleteRef`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## deleteRepositoryCustomProperty

Delete a repository custom property.

### Input fields for `deleteRepositoryCustomProperty`

* `input` (DeleteRepositoryCustomPropertyInput!):

### Return fields for `deleteRepositoryCustomProperty`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repositoryCustomProperty` (RepositoryCustomProperty): The deleted custom property.

## deleteRepositoryRuleset

Delete a repository ruleset.

### Input fields for `deleteRepositoryRuleset`

* `input` (DeleteRepositoryRulesetInput!):

### Return fields for `deleteRepositoryRuleset`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## deleteUserList

Deletes a user list.

### Input fields for `deleteUserList`

* `input` (DeleteUserListInput!):

### Return fields for `deleteUserList`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `user` (User): The owner of the list that will be deleted.

## deleteVerifiableDomain

Deletes a verifiable domain.

### Input fields for `deleteVerifiableDomain`

* `input` (DeleteVerifiableDomainInput!):

### Return fields for `deleteVerifiableDomain`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `owner` (VerifiableDomainOwner): The owning account from which the domain was deleted.

## dequeuePullRequest

Remove a pull request from the merge queue.

### Input fields for `dequeuePullRequest`

* `input` (DequeuePullRequestInput!):

### Return fields for `dequeuePullRequest`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `mergeQueueEntry` (MergeQueueEntry): The merge queue entry of the dequeued pull request.

## disablePullRequestAutoMerge

Disable auto merge on the given pull request.

### Input fields for `disablePullRequestAutoMerge`

* `input` (DisablePullRequestAutoMergeInput!):

### Return fields for `disablePullRequestAutoMerge`

* `actor` (Actor): Identifies the actor who performed the event.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request auto merge was disabled on.

## dismissPullRequestReview

Dismisses an approved or rejected pull request review.

### Input fields for `dismissPullRequestReview`

* `input` (DismissPullRequestReviewInput!):

### Return fields for `dismissPullRequestReview`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequestReview` (PullRequestReview): The dismissed pull request review.

## dismissRepositoryVulnerabilityAlert

Dismisses the Dependabot alert.

### Input fields for `dismissRepositoryVulnerabilityAlert`

* `input` (DismissRepositoryVulnerabilityAlertInput!):

### Return fields for `dismissRepositoryVulnerabilityAlert`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repositoryVulnerabilityAlert` (RepositoryVulnerabilityAlert): The Dependabot alert that was dismissed.

## enablePullRequestAutoMerge

Enable the default auto-merge on a pull request.

### Input fields for `enablePullRequestAutoMerge`

* `input` (EnablePullRequestAutoMergeInput!):

### Return fields for `enablePullRequestAutoMerge`

* `actor` (Actor): Identifies the actor who performed the event.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request auto-merge was enabled on.

## enqueuePullRequest

Add a pull request to the merge queue.

### Input fields for `enqueuePullRequest`

* `input` (EnqueuePullRequestInput!):

### Return fields for `enqueuePullRequest`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `mergeQueueEntry` (MergeQueueEntry): The merge queue entry for the enqueued pull request.

## followOrganization

Follow an organization.

### Input fields for `followOrganization`

* `input` (FollowOrganizationInput!):

### Return fields for `followOrganization`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `organization` (Organization): The organization that was followed.

## followUser

Follow a user.

### Input fields for `followUser`

* `input` (FollowUserInput!):

### Return fields for `followUser`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `user` (User): The user that was followed.

## grantEnterpriseOrganizationsMigratorRole

Grant the migrator role to a user for all organizations under an enterprise account.

### Input fields for `grantEnterpriseOrganizationsMigratorRole`

* `input` (GrantEnterpriseOrganizationsMigratorRoleInput!):

### Return fields for `grantEnterpriseOrganizationsMigratorRole`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `organizations` (OrganizationConnection): The organizations that had the migrator role applied to for the given user.

## grantMigratorRole

Grant the migrator role to a user or a team.

### Input fields for `grantMigratorRole`

* `input` (GrantMigratorRoleInput!):

### Return fields for `grantMigratorRole`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `success` (Boolean): Did the operation succeed?.

## importProject

Creates a new project by importing columns and a list of issues/PRs.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `importProject`

* `input` (ImportProjectInput!):

### Return fields for `importProject`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `project` (Project): The new Project!.

## inviteEnterpriseAdmin

Invite someone to become an administrator of the enterprise.

### Input fields for `inviteEnterpriseAdmin`

* `input` (InviteEnterpriseAdminInput!):

### Return fields for `inviteEnterpriseAdmin`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `invitation` (EnterpriseAdministratorInvitation): The created enterprise administrator invitation.

## inviteEnterpriseMember

Invite someone to become an unaffiliated member of the enterprise.

### Input fields for `inviteEnterpriseMember`

* `input` (InviteEnterpriseMemberInput!):

### Return fields for `inviteEnterpriseMember`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `invitation` (EnterpriseMemberInvitation): The created enterprise member invitation.

## linkProjectV2ToRepository

Links a project to a repository.

### Input fields for `linkProjectV2ToRepository`

* `input` (LinkProjectV2ToRepositoryInput!):

### Return fields for `linkProjectV2ToRepository`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The repository the project is linked to.

## linkProjectV2ToTeam

Links a project to a team.

### Input fields for `linkProjectV2ToTeam`

* `input` (LinkProjectV2ToTeamInput!):

### Return fields for `linkProjectV2ToTeam`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `team` (Team): The team the project is linked to.

## linkRepositoryToProject

Creates a repository link for a project.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `linkRepositoryToProject`

* `input` (LinkRepositoryToProjectInput!):

### Return fields for `linkRepositoryToProject`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `project` (Project): The linked Project.
* `repository` (Repository): The linked Repository.

## lockLockable

Lock a lockable object.

### Input fields for `lockLockable`

* `input` (LockLockableInput!):

### Return fields for `lockLockable`

* `actor` (Actor): Identifies the actor who performed the event.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `lockedRecord` (Lockable): The item that was locked.

## markDiscussionCommentAsAnswer

Mark a discussion comment as the chosen answer for discussions in an answerable category.

### Input fields for `markDiscussionCommentAsAnswer`

* `input` (MarkDiscussionCommentAsAnswerInput!):

### Return fields for `markDiscussionCommentAsAnswer`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `discussion` (Discussion): The discussion that includes the chosen comment.

## markFileAsViewed

Mark a pull request file as viewed.

### Input fields for `markFileAsViewed`

* `input` (MarkFileAsViewedInput!):

### Return fields for `markFileAsViewed`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The updated pull request.

## markProjectV2AsTemplate

Mark a project as a template. Note that only projects which are owned by an Organization can be marked as a template.

### Input fields for `markProjectV2AsTemplate`

* `input` (MarkProjectV2AsTemplateInput!):

### Return fields for `markProjectV2AsTemplate`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2` (ProjectV2): The project.

## markPullRequestReadyForReview

Marks a pull request ready for review.

### Input fields for `markPullRequestReadyForReview`

* `input` (MarkPullRequestReadyForReviewInput!):

### Return fields for `markPullRequestReadyForReview`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that is ready for review.

## mergeBranch

Merge a head into a branch.

### Input fields for `mergeBranch`

* `input` (MergeBranchInput!):

### Return fields for `mergeBranch`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `mergeCommit` (Commit): The resulting merge Commit.

## mergePullRequest

Merge a pull request.

### Input fields for `mergePullRequest`

* `input` (MergePullRequestInput!):

### Return fields for `mergePullRequest`

* `actor` (Actor): Identifies the actor who performed the event.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that was merged.

## minimizeComment

Minimizes a comment on an Issue, Commit, Pull Request, or Gist.

### Input fields for `minimizeComment`

* `input` (MinimizeCommentInput!):

### Return fields for `minimizeComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `minimizedComment` (Minimizable): The comment that was minimized.

## moveProjectCard

Moves a project card to another place.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `moveProjectCard`

* `input` (MoveProjectCardInput!):

### Return fields for `moveProjectCard`

* `cardEdge` (ProjectCardEdge): The new edge of the moved card.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## moveProjectColumn

Moves a project column to another place.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `moveProjectColumn`

* `input` (MoveProjectColumnInput!):

### Return fields for `moveProjectColumn`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `columnEdge` (ProjectColumnEdge): The new edge of the moved column.

## pinEnvironment

Pin an environment to a repository.

### Input fields for `pinEnvironment`

* `input` (PinEnvironmentInput!):

### Return fields for `pinEnvironment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `environment` (Environment): The environment that was pinned.
* `pinnedEnvironment` (PinnedEnvironment): The pinned environment if we pinned.

## pinIssue

Pin an issue to a repository.

### Input fields for `pinIssue`

* `input` (PinIssueInput!):

### Return fields for `pinIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue that was pinned.

## pinIssueComment

Pins an Issue Comment.

### Input fields for `pinIssueComment`

* `input` (PinIssueCommentInput!):

### Return fields for `pinIssueComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issueComment` (IssueComment): The Issue Comment that was pinned.

## promoteRepositoryCustomProperty

Promote a repository custom property to the enterprise level.

### Input fields for `promoteRepositoryCustomProperty`

* `input` (PromoteRepositoryCustomPropertyInput!):

### Return fields for `promoteRepositoryCustomProperty`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repositoryCustomProperty` (RepositoryCustomProperty): The repository custom property that has been promoted.

## publishSponsorsTier

Publish an existing sponsorship tier that is currently still a draft to a GitHub Sponsors profile.

### Input fields for `publishSponsorsTier`

* `input` (PublishSponsorsTierInput!):

### Return fields for `publishSponsorsTier`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `sponsorsTier` (SponsorsTier): The tier that was published.

## regenerateEnterpriseIdentityProviderRecoveryCodes

Regenerates the identity provider recovery codes for an enterprise.

### Input fields for `regenerateEnterpriseIdentityProviderRecoveryCodes`

* `input` (RegenerateEnterpriseIdentityProviderRecoveryCodesInput!):

### Return fields for `regenerateEnterpriseIdentityProviderRecoveryCodes`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `identityProvider` (EnterpriseIdentityProvider): The identity provider for the enterprise.

## regenerateVerifiableDomainToken

Regenerates a verifiable domain's verification token.

### Input fields for `regenerateVerifiableDomainToken`

* `input` (RegenerateVerifiableDomainTokenInput!):

### Return fields for `regenerateVerifiableDomainToken`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `verificationToken` (String): The verification token that was generated.

## rejectDeployments

Reject all pending deployments under one or more environments.

### Input fields for `rejectDeployments`

* `input` (RejectDeploymentsInput!):

### Return fields for `rejectDeployments`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `deployments` (\[Deployment!]): The affected deployments.

## removeAssigneesFromAssignable

Removes assignees from an assignable object.

### Input fields for `removeAssigneesFromAssignable`

* `input` (RemoveAssigneesFromAssignableInput!):

### Return fields for `removeAssigneesFromAssignable`

* `assignable` (Assignable): The item that was unassigned.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## removeBlockedBy

Removes a 'blocked by' relationship from an issue.

### Input fields for `removeBlockedBy`

* `input` (RemoveBlockedByInput!):

### Return fields for `removeBlockedBy`

* `blockingIssue` (Issue): The previously blocking issue.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The previously blocked issue.

## removeEnterpriseAdmin

Removes an administrator from the enterprise.

### Input fields for `removeEnterpriseAdmin`

* `input` (RemoveEnterpriseAdminInput!):

### Return fields for `removeEnterpriseAdmin`

* `admin` (User): The user who was removed as an administrator.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The updated enterprise.
* `message` (String): A message confirming the result of removing an administrator.
* `viewer` (User): The viewer performing the mutation.

## removeEnterpriseIdentityProvider

Removes the identity provider from an enterprise. Owners of enterprises both
with and without Enterprise Managed Users may use this mutation.

### Input fields for `removeEnterpriseIdentityProvider`

* `input` (RemoveEnterpriseIdentityProviderInput!):

### Return fields for `removeEnterpriseIdentityProvider`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `identityProvider` (EnterpriseIdentityProvider): The identity provider that was removed from the enterprise.

## removeEnterpriseMember

Completely removes a user from the enterprise.

### Input fields for `removeEnterpriseMember`

* `input` (RemoveEnterpriseMemberInput!):

### Return fields for `removeEnterpriseMember`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The updated enterprise.
* `user` (User): The user that was removed from the enterprise.
* `viewer` (User): The viewer performing the mutation.

## removeEnterpriseOrganization

Removes an organization from the enterprise.

### Input fields for `removeEnterpriseOrganization`

* `input` (RemoveEnterpriseOrganizationInput!):

### Return fields for `removeEnterpriseOrganization`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The updated enterprise.
* `organization` (Organization): The organization that was removed from the enterprise.
* `viewer` (User): The viewer performing the mutation.

## removeEnterpriseSupportEntitlement

Removes a support entitlement from an enterprise member.

### Input fields for `removeEnterpriseSupportEntitlement`

* `input` (RemoveEnterpriseSupportEntitlementInput!):

### Return fields for `removeEnterpriseSupportEntitlement`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `message` (String): A message confirming the result of removing the support entitlement.

## removeLabelsFromLabelable

Removes labels from a Labelable object.

### Input fields for `removeLabelsFromLabelable`

* `input` (RemoveLabelsFromLabelableInput!):

### Return fields for `removeLabelsFromLabelable`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `labelable` (Labelable): The Labelable the labels were removed from.

## removeOutsideCollaborator

Removes outside collaborator from all repositories in an organization.

### Input fields for `removeOutsideCollaborator`

* `input` (RemoveOutsideCollaboratorInput!):

### Return fields for `removeOutsideCollaborator`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `removedUser` (User): The user that was removed as an outside collaborator.

## removeReaction

Removes a reaction from a subject.

### Input fields for `removeReaction`

* `input` (RemoveReactionInput!):

### Return fields for `removeReaction`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `reaction` (Reaction): The reaction object.
* `reactionGroups` (\[ReactionGroup!]): The reaction groups for the subject.
* `subject` (Reactable): The reactable subject.

## removeStar

Removes a star from a Starrable.

### Input fields for `removeStar`

* `input` (RemoveStarInput!):

### Return fields for `removeStar`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `starrable` (Starrable): The starrable.

## removeSubIssue

Removes a sub-issue from a given issue.

### Input fields for `removeSubIssue`

* `input` (RemoveSubIssueInput!):

### Return fields for `removeSubIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The parent of the sub-issue.
* `subIssue` (Issue): The sub-issue of the parent.

## removeUpvote

Remove an upvote to a discussion or discussion comment.

### Input fields for `removeUpvote`

* `input` (RemoveUpvoteInput!):

### Return fields for `removeUpvote`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `subject` (Votable): The votable subject.

## reopenDiscussion

Reopen a discussion.

### Input fields for `reopenDiscussion`

* `input` (ReopenDiscussionInput!):

### Return fields for `reopenDiscussion`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `discussion` (Discussion): The discussion that was reopened.

## reopenIssue

Reopen a issue.

### Input fields for `reopenIssue`

* `input` (ReopenIssueInput!):

### Return fields for `reopenIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue that was opened.

## reopenPullRequest

Reopen a pull request.

### Input fields for `reopenPullRequest`

* `input` (ReopenPullRequestInput!):

### Return fields for `reopenPullRequest`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that was reopened.

## reorderEnvironment

Reorder a pinned repository environment.

### Input fields for `reorderEnvironment`

* `input` (ReorderEnvironmentInput!):

### Return fields for `reorderEnvironment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `environment` (Environment): The environment that was reordered.

## replaceActorsForAssignable

Replaces all actors for assignable object.

### Input fields for `replaceActorsForAssignable`

* `input` (ReplaceActorsForAssignableInput!):

### Return fields for `replaceActorsForAssignable`

* `assignable` (Assignable): The item that was assigned.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## reprioritizeSubIssue

Reprioritizes a sub-issue to a different position in the parent list.

### Input fields for `reprioritizeSubIssue`

* `input` (ReprioritizeSubIssueInput!):

### Return fields for `reprioritizeSubIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The parent issue that the sub-issue was reprioritized in.

## requestReviews

Set review requests on a pull request.

### Input fields for `requestReviews`

* `input` (RequestReviewsInput!):

### Return fields for `requestReviews`

* `actor` (Actor): Identifies the actor who performed the event.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that is getting requests.
* `requestedReviewersEdge` (UserEdge): The edge from the pull request to the requested reviewers.

## requestReviewsByLogin

Set review requests on a pull request using login strings instead of IDs.

### Input fields for `requestReviewsByLogin`

* `input` (RequestReviewsByLoginInput!):

### Return fields for `requestReviewsByLogin`

* `actor` (Actor): Identifies the actor who performed the event.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that is getting requests.
* `requestedReviewersEdge` (UserEdge): The edge from the pull request to the requested reviewers.

## rerequestCheckSuite

Rerequests an existing check suite.

### Input fields for `rerequestCheckSuite`

* `input` (RerequestCheckSuiteInput!):

### Return fields for `rerequestCheckSuite`

* `checkSuite` (CheckSuite): The requested check suite.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## resolveReviewThread

Marks a review thread as resolved.

### Input fields for `resolveReviewThread`

* `input` (ResolveReviewThreadInput!):

### Return fields for `resolveReviewThread`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `thread` (PullRequestReviewThread): The thread to resolve.

## retireSponsorsTier

Retire a published payment tier from your GitHub Sponsors profile so it cannot be used to start new sponsorships.

### Input fields for `retireSponsorsTier`

* `input` (RetireSponsorsTierInput!):

### Return fields for `retireSponsorsTier`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `sponsorsTier` (SponsorsTier): The tier that was retired.

## revertPullRequest

Create a pull request that reverts the changes from a merged pull request.

### Input fields for `revertPullRequest`

* `input` (RevertPullRequestInput!):

### Return fields for `revertPullRequest`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that was reverted.
* `revertPullRequest` (PullRequest): The new pull request that reverts the input pull request.

## revokeEnterpriseOrganizationsMigratorRole

Revoke the migrator role to a user for all organizations under an enterprise account.

### Input fields for `revokeEnterpriseOrganizationsMigratorRole`

* `input` (RevokeEnterpriseOrganizationsMigratorRoleInput!):

### Return fields for `revokeEnterpriseOrganizationsMigratorRole`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `organizations` (OrganizationConnection): The organizations that had the migrator role revoked for the given user.

## revokeMigratorRole

Revoke the migrator role from a user or a team.

### Input fields for `revokeMigratorRole`

* `input` (RevokeMigratorRoleInput!):

### Return fields for `revokeMigratorRole`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `success` (Boolean): Did the operation succeed?.

## setEnterpriseIdentityProvider

Creates or updates the identity provider for an enterprise.

### Input fields for `setEnterpriseIdentityProvider`

* `input` (SetEnterpriseIdentityProviderInput!):

### Return fields for `setEnterpriseIdentityProvider`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `identityProvider` (EnterpriseIdentityProvider): The identity provider for the enterprise.

## setIssueFieldValue

Sets the value of an IssueFieldValue.

### Input fields for `setIssueFieldValue`

* `input` (SetIssueFieldValueInput!):

### Return fields for `setIssueFieldValue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue where the field values were set.
* `issueFieldValues` (\[IssueFieldValue!]): The issue field values that were created or updated.

## setOrganizationInteractionLimit

Set an organization level interaction limit for an organization's public repositories.

### Input fields for `setOrganizationInteractionLimit`

* `input` (SetOrganizationInteractionLimitInput!):

### Return fields for `setOrganizationInteractionLimit`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `organization` (Organization): The organization that the interaction limit was set for.

## setRepositoryCustomPropertyValues

Set repository custom property values for a repository.

### Input fields for `setRepositoryCustomPropertyValues`

* `input` (SetRepositoryCustomPropertyValuesInput!):

### Return fields for `setRepositoryCustomPropertyValues`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The repository that the custom properties were set for.

## setRepositoryInteractionLimit

Sets an interaction limit setting for a repository.

### Input fields for `setRepositoryInteractionLimit`

* `input` (SetRepositoryInteractionLimitInput!):

### Return fields for `setRepositoryInteractionLimit`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The repository that the interaction limit was set for.

## setUserInteractionLimit

Set a user level interaction limit for an user's public repositories.

### Input fields for `setUserInteractionLimit`

* `input` (SetUserInteractionLimitInput!):

### Return fields for `setUserInteractionLimit`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `user` (User): The user that the interaction limit was set for.

## startOrganizationMigration

Starts a GitHub Enterprise Importer organization migration.

### Input fields for `startOrganizationMigration`

* `input` (StartOrganizationMigrationInput!):

### Return fields for `startOrganizationMigration`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `orgMigration` (OrganizationMigration): The new organization migration.

## startRepositoryMigration

Starts a GitHub Enterprise Importer (GEI) repository migration.

### Input fields for `startRepositoryMigration`

* `input` (StartRepositoryMigrationInput!):

### Return fields for `startRepositoryMigration`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repositoryMigration` (RepositoryMigration): The new repository migration.

## submitPullRequestReview

Submits a pending pull request review.

### Input fields for `submitPullRequestReview`

* `input` (SubmitPullRequestReviewInput!):

### Return fields for `submitPullRequestReview`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequestReview` (PullRequestReview): The submitted pull request review.

## transferEnterpriseOrganization

Transfer an organization from one enterprise to another enterprise.

### Input fields for `transferEnterpriseOrganization`

* `input` (TransferEnterpriseOrganizationInput!):

### Return fields for `transferEnterpriseOrganization`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `organization` (Organization): The organization for which a transfer was initiated.

## transferIssue

Transfer an issue to a different repository.

### Input fields for `transferIssue`

* `input` (TransferIssueInput!):

### Return fields for `transferIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue that was transferred.

## unarchiveProjectV2Item

Unarchives a ProjectV2Item.

### Input fields for `unarchiveProjectV2Item`

* `input` (UnarchiveProjectV2ItemInput!):

### Return fields for `unarchiveProjectV2Item`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `item` (ProjectV2Item): The item unarchived from the project.

## unarchivePullRequest

Unarchive a pull request. Removes the archived flag from the pull request.
Does not automatically reopen or unlock the pull request. Only repository
admins can unarchive pull requests.

### Input fields for `unarchivePullRequest`

* `input` (UnarchivePullRequestInput!):

### Return fields for `unarchivePullRequest`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The pull request that was unarchived.

## unarchiveRepository

Unarchives a repository.

### Input fields for `unarchiveRepository`

* `input` (UnarchiveRepositoryInput!):

### Return fields for `unarchiveRepository`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The repository that was unarchived.

## unfollowOrganization

Unfollow an organization.

### Input fields for `unfollowOrganization`

* `input` (UnfollowOrganizationInput!):

### Return fields for `unfollowOrganization`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `organization` (Organization): The organization that was unfollowed.

## unfollowUser

Unfollow a user.

### Input fields for `unfollowUser`

* `input` (UnfollowUserInput!):

### Return fields for `unfollowUser`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `user` (User): The user that was unfollowed.

## unlinkProjectV2FromRepository

Unlinks a project from a repository.

### Input fields for `unlinkProjectV2FromRepository`

* `input` (UnlinkProjectV2FromRepositoryInput!):

### Return fields for `unlinkProjectV2FromRepository`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The repository the project is no longer linked to.

## unlinkProjectV2FromTeam

Unlinks a project to a team.

### Input fields for `unlinkProjectV2FromTeam`

* `input` (UnlinkProjectV2FromTeamInput!):

### Return fields for `unlinkProjectV2FromTeam`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `team` (Team): The team the project is unlinked from.

## unlinkRepositoryFromProject

Deletes a repository link from a project.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `unlinkRepositoryFromProject`

* `input` (UnlinkRepositoryFromProjectInput!):

### Return fields for `unlinkRepositoryFromProject`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `project` (Project): The linked Project.
* `repository` (Repository): The linked Repository.

## unlockLockable

Unlock a lockable object.

### Input fields for `unlockLockable`

* `input` (UnlockLockableInput!):

### Return fields for `unlockLockable`

* `actor` (Actor): Identifies the actor who performed the event.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `unlockedRecord` (Lockable): The item that was unlocked.

## unmarkDiscussionCommentAsAnswer

Unmark a discussion comment as the chosen answer for discussions in an answerable category.

### Input fields for `unmarkDiscussionCommentAsAnswer`

* `input` (UnmarkDiscussionCommentAsAnswerInput!):

### Return fields for `unmarkDiscussionCommentAsAnswer`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `discussion` (Discussion): The discussion that includes the comment.

## unmarkFileAsViewed

Unmark a pull request file as viewed.

### Input fields for `unmarkFileAsViewed`

* `input` (UnmarkFileAsViewedInput!):

### Return fields for `unmarkFileAsViewed`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The updated pull request.

## unmarkIssueAsDuplicate

Unmark an issue as a duplicate of another issue.

### Input fields for `unmarkIssueAsDuplicate`

* `input` (UnmarkIssueAsDuplicateInput!):

### Return fields for `unmarkIssueAsDuplicate`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `duplicate` (IssueOrPullRequest): The issue or pull request that was marked as a duplicate.

## unmarkProjectV2AsTemplate

Unmark a project as a template.

### Input fields for `unmarkProjectV2AsTemplate`

* `input` (UnmarkProjectV2AsTemplateInput!):

### Return fields for `unmarkProjectV2AsTemplate`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2` (ProjectV2): The project.

## unminimizeComment

Unminimizes a comment on an Issue, Commit, Pull Request, or Gist.

### Input fields for `unminimizeComment`

* `input` (UnminimizeCommentInput!):

### Return fields for `unminimizeComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `unminimizedComment` (Minimizable): The comment that was unminimized.

## unpinIssue

Unpin a pinned issue from a repository.

### Input fields for `unpinIssue`

* `input` (UnpinIssueInput!):

### Return fields for `unpinIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `id` (ID): The id of the pinned issue that was unpinned.
* `issue` (Issue): The issue that was unpinned.

## unpinIssueComment

Unpins an Issue Comment.

### Input fields for `unpinIssueComment`

* `input` (UnpinIssueCommentInput!):

### Return fields for `unpinIssueComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issueComment` (IssueComment): The Issue Comment that was unpinned.

## unresolveReviewThread

Marks a review thread as unresolved.

### Input fields for `unresolveReviewThread`

* `input` (UnresolveReviewThreadInput!):

### Return fields for `unresolveReviewThread`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `thread` (PullRequestReviewThread): The thread to resolve.

## updateBranchProtectionRule

Update a branch protection rule.

### Input fields for `updateBranchProtectionRule`

* `input` (UpdateBranchProtectionRuleInput!):

### Return fields for `updateBranchProtectionRule`

* `branchProtectionRule` (BranchProtectionRule): The newly created BranchProtectionRule.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## updateCheckRun

Update a check run.

### Input fields for `updateCheckRun`

* `input` (UpdateCheckRunInput!):

### Return fields for `updateCheckRun`

* `checkRun` (CheckRun): The updated check run.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## updateCheckSuitePreferences

Modifies the settings of an existing check suite.

### Input fields for `updateCheckSuitePreferences`

* `input` (UpdateCheckSuitePreferencesInput!):

### Return fields for `updateCheckSuitePreferences`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The updated repository.

## updateDiscussion

Update a discussion.

### Input fields for `updateDiscussion`

* `input` (UpdateDiscussionInput!):

### Return fields for `updateDiscussion`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `discussion` (Discussion): The modified discussion.

## updateDiscussionComment

Update the contents of a comment on a Discussion.

### Input fields for `updateDiscussionComment`

* `input` (UpdateDiscussionCommentInput!):

### Return fields for `updateDiscussionComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `comment` (DiscussionComment): The modified discussion comment.

## updateEnterpriseAdministratorRole

Updates the role of an enterprise administrator.

### Input fields for `updateEnterpriseAdministratorRole`

* `input` (UpdateEnterpriseAdministratorRoleInput!):

### Return fields for `updateEnterpriseAdministratorRole`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `message` (String): A message confirming the result of changing the administrator's role.

## updateEnterpriseAllowPrivateRepositoryForkingSetting

Sets whether private repository forks are enabled for an enterprise.

### Input fields for `updateEnterpriseAllowPrivateRepositoryForkingSetting`

* `input` (UpdateEnterpriseAllowPrivateRepositoryForkingSettingInput!):

### Return fields for `updateEnterpriseAllowPrivateRepositoryForkingSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated allow private repository forking setting.
* `message` (String): A message confirming the result of updating the allow private repository forking setting.

## updateEnterpriseDefaultRepositoryPermissionSetting

Sets the base repository permission for organizations in an enterprise.

### Input fields for `updateEnterpriseDefaultRepositoryPermissionSetting`

* `input` (UpdateEnterpriseDefaultRepositoryPermissionSettingInput!):

### Return fields for `updateEnterpriseDefaultRepositoryPermissionSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated base repository permission setting.
* `message` (String): A message confirming the result of updating the base repository permission setting.

## updateEnterpriseDeployKeySetting

Sets whether deploy keys are allowed to be created and used for an enterprise.

### Input fields for `updateEnterpriseDeployKeySetting`

* `input` (UpdateEnterpriseDeployKeySettingInput!):

### Return fields for `updateEnterpriseDeployKeySetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated deploy key setting.
* `message` (String): A message confirming the result of updating the deploy key setting.

## updateEnterpriseMembersCanChangeRepositoryVisibilitySetting

Sets whether organization members with admin permissions on a repository can change repository visibility.

### Input fields for `updateEnterpriseMembersCanChangeRepositoryVisibilitySetting`

* `input` (UpdateEnterpriseMembersCanChangeRepositoryVisibilitySettingInput!):

### Return fields for `updateEnterpriseMembersCanChangeRepositoryVisibilitySetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated members can change repository visibility setting.
* `message` (String): A message confirming the result of updating the members can change repository visibility setting.

## updateEnterpriseMembersCanCreateRepositoriesSetting

Sets the members can create repositories setting for an enterprise.

### Input fields for `updateEnterpriseMembersCanCreateRepositoriesSetting`

* `input` (UpdateEnterpriseMembersCanCreateRepositoriesSettingInput!):

### Return fields for `updateEnterpriseMembersCanCreateRepositoriesSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated members can create repositories setting.
* `message` (String): A message confirming the result of updating the members can create repositories setting.

## updateEnterpriseMembersCanDeleteIssuesSetting

Sets the members can delete issues setting for an enterprise.

### Input fields for `updateEnterpriseMembersCanDeleteIssuesSetting`

* `input` (UpdateEnterpriseMembersCanDeleteIssuesSettingInput!):

### Return fields for `updateEnterpriseMembersCanDeleteIssuesSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated members can delete issues setting.
* `message` (String): A message confirming the result of updating the members can delete issues setting.

## updateEnterpriseMembersCanDeleteRepositoriesSetting

Sets the members can delete repositories setting for an enterprise.

### Input fields for `updateEnterpriseMembersCanDeleteRepositoriesSetting`

* `input` (UpdateEnterpriseMembersCanDeleteRepositoriesSettingInput!):

### Return fields for `updateEnterpriseMembersCanDeleteRepositoriesSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated members can delete repositories setting.
* `message` (String): A message confirming the result of updating the members can delete repositories setting.

## updateEnterpriseMembersCanInviteCollaboratorsSetting

Sets whether members can invite collaborators are enabled for an enterprise.

### Input fields for `updateEnterpriseMembersCanInviteCollaboratorsSetting`

* `input` (UpdateEnterpriseMembersCanInviteCollaboratorsSettingInput!):

### Return fields for `updateEnterpriseMembersCanInviteCollaboratorsSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated members can invite collaborators setting.
* `message` (String): A message confirming the result of updating the members can invite collaborators setting.

## updateEnterpriseMembersCanMakePurchasesSetting

Sets whether or not an organization owner can make purchases.

### Input fields for `updateEnterpriseMembersCanMakePurchasesSetting`

* `input` (UpdateEnterpriseMembersCanMakePurchasesSettingInput!):

### Return fields for `updateEnterpriseMembersCanMakePurchasesSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated members can make purchases setting.
* `message` (String): A message confirming the result of updating the members can make purchases setting.

## updateEnterpriseMembersCanUpdateProtectedBranchesSetting

Sets the members can update protected branches setting for an enterprise.

### Input fields for `updateEnterpriseMembersCanUpdateProtectedBranchesSetting`

* `input` (UpdateEnterpriseMembersCanUpdateProtectedBranchesSettingInput!):

### Return fields for `updateEnterpriseMembersCanUpdateProtectedBranchesSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated members can update protected branches setting.
* `message` (String): A message confirming the result of updating the members can update protected branches setting.

## updateEnterpriseMembersCanViewDependencyInsightsSetting

Sets the members can view dependency insights for an enterprise.

### Input fields for `updateEnterpriseMembersCanViewDependencyInsightsSetting`

* `input` (UpdateEnterpriseMembersCanViewDependencyInsightsSettingInput!):

### Return fields for `updateEnterpriseMembersCanViewDependencyInsightsSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated members can view dependency insights setting.
* `message` (String): A message confirming the result of updating the members can view dependency insights setting.

## updateEnterpriseOrganizationProjectsSetting

Sets whether organization projects are enabled for an enterprise.

### Input fields for `updateEnterpriseOrganizationProjectsSetting`

* `input` (UpdateEnterpriseOrganizationProjectsSettingInput!):

### Return fields for `updateEnterpriseOrganizationProjectsSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated organization projects setting.
* `message` (String): A message confirming the result of updating the organization projects setting.

## updateEnterpriseOwnerOrganizationRole

Updates the role of an enterprise owner with an organization.

### Input fields for `updateEnterpriseOwnerOrganizationRole`

* `input` (UpdateEnterpriseOwnerOrganizationRoleInput!):

### Return fields for `updateEnterpriseOwnerOrganizationRole`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `message` (String): A message confirming the result of changing the owner's organization role.

## updateEnterpriseProfile

Updates an enterprise's profile.

### Input fields for `updateEnterpriseProfile`

* `input` (UpdateEnterpriseProfileInput!):

### Return fields for `updateEnterpriseProfile`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The updated enterprise.

## updateEnterpriseRepositoryProjectsSetting

Sets whether repository projects are enabled for a enterprise.

### Input fields for `updateEnterpriseRepositoryProjectsSetting`

* `input` (UpdateEnterpriseRepositoryProjectsSettingInput!):

### Return fields for `updateEnterpriseRepositoryProjectsSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated repository projects setting.
* `message` (String): A message confirming the result of updating the repository projects setting.

## updateEnterpriseTwoFactorAuthenticationDisallowedMethodsSetting

Sets the two-factor authentication methods that users of an enterprise may not use.

### Input fields for `updateEnterpriseTwoFactorAuthenticationDisallowedMethodsSetting`

* `input` (UpdateEnterpriseTwoFactorAuthenticationDisallowedMethodsSettingInput!):

### Return fields for `updateEnterpriseTwoFactorAuthenticationDisallowedMethodsSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated two-factor authentication disallowed methods setting.
* `message` (String): A message confirming the result of updating the two-factor authentication disallowed methods setting.

## updateEnterpriseTwoFactorAuthenticationRequiredSetting

Sets whether two factor authentication is required for all users in an enterprise.

### Input fields for `updateEnterpriseTwoFactorAuthenticationRequiredSetting`

* `input` (UpdateEnterpriseTwoFactorAuthenticationRequiredSettingInput!):

### Return fields for `updateEnterpriseTwoFactorAuthenticationRequiredSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `enterprise` (Enterprise): The enterprise with the updated two factor authentication required setting.
* `message` (String): A message confirming the result of updating the two factor authentication required setting.

## updateEnvironment

Updates an environment.

### Input fields for `updateEnvironment`

* `input` (UpdateEnvironmentInput!):

### Return fields for `updateEnvironment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `environment` (Environment): The updated environment.

## updateIpAllowListEnabledSetting

Sets whether an IP allow list is enabled on an owner.

### Input fields for `updateIpAllowListEnabledSetting`

* `input` (UpdateIpAllowListEnabledSettingInput!):

### Return fields for `updateIpAllowListEnabledSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `owner` (IpAllowListOwner): The IP allow list owner on which the setting was updated.

## updateIpAllowListEntry

Updates an IP allow list entry.

### Input fields for `updateIpAllowListEntry`

* `input` (UpdateIpAllowListEntryInput!):

### Return fields for `updateIpAllowListEntry`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `ipAllowListEntry` (IpAllowListEntry): The IP allow list entry that was updated.

## updateIpAllowListForInstalledAppsEnabledSetting

Sets whether IP allow list configuration for installed GitHub Apps is enabled on an owner.

### Input fields for `updateIpAllowListForInstalledAppsEnabledSetting`

* `input` (UpdateIpAllowListForInstalledAppsEnabledSettingInput!):

### Return fields for `updateIpAllowListForInstalledAppsEnabledSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `owner` (IpAllowListOwner): The IP allow list owner on which the setting was updated.

## updateIpAllowListUserLevelEnforcementEnabledSetting

Sets whether IP allow list user-level enforcement is enabled on an enterprise.

### Input fields for `updateIpAllowListUserLevelEnforcementEnabledSetting`

* `input` (UpdateIpAllowListUserLevelEnforcementEnabledSettingInput!):

### Return fields for `updateIpAllowListUserLevelEnforcementEnabledSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `owner` (IpAllowListOwner): The IP allow list owner on which the setting was updated.

## updateIssue

Updates an Issue.

### Input fields for `updateIssue`

* `input` (UpdateIssueInput!):

### Return fields for `updateIssue`

* `actor` (Actor): Identifies the actor who performed the event.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue.

## updateIssueComment

Updates an IssueComment object.

### Input fields for `updateIssueComment`

* `input` (UpdateIssueCommentInput!):

### Return fields for `updateIssueComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issueComment` (IssueComment): The updated comment.

## updateIssueField

Updates an issue field.

### Input fields for `updateIssueField`

* `input` (UpdateIssueFieldInput!):

### Return fields for `updateIssueField`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issueField` (IssueFields): The updated issue field.

## updateIssueFieldValue

Updates an existing issue field value for an issue.

### Input fields for `updateIssueFieldValue`

* `input` (UpdateIssueFieldValueInput!):

### Return fields for `updateIssueFieldValue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The issue object.
* `issueFieldValue` (IssueFieldValue): The updated issue field value.

## updateIssueIssueType

Updates the issue type on an issue.

### Input fields for `updateIssueIssueType`

* `input` (UpdateIssueIssueTypeInput!):

### Return fields for `updateIssueIssueType`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issue` (Issue): The updated issue.

## updateIssueType

Update an issue type.

### Input fields for `updateIssueType`

* `input` (UpdateIssueTypeInput!):

### Return fields for `updateIssueType`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `issueType` (IssueType): The updated issue type.

## updateLabel

Updates an existing label.

### Input fields for `updateLabel`

* `input` (UpdateLabelInput!):

### Return fields for `updateLabel`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `label` (Label): The updated label.

## updateNotificationRestrictionSetting

Update the setting to restrict notifications to only verified or approved domains available to an owner.

### Input fields for `updateNotificationRestrictionSetting`

* `input` (UpdateNotificationRestrictionSettingInput!):

### Return fields for `updateNotificationRestrictionSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `owner` (VerifiableDomainOwner): The owner on which the setting was updated.

## updateOrganizationAllowPrivateRepositoryForkingSetting

Sets whether private repository forks are enabled for an organization.

### Input fields for `updateOrganizationAllowPrivateRepositoryForkingSetting`

* `input` (UpdateOrganizationAllowPrivateRepositoryForkingSettingInput!):

### Return fields for `updateOrganizationAllowPrivateRepositoryForkingSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `message` (String): A message confirming the result of updating the allow private repository forking setting.
* `organization` (Organization): The organization with the updated allow private repository forking setting.

## updateOrganizationWebCommitSignoffSetting

Sets whether contributors are required to sign off on web-based commits for repositories in an organization.

### Input fields for `updateOrganizationWebCommitSignoffSetting`

* `input` (UpdateOrganizationWebCommitSignoffSettingInput!):

### Return fields for `updateOrganizationWebCommitSignoffSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `message` (String): A message confirming the result of updating the web commit signoff setting.
* `organization` (Organization): The organization with the updated web commit signoff setting.

## updatePatreonSponsorability

Toggle the setting for your GitHub Sponsors profile that allows other GitHub
accounts to sponsor you on GitHub while paying for the sponsorship on Patreon.
Only applicable when you have a GitHub Sponsors profile and have connected
your GitHub account with Patreon.

### Input fields for `updatePatreonSponsorability`

* `input` (UpdatePatreonSponsorabilityInput!):

### Return fields for `updatePatreonSponsorability`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `sponsorsListing` (SponsorsListing): The GitHub Sponsors profile.

## updateProject

Updates an existing project.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `updateProject`

* `input` (UpdateProjectInput!):

### Return fields for `updateProject`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `project` (Project): The updated project.

## updateProjectCard

Updates an existing project card.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `updateProjectCard`

* `input` (UpdateProjectCardInput!):

### Return fields for `updateProjectCard`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectCard` (ProjectCard): The updated ProjectCard.

## updateProjectColumn

Updates an existing project column.

> \[!WARNING]
> **Deprecation notice:** Projects (classic) is being deprecated in favor of the new Projects experience, see: <https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/>. Removal on 2025-04-01 UTC.

### Input fields for `updateProjectColumn`

* `input` (UpdateProjectColumnInput!):

### Return fields for `updateProjectColumn`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectColumn` (ProjectColumn): The updated project column.

## updateProjectV2

Updates an existing project.

### Input fields for `updateProjectV2`

* `input` (UpdateProjectV2Input!):

### Return fields for `updateProjectV2`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2` (ProjectV2): The updated Project.

## updateProjectV2Collaborators

Update the collaborators on a team or a project.

### Input fields for `updateProjectV2Collaborators`

* `input` (UpdateProjectV2CollaboratorsInput!):

### Return fields for `updateProjectV2Collaborators`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `collaborators` (ProjectV2ActorConnection): The collaborators granted a role.

## updateProjectV2DraftIssue

Updates a draft issue within a Project.

### Input fields for `updateProjectV2DraftIssue`

* `input` (UpdateProjectV2DraftIssueInput!):

### Return fields for `updateProjectV2DraftIssue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `draftIssue` (DraftIssue): The draft issue updated in the project.

## updateProjectV2Field

Update a project field.

### Input fields for `updateProjectV2Field`

* `input` (UpdateProjectV2FieldInput!):

### Return fields for `updateProjectV2Field`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2Field` (ProjectV2FieldConfiguration): The updated field.

## updateProjectV2ItemFieldValue

This mutation updates the value of a field for an item in a Project. Currently
only single-select, text, number, date, and iteration fields are supported.

### Input fields for `updateProjectV2ItemFieldValue`

* `input` (UpdateProjectV2ItemFieldValueInput!):

### Return fields for `updateProjectV2ItemFieldValue`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `projectV2Item` (ProjectV2Item): The updated item.

## updateProjectV2ItemPosition

This mutation updates the position of the item in the project, where the position represents the priority of an item.

### Input fields for `updateProjectV2ItemPosition`

* `input` (UpdateProjectV2ItemPositionInput!):

### Return fields for `updateProjectV2ItemPosition`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `items` (ProjectV2ItemConnection): The items in the new order.

## updateProjectV2StatusUpdate

Updates a status update within a Project.

### Input fields for `updateProjectV2StatusUpdate`

* `input` (UpdateProjectV2StatusUpdateInput!):

### Return fields for `updateProjectV2StatusUpdate`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `statusUpdate` (ProjectV2StatusUpdate): The status update updated in the project.

## updatePullRequest

Update a pull request.

### Input fields for `updatePullRequest`

* `input` (UpdatePullRequestInput!):

### Return fields for `updatePullRequest`

* `actor` (Actor): Identifies the actor who performed the event.
* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The updated pull request.

## updatePullRequestBranch

Merge or Rebase HEAD from upstream branch into pull request branch.

### Input fields for `updatePullRequestBranch`

* `input` (UpdatePullRequestBranchInput!):

### Return fields for `updatePullRequestBranch`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequest` (PullRequest): The updated pull request.

## updatePullRequestReview

Updates the body of a pull request review.

### Input fields for `updatePullRequestReview`

* `input` (UpdatePullRequestReviewInput!):

### Return fields for `updatePullRequestReview`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequestReview` (PullRequestReview): The updated pull request review.

## updatePullRequestReviewComment

Updates a pull request review comment.

### Input fields for `updatePullRequestReviewComment`

* `input` (UpdatePullRequestReviewCommentInput!):

### Return fields for `updatePullRequestReviewComment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `pullRequestReviewComment` (PullRequestReviewComment): The updated comment.

## updateRef

Update a Git Ref.

### Input fields for `updateRef`

* `input` (UpdateRefInput!):

### Return fields for `updateRef`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `ref` (Ref): The updated Ref.

## updateRefs

Creates, updates and/or deletes multiple refs in a repository.
This mutation takes a list of RefUpdates and performs these updates
on the repository. All updates are performed atomically, meaning that
if one of them is rejected, no other ref will be modified.
RefUpdate.beforeOid specifies that the given reference needs to point
to the given value before performing any updates. A value of
0000000000000000000000000000000000000000 can be used to verify that
the references should not exist.
RefUpdate.afterOid specifies the value that the given reference
will point to after performing all updates. A value of
0000000000000000000000000000000000000000 can be used to delete a
reference.
If RefUpdate.force is set to true, a non-fast-forward updates
for the given reference will be allowed.

### Input fields for `updateRefs`

* `input` (UpdateRefsInput!):

### Return fields for `updateRefs`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.

## updateRepository

Update information about a repository.

### Input fields for `updateRepository`

* `input` (UpdateRepositoryInput!):

### Return fields for `updateRepository`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The updated repository.

## updateRepositoryCustomProperty

Update a repository custom property.

### Input fields for `updateRepositoryCustomProperty`

* `input` (UpdateRepositoryCustomPropertyInput!):

### Return fields for `updateRepositoryCustomProperty`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repositoryCustomProperty` (RepositoryCustomProperty): The updated repository custom property.

## updateRepositoryRuleset

Update a repository ruleset.

### Input fields for `updateRepositoryRuleset`

* `input` (UpdateRepositoryRulesetInput!):

### Return fields for `updateRepositoryRuleset`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `ruleset` (RepositoryRuleset): The newly created Ruleset.

## updateRepositoryWebCommitSignoffSetting

Sets whether contributors are required to sign off on web-based commits for a repository.

### Input fields for `updateRepositoryWebCommitSignoffSetting`

* `input` (UpdateRepositoryWebCommitSignoffSettingInput!):

### Return fields for `updateRepositoryWebCommitSignoffSetting`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `message` (String): A message confirming the result of updating the web commit signoff setting.
* `repository` (Repository): The updated repository.

## updateSponsorshipPreferences

Change visibility of your sponsorship and opt in or out of email updates from the maintainer.

### Input fields for `updateSponsorshipPreferences`

* `input` (UpdateSponsorshipPreferencesInput!):

### Return fields for `updateSponsorshipPreferences`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `sponsorship` (Sponsorship): The sponsorship that was updated.

## updateSubscription

Updates the state for subscribable subjects.

### Input fields for `updateSubscription`

* `input` (UpdateSubscriptionInput!):

### Return fields for `updateSubscription`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `subscribable` (Subscribable): The input subscribable entity.

## updateTeamReviewAssignment

Updates team review assignment.

### Input fields for `updateTeamReviewAssignment`

* `input` (UpdateTeamReviewAssignmentInput!):

### Return fields for `updateTeamReviewAssignment`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `team` (Team): The team that was modified.

## updateTeamsRepository

Update team repository.

### Input fields for `updateTeamsRepository`

* `input` (UpdateTeamsRepositoryInput!):

### Return fields for `updateTeamsRepository`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `repository` (Repository): The repository that was updated.
* `teams` (\[Team!]): The teams granted permission on the repository.

## updateTopics

Replaces the repository's topics with the given topics.

### Input fields for `updateTopics`

* `input` (UpdateTopicsInput!):

### Return fields for `updateTopics`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `invalidTopicNames` (\[String!]): Names of the provided topics that are not valid.
* `repository` (Repository): The updated repository.

## updateUserList

Updates an existing user list.

### Input fields for `updateUserList`

* `input` (UpdateUserListInput!):

### Return fields for `updateUserList`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `list` (UserList): The list that was just updated.

## updateUserListsForItem

Updates which of the viewer's lists an item belongs to.

### Input fields for `updateUserListsForItem`

* `input` (UpdateUserListsForItemInput!):

### Return fields for `updateUserListsForItem`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `item` (UserListItems): The item that was added.
* `lists` (\[UserList!]): The lists to which this item belongs.
* `user` (User): The user who owns the lists.

## verifyVerifiableDomain

Verify that a verifiable domain has the expected DNS record.

### Input fields for `verifyVerifiableDomain`

* `input` (VerifyVerifiableDomainInput!):

### Return fields for `verifyVerifiableDomain`

* `clientMutationId` (String): A unique identifier for the client performing the mutation.
* `domain` (VerifiableDomain): The verifiable domain that was verified.