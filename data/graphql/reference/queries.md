# Queries

The query type defines GraphQL operations that retrieve data from the server.

## About queries

Every GraphQL schema has a root type for both queries and mutations. The [query type](https://spec.graphql.org/June2018/#sec-Type-System) defines GraphQL operations that retrieve data from the server.

For more information, see [Forming calls with GraphQL](/en/graphql/guides/forming-calls-with-graphql#about-queries).

> \[!NOTE]
> For GitHub App requests made with user access tokens, you should use separate queries for issues and pull requests. For example, use the `is:issue` or `is:pull-request` filters and their equivalents. Using the `search` connection to return a combination of issues and pull requests in a single query will result in an empty set of nodes.

## codeOfConduct

Look up a code of conduct by its key.

**Type:** CodeOfConduct

### Arguments for `codeOfConduct`

* `key` (String!): The code of conduct's key.

## codesOfConduct

Look up a code of conduct by its key.

**Type:** \[CodeOfConduct]

## enterprise

Look up an enterprise by URL slug.

**Type:** Enterprise

### Arguments for `enterprise`

* `invitationToken` (String): The enterprise invitation token.
* `slug` (String!): The enterprise URL slug.

## enterpriseAdministratorInvitation

Look up a pending enterprise administrator invitation by invitee, enterprise and role.

**Type:** EnterpriseAdministratorInvitation

### Arguments for `enterpriseAdministratorInvitation`

* `enterpriseSlug` (String!): The slug of the enterprise the user was invited to join.
* `role` (EnterpriseAdministratorRole!): The role for the enterprise member invitation.
* `userLogin` (String!): The login of the user invited to join the enterprise.

## enterpriseAdministratorInvitationByToken

Look up a pending enterprise administrator invitation by invitation token.

**Type:** EnterpriseAdministratorInvitation

### Arguments for `enterpriseAdministratorInvitationByToken`

* `invitationToken` (String!): The invitation token sent with the invitation email.

## enterpriseMemberInvitation

Look up a pending enterprise unaffiliated member invitation by invitee and enterprise.

**Type:** EnterpriseMemberInvitation

### Arguments for `enterpriseMemberInvitation`

* `enterpriseSlug` (String!): The slug of the enterprise the user was invited to join.
* `userLogin` (String!): The login of the user invited to join the enterprise.

## enterpriseMemberInvitationByToken

Look up a pending enterprise unaffiliated member invitation by invitation token.

**Type:** EnterpriseMemberInvitation

### Arguments for `enterpriseMemberInvitationByToken`

* `invitationToken` (String!): The invitation token sent with the invitation email.

## id

ID of the object.

**Type:** ID!

## license

Look up an open source license by its key.

**Type:** License

### Arguments for `license`

* `key` (String!): The license's downcased SPDX ID.

## licenses

Return a list of known open source licenses.

**Type:** \[License]!

## marketplaceCategories

Get alphabetically sorted list of Marketplace categories.

**Type:** \[MarketplaceCategory!]!

### Arguments for `marketplaceCategories`

* `excludeEmpty` (Boolean): Exclude categories with no listings.
* `excludeSubcategories` (Boolean): Returns top level categories only, excluding any subcategories.
* `includeCategories` (\[String!]): Return only the specified categories.

## marketplaceCategory

Look up a Marketplace category by its slug.

**Type:** MarketplaceCategory

### Arguments for `marketplaceCategory`

* `slug` (String!): The URL slug of the category.
* `useTopicAliases` (Boolean): Also check topic aliases for the category slug.

## marketplaceListing

Look up a single Marketplace listing.

**Type:** MarketplaceListing

### Arguments for `marketplaceListing`

* `slug` (String!): Select the listing that matches this slug. It's the short name of the listing used in its URL.

## marketplaceListings

Look up Marketplace listings.

**Type:** MarketplaceListingConnection!

### Arguments for `marketplaceListings`

* `adminId` (ID): Select listings that can be administered by the specified user.
* `after` (String): Returns the elements in the list that come after the specified cursor.
* `allStates` (Boolean): Select listings visible to the viewer even if they are not approved. If omitted or
  false, only approved listings will be returned.
* `before` (String): Returns the elements in the list that come before the specified cursor.
* `categorySlug` (String): Select only listings with the given category.
* `first` (Int): Returns the first n elements from the list.
* `last` (Int): Returns the last n elements from the list.
* `organizationId` (ID): Select listings for products owned by the specified organization.
* `primaryCategoryOnly` (Boolean): Select only listings where the primary category matches the given category slug.
* `slugs` (\[String]): Select the listings with these slugs, if they are visible to the viewer.
* `useTopicAliases` (Boolean): Also check topic aliases for the category slug.
* `viewerCanAdmin` (Boolean): Select listings to which user has admin access. If omitted, listings visible to the
  viewer are returned.
* `withFreeTrialsOnly` (Boolean): Select only listings that offer a free trial.

## meta

Return information about the GitHub instance.

**Type:** GitHubMetadata!

## node

Fetches an object given its ID.

**Type:** Node

### Arguments for `node`

* `id` (ID!): ID of the object.

## nodes

Lookup nodes by a list of IDs.

**Type:** \[Node]!

### Arguments for `nodes`

* `ids` (\[ID!]!): The list of node IDs.

## organization

Lookup a organization by login.

**Type:** Organization

### Arguments for `organization`

* `login` (String!): The organization's login.

## rateLimit

The client's rate limit information.

**Type:** RateLimit

### Arguments for `rateLimit`

* `dryRun` (Boolean): If true, calculate the cost for the query without evaluating it.

## relay

Workaround for re-exposing the root query object. (Refer to
<https://github.com/facebook/relay/issues/112> for more information.).

**Type:** Query!

## repository

Lookup a given repository by the owner and repository name.

**Type:** Repository

### Arguments for `repository`

* `followRenames` (Boolean): Follow repository renames. If disabled, a repository referenced by its old name will return an error.
* `name` (String!): The name of the repository.
* `owner` (String!): The login field of a user or organization.

## repositoryOwner

Lookup a repository owner (ie. either a User or an Organization) by login.

**Type:** RepositoryOwner

### Arguments for `repositoryOwner`

* `login` (String!): The username to lookup the owner by.

## resource

Lookup resource by a URL.

**Type:** UniformResourceLocatable

### Arguments for `resource`

* `url` (URI!): The URL.

## search

Perform a search across resources, returning a maximum of 1,000 results.

**Type:** SearchResultItemConnection!

### Arguments for `search`

* `after` (String): Returns the elements in the list that come after the specified cursor.
* `before` (String): Returns the elements in the list that come before the specified cursor.
* `first` (Int): Returns the first n elements from the list.
* `last` (Int): Returns the last n elements from the list.
* `query` (String!): The search string to look for. GitHub search syntax is supported. For more
  information, see "Searching on
  GitHub,"
  "Understanding the search syntax,"
  and "Sorting search results.".
* `type` (SearchType!): The types of search items to search within.

## securityAdvisories

GitHub Security Advisories.

**Type:** SecurityAdvisoryConnection!

### Arguments for `securityAdvisories`

* `after` (String): Returns the elements in the list that come after the specified cursor.
* `before` (String): Returns the elements in the list that come before the specified cursor.
* `classifications` (\[SecurityAdvisoryClassification!]): A list of classifications to filter advisories by.
* `epssPercentage` (Float): The EPSS percentage to filter advisories by.
* `epssPercentile` (Float): The EPSS percentile to filter advisories by.
* `first` (Int): Returns the first n elements from the list.
* `identifier` (SecurityAdvisoryIdentifierFilter): Filter advisories by identifier, e.g. GHSA or CVE.
* `last` (Int): Returns the last n elements from the list.
* `orderBy` (SecurityAdvisoryOrder): Ordering options for the returned topics.
* `publishedSince` (DateTime): Filter advisories to those published since a time in the past.
* `updatedSince` (DateTime): Filter advisories to those updated since a time in the past.

## securityAdvisory

Fetch a Security Advisory by its GHSA ID.

**Type:** SecurityAdvisory

### Arguments for `securityAdvisory`

* `ghsaId` (String!): GitHub Security Advisory ID.

## securityVulnerabilities

Software Vulnerabilities documented by GitHub Security Advisories.

**Type:** SecurityVulnerabilityConnection!

### Arguments for `securityVulnerabilities`

* `after` (String): Returns the elements in the list that come after the specified cursor.
* `before` (String): Returns the elements in the list that come before the specified cursor.
* `classifications` (\[SecurityAdvisoryClassification!]): A list of advisory classifications to filter vulnerabilities by.
* `ecosystem` (SecurityAdvisoryEcosystem): An ecosystem to filter vulnerabilities by.
* `first` (Int): Returns the first n elements from the list.
* `last` (Int): Returns the last n elements from the list.
* `orderBy` (SecurityVulnerabilityOrder): Ordering options for the returned topics.
* `package` (String): A package name to filter vulnerabilities by.
* `severities` (\[SecurityAdvisorySeverity!]): A list of severities to filter vulnerabilities by.

## sponsorables

Users and organizations who can be sponsored via GitHub Sponsors.

**Type:** SponsorableItemConnection!

### Arguments for `sponsorables`

* `after` (String): Returns the elements in the list that come after the specified cursor.
* `before` (String): Returns the elements in the list that come before the specified cursor.
* `dependencyEcosystem` (SecurityAdvisoryEcosystem): Optional filter for which dependencies should be checked for sponsorable
  owners. Only sponsorable owners of dependencies in this ecosystem will be
  included. Used when onlyDependencies = true.
  Upcoming Change on 2022-07-01 UTC
  Description: dependencyEcosystem will be removed. Use the ecosystem argument instead.
  Reason: The type is switching from SecurityAdvisoryEcosystem to DependencyGraphEcosystem.
* `ecosystem` (DependencyGraphEcosystem): Optional filter for which dependencies should be checked for sponsorable
  owners. Only sponsorable owners of dependencies in this ecosystem will be
  included. Used when onlyDependencies = true.
* `first` (Int): Returns the first n elements from the list.
* `last` (Int): Returns the last n elements from the list.
* `onlyDependencies` (Boolean): Whether only sponsorables who own the viewer's dependencies will be
  returned. Must be authenticated to use. Can check an organization instead
  for their dependencies owned by sponsorables by passing
  orgLoginForDependencies.
* `orderBy` (SponsorableOrder): Ordering options for users and organizations returned from the connection.
* `orgLoginForDependencies` (String): Optional organization username for whose dependencies should be checked.
  Used when onlyDependencies = true. Omit to check your own dependencies. If
  you are not an administrator of the organization, only dependencies from its
  public repositories will be considered.

## topic

Look up a topic by name.

**Type:** Topic

### Arguments for `topic`

* `name` (String!): The topic's name.

## user

Lookup a user by login.

**Type:** User

### Arguments for `user`

* `login` (String!): The user's login.

## viewer

The currently authenticated user.

**Type:** User!