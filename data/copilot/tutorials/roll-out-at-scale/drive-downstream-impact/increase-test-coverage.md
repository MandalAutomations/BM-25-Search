# Increasing test coverage in your company with GitHub Copilot

Understand features, enable developers, and measure Copilot's impact.

The guide is inspired by GitHub's [Engineering System Success Playbook](https://resources.github.com/engineering-system-success-playbook/) (ESSP), which recommends strategies and metrics for driving improvements in engineering systems.

If you're starting a rollout of Copilot, we recommend defining your goals, planning your rollout accordingly, and communicating the goals clearly to staff. See [Achieving your company's engineering goals with GitHub Copilot](/en/copilot/get-started/achieve-engineering-goals).

## 1. Identify barriers to success

The first step recommended by the ESSP is to develop a clear understanding of the obstacles preventing improvements in your company. By understanding your current baseline, your desired future state, and the barriers preventing you from making progress, you can ensure changes are targeted and effective.

Many software teams face persistent challenges in maintaining high-quality code due to low unit test coverage. In fast-paced development environments, writing tests is often seen as time-consuming or non-essential, especially when teams are under pressure to deliver features quickly.

As a result, critical bugs can be discovered late in the development lifecycle, often in staging or production environments.

This leads to a chain of negative outcomes:

* **Higher bug rates** and customer-reported issues
* **Increased cost** of fixing bugs after deployment
* **Reduced developer confidence** in the stability of their code
* **Slower release cycles** due to reactive debugging and patching

In legacy systems, test coverage can be even harder to address because of complex dependencies or poorly documented code. Developers may lack familiarity with older codebases or with testing frameworks in general, further compounding the problem.

Improving test coverage is a recognized best practice, but it requires time and expertise that many teams struggle to allocate.

## 2. Evaluate your options

The next step is to evaluate and agree on solutions to address the barriers you identified in step one. In this guide, we'll focus on the impact GitHub Copilot can have on the goal you've identified. Successful rollouts of a new tool also require changes to culture and processes.

Run trials of new tools and processes with pilot groups to gather feedback and measure success. For training resources and metrics to use during trials, see [3. Implement changes](#3-implement-changes) and [Metrics to watch](#metrics-to-watch) sections.

<a href="https://github.com/enterprise/contact?ref_product=copilot&ref_type=engagement&ref_style=button" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Contact Sales</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

### How Copilot can help

GitHub Copilot can significantly accelerate and simplify the process of writing unit tests. By understanding the surrounding code and context, Copilot can suggest test functions that match the structure and logic of the code being tested.

Copilot's capabilities are useful across multiple scenarios:

* As developers write new functions, Copilot can automatically suggest corresponding test cases inline.
* When refactoring legacy code, Copilot can help generate test scaffolding to prevent regressions.
* For untested modules, developers can prompt Copilot to generate meaningful test cases, even when test coverage is missing or inconsistent.

By making unit testing easier, faster, and less manual, Copilot reduces the friction that can lead to gaps in test coverage, and helps teams adopt a quality-first mindset.

#### Use cases

* **Inline test generation**: Developers can ask Copilot to generate tests for a specific function or module without switching context.
* **Better edge case coverage**: By prompting Copilot for edge scenarios (such as null inputs, empty lists, or invalid states), developers can quickly cover more branches of logic.
* **Accelerated onboarding**: New team members can use Copilot to understand how a function is expected to behave by looking at the generated test cases.
* **Assistance with CI/CD**: Copilot can suggest how to integrate tests into your build pipeline, ensuring that coverage improvements directly support quality gates.

### Cultural considerations

Alongside your rollout of GitHub Copilot, address any social or cultural factors that could prevent you from achieving your goals.

The following examples are drawn from the "Anti-Patterns" section in the ESSP.

* Teams might **rely on manual testing** or insufficient automated testing. This could be caused by resource constraints for automation or a lack of experience with modern test tools.
* Teams might **wait too long to release**, deploying large batches of code at once, which makes bugs and regressions harder to detect. This could be caused by a lack of CI/CD pipeline maturity, strict compliance requirements, or long review cycles between PR and deployment.

## 3. Implement changes

When you've identified the right approach to overcome your barriers, scale the solutions you identified. For a successful rollout of a new tool or process, assign ownership to each part of the rollout, communicate transparently about your goals, provide effective training, and measure your outcomes.

This section provides example scenarios, best practices, and resources for developers. Use this section to **plan communications and training sessions** to help employees use Copilot in a way that aligns with your goal.

* [Generate tests inline](#generate-tests-inline)
* [Cover edge cases](#cover-edge-cases)
* [Understand new code](#understand-new-code)
* [Get assistance with CI/CD](#get-assistance-with-cicd)
* [Best practices for developers](#best-practices-for-developers)
* [Resources for developers](#resources-for-developers)
* [Recommended features](#recommended-features)

### Generate tests inline

1. In VS Code, select the function you want to test and prompt Copilot: `Generate a unit test for this code.`
2. Copilot generates a test inline or in a separate test file, depending on the language and structure.
3. Review, refine, and accept the suggestion.

### Cover edge cases

1. After writing a test, ask Copilot: `What are some edge cases I should test for this function?`

   Or: `Write test cases for when the input is null or empty.`

2. Copilot suggests additional test cases to cover boundary conditions.

3. Review the tests and incorporate them into your test suite.

### Understand new code

1. Select a legacy function and ask Copilot: `Explain what this function does and generate a test to validate it.`
2. Copilot explains the function's purpose and suggests corresponding test cases.
3. Look at the test cases to understand the expected behavior and quickly build context.

### Get assistance with CI/CD

1. Review your test cases and commit them to the codebase.
2. Ask Copilot: `Where should I place this test if I want it to run in CI?`
3. Based on the structure of the codebase, Copilot will suggest where to place test files and how to update pipeline configurations.

### Best practices for developers

Developers **should**:

* Use descriptive comments or prompts when chatting with Copilot. For example: `Generate unit tests for a function that calculates discounts based on user type and purchase amount.`
* Use Copilot to explore logic coverage. For example: `What branches or conditions does this function have that should be tested?`
* Explore different prompt techniques and compare results from different AI models.

Developers **should not**:

* Accept generated tests without reviewing logic. Make sure the tests reflect actual requirements and handle realistic inputs and outputs.
* Skip asserting edge behavior. If you only test "happy paths," you risk missing regressions.
* Rely on Copilot to guess undocumented business rules. Always provide context through prompts or comments.
* Treat Copilot as a substitute for human code reviews. Copilot accelerates the process, but you still need to apply engineering judgment.

### Resources for developers

* [Writing tests with GitHub Copilot](/en/copilot/using-github-copilot/guides-on-using-github-copilot/writing-tests-with-github-copilot)
* [How to generate unit tests with GitHub Copilot: Tips and examples](https://github.blog/ai-and-ml/github-copilot/how-to-generate-unit-tests-with-github-copilot-tips-and-examples/)
* [GitHub Copilot is EVERYWHERE in Visual Studio](https://learn.microsoft.com/en-us/shows/github-copilot-for-visual-studio/github-copilot-is-everywhere-in-visual-studio-miniseries) (video content with a section on testing)
* [Prompt engineering for GitHub Copilot Chat](/en/copilot/using-github-copilot/copilot-chat/prompt-engineering-for-copilot-chat)
* [Changing the AI model for GitHub Copilot Chat](/en/copilot/using-github-copilot/ai-models/changing-the-ai-model-for-copilot-chat)

### Recommended features

* [Copilot Chat in GitHub](/en/copilot/using-github-copilot/copilot-chat/asking-github-copilot-questions-in-github)
* [Copilot inline suggestions](/en/copilot/using-github-copilot/getting-code-suggestions-in-your-ide-with-github-copilot)
* [Copilot Chat in the IDE](/en/copilot/using-github-copilot/copilot-chat/asking-github-copilot-questions-in-your-ide)
* [Copilot cloud agent](/en/copilot/concepts/about-copilot-cloud-agent)

## Metrics to watch

To assess trials of new tools and make sure your full rollouts are delivering consistent improvements, monitor results and make adjustments when needed. We recommend considering the key zones of **quality, velocity, and developer happiness**, and how these zones come together to contribute to business outcomes.

Here are some metrics to assess Copilot's impact on this specific goal.

* **Test coverage**: Track increases in line and branch coverage after Copilot adoption. If possible, look at test coverage reports from your CI pipelines.
* **Bug rate after deployment**: Fewer bugs should be reported in production environments.
* **Developer confidence**: Use surveys or retrospectives to assess how confident developers feel shipping new code.
* **Time to write tests**: Measure reduction in time spent creating unit tests.