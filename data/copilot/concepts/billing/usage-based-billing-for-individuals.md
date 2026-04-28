# Usage-based billing for individuals

Your Copilot plan will include a monthly allowance of GitHub AI Credits. If you exhaust your AI credits, you can pay extra to keep working.

<!-- expires 2026-06-01 -->

> \[!IMPORTANT] GitHub will use the billing methods described in this article **starting June 1, 2026**. You can read more about this change on [the GitHub Blog](https://gh.io/copilot-billing-blog).

<!-- end expires 2026-06-01 -->

## What is usage-based billing?

All individual plans—Copilot Free, Copilot Pro, and Copilot Pro+—include GitHub AI Credits allowances that vary by plan. Paid plans offer higher limits than free plans.

## What are GitHub AI Credits?

GitHub AI Credits are the billing unit for Copilot usage.

When you use Copilot, the interaction consumes tokens: input tokens (what's sent to the model), output tokens (what the model generates), and cached tokens (context the model reuses or stores). Each token is priced based on the model used, and the total is converted into AI credits, where 1 AI credit = $0.01 USD.

The cost of an interaction depends on two things: the model and the number of tokens consumed. A quick chat question using a lightweight model might cost a fraction of a credit. A long coding agent session using a frontier model across multiple files will cost more, because it's doing more work.

## What affects my usage?

More complex interactions consume more of your usage allowance. The main factors are:

* **Conversation length and complexity**: Longer conversations and more elaborate tasks involve more back-and-forth with the model, consuming more.
* **Agentic features**: Features like agent mode and Copilot cloud agent can involve multiple model calls within a single task. A complex agentic session working across a large codebase will consume significantly more usage than a quick question in chat.
* **Model choice**: Different models have different costs per token. More capable models designed for complex reasoning cost more than lighter models suited to quick tasks. Switching to a less expensive model is one way to extend your usage allowance.

## What is billed in AI credits?

Copilot features that use AI models consume AI credits. This includes Copilot Chat, Copilot CLI, Copilot cloud agent, Copilot Spaces, Spark, and third-party coding agents.

Code completions and next edit suggestions are **not** billed in AI credits. They remain unlimited for all paid plans.

## How do AI credits work?

Each Copilot individual plan subscription includes a monthly AI credits allowance:

| Plan         | Total AI credits per month |
| ------------ | -------------------------- |
| Copilot Pro  | 1000                       |
| Copilot Pro+ | 3900                       |

## What happens if I exceed my included AI credits?

When your AI credits are exhausted, you can:

* Set a budget for additional usage and pay extra to continue working
* Wait until the next monthly cycle when your included usage resets

Your additional usage budget is set in US dollars, and your usage is shown in GitHub AI Credits. GitHub AI Credits draw down your budget at a fixed rate: 1 AI credits = $0.01 USD, so a $10 budget covers 1,000 AI credits.

## Do I need to prepare for usage-based billing?

For most existing individual plan subscribers, no action is required. Existing annual subscribers have a couple of options to choose from.

### If you're on a monthly plan

If you're on a monthly plan, **no action is required**. You'll be automatically migrated to usage-based billing on June 1st, 2026.

### If you're on an annual plan

If you're on an annual plan, your plan **will not auto-renew**. You'll receive communications from GitHub about your options before your annual renewal date.

You will have the option to:

* Cancel your plan and receive a prorated refund.
* Wait to be downgraded to Copilot Free at renewal time.

Note that, starting **June 1, 2026**, Copilot Pro and Copilot Pro+ subscribers on **existing annual billing plans** will experience changes to model multipliers. See [Models and pricing for GitHub Copilot](/en/copilot/reference/copilot-billing/models-and-pricing#model-multipliers-for-annual-copilot-pro-and-copilot-pro-subscribers).

## Next steps

* For guidance on how to prepare for usage-based billing, see [Preparing for your move to usage-based billing](/en/copilot/how-tos/manage-and-track-spending/prepare-for-your-move-to-usage-based-billing).