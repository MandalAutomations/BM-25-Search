# Deploy your Spark app from the command line

Learn how to deploy your Spark app from the command line.

## Introduction

If you’re developing your spark further in a GitHub codespace, you can deploy it directly from the command line using the Spark CLI, an extension of the GitHub CLI.

### Prerequisites

* **Access to GitHub Copilot**. You need a Copilot Pro+ or Copilot Enterprise license to use Spark. See [What is GitHub Copilot?](/en/copilot/about-github-copilot/what-is-github-copilot#getting-access-to-copilot).
* You must have **built a Spark app** (a "spark"). To start building, navigate to [Spark](https://github.com/spark).
* You have **created a repository** for your spark on GitHub. For instructions, see [Building and deploying AI-powered apps with GitHub Spark](/en/copilot/tutorials/spark/build-apps-with-spark#step-8-invite-collaborators-with-a-repository).

## Open your spark in a codespace

The Spark CLI currently only works within a GitHub codespace.

1. Navigate to the main page of your spark's repository on GitHub.
2. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code** button, then click the **Codespaces** tab.
3. Click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Create a codespace on main" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>** to create a codespace. The codespace opens in a new browser tab.

## Install the Spark CLI

1. In the terminal in your codespace, run the following command to install the Spark CLI:

   ```bash copy
   gh extensions install github/gh-runtime-cli
   ```

2. Once the installation is complete, to verify that the Spark CLI is installed, run:

   ```bash copy
   gh runtime-cli version
   ```

## Build your spark

1. In the terminal in your codespace, run the following command to install the latest version of the Spark SDK:

   ```bash copy
   npm install @github/spark@latest
   ```

2. Next, run the following command to compile your Spark app.

   ```bash copy
   npm run build
   ```

## Deploy your spark

1. To deploy your Spark app, run:

   ```bash copy
   gh runtime-cli deploy --dir ./dist
   ```

## Troubleshooting

If you're being asked to supply the `--app` parameter when deploying your spark, update to the latest version of the Spark SDK by following step 1 in [Build your spark](#build-your-spark).