# Changelog

The GraphQL schema changelog is a list of recent and upcoming changes to our GraphQL API schema. It includes backwards-compatible changes and upcoming breaking changes.

Breaking changes include changes that will break existing queries or could affect the runtime behavior of clients. For a list of breaking changes and when they will occur, see our [breaking changes log](/en/graphql/overview/breaking-changes).

## Schema changes for 2026-04-15

### The GraphQL schema includes these changes:

* Type ArchivePullRequestInput was added
* Input field clientMutationId of type String was added to input object type ArchivePullRequestInput
* Input field pullRequestId of type ID! was added to input object type ArchivePullRequestInput
* Type ArchivePullRequestPayload was added
* Field clientMutationId was added to object type ArchivePullRequestPayload
* Field pullRequest was added to object type ArchivePullRequestPayload
* Type UnarchivePullRequestInput was added
* Input field clientMutationId of type String was added to input object type UnarchivePullRequestInput
* Input field pullRequestId of type ID! was added to input object type UnarchivePullRequestInput
* Type UnarchivePullRequestPayload was added
* Field clientMutationId was added to object type UnarchivePullRequestPayload
* Field pullRequest was added to object type UnarchivePullRequestPayload
* Field archivePullRequest was added to object type Mutation
* Argument input: ArchivePullRequestInput! added to field Mutation.archivePullRequest
* Field unarchivePullRequest was added to object type Mutation
* Argument input: UnarchivePullRequestInput! added to field Mutation.unarchivePullRequest

## Schema changes for 2026-04-02

### The GraphQL schema includes these changes:

* Argument 'classifications: \[SecurityAdvisoryClassification!]added to fieldRepository.vulnerabilityAlerts'

## Schema changes for 2026-03-31

### The GraphQL schema includes these changes:

* Field value was added to object type IssueFieldSingleSelectValue

## Schema changes for 2026-03-30

### The GraphQL schema includes these changes:

* Type IssueFieldAddedEvent was added
* IssueFieldAddedEvent object implements Node interface
* Field actor was added to object type IssueFieldAddedEvent
* Field color was added to object type IssueFieldAddedEvent
* Field createdAt was added to object type IssueFieldAddedEvent
* Field id was added to object type IssueFieldAddedEvent
* Field issueField was added to object type IssueFieldAddedEvent
* Field value was added to object type IssueFieldAddedEvent
* Type IssueFieldChangedEvent was added
* IssueFieldChangedEvent object implements Node interface
* Field actor was added to object type IssueFieldChangedEvent
* Field createdAt was added to object type IssueFieldChangedEvent
* Field id was added to object type IssueFieldChangedEvent
* Field issueField was added to object type IssueFieldChangedEvent
* Field newColor was added to object type IssueFieldChangedEvent
* Field newValue was added to object type IssueFieldChangedEvent
* Field previousColor was added to object type IssueFieldChangedEvent
* Field previousValue was added to object type IssueFieldChangedEvent
* Type IssueFieldRemovedEvent was added
* IssueFieldRemovedEvent object implements Node interface
* Field actor was added to object type IssueFieldRemovedEvent
* Field createdAt was added to object type IssueFieldRemovedEvent
* Field id was added to object type IssueFieldRemovedEvent
* Field issueField was added to object type IssueFieldRemovedEvent
* Type IssueSearchType was added
* Enum value HYBRID was added to enum IssueSearchType
* Enum value LEXICAL was added to enum IssueSearchType
* Enum value SEMANTIC was added to enum IssueSearchType
* Type LexicalFallbackReason was added
* Enum value 'NON\_ISSUE\_TARGETwas added to enumLexicalFallbackReason'
* Enum value 'NO\_ACCESSIBLE\_REPOSwas added to enumLexicalFallbackReason'
* Enum value 'NO\_TEXT\_TERMSwas added to enumLexicalFallbackReason'
* Enum value 'ONLY\_NON\_SEMANTIC\_FIELDS\_REQUESTEDwas added to enumLexicalFallbackReason'
* Enum value 'OR\_BOOLEAN\_NOT\_SUPPORTEDwas added to enumLexicalFallbackReason'
* Enum value 'QUOTED\_TEXTwas added to enumLexicalFallbackReason'
* Enum value 'SERVER\_ERRORwas added to enumLexicalFallbackReason'
* Member IssueFieldAddedEvent was added to Union type IssueTimelineItems
* Member IssueFieldChangedEvent was added to Union type IssueTimelineItems
* Member IssueFieldRemovedEvent was added to Union type IssueTimelineItems
* Member IssueFieldAddedEvent was added to Union type PullRequestTimelineItems
* Member IssueFieldChangedEvent was added to Union type PullRequestTimelineItems
* Member IssueFieldRemovedEvent was added to Union type PullRequestTimelineItems
* Field issueSearchType was added to object type SearchResultItemConnection
* Field lexicalFallbackReason was added to object type SearchResultItemConnection
* Enum value 'ISSUE\_HYBRIDwas added to enumSearchType'
* Enum value 'ISSUE\_SEMANTICwas added to enumSearchType'

## Schema changes for 2026-03-17

### The GraphQL schema includes these changes:

* Field optionId was added to object type IssueFieldSingleSelectValue

## Schema changes for 2026-03-16

### The GraphQL schema includes these changes:

* Member User was added to Union type BypassActor

## Schema changes for 2026-03-12

### The GraphQL schema includes these changes:

* Type CreateIssueFieldInput was added
* Input field clientMutationId of type String was added to input object type CreateIssueFieldInput
* Input field dataType of type IssueFieldDataType! was added to input object type CreateIssueFieldInput
* Input field description of type String was added to input object type CreateIssueFieldInput
* Input field name of type String! was added to input object type CreateIssueFieldInput
* Input field options of type '\[IssueFieldSingleSelectOptionInput!]was added to input object typeCreateIssueFieldInput'
* Input field ownerId of type ID! was added to input object type CreateIssueFieldInput
* Input field visibility of type IssueFieldVisibility was added to input object type CreateIssueFieldInput
* Type CreateIssueFieldPayload was added
* Field clientMutationId was added to object type CreateIssueFieldPayload
* Field issueField was added to object type CreateIssueFieldPayload
* Type CreateIssueFieldValueInput was added
* Input field clientMutationId of type String was added to input object type CreateIssueFieldValueInput
* Input field issueField of type IssueFieldCreateOrUpdateInput! was added to input object type CreateIssueFieldValueInput
* Input field issueId of type ID! was added to input object type CreateIssueFieldValueInput
* Type CreateIssueFieldValuePayload was added
* Field clientMutationId was added to object type CreateIssueFieldValuePayload
* Field issue was added to object type CreateIssueFieldValuePayload
* Field issueFieldValue was added to object type CreateIssueFieldValuePayload
* Type 'CreateProjectV2IssueFieldInput' was added
* Input field clientMutationId of type String was added to input object type 'CreateProjectV2IssueFieldInput'
* Input field issueFieldId of type ID! was added to input object type 'CreateProjectV2IssueFieldInput'
* Input field projectId of type ID! was added to input object type 'CreateProjectV2IssueFieldInput'
* Type 'CreateProjectV2IssueFieldPayload' was added
* Field clientMutationId was added to object type 'CreateProjectV2IssueFieldPayload'
* Field 'projectV2Fieldwas added to object typeCreateProjectV2IssueFieldPayload'
* Type DeleteIssueFieldInput was added
* Input field clientMutationId of type String was added to input object type DeleteIssueFieldInput
* Input field fieldId of type ID! was added to input object type DeleteIssueFieldInput
* Type DeleteIssueFieldPayload was added
* Field clientMutationId was added to object type DeleteIssueFieldPayload
* Field issueField was added to object type DeleteIssueFieldPayload
* Type DeleteIssueFieldValueInput was added
* Input field clientMutationId of type String was added to input object type DeleteIssueFieldValueInput
* Input field fieldId of type ID! was added to input object type DeleteIssueFieldValueInput
* Input field issueId of type ID! was added to input object type DeleteIssueFieldValueInput
* Type DeleteIssueFieldValuePayload was added
* Field clientMutationId was added to object type DeleteIssueFieldValuePayload
* Field issue was added to object type DeleteIssueFieldValuePayload
* Field success was added to object type DeleteIssueFieldValuePayload
* Type IssueCommentPinnedEvent was added
* IssueCommentPinnedEvent object implements Node interface
* Field actor was added to object type IssueCommentPinnedEvent
* Field createdAt was added to object type IssueCommentPinnedEvent
* Field id was added to object type IssueCommentPinnedEvent
* Field issueComment was added to object type IssueCommentPinnedEvent
* Type IssueCommentUnpinnedEvent was added
* IssueCommentUnpinnedEvent object implements Node interface
* Field actor was added to object type IssueCommentUnpinnedEvent
* Field createdAt was added to object type IssueCommentUnpinnedEvent
* Field id was added to object type IssueCommentUnpinnedEvent
* Field issueComment was added to object type IssueCommentUnpinnedEvent
* Type IssueFieldCommon was added
* Field createdAt was added to interface IssueFieldCommon
* Field dataType was added to interface IssueFieldCommon
* Field description was added to interface IssueFieldCommon
* Field name was added to interface IssueFieldCommon
* Field visibility was added to interface IssueFieldCommon
* Type IssueFieldCreateOrUpdateInput was added
* Input field dateValue of type String was added to input object type IssueFieldCreateOrUpdateInput
* Input field delete of type Boolean was added to input object type IssueFieldCreateOrUpdateInput
* Input field fieldId of type ID! was added to input object type IssueFieldCreateOrUpdateInput
* Input field numberValue of type Float was added to input object type IssueFieldCreateOrUpdateInput
* Input field singleSelectOptionId of type ID was added to input object type IssueFieldCreateOrUpdateInput
* Input field textValue of type String was added to input object type IssueFieldCreateOrUpdateInput
* Type IssueFieldDataType was added
* Enum value DATE was added to enum IssueFieldDataType
* Enum value NUMBER was added to enum IssueFieldDataType
* Enum value 'SINGLE\_SELECTwas added to enumIssueFieldDataType'
* Enum value TEXT was added to enum IssueFieldDataType
* Type IssueFieldDate was added
* IssueFieldDate object implements IssueFieldCommon interface
* IssueFieldDate object implements Node interface
* Field createdAt was added to object type IssueFieldDate
* Field dataType was added to object type IssueFieldDate
* Field description was added to object type IssueFieldDate
* Field id was added to object type IssueFieldDate
* Field name was added to object type IssueFieldDate
* Field visibility was added to object type IssueFieldDate
* Type IssueFieldDateValue was added
* IssueFieldDateValue object implements IssueFieldValueCommon interface
* IssueFieldDateValue object implements Node interface
* Field field was added to object type IssueFieldDateValue
* Field id was added to object type IssueFieldDateValue
* Field value was added to object type IssueFieldDateValue
* Type IssueFieldNumber was added
* IssueFieldNumber object implements IssueFieldCommon interface
* IssueFieldNumber object implements Node interface
* Field createdAt was added to object type IssueFieldNumber
* Field dataType was added to object type IssueFieldNumber
* Field description was added to object type IssueFieldNumber
* Field id was added to object type IssueFieldNumber
* Field name was added to object type IssueFieldNumber
* Field visibility was added to object type IssueFieldNumber
* Type IssueFieldNumberValue was added
* IssueFieldNumberValue object implements IssueFieldValueCommon interface
* IssueFieldNumberValue object implements Node interface
* Field field was added to object type IssueFieldNumberValue
* Field id was added to object type IssueFieldNumberValue
* Field value was added to object type IssueFieldNumberValue
* Type IssueFieldOrder was added
* Input field direction of type OrderDirection! was added to input object type IssueFieldOrder
* Input field field of type IssueFieldOrderField! was added to input object type IssueFieldOrder
* Type IssueFieldOrderField was added
* Enum value 'CREATED\_ATwas added to enumIssueFieldOrderField'
* Enum value NAME was added to enum IssueFieldOrderField
* Type IssueFieldSingleSelect was added
* IssueFieldSingleSelect object implements IssueFieldCommon interface
* IssueFieldSingleSelect object implements Node interface
* Field createdAt was added to object type IssueFieldSingleSelect
* Field dataType was added to object type IssueFieldSingleSelect
* Field description was added to object type IssueFieldSingleSelect
* Field id was added to object type IssueFieldSingleSelect
* Field name was added to object type IssueFieldSingleSelect
* Field options was added to object type IssueFieldSingleSelect
* Field visibility was added to object type IssueFieldSingleSelect
* Type IssueFieldSingleSelectOption was added
* IssueFieldSingleSelectOption object implements Node interface
* Field color was added to object type IssueFieldSingleSelectOption
* Field description was added to object type IssueFieldSingleSelectOption
* Field id was added to object type IssueFieldSingleSelectOption
* Field name was added to object type IssueFieldSingleSelectOption
* Field priority was added to object type IssueFieldSingleSelectOption
* Type IssueFieldSingleSelectOptionColor was added
* Enum value BLUE was added to enum IssueFieldSingleSelectOptionColor
* Enum value GRAY was added to enum IssueFieldSingleSelectOptionColor
* Enum value GREEN was added to enum IssueFieldSingleSelectOptionColor
* Enum value ORANGE was added to enum IssueFieldSingleSelectOptionColor
* Enum value PINK was added to enum IssueFieldSingleSelectOptionColor
* Enum value PURPLE was added to enum IssueFieldSingleSelectOptionColor
* Enum value RED was added to enum IssueFieldSingleSelectOptionColor
* Enum value YELLOW was added to enum IssueFieldSingleSelectOptionColor
* Type IssueFieldSingleSelectOptionInput was added
* Input field color of type IssueFieldSingleSelectOptionColor! was added to input object type IssueFieldSingleSelectOptionInput
* Input field description of type String was added to input object type IssueFieldSingleSelectOptionInput
* Input field name of type String! was added to input object type IssueFieldSingleSelectOptionInput
* Input field priority of type Int! was added to input object type IssueFieldSingleSelectOptionInput
* Type IssueFieldSingleSelectValue was added
* IssueFieldSingleSelectValue object implements IssueFieldValueCommon interface
* IssueFieldSingleSelectValue object implements Node interface
* Field color was added to object type IssueFieldSingleSelectValue
* Field description was added to object type IssueFieldSingleSelectValue
* Field field was added to object type IssueFieldSingleSelectValue
* Field id was added to object type IssueFieldSingleSelectValue
* Field name was added to object type IssueFieldSingleSelectValue
* Type IssueFieldText was added
* IssueFieldText object implements IssueFieldCommon interface
* IssueFieldText object implements Node interface
* Field createdAt was added to object type IssueFieldText
* Field dataType was added to object type IssueFieldText
* Field description was added to object type IssueFieldText
* Field id was added to object type IssueFieldText
* Field name was added to object type IssueFieldText
* Field visibility was added to object type IssueFieldText
* Type IssueFieldTextValue was added
* IssueFieldTextValue object implements IssueFieldValueCommon interface
* IssueFieldTextValue object implements Node interface
* Field field was added to object type IssueFieldTextValue
* Field id was added to object type IssueFieldTextValue
* Field value was added to object type IssueFieldTextValue
* Type IssueFieldValue was added
* Member IssueFieldDateValue was added to Union type IssueFieldValue
* Member IssueFieldNumberValue was added to Union type IssueFieldValue
* Member IssueFieldSingleSelectValue was added to Union type IssueFieldValue
* Member IssueFieldTextValue was added to Union type IssueFieldValue
* Type IssueFieldValueCommon was added
* Field field was added to interface IssueFieldValueCommon
* Type IssueFieldValueConnection was added
* Field edges was added to object type IssueFieldValueConnection
* Field nodes was added to object type IssueFieldValueConnection
* Field pageInfo was added to object type IssueFieldValueConnection
* Field totalCount was added to object type IssueFieldValueConnection
* Type IssueFieldValueEdge was added
* Field cursor was added to object type IssueFieldValueEdge
* Field node was added to object type IssueFieldValueEdge
* Type IssueFieldVisibility was added
* Enum value ALL was added to enum IssueFieldVisibility
* Enum value 'ORG\_ONLYwas added to enumIssueFieldVisibility'
* Type IssueFields was added
* Member IssueFieldDate was added to Union type IssueFields
* Member IssueFieldNumber was added to Union type IssueFields
* Member IssueFieldSingleSelect was added to Union type IssueFields
* Member IssueFieldText was added to Union type IssueFields
* Type IssueFieldsConnection was added
* Field edges was added to object type IssueFieldsConnection
* Field nodes was added to object type IssueFieldsConnection
* Field pageInfo was added to object type IssueFieldsConnection
* Field totalCount was added to object type IssueFieldsConnection
* Type IssueFieldsEdge was added
* Field cursor was added to object type IssueFieldsEdge
* Field node was added to object type IssueFieldsEdge
* Type PinIssueCommentInput was added
* Input field clientMutationId of type String was added to input object type PinIssueCommentInput
* Input field issueCommentId of type ID! was added to input object type PinIssueCommentInput
* Type PinIssueCommentPayload was added
* Field clientMutationId was added to object type PinIssueCommentPayload
* Field issueComment was added to object type PinIssueCommentPayload
* Type Pinnable was added
* Field isPinned was added to interface Pinnable
* Field pinnedAt was added to interface Pinnable
* Field pinnedBy was added to interface Pinnable
* Field viewerCanPin was added to interface Pinnable
* Field viewerCanUnpin was added to interface Pinnable
* Type PinnedIssueComment was added
* PinnedIssueComment object implements Node interface
* Field databaseId was added to object type PinnedIssueComment
* Field fullDatabaseId was added to object type PinnedIssueComment
* Field id was added to object type PinnedIssueComment
* Field issue was added to object type PinnedIssueComment
* Field issueComment was added to object type PinnedIssueComment
* Field pinnedAt was added to object type PinnedIssueComment
* Field pinnedBy was added to object type PinnedIssueComment
* Type 'ProjectV2IssueFieldValues' was added
* Member IssueFieldDateValue was added to Union type 'ProjectV2IssueFieldValues'
* Member IssueFieldNumberValue was added to Union type 'ProjectV2IssueFieldValues'
* Member IssueFieldSingleSelectValue was added to Union type 'ProjectV2IssueFieldValues'
* Member IssueFieldTextValue was added to Union type 'ProjectV2IssueFieldValues'
* Type 'ProjectV2ItemIssueFieldValue' was added
* Field field was added to object type 'ProjectV2ItemIssueFieldValue'
* Field issueFieldValue was added to object type 'ProjectV2ItemIssueFieldValue'
* Type SetIssueFieldValueInput was added
* Input field clientMutationId of type String was added to input object type SetIssueFieldValueInput
* Input field issueFields of type '\[IssueFieldCreateOrUpdateInput!]!was added to input object typeSetIssueFieldValueInput'
* Input field issueId of type ID! was added to input object type SetIssueFieldValueInput
* Type SetIssueFieldValuePayload was added
* Field clientMutationId was added to object type SetIssueFieldValuePayload
* Field issue was added to object type SetIssueFieldValuePayload
* Field issueFieldValues was added to object type SetIssueFieldValuePayload
* Type UnpinIssueCommentInput was added
* Input field clientMutationId of type String was added to input object type UnpinIssueCommentInput
* Input field issueCommentId of type ID! was added to input object type UnpinIssueCommentInput
* Type UnpinIssueCommentPayload was added
* Field clientMutationId was added to object type UnpinIssueCommentPayload
* Field issueComment was added to object type UnpinIssueCommentPayload
* Type UpdateIssueFieldInput was added
* Input field clientMutationId of type String was added to input object type UpdateIssueFieldInput
* Input field description of type String was added to input object type UpdateIssueFieldInput
* Input field id of type ID! was added to input object type UpdateIssueFieldInput
* Input field name of type String was added to input object type UpdateIssueFieldInput
* Input field options of type '\[IssueFieldSingleSelectOptionInput!]was added to input object typeUpdateIssueFieldInput'
* Input field visibility of type IssueFieldVisibility was added to input object type UpdateIssueFieldInput
* Type UpdateIssueFieldPayload was added
* Field clientMutationId was added to object type UpdateIssueFieldPayload
* Field issueField was added to object type UpdateIssueFieldPayload
* Type UpdateIssueFieldValueInput was added
* Input field clientMutationId of type String was added to input object type UpdateIssueFieldValueInput
* Input field issueField of type IssueFieldCreateOrUpdateInput! was added to input object type UpdateIssueFieldValueInput
* Input field issueId of type ID! was added to input object type UpdateIssueFieldValueInput
* Type UpdateIssueFieldValuePayload was added
* Field clientMutationId was added to object type UpdateIssueFieldValuePayload
* Field issue was added to object type UpdateIssueFieldValuePayload
* Field issueFieldValue was added to object type UpdateIssueFieldValuePayload
* Input field issueFields of type '\[IssueFieldCreateOrUpdateInput!]was added to input object typeCreateIssueInput'
* Field issueFieldValues was added to object type Issue
* Argument after: String added to field Issue.issueFieldValues
* Argument before: String added to field Issue.issueFieldValues
* Argument first: Int added to field Issue.issueFieldValues
* Argument last: Int added to field Issue.issueFieldValues
* Field pinnedIssueComment was added to object type Issue
* IssueComment object implements Pinnable interface
* Field isPinned was added to object type IssueComment
* Field pinnedAt was added to object type IssueComment
* Field pinnedBy was added to object type IssueComment
* Field viewerCanPin was added to object type IssueComment
* Field viewerCanUnpin was added to object type IssueComment
* Member IssueCommentPinnedEvent was added to Union type IssueTimelineItems
* Member IssueCommentUnpinnedEvent was added to Union type IssueTimelineItems
* Field pinnedFields was added to object type IssueType
* Field createIssueField was added to object type Mutation
* Argument input: CreateIssueFieldInput! added to field Mutation.createIssueField
* Field createIssueFieldValue was added to object type Mutation
* Argument input: CreateIssueFieldValueInput! added to field Mutation.createIssueFieldValue
* Field 'createProjectV2IssueFieldwas added to object typeMutation'
* Argument 'input: CreateProjectV2IssueFieldInput!added to fieldMutation.createProjectV2IssueField'
* Field deleteIssueField was added to object type Mutation
* Argument input: DeleteIssueFieldInput! added to field Mutation.deleteIssueField
* Field deleteIssueFieldValue was added to object type Mutation
* Argument input: DeleteIssueFieldValueInput! added to field Mutation.deleteIssueFieldValue
* Field pinIssueComment was added to object type Mutation
* Argument input: PinIssueCommentInput! added to field Mutation.pinIssueComment
* Field setIssueFieldValue was added to object type Mutation
* Argument input: SetIssueFieldValueInput! added to field Mutation.setIssueFieldValue
* Field unpinIssueComment was added to object type Mutation
* Argument input: UnpinIssueCommentInput! added to field Mutation.unpinIssueComment
* Field updateIssueField was added to object type Mutation
* Argument input: UpdateIssueFieldInput! added to field Mutation.updateIssueField
* Field updateIssueFieldValue was added to object type Mutation
* Argument input: UpdateIssueFieldValueInput! added to field Mutation.updateIssueFieldValue
* Field issueFields was added to object type Organization
* Argument after: String added to field Organization.issueFields
* Argument before: String added to field Organization.issueFields
* Argument first: Int added to field Organization.issueFields
* Argument last: Int added to field Organization.issueFields
* Argument orderBy: IssueFieldOrder (with default value) added to field Organization.issueFields
* Member 'ProjectV2ItemIssueFieldValuewas added to Union typeProjectV2ItemFieldValue'
* Member IssueCommentPinnedEvent was added to Union type PullRequestTimelineItems
* Member IssueCommentUnpinnedEvent was added to Union type PullRequestTimelineItems

## Schema changes for 2026-03-10

### The GraphQL schema includes these changes:

* Field viewerCopilotAgentTaskUpdatesChannel was added to interface Agentic
* Field viewerCopilotAgentTaskUpdatesChannel was added to object type User

## Schema changes for 2026-03-03

### The GraphQL schema includes these changes:

* Field fullDatabaseId was added to object type CheckAnnotation

### The following changes will be made to the schema:

* On member Artifact.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2027-01-01.
* On member CheckAnnotation.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2027-01-01.

## Schema changes for 2026-02-25

### The GraphQL schema includes these changes:

* Input field requireExplicitValues of type Boolean was added to input object type CreateRepositoryCustomPropertyInput
* Field requireExplicitValues was added to object type RepositoryCustomProperty
* Input field requireExplicitValues of type Boolean was added to input object type UpdateRepositoryCustomPropertyInput

## Schema changes for 2026-02-23

### The GraphQL schema includes these changes:

* Enum value 'ISSUE\_COMMENT\_PINNED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'ISSUE\_COMMENT\_UNPINNED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'ISSUE\_COMMENT\_PINNED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'ISSUE\_COMMENT\_UNPINNED\_EVENTwas added to enumPullRequestTimelineItemsItemType'

## Schema changes for 2026-02-20

### The GraphQL schema includes these changes:

* Type PullRequestCreationPolicy was added
* Enum value ALL was added to enum PullRequestCreationPolicy
* Enum value 'COLLABORATORS\_ONLYwas added to enumPullRequestCreationPolicy'
* Field hasPullRequestsEnabled was added to object type Repository
* Field pullRequestCreationPolicy was added to object type Repository
* Field hasPullRequestsEnabled was added to interface RepositoryInfo
* Field pullRequestCreationPolicy was added to interface RepositoryInfo
* Input field hasPullRequestsEnabled of type Boolean was added to input object type UpdateRepositoryInput
* Input field pullRequestCreationPolicy of type PullRequestCreationPolicy was added to input object type UpdateRepositoryInput

## Schema changes for 2026-02-13

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member Team.viewerCanSubscribe:viewerCanSubscribe will be removed. Effective 2026-07-01.
* On member Team.viewerSubscription:viewerSubscription will be removed. Effective 2026-07-01.

## Schema changes for 2026-02-07

### The GraphQL schema includes these changes:

* Type AgentAssignmentInput was added
* Input field baseRef of type String was added to input object type AgentAssignmentInput
* Input field customAgent of type String was added to input object type AgentAssignmentInput
* Input field customInstructions of type String was added to input object type AgentAssignmentInput
* Input field targetRepositoryId of type ID was added to input object type AgentAssignmentInput
* Input field agentAssignment of type AgentAssignmentInput was added to input object type AddAssigneesToAssignableInput
* Input field agentAssignment of type AgentAssignmentInput was added to input object type CreateIssueInput
* Input field agentAssignment of type AgentAssignmentInput was added to input object type ReplaceActorsForAssignableInput
* Input field agentAssignment of type AgentAssignmentInput was added to input object type UpdateIssueInput

## Schema changes for 2026-02-05

### The GraphQL schema includes these changes:

* Type IpAllowListUserLevelEnforcementEnabledSettingValue was added
* Enum value DISABLED was added to enum IpAllowListUserLevelEnforcementEnabledSettingValue
* Enum value ENABLED was added to enum IpAllowListUserLevelEnforcementEnabledSettingValue
* Type UpdateIpAllowListUserLevelEnforcementEnabledSettingInput was added
* Input field clientMutationId of type String was added to input object type UpdateIpAllowListUserLevelEnforcementEnabledSettingInput
* Input field ownerId of type ID! was added to input object type UpdateIpAllowListUserLevelEnforcementEnabledSettingInput
* Input field settingValue of type IpAllowListUserLevelEnforcementEnabledSettingValue! was added to input object type UpdateIpAllowListUserLevelEnforcementEnabledSettingInput
* Type UpdateIpAllowListUserLevelEnforcementEnabledSettingPayload was added
* Field clientMutationId was added to object type UpdateIpAllowListUserLevelEnforcementEnabledSettingPayload
* Field owner was added to object type UpdateIpAllowListUserLevelEnforcementEnabledSettingPayload
* Field ipAllowListUserLevelEnforcementEnabledSetting was added to object type EnterpriseOwnerInfo
* Field updateIpAllowListUserLevelEnforcementEnabledSetting was added to object type Mutation
* Argument input: UpdateIpAllowListUserLevelEnforcementEnabledSettingInput! added to field Mutation.updateIpAllowListUserLevelEnforcementEnabledSetting

## Schema changes for 2026-01-28

### The GraphQL schema includes these changes:

* Field Issue.projectItems changed type from 'ProjectV2ItemConnection!toProjectV2ItemConnection'
* Field PullRequest.projectItems changed type from 'ProjectV2ItemConnection!toProjectV2ItemConnection'

## Schema changes for 2026-01-23

### The GraphQL schema includes these changes:

* Input field actorLogins of type '\[String!]was added to input object typeReplaceActorsForAssignableInput'
* Input field ReplaceActorsForAssignableInput.actorIds changed type from '\[ID!]!to\[ID!]'

## Schema changes for 2026-01-22

### The GraphQL schema includes these changes:

* Type RequestReviewsByLoginInput was added
* Input field botLogins of type '\[String!]was added to input object typeRequestReviewsByLoginInput'
* Input field clientMutationId of type String was added to input object type RequestReviewsByLoginInput
* Input field pullRequestId of type ID! was added to input object type RequestReviewsByLoginInput
* Input field teamSlugs of type '\[String!]was added to input object typeRequestReviewsByLoginInput'
* Input field union of type Boolean with default value false was added to input object type RequestReviewsByLoginInput
* Input field userLogins of type '\[String!]was added to input object typeRequestReviewsByLoginInput'
* Type RequestReviewsByLoginPayload was added
* Field actor was added to object type RequestReviewsByLoginPayload
* Field clientMutationId was added to object type RequestReviewsByLoginPayload
* Field pullRequest was added to object type RequestReviewsByLoginPayload
* Field requestedReviewersEdge was added to object type RequestReviewsByLoginPayload
* Field requestReviewsByLogin was added to object type Mutation
* Argument input: RequestReviewsByLoginInput! added to field Mutation.requestReviewsByLogin

## Schema changes for 2026-01-21

### The GraphQL schema includes these changes:

* Argument query: String added to field PullRequest.suggestedReviewerActors

## Schema changes for 2026-01-14

### The GraphQL schema includes these changes:

* Type UpdateEnterpriseTeamDiscussionsSettingInput was removed
* Type UpdateEnterpriseTeamDiscussionsSettingPayload was removed
* Field teamDiscussionsSettingOrganizations was removed from object type EnterpriseOwnerInfo
* Field updateEnterpriseTeamDiscussionsSetting was removed from object type Mutation

### The following changes will be made to the schema:

* On member EnterpriseOwnerInfo.teamDiscussionsSetting:teamDiscussionsSetting will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.

## Schema changes for 2026-01-08

### The GraphQL schema includes these changes:

* Type CreateTeamDiscussionInput was removed
* Type CreateTeamDiscussionPayload was removed
* Type DeleteTeamDiscussionInput was removed
* Type DeleteTeamDiscussionPayload was removed
* Type TeamDiscussion was removed
* Type TeamDiscussionConnection was removed
* Type TeamDiscussionEdge was removed
* Type TeamDiscussionOrder was removed
* Type TeamDiscussionOrderField was removed
* Type UpdateTeamDiscussionInput was removed
* Type UpdateTeamDiscussionPayload was removed
* Field createTeamDiscussion was removed from object type Mutation
* Field deleteTeamDiscussion was removed from object type Mutation
* Field updateTeamDiscussion was removed from object type Mutation
* Field discussion was removed from object type Team
* Field discussions was removed from object type Team
* Field discussionsResourcePath was removed from object type Team
* Field discussionsUrl was removed from object type Team

## Schema changes for 2026-01-06

### The GraphQL schema includes these changes:

* Type CreateTeamDiscussionInput was added
* Input field body of type String was added to input object type CreateTeamDiscussionInput
* Input field clientMutationId of type String was added to input object type CreateTeamDiscussionInput
* Input field private of type Boolean was added to input object type CreateTeamDiscussionInput
* Input field teamId of type ID was added to input object type CreateTeamDiscussionInput
* Input field title of type String was added to input object type CreateTeamDiscussionInput
* Type CreateTeamDiscussionPayload was added
* Field clientMutationId was added to object type CreateTeamDiscussionPayload
* Field teamDiscussion was added to object type CreateTeamDiscussionPayload
* Type DeleteTeamDiscussionInput was added
* Input field clientMutationId of type String was added to input object type DeleteTeamDiscussionInput
* Input field id of type ID! was added to input object type DeleteTeamDiscussionInput
* Type DeleteTeamDiscussionPayload was added
* Field clientMutationId was added to object type DeleteTeamDiscussionPayload
* Type TeamDiscussion was added
* TeamDiscussion object implements Comment interface
* TeamDiscussion object implements Deletable interface
* TeamDiscussion object implements Node interface
* TeamDiscussion object implements Reactable interface
* TeamDiscussion object implements Subscribable interface
* TeamDiscussion object implements UniformResourceLocatable interface
* TeamDiscussion object implements Updatable interface
* TeamDiscussion object implements UpdatableComment interface
* Field author was added to object type TeamDiscussion
* Field authorAssociation was added to object type TeamDiscussion
* Field body was added to object type TeamDiscussion
* Field bodyHTML was added to object type TeamDiscussion
* Field bodyText was added to object type TeamDiscussion
* Field bodyVersion was added to object type TeamDiscussion
* Field commentsResourcePath was added to object type TeamDiscussion
* Field commentsUrl was added to object type TeamDiscussion
* Field createdAt was added to object type TeamDiscussion
* Field createdViaEmail was added to object type TeamDiscussion
* Field databaseId was added to object type TeamDiscussion
* Field editor was added to object type TeamDiscussion
* Field id was added to object type TeamDiscussion
* Field includesCreatedEdit was added to object type TeamDiscussion
* Field isPinned was added to object type TeamDiscussion
* Field isPrivate was added to object type TeamDiscussion
* Field lastEditedAt was added to object type TeamDiscussion
* Field number was added to object type TeamDiscussion
* Field publishedAt was added to object type TeamDiscussion
* Field reactionGroups was added to object type TeamDiscussion
* Field reactions was added to object type TeamDiscussion
* Argument after: String added to field TeamDiscussion.reactions
* Argument before: String added to field TeamDiscussion.reactions
* Argument content: ReactionContent added to field TeamDiscussion.reactions
* Argument first: Int added to field TeamDiscussion.reactions
* Argument last: Int added to field TeamDiscussion.reactions
* Argument orderBy: ReactionOrder added to field TeamDiscussion.reactions
* Field resourcePath was added to object type TeamDiscussion
* Field team was added to object type TeamDiscussion
* Field title was added to object type TeamDiscussion
* Field updatedAt was added to object type TeamDiscussion
* Field url was added to object type TeamDiscussion
* Field userContentEdits was added to object type TeamDiscussion
* Argument after: String added to field TeamDiscussion.userContentEdits
* Argument before: String added to field TeamDiscussion.userContentEdits
* Argument first: Int added to field TeamDiscussion.userContentEdits
* Argument last: Int added to field TeamDiscussion.userContentEdits
* Field viewerCanDelete was added to object type TeamDiscussion
* Field viewerCanPin was added to object type TeamDiscussion
* Field viewerCanReact was added to object type TeamDiscussion
* Field viewerCanSubscribe was added to object type TeamDiscussion
* Field viewerCanUpdate was added to object type TeamDiscussion
* Field viewerCannotUpdateReasons was added to object type TeamDiscussion
* Field viewerDidAuthor was added to object type TeamDiscussion
* Field viewerSubscription was added to object type TeamDiscussion
* Type TeamDiscussionConnection was added
* Field edges was added to object type TeamDiscussionConnection
* Field nodes was added to object type TeamDiscussionConnection
* Field pageInfo was added to object type TeamDiscussionConnection
* Field totalCount was added to object type TeamDiscussionConnection
* Type TeamDiscussionEdge was added
* Field cursor was added to object type TeamDiscussionEdge
* Field node was added to object type TeamDiscussionEdge
* Type TeamDiscussionOrder was added
* Input field direction of type OrderDirection! was added to input object type TeamDiscussionOrder
* Input field field of type TeamDiscussionOrderField! was added to input object type TeamDiscussionOrder
* Type TeamDiscussionOrderField was added
* Enum value 'CREATED\_ATwas added to enumTeamDiscussionOrderField'
* Type UpdateTeamDiscussionInput was added
* Input field body of type String was added to input object type UpdateTeamDiscussionInput
* Input field bodyVersion of type String was added to input object type UpdateTeamDiscussionInput
* Input field clientMutationId of type String was added to input object type UpdateTeamDiscussionInput
* Input field id of type ID! was added to input object type UpdateTeamDiscussionInput
* Input field pinned of type Boolean was added to input object type UpdateTeamDiscussionInput
* Input field title of type String was added to input object type UpdateTeamDiscussionInput
* Type UpdateTeamDiscussionPayload was added
* Field clientMutationId was added to object type UpdateTeamDiscussionPayload
* Field teamDiscussion was added to object type UpdateTeamDiscussionPayload
* Field createTeamDiscussion was added to object type Mutation
* Argument input: CreateTeamDiscussionInput! added to field Mutation.createTeamDiscussion
* Field deleteTeamDiscussion was added to object type Mutation
* Argument input: DeleteTeamDiscussionInput! added to field Mutation.deleteTeamDiscussion
* Field updateTeamDiscussion was added to object type Mutation
* Argument input: UpdateTeamDiscussionInput! added to field Mutation.updateTeamDiscussion
* Field discussion was added to object type Team
* Argument number: Int! added to field Team.discussion
* Field discussions was added to object type Team
* Argument after: String added to field Team.discussions
* Argument before: String added to field Team.discussions
* Argument first: Int added to field Team.discussions
* Argument isPinned: Boolean added to field Team.discussions
* Argument last: Int added to field Team.discussions
* Argument orderBy: TeamDiscussionOrder added to field Team.discussions
* Field discussionsResourcePath was added to object type Team
* Field discussionsUrl was added to object type Team

### The following changes will be made to the schema:

* On member CreateTeamDiscussionInput.body:body will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionInput.private:private will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionInput.teamId:teamId will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionInput.title:title will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionPayload.teamDiscussion:teamDiscussion will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.authorAssociation:authorAssociation will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.bodyVersion:bodyVersion will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.commentsResourcePath:commentsResourcePath will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.commentsUrl:commentsUrl will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.isPinned:isPinned will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.isPrivate:isPrivate will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.number:number will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.resourcePath:resourcePath will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.team:team will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.title:title will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.url:url will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.viewerCanPin:viewerCanPin will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.

## Schema changes for 2026-01-05

### The GraphQL schema includes these changes:

* Type CreateTeamDiscussionInput was removed
* Type CreateTeamDiscussionPayload was removed
* Type DeleteTeamDiscussionInput was removed
* Type DeleteTeamDiscussionPayload was removed
* Type TeamDiscussion was removed
* Type TeamDiscussionConnection was removed
* Type TeamDiscussionEdge was removed
* Type TeamDiscussionOrder was removed
* Type TeamDiscussionOrderField was removed
* Type UpdateTeamDiscussionInput was removed
* Type UpdateTeamDiscussionPayload was removed
* Field createTeamDiscussion was removed from object type Mutation
* Field deleteTeamDiscussion was removed from object type Mutation
* Field updateTeamDiscussion was removed from object type Mutation
* Field discussion was removed from object type Team
* Field discussions was removed from object type Team
* Field discussionsResourcePath was removed from object type Team
* Field discussionsUrl was removed from object type Team

## Schema changes for 2026-01-04

### The GraphQL schema includes these changes:

* Type CreateTeamDiscussionCommentInput was removed
* Type CreateTeamDiscussionCommentPayload was removed
* Type DeleteTeamDiscussionCommentInput was removed
* Type DeleteTeamDiscussionCommentPayload was removed
* Type TeamDiscussionComment was removed
* Type TeamDiscussionCommentConnection was removed
* Type TeamDiscussionCommentEdge was removed
* Type TeamDiscussionCommentOrder was removed
* Type TeamDiscussionCommentOrderField was removed
* Type UpdateTeamDiscussionCommentInput was removed
* Type UpdateTeamDiscussionCommentPayload was removed
* Field createTeamDiscussionComment was removed from object type Mutation
* Field deleteTeamDiscussionComment was removed from object type Mutation
* Field updateTeamDiscussionComment was removed from object type Mutation
* Field comments (deprecated) was removed from object type TeamDiscussion

## Schema changes for 2025-12-13

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member ReviewRequest.requestedBy:requestedBy will be removed. Use requestedByActor instead. Effective 2026-04-01.

## Schema changes for 2025-12-10

### The GraphQL schema includes these changes:

* Type CreateRepositoryCustomPropertyInput was added
* Input field allowedValues of type '\[String!]was added to input object typeCreateRepositoryCustomPropertyInput'
* Input field clientMutationId of type String was added to input object type CreateRepositoryCustomPropertyInput
* Input field defaultValue of type String was added to input object type CreateRepositoryCustomPropertyInput
* Input field description of type String was added to input object type CreateRepositoryCustomPropertyInput
* Input field propertyName of type String! was added to input object type CreateRepositoryCustomPropertyInput
* Input field regex of type String was added to input object type CreateRepositoryCustomPropertyInput
* Input field required of type Boolean was added to input object type CreateRepositoryCustomPropertyInput
* Input field sourceId of type ID! was added to input object type CreateRepositoryCustomPropertyInput
* Input field valueType of type CustomPropertyValueType! was added to input object type CreateRepositoryCustomPropertyInput
* Input field valuesEditableBy of type RepositoryCustomPropertyValuesEditableBy was added to input object type CreateRepositoryCustomPropertyInput
* Type CreateRepositoryCustomPropertyPayload was added
* Field clientMutationId was added to object type CreateRepositoryCustomPropertyPayload
* Field repositoryCustomProperty was added to object type CreateRepositoryCustomPropertyPayload
* Type CustomPropertySource was added
* Member Enterprise was added to Union type CustomPropertySource
* Member Organization was added to Union type CustomPropertySource
* Type CustomPropertyValue was added
* Type CustomPropertyValueInput was added
* Input field propertyName of type String! was added to input object type CustomPropertyValueInput
* Input field value of type CustomPropertyValue was added to input object type CustomPropertyValueInput
* Type CustomPropertyValueType was added
* Enum value 'MULTI\_SELECTwas added to enumCustomPropertyValueType'
* Enum value 'SINGLE\_SELECTwas added to enumCustomPropertyValueType'
* Enum value STRING was added to enum CustomPropertyValueType
* Enum value 'TRUE\_FALSEwas added to enumCustomPropertyValueType'
* Enum value URL was added to enum CustomPropertyValueType
* Type DeleteRepositoryCustomPropertyInput was added
* Input field clientMutationId of type String was added to input object type DeleteRepositoryCustomPropertyInput
* Input field id of type ID! was added to input object type DeleteRepositoryCustomPropertyInput
* Type DeleteRepositoryCustomPropertyPayload was added
* Field clientMutationId was added to object type DeleteRepositoryCustomPropertyPayload
* Field repositoryCustomProperty was added to object type DeleteRepositoryCustomPropertyPayload
* Type PromoteRepositoryCustomPropertyInput was added
* Input field clientMutationId of type String was added to input object type PromoteRepositoryCustomPropertyInput
* Input field repositoryCustomPropertyId of type ID! was added to input object type PromoteRepositoryCustomPropertyInput
* Type PromoteRepositoryCustomPropertyPayload was added
* Field clientMutationId was added to object type PromoteRepositoryCustomPropertyPayload
* Field repositoryCustomProperty was added to object type PromoteRepositoryCustomPropertyPayload
* Type RepositoryCustomProperty was added
* RepositoryCustomProperty object implements Node interface
* Field allowedValues was added to object type RepositoryCustomProperty
* Field defaultValue was added to object type RepositoryCustomProperty
* Field description was added to object type RepositoryCustomProperty
* Field id was added to object type RepositoryCustomProperty
* Field propertyName was added to object type RepositoryCustomProperty
* Field regex was added to object type RepositoryCustomProperty
* Field required was added to object type RepositoryCustomProperty
* Field source was added to object type RepositoryCustomProperty
* Field valueType was added to object type RepositoryCustomProperty
* Field valuesEditableBy was added to object type RepositoryCustomProperty
* Type RepositoryCustomPropertyConnection was added
* Field edges was added to object type RepositoryCustomPropertyConnection
* Field nodes was added to object type RepositoryCustomPropertyConnection
* Field pageInfo was added to object type RepositoryCustomPropertyConnection
* Field totalCount was added to object type RepositoryCustomPropertyConnection
* Type RepositoryCustomPropertyEdge was added
* Field cursor was added to object type RepositoryCustomPropertyEdge
* Field node was added to object type RepositoryCustomPropertyEdge
* Type RepositoryCustomPropertyValue was added
* Field propertyName was added to object type RepositoryCustomPropertyValue
* Field value was added to object type RepositoryCustomPropertyValue
* Type RepositoryCustomPropertyValueConnection was added
* Field edges was added to object type RepositoryCustomPropertyValueConnection
* Field nodes was added to object type RepositoryCustomPropertyValueConnection
* Field pageInfo was added to object type RepositoryCustomPropertyValueConnection
* Field totalCount was added to object type RepositoryCustomPropertyValueConnection
* Type RepositoryCustomPropertyValueEdge was added
* Field cursor was added to object type RepositoryCustomPropertyValueEdge
* Field node was added to object type RepositoryCustomPropertyValueEdge
* Type RepositoryCustomPropertyValuesEditableBy was added
* Enum value 'ORG\_ACTORSwas added to enumRepositoryCustomPropertyValuesEditableBy'
* Enum value 'ORG\_AND\_REPO\_ACTORSwas added to enumRepositoryCustomPropertyValuesEditableBy'
* Type SetRepositoryCustomPropertyValuesInput was added
* Input field clientMutationId of type String was added to input object type SetRepositoryCustomPropertyValuesInput
* Input field properties of type '\[CustomPropertyValueInput!]!was added to input object typeSetRepositoryCustomPropertyValuesInput'
* Input field repositoryId of type ID! was added to input object type SetRepositoryCustomPropertyValuesInput
* Type SetRepositoryCustomPropertyValuesPayload was added
* Field clientMutationId was added to object type SetRepositoryCustomPropertyValuesPayload
* Field repository was added to object type SetRepositoryCustomPropertyValuesPayload
* Type UpdateRepositoryCustomPropertyInput was added
* Input field allowedValues of type '\[String!]was added to input object typeUpdateRepositoryCustomPropertyInput'
* Input field clientMutationId of type String was added to input object type UpdateRepositoryCustomPropertyInput
* Input field defaultValue of type String was added to input object type UpdateRepositoryCustomPropertyInput
* Input field description of type String was added to input object type UpdateRepositoryCustomPropertyInput
* Input field regex of type String was added to input object type UpdateRepositoryCustomPropertyInput
* Input field repositoryCustomPropertyId of type ID! was added to input object type UpdateRepositoryCustomPropertyInput
* Input field required of type Boolean was added to input object type UpdateRepositoryCustomPropertyInput
* Input field valuesEditableBy of type RepositoryCustomPropertyValuesEditableBy was added to input object type UpdateRepositoryCustomPropertyInput
* Type UpdateRepositoryCustomPropertyPayload was added
* Field clientMutationId was added to object type UpdateRepositoryCustomPropertyPayload
* Field repositoryCustomProperty was added to object type UpdateRepositoryCustomPropertyPayload
* Field repositoryCustomProperties was added to object type Enterprise
* Argument after: String added to field Enterprise.repositoryCustomProperties
* Argument before: String added to field Enterprise.repositoryCustomProperties
* Argument first: Int added to field Enterprise.repositoryCustomProperties
* Argument last: Int added to field Enterprise.repositoryCustomProperties
* Field repositoryCustomProperty was added to object type Enterprise
* Argument propertyName: String! added to field Enterprise.repositoryCustomProperty
* Field createRepositoryCustomProperty was added to object type Mutation
* Argument input: CreateRepositoryCustomPropertyInput! added to field Mutation.createRepositoryCustomProperty
* Field deleteRepositoryCustomProperty was added to object type Mutation
* Argument input: DeleteRepositoryCustomPropertyInput! added to field Mutation.deleteRepositoryCustomProperty
* Field promoteRepositoryCustomProperty was added to object type Mutation
* Argument input: PromoteRepositoryCustomPropertyInput! added to field Mutation.promoteRepositoryCustomProperty
* Field setRepositoryCustomPropertyValues was added to object type Mutation
* Argument input: SetRepositoryCustomPropertyValuesInput! added to field Mutation.setRepositoryCustomPropertyValues
* Field updateRepositoryCustomProperty was added to object type Mutation
* Argument input: UpdateRepositoryCustomPropertyInput! added to field Mutation.updateRepositoryCustomProperty
* Field repositoryCustomProperties was added to object type Organization
* Argument after: String added to field Organization.repositoryCustomProperties
* Argument before: String added to field Organization.repositoryCustomProperties
* Argument first: Int added to field Organization.repositoryCustomProperties
* Argument last: Int added to field Organization.repositoryCustomProperties
* Field repositoryCustomProperty was added to object type Organization
* Argument propertyName: String! added to field Organization.repositoryCustomProperty
* Field repositoryCustomPropertyValue was added to object type Repository
* Argument propertyName: String! added to field Repository.repositoryCustomPropertyValue
* Field repositoryCustomPropertyValues was added to object type Repository
* Argument after: String added to field Repository.repositoryCustomPropertyValues
* Argument before: String added to field Repository.repositoryCustomPropertyValues
* Argument first: Int added to field Repository.repositoryCustomPropertyValues
* Argument last: Int added to field Repository.repositoryCustomPropertyValues

## Schema changes for 2025-12-05

### The GraphQL schema includes these changes:

* Field automaticCopilotCodeReviewEnabled was removed from object type PullRequestParameters
* Input field automaticCopilotCodeReviewEnabled was removed from input object type PullRequestParametersInput

## Schema changes for 2025-11-30

### The GraphQL schema includes these changes:

* Type SuggestedReviewerActor was added
* Type SuggestedReviewerActorConnection was added
* Type SuggestedReviewerActorEdge was added
* Enum value 'ISSUE\_FIELD\_ADDED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'ISSUE\_FIELD\_CHANGED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'ISSUE\_FIELD\_REMOVED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Field suggestedReviewerActors was added to object type PullRequest
* Enum value 'ISSUE\_FIELD\_ADDED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'ISSUE\_FIELD\_CHANGED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'ISSUE\_FIELD\_REMOVED\_EVENTwas added to enumPullRequestTimelineItemsItemType'

## Schema changes for 2025-11-14

### The GraphQL schema includes these changes:

* Type Agentic was added
* User object implements Agentic interface
* Field viewerCopilotAgentCreatesChannel was added to object type User
* Field viewerCopilotAgentLogUpdatesChannel was added to object type User
* Field viewerCopilotAgentUpdatesChannel was added to object type User

## Schema changes for 2025-11-13

### The GraphQL schema includes these changes:

* Type RequiredReviewerConfiguration was added
* Type RequiredReviewerConfigurationInput was added
* Field requiredReviewers was added to object type PullRequestParameters
* Input field requiredReviewers of type '\[RequiredReviewerConfigurationInput!]was added to input object typePullRequestParametersInput'

## Schema changes for 2025-11-06

### The GraphQL schema includes these changes:

* Input field 'projectV2Idsof type\[ID!]was added to input object typeCreateIssueInput'

## Schema changes for 2025-10-24

### The GraphQL schema includes these changes:

* Type OrganizationPropertyConditionTarget was added
* Type OrganizationPropertyConditionTargetInput was added
* Type OrganizationPropertyTargetDefinition was added
* Type OrganizationPropertyTargetDefinitionInput was added
* Field organizationProperty was added to object type RepositoryRuleConditions
* Input field organizationProperty of type OrganizationPropertyConditionTargetInput was added to input object type RepositoryRuleConditionsInput
* Enum value INCONCLUSIVE was added to enum RepositoryVulnerabilityAlertDependencyRelationship

## Schema changes for 2025-10-22

### The GraphQL schema includes these changes:

* Argument query: String (with default value) added to field 'ProjectV2.items'

## Schema changes for 2025-10-15

### The GraphQL schema includes these changes:

* Type 'AddedToProjectV2Event' was added
* Type ConvertedFromDraftEvent was added
* Type 'ProjectV2Event' was added
* Type 'ProjectV2ItemStatusChangedEvent' was added
* Type 'RemovedFromProjectV2Event' was added
* Field totalBlockedBy was added to object type IssueDependenciesSummary
* Field totalBlocking was added to object type IssueDependenciesSummary
* Member 'AddedToProjectV2Eventwas added to Union typeIssueTimelineItems'
* Member ConvertedFromDraftEvent was added to Union type IssueTimelineItems
* Member 'ProjectV2ItemStatusChangedEventwas added to Union typeIssueTimelineItems'
* Member 'RemovedFromProjectV2Eventwas added to Union typeIssueTimelineItems'
* Enum value 'ADDED\_TO\_PROJECT\_V2\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'CONVERTED\_FROM\_DRAFT\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'PROJECT\_V2\_ITEM\_STATUS\_CHANGED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'REMOVED\_FROM\_PROJECT\_V2\_EVENTwas added to enumIssueTimelineItemsItemType'
* Member 'AddedToProjectV2Eventwas added to Union typePullRequestTimelineItems'
* Member ConvertedFromDraftEvent was added to Union type PullRequestTimelineItems
* Member 'ProjectV2ItemStatusChangedEventwas added to Union typePullRequestTimelineItems'
* Member 'RemovedFromProjectV2Eventwas added to Union typePullRequestTimelineItems'
* Enum value 'ADDED\_TO\_PROJECT\_V2\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'CONVERTED\_FROM\_DRAFT\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'PROJECT\_V2\_ITEM\_STATUS\_CHANGED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'REMOVED\_FROM\_PROJECT\_V2\_EVENTwas added to enumPullRequestTimelineItemsItemType'

## Schema changes for 2025-09-16

### The GraphQL schema includes these changes:

* Type CopilotCodeReviewParameters was added
* Type CopilotCodeReviewParametersInput was added
* Enum value 'COPILOT\_CODE\_REVIEWwas added to enumRepositoryRuleType'
* Member CopilotCodeReviewParameters was added to Union type RuleParameters
* Input field copilotCodeReview of type CopilotCodeReviewParametersInput was added to input object type RuleParametersInput

## Schema changes for 2025-09-12

### The GraphQL schema includes these changes:

* Enum value EXEMPT was added to enum RepositoryRulesetBypassActorBypassMode

## Schema changes for 2025-09-11

### The GraphQL schema includes these changes:

* Field viewerCanUnminimize was added to object type CommitComment
* Field viewerCanUnminimize was added to object type DiscussionComment
* Field viewerCanUnminimize was added to object type GistComment
* Field viewerCanUnminimize was added to object type IssueComment
* Field viewerCanUnminimize was added to interface Minimizable
* Field viewerCanUnminimize was added to object type PullRequestReview
* Field viewerCanUnminimize was added to object type PullRequestReviewComment

## Schema changes for 2025-09-10

### The GraphQL schema includes these changes:

* Enum value SY was added to enum SponsorsCountryOrRegionCode

## Schema changes for 2025-09-05

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member SearchType.ISSUE\_ADVANCED:ISSUE\_ADVANCED will be removed. Effective 2025-11-04.

## Schema changes for 2025-08-26

### The GraphQL schema includes these changes:

* Field viewerCanSetFields was added to object type Issue
* Field viewerCanSeeIssueFields was added to object type Repository

## Schema changes for 2025-08-14

### The GraphQL schema includes these changes:

* Type BlockedByAddedEvent was added
* Type BlockedByRemovedEvent was added
* Type BlockingAddedEvent was added
* Type BlockingRemovedEvent was added
* Member BlockedByAddedEvent was added to Union type IssueTimelineItems
* Member BlockedByRemovedEvent was added to Union type IssueTimelineItems
* Member BlockingAddedEvent was added to Union type IssueTimelineItems
* Member BlockingRemovedEvent was added to Union type IssueTimelineItems
* Member BlockedByAddedEvent was added to Union type PullRequestTimelineItems
* Member BlockedByRemovedEvent was added to Union type PullRequestTimelineItems
* Member BlockingAddedEvent was added to Union type PullRequestTimelineItems
* Member BlockingRemovedEvent was added to Union type PullRequestTimelineItems

## Schema changes for 2025-08-11

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member NotificationThread.list:list will be removed. Use the optionalList field instead. Effective 2026-01-01.
* On member NotificationThread.subject:subject will be removed. Use the optionalSubject field instead. Effective 2026-01-01.

## Schema changes for 2025-08-05

### The GraphQL schema includes these changes:

* Field securityContactEmail was added to object type Enterprise
* Input field securityContactEmail of type String was added to input object type UpdateEnterpriseProfileInput

## Schema changes for 2025-07-31

### The GraphQL schema includes these changes:

* Enum value 'BLOCKED\_BY\_REMOVED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'BLOCKING\_ADDED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'BLOCKING\_REMOVED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'BLOCKED\_BY\_REMOVED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'BLOCKING\_ADDED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'BLOCKING\_REMOVED\_EVENTwas added to enumPullRequestTimelineItemsItemType'

## Schema changes for 2025-07-30

### The GraphQL schema includes these changes:

* Type AddBlockedByInput was added
* Type AddBlockedByPayload was added
* Type IssueDependenciesSummary was added
* Type IssueDependencyOrder was added
* Type IssueDependencyOrderField was added
* Type RemoveBlockedByInput was added
* Type RemoveBlockedByPayload was added
* Field blockedBy was added to object type Issue
* Field blocking was added to object type Issue
* Field issueDependenciesSummary was added to object type Issue
* Enum value 'BLOCKED\_BY\_ADDED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Field addBlockedBy was added to object type Mutation
* Field removeBlockedBy was added to object type Mutation
* Enum value 'BLOCKED\_BY\_ADDED\_EVENTwas added to enumPullRequestTimelineItemsItemType'

## Schema changes for 2025-07-15

### The GraphQL schema includes these changes:

* Directive deprecated was removed from field ClosedEvent.stateReason
* Directive deprecated was removed from field Issue.stateReason

### The following changes will be made to the schema:

* On member Issue.stateReason.enableDuplicate:enableDuplicate will be removed. Effective 2025-10-01.

## Schema changes for 2025-07-04

### The GraphQL schema includes these changes:

* Field immutable was added to object type Release

## Schema changes for 2025-06-25

### The GraphQL schema includes these changes:

* Field name was added to object type Mannequin

## Schema changes for 2025-06-17

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member ClosedEvent.stateReason:stateReason will be removed. Effective 2025-10-01.
* On member Issue.stateReason:stateReason will be removed. Effective 2025-10-01.

## Schema changes for 2025-06-13

### The GraphQL schema includes these changes:

* Type BotOrUser was removed
* Input field botIds of type '\[ID!]was added to input object typeRequestReviewsInput'

## Schema changes for 2025-05-27

### The GraphQL schema includes these changes:

* Enum value 'ISSUE\_COUNTwas added to enumLabelOrderField'
* Field digest was added to object type ReleaseAsset

## Schema changes for 2025-05-22

### The GraphQL schema includes these changes:

* Field duplicateOf was added to object type ClosedEvent
* Field duplicateOf was added to object type Issue

## Schema changes for 2025-05-06

### The GraphQL schema includes these changes:

* Type BotOrUser was added

## Schema changes for 2025-05-01

### The GraphQL schema includes these changes:

* Input field AddPullRequestReviewThreadInput.path changed type from String! to String

## Schema changes for 2025-04-30

### The GraphQL schema includes these changes:

* Field closedIssueCount was added to object type Milestone
* Field openIssueCount was added to object type Milestone

## Schema changes for 2025-04-29

### The GraphQL schema includes these changes:

* Input field DraftPullRequestReviewThread.line changed type from Int! to Int
* Input field DraftPullRequestReviewThread.path changed type from String! to String

## Schema changes for 2025-04-15

### The GraphQL schema includes these changes:

* Type RepositorySuggestedActorFilter was added
* Argument 'capabilities: \[RepositorySuggestedActorFilter!]!added to fieldRepository.suggestedActors'

## Schema changes for 2025-04-15

### The GraphQL schema includes these changes:

* Type ActorConnection was added
* Type ActorEdge was added
* Type AssigneeConnection was added
* Type AssigneeEdge was added
* Type ReplaceActorsForAssignableInput was added
* Type ReplaceActorsForAssignablePayload was added
* Field assignedActors was added to interface Assignable
* Field suggestedActors was added to interface Assignable
* Field assignedActors was added to object type Issue
* Field suggestedActors was added to object type Issue
* Field replaceActorsForAssignable was added to object type Mutation
* Field assignedActors was added to object type PullRequest
* Field suggestedActors was added to object type PullRequest
* Field suggestedActors was added to object type Repository

## Schema changes for 2025-04-14

### The GraphQL schema includes these changes:

* Type AnnouncementBannerI was removed
* Input field isPrivate was removed from input object type CreateIssueTypeInput
* Enterprise object type no longer implements AnnouncementBannerI interface
* Field announcement (deprecated) was removed from object type Enterprise
* Field announcementCreatedAt (deprecated) was removed from object type Enterprise
* Field announcementExpiresAt (deprecated) was removed from object type Enterprise
* Field announcementUserDismissible (deprecated) was removed from object type Enterprise
* Input field type of type String was added to input object type IssueFilters
* Organization object type no longer implements AnnouncementBannerI interface
* Field announcement (deprecated) was removed from object type Organization
* Field announcementCreatedAt (deprecated) was removed from object type Organization
* Field announcementExpiresAt (deprecated) was removed from object type Organization
* Field announcementUserDismissible (deprecated) was removed from object type Organization
* Input field isPrivate was removed from input object type UpdateIssueTypeInput

### The following changes will be made to the schema:

* On member AuditEntry.action:action will be removed. Effective 2026-04-01.
* On member AuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member AuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member AuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member AuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member AuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member AuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member AuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member AuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member AuditEntry.user:user will be removed. Effective 2026-04-01.
* On member AuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member AuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member AuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposClearAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposDisableAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member MembersCanDeleteReposEnableAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.applicationUrl:applicationUrl will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.callbackUrl:callbackUrl will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.rateLimit:rateLimit will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.state:state will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OauthApplicationCreateAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.invitationEmail:invitationEmail will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgAddBillingManagerAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.permission:permission will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgAddMemberAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.blockedUser:blockedUser will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.blockedUserName:blockedUserName will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.blockedUserResourcePath:blockedUserResourcePath will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.blockedUserUrl:blockedUserUrl will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgBlockUserAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgConfigDisableCollaboratorsOnlyAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgConfigEnableCollaboratorsOnlyAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.billingPlan:billingPlan will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgCreateAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgDisableOauthAppRestrictionsAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.digestMethodUrl:digestMethodUrl will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.issuerUrl:issuerUrl will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.signatureMethodUrl:signatureMethodUrl will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.singleSignOnUrl:singleSignOnUrl will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgDisableSamlAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgDisableTwoFactorRequirementAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgEnableOauthAppRestrictionsAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.digestMethodUrl:digestMethodUrl will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.issuerUrl:issuerUrl will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.signatureMethodUrl:signatureMethodUrl will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.singleSignOnUrl:singleSignOnUrl will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgEnableSamlAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgEnableTwoFactorRequirementAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.email:email will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.organizationInvitation:organizationInvitation will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgInviteMemberAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgInviteToBusinessAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessApprovedAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessBlockedAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessDeniedAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessRequestedAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgOauthAppAccessUnblockedAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.reason:reason will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgRemoveBillingManagerAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.membershipTypes:membershipTypes will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.reason:reason will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgRemoveMemberAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.membershipTypes:membershipTypes will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.reason:reason will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgRemoveOutsideCollaboratorAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.restoredCustomEmailRoutingsCount:restoredCustomEmailRoutingsCount will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.restoredIssueAssignmentsCount:restoredIssueAssignmentsCount will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.restoredMemberships:restoredMemberships will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.restoredMembershipsCount:restoredMembershipsCount will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.restoredRepositoriesCount:restoredRepositoriesCount will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.restoredRepositoryStarsCount:restoredRepositoryStarsCount will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.restoredRepositoryWatchesCount:restoredRepositoryWatchesCount will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberMembershipOrganizationAuditEntryData.organization:organization will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberMembershipOrganizationAuditEntryData.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberMembershipOrganizationAuditEntryData.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgRestoreMemberMembershipOrganizationAuditEntryData.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.blockedUser:blockedUser will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.blockedUserName:blockedUserName will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.blockedUserResourcePath:blockedUserResourcePath will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.blockedUserUrl:blockedUserUrl will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgUnblockUserAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.permission:permission will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.permissionWas:permissionWas will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateDefaultRepositoryPermissionAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.permission:permission will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.permissionWas:permissionWas will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.canCreateRepositories:canCreateRepositories will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryCreationPermissionAuditEntry.visibility:visibility will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.canInviteOutsideCollaboratorsToRepositories:canInviteOutsideCollaboratorsToRepositories will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member Organization.auditLog:auditLog will be removed. Effective 2026-04-01.
* On member OrganizationAuditEntryData.organization:organization will be removed. Effective 2026-04-01.
* On member OrganizationAuditEntryData.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member OrganizationAuditEntryData.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member OrganizationAuditEntryData.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingDisableAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member PrivateRepositoryForkingEnableAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoAccessAuditEntry.visibility:visibility will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoAddMemberAuditEntry.visibility:visibility will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoAddTopicAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoArchivedAuditEntry.visibility:visibility will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.isEnabled:isEnabled will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.mergeType:mergeType will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoChangeMergeSettingAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableAnonymousGitAccessAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableCollaboratorsOnlyAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableContributorsOnlyAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigDisableSockpuppetDisallowedAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableAnonymousGitAccessAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableCollaboratorsOnlyAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableContributorsOnlyAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigEnableSockpuppetDisallowedAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigLockAnonymousGitAccessAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoConfigUnlockAnonymousGitAccessAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.forkParentName:forkParentName will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.forkSourceName:forkSourceName will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoCreateAuditEntry.visibility:visibility will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoDestroyAuditEntry.visibility:visibility will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepoRemoveMemberAuditEntry.visibility:visibility will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepoRemoveTopicAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeDisableAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member RepositoryVisibilityChangeEnableAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.isLdapMapped:isLdapMapped will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member TeamAddMemberAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.isLdapMapped:isLdapMapped will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member TeamAddRepositoryAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.isLdapMapped:isLdapMapped will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.parentTeam:parentTeam will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.parentTeamName:parentTeamName will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.parentTeamNameWas:parentTeamNameWas will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.parentTeamResourcePath:parentTeamResourcePath will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.parentTeamUrl:parentTeamUrl will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.parentTeamWas:parentTeamWas will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.parentTeamWasResourcePath:parentTeamWasResourcePath will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.parentTeamWasUrl:parentTeamWasUrl will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member TeamChangeParentTeamAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.isLdapMapped:isLdapMapped will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member TeamRemoveMemberAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.action:action will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.actor:actor will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.actorIp:actorIp will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.actorLocation:actorLocation will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.actorLogin:actorLogin will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.actorResourcePath:actorResourcePath will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.actorUrl:actorUrl will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.createdAt:createdAt will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.isLdapMapped:isLdapMapped will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.operationType:operationType will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.organization:organization will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.organizationName:organizationName will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.organizationResourcePath:organizationResourcePath will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.organizationUrl:organizationUrl will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.user:user will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.userLogin:userLogin will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.userResourcePath:userResourcePath will be removed. Effective 2026-04-01.
* On member TeamRemoveRepositoryAuditEntry.userUrl:userUrl will be removed. Effective 2026-04-01.

## Schema changes for 2025-03-27

### The GraphQL schema includes these changes:

* Type CreateIssueTypeInput was added
* Type CreateIssueTypePayload was added
* Type DeleteIssueTypeInput was added
* Type DeleteIssueTypePayload was added
* Type IssueType was added
* Type IssueTypeAddedEvent was added
* Type IssueTypeChangedEvent was added
* Type IssueTypeColor was added
* Type IssueTypeConnection was added
* Type IssueTypeEdge was added
* Type IssueTypeOrder was added
* Type IssueTypeOrderField was added
* Type IssueTypeRemovedEvent was added
* Type PullRequestAllowedMergeMethods was added
* Type RepositoryVulnerabilityAlertDependencyRelationship was added
* Type UpdateIssueIssueTypeInput was added
* Type UpdateIssueIssueTypePayload was added
* Type UpdateIssueTypeInput was added
* Type UpdateIssueTypePayload was added
* Input field issueTypeId of type ID was added to input object type CreateIssueInput
* Field packageUrl was added to object type DependencyGraphDependency
* Field issueType was added to object type Issue
* Field type was added to object type IssueTemplate
* Member IssueTypeAddedEvent was added to Union type IssueTimelineItems
* Member IssueTypeChangedEvent was added to Union type IssueTimelineItems
* Member IssueTypeRemovedEvent was added to Union type IssueTimelineItems
* Enum value 'ISSUE\_TYPE\_ADDED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'ISSUE\_TYPE\_CHANGED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'ISSUE\_TYPE\_REMOVED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Field descriptionHTML was added to object type Milestone
* Field createIssueType was added to object type Mutation
* Field deleteIssueType was added to object type Mutation
* Field updateIssueIssueType was added to object type Mutation
* Field updateIssueType was added to object type Mutation
* Field issueTypes was added to object type Organization
* Enum value 'ISSUE\_TYPEwas added to enumProjectV2FieldType'
* Field automaticCopilotCodeReviewEnabled was added to object type PullRequestParameters
* Field PullRequestParameters.allowedMergeMethods changed type from '\[String!]to\[PullRequestAllowedMergeMethods!]'
* Input field automaticCopilotCodeReviewEnabled of type Boolean was added to input object type PullRequestParametersInput
* Input field PullRequestParametersInput.allowedMergeMethods changed type from '\[String!]to\[PullRequestAllowedMergeMethods!]'
* Member IssueTypeAddedEvent was added to Union type PullRequestTimelineItems
* Member IssueTypeChangedEvent was added to Union type PullRequestTimelineItems
* Member IssueTypeRemovedEvent was added to Union type PullRequestTimelineItems
* Enum value 'ISSUE\_TYPE\_ADDED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'ISSUE\_TYPE\_CHANGED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'ISSUE\_TYPE\_REMOVED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Field issueType was added to object type Repository
* Field issueTypes was added to object type Repository
* Field dependencyRelationship was added to object type RepositoryVulnerabilityAlert
* Enum value 'ISSUE\_ADVANCEDwas added to enumSearchType'
* Input field issueTypeId of type ID was added to input object type UpdateIssueInput

### The following changes will be made to the schema:

* On member AddedToProjectEvent.project:project will be removed. Effective 2025-04-01.
* On member ConvertedNoteToIssueEvent.project:project will be removed. Effective 2025-04-01.
* On member CreateIssueTypeInput.isPrivate:isPrivate will be removed. Effective 2025-04-01.
* On member Issue.projectCards:projectCards will be removed. Effective 2025-04-01.
* On member IssueType.isPrivate:isPrivate will be removed. Effective 2025-04-01.
* On member MovedColumnsInProjectEvent.project:project will be removed. Effective 2025-04-01.
* On member Organization.viewerCanCreateProjects:viewerCanCreateProjects will be removed. Effective 2025-04-01.
* On member ProjectCardArchivedState.ARCHIVED:ARCHIVED will be removed. Effective 2025-04-01.
* On member ProjectCardArchivedState.NOT\_ARCHIVED:NOT\_ARCHIVED will be removed. Effective 2025-04-01.
* On member ProjectOwner.id:id will be removed. Effective 2025-04-01.
* On member ProjectOwner.projectsResourcePath:projectsResourcePath will be removed. Effective 2025-04-01.
* On member ProjectOwner.projectsUrl:projectsUrl will be removed. Effective 2025-04-01.
* On member ProjectOwner.viewerCanCreateProjects:viewerCanCreateProjects will be removed. Effective 2025-04-01.
* On member PullRequest.projectCards:projectCards will be removed. Effective 2025-04-01.
* On member RemovedFromProjectEvent.project:project will be removed. Effective 2025-04-01.
* On member Repository.viewerCanCreateProjects:viewerCanCreateProjects will be removed. Effective 2025-04-01.
* On member UpdateIssueTypeInput.isPrivate:isPrivate will be removed. Effective 2025-04-01.
* On member User.viewerCanCreateProjects:viewerCanCreateProjects will be removed. Effective 2025-04-01.
* On member SearchType.ISSUE\_ADVANCED:ISSUE\_ADVANCED will be removed. Effective 2025-09-04.

## Schema changes for 2025-02-26

### The GraphQL schema includes these changes:

* Field repository was removed from object type UserNamespaceRepository

## Schema changes for 2025-02-14

### The GraphQL schema includes these changes:

* Type 'ProjectV2Iteration' was added
* Type 'ProjectV2IterationFieldConfigurationInput' was added
* Input field iterationConfiguration of type 'ProjectV2IterationFieldConfigurationInputwas added to input object typeCreateProjectV2FieldInput'
* Enum value ITERATION was added to enum 'ProjectV2CustomFieldType'
* Input field iterationConfiguration of type 'ProjectV2IterationFieldConfigurationInputwas added to input object typeUpdateProjectV2FieldInput'

## Schema changes for 2025-02-06

### The GraphQL schema includes these changes:

* Enum value UNAFFILIATED was added to enum EnterpriseAdministratorRole

## Schema changes for 2025-02-01

### The GraphQL schema includes these changes:

* Enum value 'PARENT\_ISSUEwas added to enumProjectV2FieldType'
* Enum value 'SUB\_ISSUES\_PROGRESSwas added to enumProjectV2FieldType'

## Schema changes for 2025-01-31

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member AddedToProjectEvent.databaseId:databaseId will be removed. Effective 2025-04-01.
* On member AddedToProjectEvent.projectCard:projectCard will be removed. Effective 2025-04-01.
* On member AddedToProjectEvent.projectColumnName:projectColumnName will be removed. Effective 2025-04-01.
* On member ConvertedNoteToIssueEvent.projectCard:projectCard will be removed. Effective 2025-04-01.
* On member MovedColumnsInProjectEvent.databaseId:databaseId will be removed. Effective 2025-04-01.
* On member MovedColumnsInProjectEvent.previousProjectColumnName:previousProjectColumnName will be removed. Effective 2025-04-01.
* On member MovedColumnsInProjectEvent.projectCard:projectCard will be removed. Effective 2025-04-01.
* On member MovedColumnsInProjectEvent.projectColumnName:projectColumnName will be removed. Effective 2025-04-01.
* On member Mutation.addProjectCard:addProjectCard will be removed. Effective 2025-04-01.
* On member Mutation.addProjectColumn:addProjectColumn will be removed. Effective 2025-04-01.
* On member Mutation.cloneProject:cloneProject will be removed. Effective 2025-04-01.
* On member Mutation.convertProjectCardNoteToIssue:convertProjectCardNoteToIssue will be removed. Effective 2025-04-01.
* On member Mutation.createProject:createProject will be removed. Effective 2025-04-01.
* On member Mutation.deleteProject:deleteProject will be removed. Effective 2025-04-01.
* On member Mutation.deleteProjectCard:deleteProjectCard will be removed. Effective 2025-04-01.
* On member Mutation.deleteProjectColumn:deleteProjectColumn will be removed. Effective 2025-04-01.
* On member Mutation.importProject:importProject will be removed. Effective 2025-04-01.
* On member Mutation.linkRepositoryToProject:linkRepositoryToProject will be removed. Effective 2025-04-01.
* On member Mutation.moveProjectCard:moveProjectCard will be removed. Effective 2025-04-01.
* On member Mutation.moveProjectColumn:moveProjectColumn will be removed. Effective 2025-04-01.
* On member Mutation.unlinkRepositoryFromProject:unlinkRepositoryFromProject will be removed. Effective 2025-04-01.
* On member Mutation.updateProject:updateProject will be removed. Effective 2025-04-01.
* On member Mutation.updateProjectCard:updateProjectCard will be removed. Effective 2025-04-01.
* On member Mutation.updateProjectColumn:updateProjectColumn will be removed. Effective 2025-04-01.
* On member Organization.project:project will be removed. Effective 2025-04-01.
* On member Organization.projects:projects will be removed. Effective 2025-04-01.
* On member Project.body:body will be removed. Effective 2025-04-01.
* On member Project.bodyHTML:bodyHtml will be removed. Effective 2025-04-01.
* On member Project.columns:columns will be removed. Effective 2025-04-01.
* On member Project.createdAt:createdAt will be removed. Effective 2025-04-01.
* On member Project.creator:creator will be removed. Effective 2025-04-01.
* On member Project.databaseId:databaseId will be removed. Effective 2025-04-01.
* On member Project.id:id will be removed. Effective 2025-04-01.
* On member Project.name:name will be removed. Effective 2025-04-01.
* On member Project.number:number will be removed. Effective 2025-04-01.
* On member Project.owner:owner will be removed. Effective 2025-04-01.
* On member Project.pendingCards:pendingCards will be removed. Effective 2025-04-01.
* On member Project.progress:progress will be removed. Effective 2025-04-01.
* On member Project.resourcePath:resourcePath will be removed. Effective 2025-04-01.
* On member Project.state:state will be removed. Effective 2025-04-01.
* On member Project.updatedAt:updatedAt will be removed. Effective 2025-04-01.
* On member Project.url:url will be removed. Effective 2025-04-01.
* On member ProjectCard.column:column will be removed. Effective 2025-04-01.
* On member ProjectCard.content:content will be removed. Effective 2025-04-01.
* On member ProjectCard.createdAt:createdAt will be removed. Effective 2025-04-01.
* On member ProjectCard.creator:creator will be removed. Effective 2025-04-01.
* On member ProjectCard.databaseId:databaseId will be removed. Effective 2025-04-01.
* On member ProjectCard.id:id will be removed. Effective 2025-04-01.
* On member ProjectCard.isArchived:isArchived will be removed. Effective 2025-04-01.
* On member ProjectCard.note:note will be removed. Effective 2025-04-01.
* On member ProjectCard.project:project will be removed. Effective 2025-04-01.
* On member ProjectCard.resourcePath:resourcePath will be removed. Effective 2025-04-01.
* On member ProjectCard.state:state will be removed. Effective 2025-04-01.
* On member ProjectCard.updatedAt:updatedAt will be removed. Effective 2025-04-01.
* On member ProjectCard.url:url will be removed. Effective 2025-04-01.
* On member ProjectColumn.cards:cards will be removed. Effective 2025-04-01.
* On member ProjectColumn.createdAt:createdAt will be removed. Effective 2025-04-01.
* On member ProjectColumn.databaseId:databaseId will be removed. Effective 2025-04-01.
* On member ProjectColumn.id:id will be removed. Effective 2025-04-01.
* On member ProjectColumn.name:name will be removed. Effective 2025-04-01.
* On member ProjectColumn.project:project will be removed. Effective 2025-04-01.
* On member ProjectColumn.purpose:purpose will be removed. Effective 2025-04-01.
* On member ProjectColumn.resourcePath:resourcePath will be removed. Effective 2025-04-01.
* On member ProjectColumn.updatedAt:updatedAt will be removed. Effective 2025-04-01.
* On member ProjectColumn.url:url will be removed. Effective 2025-04-01.
* On member ProjectOwner.project:project will be removed. Effective 2025-04-01.
* On member ProjectOwner.projects:projects will be removed. Effective 2025-04-01.
* On member ProjectProgress.doneCount:doneCount will be removed. Effective 2025-04-01.
* On member ProjectProgress.donePercentage:donePercentage will be removed. Effective 2025-04-01.
* On member ProjectProgress.enabled:enabled will be removed. Effective 2025-04-01.
* On member ProjectProgress.inProgressCount:inProgressCount will be removed. Effective 2025-04-01.
* On member ProjectProgress.inProgressPercentage:inProgressPercentage will be removed. Effective 2025-04-01.
* On member ProjectProgress.todoCount:todoCount will be removed. Effective 2025-04-01.
* On member ProjectProgress.todoPercentage:todoPercentage will be removed. Effective 2025-04-01.
* On member RemovedFromProjectEvent.databaseId:databaseId will be removed. Effective 2025-04-01.
* On member RemovedFromProjectEvent.projectColumnName:projectColumnName will be removed. Effective 2025-04-01.
* On member Repository.project:project will be removed. Effective 2025-04-01.
* On member Repository.projects:projects will be removed. Effective 2025-04-01.
* On member SearchShortcutQueryProjectTerm.project:project will be removed. Effective 2025-04-01.
* On member User.project:project will be removed. Effective 2025-04-01.
* On member User.projects:projects will be removed. Effective 2025-04-01.

## Schema changes for 2025-01-16

### The GraphQL schema includes these changes:

* Field updatedAt was added to object type Enterprise

## Schema changes for 2025-01-14

### The GraphQL schema includes these changes:

* Type CopilotLicenseType was removed
* Type CopilotLimitedFeature was removed
* Type CopilotLimitedUser was removed
* Type CreateSavedNotificationThreadInput was removed
* Type CreateSavedNotificationThreadPayload was removed
* Type DeleteSavedNotificationThreadInput was removed
* Type DeleteSavedNotificationThreadPayload was removed
* Type DiscussionPubSubTopic was removed
* Type IssuePubSubTopic was removed
* Type MarkAllNotificationsInput was removed
* Type MarkAllNotificationsPayload was removed
* Type MarkNotificationAsDoneInput was removed
* Type MarkNotificationAsDonePayload was removed
* Type MarkNotificationAsReadInput was removed
* Type MarkNotificationAsReadPayload was removed
* Type MarkNotificationAsUndoneInput was removed
* Type MarkNotificationAsUndonePayload was removed
* Type MarkNotificationAsUnreadInput was removed
* Type MarkNotificationAsUnreadPayload was removed
* Type MarkNotificationSubjectAsReadInput was removed
* Type MarkNotificationSubjectAsReadPayload was removed
* Type MarkNotificationsAsDoneInput was removed
* Type MarkNotificationsAsDonePayload was removed
* Type MarkNotificationsAsReadInput was removed
* Type MarkNotificationsAsReadPayload was removed
* Type MarkNotificationsAsUndoneInput was removed
* Type MarkNotificationsAsUndonePayload was removed
* Type MarkNotificationsAsUnreadInput was removed
* Type MarkNotificationsAsUnreadPayload was removed
* Type NotificationReason was removed
* Type NotificationStatus was removed
* Type NotificationThread was removed
* Type NotificationThreadConnection was removed
* Type NotificationThreadEdge was removed
* Type NotificationThreadFilters was removed
* Type NotificationThreadSubscriptionState was removed
* Type NotificationsList was removed
* Type NotificationsSubject was removed
* Type PullRequestPubSubTopic was removed
* Type RepositoryDependabotAlertsThread was removed
* Type UnsubscribeFromNotificationsInput was removed
* Type UnsubscribeFromNotificationsPayload was removed
* Type UserPubSubTopic was removed
* Field updatesChannel was removed from object type Commit
* Field comment was removed from object type Discussion
* Field updatesChannel was removed from object type Discussion
* Argument renderMobileTasklistBlocks: Boolean was removed from field Discussion.bodyHTML
* Field updatesChannel was removed from object type Issue
* Argument renderMobileTasklistBlocks: Boolean was removed from field Issue.bodyHTML
* Field createSavedNotificationThread was removed from object type Mutation
* Field deleteSavedNotificationThread was removed from object type Mutation
* Field markAllNotifications was removed from object type Mutation
* Field markNotificationAsDone was removed from object type Mutation
* Field markNotificationAsRead was removed from object type Mutation
* Field markNotificationAsUndone was removed from object type Mutation
* Field markNotificationAsUnread was removed from object type Mutation
* Field markNotificationSubjectAsRead was removed from object type Mutation
* Field markNotificationsAsDone was removed from object type Mutation
* Field markNotificationsAsRead was removed from object type Mutation
* Field markNotificationsAsUndone was removed from object type Mutation
* Field markNotificationsAsUnread was removed from object type Mutation
* Field unsubscribeFromNotifications was removed from object type Mutation
* Field updatesChannel was removed from object type 'ProjectV2'
* Field updatesChannel was removed from object type PullRequest
* Argument renderMobileTasklistBlocks: Boolean was removed from field PullRequest.bodyHTML
* Field mobileUpdatesUrl was removed from object type Query
* Field viewerUpdatesChannel was removed from object type Query
* Field updatesChannel was removed from object type Ref
* Field copilotLicenseType was removed from object type User
* Field copilotLimitedUser was removed from object type User
* Field notificationThreads was removed from object type User

## Schema changes for 2025-01-13

### The GraphQL schema includes these changes:

* Type CopilotLicenseType was added
* Field copilotLicenseType was added to object type User

## Schema changes for 2025-01-10

### The GraphQL schema includes these changes:

* Type AccessUserNamespaceRepositoryInput was added
* Type AccessUserNamespaceRepositoryPayload was added
* Type AnnouncementBanner was added
* Type CopilotLimitedFeature was added
* Type CopilotLimitedUser was added
* Type CreateSavedNotificationThreadInput was added
* Type CreateSavedNotificationThreadPayload was added
* Type CvssSeverities was added
* Type DeleteSavedNotificationThreadInput was added
* Type DeleteSavedNotificationThreadPayload was added
* Type DiscussionPubSubTopic was added
* Type IssuePubSubTopic was added
* Type MarkAllNotificationsInput was added
* Type MarkAllNotificationsPayload was added
* Type MarkNotificationAsReadInput was added
* Type MarkNotificationAsReadPayload was added
* Type MarkNotificationAsUndoneInput was added
* Type MarkNotificationAsUndonePayload was added
* Type MarkNotificationAsUnreadInput was added
* Type MarkNotificationAsUnreadPayload was added
* Type MarkNotificationSubjectAsReadInput was added
* Type MarkNotificationSubjectAsReadPayload was added
* Type MarkNotificationsAsDoneInput was added
* Type MarkNotificationsAsDonePayload was added
* Type MarkNotificationsAsReadInput was added
* Type MarkNotificationsAsReadPayload was added
* Type MarkNotificationsAsUndoneInput was added
* Type MarkNotificationsAsUndonePayload was added
* Type MarkNotificationsAsUnreadInput was added
* Type MarkNotificationsAsUnreadPayload was added
* Type NotificationReason was added
* Type NotificationStatus was added
* Type NotificationThread was added
* Type NotificationThreadConnection was added
* Type NotificationThreadEdge was added
* Type NotificationThreadFilters was added
* Type NotificationThreadSubscriptionState was added
* Type NotificationsList was added
* Type NotificationsSubject was added
* Type ParentIssueAddedEvent was added
* Type ParentIssueRemovedEvent was added
* Type PullRequestPubSubTopic was added
* Type RepositoryDependabotAlertsThread was added
* Type SubIssueAddedEvent was added
* Type SubIssueRemovedEvent was added
* Type UserNamespaceRepository was added
* Type UserNamespaceRepositoryConnection was added
* Type UserNamespaceRepositoryEdge was added
* Type UserPubSubTopic was added
* Input field duplicateIssueId of type ID was added to input object type CloseIssueInput
* Field updatesChannel was added to object type Commit
* Field relationship was added to object type DependencyGraphDependency
* Field comment was added to object type Discussion
* Field updatesChannel was added to object type Discussion
* Argument renderMobileTasklistBlocks: Boolean (with default value) added to field Discussion.bodyHTML
* Field announcementBanner was added to object type Enterprise
* Field ruleset was added to object type Enterprise
* Field rulesets was added to object type Enterprise
* Field userNamespaceRepositories was added to object type Enterprise
* Field updatesChannel was added to object type Issue
* Argument renderMobileTasklistBlocks: Boolean (with default value) added to field Issue.bodyHTML
* Argument enableDuplicate: Boolean (with default value) added to field Issue.stateReason
* Member ParentIssueAddedEvent was added to Union type IssueTimelineItems
* Member ParentIssueRemovedEvent was added to Union type IssueTimelineItems
* Member SubIssueAddedEvent was added to Union type IssueTimelineItems
* Member SubIssueRemovedEvent was added to Union type IssueTimelineItems
* Enum value 'PARENT\_ISSUE\_ADDED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'PARENT\_ISSUE\_REMOVED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'SUB\_ISSUE\_ADDED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Enum value 'SUB\_ISSUE\_REMOVED\_EVENTwas added to enumIssueTimelineItemsItemType'
* Field accessUserNamespaceRepository was added to object type Mutation
* Field createSavedNotificationThread was added to object type Mutation
* Field deleteSavedNotificationThread was added to object type Mutation
* Field markAllNotifications was added to object type Mutation
* Field markNotificationAsRead was added to object type Mutation
* Field markNotificationAsUndone was added to object type Mutation
* Field markNotificationAsUnread was added to object type Mutation
* Field markNotificationSubjectAsRead was added to object type Mutation
* Field markNotificationsAsDone was added to object type Mutation
* Field markNotificationsAsRead was added to object type Mutation
* Field markNotificationsAsUndone was added to object type Mutation
* Field markNotificationsAsUnread was added to object type Mutation
* Field announcementBanner was added to object type Organization
* Field updatesChannel was added to object type 'ProjectV2'
* Field updatesChannel was added to object type PullRequest
* Argument renderMobileTasklistBlocks: Boolean (with default value) added to field PullRequest.bodyHTML
* Field allowedMergeMethods was added to object type PullRequestParameters
* Input field allowedMergeMethods of type '\[String!]was added to input object typePullRequestParametersInput'
* Member ParentIssueAddedEvent was added to Union type PullRequestTimelineItems
* Member ParentIssueRemovedEvent was added to Union type PullRequestTimelineItems
* Member SubIssueAddedEvent was added to Union type PullRequestTimelineItems
* Member SubIssueRemovedEvent was added to Union type PullRequestTimelineItems
* Enum value 'PARENT\_ISSUE\_ADDED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'PARENT\_ISSUE\_REMOVED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'SUB\_ISSUE\_ADDED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'SUB\_ISSUE\_REMOVED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Field mobileUpdatesUrl was added to object type Query
* Field viewerUpdatesChannel was added to object type Query
* Field updatesChannel was added to object type Ref
* Enum value REPOSITORY was added to enum RepositoryRulesetTarget
* Field cvssSeverities was added to object type SecurityAdvisory
* Field copilotLimitedUser was added to object type User
* Field notificationThreads was added to object type User

### The following changes will be made to the schema:

* On member AnnouncementBannerI.announcement:announcement will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member AnnouncementBannerI.announcementCreatedAt:announcementCreatedAt will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member AnnouncementBannerI.announcementExpiresAt:announcementExpiresAt will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member AnnouncementBannerI.announcementUserDismissible:announcementUserDismissible will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member Enterprise.announcement:announcement will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member Enterprise.announcementCreatedAt:announcementCreatedAt will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member Enterprise.announcementExpiresAt:announcementExpiresAt will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member Enterprise.announcementUserDismissible:announcementUserDismissible will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member Organization.announcement:announcement will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member Organization.announcementCreatedAt:announcementCreatedAt will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member Organization.announcementExpiresAt:announcementExpiresAt will be removed. Use the announcementBanner object instead. Effective 2025-04-01.
* On member Organization.announcementUserDismissible:announcementUserDismissible will be removed. Use the announcementBanner object instead. Effective 2025-04-01.

## Schema changes for 2024-12-04

### The GraphQL schema includes these changes:

* Type 'UpdateProjectV2FieldInput' was added
* Type 'UpdateProjectV2FieldPayload' was added
* Field 'updateProjectV2Fieldwas added to object typeMutation'

## Schema changes for 2024-12-02

### The GraphQL schema includes these changes:

* Type AddSubIssueInput was added
* Type AddSubIssuePayload was added
* Type AnnouncementBannerI was added
* Type RemoveSubIssueInput was added
* Type RemoveSubIssuePayload was added
* Type ReprioritizeSubIssueInput was added
* Type ReprioritizeSubIssuePayload was added
* Type SubIssuesSummary was added
* Type AnnouncementBanner was removed
* Input field parentIssueId of type ID was added to input object type CreateIssueInput
* Field enabled was added to object type DeployKey
* Enterprise object implements AnnouncementBannerI interface
* Enterprise object type no longer implements AnnouncementBanner interface
* Field repositoryDeployKeySetting was added to object type EnterpriseOwnerInfo
* Field repositoryDeployKeySettingOrganizations was added to object type EnterpriseOwnerInfo
* Field verifiedAt was added to interface GitSignature
* Field verifiedAt was added to object type GpgSignature
* Field parent was added to object type Issue
* Field subIssues was added to object type Issue
* Field subIssuesSummary was added to object type Issue
* Field addSubIssue was added to object type Mutation
* Field removeSubIssue was added to object type Mutation
* Field reprioritizeSubIssue was added to object type Mutation
* Organization object implements AnnouncementBannerI interface
* Organization object type no longer implements AnnouncementBanner interface
* Field verifiedAt was added to object type SmimeSignature
* Field verifiedAt was added to object type SshSignature
* Field verifiedAt was added to object type UnknownSignature

## Schema changes for 2024-11-07

### The GraphQL schema includes these changes:

* Type UpdateEnterpriseDeployKeySettingInput was added
* Type UpdateEnterpriseDeployKeySettingPayload was added
* Field updateEnterpriseDeployKeySetting was added to object type Mutation

## Schema changes for 2024-11-01

### The GraphQL schema includes these changes:

* Enum value BLUESKY was added to enum SocialAccountProvider

## Schema changes for 2024-10-18

### The GraphQL schema includes these changes:

* Type EPSS was added
* Type UserViewType was added
* Argument epssPercentage: Float added to field Query.securityAdvisories
* Argument epssPercentile: Float added to field Query.securityAdvisories
* Field epss was added to object type SecurityAdvisory
* Field userViewType was added to object type User

## Schema changes for 2024-10-11

### The GraphQL schema includes these changes:

* Enum value DUPLICATE was added to enum IssueClosedStateReason
* Enum value DUPLICATE was added to enum IssueStateReason

## Schema changes for 2024-10-09

### The GraphQL schema includes these changes:

* Argument 'targets: \[RepositoryRulesetTarget!]added to fieldOrganization.rulesets'
* Argument 'targets: \[RepositoryRulesetTarget!]added to fieldRepository.rulesets'

## Schema changes for 2024-10-08

### The GraphQL schema includes these changes:

* Type EnterpriseDisallowedMethodsSettingValue was added
* Type TwoFactorCredentialSecurityType was added
* Type UpdateEnterpriseTwoFactorAuthenticationDisallowedMethodsSettingInput was added
* Type UpdateEnterpriseTwoFactorAuthenticationDisallowedMethodsSettingPayload was added
* Field clientId was added to object type App
* Argument twoFactorMethodSecurity: TwoFactorCredentialSecurityType added to field Enterprise.members
* Field twoFactorDisallowedMethodsSetting was added to object type EnterpriseOwnerInfo
* Argument twoFactorMethodSecurity: TwoFactorCredentialSecurityType added to field EnterpriseOwnerInfo.admins
* Argument twoFactorMethodSecurity: TwoFactorCredentialSecurityType added to field EnterpriseOwnerInfo.outsideCollaborators
* Field updateEnterpriseTwoFactorAuthenticationDisallowedMethodsSetting was added to object type Mutation
* Argument includeParents: Boolean (with default value) added to field Organization.ruleset
* Field fullDatabaseId was added to object type 'ProjectV2'
* Field fullDatabaseId was added to object type 'ProjectV2StatusUpdate'
* Field fullDatabaseId was added to object type 'ProjectV2View'
* Field fullDatabaseId was added to object type 'ProjectV2Workflow'
* Query object implements Node interface
* Field id was added to object type Query
* Field enterpriseOwner was added to object type RepositoryRulesetBypassActor
* Input field enterpriseOwner of type Boolean was added to input object type RepositoryRulesetBypassActorInput
* Member Enterprise was added to Union type RuleSource
* Enum value 'EPSS\_PERCENTAGEwas added to enumSecurityAdvisoryOrderField'
* Enum value 'EPSS\_PERCENTILEwas added to enumSecurityAdvisoryOrderField'

### The following changes will be made to the schema:

* On member Enterprise.members.hasTwoFactorEnabled:hasTwoFactorEnabled will be removed. Use two\_factor\_method\_security instead. Effective 2025-04-01.
* On member EnterpriseOwnerInfo.admins.hasTwoFactorEnabled:hasTwoFactorEnabled will be removed. Use two\_factor\_method\_security instead. Effective 2025-04-01.
* On member EnterpriseOwnerInfo.outsideCollaborators.hasTwoFactorEnabled:hasTwoFactorEnabled will be removed. Use two\_factor\_method\_security instead. Effective 2025-04-01.
* On member ProjectV2.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2025-04-01.
* On member ProjectV2Item.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2025-04-01.
* On member ProjectV2StatusUpdate.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2025-04-01.
* On member ProjectV2View\.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2025-04-01.
* On member ProjectV2Workflow\.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2025-04-01.
* On member SecurityAdvisory.cvss:cvss will be removed. New cvss\_severities field will now contain both cvss\_v3 and cvss\_v4 properties. Effective 2025-10-01.

## Schema changes for 2024-08-29

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member AddMobileDevicePublicKeyPayload.expiresAt:expiresAt will be removed. Do not rely on this field, it is currently set to a date far in the future if a device key is expirationless Effective 2025-01-01.

## Schema changes for 2024-08-10

### The GraphQL schema includes these changes:

* Enum value 'THANKS\_DEVwas added to enumFundingPlatform'

## Schema changes for 2024-07-25

### The GraphQL schema includes these changes:

* Field doNotEnforceOnCreate was added to object type RequiredStatusChecksParameters
* Input field doNotEnforceOnCreate of type Boolean was added to input object type RequiredStatusChecksParametersInput
* Field doNotEnforceOnCreate was added to object type WorkflowsParameters
* Input field doNotEnforceOnCreate of type Boolean was added to input object type WorkflowsParametersInput

## Schema changes for 2024-07-24

### The GraphQL schema includes these changes:

* Type MergeQueueGroupingStrategy was added
* Type MergeQueueMergeMethod was added
* Type MergeQueueParameters was added
* Type MergeQueueParametersInput was added
* Field viewerCanLabel was added to object type Discussion
* Field viewerCanLabel was added to object type Issue
* Field viewerCanLabel was added to interface Labelable
* Field viewerCanLabel was added to object type PullRequest
* Member MergeQueueParameters was added to Union type RuleParameters
* Input field mergeQueue of type MergeQueueParametersInput was added to input object type RuleParametersInput

## Schema changes for 2024-07-16

### The GraphQL schema includes these changes:

* Field closedByPullRequestsReferences was added to object type Issue

## Schema changes for 2024-07-08

### The GraphQL schema includes these changes:

* Type 'ProjectV2PermissionLevel' was added
* Argument 'minPermissionLevel: ProjectV2PermissionLevel' (with default value) added to field 'Issue.projectsV2'
* Argument 'minPermissionLevel: ProjectV2PermissionLevel' (with default value) added to field 'Organization.projectsV2'
* Argument 'minPermissionLevel: ProjectV2PermissionLevel' (with default value) added to field 'ProjectV2Owner.projectsV2'
* Argument 'minPermissionLevel: ProjectV2PermissionLevel' (with default value) added to field 'PullRequest.projectsV2'
* Argument 'minPermissionLevel: ProjectV2PermissionLevel' (with default value) added to field 'Repository.projectsV2'
* Argument 'minPermissionLevel: ProjectV2PermissionLevel' (with default value) added to field 'Team.projectsV2'
* Argument 'minPermissionLevel: ProjectV2PermissionLevel' (with default value) added to field 'User.projectsV2'

## Schema changes for 2024-06-27

### The GraphQL schema includes these changes:

* Field source was added to object type PropertyTargetDefinition
* Input field source of type String was added to input object type PropertyTargetDefinitionInput

## Schema changes for 2024-06-25

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member Workflow\.hasWorkflowDispatchTrigger:hasWorkflowDispatchTrigger will be removed. Use has\_workflow\_dispatch\_trigger\_for\_branch(branch\_ref) instead. Effective 2024-10-01.

## Schema changes for 2024-06-21

### The GraphQL schema includes these changes:

* Type 'ConvertProjectV2DraftIssueItemToIssueInput' was added
* Type 'ConvertProjectV2DraftIssueItemToIssuePayload' was added
* Type 'CreateProjectV2StatusUpdateInput' was added
* Type 'CreateProjectV2StatusUpdatePayload' was added
* Type 'DeleteProjectV2StatusUpdateInput' was added
* Type 'DeleteProjectV2StatusUpdatePayload' was added
* Type 'ProjectV2StatusOrder' was added
* Type 'ProjectV2StatusUpdate' was added
* Type 'ProjectV2StatusUpdateConnection' was added
* Type 'ProjectV2StatusUpdateEdge' was added
* Type 'ProjectV2StatusUpdateOrderField' was added
* Type 'ProjectV2StatusUpdateStatus' was added
* Type 'UpdateProjectV2StatusUpdateInput' was added
* Type 'UpdateProjectV2StatusUpdatePayload' was added
* Field 'convertProjectV2DraftIssueItemToIssuewas added to object typeMutation'
* Field 'createProjectV2StatusUpdatewas added to object typeMutation'
* Field 'deleteProjectV2StatusUpdatewas added to object typeMutation'
* Field 'updateProjectV2StatusUpdatewas added to object typeMutation'
* Field statusUpdates was added to object type 'ProjectV2'

## Schema changes for 2024-06-14

### The GraphQL schema includes these changes:

* Field readme was added to object type Enterprise
* Field readmeHTML was added to object type Enterprise

## Schema changes for 2024-06-13

### The GraphQL schema includes these changes:

* Type AcceptEnterpriseMemberInvitationInput was added
* Type AcceptEnterpriseMemberInvitationPayload was added
* Type CancelEnterpriseMemberInvitationInput was added
* Type CancelEnterpriseMemberInvitationPayload was added
* Type EnterpriseMemberInvitation was added
* Type EnterpriseMemberInvitationConnection was added
* Type EnterpriseMemberInvitationEdge was added
* Type EnterpriseMemberInvitationOrder was added
* Type EnterpriseMemberInvitationOrderField was added
* Type InviteEnterpriseMemberInput was added
* Type InviteEnterpriseMemberPayload was added
* Field pendingUnaffiliatedMemberInvitations was added to object type EnterpriseOwnerInfo
* Field acceptEnterpriseMemberInvitation was added to object type Mutation
* Field cancelEnterpriseMemberInvitation was added to object type Mutation
* Field inviteEnterpriseMember was added to object type Mutation
* Field enterpriseMemberInvitation was added to object type Query
* Field enterpriseMemberInvitationByToken was added to object type Query

## Schema changes for 2024-05-24

### The GraphQL schema includes these changes:

* Type CopilotEndpoints was added
* Field copilotEndpoints was added to object type User

## Schema changes for 2024-05-20

### The GraphQL schema includes these changes:

* Field announcementCreatedAt was added to interface AnnouncementBanner
* Field announcementCreatedAt was added to object type Enterprise
* Field announcementCreatedAt was added to object type Organization

## Schema changes for 2024-05-17

### The GraphQL schema includes these changes:

* Enum value 'BRANCH\_POLICYwas added to enumDeploymentProtectionRuleType'

## Schema changes for 2024-05-15

### The GraphQL schema includes these changes:

* Type EnvironmentPinnedFilterField was added
* Type PinEnvironmentInput was added
* Type PinEnvironmentPayload was added
* Type PinnedEnvironment was added
* Type PinnedEnvironmentConnection was added
* Type PinnedEnvironmentEdge was added
* Type PinnedEnvironmentOrder was added
* Type PinnedEnvironmentOrderField was added
* Type ReorderEnvironmentInput was added
* Type ReorderEnvironmentPayload was added
* Field isPinned was added to object type Environment
* Field latestCompletedDeployment was added to object type Environment
* Field pinnedPosition was added to object type Environment
* Field pinEnvironment was added to object type Mutation
* Field reorderEnvironment was added to object type Mutation
* Field pinnedEnvironments was added to object type Repository
* Argument pinnedEnvironmentFilter: EnvironmentPinnedFilterField (with default value) added to field Repository.environments

## Schema changes for 2024-05-02

### The GraphQL schema includes these changes:

* Type CodeScanningParameters was added
* Type CodeScanningParametersInput was added
* Type CodeScanningTool was added
* Type CodeScanningToolInput was added
* Enum value 'CODE\_SCANNINGwas added to enumRepositoryRuleType'
* Member CodeScanningParameters was added to Union type RuleParameters
* Input field codeScanning of type CodeScanningParametersInput was added to input object type RuleParametersInput

## Schema changes for 2024-04-27

### The GraphQL schema includes these changes:

* Field deployKey was added to object type RepositoryRulesetBypassActor
* Input field deployKey of type Boolean was added to input object type RepositoryRulesetBypassActorInput

## Schema changes for 2024-04-26

### The GraphQL schema includes these changes:

* Type FileExtensionRestrictionParameters was added
* Type FileExtensionRestrictionParametersInput was added
* Type FilePathRestrictionParameters was added
* Type FilePathRestrictionParametersInput was added
* Type MaxFilePathLengthParameters was added
* Type MaxFilePathLengthParametersInput was added
* Type MaxFileSizeParameters was added
* Type MaxFileSizeParametersInput was added
* Member 'ProjectV2was added to Union typeCloser'
* Enum value 'FILE\_EXTENSION\_RESTRICTIONwas added to enumRepositoryRuleType'
* Enum value 'FILE\_PATH\_RESTRICTIONwas added to enumRepositoryRuleType'
* Enum value 'MAX\_FILE\_PATH\_LENGTHwas added to enumRepositoryRuleType'
* Enum value 'MAX\_FILE\_SIZEwas added to enumRepositoryRuleType'
* Enum value PUSH was added to enum RepositoryRulesetTarget
* Member FileExtensionRestrictionParameters was added to Union type RuleParameters
* Member FilePathRestrictionParameters was added to Union type RuleParameters
* Member MaxFilePathLengthParameters was added to Union type RuleParameters
* Member MaxFileSizeParameters was added to Union type RuleParameters
* Input field fileExtensionRestriction of type FileExtensionRestrictionParametersInput was added to input object type RuleParametersInput
* Input field filePathRestriction of type FilePathRestrictionParametersInput was added to input object type RuleParametersInput
* Input field maxFilePathLength of type MaxFilePathLengthParametersInput was added to input object type RuleParametersInput
* Input field maxFileSize of type MaxFileSizeParametersInput was added to input object type RuleParametersInput

## Schema changes for 2024-04-16

### The GraphQL schema includes these changes:

* Input field StartRepositoryMigrationInput.sourceRepositoryUrl changed type from URI to URI!

## Schema changes for 2024-04-11

### The GraphQL schema includes these changes:

* Field statusCheckRollup was added to object type PullRequest

## Schema changes for 2024-04-09

### The GraphQL schema includes these changes:

* Type RepositoryPlanFeatures was added
* Field planFeatures was added to object type Repository

## Schema changes for 2024-03-12

### The GraphQL schema includes these changes:

* Enum value 'BUY\_ME\_A\_COFFEEwas added to enumFundingPlatform'

## Schema changes for 2024-03-09

### The GraphQL schema includes these changes:

* Input field recurring of type Boolean was added to input object type CreateSponsorshipsInput

## Schema changes for 2024-03-08

### The GraphQL schema includes these changes:

* Enum value OTECHIE was removed from enum FundingPlatform

## Schema changes for 2024-03-07

### The GraphQL schema includes these changes:

* Argument 'names: \[String!]' (with default value) added to field Repository.environments

## Schema changes for 2024-03-02

### The GraphQL schema includes these changes:

* Enum value 'RULESET\_REQUIRED\_SIGNATURESwas removed from enumRepositoryRuleType'

## Schema changes for 2024-02-27

### The GraphQL schema includes these changes:

* Field fullDatabaseId was added to object type 'ProjectV2Item'

## Schema changes for 2024-02-25

### The GraphQL schema includes these changes:

* Type MarkNotificationAsDoneInput was added
* Type MarkNotificationAsDonePayload was added
* Field markNotificationAsDone was added to object type Mutation

## Schema changes for 2024-02-15

### The GraphQL schema includes these changes:

* Enum value POLAR was added to enum FundingPlatform

## Schema changes for 2024-02-09

### The GraphQL schema includes these changes:

* Field fullDatabaseId was added to object type PullRequest
* Field fullDatabaseId was added to object type PullRequestReview
* Field fullDatabaseId was added to object type PullRequestReviewComment

### The following changes will be made to the schema:

* On member PullRequest.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2024-07-01.
* On member PullRequestReview\.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2024-07-01.
* On member PullRequestReviewComment.databaseId:databaseId will be removed. Use fullDatabaseId instead. Effective 2024-07-01.

## Schema changes for 2024-02-07

### The GraphQL schema includes these changes:

* Field hasSponsorshipsEnabled was added to object type Repository
* Field hasSponsorshipsEnabled was added to interface RepositoryInfo
* Input field hasSponsorshipsEnabled of type Boolean was added to input object type UpdateRepositoryInput

## Schema changes for 2024-02-01

### The GraphQL schema includes these changes:

* Field isInMergeQueue was added to object type PullRequest
* Field isMergeQueueEnabled was added to object type PullRequest
* Field mergeQueue was added to object type PullRequest
* Input field countMembersAlreadyRequested of type Boolean was added to input object type UpdateTeamReviewAssignmentInput
* Input field includeChildTeamMembers of type Boolean was added to input object type UpdateTeamReviewAssignmentInput
* Input field removeTeamRequest of type Boolean was added to input object type UpdateTeamReviewAssignmentInput

## Schema changes for 2024-01-31

### The GraphQL schema includes these changes:

* Type PropertyTargetDefinition was added
* Type PropertyTargetDefinitionInput was added
* Type RepositoryPropertyConditionTarget was added
* Type RepositoryPropertyConditionTargetInput was added
* Field repositoryProperty was added to object type RepositoryRuleConditions
* Input field repositoryProperty of type RepositoryPropertyConditionTargetInput was added to input object type RepositoryRuleConditionsInput

## Schema changes for 2024-01-27

### The GraphQL schema includes these changes:

* Field billingEmail was added to object type Enterprise

## Schema changes for 2024-01-25

### The GraphQL schema includes these changes:

* Type SponsorAndLifetimeValue was added
* Type SponsorAndLifetimeValueConnection was added
* Type SponsorAndLifetimeValueEdge was added
* Type SponsorAndLifetimeValueOrder was added
* Type SponsorAndLifetimeValueOrderField was added
* Field lifetimeReceivedSponsorshipValues was added to object type Organization
* Field lifetimeReceivedSponsorshipValues was added to interface Sponsorable
* Field lifetimeReceivedSponsorshipValues was added to object type User

## Schema changes for 2024-01-23

### The GraphQL schema includes these changes:

* Field id was added to object type UnpinIssuePayload

## Schema changes for 2024-01-10

### The GraphQL schema includes these changes:

* Argument visibility: RepositoryVisibility added to field Organization.repositories
* Argument visibility: RepositoryVisibility added to field Repository.forks
* Argument visibility: RepositoryVisibility added to field RepositoryOwner.repositories
* Argument visibility: RepositoryVisibility added to field Topic.repositories
* Argument visibility: RepositoryVisibility added to field User.repositories
* Argument visibility: RepositoryVisibility added to field User.watching

## Schema changes for 2024-01-09

### The GraphQL schema includes these changes:

* Type RepositoryRuleOrder was added
* Type RepositoryRuleOrderField was added
* Field inviterActor was added to object type OrganizationInvitation
* Field rules was added to object type Ref

### The following changes will be made to the schema:

* On member OrganizationInvitation.inviter:inviter will be removed. inviter will be replaced by inviterActor. Effective 2024-07-01.

## Schema changes for 2024-01-01

### The GraphQL schema includes these changes:

* Input field AcceptTopicSuggestionInput.name changed type from String! to String
* Input field AcceptTopicSuggestionInput.repositoryId changed type from ID! to ID
* Input field DeclineTopicSuggestionInput.name changed type from String! to String
* Input field DeclineTopicSuggestionInput.reason changed type from TopicSuggestionDeclineReason! to TopicSuggestionDeclineReason
* Input field DeclineTopicSuggestionInput.repositoryId changed type from ID! to ID

### The following changes will be made to the schema:

* On member AcceptTopicSuggestionInput.name:name will be removed. Effective 2024-04-01.
* On member AcceptTopicSuggestionInput.repositoryId:repositoryId will be removed. Effective 2024-04-01.
* On member AcceptTopicSuggestionPayload.topic:topic will be removed. Effective 2024-04-01.
* On member DeclineTopicSuggestionInput.name:name will be removed. Effective 2024-04-01.
* On member DeclineTopicSuggestionInput.reason:reason will be removed. Effective 2024-04-01.
* On member DeclineTopicSuggestionInput.repositoryId:repositoryId will be removed. Effective 2024-04-01.
* On member DeclineTopicSuggestionPayload.topic:topic will be removed. Effective 2024-04-01.
* On member TopicSuggestionDeclineReason.NOT\_RELEVANT:NOT\_RELEVANT will be removed. Effective 2024-04-01.
* On member TopicSuggestionDeclineReason.PERSONAL\_PREFERENCE:PERSONAL\_PREFERENCE will be removed. Effective 2024-04-01.
* On member TopicSuggestionDeclineReason.TOO\_GENERAL:TOO\_GENERAL will be removed. Effective 2024-04-01.
* On member TopicSuggestionDeclineReason.TOO\_SPECIFIC:TOO\_SPECIFIC will be removed. Effective 2024-04-01.

## Schema changes for 2023-11-30

### The GraphQL schema includes these changes:

* Type CreateUserListInput was added
* Type CreateUserListPayload was added
* Type DeleteUserListInput was added
* Type DeleteUserListPayload was added
* Type UpdateUserListInput was added
* Type UpdateUserListPayload was added
* Type UpdateUserListsForItemInput was added
* Type UpdateUserListsForItemPayload was added
* Type UserList was added
* Type UserListConnection was added
* Type UserListEdge was added
* Type UserListItems was added
* Type UserListItemsConnection was added
* Type UserListItemsEdge was added
* Type UserListSuggestion was added
* Field createUserList was added to object type Mutation
* Field deleteUserList was added to object type Mutation
* Field updateUserList was added to object type Mutation
* Field updateUserListsForItem was added to object type Mutation
* Field lists was added to object type User
* Field suggestedListNames was added to object type User

## Schema changes for 2023-11-22

### The GraphQL schema includes these changes:

* Type UnsubscribeFromNotificationsInput was added
* Type UnsubscribeFromNotificationsPayload was added
* Field unsubscribeFromNotifications was added to object type Mutation

## Schema changes for 2023-11-18

### The GraphQL schema includes these changes:

* Type UpdatePatreonSponsorabilityInput was added
* Type UpdatePatreonSponsorabilityPayload was added
* Field updatePatreonSponsorability was added to object type Mutation

## Schema changes for 2023-11-17

### The GraphQL schema includes these changes:

* Type MemberFeatureRequestNotification was added
* Field paymentSource was added to object type SponsorsActivity

## Schema changes for 2023-11-14

### The GraphQL schema includes these changes:

* Type SponsorshipPaymentSource was added
* Field paymentSource was added to object type Sponsorship

## Schema changes for 2023-11-04

### The GraphQL schema includes these changes:

* Type AbortRepositoryMigrationInput was added
* Type AbortRepositoryMigrationPayload was added
* Field abortRepositoryMigration was added to object type Mutation
* PullRequestReview object implements Minimizable interface
* Field isMinimized was added to object type PullRequestReview
* Field minimizedReason was added to object type PullRequestReview
* Field viewerCanMinimize was added to object type PullRequestReview

## Schema changes for 2023-11-01

### The GraphQL schema includes these changes:

* Enum value 'FILE\_PATH\_PATTERNwas removed from enumRepositoryRuleType'

## Schema changes for 2023-10-23

### The GraphQL schema includes these changes:

* Field roleName was added to object type PermissionSource

## Schema changes for 2023-10-17

### The GraphQL schema includes these changes:

* Enum value 'TRANSFERRING\_OWNERSHIPwas added to enumRepositoryLockReason'

## Schema changes for 2023-10-12

### The GraphQL schema includes these changes:

* Enum value NPM was added to enum SocialAccountProvider

## Schema changes for 2023-10-11

### The GraphQL schema includes these changes:

* Type WorkflowFileReference was added
* Type WorkflowFileReferenceInput was added
* Type WorkflowsParameters was added
* Type WorkflowsParametersInput was added
* Enum value AUTHORIZATION was added to enum RepositoryRuleType
* Enum value 'FILE\_PATH\_PATTERNwas added to enumRepositoryRuleType'
* Enum value 'LOCK\_BRANCHwas added to enumRepositoryRuleType'
* Enum value 'MAX\_REF\_UPDATESwas added to enumRepositoryRuleType'
* Enum value 'MERGE\_QUEUEwas added to enumRepositoryRuleType'
* Enum value 'MERGE\_QUEUE\_LOCKED\_REFwas added to enumRepositoryRuleType'
* Enum value 'REQUIRED\_REVIEW\_THREAD\_RESOLUTIONwas added to enumRepositoryRuleType'
* Enum value 'REQUIRED\_WORKFLOW\_STATUS\_CHECKSwas added to enumRepositoryRuleType'
* Enum value 'RULESET\_REQUIRED\_SIGNATURESwas added to enumRepositoryRuleType'
* Enum value 'SECRET\_SCANNINGwas added to enumRepositoryRuleType'
* Enum value TAG was added to enum RepositoryRuleType
* Enum value WORKFLOWS was added to enum RepositoryRuleType
* Enum value 'WORKFLOW\_UPDATESwas added to enumRepositoryRuleType'
* Member WorkflowsParameters was added to Union type RuleParameters
* Input field workflows of type WorkflowsParametersInput was added to input object type RuleParametersInput

## Schema changes for 2023-10-07

### The GraphQL schema includes these changes:

* Field preventSelfReview was added to object type DeploymentProtectionRule
* Input field preventSelfReview of type Boolean was added to input object type UpdateEnvironmentInput

## Schema changes for 2023-09-27

### The GraphQL schema includes these changes:

* Field issue was added to object type CreateLinkedBranchPayload

## Schema changes for 2023-09-22

### The GraphQL schema includes these changes:

* Field isAnswered was added to object type Discussion
* Argument answered: Boolean added to field Repository.discussions

## Schema changes for 2023-09-13

### The GraphQL schema includes these changes:

* Field repositoryRuleset was added to object type RepositoryRule

## Schema changes for 2023-09-12

### The GraphQL schema includes these changes:

* Type ContributingGuidelines was added
* Field contributingGuidelines was added to object type Repository

## Schema changes for 2023-09-12

### The GraphQL schema includes these changes:

* Field archivedAt was added to object type Organization

## Schema changes for 2023-09-08

### The GraphQL schema includes these changes:

* Type EnterpriseConnection was added
* Type EnterpriseEdge was added
* Type EnterpriseMembershipType was added
* Type EnterpriseOrder was added
* Type EnterpriseOrderField was added
* Field enterprises was added to object type User

## Schema changes for 2023-08-14

### The GraphQL schema includes these changes:

* Type AddPullRequestReviewThreadReplyInput was added
* Type AddPullRequestReviewThreadReplyPayload was added
* Type PullRequestBranchUpdateMethod was added
* Field githubEnterpriseImporterIpAddresses was added to object type GitHubMetadata
* Field addPullRequestReviewThreadReply was added to object type Mutation
* Input field updateMethod of type PullRequestBranchUpdateMethod was added to input object type UpdatePullRequestBranchInput

## Schema changes for 2023-07-31

### The GraphQL schema includes these changes:

* Argument hasIssuesEnabled: Boolean added to field Organization.repositories
* Argument hasIssuesEnabled: Boolean added to field Repository.forks
* Argument hasIssuesEnabled: Boolean added to field RepositoryOwner.repositories
* Argument hasIssuesEnabled: Boolean added to field Topic.repositories
* Argument hasIssuesEnabled: Boolean added to field User.repositories
* Argument hasIssues: Boolean added to field User.repositoriesContributedTo
* Argument hasIssuesEnabled: Boolean added to field User.watching

## Schema changes for 2023-07-21

### The GraphQL schema includes these changes:

* Type SubscribableThread was added
* Type ThreadSubscriptionFormAction was added
* Type ThreadSubscriptionState was added
* Issue object implements SubscribableThread interface
* Field viewerThreadSubscriptionFormAction was added to object type Issue
* Field viewerThreadSubscriptionStatus was added to object type Issue

## Schema changes for 2023-07-19

### The GraphQL schema includes these changes:

* Argument includePrivate: Boolean (with default value) added to field Organization.sponsorsActivities
* Argument includePrivate: Boolean (with default value) added to field Sponsorable.sponsorsActivities
* Argument includePrivate: Boolean (with default value) added to field User.sponsorsActivities

## Schema changes for 2023-07-13

### The GraphQL schema includes these changes:

* Type EnvironmentOrderField was added
* Type Environments was added
* Argument orderBy: Environments (with default value) added to field Repository.environments

## Schema changes for 2023-07-12

### The GraphQL schema includes these changes:

* Member Bot was added to Union type RequestedReviewer

## Schema changes for 2023-07-11

### The GraphQL schema includes these changes:

* Argument login: String added to field Organization.mannequins

## Schema changes for 2023-07-10

### The GraphQL schema includes these changes:

* Type OrgOauthAppAccessBlockedAuditEntry was added
* Type OrgOauthAppAccessUnblockedAuditEntry was added
* Type RepositoryIdConditionTarget was added
* Type RepositoryIdConditionTargetInput was added
* Type RepositoryRulesetBypassActorBypassMode was added
* Type RepositoryRulesetBypassActorInput was added
* Type RuleBypassMode was removed
* Input field bypassActors of type '\[RepositoryRulesetBypassActorInput!]was added to input object typeCreateRepositoryRulesetInput'
* Input field bypassActorIds was removed from input object type CreateRepositoryRulesetInput
* Input field bypassMode was removed from input object type CreateRepositoryRulesetInput
* Input field CreateTeamDiscussionCommentInput.body changed type from String! to String
* Input field CreateTeamDiscussionCommentInput.discussionId changed type from ID! to ID
* Input field CreateTeamDiscussionInput.body changed type from String! to String
* Input field CreateTeamDiscussionInput.teamId changed type from ID! to ID
* Input field CreateTeamDiscussionInput.title changed type from String! to String
* Argument isArchived: Boolean added to field Organization.repositories
* Member OrgOauthAppAccessBlockedAuditEntry was added to Union type OrganizationAuditEntry
* Member OrgOauthAppAccessUnblockedAuditEntry was added to Union type OrganizationAuditEntry
* Field color was added to object type 'ProjectV2ItemFieldSingleSelectValue'
* Field description was added to object type 'ProjectV2ItemFieldSingleSelectValue'
* Field descriptionHTML was added to object type 'ProjectV2ItemFieldSingleSelectValue'
* Field color was added to object type 'ProjectV2SingleSelectFieldOption'
* Field description was added to object type 'ProjectV2SingleSelectFieldOption'
* Field descriptionHTML was added to object type 'ProjectV2SingleSelectFieldOption'
* Field path was added to object type PullRequestThread
* Field subjectType was added to object type PullRequestThread
* Argument isArchived: Boolean added to field RepositoryOwner.repositories
* Field repositoryId was added to object type RepositoryRuleConditions
* Input field repositoryId of type RepositoryIdConditionTargetInput was added to input object type RepositoryRuleConditionsInput
* Field bypassMode was removed from object type RepositoryRuleset
* Field bypassMode was added to object type RepositoryRulesetBypassActor
* Field organizationAdmin was added to object type RepositoryRulesetBypassActor
* Field repositoryRoleDatabaseId was added to object type RepositoryRulesetBypassActor
* Field repositoryRoleName was added to object type RepositoryRulesetBypassActor
* Field currentPrivacyLevel was added to object type SponsorsActivity
* Input field bypassActors of type '\[RepositoryRulesetBypassActorInput!]was added to input object typeUpdateRepositoryRulesetInput'
* Input field bypassActorIds was removed from input object type UpdateRepositoryRulesetInput
* Input field bypassMode was removed from input object type UpdateRepositoryRulesetInput
* Argument isArchived: Boolean added to field User.repositories

### The following changes will be made to the schema:

* On member CreateTeamDiscussionCommentInput.body:body will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionCommentInput.discussionId:discussionId will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionCommentPayload.teamDiscussionComment:teamDiscussionComment will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionInput.body:body will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionInput.private:private will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionInput.teamId:teamId will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionInput.title:title will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member CreateTeamDiscussionPayload.teamDiscussion:teamDiscussion will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.authorAssociation:authorAssociation will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.bodyVersion:bodyVersion will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.comments:comments will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.commentsResourcePath:commentsResourcePath will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.commentsUrl:commentsUrl will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.isPinned:isPinned will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.isPrivate:isPrivate will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.number:number will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.resourcePath:resourcePath will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.team:team will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.title:title will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.url:url will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussion.viewerCanPin:viewerCanPin will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussionComment.authorAssociation:authorAssociation will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussionComment.bodyVersion:bodyVersion will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussionComment.discussion:discussion will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussionComment.number:number will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussionComment.resourcePath:resourcePath will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.
* On member TeamDiscussionComment.url:url will be removed. Follow the guide at <https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/> to find a suitable replacement. Effective 2024-07-01.

## Schema changes for 2023-06-20

### The GraphQL schema includes these changes:

* Enum value SWIFT was added to enum DependencyGraphEcosystem
* Default value for argument includeParents on field Organization.rulesets changed from false to true
* Argument 'names: \[String!]added to fieldProjectV2SingleSelectField.options'
* Argument includeParents: Boolean (with default value) added to field Repository.ruleset
* Default value for argument includeParents on field Repository.rulesets changed from false to true
* Enum value SWIFT was added to enum SecurityAdvisoryEcosystem

## Schema changes for 2023-06-16

### The GraphQL schema includes these changes:

* Type 'ProjectV2Actor' was added
* Type 'ProjectV2ActorConnection' was added
* Type 'ProjectV2ActorEdge' was added
* Type 'ProjectV2Collaborator' was added
* Type 'ProjectV2Roles' was added
* Type 'UpdateProjectV2CollaboratorsInput' was added
* Type 'UpdateProjectV2CollaboratorsPayload' was added
* Field 'updateProjectV2Collaboratorswas added to object typeMutation'

## Schema changes for 2023-06-13

### The GraphQL schema includes these changes:

* Type 'MarkProjectV2AsTemplateInput' was added
* Type 'MarkProjectV2AsTemplatePayload' was added
* Type 'UnmarkProjectV2AsTemplateInput' was added
* Type 'UnmarkProjectV2AsTemplatePayload' was added
* Field 'markProjectV2AsTemplatewas added to object typeMutation'
* Field 'unmarkProjectV2AsTemplatewas added to object typeMutation'
* Enum value 'ORGANIZATION\_ALWAYSwas added to enumRuleBypassMode'
* Enum value 'ORGANIZATION\_NONEwas added to enumRuleBypassMode'
* Enum value 'ORGANIZATION\_PRS\_ONLYwas added to enumRuleBypassMode'

## Schema changes for 2023-06-09

### The GraphQL schema includes these changes:

* Type WorkflowRunFile was added
* Field file was added to object type WorkflowRun

## Schema changes for 2023-06-07

### The GraphQL schema includes these changes:

* Enum value 'FAILED\_VALIDATIONwas added to enumOrganizationMigrationState'
* Enum value 'PENDING\_VALIDATIONwas added to enumOrganizationMigrationState'

## Schema changes for 2023-06-06

### The GraphQL schema includes these changes:

* Issue object implements Deletable interface
* Field viewerCanDelete was added to object type Issue

## Schema changes for 2023-06-01

### The GraphQL schema includes these changes:

* Field ruleset was added to object type Organization
* Field ruleset was added to object type Repository
* Field createdAt was added to object type RepositoryRuleset
* Field updatedAt was added to object type RepositoryRuleset

## Schema changes for 2023-05-31

### The GraphQL schema includes these changes:

* Field warningsCount was added to interface Migration
* Field warningsCount was added to object type RepositoryMigration

## Schema changes for 2023-04-21

### The GraphQL schema includes these changes:

* Field BranchNamePatternParameters.name changed type from String! to String
* Field BranchNamePatternParameters.operator changed type from String to String!
* Field BranchNamePatternParameters.pattern changed type from String to String!
* Field CommitAuthorEmailPatternParameters.name changed type from String! to String
* Field CommitAuthorEmailPatternParameters.operator changed type from String to String!
* Field CommitAuthorEmailPatternParameters.pattern changed type from String to String!
* Field CommitMessagePatternParameters.name changed type from String! to String
* Field CommitMessagePatternParameters.operator changed type from String to String!
* Field CommitMessagePatternParameters.pattern changed type from String to String!
* Field CommitterEmailPatternParameters.name changed type from String! to String
* Field CommitterEmailPatternParameters.operator changed type from String to String!
* Field CommitterEmailPatternParameters.pattern changed type from String to String!
* Field PullRequestParameters.dismissStaleReviewsOnPush changed type from Boolean to Boolean!
* Field PullRequestParameters.requireCodeOwnerReview changed type from Boolean to Boolean!
* Field PullRequestParameters.requireLastPushApproval changed type from Boolean to Boolean!
* Field PullRequestParameters.requiredApprovingReviewCount changed type from Int to Int!
* Field PullRequestParameters.requiredReviewThreadResolution changed type from Boolean to Boolean!
* Field RefNameConditionTarget.exclude changed type from '\[String!]to\[String!]!'
* Field RefNameConditionTarget.include changed type from '\[String!]to\[String!]!'
* Field RepositoryNameConditionTarget.exclude changed type from '\[String!]to\[String!]!'
* Field RepositoryNameConditionTarget.include changed type from '\[String!]to\[String!]!'
* Field RequiredDeploymentsParameters.requiredDeploymentEnvironments changed type from '\[String!]to\[String!]!'
* Field RequiredStatusChecksParameters.requiredStatusChecks changed type from '\[StatusCheckConfiguration!]to\[StatusCheckConfiguration!]!'
* Field RequiredStatusChecksParameters.strictRequiredStatusChecksPolicy changed type from Boolean to Boolean!
* Field StatusCheckConfiguration.context changed type from String to String!
* Field StatusCheckConfiguration.integrationId changed type from Int! to Int
* Field TagNamePatternParameters.name changed type from String! to String
* Field TagNamePatternParameters.operator changed type from String to String!
* Field TagNamePatternParameters.pattern changed type from String to String!
* Field UpdateParameters.updateAllowsFetchAndMerge changed type from Boolean to Boolean!

## Schema changes for 2023-04-20

### The GraphQL schema includes these changes:

* Field assignees was added to object type IssueTemplate

## Schema changes for 2023-04-19

### The GraphQL schema includes these changes:

* Field labels was added to object type IssueTemplate
* Workflow object implements UniformResourceLocatable interface
* Field resourcePath was added to object type Workflow
* Field url was added to object type Workflow

## Schema changes for 2023-04-18

### The GraphQL schema includes these changes:

* Type BranchNamePatternParameters was added
* Type BranchNamePatternParametersInput was added
* Type BypassActor was added
* Type CommitAuthorEmailPatternParameters was added
* Type CommitAuthorEmailPatternParametersInput was added
* Type CommitMessagePatternParameters was added
* Type CommitMessagePatternParametersInput was added
* Type CommitterEmailPatternParameters was added
* Type CommitterEmailPatternParametersInput was added
* Type CreateRepositoryRulesetInput was added
* Type CreateRepositoryRulesetPayload was added
* Type DeleteRepositoryRulesetInput was added
* Type DeleteRepositoryRulesetPayload was added
* Type PullRequestParameters was added
* Type PullRequestParametersInput was added
* Type RefNameConditionTarget was added
* Type RefNameConditionTargetInput was added
* Type RepositoryNameConditionTarget was added
* Type RepositoryNameConditionTargetInput was added
* Type RepositoryRule was added
* Type RepositoryRuleConditions was added
* Type RepositoryRuleConditionsInput was added
* Type RepositoryRuleConnection was added
* Type RepositoryRuleEdge was added
* Type RepositoryRuleInput was added
* Type RepositoryRuleType was added
* Type RepositoryRuleset was added
* Type RepositoryRulesetBypassActor was added
* Type RepositoryRulesetBypassActorConnection was added
* Type RepositoryRulesetBypassActorEdge was added
* Type RepositoryRulesetConnection was added
* Type RepositoryRulesetEdge was added
* Type RepositoryRulesetTarget was added
* Type RequiredDeploymentsParameters was added
* Type RequiredDeploymentsParametersInput was added
* Type RequiredStatusChecksParameters was added
* Type RequiredStatusChecksParametersInput was added
* Type RuleBypassMode was added
* Type RuleEnforcement was added
* Type RuleParameters was added
* Type RuleParametersInput was added
* Type RuleSource was added
* Type StatusCheckConfiguration was added
* Type StatusCheckConfigurationInput was added
* Type TagNamePatternParameters was added
* Type TagNamePatternParametersInput was added
* Type UpdateParameters was added
* Type UpdateParametersInput was added
* Type UpdateRepositoryRulesetInput was added
* Type UpdateRepositoryRulesetPayload was added
* Field createRepositoryRuleset was added to object type Mutation
* Field deleteRepositoryRuleset was added to object type Mutation
* Field updateRepositoryRuleset was added to object type Mutation
* Field rulesets was added to object type Organization
* Field rulesets was added to object type Repository

## Schema changes for 2023-04-14

### The GraphQL schema includes these changes:

* Type BulkSponsorship was added
* Type CreateSponsorshipsInput was added
* Type CreateSponsorshipsPayload was added
* Field createSponsorships was added to object type Mutation
* Field autoDismissedAt was added to object type RepositoryVulnerabilityAlert
* Enum value 'AUTO\_DISMISSEDwas added to enumRepositoryVulnerabilityAlertState'
* Field viaBulkSponsorship was added to object type SponsorsActivity

## Schema changes for 2023-04-13

### The GraphQL schema includes these changes:

* Type AddedToMergeQueueEvent was added
* Type DequeuePullRequestInput was added
* Type DequeuePullRequestPayload was added
* Type EnqueuePullRequestInput was added
* Type EnqueuePullRequestPayload was added
* Type MergeQueue was added
* Type MergeQueueConfiguration was added
* Type MergeQueueEntry was added
* Type MergeQueueEntryConnection was added
* Type MergeQueueEntryEdge was added
* Type MergeQueueEntryState was added
* Type MergeQueueMergingStrategy was added
* Type RemovedFromMergeQueueEvent was added
* Field dequeuePullRequest was added to object type Mutation
* Field enqueuePullRequest was added to object type Mutation
* Field mergeQueueEntry was added to object type PullRequest
* Member AddedToMergeQueueEvent was added to Union type PullRequestTimelineItems
* Member RemovedFromMergeQueueEvent was added to Union type PullRequestTimelineItems
* Field mergeQueue was added to object type Repository

## Schema changes for 2023-04-11

### The GraphQL schema includes these changes:

* Field archivedAt was added to object type Repository
* Field archivedAt was added to interface RepositoryInfo

## Schema changes for 2023-04-08

### The GraphQL schema includes these changes:

* Type TeamNotificationSetting was added
* Argument notificationSetting: TeamNotificationSetting added to field Organization.teams
* Field notificationSetting was added to object type Team

## Schema changes for 2023-04-07

### The GraphQL schema includes these changes:

* Field fixReason (deprecated) was removed from object type RepositoryVulnerabilityAlert

## Schema changes for 2023-04-04

### The GraphQL schema includes these changes:

* Input field AddPullRequestReviewThreadInput.line changed type from Int! to Int

## Schema changes for 2023-04-03

### The GraphQL schema includes these changes:

* Type BigInt was added
* Field fullDatabaseId was added to object type Issue
* Field fullDatabaseId was added to object type IssueComment
* Field fullDatabaseId was added to object type PinnedIssue

## Schema changes for 2023-04-01

### The GraphQL schema includes these changes:

* Enum value SUCCESS was added to enum DeploymentState

### The following changes will be made to the schema:

* On member Commit.pushedDate:pushedDate will be removed. Effective 2023-07-01.

## Schema changes for 2023-03-29

### The GraphQL schema includes these changes:

* Input field AddPullRequestReviewCommentInput.body changed type from String! to String

### The following changes will be made to the schema:

* On member AddPullRequestReviewCommentInput.body:body will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead Effective 2023-10-01.
* On member AddPullRequestReviewCommentInput.commitOID:commitOID will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead Effective 2023-10-01.
* On member AddPullRequestReviewCommentInput.inReplyTo:inReplyTo will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead Effective 2023-10-01.
* On member AddPullRequestReviewCommentInput.path:path will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead Effective 2023-10-01.
* On member AddPullRequestReviewCommentInput.position:position will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead Effective 2023-10-01.
* On member AddPullRequestReviewCommentInput.pullRequestId:pullRequestId will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead Effective 2023-10-01.
* On member AddPullRequestReviewCommentInput.pullRequestReviewId:pullRequestReviewId will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead Effective 2023-10-01.
* On member AddPullRequestReviewInput.comments:comments will be removed. use the threads argument instead Effective 2023-10-01.
* On member PullRequestReviewComment.originalPosition:originalPosition will be removed. Effective 2023-10-01.
* On member PullRequestReviewComment.position:position will be removed. Use the line and startLine fields instead, which are file line numbers instead of diff line numbers Effective 2023-10-01.

## Schema changes for 2023-03-28

### The GraphQL schema includes these changes:

* Type PullRequestReviewThreadSubjectType was added
* Input field subjectType was added to input object type AddPullRequestReviewThreadInput
* Field subjectType was added to object type PullRequestReviewComment
* Field subjectType was added to object type PullRequestReviewThread

## Schema changes for 2023-03-24

### The GraphQL schema includes these changes:

* Field line was added to object type PullRequestReviewComment
* Field originalLine was added to object type PullRequestReviewComment
* Field originalStartLine was added to object type PullRequestReviewComment
* Field startLine was added to object type PullRequestReviewComment

## Schema changes for 2023-03-23

### The GraphQL schema includes these changes:

* Type EnterpriseServerInstallationMembershipConnection was added
* Type EnterpriseServerInstallationMembershipEdge was added
* Type WorkflowState was added
* Input field CreateMigrationSourceInput.url changed type from String! to String
* Field enterpriseInstallations was added to object type EnterpriseUserAccount
* Input field StartRepositoryMigrationInput.accessToken changed type from String! to String
* Input field StartRepositoryMigrationInput.sourceRepositoryUrl changed type from URI! to URI
* Field pronouns was added to object type User
* Field state was added to object type Workflow

## Schema changes for 2023-03-16

### The GraphQL schema includes these changes:

* Type CloseDiscussionInput was added
* Type CloseDiscussionPayload was added
* Type 'DeleteProjectV2WorkflowInput' was added
* Type 'DeleteProjectV2WorkflowPayload' was added
* Type DiscussionCloseReason was added
* Type DiscussionState was added
* Type DiscussionStateReason was added
* Type ReopenDiscussionInput was added
* Type ReopenDiscussionPayload was added
* Field viewerCanClose was added to interface Closable
* Field viewerCanReopen was added to interface Closable
* Field stateReason was added to object type Discussion
* Field viewerCanClose was added to object type Discussion
* Field viewerCanReopen was added to object type Discussion
* Field viewerCanClose was added to object type Issue
* Field viewerCanReopen was added to object type Issue
* Field viewerCanClose was added to object type Milestone
* Field viewerCanReopen was added to object type Milestone
* Field closeDiscussion was added to object type Mutation
* Field 'deleteProjectV2Workflowwas added to object typeMutation'
* Field reopenDiscussion was added to object type Mutation
* Argument 'states: \[DiscussionState!]added to fieldOrganization.repositoryDiscussions'
* Field viewerCanClose was added to object type Project
* Field viewerCanReopen was added to object type Project
* Field viewerCanClose was added to object type 'ProjectV2'
* Field viewerCanReopen was added to object type 'ProjectV2'
* Field viewerCanClose was added to object type PullRequest
* Field viewerCanReopen was added to object type PullRequest
* Field viewerCanUpdateBranch was added to object type PullRequest
* Argument 'states: \[DiscussionState!]added to fieldRepository.discussions'
* Argument 'states: \[DiscussionState!]added to fieldRepositoryDiscussionAuthor.repositoryDiscussions'
* Argument 'states: \[DiscussionState!]added to fieldUser.repositoryDiscussions'

## Schema changes for 2023-03-11

### The GraphQL schema includes these changes:

* Argument login: String added to field Repository.collaborators

## Schema changes for 2023-03-07

### The GraphQL schema includes these changes:

* Field template was added to object type 'ProjectV2'

## Schema changes for 2023-03-03

### The GraphQL schema includes these changes:

* Type SocialAccount was added
* Type SocialAccountConnection was added
* Type SocialAccountEdge was added
* Type SocialAccountProvider was added
* Field socialAccounts was added to object type User

## Schema changes for 2023-03-01

### The GraphQL schema includes these changes:

* Field requiredDeploymentEnvironments was added to object type BranchProtectionRule
* Field requiresDeployments was added to object type BranchProtectionRule
* Input field requiredDeploymentEnvironments was added to input object type CreateBranchProtectionRuleInput
* Input field requiresDeployments was added to input object type CreateBranchProtectionRuleInput
* Input field requiredDeploymentEnvironments was added to input object type UpdateBranchProtectionRuleInput
* Input field requiresDeployments was added to input object type UpdateBranchProtectionRuleInput
* Field event was added to object type WorkflowRun

## Schema changes for 2023-02-24

### The GraphQL schema includes these changes:

* Input field expectedHeadOid was added to input object type EnablePullRequestAutoMergeInput

## Schema changes for 2023-02-22

### The GraphQL schema includes these changes:

* Type 'CreateProjectV2FieldInput' was added
* Type 'CreateProjectV2FieldPayload' was added
* Type 'DeleteProjectV2FieldInput' was added
* Type 'DeleteProjectV2FieldPayload' was added
* Type 'ProjectV2CustomFieldType' was added
* Type 'ProjectV2SingleSelectFieldOptionColor' was added
* Type 'ProjectV2SingleSelectFieldOptionInput' was added
* Field 'createProjectV2Fieldwas added to object typeMutation'
* Field 'deleteProjectV2Fieldwas added to object typeMutation'

## Schema changes for 2023-02-16

### The GraphQL schema includes these changes:

* Enum value 'ROADMAP\_LAYOUTwas added to enumProjectV2ViewLayout'

## Schema changes for 2023-02-15

### The GraphQL schema includes these changes:

* Field vulnerabilityAlert was added to object type Repository

## Schema changes for 2023-02-11

### The GraphQL schema includes these changes:

* Type 'DeleteProjectV2Input' was added
* Type 'DeleteProjectV2Payload' was added
* Field 'deleteProjectV2was added to object typeMutation'

## Schema changes for 2023-02-09

### The GraphQL schema includes these changes:

* Type 'ProjectV2Workflow' was added
* Type 'ProjectV2WorkflowConnection' was added
* Type 'ProjectV2WorkflowEdge' was added
* Type 'ProjectV2WorkflowOrder' was added
* Type 'ProjectV2WorkflowsOrderField' was added
* Field workflow was added to object type 'ProjectV2'
* Field workflows was added to object type 'ProjectV2'

## Schema changes for 2023-02-08

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member MergeQueueEntry.baseOid:baseOid will be removed. Use baseCommit instead. Effective 2023-07-01.
* On member MergeQueueEntry.headOid:headOid will be removed. Use headCommit instead. Effective 2023-07-01.

## Schema changes for 2023-02-07

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member MergeQueue.headOid:headOid will be removed. Use entry.headOid instead. Effective 2023-07-01.
* On member MergeQueue.mergeMethod:mergeMethod will be removed. Use configuration.merge\_method instead. Effective 2023-07-01.
* On member MergeQueue.mergingEntries:mergingEntries will be removed. Effective 2023-07-01.
* On member MergeQueue.pendingRemovalEntries:pendingRemovalEntries will be removed. Effective 2023-07-01.
* On member MergeQueueEntry.blockedByMergeConflicts:blockedByMergeConflicts will be removed. Use state instead. Effective 2023-07-01.
* On member MergeQueueEntry.checkStatus:checkStatus will be removed. Use state instead. Effective 2023-07-01.
* On member MergeQueueEntry.hasJumpedQueue:hasJumpedQueue will be removed. Use jump instead. Effective 2023-07-01.
* On member MergeQueueEntry.isSolo:isSolo will be removed. Use solo instead. Effective 2023-07-01.

## Schema changes for 2023-02-05

### The GraphQL schema includes these changes:

* Type 'CopyProjectV2Input' was added
* Type 'CopyProjectV2Payload' was added
* Field 'copyProjectV2was added to object typeMutation'

## Schema changes for 2023-02-03

### The GraphQL schema includes these changes:

* Discussion object implements Closable interface
* Field closed was added to object type Discussion
* Field closedAt was added to object type Discussion

## Schema changes for 2023-02-01

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member ProjectV2ItemFieldGroup.field:field will be removed. Check out the ProjectV2ItemFieldGroup#groupByField API as an example for the more capable alternative. Effective 2023-07-01.

## Schema changes for 2023-01-31

### The GraphQL schema includes these changes:

* Type AnnouncementBanner was added
* Type EnterpriseFailedInvitationConnection was added
* Type EnterpriseFailedInvitationEdge was added
* Type OrganizationInvitationSource was added
* Enterprise object implements AnnouncementBanner interface
* Field announcement was added to object type Enterprise
* Field announcementExpiresAt was added to object type Enterprise
* Field announcementUserDismissible was added to object type Enterprise
* Field failedInvitations was added to object type EnterpriseOwnerInfo
* Argument invitationSource: OrganizationInvitationSource added to field EnterpriseOwnerInfo.pendingMemberInvitations
* Organization object implements AnnouncementBanner interface
* Field announcement was added to object type Organization
* Field announcementExpiresAt was added to object type Organization
* Field announcementUserDismissible was added to object type Organization
* Field invitationSource was added to object type OrganizationInvitation

## Schema changes for 2023-01-28

### The GraphQL schema includes these changes:

* Type RemoveEnterpriseMemberInput was added
* Type RemoveEnterpriseMemberPayload was added
* Field removeEnterpriseMember was added to object type Mutation

## Schema changes for 2023-01-27

### The GraphQL schema includes these changes:

* Type RevertPullRequestInput was added
* Type RevertPullRequestPayload was added
* Field revertPullRequest was added to object type Mutation

### The following changes will be made to the schema:

* On member MergeQueue.headOid:headOid will be removed. Use entry.headOid instead. Effective 2023-07-01.
* On member MergeQueue.mergeMethod:mergeMethod will be removed. Use configuration.merge\_method instead. Effective 2023-07-01.
* On member MergeQueue.mergingEntries:mergingEntries will be removed. Effective 2023-07-01.
* On member MergeQueue.pendingRemovalEntries:pendingRemovalEntries will be removed. Effective 2023-07-01.
* On member MergeQueueEntry.blockedByMergeConflicts:blockedByMergeConflicts will be removed. Use state instead. Effective 2023-07-01.
* On member MergeQueueEntry.checkStatus:checkStatus will be removed. Use state instead. Effective 2023-07-01.
* On member MergeQueueEntry.hasJumpedQueue:hasJumpedQueue will be removed. Use jump instead. Effective 2023-07-01.
* On member MergeQueueEntry.isSolo:isSolo will be removed. Use solo instead. Effective 2023-07-01.

## Schema changes for 2023-01-19

### The GraphQL schema includes these changes:

* Argument orderBy: OrganizationOrder added to field OrganizationsHovercardContext.relevantOrganizations
* Argument orderBy: OrganizationOrder added to field User.organizations

## Schema changes for 2023-01-18

### The GraphQL schema includes these changes:

* Type AddProjectDraftIssueInput was removed
* Type AddProjectDraftIssuePayload was removed
* Type AddProjectNextItemInput was removed
* Type AddProjectNextItemPayload was removed
* Type DeleteProjectNextItemInput was removed
* Type DeleteProjectNextItemPayload was removed
* Type ProjectItemType was removed
* Type ProjectNext was removed
* Type ProjectNextConnection was removed
* Type ProjectNextEdge was removed
* Type ProjectNextField was removed
* Type ProjectNextFieldCommon was removed
* Type ProjectNextFieldConfiguration was removed
* Type ProjectNextFieldConfigurationConnection was removed
* Type ProjectNextFieldConfigurationEdge was removed
* Type ProjectNextFieldConnection was removed
* Type ProjectNextFieldEdge was removed
* Type ProjectNextFieldType was removed
* Type ProjectNextItem was removed
* Type ProjectNextItemConnection was removed
* Type ProjectNextItemContent was removed
* Type ProjectNextItemEdge was removed
* Type ProjectNextItemFieldValue was removed
* Type ProjectNextItemFieldValueConnection was removed
* Type ProjectNextItemFieldValueEdge was removed
* Type ProjectNextIterationField was removed
* Type ProjectNextIterationFieldConfiguration was removed
* Type ProjectNextIterationFieldIteration was removed
* Type ProjectNextOrderField was removed
* Type ProjectNextOwner was removed
* Type ProjectNextSingleSelectField was removed
* Type ProjectNextSingleSelectFieldOption was removed
* Type ProjectView was removed
* Type ProjectViewConnection was removed
* Type ProjectViewEdge was removed
* Type ProjectViewLayout was removed
* Type SortBy was removed
* Type UpdateProjectDraftIssueInput was removed
* Type UpdateProjectDraftIssuePayload was removed
* Type UpdateProjectNextInput was removed
* Type UpdateProjectNextItemFieldInput was removed
* Type UpdateProjectNextItemFieldPayload was removed
* Type UpdateProjectNextPayload was removed
* Field project was removed from object type DraftIssue
* Field projectItem was removed from object type DraftIssue
* Issue object type no longer implements ProjectNextOwner interface
* Field projectNext (deprecated) was removed from object type Issue
* Field projectNextItems was removed from object type Issue
* Field projectsNext (deprecated) was removed from object type Issue
* Field addProjectDraftIssue (deprecated) was removed from object type Mutation
* Field addProjectNextItem (deprecated) was removed from object type Mutation
* Field deleteProjectNextItem (deprecated) was removed from object type Mutation
* Field updateProjectDraftIssue (deprecated) was removed from object type Mutation
* Field updateProjectNext (deprecated) was removed from object type Mutation
* Field updateProjectNextItemField (deprecated) was removed from object type Mutation
* Organization object type no longer implements ProjectNextOwner interface
* Field projectNext (deprecated) was removed from object type Organization
* Field projectsNext (deprecated) was removed from object type Organization
* PullRequest object type no longer implements ProjectNextOwner interface
* Field projectNext (deprecated) was removed from object type PullRequest
* Field projectNextItems (deprecated) was removed from object type PullRequest
* Field projectsNext (deprecated) was removed from object type PullRequest
* Field projectNext (deprecated) was removed from object type Repository
* Field projectsNext (deprecated) was removed from object type Repository
* User object type no longer implements ProjectNextOwner interface
* Field projectNext (deprecated) was removed from object type User
* Field projectsNext (deprecated) was removed from object type User

## Schema changes for 2023-01-15

### The GraphQL schema includes these changes:

* Argument includeUnpublished: Boolean added to field SponsorsListing.tiers

## Schema changes for 2023-01-10

### The GraphQL schema includes these changes:

* Type OrganizationMigration was added
* Type OrganizationMigrationState was added
* Type ProjectNextFieldConfiguration was added
* Type ProjectNextFieldConfigurationConnection was added
* Type ProjectNextFieldConfigurationEdge was added
* Type ProjectNextIterationField was added
* Type ProjectNextIterationFieldConfiguration was added
* Type ProjectNextIterationFieldIteration was added
* Type ProjectNextSingleSelectField was added
* Type ProjectNextSingleSelectFieldOption was added
* Type PublishSponsorsTierInput was added
* Type PublishSponsorsTierPayload was added
* Type RetireSponsorsTierInput was added
* Type RetireSponsorsTierPayload was added
* Type StartOrganizationMigrationInput was added
* Type StartOrganizationMigrationPayload was added
* Type StripeConnectAccount was added
* Field reactionGroups was added to object type AddReactionPayload
* Input field headRepositoryId was added to input object type CreatePullRequestInput
* Field publishSponsorsTier was added to object type Mutation
* Field retireSponsorsTier was added to object type Mutation
* Field startOrganizationMigration was added to object type Mutation
* Field totalSponsorshipAmountAsSponsorInCents was added to object type Organization
* Argument activeOnly: Boolean added to field Organization.sponsorshipForViewerAsSponsor
* Argument activeOnly: Boolean added to field Organization.sponsorshipForViewerAsSponsorable
* Argument activeOnly: Boolean added to field Organization.sponsorshipsAsMaintainer
* Argument activeOnly: Boolean added to field Organization.sponsorshipsAsSponsor
* Field fieldConstraints was added to object type ProjectNext
* Field projectFieldConstraint was added to object type ProjectNextItemFieldValue
* Field reactionGroups was added to object type RemoveReactionPayload
* Field hasVulnerabilityAlertsEnabled was added to object type Repository
* Field totalSponsorshipAmountAsSponsorInCents was added to interface Sponsorable
* Argument activeOnly: Boolean added to field Sponsorable.sponsorshipForViewerAsSponsor
* Argument activeOnly: Boolean added to field Sponsorable.sponsorshipForViewerAsSponsorable
* Argument activeOnly: Boolean added to field Sponsorable.sponsorshipsAsMaintainer
* Argument activeOnly: Boolean added to field Sponsorable.sponsorshipsAsSponsor
* Field activeStripeConnectAccount was added to object type SponsorsListing
* Field isActive was added to object type Sponsorship
* Field author was added to object type SponsorshipNewsletter
* Input field fieldConstraintId was added to input object type UpdateProjectNextItemFieldInput
* Input field fieldWithSettingId was added to input object type UpdateProjectNextItemFieldInput
* Field totalSponsorshipAmountAsSponsorInCents was added to object type User
* Argument activeOnly: Boolean added to field User.sponsorshipForViewerAsSponsor
* Argument activeOnly: Boolean added to field User.sponsorshipForViewerAsSponsorable
* Argument activeOnly: Boolean added to field User.sponsorshipsAsMaintainer
* Argument activeOnly: Boolean added to field User.sponsorshipsAsSponsor

### The following changes will be made to the schema:

* On member PackageType.RUBYGEMS:RUBYGEMS will be removed. Effective 2022-12-28.
* On member PackageType.MAVEN:MAVEN will be removed. Effective 2023-02-10.

## Schema changes for 2022-12-09

### The GraphQL schema includes these changes:

* Type Claimable was added
* Type CreateAttributionInvitationInput was added
* Type CreateAttributionInvitationPayload was added
* Type CreateSponsorsListingInput was added
* Type CreateSponsorsListingPayload was added
* Type MannequinConnection was added
* Type MannequinEdge was added
* Type MannequinOrder was added
* Type MannequinOrderField was added
* Type SponsorsCountryOrRegionCode was added
* Field createAttributionInvitation was added to object type Mutation
* Field createSponsorsListing was added to object type Mutation
* Field mannequins was added to object type Organization
* Field isDraft was added to object type SponsorsTierAdminInfo
* Field isPublished was added to object type SponsorsTierAdminInfo
* Field isRetired was added to object type SponsorsTierAdminInfo

### The following changes will be made to the schema:

* On member RepositoryVulnerabilityAlert.fixReason:fixReason will be removed. Effective 2023-04-01.

## Schema changes for 2022-12-07

### The GraphQL schema includes these changes:

* Field fiscalHost was added to object type SponsorsListing
* WorkflowRun object implements UniformResourceLocatable interface

### The following changes will be made to the schema:

* On member PackageType.NPM:NPM will be removed. Effective 2022-11-21.
* On member PackageType.NUGET:NUGET will be removed. Effective 2022-11-21.

## Schema changes for 2022-12-02

### The GraphQL schema includes these changes:

* Type SponsorsListingFeatureableItem was added
* Field featureable was added to object type SponsorsListingFeaturedItem

## Schema changes for 2022-12-01

### The GraphQL schema includes these changes:

* Field totalCommentsCount was added to object type PullRequest

## Schema changes for 2022-11-29

### The GraphQL schema includes these changes:

* Enum value 'TRADE\_RESTRICTIONwas added to enumRepositoryLockReason'

## Schema changes for 2022-11-24

### The GraphQL schema includes these changes:

* Type AddEnterpriseOrganizationMemberInput was added
* Type AddEnterpriseOrganizationMemberPayload was added
* Field addEnterpriseOrganizationMember was added to object type Mutation

## Schema changes for 2022-11-18

### The GraphQL schema includes these changes:

* Type SponsorsListingFeaturedItem was added
* Type SponsorsListingFeaturedItemFeatureableType was added
* Field featuredItems was added to object type SponsorsListing

## Schema changes for 2022-11-17

### The GraphQL schema includes these changes:

* Argument includeAsSponsor: Boolean added to field Organization.sponsorsActivities
* Argument includeAsSponsor: Boolean added to field Sponsorable.sponsorsActivities
* Argument includeAsSponsor: Boolean added to field User.sponsorsActivities

## Schema changes for 2022-11-16

### The GraphQL schema includes these changes:

* Type TransferEnterpriseOrganizationInput was added
* Type TransferEnterpriseOrganizationPayload was added
* Field transferEnterpriseOrganization was added to object type Mutation
* Argument 'maintainerLogins: \[String!]added to fieldOrganization.sponsorshipsAsSponsor'
* Argument 'maintainerLogins: \[String!]added to fieldSponsorable.sponsorshipsAsSponsor'
* Field contactEmailAddress was added to object type SponsorsListing
* Field nameRaw was added to object type Submodule
* Field pathRaw was added to object type Submodule
* Field nameRaw was added to object type TreeEntry
* Field pathRaw was added to object type TreeEntry
* Argument 'maintainerLogins: \[String!]added to fieldUser.sponsorshipsAsSponsor'

## Schema changes for 2022-11-15

### The GraphQL schema includes these changes:

* Input field teamId was added to input object type 'CreateProjectV2Input'
* Field billingCountryOrRegion was added to object type SponsorsListing
* Field residenceCountryOrRegion was added to object type SponsorsListing

### The following changes will be made to the schema:

* On member Repository.squashPrTitleUsedAsDefault:squashPrTitleUsedAsDefault will be removed. Use Repository.squashMergeCommitTitle instead. Effective 2023-04-01.

## Schema changes for 2022-11-12

### The GraphQL schema includes these changes:

* Input field repositoryId was added to input object type 'CreateProjectV2Input'

## Schema changes for 2022-11-11

### The GraphQL schema includes these changes:

* Type 'LinkProjectV2ToTeamInput' was added
* Type 'LinkProjectV2ToTeamPayload' was added
* Type 'ProjectV2Filters' was added
* Type 'ProjectV2State' was added
* Type 'UnlinkProjectV2FromTeamInput' was added
* Type 'UnlinkProjectV2FromTeamPayload' was added
* Field 'linkProjectV2ToTeamwas added to object typeMutation'
* Field 'unlinkProjectV2FromTeamwas added to object typeMutation'
* Argument 'filterBy: ProjectV2Filtersadded to fieldTeam.projectsV2'
* Argument query: String added to field 'Team.projectsV2'

## Schema changes for 2022-11-10

### The GraphQL schema includes these changes:

* Argument since: DateTime added to field Organization.sponsorsActivities
* Argument until: DateTime added to field Organization.sponsorsActivities
* Argument since: DateTime added to field Sponsorable.sponsorsActivities
* Argument until: DateTime added to field Sponsorable.sponsorsActivities
* Argument since: DateTime added to field User.sponsorsActivities
* Argument until: DateTime added to field User.sponsorsActivities

## Schema changes for 2022-11-05

### The GraphQL schema includes these changes:

* Field hasDiscussionsEnabled was added to interface RepositoryInfo

## Schema changes for 2022-11-02

### The GraphQL schema includes these changes:

* Type 'ArchiveProjectV2ItemInput' was added
* Type 'ArchiveProjectV2ItemPayload' was added
* Type 'LinkProjectV2ToRepositoryInput' was added
* Type 'LinkProjectV2ToRepositoryPayload' was added
* Type 'UnarchiveProjectV2ItemInput' was added
* Type 'UnarchiveProjectV2ItemPayload' was added
* Type 'UnlinkProjectV2FromRepositoryInput' was added
* Type 'UnlinkProjectV2FromRepositoryPayload' was added
* Field lockAllowsFetchAndMerge was added to object type BranchProtectionRule
* Field lockBranch was added to object type BranchProtectionRule
* Field requireLastPushApproval was added to object type BranchProtectionRule
* Input field lockAllowsFetchAndMerge was added to input object type CreateBranchProtectionRuleInput
* Input field lockBranch was added to input object type CreateBranchProtectionRuleInput
* Input field requireLastPushApproval was added to input object type CreateBranchProtectionRuleInput
* Field 'archiveProjectV2Itemwas added to object typeMutation'
* Field 'linkProjectV2ToRepositorywas added to object typeMutation'
* Field 'unarchiveProjectV2Itemwas added to object typeMutation'
* Field 'unlinkProjectV2FromRepositorywas added to object typeMutation'
* Enum value 'TRACKED\_BYwas added to enumProjectNextFieldType'
* Enum value 'TRACKED\_BYwas added to enumProjectV2FieldType'
* Field hasDiscussionsEnabled was added to object type Repository
* Input field lockAllowsFetchAndMerge was added to input object type UpdateBranchProtectionRuleInput
* Input field lockBranch was added to input object type UpdateBranchProtectionRuleInput
* Input field requireLastPushApproval was added to input object type UpdateBranchProtectionRuleInput
* Input field hasDiscussionsEnabled was added to input object type UpdateRepositoryInput

### The following changes will be made to the schema:

* On member ProjectNextFieldType.TRACKED\_BY:TRACKED\_BY will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.

## Schema changes for 2022-10-24

### The GraphQL schema includes these changes:

* Field filename was added to object type IssueTemplate

## Schema changes for 2022-10-21

### The GraphQL schema includes these changes:

* Field teams was added to object type 'ProjectV2'
* Field 'projectV2was added to object typeTeam'
* Field 'projectsV2was added to object typeTeam'

## Schema changes for 2022-10-19

### The GraphQL schema includes these changes:

* Field language was added to object type TreeEntry

## Schema changes for 2022-10-18

### The GraphQL schema includes these changes:

* Type Comparison was added
* Type ComparisonCommitConnection was added
* Type ComparisonStatus was added
* Type 'ProjectV2SortByField' was added
* Type 'ProjectV2SortByFieldConnection' was added
* Type 'ProjectV2SortByFieldEdge' was added
* Field sortByFields was added to object type 'ProjectV2View'
* Field verticalGroupByFields was added to object type 'ProjectV2View'
* Field compare was added to object type Ref

### The following changes will be made to the schema:

* On member ProjectV2View\.sortBy:sortBy will be removed. Check out the ProjectV2View#sort\_by\_fields API as an example for the more capable alternative. Effective 2023-04-01.
* On member ProjectV2View\.verticalGroupBy:verticalGroupBy will be removed. Check out the ProjectV2View#vertical\_group\_by\_fields API as an example for the more capable alternative. Effective 2023-04-01.

## Schema changes for 2022-10-07

### The GraphQL schema includes these changes:

* Enum value PUB was added to enum DependencyGraphEcosystem
* Field groupByFields was added to object type 'ProjectV2View'
* Enum value PUB was added to enum SecurityAdvisoryEcosystem

### The following changes will be made to the schema:

* On member ProjectV2View\.groupBy:groupBy will be removed. Check out the ProjectV2View#group\_by\_fields API as an example for the more capable alternative. Effective 2023-04-01.

## Schema changes for 2022-10-03

### The GraphQL schema includes these changes:

* Type CreateLinkedBranchInput was added
* Type CreateLinkedBranchPayload was added
* Type DeleteLinkedBranchInput was added
* Type DeleteLinkedBranchPayload was added
* Type LinkedBranch was added
* Type LinkedBranchConnection was added
* Type LinkedBranchEdge was added
* Field linkedBranches was added to object type Issue
* Field createLinkedBranch was added to object type Mutation
* Field deleteLinkedBranch was added to object type Mutation

## Schema changes for 2022-09-30

### The GraphQL schema includes these changes:

* Field view was added to object type 'ProjectV2'

## Schema changes for 2022-09-28

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member AddProjectDraftIssueInput.assigneeIds:assigneeIds will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member AddProjectDraftIssueInput.body:body will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member AddProjectDraftIssueInput.projectId:projectId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member AddProjectDraftIssueInput.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member AddProjectDraftIssuePayload.projectNextItem:projectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member AddProjectNextItemInput.contentId:contentId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member AddProjectNextItemInput.projectId:projectId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member AddProjectNextItemPayload.projectNextItem:projectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member DeleteProjectNextItemInput.itemId:itemId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member DeleteProjectNextItemInput.projectId:projectId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member DeleteProjectNextItemPayload.deletedItemId:deletedItemId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Issue.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Issue.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Mutation.addProjectDraftIssue:addProjectDraftIssue will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Mutation.addProjectNextItem:addProjectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Mutation.deleteProjectNextItem:deleteProjectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Mutation.updateProjectDraftIssue:updateProjectDraftIssue will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Mutation.updateProjectNext:updateProjectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Mutation.updateProjectNextItemField:updateProjectNextItemField will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Organization.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Organization.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Organization.recentProjectsNext:recentProjectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.closed:closed will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.creator:creator will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.defaultView:defaultView will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.description:description will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.fieldConstraints:fieldConstraints will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.fields:fields will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.items:items will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.number:number will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.owner:owner will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.public:public will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.repositories:repositories will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.resourcePath:resourcePath will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.shortDescription:shortDescription will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.url:url will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNext.views:views will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextField.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextField.dataType:dataType will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextField.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextField.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextField.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextField.settings:settings will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextField.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldCommon.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldCommon.dataType:dataType will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldCommon.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldCommon.id:id will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldCommon.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldCommon.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldCommon.settings:settings will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldCommon.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.ASSIGNEES:ASSIGNEES will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.DATE:DATE will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.ITERATION:ITERATION will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.LABELS:LABELS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.LINKED\_PULL\_REQUESTS:LINKED\_PULL\_REQUESTS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.MILESTONE:MILESTONE will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.NUMBER:NUMBER will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.REPOSITORY:REPOSITORY will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.REVIEWERS:REVIEWERS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.SINGLE\_SELECT:SINGLE\_SELECT will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.TEXT:TEXT will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.TITLE:TITLE will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextFieldType.TRACKS:TRACKS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.content:content will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.creator:creator will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.fieldValues:fieldValues will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.isArchived:isArchived will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.type:type will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItem.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItemFieldValue.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItemFieldValue.creator:creator will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItemFieldValue.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItemFieldValue.projectField:projectField will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItemFieldValue.projectFieldConstraint:projectFieldConstraint will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItemFieldValue.projectItem:projectItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItemFieldValue.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextItemFieldValue.value:value will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationField.configuration:configuration will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationField.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationField.dataType:dataType will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationField.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationField.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationField.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationField.settings:settings will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationField.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationFieldConfiguration.completedIterations:completedIterations will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationFieldConfiguration.duration:duration will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationFieldConfiguration.iterations:iterations will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationFieldConfiguration.startDay:startDay will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationFieldIteration.duration:duration will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationFieldIteration.id:id will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationFieldIteration.startDate:startDate will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationFieldIteration.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextIterationFieldIteration.titleHTML:titleHtml will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextOrderField.CREATED\_AT:CREATED\_AT will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextOrderField.NUMBER:NUMBER will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextOrderField.TITLE:TITLE will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextOrderField.UPDATED\_AT:UPDATED\_AT will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextOwner.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextOwner.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextRecent.recentProjectsNext:recentProjectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectField.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectField.dataType:dataType will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectField.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectField.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectField.options:options will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectField.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectField.settings:settings will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectField.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectFieldOption.id:id will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectFieldOption.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectNextSingleSelectFieldOption.nameHTML:nameHtml will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.filter:filter will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.groupBy:groupBy will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.groupedItems:groupedItems will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.items:items will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.layout:layout will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.number:number will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.sortBy:sortBy will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.verticalGroupBy:verticalGroupBy will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member ProjectView\.visibleFields:visibleFields will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member PullRequest.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member PullRequest.projectNextItems:projectNextItems will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member PullRequest.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Repository.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Repository.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member Repository.recentProjectsNext:recentProjectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextInput.closed:closed will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextInput.description:description will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextInput.projectId:projectId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextInput.public:public will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextInput.shortDescription:shortDescription will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextInput.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextItemFieldInput.fieldConstraintId:fieldConstraintId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextItemFieldInput.fieldId:fieldId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextItemFieldInput.itemId:itemId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextItemFieldInput.value:value will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextItemFieldPayload.projectNextItem:projectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member UpdateProjectNextPayload.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member User.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member User.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.
* On member User.recentProjectsNext:recentProjectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2023-01-01.

## Schema changes for 2022-09-27

### The GraphQL schema includes these changes:

* Field dashboardResourcePath was added to object type SponsorsListing
* Field dashboardUrl was added to object type SponsorsListing
* Field resourcePath was added to object type SponsorsListing
* Field url was added to object type SponsorsListing

## Schema changes for 2022-09-22

### The GraphQL schema includes these changes:

* Field databaseId was added to interface Migration
* Field databaseId was added to object type RepositoryMigration

## Schema changes for 2022-09-16

### The GraphQL schema includes these changes:

* Type 'ClearProjectV2ItemFieldValueInput' was added
* Type 'ClearProjectV2ItemFieldValuePayload' was added
* Field pullRequestReviewComment was added to object type DeletePullRequestReviewCommentPayload
* Argument hasTwoFactorEnabled: Boolean added to field Enterprise.members
* Argument hasTwoFactorEnabled: Boolean added to field EnterpriseOwnerInfo.admins
* Field 'clearProjectV2ItemFieldValuewas added to object typeMutation'

## Schema changes for 2022-09-15

### The GraphQL schema includes these changes:

* Type CheckRunState was added
* Type CheckRunStateCount was added
* Type StatusContextStateCount was added
* Field fields was added to object type 'ProjectV2View'
* Field checkRunCount was added to object type StatusCheckRollupContextConnection
* Field checkRunCountsByState was added to object type StatusCheckRollupContextConnection
* Field statusContextCount was added to object type StatusCheckRollupContextConnection
* Field statusContextCountsByState was added to object type StatusCheckRollupContextConnection

### The following changes will be made to the schema:

* On member ProjectV2View\.visibleFields:visibleFields will be removed. Check out the ProjectV2View#fields API as an example for the more capable alternative. Effective 2023-01-01.

## Schema changes for 2022-09-14

### The GraphQL schema includes these changes:

* Field diffSide was added to object type PullRequestThread
* Field line was added to object type PullRequestThread
* Field startDiffSide was added to object type PullRequestThread
* Field startLine was added to object type PullRequestThread

## Schema changes for 2022-09-08

### The GraphQL schema includes these changes:

* Type EnterpriseAllowPrivateRepositoryForkingPolicyValue was added
* Field changedFilesIfAvailable was added to object type Commit
* Field allowPrivateRepositoryForkingSettingPolicyValue was added to object type EnterpriseOwnerInfo
* Input field policyValue was added to input object type UpdateEnterpriseAllowPrivateRepositoryForkingSettingInput

### The following changes will be made to the schema:

* On member Commit.changedFiles:changedFiles will be removed. Use changedFilesIfAvailable instead. Effective 2023-01-01.

## Schema changes for 2022-09-07

### The GraphQL schema includes these changes:

* Type SshSignature was added
* Type WorkflowRunConnection was added
* Type WorkflowRunEdge was added
* Type WorkflowRunOrder was added
* Type WorkflowRunOrderField was added
* Input field conclusions was added to input object type CheckRunFilter
* Input field statuses was added to input object type CheckRunFilter
* Field runs was added to object type Workflow

## Schema changes for 2022-09-01

### The GraphQL schema includes these changes:

* Type MergeCommitMessage was added
* Type MergeCommitTitle was added
* Type SquashMergeCommitMessage was added
* Type SquashMergeCommitTitle was added
* Field mergeCommitMessage was added to object type Repository
* Field mergeCommitTitle was added to object type Repository
* Field squashMergeCommitMessage was added to object type Repository
* Field squashMergeCommitTitle was added to object type Repository

## Schema changes for 2022-08-26

### The GraphQL schema includes these changes:

* Enum value GITHUB was removed from enum MigrationSourceType
* Enum value GITLAB was removed from enum MigrationSourceType

## Schema changes for 2022-08-24

### The GraphQL schema includes these changes:

* Input field createLabelsIfMissing was added to input object type TransferIssueInput

## Schema changes for 2022-08-22

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member ProjectView\.groupedItems:groupedItems will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.

## Schema changes for 2022-08-19

### The GraphQL schema includes these changes:

* Type UpdateOrganizationWebCommitSignoffSettingInput was added
* Type UpdateOrganizationWebCommitSignoffSettingPayload was added
* Type UpdateRepositoryWebCommitSignoffSettingInput was added
* Type UpdateRepositoryWebCommitSignoffSettingPayload was added
* Enum value UNAFFILIATED was added to enum EnterpriseUserAccountMembershipRole
* Field updateOrganizationWebCommitSignoffSetting was added to object type Mutation
* Field updateRepositoryWebCommitSignoffSetting was added to object type Mutation
* Field webCommitSignoffRequired was added to object type Organization
* Enum value TRACKS was added to enum ProjectNextFieldType
* Enum value TASKS (deprecated) was removed from enum ProjectNextFieldType
* Enum value TRACKS was added to enum 'ProjectV2FieldType'
* Enum value TASKS was removed from enum 'ProjectV2FieldType'
* Field webCommitSignoffRequired was added to object type Repository
* Field dismissComment was added to object type RepositoryVulnerabilityAlert
* Input field lockSource was added to input object type StartRepositoryMigrationInput

### The following changes will be made to the schema:

* On member ProjectNextFieldType.TRACKS:TRACKS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.

## Schema changes for 2022-08-16

### The GraphQL schema includes these changes:

* Field slug was added to object type DiscussionCategory
* Field discussionCategory was added to object type Repository

## Schema changes for 2022-08-11

### The GraphQL schema includes these changes:

* Input field targetRepoVisibility was added to input object type StartRepositoryMigrationInput

## Schema changes for 2022-08-06

### The GraphQL schema includes these changes:

* Enum value TASKS was added to enum ProjectNextFieldType
* Enum value TRACKS (deprecated) was removed from enum ProjectNextFieldType
* Enum value TASKS was added to enum 'ProjectV2FieldType'
* Enum value TRACKS was removed from enum 'ProjectV2FieldType'

### The following changes will be made to the schema:

* On member ProjectNextFieldType.TASKS:TASKS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.

## Schema changes for 2022-08-04

### The GraphQL schema includes these changes:

* Enum value ACTIONS was added to enum SecurityAdvisoryEcosystem

## Schema changes for 2022-08-03

### The GraphQL schema includes these changes:

* Field size was added to object type TreeEntry

## Schema changes for 2022-08-02

### The GraphQL schema includes these changes:

* Field fieldValueByName was added to object type 'ProjectV2Item'

## Schema changes for 2022-07-28

### The GraphQL schema includes these changes:

* Type PullRequestThread was added

## Schema changes for 2022-07-23

### The GraphQL schema includes these changes:

* Field fieldValueByName was removed from object type 'ProjectV2Item'

## Schema changes for 2022-07-22

### The GraphQL schema includes these changes:

* Argument 'actions: \[SponsorsActivityAction!]added to fieldOrganization.sponsorsActivities'
* Field fieldValueByName was added to object type 'ProjectV2Item'
* Argument 'actions: \[SponsorsActivityAction!]added to fieldSponsorable.sponsorsActivities'
* Argument 'actions: \[SponsorsActivityAction!]added to fieldUser.sponsorsActivities'

## Schema changes for 2022-07-19

### The GraphQL schema includes these changes:

* Type EnterpriseUserAccountConnection was removed
* Type EnterpriseUserAccountEdge was removed
* Field userAccounts (deprecated) was removed from object type Enterprise
* Field items was removed from object type 'ProjectV2View'
* Argument 'orderBy: ProjectV2FieldOrderadded to fieldProjectV2View\.groupBy'
* Argument 'orderBy: ProjectV2FieldOrderadded to fieldProjectV2View\.verticalGroupBy'
* Argument 'orderBy: ProjectV2FieldOrderadded to fieldProjectV2View\.visibleFields'
* Field items (deprecated) was removed from object type ProjectView

## Schema changes for 2022-07-14

### The GraphQL schema includes these changes:

* Type 'ProjectV2ItemFieldValueOrder' was added
* Type 'ProjectV2ItemFieldValueOrderField' was added
* Argument 'orderBy: ProjectV2ItemFieldValueOrderadded to fieldProjectV2Item.fieldValues'
* Argument orderBy: PullRequestOrder added to field 'ProjectV2ItemFieldPullRequestValue.pullRequests'

## Schema changes for 2022-07-11

### The GraphQL schema includes these changes:

* Type 'ProjectV2FieldOrder' was added
* Type 'ProjectV2FieldOrderField' was added
* Type 'ProjectV2ItemOrder' was added
* Type 'ProjectV2ItemOrderField' was added
* Type 'ProjectV2ViewOrder' was added
* Type 'ProjectV2ViewOrderField' was added
* Argument 'orderBy: ProjectV2FieldOrderadded to fieldProjectV2.fields'
* Argument 'orderBy: ProjectV2ItemOrderadded to fieldProjectV2.items'
* Argument orderBy: RepositoryOrder added to field 'ProjectV2.repositories'
* Argument 'orderBy: ProjectV2ViewOrderadded to fieldProjectV2.views'

## Schema changes for 2022-06-29

### The GraphQL schema includes these changes:

* Type RepositoryVulnerabilityAlertDependencyScope was added
* Argument 'dependencyScopes: \[RepositoryVulnerabilityAlertDependencyScope!]added to fieldRepository.vulnerabilityAlerts'
* Field dependencyScope was added to object type RepositoryVulnerabilityAlert
* Enum value ERLANG was added to enum SecurityAdvisoryEcosystem

## Schema changes for 2022-06-24

### The GraphQL schema includes these changes:

* Input field AddProjectDraftIssueInput.projectId changed type from ID! to ID
* Input field AddProjectDraftIssueInput.title changed type from String! to String
* Input field AddProjectNextItemInput.contentId changed type from ID! to ID
* Input field AddProjectNextItemInput.projectId changed type from ID! to ID
* Input field DeleteProjectNextItemInput.itemId changed type from ID! to ID
* Input field DeleteProjectNextItemInput.projectId changed type from ID! to ID
* Input field UpdateProjectNextInput.projectId changed type from ID! to ID
* Input field UpdateProjectNextItemFieldInput.itemId changed type from ID! to ID
* Input field UpdateProjectNextItemFieldInput.projectId changed type from ID! to ID
* Input field UpdateProjectNextItemFieldInput.value changed type from String! to String

### The following changes will be made to the schema:

* On member AddProjectDraftIssueInput.assigneeIds:assigneeIds will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member AddProjectDraftIssueInput.body:body will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member AddProjectDraftIssueInput.projectId:projectId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member AddProjectDraftIssueInput.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member AddProjectDraftIssuePayload.projectNextItem:projectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member AddProjectNextItemInput.contentId:contentId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member AddProjectNextItemInput.projectId:projectId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member AddProjectNextItemPayload.projectNextItem:projectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member DeleteProjectNextItemInput.itemId:itemId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member DeleteProjectNextItemInput.projectId:projectId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member DeleteProjectNextItemPayload.deletedItemId:deletedItemId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Issue.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Issue.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member LockMergeQueueInput.branch:branch will be removed. Effective 2022-10-01.
* On member MergeLockedMergeGroupInput.branch:branch will be removed. Effective 2022-10-01.
* On member Mutation.addProjectDraftIssue:addProjectDraftIssue will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Mutation.addProjectNextItem:addProjectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Mutation.deleteProjectNextItem:deleteProjectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Mutation.updateProjectDraftIssue:updateProjectDraftIssue will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Mutation.updateProjectNext:updateProjectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Mutation.updateProjectNextItemField:updateProjectNextItemField will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Organization.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Organization.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Organization.recentProjectsNext:recentProjectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.closed:closed will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.creator:creator will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.defaultView:defaultView will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.description:description will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.fieldConstraints:fieldConstraints will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.fields:fields will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.items:items will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.number:number will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.owner:owner will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.public:public will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.repositories:repositories will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.resourcePath:resourcePath will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.shortDescription:shortDescription will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.url:url will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNext.views:views will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextField.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextField.dataType:dataType will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextField.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextField.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextField.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextField.settings:settings will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextField.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldCommon.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldCommon.dataType:dataType will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldCommon.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldCommon.id:id will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldCommon.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldCommon.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldCommon.settings:settings will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldCommon.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.ASSIGNEES:ASSIGNEES will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.DATE:DATE will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.ITERATION:ITERATION will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.LABELS:LABELS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.LINKED\_PULL\_REQUESTS:LINKED\_PULL\_REQUESTS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.MILESTONE:MILESTONE will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.NUMBER:NUMBER will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.REPOSITORY:REPOSITORY will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.REVIEWERS:REVIEWERS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.SINGLE\_SELECT:SINGLE\_SELECT will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.TEXT:TEXT will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.TITLE:TITLE will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextFieldType.TRACKS:TRACKS will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.content:content will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.creator:creator will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.fieldValues:fieldValues will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.isArchived:isArchived will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.type:type will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItem.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItemFieldValue.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItemFieldValue.creator:creator will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItemFieldValue.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItemFieldValue.projectField:projectField will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItemFieldValue.projectFieldConstraint:projectFieldConstraint will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItemFieldValue.projectItem:projectItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItemFieldValue.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextItemFieldValue.value:value will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationField.configuration:configuration will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationField.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationField.dataType:dataType will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationField.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationField.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationField.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationField.settings:settings will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationField.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationFieldConfiguration.completedIterations:completedIterations will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationFieldConfiguration.duration:duration will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationFieldConfiguration.iterations:iterations will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationFieldConfiguration.startDay:startDay will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationFieldIteration.duration:duration will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationFieldIteration.id:id will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationFieldIteration.startDate:startDate will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationFieldIteration.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextIterationFieldIteration.titleHTML:titleHtml will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextOrderField.CREATED\_AT:CREATED\_AT will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextOrderField.NUMBER:NUMBER will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextOrderField.TITLE:TITLE will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextOrderField.UPDATED\_AT:UPDATED\_AT will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextOwner.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextOwner.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextRecent.recentProjectsNext:recentProjectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectField.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectField.dataType:dataType will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectField.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectField.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectField.options:options will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectField.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectField.settings:settings will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectField.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectFieldOption.id:id will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectFieldOption.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectNextSingleSelectFieldOption.nameHTML:nameHtml will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.createdAt:createdAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.databaseId:databaseId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.filter:filter will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.groupBy:groupBy will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.items:items will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.layout:layout will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.name:name will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.number:number will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.project:project will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.sortBy:sortBy will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.updatedAt:updatedAt will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.verticalGroupBy:verticalGroupBy will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member ProjectView\.visibleFields:visibleFields will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member PullRequest.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member PullRequest.projectNextItems:projectNextItems will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member PullRequest.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Repository.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Repository.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member Repository.recentProjectsNext:recentProjectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UnlockAndResetMergeGroupInput.branch:branch will be removed. Effective 2022-10-01.
* On member UpdateProjectNextInput.closed:closed will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextInput.description:description will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextInput.projectId:projectId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextInput.public:public will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextInput.shortDescription:shortDescription will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextInput.title:title will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextItemFieldInput.fieldConstraintId:fieldConstraintId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextItemFieldInput.fieldId:fieldId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextItemFieldInput.itemId:itemId will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextItemFieldInput.value:value will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextItemFieldPayload.projectNextItem:projectNextItem will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member UpdateProjectNextPayload.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member User.projectNext:projectNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member User.projectsNext:projectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.
* On member User.recentProjectsNext:recentProjectsNext will be removed. Follow the ProjectV2 guide at <https://github.blog/changelog/2022-06-23-the-new-github-issues-june-23rd-update/>, to find a suitable replacement. Effective 2022-10-01.

## Schema changes for 2022-06-23

### The GraphQL schema includes these changes:

* Type AddDiscussionPollVoteInput was added
* Type AddDiscussionPollVotePayload was added
* Type 'AddProjectV2DraftIssueInput' was added
* Type 'AddProjectV2DraftIssuePayload' was added
* Type 'AddProjectV2ItemByIdInput' was added
* Type 'AddProjectV2ItemByIdPayload' was added
* Type 'CreateProjectV2Input' was added
* Type 'CreateProjectV2Payload' was added
* Type 'DeleteProjectV2ItemInput' was added
* Type 'DeleteProjectV2ItemPayload' was added
* Type DiscussionPoll was added
* Type DiscussionPollOption was added
* Type DiscussionPollOptionConnection was added
* Type DiscussionPollOptionEdge was added
* Type DiscussionPollOptionOrder was added
* Type DiscussionPollOptionOrderField was added
* Type OrganizationOrUser was added
* Type 'ProjectV2' was added
* Type 'ProjectV2Connection' was added
* Type 'ProjectV2Edge' was added
* Type 'ProjectV2Field' was added
* Type 'ProjectV2FieldCommon' was added
* Type 'ProjectV2FieldConfiguration' was added
* Type 'ProjectV2FieldConfigurationConnection' was added
* Type 'ProjectV2FieldConfigurationEdge' was added
* Type 'ProjectV2FieldConnection' was added
* Type 'ProjectV2FieldEdge' was added
* Type 'ProjectV2FieldType' was added
* Type 'ProjectV2FieldValue' was added
* Type 'ProjectV2Item' was added
* Type 'ProjectV2ItemConnection' was added
* Type 'ProjectV2ItemContent' was added
* Type 'ProjectV2ItemEdge' was added
* Type 'ProjectV2ItemFieldDateValue' was added
* Type 'ProjectV2ItemFieldIterationValue' was added
* Type 'ProjectV2ItemFieldLabelValue' was added
* Type 'ProjectV2ItemFieldMilestoneValue' was added
* Type 'ProjectV2ItemFieldNumberValue' was added
* Type 'ProjectV2ItemFieldPullRequestValue' was added
* Type 'ProjectV2ItemFieldRepositoryValue' was added
* Type 'ProjectV2ItemFieldReviewerValue' was added
* Type 'ProjectV2ItemFieldSingleSelectValue' was added
* Type 'ProjectV2ItemFieldTextValue' was added
* Type 'ProjectV2ItemFieldUserValue' was added
* Type 'ProjectV2ItemFieldValue' was added
* Type 'ProjectV2ItemFieldValueCommon' was added
* Type 'ProjectV2ItemFieldValueConnection' was added
* Type 'ProjectV2ItemFieldValueEdge' was added
* Type 'ProjectV2ItemType' was added
* Type 'ProjectV2IterationField' was added
* Type 'ProjectV2IterationFieldConfiguration' was added
* Type 'ProjectV2IterationFieldIteration' was added
* Type 'ProjectV2Order' was added
* Type 'ProjectV2OrderField' was added
* Type 'ProjectV2Owner' was added
* Type 'ProjectV2Recent' was added
* Type 'ProjectV2SingleSelectField' was added
* Type 'ProjectV2SingleSelectFieldOption' was added
* Type 'ProjectV2SortBy' was added
* Type 'ProjectV2SortByConnection' was added
* Type 'ProjectV2SortByEdge' was added
* Type 'ProjectV2View' was added
* Type 'ProjectV2ViewConnection' was added
* Type 'ProjectV2ViewEdge' was added
* Type 'ProjectV2ViewLayout' was added
* Type RequestedReviewerConnection was added
* Type RequestedReviewerEdge was added
* Type 'UpdateProjectV2DraftIssueInput' was added
* Type 'UpdateProjectV2DraftIssuePayload' was added
* Type 'UpdateProjectV2Input' was added
* Type 'UpdateProjectV2ItemFieldValueInput' was added
* Type 'UpdateProjectV2ItemFieldValuePayload' was added
* Type 'UpdateProjectV2ItemPositionInput' was added
* Type 'UpdateProjectV2ItemPositionPayload' was added
* Type 'UpdateProjectV2Payload' was added
* Field poll was added to object type Discussion
* Field 'projectV2Itemswas added to object typeDraftIssue'
* Field 'projectsV2was added to object typeDraftIssue'
* Issue object implements 'ProjectV2Owner' interface
* Field projectItems was added to object type Issue
* Field 'projectV2was added to object typeIssue'
* Field 'projectsV2was added to object typeIssue'
* Field addDiscussionPollVote was added to object type Mutation
* Field 'addProjectV2DraftIssuewas added to object typeMutation'
* Field 'addProjectV2ItemByIdwas added to object typeMutation'
* Field 'createProjectV2was added to object typeMutation'
* Field 'deleteProjectV2Itemwas added to object typeMutation'
* Field 'updateProjectV2was added to object typeMutation'
* Field 'updateProjectV2DraftIssuewas added to object typeMutation'
* Field 'updateProjectV2ItemFieldValuewas added to object typeMutation'
* Field 'updateProjectV2ItemPositionwas added to object typeMutation'
* Enum value SUSPENDED was added to enum OrgRemoveMemberAuditEntryMembershipType
* Organization object implements 'ProjectV2Owner' interface
* Organization object implements 'ProjectV2Recent' interface
* Field 'projectV2was added to object typeOrganization'
* Field 'projectsV2was added to object typeOrganization'
* Field recentProjects was added to object type Organization
* PullRequest object implements 'ProjectV2Owner' interface
* Field projectItems was added to object type PullRequest
* Field 'projectV2was added to object typePullRequest'
* Field 'projectsV2was added to object typePullRequest'
* Field viewerCanEditFiles was added to object type PullRequest
* Repository object implements 'ProjectV2Recent' interface
* Field allowUpdateBranch was added to object type Repository
* Field 'projectV2was added to object typeRepository'
* Field 'projectsV2was added to object typeRepository'
* Field recentProjects was added to object type Repository
* User object implements 'ProjectV2Owner' interface
* User object implements 'ProjectV2Recent' interface
* Field 'projectV2was added to object typeUser'
* Field 'projectsV2was added to object typeUser'
* Field recentProjects was added to object type User

### The following changes will be made to the schema:

* On member RepositoryVulnerabilityAlert.fixReason:fixReason will be removed. Effective 2022-10-01.

## Schema changes for 2022-06-13

### The GraphQL schema includes these changes:

### The following changes will be made to the schema:

* On member DependencyGraphDependency.packageLabel:packageLabel will be removed. Use normalized packageName field instead. Effective 2022-10-01.

## Schema changes for 2022-06-10

### The GraphQL schema includes these changes:

* Enum value RUST was added to enum DependencyGraphEcosystem
* Field squashPrTitleUsedAsDefault was added to object type Repository

## Schema changes for 2022-06-06

### The GraphQL schema includes these changes:

* Type SecurityAdvisoryClassification was added
* Type 'ProjectV2Owner' was removed
* Issue object type no longer implements 'ProjectV2Owner' interface
* Organization object type no longer implements 'ProjectV2Owner' interface
* PullRequest object type no longer implements 'ProjectV2Owner' interface
* Argument 'classifications: \[SecurityAdvisoryClassification!]added to fieldQuery.securityAdvisories'
* Argument 'classifications: \[SecurityAdvisoryClassification!]added to fieldQuery.securityVulnerabilities'
* Field classification was added to object type SecurityAdvisory
* Argument 'classifications: \[SecurityAdvisoryClassification!]added to fieldSecurityAdvisory.vulnerabilities'
* User object type no longer implements 'ProjectV2Owner' interface

## Schema changes for 2022-05-31

### The GraphQL schema includes these changes:

* Field viewerIsFollowing was added to object type Organization

## Schema changes for 2022-05-29

### The GraphQL schema includes these changes:

* Type ExternalIdentityAttribute was added
* Type IssueClosedStateReason was added
* Type IssueStateReason was added
* Member App was added to Union type BranchActorAllowanceActor
* Input field stateReason was added to input object type CloseIssueInput
* Field stateReason was added to object type ClosedEvent
* Field attributes was added to object type ExternalIdentitySamlAttributes
* Field stateReason was added to object type Issue
* Enum value 'FAILED\_VALIDATIONwas added to enumMigrationState'
* Enum value 'PENDING\_VALIDATIONwas added to enumMigrationState'
* Field stateReason was added to object type ReopenedEvent
* Member App was added to Union type ReviewDismissalAllowanceActor
* Input field StartRepositoryMigrationInput.accessToken changed type from String to String!

### The following changes will be made to the schema:

* On member RemovePullRequestFromMergeQueueInput.branch:branch will be removed. Effective 2022-10-01.

## Schema changes for 2022-05-10

### The GraphQL schema includes these changes:

* Type FollowOrganizationInput was added
* Type FollowOrganizationPayload was added
* Type UnfollowOrganizationInput was added
* Type UnfollowOrganizationPayload was added
* Type UpdateTeamsRepositoryInput was added
* Type UpdateTeamsRepositoryPayload was added
* Argument 'organizationLogins: \[String!]added to fieldEnterpriseOwnerInfo.pendingMemberInvitations'
* Field migrationLogUrl was added to interface Migration
* Field repositoryName was added to interface Migration
* Field followOrganization was added to object type Mutation
* Field unfollowOrganization was added to object type Mutation
* Field updateTeamsRepository was added to object type Mutation
* Argument repositoryName: String added to field Organization.repositoryMigrations
* Field items was added to object type ProjectView
* Field migrationLogUrl was added to object type RepositoryMigration
* Field repositoryName was added to object type RepositoryMigration

## Schema changes for 2022-04-28

### The GraphQL schema includes these changes:

* Type PatchStatus was added
* Field isUnlicensed (deprecated) was removed from object type EnterpriseMemberEdge
* Field isUnlicensed (deprecated) was removed from object type EnterpriseOutsideCollaboratorEdge
* Argument 'organizationLogins: \[String!]added to fieldEnterpriseOwnerInfo.admins'
* Argument hasTwoFactorEnabled: Boolean added to field EnterpriseOwnerInfo.outsideCollaborators
* Argument 'organizationLogins: \[String!]added to fieldEnterpriseOwnerInfo.outsideCollaborators'
* Field isUnlicensed (deprecated) was removed from object type EnterprisePendingMemberInvitationEdge
* Field changeType was added to object type PullRequestChangedFile

## Schema changes for 2022-04-21

### The GraphQL schema includes these changes:

* Type AddProjectDraftIssueInput was added
* Type AddProjectDraftIssuePayload was added
* Type UpdateProjectDraftIssueInput was added
* Type UpdateProjectDraftIssuePayload was added
* Field availableSeats (deprecated) was removed from object type EnterpriseBillingInfo
* Field seats (deprecated) was removed from object type EnterpriseBillingInfo
* Field addProjectDraftIssue was added to object type Mutation
* Field updateProjectDraftIssue was added to object type Mutation

## Schema changes for 2022-04-14

### The GraphQL schema includes these changes:

* Type 'ProjectV2Owner' was added
* Issue object implements 'ProjectV2Owner' interface
* Organization object implements 'ProjectV2Owner' interface
* PullRequest object implements 'ProjectV2Owner' interface
* Input field skipReleases was added to input object type StartRepositoryMigrationInput
* Field lineCount was added to object type TreeEntry
* User object implements 'ProjectV2Owner' interface

### The following changes will be made to the schema:

* On member UpdateProjectNextItemFieldInput.fieldWithSettingId:fieldWithSettingId will be removed. Use fieldConstraintId instead Effective 2022-10-01.

## Schema changes for 2022-04-03

### The GraphQL schema includes these changes:

* Field blocksCreations was added to object type BranchProtectionRule
* Input field blocksCreations was added to input object type CreateBranchProtectionRuleInput
* Field blocksCreations was added to object type RefUpdateRule
* Input field blocksCreations was added to input object type UpdateBranchProtectionRuleInput

## Schema changes for 2022-03-30

### The GraphQL schema includes these changes:

* Type CreateSponsorsTierInput was added
* Type CreateSponsorsTierPayload was added
* Type DependabotUpdate was added
* Type DependabotUpdateError was added
* Type DraftIssue was added
* Type ProjectItemType was added
* Type ProjectNextFieldCommon was added
* Type ProjectNextFieldType was added
* Type ProjectView was added
* Type ProjectViewConnection was added
* Type ProjectViewEdge was added
* Type ProjectViewLayout was added
* Type SortBy was added
* Type TrackedIssueStates was added
* Type EnterprisePendingCollaboratorConnection was removed
* Type EnterprisePendingCollaboratorEdge was removed
* Input field CreateMigrationSourceInput.accessToken changed type from String! to String
* Field pendingCollaborators (deprecated) was removed from object type EnterpriseOwnerInfo
* Field trackedInIssues was added to object type Issue
* Field trackedIssues was added to object type Issue
* Field trackedIssuesCount was added to object type Issue
* Field createSponsorsTier was added to object type Mutation
* Field views was added to object type ProjectNext
* ProjectNextField object implements Node interface
* ProjectNextField object implements ProjectNextFieldCommon interface
* Field dataType was added to object type ProjectNextField
* Field type was added to object type ProjectNextItem
* Member DraftIssue was added to Union type ProjectNextItemContent
* Enum value 'INVITEE\_LOGIN' (deprecated) was removed from enum RepositoryInvitationOrderField
* Field dependabotUpdate was added to object type RepositoryVulnerabilityAlert
* Input field UpdateProjectNextItemFieldInput.fieldId changed type from ID! to ID

### The following changes will be made to the schema:

* On member AddPullRequestToMergeQueueInput.branch:branch will be removed. Effective 2022-07-01.
* On member Enterprise.userAccounts:userAccounts will be removed. Use the Enterprise.members field instead. Effective 2022-07-01.

## Schema changes for 2022-02-28

### The GraphQL schema includes these changes:

* Type DependencyGraphEcosystem was added
* Field viewerCanMergeAsAdmin was added to object type PullRequest
* Argument ecosystem: DependencyGraphEcosystem added to field Query.sponsorables
* Input field accessToken was added to input object type StartRepositoryMigrationInput
* Input field githubPat was added to input object type StartRepositoryMigrationInput

### The following changes will be made to the schema:

* On member PullRequest.viewerCanOverrideMergeQueue:viewerCanOverrideMergeQueue will be removed. Use PullRequest.viewerCanMergeAsAdmin instead. Effective 2022-04-01.
* On member Repository.defaultMergeQueue:defaultMergeQueue will be removed. Use Repository.mergeQueue instead. Effective 2022-04-01.
* On member Query.sponsorables.dependencyEcosystem:dependencyEcosystem will be removed. Use the ecosystem argument instead. Effective 2022-07-01.

## Schema changes for 2022-02-16

### The GraphQL schema includes these changes:

* Type RepositoryCodeowners was added
* Type RepositoryCodeownersError was added
* Type RepositoryVulnerabilityAlertState was added
* Type UpdateProjectNextInput was added
* Type UpdateProjectNextPayload was added
* Input field milestoneNumber was added to input object type IssueFilters
* Field updateProjectNext was added to object type Mutation
* Field repositories was added to object type ProjectNext
* Argument userLinkedOnly: Boolean added to field PullRequest.closingIssuesReferences
* Field codeowners was added to object type Repository
* Field projectNext was added to object type Repository
* Field projectsNext was added to object type Repository
* Argument 'states: \[RepositoryVulnerabilityAlertState!]added to fieldRepository.vulnerabilityAlerts'
* Field fixReason was added to object type RepositoryVulnerabilityAlert
* Field fixedAt was added to object type RepositoryVulnerabilityAlert
* Field number was added to object type RepositoryVulnerabilityAlert
* Field state was added to object type RepositoryVulnerabilityAlert

## Schema changes for 2022-02-07

### The GraphQL schema includes these changes:

* Type Import was removed
* Input field gitArchiveUrl was added to input object type StartRepositoryMigrationInput
* Input field metadataArchiveUrl was added to input object type StartRepositoryMigrationInput

## Schema changes for 2022-02-03

### The GraphQL schema includes these changes:

* Type AbortQueuedMigrationsInput was added
* Type AbortQueuedMigrationsPayload was added
* Type ActorType was added
* Type CreateMigrationSourceInput was added
* Type CreateMigrationSourcePayload was added
* Type GrantEnterpriseOrganizationsMigratorRoleInput was added
* Type GrantEnterpriseOrganizationsMigratorRolePayload was added
* Type GrantMigratorRoleInput was added
* Type GrantMigratorRolePayload was added
* Type Import was added
* Type Migration was added
* Type MigrationSource was added
* Type MigrationSourceType was added
* Type MigrationState was added
* Type RepositoryMigration was added
* Type RepositoryMigrationConnection was added
* Type RepositoryMigrationEdge was added
* Type RepositoryMigrationOrder was added
* Type RepositoryMigrationOrderDirection was added
* Type RepositoryMigrationOrderField was added
* Type RevokeEnterpriseOrganizationsMigratorRoleInput was added
* Type RevokeEnterpriseOrganizationsMigratorRolePayload was added
* Type RevokeMigratorRoleInput was added
* Type RevokeMigratorRolePayload was added
* Type StartRepositoryMigrationInput was added
* Type StartRepositoryMigrationPayload was added
* Type UpdateEnterpriseOwnerOrganizationRoleInput was added
* Type UpdateEnterpriseOwnerOrganizationRolePayload was added
* Argument login: String added to field EnterpriseIdentityProvider.externalIdentities
* Argument userName: String added to field EnterpriseIdentityProvider.externalIdentities
* Field projectNextItems was added to object type Issue
* Field abortQueuedMigrations was added to object type Mutation
* Field createMigrationSource was added to object type Mutation
* Field grantEnterpriseOrganizationsMigratorRole was added to object type Mutation
* Field grantMigratorRole was added to object type Mutation
* Field revokeEnterpriseOrganizationsMigratorRole was added to object type Mutation
* Field revokeMigratorRole was added to object type Mutation
* Field startRepositoryMigration was added to object type Mutation
* Field updateEnterpriseOwnerOrganizationRole was added to object type Mutation
* Argument login: String added to field OIDCProvider.externalIdentities
* Argument userName: String added to field OIDCProvider.externalIdentities
* Field repositoryMigrations was added to object type Organization
* Argument login: String added to field OrganizationIdentityProvider.externalIdentities
* Argument userName: String added to field OrganizationIdentityProvider.externalIdentities
* Field public was added to object type ProjectNext
* Field shortDescription was added to object type ProjectNext
* Field isArchived was added to object type ProjectNextItem
* Field projectNextItems was added to object type PullRequest

## Schema changes for 2022-01-16

### The GraphQL schema includes these changes:

* Type OrgEnterpriseOwnerOrder was added
* Type OrgEnterpriseOwnerOrderField was added
* Type OrganizationEnterpriseOwnerConnection was added
* Type OrganizationEnterpriseOwnerEdge was added
* Enum value 'LFX\_CROWDFUNDINGwas added to enumFundingPlatform'
* Field enterpriseOwners was added to object type Organization
* Enum value 'ADDED\_TO\_MERGE\_QUEUE\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'REMOVED\_FROM\_MERGE\_QUEUE\_EVENTwas added to enumPullRequestTimelineItemsItemType'

## Schema changes for 2022-01-04

### The GraphQL schema includes these changes:

* Type BypassForcePushAllowance was added
* Type BypassForcePushAllowanceConnection was added
* Type BypassForcePushAllowanceEdge was added
* Field bypassForcePushAllowances was added to object type BranchProtectionRule
* Input field bypassForcePushActorIds was added to input object type CreateBranchProtectionRuleInput
* Field Push.pusher changed type from User! to Actor!
* Input field bypassForcePushActorIds was added to input object type UpdateBranchProtectionRuleInput

## Schema changes for 2021-12-15

### The GraphQL schema includes these changes:

* Type ProjectNextOrderField was added
* Type RoleInOrganization was added
* Type UpdateOrganizationAllowPrivateRepositoryForkingSettingInput was added
* Type UpdateOrganizationAllowPrivateRepositoryForkingSettingPayload was added
* Argument viewerOrganizationRole: RoleInOrganization added to field Enterprise.organizations
* Issue object implements ProjectNextOwner interface
* Field projectNext was added to object type Issue
* Field projectsNext was added to object type Issue
* Field updateOrganizationAllowPrivateRepositoryForkingSetting was added to object type Mutation
* Field membersCanForkPrivateRepositories was added to object type Organization
* Argument query: String added to field Organization.projectsNext
* Argument sortBy: ProjectNextOrderField added to field Organization.projectsNext
* Argument query: String added to field ProjectNextOwner.projectsNext
* Argument sortBy: ProjectNextOrderField added to field ProjectNextOwner.projectsNext
* PullRequest object implements ProjectNextOwner interface
* Field projectNext was added to object type PullRequest
* Field projectsNext was added to object type PullRequest
* Argument query: String added to field User.projectsNext
* Argument sortBy: ProjectNextOrderField added to field User.projectsNext

## Schema changes for 2021-12-11

### The GraphQL schema includes these changes:

* Type ConvertedToDiscussionEvent was added
* Member ConvertedToDiscussionEvent was added to Union type IssueTimelineItems
* Enum value 'CONVERTED\_TO\_DISCUSSION\_EVENTwas added to enumIssueTimelineItemsItemType'
* Member ConvertedToDiscussionEvent was added to Union type PullRequestTimelineItems
* Enum value 'CONVERTED\_TO\_DISCUSSION\_EVENTwas added to enumPullRequestTimelineItemsItemType'

## Schema changes for 2021-12-09

### The GraphQL schema includes these changes:

* Argument filterByAssignable: Boolean added to field Repository.discussionCategories

## Schema changes for 2021-12-03

### The GraphQL schema includes these changes:

* Type BranchActorAllowanceActor was added
* Type BypassPullRequestAllowance was added
* Type BypassPullRequestAllowanceConnection was added
* Type BypassPullRequestAllowanceEdge was added
* Type ContentAttachment was removed
* Type ContentReference was removed
* Type CreateContentAttachmentInput was removed
* Type CreateContentAttachmentPayload was removed
* Field bypassPullRequestAllowances was added to object type BranchProtectionRule
* Input field bypassPullRequestActorIds was added to input object type CreateBranchProtectionRuleInput
* Field createContentAttachment was removed from object type Mutation
* Input field bypassPullRequestActorIds was added to input object type UpdateBranchProtectionRuleInput

## Schema changes for 2021-11-18

### The GraphQL schema includes these changes:

* Type RequiredStatusCheckDescription was added
* Type RequiredStatusCheckInput was added
* Field requiredStatusChecks was added to object type BranchProtectionRule
* Input field requiredStatusChecks was added to input object type CreateBranchProtectionRuleInput
* Input field requiredStatusChecks was added to input object type UpdateBranchProtectionRuleInput

## Schema changes for 2021-11-16

### The GraphQL schema includes these changes:

* Argument followRenames: Boolean added to field Organization.repository
* Argument followRenames: Boolean added to field Query.repository
* Argument followRenames: Boolean added to field RepositoryOwner.repository
* Argument followRenames: Boolean added to field User.repository

## Schema changes for 2021-11-10

### The GraphQL schema includes these changes:

* Type UpdatePullRequestBranchInput was added
* Type UpdatePullRequestBranchPayload was added
* Field updatePullRequestBranch was added to object type Mutation

## Schema changes for 2021-10-29

### The GraphQL schema includes these changes:

* Type DismissReason was added
* Type DismissRepositoryVulnerabilityAlertInput was added
* Type DismissRepositoryVulnerabilityAlertPayload was added
* Field dismissRepositoryVulnerabilityAlert was added to object type Mutation

## Schema changes for 2021-10-22

### The GraphQL schema includes these changes:

* Type AddProjectNextItemInput was added
* Type AddProjectNextItemPayload was added
* Type DeleteProjectNextItemInput was added
* Type DeleteProjectNextItemPayload was added
* Type OIDCProvider was added
* Type OIDCProviderType was added
* Type ProjectNext was added
* Type ProjectNextConnection was added
* Type ProjectNextEdge was added
* Type ProjectNextField was added
* Type ProjectNextFieldConnection was added
* Type ProjectNextFieldEdge was added
* Type ProjectNextItem was added
* Type ProjectNextItemConnection was added
* Type ProjectNextItemContent was added
* Type ProjectNextItemEdge was added
* Type ProjectNextItemFieldValue was added
* Type ProjectNextItemFieldValueConnection was added
* Type ProjectNextItemFieldValueEdge was added
* Type ProjectNextOwner was added
* Type UpdateProjectNextItemFieldInput was added
* Type UpdateProjectNextItemFieldPayload was added
* Field oidcProvider was added to object type EnterpriseOwnerInfo
* Field addProjectNextItem was added to object type Mutation
* Field deleteProjectNextItem was added to object type Mutation
* Field updateProjectNextItemField was added to object type Mutation
* Organization object implements ProjectNextOwner interface
* Field projectNext was added to object type Organization
* Field projectsNext was added to object type Organization
* User object implements ProjectNextOwner interface
* Field projectNext was added to object type User
* Field projectsNext was added to object type User

## Schema changes for 2021-10-04

### The GraphQL schema includes these changes:

* Field repositories was added to object type Topic

## Schema changes for 2021-09-23

### The GraphQL schema includes these changes:

* Enum value RUST was added to enum SecurityAdvisoryEcosystem

## Schema changes for 2021-09-15

### The GraphQL schema includes these changes:

* Type UpdateSponsorshipPreferencesInput was added
* Type UpdateSponsorshipPreferencesPayload was added
* Field updateSponsorshipPreferences was added to object type Mutation

## Schema changes for 2021-09-14

### The GraphQL schema includes these changes:

* Field forkingAllowed was added to object type Repository

## Schema changes for 2021-09-09

### The GraphQL schema includes these changes:

* Type 'Base64String' was added
* Type CancelSponsorshipInput was added
* Type CancelSponsorshipPayload was added
* Type CommitMessage was added
* Type CommittableBranch was added
* Type CreateCommitOnBranchInput was added
* Type CreateCommitOnBranchPayload was added
* Type FileAddition was added
* Type FileChanges was added
* Type FileDeletion was added
* Field cancelSponsorship was added to object type Mutation
* Field createCommitOnBranch was added to object type Mutation
* Field sponsorsListing (deprecated) was removed from object type Query

## Schema changes for 2021-09-03

### The GraphQL schema includes these changes:

* Field sponsorshipForViewerAsSponsorable was added to object type Organization
* Field sponsorshipForViewerAsSponsorable was added to interface Sponsorable
* Field isSponsorOptedIntoEmail was added to object type Sponsorship
* Field sponsorshipForViewerAsSponsorable was added to object type User

## Schema changes for 2021-08-27

### The GraphQL schema includes these changes:

* DeploymentProtectionRule object type no longer implements Node interface
* Field id was removed from object type DeploymentProtectionRule
* Field isFollowingViewer was added to object type User

## Schema changes for 2021-08-25

### The GraphQL schema includes these changes:

* Field visibility was added to object type Repository
* Field visibility was added to interface RepositoryInfo

## Schema changes for 2021-08-24

### The GraphQL schema includes these changes:

* Input field amount was added to input object type CreateSponsorshipInput
* Input field isRecurring was added to input object type CreateSponsorshipInput
* Input field sponsorLogin was added to input object type CreateSponsorshipInput
* Input field sponsorableLogin was added to input object type CreateSponsorshipInput
* Input field CreateSponsorshipInput.sponsorId changed type from ID! to ID
* Input field CreateSponsorshipInput.sponsorableId changed type from ID! to ID
* Input field CreateSponsorshipInput.tierId changed type from ID! to ID

## Schema changes for 2021-08-19

### The GraphQL schema includes these changes:

* Type CreateSponsorshipInput was added
* Type CreateSponsorshipPayload was added
* Field createSponsorship was added to object type Mutation

## Schema changes for 2021-08-18

### The GraphQL schema includes these changes:

* Field estimatedNextSponsorsPayoutInCents was added to object type Organization
* Field monthlyEstimatedSponsorsIncomeInCents was added to object type Organization
* Enum value INTERNAL was added to enum OrganizationMembersCanCreateRepositoriesSettingValue
* Field estimatedNextSponsorsPayoutInCents was added to interface Sponsorable
* Field monthlyEstimatedSponsorsIncomeInCents was added to interface Sponsorable
* Field estimatedNextSponsorsPayoutInCents was added to object type User
* Field monthlyEstimatedSponsorsIncomeInCents was added to object type User

## Schema changes for 2021-08-13

### The GraphQL schema includes these changes:

* Enum value OTHER was removed from enum SecurityAdvisoryEcosystem

## Schema changes for 2021-08-12

### The GraphQL schema includes these changes:

* Type SponsorshipNewsletter was added
* Type SponsorshipNewsletterConnection was added
* Type SponsorshipNewsletterEdge was added
* Type SponsorshipNewsletterOrder was added
* Type SponsorshipNewsletterOrderField was added
* Field sponsorshipNewsletters was added to object type Organization
* Field sponsorshipNewsletters was added to interface Sponsorable
* Field sponsorshipNewsletters was added to object type User

## Schema changes for 2021-08-04

### The GraphQL schema includes these changes:

* Field sponsoring was added to object type Organization
* Field sponsoring was added to interface Sponsorable
* Field sponsoring was added to object type User

## Schema changes for 2021-08-03

### The GraphQL schema includes these changes:

* Field autoMergeAllowed was added to object type Repository

## Schema changes for 2021-08-01

### The GraphQL schema includes these changes:

* Type SponsorConnection was added
* Type SponsorEdge was added
* Type SponsorOrder was added
* Type SponsorOrderField was added
* Field sponsors was added to object type Organization
* Field sponsors was added to interface Sponsorable
* Field sponsors was added to object type User

## Schema changes for 2021-07-27

### The GraphQL schema includes these changes:

* Argument membersOnly: Boolean added to field EnterpriseIdentityProvider.externalIdentities
* Argument membersOnly: Boolean added to field OrganizationIdentityProvider.externalIdentities
* Field mentions was added to object type Release
* Field isPublic was added to object type SponsorsListing
* Field nextPayoutDate was added to object type SponsorsListing
* Field sponsorable was added to object type SponsorsListing

## Schema changes for 2021-07-13

### The GraphQL schema includes these changes:

* Type SponsorsActivity was added
* Type SponsorsActivityAction was added
* Type SponsorsActivityConnection was added
* Type SponsorsActivityEdge was added
* Type SponsorsActivityOrder was added
* Type SponsorsActivityOrderField was added
* Type SponsorsActivityPeriod was added
* Field sponsorsActivities was added to object type Organization
* Enum value OTHER was added to enum SecurityAdvisoryEcosystem
* Field sponsorsActivities was added to interface Sponsorable
* Field sponsorsActivities was added to object type User

## Schema changes for 2021-06-22

### The GraphQL schema includes these changes:

* Field ipAllowListEntries was added to object type App
* Member App was added to Union type IpAllowListOwner

### The [Access to a repositories dependency graph preview](/en/graphql/overview/schema-previews#access-to-a-repositories-dependency-graph-preview) includes these changes:

* Field packageLabel was added to object type DependencyGraphDependency

## Schema changes for 2021-06-20

### The GraphQL schema includes these changes:

* Type Reactor was added
* Type ReactorConnection was added
* Type ReactorEdge was added
* Field reactors was added to object type ReactionGroup

### The following changes will be made to the schema:

* On member ReactionGroup.users:users will be removed. Use the reactors field instead. Effective 2021-10-01.

## Schema changes for 2021-06-18

### The GraphQL schema includes these changes:

* Type IpAllowListForInstalledAppsEnabledSettingValue was added
* Type UpdateIpAllowListForInstalledAppsEnabledSettingInput was added
* Type UpdateIpAllowListForInstalledAppsEnabledSettingPayload was added
* Field requiresConversationResolution was added to object type BranchProtectionRule
* Input field requiresConversationResolution was added to input object type CreateBranchProtectionRuleInput
* Field ipAllowListForInstalledAppsEnabledSetting was added to object type EnterpriseOwnerInfo
* Field titleHTML was added to object type Issue
* Field updateIpAllowListForInstalledAppsEnabledSetting was added to object type Mutation
* Field ipAllowListForInstalledAppsEnabledSetting was added to object type Organization
* Field titleHTML was added to object type PullRequest
* Field requiresConversationResolution was added to object type RefUpdateRule
* Input field requiresConversationResolution was added to input object type UpdateBranchProtectionRuleInput

## Schema changes for 2021-06-07

### The GraphQL schema includes these changes:

* Type AddDiscussionCommentInput was added
* Type AddDiscussionCommentPayload was added
* Type AddUpvoteInput was added
* Type AddUpvotePayload was added
* Type ApproveDeploymentsInput was added
* Type ApproveDeploymentsPayload was added
* Type CheckStep was added
* Type CheckStepConnection was added
* Type CheckStepEdge was added
* Type CreateDiscussionInput was added
* Type CreateDiscussionPayload was added
* Type CreateEnvironmentInput was added
* Type CreateEnvironmentPayload was added
* Type DeleteDiscussionCommentInput was added
* Type DeleteDiscussionCommentPayload was added
* Type DeleteDiscussionInput was added
* Type DeleteDiscussionPayload was added
* Type DeleteEnvironmentInput was added
* Type DeleteEnvironmentPayload was added
* Type DeploymentProtectionRule was added
* Type DeploymentProtectionRuleConnection was added
* Type DeploymentProtectionRuleEdge was added
* Type DeploymentProtectionRuleType was added
* Type DeploymentRequest was added
* Type DeploymentRequestConnection was added
* Type DeploymentRequestEdge was added
* Type DeploymentReview was added
* Type DeploymentReviewConnection was added
* Type DeploymentReviewEdge was added
* Type DeploymentReviewState was added
* Type DeploymentReviewer was added
* Type DeploymentReviewerConnection was added
* Type DeploymentReviewerEdge was added
* Type Discussion was added
* Type DiscussionCategory was added
* Type DiscussionCategoryConnection was added
* Type DiscussionCategoryEdge was added
* Type DiscussionComment was added
* Type DiscussionCommentConnection was added
* Type DiscussionCommentEdge was added
* Type DiscussionConnection was added
* Type DiscussionEdge was added
* Type DiscussionOrder was added
* Type DiscussionOrderField was added
* Type Environment was added
* Type EnvironmentConnection was added
* Type EnvironmentEdge was added
* Type MarkDiscussionCommentAsAnswerInput was added
* Type MarkDiscussionCommentAsAnswerPayload was added
* Type PinnedDiscussion was added
* Type PinnedDiscussionConnection was added
* Type PinnedDiscussionEdge was added
* Type PinnedDiscussionGradient was added
* Type PinnedDiscussionPattern was added
* Type RejectDeploymentsInput was added
* Type RejectDeploymentsPayload was added
* Type RemoveUpvoteInput was added
* Type RemoveUpvotePayload was added
* Type RepositoryDiscussionAuthor was added
* Type RepositoryDiscussionCommentAuthor was added
* Type UnmarkDiscussionCommentAsAnswerInput was added
* Type UnmarkDiscussionCommentAsAnswerPayload was added
* Type UpdateDiscussionCommentInput was added
* Type UpdateDiscussionCommentPayload was added
* Type UpdateDiscussionInput was added
* Type UpdateDiscussionPayload was added
* Type UpdateEnvironmentInput was added
* Type UpdateEnvironmentPayload was added
* Type Votable was added
* Type Workflow was added
* Type WorkflowRun was added
* Field deployment was added to object type CheckRun
* Field pendingDeploymentRequest was added to object type CheckRun
* Field steps was added to object type CheckRun
* Enum value PENDING was added to enum CheckStatusState
* Field creator was added to object type CheckSuite
* Field workflowRun was added to object type CheckSuite
* Field addDiscussionComment was added to object type Mutation
* Field addUpvote was added to object type Mutation
* Field approveDeployments was added to object type Mutation
* Field createDiscussion was added to object type Mutation
* Field createEnvironment was added to object type Mutation
* Field deleteDiscussion was added to object type Mutation
* Field deleteDiscussionComment was added to object type Mutation
* Field deleteEnvironment was added to object type Mutation
* Field markDiscussionCommentAsAnswer was added to object type Mutation
* Field rejectDeployments was added to object type Mutation
* Field removeUpvote was added to object type Mutation
* Field unmarkDiscussionCommentAsAnswer was added to object type Mutation
* Field updateDiscussion was added to object type Mutation
* Field updateDiscussionComment was added to object type Mutation
* Field updateEnvironment was added to object type Mutation
* Organization object implements RepositoryDiscussionAuthor interface
* Organization object implements RepositoryDiscussionCommentAuthor interface
* Field repositoryDiscussionComments was added to object type Organization
* Field repositoryDiscussions was added to object type Organization
* Field closingIssuesReferences was added to object type PullRequest
* Release object implements Reactable interface
* Field databaseId was added to object type Release
* Field reactionGroups was added to object type Release
* Field reactions was added to object type Release
* Field viewerCanReact was added to object type Release
* Field discussion was added to object type Repository
* Field discussionCategories was added to object type Repository
* Field discussions was added to object type Repository
* Field environment was added to object type Repository
* Field environments was added to object type Repository
* Field pinnedDiscussions was added to object type Repository
* Enum value PENDING was added to enum RequestableCheckStatusState
* Member Discussion was added to Union type SearchResultItem
* Field discussionCount was added to object type SearchResultItemConnection
* Enum value DISCUSSION was added to enum SearchType
* Enum value GO was added to enum SecurityAdvisoryEcosystem
* Field totalRecurringMonthlyPriceInCents was added to object type SponsorshipConnection
* Field totalRecurringMonthlyPriceInDollars was added to object type SponsorshipConnection
* User object implements RepositoryDiscussionAuthor interface
* User object implements RepositoryDiscussionCommentAuthor interface
* Field repositoryDiscussionComments was added to object type User
* Field repositoryDiscussions was added to object type User

### The following changes will be made to the schema:

* On member PackageType.DOCKER:DOCKER will be removed. Effective 2021-06-21.

## Schema changes for 2021-05-16

### The GraphQL schema includes these changes:

* Argument isApproved: Boolean added to field Organization.domains
* Field canReceiveOrganizationEmailsWhenNotificationsRestricted was added to object type User
* Field isApproved was added to object type VerifiableDomain
* Argument isApproved: Boolean added to field EnterpriseOwnerInfo.domains

## Schema changes for 2021-05-12

### The GraphQL schema includes these changes:

* Field claimant was added to object type Mannequin

## Schema changes for 2021-05-04

### The GraphQL schema includes these changes:

* Type PullRequestTemplate was added
* Field pullRequestTemplates was added to object type Repository

## Schema changes for 2021-04-20

### The GraphQL schema includes these changes:

* Type ConvertPullRequestToDraftInput was added
* Type ConvertPullRequestToDraftPayload was added
* Field convertPullRequestToDraft was added to object type Mutation

## Schema changes for 2021-04-07

### The GraphQL schema includes these changes:

* Field tierSelectedAt was added to object type Sponsorship

## Schema changes for 2021-03-27

### The GraphQL schema includes these changes:

* Field closestLesserValueTier was added to object type SponsorsTier
* Field isCustomAmount was added to object type SponsorsTier
* Field isOneTimePayment was added to object type Sponsorship

## Schema changes for 2021-03-25

### The GraphQL schema includes these changes:

* Field isOneTime was added to object type SponsorsTier

## Schema changes for 2021-03-21

### The GraphQL schema includes these changes:

* Type RequirableByPullRequest was added
* Field viewerLatestReview was added to object type PullRequest
* Field viewerLatestReviewRequest was added to object type PullRequest
* CheckRun object implements RequirableByPullRequest interface
* Type for argument pullRequestId on field CheckRun.isRequired changed from ID! to ID
* Argument pullRequestNumber: Int added to field CheckRun.isRequired
* StatusContext object implements RequirableByPullRequest interface
* Type for argument pullRequestId on field StatusContext.isRequired changed from ID! to ID
* Argument pullRequestNumber: Int added to field StatusContext.isRequired

## Schema changes for 2021-03-19

### The GraphQL schema includes these changes:

* Field requiresCodeOwnerReviews was added to object type RefUpdateRule
* Field viewerAllowedToDismissReviews was added to object type RefUpdateRule

## Schema changes for 2021-03-18

### The GraphQL schema includes these changes:

* Field isRequired was added to object type CheckRun
* Field isRequired was added to object type StatusContext

## Schema changes for 2021-03-03

### The GraphQL schema includes these changes:

* Field isPinned was added to object type Issue
* Enum value 'CREATED\_ATwas added to enumVerifiableDomainOrderField'
* Field createdAt was added to object type VerifiableDomain
* Field updatedAt was added to object type VerifiableDomain

## Schema changes for 2021-03-02

### The GraphQL schema includes these changes:

* Field isGitHubStar was added to object type User
* Field tagCommit was added to object type Release

## Schema changes for 2021-02-25

### The GraphQL schema includes these changes:

* Type ApproveVerifiableDomainInput was added
* Type ApproveVerifiableDomainPayload was added
* Field approveVerifiableDomain was added to object type Mutation

## Schema changes for 2021-02-16

### The GraphQL schema includes these changes:

* Type CVSS was added
* Type CWEConnection was added
* Type CWEEdge was added
* Type CWE was added
* Type SponsorsGoal was added
* Type SponsorsGoalKind was added
* Field repository was added to object type Release
* Field cvss was added to object type SecurityAdvisory
* Field cwes was added to object type SecurityAdvisory
* Field activeGoal was added to object type SponsorsListing

## Schema changes for 2021-02-05

### The GraphQL schema includes these changes:

* Type AutoMergeRequest was added
* Type SponsorableOrder was added
* Type SponsorableOrderField was added
* Type SponsorableItemConnection was added
* Type SponsorableItemEdge was added
* Type SponsorableItem was added
* Type DisablePullRequestAutoMergeInput was added
* Type DisablePullRequestAutoMergePayload was added
* Type EnablePullRequestAutoMergeInput was added
* Type EnablePullRequestAutoMergePayload was added
* Field sponsorables was added to object type Query
* Field isSponsoredBy was added to object type Organization
* Field sponsorshipForViewerAsSponsor was added to object type Organization
* Field isSponsoredBy was added to object type User
* Field sponsorshipForViewerAsSponsor was added to object type User
* Field autoMergeRequest was added to object type PullRequest
* Field viewerCanDisableAutoMerge was added to object type PullRequest
* Field viewerCanEnableAutoMerge was added to object type PullRequest
* Field isSponsoredBy was added to interface Sponsorable
* Field sponsorshipForViewerAsSponsor was added to interface Sponsorable
* Field disablePullRequestAutoMerge was added to object type Mutation
* Field enablePullRequestAutoMerge was added to object type Mutation

## Schema changes for 2021-02-01

### The GraphQL schema includes these changes:

* Type NotificationRestrictionSettingValue was added
* Type UpdateNotificationRestrictionSettingInput was added
* Type UpdateNotificationRestrictionSettingPayload was added
* Field notificationDeliveryRestrictionEnabledSetting was added to object type Organization
* Field notificationsPermalink was added to object type SecurityAdvisory
* Field notificationDeliveryRestrictionEnabledSetting was added to object type EnterpriseOwnerInfo
* Field updateNotificationRestrictionSetting was added to object type Mutation

## Schema changes for 2021-01-19

### The GraphQL schema includes these changes:

* Type ContributionLevel was added
* Type VerifiableDomainOrder was added
* Type VerifiableDomainOrderField was added
* Type VerifiableDomainConnection was added
* Type VerifiableDomainEdge was added
* Type VerifiableDomain was added
* Type VerifiableDomainOwner was added
* Type AddVerifiableDomainInput was added
* Type AddVerifiableDomainPayload was added
* Type DeleteVerifiableDomainInput was added
* Type DeleteVerifiableDomainPayload was added
* Type RegenerateVerifiableDomainTokenInput was added
* Type RegenerateVerifiableDomainTokenPayload was added
* Type VerifyVerifiableDomainInput was added
* Type VerifyVerifiableDomainPayload was added
* Field domains was added to object type Organization
* Field isLatest was added to object type Release
* Field latestRelease was added to object type Repository
* Enum value WAITING was added to enum DeploymentStatusState
* Field contributionLevel was added to object type ContributionCalendarDay
* Field domains was added to object type EnterpriseOwnerInfo
* Field addVerifiableDomain was added to object type Mutation
* Field deleteVerifiableDomain was added to object type Mutation
* Field regenerateVerifiableDomainToken was added to object type Mutation
* Field verifyVerifiableDomain was added to object type Mutation

## Schema changes for 2021-01-12

### The GraphQL schema includes these changes:

* Type AutoMergeDisabledEvent was added
* Type AutoMergeEnabledEvent was added
* Type AutoRebaseEnabledEvent was added
* Type AutoSquashEnabledEvent was added
* Type AddEnterpriseSupportEntitlementInput was added
* Type AddEnterpriseSupportEntitlementPayload was added
* Type RemoveEnterpriseSupportEntitlementInput was added
* Type RemoveEnterpriseSupportEntitlementPayload was added
* Enum value WAITING was added to enum CheckStatusState
* Enum value 'AUTO\_MERGE\_DISABLED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'AUTO\_MERGE\_ENABLED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'AUTO\_REBASE\_ENABLED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Enum value 'AUTO\_SQUASH\_ENABLED\_EVENTwas added to enumPullRequestTimelineItemsItemType'
* Member AutoMergeDisabledEvent was added to Union type PullRequestTimelineItems
* Member AutoMergeEnabledEvent was added to Union type PullRequestTimelineItems
* Member AutoRebaseEnabledEvent was added to Union type PullRequestTimelineItems
* Member AutoSquashEnabledEvent was added to Union type PullRequestTimelineItems
* Field supportEntitlements was added to object type EnterpriseOwnerInfo
* Field addEnterpriseSupportEntitlement was added to object type Mutation
* Field removeEnterpriseSupportEntitlement was added to object type Mutation
* Enum value WAITING was added to enum RequestableCheckStatusState

## Schema changes for 2020-12-09

### The GraphQL schema includes these changes:

* Field hasVerifiedOwner was added to object type MarketplaceListing

## Schema changes for 2020-11-13

### The GraphQL schema includes these changes:

* Input field requiresLinearHistory was added to input object type UpdateBranchProtectionRuleInput
* Input field allowsForcePushes was added to input object type UpdateBranchProtectionRuleInput
* Input field allowsDeletions was added to input object type UpdateBranchProtectionRuleInput
* Input field requiresLinearHistory was added to input object type CreateBranchProtectionRuleInput
* Input field allowsForcePushes was added to input object type CreateBranchProtectionRuleInput
* Input field allowsDeletions was added to input object type CreateBranchProtectionRuleInput
* Field requiresLinearHistory was added to object type BranchProtectionRule
* Field allowsForcePushes was added to object type BranchProtectionRule
* Field allowsDeletions was added to object type BranchProtectionRule

## Schema changes for 2020-10-12

### The GraphQL schema includes these changes:

* Field updateEnterpriseActionExecutionCapabilitySetting was removed from object type Mutation
* Field actionExecutionCapabilitySettingOrganizations was removed from object type EnterpriseOwnerInfo
* Type UpdateEnterpriseActionExecutionCapabilitySettingInput was removed
* Type UpdateEnterpriseActionExecutionCapabilitySettingPayload was removed
* Type ActionExecutionCapabilitySetting was removed

## Schema changes for 2020-09-30

### The GraphQL schema includes these changes:

* Field issuePrioritiesDebug was removed from object type Milestone

## Schema changes for 2020-09-23

### The GraphQL schema includes these changes:

* Field Blob.isBinary changed type from Boolean! to Boolean
* Field Ref.target changed type from GitObject! to GitObject
* Union member BaseRefDeletedEvent was added to Union type PullRequestTimelineItem
* Enum value BASE\_REF\_DELETED\_EVENT was added to enum PullRequestTimelineItemsItemType
* Union member BaseRefDeletedEvent was added to Union type PullRequestTimelineItems
* Enum value PUBLIC\_PRIVATE was added to enum OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility
* Enum value PUBLIC\_INTERNAL was added to enum OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility
* Enum value PRIVATE\_INTERNAL was added to enum OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility
* Enum value PRIVATE was added to enum OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility
* Enum value NONE was added to enum OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility
* Enum value INTERNAL was added to enum OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility
* Enum value MANNEQUIN was added to enum CommentAuthorAssociation
* Field path was added to object type TreeEntry
* Field isGenerated was added to object type TreeEntry
* Field extension was added to object type TreeEntry
* Field used was added to object type RateLimit
* Field asCodeOwner was added to object type ReviewRequest
* Field viewerViewedState was added to object type PullRequestChangedFile
* Field unmarkFileAsViewed was added to object type Mutation
* Field markFileAsViewed was added to object type Mutation
* Input field authorEmail was added to input object type MergePullRequestInput
* Input field authorEmail was added to input object type MergeBranchInput
* Field isCrossRepository was added to object type UnmarkedAsDuplicateEvent
* Field duplicate was added to object type UnmarkedAsDuplicateEvent
* Field canonical was added to object type UnmarkedAsDuplicateEvent
* Field isCrossRepository was added to object type MarkedAsDuplicateEvent
* Field duplicate was added to object type MarkedAsDuplicateEvent
* Field canonical was added to object type MarkedAsDuplicateEvent
* Field groups was added to object type ExternalIdentityScimAttributes
* Field givenName was added to object type ExternalIdentityScimAttributes
* Field familyName was added to object type ExternalIdentityScimAttributes
* Field emails was added to object type ExternalIdentityScimAttributes
* Field username was added to object type ExternalIdentitySamlAttributes
* Field groups was added to object type ExternalIdentitySamlAttributes
* Field givenName was added to object type ExternalIdentitySamlAttributes
* Field familyName was added to object type ExternalIdentitySamlAttributes
* Field emails was added to object type ExternalIdentitySamlAttributes
* Field isInOrganization was added to object type RepositoryInfo
* Field permalink was added to object type RepositoryInvitation
* Input field issueTemplate was added to input object type CreateIssueInput
* Field combinedContexts was added to object type Status
* Field deletedCommentAuthor was added to object type CommentDeletedEvent
* Field pullRequest was added to object type BaseRefChangedEvent
* Field previousRefName was added to object type BaseRefChangedEvent
* Field currentRefName was added to object type BaseRefChangedEvent
* Field stargazerCount was added to object type Gist
* Field refUpdateRule was added to object type Ref
* Field branchProtectionRule was added to object type Ref
* Argument query: String added to field Repository.milestones
* Field viewerPossibleCommitEmails was added to object type Repository
* Field viewerDefaultMergeMethod was added to object type Repository
* Field viewerDefaultCommitEmail was added to object type Repository
* Field securityPolicyUrl was added to object type Repository
* Field issueTemplates was added to object type Repository
* Field isUserConfigurationRepository was added to object type Repository
* Field isSecurityPolicyEnabled was added to object type Repository
* Field isEmpty was added to object type Repository
* Field isBlankIssuesEnabled was added to object type Repository
* Field contactLinks was added to object type Repository
* Field stargazerCount was added to object type Repository
* Field isInOrganization was added to object type Repository
* Field viewerCanReply was added to object type PullRequestReviewThread
* Field path was added to object type PullRequestReviewThread
* Field isOutdated was added to object type PullRequestReviewThread
* Field isCollapsed was added to object type PullRequestReviewThread
* Input field AddPullRequestReviewThreadInput.pullRequestReviewId changed type from ID! to ID
* Input field pullRequestId was added to input object type AddPullRequestReviewThreadInput
* Field authorCanPushToRepository was added to object type PullRequestReview
* Field progressPercentage was added to object type Milestone
* Enum value MergeStateStatus.DRAFT was deprecated with reason DRAFT state will be removed from this enum and isDraft should be used instead Use PullRequest.isDraft instead. Removal on 2021-01-01 UTC.
* Field viewerMergeHeadlineText was added to object type PullRequest
* Field viewerMergeBodyText was added to object type PullRequest
* Field viewerCanDeleteHeadRef was added to object type PullRequest
* Field latestReviews was added to object type PullRequest
* Field latestOpinionatedReviews was added to object type PullRequest
* Field isReadByViewer was added to object type PullRequest
* Field progress was added to object type Project
* Field file was added to object type Commit
* Field authors was added to object type Commit
* Field isReadByViewer was added to object type Issue
* Field bodyUrl was added to object type Issue
* Field bodyResourcePath was added to object type Issue
* Field stargazerCount was added to object type Starrable
* Field stargazerCount was added to object type Topic
* Type RepositoryContactLink was added
* Type RefUpdateRule was added
* Type ProjectProgress was added
* Type UnmarkFileAsViewedInput was added
* Type UnmarkFileAsViewedPayload was added
* Type MarkFileAsViewedPayload was added
* Type MarkFileAsViewedInput was added
* Type GitActorEdge was added
* Type FileViewedState was added
* Type UserEmailMetadata was added
* Type GitActorConnection was added
* Type BaseRefDeletedEvent was added
* Type IssueTemplate was added

### The following changes will be made to the schema:

* On member EnterprisePendingMemberInvitationEdge.isUnlicensed: isUnlicensed will be removed. Effective 2020-07-01.
* On member EnterpriseMemberEdge.isUnlicensed: isUnlicensed will be removed. Effective 2021-01-01.
* On member EnterpriseOutsideCollaboratorEdge.isUnlicensed: isUnlicensed will be removed. Effective 2021-01-01.
* On member EnterprisePendingCollaboratorEdge.isUnlicensed: isUnlicensed will be removed. Effective 2021-01-01.
* On member MergeStateStatus.DRAFT: DRAFT will be removed. Use PullRequest.isDraft instead. Effective 2021-01-01.

## Schema changes for 2020-06-26

### The GraphQL schema includes these changes:

* Type TopicEdge was removed
* Type RegistryPackageVersionEdge was removed
* Type RegistryPackageVersionStatistics was removed
* Type RegistryPackageTagEdge was removed
* Type RegistryPackageFileEdge was removed
* Type RegistryPackageDependencyEdge was removed
* Type RegistryPackageMetadatum was removed
* Type TopicConnection was removed
* Type RegistryPackageTag was removed
* Type RegistryPackageTagConnection was removed
* Type RegistryPackageStatistics was removed
* Type RegistryPackageVersionConnection was removed
* Type RegistryPackageType was removed
* Type RegistryPackage was removed
* Type RegistryPackageFileConnection was removed
* Type RegistryPackageFile was removed
* Type RegistryPackageDependencyType was removed
* Type RegistryPackageDependency was removed
* Type RegistryPackageDependencyConnection was removed
* Type RegistryPackageVersion was removed

## Schema changes for 2020-06-23

### The GraphQL schema includes these changes:

* Argument packageType: PackageType added to field Organization.packages
* Argument packageType: PackageType added to field User.packages
* Argument packageType: PackageType added to field PackageOwner.packages
* Argument packageType: PackageType added to field Repository.packages

## Schema changes for 2020-06-18

### The GraphQL schema includes these changes:

* Field databaseId was added to object type Team

## Schema changes for 2020-06-05

### The GraphQL schema includes these changes:

* Enum value TWO\_FACTOR\_ACCOUNT\_RECOVERY was added to enum OrgRemoveMemberAuditEntryReason

## Schema changes for 2020-06-01

### The GraphQL schema includes these changes:

* Field twitterUsername was added to object type Organization
* Field twitterUsername was added to object type User

### The following changes will be made to the schema:

* On member Blob.isBinary: Type for isBinary will change from Boolean! to Boolean. Effective 2019-07-01.
* On member Ref.target: Type for target will change from GitObject! to GitObject. Effective 2019-07-01.

## Schema changes for 2020-05-23

### The GraphQL schema includes these changes:

* Field ipAllowListEntries was added to object type Organization
* Field ipAllowListEnabledSetting was added to object type Organization

## Schema changes for 2020-05-21

### The GraphQL schema includes these changes:

* Enum value AUTOMATIC\_BASE\_CHANGE\_SUCCEEDED\_EVENT was added to enum PullRequestTimelineItemsItemType
* Enum value AUTOMATIC\_BASE\_CHANGE\_FAILED\_EVENT was added to enum PullRequestTimelineItemsItemType
* Union member AutomaticBaseChangeSucceededEvent was added to Union type PullRequestTimelineItems
* Union member AutomaticBaseChangeFailedEvent was added to Union type PullRequestTimelineItems
* Type AutomaticBaseChangeSucceededEvent was added
* Type AutomaticBaseChangeFailedEvent was added

### The following changes will be made to the schema:

* On member RepositoryCollaboratorEdge.permission: Type for permission will change from RepositoryPermission! to String. Effective 2020-10-01.
* On member RepositoryInvitation.permission: Type for permission will change from RepositoryPermission! to String. Effective 2020-10-01.
* On member TeamRepositoryEdge.permission: Type for permission will change from RepositoryPermission! to String. Effective 2020-10-01.

## Schema changes for 2020-05-19

### The GraphQL schema includes these changes:

* Field RepositoryInvitation.invitee changed type from User! to User
* Default value for argument orderBy on field EnterpriseOwnerInfo.pendingCollaborators changed from {"field"=>"INVITEE\_LOGIN", "direction"=>"ASC"} to {"field"=>"CREATED\_AT", "direction"=>"DESC"}
* Enum value RepositoryInvitationOrderField.INVITEE\_LOGIN was deprecated with reason `INVITEE_LOGIN is no longer a valid field value. Repository invitations can now be associated with an email, not only an invitee. Removal on 2020-10-01 UTC.`
* Field email was added to object type RepositoryInvitation
* Field pendingCollaboratorInvitations was added to object type EnterpriseOwnerInfo
* Type RepositoryInvitationEdge was added
* Type RepositoryInvitationConnection was added

### The following changes will be made to the schema:

* On member EnterpriseOwnerInfo.pendingCollaborators: pendingCollaborators will be removed. Use the pendingCollaboratorInvitations field instead. Effective 2020-10-01.
* On member RepositoryInvitationOrderField.INVITEE\_LOGIN: INVITEE\_LOGIN will be removed. Effective 2020-10-01.

## Schema changes for 2020-05-13

### The GraphQL schema includes these changes:

* Field packageName was removed from object type RepositoryVulnerabilityAlert
* Field fixedIn was removed from object type RepositoryVulnerabilityAlert
* Field externalReference was removed from object type RepositoryVulnerabilityAlert
* Field externalIdentifier was removed from object type RepositoryVulnerabilityAlert
* Field affectedRange was removed from object type RepositoryVulnerabilityAlert
* Field isDelisted was removed from object type MarketplaceListing
* Field isApproved was removed from object type MarketplaceListing
* Field hasApprovalBeenRequested was removed from object type MarketplaceListing
* Field pinnedRepositories was removed from object type RepositoryOwner
* Input field field was removed from input object type ContributionOrder
* Field pinnedRepositories was removed from object type Organization
* Field pinnedRepositories was removed from object type User
* Type ContributionOrderField was removed
* Default value for argument orderBy on field PullRequestReviewContributionsByRepository.contributions changed from {"field"=>"OCCURRED\_AT", "direction"=>"DESC"} to {"direction"=>"DESC"}
* Default value for argument orderBy on field PullRequestContributionsByRepository.contributions changed from {"field"=>"OCCURRED\_AT", "direction"=>"DESC"} to {"direction"=>"DESC"}
* Default value for argument orderBy on field IssueContributionsByRepository.contributions changed from {"field"=>"OCCURRED\_AT", "direction"=>"DESC"} to {"direction"=>"DESC"}
* Default value for argument orderBy on field ContributionsCollection.repositoryContributions changed from {"field"=>"OCCURRED\_AT", "direction"=>"DESC"} to {"direction"=>"DESC"}
* Default value for argument orderBy on field ContributionsCollection.pullRequestReviewContributions changed from {"field"=>"OCCURRED\_AT", "direction"=>"DESC"} to {"direction"=>"DESC"}
* Default value for argument orderBy on field ContributionsCollection.pullRequestContributions changed from {"field"=>"OCCURRED\_AT", "direction"=>"DESC"} to {"direction"=>"DESC"}
* Default value for argument orderBy on field ContributionsCollection.issueContributions changed from {"field"=>"OCCURRED\_AT", "direction"=>"DESC"} to {"direction"=>"DESC"}

## Schema changes for 2020-05-12

### The GraphQL schema includes these changes:

* Field organizationVerifiedDomainEmails was added to object type User

## Schema changes for 2020-05-11

### The GraphQL schema includes these changes:

* Field sponsorEntity was added to object type Sponsorship
* Type Sponsor was added

### The following changes will be made to the schema:

* On member Sponsorship.sponsor: sponsor will be removed. Use Sponsorship.sponsorEntity instead. Effective 2020-10-01.

## Schema changes for 2020-05-01

### The GraphQL schema includes these changes:

* Input field includeAllBranches was added to input object type CloneTemplateRepositoryInput

## Schema changes for 2020-04-23

### The following changes will be made to the schema:

* On member Issue.timeline: timeline will be removed. Use Issue.timelineItems instead. Effective 2020-10-01.
* On member PullRequest.timeline: timeline will be removed. Use PullRequest.timelineItems instead. Effective 2020-10-01.

## Schema changes for 2020-04-20

### The GraphQL schema includes these changes:

* Enum value USER\_ACCOUNT\_DELETED was added to enum OrgRemoveMemberAuditEntryReason

## Schema changes for 2020-04-15

### The GraphQL schema includes these changes:

* Enum value CONVERT\_TO\_DRAFT\_EVENT was added to enum PullRequestTimelineItemsItemType
* Union member ConvertToDraftEvent was added to Union type PullRequestTimelineItems
* Field DeploymentStatus.creator changed type from Actor to Actor!
* Field isOverLimit was added to object type StarredRepositoryConnection
* Field Deployment.creator changed type from Actor to Actor!
* Field onBehalfOf was added to object type Commit
* Type ConvertToDraftEvent was added

## Schema changes for 2020-03-23

### The GraphQL schema includes these changes:

* Type IssueOrPullRequestEdge was removed
* Default value for argument affiliations on field RepositoryOwner.repositories changed from \["OWNER", "COLLABORATOR"] to **no\_default**
* Default value for argument affiliations on field RepositoryOwner.pinnedRepositories changed from \["OWNER", "COLLABORATOR"] to **no\_default**
* Default value for argument affiliations on field Organization.repositories changed from \["OWNER", "COLLABORATOR"] to \`\`
* Default value for argument affiliations on field Organization.pinnedRepositories changed from \["OWNER", "COLLABORATOR"] to \`\`
* Default value for argument affiliations on field User.watching changed from \["OWNER", "COLLABORATOR", "ORGANIZATION\_MEMBER"] to \`\`
* Default value for argument affiliations on field User.repositories changed from \["OWNER", "COLLABORATOR"] to \`\`
* Default value for argument affiliations on field User.pinnedRepositories changed from \["OWNER", "COLLABORATOR"] to \`\`
* Default value for argument affiliations on field Repository.forks changed from \["OWNER", "COLLABORATOR"] to \`\`
* Field submodule was added to object type TreeEntry
* Field reviewDecision was added to object type ReviewStatusHovercardContext
* Field permalink was added to object type SecurityAdvisory
* Field updateIpAllowListEntry was added to object type Mutation
* Field updateIpAllowListEnabledSetting was added to object type Mutation
* Field setEnterpriseIdentityProvider was added to object type Mutation
* Field removeEnterpriseIdentityProvider was added to object type Mutation
* Field deleteIpAllowListEntry was added to object type Mutation
* Field createIpAllowListEntry was added to object type Mutation
* Field ipAllowListEntries was added to object type EnterpriseOwnerInfo
* Field ipAllowListEnabledSetting was added to object type EnterpriseOwnerInfo
* Field submodules was added to object type Repository
* Field reviewDecision was added to object type PullRequest
* Field submodules was added to object type Commit
* Field slug was added to object type Enterprise
* Type SubmoduleEdge was added
* Type PullRequestReviewDecision was added
* Type UpdateIpAllowListEntryInput was added
* Type UpdateIpAllowListEntryPayload was added
* Type UpdateIpAllowListEnabledSettingInput was added
* Type UpdateIpAllowListEnabledSettingPayload was added
* Type SetEnterpriseIdentityProviderInput was added
* Type SetEnterpriseIdentityProviderPayload was added
* Type RemoveEnterpriseIdentityProviderInput was added
* Type RemoveEnterpriseIdentityProviderPayload was added
* Type IpAllowListEntryOrderField was added
* Type IpAllowListEntryEdge was added
* Type IpAllowListOwner was added
* Type IpAllowListEntryOrder was added
* Type IpAllowListEntryConnection was added
* Type IpAllowListEnabledSettingValue was added
* Type DeleteIpAllowListEntryPayload was added
* Type DeleteIpAllowListEntryInput was added
* Type CreateIpAllowListEntryPayload was added
* Type IpAllowListEntry was added
* Type CreateIpAllowListEntryInput was added
* Type Submodule was added
* Type SubmoduleConnection was added

## Schema changes for 2020-03-10

### The GraphQL schema includes these changes:

* Type MentionableItemEdge was removed
* Type MentionableItem was removed
* Field statusCheckRollup was added to object type Commit
* Type StatusCheckRollupContext was added
* Type StatusCheckRollupContextEdge was added
* Type StatusCheckRollupContextConnection was added
* Type StatusCheckRollup was added

## Schema changes for 2020-03-05

### The GraphQL schema includes these changes:

* Field actor was added to object type RequestReviewsPayload
* Type MentionableItemEdge was added
* Type MentionableItem was added

## Schema changes for 2020-02-19

### The GraphQL schema includes these changes:

* Type PackageType was added

### The GitHub Packages preview includes these changes:

* Field packageType was added to object type Package

## Schema changes for 2020-02-12

### The GraphQL schema includes these changes:

* Field deleteDeployment was added to object type Mutation
* Type DeleteDeploymentInput was added
* Type DeleteDeploymentPayload was added

## Schema changes for 2020-02-05

### The GraphQL schema includes these changes:

* Type EnterpriseOrderField was removed
* Type CollectionItemContent was removed
* Enum value UNMARKED\_AS\_DUPLICATE\_EVENT was added to enum PullRequestTimelineItemsItemType
* Enum value DISCONNECTED\_EVENT was added to enum PullRequestTimelineItemsItemType
* Enum value CONNECTED\_EVENT was added to enum PullRequestTimelineItemsItemType
* Union member UnmarkedAsDuplicateEvent was added to Union type PullRequestTimelineItems
* Union member DisconnectedEvent was added to Union type PullRequestTimelineItems
* Union member ConnectedEvent was added to Union type PullRequestTimelineItems
* Enum value UNMARKED\_AS\_DUPLICATE\_EVENT was added to enum IssueTimelineItemsItemType
* Enum value DISCONNECTED\_EVENT was added to enum IssueTimelineItemsItemType
* Enum value CONNECTED\_EVENT was added to enum IssueTimelineItemsItemType
* Union member UnmarkedAsDuplicateEvent was added to Union type IssueTimelineItems
* Union member DisconnectedEvent was added to Union type IssueTimelineItems
* Union member ConnectedEvent was added to Union type IssueTimelineItems
* Input field SubmitPullRequestReviewInput.pullRequestReviewId changed type from ID! to ID
* Input field pullRequestId was added to input object type SubmitPullRequestReviewInput
* Input field AddPullRequestReviewCommentInput.pullRequestReviewId changed type from ID! to ID
* Input field pullRequestId was added to input object type AddPullRequestReviewCommentInput
* Field originalEnvironment was added to object type Deployment
* Field latestEnvironment was added to object type Deployment
* Field checksUrl was added to object type PullRequest
* Field checksResourcePath was added to object type PullRequest
* Type UnmarkedAsDuplicateEvent was added
* Type DisconnectedEvent was added
* Type ConnectedEvent was added

### The [Checks preview](/en/graphql/overview/schema-previews#checks-preview) includes these changes:

* Enum value STALE was added to enum CheckConclusionState
* Enum value SKIPPED was added to enum CheckConclusionState

## Schema changes for 2020-01-09

### The GraphQL schema includes these changes:

* Enum value DUPLICATE was added to enum ReportedContentClassifiers
* Field deleteBranchOnMerge was added to object type Repository

## Schema changes for 2020-01-06

### The GraphQL schema includes these changes:

* Field sponsorable was added to object type Sponsorship

### The following changes will be made to the schema:

* On member Sponsorship.maintainer: maintainer will be removed. Use Sponsorship.sponsorable instead. Effective 2020-04-01.

## Schema changes for 2019-12-16

### The GraphQL schema includes these changes:

* Field actor was added to object type UpdatePullRequestPayload
* Field actor was added to object type UpdateIssuePayload
* Field actor was added to object type UnlockLockablePayload
* Field actor was added to object type MergePullRequestPayload
* Field actor was added to object type LockLockablePayload
* Argument orderBy: LabelOrder added to field Repository.labels
* Argument orderBy: LabelOrder added to field Issue.labels
* Argument orderBy: LabelOrder added to field Labelable.labels
* Argument orderBy: LabelOrder added to field PullRequest.labels
* Type LabelOrderField was added
* Type LabelOrder was added

## Schema changes for 2019-12-11

### The GraphQL schema includes these changes:

* Field createdAt was added to object type RepositoryVulnerabilityAlert

## Schema changes for 2019-12-05

### The GraphQL schema includes these changes:

* Field createdAt was added to object type SponsorsListing

## Schema changes for 2019-11-25

### The GitHub Packages preview includes these changes:

* Field statistics was added to object type PackageVersion
* Field statistics was added to object type Package
* Type PackageStatistics was added
* Type PackageVersionStatistics was added

### The following changes will be made to the schema:

* On member Organization.registryPackages: registryPackages will be removed. Use the PackageOwner object instead. Effective 2020-04-01.
* On member Organization.registryPackagesForQuery: registryPackagesForQuery will be removed. Use the PackageSearch object instead. Effective 2020-04-01.
* On member RegistryPackage.color: color will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.latestVersion: latestVersion will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.name: name will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.nameWithOwner: nameWithOwner will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.packageFileByGuid: packageFileByGuid will be removed. Use the Package object. Effective 2020-04-01.
* On member RegistryPackage.packageFileBySha256: packageFileBySha256 will be removed. Use the Package object. Effective 2020-04-01.
* On member RegistryPackage.packageType: packageType will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.preReleaseVersions: preReleaseVersions will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.registryPackageType: registryPackageType will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.repository: repository will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.statistics: statistics will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.tags: tags will be removed. Use the Package object. Effective 2020-04-01.
* On member RegistryPackage.topics: topics will be removed. Use the Package object. Effective 2020-04-01.
* On member RegistryPackage.version: version will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.versionByPlatform: versionByPlatform will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.versionBySha256: versionBySha256 will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.versions: versions will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackage.versionsByMetadatum: versionsByMetadatum will be removed. Use the Package object instead. Effective 2020-04-01.
* On member RegistryPackageDependency.dependencyType: dependencyType will be removed. Use the PackageDependency object instead. Effective 2020-04-01.
* On member RegistryPackageDependency.name: name will be removed. Use the PackageDependency object instead. Effective 2020-04-01.
* On member RegistryPackageDependency.version: version will be removed. Use the PackageDependency object instead. Effective 2020-04-01.
* On member RegistryPackageFile.guid: guid will be removed. Use the PackageFile object instead. Effective 2020-04-01.
* On member RegistryPackageFile.md5: md5 will be removed. Use the PackageFile object instead. Effective 2020-04-01.
* On member RegistryPackageFile.metadataUrl: metadataUrl will be removed. Use the PackageFile object instead. Effective 2020-04-01.
* On member RegistryPackageFile.name: name will be removed. Use the PackageFile object instead. Effective 2020-04-01.
* On member RegistryPackageFile.packageVersion: packageVersion will be removed. Use the PackageFile object instead. Effective 2020-04-01.
* On member RegistryPackageFile.sha1: sha1 will be removed. Use the PackageFile object instead. Effective 2020-04-01.
* On member RegistryPackageFile.sha256: sha256 will be removed. Use the PackageFile object instead. Effective 2020-04-01.
* On member RegistryPackageFile.size: size will be removed. Use the PackageFile object instead. Effective 2020-04-01.
* On member RegistryPackageFile.url: url will be removed. Use the PackageFile object instead. Effective 2020-04-01.
* On member RegistryPackageOwner.registryPackages: registryPackages will be removed. Use the PackageOwner object instead. Effective 2020-04-01.
* On member RegistryPackageSearch.registryPackagesForQuery: registryPackagesForQuery will be removed. Use the PackageSearch object instead. Effective 2020-04-01.
* On member RegistryPackageStatistics.downloadsThisMonth: downloadsThisMonth will be removed. Use the PackageStatistics object instead. Effective 2020-04-01.
* On member RegistryPackageStatistics.downloadsThisWeek: downloadsThisWeek will be removed. Use the PackageStatistics object instead. Effective 2020-04-01.
* On member RegistryPackageStatistics.downloadsThisYear: downloadsThisYear will be removed. Use the PackageStatistics object instead. Effective 2020-04-01.
* On member RegistryPackageStatistics.downloadsToday: downloadsToday will be removed. Use the PackageStatistics object instead. Effective 2020-04-01.
* On member RegistryPackageStatistics.downloadsTotalCount: downloadsTotalCount will be removed. Use the PackageStatistics object instead. Effective 2020-04-01.
* On member RegistryPackageTag.name: name will be removed. Use the PackageTag object instead. Effective 2020-04-01.
* On member RegistryPackageTag.version: version will be removed. Use the PackageTag object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.deleted: deleted will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.dependencies: dependencies will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.fileByName: fileByName will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.files: files will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.installationCommand: installationCommand will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.manifest: manifest will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.platform: platform will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.preRelease: preRelease will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.readme: readme will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.readmeHtml: readmeHtml will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.registryPackage: registryPackage will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.release: release will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.sha256: sha256 will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.size: size will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.statistics: statistics will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.summary: summary will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.updatedAt: updatedAt will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.version: version will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersion.viewerCanEdit: viewerCanEdit will be removed. Use the PackageVersion object instead. Effective 2020-04-01.
* On member RegistryPackageVersionStatistics.downloadsThisMonth: downloadsThisMonth will be removed. Use the PackageVersionStatistics object instead. Effective 2020-04-01.
* On member RegistryPackageVersionStatistics.downloadsThisWeek: downloadsThisWeek will be removed. Use the PackageVersionStatistics object instead. Effective 2020-04-01.
* On member RegistryPackageVersionStatistics.downloadsThisYear: downloadsThisYear will be removed. Use the PackageVersionStatistics object instead. Effective 2020-04-01.
* On member RegistryPackageVersionStatistics.downloadsToday: downloadsToday will be removed. Use the PackageVersionStatistics object instead. Effective 2020-04-01.
* On member RegistryPackageVersionStatistics.downloadsTotalCount: downloadsTotalCount will be removed. Use the PackageVersionStatistics object instead. Effective 2020-04-01.
* On member Repository.registryPackages: registryPackages will be removed. Use the PackageOwner object instead. Effective 2020-04-01.
* On member Repository.registryPackagesForQuery: registryPackagesForQuery will be removed. Use the PackageSearch object instead. Effective 2020-04-01.
* On member User.registryPackages: registryPackages will be removed. Use the PackageOwner object instead. Effective 2020-04-01.
* On member User.registryPackagesForQuery: registryPackagesForQuery will be removed. Use the PackageSearch object instead. Effective 2020-04-01.

## Schema changes for 2019-11-22

### The GraphQL schema includes these changes:

* Field unarchiveRepository was added to object type Mutation
* Field archiveRepository was added to object type Mutation
* Field fundingLinks was added to object type Repository
* Type UpdateTeamReviewAssignmentPayload was added
* Type UnarchiveRepositoryInput was added
* Type UnarchiveRepositoryPayload was added
* Type ArchiveRepositoryInput was added
* Type ArchiveRepositoryPayload was added
* Type FundingPlatform was added
* Type FundingLink was added

### The [Team Review Assignments Preview preview](/en/graphql/overview/schema-previews#team-review-assignments-preview) includes these changes:

* Field updateTeamReviewAssignment was added to object type Mutation
* Field reviewRequestDelegationNotifyTeam was added to object type Team
* Field reviewRequestDelegationMemberCount was added to object type Team
* Field reviewRequestDelegationEnabled was added to object type Team
* Field reviewRequestDelegationAlgorithm was added to object type Team
* Type UpdateTeamReviewAssignmentInput was added
* Type TeamReviewAssignmentAlgorithm was added

## Schema changes for 2019-11-19

### The GraphQL schema includes these changes:

* Field hasProjectsEnabled was added to object type RepositoryInfo
* Field hasProjectsEnabled was added to object type Repository

## Schema changes for 2019-11-06

### The [Update refs preview](/en/graphql/overview/schema-previews#update-refs-preview) includes these changes:

* Field updateRefs was added to object type Mutation
* Type GitRefname was added
* Type RefUpdate was added
* Type UpdateRefsInput was added
* Type UpdateRefsPayload was added

## Schema changes for 2019-10-31

### The GraphQL schema includes these changes:

* Input field field was added to input object type SponsorshipOrder
* Repository object implements PackageOwner interface
* User object implements PackageOwner interface
* Organization object implements PackageOwner interface
* Field tiers was added to object type SponsorsListing
* Field adminInfo was added to object type SponsorsTier
* Field sponsorsListing was added to object type Sponsorable
* Field sponsorsListing was added to object type User
* Field sponsorsListing was added to object type Organization
* Type SponsorsTierOrderField was added
* Type SponsorsTierOrder was added
* Type SponsorshipOrderField was added
* Type SponsorsTierAdminInfo was added
* Type SponsorsTierConnection was added
* Type PackageVersionEdge was added
* Type PackageVersionConnection was added
* Type PackageFileEdge was added
* Type PackageFileConnection was added
* Type PackageEdge was added
* Type PackageConnection was added

### The GitHub Packages preview includes these changes:

* Field packages was added to object type Repository
* Field packages was added to object type User
* Field packages was added to object type Organization
* Type PackageTag was added
* Type PackageVersionOrderField was added
* Type PackageVersionOrder was added
* Type PackageOrderField was added
* Type PackageOrder was added
* Type PackageFileOrderField was added
* Type PackageFileOrder was added
* Type PackageFile was added
* Type PackageVersion was added
* Type Package was added
* Type PackageOwner was added

### The following changes will be made to the schema:

* On member Query.sponsorsListing: sponsorsListing will be removed. Use Sponsorable.sponsorsListing instead. Effective 2020-04-01.

## Schema changes for 2019-10-23

### The GraphQL schema includes these changes:

* Field tier was added to object type Sponsorship
* Type SponsorsTierEdge was added
* Type SponsorsTier was added

## Schema changes for 2019-10-09

### The GraphQL schema includes these changes:

* Argument query: String added to field Repository.mentionableUsers

## Schema changes for 2019-09-24

### The GraphQL schema includes these changes:

* Field unfollowUser was added to object type Mutation
* Type UnfollowUserInput was added
* Type UnfollowUserPayload was added

## Schema changes for 2019-09-20

### The GraphQL schema includes these changes:

* Organization object implements Sponsorable interface
* Field followUser was added to object type Mutation
* Field sponsorshipsAsSponsor was added to object type Organization
* Field sponsorshipsAsMaintainer was added to object type Organization
* Type FollowUserInput was added
* Type FollowUserPayload was added

## Schema changes for 2019-09-19

### The GraphQL schema includes these changes:

* Union member OrgCreateAuditEntry was added to Union type OrganizationAuditEntry
* Enum value COMPOSER was added to enum SecurityAdvisoryEcosystem
* Field email was added to object type Mannequin
* Type OrgCreateAuditEntryBillingPlan was added
* Type OrgCreateAuditEntry was added

## Schema changes for 2019-09-17

### The GraphQL schema includes these changes:

* Repository object implements RegistryPackageSearch interface
* Field registryPackagesForQuery was added to object type Repository

## Schema changes for 2019-09-14

### The GraphQL schema includes these changes:

* Argument query: String added to field Repository.assignableUsers

## Schema changes for 2019-09-12

### The GraphQL schema includes these changes:

* Argument query: String added to field Repository.collaborators

## Schema changes for 2019-09-10

### The GraphQL schema includes these changes:

* Field updatedAt was added to object type Organization
* Field createdAt was added to object type Organization

## Schema changes for 2019-09-08

### The GraphQL schema includes these changes:

* Argument skip: Int added to field PullRequestReviewThread.comments

## Schema changes for 2019-09-05

### The GraphQL schema includes these changes:

* Input field mergeMethod was added to input object type MergePullRequestInput
* Field operationType was added to object type TeamRemoveRepositoryAuditEntry
* Field operationType was added to object type TeamRemoveMemberAuditEntry
* Field operationType was added to object type TeamChangeParentTeamAuditEntry
* Field operationType was added to object type TeamAddRepositoryAuditEntry
* Field operationType was added to object type TeamAddMemberAuditEntry
* Field operationType was added to object type RepositoryVisibilityChangeEnableAuditEntry
* Field operationType was added to object type RepositoryVisibilityChangeDisableAuditEntry
* Field operationType was added to object type RepoRemoveTopicAuditEntry
* Field operationType was added to object type RepoRemoveMemberAuditEntry
* Field operationType was added to object type RepoDestroyAuditEntry
* Field operationType was added to object type RepoCreateAuditEntry
* Field operationType was added to object type RepoConfigUnlockAnonymousGitAccessAuditEntry
* Field operationType was added to object type RepoConfigLockAnonymousGitAccessAuditEntry
* Field operationType was added to object type RepoConfigEnableSockpuppetDisallowedAuditEntry
* Field operationType was added to object type RepoConfigEnableContributorsOnlyAuditEntry
* Field operationType was added to object type RepoConfigEnableCollaboratorsOnlyAuditEntry
* Field operationType was added to object type RepoConfigEnableAnonymousGitAccessAuditEntry
* Field operationType was added to object type RepoConfigDisableSockpuppetDisallowedAuditEntry
* Field operationType was added to object type RepoConfigDisableContributorsOnlyAuditEntry
* Field operationType was added to object type RepoConfigDisableCollaboratorsOnlyAuditEntry
* Field operationType was added to object type RepoConfigDisableAnonymousGitAccessAuditEntry
* Field operationType was added to object type RepoChangeMergeSettingAuditEntry
* Field operationType was added to object type RepoArchivedAuditEntry
* Field operationType was added to object type RepoAddTopicAuditEntry
* Field operationType was added to object type RepoAddMemberAuditEntry
* Field operationType was added to object type RepoAccessAuditEntry
* Field operationType was added to object type PrivateRepositoryForkingEnableAuditEntry
* Field operationType was added to object type PrivateRepositoryForkingDisableAuditEntry
* Field operationType was added to object type OrgUpdateMemberRepositoryInvitationPermissionAuditEntry
* Field operationType was added to object type OrgUpdateMemberRepositoryCreationPermissionAuditEntry
* Field operationType was added to object type OrgUpdateMemberAuditEntry
* Field operationType was added to object type OrgUpdateDefaultRepositoryPermissionAuditEntry
* Field operationType was added to object type OrgUnblockUserAuditEntry
* Field operationType was added to object type OrgRestoreMemberAuditEntry
* Field operationType was added to object type OrgRemoveOutsideCollaboratorAuditEntry
* Field operationType was added to object type OrgRemoveMemberAuditEntry
* Field operationType was added to object type OrgRemoveBillingManagerAuditEntry
* Field operationType was added to object type OrgOauthAppAccessRequestedAuditEntry
* Field operationType was added to object type OrgOauthAppAccessDeniedAuditEntry
* Field operationType was added to object type OrgOauthAppAccessApprovedAuditEntry
* Field operationType was added to object type OrgInviteToBusinessAuditEntry
* Field operationType was added to object type OrgInviteMemberAuditEntry
* Field operationType was added to object type OrgEnableTwoFactorRequirementAuditEntry
* Field operationType was added to object type OrgEnableSamlAuditEntry
* Field operationType was added to object type OrgEnableOauthAppRestrictionsAuditEntry
* Field operationType was added to object type OrgDisableTwoFactorRequirementAuditEntry
* Field operationType was added to object type OrgDisableSamlAuditEntry
* Field operationType was added to object type OrgDisableOauthAppRestrictionsAuditEntry
* Field operationType was added to object type OrgConfigEnableCollaboratorsOnlyAuditEntry
* Field operationType was added to object type OrgConfigDisableCollaboratorsOnlyAuditEntry
* Field operationType was added to object type OrgBlockUserAuditEntry
* Field operationType was added to object type OrgAddMemberAuditEntry
* Field operationType was added to object type OrgAddBillingManagerAuditEntry
* Field operationType was added to object type OauthApplicationCreateAuditEntry
* Field operationType was added to object type MembersCanDeleteReposEnableAuditEntry
* Field operationType was added to object type MembersCanDeleteReposDisableAuditEntry
* Field operationType was added to object type AuditEntry
* Field operationType was added to object type MembersCanDeleteReposClearAuditEntry
* Field descriptionHTML was added to object type Organization
* Type PullRequestMergeMethod was added
* Type OperationType was added

## Schema changes for 2019-08-29

### The GraphQL schema includes these changes:

* Field topRepositories was added to object type User

## Schema changes for 2019-08-27

### The GraphQL schema includes these changes:

* Field preRelease was added to object type RegistryPackageVersion

## Schema changes for 2019-08-23

### The GraphQL schema includes these changes:

* Union member App was added to Union type PushAllowanceActor

## Schema changes for 2019-08-21

### The GraphQL schema includes these changes:

* Field shortDescriptionHTML was added to object type Release
* Field descriptionHTML was added to object type Release

## Schema changes for 2019-08-15

### The GraphQL schema includes these changes:

* Field removeEnterpriseIdentityProvider was removed from object type Mutation
* Type RemoveEnterpriseIdentityProviderInput was removed
* Type RemoveEnterpriseIdentityProviderPayload was removed
* Enum value ARCHIVED was added to enum CommentCannotUpdateReason

## Schema changes for 2019-08-13

### The GraphQL schema includes these changes:

* Field setEnterpriseIdentityProvider was removed from object type Mutation
* Type SetEnterpriseIdentityProviderInput was removed
* Type SetEnterpriseIdentityProviderPayload was removed

## Schema changes for 2019-08-09

### The GraphQL schema includes these changes:

* Field transferIssue was added to object type Mutation
* Type TransferIssueInput was added
* Type TransferIssuePayload was added

## Schema changes for 2019-08-08

### The GraphQL schema includes these changes:

* Union member RepoRemoveTopicAuditEntry was added to Union type OrganizationAuditEntry
* Union member RepoDestroyAuditEntry was added to Union type OrganizationAuditEntry
* Union member RepoCreateAuditEntry was added to Union type OrganizationAuditEntry
* Union member RepoChangeMergeSettingAuditEntry was added to Union type OrganizationAuditEntry
* Union member RepoArchivedAuditEntry was added to Union type OrganizationAuditEntry
* Union member RepoAddTopicAuditEntry was added to Union type OrganizationAuditEntry
* Type UpdateEnterpriseTwoFactorAuthenticationRequiredSettingInput was added
* Type UpdateEnterpriseTwoFactorAuthenticationRequiredSettingPayload was added
* Type UpdateEnterpriseTeamDiscussionsSettingInput was added
* Type UpdateEnterpriseTeamDiscussionsSettingPayload was added
* Type UpdateEnterpriseRepositoryProjectsSettingInput was added
* Type UpdateEnterpriseRepositoryProjectsSettingPayload was added
* Type UpdateEnterpriseProfileInput was added
* Type UpdateEnterpriseProfilePayload was added
* Type UpdateEnterpriseOrganizationProjectsSettingInput was added
* Type UpdateEnterpriseOrganizationProjectsSettingPayload was added
* Type UpdateEnterpriseMembersCanViewDependencyInsightsSettingInput was added
* Type UpdateEnterpriseMembersCanViewDependencyInsightsSettingPayload was added
* Type UpdateEnterpriseMembersCanUpdateProtectedBranchesSettingInput was added
* Type UpdateEnterpriseMembersCanUpdateProtectedBranchesSettingPayload was added
* Type UpdateEnterpriseMembersCanMakePurchasesSettingInput was added
* Type UpdateEnterpriseMembersCanMakePurchasesSettingPayload was added
* Type UpdateEnterpriseMembersCanInviteCollaboratorsSettingInput was added
* Type UpdateEnterpriseMembersCanInviteCollaboratorsSettingPayload was added
* Type UpdateEnterpriseMembersCanDeleteRepositoriesSettingInput was added
* Type UpdateEnterpriseMembersCanDeleteRepositoriesSettingPayload was added
* Type UpdateEnterpriseMembersCanDeleteIssuesSettingInput was added
* Type UpdateEnterpriseMembersCanDeleteIssuesSettingPayload was added
* Type UpdateEnterpriseMembersCanCreateRepositoriesSettingInput was added
* Type UpdateEnterpriseMembersCanCreateRepositoriesSettingPayload was added
* Type UpdateEnterpriseMembersCanChangeRepositoryVisibilitySettingInput was added
* Type UpdateEnterpriseMembersCanChangeRepositoryVisibilitySettingPayload was added
* Type UpdateEnterpriseDefaultRepositoryPermissionSettingInput was added
* Type UpdateEnterpriseDefaultRepositoryPermissionSettingPayload was added
* Type UpdateEnterpriseAllowPrivateRepositoryForkingSettingInput was added
* Type UpdateEnterpriseAllowPrivateRepositoryForkingSettingPayload was added
* Type UpdateEnterpriseAdministratorRoleInput was added
* Type UpdateEnterpriseAdministratorRolePayload was added
* Type UpdateEnterpriseActionExecutionCapabilitySettingInput was added
* Type UpdateEnterpriseActionExecutionCapabilitySettingPayload was added
* Type SetEnterpriseIdentityProviderInput was added
* Type SetEnterpriseIdentityProviderPayload was added
* Type RemoveEnterpriseOrganizationInput was added
* Type RemoveEnterpriseOrganizationPayload was added
* Type RemoveEnterpriseIdentityProviderInput was added
* Type RemoveEnterpriseIdentityProviderPayload was added
* Type RemoveEnterpriseAdminInput was added
* Type RemoveEnterpriseAdminPayload was added
* Type RegenerateEnterpriseIdentityProviderRecoveryCodesInput was added
* Type RegenerateEnterpriseIdentityProviderRecoveryCodesPayload was added
* Type InviteEnterpriseAdminInput was added
* Type InviteEnterpriseAdminPayload was added
* Type CreateEnterpriseOrganizationInput was added
* Type CreateEnterpriseOrganizationPayload was added
* Type CancelEnterpriseAdminInvitationInput was added
* Type CancelEnterpriseAdminInvitationPayload was added
* Type AcceptEnterpriseAdministratorInvitationInput was added
* Type AcceptEnterpriseAdministratorInvitationPayload was added
* Type EnterpriseUserAccountEdge was added
* Type EnterpriseUserAccountConnection was added
* Type IdentityProviderConfigurationState was added
* Type EnterpriseAdministratorInvitationEdge was added
* Type EnterpriseAdministratorInvitationConnection was added
* Type EnterpriseRepositoryInfoEdge was added
* Type EnterpriseRepositoryInfoConnection was added
* Type EnterpriseServerUserAccountsUploadEdge was added
* Type EnterpriseServerUserAccountsUploadConnection was added
* Type EnterpriseServerUserAccountEmailEdge was added
* Type EnterpriseServerUserAccountEmailConnection was added
* Type EnterpriseServerUserAccountEdge was added
* Type EnterpriseServerUserAccountConnection was added
* Type EnterpriseServerInstallationEdge was added
* Type EnterpriseServerInstallationConnection was added
* Type RepoRemoveTopicAuditEntry was added
* Type RepoDestroyAuditEntryVisibility was added
* Type RepoDestroyAuditEntry was added
* Type RepoCreateAuditEntryVisibility was added
* Type RepoCreateAuditEntry was added
* Type RepoChangeMergeSettingAuditEntryMergeType was added
* Type RepoChangeMergeSettingAuditEntry was added
* Type RepoArchivedAuditEntryVisibility was added
* Type RepoArchivedAuditEntry was added
* Type TopicAuditEntryData was added
* Type RepoAddTopicAuditEntry was added

### The Enterprise accounts preview includes these changes:

* Field updateEnterpriseTwoFactorAuthenticationRequiredSetting was added to object type Mutation
* Field updateEnterpriseTeamDiscussionsSetting was added to object type Mutation
* Field updateEnterpriseRepositoryProjectsSetting was added to object type Mutation
* Field updateEnterpriseProfile was added to object type Mutation
* Field updateEnterpriseOrganizationProjectsSetting was added to object type Mutation
* Field updateEnterpriseMembersCanViewDependencyInsightsSetting was added to object type Mutation
* Field updateEnterpriseMembersCanUpdateProtectedBranchesSetting was added to object type Mutation
* Field updateEnterpriseMembersCanMakePurchasesSetting was added to object type Mutation
* Field updateEnterpriseMembersCanInviteCollaboratorsSetting was added to object type Mutation
* Field updateEnterpriseMembersCanDeleteRepositoriesSetting was added to object type Mutation
* Field updateEnterpriseMembersCanDeleteIssuesSetting was added to object type Mutation
* Field updateEnterpriseMembersCanCreateRepositoriesSetting was added to object type Mutation
* Field updateEnterpriseMembersCanChangeRepositoryVisibilitySetting was added to object type Mutation
* Field updateEnterpriseDefaultRepositoryPermissionSetting was added to object type Mutation
* Field updateEnterpriseAllowPrivateRepositoryForkingSetting was added to object type Mutation
* Field updateEnterpriseAdministratorRole was added to object type Mutation
* Field updateEnterpriseActionExecutionCapabilitySetting was added to object type Mutation
* Field setEnterpriseIdentityProvider was added to object type Mutation
* Field removeEnterpriseOrganization was added to object type Mutation
* Field removeEnterpriseIdentityProvider was added to object type Mutation
* Field removeEnterpriseAdmin was added to object type Mutation
* Field regenerateEnterpriseIdentityProviderRecoveryCodes was added to object type Mutation
* Field inviteEnterpriseAdmin was added to object type Mutation
* Field createEnterpriseOrganization was added to object type Mutation
* Field cancelEnterpriseAdminInvitation was added to object type Mutation
* Field acceptEnterpriseAdministratorInvitation was added to object type Mutation
* Field enterpriseAdministratorInvitationByToken was added to object type Query
* Field enterpriseAdministratorInvitation was added to object type Query
* Field enterprise was added to object type Query
* Type EnterpriseOrderField was added
* Type ActionExecutionCapabilitySetting was added
* Type EnterpriseEnabledSettingValue was added
* Type SamlSignatureAlgorithm was added
* Type SamlDigestAlgorithm was added
* Type EnterpriseIdentityProvider was added
* Type EnterprisePendingMemberInvitationEdge was added
* Type EnterprisePendingMemberInvitationConnection was added
* Type RepositoryInvitationOrderField was added
* Type RepositoryInvitationOrder was added
* Type EnterprisePendingCollaboratorEdge was added
* Type EnterprisePendingCollaboratorConnection was added
* Type EnterpriseAdministratorInvitationOrderField was added
* Type EnterpriseAdministratorInvitationOrder was added
* Type EnterpriseAdministratorInvitation was added
* Type EnterpriseRepositoryInfo was added
* Type EnterpriseOutsideCollaboratorEdge was added
* Type EnterpriseOutsideCollaboratorConnection was added
* Type EnterpriseMembersCanMakePurchasesSettingValue was added
* Type OrganizationMembersCanCreateRepositoriesSettingValue was added
* Type EnterpriseMembersCanCreateRepositoriesSettingValue was added
* Type EnterpriseServerInstallationOrderField was added
* Type EnterpriseServerInstallationOrder was added
* Type EnterpriseServerUserAccountsUploadOrderField was added
* Type EnterpriseServerUserAccountsUploadOrder was added
* Type EnterpriseServerUserAccountsUploadSyncState was added
* Type EnterpriseServerUserAccountsUpload was added
* Type EnterpriseServerUserAccountOrderField was added
* Type EnterpriseServerUserAccountOrder was added
* Type EnterpriseServerUserAccountEmailOrderField was added
* Type EnterpriseServerUserAccountEmailOrder was added
* Type EnterpriseServerUserAccountEmail was added
* Type EnterpriseServerUserAccount was added
* Type EnterpriseServerInstallation was added
* Type EnterpriseDefaultRepositoryPermissionSettingValue was added
* Type EnterpriseEnabledDisabledSettingValue was added
* Type EnterpriseAdministratorRole was added
* Type EnterpriseAdministratorEdge was added
* Type EnterpriseAdministratorConnection was added
* Type EnterpriseOwnerInfo was added
* Type EnterpriseMemberOrderField was added
* Type EnterpriseMemberOrder was added
* Type EnterpriseUserDeployment was added
* Type OrganizationOrderField was added
* Type OrganizationOrder was added
* Type EnterpriseUserAccountMembershipRole was added
* Type EnterpriseOrganizationMembershipEdge was added
* Type EnterpriseOrganizationMembershipConnection was added
* Type EnterpriseUserAccount was added
* Type EnterpriseMember was added
* Type EnterpriseMemberEdge was added
* Type EnterpriseMemberConnection was added
* Type EnterpriseBillingInfo was added
* Type Enterprise was added

## Schema changes for 2019-07-31

### The GraphQL schema includes these changes:

* Enum value MARKED\_AS\_DUPLICATE\_EVENT was added to enum IssueTimelineItemsItemType
* Union member MarkedAsDuplicateEvent was added to Union type IssueTimelineItems
* Enum value MARKED\_AS\_DUPLICATE\_EVENT was added to enum PullRequestTimelineItemsItemType
* Union member MarkedAsDuplicateEvent was added to Union type PullRequestTimelineItems
* Argument publicOnly: Boolean added to field RegistryPackageOwner.registryPackages
* Argument publicOnly: Boolean added to field Repository.registryPackages
* Argument publicOnly: Boolean added to field User.registryPackages
* Argument publicOnly: Boolean added to field Organization.registryPackages
* Type IssueOrPullRequestEdge was added
* Type MarkedAsDuplicateEvent was added

## Schema changes for 2019-07-29

### The GraphQL schema includes these changes:

* User object implements Sponsorable interface
* Field sponsorshipsAsSponsor was added to object type User
* Field sponsorshipsAsMaintainer was added to object type User
* Type SponsorshipOrder was added
* Type SponsorshipPrivacy was added
* Type Sponsorship was added
* Type SponsorshipEdge was added
* Type SponsorshipConnection was added
* Type Sponsorable was added

## Schema changes for 2019-07-26

### The GraphQL schema includes these changes:

* Field registryPackagesForQuery was added to object type RegistryPackageSearch
* Field registryPackages was added to object type RegistryPackageOwner
* Field registryPackages was added to object type Repository
* Field registryPackagesForQuery was added to object type User
* Field registryPackages was added to object type User
* Field registryPackagesForQuery was added to object type Organization
* Field registryPackages was added to object type Organization
* Type RegistryPackageMetadatum was added
* Type RegistryPackageTag was added
* Type RegistryPackageTagEdge was added
* Type RegistryPackageTagConnection was added
* Type RegistryPackageStatistics was added
* Type RegistryPackageVersionEdge was added
* Type RegistryPackageVersionConnection was added
* Type RegistryPackageType was added
* Type RegistryPackageVersionStatistics was added
* Type RegistryPackageFileEdge was added
* Type RegistryPackageFileConnection was added
* Type RegistryPackageFile was added
* Type RegistryPackageDependencyType was added
* Type RegistryPackageDependency was added
* Type RegistryPackageDependencyEdge was added
* Type RegistryPackageDependencyConnection was added
* Type RegistryPackageVersion was added
* Type RegistryPackage was added
* Type RegistryPackageEdge was added
* Type RegistryPackageConnection was added

## Schema changes for 2019-07-24

### The GraphQL schema includes these changes:

* Union member Bot was added to Union type Assignee
* Field emojiHTML was added to object type UserStatus

### The [Checks preview](/en/graphql/overview/schema-previews#checks-preview) includes these changes:

* Field url was added to object type CheckSuite
* Field resourcePath was added to object type CheckSuite

## Schema changes for 2019-07-23

### The GraphQL schema includes these changes:

* Input field repositoryIds was added to input object type CreateProjectInput
* Field unlinkRepositoryFromProject was added to object type Mutation
* Field linkRepositoryToProject was added to object type Mutation
* Type UnlinkRepositoryFromProjectInput was added
* Type UnlinkRepositoryFromProjectPayload was added
* Type LinkRepositoryToProjectInput was added
* Type LinkRepositoryToProjectPayload was added

## Schema changes for 2019-07-19

### The GraphQL schema includes these changes:

* Argument ignoreTimeRange: Boolean was removed from field ContributionsCollection.joinedGitHubContribution
* Argument ignoreTimeRange: Boolean was removed from field ContributionsCollection.firstRepositoryContribution
* Argument ignoreTimeRange: Boolean was removed from field ContributionsCollection.firstPullRequestContribution
* Argument ignoreTimeRange: Boolean was removed from field ContributionsCollection.firstIssueContribution
* Field messageHtml was removed from object type ReviewDismissedEvent
* Field message was removed from object type ReviewDismissedEvent
* Field members was removed from object type Organization
* Gist object implements UniformResourceLocatable interface
* Field assignee was added to object type UnassignedEvent
* Field assignee was added to object type AssignedEvent
* Field url was added to object type Gist
* Field resourcePath was added to object type Gist
* Field savedReplies was added to object type User
* Field sponsorsListing was added to object type Query
* Type SponsorsListing was added
* Type SavedReplyOrderField was added
* Type SavedReplyOrder was added
* Type SavedReply was added
* Type SavedReplyEdge was added
* Type SavedReplyConnection was added
* Type Assignee was added

### The following changes will be made to the schema:

* On member AssignedEvent.user: user will be removed. Use the assignee field instead. Effective 2020-01-01.
* On member UnassignedEvent.user: user will be removed. Use the assignee field instead. Effective 2020-01-01.

## Schema changes for 2019-07-17

### The GraphQL schema includes these changes:

* Type BusinessAuditEntryData was removed
* Input field template was added to input object type CreateProjectInput
* Field updateRepository was added to object type Mutation
* Field mergeBranch was added to object type Mutation
* Type UpdateRepositoryInput was added
* Type UpdateRepositoryPayload was added
* Type MergeBranchInput was added
* Type MergeBranchPayload was added
* Type ProjectTemplate was added

### The Audit Log preview includes these changes:

* Field businessUrl was removed from object type RepositoryVisibilityChangeEnableAuditEntry
* Field businessSlug was removed from object type RepositoryVisibilityChangeEnableAuditEntry
* Field businessResourcePath was removed from object type RepositoryVisibilityChangeEnableAuditEntry
* RepositoryVisibilityChangeEnableAuditEntry object type no longer implements BusinessAuditEntryData interface
* Field businessUrl was removed from object type RepositoryVisibilityChangeDisableAuditEntry
* Field businessSlug was removed from object type RepositoryVisibilityChangeDisableAuditEntry
* Field businessResourcePath was removed from object type RepositoryVisibilityChangeDisableAuditEntry
* RepositoryVisibilityChangeDisableAuditEntry object type no longer implements BusinessAuditEntryData interface
* Field businessUrl was removed from object type PrivateRepositoryForkingEnableAuditEntry
* Field businessSlug was removed from object type PrivateRepositoryForkingEnableAuditEntry
* Field businessResourcePath was removed from object type PrivateRepositoryForkingEnableAuditEntry
* PrivateRepositoryForkingEnableAuditEntry object type no longer implements BusinessAuditEntryData interface
* Field businessUrl was removed from object type PrivateRepositoryForkingDisableAuditEntry
* Field businessSlug was removed from object type PrivateRepositoryForkingDisableAuditEntry
* Field businessResourcePath was removed from object type PrivateRepositoryForkingDisableAuditEntry
* PrivateRepositoryForkingDisableAuditEntry object type no longer implements BusinessAuditEntryData interface
* Field businessUrl was removed from object type OrgInviteToBusinessAuditEntry
* Field businessSlug was removed from object type OrgInviteToBusinessAuditEntry
* Field businessResourcePath was removed from object type OrgInviteToBusinessAuditEntry
* OrgInviteToBusinessAuditEntry object type no longer implements BusinessAuditEntryData interface
* Field businessUrl was removed from object type MembersCanDeleteReposEnableAuditEntry
* Field businessSlug was removed from object type MembersCanDeleteReposEnableAuditEntry
* Field businessResourcePath was removed from object type MembersCanDeleteReposEnableAuditEntry
* MembersCanDeleteReposEnableAuditEntry object type no longer implements BusinessAuditEntryData interface
* Field businessUrl was removed from object type MembersCanDeleteReposDisableAuditEntry
* Field businessSlug was removed from object type MembersCanDeleteReposDisableAuditEntry
* Field businessResourcePath was removed from object type MembersCanDeleteReposDisableAuditEntry
* MembersCanDeleteReposDisableAuditEntry object type no longer implements BusinessAuditEntryData interface
* Field businessUrl was removed from object type MembersCanDeleteReposClearAuditEntry
* Field businessSlug was removed from object type MembersCanDeleteReposClearAuditEntry
* Field businessResourcePath was removed from object type MembersCanDeleteReposClearAuditEntry
* MembersCanDeleteReposClearAuditEntry object type no longer implements BusinessAuditEntryData interface
* RepositoryVisibilityChangeEnableAuditEntry object implements EnterpriseAuditEntryData interface
* RepositoryVisibilityChangeDisableAuditEntry object implements EnterpriseAuditEntryData interface
* PrivateRepositoryForkingEnableAuditEntry object implements EnterpriseAuditEntryData interface
* PrivateRepositoryForkingDisableAuditEntry object implements EnterpriseAuditEntryData interface
* OrgInviteToBusinessAuditEntry object implements EnterpriseAuditEntryData interface
* MembersCanDeleteReposEnableAuditEntry object implements EnterpriseAuditEntryData interface
* MembersCanDeleteReposDisableAuditEntry object implements EnterpriseAuditEntryData interface
* MembersCanDeleteReposClearAuditEntry object implements EnterpriseAuditEntryData interface
* Field enterpriseUrl was added to object type RepositoryVisibilityChangeEnableAuditEntry
* Field enterpriseSlug was added to object type RepositoryVisibilityChangeEnableAuditEntry
* Field enterpriseResourcePath was added to object type RepositoryVisibilityChangeEnableAuditEntry
* Field enterpriseUrl was added to object type RepositoryVisibilityChangeDisableAuditEntry
* Field enterpriseSlug was added to object type RepositoryVisibilityChangeDisableAuditEntry
* Field enterpriseResourcePath was added to object type RepositoryVisibilityChangeDisableAuditEntry
* Field enterpriseUrl was added to object type PrivateRepositoryForkingEnableAuditEntry
* Field enterpriseSlug was added to object type PrivateRepositoryForkingEnableAuditEntry
* Field enterpriseResourcePath was added to object type PrivateRepositoryForkingEnableAuditEntry
* Field enterpriseUrl was added to object type PrivateRepositoryForkingDisableAuditEntry
* Field enterpriseSlug was added to object type PrivateRepositoryForkingDisableAuditEntry
* Field enterpriseResourcePath was added to object type PrivateRepositoryForkingDisableAuditEntry
* Field enterpriseUrl was added to object type OrgInviteToBusinessAuditEntry
* Field enterpriseSlug was added to object type OrgInviteToBusinessAuditEntry
* Field enterpriseResourcePath was added to object type OrgInviteToBusinessAuditEntry
* Field enterpriseUrl was added to object type MembersCanDeleteReposEnableAuditEntry
* Field enterpriseSlug was added to object type MembersCanDeleteReposEnableAuditEntry
* Field enterpriseResourcePath was added to object type MembersCanDeleteReposEnableAuditEntry
* Field enterpriseUrl was added to object type MembersCanDeleteReposDisableAuditEntry
* Field enterpriseSlug was added to object type MembersCanDeleteReposDisableAuditEntry
* Field enterpriseResourcePath was added to object type MembersCanDeleteReposDisableAuditEntry
* Field enterpriseUrl was added to object type MembersCanDeleteReposClearAuditEntry
* Field enterpriseSlug was added to object type MembersCanDeleteReposClearAuditEntry
* Field enterpriseResourcePath was added to object type MembersCanDeleteReposClearAuditEntry
* Type EnterpriseAuditEntryData was added

## Schema changes for 2019-07-04

### The GraphQL schema includes these changes:

* Enum value READY\_FOR\_REVIEW\_EVENT was added to enum PullRequestTimelineItemsItemType
* Union member ReadyForReviewEvent was added to Union type PullRequestTimelineItems
* Type ReadyForReviewEvent was added

## Schema changes for 2019-06-28

### The GraphQL schema includes these changes:

* Field updateRef was added to object type Mutation
* Field deleteRef was added to object type Mutation
* Field createRef was added to object type Mutation
* Type UpdateRefInput was added
* Type UpdateRefPayload was added
* Type DeleteRefInput was added
* Type DeleteRefPayload was added
* Type CreateRefInput was added
* Type CreateRefPayload was added

### The following changes will be made to the schema:

* On member Organization.pinnedRepositories: pinnedRepositories will be removed. Use ProfileOwner.pinnedItems instead. Effective 2019-10-01.
* On member RepositoryOwner.pinnedRepositories: pinnedRepositories will be removed. Use ProfileOwner.pinnedItems instead. Effective 2019-10-01.
* On member RepositoryVulnerabilityAlert.affectedRange: affectedRange will be removed. Use securityVulnerability.vulnerableVersionRange instead. Effective 2019-10-01.
* On member RepositoryVulnerabilityAlert.externalIdentifier: externalIdentifier will be removed. Use securityAdvisory.identifiers instead. Effective 2019-10-01.
* On member RepositoryVulnerabilityAlert.externalReference: externalReference will be removed. Use securityAdvisory.references instead. Effective 2019-10-01.
* On member RepositoryVulnerabilityAlert.fixedIn: fixedIn will be removed. Use securityVulnerability.firstPatchedVersion instead. Effective 2019-10-01.
* On member RepositoryVulnerabilityAlert.packageName: packageName will be removed. Use securityVulnerability.package instead. Effective 2019-10-01.
* On member User.pinnedRepositories: pinnedRepositories will be removed. Use ProfileOwner.pinnedItems instead. Effective 2019-10-01.

## Schema changes for 2019-06-26

### The GraphQL schema includes these changes:

* Field createRepository was added to object type Mutation
* Type CreateRepositoryInput was added
* Type CreateRepositoryPayload was added

## Schema changes for 2019-06-25

### The GraphQL schema includes these changes:

* Field PublicKey.updatedAt changed type from DateTime! to DateTime
* Field PublicKey.isReadOnly changed type from Boolean! to Boolean
* Field PublicKey.createdAt changed type from DateTime! to DateTime
* Field PublicKey.fingerprint changed type from String to String!
* Field issuePrioritiesDebug was added to object type Milestone

## Schema changes for 2019-06-19

### The GraphQL schema includes these changes:

* Union member App was added to Union type SearchResultItem
* Field cloneTemplateRepository was added to object type Mutation
* Field isTemplate was added to object type RepositoryInfo
* Field templateRepository was added to object type Repository
* Field isTemplate was added to object type Repository
* Type RepositoryVisibility was added
* Type CloneTemplateRepositoryInput was added
* Type CloneTemplateRepositoryPayload was added

## Schema changes for 2019-06-14

### The GraphQL schema includes these changes:

* Input field ContributionOrder.field changed type from ContributionOrderField! to ContributionOrderField

### The following changes will be made to the schema:

* On member ContributionOrder.field: field will be removed. Only one order field is supported. Effective 2019-10-01.

## Schema changes for 2019-06-13

### The GraphQL schema includes these changes:

* Argument oid: GitObjectID added to field Gist.files
* Field forks was added to object type Gist

## Schema changes for 2019-06-12

### The GraphQL schema includes these changes:

* Enum value USER was added to enum PinnableItemType
* Enum value TEAM was added to enum PinnableItemType
* Enum value PULL\_REQUEST was added to enum PinnableItemType
* Enum value PROJECT was added to enum PinnableItemType
* Enum value ORGANIZATION was added to enum PinnableItemType
* Field requiresCodeOwnerReviews was added to object type BranchProtectionRule

### The [Labels Preview preview](/en/graphql/overview/schema-previews#labels-preview) includes these changes:

* Input field description was added to input object type UpdateLabelInput
* Input field description was added to input object type CreateLabelInput

## Schema changes for 2019-06-04

### The following changes will be made to the schema:

* On member Issue.timeline: timeline will be removed. Use Issue.timelineItems instead. Effective 2019-10-01.
* On member PullRequest.timeline: timeline will be removed. Use PullRequest.timelineItems instead. Effective 2019-10-01.

## Schema changes for 2019-05-31

### The GraphQL schema includes these changes:

* Input field expiresAt was added to input object type ChangeUserStatusInput
* Field avatarUrl was added to object type StatusContext
* Field expiresAt was added to object type UserStatus

## Schema changes for 2019-05-29

### The GraphQL schema includes these changes:

* Enum value TRIAGE was added to enum RepositoryPermission
* Enum value MAINTAIN was added to enum RepositoryPermission
* Field openGraphImageUrl was added to object type Repository
* Field openGraphImageUrl was added to object type RepositoryInfo
* Field usesCustomOpenGraphImage was added to object type Repository
* Field usesCustomOpenGraphImage was added to object type RepositoryInfo

## Schema changes for 2019-05-23

### The GraphQL schema includes these changes:

* Type OrganizationAuditEntryEdge was added
* Type OrganizationAuditEntryConnection was added

### The Audit Log preview includes these changes:

* Field auditLog was added to object type Organization
* Type AuditLogOrderField was added
* Type AuditLogOrder was added
* Type TeamRemoveRepositoryAuditEntry was added
* Type TeamRemoveMemberAuditEntry was added
* Type TeamChangeParentTeamAuditEntry was added
* Type TeamAddRepositoryAuditEntry was added
* Type TeamAddMemberAuditEntry was added
* Type RepositoryVisibilityChangeEnableAuditEntry was added
* Type RepositoryVisibilityChangeDisableAuditEntry was added
* Type RepoRemoveMemberAuditEntryVisibility was added
* Type RepoRemoveMemberAuditEntry was added
* Type RepoConfigUnlockAnonymousGitAccessAuditEntry was added
* Type RepoConfigLockAnonymousGitAccessAuditEntry was added
* Type RepoConfigEnableSockpuppetDisallowedAuditEntry was added
* Type RepoConfigEnableContributorsOnlyAuditEntry was added
* Type RepoConfigEnableCollaboratorsOnlyAuditEntry was added
* Type RepoConfigEnableAnonymousGitAccessAuditEntry was added
* Type RepoConfigDisableSockpuppetDisallowedAuditEntry was added
* Type RepoConfigDisableContributorsOnlyAuditEntry was added
* Type RepoConfigDisableCollaboratorsOnlyAuditEntry was added
* Type RepoConfigDisableAnonymousGitAccessAuditEntry was added
* Type RepoAddMemberAuditEntryVisibility was added
* Type RepoAddMemberAuditEntry was added
* Type RepoAccessAuditEntryVisibility was added
* Type RepoAccessAuditEntry was added
* Type PrivateRepositoryForkingEnableAuditEntry was added
* Type PrivateRepositoryForkingDisableAuditEntry was added
* Type OrgUpdateMemberRepositoryInvitationPermissionAuditEntry was added
* Type OrgUpdateMemberRepositoryCreationPermissionAuditEntryVisibility was added
* Type OrgUpdateMemberRepositoryCreationPermissionAuditEntry was added
* Type OrgUpdateMemberAuditEntryPermission was added
* Type OrgUpdateMemberAuditEntry was added
* Type OrgUpdateDefaultRepositoryPermissionAuditEntryPermission was added
* Type OrgUpdateDefaultRepositoryPermissionAuditEntry was added
* Type OrgUnblockUserAuditEntry was added
* Type TeamAuditEntryData was added
* Type OrgRestoreMemberMembershipTeamAuditEntryData was added
* Type RepositoryAuditEntryData was added
* Type OrgRestoreMemberMembershipRepositoryAuditEntryData was added
* Type OrgRestoreMemberMembershipOrganizationAuditEntryData was added
* Type OrgRestoreMemberAuditEntryMembership was added
* Type OrgRestoreMemberAuditEntry was added
* Type OrgRemoveOutsideCollaboratorAuditEntryReason was added
* Type OrgRemoveOutsideCollaboratorAuditEntryMembershipType was added
* Type OrgRemoveOutsideCollaboratorAuditEntry was added
* Type OrgRemoveMemberAuditEntryReason was added
* Type OrgRemoveMemberAuditEntryMembershipType was added
* Type OrgRemoveMemberAuditEntry was added
* Type OrgRemoveBillingManagerAuditEntryReason was added
* Type OrgRemoveBillingManagerAuditEntry was added
* Type OrgOauthAppAccessRequestedAuditEntry was added
* Type OrgOauthAppAccessDeniedAuditEntry was added
* Type OrgOauthAppAccessApprovedAuditEntry was added
* Type OrgInviteToBusinessAuditEntry was added
* Type OrgInviteMemberAuditEntry was added
* Type OrgEnableTwoFactorRequirementAuditEntry was added
* Type OrgEnableSamlAuditEntry was added
* Type OrgEnableOauthAppRestrictionsAuditEntry was added
* Type OrgDisableTwoFactorRequirementAuditEntry was added
* Type OrgDisableSamlAuditEntry was added
* Type OrgDisableOauthAppRestrictionsAuditEntry was added
* Type OrgConfigEnableCollaboratorsOnlyAuditEntry was added
* Type OrgConfigDisableCollaboratorsOnlyAuditEntry was added
* Type OrgBlockUserAuditEntry was added
* Type OrgAddMemberAuditEntryPermission was added
* Type OrgAddMemberAuditEntry was added
* Type OrgAddBillingManagerAuditEntry was added
* Type OauthApplicationCreateAuditEntryState was added
* Type OauthApplicationAuditEntryData was added
* Type OauthApplicationCreateAuditEntry was added
* Type MembersCanDeleteReposEnableAuditEntry was added
* Type MembersCanDeleteReposDisableAuditEntry was added
* Type OrganizationAuditEntryData was added
* Type BusinessAuditEntryData was added
* Type PreciseDateTime was added
* Type ActorLocation was added
* Type AuditEntryActor was added
* Type AuditEntry was added
* Type MembersCanDeleteReposClearAuditEntry was added
* Type OrganizationAuditEntry was added

## Schema changes for 2019-05-13

### The GraphQL schema includes these changes:

* Enum value ISSUE was added to enum PinnableItemType
* Field origin was added to object type SecurityAdvisory

## Schema changes for 2019-05-09

### The GraphQL schema includes these changes:

* Union member Mannequin was added to Union type RequestedReviewer
* Type Mannequin was added

## Schema changes for 2019-04-23

### The GraphQL schema includes these changes:

* Field isArchived was added to object type MarketplaceListing

### The following changes will be made to the schema:

* On member MarketplaceListing.hasApprovalBeenRequested: hasApprovalBeenRequested will be removed. Use isVerificationPendingFromDraft instead. Effective 2019-10-01.
* On member MarketplaceListing.isApproved: isApproved will be removed. Use isPublic instead. Effective 2019-10-01.
* On member MarketplaceListing.isDelisted: isDelisted will be removed. Use isArchived instead. Effective 2019-10-01.

## Schema changes for 2019-04-10

### The GraphQL schema includes these changes:

* Field permissionSources was added to object type RepositoryCollaboratorEdge
* Type PermissionGranter was added
* Type PermissionSource was added

## Schema changes for 2019-04-04

### The GraphQL schema includes these changes:

* Enum value USER\_BLOCKED\_EVENT was added to enum IssueTimelineItemsItemType
* Union member UserBlockedEvent was added to Union type IssueTimelineItems
* Union member UserBlockedEvent was added to Union type IssueTimelineItem
* Enum value USER\_BLOCKED\_EVENT was added to enum PullRequestTimelineItemsItemType
* Union member UserBlockedEvent was added to Union type PullRequestTimelineItems
* Union member UserBlockedEvent was added to Union type PullRequestTimelineItem
* Field isDisabled was added to object type Repository
* Type UserBlockDuration was added
* Type UserBlockedEvent was added

## Schema changes for 2019-03-30

### The GraphQL schema includes these changes:

* User object implements ProfileOwner interface
* Organization object implements ProfileOwner interface
* Field viewerCanChangePinnedItems was added to object type User
* Field pinnedItemsRemaining was added to object type User
* Field pinnedItems was added to object type User
* Field pinnableItems was added to object type User
* Field itemShowcase was added to object type User
* Field anyPinnableItems was added to object type User
* Field viewerCanChangePinnedItems was added to object type Organization
* Field pinnedItemsRemaining was added to object type Organization
* Field pinnedItems was added to object type Organization
* Field pinnableItems was added to object type Organization
* Field itemShowcase was added to object type Organization
* Field anyPinnableItems was added to object type Organization
* Type PinnableItem was added
* Type PinnableItemEdge was added
* Type PinnableItemConnection was added
* Type ProfileItemShowcase was added
* Type PinnableItemType was added
* Type ProfileOwner was added

### The following changes will be made to the schema:

* On member Organization.pinnedRepositories: pinnedRepositories will be removed. Use ProfileOwner.pinnedItems instead. Effective 2019-07-01.
* On member RepositoryOwner.pinnedRepositories: pinnedRepositories will be removed. Use ProfileOwner.pinnedItems instead. Effective 2019-07-01.
* On member User.pinnedRepositories: pinnedRepositories will be removed. Use ProfileOwner.pinnedItems instead. Effective 2019-07-01.

## Schema changes for 2019-03-29

### The GraphQL schema includes these changes:

* Field cloneProject was added to object type Mutation
* Type CloneProjectInput was added
* Type CloneProjectPayload was added

## Schema changes for 2019-03-23

### The following changes will be made to the schema:

* On member Repository.protectedBranches: protectedBranches will be removed. Use Repository.branchProtectionRules instead. Effective 2019-01-01.
* On member Migration.uploadUrlTemplate: uploadUrlTemplate will be removed. Use uploadUrl instead. Effective 2019-04-01.
* On member Organization.members: members will be removed. Use Organization.membersWithRole instead. Effective 2019-04-01.
* On member ContributionsCollection.firstIssueContribution.ignoreTimeRange: ignoreTimeRange will be removed. Use a ContributionsCollection starting sufficiently far back Effective 2019-07-01.
* On member ContributionsCollection.firstPullRequestContribution.ignoreTimeRange: ignoreTimeRange will be removed. Use a ContributionsCollection starting sufficiently far back Effective 2019-07-01.
* On member ContributionsCollection.firstRepositoryContribution.ignoreTimeRange: ignoreTimeRange will be removed. Use a ContributionsCollection starting sufficiently far back Effective 2019-07-01.
* On member ContributionsCollection.joinedGitHubContribution.ignoreTimeRange: ignoreTimeRange will be removed. Use a ContributionsCollection starting sufficiently far back Effective 2019-07-01.
* On member RepositoryVulnerabilityAlert.affectedRange: affectedRange will be removed. Use securityVulnerability.vulnerableVersionRange instead. Effective 2019-07-01.
* On member RepositoryVulnerabilityAlert.externalIdentifier: externalIdentifier will be removed. Use securityAdvisory.identifiers instead. Effective 2019-07-01.
* On member RepositoryVulnerabilityAlert.externalReference: externalReference will be removed. Use securityAdvisory.references instead. Effective 2019-07-01.
* On member RepositoryVulnerabilityAlert.fixedIn: fixedIn will be removed. Use securityVulnerability.firstPatchedVersion instead. Effective 2019-07-01.
* On member RepositoryVulnerabilityAlert.packageName: packageName will be removed. Use securityVulnerability.package instead. Effective 2019-07-01.
* On member ReviewDismissedEvent.message: message will be removed. Use dismissalMessage instead. Effective 2019-07-01.
* On member ReviewDismissedEvent.messageHtml: messageHtml will be removed. Use dismissalMessageHTML instead. Effective 2019-07-01.

## Schema changes for 2019-03-21

### The GraphQL schema includes these changes:

* Field baseRepository was added to object type PullRequest

## Schema changes for 2019-03-19

### The following changes will be made to the schema:

* On member ContributionsCollection.firstIssueContribution.ignoreTimeRange: ignoreTimeRange will be removed. Use a ContributionsCollection starting sufficiently far back Effective 2019-07-01.
* On member ContributionsCollection.firstPullRequestContribution.ignoreTimeRange: ignoreTimeRange will be removed. Use a ContributionsCollection starting sufficiently far back Effective 2019-07-01.
* On member ContributionsCollection.firstRepositoryContribution.ignoreTimeRange: ignoreTimeRange will be removed. Use a ContributionsCollection starting sufficiently far back Effective 2019-07-01.
* On member ContributionsCollection.joinedGitHubContribution.ignoreTimeRange: ignoreTimeRange will be removed. Use a ContributionsCollection starting sufficiently far back Effective 2019-07-01.

## Schema changes for 2019-03-08

### The GraphQL schema includes these changes:

* Field associatedPullRequests was added to object type Commit
* Type PullRequestOrder was added

## Schema changes for 2019-03-06

### The GraphQL schema includes these changes:

* Field pullRequestReviewContributionsByRepository was added to object type ContributionsCollection
* Field pullRequestContributionsByRepository was added to object type ContributionsCollection
* Field issueContributionsByRepository was added to object type ContributionsCollection
* Type PullRequestReviewContributionsByRepository was added
* Type PullRequestContributionsByRepository was added
* Type IssueContributionsByRepository was added

### The Unified business identity preview includes these changes:

* Field pendingCollaborators was added to object type BusinessAdminInfo
* Field outsideCollaborators was added to object type BusinessAdminInfo
* Field members was added to object type Business
* Type BusinessMemberEdge was added
* Type BusinessMemberConnection was added
* Type RepositoryInvitationOrder was added
* Type BusinessPendingCollaboratorEdge was added
* Type BusinessPendingCollaboratorConnection was added
* Type BusinessRepositoryInfoEdge was added
* Type BusinessRepositoryInfoConnection was added
* Type BusinessOutsideCollaboratorEdge was added
* Type BusinessOutsideCollaboratorConnection was added

## Schema changes for 2019-03-04

### The GraphQL schema includes these changes:

* Field updateBusinessMembersCanUpdateProtectedBranchesSetting was removed from object type Mutation
* Type UpdateBusinessMembersCanUpdateProtectedBranchesSettingInput was removed
* Type UpdateBusinessMembersCanUpdateProtectedBranchesSettingPayload was removed
* Field pullRequestReviewContributions was added to object type ContributionsCollection
* Field contributionYears was added to object type ContributionsCollection
* Type CreatedPullRequestReviewContribution was added
* Type CreatedPullRequestReviewContributionEdge was added
* Type CreatedPullRequestReviewContributionConnection was added

### The Unified business identity preview includes these changes:

* Argument orderBy: BusinessMemberInvitationOrder added to field BusinessBillingInfo.pendingBillingManagerInvitations
* Argument orderBy: OrganizationInvitationOrder added to field BusinessAdminInfo.pendingMemberInvitations
* Argument orderBy: BusinessMemberInvitationOrder added to field BusinessAdminInfo.pendingAdminInvitations
* Type RepositoryInvitationOrderField was added
* Type OrganizationInvitationOrderField was added
* Type OrganizationInvitationOrder was added
* Type BusinessMemberInvitationOrderField was added
* Type BusinessMemberInvitationOrder was added

## Schema changes for 2019-03-02

### The GraphQL schema includes these changes:

* Argument orderBy: ContributionOrder added to field ContributionsCollection.issueContributions
* Field repositoryContributions was added to object type ContributionsCollection
* Type CreatedRepositoryContributionEdge was added
* Type CreatedRepositoryContributionConnection was added

## Schema changes for 2019-02-26

### The GraphQL schema includes these changes:

* Field OrganizationMemberEdge.hasTwoFactorEnabled changed type from Boolean! to Boolean

## Schema changes for 2019-02-23

### The GraphQL schema includes these changes:

* Field language was added to object type GistFile
* Field isTruncated was added to object type GistFile
* Field isImage was added to object type GistFile
* Field extension was added to object type GistFile
* Field encodedName was added to object type GistFile
* Type IdentityProviderConfigurationState was added

### The Unified business identity preview includes these changes:

* Field samlIdentityProviderSettingOrganizations was added to object type BusinessAdminInfo
* Field actionExecutionCapabilitySettingOrganizations was added to object type BusinessAdminInfo
* Argument query: String added to field Business.organizations

## Schema changes for 2019-02-21

### The GraphQL schema includes these changes:

* Enum value DRAFT was added to enum MergeStateStatus
* Field isVerified was added to object type MarketplaceListing
* Field isVerificationPendingFromUnverified was added to object type MarketplaceListing
* Field isVerificationPendingFromDraft was added to object type MarketplaceListing
* Field isUnverifiedPending was added to object type MarketplaceListing
* Field isUnverified was added to object type MarketplaceListing
* Field isPublic was added to object type MarketplaceListing

## Schema changes for 2019-02-20

### The GraphQL schema includes these changes:

* Field contributions was added to object type CommitContributionsByRepository
* Field pullRequestContributions was added to object type ContributionsCollection
* Field firstRepositoryContribution was added to object type ContributionsCollection
* Type ContributionOrderField was added
* Type ContributionOrder was added
* Type CreatedPullRequestContributionConnection was added
* Type CreatedRepositoryContribution was added
* Type CreatedRepositoryOrRestrictedContribution was added
* Type CommitContributionOrderField was added
* Type CommitContributionOrder was added
* Type CreatedCommitContribution was added
* Type CreatedCommitContributionEdge was added
* Type CreatedCommitContributionConnection was added

## Schema changes for 2019-02-15

### The GraphQL schema includes these changes:

* Field isFork was added to object type Gist
* Field files was added to object type Gist
* Field commitContributionsByRepository was added to object type ContributionsCollection
* Type GistFile was added
* Type CommitContributionsByRepository was added

### The Draft Pull Requests Preview preview includes these changes:

* Input field draft was added to input object type CreatePullRequestInput
* Field markPullRequestReadyForReview was added to object type Mutation
* Field isDraft was added to object type PullRequest
* Type MarkPullRequestReadyForReviewInput was added
* Type MarkPullRequestReadyForReviewPayload was added

## Schema changes for 2019-02-13

### The GraphQL schema includes these changes:

* Organization object implements MemberStatusable interface
* Team object implements MemberStatusable interface
* User object implements ProjectOwner interface
* Field changeUserStatus was added to object type Mutation
* Field memberStatuses was added to object type Organization
* Field memberStatuses was added to object type Team
* Field viewerCanCreateProjects was added to object type User
* Field status was added to object type User
* Field projectsUrl was added to object type User
* Field projectsResourcePath was added to object type User
* Field projects was added to object type User
* Field project was added to object type User
* Type ChangeUserStatusInput was added
* Type ChangeUserStatusPayload was added
* Type UserStatusOrderField was added
* Type UserStatusOrder was added
* Type UserStatus was added
* Type UserStatusEdge was added
* Type UserStatusConnection was added
* Type MemberStatusable was added

## Schema changes for 2019-02-12

### The GraphQL schema includes these changes:

* Field updatedAt was added to object type PublicKey
* Field isReadOnly was added to object type PublicKey
* Field fingerprint was added to object type PublicKey
* Field createdAt was added to object type PublicKey
* Field accessedAt was added to object type PublicKey
* Field hasTwoFactorEnabled was added to object type OrganizationMemberEdge
* Type SetBusinessIdentityProviderInput was added
* Type SetBusinessIdentityProviderPayload was added
* Type RemoveBusinessIdentityProviderInput was added
* Type RemoveBusinessIdentityProviderPayload was added
* Type RegenerateBusinessIdentityProviderRecoveryCodesInput was added
* Type RegenerateBusinessIdentityProviderRecoveryCodesPayload was added

### The Unified business identity preview includes these changes:

* Field setBusinessIdentityProvider was added to object type Mutation
* Field removeBusinessIdentityProvider was added to object type Mutation
* Field regenerateBusinessIdentityProviderRecoveryCodes was added to object type Mutation
* Field twoFactorRequiredSettingOrganizations was added to object type BusinessAdminInfo
* Field teamDiscussionsSettingOrganizations was added to object type BusinessAdminInfo
* Field samlIdentityProvider was added to object type BusinessAdminInfo
* Field repositoryProjectsSettingOrganizations was added to object type BusinessAdminInfo
* Field organizationProjectsSettingOrganizations was added to object type BusinessAdminInfo
* Field membersCanInviteCollaboratorsSettingOrganizations was added to object type BusinessAdminInfo
* Field membersCanDeleteRepositoriesSettingOrganizations was added to object type BusinessAdminInfo
* Field membersCanDeleteIssuesSettingOrganizations was added to object type BusinessAdminInfo
* Field membersCanCreateRepositoriesSettingOrganizations was added to object type BusinessAdminInfo
* Field membersCanChangeRepositoryVisibilitySettingOrganizations was added to object type BusinessAdminInfo
* Field defaultRepositoryPermissionSettingOrganizations was added to object type BusinessAdminInfo
* Field allowPrivateRepositoryForkingSettingOrganizations was added to object type BusinessAdminInfo
* Type SamlSignatureAlgorithm was added
* Type SamlDigestAlgorithm was added
* Type BusinessIdentityProvider was added
* Type OrganizationMembersCanCreateRepositoriesSettingValue was added

## Schema changes for 2019-02-09

### The GraphQL schema includes these changes:

* Default value for argument orderBy on field Commit.deployments changed from {"field"=>"CREATED\_AT", "direction"=>"DESC"} to {"field"=>"CREATED\_AT", "direction"=>"ASC"}
* Default value for argument orderBy on field Repository.deployments changed from {"field"=>"CREATED\_AT", "direction"=>"DESC"} to {"field"=>"CREATED\_AT", "direction"=>"ASC"}

## Schema changes for 2019-02-07

### The GraphQL schema includes these changes:

* Type DefaultRepositoryPermissionField was added

### The Repository Vulnerability Alerts preview includes these changes:

* Field RepositoryVulnerabilityAlert.externalReference changed type from String to String!
* Field vulnerableRequirements was added to object type RepositoryVulnerabilityAlert
* Field vulnerableManifestPath was added to object type RepositoryVulnerabilityAlert
* Field vulnerableManifestFilename was added to object type RepositoryVulnerabilityAlert
* Field securityVulnerability was added to object type RepositoryVulnerabilityAlert
* Field securityAdvisory was added to object type RepositoryVulnerabilityAlert

### The following changes will be made to the schema:

* On member RepositoryVulnerabilityAlert.affectedRange: affectedRange will be removed. Use securityVulnerability.vulnerableVersionRange instead. Effective 2019-07-01.
* On member RepositoryVulnerabilityAlert.externalIdentifier: externalIdentifier will be removed. Use securityAdvisory.identifiers instead. Effective 2019-07-01.
* On member RepositoryVulnerabilityAlert.externalReference: externalReference will be removed. Use securityAdvisory.references instead. Effective 2019-07-01.
* On member RepositoryVulnerabilityAlert.fixedIn: fixedIn will be removed. Use securityVulnerability.firstPatchedVersion instead. Effective 2019-07-01.
* On member RepositoryVulnerabilityAlert.packageName: packageName will be removed. Use securityVulnerability.package instead. Effective 2019-07-01.

## Schema changes for 2019-02-06

### The GraphQL schema includes these changes:

* Enum value QUEUED was added to enum DeploymentStatusState
* Enum value IN\_PROGRESS was added to enum DeploymentStatusState
* Field dismissalMessageHTML was added to object type ReviewDismissedEvent
* Field dismissalMessage was added to object type ReviewDismissedEvent

### The following changes will be made to the schema:

* On member ReviewDismissedEvent.message: message will be removed. Use dismissalMessage instead. Effective 2019-07-01.
* On member ReviewDismissedEvent.messageHtml: messageHtml will be removed. Use dismissalMessageHTML instead. Effective 2019-07-01.

## Schema changes for 2019-02-04

### The GraphQL schema includes these changes:

* Field deployments was added to object type Commit
* Argument orderBy: DeploymentOrder added to field Repository.deployments
* Type UpdateBusinessTwoFactorAuthenticationRequiredSettingInput was added
* Type UpdateBusinessTwoFactorAuthenticationRequiredSettingPayload was added
* Type UpdateBusinessTeamDiscussionsSettingInput was added
* Type UpdateBusinessTeamDiscussionsSettingPayload was added
* Type UpdateBusinessRepositoryProjectsSettingInput was added
* Type UpdateBusinessRepositoryProjectsSettingPayload was added
* Type UpdateBusinessProfileInput was added
* Type UpdateBusinessProfilePayload was added
* Type UpdateBusinessOrganizationProjectsSettingInput was added
* Type UpdateBusinessOrganizationProjectsSettingPayload was added
* Type UpdateBusinessMembersCanUpdateProtectedBranchesSettingInput was added
* Type UpdateBusinessMembersCanUpdateProtectedBranchesSettingPayload was added
* Type UpdateBusinessMembersCanInviteCollaboratorsSettingInput was added
* Type UpdateBusinessMembersCanInviteCollaboratorsSettingPayload was added
* Type UpdateBusinessMembersCanDeleteRepositoriesSettingInput was added
* Type UpdateBusinessMembersCanDeleteRepositoriesSettingPayload was added
* Type UpdateBusinessMembersCanDeleteIssuesSettingInput was added
* Type UpdateBusinessMembersCanDeleteIssuesSettingPayload was added
* Type UpdateBusinessMembersCanCreateRepositoriesSettingInput was added
* Type UpdateBusinessMembersCanCreateRepositoriesSettingPayload was added
* Type UpdateBusinessMembersCanChangeRepositoryVisibilitySettingInput was added
* Type UpdateBusinessMembersCanChangeRepositoryVisibilitySettingPayload was added
* Type UpdateBusinessDefaultRepositoryPermissionSettingInput was added
* Type UpdateBusinessDefaultRepositoryPermissionSettingPayload was added
* Type UpdateBusinessAllowPrivateRepositoryForkingSettingInput was added
* Type UpdateBusinessAllowPrivateRepositoryForkingSettingPayload was added
* Type RemoveBusinessBillingManagerInput was added
* Type RemoveBusinessBillingManagerPayload was added
* Type RemoveBusinessAdminInput was added
* Type RemoveBusinessAdminPayload was added
* Type InviteBusinessBillingManagerInput was added
* Type InviteBusinessBillingManagerPayload was added
* Type InviteBusinessAdminInput was added
* Type InviteBusinessAdminPayload was added
* Type CancelBusinessBillingManagerInvitationInput was added
* Type CancelBusinessBillingManagerInvitationPayload was added
* Type CancelBusinessAdminInvitationInput was added
* Type CancelBusinessAdminInvitationPayload was added
* Type AcceptBusinessMemberInvitationInput was added
* Type AcceptBusinessMemberInvitationPayload was added
* Type BusinessMemberInvitationEdge was added
* Type BusinessMemberInvitationConnection was added
* Type DeploymentOrderField was added
* Type DeploymentOrder was added

### The Unified business identity preview includes these changes:

* Field updateBusinessTwoFactorAuthenticationRequiredSetting was added to object type Mutation
* Field updateBusinessTeamDiscussionsSetting was added to object type Mutation
* Field updateBusinessRepositoryProjectsSetting was added to object type Mutation
* Field updateBusinessProfile was added to object type Mutation
* Field updateBusinessOrganizationProjectsSetting was added to object type Mutation
* Field updateBusinessMembersCanUpdateProtectedBranchesSetting was added to object type Mutation
* Field updateBusinessMembersCanInviteCollaboratorsSetting was added to object type Mutation
* Field updateBusinessMembersCanDeleteRepositoriesSetting was added to object type Mutation
* Field updateBusinessMembersCanDeleteIssuesSetting was added to object type Mutation
* Field updateBusinessMembersCanCreateRepositoriesSetting was added to object type Mutation
* Field updateBusinessMembersCanChangeRepositoryVisibilitySetting was added to object type Mutation
* Field updateBusinessDefaultRepositoryPermissionSetting was added to object type Mutation
* Field updateBusinessAllowPrivateRepositoryForkingSetting was added to object type Mutation
* Field removeBusinessBillingManager was added to object type Mutation
* Field removeBusinessAdmin was added to object type Mutation
* Field inviteBusinessBillingManager was added to object type Mutation
* Field inviteBusinessAdmin was added to object type Mutation
* Field cancelBusinessBillingManagerInvitation was added to object type Mutation
* Field cancelBusinessAdminInvitation was added to object type Mutation
* Field acceptBusinessMemberInvitation was added to object type Mutation
* Field businessMemberInvitationByToken was added to object type Query
* Field businessMemberInvitation was added to object type Query
* Field business was added to object type Query
* Type BusinessRepositoryInfo was added
* Type OrganizationOrderField was added
* Type OrganizationOrder was added
* Type BusinessBillingInfo was added
* Type BusinessEnabledSettingValue was added
* Type BusinessPendingMemberInvitationConnection was added
* Type BusinessMemberInvitationRole was added
* Type BusinessMemberInvitation was added
* Type BusinessMembersCanCreateRepositoriesSettingValue was added
* Type BusinessDefaultRepositoryPermissionSettingValue was added
* Type BusinessEnabledDisabledSettingValue was added
* Type BusinessAdminInfo was added
* Type Business was added

## Schema changes for 2019-01-31

### The GraphQL schema includes these changes:

* CodeOfConduct object implements Node interface
* Field resourcePath was added to object type CodeOfConduct
* Field id was added to object type CodeOfConduct
* Type PullRequestReviewThreadEdge was added
* Type PullRequestReviewThreadConnection was added

### The Pull Requests Preview preview includes these changes:

* Field reviewThreads was added to object type PullRequest

## Schema changes for 2019-01-30

### The GraphQL schema includes these changes:

* CodeOfConduct object implements Node interface
* Field resourcePath was added to object type CodeOfConduct
* Field id was added to object type CodeOfConduct
* Type PullRequestReviewThreadEdge was added
* Type PullRequestReviewThreadConnection was added

### The Pull Requests Preview preview includes these changes:

* Field reviewThreads was added to object type PullRequest

## Schema changes for 2019-01-19

### The GraphQL schema includes these changes:

* Field pendingMembers was added to object type Organization

## Schema changes for 2019-01-18

### The GraphQL schema includes these changes:

* Enum value ROCKET was added to enum ReactionContent
* Enum value EYES was added to enum ReactionContent

## Schema changes for 2019-01-16

### The GraphQL schema includes these changes:

* Field issueContributions was added to object type ContributionsCollection
* Type CreatedIssueContributionConnection was added

## Schema changes for 2019-01-11

### The GraphQL schema includes these changes:

* PullRequestReview object implements Reactable interface
* Field viewerCanReact was added to object type PullRequestReview
* Field reactions was added to object type PullRequestReview
* Field reactionGroups was added to object type PullRequestReview

### The Hovercards preview includes these changes:

* Argument includeNotificationContexts: Boolean added to field PullRequest.hovercard
* Argument includeNotificationContexts: Boolean added to field Issue.hovercard

## Schema changes for 2019-01-08

### The GraphQL schema includes these changes:

* Field protectedBranch was removed from object type ReviewDismissalAllowance
* Field protectedBranch was removed from object type PushAllowance

## Schema changes for 2019-01-05

### The GraphQL schema includes these changes:

* Type DeleteIssueInput was added
* Type DeleteIssuePayload was added

### The Issues Preview preview includes these changes:

* Field deleteIssue was added to object type Mutation

## Schema changes for 2019-01-03

### The GraphQL schema includes these changes:

* Field UpdateTopicsPayload.repository changed type from Repository! to Repository
* Field UpdateSubscriptionPayload.subscribable changed type from Subscribable! to Subscribable
* Field UpdatePullRequestReviewCommentPayload.pullRequestReviewComment changed type from PullRequestReviewComment! to PullRequestReviewComment
* Field UpdatePullRequestReviewPayload.pullRequestReview changed type from PullRequestReview! to PullRequestReview
* Field UpdateProjectColumnPayload.projectColumn changed type from ProjectColumn! to ProjectColumn
* Field UpdateProjectCardPayload.projectCard changed type from ProjectCard! to ProjectCard
* Field UpdateProjectPayload.project changed type from Project! to Project
* Field SubmitPullRequestReviewPayload.pullRequestReview changed type from PullRequestReview! to PullRequestReview
* Field RequestReviewsPayload.requestedReviewersEdge changed type from UserEdge! to UserEdge
* Field RequestReviewsPayload.pullRequest changed type from PullRequest! to PullRequest
* Field RemoveStarPayload.starrable changed type from Starrable! to Starrable
* Field RemoveReactionPayload.subject changed type from Reactable! to Reactable
* Field RemoveReactionPayload.reaction changed type from Reaction! to Reaction
* Field RemoveOutsideCollaboratorPayload.removedUser changed type from User! to User
* Field MoveProjectColumnPayload.columnEdge changed type from ProjectColumnEdge! to ProjectColumnEdge
* Field MoveProjectCardPayload.cardEdge changed type from ProjectCardEdge! to ProjectCardEdge
* Field DismissPullRequestReviewPayload.pullRequestReview changed type from PullRequestReview! to PullRequestReview
* Field DeletePullRequestReviewPayload.pullRequestReview changed type from PullRequestReview! to PullRequestReview
* Field DeleteProjectColumnPayload.project changed type from Project! to Project
* Field DeleteProjectColumnPayload.deletedColumnId changed type from ID! to ID
* Field DeleteProjectCardPayload.deletedCardId changed type from ID! to ID
* Field DeleteProjectCardPayload.column changed type from ProjectColumn! to ProjectColumn
* Field DeleteProjectPayload.owner changed type from ProjectOwner! to ProjectOwner
* Field DeclineTopicSuggestionPayload.topic changed type from Topic! to Topic
* Field CreateProjectPayload.project changed type from Project! to Project
* Field AddStarPayload.starrable changed type from Starrable! to Starrable
* Field AddReactionPayload.subject changed type from Reactable! to Reactable
* Field AddReactionPayload.reaction changed type from Reaction! to Reaction
* Field AddPullRequestReviewCommentPayload.commentEdge changed type from PullRequestReviewCommentEdge! to PullRequestReviewCommentEdge
* Field AddPullRequestReviewCommentPayload.comment changed type from PullRequestReviewComment! to PullRequestReviewComment
* Field AddPullRequestReviewPayload.reviewEdge changed type from PullRequestReviewEdge! to PullRequestReviewEdge
* Field AddPullRequestReviewPayload.pullRequestReview changed type from PullRequestReview! to PullRequestReview
* Field AddProjectColumnPayload.project changed type from Project! to Project
* Field AddProjectColumnPayload.columnEdge changed type from ProjectColumnEdge! to ProjectColumnEdge
* Field AddProjectCardPayload.projectColumn changed type from Project! to ProjectColumn
* Field AddProjectCardPayload.cardEdge changed type from ProjectCardEdge! to ProjectCardEdge
* Field AddCommentPayload.timelineEdge changed type from IssueTimelineItemEdge! to IssueTimelineItemEdge
* Field AddCommentPayload.subject changed type from Node! to Node
* Field AddCommentPayload.commentEdge changed type from IssueCommentEdge! to IssueCommentEdge
* Field AcceptTopicSuggestionPayload.topic changed type from Topic! to Topic

## Schema changes for 2018-12-21

### The GraphQL schema includes these changes:

* Field firstPullRequestContribution was added to object type ContributionsCollection
* Field firstIssueContribution was added to object type ContributionsCollection
* Type CreatedPullRequestOrRestrictedContribution was added
* Type RestrictedContribution was added
* Type CreatedIssueOrRestrictedContribution was added

## Schema changes for 2018-12-20

### The GraphQL schema includes these changes:

* Argument first: Int added to field Topic.relatedTopics

## Schema changes for 2018-12-18

### The Hovercards preview includes these changes:

* Field hovercard was added to object type PullRequest
* Field hovercard was added to object type Issue
* Type ViewerHovercardContext was added
* Type ReviewStatusHovercardContext was added

## Schema changes for 2018-12-14

### The GraphQL schema includes these changes:

* Field popularPullRequestContribution was added to object type ContributionsCollection
* Field popularIssueContribution was added to object type ContributionsCollection
* Field mostRecentCollectionWithoutActivity was added to object type ContributionsCollection
* Field joinedGitHubContribution was added to object type ContributionsCollection
* Field hasActivityInThePast was added to object type ContributionsCollection
* Type CreatedPullRequestContributionEdge was added
* Type CreatedIssueContributionEdge was added
* Type CreatedPullRequestContribution was added
* Type CreatedIssueContribution was added
* Type Contribution was added
* Type JoinedGitHubContribution was added

## Schema changes for 2018-12-13

### The GraphQL schema includes these changes:

* Enum value UNPINNED\_EVENT was added to enum IssueTimelineItemsItemType
* Enum value PINNED\_EVENT was added to enum IssueTimelineItemsItemType
* Union member UnpinnedEvent was added to Union type IssueTimelineItems
* Union member PinnedEvent was added to Union type IssueTimelineItems
* Enum value UNPINNED\_EVENT was added to enum PullRequestTimelineItemsItemType
* Enum value PINNED\_EVENT was added to enum PullRequestTimelineItemsItemType
* Union member UnpinnedEvent was added to Union type PullRequestTimelineItems
* Union member PinnedEvent was added to Union type PullRequestTimelineItems
* Type UnpinIssueInput was added
* Type UnpinIssuePayload was added
* Type PinIssueInput was added
* Type PinIssuePayload was added
* Type UnpinnedEvent was added
* Type PinnedEvent was added

### The [Pinned Issues Preview preview](/en/graphql/overview/schema-previews#pinned-issues-preview) includes these changes:

* Field unpinIssue was added to object type Mutation
* Field pinIssue was added to object type Mutation
* Field pinnedIssues was added to object type Repository
* Type PinnedIssue was added
* Type PinnedIssueEdge was added
* Type PinnedIssueConnection was added

## Schema changes for 2018-12-11

### The GraphQL schema includes these changes:

* Field tagName was added to object type Release

## Schema changes for 2018-12-06

### The GraphQL schema includes these changes:

* Type CreateContentAttachmentInput was added
* Type ContentReference was added
* Type ContentAttachment was added
* Type CreateContentAttachmentPayload was added

### The [Create content attachments preview](/en/graphql/overview/schema-previews#create-content-attachments-preview) includes these changes:

* Field createContentAttachment was added to object type Mutation

## Schema changes for 2018-12-03

### The GraphQL schema includes these changes:

* Field membersWithRole was added to object type Organization
* Type OrganizationMemberRole was added
* Type OrganizationMemberEdge was added
* Type OrganizationMemberConnection was added

### The following changes will be made to the schema:

* On member Organization.members: members will be removed. Use Organization.membersWithRole instead. Effective 2019-04-01.

## Schema changes for 2018-12-01

### The GraphQL schema includes these changes:

* Field contributionsCollection was added to object type User
* Type ContributionCalendarDay was added
* Type ContributionCalendarWeek was added
* Type Date was added
* Type ContributionCalendarMonth was added
* Type ContributionCalendar was added
* Type ContributionsCollection was added

## Schema changes for 2018-11-16

### The following changes will be made to the schema:

* On member Migration.uploadUrlTemplate: uploadUrlTemplate will be removed. Use uploadUrl instead. Effective 2019-04-01.

## Schema changes for 2018-11-12

### The GraphQL schema includes these changes:

* Field commitOid was added to object type Deployment

### The following changes will be made to the schema:

* On member AddProjectCardPayload.projectColumn: Type for projectColumn will change from Project! to ProjectColumn. Effective 2019-01-01.

## Schema changes for 2018-11-07

### The GraphQL schema includes these changes:

* Enum value TRANSFERRED\_EVENT was added to enum IssueTimelineItemsItemType
* Union member TransferredEvent was added to Union type IssueTimelineItems
* Union member TransferredEvent was added to Union type IssueTimelineItem
* GistComment object implements Minimizable interface
* Enum value TRANSFERRED\_EVENT was added to enum PullRequestTimelineItemsItemType
* Union member TransferredEvent was added to Union type PullRequestTimelineItems
* PullRequestReviewComment object implements Minimizable interface
* CommitComment object implements Minimizable interface
* Commit object implements UniformResourceLocatable interface
* IssueComment object implements Minimizable interface
* Enum value DENIED was added to enum CommentCannotUpdateReason
* Field viewerCanMinimize was added to object type GistComment
* Field minimizedReason was added to object type GistComment
* Field isMinimized was added to object type GistComment
* Field viewerCanMinimize was added to object type PullRequestReviewComment
* Field minimizedReason was added to object type PullRequestReviewComment
* Field isMinimized was added to object type PullRequestReviewComment
* Field viewerCanMinimize was added to object type CommitComment
* Field minimizedReason was added to object type CommitComment
* Field isMinimized was added to object type CommitComment
* Field viewerCanMinimize was added to object type IssueComment
* Field minimizedReason was added to object type IssueComment
* Field isMinimized was added to object type IssueComment
* Type UnminimizeCommentInput was added
* Type UnminimizeCommentPayload was added
* Type ReportedContentClassifiers was added
* Type MinimizeCommentInput was added
* Type MinimizeCommentPayload was added
* Type TransferredEvent was added

### The *Minimize Comments* preview includes these changes:

* Field unminimizeComment was added to object type Mutation
* Field minimizeComment was added to object type Mutation
* Type Minimizable was added

## Schema changes for 2018-10-24

### The Pull Requests Preview preview includes these changes:

* Field updatePullRequest was added to object type Mutation
* Field reopenPullRequest was added to object type Mutation
* Field mergePullRequest was added to object type Mutation
* Field deletePullRequestReviewComment was added to object type Mutation
* Field createPullRequest was added to object type Mutation
* Field closePullRequest was added to object type Mutation
* Field files was added to object type PullRequest
* Type UpdatePullRequestInput was added
* Type UpdatePullRequestPayload was added
* Type ReopenPullRequestInput was added
* Type ReopenPullRequestPayload was added
* Type MergePullRequestInput was added
* Type MergePullRequestPayload was added
* Type DeletePullRequestReviewCommentInput was added
* Type DeletePullRequestReviewCommentPayload was added
* Type CreatePullRequestInput was added
* Type CreatePullRequestPayload was added
* Type ClosePullRequestInput was added
* Type ClosePullRequestPayload was added
* Type PullRequestChangedFile was added
* Type PullRequestChangedFileEdge was added
* Type PullRequestChangedFileConnection was added

## Schema changes for 2018-10-19

### The GraphQL schema includes these changes:

* Argument ownerAffiliations: \[RepositoryAffiliation] added to field Repository.forks
* Argument ownerAffiliations: \[RepositoryAffiliation] added to field RepositoryOwner.repositories
* Argument ownerAffiliations: \[RepositoryAffiliation] added to field RepositoryOwner.pinnedRepositories
* Argument ownerAffiliations: \[RepositoryAffiliation] added to field User.watching
* Argument ownerAffiliations: \[RepositoryAffiliation] added to field User.repositories
* Argument ownerAffiliations: \[RepositoryAffiliation] added to field User.pinnedRepositories
* Argument ownerAffiliations: \[RepositoryAffiliation] added to field Organization.repositories
* Argument ownerAffiliations: \[RepositoryAffiliation] added to field Organization.pinnedRepositories

## Schema changes for 2018-10-16

### The Access to GitHub Security Advisories preview includes these changes:

* Field securityVulnerabilities was added to object type Query
* Field securityAdvisory was added to object type Query
* Field securityAdvisories was added to object type Query
* Type SecurityAdvisoryOrderField was added
* Type SecurityAdvisoryOrder was added
* Type SecurityAdvisoryIdentifierType was added
* Type SecurityAdvisoryIdentifierFilter was added
* Type SecurityVulnerabilityOrderField was added
* Type SecurityVulnerabilityOrder was added
* Type SecurityAdvisoryEcosystem was added
* Type SecurityAdvisoryPackage was added
* Type SecurityAdvisoryPackageVersion was added
* Type SecurityVulnerability was added
* Type SecurityVulnerabilityEdge was added
* Type SecurityVulnerabilityConnection was added
* Type SecurityAdvisorySeverity was added
* Type SecurityAdvisoryReference was added
* Type SecurityAdvisoryIdentifier was added
* Type SecurityAdvisory was added
* Type SecurityAdvisoryEdge was added
* Type SecurityAdvisoryConnection was added

## Schema changes for 2018-10-12

### The GraphQL schema includes these changes:

* Field outdated was added to object type PullRequestReviewComment
* Field onBehalfOf was added to object type PullRequestReview

## Schema changes for 2018-10-11

### The GraphQL schema includes these changes:

* Field state was added to object type PullRequestReviewComment
* Type PullRequestReviewCommentState was added

## Schema changes for 2018-10-08

### The following changes will be made to the schema:

* On member PushAllowance.protectedBranch: protectedBranch will be removed. Use Repository.branchProtectionRule instead. Effective 2019-01-01.
* On member Repository.protectedBranches: protectedBranches will be removed. Use Repository.branchProtectionRules instead. Effective 2019-01-01.
* On member ReviewDismissalAllowance.protectedBranch: protectedBranch will be removed. Use ReviewDismissalAllowance.branchProtectionRule instead. Effective 2019-01-01.

## Schema changes for 2018-09-26

### The GraphQL schema includes these changes:

* Field viewerCanApplySuggestion was added to object type PullRequest

## Schema changes for 2018-09-25

### The GraphQL schema includes these changes:

* Field ref was added to object type Deployment

## Schema changes for 2018-09-19

### The Issues Preview preview includes these changes:

* Field convertProjectCardNoteToIssue was added to object type Mutation
* Type ConvertProjectCardNoteToIssueInput was added
* Type ConvertProjectCardNoteToIssuePayload was added

## Schema changes for 2018-09-14

### The GraphQL schema includes these changes:

* Enum value UNMARKED\_AS\_DUPLICATE\_EVENT was removed from enum IssueTimelineItemsItemType
* Enum value MARKED\_AS\_DUPLICATE\_EVENT was removed from enum IssueTimelineItemsItemType
* Enum value UNMARKED\_AS\_DUPLICATE\_EVENT was removed from enum PullRequestTimelineItemsItemType
* Enum value MARKED\_AS\_DUPLICATE\_EVENT was removed from enum PullRequestTimelineItemsItemType

## Schema changes for 2018-09-13

### The [Checks preview](/en/graphql/overview/schema-previews#checks-preview) includes these changes:

* Field app was added to object type CheckSuite

## Schema changes for 2018-09-12

### The GraphQL schema includes these changes:

* Type UpdateIssueCommentInput was added
* Type UpdateIssueCommentPayload was added
* Type UpdateIssueInput was added
* Type UpdateIssuePayload was added
* Type UnmarkIssueAsDuplicateInput was added
* Type UnmarkIssueAsDuplicatePayload was added
* Type ReopenIssueInput was added
* Type ReopenIssuePayload was added
* Type RemoveLabelsFromLabelableInput was added
* Type RemoveLabelsFromLabelablePayload was added
* Type RemoveAssigneesFromAssignableInput was added
* Type RemoveAssigneesFromAssignablePayload was added
* Type DeleteIssueCommentInput was added
* Type DeleteIssueCommentPayload was added
* Type CreateIssueInput was added
* Type CreateIssuePayload was added
* Type CloseIssueInput was added
* Type CloseIssuePayload was added
* Type ClearLabelsFromLabelableInput was added
* Type ClearLabelsFromLabelablePayload was added
* Type AddLabelsToLabelableInput was added
* Type AddLabelsToLabelablePayload was added
* Type AddAssigneesToAssignableInput was added
* Type AddAssigneesToAssignablePayload was added
* Type IssueTimelineItemsItemType was added
* Type IssueTimelineItems was added
* Type IssueTimelineItemsEdge was added
* Type IssueTimelineItemsConnection was added
* Type PullRequestTimelineItemsItemType was added
* Type PullRequestTimelineItems was added
* Type PullRequestTimelineItemsEdge was added
* Type PullRequestTimelineItemsConnection was added

### The Issues Preview preview includes these changes:

* Field updateIssueComment was added to object type Mutation
* Field updateIssue was added to object type Mutation
* Field unmarkIssueAsDuplicate was added to object type Mutation
* Field reopenIssue was added to object type Mutation
* Field removeLabelsFromLabelable was added to object type Mutation
* Field removeAssigneesFromAssignable was added to object type Mutation
* Field deleteIssueComment was added to object type Mutation
* Field createIssue was added to object type Mutation
* Field closeIssue was added to object type Mutation
* Field clearLabelsFromLabelable was added to object type Mutation
* Field addLabelsToLabelable was added to object type Mutation
* Field addAssigneesToAssignable was added to object type Mutation
* Argument filterBy: IssueFilters added to field Milestone.issues
* Argument filterBy: IssueFilters added to field Label.issues
* Field timelineItems was added to object type PullRequest
* Argument filterBy: IssueFilters added to field Repository.issues
* Argument filterBy: IssueFilters added to field User.issues
* Field timelineItems was added to object type Issue
* Type PullRequestRevisionMarker was added
* Type PullRequestCommitCommentThread was added
* Type IssueFilters was added

### The Branch Protection Rules preview includes these changes:

* Field updateBranchProtectionRule was added to object type Mutation
* Field deleteBranchProtectionRule was added to object type Mutation
* Field createBranchProtectionRule was added to object type Mutation
* Field branchProtectionRule was added to object type ReviewDismissalAllowance
* Field branchProtectionRule was added to object type PushAllowance
* Field branchProtectionRules was added to object type Repository
* Type UpdateBranchProtectionRuleInput was added
* Type UpdateBranchProtectionRulePayload was added
* Type DeleteBranchProtectionRuleInput was added
* Type DeleteBranchProtectionRulePayload was added
* Type CreateBranchProtectionRuleInput was added
* Type CreateBranchProtectionRulePayload was added
* Type BranchProtectionRuleConflict was added
* Type BranchProtectionRuleConflictEdge was added
* Type BranchProtectionRuleConflictConnection was added
* Type BranchProtectionRule was added
* Type BranchProtectionRuleEdge was added
* Type BranchProtectionRuleConnection was added

## Schema changes for 2018-09-10

### The [Project Event Details preview](/en/graphql/overview/schema-previews#project-event-details-preview) includes these changes:

* Field projectColumnName was added to object type RemovedFromProjectEvent
* Field project was added to object type RemovedFromProjectEvent
* Field projectColumnName was added to object type MovedColumnsInProjectEvent
* Field projectCard was added to object type MovedColumnsInProjectEvent
* Field project was added to object type MovedColumnsInProjectEvent
* Field previousProjectColumnName was added to object type MovedColumnsInProjectEvent
* Field projectColumnName was added to object type ConvertedNoteToIssueEvent
* Field projectCard was added to object type ConvertedNoteToIssueEvent
* Field project was added to object type ConvertedNoteToIssueEvent
* Field projectColumnName was added to object type AddedToProjectEvent
* Field projectCard was added to object type AddedToProjectEvent
* Field project was added to object type AddedToProjectEvent

## Schema changes for 2018-09-06

### The GraphQL schema includes these changes:

* Enum value BAD\_CERT was added to enum GitSignatureState

## Schema changes for 2018-09-04

### The GraphQL schema includes these changes:

* Input field isArchived was added to input object type UpdateProjectCardInput
* Argument archivedStates: \[ProjectCardArchivedState] added to field PullRequest.projectCards
* Argument archivedStates: \[ProjectCardArchivedState] added to field Issue.projectCards
* Field isArchived was added to object type ProjectCard
* Argument archivedStates: \[ProjectCardArchivedState] added to field ProjectColumn.cards
* Field purpose was added to object type ProjectColumn
* Argument archivedStates: \[ProjectCardArchivedState] added to field Project.pendingCards
* Type PullRequestOrderField was added
* Type ProjectColumnPurpose was added
* Type ProjectCardArchivedState was added

## Schema changes for 2018-08-31

### The GraphQL schema includes these changes:

* Field logoBackgroundColor was added to object type App

## Schema changes for 2018-08-24

### The GraphQL schema includes these changes:

* Argument includeCategories: \[String!] added to field Query.marketplaceCategories

## Schema changes for 2018-08-13

### The GraphQL schema includes these changes:

* Union member DeploymentEnvironmentChangedEvent was added to Union type PullRequestTimelineItem
* Type DeploymentEnvironmentChangedEvent was added

## Schema changes for 2018-08-09

### The Temporary Cloning Token for Private Repositories preview includes these changes:

* Field tempCloneToken was added to object type Repository

## Schema changes for 2018-08-07

### The GraphQL schema includes these changes:

* Field isVerified was added to object type Organization
* Field app was added to object type MarketplaceListing
* Type App was added

### The [Checks preview](/en/graphql/overview/schema-previews#checks-preview) includes these changes:

* Field warningLevel was removed from object type CheckAnnotation
* Field startLine was removed from object type CheckAnnotation
* Field filename was removed from object type CheckAnnotation
* Field endLine was removed from object type CheckAnnotation
* Field creator was removed from object type CheckRun
* Field updateCheckSuitePreferences was added to object type Mutation
* Field updateCheckRun was added to object type Mutation
* Field rerequestCheckSuite was added to object type Mutation
* Field createCheckSuite was added to object type Mutation
* Field createCheckRun was added to object type Mutation
* Field path was added to object type CheckAnnotation
* Field location was added to object type CheckAnnotation
* Field annotationLevel was added to object type CheckAnnotation
* Type CheckSuiteAutoTriggerPreference was added
* Type UpdateCheckSuitePreferencesInput was added
* Type UpdateCheckSuitePreferencesPayload was added
* Type UpdateCheckRunInput was added
* Type UpdateCheckRunPayload was added
* Type RerequestCheckSuiteInput was added
* Type RerequestCheckSuitePayload was added
* Type CreateCheckSuiteInput was added
* Type CreateCheckSuitePayload was added
* Type RequestableCheckStatusState was added
* Type CheckRunOutputImage was added
* Type CheckAnnotationRange was added
* Type CheckAnnotationData was added
* Type CheckRunOutput was added
* Type CheckRunAction was added
* Type CreateCheckRunInput was added
* Type CreateCheckRunPayload was added
* Type CheckAnnotationPosition was added
* Type CheckAnnotationSpan was added

## Schema changes for 2018-08-01

### The following changes will be made to the schema:

* On member AcceptTopicSuggestionPayload.topic: Type for topic will change from Topic! to Topic. Effective 2019-01-01.
* On member AddCommentPayload.commentEdge: Type for commentEdge will change from IssueCommentEdge! to IssueCommentEdge. Effective 2019-01-01.
* On member AddCommentPayload.subject: Type for subject will change from Node! to Node. Effective 2019-01-01.
* On member AddCommentPayload.timelineEdge: Type for timelineEdge will change from IssueTimelineItemEdge! to IssueTimelineItemEdge. Effective 2019-01-01.
* On member AddProjectCardPayload.cardEdge: Type for cardEdge will change from ProjectCardEdge! to ProjectCardEdge. Effective 2019-01-01.
* On member AddProjectCardPayload.projectColumn: Type for projectColumn will change from Project! to Project. Effective 2019-01-01.
* On member AddProjectColumnPayload.columnEdge: Type for columnEdge will change from ProjectColumnEdge! to ProjectColumnEdge. Effective 2019-01-01.
* On member AddProjectColumnPayload.project: Type for project will change from Project! to Project. Effective 2019-01-01.
* On member AddPullRequestReviewCommentPayload.comment: Type for comment will change from PullRequestReviewComment! to PullRequestReviewComment. Effective 2019-01-01.
* On member AddPullRequestReviewCommentPayload.commentEdge: Type for commentEdge will change from PullRequestReviewCommentEdge! to PullRequestReviewCommentEdge. Effective 2019-01-01.
* On member AddPullRequestReviewPayload.pullRequestReview: Type for pullRequestReview will change from PullRequestReview! to PullRequestReview. Effective 2019-01-01.
* On member AddPullRequestReviewPayload.reviewEdge: Type for reviewEdge will change from PullRequestReviewEdge! to PullRequestReviewEdge. Effective 2019-01-01.
* On member AddReactionPayload.reaction: Type for reaction will change from Reaction! to Reaction. Effective 2019-01-01.
* On member AddReactionPayload.subject: Type for subject will change from Reactable! to Reactable. Effective 2019-01-01.
* On member AddStarPayload.starrable: Type for starrable will change from Starrable! to Starrable. Effective 2019-01-01.
* On member CreateProjectPayload.project: Type for project will change from Project! to Project. Effective 2019-01-01.
* On member DeclineTopicSuggestionPayload.topic: Type for topic will change from Topic! to Topic. Effective 2019-01-01.
* On member DeleteProjectCardPayload.column: Type for column will change from ProjectColumn! to ProjectColumn. Effective 2019-01-01.
* On member DeleteProjectCardPayload.deletedCardId: Type for deletedCardId will change from ID! to ID. Effective 2019-01-01.
* On member DeleteProjectColumnPayload.deletedColumnId: Type for deletedColumnId will change from ID! to ID. Effective 2019-01-01.
* On member DeleteProjectColumnPayload.project: Type for project will change from Project! to Project. Effective 2019-01-01.
* On member DeleteProjectPayload.owner: Type for owner will change from ProjectOwner! to ProjectOwner. Effective 2019-01-01.
* On member DeletePullRequestReviewPayload.pullRequestReview: Type for pullRequestReview will change from PullRequestReview! to PullRequestReview. Effective 2019-01-01.
* On member DismissPullRequestReviewPayload.pullRequestReview: Type for pullRequestReview will change from PullRequestReview! to PullRequestReview. Effective 2019-01-01.
* On member MoveProjectCardPayload.cardEdge: Type for cardEdge will change from ProjectCardEdge! to ProjectCardEdge. Effective 2019-01-01.
* On member MoveProjectColumnPayload.columnEdge: Type for columnEdge will change from ProjectColumnEdge! to ProjectColumnEdge. Effective 2019-01-01.
* On member RemoveOutsideCollaboratorPayload.removedUser: Type for removedUser will change from User! to User. Effective 2019-01-01.
* On member RemoveReactionPayload.reaction: Type for reaction will change from Reaction! to Reaction. Effective 2019-01-01.
* On member RemoveReactionPayload.subject: Type for subject will change from Reactable! to Reactable. Effective 2019-01-01.
* On member RemoveStarPayload.starrable: Type for starrable will change from Starrable! to Starrable. Effective 2019-01-01.
* On member RequestReviewsPayload.pullRequest: Type for pullRequest will change from PullRequest! to PullRequest. Effective 2019-01-01.
* On member RequestReviewsPayload.requestedReviewersEdge: Type for requestedReviewersEdge will change from UserEdge! to UserEdge. Effective 2019-01-01.
* On member SubmitPullRequestReviewPayload.pullRequestReview: Type for pullRequestReview will change from PullRequestReview! to PullRequestReview. Effective 2019-01-01.
* On member UpdateProjectCardPayload.projectCard: Type for projectCard will change from ProjectCard! to ProjectCard. Effective 2019-01-01.
* On member UpdateProjectColumnPayload.projectColumn: Type for projectColumn will change from ProjectColumn! to ProjectColumn. Effective 2019-01-01.
* On member UpdateProjectPayload.project: Type for project will change from Project! to Project. Effective 2019-01-01.
* On member UpdatePullRequestReviewCommentPayload.pullRequestReviewComment: Type for pullRequestReviewComment will change from PullRequestReviewComment! to PullRequestReviewComment. Effective 2019-01-01.
* On member UpdatePullRequestReviewPayload.pullRequestReview: Type for pullRequestReview will change from PullRequestReview! to PullRequestReview. Effective 2019-01-01.
* On member UpdateSubscriptionPayload.subscribable: Type for subscribable will change from Subscribable! to Subscribable. Effective 2019-01-01.
* On member UpdateTopicsPayload.repository: Type for repository will change from Repository! to Repository. Effective 2019-01-01.

## Schema changes for 2018-07-26

### The [Deployments preview](/en/graphql/overview/schema-previews#deployments-preview) includes these changes:

* Enum value QUEUED was added to enum DeploymentState
* Enum value IN\_PROGRESS was added to enum DeploymentState
* Field createDeploymentStatus was added to object type Mutation
* Field createDeployment was added to object type Mutation
* Field environment was added to object type DeploymentStatus
* Type CreateDeploymentStatusInput was added
* Type CreateDeploymentStatusPayload was added
* Type CreateDeploymentInput was added
* Type CreateDeploymentPayload was added

## Schema changes for 2018-07-16

### The GraphQL schema includes these changes:

* Field task was added to object type Deployment

## Schema changes for 2018-07-13

### The GraphQL schema includes these changes:

* Field GitHubMetadata.gitHubServicesSha changed type from String! to GitObjectID!
* Type RepositoryInvitationEdge was removed
* Type RepositoryCollaboratorAffiliation was removed
* Type PullRequestPubSubTopic was removed
* Type IssuePubSubTopic was removed
* Type DefaultRepositoryPermissionField was removed
* Type Date was removed

## Schema changes for 2018-07-11

### The GraphQL schema includes these changes:

* Field checkSuites was added to object type Commit
* Type CheckSuiteFilter was added
* Type Push was added
* Type CheckRunType was added
* Type CheckRunFilter was added
* Type CheckStatusState was added
* Type CheckConclusionState was added
* Type CheckAnnotationLevel was added
* Type CheckAnnotation was added
* Type CheckAnnotationEdge was added
* Type CheckAnnotationConnection was added
* Type CheckRun was added
* Type CheckRunEdge was added
* Type CheckRunConnection was added
* Type CheckSuite was added
* Type CheckSuiteEdge was added
* Type CheckSuiteConnection was added

## Schema changes for 2018-07-06

### The GraphQL schema includes these changes:

* Field updatedAt was added to object type Deployment
* Field description was added to object type Deployment

## Schema changes for 2018-07-04

### The GraphQL schema includes these changes:

* Field subject was removed from object type ReviewRequestedEvent
* Field subject was removed from object type ReviewRequestRemovedEvent
* Field isCrossReference was removed from object type ReferencedEvent
* Field commit was removed from object type ClosedEvent
* Field reviewer was removed from object type ReviewRequest
* Field license was removed from object type RepositoryInfo
* Field license was removed from object type Repository
* Field contributedRepositories was removed from object type User
* Field projectColumn was removed from object type ProjectCard

## Schema changes for 2018-07-03

### The GraphQL schema includes these changes:

* Repository object implements RegistryPackageOwner interface
* User object implements RegistryPackageSearch interface
* User object implements RegistryPackageOwner interface
* Organization object implements RegistryPackageSearch interface
* Organization object implements RegistryPackageOwner interface
* Type RegistryPackageSearch was added
* Type RegistryPackageOwner was added

## Schema changes for 2018-06-26

### The GraphQL schema includes these changes:

* Field permalink was added to object type PullRequest

## Schema changes for 2018-06-22

### The GraphQL schema includes these changes:

* Input field UpdateProjectCardInput.note changed type from String! to String

## Schema changes for 2018-06-21

### The GraphQL schema includes these changes:

* Argument useTopicAliases: Boolean added to field Query.marketplaceListings
* Argument useTopicAliases: Boolean added to field Query.marketplaceCategory

## Schema changes for 2018-06-14

### The GraphQL schema includes these changes:

* Field unlockLockable was added to object type Mutation
* Type UnlockLockableInput was added
* Type UnlockLockablePayload was added

## Schema changes for 2018-06-12

### The GraphQL schema includes these changes:

* Field subject was added to object type ReviewRequestedEvent
* Field subject was added to object type ReviewRequestRemovedEvent
* Field isCrossReference was added to object type ReferencedEvent
* Field commit was added to object type ClosedEvent
* Field reviewer was added to object type ReviewRequest
* Field license was added to object type RepositoryInfo
* Field license was added to object type Repository
* Field contributedRepositories was added to object type User
* Field projectColumn was added to object type ProjectCard
* Type TopicConnection was added
* Type RepositoryInvitationEdge was added
* Type RepositoryCollaboratorAffiliation was added
* Type PullRequestPubSubTopic was added
* Type IssuePubSubTopic was added
* Type DefaultRepositoryPermissionField was added
* Type Date was added
* Type MergeStateStatus was added

### The Team discussions preview includes these changes:

* Field updateTeamDiscussionComment was added to object type Mutation
* Field updateTeamDiscussion was added to object type Mutation
* Field deleteTeamDiscussionComment was added to object type Mutation
* Field deleteTeamDiscussion was added to object type Mutation
* Field createTeamDiscussionComment was added to object type Mutation
* Field createTeamDiscussion was added to object type Mutation
* Field discussionsUrl was added to object type Team
* Field discussionsResourcePath was added to object type Team
* Field discussions was added to object type Team
* Field discussion was added to object type Team
* Type UpdateTeamDiscussionCommentInput was added
* Type UpdateTeamDiscussionCommentPayload was added
* Type UpdateTeamDiscussionInput was added
* Type UpdateTeamDiscussionPayload was added
* Type DeleteTeamDiscussionCommentInput was added
* Type DeleteTeamDiscussionCommentPayload was added
* Type DeleteTeamDiscussionInput was added
* Type DeleteTeamDiscussionPayload was added
* Type CreateTeamDiscussionCommentInput was added
* Type CreateTeamDiscussionCommentPayload was added
* Type CreateTeamDiscussionInput was added
* Type CreateTeamDiscussionPayload was added
* Type TeamDiscussionOrderField was added
* Type TeamDiscussionOrder was added
* Type TeamDiscussionEdge was added
* Type TeamDiscussionConnection was added
* Type TeamDiscussionCommentOrderField was added
* Type TeamDiscussionCommentOrder was added
* Type TeamDiscussionComment was added
* Type TeamDiscussionCommentEdge was added
* Type TeamDiscussionCommentConnection was added
* Type TeamDiscussion was added

### The Protected Branch: Multiple Required Approving Reviews preview includes these changes:

* Field requiredApprovingReviewCount was added to object type ProtectedBranch

### The Protected Branch: Required Signatures preview includes these changes:

* Field hasRequiredSignatures was added to object type ProtectedBranch

### The [Merge info preview](/en/graphql/overview/schema-previews#merge-info-preview) includes these changes:

* Field mergeStateStatus was added to object type PullRequest
* Field canBeRebased was added to object type PullRequest

### The Repository Vulnerability Alerts preview includes these changes:

* Field vulnerabilityAlerts was added to object type Repository
* Type RepositoryVulnerabilityAlert was added
* Type RepositoryVulnerabilityAlertEdge was added
* Type RepositoryVulnerabilityAlertConnection was added

### The [Access to a Repositories Dependency Graph preview](/en/graphql/overview/schema-previews#access-to-a-repositories-dependency-graph-preview) includes these changes:

* Field dependencyGraphManifests was added to object type Repository
* Type DependencyGraphDependency was added
* Type DependencyGraphDependencyEdge was added
* Type DependencyGraphDependencyConnection was added
* Type DependencyGraphManifest was added
* Type DependencyGraphManifestEdge was added
* Type DependencyGraphManifestConnection was added

### The Hovercards preview includes these changes:

* Field hovercard was added to object type User
* Type OrganizationsHovercardContext was added
* Type OrganizationTeamsHovercardContext was added
* Type GenericHovercardContext was added
* Type HovercardContext was added
* Type Hovercard was added

## Schema changes for 2018-06-11

### The GraphQL schema includes these changes:

* Default value for argument affiliations on field User.watching changed from \["OWNER", "COLLABORATOR"] to \["OWNER", "COLLABORATOR", "ORGANIZATION\_MEMBER"]

## Schema changes for 2018-05-30

### The GraphQL schema includes these changes:

* Field editedAt was added to object type UserContentEdit

## Schema changes for 2018-05-25

### The GraphQL schema includes these changes:

* Field TextMatch.highlights changed type from \[TextMatchHighlight]! to \[TextMatchHighlight!]!
* Type MergeStateStatus was added

### The [Merge info preview](/en/graphql/overview/schema-previews#merge-info-preview) includes these changes:

* Field mergeStateStatus was added to object type PullRequest
* Field canBeRebased was added to object type PullRequest

## Schema changes for 2018-05-18

### The GraphQL schema includes these changes:

* License object implements Node interface

## Schema changes for 2018-05-17

### The GraphQL schema includes these changes:

* MarketplaceCategory object implements Node interface
* Field id was added to object type MarketplaceCategory

## Schema changes for 2018-05-09

### The GraphQL schema includes these changes:

* Field includesCreatedEdit was added to object type GistComment
* Field includesCreatedEdit was added to object type PullRequestReviewComment
* Field includesCreatedEdit was added to object type PullRequestReview
* Field includesCreatedEdit was added to object type IssueComment
* Field includesCreatedEdit was added to object type PullRequest
* Field includesCreatedEdit was added to object type Comment
* Field includesCreatedEdit was added to object type CommitComment
* Field includesCreatedEdit was added to object type Issue
* Argument excludeSubcategories: Boolean added to field Query.marketplaceCategories

### The Team discussions preview includes these changes:

* Field includesCreatedEdit was added to object type TeamDiscussionComment
* Field includesCreatedEdit was added to object type TeamDiscussion

## Schema changes for 2018-05-08

### The GraphQL schema includes these changes:

* ClosedEvent object implements UniformResourceLocatable interface
* Field url was added to object type ClosedEvent
* Field resourcePath was added to object type ClosedEvent

## Schema changes for 2018-05-03

### The [Access to a Repositories Dependency Graph preview](/en/graphql/overview/schema-previews#access-to-a-repositories-dependency-graph-preview) includes these changes:

* Field totalCount was added to object type DependencyGraphDependencyConnection

## Schema changes for 2018-04-28

### The Repository Vulnerability Alerts preview includes these changes:

* Field externalReference was added to object type RepositoryVulnerabilityAlert
* Field externalIdentifier was added to object type RepositoryVulnerabilityAlert
* Field dismisser was added to object type RepositoryVulnerabilityAlert
* Field dismissedAt was added to object type RepositoryVulnerabilityAlert
* Field dismissReason was added to object type RepositoryVulnerabilityAlert

## Schema changes for 2018-04-27

### The GraphQL schema includes these changes:

* Enum value TIMELINE was added to enum PullRequestPubSubTopic
* Enum value TIMELINE was added to enum IssuePubSubTopic

## Schema changes for 2018-04-24

### The GraphQL schema includes these changes:

* Field lockReason was added to object type LockedEvent

### The Repository Vulnerability Alerts preview includes these changes:

* Field vulnerabilityAlerts was added to object type Repository
* Type RepositoryVulnerabilityAlert was added
* Type RepositoryVulnerabilityAlertEdge was added
* Type RepositoryVulnerabilityAlertConnection was added

### The [Access to a Repositories Dependency Graph preview](/en/graphql/overview/schema-previews#access-to-a-repositories-dependency-graph-preview) includes these changes:

* Field dependencyGraphManifests was added to object type Repository
* Type DependencyGraphDependency was added
* Type DependencyGraphDependencyEdge was added
* Type DependencyGraphDependencyConnection was added
* Type DependencyGraphManifest was added
* Type DependencyGraphManifestEdge was added
* Type DependencyGraphManifestConnection was added

## Schema changes for 2018-04-23

### The GraphQL schema includes these changes:

* Field Team.viewerSubscription changed type from SubscriptionState! to SubscriptionState
* Field PullRequest.viewerSubscription changed type from SubscriptionState! to SubscriptionState
* Field Commit.viewerSubscription changed type from SubscriptionState! to SubscriptionState
* Enum value UNAVAILABLE was removed from enum SubscriptionState
* Field Subscribable.viewerSubscription changed type from SubscriptionState! to SubscriptionState
* Field Repository.viewerSubscription changed type from SubscriptionState! to SubscriptionState
* Field Issue.viewerSubscription changed type from SubscriptionState! to SubscriptionState

### The Team discussions preview includes these changes:

* Field TeamDiscussion.viewerSubscription changed type from SubscriptionState! to SubscriptionState

## Schema changes for 2018-04-19

### The GraphQL schema includes these changes:

* Type RepositoryInvitationEdge was added

## Schema changes for 2018-04-13

### The GraphQL schema includes these changes:

* Field wasSignedByGitHub was added to object type UnknownSignature
* Field wasSignedByGitHub was added to object type SmimeSignature
* Field wasSignedByGitHub was added to object type GpgSignature
* Field wasSignedByGitHub was added to object type GitSignature

## Schema changes for 2018-04-12

### The GraphQL schema includes these changes:

* Field url was added to object type Label
* Field updatedAt was added to object type Label
* Field resourcePath was added to object type Label
* Field createdAt was added to object type Label
* Field pseudoLicense was added to object type License

## Schema changes for 2018-04-10

### The GraphQL schema includes these changes:

* Field mergedBy was added to object type PullRequest
* Field maintainerCanModify was added to object type PullRequest
* Field diff was added to object type UserContentEdit
* Field deletedBy was added to object type UserContentEdit
* Field deletedAt was added to object type UserContentEdit

## Schema changes for 2018-04-03

### The GraphQL schema includes these changes:

* Field bodyText was added to object type GistComment
* Field bodyText was added to object type Comment
* Field bodyText was added to object type CommitComment

### The Team discussions preview includes these changes:

* Field bodyText was added to object type TeamDiscussionComment
* Field bodyText was added to object type TeamDiscussion

## Schema changes for 2018-03-28

### The GraphQL schema includes these changes:

* Type StaffHovercardContext was removed

## Schema changes for 2018-03-22

### The GraphQL schema includes these changes:

* Argument orderBy: TeamMemberOrder added to field Team.members
* Type TeamMemberOrderField was added
* Type TeamMemberOrder was added

### The Hovercards preview includes these changes:

* Field hovercard was added to object type User
* Type StaffHovercardContext was added
* Type OrganizationsHovercardContext was added
* Type OrganizationTeamsHovercardContext was added
* Type GenericHovercardContext was added
* Type HovercardContext was added
* Type Hovercard was added

## Schema changes for 2018-03-16

### The Protected Branch: Multiple Required Approving Reviews preview includes these changes:

* Field requiredApprovingReviewCount was added to object type ProtectedBranch

## Schema changes for 2018-03-14

### The GraphQL schema includes these changes:

* Enum value OCSP\_REVOKED was added to enum GitSignatureState
* Enum value OCSP\_PENDING was added to enum GitSignatureState
* Enum value OCSP\_ERROR was added to enum GitSignatureState

### The following changes will be made to the schema:

* On member AddedToProjectEvent.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member BaseRefChangedEvent.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Bot.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Bot.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member ClosedEvent.commit: commit will be removed. Use ClosedEvent.closer instead. Effective 2018-07-01.
* On member Comment.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member CommentDeletedEvent.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member CommitComment.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member CommitComment.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member ConvertedNoteToIssueEvent.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member DeployedEvent.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Deployment.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member DeploymentStatus.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member Gist.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member GistComment.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member GistComment.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member Issue.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Issue.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member IssueComment.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member IssueComment.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member MentionedEvent.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Milestone.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member MovedColumnsInProjectEvent.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Organization.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Project.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Project.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member ProjectCard.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member ProjectCard.projectColumn: projectColumn will be removed. Use ProjectCard.column instead. Effective 2018-07-01.
* On member ProjectCard.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member ProjectColumn.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member ProjectColumn.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member PullRequest.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member PullRequest.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member PullRequestReview\.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member PullRequestReview\.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member PullRequestReviewComment.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Reactable.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Reaction.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member ReferencedEvent.isCrossReference: isCrossReference will be removed. Use ReferencedEvent.isCrossRepository instead. Effective 2018-07-01.
* On member Release.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member ReleaseAsset.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member RemovedFromProjectEvent.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Repository.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member Repository.license: license will be removed. Use Repository.licenseInfo instead. Effective 2018-07-01.
* On member Repository.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member RepositoryInfo.license: license will be removed. Use Repository.licenseInfo instead. Effective 2018-07-01.
* On member RepositoryInfo.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member ReviewDismissedEvent.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member ReviewRequest.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member ReviewRequest.reviewer: reviewer will be removed. Use ReviewRequest.requestedReviewer instead. Effective 2018-07-01.
* On member ReviewRequestRemovedEvent.subject: subject will be removed. Use ReviewRequestRemovedEvent.requestedReviewer instead. Effective 2018-07-01.
* On member ReviewRequestedEvent.subject: subject will be removed. Use ReviewRequestedEvent.requestedReviewer instead. Effective 2018-07-01.
* On member Team.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member TeamDiscussion.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member TeamDiscussion.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member TeamDiscussionComment.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member TeamDiscussionComment.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member User.contributedRepositories: contributedRepositories will be removed. Use User.repositoriesContributedTo instead. Effective 2018-07-01.
* On member User.databaseId: databaseId will be removed. Use Node.id instead. Effective 2018-07-01.
* On member User.updatedAt: updatedAt will be removed. Effective 2018-07-01.
* On member UserContentEdit.updatedAt: updatedAt will be removed. Effective 2018-07-01.

## Schema changes for 2018-03-13

### The GraphQL schema includes these changes:

* Field RepositoryInvitation.repository changed type from RepositoryInvitationRepository to RepositoryInfo
* Type RepositoryInvitationRepository was removed
* Field squashMergeAllowed was added to object type Repository
* Field rebaseMergeAllowed was added to object type Repository
* Field mergeCommitAllowed was added to object type Repository

## Schema changes for 2018-03-10

### The GraphQL schema includes these changes:

* Enum value NONE was added to enum DefaultRepositoryPermissionField

## Schema changes for 2018-03-09

### The GraphQL schema includes these changes:

* Field databaseId was added to object type GistComment

## Schema changes for 2018-03-07

### The GraphQL schema includes these changes:

* Field permission was added to object type RepositoryInvitation
* Field isDefault was added to object type Label
* Field description was added to object type Label
* Argument query: String added to field Repository.labels
* Field viewerPermission was added to object type Repository
* Type CollectionItemContent was added

### The Team discussions preview includes these changes:

* Type TeamDiscussion was added
* Field updateTeamDiscussionComment was added to object type Mutation
* Field updateTeamDiscussion was added to object type Mutation
* Field deleteTeamDiscussionComment was added to object type Mutation
* Field deleteTeamDiscussion was added to object type Mutation
* Field createTeamDiscussionComment was added to object type Mutation
* Field createTeamDiscussion was added to object type Mutation
* Field discussionsUrl was added to object type Team
* Field discussionsResourcePath was added to object type Team
* Field discussions was added to object type Team
* Field discussion was added to object type Team
* Type UpdateTeamDiscussionCommentInput was added
* Type UpdateTeamDiscussionCommentPayload was added
* Type UpdateTeamDiscussionInput was added
* Type UpdateTeamDiscussionPayload was added
* Type DeleteTeamDiscussionCommentInput was added
* Type DeleteTeamDiscussionCommentPayload was added
* Type DeleteTeamDiscussionInput was added
* Type DeleteTeamDiscussionPayload was added
* Type CreateTeamDiscussionCommentInput was added
* Type CreateTeamDiscussionCommentPayload was added
* Type CreateTeamDiscussionInput was added
* Type CreateTeamDiscussionPayload was added
* Type TeamDiscussionOrderField was added
* Type TeamDiscussionOrder was added
* Type TeamDiscussionEdge was added
* Type TeamDiscussionConnection was added
* Type TeamDiscussionCommentOrderField was added
* Type TeamDiscussionCommentOrder was added
* Type TeamDiscussionComment was added
* Type TeamDiscussionCommentEdge was added
* Type TeamDiscussionCommentConnection was added

### The Protected Branch Required Signatures preview includes these changes:

* Field hasRequiredSignatures was added to object type ProtectedBranch

## Schema changes for 2018-02-14

### The following changes were made to the GraphQL schema:

* Argument orderBy: MilestoneOrder added to field Repository.milestones
* Argument states: \[MilestoneState!] added to field Repository.milestones
* Default value \["OWNER", "COLLABORATOR"] was added to argument affiliations on field Organization.pinnedRepositories.
* Default value \["OWNER", "COLLABORATOR"] was added to argument affiliations on field Organization.repositories.
* Default value \["OWNER", "COLLABORATOR"] was added to argument affiliations on field Repository.forks.
* Default value \["OWNER", "COLLABORATOR"] was added to argument affiliations on field RepositoryOwner.pinnedRepositories.
* Default value \["OWNER", "COLLABORATOR"] was added to argument affiliations on field RepositoryOwner.repositories.
* Default value \["OWNER", "COLLABORATOR"] was added to argument affiliations on field User.contributedRepositories.
* Default value \["OWNER", "COLLABORATOR"] was added to argument affiliations on field User.pinnedRepositories.
* Default value \["OWNER", "COLLABORATOR"] was added to argument affiliations on field User.repositories.
* Default value \["OWNER", "COLLABORATOR"] was added to argument affiliations on field User.watching.
* Field avatarUrl was added to object type Team
* Field createdAt was added to object type OrganizationInvitation
* Field organization was added to object type OrganizationInvitation
* Type MilestoneOrderField was added
* Type MilestoneOrder was added

## Schema changes for 2018-01-19

### The following changes were made to the GraphQL schema:

* Field baseRefOid was added to object type PullRequest
* Field headRefOid was added to object type PullRequest

## Schema changes for 2018-01-10

### The following changes were made to the GraphQL schema:

* Field activeLockReason was added to object type Issue
* Field activeLockReason was added to object type Lockable
* Field activeLockReason was added to object type PullRequest
* Field lockLockable was added to object type Mutation
* Type LockLockableInput was added
* Type LockLockablePayload was added
* Type LockReason was added

## Schema changes for 2017-12-15

### The following changes were made to the GraphQL schema:

* Field additions was added to object type Commit
* Field changedFiles was added to object type Commit
* Field closedAt was added to object type Milestone
* Field closed was added to object type Milestone
* Field createdAt was added to object type Milestone
* Field deletions was added to object type Commit
* Field updatedAt was added to object type Milestone
* Milestone object implements Closable interface

## Schema changes for 2017-12-12

### The following changes were made to the GraphQL schema:

* Enum value UNAVAILABLE was added to enum SubscriptionState
* Field authoredDate was added to object type Commit
* Field pushedDate was added to object type Commit

## Schema changes for 2017-12-09

### The following changes were made to the GraphQL schema:

* Field deployKeys was added to object type Repository
* Type DeployKeyConnection was added
* Type DeployKeyEdge was added
* Type DeployKey was added

## Schema changes for 2017-12-05

### The following changes were made to the GraphQL schema:

* Field release was added to object type Repository

## Schema changes for 2017-12-02

### The following changes were made to the GraphQL schema:

* Field forkCount was added to object type RepositoryInfo
* Field forkCount was added to object type RepositoryInvitationRepository
* Field forkCount was added to object type Repository
* Field marketplaceListing was added to object type Query
* Field marketplaceListings was added to object type Query
* Type MarketplaceListingConnection was added
* Type MarketplaceListingEdge was added
* Type MarketplaceListing was added
* Union member MarketplaceListing was added to Union type SearchResultItem

## Schema changes for 2017-11-28

### The following changes were made to the GraphQL schema:

* Field repositoriesContributedTo was added to object type User

## Schema changes for 2017-11-24

### The following changes were made to the GraphQL schema:

* Field changedFiles was added to object type PullRequest
* Field reactable was added to object type Reaction

## Schema changes for 2017-11-18

### The following changes were made to the GraphQL schema:

* Input field UpdateProjectInput.name changed type from String! to String
* Input field public was added to input object type UpdateProjectInput

## Schema changes for 2017-11-17

### The following changes were made to the GraphQL schema:

* Field issues was added to object type Milestone
* Type TopicConnection was added

## Schema changes for 2017-11-16

### The following changes were made to the GraphQL schema:

* Field issues was added to object type Milestone

## Schema changes for 2017-11-15

### The following changes were made to the GraphQL schema:

* Field parents was added to object type Commit
* Type CommitConnection was added

## Schema changes for 2017-11-14

### The following changes were made to the GraphQL schema:

* Argument orderBy: ReleaseOrder added to field Repository.releases
* Field marketplaceCategories was added to object type Query
* Field marketplaceCategory was added to object type Query
* Field parents was added to object type Commit
* Field publicKeys was added to object type User
* Field totalCount was added to object type CommitHistoryConnection
* Type CommitConnection was added
* Type MarketplaceCategory was added
* Type PublicKeyConnection was added
* Type PublicKeyEdge was added
* Type PublicKey was added
* Type ReleaseOrderField was added
* Type ReleaseOrder was added

## Schema changes for 2017-11-10

### The following changes were made to the GraphQL schema:

* Field createdAt was added to object type DeploymentStatus
* Field updatedAt was added to object type DeploymentStatus
* Field viewerCanSubscribe was added to object type Team
* Field viewerSubscription was added to object type Team
* Team object implements Subscribable interface

## Schema changes for 2017-11-08

### The following changes were made to the GraphQL schema:

* Field BaseRefForcePushedEvent.afterCommit changed type from Commit! to Commit
* Field BaseRefForcePushedEvent.beforeCommit changed type from Commit! to Commit
* Field HeadRefForcePushedEvent.afterCommit changed type from Commit! to Commit
* Field HeadRefForcePushedEvent.beforeCommit changed type from Commit! to Commit
* Field ReviewRequestRemovedEvent.subject changed type from User! to User
* Field ReviewRequestedEvent.subject changed type from User! to User
* Argument orderBy: RefOrder added to field Repository.refs
* Field requestedReviewer was added to object type ReviewRequestRemovedEvent
* Field requestedReviewer was added to object type ReviewRequest
* Field requestedReviewer was added to object type ReviewRequestedEvent
* Type RefOrderField was added
* Type RefOrder was added
* Type RequestedReviewer was added

## Schema changes for 2017-11-03

### The following changes were made to the GraphQL schema:

* Field tarballUrl was added to object type Commit
* Field zipballUrl was added to object type Commit

## Schema changes for 2017-11-02

### The following changes were made to the GraphQL schema:

* Field tarballUrl was added to object type Commit
* Field zipballUrl was added to object type Commit
* Type TopicEdge was added

## Schema changes for 2017-10-27

### The following changes were made to the GraphQL schema:

* Argument author: String added to field PullRequest.reviews
* Field additions was added to object type PullRequest
* Field deletions was added to object type PullRequest

## Schema changes for 2017-10-25

### The following changes were made to the GraphQL schema:

* Type UserContentEditEdge was added
* Type UserContentEdit was added

## Schema changes for 2017-10-24

### The following changes were made to the GraphQL schema:

* Field assignableUsers was added to object type Repository
* Type UserContentEditEdge was added
* Type UserContentEdit was added

## Schema changes for 2017-10-20

### The following changes were made to the GraphQL schema:

* Field projectCards was added to object type Issue
* Field projectCards was added to object type PullRequest

## Schema changes for 2017-10-14

### The following changes were made to the GraphQL schema:

* Field isInvoiced was removed from object type Organization
* Field isInvoiced was removed from object type User

## Schema changes for 2017-10-04

### The following changes were made to the GraphQL schema:

* Field collaborators was added to object type Repository
* Field isArchived was added to object type RepositoryInfo
* Field isArchived was added to object type RepositoryInvitationRepository
* Field isArchived was added to object type Repository
* Type CollaboratorAffiliation was added
* Type RepositoryCollaboratorConnection was added
* Type RepositoryCollaboratorEdge was added

## Schema changes for 2017-09-28

### The following changes were made to the GraphQL schema:

* Type Date was added

## Schema changes for 2017-09-22

### The following changes were made to the GraphQL schema:

* Field gitIpAddresses was added to object type GitHubMetadata
* Field hookIpAddresses was added to object type GitHubMetadata
* Field importerIpAddresses was added to object type GitHubMetadata
* Field pagesIpAddresses was added to object type GitHubMetadata

## Schema changes for 2017-09-18

### The following changes were made to the GraphQL schema:

* Field GistComment.gist changed type from Gist to Gist!

## Schema changes for 2017-09-15

### The following changes were made to the GraphQL schema:

* Field meta was added to object type Query
* Type GitHubMetadata was added

## Schema changes for 2017-09-14

### The following changes were made to the GraphQL schema:

* Field User.gistComments changed type from IssueCommentConnection! to GistCommentConnection!

## Schema changes for 2017-09-13

### The following changes were made to the GraphQL schema:

* Field createdAt was added to object type Bot
* Field gist was added to object type GistComment
* Field updatedAt was added to object type Bot

## Schema changes for 2017-09-11

### The following changes were made to the GraphQL schema:

* Field downloadUrl was added to object type ReleaseAsset

## Schema changes for 2017-09-08

### The following changes were made to the GraphQL schema:

* OrganizationInvitation object implements Node interface

## Schema changes for 2017-09-07

### The following changes were made to the GraphQL schema:

* Field meta was removed from object type Query
* GitHubMetadata was removed
* Field closed was added to object type Project
* Field invitationType was added to object type OrganizationInvitation
* Field pendingCards was added to object type Project
* Field resourcePath was added to object type ProjectColumn
* Field url was added to object type ProjectColumn
* Type OrganizationInvitationType was added
* Project object implements Closable interface

## Schema changes for 2017-09-06

### The following changes were made to the GraphQL schema:

* Field GitHubMetadata.gitIpAddresses changed type from String to \[String!]
* Field GitHubMetadata.hookIpAddresses changed type from String to \[String!]
* Field GitHubMetadata.importerIpAddresses changed type from String to \[String!]
* Field GitHubMetadata.pagesIpAddresses changed type from String to \[String!]
* Field installedVersion was removed from object type GitHubMetadata
* Field repository was added to object type PullRequestReviewThread

## Schema changes for 2017-09-05

### The following changes were made to the GraphQL schema:

* Field repository was removed from object type PullRequestReviewThread
* Field meta was added to object type Query
* Type GitHubMetadata was added

## Schema changes for 2017-09-04

### The following changes were made to the GraphQL schema:

* Field closed was removed from object type Project
* Field pendingCards was removed from object type Project
* Field resourcePath was removed from object type ProjectColumn
* Field url was removed from object type ProjectColumn
* Project object type no longer implements Closable interface
* Field repository was added to object type PullRequestReviewThread

## Schema changes for 2017-09-01

### The following changes were made to the GraphQL schema:

* Field channel was removed from object type Project
* Field searchQueryForViewer was removed from object type Project

## Schema changes for 2017-08-31

### The following changes were made to the GraphQL schema:

* Field resourcePath was added to object type ProjectColumn
* Field searchQueryForViewer was added to object type Project
* Field url was added to object type ProjectColumn

## Schema changes for 2017-08-30

### The following changes were made to the GraphQL schema:

* Field channel was added to object type Project
* Field closed was added to object type Project
* Field pendingCards was added to object type Project
* Project object implements Closable interface

## Schema changes for 2017-08-21

### The following changes were made to the GraphQL schema:

* Field replyTo was added to object type PullRequestReviewComment

## Schema changes for 2017-08-16

### The following changes were made to the GraphQL schema:

* Field description was added to object type Organization
* Field email was added to object type Organization
* Field location was added to object type Organization
* Field websiteUrl was added to object type Organization

## Schema changes for 2017-08-15

### The following changes were made to the GraphQL schema:

* Field gistComments was added to object type User
* Field id was added to object type Subscribable
* Field issueComments was added to object type User
* Field resourcePath was added to object type CommitComment
* Field url was added to object type CommitComment

## Schema changes for 2017-08-14

### The following changes were made to the GraphQL schema:

* Field blog was removed from object type Organization
* Field description was removed from object type Organization
* Field email was removed from object type Organization
* Field location was removed from object type Organization
* Argument dryRun: Boolean added to field Query.rateLimit
* Field milestone was added to object type PullRequest
* Field nodeCount was added to object type RateLimit
* Union member CrossReferencedEvent was added to Union type PullRequestTimelineItem

## Schema changes for 2017-08-11

### The following changes were made to the GraphQL schema:

* Argument dryRun: Boolean was removed from field Query.rateLimit
* Field closed was removed from object type Project
* Field gistComments was removed from object type User
* Field id was removed from object type Subscribable
* Field issueComments was removed from object type User
* Field milestone was removed from object type PullRequest
* Field nodeCount was removed from object type RateLimit
* Field pendingCards was removed from object type Project
* Field replyTo was removed from object type PullRequestReviewComment
* Field repository was removed from object type PullRequestReviewThread
* Field resourcePath was removed from object type CommitComment
* Field resourcePath was removed from object type ProjectColumn
* Field url was removed from object type CommitComment
* Field url was removed from object type ProjectColumn
* Field websiteUrl was removed from object type Organization
* Union member CrossReferencedEvent was removed from Union type PullRequestTimelineItem
* Project object type no longer implements Closable interface
* Field blog was added to object type Organization

## Schema changes for 2017-08-10

### The following changes were made to the GraphQL schema:

* Argument dryRun: Boolean added to field Query.rateLimit
* Field closed was added to object type Project
* Field description was added to object type Organization
* Field email was added to object type Organization
* Field gistComments was added to object type User
* Field id was added to object type Subscribable
* Field issueComments was added to object type User
* Field location was added to object type Organization
* Field milestone was added to object type PullRequest
* Field nodeCount was added to object type RateLimit
* Field pendingCards was added to object type Project
* Field replyTo was added to object type PullRequestReviewComment
* Field repository was added to object type PullRequestReviewThread
* Field resourcePath was added to object type CommitComment
* Field resourcePath was added to object type ProjectColumn
* Field url was added to object type CommitComment
* Field url was added to object type ProjectColumn
* Field websiteUrl was added to object type Organization
* Type CrossReferencedEvent was added
* Union member CrossReferencedEvent was added to Union type IssueTimelineItem
* Union member CrossReferencedEvent was added to Union type PullRequestTimelineItem
* Project object implements Closable interface

## Schema changes for 2017-08-09

### The following changes were made to the GraphQL schema:

* Field PullRequestReviewComment.originalCommit changed type from Commit! to Commit

## Schema changes for 2017-08-08

### The following changes were made to the GraphQL schema:

* Field Organization.name changed type from String! to String
* Field databaseId was added to object type Deployment
* Field licenseInfo was added to object type RepositoryInfo
* Field licenseInfo was added to object type RepositoryInvitationRepository
* Field licenseInfo was added to object type Repository
* Field license was added to object type Query
* Field licenses was added to object type Query
* Field payload was added to object type Deployment
* Type LicenseRule was added
* Type License was added

## Schema changes for 2017-08-07

### The following changes were made to the GraphQL schema:

* Field contentType was added to object type ReleaseAsset
* Field createdAt was added to object type ReleaseAsset
* Field createdAt was added to object type Team
* Field downloadCount was added to object type ReleaseAsset
* Field size was added to object type ReleaseAsset
* Field updatedAt was added to object type ReleaseAsset
* Field updatedAt was added to object type Team
* Field uploadedBy was added to object type ReleaseAsset

## Schema changes for 2017-08-03

### The following changes were made to the GraphQL schema:

* Field repositoriesContributedTo was removed from object type User
* Field author was added to object type Release
* Field commitComments was added to object type User
* Field createdAt was added to object type Release
* Field isDraft was added to object type Release
* Field isPrerelease was added to object type Release
* Field updatedAt was added to object type Release

## Schema changes for 2017-08-02

### The following changes were made to the GraphQL schema:

* Field commitComments was removed from object type User
* Field repositoriesContributedTo was added to object type User
* Field shortDescriptionHTML was added to object type RepositoryInfo
* Field shortDescriptionHTML was added to object type RepositoryInvitationRepository
* Field shortDescriptionHTML was added to object type Repository

## Schema changes for 2017-08-01

### The following changes were made to the GraphQL schema:

* Field commitComments was added to object type User

## Schema changes for 2017-07-28

### The following changes were made to the GraphQL schema:

* Enum value FIRST\_TIMER was added to enum CommentAuthorAssociation
* Field pullRequest was added to object type IssueComment

## Schema changes for 2017-07-27

### The following changes were made to the GraphQL schema:

* Field CommitComment.commit changed type from Commit! to Commit
* Field databaseId was removed from object type Deployment
* Field payload was removed from object type Deployment
* Argument environments: \[String!] added to field Repository.deployments

## Schema changes for 2017-07-26

### The following changes were made to the GraphQL schema:

* Field databaseId was added to object type Deployment

## Schema changes for 2017-07-25

### The following changes were made to the GraphQL schema:

* Enum value FIRST\_TIMER was removed from enum CommentAuthorAssociation
* Argument orderBy: GistOrder added to field User.gists
* Field payload was added to object type Deployment
* Field pushedAt was added to object type Gist
* Type GistOrderField was added
* Type GistOrder was added

## Schema changes for 2017-07-24

### The following changes were made to the GraphQL schema:

* Enum value FIRST\_TIMER was added to enum CommentAuthorAssociation

## Schema changes for 2017-07-21

### The following changes were made to the GraphQL schema:

* Argument rootTeamsOnly: Boolean added to field Organization.teams
* Field ancestors was added to object type Team
* Field childTeams was added to object type Team
* Field combinedSlug was added to object type Team
* Field membersResourcePath was added to object type Team
* Field membersUrl was added to object type Team
* Field members was added to object type Team
* Field newTeamResourcePath was added to object type Team
* Field newTeamUrl was added to object type Team
* Field parentTeam was added to object type Team
* Field repositoriesResourcePath was added to object type Team
* Field repositoriesUrl was added to object type Team
* Field repositories was added to object type Team
* Field teamsResourcePath was added to object type Team
* Field teamsUrl was added to object type Team
* Field viewerCanAdminister was added to object type Team
* Type RepositoryPermission was added
* Type TeamMemberConnection was added
* Type TeamMemberEdge was added
* Type TeamMemberRole was added
* Type TeamMembershipType was added
* Type TeamRepositoryConnection was added
* Type TeamRepositoryEdge was added
* Type TeamRepositoryOrderField was added
* Type TeamRepositoryOrder was added

## Schema changes for 2017-07-20

### The following changes were made to the GraphQL schema:

* Field Label.pullRequests changed type from PullRequestConnection to PullRequestConnection!
* Field releaseAsset was removed from object type Release
* Argument baseRefName: String added to field Label.pullRequests
* Argument baseRefName: String added to field Ref.associatedPullRequests
* Argument headRefName: String added to field Label.pullRequests
* Argument headRefName: String added to field Ref.associatedPullRequests
* Argument labels: \[String!] added to field Label.pullRequests
* Argument labels: \[String!] added to field Ref.associatedPullRequests
* Argument name: String added to field Release.releaseAssets
* Argument orderBy: IssueOrder added to field Label.pullRequests
* Argument orderBy: IssueOrder added to field Ref.associatedPullRequests
* Argument states: \[PullRequestState!] added to field Label.pullRequests
* Field pinnedRepositories was added to object type Organization
* Field pinnedRepositories was added to object type RepositoryOwner

## Schema changes for 2017-07-19

### The following changes were made to the GraphQL schema:

* Argument rootTeamsOnly: Boolean was removed from field Organization.teams
* ChildTeamDescendants was removed
* Field TreeEntry.object changed type from GitObject! to GitObject
* Field ancestors was removed from object type Team
* Field childTeams was removed from object type Team
* Field combinedSlug was removed from object type Team
* Field membersResourcePath was removed from object type Team
* Field membersUrl was removed from object type Team
* Field members was removed from object type Team
* Field newTeamResourcePath was removed from object type Team
* Field newTeamUrl was removed from object type Team
* Field parentTeam was removed from object type Team
* Field repositoriesResourcePath was removed from object type Team
* Field repositoriesUrl was removed from object type Team
* Field repositories was removed from object type Team
* Field teamsResourcePath was removed from object type Team
* Field teamsUrl was removed from object type Team
* Field viewerCanAdminister was removed from object type Team
* RepositoryPermission was removed
* TeamMemberConnection was removed
* TeamMemberEdge was removed
* TeamMemberRole was removed
* TeamMembershipType was removed
* TeamRepositoryConnection was removed
* TeamRepositoryEdge was removed
* TeamRepositoryOrder was removed
* TeamRepositoryOrderField was removed

## Schema changes for 2017-07-18

### The following changes were made to the GraphQL schema:

* Argument rootTeamsOnly: Boolean added to field Organization.teams
* Field ancestors was added to object type Team
* Field childTeams was added to object type Team
* Field combinedSlug was added to object type Team
* Field membersResourcePath was added to object type Team
* Field membersUrl was added to object type Team
* Field members was added to object type Team
* Field newTeamResourcePath was added to object type Team
* Field newTeamUrl was added to object type Team
* Field parentTeam was added to object type Team
* Field repositoriesResourcePath was added to object type Team
* Field repositoriesUrl was added to object type Team
* Field repositories was added to object type Team
* Field teamsResourcePath was added to object type Team
* Field teamsUrl was added to object type Team
* Field viewerCanAdminister was added to object type Team
* Type ChildTeamDescendants was added
* Type CommitCommentThread was added
* Type RepositoryPermission was added
* Type TeamMemberConnection was added
* Type TeamMemberEdge was added
* Type TeamMemberRole was added
* Type TeamMembershipType was added
* Type TeamRepositoryConnection was added
* Type TeamRepositoryEdge was added
* Type TeamRepositoryOrderField was added
* Type TeamRepositoryOrder was added
* Union member CommitCommentThread was added to Union type PullRequestTimelineItem

## Schema changes for 2017-07-17

### The following changes were made to the GraphQL schema:

* Milestone object implements UniformResourceLocatable interface

## Schema changes for 2017-07-13

### The following changes were made to the GraphQL schema:

* CrossReferencedEvent was removed
* Union member CrossReferencedEvent was removed from Union type IssueTimelineItem

## Schema changes for 2017-07-11

### The following changes were made to the GraphQL schema:

* Argument name: String was removed from field Release.releaseAssets
* Field releaseAsset was added to object type Release
* Type CrossReferencedEvent was added
* Union member CrossReferencedEvent was added to Union type IssueTimelineItem

## Schema changes for 2017-07-10

### The following changes were made to the GraphQL schema:

* CrossReferencedEvent was removed
* Field releaseAsset was removed from object type Release
* Union member CrossReferencedEvent was removed from Union type IssueTimelineItem
* Argument labels: \[String!] added to field Label.issues
* Argument name: String added to field Release.releaseAssets
* Field issues was added to object type User

## Schema changes for 2017-07-07

### The following changes were made to the GraphQL schema:

* Argument labels: \[String!] was removed from field Label.issues
* Field issues was removed from object type User
* Type CrossReferencedEvent was added
* Union member CrossReferencedEvent was added to Union type IssueTimelineItem

## Schema changes for 2017-07-06

### The following changes were made to the GraphQL schema:

* AddTeamMemberInput was removed
* AddTeamMemberPayload was removed
* ChildTeamDescendants was removed
* CreateTeamInput was removed
* CreateTeamPayload was removed
* DeleteTeamInput was removed
* DeleteTeamPayload was removed
* Field addTeamMember was removed from object type Mutation
* Field ancestors was removed from object type Team
* Field childTeams was removed from object type Team
* Field combinedSlug was removed from object type Team
* Field createTeam was removed from object type Mutation
* Field deleteTeam was removed from object type Mutation
* Field membersResourcePath was removed from object type Team
* Field membersUrl was removed from object type Team
* Field members was removed from object type Team
* Field newTeamResourcePath was removed from object type Team
* Field newTeamUrl was removed from object type Team
* Field parentTeam was removed from object type Team
* Field removeTeamMember was removed from object type Mutation
* Field repositoriesResourcePath was removed from object type Team
* Field repositoriesUrl was removed from object type Team
* Field repositories was removed from object type Team
* Field teamsResourcePath was removed from object type Team
* Field teamsUrl was removed from object type Team
* Field updateTeamMember was removed from object type Mutation
* Field updateTeam was removed from object type Mutation
* Field viewerCanAdminister was removed from object type Team
* RemoveTeamMemberInput was removed
* RemoveTeamMemberPayload was removed
* TeamMemberConnection was removed
* TeamMemberEdge was removed
* TeamMembershipType was removed
* TeamRepositoryConnection was removed
* TeamRepositoryEdge was removed
* TeamRepositoryOrder was removed
* TeamRepositoryOrderField was removed
* UpdateTeamInput was removed
* UpdateTeamMemberInput was removed
* UpdateTeamMemberPayload was removed
* UpdateTeamPayload was removed
* Argument labels: \[String!] added to field Label.issues
* Field issues was added to object type User

## Schema changes for 2017-07-05

### The following changes were made to the GraphQL schema:

* Input field RequestReviewsInput.userIds changed type from \[ID!]! to \[ID!]
* Field addTeamMember was added to object type Mutation
* Field ancestors was added to object type Team
* Field childTeams was added to object type Team
* Field combinedSlug was added to object type Team
* Field createTeam was added to object type Mutation
* Field deleteTeam was added to object type Mutation
* Field membersResourcePath was added to object type Team
* Field membersUrl was added to object type Team
* Field members was added to object type Team
* Field newTeamResourcePath was added to object type Team
* Field newTeamUrl was added to object type Team
* Field parentTeam was added to object type Team
* Field removeTeamMember was added to object type Mutation
* Field repositoriesResourcePath was added to object type Team
* Field repositoriesUrl was added to object type Team
* Field repositories was added to object type Team
* Field teamsResourcePath was added to object type Team
* Field teamsUrl was added to object type Team
* Field updateTeamMember was added to object type Mutation
* Field updateTeam was added to object type Mutation
* Field viewerCanAdminister was added to object type Team
* Input field teamIds was added to input object type RequestReviewsInput
* Type AddTeamMemberInput was added
* Type AddTeamMemberPayload was added
* Type AddedToProjectEvent was added
* Type BaseRefChangedEvent was added
* Type ChildTeamDescendants was added
* Type CommentDeletedEvent was added
* Type ConvertedNoteToIssueEvent was added
* Type CreateTeamInput was added
* Type CreateTeamPayload was added
* Type DeleteTeamInput was added
* Type DeleteTeamPayload was added
* Type MentionedEvent was added
* Type MovedColumnsInProjectEvent was added
* Type RemoveTeamMemberInput was added
* Type RemoveTeamMemberPayload was added
* Type RemovedFromProjectEvent was added
* Type TeamMemberConnection was added
* Type TeamMemberEdge was added
* Type TeamMembershipType was added
* Type TeamRepositoryConnection was added
* Type TeamRepositoryEdge was added
* Type TeamRepositoryOrderField was added
* Type TeamRepositoryOrder was added
* Type UpdateTeamInput was added
* Type UpdateTeamMemberInput was added
* Type UpdateTeamMemberPayload was added
* Type UpdateTeamPayload was added

## Schema changes for 2017-07-04

### The following changes were made to the GraphQL schema:

* AddTeamMemberInput was removed
* AddTeamMemberPayload was removed
* ChildTeamDescendants was removed
* CreateTeamInput was removed
* CreateTeamPayload was removed
* DeleteTeamInput was removed
* DeleteTeamPayload was removed
* Field addTeamMember was removed from object type Mutation
* Field ancestors was removed from object type Team
* Field childTeams was removed from object type Team
* Field combinedSlug was removed from object type Team
* Field createTeam was removed from object type Mutation
* Field deleteTeam was removed from object type Mutation
* Field membersResourcePath was removed from object type Team
* Field membersUrl was removed from object type Team
* Field members was removed from object type Team
* Field newTeamResourcePath was removed from object type Team
* Field newTeamUrl was removed from object type Team
* Field parentTeam was removed from object type Team
* Field removeTeamMember was removed from object type Mutation
* Field repositoriesResourcePath was removed from object type Team
* Field repositoriesUrl was removed from object type Team
* Field repositories was removed from object type Team
* Field teamsResourcePath was removed from object type Team
* Field teamsUrl was removed from object type Team
* Field updateTeamMember was removed from object type Mutation
* Field updateTeam was removed from object type Mutation
* Field viewerCanAdminister was removed from object type Team
* MemberOrder was removed
* RemoveTeamMemberInput was removed
* RemoveTeamMemberPayload was removed
* TeamMemberConnection was removed
* TeamMemberEdge was removed
* TeamMembershipType was removed
* TeamRepositoryConnection was removed
* TeamRepositoryEdge was removed
* TeamRepositoryOrder was removed
* TeamRepositoryOrderField was removed
* UpdateTeamInput was removed
* UpdateTeamMemberInput was removed
* UpdateTeamMemberPayload was removed
* UpdateTeamPayload was removed
* UserOrderField was removed

## Schema changes for 2017-07-01

### The following changes were made to the GraphQL schema:

* Input field RequestReviewsInput.userIds changed type from \[ID!] to \[ID!]!
* Input field teamIds was removed from input object type RequestReviewsInput
* Field addTeamMember was added to object type Mutation
* Field ancestors was added to object type Team
* Field childTeams was added to object type Team
* Field combinedSlug was added to object type Team
* Field createTeam was added to object type Mutation
* Field deleteTeam was added to object type Mutation
* Field isCrossRepository was added to object type ReferencedEvent
* Field membersResourcePath was added to object type Team
* Field membersUrl was added to object type Team
* Field members was added to object type Team
* Field newTeamResourcePath was added to object type Team
* Field newTeamUrl was added to object type Team
* Field parentTeam was added to object type Team
* Field removeTeamMember was added to object type Mutation
* Field repositoriesResourcePath was added to object type Team
* Field repositoriesUrl was added to object type Team
* Field repositories was added to object type Team
* Field teamsResourcePath was added to object type Team
* Field teamsUrl was added to object type Team
* Field updateTeamMember was added to object type Mutation
* Field updateTeam was added to object type Mutation
* Field viewerCanAdminister was added to object type Team
* Type AddTeamMemberInput was added
* Type AddTeamMemberPayload was added
* Type ChildTeamDescendants was added
* Type CreateTeamInput was added
* Type CreateTeamPayload was added
* Type DeleteTeamInput was added
* Type DeleteTeamPayload was added
* Type RemoveTeamMemberInput was added
* Type RemoveTeamMemberPayload was added
* Type TeamMemberConnection was added
* Type TeamMemberEdge was added
* Type TeamMembershipType was added
* Type TeamRepositoryConnection was added
* Type TeamRepositoryEdge was added
* Type TeamRepositoryOrderField was added
* Type TeamRepositoryOrder was added
* Type UpdateTeamInput was added
* Type UpdateTeamMemberInput was added
* Type UpdateTeamMemberPayload was added
* Type UpdateTeamPayload was added

## Schema changes for 2017-06-30

### The following changes were made to the GraphQL schema:

* Field isCrossRepository was removed from object type ReferencedEvent
* Input field RequestReviewsInput.userIds changed type from \[ID!]! to \[ID!]
* Input field teamIds was added to input object type RequestReviewsInput

## Schema changes for 2017-06-29

### The following changes were made to the GraphQL schema:

* Field isCrossRepository was added to object type ReferencedEvent
* Field revertResourcePath was added to object type PullRequest
* Field revertUrl was added to object type PullRequest

## Schema changes for 2017-06-28

### The following changes were made to the GraphQL schema:

* Field PullRequestReviewComment.pullRequestReview changed type from PullRequestReview! to PullRequestReview

## Schema changes for 2017-06-27

### The following changes were made to the GraphQL schema:

* Field revertResourcePath was removed from object type MergedEvent
* Field revertUrl was removed from object type MergedEvent

## Schema changes for 2017-06-26

### The following changes were made to the GraphQL schema:

* Field issues was removed from object type User
* Enum value STARGAZERS was added to enum RepositoryOrderField
* Field revertResourcePath was added to object type MergedEvent
* Field revertUrl was added to object type MergedEvent

## Schema changes for 2017-06-25

### The following changes were made to the GraphQL schema:

* Field issues was added to object type User

## Schema changes for 2017-06-23

### The following changes were made to the GraphQL schema:

* Field databaseId was removed from object type AssignedEvent
* Field databaseId was removed from object type BaseRefForcePushedEvent
* Field databaseId was removed from object type ClosedEvent
* Field databaseId was removed from object type DemilestonedEvent
* Field databaseId was removed from object type HeadRefDeletedEvent
* Field databaseId was removed from object type HeadRefForcePushedEvent
* Field databaseId was removed from object type HeadRefRestoredEvent
* Field databaseId was removed from object type LabeledEvent
* Field databaseId was removed from object type LockedEvent
* Field databaseId was removed from object type MergedEvent
* Field databaseId was removed from object type MilestonedEvent
* Field databaseId was removed from object type ReferencedEvent
* Field databaseId was removed from object type RenamedTitleEvent
* Field databaseId was removed from object type ReopenedEvent
* Field databaseId was removed from object type ReviewRequestRemovedEvent
* Field databaseId was removed from object type ReviewRequestedEvent
* Field databaseId was removed from object type SubscribedEvent
* Field databaseId was removed from object type UnassignedEvent
* Field databaseId was removed from object type UnlabeledEvent
* Field databaseId was removed from object type UnlockedEvent
* Field databaseId was removed from object type UnsubscribedEvent
* TimelineEvent was removed
* AssignedEvent object type no longer implements TimelineEvent interface
* BaseRefForcePushedEvent object type no longer implements TimelineEvent interface
* ClosedEvent object type no longer implements TimelineEvent interface
* DemilestonedEvent object type no longer implements TimelineEvent interface
* DeployedEvent object type no longer implements TimelineEvent interface
* HeadRefDeletedEvent object type no longer implements TimelineEvent interface
* HeadRefForcePushedEvent object type no longer implements TimelineEvent interface
* HeadRefRestoredEvent object type no longer implements TimelineEvent interface
* LabeledEvent object type no longer implements TimelineEvent interface
* LockedEvent object type no longer implements TimelineEvent interface
* MergedEvent object type no longer implements TimelineEvent interface
* MilestonedEvent object type no longer implements TimelineEvent interface
* ReferencedEvent object type no longer implements TimelineEvent interface
* RenamedTitleEvent object type no longer implements TimelineEvent interface
* ReopenedEvent object type no longer implements TimelineEvent interface
* ReviewDismissedEvent object type no longer implements TimelineEvent interface
* ReviewRequestRemovedEvent object type no longer implements TimelineEvent interface
* ReviewRequestedEvent object type no longer implements TimelineEvent interface
* SubscribedEvent object type no longer implements TimelineEvent interface
* UnassignedEvent object type no longer implements TimelineEvent interface
* UnlabeledEvent object type no longer implements TimelineEvent interface
* UnlockedEvent object type no longer implements TimelineEvent interface
* UnsubscribedEvent object type no longer implements TimelineEvent interface
* Field resourcePath was added to object type PullRequestReviewComment

## Schema changes for 2017-06-22

### The following changes were made to the GraphQL schema:

* Field databaseId was added to object type AssignedEvent
* Field databaseId was added to object type BaseRefForcePushedEvent
* Field databaseId was added to object type ClosedEvent
* Field databaseId was added to object type DemilestonedEvent
* Field databaseId was added to object type HeadRefDeletedEvent
* Field databaseId was added to object type HeadRefForcePushedEvent
* Field databaseId was added to object type HeadRefRestoredEvent
* Field databaseId was added to object type LabeledEvent
* Field databaseId was added to object type LockedEvent
* Field databaseId was added to object type MergedEvent
* Field databaseId was added to object type MilestonedEvent
* Field databaseId was added to object type ReferencedEvent
* Field databaseId was added to object type RenamedTitleEvent
* Field databaseId was added to object type ReopenedEvent
* Field databaseId was added to object type ReviewRequestRemovedEvent
* Field databaseId was added to object type ReviewRequestedEvent
* Field databaseId was added to object type SubscribedEvent
* Field databaseId was added to object type UnassignedEvent
* Field databaseId was added to object type UnlabeledEvent
* Field databaseId was added to object type UnlockedEvent
* Field databaseId was added to object type UnsubscribedEvent
* Field deployments was added to object type Repository
* Type DeploymentConnection was added
* Type DeploymentEdge was added
* Type TimelineEvent was added
* AssignedEvent object implements TimelineEvent interface
* BaseRefForcePushedEvent object implements TimelineEvent interface
* ClosedEvent object implements TimelineEvent interface
* DemilestonedEvent object implements TimelineEvent interface
* DeployedEvent object implements TimelineEvent interface
* HeadRefDeletedEvent object implements TimelineEvent interface
* HeadRefForcePushedEvent object implements TimelineEvent interface
* HeadRefRestoredEvent object implements TimelineEvent interface
* LabeledEvent object implements TimelineEvent interface
* LockedEvent object implements TimelineEvent interface
* MergedEvent object implements TimelineEvent interface
* MilestonedEvent object implements TimelineEvent interface
* ReferencedEvent object implements TimelineEvent interface
* RenamedTitleEvent object implements TimelineEvent interface
* ReopenedEvent object implements TimelineEvent interface
* ReviewDismissedEvent object implements TimelineEvent interface
* ReviewRequestRemovedEvent object implements TimelineEvent interface
* ReviewRequestedEvent object implements TimelineEvent interface
* SubscribedEvent object implements TimelineEvent interface
* UnassignedEvent object implements TimelineEvent interface
* UnlabeledEvent object implements TimelineEvent interface
* UnlockedEvent object implements TimelineEvent interface
* UnsubscribedEvent object implements TimelineEvent interface

## Schema changes for 2017-06-21

### The following changes were made to the GraphQL schema:

* AddTeamMemberInput was removed
* AddTeamMemberPayload was removed
* ChildTeamDescendants was removed
* CreateTeamInput was removed
* CreateTeamPayload was removed
* DeleteTeamInput was removed
* DeleteTeamPayload was removed
* Field MergedEvent.commit changed type from Commit! to Commit
* Field addTeamMember was removed from object type Mutation
* Field ancestors was removed from object type Team
* Field childTeams was removed from object type Team
* Field combinedSlug was removed from object type Team
* Field createTeam was removed from object type Mutation
* Field deleteTeam was removed from object type Mutation
* Field membersResourcePath was removed from object type Team
* Field membersUrl was removed from object type Team
* Field members was removed from object type Team
* Field newTeamResourcePath was removed from object type Team
* Field newTeamUrl was removed from object type Team
* Field parentTeam was removed from object type Team
* Field removeTeamMember was removed from object type Mutation
* Field repositoriesResourcePath was removed from object type Team
* Field repositoriesUrl was removed from object type Team
* Field repositories was removed from object type Team
* Field teamsResourcePath was removed from object type Team
* Field teamsUrl was removed from object type Team
* Field updateTeamMember was removed from object type Mutation
* Field updateTeam was removed from object type Mutation
* Field viewerCanAdminister was removed from object type Team
* RemoveTeamMemberInput was removed
* RemoveTeamMemberPayload was removed
* TeamMemberConnection was removed
* TeamMemberEdge was removed
* TeamMembershipType was removed
* TeamRepositoryConnection was removed
* TeamRepositoryEdge was removed
* TeamRepositoryOrder was removed
* TeamRepositoryOrderField was removed
* UpdateTeamInput was removed
* UpdateTeamMemberInput was removed
* UpdateTeamMemberPayload was removed
* UpdateTeamPayload was removed
* Field authorAssociation was added to object type Comment
* Field authorAssociation was added to object type CommitComment
* Field authorAssociation was added to object type GistComment
* Field authorAssociation was added to object type IssueComment
* Field authorAssociation was added to object type Issue
* Field authorAssociation was added to object type PullRequestReviewComment
* Field authorAssociation was added to object type PullRequestReview
* Field authorAssociation was added to object type PullRequest
* Field resourcePath was added to object type MergedEvent
* Field url was added to object type MergedEvent
* Type CommentAuthorAssociation was added
* MergedEvent object implements UniformResourceLocatable interface

## Schema changes for 2017-06-20

### The following changes were made to the GraphQL schema:

* Field MergedEvent.commit changed type from Commit to Commit!
* Field resourcePath was removed from object type MergedEvent
* Field url was removed from object type MergedEvent
* MergedEvent object type no longer implements UniformResourceLocatable interface
* Field addTeamMember was added to object type Mutation
* Field ancestors was added to object type Team
* Field childTeams was added to object type Team
* Field combinedSlug was added to object type Team
* Field createTeam was added to object type Mutation
* Field deleteTeam was added to object type Mutation
* Field membersResourcePath was added to object type Team
* Field membersUrl was added to object type Team
* Field members was added to object type Team
* Field newTeamResourcePath was added to object type Team
* Field newTeamUrl was added to object type Team
* Field parentTeam was added to object type Team
* Field removeTeamMember was added to object type Mutation
* Field repositoriesResourcePath was added to object type Team
* Field repositoriesUrl was added to object type Team
* Field repositories was added to object type Team
* Field teamsResourcePath was added to object type Team
* Field teamsUrl was added to object type Team
* Field updateTeamMember was added to object type Mutation
* Field updateTeam was added to object type Mutation
* Field viewerCanAdminister was added to object type Team
* Type AddTeamMemberInput was added
* Type AddTeamMemberPayload was added
* Type ChildTeamDescendants was added
* Type CreateTeamInput was added
* Type CreateTeamPayload was added
* Type DeleteTeamInput was added
* Type DeleteTeamPayload was added
* Type RemoveTeamMemberInput was added
* Type RemoveTeamMemberPayload was added
* Type TeamMemberConnection was added
* Type TeamMemberEdge was added
* Type TeamMembershipType was added
* Type TeamRepositoryConnection was added
* Type TeamRepositoryEdge was added
* Type TeamRepositoryOrderField was added
* Type TeamRepositoryOrder was added
* Type UpdateTeamInput was added
* Type UpdateTeamMemberInput was added
* Type UpdateTeamMemberPayload was added
* Type UpdateTeamPayload was added

## Schema changes for 2017-06-16

### The following changes were made to the GraphQL schema:

* Field MergedEvent.commit changed type from Commit! to Commit
* Field isDirectReference was added to object type ReferencedEvent

## Schema changes for 2017-06-15

### The following changes were made to the GraphQL schema:

* Field resourcePath was added to object type MergedEvent
* Field url was added to object type MergedEvent
* MergedEvent object implements UniformResourceLocatable interface

## Schema changes for 2017-06-14

### The following changes were made to the GraphQL schema:

* Field column was added to object type ProjectCard
* Field project was added to object type ProjectCard
* Field resourcePath was added to object type ProjectCard
* Field url was added to object type ProjectCard

## Schema changes for 2017-06-12

### The following changes were made to the GraphQL schema:

* Field column was removed from object type ProjectCard
* Field project was removed from object type ProjectCard
* Field resourcePath was removed from object type ProjectCard
* Field teamsSearchResourcePath was removed from object type Organization
* Field teamsSearchUrl was removed from object type Organization
* Field url was removed from object type ProjectCard

## Schema changes for 2017-06-09

### The following changes were made to the GraphQL schema:

* Field PullRequest.headRepositoryOwner changed type from RepositoryOwner! to RepositoryOwner
* Enum value HEAD\_REF was added to enum PullRequestPubSubTopic
* Field column was added to object type ProjectCard
* Field isCrossRepository was added to object type PullRequest
* Field project was added to object type ProjectCard
* Field resourcePath was added to object type ProjectCard
* Field url was added to object type ProjectCard

## Schema changes for 2017-06-06

### The following changes were made to the GraphQL schema:

* App was removed
* AppConnection was removed
* AppEdge was removed
* Field viaApp was removed from object type DeployedEvent
* Field viaApp was removed from object type IssueComment
* Field viaApp was removed from object type Issue
* Field viaApp was removed from object type PullRequest
* PerformableViaApp was removed
* DeployedEvent object type no longer implements PerformableViaApp interface
* IssueComment object type no longer implements PerformableViaApp interface
* Issue object type no longer implements PerformableViaApp interface
* PullRequest object type no longer implements PerformableViaApp interface
* Field addTeamMember was added to object type Mutation
* Field ancestors was added to object type Team
* Field childTeams was added to object type Team
* Field combinedSlug was added to object type Team
* Field createTeam was added to object type Mutation
* Field deleteTeam was added to object type Mutation
* Field membersResourcePath was added to object type Team
* Field membersUrl was added to object type Team
* Field members was added to object type Team
* Field newTeamResourcePath was added to object type Team
* Field newTeamUrl was added to object type Team
* Field parentTeam was added to object type Team
* Field removeTeamMember was added to object type Mutation
* Field repositoriesResourcePath was added to object type Team
* Field repositoriesUrl was added to object type Team
* Field repositories was added to object type Team
* Field teamsResourcePath was added to object type Team
* Field teamsUrl was added to object type Team
* Field updateTeamMember was added to object type Mutation
* Field updateTeam was added to object type Mutation
* Field viaIntegration was added to object type DeployedEvent
* Field viaIntegration was added to object type IssueComment
* Field viaIntegration was added to object type Issue
* Field viaIntegration was added to object type PullRequest
* Field viewerCanAdminister was added to object type Team
* Type AddTeamMemberInput was added
* Type AddTeamMemberPayload was added
* Type ChildTeamDescendants was added
* Type CreateTeamInput was added
* Type CreateTeamPayload was added
* Type DeleteTeamInput was added
* Type DeleteTeamPayload was added
* Type IntegrationConnection was added
* Type IntegrationEdge was added
* Type Integration was added
* Type PerformableViaIntegration was added
* Type RemoveTeamMemberInput was added
* Type RemoveTeamMemberPayload was added
* Type TeamMemberConnection was added
* Type TeamMemberEdge was added
* Type TeamMembershipType was added
* Type TeamRepositoryConnection was added
* Type TeamRepositoryEdge was added
* Type TeamRepositoryOrderField was added
* Type TeamRepositoryOrder was added
* Type UpdateTeamInput was added
* Type UpdateTeamMemberInput was added
* Type UpdateTeamMemberPayload was added
* Type UpdateTeamPayload was added
* DeployedEvent object implements PerformableViaIntegration interface
* IssueComment object implements PerformableViaIntegration interface
* Issue object implements PerformableViaIntegration interface
* Organization object implements Actor interface
* PullRequest object implements PerformableViaIntegration interface

## Schema changes for 2017-06-05

### The following changes were made to the GraphQL schema:

* Enum value HEAD\_REF was removed from enum PullRequestPubSubTopic
* Field hasLimitExceeded was removed from object type PullRequestCommitConnection
* Field isCrossRepository was removed from object type PullRequest
* Field viaIntegration was removed from object type DeployedEvent
* Field viaIntegration was removed from object type IssueComment
* Field viaIntegration was removed from object type Issue
* Field viaIntegration was removed from object type PullRequest
* Integration was removed
* IntegrationConnection was removed
* IntegrationEdge was removed
* PerformableViaIntegration was removed
* DeployedEvent object type no longer implements PerformableViaIntegration interface
* IssueComment object type no longer implements PerformableViaIntegration interface
* Issue object type no longer implements PerformableViaIntegration interface
* PullRequest object type no longer implements PerformableViaIntegration interface
* Field viaApp was added to object type DeployedEvent
* Field viaApp was added to object type IssueComment
* Field viaApp was added to object type Issue
* Field viaApp was added to object type PullRequest
* Type AppConnection was added
* Type AppEdge was added
* Type App was added
* Type PerformableViaApp was added
* DeployedEvent object implements PerformableViaApp interface
* IssueComment object implements PerformableViaApp interface
* Issue object implements PerformableViaApp interface
* PullRequest object implements PerformableViaApp interface

## Schema changes for 2017-06-02

### The following changes were made to the GraphQL schema:

* Organization object type no longer implements Actor interface
* Enum value HEAD\_REF was added to enum PullRequestPubSubTopic
* Field hasLimitExceeded was added to object type PullRequestCommitConnection
* Field isCrossRepository was added to object type PullRequest

## Schema changes for 2017-06-01

### The following changes were made to the GraphQL schema:

* Enum value HEAD\_REF was removed from enum PullRequestPubSubTopic
* Field hasLimitExceeded was removed from object type PullRequestCommitConnection
* Field isCrossRepository was removed from object type PullRequest
* Field comments was added to object type Gist
* Type GistCommentConnection was added
* Type GistCommentEdge was added
* Organization object implements Actor interface

## Schema changes for 2017-05-31

### The following changes were made to the GraphQL schema:

* AddTeamMemberInput was removed
* AddTeamMemberPayload was removed
* ChildTeamDescendants was removed
* CreateTeamInput was removed
* CreateTeamPayload was removed
* DeleteTeamInput was removed
* DeleteTeamPayload was removed
* Field addTeamMember was removed from object type Mutation
* Field ancestors was removed from object type Team
* Field childTeams was removed from object type Team
* Field combinedSlug was removed from object type Team
* Field createTeam was removed from object type Mutation
* Field deleteTeam was removed from object type Mutation
* Field membersResourcePath was removed from object type Team
* Field membersUrl was removed from object type Team
* Field members was removed from object type Team
* Field newTeamResourcePath was removed from object type Team
* Field newTeamUrl was removed from object type Team
* Field parentTeam was removed from object type Team
* Field removeTeamMember was removed from object type Mutation
* Field repositoriesResourcePath was removed from object type Team
* Field repositoriesUrl was removed from object type Team
* Field repositories was removed from object type Team
* Field teamsResourcePath was removed from object type Team
* Field teamsUrl was removed from object type Team
* Field updateTeamMember was removed from object type Mutation
* Field updateTeam was removed from object type Mutation
* Field viewerCanAdminister was removed from object type Team
* RemoveTeamMemberInput was removed
* RemoveTeamMemberPayload was removed
* TeamMemberConnection was removed
* TeamMemberEdge was removed
* TeamMembershipType was removed
* TeamRepositoryConnection was removed
* TeamRepositoryEdge was removed
* TeamRepositoryOrder was removed
* TeamRepositoryOrderField was removed
* UpdateTeamInput was removed
* UpdateTeamMemberInput was removed
* UpdateTeamMemberPayload was removed
* UpdateTeamPayload was removed
* Enum value HEAD\_REF was added to enum PullRequestPubSubTopic
* Field hasLimitExceeded was added to object type PullRequestCommitConnection
* Field isCrossRepository was added to object type PullRequest

## Schema changes for 2017-05-30

### The following changes were made to the GraphQL schema:

* Enum value HEAD\_REF was removed from enum PullRequestPubSubTopic
* Field hasLimitExceeded was removed from object type PullRequestCommitConnection
* Field isCrossRepository was removed from object type PullRequest
* Field addTeamMember was added to object type Mutation
* Field ancestors was added to object type Team
* Field childTeams was added to object type Team
* Field combinedSlug was added to object type Team
* Field createTeam was added to object type Mutation
* Field deleteTeam was added to object type Mutation
* Field membersResourcePath was added to object type Team
* Field membersUrl was added to object type Team
* Field members was added to object type Team
* Field newTeamResourcePath was added to object type Team
* Field newTeamUrl was added to object type Team
* Field parentTeam was added to object type Team
* Field removeTeamMember was added to object type Mutation
* Field repositoriesResourcePath was added to object type Team
* Field repositoriesUrl was added to object type Team
* Field repositories was added to object type Team
* Field teamsResourcePath was added to object type Team
* Field teamsUrl was added to object type Team
* Field updateTeamMember was added to object type Mutation
* Field updateTeam was added to object type Mutation
* Field viewerCanAdminister was added to object type Team
* Field viewerCanSubscribe was added to object type Commit
* Field viewerSubscription was added to object type Commit
* Input field commitOID was added to input object type AddPullRequestReviewInput
* Type AddTeamMemberInput was added
* Type AddTeamMemberPayload was added
* Type ChildTeamDescendants was added
* Type CreateTeamInput was added
* Type CreateTeamPayload was added
* Type DeleteTeamInput was added
* Type DeleteTeamPayload was added
* Type RemoveTeamMemberInput was added
* Type RemoveTeamMemberPayload was added
* Type TeamMemberConnection was added
* Type TeamMemberEdge was added
* Type TeamMembershipType was added
* Type TeamRepositoryConnection was added
* Type TeamRepositoryEdge was added
* Type TeamRepositoryOrderField was added
* Type TeamRepositoryOrder was added
* Type UpdateTeamInput was added
* Type UpdateTeamMemberInput was added
* Type UpdateTeamMemberPayload was added
* Type UpdateTeamPayload was added
* Commit object implements Subscribable interface

## Schema changes for 2017-05-26

### The following changes were made to the GraphQL schema:

* AddTeamMemberInput was removed
* AddTeamMemberPayload was removed
* CreateTeamInput was removed
* CreateTeamPayload was removed
* DeleteTeamInput was removed
* DeleteTeamPayload was removed
* Field addTeamMember was removed from object type Mutation
* Field ancestors was removed from object type Team
* Field combinedSlug was removed from object type Team
* Field createTeam was removed from object type Mutation
* Field deleteTeam was removed from object type Mutation
* Field membersResourcePath was removed from object type Team
* Field membersUrl was removed from object type Team
* Field members was removed from object type Team
* Field newTeamResourcePath was removed from object type Team
* Field newTeamUrl was removed from object type Team
* Field parentTeam was removed from object type Team
* Field removeTeamMember was removed from object type Mutation
* Field repositoriesResourcePath was removed from object type Team
* Field repositoriesUrl was removed from object type Team
* Field repositories was removed from object type Team
* Field teamsResourcePath was removed from object type Team
* Field teamsUrl was removed from object type Team
* Field updateTeamMember was removed from object type Mutation
* Field updateTeam was removed from object type Mutation
* Field viewerCanAdminister was removed from object type Team
* RemoveTeamMemberInput was removed
* RemoveTeamMemberPayload was removed
* TeamMemberConnection was removed
* TeamMemberEdge was removed
* TeamMembershipType was removed
* TeamRepositoryConnection was removed
* TeamRepositoryEdge was removed
* TeamRepositoryOrder was removed
* TeamRepositoryOrderField was removed
* UpdateTeamInput was removed
* UpdateTeamMemberInput was removed
* UpdateTeamMemberPayload was removed
* UpdateTeamPayload was removed
* Enum value HEAD\_REF was added to enum PullRequestPubSubTopic
* Field hasLimitExceeded was added to object type PullRequestCommitConnection
* Field isCrossRepository was added to object type PullRequest

## Schema changes for 2017-05-25

### The following changes were made to the GraphQL schema:

* Field membershipRequests was removed from object type Team
* TeamMembershipRequest was removed
* TeamMembershipRequestConnection was removed
* TeamMembershipRequestEdge was removed
* Field repositoriesResourcePath was added to object type Team
* Field repositoriesUrl was added to object type Team

## Schema changes for 2017-05-24

### The following changes were made to the GraphQL schema:

* Field comments was removed from object type Gist
* Field isAuthoredByPusher was removed from object type ReferencedEvent
* Field isDirectReference was removed from object type ReferencedEvent
* Field viewerCanSubscribe was removed from object type Commit
* Field viewerSubscription was removed from object type Commit
* GistCommentConnection was removed
* GistCommentEdge was removed
* Input field commitOID was removed from input object type AddPullRequestReviewInput
* Commit object type no longer implements Subscribable interface
* Organization object type no longer implements Actor interface
* Field addTeamMember was added to object type Mutation
* Field ancestors was added to object type Team
* Field combinedSlug was added to object type Team
* Field createTeam was added to object type Mutation
* Field deleteTeam was added to object type Mutation
* Field membersResourcePath was added to object type Team
* Field membersUrl was added to object type Team
* Field members was added to object type Team
* Field membershipRequests was added to object type Team
* Field newTeamResourcePath was added to object type Team
* Field newTeamUrl was added to object type Team
* Field parentTeam was added to object type Team
* Field removeTeamMember was added to object type Mutation
* Field repositories was added to object type Team
* Field teamsResourcePath was added to object type Team
* Field teamsUrl was added to object type Team
* Field updateTeamMember was added to object type Mutation
* Field updateTeam was added to object type Mutation
* Field viewerCanAdminister was added to object type Team
* Type AddTeamMemberInput was added
* Type AddTeamMemberPayload was added
* Type CreateTeamInput was added
* Type CreateTeamPayload was added
* Type DeleteTeamInput was added
* Type DeleteTeamPayload was added
* Type RemoveTeamMemberInput was added
* Type RemoveTeamMemberPayload was added
* Type TeamMemberConnection was added
* Type TeamMemberEdge was added
* Type TeamMembershipRequestConnection was added
* Type TeamMembershipRequestEdge was added
* Type TeamMembershipRequest was added
* Type TeamMembershipType was added
* Type TeamRepositoryConnection was added
* Type TeamRepositoryEdge was added
* Type TeamRepositoryOrderField was added
* Type TeamRepositoryOrder was added
* Type UpdateTeamInput was added
* Type UpdateTeamMemberInput was added
* Type UpdateTeamMemberPayload was added
* Type UpdateTeamPayload was added

## Schema changes for 2017-05-23

### The following changes were made to the GraphQL schema:

* Field comments was added to object type Gist
* Field isAuthoredByPusher was added to object type ReferencedEvent
* Field isDirectReference was added to object type ReferencedEvent
* Field organization was added to object type Team
* Field viewerCanSubscribe was added to object type Commit
* Field viewerSubscription was added to object type Commit
* Input field commitOID was added to input object type AddPullRequestReviewInput
* Type GistCommentConnection was added
* Type GistCommentEdge was added
* Commit object implements Subscribable interface
* Organization object implements Actor interface

## Schema changes for 2017-05-22

### The following changes were made to the GraphQL schema:

* Nothing! The schema was made public!