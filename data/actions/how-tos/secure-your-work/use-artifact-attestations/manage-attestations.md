# Managing the lifecycle of artifact attestations

Search for and delete attestations that you no longer need.

Attestations are only meaningful when they are linked to artifacts that people consume. To keep your attestations relevant and manageable, you should delete attestations that are no longer needed, such as:

* Attestations created by accident
* Attestations linked to artifacts that no longer exist
* Attestations linked to artifacts that consumers should no longer trust

When consumers have a verification process in place, deleting an attestation can prevent the associated artifact from being used. Consider setting up automations to ensure that attestations are deleted when the associated artifact is removed from an external service (for example, an image is deleted from a container registry).

## Finding attestations

1. Navigate to the repository where the attestation was produced.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)
3. In the left sidebar, under "Management," click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-verified" aria-label="verified" role="img"><path d="m9.585.52.929.68c.153.112.331.186.518.215l1.138.175a2.678 2.678 0 0 1 2.24 2.24l.174 1.139c.029.187.103.365.215.518l.68.928a2.677 2.677 0 0 1 0 3.17l-.68.928a1.174 1.174 0 0 0-.215.518l-.175 1.138a2.678 2.678 0 0 1-2.241 2.241l-1.138.175a1.17 1.17 0 0 0-.518.215l-.928.68a2.677 2.677 0 0 1-3.17 0l-.928-.68a1.174 1.174 0 0 0-.518-.215L3.83 14.41a2.678 2.678 0 0 1-2.24-2.24l-.175-1.138a1.17 1.17 0 0 0-.215-.518l-.68-.928a2.677 2.677 0 0 1 0-3.17l.68-.928c.112-.153.186-.331.215-.518l.175-1.14a2.678 2.678 0 0 1 2.24-2.24l1.139-.175c.187-.029.365-.103.518-.215l.928-.68a2.677 2.677 0 0 1 3.17 0ZM7.303 1.728l-.927.68a2.67 2.67 0 0 1-1.18.489l-1.137.174a1.179 1.179 0 0 0-.987.987l-.174 1.136a2.677 2.677 0 0 1-.489 1.18l-.68.928a1.18 1.18 0 0 0 0 1.394l.68.927c.256.348.424.753.489 1.18l.174 1.137c.078.509.478.909.987.987l1.136.174a2.67 2.67 0 0 1 1.18.489l.928.68c.414.305.979.305 1.394 0l.927-.68a2.67 2.67 0 0 1 1.18-.489l1.137-.174a1.18 1.18 0 0 0 .987-.987l.174-1.136a2.67 2.67 0 0 1 .489-1.18l.68-.928a1.176 1.176 0 0 0 0-1.394l-.68-.927a2.686 2.686 0 0 1-.489-1.18l-.174-1.137a1.179 1.179 0 0 0-.987-.987l-1.136-.174a2.677 2.677 0 0 1-1.18-.489l-.928-.68a1.176 1.176 0 0 0-1.394 0ZM11.28 6.78l-3.75 3.75a.75.75 0 0 1-1.06 0L4.72 8.78a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L7 8.94l3.22-3.22a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Attestations**.
4. The attestations are sorted by creation date, newest first. Use the "Search or filter" bar to search for an attestation or filter the results.

### Searching and filtering

Enter **free text** to search by subject name. This returns all attestations with subject names that partially match your search string. Multiple attestations can have the same subject name.

Use the `created` filter to filter by creation date. To enter a custom date range, click today's date then edit the default query.

* For example: `created:<2025-04-03`.
* Supported operators: `> <`.

Use the `predicate` filter to filter by the kind of attestation. A predicate is the type of claim that an attestation makes about an artifact, such as "this artifact was built during a particular workflow run and originates from this repository."

* Provenance attestations were created with the `attest` action.
* SBOM attestations were created with the `attest` action using the `sbom-path` input.
* Custom predicate type patterns are **not** supported in the search field, but are supported by the API.

## Deleting attestations

Before deleting an attestation, we recommend downloading a copy of it. Once the attestation is deleted, consumers with a verification process in place will **no longer be able to use the associated artifact**, and you will no longer be able to find the attestation on GitHub.

1. In the list of attestations, select the checkbox next to the attestations you want to delete. You can select multiple attestations at a time.
2. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-trash" aria-label="trash" role="img"><path d="M11 1.75V3h2.25a.75.75 0 0 1 0 1.5H2.75a.75.75 0 0 1 0-1.5H5V1.75C5 .784 5.784 0 6.75 0h2.5C10.216 0 11 .784 11 1.75ZM4.496 6.675l.66 6.6a.25.25 0 0 0 .249.225h5.19a.25.25 0 0 0 .249-.225l.66-6.6a.75.75 0 0 1 1.492.149l-.66 6.6A1.748 1.748 0 0 1 10.595 15h-5.19a1.75 1.75 0 0 1-1.741-1.575l-.66-6.6a.75.75 0 1 1 1.492-.15ZM6.5 1.75V3h3V1.75a.25.25 0 0 0-.25-.25h-2.5a.25.25 0 0 0-.25.25Z"></path></svg> Delete**.
3. Read the message, then confirm by clicking **Delete attestations**.

## Managing attestations with the API

To manage attestations in bulk with the REST API, see [REST API endpoints for artifact attestations](/en/rest/users/attestations).