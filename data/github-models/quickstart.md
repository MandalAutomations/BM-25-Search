# Quickstart for GitHub Models

Run your first model with GitHub Models in minutes.

## Introduction

GitHub Models is an AI inference API from GitHub that lets you run AI models using just your GitHub credentials. You can choose from many different models—including from OpenAI, Meta, and DeepSeek—and use them in scripts, apps, or even GitHub Actions, with no separate authentication process.

This guide helps you try out models quickly in the playground, then shows you how to run your first model via API or workflow.

## Step 1: Try models in the playground

1. Go to **<https://github.com/marketplace/models>**.
2. In the playground, select at least one model from the dropdown menu.
3. Test out different prompts using the **Chat** view, and compare responses from different models.
4. Use the **Parameters** view to customize the parameters for the models you are testing, then see how they impact responses.

   > \[!NOTE]
   > The playground works out of the box if you're signed in to GitHub. It uses your GitHub account for access—no setup or API keys required.

## Step 2: Make an API call

For full details on available fields, headers, and request formats, see the [API reference for GitHub Models](/en/rest/models/inference?apiVersion=2022-11-28).

To call models programmatically, you’ll need:

* A GitHub account.
* A personal access token (PAT) with the `models` scope, which you can create [in settings](https://github.com/settings/tokens).

1. Run the following `curl` command, replacing `YOUR_GITHUB_PAT` with your token.

   ```bash copy
     curl -L \
     -X POST \
     -H "Accept: application/vnd.github+json" \
     -H "Authorization: Bearer YOUR_GITHUB_PAT" \
     -H "X-GitHub-Api-Version: 2022-11-28" \
     -H "Content-Type: application/json" \
     https://models.github.ai/inference/chat/completions \
     -d '{"model":"openai/gpt-4.1","messages":[{"role":"user","content":"What is the capital of France?"}]}'
   ```

2. You’ll receive a response like this:

   ```json
   {
     "choices": [
       {
         "message": {
           "role": "assistant",
           "content": "The capital of France is **Paris**."
         }
       }
     ],
     ...other fields omitted
   }
   ```

3. To try other models, change the value of the `model` field in the JSON payload to one from the [marketplace](https://github.com/marketplace/models).

## Step 3: Run models in GitHub Actions

1. In your repository, create a workflow file at `.github/workflows/models-demo.yml`.

2. Paste the following workflow into the file you just created.

   ```yaml copy
   name: Use GitHub Models

   on: [push]

   permissions:
     models: read

   jobs:
     call-model:
       runs-on: ubuntu-latest
       steps:
         - name: Call AI model
           env:
             GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
           run: |
             curl "https://models.github.ai/inference/chat/completions" \
                -H "Content-Type: application/json" \
                -H "Authorization: Bearer $GITHUB_TOKEN" \
                -d '{
                 "messages": [
                     {
                        "role": "user",
                        "content": "Explain the concept of recursion."
                     }
                  ],
                  "model": "openai/gpt-4o"
               }'
   ```

   > \[!NOTE]
   > Workflows that call GitHub Models must include `models: read` in the permissions block. GitHub-hosted runners provide a `GITHUB_TOKEN` automatically.

3. Commit and push to trigger the workflow.

This example shows how to send a prompt to a model and use the response in your continuous integration (CI) workflows. For more advanced use cases, such as summarizing issues, detecting missing reproduction steps for bug reports, or responding to pull requests, see [Configuring access to AI models in GitHub Copilot](/en/github-models/use-github-models/integrating-ai-models-into-your-development-workflow).

## Step 4: Save your first prompt file

GitHub Models supports reusable prompts defined in `.prompt.yml` files. Once you add this file to your repository, it will appear in the Models page of your repository and can be run directly in the Prompt Editor and evaluation tooling. Learn more about [Storing prompts in GitHub repositories](/en/github-models/use-github-models/storing-prompts-in-github-repositories).

1. In your repository, create a file named `summarize.prompt.yml`. You can save it in any directory.

2. Paste the following example prompt into the file you just created.

   ```yaml copy
   name: Text Summarizer
   description: Summarizes input text concisely
   model: openai/gpt-4o-mini
   modelParameters:
     temperature: 0.5
   messages:
     - role: system
       content: You are a text summarizer. Your only job is to summarize text given to you.
     - role: user
       content: |
         Summarize the given text, beginning with "Summary -":
         <text>
         {{input}}
         </text>
   ```

3. Commit and push the file to your repository.

4. Go to the **Models** tab in your repository.

5. In the navigation menu, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-note" aria-label="none" role="img"><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25Zm1.75-.25a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25ZM3.5 6.25a.75.75 0 0 1 .75-.75h7a.75.75 0 0 1 0 1.5h-7a.75.75 0 0 1-.75-.75Zm.75 2.25h4a.75.75 0 0 1 0 1.5h-4a.75.75 0 0 1 0-1.5Z"></path></svg> Prompts**, then click on the prompt file.

6. The prompt will open in the prompt editor. Click **Run**. A right-hand sidebar will appear asking you to enter input text. Enter any input text, then click **Run** again in the bottom right corner to test it out.

   > \[!NOTE]
   > The prompt editor doesn’t automatically pass repository content into prompts. You provide the input manually.

## Step 5: Set up your first evaluation

Evaluations help you measure how different models respond to the same inputs so you can choose the best one for your use case.

1. Go back to the `summarize.prompt.yml` file you created in the previous step.

2. Update the file to match the following example.

   ```yaml copy
   name: Text Summarizer
   description: Summarizes input text concisely
   model: openai/gpt-4o-mini
   modelParameters:
     temperature: 0.5
   messages:
     - role: system
       content: You are a text summarizer. Your only job is to summarize text given to you.
     - role: user
       content: |
         Summarize the given text, beginning with "Summary -":
         <text>
         {{input}}
         </text>
   testData:
     - input: |
         The quick brown fox jumped over the lazy dog.
         The dog was too tired to react.
       expected: Summary - A fox jumped over a lazy, unresponsive dog.
     - input: |
         The museum opened a new dinosaur exhibit this weekend. Families from all
         over the city came to see the life-sized fossils and interactive displays.
       expected: Summary - The museum's new dinosaur exhibit attracted many families with its fossils and interactive displays.
   evaluators:
     - name: Output should start with 'Summary -'
       string:
         startsWith: 'Summary -'
     - name: Similarity
       uses: github/similarity
   ```

3. Commit and push the file to your repository.

4. In your repository, click the **Models** tab. Then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-note" aria-label="none" role="img"><path d="M0 3.75C0 2.784.784 2 1.75 2h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 14H1.75A1.75 1.75 0 0 1 0 12.25Zm1.75-.25a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25ZM3.5 6.25a.75.75 0 0 1 .75-.75h7a.75.75 0 0 1 0 1.5h-7a.75.75 0 0 1-.75-.75Zm.75 2.25h4a.75.75 0 0 1 0 1.5h-4a.75.75 0 0 1 0-1.5Z"></path></svg> Prompts** and reopen the same prompt in the prompt editor.

5. In the top left-hand corner, you can toggle the view from **Edit** to **Compare**. Click **Compare**.

6. Your evaluation will be set up automatically. Click **Run** to see results.

   > \[!TIP]
   > By clicking **Add prompt**, you can run the same prompt with different models or change the prompt wording to get inference responses with multiple variations at once, see evaluations, and view them side by side to make data-driven model decisions.

## Next steps

* [About GitHub Models](/en/github-models/about-github-models).
* [Browse the model catalog](https://github.com/marketplace?type=models)
* [Storing prompts in GitHub repositories](/en/github-models/use-github-models/storing-prompts-in-github-repositories)
* [Evaluating AI models](/en/github-models/use-github-models/evaluating-ai-models)
* [Configuring access to AI models in GitHub Copilot](/en/github-models/use-github-models/integrating-ai-models-into-your-development-workflow#using-ai-models-with-github-actions)