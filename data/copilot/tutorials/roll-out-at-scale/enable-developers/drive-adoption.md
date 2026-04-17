# Driving GitHub Copilot adoption in your company

Learn how to plan an effective enablement process to drive Copilot adoption.

An effective enablement process is essential to drive adoption of Copilot in your organization. This process should be tailored to your organization's needs and goals, and should be designed to help your teams understand how to use Copilot effectively.

Your enablement process may evolve based on feedback and results. You should regularly review and update the process to ensure it continues to meet your organization's needs.

The GitHub Copilot enablement process can be broken down into the following stages:

* Granting licenses
* Supporting users setting up their environment
* Supporting effective use of Copilot

## Prerequisites

* GitHub Copilot must be set up in your organization. For more information, see [Setting up GitHub Copilot for your organization](/en/copilot/setting-up-github-copilot/setting-up-github-copilot-for-your-organization).

## Example rollout timeline

For optimal Copilot adoption, tailor the timing and approach to your organization’s needs. For example, a rollout timeline might look like:

1. Begin onboarding 45 days before rollout: define success metrics and train champions.
2. Share announcements and asynchronous resources 14 days out.
3. Host a workshop at 7 days out.
4. On launch day, provide a Slack channel, wiki, and curated online resources.
5. Continue to provide training. This can be formal at first, then shift to specific, on-demand support as adoption grows.

## Granting licenses

Before you can drive adoption of GitHub Copilot, you need to ensure that your teams have access to the product. For more information, see [Granting access to GitHub Copilot for members of your organization](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-access-to-github-copilot-in-your-organization/granting-access-to-copilot-for-members-of-your-organization).

Depending on the size of your organization, you may want to start with a small pilot program. This will allow you to test your enablement process and make any necessary adjustments before rolling it out to the rest of your organization.

You can start by identifying a small number of teams that are interested in using Copilot. You can then work with these teams to help them get started with Copilot.

GitHub has found that many successful rollouts offer a fully self-service model where developers can claim a license without approval. To learn about options for setting up this process, see [Setting up a self-serve process for GitHub Copilot licenses](/en/copilot/rolling-out-github-copilot-at-scale/setting-up-a-self-serve-process-for-github-copilot-licenses).

## Supporting users setting up their environment

Once your teams have access to GitHub Copilot, ensure they're confident with setting up their environment. GitHub provides comprehensive documentation to help users set up their environment and resolve common issues. See [Setting up GitHub Copilot for yourself](/en/copilot/setting-up-github-copilot/setting-up-github-copilot-for-yourself) and [Troubleshoot GitHub Copilot](/en/copilot/troubleshooting-github-copilot).

If your company uses a corporate proxy or firewall, there are additional steps for ensuring users can connect to GitHub Copilot:

* Ensure that key URLs are added to the allowlist for the proxy server or firewall. See [Copilot allowlist reference](/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/configuring-your-proxy-server-or-firewall-for-copilot).
* Provide guidance for your users to set up their environment to connect via your proxy. You may also need to install custom SSL certificates on your users' machines. See [Configuring network settings for GitHub Copilot](/en/copilot/managing-copilot/configure-personal-settings/configuring-network-settings-for-github-copilot).

For more complex issues, you may also choose to designate an internal point of contact to help users resolve issues, or escalate them to GitHub Support. You should choose a point of contact who is confident troubleshooting firewall and network configuration issues.

## Supporting effective use of Copilot in your organization

This section offers examples of how you can support effective use of Copilot. You can use these examples as a starting point and adapt them to meet your organization's needs and goals.

To drive and measure downstream impact of Copilot, GitHub recommends leading your rollout with specific engineering goals in mind. You should communicate your goals to staff and organize training accordingly. See [Achieving your company's engineering goals with GitHub Copilot](/en/copilot/get-started/achieve-engineering-goals).

### Creating onboarding resources

You may choose to create internal onboarding materials to help teams get started with Copilot. These materials could include your organization's policies and guidelines for using Copilot, GitHub documentation, relevant GitHub blog posts, and any other resources that you think will be helpful.

GitHub documentation that you may want to feature in your onboarding materials includes:

* [Best practices for using GitHub Copilot](/en/copilot/using-github-copilot/best-practices-for-using-github-copilot)
* [Prompt engineering for GitHub Copilot Chat](/en/copilot/using-github-copilot/copilot-chat/prompt-engineering-for-copilot-chat)
* [Getting code suggestions in your IDE with GitHub Copilot](/en/copilot/using-github-copilot/getting-code-suggestions-in-your-ide-with-github-copilot)
* [Asking GitHub Copilot questions in your IDE](/en/copilot/using-github-copilot/asking-github-copilot-questions-in-your-ide)

You can also create a GitHub repository to store these materials, and encourage teams to contribute their own resources and best practices. This can help foster a sense of community among teams that are using Copilot, and make it easier for new teams to get started.

### Working with your pilot program

Once the users in your pilot program have used your onboarding resources, you will have an initial opportunity for feedback, to see whether there are any sticking points that should be resolved before rolling out Copilot on a larger scale.

One way to gather feedback is with a survey. You can use the Copilot survey engine to create an app that will trigger a survey at specific points in the Copilot experience. See the [Copilot survey engine](https://github.com/github/copilot-survey-engine).

### Offering training and support

From your pilot program, you can identify a group of Copilot champions who are enthusiastic about using Copilot and are willing to help others get started. You can work with these champions to create training sessions, workshops, and other resources to help teams get started with Copilot.

You can also use GitHub Discussions to create a space where teams can ask questions, share best practices, and learn from each other. This can help foster a sense of community among teams that are using Copilot, and make it easier for new teams to get started.

GitHub also provides a dedicated Copilot Workshops repository, which contains a selection of workshops designed to help teams learn how to use Copilot effectively. See [Copilot Workshops](https://github.com/copilot-workshops).

The following sections provide practical examples for helping teams to start using Copilot successfully, sourced from real organizations.

#### 1. Run a team onboarding sprint

* Set aside a day or week where everyone focuses on using Copilot.
* Pair up experienced developers with newer team members to explore Copilot in your real codebase.
* Encourage everyone to try Copilot for a specific workflow (such as writing tests or drafting content).
* Debrief as a group. What surprised you, what worked, and what didn’t?

#### 2. Build regular feedback loops

* Add Copilot discussion to your sprint retro or weekly sync.
* Prompt: “What’s one place Copilot helped (or didn’t) this week?”
* Use patterns from these conversations to tweak team documentation or onboarding.

#### 3. Track and celebrate success

* Pick a few metrics that matter (such as faster PRs or fewer “how do I start?” questions).
* Share wins in your team channel or during meetings.
* Recognize individuals who help others get value from Copilot.

### Providing learning resources

In addition to your onboarding resources, you may want to provide a library of learning resources to help teams advance their skills with Copilot. The Copilot Chat Cookbook is a great place to start. The Cookbook is a collection of example prompts that you can use to learn how to ask Copilot for help with a wide range of tasks. See [GitHub Copilot Chat Cookbook](/en/copilot/copilot-chat-cookbook).

### Communicating expectations

If your organization has specific Copilot usage guidelines, these should be clearly communicated in onboarding materials and anywhere else that teams might look for information. For example, if you plan to revoke access to Copilot for users who have not used it in a certain period of time, ensure that your users are aware of this policy.

Many users may not be aware of all of Copilot's capabilities. You should offer guidance on how you expect the different features to fit into your organization's workflows, and provide training to support this. For an end-to-end example, see [Integrating agentic AI into your enterprise's software development lifecycle](/en/copilot/rolling-out-github-copilot-at-scale/enabling-developers/integrating-agentic-ai).

### Ongoing analysis and optimization

Once you have implemented your Copilot enablement process, you should regularly review and optimize it to ensure it continues to meet your organization's needs. Some ways you can do this are:

* Monitoring usage data to identify trends and patterns. See [Tracking license activation and initial usage with Copilot usage metrics](/en/copilot/rolling-out-github-copilot-at-scale/analyzing-usage-over-time-with-the-copilot-metrics-api).
* Following up with users who haven't been using their assigned license. You can use the API to see the latest activity date for each assigned seat. See [Reminding inactive users to use their GitHub Copilot license](/en/copilot/rolling-out-github-copilot-at-scale/reminding-inactive-users).
* Gathering feedback from teams to understand what is working well and what could be improved.
* Reviewing GitHub Discussions and other communication channels to identify common issues and questions.
* Iterating on your enablement process based on lessons learned.
* After a successful rollout, sharing your onboarding checklist or playbook with other teams to scale adoption.

## Further reading

For more concrete examples and a detailed playbook, see the [Training and Onboarding Developers on GitHub Copilot whitepaper](https://github.com/resources/whitepapers/training-and-onboarding-developers-on-github-copilot).