# User prompt transformed hook

The userPromptTransformed hook runs after the runtime adds generated context to a submitted prompt, but before the resulting content is persisted to session history or sent to the model.

<!-- markdownlint-disable GHD046 GHD005 -->
<!-- Suppressed: GHD046 (outdated release terminology), GHD005 (hardcoded data variable) -->

Use it when you need to inspect or replace the exact model-facing prompt. The `prompt` input contains the user prompt after any `userPromptSubmitted` hooks have run, while `transformedPrompt` also contains runtime-generated context such as `<current_datetime>`.

## Input and output

| Input field | Type | Description |
| --- | --- | --- |
| `sessionId` | string | Runtime session ID |
| `timestamp` | date/time | Time the hook was invoked |
| `cwd` / `workingDirectory` | string | Current working directory |
| `prompt` | string | Prompt after `userPromptSubmitted` hooks |
| `transformedPrompt` | string | Model-facing prompt after runtime transformations |

Return no value to leave the transformed prompt unchanged. Return `modifiedTransformedPrompt` to replace the content that is stored in session history and sent to the model.

## Examples

<div class="ghd-codetabs">
<div class="ghd-codetab" data-lang="typescript" data-label="TypeScript"><div class="ghd-codetab-fallback-label" role="heading" aria-level="3">TypeScript</div>

<!-- docs-validate: skip -->

```typescript
const session = await client.createSession({
  hooks: {
    onUserPromptTransformed: async (input) => ({
      modifiedTransformedPrompt: redact(input.transformedPrompt),
    }),
  },
});
```

</div>

<div class="ghd-codetab" data-lang="python" data-label="Python"><div class="ghd-codetab-fallback-label" role="heading" aria-level="3">Python</div>

<!-- docs-validate: skip -->

```python
session = await client.create_session(
    hooks={
        "on_user_prompt_transformed": lambda input_data, invocation: {
            "modifiedTransformedPrompt": redact(input_data["transformedPrompt"])
        }
    }
)
```

</div>

<div class="ghd-codetab" data-lang="go" data-label="Go"><div class="ghd-codetab-fallback-label" role="heading" aria-level="3">Go</div>

<!-- docs-validate: skip -->

```golang
session, err := client.CreateSession(ctx, &copilot.SessionConfig{
	Hooks: &copilot.SessionHooks{
		OnUserPromptTransformed: func(input copilot.UserPromptTransformedHookInput, invocation copilot.HookInvocation) (*copilot.UserPromptTransformedHookOutput, error) {
			return &copilot.UserPromptTransformedHookOutput{
				ModifiedTransformedPrompt: copilot.String(redact(input.TransformedPrompt)),
			}, nil
		},
	},
})
```

</div>

<div class="ghd-codetab" data-lang="dotnet" data-label=".NET"><div class="ghd-codetab-fallback-label" role="heading" aria-level="3">.NET</div>

<!-- docs-validate: skip -->

```csharp
var session = await client.CreateSessionAsync(new SessionConfig
{
    Hooks = new SessionHooks
    {
        OnUserPromptTransformed = (input, invocation) =>
            Task.FromResult<UserPromptTransformedHookOutput?>(new()
            {
                ModifiedTransformedPrompt = Redact(input.TransformedPrompt),
            }),
    },
});
```

</div>

<div class="ghd-codetab" data-lang="java" data-label="Java"><div class="ghd-codetab-fallback-label" role="heading" aria-level="3">Java</div>

<!-- docs-validate: skip -->

```java
var hooks = new SessionHooks().setOnUserPromptTransformed((input, invocation) ->
    CompletableFuture.completedFuture(
        new UserPromptTransformedHookOutput(redact(input.transformedPrompt()))));

var session = client.createSession(new SessionConfig().setHooks(hooks)).get();
```

</div>

<div class="ghd-codetab" data-lang="rust" data-label="Rust"><div class="ghd-codetab-fallback-label" role="heading" aria-level="3">Rust</div>

```rust
#[async_trait]
impl SessionHooks for MyHooks {
    async fn on_user_prompt_transformed(
        &self,
        input: UserPromptTransformedInput,
        _ctx: HookContext,
    ) -> Option<UserPromptTransformedOutput> {
        Some(UserPromptTransformedOutput {
            modified_transformed_prompt: Some(redact(&input.transformed_prompt)),
        })
    }
}

let session = client
    .create_session(SessionConfig::default().with_hooks(Arc::new(MyHooks)))
    .await?;
```

</div>

</div>

The replacement is persisted as the user message content, so resumed sessions replay the modified content unchanged.