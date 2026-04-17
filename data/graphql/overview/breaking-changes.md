# Breaking changes

Learn about recent and upcoming breaking changes to the GitHub GraphQL API.

## About breaking changes

Breaking changes are any changes that might require action from our integrators. We divide these changes into two categories:

* **Breaking:** Changes that will break existing queries to the GraphQL API. For example, removing a field would be a breaking change.
* **Dangerous:** Changes that won't break existing queries but could affect the runtime behavior of clients. Adding an enum value is an example of a dangerous change.

We'll announce upcoming breaking changes at least three months before making changes to the GraphQL schema, to give integrators time to make the necessary adjustments. Changes go into effect on the first day of a quarter (January 1st, April 1st, July 1st, or October 1st). For example, if we announce a change on January 15th, it will be made on July 1st.


## Changes scheduled for 2027-01-01


- **Breaking** A change will be made to `CheckAnnotation.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.


- **Breaking** A change will be made to `Artifact.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.



## Changes scheduled for 2026-07-01


- **Breaking** A change will be made to `Team.viewerSubscription`.

  **Description:** viewerSubscription will be removed.

  **Reason:** Team.viewerSubscription will be removed. Team notifications subscriptions are being deprecated.


- **Breaking** A change will be made to `Team.viewerCanSubscribe`.

  **Description:** viewerCanSubscribe will be removed.

  **Reason:** Team.viewerCanSubscribe will be removed. Team notifications subscriptions are being deprecated.



## Changes scheduled for 2026-04-01


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.isLdapMapped`.

  **Description:** isLdapMapped will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveRepositoryAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.isLdapMapped`.

  **Description:** isLdapMapped will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamRemoveMemberAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.parentTeamWasUrl`.

  **Description:** parentTeamWasUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.parentTeamWasResourcePath`.

  **Description:** parentTeamWasResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.parentTeamWas`.

  **Description:** parentTeamWas will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.parentTeamUrl`.

  **Description:** parentTeamUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.parentTeamResourcePath`.

  **Description:** parentTeamResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.parentTeamNameWas`.

  **Description:** parentTeamNameWas will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.parentTeamName`.

  **Description:** parentTeamName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.parentTeam`.

  **Description:** parentTeam will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.isLdapMapped`.

  **Description:** isLdapMapped will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamChangeParentTeamAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.isLdapMapped`.

  **Description:** isLdapMapped will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddRepositoryAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.isLdapMapped`.

  **Description:** isLdapMapped will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `TeamAddMemberAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `ReviewRequest.requestedBy`.

  **Description:** requestedBy will be removed. Use requestedByActor instead.

  **Reason:** requestedBy will be removed.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeEnableAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepositoryVisibilityChangeDisableAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveTopicAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.visibility`.

  **Description:** visibility will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoRemoveMemberAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.visibility`.

  **Description:** visibility will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoDestroyAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.visibility`.

  **Description:** visibility will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.forkSourceName`.

  **Description:** forkSourceName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.forkParentName`.

  **Description:** forkParentName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoCreateAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigUnlockAnonymousGitAccessAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigLockAnonymousGitAccessAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableSockpuppetDisallowedAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableContributorsOnlyAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableCollaboratorsOnlyAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigEnableAnonymousGitAccessAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableSockpuppetDisallowedAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableContributorsOnlyAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableCollaboratorsOnlyAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoConfigDisableAnonymousGitAccessAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.mergeType`.

  **Description:** mergeType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.isEnabled`.

  **Description:** isEnabled will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoChangeMergeSettingAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.visibility`.

  **Description:** visibility will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoArchivedAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddTopicAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.visibility`.

  **Description:** visibility will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAddMemberAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.visibility`.

  **Description:** visibility will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `RepoAccessAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingEnableAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `PrivateRepositoryForkingDisableAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrganizationAuditEntryData.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrganizationAuditEntryData.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrganizationAuditEntryData.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrganizationAuditEntryData.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `Organization.auditLog`.

  **Description:** auditLog will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.canInviteOutsideCollaboratorsToRepositories`.

  **Description:** canInviteOutsideCollaboratorsToRepositories will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryInvitationPermissionAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.visibility`.

  **Description:** visibility will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.canCreateRepositories`.

  **Description:** canCreateRepositories will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberRepositoryCreationPermissionAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.permissionWas`.

  **Description:** permissionWas will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.permission`.

  **Description:** permission will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateMemberAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.permissionWas`.

  **Description:** permissionWas will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.permission`.

  **Description:** permission will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUpdateDefaultRepositoryPermissionAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.blockedUserUrl`.

  **Description:** blockedUserUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.blockedUserResourcePath`.

  **Description:** blockedUserResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.blockedUserName`.

  **Description:** blockedUserName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.blockedUser`.

  **Description:** blockedUser will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgUnblockUserAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberMembershipOrganizationAuditEntryData.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberMembershipOrganizationAuditEntryData.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberMembershipOrganizationAuditEntryData.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberMembershipOrganizationAuditEntryData.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.restoredRepositoryWatchesCount`.

  **Description:** restoredRepositoryWatchesCount will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.restoredRepositoryStarsCount`.

  **Description:** restoredRepositoryStarsCount will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.restoredRepositoriesCount`.

  **Description:** restoredRepositoriesCount will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.restoredMembershipsCount`.

  **Description:** restoredMembershipsCount will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.restoredMemberships`.

  **Description:** restoredMemberships will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.restoredIssueAssignmentsCount`.

  **Description:** restoredIssueAssignmentsCount will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.restoredCustomEmailRoutingsCount`.

  **Description:** restoredCustomEmailRoutingsCount will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRestoreMemberAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.reason`.

  **Description:** reason will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.membershipTypes`.

  **Description:** membershipTypes will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveOutsideCollaboratorAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.reason`.

  **Description:** reason will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.membershipTypes`.

  **Description:** membershipTypes will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveMemberAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.reason`.

  **Description:** reason will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgRemoveBillingManagerAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessUnblockedAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessRequestedAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessDeniedAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessBlockedAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgOauthAppAccessApprovedAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteToBusinessAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.organizationInvitation`.

  **Description:** organizationInvitation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.email`.

  **Description:** email will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgInviteMemberAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableTwoFactorRequirementAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.singleSignOnUrl`.

  **Description:** singleSignOnUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.signatureMethodUrl`.

  **Description:** signatureMethodUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.issuerUrl`.

  **Description:** issuerUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.digestMethodUrl`.

  **Description:** digestMethodUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableSamlAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgEnableOauthAppRestrictionsAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableTwoFactorRequirementAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.singleSignOnUrl`.

  **Description:** singleSignOnUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.signatureMethodUrl`.

  **Description:** signatureMethodUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.issuerUrl`.

  **Description:** issuerUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.digestMethodUrl`.

  **Description:** digestMethodUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableSamlAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgDisableOauthAppRestrictionsAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.billingPlan`.

  **Description:** billingPlan will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgCreateAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigEnableCollaboratorsOnlyAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgConfigDisableCollaboratorsOnlyAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.blockedUserUrl`.

  **Description:** blockedUserUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.blockedUserResourcePath`.

  **Description:** blockedUserResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.blockedUserName`.

  **Description:** blockedUserName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.blockedUser`.

  **Description:** blockedUser will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgBlockUserAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.permission`.

  **Description:** permission will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddMemberAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.invitationEmail`.

  **Description:** invitationEmail will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OrgAddBillingManagerAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.state`.

  **Description:** state will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.rateLimit`.

  **Description:** rateLimit will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.callbackUrl`.

  **Description:** callbackUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.applicationUrl`.

  **Description:** applicationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `OauthApplicationCreateAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposEnableAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposDisableAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.organizationUrl`.

  **Description:** organizationUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.organizationResourcePath`.

  **Description:** organizationResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.organizationName`.

  **Description:** organizationName will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.organization`.

  **Description:** organization will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `MembersCanDeleteReposClearAuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.userUrl`.

  **Description:** userUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.userResourcePath`.

  **Description:** userResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.userLogin`.

  **Description:** userLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.user`.

  **Description:** user will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.operationType`.

  **Description:** operationType will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.actorUrl`.

  **Description:** actorUrl will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.actorResourcePath`.

  **Description:** actorResourcePath will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.actorLogin`.

  **Description:** actorLogin will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.actorLocation`.

  **Description:** actorLocation will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.actorIp`.

  **Description:** actorIp will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.actor`.

  **Description:** actor will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.


- **Breaking** A change will be made to `AuditEntry.action`.

  **Description:** action will be removed.

  **Reason:** The GraphQL audit-log is deprecated. Please use the REST API instead.



## Changes scheduled for 2026-01-01


- **Breaking** A change will be made to `NotificationThread.subject`.

  **Description:** subject will be removed. Use the optionalSubject field instead.

  **Reason:** Null values are possible for this field.


- **Breaking** A change will be made to `NotificationThread.list`.

  **Description:** list will be removed. Use the optionalList field instead.

  **Reason:** Null values are possible for this field.



## Changes scheduled for 2025-10-01


- **Breaking** A change will be made to `SecurityAdvisory.cvss`.

  **Description:** cvss will be removed. New cvss_severities field will now contain both cvss_v3 and cvss_v4 properties.

  **Reason:** cvss will be removed.


- **Breaking** A change will be made to `Issue.stateReason.enableDuplicate`.

  **Description:** enableDuplicate will be removed.

  **Reason:** The state reason for duplicate issue is now returned by default.



## Changes scheduled for 2025-04-01


- **Breaking** A change will be made to `User.viewerCanCreateProjects`.

  **Description:** viewerCanCreateProjects will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `User.projects`.

  **Description:** projects will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `User.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `SearchShortcutQueryProjectTerm.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Repository.viewerCanCreateProjects`.

  **Description:** viewerCanCreateProjects will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Repository.projects`.

  **Description:** projects will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Repository.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `RemovedFromProjectEvent.projectColumnName`.

  **Description:** projectColumnName will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `RemovedFromProjectEvent.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `RemovedFromProjectEvent.databaseId`.

  **Description:** databaseId will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `PullRequest.projectCards`.

  **Description:** projectCards will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectV2Workflow.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.


- **Breaking** A change will be made to `ProjectV2View.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.


- **Breaking** A change will be made to `ProjectV2StatusUpdate.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.


- **Breaking** A change will be made to `ProjectV2Item.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.


- **Breaking** A change will be made to `ProjectV2.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.


- **Breaking** A change will be made to `ProjectProgress.todoPercentage`.

  **Description:** todoPercentage will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectProgress.todoCount`.

  **Description:** todoCount will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectProgress.inProgressPercentage`.

  **Description:** inProgressPercentage will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectProgress.inProgressCount`.

  **Description:** inProgressCount will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectProgress.enabled`.

  **Description:** enabled will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectProgress.donePercentage`.

  **Description:** donePercentage will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectProgress.doneCount`.

  **Description:** doneCount will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectOwner.viewerCanCreateProjects`.

  **Description:** viewerCanCreateProjects will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectOwner.projectsUrl`.

  **Description:** projectsUrl will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectOwner.projectsResourcePath`.

  **Description:** projectsResourcePath will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectOwner.projects`.

  **Description:** projects will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectOwner.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectOwner.id`.

  **Description:** id will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.url`.

  **Description:** url will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.updatedAt`.

  **Description:** updatedAt will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.resourcePath`.

  **Description:** resourcePath will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.purpose`.

  **Description:** purpose will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.name`.

  **Description:** name will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.id`.

  **Description:** id will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.databaseId`.

  **Description:** databaseId will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectColumn.cards`.

  **Description:** cards will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCardArchivedState.NOT_ARCHIVED`.

  **Description:** NOT_ARCHIVED will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCardArchivedState.ARCHIVED`.

  **Description:** ARCHIVED will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.url`.

  **Description:** url will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.updatedAt`.

  **Description:** updatedAt will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.state`.

  **Description:** state will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.resourcePath`.

  **Description:** resourcePath will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.note`.

  **Description:** note will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.isArchived`.

  **Description:** isArchived will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.id`.

  **Description:** id will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.databaseId`.

  **Description:** databaseId will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.creator`.

  **Description:** creator will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.content`.

  **Description:** content will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ProjectCard.column`.

  **Description:** column will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.url`.

  **Description:** url will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.updatedAt`.

  **Description:** updatedAt will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.state`.

  **Description:** state will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.resourcePath`.

  **Description:** resourcePath will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.progress`.

  **Description:** progress will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.pendingCards`.

  **Description:** pendingCards will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.owner`.

  **Description:** owner will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.number`.

  **Description:** number will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.name`.

  **Description:** name will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.id`.

  **Description:** id will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.databaseId`.

  **Description:** databaseId will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.creator`.

  **Description:** creator will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.createdAt`.

  **Description:** createdAt will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.columns`.

  **Description:** columns will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.bodyHTML`.

  **Description:** bodyHtml will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Project.body`.

  **Description:** body will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Organization.viewerCanCreateProjects`.

  **Description:** viewerCanCreateProjects will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Organization.projects`.

  **Description:** projects will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Organization.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.updateProjectColumn`.

  **Description:** updateProjectColumn will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.updateProjectCard`.

  **Description:** updateProjectCard will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.updateProject`.

  **Description:** updateProject will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.unlinkRepositoryFromProject`.

  **Description:** unlinkRepositoryFromProject will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.moveProjectColumn`.

  **Description:** moveProjectColumn will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.moveProjectCard`.

  **Description:** moveProjectCard will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.linkRepositoryToProject`.

  **Description:** linkRepositoryToProject will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.importProject`.

  **Description:** importProject will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.deleteProjectColumn`.

  **Description:** deleteProjectColumn will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.deleteProjectCard`.

  **Description:** deleteProjectCard will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.deleteProject`.

  **Description:** deleteProject will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.createProject`.

  **Description:** createProject will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.convertProjectCardNoteToIssue`.

  **Description:** convertProjectCardNoteToIssue will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.cloneProject`.

  **Description:** cloneProject will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.addProjectColumn`.

  **Description:** addProjectColumn will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `Mutation.addProjectCard`.

  **Description:** addProjectCard will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `MovedColumnsInProjectEvent.projectColumnName`.

  **Description:** projectColumnName will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `MovedColumnsInProjectEvent.projectCard`.

  **Description:** projectCard will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `MovedColumnsInProjectEvent.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `MovedColumnsInProjectEvent.previousProjectColumnName`.

  **Description:** previousProjectColumnName will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `MovedColumnsInProjectEvent.databaseId`.

  **Description:** databaseId will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `IssueType.isPrivate`.

  **Description:** isPrivate will be removed.

  **Reason:** Private issue types are being deprecated and can no longer be created.


- **Breaking** A change will be made to `Issue.projectCards`.

  **Description:** projectCards will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `EnterpriseOwnerInfo.outsideCollaborators.hasTwoFactorEnabled`.

  **Description:** hasTwoFactorEnabled will be removed. Use two_factor_method_security instead.

  **Reason:** has_two_factor_enabled will be removed.


- **Breaking** A change will be made to `EnterpriseOwnerInfo.admins.hasTwoFactorEnabled`.

  **Description:** hasTwoFactorEnabled will be removed. Use two_factor_method_security instead.

  **Reason:** has_two_factor_enabled will be removed.


- **Breaking** A change will be made to `Enterprise.members.hasTwoFactorEnabled`.

  **Description:** hasTwoFactorEnabled will be removed. Use two_factor_method_security instead.

  **Reason:** has_two_factor_enabled will be removed.


- **Breaking** A change will be made to `ConvertedNoteToIssueEvent.projectCard`.

  **Description:** projectCard will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `ConvertedNoteToIssueEvent.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `AddedToProjectEvent.projectColumnName`.

  **Description:** projectColumnName will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `AddedToProjectEvent.projectCard`.

  **Description:** projectCard will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `AddedToProjectEvent.project`.

  **Description:** project will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.


- **Breaking** A change will be made to `AddedToProjectEvent.databaseId`.

  **Description:** databaseId will be removed.

  **Reason:** Projects (classic) is being deprecated in favor of the new Projects experience, see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.



## Changes scheduled for 2025-01-01


- **Breaking** A change will be made to `AddMobileDevicePublicKeyPayload.expiresAt`.

  **Description:** expiresAt will be removed. Do not rely on this field, it is currently set to a date far in the future if a device key is expirationless

  **Reason:** We are deprecating expirations for mobile device keys used in mobile 2FA



## Changes scheduled for 2024-10-01


- **Breaking** A change will be made to `Workflow.hasWorkflowDispatchTrigger`.

  **Description:** hasWorkflowDispatchTrigger will be removed. Use has_workflow_dispatch_trigger_for_branch(branch_ref) instead.

  **Reason:** has_workflow_dispatch_trigger is being removed because it can be misleading and only checks a repository's default branch



## Changes scheduled for 2024-07-01


- **Breaking** A change will be made to `PullRequestReviewComment.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.


- **Breaking** A change will be made to `PullRequestReview.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.


- **Breaking** A change will be made to `PullRequest.databaseId`.

  **Description:** databaseId will be removed. Use fullDatabaseId instead.

  **Reason:** databaseId will be removed because it does not support 64-bit signed integer identifiers.


- **Breaking** A change will be made to `OrganizationInvitation.inviter`.

  **Description:** inviter will be removed. inviter will be replaced by inviterActor.

  **Reason:** inviter will be removed.


- **Breaking** A change will be made to `EnterpriseOwnerInfo.teamDiscussionsSetting`.

  **Description:** teamDiscussionsSetting will be removed. Follow the guide at https://github.blog/changelog/2023-02-08-sunset-notice-team-discussions/ to find a suitable replacement.

  **Reason:** The Team Discussions feature is deprecated in favor of Organization Discussions.



## Changes scheduled for 2024-04-01


- **Breaking** A change will be made to `TopicSuggestionDeclineReason.TOO_SPECIFIC`.

  **Description:** TOO_SPECIFIC will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `TopicSuggestionDeclineReason.TOO_GENERAL`.

  **Description:** TOO_GENERAL will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `TopicSuggestionDeclineReason.PERSONAL_PREFERENCE`.

  **Description:** PERSONAL_PREFERENCE will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `TopicSuggestionDeclineReason.NOT_RELEVANT`.

  **Description:** NOT_RELEVANT will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `DeclineTopicSuggestionPayload.topic`.

  **Description:** topic will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `DeclineTopicSuggestionInput.repositoryId`.

  **Description:** repositoryId will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `DeclineTopicSuggestionInput.reason`.

  **Description:** reason will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `DeclineTopicSuggestionInput.name`.

  **Description:** name will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `AcceptTopicSuggestionPayload.topic`.

  **Description:** topic will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `AcceptTopicSuggestionInput.repositoryId`.

  **Description:** repositoryId will be removed.

  **Reason:** Suggested topics are no longer supported


- **Breaking** A change will be made to `AcceptTopicSuggestionInput.name`.

  **Description:** name will be removed.

  **Reason:** Suggested topics are no longer supported



## Changes scheduled for 2023-10-01


- **Breaking** A change will be made to `PullRequestReviewComment.position`.

  **Description:** position will be removed. Use the line and startLine fields instead, which are file line numbers instead of diff line numbers

  **Reason:** We are phasing out diff-relative positioning for PR comments


- **Breaking** A change will be made to `PullRequestReviewComment.originalPosition`.

  **Description:** originalPosition will be removed.

  **Reason:** We are phasing out diff-relative positioning for PR comments


- **Breaking** A change will be made to `AddPullRequestReviewInput.comments`.

  **Description:** comments will be removed. use the threads argument instead

  **Reason:** We are deprecating comment fields that use diff-relative positioning


- **Breaking** A change will be made to `AddPullRequestReviewCommentInput.pullRequestReviewId`.

  **Description:** pullRequestReviewId will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead

  **Reason:** We are deprecating the addPullRequestReviewComment mutation


- **Breaking** A change will be made to `AddPullRequestReviewCommentInput.pullRequestId`.

  **Description:** pullRequestId will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead

  **Reason:** We are deprecating the addPullRequestReviewComment mutation


- **Breaking** A change will be made to `AddPullRequestReviewCommentInput.position`.

  **Description:** position will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead

  **Reason:** We are deprecating the addPullRequestReviewComment mutation


- **Breaking** A change will be made to `AddPullRequestReviewCommentInput.path`.

  **Description:** path will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead

  **Reason:** We are deprecating the addPullRequestReviewComment mutation


- **Breaking** A change will be made to `AddPullRequestReviewCommentInput.inReplyTo`.

  **Description:** inReplyTo will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead

  **Reason:** We are deprecating the addPullRequestReviewComment mutation


- **Breaking** A change will be made to `AddPullRequestReviewCommentInput.commitOID`.

  **Description:** commitOID will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead

  **Reason:** We are deprecating the addPullRequestReviewComment mutation


- **Breaking** A change will be made to `AddPullRequestReviewCommentInput.body`.

  **Description:** body will be removed. use addPullRequestReviewThread or addPullRequestReviewThreadReply instead

  **Reason:** We are deprecating the addPullRequestReviewComment mutation



## Changes scheduled for 2023-07-01


- **Breaking** A change will be made to `ProjectV2ItemFieldGroup.field`.

  **Description:** field will be removed. Check out the ProjectV2ItemFieldGroup#groupByField API as an example for the more capable alternative.

  **Reason:** The ProjectV2ItemFieldGroup#field API is deprecated in favour of the more capable ProjectV2ItemFieldGroup#groupByField API.


- **Breaking** A change will be made to `MergeQueueEntry.isSolo`.

  **Description:** isSolo will be removed. Use solo instead.

  **Reason:** isSolo will be removed.


- **Breaking** A change will be made to `MergeQueueEntry.headOid`.

  **Description:** headOid will be removed. Use headCommit instead.

  **Reason:** headOid will be removed.


- **Breaking** A change will be made to `MergeQueueEntry.hasJumpedQueue`.

  **Description:** hasJumpedQueue will be removed. Use jump instead.

  **Reason:** hasJumpedQueue will be removed.


- **Breaking** A change will be made to `MergeQueueEntry.checkStatus`.

  **Description:** checkStatus will be removed. Use state instead.

  **Reason:** checkStatus will be removed.


- **Breaking** A change will be made to `MergeQueueEntry.blockedByMergeConflicts`.

  **Description:** blockedByMergeConflicts will be removed. Use state instead.

  **Reason:** blockedByMergeConflicts will be removed.


- **Breaking** A change will be made to `MergeQueueEntry.baseOid`.

  **Description:** baseOid will be removed. Use baseCommit instead.

  **Reason:** baseOid will be removed.


- **Breaking** A change will be made to `MergeQueue.pendingRemovalEntries`.

  **Description:** pendingRemovalEntries will be removed.

  **Reason:** pendingRemovalEntries will be removed.


- **Breaking** A change will be made to `MergeQueue.mergingEntries`.

  **Description:** mergingEntries will be removed.

  **Reason:** mergingEntries will be removed.


- **Breaking** A change will be made to `MergeQueue.mergeMethod`.

  **Description:** mergeMethod will be removed. Use configuration.merge_method instead.

  **Reason:** mergeMethod will be removed.


- **Breaking** A change will be made to `MergeQueue.headOid`.

  **Description:** headOid will be removed. Use entry.headOid instead.

  **Reason:** headOid will be removed.


- **Breaking** A change will be made to `Commit.pushedDate`.

  **Description:** pushedDate will be removed.

  **Reason:** pushedDate is no longer supported.



## Changes scheduled for 2023-04-01


- **Breaking** A change will be made to `Repository.squashPrTitleUsedAsDefault`.

  **Description:** squashPrTitleUsedAsDefault will be removed. Use Repository.squashMergeCommitTitle instead.

  **Reason:** squashPrTitleUsedAsDefault will be removed.


- **Breaking** A change will be made to `ProjectV2View.verticalGroupBy`.

  **Description:** verticalGroupBy will be removed. Check out the ProjectV2View#vertical_group_by_fields API as an example for the more capable alternative.

  **Reason:** The ProjectV2View#vertical_group_by API is deprecated in favour of the more capable ProjectV2View#vertical_group_by_fields API.


- **Breaking** A change will be made to `ProjectV2View.sortBy`.

  **Description:** sortBy will be removed. Check out the ProjectV2View#sort_by_fields API as an example for the more capable alternative.

  **Reason:** The ProjectV2View#sort_by API is deprecated in favour of the more capable ProjectV2View#sort_by_fields API.


- **Breaking** A change will be made to `ProjectV2View.groupBy`.

  **Description:** groupBy will be removed. Check out the ProjectV2View#group_by_fields API as an example for the more capable alternative.

  **Reason:** The ProjectV2View#order_by API is deprecated in favour of the more capable ProjectV2View#group_by_field API.



## Changes scheduled for 2023-02-10


- **Breaking** A change will be made to `PackageType.MAVEN`.

  **Description:** MAVEN will be removed.

  **Reason:** MAVEN will be removed from this enum as this type will be migrated to only be used by the Packages REST API.



## Changes scheduled for 2023-01-01


- **Breaking** A change will be made to `ProjectV2View.visibleFields`.

  **Description:** visibleFields will be removed. Check out the ProjectV2View#fields API as an example for the more capable alternative.

  **Reason:** The ProjectV2View#visibleFields API is deprecated in favour of the more capable ProjectV2View#fields API.


- **Breaking** A change will be made to `Commit.changedFiles`.

  **Description:** changedFiles will be removed. Use changedFilesIfAvailable instead.

  **Reason:** changedFiles will be removed.



## Changes scheduled for 2022-12-28


- **Breaking** A change will be made to `PackageType.RUBYGEMS`.

  **Description:** RUBYGEMS will be removed.

  **Reason:** RUBYGEMS will be removed from this enum as this type will be migrated to only be used by the Packages REST API.



## Changes scheduled for 2022-11-21


- **Breaking** A change will be made to `PackageType.NUGET`.

  **Description:** NUGET will be removed.

  **Reason:** NUGET will be removed from this enum as this type will be migrated to only be used by the Packages REST API.


- **Breaking** A change will be made to `PackageType.NPM`.

  **Description:** NPM will be removed.

  **Reason:** NPM will be removed from this enum as this type will be migrated to only be used by the Packages REST API.



## Changes scheduled for 2022-10-01


- **Breaking** A change will be made to `RemovePullRequestFromMergeQueueInput.branch`.

  **Description:** branch will be removed.

  **Reason:** PRs are removed from the merge queue for the base branch, the branch argument is now a no-op


- **Breaking** A change will be made to `DependencyGraphDependency.packageLabel`.

  **Description:** packageLabel will be removed. Use normalized packageName field instead.

  **Reason:** packageLabel will be removed.



## Changes scheduled for 2022-07-01


- **Breaking** A change will be made to `Query.sponsorables.dependencyEcosystem`.

  **Description:** dependencyEcosystem will be removed. Use the ecosystem argument instead.

  **Reason:** The type is switching from SecurityAdvisoryEcosystem to DependencyGraphEcosystem.


- **Breaking** A change will be made to `AddPullRequestToMergeQueueInput.branch`.

  **Description:** branch will be removed.

  **Reason:** PRs are added to the merge queue for the base branch, the branch argument is now a no-op



## Changes scheduled for 2021-10-01


- **Breaking** A change will be made to `ReactionGroup.users`.

  **Description:** users will be removed. Use the reactors field instead.

  **Reason:** Reactors can now be mannequins, bots, and organizations.



## Changes scheduled for 2021-06-21


- **Breaking** A change will be made to `PackageType.DOCKER`.

  **Description:** DOCKER will be removed.

  **Reason:** DOCKER will be removed from this enum as this type will be migrated to only be used by the Packages REST API.



## Changes scheduled for 2021-01-01


- **Breaking** A change will be made to `MergeStateStatus.DRAFT`.

  **Description:** DRAFT will be removed. Use PullRequest.isDraft instead.

  **Reason:** DRAFT state will be removed from this enum and isDraft should be used instead



## Changes scheduled for 2020-10-01


- **Breaking** A change will be made to `Sponsorship.sponsor`.

  **Description:** sponsor will be removed. Use Sponsorship.sponsorEntity instead.

  **Reason:** Sponsorship.sponsor will be removed.


- **Breaking** A change will be made to `PullRequest.timeline`.

  **Description:** timeline will be removed. Use PullRequest.timelineItems instead.

  **Reason:** timeline will be removed


- **Breaking** A change will be made to `Issue.timeline`.

  **Description:** timeline will be removed. Use Issue.timelineItems instead.

  **Reason:** timeline will be removed



## Changes scheduled for 2020-04-01


- **Breaking** A change will be made to `Sponsorship.maintainer`.

  **Description:** maintainer will be removed. Use Sponsorship.sponsorable instead.

  **Reason:** Sponsorship.maintainer will be removed.



## Changes scheduled for 2020-01-01


- **Breaking** A change will be made to `UnassignedEvent.user`.

  **Description:** user will be removed. Use the assignee field instead.

  **Reason:** Assignees can now be mannequins.


- **Breaking** A change will be made to `AssignedEvent.user`.

  **Description:** user will be removed. Use the assignee field instead.

  **Reason:** Assignees can now be mannequins.



## Changes scheduled for 2019-04-01


- **Breaking** A change will be made to `LegacyMigration.uploadUrlTemplate`.

  **Description:** uploadUrlTemplate will be removed. Use uploadUrl instead.

  **Reason:** uploadUrlTemplate is being removed because it is not a standard URL and adds an extra user step.