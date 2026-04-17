# Searching GitHub Models

You can search for models that are available on GitHub Models.

## About searching GitHub Models

You can find models on GitHub Models in two ways:

* Search from GitHub Marketplace.
* Search across all of GitHub and then filter the results to Marketplace.

## Searching in GitHub Marketplace

1. To open GitHub Marketplace, in the top-left corner of GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-three-bars" aria-label="Open global navigation menu" role="img"><path d="M1 2.75A.75.75 0 0 1 1.75 2h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 2.75Zm0 5A.75.75 0 0 1 1.75 7h12.5a.75.75 0 0 1 0 1.5H1.75A.75.75 0 0 1 1 7.75ZM1.75 12h12.5a.75.75 0 0 1 0 1.5H1.75a.75.75 0 0 1 0-1.5Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gift" aria-label="gift" role="img"><path d="M2 2.75A2.75 2.75 0 0 1 4.75 0c.983 0 1.873.42 2.57 1.232.268.318.497.668.68 1.042.183-.375.411-.725.68-1.044C9.376.42 10.266 0 11.25 0a2.75 2.75 0 0 1 2.45 4h.55c.966 0 1.75.784 1.75 1.75v2c0 .698-.409 1.301-1 1.582v4.918A1.75 1.75 0 0 1 13.25 16H2.75A1.75 1.75 0 0 1 1 14.25V9.332C.409 9.05 0 8.448 0 7.75v-2C0 4.784.784 4 1.75 4h.55c-.192-.375-.3-.8-.3-1.25ZM7.25 9.5H2.5v4.75c0 .138.112.25.25.25h4.5Zm1.5 0v5h4.5a.25.25 0 0 0 .25-.25V9.5Zm0-4V8h5.5a.25.25 0 0 0 .25-.25v-2a.25.25 0 0 0-.25-.25Zm-7 0a.25.25 0 0 0-.25.25v2c0 .138.112.25.25.25h5.5V5.5h-5.5Zm3-4a1.25 1.25 0 0 0 0 2.5h2.309c-.233-.818-.542-1.401-.878-1.793-.43-.502-.915-.707-1.431-.707ZM8.941 4h2.309a1.25 1.25 0 0 0 0-2.5c-.516 0-1 .205-1.43.707-.337.392-.646.975-.879 1.793Z"></path></svg> Marketplace**.

   ![Screenshot of the navigation bar on GitHub. The "Open global navigation menu" icon is outlined in dark orange.](/assets/images/help/navigation/global-navigation-menu-icon.png)
2. Type any keywords and `type:models` and press **Enter**.

## Searching across GitHub

Anytime you search across all of GitHub, you can filter the results to see matching models from GitHub Marketplace.

1. Navigate to <https://github.com/search>.
2. Type any keywords and press **Enter**.
3. To see all available filters for your search, in the "Filter by" sidebar, click **More**.
4. To see results from GitHub Models, click **Marketplace**.

## Searching within a specific field

The `in` qualifier used in conjunction with search text finds models that match the specified text in that field. Possible fields include `tags`, `license`, `name`, `description`, `transparency`, and `task`.

| Qualifier                      | Example                                                                                                                                                                                                   |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <code>in:<em>FIELD</em></code> | [**in:tags agents**](https://github.com/search?q=in:tags+agents\&type=marketplace) matches models with the 'agents' tag.                                                                                  |
| <code>in:<em>FIELD</em></code> | [**in:license distribute**](https://github.com/search?q=in:license+distribute\&type=marketplace) matches models who mention 'distribute' in their license.                                                |
| <code>in:<em>FIELD</em></code> | [**in:transparency "responsible ai"**](https://github.com/search?q=in:transparency+%22responsible+ai%22\&type=marketplace) matches models who mention 'responsible ai' in their transparency information. |

## Search by category

The `category` qualifier finds models that are tagged with a specific term.

| Qualifier                               | Example                                                                                                                                                   |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <code>category:<em>CATEGORY</em></code> | [**category:multilingual**](https://github.com/search?q=category:multilingual\&type=marketplace) matches models in the multilingual category.             |
| <code>category:<em>CATEGORY</em></code> | [**category:"large context"**](https://github.com/search?q=category:%22large+context%22+\&type=marketplace) matches models in the large context category. |

## Search by input modality

The `input-modality` qualifier finds models that support a particular medium for providing input. Possible modalities include `text`, `image`, and `audio`.

| Qualifier                                     | Example                                                                                                                              |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| <code>input-modality:<em>MODALITY</em></code> | [**input-modality:text**](https://github.com/search?q=input-modality:text\&type=marketplace) matches models that support text input. |

## Search by output modality

The `output-modality` qualifier finds models that support a particular medium for providing output. Possible modalities include `text` and `embeddings`.

| Qualifier                                      | Example                                                                                                                                                  |
| ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <code>output-modality:<em>MODALITY</em></code> | [**output-modality:embeddings**](https://github.com/search?q=output-modality:embeddings\&type=marketplace) matches models that support embedding output. |

## Search by language

The `language` qualifier finds models that support a specified human language.

| Qualifier                                           | Example                                                                                                                  |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| <code>language:<em>TWO\_CHARACTER\_CODE</em></code> | [**language:es**](https://github.com/search?q=language:es\&type=marketplace) matches models that support Spanish.        |
| <code>language:<em>NAME</em></code>                 | [**language:arabic**](https://github.com/search?q=language:arabic\&type=marketplace) matches models that support Arabic. |

## Search by task

The `task` qualifier finds models that can be used to accomplish a specific task.

| Qualifier                       | Example                                                                                                                                          |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| <code>task:<em>TASK</em></code> | [**task:embeddings**](https://github.com/search?q=task:embeddings\&type=marketplace) matches models that support embedding.                      |
| <code>task:<em>TASK</em></code> | [**task:chat-completion**](https://github.com/search?q=task:chat-completion\&type=marketplace) matches models that support interaction via chat. |

## Search by publisher

The `publisher` qualifier finds models released by a particular publisher.

| Qualifier                                       | Example                                                                                                                              |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| <code>publisher:<em>PUBLISHER\_NAME</em></code> | [**publisher:"Mistral AI"**](https://github.com/search?q=publisher:%22Mistral+AI%22\&type=marketplace) matches models by Mistral AI. |

## Search by input token limit

The `input-tokens` qualifier finds models with an input token limit above or below a particular value, or within a range.

| Qualifier                                | Example                                                                                                                                                                      |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <code>input-tokens:<em>VALUE</em></code> | [**input-tokens:>10000**](https://github.com/search?q=input-tokens:%3E10000\&type=marketplace) matches models with an input token limit greater than 10,000.                 |
| <code>input-tokens:<em>VALUE</em></code> | [**input-tokens:15000..20000**](https://github.com/search?q=input-tokens:15000..20000\&type=marketplace) matches models with an input token limit between 15,000 and 20,000. |

## Search by output token limit

The `output-tokens` qualifier finds models with an output token limit above or below a particular value, or within a range.

| Qualifier                                 | Example                                                                                                                                                                         |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <code>output-tokens:<em>VALUE</em></code> | [**output-tokens:<8000**](https://github.com/search?q=output-tokens:%3C8000\&type=marketplace) matches models with an output token limit less than 8,000.                       |
| <code>output-tokens:<em>VALUE</em></code> | [**output-tokens:15000..20000**](https://github.com/search?q=output-tokens:15000..20000\&type=marketplace) matches models with an output token limit between 15,000 and 20,000. |

## Search by rate limit tier

The `rate-limit-tier` qualifier finds models with a particular tier of rate limit. Possible tiers include `low`, `high`, and `custom`.

| Qualifier                                  | Example                                                                                                                                 |
| ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| <code>rate-limit-tier:<em>TIER</em></code> | [**rate-limit-tier:low**](https://github.com/search?q=rate-limit-tier:low\&type=marketplace) matches models with a low rate limit tier. |

## Search by license type

The `license` qualifier finds models that use a particular license.

| Qualifier                             | Example                                                                                                                      |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| <code>license:<em>LICENSE</em></code> | [**license:mit**](https://github.com/search?q=license:mit\&type=marketplace) matches models that use the MIT license.        |
| <code>license:<em>LICENSE</em></code> | [**license:custom**](https://github.com/search?q=license:custom\&type=marketplace) matches models that use a custom license. |

## Sorting results

The `sort` qualifier is used to sort results. It can be used alone or combined with other qualifiers and search text.

| Qualifier                        | Example                                                                                                                                                                                             |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <code>sort:<em>FIELD</em></code> | [**sort:created-desc publisher:meta**](https://github.com/search?q=sort:created-desc+publisher:meta\&type=marketplace) matches models published by Meta, sorted with the most recently added first. |
| <code>sort:<em>FIELD</em></code> | [**sort:name-asc in:task chat-completion**](https://github.com/search?q=sort:name-asc+in:task+chat-completion\&type=marketplace) matches models that allow chat completion, sorted alphabetically.  |

## Further reading

* [Sorting search results](/en/search-github/getting-started-with-searching-on-github/sorting-search-results)