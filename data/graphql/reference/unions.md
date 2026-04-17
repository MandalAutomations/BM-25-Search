# Unions

A union is a type of object representing many objects.

## About unions

A [union](https://spec.graphql.org/June2018/#sec-Unions) is a type of object representing many objects.

For example, a field marked as an [`ProjectCardItem`](/en/graphql/reference/unions#projectcarditem) could be an [`Issue`](/en/graphql/reference/objects#issue) or a [`PullRequest`](/en/graphql/reference/objects#pullrequest) because each of those objects can be inside a project card. Using a union instead of an object gives you flexibility.

For more information, see [Introduction to GraphQL](/en/graphql/guides/introduction-to-graphql).

## Assignee

Types that can be assigned to issues.

### Possible types for `Assignee`

* Bot
* Mannequin
* Organization
* User

## AuditEntryActor

Types that can initiate an audit log event.

### Possible types for `AuditEntryActor`

* Bot
* Organization
* User

## BranchActorAllowanceActor

Types which can be actors for BranchActorAllowance objects.

### Possible types for `BranchActorAllowanceActor`

* App
* Team
* User

## BypassActor

Types that can represent a repository ruleset bypass actor.

### Possible types for `BypassActor`

* App
* Team
* User

## Claimable

An object which can have its data claimed or claim data from another.

### Possible types for `Claimable`

* Mannequin
* User

## Closer

The object which triggered a ClosedEvent.

### Possible types for `Closer`

* Commit
* ProjectV2
* PullRequest

## CreatedIssueOrRestrictedContribution

Represents either a issue the viewer can access or a restricted contribution.

### Possible types for `CreatedIssueOrRestrictedContribution`

* CreatedIssueContribution
* RestrictedContribution

## CreatedPullRequestOrRestrictedContribution

Represents either a pull request the viewer can access or a restricted contribution.

### Possible types for `CreatedPullRequestOrRestrictedContribution`

* CreatedPullRequestContribution
* RestrictedContribution

## CreatedRepositoryOrRestrictedContribution

Represents either a repository the viewer can access or a restricted contribution.

### Possible types for `CreatedRepositoryOrRestrictedContribution`

* CreatedRepositoryContribution
* RestrictedContribution

## CustomPropertySource

Sources which can have custom properties defined.

### Possible types for `CustomPropertySource`

* Enterprise
* Organization

## DeploymentReviewer

Users and teams.

### Possible types for `DeploymentReviewer`

* Team
* User

## EnterpriseMember

An object that is a member of an enterprise.

### Possible types for `EnterpriseMember`

* EnterpriseUserAccount
* User

## IpAllowListOwner

Types that can own an IP allow list.

### Possible types for `IpAllowListOwner`

* App
* Enterprise
* Organization

## IssueFieldValue

Issue field values.

### Possible types for `IssueFieldValue`

* IssueFieldDateValue
* IssueFieldNumberValue
* IssueFieldSingleSelectValue
* IssueFieldTextValue

## IssueFields

Possible issue fields.

### Possible types for `IssueFields`

* IssueFieldDate
* IssueFieldNumber
* IssueFieldSingleSelect
* IssueFieldText

## IssueOrPullRequest

Used for return value of Repository.issueOrPullRequest.

### Possible types for `IssueOrPullRequest`

* Issue
* PullRequest

## IssueTimelineItem

An item in an issue timeline.

### Possible types for `IssueTimelineItem`

* AssignedEvent
* ClosedEvent
* Commit
* CrossReferencedEvent
* DemilestonedEvent
* IssueComment
* LabeledEvent
* LockedEvent
* MilestonedEvent
* ReferencedEvent
* RenamedTitleEvent
* ReopenedEvent
* SubscribedEvent
* TransferredEvent
* UnassignedEvent
* UnlabeledEvent
* UnlockedEvent
* UnsubscribedEvent
* UserBlockedEvent

## IssueTimelineItems

An item in an issue timeline.

### Possible types for `IssueTimelineItems`

* AddedToProjectEvent
* AddedToProjectV2Event
* AssignedEvent
* BlockedByAddedEvent
* BlockedByRemovedEvent
* BlockingAddedEvent
* BlockingRemovedEvent
* ClosedEvent
* CommentDeletedEvent
* ConnectedEvent
* ConvertedFromDraftEvent
* ConvertedNoteToIssueEvent
* ConvertedToDiscussionEvent
* CrossReferencedEvent
* DemilestonedEvent
* DisconnectedEvent
* IssueComment
* IssueCommentPinnedEvent
* IssueCommentUnpinnedEvent
* IssueFieldAddedEvent
* IssueFieldChangedEvent
* IssueFieldRemovedEvent
* IssueTypeAddedEvent
* IssueTypeChangedEvent
* IssueTypeRemovedEvent
* LabeledEvent
* LockedEvent
* MarkedAsDuplicateEvent
* MentionedEvent
* MilestonedEvent
* MovedColumnsInProjectEvent
* ParentIssueAddedEvent
* ParentIssueRemovedEvent
* PinnedEvent
* ProjectV2ItemStatusChangedEvent
* ReferencedEvent
* RemovedFromProjectEvent
* RemovedFromProjectV2Event
* RenamedTitleEvent
* ReopenedEvent
* SubIssueAddedEvent
* SubIssueRemovedEvent
* SubscribedEvent
* TransferredEvent
* UnassignedEvent
* UnlabeledEvent
* UnlockedEvent
* UnmarkedAsDuplicateEvent
* UnpinnedEvent
* UnsubscribedEvent
* UserBlockedEvent

## MilestoneItem

Types that can be inside a Milestone.

### Possible types for `MilestoneItem`

* Issue
* PullRequest

## OrgRestoreMemberAuditEntryMembership

Types of memberships that can be restored for an Organization member.

### Possible types for `OrgRestoreMemberAuditEntryMembership`

* OrgRestoreMemberMembershipOrganizationAuditEntryData
* OrgRestoreMemberMembershipRepositoryAuditEntryData
* OrgRestoreMemberMembershipTeamAuditEntryData

## OrganizationAuditEntry

An audit entry in an organization audit log.

### Possible types for `OrganizationAuditEntry`

* MembersCanDeleteReposClearAuditEntry
* MembersCanDeleteReposDisableAuditEntry
* MembersCanDeleteReposEnableAuditEntry
* OauthApplicationCreateAuditEntry
* OrgAddBillingManagerAuditEntry
* OrgAddMemberAuditEntry
* OrgBlockUserAuditEntry
* OrgConfigDisableCollaboratorsOnlyAuditEntry
* OrgConfigEnableCollaboratorsOnlyAuditEntry
* OrgCreateAuditEntry
* OrgDisableOauthAppRestrictionsAuditEntry
* OrgDisableSamlAuditEntry
* OrgDisableTwoFactorRequirementAuditEntry
* OrgEnableOauthAppRestrictionsAuditEntry
* OrgEnableSamlAuditEntry
* OrgEnableTwoFactorRequirementAuditEntry
* OrgInviteMemberAuditEntry
* OrgInviteToBusinessAuditEntry
* OrgOauthAppAccessApprovedAuditEntry
* OrgOauthAppAccessBlockedAuditEntry
* OrgOauthAppAccessDeniedAuditEntry
* OrgOauthAppAccessRequestedAuditEntry
* OrgOauthAppAccessUnblockedAuditEntry
* OrgRemoveBillingManagerAuditEntry
* OrgRemoveMemberAuditEntry
* OrgRemoveOutsideCollaboratorAuditEntry
* OrgRestoreMemberAuditEntry
* OrgUnblockUserAuditEntry
* OrgUpdateDefaultRepositoryPermissionAuditEntry
* OrgUpdateMemberAuditEntry
* OrgUpdateMemberRepositoryCreationPermissionAuditEntry
* OrgUpdateMemberRepositoryInvitationPermissionAuditEntry
* PrivateRepositoryForkingDisableAuditEntry
* PrivateRepositoryForkingEnableAuditEntry
* RepoAccessAuditEntry
* RepoAddMemberAuditEntry
* RepoAddTopicAuditEntry
* RepoArchivedAuditEntry
* RepoChangeMergeSettingAuditEntry
* RepoConfigDisableAnonymousGitAccessAuditEntry
* RepoConfigDisableCollaboratorsOnlyAuditEntry
* RepoConfigDisableContributorsOnlyAuditEntry
* RepoConfigDisableSockpuppetDisallowedAuditEntry
* RepoConfigEnableAnonymousGitAccessAuditEntry
* RepoConfigEnableCollaboratorsOnlyAuditEntry
* RepoConfigEnableContributorsOnlyAuditEntry
* RepoConfigEnableSockpuppetDisallowedAuditEntry
* RepoConfigLockAnonymousGitAccessAuditEntry
* RepoConfigUnlockAnonymousGitAccessAuditEntry
* RepoCreateAuditEntry
* RepoDestroyAuditEntry
* RepoRemoveMemberAuditEntry
* RepoRemoveTopicAuditEntry
* RepositoryVisibilityChangeDisableAuditEntry
* RepositoryVisibilityChangeEnableAuditEntry
* TeamAddMemberAuditEntry
* TeamAddRepositoryAuditEntry
* TeamChangeParentTeamAuditEntry
* TeamRemoveMemberAuditEntry
* TeamRemoveRepositoryAuditEntry

## OrganizationOrUser

Used for argument of CreateProjectV2 mutation.

### Possible types for `OrganizationOrUser`

* Organization
* User

## PermissionGranter

Types that can grant permissions on a repository to a user.

### Possible types for `PermissionGranter`

* Organization
* Repository
* Team

## PinnableItem

Types that can be pinned to a profile page.

### Possible types for `PinnableItem`

* Gist
* Repository

## ProjectCardItem

Types that can be inside Project Cards.

### Possible types for `ProjectCardItem`

* Issue
* PullRequest

## ProjectV2Actor

Possible collaborators for a project.

### Possible types for `ProjectV2Actor`

* Team
* User

## ProjectV2FieldConfiguration

Configurations for project fields.

### Possible types for `ProjectV2FieldConfiguration`

* ProjectV2Field
* ProjectV2IterationField
* ProjectV2SingleSelectField

## ProjectV2IssueFieldValues

Possible issue field values for a Project item.

### Possible types for `ProjectV2IssueFieldValues`

* IssueFieldDateValue
* IssueFieldNumberValue
* IssueFieldSingleSelectValue
* IssueFieldTextValue

## ProjectV2ItemContent

Types that can be inside Project Items.

### Possible types for `ProjectV2ItemContent`

* DraftIssue
* Issue
* PullRequest

## ProjectV2ItemFieldValue

Project field values.

### Possible types for `ProjectV2ItemFieldValue`

* ProjectV2ItemFieldDateValue
* ProjectV2ItemFieldIterationValue
* ProjectV2ItemFieldLabelValue
* ProjectV2ItemFieldMilestoneValue
* ProjectV2ItemFieldNumberValue
* ProjectV2ItemFieldPullRequestValue
* ProjectV2ItemFieldRepositoryValue
* ProjectV2ItemFieldReviewerValue
* ProjectV2ItemFieldSingleSelectValue
* ProjectV2ItemFieldTextValue
* ProjectV2ItemFieldUserValue
* ProjectV2ItemIssueFieldValue

## PullRequestTimelineItem

An item in a pull request timeline.

### Possible types for `PullRequestTimelineItem`

* AssignedEvent
* BaseRefDeletedEvent
* BaseRefForcePushedEvent
* ClosedEvent
* Commit
* CommitCommentThread
* CrossReferencedEvent
* DemilestonedEvent
* DeployedEvent
* DeploymentEnvironmentChangedEvent
* HeadRefDeletedEvent
* HeadRefForcePushedEvent
* HeadRefRestoredEvent
* IssueComment
* LabeledEvent
* LockedEvent
* MergedEvent
* MilestonedEvent
* PullRequestReview
* PullRequestReviewComment
* PullRequestReviewThread
* ReferencedEvent
* RenamedTitleEvent
* ReopenedEvent
* ReviewDismissedEvent
* ReviewRequestRemovedEvent
* ReviewRequestedEvent
* SubscribedEvent
* UnassignedEvent
* UnlabeledEvent
* UnlockedEvent
* UnsubscribedEvent
* UserBlockedEvent

## PullRequestTimelineItems

An item in a pull request timeline.

### Possible types for `PullRequestTimelineItems`

* AddedToMergeQueueEvent
* AddedToProjectEvent
* AddedToProjectV2Event
* AssignedEvent
* AutoMergeDisabledEvent
* AutoMergeEnabledEvent
* AutoRebaseEnabledEvent
* AutoSquashEnabledEvent
* AutomaticBaseChangeFailedEvent
* AutomaticBaseChangeSucceededEvent
* BaseRefChangedEvent
* BaseRefDeletedEvent
* BaseRefForcePushedEvent
* BlockedByAddedEvent
* BlockedByRemovedEvent
* BlockingAddedEvent
* BlockingRemovedEvent
* ClosedEvent
* CommentDeletedEvent
* ConnectedEvent
* ConvertToDraftEvent
* ConvertedFromDraftEvent
* ConvertedNoteToIssueEvent
* ConvertedToDiscussionEvent
* CrossReferencedEvent
* DemilestonedEvent
* DeployedEvent
* DeploymentEnvironmentChangedEvent
* DisconnectedEvent
* HeadRefDeletedEvent
* HeadRefForcePushedEvent
* HeadRefRestoredEvent
* IssueComment
* IssueCommentPinnedEvent
* IssueCommentUnpinnedEvent
* IssueFieldAddedEvent
* IssueFieldChangedEvent
* IssueFieldRemovedEvent
* IssueTypeAddedEvent
* IssueTypeChangedEvent
* IssueTypeRemovedEvent
* LabeledEvent
* LockedEvent
* MarkedAsDuplicateEvent
* MentionedEvent
* MergedEvent
* MilestonedEvent
* MovedColumnsInProjectEvent
* ParentIssueAddedEvent
* ParentIssueRemovedEvent
* PinnedEvent
* ProjectV2ItemStatusChangedEvent
* PullRequestCommit
* PullRequestCommitCommentThread
* PullRequestReview
* PullRequestReviewThread
* PullRequestRevisionMarker
* ReadyForReviewEvent
* ReferencedEvent
* RemovedFromMergeQueueEvent
* RemovedFromProjectEvent
* RemovedFromProjectV2Event
* RenamedTitleEvent
* ReopenedEvent
* ReviewDismissedEvent
* ReviewRequestRemovedEvent
* ReviewRequestedEvent
* SubIssueAddedEvent
* SubIssueRemovedEvent
* SubscribedEvent
* TransferredEvent
* UnassignedEvent
* UnlabeledEvent
* UnlockedEvent
* UnmarkedAsDuplicateEvent
* UnpinnedEvent
* UnsubscribedEvent
* UserBlockedEvent

## PushAllowanceActor

Types that can be an actor.

### Possible types for `PushAllowanceActor`

* App
* Team
* User

## Reactor

Types that can be assigned to reactions.

### Possible types for `Reactor`

* Bot
* Mannequin
* Organization
* User

## ReferencedSubject

Any referencable object.

### Possible types for `ReferencedSubject`

* Issue
* PullRequest

## RenamedTitleSubject

An object which has a renamable title.

### Possible types for `RenamedTitleSubject`

* Issue
* PullRequest

## RequestedReviewer

Types that can be requested reviewers.

### Possible types for `RequestedReviewer`

* Bot
* Mannequin
* Team
* User

## ReviewDismissalAllowanceActor

Types that can be an actor.

### Possible types for `ReviewDismissalAllowanceActor`

* App
* Team
* User

## RuleParameters

Types which can be parameters for RepositoryRule objects.

### Possible types for `RuleParameters`

* BranchNamePatternParameters
* CodeScanningParameters
* CommitAuthorEmailPatternParameters
* CommitMessagePatternParameters
* CommitterEmailPatternParameters
* CopilotCodeReviewParameters
* FileExtensionRestrictionParameters
* FilePathRestrictionParameters
* MaxFilePathLengthParameters
* MaxFileSizeParameters
* MergeQueueParameters
* PullRequestParameters
* RequiredDeploymentsParameters
* RequiredStatusChecksParameters
* TagNamePatternParameters
* UpdateParameters
* WorkflowsParameters

## RuleSource

Types which can have RepositoryRule objects.

### Possible types for `RuleSource`

* Enterprise
* Organization
* Repository

## SearchResultItem

The results of a search.

### Possible types for `SearchResultItem`

* App
* Discussion
* Issue
* MarketplaceListing
* Organization
* PullRequest
* Repository
* User

## Sponsor

Entities that can sponsor others via GitHub Sponsors.

### Possible types for `Sponsor`

* Organization
* User

## SponsorableItem

Entities that can be sponsored via GitHub Sponsors.

### Possible types for `SponsorableItem`

* Organization
* User

## SponsorsListingFeatureableItem

A record that can be featured on a GitHub Sponsors profile.

### Possible types for `SponsorsListingFeatureableItem`

* Repository
* User

## StatusCheckRollupContext

Types that can be inside a StatusCheckRollup context.

### Possible types for `StatusCheckRollupContext`

* CheckRun
* StatusContext

## UserListItems

Types that can be added to a user list.

### Possible types for `UserListItems`

* Repository

## VerifiableDomainOwner

Types that can own a verifiable domain.

### Possible types for `VerifiableDomainOwner`

* Enterprise
* Organization