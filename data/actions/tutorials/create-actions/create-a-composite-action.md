# Creating a composite action

In this tutorial, you'll learn how to build a composite action.

## Introduction

In this guide, you'll learn about the basic components needed to create and use a packaged composite action. To focus this guide on the components needed to package the action, the functionality of the action's code is minimal. The action prints "Hello World" and then "Goodbye", or if you provide a custom name, it prints "Hello \[who-to-greet]" and then "Goodbye". The action also maps a random number to the `random-number` output variable, and runs a script named `goodbye.sh`.

Once you complete this project, you should understand how to build your own composite action and test it in a workflow.

> \[!WARNING]
> When creating workflows and actions, you should always consider whether your code might execute untrusted input from possible attackers. Certain contexts should be treated as untrusted input, as an attacker could insert their own malicious content. For more information, see [Secure use reference](/en/actions/security-guides/security-hardening-for-github-actions#understanding-the-risk-of-script-injections).

### Composite actions and reusable workflows

Composite actions allow you to collect a series of workflow job steps into a single action which you can then run as a single job step in multiple workflows. Reusable workflows provide another way of avoiding duplication, by allowing you to run a complete workflow from within other workflows. For more information, see [Reusing workflow configurations](/en/actions/using-workflows/avoiding-duplication).

## Prerequisites

> \[!NOTE]
> This example explains how to create a composite action within a separate repository. However, it is possible to create a composite action within the same repository. For more information, see [Creating a composite action](/en/actions/creating-actions/creating-a-composite-action#creating-a-composite-action-within-the-same-repository).

Before you begin, you'll create a repository on GitHub.

1. Create a new public repository on GitHub. You can choose any repository name, or use the following `hello-world-composite-action` example. You can add these files after your project has been pushed to GitHub. For more information, see [Creating a new repository](/en/repositories/creating-and-managing-repositories/creating-a-new-repository).

2. Clone your repository to your computer. For more information, see [Cloning a repository](/en/repositories/creating-and-managing-repositories/cloning-a-repository).

3. From your terminal, change directories into your new repository.

   ```shell copy
   cd hello-world-composite-action
   ```

4. In the `hello-world-composite-action` repository, create a new file called `goodbye.sh` with example code:

   ```shell copy
   echo "echo Goodbye" > goodbye.sh
   ```

5. From your terminal, make `goodbye.sh` executable.

   <div class="ghd-tool linux">

   ```shell copy
   chmod +x goodbye.sh
   ```

   </div>

   <div class="ghd-tool mac">

   ```shell copy
   chmod +x goodbye.sh
   ```

   </div>

   <div class="ghd-tool windows">

   ```shell copy
   git add --chmod=+x -- goodbye.sh
   ```

   </div>

6. From your terminal, check in your `goodbye.sh` file.

   <div class="ghd-tool linux">

   ```shell copy
   git add goodbye.sh
   git commit -m "Add goodbye script"
   git push
   ```

   </div>

   <div class="ghd-tool mac">

   ```shell copy
   git add goodbye.sh
   git commit -m "Add goodbye script"
   git push
   ```

   </div>

   <div class="ghd-tool windows">

   ```shell copy
   git commit -m "Add goodbye script"
   git push
   ```

   </div>

## Creating an action metadata file

1. In the `hello-world-composite-action` repository, create a new file called `action.yml` and add the following example code. For more information about this syntax, see [Metadata syntax reference](/en/actions/creating-actions/metadata-syntax-for-github-actions#runs-for-composite-actions).

   ```yaml copy
   name: 'Hello World'
   description: 'Greet someone'
   inputs:
     who-to-greet:  # id of input
       description: 'Who to greet'
       required: true
       default: 'World'
   outputs:
     random-number:
       description: "Random number"
       value: ${{ steps.random-number-generator.outputs.random-number }}
   runs:
     using: "composite"
     steps:
       - name: Set Greeting
         run: echo "Hello $INPUT_WHO_TO_GREET."
         shell: bash
         env:
           INPUT_WHO_TO_GREET: ${{ inputs.who-to-greet }}

       - name: Random Number Generator
         id: random-number-generator
         run: echo "random-number=$(echo $RANDOM)" >> $GITHUB_OUTPUT
         shell: bash

       - name: Set GitHub Path
         run: echo "$GITHUB_ACTION_PATH" >> $GITHUB_PATH
         shell: bash
         env:
           GITHUB_ACTION_PATH: ${{ github.action_path }}

       - name: Run goodbye.sh
         run: goodbye.sh
         shell: bash

   ```

   This file defines the `who-to-greet` input, maps the random generated number to the `random-number` output variable, adds the action's path to the runner system path (to locate the `goodbye.sh` script during execution), and runs the `goodbye.sh` script.

   For more information about managing outputs, see [Metadata syntax reference](/en/actions/creating-actions/metadata-syntax-for-github-actions#outputs-for-composite-actions).

   For more information about how to use `github.action_path`, see [Contexts reference](/en/actions/learn-github-actions/contexts#github-context).

2. From your terminal, check in your `action.yml` file.

   ```shell copy
   git add action.yml
   git commit -m "Add action"
   git push
   ```

3. From your terminal, add a tag. This example uses a tag called `v1`. For more information, see [About custom actions](/en/actions/creating-actions/about-custom-actions#using-release-management-for-actions).

   ```shell copy
   git tag -a -m "Description of this release" v1
   git push --follow-tags
   ```

## Testing out your action in a workflow

The following workflow code uses the completed hello world action that you made in [Creating a composite action](/en/actions/creating-actions/creating-a-composite-action#creating-an-action-metadata-file).

Copy the workflow code into a `.github/workflows/main.yml` file in another repository, replacing `OWNER` and `SHA` with the repository owner and the SHA of the commit you want to use, respectively. You can also replace the `who-to-greet` input with your name.

```yaml copy
on: [push]

jobs:
  hello_world_job:
    runs-on: ubuntu-latest
    name: A job to say hello
    steps:
      - uses: actions/checkout@v5
      - id: foo
        uses: OWNER/hello-world-composite-action@SHA
        with:
          who-to-greet: 'Mona the Octocat'
      - run: echo random-number "$RANDOM_NUMBER"
        shell: bash
        env:
          RANDOM_NUMBER: ${{ steps.foo.outputs.random-number }}
```

From your repository, click the **Actions** tab, and select the latest workflow run. The output should include: "Hello Mona the Octocat", the result of the "Goodbye" script, and a random number.

## Creating a composite action within the same repository

1. Create a new subfolder called `hello-world-composite-action`, this can be placed in any subfolder within the repository. However, it is recommended that this be placed in the `.github/actions` subfolder to make organization easier.

2. In the `hello-world-composite-action` folder, do the same steps to create the `goodbye.sh` script

   ```shell copy
   echo "echo Goodbye" > goodbye.sh
   ```

   <div class="ghd-tool linux">

   ```shell copy
   chmod +x goodbye.sh
   ```

   </div>

   <div class="ghd-tool mac">

   ```shell copy
   chmod +x goodbye.sh
   ```

   </div>

   <div class="ghd-tool windows">

   ```shell copy
   git add --chmod=+x -- goodbye.sh
   ```

   </div>

   <div class="ghd-tool linux">

   ```shell copy
   git add goodbye.sh
   git commit -m "Add goodbye script"
   git push
   ```

   </div>

   <div class="ghd-tool mac">

   ```shell copy
   git add goodbye.sh
   git commit -m "Add goodbye script"
   git push
   ```

   </div>

   <div class="ghd-tool windows">

   ```shell copy
   git commit -m "Add goodbye script"
   git push
   ```

   </div>

3. In the `hello-world-composite-action` folder, create the `action.yml` file based on the steps in [Creating a composite action](/en/actions/creating-actions/creating-a-composite-action#creating-an-action-metadata-file).

4. When using the action, use the relative path to the folder where the composite action's `action.yml` file is located in the `uses` key. The below example assumes it is in the `.github/actions/hello-world-composite-action` folder.

```yaml copy
on: [push]

jobs:
  hello_world_job:
    runs-on: ubuntu-latest
    name: A job to say hello
    steps:
      - uses: actions/checkout@v5
      - id: foo
        uses: ./.github/actions/hello-world-composite-action
        with:
          who-to-greet: 'Mona the Octocat'
      - run: echo random-number "$RANDOM_NUMBER"
        shell: bash
        env:
          RANDOM_NUMBER: ${{ steps.foo.outputs.random-number }}
```

## Example composite actions on GitHub

You can find many examples of composite actions on GitHub.

* [microsoft/action-python](https://github.com/microsoft/action-python)
* [microsoft/gpt-review](https://github.com/microsoft/gpt-review)
* [tailscale/github-action](https://github.com/tailscale/github-action)