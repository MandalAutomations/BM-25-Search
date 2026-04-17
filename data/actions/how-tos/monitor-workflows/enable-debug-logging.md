# Enabling debug logging

If the workflow logs do not provide enough detail to diagnose why a workflow, job, or step is not working as expected, you can enable additional debug logging.

These extra logs are enabled by setting secrets or variables in the repository containing the workflow, so the same permissions requirements will apply:

* To create secrets or variables on GitHub for an organization repository, you must have `write` access. For a personal account repository, you must be a repository collaborator.
* To create secrets or variables for an environment in a personal account repository, you must be the repository owner. To create secrets or variables for an environment in an organization repository, you must have `admin` access. For more information on environments, see [Managing environments for deployment](/en/actions/deployment/targeting-different-environments/managing-environments-for-deployment).
* Organization owners can create secrets or variables at the organization level.

For more information on setting secrets and variables, see [Using secrets in GitHub Actions](/en/actions/security-guides/using-secrets-in-github-actions) and [Store information in variables](/en/actions/learn-github-actions/variables).

Additionally, anyone who has access to run a workflow can enable runner diagnostic logging and step debug logging for a workflow re-run. For more information, see [Re-running workflows and jobs](/en/actions/managing-workflow-runs/re-running-workflows-and-jobs).

## Enabling runner diagnostic logging

Runner diagnostic logging provides additional log files that contain information about how a runner is executing a job. Two extra log files are added to the log archive:

* The runner process log, which includes information about coordinating and setting up runners to execute jobs.
* The worker process log, which logs the execution of a job.

1. To enable runner diagnostic logging, set the following secret or variable in the repository that contains the workflow: `ACTIONS_RUNNER_DEBUG` to `true`. If both the secret and variable are set, the value of the secret takes precedence over the variable.
2. To download runner diagnostic logs, download the log archive of the workflow run. The runner diagnostic logs are contained in the `runner-diagnostic-logs` folder. For more information on downloading logs, see [Using workflow run logs](/en/actions/monitoring-and-troubleshooting-workflows/using-workflow-run-logs#downloading-logs).

## Enabling step debug logging

Step debug logging increases the verbosity of a job's logs during and after a job's execution.

1. To enable step debug logging, set the following secret or variable in the repository that contains the workflow: `ACTIONS_STEP_DEBUG` to `true`. If both the secret and variable are set, the value of the secret takes precedence over the variable.
2. After setting the secret or variable, more debug events are shown in the step logs. For more information, see [Using workflow run logs](/en/actions/monitoring-and-troubleshooting-workflows/using-workflow-run-logs#viewing-logs-to-diagnose-failures).

You can also use the `runner.debug` context to conditionally run steps only when debug logging is enabled. For more information, see [Contexts reference](/en/actions/reference/workflows-and-actions/contexts#runner-context).