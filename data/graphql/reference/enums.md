# Enums

Enums represent possible sets of values for a field.

## About enums

[Enums](https://spec.graphql.org/June2018/#sec-Enums) represent possible sets of values for a field.

For example, the [`Issue`](/en/graphql/reference/objects#issue) object has a field called `state`. The state is an enum (specifically, of type [`IssueState`](/en/graphql/reference/enums#issuestate)) because it may be `OPEN` or `CLOSED`.

For more information, see [Introduction to GraphQL](/en/graphql/guides/introduction-to-graphql).

## ActorType

The actor's type.

### Values for `ActorType`

* `TEAM`: Indicates a team actor.
* `USER`: Indicates a user actor.

## AuditLogOrderField

Properties by which Audit Log connections can be ordered.

### Values for `AuditLogOrderField`

* `CREATED_AT`: Order audit log entries by timestamp.

## CheckAnnotationLevel

Represents an annotation's information level.

### Values for `CheckAnnotationLevel`

* `FAILURE`: An annotation indicating an inescapable error.
* `NOTICE`: An annotation indicating some information.
* `WARNING`: An annotation indicating an ignorable error.

## CheckConclusionState

The possible states for a check suite or run conclusion.

### Values for `CheckConclusionState`

* `ACTION_REQUIRED`: The check suite or run requires action.
* `CANCELLED`: The check suite or run has been cancelled.
* `FAILURE`: The check suite or run has failed.
* `NEUTRAL`: The check suite or run was neutral.
* `SKIPPED`: The check suite or run was skipped.
* `STALE`: The check suite or run was marked stale by GitHub. Only GitHub can use this conclusion.
* `STARTUP_FAILURE`: The check suite or run has failed at startup.
* `SUCCESS`: The check suite or run has succeeded.
* `TIMED_OUT`: The check suite or run has timed out.

## CheckRunState

The possible states of a check run in a status rollup.

### Values for `CheckRunState`

* `ACTION_REQUIRED`: The check run requires action.
* `CANCELLED`: The check run has been cancelled.
* `COMPLETED`: The check run has been completed.
* `FAILURE`: The check run has failed.
* `IN_PROGRESS`: The check run is in progress.
* `NEUTRAL`: The check run was neutral.
* `PENDING`: The check run is in pending state.
* `QUEUED`: The check run has been queued.
* `SKIPPED`: The check run was skipped.
* `STALE`: The check run was marked stale by GitHub. Only GitHub can use this conclusion.
* `STARTUP_FAILURE`: The check run has failed at startup.
* `SUCCESS`: The check run has succeeded.
* `TIMED_OUT`: The check run has timed out.
* `WAITING`: The check run is in waiting state.

## CheckRunType

The possible types of check runs.

### Values for `CheckRunType`

* `ALL`: Every check run available.
* `LATEST`: The latest check run.

## CheckStatusState

The possible states for a check suite or run status.

### Values for `CheckStatusState`

* `COMPLETED`: The check suite or run has been completed.
* `IN_PROGRESS`: The check suite or run is in progress.
* `PENDING`: The check suite or run is in pending state.
* `QUEUED`: The check suite or run has been queued.
* `REQUESTED`: The check suite or run has been requested.
* `WAITING`: The check suite or run is in waiting state.

## CollaboratorAffiliation

Collaborators affiliation level with a subject.

### Values for `CollaboratorAffiliation`

* `ALL`: All collaborators the authenticated user can see.
* `DIRECT`: All collaborators with permissions to an organization-owned subject, regardless of organization membership status.
* `OUTSIDE`: All outside collaborators of an organization-owned subject.

## CommentAuthorAssociation

A comment author association with repository.

### Values for `CommentAuthorAssociation`

* `COLLABORATOR`: Author has been invited to collaborate on the repository.
* `CONTRIBUTOR`: Author has previously committed to the repository.
* `FIRST_TIMER`: Author has not previously committed to GitHub.
* `FIRST_TIME_CONTRIBUTOR`: Author has not previously committed to the repository.
* `MANNEQUIN`: Author is a placeholder for an unclaimed user.
* `MEMBER`: Author is a member of the organization that owns the repository.
* `NONE`: Author has no association with the repository.
* `OWNER`: Author is the owner of the repository.

## CommentCannotUpdateReason

The possible errors that will prevent a user from updating a comment.

### Values for `CommentCannotUpdateReason`

* `ARCHIVED`: Unable to create comment because repository is archived.
* `DENIED`: You cannot update this comment.
* `INSUFFICIENT_ACCESS`: You must be the author or have write access to this repository to update this comment.
* `LOCKED`: Unable to create comment because issue is locked.
* `LOGIN_REQUIRED`: You must be logged in to update this comment.
* `MAINTENANCE`: Repository is under maintenance.
* `VERIFIED_EMAIL_REQUIRED`: At least one email address must be verified to update this comment.

## CommitContributionOrderField

Properties by which commit contribution connections can be ordered.

### Values for `CommitContributionOrderField`

* `COMMIT_COUNT`: Order commit contributions by how many commits they represent.
* `OCCURRED_AT`: Order commit contributions by when they were made.

## ComparisonStatus

The status of a git comparison between two refs.

### Values for `ComparisonStatus`

* `AHEAD`: The head ref is ahead of the base ref.
* `BEHIND`: The head ref is behind the base ref.
* `DIVERGED`: The head ref is both ahead and behind of the base ref, indicating git history has diverged.
* `IDENTICAL`: The head ref and base ref are identical.

## ContributionLevel

Varying levels of contributions from none to many.

### Values for `ContributionLevel`

* `FIRST_QUARTILE`: Lowest 25% of days of contributions.
* `FOURTH_QUARTILE`: Highest 25% of days of contributions. More contributions than the third quartile.
* `NONE`: No contributions occurred.
* `SECOND_QUARTILE`: Second lowest 25% of days of contributions. More contributions than the first quartile.
* `THIRD_QUARTILE`: Second highest 25% of days of contributions. More contributions than second quartile, less than the fourth quartile.

## CustomPropertyValueType

The allowed value types for a custom property definition.

### Values for `CustomPropertyValueType`

* `MULTI_SELECT`: A multi-select value.
* `SINGLE_SELECT`: A single-select value.
* `STRING`: A string value.
* `TRUE_FALSE`: A true/false value.
* `URL`: A URL value.

## DefaultRepositoryPermissionField

The possible base permissions for repositories.

### Values for `DefaultRepositoryPermissionField`

* `ADMIN`: Can read, write, and administrate repos by default.
* `NONE`: No access.
* `READ`: Can read repos by default.
* `WRITE`: Can read and write repos by default.

## DependencyGraphEcosystem

The possible ecosystems of a dependency graph package.

### Values for `DependencyGraphEcosystem`

* `ACTIONS`: GitHub Actions.
* `COMPOSER`: PHP packages hosted at packagist.org.
* `GO`: Go modules.
* `MAVEN`: Java artifacts hosted at the Maven central repository.
* `NPM`: JavaScript packages hosted at npmjs.com.
* `NUGET`: .NET packages hosted at the NuGet Gallery.
* `PIP`: Python packages hosted at PyPI.org.
* `PUB`: Dart packages hosted at pub.dev.
* `RUBYGEMS`: Ruby gems hosted at RubyGems.org.
* `RUST`: Rust crates.
* `SWIFT`: Swift packages.

## DeploymentOrderField

Properties by which deployment connections can be ordered.

### Values for `DeploymentOrderField`

* `CREATED_AT`: Order collection by creation time.

## DeploymentProtectionRuleType

The possible protection rule types.

### Values for `DeploymentProtectionRuleType`

* `BRANCH_POLICY`: Branch policy.
* `REQUIRED_REVIEWERS`: Required reviewers.
* `WAIT_TIMER`: Wait timer.

## DeploymentReviewState

The possible states for a deployment review.

### Values for `DeploymentReviewState`

* `APPROVED`: The deployment was approved.
* `REJECTED`: The deployment was rejected.

## DeploymentState

The possible states in which a deployment can be.

### Values for `DeploymentState`

* `ABANDONED`: The pending deployment was not updated after 30 minutes.
* `ACTIVE`: The deployment is currently active.
* `DESTROYED`: An inactive transient deployment.
* `ERROR`: The deployment experienced an error.
* `FAILURE`: The deployment has failed.
* `INACTIVE`: The deployment is inactive.
* `IN_PROGRESS`: The deployment is in progress.
* `PENDING`: The deployment is pending.
* `QUEUED`: The deployment has queued.
* `SUCCESS`: The deployment was successful.
* `WAITING`: The deployment is waiting.

## DeploymentStatusState

The possible states for a deployment status.

### Values for `DeploymentStatusState`

* `ERROR`: The deployment experienced an error.
* `FAILURE`: The deployment has failed.
* `INACTIVE`: The deployment is inactive.
* `IN_PROGRESS`: The deployment is in progress.
* `PENDING`: The deployment is pending.
* `QUEUED`: The deployment is queued.
* `SUCCESS`: The deployment was successful.
* `WAITING`: The deployment is waiting.

## DiffSide

The possible sides of a diff.

### Values for `DiffSide`

* `LEFT`: The left side of the diff.
* `RIGHT`: The right side of the diff.

## DiscussionCloseReason

The possible reasons for closing a discussion.

### Values for `DiscussionCloseReason`

* `DUPLICATE`: The discussion is a duplicate of another.
* `OUTDATED`: The discussion is no longer relevant.
* `RESOLVED`: The discussion has been resolved.

## DiscussionOrderField

Properties by which discussion connections can be ordered.

### Values for `DiscussionOrderField`

* `CREATED_AT`: Order discussions by creation time.
* `UPDATED_AT`: Order discussions by most recent modification time.

## DiscussionPollOptionOrderField

Properties by which discussion poll option connections can be ordered.

### Values for `DiscussionPollOptionOrderField`

* `AUTHORED_ORDER`: Order poll options by the order that the poll author specified when creating the poll.
* `VOTE_COUNT`: Order poll options by the number of votes it has.

## DiscussionState

The possible states of a discussion.

### Values for `DiscussionState`

* `CLOSED`: A discussion that has been closed.
* `OPEN`: A discussion that is open.

## DiscussionStateReason

The possible state reasons of a discussion.

### Values for `DiscussionStateReason`

* `DUPLICATE`: The discussion is a duplicate of another.
* `OUTDATED`: The discussion is no longer relevant.
* `REOPENED`: The discussion was reopened.
* `RESOLVED`: The discussion has been resolved.

## DismissReason

The possible reasons that a Dependabot alert was dismissed.

### Values for `DismissReason`

* `FIX_STARTED`: A fix has already been started.
* `INACCURATE`: This alert is inaccurate or incorrect.
* `NOT_USED`: Vulnerable code is not actually used.
* `NO_BANDWIDTH`: No bandwidth to fix this.
* `TOLERABLE_RISK`: Risk is tolerable to this project.

## EnterpriseAdministratorInvitationOrderField

Properties by which enterprise administrator invitation connections can be ordered.

### Values for `EnterpriseAdministratorInvitationOrderField`

* `CREATED_AT`: Order enterprise administrator member invitations by creation time.

## EnterpriseAdministratorRole

The possible administrator roles in an enterprise account.

### Values for `EnterpriseAdministratorRole`

* `BILLING_MANAGER`: Represents a billing manager of the enterprise account.
* `OWNER`: Represents an owner of the enterprise account.
* `UNAFFILIATED`: Unaffiliated member of the enterprise account without an admin role.

## EnterpriseAllowPrivateRepositoryForkingPolicyValue

The possible values for the enterprise allow private repository forking policy value.

### Values for `EnterpriseAllowPrivateRepositoryForkingPolicyValue`

* `ENTERPRISE_ORGANIZATIONS`: Members can fork a repository to an organization within this enterprise.
* `ENTERPRISE_ORGANIZATIONS_USER_ACCOUNTS`: Members can fork a repository to their enterprise-managed user account or an organization inside this enterprise.
* `EVERYWHERE`: Members can fork a repository to their user account or an organization, either inside or outside of this enterprise.
* `SAME_ORGANIZATION`: Members can fork a repository only within the same organization (intra-org).
* `SAME_ORGANIZATION_USER_ACCOUNTS`: Members can fork a repository to their user account or within the same organization.
* `USER_ACCOUNTS`: Members can fork a repository to their user account.

## EnterpriseDefaultRepositoryPermissionSettingValue

The possible values for the enterprise base repository permission setting.

### Values for `EnterpriseDefaultRepositoryPermissionSettingValue`

* `ADMIN`: Organization members will be able to clone, pull, push, and add new collaborators to all organization repositories.
* `NONE`: Organization members will only be able to clone and pull public repositories.
* `NO_POLICY`: Organizations in the enterprise choose base repository permissions for their members.
* `READ`: Organization members will be able to clone and pull all organization repositories.
* `WRITE`: Organization members will be able to clone, pull, and push all organization repositories.

## EnterpriseDisallowedMethodsSettingValue

The possible values for an enabled/no policy enterprise setting.

### Values for `EnterpriseDisallowedMethodsSettingValue`

* `INSECURE`: The setting prevents insecure 2FA methods from being used by members of the enterprise.
* `NO_POLICY`: There is no policy set for preventing insecure 2FA methods from being used by members of the enterprise.

## EnterpriseEnabledDisabledSettingValue

The possible values for an enabled/disabled enterprise setting.

### Values for `EnterpriseEnabledDisabledSettingValue`

* `DISABLED`: The setting is disabled for organizations in the enterprise.
* `ENABLED`: The setting is enabled for organizations in the enterprise.
* `NO_POLICY`: There is no policy set for organizations in the enterprise.

## EnterpriseEnabledSettingValue

The possible values for an enabled/no policy enterprise setting.

### Values for `EnterpriseEnabledSettingValue`

* `ENABLED`: The setting is enabled for organizations in the enterprise.
* `NO_POLICY`: There is no policy set for organizations in the enterprise.

## EnterpriseMemberInvitationOrderField

Properties by which enterprise member invitation connections can be ordered.

### Values for `EnterpriseMemberInvitationOrderField`

* `CREATED_AT`: Order enterprise member invitations by creation time.

## EnterpriseMemberOrderField

Properties by which enterprise member connections can be ordered.

### Values for `EnterpriseMemberOrderField`

* `CREATED_AT`: Order enterprise members by creation time.
* `LOGIN`: Order enterprise members by login.

## EnterpriseMembersCanCreateRepositoriesSettingValue

The possible values for the enterprise members can create repositories setting.

### Values for `EnterpriseMembersCanCreateRepositoriesSettingValue`

* `ALL`: Members will be able to create public and private repositories.
* `DISABLED`: Members will not be able to create public or private repositories.
* `NO_POLICY`: Organization owners choose whether to allow members to create repositories.
* `PRIVATE`: Members will be able to create only private repositories.
* `PUBLIC`: Members will be able to create only public repositories.

## EnterpriseMembersCanMakePurchasesSettingValue

The possible values for the members can make purchases setting.

### Values for `EnterpriseMembersCanMakePurchasesSettingValue`

* `DISABLED`: The setting is disabled for organizations in the enterprise.
* `ENABLED`: The setting is enabled for organizations in the enterprise.

## EnterpriseMembershipType

The possible values we have for filtering Platform::Objects::User#enterprises.

### Values for `EnterpriseMembershipType`

* `ADMIN`: Returns all enterprises in which the user is an admin.
* `ALL`: Returns all enterprises in which the user is a member, admin, or billing manager.
* `BILLING_MANAGER`: Returns all enterprises in which the user is a billing manager.
* `ORG_MEMBERSHIP`: Returns all enterprises in which the user is a member of an org that is owned by the enterprise.

## EnterpriseOrderField

Properties by which enterprise connections can be ordered.

### Values for `EnterpriseOrderField`

* `NAME`: Order enterprises by name.

## EnterpriseServerInstallationOrderField

Properties by which Enterprise Server installation connections can be ordered.

### Values for `EnterpriseServerInstallationOrderField`

* `CREATED_AT`: Order Enterprise Server installations by creation time.
* `CUSTOMER_NAME`: Order Enterprise Server installations by customer name.
* `HOST_NAME`: Order Enterprise Server installations by host name.

## EnterpriseServerUserAccountEmailOrderField

Properties by which Enterprise Server user account email connections can be ordered.

### Values for `EnterpriseServerUserAccountEmailOrderField`

* `EMAIL`: Order emails by email.

## EnterpriseServerUserAccountOrderField

Properties by which Enterprise Server user account connections can be ordered.

### Values for `EnterpriseServerUserAccountOrderField`

* `LOGIN`: Order user accounts by login.
* `REMOTE_CREATED_AT`: Order user accounts by creation time on the Enterprise Server installation.

## EnterpriseServerUserAccountsUploadOrderField

Properties by which Enterprise Server user accounts upload connections can be ordered.

### Values for `EnterpriseServerUserAccountsUploadOrderField`

* `CREATED_AT`: Order user accounts uploads by creation time.

## EnterpriseServerUserAccountsUploadSyncState

Synchronization state of the Enterprise Server user accounts upload.

### Values for `EnterpriseServerUserAccountsUploadSyncState`

* `FAILURE`: The synchronization of the upload failed.
* `PENDING`: The synchronization of the upload is pending.
* `SUCCESS`: The synchronization of the upload succeeded.

## EnterpriseUserAccountMembershipRole

The possible roles for enterprise membership.

### Values for `EnterpriseUserAccountMembershipRole`

* `MEMBER`: The user is a member of an organization in the enterprise.
* `OWNER`: The user is an owner of an organization in the enterprise.
* `UNAFFILIATED`: The user is not an owner of the enterprise, and not a member or owner of any
  organizations in the enterprise; only for EMU-enabled enterprises.

## EnterpriseUserDeployment

The possible GitHub Enterprise deployments where this user can exist.

### Values for `EnterpriseUserDeployment`

* `CLOUD`: The user is part of a GitHub Enterprise Cloud deployment.
* `SERVER`: The user is part of a GitHub Enterprise Server deployment.

## EnvironmentOrderField

Properties by which environments connections can be ordered.

### Values for `EnvironmentOrderField`

* `NAME`: Order environments by name.

## EnvironmentPinnedFilterField

Properties by which environments connections can be ordered.

### Values for `EnvironmentPinnedFilterField`

* `ALL`: All environments will be returned.
* `NONE`: Environments exclude pinned will be returned.
* `ONLY`: Only pinned environment will be returned.

## FileViewedState

The possible viewed states of a file .

### Values for `FileViewedState`

* `DISMISSED`: The file has new changes since last viewed.
* `UNVIEWED`: The file has not been marked as viewed.
* `VIEWED`: The file has been marked as viewed.

## FundingPlatform

The possible funding platforms for repository funding links.

### Values for `FundingPlatform`

* `BUY_ME_A_COFFEE`: Buy Me a Coffee funding platform.
* `COMMUNITY_BRIDGE`: Community Bridge funding platform.
* `CUSTOM`: Custom funding platform.
* `GITHUB`: GitHub funding platform.
* `ISSUEHUNT`: IssueHunt funding platform.
* `KO_FI`: Ko-fi funding platform.
* `LFX_CROWDFUNDING`: LFX Crowdfunding funding platform.
* `LIBERAPAY`: Liberapay funding platform.
* `OPEN_COLLECTIVE`: Open Collective funding platform.
* `PATREON`: Patreon funding platform.
* `POLAR`: Polar funding platform.
* `THANKS_DEV`: thanks.dev funding platform.
* `TIDELIFT`: Tidelift funding platform.

## GistOrderField

Properties by which gist connections can be ordered.

### Values for `GistOrderField`

* `CREATED_AT`: Order gists by creation time.
* `PUSHED_AT`: Order gists by push time.
* `UPDATED_AT`: Order gists by update time.

## GistPrivacy

The privacy of a Gist.

### Values for `GistPrivacy`

* `ALL`: Gists that are public and secret.
* `PUBLIC`: Public.
* `SECRET`: Secret.

## GitSignatureState

The state of a Git signature.

### Values for `GitSignatureState`

* `BAD_CERT`: The signing certificate or its chain could not be verified.
* `BAD_EMAIL`: Invalid email used for signing.
* `EXPIRED_KEY`: Signing key expired.
* `GPGVERIFY_ERROR`: Internal error - the GPG verification service misbehaved.
* `GPGVERIFY_UNAVAILABLE`: Internal error - the GPG verification service is unavailable at the moment.
* `INVALID`: Invalid signature.
* `MALFORMED_SIG`: Malformed signature.
* `NOT_SIGNING_KEY`: The usage flags for the key that signed this don't allow signing.
* `NO_USER`: Email used for signing not known to GitHub.
* `OCSP_ERROR`: Valid signature, though certificate revocation check failed.
* `OCSP_PENDING`: Valid signature, pending certificate revocation checking.
* `OCSP_REVOKED`: One or more certificates in chain has been revoked.
* `UNKNOWN_KEY`: Key used for signing not known to GitHub.
* `UNKNOWN_SIG_TYPE`: Unknown signature type.
* `UNSIGNED`: Unsigned.
* `UNVERIFIED_EMAIL`: Email used for signing unverified on GitHub.
* `VALID`: Valid signature and verified by GitHub.

## IdentityProviderConfigurationState

The possible states in which authentication can be configured with an identity provider.

### Values for `IdentityProviderConfigurationState`

* `CONFIGURED`: Authentication with an identity provider is configured but not enforced.
* `ENFORCED`: Authentication with an identity provider is configured and enforced.
* `UNCONFIGURED`: Authentication with an identity provider is not configured.

## IpAllowListEnabledSettingValue

The possible values for the IP allow list enabled setting.

### Values for `IpAllowListEnabledSettingValue`

* `DISABLED`: The setting is disabled for the owner.
* `ENABLED`: The setting is enabled for the owner.

## IpAllowListEntryOrderField

Properties by which IP allow list entry connections can be ordered.

### Values for `IpAllowListEntryOrderField`

* `ALLOW_LIST_VALUE`: Order IP allow list entries by the allow list value.
* `CREATED_AT`: Order IP allow list entries by creation time.

## IpAllowListForInstalledAppsEnabledSettingValue

The possible values for the IP allow list configuration for installed GitHub Apps setting.

### Values for `IpAllowListForInstalledAppsEnabledSettingValue`

* `DISABLED`: The setting is disabled for the owner.
* `ENABLED`: The setting is enabled for the owner.

## IpAllowListUserLevelEnforcementEnabledSettingValue

The possible values for the IP allow list user-level enforcement enabled setting.

### Values for `IpAllowListUserLevelEnforcementEnabledSettingValue`

* `DISABLED`: The setting is disabled for the owner.
* `ENABLED`: The setting is enabled for the owner.

## IssueClosedStateReason

The possible state reasons of a closed issue.

### Values for `IssueClosedStateReason`

* `COMPLETED`: An issue that has been closed as completed.
* `DUPLICATE`: An issue that has been closed as a duplicate.
* `NOT_PLANNED`: An issue that has been closed as not planned.

## IssueCommentOrderField

Properties by which issue comment connections can be ordered.

### Values for `IssueCommentOrderField`

* `UPDATED_AT`: Order issue comments by update time.

## IssueDependencyOrderField

Properties by which issue dependencies can be ordered.

### Values for `IssueDependencyOrderField`

* `CREATED_AT`: Order issue dependencies by the creation time of the dependent issue.
* `DEPENDENCY_ADDED_AT`: Order issue dependencies by time of when the dependency relationship was added.

## IssueFieldDataType

The type of an issue field.

### Values for `IssueFieldDataType`

* `DATE`: Date.
* `NUMBER`: Number.
* `SINGLE_SELECT`: Single Select.
* `TEXT`: Text.

## IssueFieldOrderField

Properties by which issue field connections can be ordered.

### Values for `IssueFieldOrderField`

* `CREATED_AT`: Order issue fields by creation time.
* `NAME`: Order issue fields by name.

## IssueFieldSingleSelectOptionColor

The display color of a single-select field option.

### Values for `IssueFieldSingleSelectOptionColor`

* `BLUE`: blue.
* `GRAY`: gray.
* `GREEN`: green.
* `ORANGE`: orange.
* `PINK`: pink.
* `PURPLE`: purple.
* `RED`: red.
* `YELLOW`: yellow.

## IssueFieldVisibility

The visibility of an issue field.

### Values for `IssueFieldVisibility`

* `ALL`: All.
* `ORG_ONLY`: Org Only.

## IssueOrderField

Properties by which issue connections can be ordered.

### Values for `IssueOrderField`

* `COMMENTS`: Order issues by comment count.
* `CREATED_AT`: Order issues by creation time.
* `UPDATED_AT`: Order issues by update time.

## IssueSearchType

Type of issue search performed.

### Values for `IssueSearchType`

* `HYBRID`: Hybrid search combining lexical and semantic approaches.
* `LEXICAL`: Lexical (keyword-based) search.
* `SEMANTIC`: Semantic (meaning-based) search using embeddings.

## IssueState

The possible states of an issue.

### Values for `IssueState`

* `CLOSED`: An issue that has been closed.
* `OPEN`: An issue that is still open.

## IssueStateReason

The possible state reasons of an issue.

### Values for `IssueStateReason`

* `COMPLETED`: An issue that has been closed as completed.
* `DUPLICATE`: An issue that has been closed as a duplicate.
* `NOT_PLANNED`: An issue that has been closed as not planned.
* `REOPENED`: An issue that has been reopened.

## IssueTimelineItemsItemType

The possible item types found in a timeline.

### Values for `IssueTimelineItemsItemType`

* `ADDED_TO_PROJECT_EVENT`: Represents aadded\_to\_projectevent on a given issue or pull request.
* `ADDED_TO_PROJECT_V2_EVENT`: Represents aadded\_to\_project\_v2event on a given issue or pull request.
* `ASSIGNED_EVENT`: Represents anassignedevent on any assignable object.
* `BLOCKED_BY_ADDED_EVENT`: Represents ablocked\_by\_addedevent on a given issue.
* `BLOCKED_BY_REMOVED_EVENT`: Represents ablocked\_by\_removedevent on a given issue.
* `BLOCKING_ADDED_EVENT`: Represents ablocking\_addedevent on a given issue.
* `BLOCKING_REMOVED_EVENT`: Represents ablocking\_removedevent on a given issue.
* `CLOSED_EVENT`: Represents aclosedevent on any Closable.
* `COMMENT_DELETED_EVENT`: Represents acomment\_deletedevent on a given issue or pull request.
* `CONNECTED_EVENT`: Represents aconnectedevent on a given issue or pull request.
* `CONVERTED_FROM_DRAFT_EVENT`: Represents aconverted\_from\_draftevent on a given issue or pull request.
* `CONVERTED_NOTE_TO_ISSUE_EVENT`: Represents aconverted\_note\_to\_issueevent on a given issue or pull request.
* `CONVERTED_TO_DISCUSSION_EVENT`: Represents aconverted\_to\_discussionevent on a given issue.
* `CROSS_REFERENCED_EVENT`: Represents a mention made by one issue or pull request to another.
* `DEMILESTONED_EVENT`: Represents ademilestonedevent on a given issue or pull request.
* `DISCONNECTED_EVENT`: Represents adisconnectedevent on a given issue or pull request.
* `ISSUE_COMMENT`: Represents a comment on an Issue.
* `ISSUE_COMMENT_PINNED_EVENT`: Represents aissue\_comment\_pinnedevent on a given issue.
* `ISSUE_COMMENT_UNPINNED_EVENT`: Represents aissue\_comment\_unpinnedevent on a given issue.
* `ISSUE_FIELD_ADDED_EVENT`: Represents aissue\_field\_addedevent on a given issue.
* `ISSUE_FIELD_CHANGED_EVENT`: Represents aissue\_field\_changedevent on a given issue.
* `ISSUE_FIELD_REMOVED_EVENT`: Represents aissue\_field\_removedevent on a given issue.
* `ISSUE_TYPE_ADDED_EVENT`: Represents aissue\_type\_addedevent on a given issue.
* `ISSUE_TYPE_CHANGED_EVENT`: Represents aissue\_type\_changedevent on a given issue.
* `ISSUE_TYPE_REMOVED_EVENT`: Represents aissue\_type\_removedevent on a given issue.
* `LABELED_EVENT`: Represents alabeledevent on a given issue or pull request.
* `LOCKED_EVENT`: Represents alockedevent on a given issue or pull request.
* `MARKED_AS_DUPLICATE_EVENT`: Represents amarked\_as\_duplicateevent on a given issue or pull request.
* `MENTIONED_EVENT`: Represents amentionedevent on a given issue or pull request.
* `MILESTONED_EVENT`: Represents amilestonedevent on a given issue or pull request.
* `MOVED_COLUMNS_IN_PROJECT_EVENT`: Represents amoved\_columns\_in\_projectevent on a given issue or pull request.
* `PARENT_ISSUE_ADDED_EVENT`: Represents aparent\_issue\_addedevent on a given issue.
* `PARENT_ISSUE_REMOVED_EVENT`: Represents aparent\_issue\_removedevent on a given issue.
* `PINNED_EVENT`: Represents apinnedevent on a given issue or pull request.
* `PROJECT_V2_ITEM_STATUS_CHANGED_EVENT`: Represents aproject\_v2\_item\_status\_changedevent on a given issue or pull request.
* `REFERENCED_EVENT`: Represents areferencedevent on a given ReferencedSubject.
* `REMOVED_FROM_PROJECT_EVENT`: Represents aremoved\_from\_projectevent on a given issue or pull request.
* `REMOVED_FROM_PROJECT_V2_EVENT`: Represents aremoved\_from\_project\_v2event on a given issue or pull request.
* `RENAMED_TITLE_EVENT`: Represents arenamedevent on a given issue or pull request.
* `REOPENED_EVENT`: Represents areopenedevent on any Closable.
* `SUBSCRIBED_EVENT`: Represents asubscribedevent on a given Subscribable.
* `SUB_ISSUE_ADDED_EVENT`: Represents asub\_issue\_addedevent on a given issue.
* `SUB_ISSUE_REMOVED_EVENT`: Represents asub\_issue\_removedevent on a given issue.
* `TRANSFERRED_EVENT`: Represents atransferredevent on a given issue or pull request.
* `UNASSIGNED_EVENT`: Represents anunassignedevent on any assignable object.
* `UNLABELED_EVENT`: Represents anunlabeledevent on a given issue or pull request.
* `UNLOCKED_EVENT`: Represents anunlockedevent on a given issue or pull request.
* `UNMARKED_AS_DUPLICATE_EVENT`: Represents anunmarked\_as\_duplicateevent on a given issue or pull request.
* `UNPINNED_EVENT`: Represents anunpinnedevent on a given issue or pull request.
* `UNSUBSCRIBED_EVENT`: Represents anunsubscribedevent on a given Subscribable.
* `USER_BLOCKED_EVENT`: Represents auser\_blockedevent on a given user.

## IssueTypeColor

The possible color for an issue type.

### Values for `IssueTypeColor`

* `BLUE`: blue.
* `GRAY`: gray.
* `GREEN`: green.
* `ORANGE`: orange.
* `PINK`: pink.
* `PURPLE`: purple.
* `RED`: red.
* `YELLOW`: yellow.

## IssueTypeOrderField

Properties by which issue type connections can be ordered.

### Values for `IssueTypeOrderField`

* `CREATED_AT`: Order issue types by creation time.
* `NAME`: Order issue types by name.

## LabelOrderField

Properties by which label connections can be ordered.

### Values for `LabelOrderField`

* `CREATED_AT`: Order labels by creation time.
* `ISSUE_COUNT`: Order labels by issue count.
* `NAME`: Order labels by name.

## LanguageOrderField

Properties by which language connections can be ordered.

### Values for `LanguageOrderField`

* `SIZE`: Order languages by the size of all files containing the language.

## LexicalFallbackReason

Reason why a semantic or hybrid issue search fell back to lexical search.

### Values for `LexicalFallbackReason`

* `NON_ISSUE_TARGET`: Query targets non-issue types (e.g., pull requests).
* `NO_ACCESSIBLE_REPOS`: Scoped query resolved to zero accessible repositories.
* `NO_TEXT_TERMS`: Query has only qualifiers and no free text terms.
* `ONLY_NON_SEMANTIC_FIELDS_REQUESTED`: Query uses an in: qualifier targeting non-semantic fields.
* `OR_BOOLEAN_NOT_SUPPORTED`: Query contains OR operators (nested boolean qualifiers).
* `QUOTED_TEXT`: Query contains quoted text requiring exact matches.
* `SERVER_ERROR`: Embedding generation failed or timed out.

## LockReason

The possible reasons that an issue or pull request was locked.

### Values for `LockReason`

* `OFF_TOPIC`: The issue or pull request was locked because the conversation was off-topic.
* `RESOLVED`: The issue or pull request was locked because the conversation was resolved.
* `SPAM`: The issue or pull request was locked because the conversation was spam.
* `TOO_HEATED`: The issue or pull request was locked because the conversation was too heated.

## MannequinOrderField

Properties by which mannequins can be ordered.

### Values for `MannequinOrderField`

* `CREATED_AT`: Order mannequins why when they were created.
* `LOGIN`: Order mannequins alphabetically by their source login.

## MergeCommitMessage

The possible default commit messages for merges.

### Values for `MergeCommitMessage`

* `BLANK`: Default to a blank commit message.
* `PR_BODY`: Default to the pull request's body.
* `PR_TITLE`: Default to the pull request's title.

## MergeCommitTitle

The possible default commit titles for merges.

### Values for `MergeCommitTitle`

* `MERGE_MESSAGE`: Default to the classic title for a merge message (e.g., Merge pull request #123 from branch-name).
* `PR_TITLE`: Default to the pull request's title.

## MergeQueueEntryState

The possible states for a merge queue entry.

### Values for `MergeQueueEntryState`

* `AWAITING_CHECKS`: The entry is currently waiting for checks to pass.
* `LOCKED`: The entry is currently locked.
* `MERGEABLE`: The entry is currently mergeable.
* `QUEUED`: The entry is currently queued.
* `UNMERGEABLE`: The entry is currently unmergeable.

## MergeQueueGroupingStrategy

When set to ALLGREEN, the merge commit created by merge queue for each PR in the
group must pass all required checks to merge. When set to HEADGREEN, only the
commit at the head of the merge group, i.e. the commit containing changes from
all of the PRs in the group, must pass its required checks to merge.

### Values for `MergeQueueGroupingStrategy`

* `ALLGREEN`: The merge commit created by merge queue for each PR in the group must pass all required checks to merge.
* `HEADGREEN`: Only the commit at the head of the merge group must pass its required checks to merge.

## MergeQueueMergeMethod

Method to use when merging changes from queued pull requests.

### Values for `MergeQueueMergeMethod`

* `MERGE`: Merge commit.
* `REBASE`: Rebase and merge.
* `SQUASH`: Squash and merge.

## MergeQueueMergingStrategy

The possible merging strategies for a merge queue.

### Values for `MergeQueueMergingStrategy`

* `ALLGREEN`: Entries only allowed to merge if they are passing.
* `HEADGREEN`: Failing Entires are allowed to merge if they are with a passing entry.

## MergeStateStatus

Detailed status information about a pull request merge.

### Values for `MergeStateStatus`

* `BEHIND`: The head ref is out of date.
* `BLOCKED`: The merge is blocked.
* `CLEAN`: Mergeable and passing commit status.
* `DIRTY`: The merge commit cannot be cleanly created.
* `DRAFT`: The merge is blocked due to the pull request being a draft.
* `HAS_HOOKS`: Mergeable with passing commit status and pre-receive hooks.
* `UNKNOWN`: The state cannot currently be determined.
* `UNSTABLE`: Mergeable with non-passing commit status.

## MergeableState

Whether or not a PullRequest can be merged.

### Values for `MergeableState`

* `CONFLICTING`: The pull request cannot be merged due to merge conflicts.
* `MERGEABLE`: The pull request can be merged.
* `UNKNOWN`: The mergeability of the pull request is still being calculated.

## MigrationSourceType

Represents the different GitHub Enterprise Importer (GEI) migration sources.

### Values for `MigrationSourceType`

* `AZURE_DEVOPS`: An Azure DevOps migration source.
* `BITBUCKET_SERVER`: A Bitbucket Server migration source.
* `GITHUB_ARCHIVE`: A GitHub Migration API source.

## MigrationState

The GitHub Enterprise Importer (GEI) migration state.

### Values for `MigrationState`

* `FAILED`: The migration has failed.
* `FAILED_VALIDATION`: The migration has invalid credentials.
* `IN_PROGRESS`: The migration is in progress.
* `NOT_STARTED`: The migration has not started.
* `PENDING_VALIDATION`: The migration needs to have its credentials validated.
* `QUEUED`: The migration has been queued.
* `SUCCEEDED`: The migration has succeeded.

## MilestoneOrderField

Properties by which milestone connections can be ordered.

### Values for `MilestoneOrderField`

* `CREATED_AT`: Order milestones by when they were created.
* `DUE_DATE`: Order milestones by when they are due.
* `NUMBER`: Order milestones by their number.
* `UPDATED_AT`: Order milestones by when they were last updated.

## MilestoneState

The possible states of a milestone.

### Values for `MilestoneState`

* `CLOSED`: A milestone that has been closed.
* `OPEN`: A milestone that is still open.

## NotificationRestrictionSettingValue

The possible values for the notification restriction setting.

### Values for `NotificationRestrictionSettingValue`

* `DISABLED`: The setting is disabled for the owner.
* `ENABLED`: The setting is enabled for the owner.

## OIDCProviderType

The OIDC identity provider type.

### Values for `OIDCProviderType`

* `AAD`: Azure Active Directory.

## OauthApplicationCreateAuditEntryState

The state of an OAuth application when it was created.

### Values for `OauthApplicationCreateAuditEntryState`

* `ACTIVE`: The OAuth application was active and allowed to have OAuth Accesses.
* `PENDING_DELETION`: The OAuth application was in the process of being deleted.
* `SUSPENDED`: The OAuth application was suspended from generating OAuth Accesses due to abuse or security concerns.

## OperationType

The corresponding operation type for the action.

### Values for `OperationType`

* `ACCESS`: An existing resource was accessed.
* `AUTHENTICATION`: A resource performed an authentication event.
* `CREATE`: A new resource was created.
* `MODIFY`: An existing resource was modified.
* `REMOVE`: An existing resource was removed.
* `RESTORE`: An existing resource was restored.
* `TRANSFER`: An existing resource was transferred between multiple resources.

## OrderDirection

Possible directions in which to order a list of items when provided an orderBy argument.

### Values for `OrderDirection`

* `ASC`: Specifies an ascending order for a given orderBy argument.
* `DESC`: Specifies a descending order for a given orderBy argument.

## OrgAddMemberAuditEntryPermission

The permissions available to members on an Organization.

### Values for `OrgAddMemberAuditEntryPermission`

* `ADMIN`: Can read, clone, push, and add collaborators to repositories.
* `READ`: Can read and clone repositories.

## OrgCreateAuditEntryBillingPlan

The billing plans available for organizations.

### Values for `OrgCreateAuditEntryBillingPlan`

* `BUSINESS`: Team Plan.
* `BUSINESS_PLUS`: Enterprise Cloud Plan.
* `FREE`: Free Plan.
* `TIERED_PER_SEAT`: Tiered Per Seat Plan.
* `UNLIMITED`: Legacy Unlimited Plan.

## OrgEnterpriseOwnerOrderField

Properties by which enterprise owners can be ordered.

### Values for `OrgEnterpriseOwnerOrderField`

* `LOGIN`: Order enterprise owners by login.

## OrgRemoveBillingManagerAuditEntryReason

The reason a billing manager was removed from an Organization.

### Values for `OrgRemoveBillingManagerAuditEntryReason`

* `SAML_EXTERNAL_IDENTITY_MISSING`: SAML external identity missing.
* `SAML_SSO_ENFORCEMENT_REQUIRES_EXTERNAL_IDENTITY`: SAML SSO enforcement requires an external identity.
* `TWO_FACTOR_REQUIREMENT_NON_COMPLIANCE`: The organization required 2FA of its billing managers and this user did not have 2FA enabled.

## OrgRemoveMemberAuditEntryMembershipType

The type of membership a user has with an Organization.

### Values for `OrgRemoveMemberAuditEntryMembershipType`

* `ADMIN`: Organization owners have full access and can change several settings,
  including the names of repositories that belong to the Organization and Owners
  team membership. In addition, organization owners can delete the organization
  and all of its repositories.
* `BILLING_MANAGER`: A billing manager is a user who manages the billing settings for the Organization, such as updating payment information.
* `DIRECT_MEMBER`: A direct member is a user that is a member of the Organization.
* `OUTSIDE_COLLABORATOR`: An outside collaborator is a person who isn't explicitly a member of the
  Organization, but who has Read, Write, or Admin permissions to one or more
  repositories in the organization.
* `SUSPENDED`: A suspended member.
* `UNAFFILIATED`: An unaffiliated collaborator is a person who is not a member of the
  Organization and does not have access to any repositories in the Organization.

## OrgRemoveMemberAuditEntryReason

The reason a member was removed from an Organization.

### Values for `OrgRemoveMemberAuditEntryReason`

* `SAML_EXTERNAL_IDENTITY_MISSING`: SAML external identity missing.
* `SAML_SSO_ENFORCEMENT_REQUIRES_EXTERNAL_IDENTITY`: SAML SSO enforcement requires an external identity.
* `TWO_FACTOR_ACCOUNT_RECOVERY`: User was removed from organization during account recovery.
* `TWO_FACTOR_REQUIREMENT_NON_COMPLIANCE`: The organization required 2FA of its billing managers and this user did not have 2FA enabled.
* `USER_ACCOUNT_DELETED`: User account has been deleted.

## OrgRemoveOutsideCollaboratorAuditEntryMembershipType

The type of membership a user has with an Organization.

### Values for `OrgRemoveOutsideCollaboratorAuditEntryMembershipType`

* `BILLING_MANAGER`: A billing manager is a user who manages the billing settings for the Organization, such as updating payment information.
* `OUTSIDE_COLLABORATOR`: An outside collaborator is a person who isn't explicitly a member of the
  Organization, but who has Read, Write, or Admin permissions to one or more
  repositories in the organization.
* `UNAFFILIATED`: An unaffiliated collaborator is a person who is not a member of the
  Organization and does not have access to any repositories in the organization.

## OrgRemoveOutsideCollaboratorAuditEntryReason

The reason an outside collaborator was removed from an Organization.

### Values for `OrgRemoveOutsideCollaboratorAuditEntryReason`

* `SAML_EXTERNAL_IDENTITY_MISSING`: SAML external identity missing.
* `TWO_FACTOR_REQUIREMENT_NON_COMPLIANCE`: The organization required 2FA of its billing managers and this user did not have 2FA enabled.

## OrgUpdateDefaultRepositoryPermissionAuditEntryPermission

The default permission a repository can have in an Organization.

### Values for `OrgUpdateDefaultRepositoryPermissionAuditEntryPermission`

* `ADMIN`: Can read, clone, push, and add collaborators to repositories.
* `NONE`: No default permission value.
* `READ`: Can read and clone repositories.
* `WRITE`: Can read, clone and push to repositories.

## OrgUpdateMemberAuditEntryPermission

The permissions available to members on an Organization.

### Values for `OrgUpdateMemberAuditEntryPermission`

* `ADMIN`: Can read, clone, push, and add collaborators to repositories.
* `READ`: Can read and clone repositories.

## OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility

The permissions available for repository creation on an Organization.

### Values for `OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility`

* `ALL`: All organization members are restricted from creating any repositories.
* `INTERNAL`: All organization members are restricted from creating internal repositories.
* `NONE`: All organization members are allowed to create any repositories.
* `PRIVATE`: All organization members are restricted from creating private repositories.
* `PRIVATE_INTERNAL`: All organization members are restricted from creating private or internal repositories.
* `PUBLIC`: All organization members are restricted from creating public repositories.
* `PUBLIC_INTERNAL`: All organization members are restricted from creating public or internal repositories.
* `PUBLIC_PRIVATE`: All organization members are restricted from creating public or private repositories.

## OrganizationInvitationRole

The possible organization invitation roles.

### Values for `OrganizationInvitationRole`

* `ADMIN`: The user is invited to be an admin of the organization.
* `BILLING_MANAGER`: The user is invited to be a billing manager of the organization.
* `DIRECT_MEMBER`: The user is invited to be a direct member of the organization.
* `REINSTATE`: The user's previous role will be reinstated.

## OrganizationInvitationSource

The possible organization invitation sources.

### Values for `OrganizationInvitationSource`

* `MEMBER`: The invitation was created from the web interface or from API.
* `SCIM`: The invitation was created from SCIM.
* `UNKNOWN`: The invitation was sent before this feature was added.

## OrganizationInvitationType

The possible organization invitation types.

### Values for `OrganizationInvitationType`

* `EMAIL`: The invitation was to an email address.
* `USER`: The invitation was to an existing user.

## OrganizationMemberRole

The possible roles within an organization for its members.

### Values for `OrganizationMemberRole`

* `ADMIN`: The user is an administrator of the organization.
* `MEMBER`: The user is a member of the organization.

## OrganizationMembersCanCreateRepositoriesSettingValue

The possible values for the members can create repositories setting on an organization.

### Values for `OrganizationMembersCanCreateRepositoriesSettingValue`

* `ALL`: Members will be able to create public and private repositories.
* `DISABLED`: Members will not be able to create public or private repositories.
* `INTERNAL`: Members will be able to create only internal repositories.
* `PRIVATE`: Members will be able to create only private repositories.

## OrganizationMigrationState

The Octoshift Organization migration state.

### Values for `OrganizationMigrationState`

* `FAILED`: The Octoshift migration has failed.
* `FAILED_VALIDATION`: The Octoshift migration has invalid credentials.
* `IN_PROGRESS`: The Octoshift migration is in progress.
* `NOT_STARTED`: The Octoshift migration has not started.
* `PENDING_VALIDATION`: The Octoshift migration needs to have its credentials validated.
* `POST_REPO_MIGRATION`: The Octoshift migration is performing post repository migrations.
* `PRE_REPO_MIGRATION`: The Octoshift migration is performing pre repository migrations.
* `QUEUED`: The Octoshift migration has been queued.
* `REPO_MIGRATION`: The Octoshift org migration is performing repository migrations.
* `SUCCEEDED`: The Octoshift migration has succeeded.

## OrganizationOrderField

Properties by which organization connections can be ordered.

### Values for `OrganizationOrderField`

* `CREATED_AT`: Order organizations by creation time.
* `LOGIN`: Order organizations by login.

## PackageFileOrderField

Properties by which package file connections can be ordered.

### Values for `PackageFileOrderField`

* `CREATED_AT`: Order package files by creation time.

## PackageOrderField

Properties by which package connections can be ordered.

### Values for `PackageOrderField`

* `CREATED_AT`: Order packages by creation time.

## PackageType

The possible types of a package.

### Values for `PackageType`

* `DEBIAN`: A debian package.
* `DOCKER`: A docker image.
* `MAVEN`: A maven package.
* `NPM`: An npm package.
* `NUGET`: A nuget package.
* `PYPI`: A python package.
* `RUBYGEMS`: A rubygems package.

## PackageVersionOrderField

Properties by which package version connections can be ordered.

### Values for `PackageVersionOrderField`

* `CREATED_AT`: Order package versions by creation time.

## PatchStatus

The possible types of patch statuses.

### Values for `PatchStatus`

* `ADDED`: The file was added. Git status 'A'.
* `CHANGED`: The file's type was changed. Git status 'T'.
* `COPIED`: The file was copied. Git status 'C'.
* `DELETED`: The file was deleted. Git status 'D'.
* `MODIFIED`: The file's contents were changed. Git status 'M'.
* `RENAMED`: The file was renamed. Git status 'R'.

## PinnableItemType

Represents items that can be pinned to a profile page or dashboard.

### Values for `PinnableItemType`

* `GIST`: A gist.
* `ISSUE`: An issue.
* `ORGANIZATION`: An organization.
* `PROJECT`: A project.
* `PULL_REQUEST`: A pull request.
* `REPOSITORY`: A repository.
* `TEAM`: A team.
* `USER`: A user.

## PinnedDiscussionGradient

Preconfigured gradients that may be used to style discussions pinned within a repository.

### Values for `PinnedDiscussionGradient`

* `BLUE_MINT`: A gradient of blue to mint.
* `BLUE_PURPLE`: A gradient of blue to purple.
* `PINK_BLUE`: A gradient of pink to blue.
* `PURPLE_CORAL`: A gradient of purple to coral.
* `RED_ORANGE`: A gradient of red to orange.

## PinnedDiscussionPattern

Preconfigured background patterns that may be used to style discussions pinned within a repository.

### Values for `PinnedDiscussionPattern`

* `CHEVRON_UP`: An upward-facing chevron pattern.
* `DOT`: A hollow dot pattern.
* `DOT_FILL`: A solid dot pattern.
* `HEART_FILL`: A heart pattern.
* `PLUS`: A plus sign pattern.
* `ZAP`: A lightning bolt pattern.

## PinnedEnvironmentOrderField

Properties by which pinned environments connections can be ordered.

### Values for `PinnedEnvironmentOrderField`

* `POSITION`: Order pinned environments by position.

## ProjectCardArchivedState

The possible archived states of a project card.

### Values for `ProjectCardArchivedState`

* `ARCHIVED`: A project card that is archived.
* `NOT_ARCHIVED`: A project card that is not archived.

## ProjectCardState

Various content states of a ProjectCard.

### Values for `ProjectCardState`

* `CONTENT_ONLY`: The card has content only.
* `NOTE_ONLY`: The card has a note only.
* `REDACTED`: The card is redacted.

## ProjectColumnPurpose

The semantic purpose of the column - todo, in progress, or done.

### Values for `ProjectColumnPurpose`

* `DONE`: The column contains cards which are complete.
* `IN_PROGRESS`: The column contains cards which are currently being worked on.
* `TODO`: The column contains cards still to be worked on.

## ProjectOrderField

Properties by which project connections can be ordered.

### Values for `ProjectOrderField`

* `CREATED_AT`: Order projects by creation time.
* `NAME`: Order projects by name.
* `UPDATED_AT`: Order projects by update time.

## ProjectState

State of the project; eitheropenor 'closed'.

### Values for `ProjectState`

* `CLOSED`: The project is closed.
* `OPEN`: The project is open.

## ProjectTemplate

GitHub-provided templates for Projects.

### Values for `ProjectTemplate`

* `AUTOMATED_KANBAN_V2`: Create a board with v2 triggers to automatically move cards across To do, In progress and Done columns.
* `AUTOMATED_REVIEWS_KANBAN`: Create a board with triggers to automatically move cards across columns with review automation.
* `BASIC_KANBAN`: Create a board with columns for To do, In progress and Done.
* `BUG_TRIAGE`: Create a board to triage and prioritize bugs with To do, priority, and Done columns.

## ProjectV2CustomFieldType

The type of a project field.

### Values for `ProjectV2CustomFieldType`

* `DATE`: Date.
* `ITERATION`: Iteration.
* `NUMBER`: Number.
* `SINGLE_SELECT`: Single Select.
* `TEXT`: Text.

## ProjectV2FieldOrderField

Properties by which project v2 field connections can be ordered.

### Values for `ProjectV2FieldOrderField`

* `CREATED_AT`: Order project v2 fields by creation time.
* `NAME`: Order project v2 fields by name.
* `POSITION`: Order project v2 fields by position.

## ProjectV2FieldType

The type of a project field.

### Values for `ProjectV2FieldType`

* `ASSIGNEES`: Assignees.
* `DATE`: Date.
* `ISSUE_TYPE`: Issue type.
* `ITERATION`: Iteration.
* `LABELS`: Labels.
* `LINKED_PULL_REQUESTS`: Linked Pull Requests.
* `MILESTONE`: Milestone.
* `NUMBER`: Number.
* `PARENT_ISSUE`: Parent issue.
* `REPOSITORY`: Repository.
* `REVIEWERS`: Reviewers.
* `SINGLE_SELECT`: Single Select.
* `SUB_ISSUES_PROGRESS`: Sub-issues progress.
* `TEXT`: Text.
* `TITLE`: Title.
* `TRACKED_BY`: Tracked by.
* `TRACKS`: Tracks.

## ProjectV2ItemFieldValueOrderField

Properties by which project v2 item field value connections can be ordered.

### Values for `ProjectV2ItemFieldValueOrderField`

* `POSITION`: Order project v2 item field values by the their position in the project.

## ProjectV2ItemOrderField

Properties by which project v2 item connections can be ordered.

### Values for `ProjectV2ItemOrderField`

* `POSITION`: Order project v2 items by the their position in the project.

## ProjectV2ItemType

The type of a project item.

### Values for `ProjectV2ItemType`

* `DRAFT_ISSUE`: Draft Issue.
* `ISSUE`: Issue.
* `PULL_REQUEST`: Pull Request.
* `REDACTED`: Redacted Item.

## ProjectV2OrderField

Properties by which projects can be ordered.

### Values for `ProjectV2OrderField`

* `CREATED_AT`: The project's date and time of creation.
* `NUMBER`: The project's number.
* `TITLE`: The project's title.
* `UPDATED_AT`: The project's date and time of update.

## ProjectV2PermissionLevel

The possible roles of a collaborator on a project.

### Values for `ProjectV2PermissionLevel`

* `ADMIN`: The collaborator can view, edit, and maange the settings of the project.
* `READ`: The collaborator can view the project.
* `WRITE`: The collaborator can view and edit the project.

## ProjectV2Roles

The possible roles of a collaborator on a project.

### Values for `ProjectV2Roles`

* `ADMIN`: The collaborator can view, edit, and maange the settings of the project.
* `NONE`: The collaborator has no direct access to the project.
* `READER`: The collaborator can view the project.
* `WRITER`: The collaborator can view and edit the project.

## ProjectV2SingleSelectFieldOptionColor

The display color of a single-select field option.

### Values for `ProjectV2SingleSelectFieldOptionColor`

* `BLUE`: BLUE.
* `GRAY`: GRAY.
* `GREEN`: GREEN.
* `ORANGE`: ORANGE.
* `PINK`: PINK.
* `PURPLE`: PURPLE.
* `RED`: RED.
* `YELLOW`: YELLOW.

## ProjectV2State

The possible states of a project v2.

### Values for `ProjectV2State`

* `CLOSED`: A project v2 that has been closed.
* `OPEN`: A project v2 that is still open.

## ProjectV2StatusUpdateOrderField

Properties by which project v2 status updates can be ordered.

### Values for `ProjectV2StatusUpdateOrderField`

* `CREATED_AT`: Allows chronological ordering of project v2 status updates.

## ProjectV2StatusUpdateStatus

The possible statuses of a project v2.

### Values for `ProjectV2StatusUpdateStatus`

* `AT_RISK`: A project v2 that is at risk and encountering some challenges.
* `COMPLETE`: A project v2 that is complete.
* `INACTIVE`: A project v2 that is inactive.
* `OFF_TRACK`: A project v2 that is off track and needs attention.
* `ON_TRACK`: A project v2 that is on track with no risks.

## ProjectV2ViewLayout

The layout of a project v2 view.

### Values for `ProjectV2ViewLayout`

* `BOARD_LAYOUT`: Board layout.
* `ROADMAP_LAYOUT`: Roadmap layout.
* `TABLE_LAYOUT`: Table layout.

## ProjectV2ViewOrderField

Properties by which project v2 view connections can be ordered.

### Values for `ProjectV2ViewOrderField`

* `CREATED_AT`: Order project v2 views by creation time.
* `NAME`: Order project v2 views by name.
* `POSITION`: Order project v2 views by position.

## ProjectV2WorkflowsOrderField

Properties by which project workflows can be ordered.

### Values for `ProjectV2WorkflowsOrderField`

* `CREATED_AT`: The date and time of the workflow creation.
* `NAME`: The name of the workflow.
* `NUMBER`: The number of the workflow.
* `UPDATED_AT`: The date and time of the workflow update.

## PullRequestAllowedMergeMethods

Array of allowed merge methods. Allowed values include merge, squash, and rebase. At least one option must be enabled.

### Values for `PullRequestAllowedMergeMethods`

* `MERGE`: Add all commits from the head branch to the base branch with a merge commit.
* `REBASE`: Add all commits from the head branch onto the base branch individually.
* `SQUASH`: Combine all commits from the head branch into a single commit in the base branch.

## PullRequestBranchUpdateMethod

The possible methods for updating a pull request's head branch with the base branch.

### Values for `PullRequestBranchUpdateMethod`

* `MERGE`: Update branch via merge.
* `REBASE`: Update branch via rebase.

## PullRequestCreationPolicy

The policy controlling who can create pull requests in a repository.

### Values for `PullRequestCreationPolicy`

* `ALL`: Anyone can create pull requests.
* `COLLABORATORS_ONLY`: Only collaborators can create pull requests.

## PullRequestMergeMethod

Represents available types of methods to use when merging a pull request.

### Values for `PullRequestMergeMethod`

* `MERGE`: Add all commits from the head branch to the base branch with a merge commit.
* `REBASE`: Add all commits from the head branch onto the base branch individually.
* `SQUASH`: Combine all commits from the head branch into a single commit in the base branch.

## PullRequestOrderField

Properties by which pull\_requests connections can be ordered.

### Values for `PullRequestOrderField`

* `CREATED_AT`: Order pull\_requests by creation time.
* `UPDATED_AT`: Order pull\_requests by update time.

## PullRequestReviewCommentState

The possible states of a pull request review comment.

### Values for `PullRequestReviewCommentState`

* `PENDING`: A comment that is part of a pending review.
* `SUBMITTED`: A comment that is part of a submitted review.

## PullRequestReviewDecision

The review status of a pull request.

### Values for `PullRequestReviewDecision`

* `APPROVED`: The pull request has received an approving review.
* `CHANGES_REQUESTED`: Changes have been requested on the pull request.
* `REVIEW_REQUIRED`: A review is required before the pull request can be merged.

## PullRequestReviewEvent

The possible events to perform on a pull request review.

### Values for `PullRequestReviewEvent`

* `APPROVE`: Submit feedback and approve merging these changes.
* `COMMENT`: Submit general feedback without explicit approval.
* `DISMISS`: Dismiss review so it now longer effects merging.
* `REQUEST_CHANGES`: Submit feedback that must be addressed before merging.

## PullRequestReviewState

The possible states of a pull request review.

### Values for `PullRequestReviewState`

* `APPROVED`: A review allowing the pull request to merge.
* `CHANGES_REQUESTED`: A review blocking the pull request from merging.
* `COMMENTED`: An informational review.
* `DISMISSED`: A review that has been dismissed.
* `PENDING`: A review that has not yet been submitted.

## PullRequestReviewThreadSubjectType

The possible subject types of a pull request review comment.

### Values for `PullRequestReviewThreadSubjectType`

* `FILE`: A comment that has been made against the file of a pull request.
* `LINE`: A comment that has been made against the line of a pull request.

## PullRequestState

The possible states of a pull request.

### Values for `PullRequestState`

* `CLOSED`: A pull request that has been closed without being merged.
* `MERGED`: A pull request that has been closed by being merged.
* `OPEN`: A pull request that is still open.

## PullRequestTimelineItemsItemType

The possible item types found in a timeline.

### Values for `PullRequestTimelineItemsItemType`

* `ADDED_TO_MERGE_QUEUE_EVENT`: Represents anadded\_to\_merge\_queueevent on a given pull request.
* `ADDED_TO_PROJECT_EVENT`: Represents aadded\_to\_projectevent on a given issue or pull request.
* `ADDED_TO_PROJECT_V2_EVENT`: Represents aadded\_to\_project\_v2event on a given issue or pull request.
* `ASSIGNED_EVENT`: Represents anassignedevent on any assignable object.
* `AUTOMATIC_BASE_CHANGE_FAILED_EVENT`: Represents aautomatic\_base\_change\_failedevent on a given pull request.
* `AUTOMATIC_BASE_CHANGE_SUCCEEDED_EVENT`: Represents aautomatic\_base\_change\_succeededevent on a given pull request.
* `AUTO_MERGE_DISABLED_EVENT`: Represents aauto\_merge\_disabledevent on a given pull request.
* `AUTO_MERGE_ENABLED_EVENT`: Represents aauto\_merge\_enabledevent on a given pull request.
* `AUTO_REBASE_ENABLED_EVENT`: Represents aauto\_rebase\_enabledevent on a given pull request.
* `AUTO_SQUASH_ENABLED_EVENT`: Represents aauto\_squash\_enabledevent on a given pull request.
* `BASE_REF_CHANGED_EVENT`: Represents abase\_ref\_changedevent on a given issue or pull request.
* `BASE_REF_DELETED_EVENT`: Represents abase\_ref\_deletedevent on a given pull request.
* `BASE_REF_FORCE_PUSHED_EVENT`: Represents abase\_ref\_force\_pushedevent on a given pull request.
* `BLOCKED_BY_ADDED_EVENT`: Represents ablocked\_by\_addedevent on a given issue.
* `BLOCKED_BY_REMOVED_EVENT`: Represents ablocked\_by\_removedevent on a given issue.
* `BLOCKING_ADDED_EVENT`: Represents ablocking\_addedevent on a given issue.
* `BLOCKING_REMOVED_EVENT`: Represents ablocking\_removedevent on a given issue.
* `CLOSED_EVENT`: Represents aclosedevent on any Closable.
* `COMMENT_DELETED_EVENT`: Represents acomment\_deletedevent on a given issue or pull request.
* `CONNECTED_EVENT`: Represents aconnectedevent on a given issue or pull request.
* `CONVERTED_FROM_DRAFT_EVENT`: Represents aconverted\_from\_draftevent on a given issue or pull request.
* `CONVERTED_NOTE_TO_ISSUE_EVENT`: Represents aconverted\_note\_to\_issueevent on a given issue or pull request.
* `CONVERTED_TO_DISCUSSION_EVENT`: Represents aconverted\_to\_discussionevent on a given issue.
* `CONVERT_TO_DRAFT_EVENT`: Represents aconvert\_to\_draftevent on a given pull request.
* `CROSS_REFERENCED_EVENT`: Represents a mention made by one issue or pull request to another.
* `DEMILESTONED_EVENT`: Represents ademilestonedevent on a given issue or pull request.
* `DEPLOYED_EVENT`: Represents adeployedevent on a given pull request.
* `DEPLOYMENT_ENVIRONMENT_CHANGED_EVENT`: Represents adeployment\_environment\_changedevent on a given pull request.
* `DISCONNECTED_EVENT`: Represents adisconnectedevent on a given issue or pull request.
* `HEAD_REF_DELETED_EVENT`: Represents ahead\_ref\_deletedevent on a given pull request.
* `HEAD_REF_FORCE_PUSHED_EVENT`: Represents ahead\_ref\_force\_pushedevent on a given pull request.
* `HEAD_REF_RESTORED_EVENT`: Represents ahead\_ref\_restoredevent on a given pull request.
* `ISSUE_COMMENT`: Represents a comment on an Issue.
* `ISSUE_COMMENT_PINNED_EVENT`: Represents aissue\_comment\_pinnedevent on a given issue.
* `ISSUE_COMMENT_UNPINNED_EVENT`: Represents aissue\_comment\_unpinnedevent on a given issue.
* `ISSUE_FIELD_ADDED_EVENT`: Represents aissue\_field\_addedevent on a given issue.
* `ISSUE_FIELD_CHANGED_EVENT`: Represents aissue\_field\_changedevent on a given issue.
* `ISSUE_FIELD_REMOVED_EVENT`: Represents aissue\_field\_removedevent on a given issue.
* `ISSUE_TYPE_ADDED_EVENT`: Represents aissue\_type\_addedevent on a given issue.
* `ISSUE_TYPE_CHANGED_EVENT`: Represents aissue\_type\_changedevent on a given issue.
* `ISSUE_TYPE_REMOVED_EVENT`: Represents aissue\_type\_removedevent on a given issue.
* `LABELED_EVENT`: Represents alabeledevent on a given issue or pull request.
* `LOCKED_EVENT`: Represents alockedevent on a given issue or pull request.
* `MARKED_AS_DUPLICATE_EVENT`: Represents amarked\_as\_duplicateevent on a given issue or pull request.
* `MENTIONED_EVENT`: Represents amentionedevent on a given issue or pull request.
* `MERGED_EVENT`: Represents amergedevent on a given pull request.
* `MILESTONED_EVENT`: Represents amilestonedevent on a given issue or pull request.
* `MOVED_COLUMNS_IN_PROJECT_EVENT`: Represents amoved\_columns\_in\_projectevent on a given issue or pull request.
* `PARENT_ISSUE_ADDED_EVENT`: Represents aparent\_issue\_addedevent on a given issue.
* `PARENT_ISSUE_REMOVED_EVENT`: Represents aparent\_issue\_removedevent on a given issue.
* `PINNED_EVENT`: Represents apinnedevent on a given issue or pull request.
* `PROJECT_V2_ITEM_STATUS_CHANGED_EVENT`: Represents aproject\_v2\_item\_status\_changedevent on a given issue or pull request.
* `PULL_REQUEST_COMMIT`: Represents a Git commit part of a pull request.
* `PULL_REQUEST_COMMIT_COMMENT_THREAD`: Represents a commit comment thread part of a pull request.
* `PULL_REQUEST_REVIEW`: A review object for a given pull request.
* `PULL_REQUEST_REVIEW_THREAD`: A threaded list of comments for a given pull request.
* `PULL_REQUEST_REVISION_MARKER`: Represents the latest point in the pull request timeline for which the viewer has seen the pull request's commits.
* `READY_FOR_REVIEW_EVENT`: Represents aready\_for\_reviewevent on a given pull request.
* `REFERENCED_EVENT`: Represents areferencedevent on a given ReferencedSubject.
* `REMOVED_FROM_MERGE_QUEUE_EVENT`: Represents aremoved\_from\_merge\_queueevent on a given pull request.
* `REMOVED_FROM_PROJECT_EVENT`: Represents aremoved\_from\_projectevent on a given issue or pull request.
* `REMOVED_FROM_PROJECT_V2_EVENT`: Represents aremoved\_from\_project\_v2event on a given issue or pull request.
* `RENAMED_TITLE_EVENT`: Represents arenamedevent on a given issue or pull request.
* `REOPENED_EVENT`: Represents areopenedevent on any Closable.
* `REVIEW_DISMISSED_EVENT`: Represents areview\_dismissedevent on a given issue or pull request.
* `REVIEW_REQUESTED_EVENT`: Represents anreview\_requestedevent on a given pull request.
* `REVIEW_REQUEST_REMOVED_EVENT`: Represents anreview\_request\_removedevent on a given pull request.
* `SUBSCRIBED_EVENT`: Represents asubscribedevent on a given Subscribable.
* `SUB_ISSUE_ADDED_EVENT`: Represents asub\_issue\_addedevent on a given issue.
* `SUB_ISSUE_REMOVED_EVENT`: Represents asub\_issue\_removedevent on a given issue.
* `TRANSFERRED_EVENT`: Represents atransferredevent on a given issue or pull request.
* `UNASSIGNED_EVENT`: Represents anunassignedevent on any assignable object.
* `UNLABELED_EVENT`: Represents anunlabeledevent on a given issue or pull request.
* `UNLOCKED_EVENT`: Represents anunlockedevent on a given issue or pull request.
* `UNMARKED_AS_DUPLICATE_EVENT`: Represents anunmarked\_as\_duplicateevent on a given issue or pull request.
* `UNPINNED_EVENT`: Represents anunpinnedevent on a given issue or pull request.
* `UNSUBSCRIBED_EVENT`: Represents anunsubscribedevent on a given Subscribable.
* `USER_BLOCKED_EVENT`: Represents auser\_blockedevent on a given user.

## PullRequestUpdateState

The possible target states when updating a pull request.

### Values for `PullRequestUpdateState`

* `CLOSED`: A pull request that has been closed without being merged.
* `OPEN`: A pull request that is still open.

## ReactionContent

Emojis that can be attached to Issues, Pull Requests and Comments.

### Values for `ReactionContent`

* `CONFUSED`: Represents the :confused: emoji.
* `EYES`: Represents the :eyes: emoji.
* `HEART`: Represents the :heart: emoji.
* `HOORAY`: Represents the :hooray: emoji.
* `LAUGH`: Represents the :laugh: emoji.
* `ROCKET`: Represents the :rocket: emoji.
* `THUMBS_DOWN`: Represents the :-1: emoji.
* `THUMBS_UP`: Represents the :+1: emoji.

## ReactionOrderField

A list of fields that reactions can be ordered by.

### Values for `ReactionOrderField`

* `CREATED_AT`: Allows ordering a list of reactions by when they were created.

## RefOrderField

Properties by which ref connections can be ordered.

### Values for `RefOrderField`

* `ALPHABETICAL`: Order refs by their alphanumeric name.
* `TAG_COMMIT_DATE`: Order refs by underlying commit date if the ref prefix is refs/tags/.

## ReleaseOrderField

Properties by which release connections can be ordered.

### Values for `ReleaseOrderField`

* `CREATED_AT`: Order releases by creation time.
* `NAME`: Order releases alphabetically by name.

## RepoAccessAuditEntryVisibility

The privacy of a repository.

### Values for `RepoAccessAuditEntryVisibility`

* `INTERNAL`: The repository is visible only to users in the same enterprise.
* `PRIVATE`: The repository is visible only to those with explicit access.
* `PUBLIC`: The repository is visible to everyone.

## RepoAddMemberAuditEntryVisibility

The privacy of a repository.

### Values for `RepoAddMemberAuditEntryVisibility`

* `INTERNAL`: The repository is visible only to users in the same enterprise.
* `PRIVATE`: The repository is visible only to those with explicit access.
* `PUBLIC`: The repository is visible to everyone.

## RepoArchivedAuditEntryVisibility

The privacy of a repository.

### Values for `RepoArchivedAuditEntryVisibility`

* `INTERNAL`: The repository is visible only to users in the same enterprise.
* `PRIVATE`: The repository is visible only to those with explicit access.
* `PUBLIC`: The repository is visible to everyone.

## RepoChangeMergeSettingAuditEntryMergeType

The merge options available for pull requests to this repository.

### Values for `RepoChangeMergeSettingAuditEntryMergeType`

* `MERGE`: The pull request is added to the base branch in a merge commit.
* `REBASE`: Commits from the pull request are added onto the base branch individually without a merge commit.
* `SQUASH`: The pull request's commits are squashed into a single commit before they are merged to the base branch.

## RepoCreateAuditEntryVisibility

The privacy of a repository.

### Values for `RepoCreateAuditEntryVisibility`

* `INTERNAL`: The repository is visible only to users in the same enterprise.
* `PRIVATE`: The repository is visible only to those with explicit access.
* `PUBLIC`: The repository is visible to everyone.

## RepoDestroyAuditEntryVisibility

The privacy of a repository.

### Values for `RepoDestroyAuditEntryVisibility`

* `INTERNAL`: The repository is visible only to users in the same enterprise.
* `PRIVATE`: The repository is visible only to those with explicit access.
* `PUBLIC`: The repository is visible to everyone.

## RepoRemoveMemberAuditEntryVisibility

The privacy of a repository.

### Values for `RepoRemoveMemberAuditEntryVisibility`

* `INTERNAL`: The repository is visible only to users in the same enterprise.
* `PRIVATE`: The repository is visible only to those with explicit access.
* `PUBLIC`: The repository is visible to everyone.

## ReportedContentClassifiers

The reasons a piece of content can be reported or minimized.

### Values for `ReportedContentClassifiers`

* `ABUSE`: An abusive or harassing piece of content.
* `DUPLICATE`: A duplicated piece of content.
* `OFF_TOPIC`: An irrelevant piece of content.
* `OUTDATED`: An outdated piece of content.
* `RESOLVED`: The content has been resolved.
* `SPAM`: A spammy piece of content.

## RepositoryAffiliation

The affiliation of a user to a repository.

### Values for `RepositoryAffiliation`

* `COLLABORATOR`: Repositories that the user has been added to as a collaborator.
* `ORGANIZATION_MEMBER`: Repositories that the user has access to through being a member of an
  organization. This includes every repository on every team that the user is on.
* `OWNER`: Repositories that are owned by the authenticated user.

## RepositoryContributionType

The reason a repository is listed as 'contributed'.

### Values for `RepositoryContributionType`

* `COMMIT`: Created a commit.
* `ISSUE`: Created an issue.
* `PULL_REQUEST`: Created a pull request.
* `PULL_REQUEST_REVIEW`: Reviewed a pull request.
* `REPOSITORY`: Created the repository.

## RepositoryCustomPropertyValuesEditableBy

The allowed actors who can edit the values of a custom property.

### Values for `RepositoryCustomPropertyValuesEditableBy`

* `ORG_ACTORS`: The organization actors.
* `ORG_AND_REPO_ACTORS`: The organization and repository actors.

## RepositoryInteractionLimit

A repository interaction limit.

### Values for `RepositoryInteractionLimit`

* `COLLABORATORS_ONLY`: Users that are not collaborators will not be able to interact with the repository.
* `CONTRIBUTORS_ONLY`: Users that have not previously committed to a repository’s default branch will be unable to interact with the repository.
* `EXISTING_USERS`: Users that have recently created their account will be unable to interact with the repository.
* `NO_LIMIT`: No interaction limits are enabled.

## RepositoryInteractionLimitExpiry

The length for a repository interaction limit to be enabled for.

### Values for `RepositoryInteractionLimitExpiry`

* `ONE_DAY`: The interaction limit will expire after 1 day.
* `ONE_MONTH`: The interaction limit will expire after 1 month.
* `ONE_WEEK`: The interaction limit will expire after 1 week.
* `SIX_MONTHS`: The interaction limit will expire after 6 months.
* `THREE_DAYS`: The interaction limit will expire after 3 days.

## RepositoryInteractionLimitOrigin

Indicates where an interaction limit is configured.

### Values for `RepositoryInteractionLimitOrigin`

* `ORGANIZATION`: A limit that is configured at the organization level.
* `REPOSITORY`: A limit that is configured at the repository level.
* `USER`: A limit that is configured at the user-wide level.

## RepositoryInvitationOrderField

Properties by which repository invitation connections can be ordered.

### Values for `RepositoryInvitationOrderField`

* `CREATED_AT`: Order repository invitations by creation time.

## RepositoryLockReason

The possible reasons a given repository could be in a locked state.

### Values for `RepositoryLockReason`

* `BILLING`: The repository is locked due to a billing related reason.
* `MIGRATING`: The repository is locked due to a migration.
* `MOVING`: The repository is locked due to a move.
* `RENAME`: The repository is locked due to a rename.
* `TRADE_RESTRICTION`: The repository is locked due to a trade controls related reason.
* `TRANSFERRING_OWNERSHIP`: The repository is locked due to an ownership transfer.

## RepositoryMigrationOrderDirection

Possible directions in which to order a list of repository migrations when provided an orderBy argument.

### Values for `RepositoryMigrationOrderDirection`

* `ASC`: Specifies an ascending order for a given orderBy argument.
* `DESC`: Specifies a descending order for a given orderBy argument.

## RepositoryMigrationOrderField

Properties by which repository migrations can be ordered.

### Values for `RepositoryMigrationOrderField`

* `CREATED_AT`: Order mannequins why when they were created.

## RepositoryOrderField

Properties by which repository connections can be ordered.

### Values for `RepositoryOrderField`

* `CREATED_AT`: Order repositories by creation time.
* `NAME`: Order repositories by name.
* `PUSHED_AT`: Order repositories by push time.
* `STARGAZERS`: Order repositories by number of stargazers.
* `UPDATED_AT`: Order repositories by update time.

## RepositoryPermission

The access level to a repository.

### Values for `RepositoryPermission`

* `ADMIN`: Can read, clone, and push to this repository. Can also manage issues, pull
  requests, and repository settings, including adding collaborators.
* `MAINTAIN`: Can read, clone, and push to this repository. They can also manage issues, pull requests, and some repository settings.
* `READ`: Can read and clone this repository. Can also open and comment on issues and pull requests.
* `TRIAGE`: Can read and clone this repository. Can also manage issues and pull requests.
* `WRITE`: Can read, clone, and push to this repository. Can also manage issues and pull requests.

## RepositoryPrivacy

The privacy of a repository.

### Values for `RepositoryPrivacy`

* `PRIVATE`: Private.
* `PUBLIC`: Public.

## RepositoryRuleOrderField

Properties by which repository rule connections can be ordered.

### Values for `RepositoryRuleOrderField`

* `CREATED_AT`: Order repository rules by created time.
* `TYPE`: Order repository rules by type.
* `UPDATED_AT`: Order repository rules by updated time.

## RepositoryRuleType

The rule types supported in rulesets.

### Values for `RepositoryRuleType`

* `AUTHORIZATION`: Authorization.
* `BRANCH_NAME_PATTERN`: Branch name pattern.
* `CODE_SCANNING`: Choose which tools must provide code scanning results before the reference is
  updated. When configured, code scanning must be enabled and have results for
  both the commit and the reference being updated.
* `COMMITTER_EMAIL_PATTERN`: Committer email pattern.
* `COMMIT_AUTHOR_EMAIL_PATTERN`: Commit author email pattern.
* `COMMIT_MESSAGE_PATTERN`: Commit message pattern.
* `COPILOT_CODE_REVIEW`: Request Copilot code review for new pull requests automatically if the author
  has access to Copilot code review and their premium requests quota has not
  reached the limit.
* `CREATION`: Only allow users with bypass permission to create matching refs.
* `DELETION`: Only allow users with bypass permissions to delete matching refs.
* `FILE_EXTENSION_RESTRICTION`: Prevent commits that include files with specified file extensions from being pushed to the commit graph.
* `FILE_PATH_RESTRICTION`: Prevent commits that include changes in specified file and folder paths from
  being pushed to the commit graph. This includes absolute paths that contain file names.
* `LOCK_BRANCH`: Branch is read-only. Users cannot push to the branch.
* `MAX_FILE_PATH_LENGTH`: Prevent commits that include file paths that exceed the specified character limit from being pushed to the commit graph.
* `MAX_FILE_SIZE`: Prevent commits with individual files that exceed the specified limit from being pushed to the commit graph.
* `MAX_REF_UPDATES`: Max ref updates.
* `MERGE_QUEUE`: Merges must be performed via a merge queue.
* `MERGE_QUEUE_LOCKED_REF`: Merge queue locked ref.
* `NON_FAST_FORWARD`: Prevent users with push access from force pushing to refs.
* `PULL_REQUEST`: Require all commits be made to a non-target branch and submitted via a pull request before they can be merged.
* `REQUIRED_DEPLOYMENTS`: Choose which environments must be successfully deployed to before refs can be pushed into a ref that matches this rule.
* `REQUIRED_LINEAR_HISTORY`: Prevent merge commits from being pushed to matching refs.
* `REQUIRED_REVIEW_THREAD_RESOLUTION`: When enabled, all conversations on code must be resolved before a pull request
  can be merged into a branch that matches this rule.
* `REQUIRED_SIGNATURES`: Commits pushed to matching refs must have verified signatures.
* `REQUIRED_STATUS_CHECKS`: Choose which status checks must pass before the ref is updated. When enabled,
  commits must first be pushed to another ref where the checks pass.
* `REQUIRED_WORKFLOW_STATUS_CHECKS`: Require all commits be made to a non-target branch and submitted via a pull
  request and required workflow checks to pass before they can be merged.
* `SECRET_SCANNING`: Secret scanning.
* `TAG`: Tag.
* `TAG_NAME_PATTERN`: Tag name pattern.
* `UPDATE`: Only allow users with bypass permission to update matching refs.
* `WORKFLOWS`: Require all changes made to a targeted branch to pass the specified workflows before they can be merged.
* `WORKFLOW_UPDATES`: Workflow files cannot be modified.

## RepositoryRulesetBypassActorBypassMode

The bypass mode for a specific actor on a ruleset.

### Values for `RepositoryRulesetBypassActorBypassMode`

* `ALWAYS`: The actor can always bypass rules.
* `EXEMPT`: The actor is exempt from rules without generating a pass / fail result.
* `PULL_REQUEST`: The actor can only bypass rules via a pull request.

## RepositoryRulesetTarget

The targets supported for rulesets.

### Values for `RepositoryRulesetTarget`

* `BRANCH`: Branch.
* `PUSH`: Push.
* `REPOSITORY`: repository.
* `TAG`: Tag.

## RepositorySuggestedActorFilter

The possible filters for suggested actors in a repository.

### Values for `RepositorySuggestedActorFilter`

* `CAN_BE_ASSIGNED`: Actors that can be assigned to issues and pull requests.
* `CAN_BE_AUTHOR`: Actors that can be the author of issues and pull requests.

## RepositoryVisibility

The repository's visibility level.

### Values for `RepositoryVisibility`

* `INTERNAL`: The repository is visible only to users in the same enterprise.
* `PRIVATE`: The repository is visible only to those with explicit access.
* `PUBLIC`: The repository is visible to everyone.

## RepositoryVulnerabilityAlertDependencyRelationship

The possible relationships of an alert's dependency.

### Values for `RepositoryVulnerabilityAlertDependencyRelationship`

* `DIRECT`: A direct dependency of your project.
* `INCONCLUSIVE`: The relationship could not be determined.
* `TRANSITIVE`: A transitive dependency of your project.
* `UNKNOWN`: The relationship is unknown.

## RepositoryVulnerabilityAlertDependencyScope

The possible scopes of an alert's dependency.

### Values for `RepositoryVulnerabilityAlertDependencyScope`

* `DEVELOPMENT`: A dependency that is only used in development.
* `RUNTIME`: A dependency that is leveraged during application runtime.

## RepositoryVulnerabilityAlertState

The possible states of an alert.

### Values for `RepositoryVulnerabilityAlertState`

* `AUTO_DISMISSED`: An alert that has been automatically closed by Dependabot.
* `DISMISSED`: An alert that has been manually closed by a user.
* `FIXED`: An alert that has been resolved by a code change.
* `OPEN`: An alert that is still open.

## RequestableCheckStatusState

The possible states that can be requested when creating a check run.

### Values for `RequestableCheckStatusState`

* `COMPLETED`: The check suite or run has been completed.
* `IN_PROGRESS`: The check suite or run is in progress.
* `PENDING`: The check suite or run is in pending state.
* `QUEUED`: The check suite or run has been queued.
* `WAITING`: The check suite or run is in waiting state.

## RoleInOrganization

Possible roles a user may have in relation to an organization.

### Values for `RoleInOrganization`

* `DIRECT_MEMBER`: A user who is a direct member of the organization.
* `OWNER`: A user with full administrative access to the organization.
* `UNAFFILIATED`: A user who is unaffiliated with the organization.

## RuleEnforcement

The level of enforcement for a rule or ruleset.

### Values for `RuleEnforcement`

* `ACTIVE`: Rules will be enforced.
* `DISABLED`: Do not evaluate or enforce rules.
* `EVALUATE`: Allow admins to test rules before enforcing them. Admins can view insights on
  the Rule Insights page (evaluate is only available with GitHub Enterprise).

## SamlDigestAlgorithm

The possible digest algorithms used to sign SAML requests for an identity provider.

### Values for `SamlDigestAlgorithm`

* `SHA1`: SHA1.
* `SHA256`: SHA256.
* `SHA384`: SHA384.
* `SHA512`: SHA512.

## SamlSignatureAlgorithm

The possible signature algorithms used to sign SAML requests for a Identity Provider.

### Values for `SamlSignatureAlgorithm`

* `RSA_SHA1`: RSA-SHA1.
* `RSA_SHA256`: RSA-SHA256.
* `RSA_SHA384`: RSA-SHA384.
* `RSA_SHA512`: RSA-SHA512.

## SavedReplyOrderField

Properties by which saved reply connections can be ordered.

### Values for `SavedReplyOrderField`

* `UPDATED_AT`: Order saved reply by when they were updated.

## SearchType

Represents the individual results of a search.

### Values for `SearchType`

* `DISCUSSION`: Returns matching discussions in repositories.
* `ISSUE`: Returns results matching issues in repositories.
* `ISSUE_ADVANCED`: Returns results matching issues in repositories.
* `ISSUE_HYBRID`: Returns results matching issues using hybrid (lexical + semantic) search.
* `ISSUE_SEMANTIC`: Returns results matching issues using semantic search.
* `REPOSITORY`: Returns results matching repositories.
* `USER`: Returns results matching users and organizations on GitHub.

## SecurityAdvisoryClassification

Classification of the advisory.

### Values for `SecurityAdvisoryClassification`

* `GENERAL`: Classification of general advisories.
* `MALWARE`: Classification of malware advisories.

## SecurityAdvisoryEcosystem

The possible ecosystems of a security vulnerability's package.

### Values for `SecurityAdvisoryEcosystem`

* `ACTIONS`: GitHub Actions.
* `COMPOSER`: PHP packages hosted at packagist.org.
* `ERLANG`: Erlang/Elixir packages hosted at hex.pm.
* `GO`: Go modules.
* `MAVEN`: Java artifacts hosted at the Maven central repository.
* `NPM`: JavaScript packages hosted at npmjs.com.
* `NUGET`: .NET packages hosted at the NuGet Gallery.
* `PIP`: Python packages hosted at PyPI.org.
* `PUB`: Dart packages hosted at pub.dev.
* `RUBYGEMS`: Ruby gems hosted at RubyGems.org.
* `RUST`: Rust crates.
* `SWIFT`: Swift packages.

## SecurityAdvisoryIdentifierType

Identifier formats available for advisories.

### Values for `SecurityAdvisoryIdentifierType`

* `CVE`: Common Vulnerabilities and Exposures Identifier.
* `GHSA`: GitHub Security Advisory ID.

## SecurityAdvisoryOrderField

Properties by which security advisory connections can be ordered.

### Values for `SecurityAdvisoryOrderField`

* `EPSS_PERCENTAGE`: Order advisories by EPSS percentage.
* `EPSS_PERCENTILE`: Order advisories by EPSS percentile.
* `PUBLISHED_AT`: Order advisories by publication time.
* `UPDATED_AT`: Order advisories by update time.

## SecurityAdvisorySeverity

Severity of the vulnerability.

### Values for `SecurityAdvisorySeverity`

* `CRITICAL`: Critical.
* `HIGH`: High.
* `LOW`: Low.
* `MODERATE`: Moderate.

## SecurityVulnerabilityOrderField

Properties by which security vulnerability connections can be ordered.

### Values for `SecurityVulnerabilityOrderField`

* `UPDATED_AT`: Order vulnerability by update time.

## SocialAccountProvider

Software or company that hosts social media accounts.

### Values for `SocialAccountProvider`

* `BLUESKY`: Decentralized microblogging social platform.
* `FACEBOOK`: Social media and networking website.
* `GENERIC`: Catch-all for social media providers that do not yet have specific handling.
* `HOMETOWN`: Fork of Mastodon with a greater focus on local posting.
* `INSTAGRAM`: Social media website with a focus on photo and video sharing.
* `LINKEDIN`: Professional networking website.
* `MASTODON`: Open-source federated microblogging service.
* `NPM`: JavaScript package registry.
* `REDDIT`: Social news aggregation and discussion website.
* `TWITCH`: Live-streaming service.
* `TWITTER`: Microblogging website.
* `YOUTUBE`: Online video platform.

## SponsorAndLifetimeValueOrderField

Properties by which sponsor and lifetime value connections can be ordered.

### Values for `SponsorAndLifetimeValueOrderField`

* `LIFETIME_VALUE`: Order results by how much money the sponsor has paid in total.
* `SPONSOR_LOGIN`: Order results by the sponsor's login (username).
* `SPONSOR_RELEVANCE`: Order results by the sponsor's relevance to the viewer.

## SponsorOrderField

Properties by which sponsor connections can be ordered.

### Values for `SponsorOrderField`

* `LOGIN`: Order sponsorable entities by login (username).
* `RELEVANCE`: Order sponsors by their relevance to the viewer.

## SponsorableOrderField

Properties by which sponsorable connections can be ordered.

### Values for `SponsorableOrderField`

* `LOGIN`: Order sponsorable entities by login (username).

## SponsorsActivityAction

The possible actions that GitHub Sponsors activities can represent.

### Values for `SponsorsActivityAction`

* `CANCELLED_SPONSORSHIP`: The activity was cancelling a sponsorship.
* `NEW_SPONSORSHIP`: The activity was starting a sponsorship.
* `PENDING_CHANGE`: The activity was scheduling a downgrade or cancellation.
* `REFUND`: The activity was funds being refunded to the sponsor or GitHub.
* `SPONSOR_MATCH_DISABLED`: The activity was disabling matching for a previously matched sponsorship.
* `TIER_CHANGE`: The activity was changing the sponsorship tier, either directly by the sponsor or by a scheduled/pending change.

## SponsorsActivityOrderField

Properties by which GitHub Sponsors activity connections can be ordered.

### Values for `SponsorsActivityOrderField`

* `TIMESTAMP`: Order activities by when they happened.

## SponsorsActivityPeriod

The possible time periods for which Sponsors activities can be requested.

### Values for `SponsorsActivityPeriod`

* `ALL`: Don't restrict the activity to any date range, include all activity.
* `DAY`: The previous calendar day.
* `MONTH`: The previous thirty days.
* `WEEK`: The previous seven days.

## SponsorsCountryOrRegionCode

Represents countries or regions for billing and residence for a GitHub Sponsors profile.

### Values for `SponsorsCountryOrRegionCode`

* `AD`: Andorra.
* `AE`: United Arab Emirates.
* `AF`: Afghanistan.
* `AG`: Antigua and Barbuda.
* `AI`: Anguilla.
* `AL`: Albania.
* `AM`: Armenia.
* `AO`: Angola.
* `AQ`: Antarctica.
* `AR`: Argentina.
* `AS`: American Samoa.
* `AT`: Austria.
* `AU`: Australia.
* `AW`: Aruba.
* `AX`: Åland.
* `AZ`: Azerbaijan.
* `BA`: Bosnia and Herzegovina.
* `BB`: Barbados.
* `BD`: Bangladesh.
* `BE`: Belgium.
* `BF`: Burkina Faso.
* `BG`: Bulgaria.
* `BH`: Bahrain.
* `BI`: Burundi.
* `BJ`: Benin.
* `BL`: Saint Barthélemy.
* `BM`: Bermuda.
* `BN`: Brunei Darussalam.
* `BO`: Bolivia.
* `BQ`: Bonaire, Sint Eustatius and Saba.
* `BR`: Brazil.
* `BS`: Bahamas.
* `BT`: Bhutan.
* `BV`: Bouvet Island.
* `BW`: Botswana.
* `BY`: Belarus.
* `BZ`: Belize.
* `CA`: Canada.
* `CC`: Cocos (Keeling) Islands.
* `CD`: Congo (Kinshasa).
* `CF`: Central African Republic.
* `CG`: Congo (Brazzaville).
* `CH`: Switzerland.
* `CI`: Côte d'Ivoire.
* `CK`: Cook Islands.
* `CL`: Chile.
* `CM`: Cameroon.
* `CN`: China.
* `CO`: Colombia.
* `CR`: Costa Rica.
* `CV`: Cape Verde.
* `CW`: Curaçao.
* `CX`: Christmas Island.
* `CY`: Cyprus.
* `CZ`: Czech Republic.
* `DE`: Germany.
* `DJ`: Djibouti.
* `DK`: Denmark.
* `DM`: Dominica.
* `DO`: Dominican Republic.
* `DZ`: Algeria.
* `EC`: Ecuador.
* `EE`: Estonia.
* `EG`: Egypt.
* `EH`: Western Sahara.
* `ER`: Eritrea.
* `ES`: Spain.
* `ET`: Ethiopia.
* `FI`: Finland.
* `FJ`: Fiji.
* `FK`: Falkland Islands.
* `FM`: Micronesia.
* `FO`: Faroe Islands.
* `FR`: France.
* `GA`: Gabon.
* `GB`: United Kingdom.
* `GD`: Grenada.
* `GE`: Georgia.
* `GF`: French Guiana.
* `GG`: Guernsey.
* `GH`: Ghana.
* `GI`: Gibraltar.
* `GL`: Greenland.
* `GM`: Gambia.
* `GN`: Guinea.
* `GP`: Guadeloupe.
* `GQ`: Equatorial Guinea.
* `GR`: Greece.
* `GS`: South Georgia and South Sandwich Islands.
* `GT`: Guatemala.
* `GU`: Guam.
* `GW`: Guinea-Bissau.
* `GY`: Guyana.
* `HK`: Hong Kong.
* `HM`: Heard and McDonald Islands.
* `HN`: Honduras.
* `HR`: Croatia.
* `HT`: Haiti.
* `HU`: Hungary.
* `ID`: Indonesia.
* `IE`: Ireland.
* `IL`: Israel.
* `IM`: Isle of Man.
* `IN`: India.
* `IO`: British Indian Ocean Territory.
* `IQ`: Iraq.
* `IR`: Iran.
* `IS`: Iceland.
* `IT`: Italy.
* `JE`: Jersey.
* `JM`: Jamaica.
* `JO`: Jordan.
* `JP`: Japan.
* `KE`: Kenya.
* `KG`: Kyrgyzstan.
* `KH`: Cambodia.
* `KI`: Kiribati.
* `KM`: Comoros.
* `KN`: Saint Kitts and Nevis.
* `KR`: Korea, South.
* `KW`: Kuwait.
* `KY`: Cayman Islands.
* `KZ`: Kazakhstan.
* `LA`: Laos.
* `LB`: Lebanon.
* `LC`: Saint Lucia.
* `LI`: Liechtenstein.
* `LK`: Sri Lanka.
* `LR`: Liberia.
* `LS`: Lesotho.
* `LT`: Lithuania.
* `LU`: Luxembourg.
* `LV`: Latvia.
* `LY`: Libya.
* `MA`: Morocco.
* `MC`: Monaco.
* `MD`: Moldova.
* `ME`: Montenegro.
* `MF`: Saint Martin (French part).
* `MG`: Madagascar.
* `MH`: Marshall Islands.
* `MK`: Macedonia.
* `ML`: Mali.
* `MM`: Myanmar.
* `MN`: Mongolia.
* `MO`: Macau.
* `MP`: Northern Mariana Islands.
* `MQ`: Martinique.
* `MR`: Mauritania.
* `MS`: Montserrat.
* `MT`: Malta.
* `MU`: Mauritius.
* `MV`: Maldives.
* `MW`: Malawi.
* `MX`: Mexico.
* `MY`: Malaysia.
* `MZ`: Mozambique.
* `NA`: Namibia.
* `NC`: New Caledonia.
* `NE`: Niger.
* `NF`: Norfolk Island.
* `NG`: Nigeria.
* `NI`: Nicaragua.
* `NL`: Netherlands.
* `NO`: Norway.
* `NP`: Nepal.
* `NR`: Nauru.
* `NU`: Niue.
* `NZ`: New Zealand.
* `OM`: Oman.
* `PA`: Panama.
* `PE`: Peru.
* `PF`: French Polynesia.
* `PG`: Papua New Guinea.
* `PH`: Philippines.
* `PK`: Pakistan.
* `PL`: Poland.
* `PM`: Saint Pierre and Miquelon.
* `PN`: Pitcairn.
* `PR`: Puerto Rico.
* `PS`: Palestine.
* `PT`: Portugal.
* `PW`: Palau.
* `PY`: Paraguay.
* `QA`: Qatar.
* `RE`: Reunion.
* `RO`: Romania.
* `RS`: Serbia.
* `RU`: Russian Federation.
* `RW`: Rwanda.
* `SA`: Saudi Arabia.
* `SB`: Solomon Islands.
* `SC`: Seychelles.
* `SD`: Sudan.
* `SE`: Sweden.
* `SG`: Singapore.
* `SH`: Saint Helena.
* `SI`: Slovenia.
* `SJ`: Svalbard and Jan Mayen Islands.
* `SK`: Slovakia.
* `SL`: Sierra Leone.
* `SM`: San Marino.
* `SN`: Senegal.
* `SO`: Somalia.
* `SR`: Suriname.
* `SS`: South Sudan.
* `ST`: Sao Tome and Principe.
* `SV`: El Salvador.
* `SX`: Sint Maarten (Dutch part).
* `SY`: Syria.
* `SZ`: Swaziland.
* `TC`: Turks and Caicos Islands.
* `TD`: Chad.
* `TF`: French Southern Lands.
* `TG`: Togo.
* `TH`: Thailand.
* `TJ`: Tajikistan.
* `TK`: Tokelau.
* `TL`: Timor-Leste.
* `TM`: Turkmenistan.
* `TN`: Tunisia.
* `TO`: Tonga.
* `TR`: Türkiye.
* `TT`: Trinidad and Tobago.
* `TV`: Tuvalu.
* `TW`: Taiwan.
* `TZ`: Tanzania.
* `UA`: Ukraine.
* `UG`: Uganda.
* `UM`: United States Minor Outlying Islands.
* `US`: United States of America.
* `UY`: Uruguay.
* `UZ`: Uzbekistan.
* `VA`: Vatican City.
* `VC`: Saint Vincent and the Grenadines.
* `VE`: Venezuela.
* `VG`: Virgin Islands, British.
* `VI`: Virgin Islands, U.S.
* `VN`: Vietnam.
* `VU`: Vanuatu.
* `WF`: Wallis and Futuna Islands.
* `WS`: Samoa.
* `YE`: Yemen.
* `YT`: Mayotte.
* `ZA`: South Africa.
* `ZM`: Zambia.
* `ZW`: Zimbabwe.

## SponsorsGoalKind

The different kinds of goals a GitHub Sponsors member can have.

### Values for `SponsorsGoalKind`

* `MONTHLY_SPONSORSHIP_AMOUNT`: The goal is about getting a certain amount in USD from sponsorships each month.
* `TOTAL_SPONSORS_COUNT`: The goal is about reaching a certain number of sponsors.

## SponsorsListingFeaturedItemFeatureableType

The different kinds of records that can be featured on a GitHub Sponsors profile page.

### Values for `SponsorsListingFeaturedItemFeatureableType`

* `REPOSITORY`: A repository owned by the user or organization with the GitHub Sponsors profile.
* `USER`: A user who belongs to the organization with the GitHub Sponsors profile.

## SponsorsTierOrderField

Properties by which Sponsors tiers connections can be ordered.

### Values for `SponsorsTierOrderField`

* `CREATED_AT`: Order tiers by creation time.
* `MONTHLY_PRICE_IN_CENTS`: Order tiers by their monthly price in cents.

## SponsorshipNewsletterOrderField

Properties by which sponsorship update connections can be ordered.

### Values for `SponsorshipNewsletterOrderField`

* `CREATED_AT`: Order sponsorship newsletters by when they were created.

## SponsorshipOrderField

Properties by which sponsorship connections can be ordered.

### Values for `SponsorshipOrderField`

* `CREATED_AT`: Order sponsorship by creation time.

## SponsorshipPaymentSource

How payment was made for funding a GitHub Sponsors sponsorship.

### Values for `SponsorshipPaymentSource`

* `GITHUB`: Payment was made through GitHub.
* `PATREON`: Payment was made through Patreon.

## SponsorshipPrivacy

The privacy of a sponsorship.

### Values for `SponsorshipPrivacy`

* `PRIVATE`: Private.
* `PUBLIC`: Public.

## SquashMergeCommitMessage

The possible default commit messages for squash merges.

### Values for `SquashMergeCommitMessage`

* `BLANK`: Default to a blank commit message.
* `COMMIT_MESSAGES`: Default to the branch's commit messages.
* `PR_BODY`: Default to the pull request's body.

## SquashMergeCommitTitle

The possible default commit titles for squash merges.

### Values for `SquashMergeCommitTitle`

* `COMMIT_OR_PR_TITLE`: Default to the commit's title (if only one commit) or the pull request's title (when more than one commit).
* `PR_TITLE`: Default to the pull request's title.

## StarOrderField

Properties by which star connections can be ordered.

### Values for `StarOrderField`

* `STARRED_AT`: Allows ordering a list of stars by when they were created.

## StatusState

The possible commit status states.

### Values for `StatusState`

* `ERROR`: Status is errored.
* `EXPECTED`: Status is expected.
* `FAILURE`: Status is failing.
* `PENDING`: Status is pending.
* `SUCCESS`: Status is successful.

## SubscriptionState

The possible states of a subscription.

### Values for `SubscriptionState`

* `IGNORED`: The User is never notified.
* `SUBSCRIBED`: The User is notified of all conversations.
* `UNSUBSCRIBED`: The User is only notified when participating or @mentioned.

## TeamMemberOrderField

Properties by which team member connections can be ordered.

### Values for `TeamMemberOrderField`

* `CREATED_AT`: Order team members by creation time.
* `LOGIN`: Order team members by login.

## TeamMemberRole

The possible team member roles; eithermaintaineror 'member'.

### Values for `TeamMemberRole`

* `MAINTAINER`: A team maintainer has permission to add and remove team members.
* `MEMBER`: A team member has no administrative permissions on the team.

## TeamMembershipType

Defines which types of team members are included in the returned list. Can be one of IMMEDIATE, CHILD\_TEAM or ALL.

### Values for `TeamMembershipType`

* `ALL`: Includes immediate and child team members for the team.
* `CHILD_TEAM`: Includes only child team members for the team.
* `IMMEDIATE`: Includes only immediate members of the team.

## TeamNotificationSetting

The possible team notification values.

### Values for `TeamNotificationSetting`

* `NOTIFICATIONS_DISABLED`: No one will receive notifications.
* `NOTIFICATIONS_ENABLED`: Everyone will receive notifications when the team is @mentioned.

## TeamOrderField

Properties by which team connections can be ordered.

### Values for `TeamOrderField`

* `NAME`: Allows ordering a list of teams by name.

## TeamPrivacy

The possible team privacy values.

### Values for `TeamPrivacy`

* `SECRET`: A secret team can only be seen by its members.
* `VISIBLE`: A visible team can be seen and @mentioned by every member of the organization.

## TeamRepositoryOrderField

Properties by which team repository connections can be ordered.

### Values for `TeamRepositoryOrderField`

* `CREATED_AT`: Order repositories by creation time.
* `NAME`: Order repositories by name.
* `PERMISSION`: Order repositories by permission.
* `PUSHED_AT`: Order repositories by push time.
* `STARGAZERS`: Order repositories by number of stargazers.
* `UPDATED_AT`: Order repositories by update time.

## TeamReviewAssignmentAlgorithm

The possible team review assignment algorithms.

### Values for `TeamReviewAssignmentAlgorithm`

* `LOAD_BALANCE`: Balance review load across the entire team.
* `ROUND_ROBIN`: Alternate reviews between each team member.

## TeamRole

The role of a user on a team.

### Values for `TeamRole`

* `ADMIN`: User has admin rights on the team.
* `MEMBER`: User is a member of the team.

## ThreadSubscriptionFormAction

The possible states of a thread subscription form action.

### Values for `ThreadSubscriptionFormAction`

* `NONE`: The User cannot subscribe or unsubscribe to the thread.
* `SUBSCRIBE`: The User can subscribe to the thread.
* `UNSUBSCRIBE`: The User can unsubscribe to the thread.

## ThreadSubscriptionState

The possible states of a subscription.

### Values for `ThreadSubscriptionState`

* `DISABLED`: The subscription status is currently disabled.
* `IGNORING_LIST`: The User is never notified because they are ignoring the list.
* `IGNORING_THREAD`: The User is never notified because they are ignoring the thread.
* `NONE`: The User is not recieving notifications from this thread.
* `SUBSCRIBED_TO_LIST`: The User is notified becuase they are watching the list.
* `SUBSCRIBED_TO_THREAD`: The User is notified because they are subscribed to the thread.
* `SUBSCRIBED_TO_THREAD_EVENTS`: The User is notified because they chose custom settings for this thread.
* `SUBSCRIBED_TO_THREAD_TYPE`: The User is notified because they chose custom settings for this thread.
* `UNAVAILABLE`: The subscription status is currently unavailable.

## TopicSuggestionDeclineReason

Reason that the suggested topic is declined.

### Values for `TopicSuggestionDeclineReason`

* `NOT_RELEVANT`: The suggested topic is not relevant to the repository.
* `PERSONAL_PREFERENCE`: The viewer does not like the suggested topic.
* `TOO_GENERAL`: The suggested topic is too general for the repository.
* `TOO_SPECIFIC`: The suggested topic is too specific for the repository (e.g. #ruby-on-rails-version-4-2-1).

## TrackedIssueStates

The possible states of a tracked issue.

### Values for `TrackedIssueStates`

* `CLOSED`: The tracked issue is closed.
* `OPEN`: The tracked issue is open.

## TwoFactorCredentialSecurityType

Filters by whether or not 2FA is enabled and if the method configured is considered secure or insecure.

### Values for `TwoFactorCredentialSecurityType`

* `DISABLED`: No method of two-factor authentication.
* `INSECURE`: Has an insecure method of two-factor authentication. GitHub currently defines this as SMS two-factor authentication.
* `SECURE`: Has only secure methods of two-factor authentication.

## UserBlockDuration

The possible durations that a user can be blocked for.

### Values for `UserBlockDuration`

* `ONE_DAY`: The user was blocked for 1 day.
* `ONE_MONTH`: The user was blocked for 30 days.
* `ONE_WEEK`: The user was blocked for 7 days.
* `PERMANENT`: The user was blocked permanently.
* `THREE_DAYS`: The user was blocked for 3 days.

## UserStatusOrderField

Properties by which user status connections can be ordered.

### Values for `UserStatusOrderField`

* `UPDATED_AT`: Order user statuses by when they were updated.

## UserViewType

Whether a user being viewed contains public or private information.

### Values for `UserViewType`

* `PRIVATE`: A user containing information only visible to the authenticated user.
* `PUBLIC`: A user that is publicly visible.

## VerifiableDomainOrderField

Properties by which verifiable domain connections can be ordered.

### Values for `VerifiableDomainOrderField`

* `CREATED_AT`: Order verifiable domains by their creation date.
* `DOMAIN`: Order verifiable domains by the domain name.

## WorkflowRunOrderField

Properties by which workflow run connections can be ordered.

### Values for `WorkflowRunOrderField`

* `CREATED_AT`: Order workflow runs by most recently created.

## WorkflowState

The possible states for a workflow.

### Values for `WorkflowState`

* `ACTIVE`: The workflow is active.
* `DELETED`: The workflow was deleted from the git repository.
* `DISABLED_FORK`: The workflow was disabled by default on a fork.
* `DISABLED_INACTIVITY`: The workflow was disabled for inactivity in the repository.
* `DISABLED_MANUALLY`: The workflow was disabled manually.