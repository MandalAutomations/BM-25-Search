# Auditing your organization's builds on the linked artifacts page

View or export metadata for build runs, storage details, and deployment context.

You can use the linked artifacts page to connect your organization's artifacts to their build details, deployment context, and security metadata. The linked artifacts page collects metadata for artifacts built with GitHub Actions in your organization's repositories, regardless of whether the artifacts are stored on GitHub. For more information, see [About linked artifacts](/en/code-security/concepts/supply-chain-security/linked-artifacts).

## Viewing an artifact

1. On GitHub, navigate to the main page of your organization.
2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-package" aria-label="package" role="img"><path d="m8.878.392 5.25 3.045c.54.314.872.89.872 1.514v6.098a1.75 1.75 0 0 1-.872 1.514l-5.25 3.045a1.75 1.75 0 0 1-1.756 0l-5.25-3.045A1.75 1.75 0 0 1 1 11.049V4.951c0-.624.332-1.201.872-1.514L7.122.392a1.75 1.75 0 0 1 1.756 0ZM7.875 1.69l-4.63 2.685L8 7.133l4.755-2.758-4.63-2.685a.248.248 0 0 0-.25 0ZM2.5 5.677v5.372c0 .09.047.171.125.216l4.625 2.683V8.432Zm6.25 8.271 4.625-2.683a.25.25 0 0 0 .125-.216V5.677L8.75 8.432Z"></path></svg> Packages** tab.

   ![Screenshot of @octo-org's profile page. The "Packages" tab is highlighted with an orange outline.](/assets/images/help/package-registry/org-tab-for-packages-with-overview-tab.png)
3. In the left sidebar, click **Linked artifacts**.
4. Click the artifact you want to view.
5. On the artifact's page, you can:

   * View the artifact's deployment history and registry storage details
   * Click through to the repository where the artifact's source code is defined
   * If available, click on the artifact's provenance attestation to find the workflow run that was used to build the artifact

For more information about how data enters the linked artifacts page, see [Uploading storage and deployment data to the linked artifacts page](/en/code-security/how-tos/secure-your-supply-chain/establish-provenance-and-integrity/upload-linked-artifacts).

## Exporting artifact metadata

To export metadata in bulk for an audit, use the [List artifact deployment records](/en/rest/orgs/artifact-metadata#list-artifact-deployment-records) and [List artifact storage records](/en/rest/orgs/artifact-metadata#list-artifact-storage-records) endpoints of the artifact metadata API.