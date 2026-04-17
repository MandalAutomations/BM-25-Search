# Searching for packages

You can search for packages on GitHub and narrow the results using search qualifiers.

<!-- 2148AF7B-5FF8-4B28-A808-D692FEE2225A -->

## About searching for packages

You can search for packages globally across all of GitHub, or search for packages within a particular organization. For more information, see [About searching on GitHub](/en/search-github/getting-started-with-searching-on-github/about-searching-on-github).

> \[!TIP]
>
> * This article contains links to example searches on the GitHub.com website, but you can use the same search filters in any GitHub platform. In the linked example searches, replace `github.com` with the hostname for your GitHub platform.
> * For a list of search syntaxes that you can add to any search qualifier to further improve your results, see [Understanding the search syntax](/en/search-github/getting-started-with-searching-on-github/understanding-the-search-syntax).
> * Use quotations around multi-word search terms. For example, if you want to search for issues with the label "In progress," you'd search for `label:"in progress"`. Search is not case sensitive.

## Searching within a user's or organization's packages

To find packages owned by a certain user or organization, use the `user` or `org` qualifier.

| Qualifier                           | Example                                                                                                                               |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| <code>user:<em>USERNAME</em></code> | [**`user:codertocat`**](https://github.com/search?q=user%3Acodertocat\&type=RegistryPackages) matches packages owned by @codertocat   |
| <code>org:<em>ORGNAME</em></code>   | [**`org:github`**](https://github.com/search?q=org%3Agithub\&type=RegistryPackages) matches packages owned by the GitHub organization |

## Filtering by package visibility

To filter your search by whether a package is public or private, use the `is` qualifier.

| Qualifier    | Example                                                                                                                                                 |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `is:public`  | [**is:public angular**](https://github.com/search?q=is%3Apublic+angular\&type=RegistryPackages) matches public packages that contain the word "angular" |
| `is:private` | [**is:private php**](https://github.com/search?q=is%3Aprivate+php\&type=RegistryPackages) matches private packages that contain the word "php"          |