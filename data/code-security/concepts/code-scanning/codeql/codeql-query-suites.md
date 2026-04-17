# CodeQL query suites

You can choose from different built-in CodeQL query suites to use in your CodeQL code scanning setup.

## What are query suites?

Query suites allow you to pass multiple queries to CodeQL without having to specify the path to each query file individually. They provide a way of selecting queries based on their filename, metadata properties, or location on disk or in a CodeQL pack.

You should use query suites for the queries that you want to frequently use in your CodeQL analyses. You can use a built-in query suite available through GitHub, or you can create your own.

## Built-in CodeQL query suites

The built-in CodeQL query suites, `default` and `security-extended`, are created and maintained by GitHub. Both of these query suites are available with default setup for every CodeQL-supported language.

Organization owners and security managers can recommend a query suite for use with default setup throughout their organization. For more information, see [Configuring default setup for code scanning at scale](/en/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning-at-scale).

For a complete list of queries included in each query suite for every language, see [Queries for CodeQL analysis](/en/code-security/code-scanning/reference/code-ql-built-in-queries).

### `default` query suite

* The `default` query suite is the group of queries run by default in CodeQL code scanning on GitHub.
* The queries in the `default` query suite are highly precise and return few false positive code scanning results. Relative to the `security-extended` query suite, the `default` suite returns fewer low-confidence code scanning results.
* This query suite is available for use with default setup for code scanning.

### `security-extended` query suite

* The `security-extended` query suite consists of all the queries in the `default` query suite, plus additional queries with slightly lower precision and severity.
* Relative to the `default` query suite, the `security-extended` suite may return a greater number of false positive code scanning results.
* This query suite is available for use with default setup for code scanning, and is referred to as the "Extended" query suite on GitHub.

## Custom query suites

To use a custom query suite, you must configure advanced setup for CodeQL code scanning. For more information, see [Configuring advanced setup for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/configuring-advanced-setup-for-code-scanning).

Query suite definitions are stored in YAML files with the extension `.qls`. A suite definition is a sequence of instructions, where each instruction is a YAML mapping with (usually) a single key. The instructions are executed in the order they appear in the query suite definition. After all the instructions in the suite definition have been executed, the result is a set of selected queries. For more information, see [Creating CodeQL query suites](/en/code-security/tutorials/customize-code-scanning/creating-codeql-query-suites).

## Further reading

* [Creating CodeQL query suites](/en/code-security/codeql-cli/using-the-advanced-functionality-of-the-codeql-cli/creating-codeql-query-suites)