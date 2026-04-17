# Using GitHub Models to develop AI-powered applications in your enterprise

Streamline AI development in your enterprise.

> \[!NOTE]
> GitHub Models for organizations and repositories is in public preview and subject to change.

GitHub Models allows your developers to build AI-powered applications at scale while your enterprise maintains control, compliance, and cost efficiency.

## Why GitHub Models?

* **Centralized model management:** Control which AI models and providers are available to developers across your organization.
* **AI development at speed:** Quickly prototype, evaluate, and optimize prompts and models.
* **API access:** Use the GitHub Models REST API to automate and integrate with enterprise workflows.
* **Custom model integration:** Bring your own LLM API keys to connect external or custom models, giving your organization greater flexibility and control over which models are available in GitHub Models, whilst keeping aligned with your existing payment methods, credits, and providers.
* **Governance and compliance controls:** Enforce your organization's standards and monitor model usage.
* **Cost optimization:** Avoid unexpected costs from high-priced models.
* **Collaboration:** Share prompts and results using standard GitHub development practices.
* **Security-focused architecture:** Rest assured that your data remains within GitHub and Azure and is not shared with model providers.
* **Visual interface:** Allow non-technical team members to contribute alongside developers.
* **Version control:** All prompt and model changes go through a standard GitHub commit and pull request flow so you know when and why a prompt changed.

See [About GitHub Models](/en/github-models/about-github-models).

## Best practices for using GitHub Models at scale

The following best practices can help you effectively use GitHub Models across your organization.

### Compare and evaluate AI models for governance and compliance

Review and compare available AI models against your company’s governance, data security, and compliance requirements. You can do this in any Models-enabled GitHub repository or in the GitHub Models catalog from the GitHub Marketplace at <https://github.com/marketplace?type=models>. Your considerations may include:

* **Governance and security:** Examine each model's compliance with standards and regulations such as GDPR, SOC 2, and ISO 27001, and ensure data is not persisted outside of your organization unless explicitly logged with consent.
* **Model performance:** Run benchmark evaluations on your internal datasets to assess reasoning, context retention, and hallucination rates.
* **API control and visibility:** Require fine-grained controls over usage quotas, prompt inspection, and rate limits at a team or organization level.
* **Cost optimization:** Include token pricing, inference speed, and the availability of model variants for tiered use. For example, you can use cheaper models for test case generation compared to advanced models for architecture discussions.

Once you have decided which models you want to use, you can limit access in your organization to only those models, see [Managing your team's model usage](/en/github-models/github-models-at-scale/manage-models-at-scale).

### Optimize and share prompts across teams

Your developers can use the prompt editor in GitHub Models to create and refine prompts. Teams can experiment with different prompt variations and models in a stable, non-production environment that integrates with GitHub development workflows. The visual interface allows non-technical stakeholders to contribute alongside developers. See [Using the prompt editor](/en/github-models/use-github-models/prototyping-with-ai-models#using-the-prompt-editor).

The lightweight evaluation tooling allows your team to compare results across common metrics like latency, relevance, and groundedness, or you can create custom evaluators. Compare prompt and model performance for your specific generative AI use cases, such as creating code, tests, documentation, or code review suggestions.

As your team creates effective prompts, they can save them as YAML files and share them for review using GitHub pull requests. Committed prompts are accessible to other teams and workflows and can be kept consistent with your company's standards. This centralized and collaborative approach to prompt management accelerates development and can help you enforce best practices across your organization.

### Evaluate and optimize model usage costs

As adoption of your AI-powered application grows and AI models improve, use GitHub Models to evaluate the cost and performance of different models and model updates. Select the most cost-effective options for your organization's needs and manage expenses as usage scales across multiple teams.

### Use the GitHub Models REST API or extensions for programmatic management

To more efficiently manage resources across all teams, you can leverage the GitHub Models REST API to:

* **Manage and update organization settings:** Programmatically update model access permissions and governance settings across multiple teams at once, to ensure consistency and compliance.
* **List and retrieve prompts:** List, retrieve, and audit prompts used by different teams, to monitor usage, share successful prompts, and maintain a central repository of best practices.
* **Run model inference requests:** Run inference requests for specific models and parameters such as frequency penalty, maximum tokens, response format, and presence penalty.

You can also use these extensions to run inference requests and manage prompts:

* GitHub Models extension for GitHub CLI
* GitHub Models extension for GitHub Copilot Chat
* GitHub Models VS Code extension

### Monitor, iterate, and integrate

With built-in governance features, you can monitor model usage and ensure ongoing compliance with company policies. Audit logs provide visibility into who accessed or modified models and prompts. The GitHub Models repository integration allows all stakeholders to collaborate and continuously iterate on AI-powered applications.

## Example: Use GitHub Models with GitHub Actions to summarize issues

Large software development projects often contain issues full of technical details. You can roll out AI-powered issue summaries using GitHub Models and GitHub Actions.

**Prerequisite:** Enable GitHub Models in your organization, and set the models and publishers you want to make available to individual repositories.

1. **Create a prompt in a repository**

   In the "Models" tab of a repository, create a prompt using the prompt editor.

   Example system prompt:

   > You are a summarizer of GitHub issues. Emphasize key technical points or important questions.

   Example user prompt:

   > Summarize this issue - {{input}}

2. **Run and iterate on your prompt**

   Run your prompt. Provide some sample issue content in the "Variables" pane as the value of `{{input}}`.

   Try different models (for example, OpenAI GPT-4o) and compare results. Adjust parameters such as max tokens and temperature. Iterate until you are satisfied with the results.

3. **Optionally, run more extensive tests**

   The "Compare" view allows you to run multiple of your prompt against different models simultaneously and see how the results compare in a grid view. You can also define and use evaluators to ensure that the results contain certain keywords or meet other standards.

4. **Commit your prompt**

   Name your prompt and commit changes to go through the pull request flow. For example, if you name your prompt `summarize`, you'll get a `summarize.prompt.yaml` file at the root level of your repository that looks something like this:

   ```yaml
   messages:
     - role: system
       content: >-
         You are a summarizer of GitHub issues. Emphasize key technical points or
         important questions.
     - role: user
       content: 'Summarize this issue, please - {{input}}'
   model: openai/gpt-4o
   modelParameters:
     max_tokens: 4096
   ```

   Once your pull request is reviewed and merged, your prompt will be available for anyone to use in the repository.

5. **Call your prompt in a workflow**

   For information on creating workflows, see [Writing workflows](/en/actions/writing-workflows).

   You need to set `models: read` permission to allow a prompt to be called in a workflow.

   Here's an example workflow that adds an AI-generated summary as a comment on any newly created issue:

   ```yaml copy
   name: Summarize New Issue

   on:
     issues:
       types: [opened]

   permissions:
     issues: write
     contents: read
     models: read

   jobs:
     summarize_issue:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout repository
           uses: actions/checkout@v5

         - name: Install gh-models extension
           run: gh extension install https://github.com/github/gh-models
           env:
             GH_TOKEN: ${{ github.token }}

         - name: Create issue body file
           run: |
             cat > issue_body.txt << 'EOT'
             ${{ github.event.issue.body }}
             EOT

         - name: Summarize new issue
           run: |
             cat issue_body.txt | gh models run --file summarize.prompt.yml > summary.txt
           env:
             GH_TOKEN: ${{ github.token }}

         - name: Update issue with summary
           run: |
             SUMMARY=$(cat summary.txt)
             gh issue comment ${{ github.event.issue.number }} --body "### Issue Summary
             ${SUMMARY}"
           env:
             GH_TOKEN: ${{ github.token }}
   ```

6. **Monitor and iterate**

   You can monitor the performance of the action and iterate on the prompt and model selection using the GitHub Models prompt editor. You can also use the [CLI extension](https://github.com/github/gh-models) to test locally, or use the  [GitHub Models REST API](/en/rest/models?apiVersion=2022-11-28) to programmatically update the prompt and model settings.

   You may also want to consider saving the model response as a file in your repository, so that you can review and iterate on the model's performance over time. This allows you to continuously improve the quality of the summaries and ensure they meet your team's needs.