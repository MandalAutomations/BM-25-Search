# Searching in forks

By default, forks are not shown in search results. You can choose to include them in repository searches, and in code searches if they meet certain criteria.

To show forks in repository search results, add `fork:true` or `fork:only` to your query. For more information, see [Searching for repositories](/en/search-github/searching-on-github/searching-for-repositories).

> \[!NOTE]
> Forks can only be included in repository and code searches.

## Repository search

The `fork:true` qualifier finds all results that match your search query, including forks. The `fork:only` qualifier finds *only* forks that match your search query.

| Qualifier                                  | Example                                                                                                                                                                                     |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fork:true`                                | [**github fork:true**](https://github.com/search?q=github+fork%3Atrue\&type=Repositories) matches all repositories containing the word "github," including forks.                           |
| `fork:only`                                | [**github fork:only**](https://github.com/search?q=github+fork%3Aonly\&type=Repositories) matches all fork repositories containing the word "github."                                       |
| <code>forks:><em>n</em></code> `fork:only` | [**forks:>500 fork:only**](https://github.com/search?q=forks%3A%3E500+fork%3Aonly\&type=Repositories) matches repositories with more than 500 forks, and only returns those that are forks. |

## Code search

GitHub code search uses `is:fork` instead of `fork:true` to include forked repositories in code search results. To exclude forks, use `NOT is:fork`. For more information, see [Understanding GitHub Code Search syntax](/en/search-github/github-code-search/understanding-github-code-search-syntax).

| Qualifier     | Example                                                                                                                                                                                                           |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `is:fork`     | [**android language:java is:fork**](https://github.com/search?q=android+language%3Ajava+is%3Afork\&type=code) matches code with the word "android" that's written in Java, in forked repositories.                |
| `NOT is:fork` | [**android language:java NOT is:fork**](https://github.com/search?q=android+language%3Ajava+NOT+is%3Afork\&type=code) matches code with the word "android" that's written in Java, excluding forked repositories. |

## Further reading

* [About forks](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks)
* [Understanding connections between repositories](/en/repositories/viewing-activity-and-data-for-your-repository/understanding-connections-between-repositories#listing-the-forks-of-a-repository)
* [About searching on GitHub](/en/search-github/getting-started-with-searching-on-github/about-searching-on-github)