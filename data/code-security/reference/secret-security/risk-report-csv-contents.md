# Contents of the secret risk assessment report CSV

Understand the data included in the CSV export of the secret risk assessment report.

The secret risk assessment report CSV file includes the following information:

| CSV column | Name                   | Description                                                                                                                                                                                                                                        |
| ---------- | ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A          | `Organization Name`    | The name of the organization the secret was detected in                                                                                                                                                                                            |
| B          | `Name`                 | The token name for the type of secret                                                                                                                                                                                                              |
| C          | `Slug`                 | The normalized string for the token. This corresponds to `Token` in the table of supported secrets. See [Supported secret scanning patterns](/en/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#supported-secrets). |
| D          | `Push Protected`       | A `boolean` to indicate whether the secret would be detected and blocked by push protection if it were enabled                                                                                                                                     |
| E          | `Non-Provider Pattern` | A `boolean` to indicate whether the secret matched a non-provider pattern and would generate an alert if secret scanning with non-provider patterns were enabled                                                                                   |
| F          | `Secret Count`         | An aggregate count of the active and inactive secrets found for the token type                                                                                                                                                                     |
| G          | `Repository Count`     | An aggregate count of distinct repositories in which the secret type was found, including public, private, and archived repositories                                                                                                               |

## Next steps

To learn which secrets you should prioritize for remediation, see [Interpreting secret risk assessment results](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/interpreting-secret-risk-assessment-results#step-5-prioritizing-remediation-and-related-actions).