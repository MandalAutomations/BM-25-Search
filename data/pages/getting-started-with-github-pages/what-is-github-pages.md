# What is GitHub Pages?

You can use GitHub Pages to host a website about yourself, your organization, or your project directly from a repository on GitHub.

## About GitHub Pages

GitHub Pages is a static site hosting service that takes HTML, CSS, and JavaScript files straight from a repository on GitHub, optionally runs the files through a build process, and publishes a website. You can see examples of GitHub Pages sites in the [GitHub Pages examples collection](https://github.com/collections/github-pages-examples).

## Types of GitHub Pages sites

There are two types of GitHub Pages sites. Sites associated with a user or organization account, and sites for a specific project.

<table>
<thead>
<tr>
<th>Property</th>
<th>User and organization sites</th>
<th>Project sites</th>
</tr>
</thead>
<tbody>
<tr>
<th>Source files</th>
<td>Must be stored in a repository named <code>&lt;owner&gt;.github.io</code>, where <code>&lt;owner&gt;</code> is the personal or organization account name</td>
<td>Stored in a folder within the repository that contains the project&#39;s code</td>
</tr>
<tr>
<th>Limits</th>
<td>Maximum of one pages site per account</td>
<td>Maximum of one pages site per repository</td>
</tr>

<tr>
<th>Default site location</th>
<td><code>http(s)://&lt;owner&gt;.github.io</code></td>
<td><code>http(s)://&lt;owner&gt;.github.io/&lt;repositoryname&gt;</code></td>
</tr>

</tbody>
</table>

### Hosting on your own custom domain

You can host your site on GitHub's `github.io` domain or your own custom domain. See [Configuring a custom domain for your GitHub Pages site](/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

## Data collection

When a GitHub Pages site is visited, the visitor's IP address is logged and stored for security purposes, regardless of whether the visitor has signed into GitHub or not. For more information about GitHub's security practices, see [GitHub Privacy Statement](/en/site-policy/privacy-policies/github-privacy-statement).

## Further reading

* [GitHub Pages](https://github.com/skills/github-pages) on GitHub Skills
* [REST API endpoints for repositories](/en/rest/repos#pages)
* [Configuring a publishing source for your GitHub Pages site](/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
* [About custom domains and GitHub Pages](/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages#using-a-custom-domain-across-multiple-repositories)