# Configuring runners for GitHub Copilot code review

Use self-hosted runners or larger GitHub-hosted runners for Copilot code review.

## About GitHub Actions usage for code review tools

Copilot code review uses GitHub Actions to run the agentic capabilities, including full project context gathering and any capabilities in public preview. By default, Copilot code review uses GitHub-hosted runners.

If your organization has disabled GitHub-hosted runners, the agentic capabilities will not be available. In this case, code reviews will fall back to a more limited review. Organizations in this situation can use self-hosted runners.

You can also upgrade to larger GitHub-hosted runners for better performance.

## Configure self-hosted runners for code review

Run Copilot code review using self-hosted GitHub Actions runners with ARC (Actions Runner Controller). You must first set up ARC-managed scale sets in your environment. For more information on ARC, see [Actions Runner Controller](/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/about-actions-runner-controller).

> \[!WARNING]
> ARC is the only officially supported solution for self-hosting Copilot code review. For security reasons, do not use non-ARC self-hosted runners.

Copilot code review is only compatible with Ubuntu x64 Linux runners.

To configure self-hosted runners for Copilot code review:

1. Configure network security controls for your GitHub Actions runners to ensure that Copilot code review does not have open access to your network or the public internet.

   You must configure your firewall to allow connections to the [standard hosts required for GitHub Actions self-hosted runners](/en/actions/reference/runners/self-hosted-runners#accessible-domains-by-function), plus the following hosts:

   * `api.githubcopilot.com`
   * `uploads.github.com`
   * `user-images.githubusercontent.com`
2. In your `copilot-setup-steps.yml` file, set the `runs-on` attribute to your ARC-managed scale set name. For more information, see [Customizing the development environment for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/customize-the-agent-environment#preinstalling-tools-or-dependencies-in-copilots-environment).

   ```yaml
   # ...

   jobs:
     copilot-setup-steps:
       runs-on: arc-scale-set-name
       # ...
   ```

## Upgrade to larger GitHub-hosted GitHub Actions runners

By default, Copilot code review runs on a standard GitHub Actions runner. Larger runners provide better performance (CPU and memory), more disk space, and advanced features like Azure private networking. See [Larger runners](/en/actions/using-github-hosted-runners/using-larger-runners/about-larger-runners).

> \[!NOTE]
> Usage of larger GitHub-hosted runners is billed per-minute and may incur additional GitHub Actions charges.

1. Set up larger runners for your organization. See [Managing larger runners](/en/actions/using-github-hosted-runners/managing-larger-runners).

2. If you are using larger runners with Azure private networking, configure your Azure private network to allow outbound access to the following hosts:

   * `api.githubcopilot.com`
   * `uploads.github.com`
   * `user-images.githubusercontent.com`

3. In your `copilot-setup-steps.yml` file, set the `runs-on` attribute to the label for the larger runners you want Copilot code review to use. See [Running jobs on larger runners](/en/actions/using-github-hosted-runners/running-jobs-on-larger-runners).

   ```yaml
   # ...

   jobs:
     copilot-setup-steps:
       runs-on: ubuntu-4-core
       # ...
   ```