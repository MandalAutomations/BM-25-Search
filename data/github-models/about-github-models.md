# About GitHub Models

GitHub Models is a suite of developer tools that take you from AI idea to ship, including a model catalog, prompt management, and quantitative evaluations.

> \[!NOTE]
> GitHub Models for organizations and repositories is in public preview and subject to change.

## Overview

GitHub Models is a workspace lowering the barrier to enterprise-grade AI adoption. It helps you move beyond isolated experimentation by embedding AI development directly into familiar GitHub workflows. GitHub Models provides tools to test large language models (LLMs), refine prompts, evaluate outputs, and make informed decisions based on structured metrics. To get started, see [Optimizing your AI-powered app with Models](/en/github-models/use-github-models/optimizing-your-ai-powered-app-with-github-models).

## Capabilities

GitHub Models offers a set of features to support prompt iteration, evaluation, and integration for AI development.

* **Prompt development**: Start AI development directly in a structured editor that supports system instructions, test inputs, and variable configuration.
* **Model comparison**: Test multiple models side by side with identical prompts and inputs to experiment with different outputs.
* **Evaluators**: Use scoring metrics such as similarity, relevance, and groundedness to analyze outputs and track performance.
* **Prompt configurations**: Save prompt, model, and parameter settings as `.prompt.yml` files in your repository. This enables review, collaboration, and reproducibility.
* **Production integration**: Use your saved configuration to build AI features or connect through SDKs and the [GitHub Models REST API](/en/rest/models?apiVersion=2022-11-28).

## Enabling GitHub Models

There are a few ways you can start using GitHub Models, depending on your role and needs.

To use the GitHub Models API, see [Experimenting with AI models using the API](/en/github-models/use-github-models/prototyping-with-ai-models#experimenting-with-ai-models-using-the-api).

### For individuals

To use GitHub Models, create a new GitHub repository or open an existing one. In the repository settings, click **Models** in the sidebar and enable the feature.

### For organizations and enterprises

To use GitHub Models in your organization, an enterprise owner must first enable the feature. Organization owners can then configure which models are allowed.

See [Managing your team's model usage](/en/github-models/github-models-at-scale/manage-models-at-scale).

## Searching GitHub Models

To search for available models, see [Searching GitHub Models](/en/search-github/searching-on-github/searching-github-models). You can search for models by name, publisher, language, modality, and other filters.

## Prompts

Manage your prompt configurations stored in the repository. Each prompt is saved as a `.prompt.yml` file, which defines the model, parameters, and test inputs. From here, you can create, edit, and organize prompts to support experimentation or production use.

## Comparisons

Use the Comparisons view to evaluate the outputs of multiple prompt configurations in a consistent, test-driven workflow. Run tests across rows of input data and view evaluator scores for each configuration, such as similarity, relevance, and groundedness. This view is ideal for refining prompts, validating changes, and avoiding regressions.

## Playground

Use the Playground to quickly explore models and test prompt ideas in real time. The Playground is ideal for early experimentation, helping you understand a model’s behavior, capabilities, and response style. You can interactively select models, adjust parameters, and compare responses side by side.

## Billing

For more information about billing for GitHub Models, see [GitHub Models billing](/en/billing/managing-billing-for-your-products/about-billing-for-github-models).

## Join the community

To ask questions and share feedback, see this [GitHub Models discussion post](https://github.com/orgs/community/discussions/159087).\
To learn how others are using GitHub Models, visit the [GitHub Community discussions for Models](https://github.com/orgs/community/discussions/categories/models).

## Further reading

* [Searching GitHub Models](/en/search-github/searching-on-github/searching-github-models)
* [Prototyping with AI models](/en/github-models/use-github-models/prototyping-with-ai-models)
* [Optimizing your AI-powered app with Models](/en/github-models/use-github-models/optimizing-your-ai-powered-app-with-github-models)
* [Evaluating AI models](/en/github-models/use-github-models/evaluating-ai-models)
* [GitHub Models billing](/en/billing/managing-billing-for-your-products/about-billing-for-github-models)