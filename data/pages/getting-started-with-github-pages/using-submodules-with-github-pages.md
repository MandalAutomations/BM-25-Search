# Using submodules with GitHub Pages

You can use submodules with GitHub Pages to include other projects in your site's code.

If the repository for your GitHub Pages site contains submodules, their contents will automatically be pulled in when your site is built.

You can only use submodules that point to public repositories, because the GitHub Pages server cannot access private repositories.

Use the `https://` read-only URL for your submodules, including nested submodules. You can make this change in your `.gitmodules` file.

## Further reading

* [Git Tools - Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) from the *Pro Git* book
* [Troubleshooting Jekyll build errors for GitHub Pages sites](/en/pages/setting-up-a-github-pages-site-with-jekyll/troubleshooting-jekyll-build-errors-for-github-pages-sites)