# Managing GitHub Copilot code review in your enterprise

Enable members of your enterprise to use Copilot to review code and create pull request summaries.

This policy controls the use of Copilot code review and Copilot pull request summaries in your enterprise.

For an introduction to Copilot code review, see [About GitHub Copilot code review](/en/copilot/concepts/code-review).

For more information about Copilot pull request summaries, see [Creating a pull request summary with GitHub Copilot](/en/copilot/how-tos/copilot-on-github/copilot-for-github-tasks/create-a-pr-summary).

## Enabling Copilot code review for your Copilot subscribers

You can allow your members to use Copilot code review and Copilot pull request summaries from the AI Controls tab for your enterprise. See [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-policies-and-features-for-copilot-in-your-enterprise#defining-policies-for-your-enterprise).

> \[!NOTE]
>
> * Several tools in Copilot code review are in public preview and subject to change.
> * The [GitHub Pre-release License Terms](/en/site-policy/github-terms/github-pre-release-license-terms) apply to your use of this product.

### Next steps

* If you selected **Enabled everywhere**, tell organization owners that these features are enabled for all members.
* If you selected **Let organizations decide**, discuss member enablement with organization owners.

## Disabling Copilot code review in your repositories

Copilot policies affect only the users you assign a Copilot license to.

If there are Copilot Pro or Copilot Pro+ users with access to your enterprise's repositories, they will be able to use Copilot code review and will not be restricted by your policies.

Alternatively, you can disable the agent for all repositories owned by your enterprise.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> AI controls**.
3. In the "Installed Agents" section, click **Copilot code review**.
4. In the "Copilot code review" section, next to "Block Copilot code review in all enterprise repositories", click the toggle.