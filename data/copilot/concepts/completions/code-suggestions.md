# GitHub Copilot code suggestions in your IDE

Learn about Copilot code suggestions in different IDEs.

<div class="ghd-tool vscode">

## About code suggestions in Visual Studio Code

Copilot in Visual Studio Code provides two kinds of code suggestions:

* **Next edit suggestions**

  Based on the edits you are making, Copilot both predicts the location of the next edit you'll want to make and what that edit should be. To enable next edit suggestions, see [Configuring GitHub Copilot in your environment](/en/copilot/managing-copilot/configure-personal-settings/configuring-github-copilot-in-your-environment#enabling-next-edit-suggestions).

* **Ghost text suggestions**

  Copilot offers coding suggestions as you type. Start typing in the editor, and Copilot provides dimmed ghost text suggestions at your current cursor location. You can also describe something you want to do using natural language within a comment, and Copilot will suggest the code to accomplish your goal.

GitHub Copilot provides suggestions for numerous languages and a wide variety of frameworks, but works especially well for Python, JavaScript, TypeScript, Ruby, Go, C# and C++. GitHub Copilot can also assist in query generation for databases, generating suggestions for APIs and frameworks, and can help with infrastructure as code development.

</div>

<div class="ghd-tool jetbrains">

## About code suggestions in JetBrains IDEs

Copilot offers inline suggestions as you type.

GitHub Copilot provides suggestions for numerous languages and a wide variety of frameworks, but works especially well for Python, JavaScript, TypeScript, Ruby, Go, C# and C++. GitHub Copilot can also assist in query generation for databases, generating suggestions for APIs and frameworks, and can help with infrastructure as code development.

</div>

<div class="ghd-tool visualstudio">

## About code suggestions in Visual Studio

Copilot in Visual Studio provides two kinds of code suggestions:

* **Ghost text suggestions**

  Copilot offers coding suggestions as you type.

* **Next edit suggestions (public preview)**

  Based on the edits you are making, Copilot will predict the location of the next edit you are likely to make and suggest a completion for it. Suggestions may span a single symbol, an entire line, or multiple lines, depending on the scope of the potential change. To enable next edit suggestions, see [Configuring GitHub Copilot in your environment](/en/copilot/managing-copilot/configure-personal-settings/configuring-github-copilot-in-your-environment#enabling-next-edit-suggestions).

GitHub Copilot provides suggestions for numerous languages and a wide variety of frameworks, but works especially well for Python, JavaScript, TypeScript, Ruby, Go, C# and C++. GitHub Copilot can also assist in query generation for databases, generating suggestions for APIs and frameworks, and can help with infrastructure as code development.

</div>

<div class="ghd-tool vimneovim">

## About code suggestions in Vim/Neovim

GitHub Copilot provides inline suggestions as you type in Vim/Neovim.

</div>

<div class="ghd-tool azure_data_studio">

## About code suggestions in Azure Data Studio

GitHub Copilot provides you with inline suggestions as you create SQL databases in Azure Data Studio.

</div>

<div class="ghd-tool xcode">

## About code suggestions in Xcode

GitHub Copilot in Xcode provides two kinds of code suggestions:

* **Ghost text suggestions**
  * Copilot offers coding suggestions as you type. You can also describe something you want to do using natural language within a comment, and Copilot will suggest the code to accomplish your goal.
* **Next edit suggestions (public preview)**
  * Based on the edits you are making, Copilot will predict the location of the next edit you are likely to make and suggest a completion for it. Suggestions may span an entire line, or multiple lines, depending on the scope of the potential change. Next edit suggestions are enabled by default. To disable, see [Configuring GitHub Copilot in your environment](/en/copilot/how-tos/configure-personal-settings/configure-in-ide?tool=xcode#enabling-next-edit-suggestions-2).

</div>

<div class="ghd-tool eclipse">

## About code suggestions in Eclipse

GitHub Copilot in Eclipse provides two kinds of code suggestions:

* **Ghost text suggestions**
  * Copilot offers coding suggestions as you type. You can also describe something you want to do using natural language within a comment, and Copilot will suggest the code to accomplish your goal.
* **Next edit suggestions (public preview)**
  * Based on the edits you are making, Copilot will predict the location of the next edit you are likely to make and suggest a completion for it. Suggestions may span a single symbol, an entire line, or multiple lines, depending on the scope of the potential change. To enable next edit suggestions, see [Configuring GitHub Copilot in your environment](/en/copilot/how-tos/configure-personal-settings/configure-in-ide?tool=eclipse#enabling-next-edit-suggestions-3).

GitHub Copilot provides suggestions for numerous languages and a wide variety of frameworks, but works especially well for Python, JavaScript, TypeScript, Ruby, Go, C# and C++. GitHub Copilot can also assist in query generation for databases, generating suggestions for APIs and frameworks, and can help with infrastructure as code development.

</div>

## Code suggestions that match public code

GitHub Copilot checks each suggestion for matches with publicly available code. Matches may be discarded or suggested with a code reference, based on the setting of the "Suggestions matching public code" policy for your account or organization. See [GitHub Copilot code referencing](/en/copilot/concepts/completions/code-referencing).

<div class="ghd-tool vscode">

## Changing the model used for inline suggestions

You can switch the AI model that's used for Copilot inline suggestions if:

* An alternative model is currently available
* You are using the latest releases of VS Code with the latest version of the GitHub Copilot extension

Changing the model only affects Copilot ghost text suggestions. It does not affect Copilot next edit suggestions.

> \[!NOTE] The list of available models will change over time. When only one model is available for inline suggestions, the model picker will only show that model. Preview models and additional models will be added to the picker as they become available.

For details of how to switch the model for Copilot inline suggestions, see [Changing the AI model for GitHub Copilot inline suggestions](/en/copilot/how-tos/use-ai-models/change-the-completion-model).

## Effects of switching the AI model

Changing the model that's used for Copilot inline suggestions does not affect the model that's used by Copilot next edit suggestions or Copilot Chat. See [Changing the AI model for GitHub Copilot Chat](/en/copilot/using-github-copilot/ai-models/changing-the-ai-model-for-copilot-chat).

There are no changes to the data collection and usage policy if you change the AI model.

If you are on a Copilot Free plan, all completions count against your completions quota regardless of the model used. See [Plans for GitHub Copilot](/en/copilot/about-github-copilot/subscription-plans-for-github-copilot#comparing-copilot-subscriptions).

The setting to enable or disable suggestions that match public code is applied irrespective of which model you choose. See [Finding public code that matches GitHub Copilot suggestions](/en/copilot/using-github-copilot/finding-public-code-that-matches-github-copilot-suggestions).

## Enabling the model switcher

If you have a Copilot Free or Copilot Pro plan, the model switcher for Copilot inline suggestions is automatically enabled.

If you're using a Copilot Business or Copilot Enterprise plan, the organization or enterprise that provides your plan must enable the **Editor preview features** setting. See [Managing policies and features for GitHub Copilot in your organization](/en/enterprise-cloud@latest/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-policies-for-copilot-in-your-organization#enabling-copilot-features-in-your-organization) or [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-policies-and-features-for-copilot-in-your-enterprise#configuring-policies-for-github-copilot).

</div>

<div class="ghd-tool visualstudio">

## Changing the model used for inline suggestions

You can switch the AI model that's used for Copilot inline suggestions if:

* An alternative model is currently available
* You are using Visual Studio 17.14 Preview 2 or later

> \[!NOTE] The list of available models will change over time. When only one model is available for inline suggestions, the model picker will only show that model. Preview models and additional models will be added to the picker as they become available.

For details of how to switch the model for Copilot inline suggestions, see [Changing the AI model for GitHub Copilot inline suggestions](/en/copilot/how-tos/use-ai-models/change-the-completion-model).

## Effects of switching the AI model

Changing the model that's used for Copilot inline suggestions does not affect the model that's used by Copilot next edit suggestions or Copilot Chat. See [Changing the AI model for GitHub Copilot Chat](/en/copilot/using-github-copilot/ai-models/changing-the-ai-model-for-copilot-chat).

There are no changes to the data collection and usage policy if you change the AI model.

If you are on a Copilot Free plan, all completions count against your completions quota regardless of the model used. See [Plans for GitHub Copilot](/en/copilot/about-github-copilot/subscription-plans-for-github-copilot#comparing-copilot-subscriptions).

The setting to enable or disable suggestions that match public code is applied irrespective of which model you choose. See [Finding public code that matches GitHub Copilot suggestions](/en/copilot/using-github-copilot/finding-public-code-that-matches-github-copilot-suggestions).

## Enabling the model switcher

If you have a Copilot Free or Copilot Pro plan, the model switcher for Copilot inline suggestions is automatically enabled.

If you're using a Copilot Business or Copilot Enterprise plan, the organization or enterprise that provides your plan must enable the **Editor preview features** setting. See [Managing policies and features for GitHub Copilot in your organization](/en/enterprise-cloud@latest/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-policies-for-copilot-in-your-organization#enabling-copilot-features-in-your-organization) or [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-policies-and-features-for-copilot-in-your-enterprise#configuring-policies-for-github-copilot).

</div>

<div class="ghd-tool jetbrains">

## Changing the model used for inline suggestions

You can switch the AI model that's used for Copilot inline suggestions if:

* An alternative model is currently available
* You are using the latest release of JetBrains IDEs with the latest version of the GitHub Copilot extension

> \[!NOTE] The list of available models will change over time. When only one model is available for inline suggestions, the model picker will only show that model. Preview models and additional models will be added to the picker as they become available.

For details of how to switch the model for Copilot inline suggestions, see [Changing the AI model for GitHub Copilot inline suggestions](/en/copilot/how-tos/use-ai-models/change-the-completion-model).

## Effects of switching the AI model

Changing the model that's used for Copilot inline suggestions does not affect the model that's used by Copilot next edit suggestions or Copilot Chat. See [Changing the AI model for GitHub Copilot Chat](/en/copilot/using-github-copilot/ai-models/changing-the-ai-model-for-copilot-chat).

There are no changes to the data collection and usage policy if you change the AI model.

If you are on a Copilot Free plan, all completions count against your completions quota regardless of the model used. See [Plans for GitHub Copilot](/en/copilot/about-github-copilot/subscription-plans-for-github-copilot#comparing-copilot-subscriptions).

The setting to enable or disable suggestions that match public code is applied irrespective of which model you choose. See [Finding public code that matches GitHub Copilot suggestions](/en/copilot/using-github-copilot/finding-public-code-that-matches-github-copilot-suggestions).

## Enabling the model switcher

If you have a Copilot Free or Copilot Pro plan, the model switcher for Copilot inline suggestions is automatically enabled.

If you're using a Copilot Business or Copilot Enterprise plan, the organization or enterprise that provides your plan must enable the **Editor preview features** setting. See [Managing policies and features for GitHub Copilot in your organization](/en/enterprise-cloud@latest/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-policies-for-copilot-in-your-organization#enabling-copilot-features-in-your-organization) or [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/managing-copilot/managing-copilot-for-your-enterprise/managing-policies-and-features-for-copilot-in-your-enterprise#configuring-policies-for-github-copilot).

</div>

## Programming languages included in the default model

The following programming languages and technologies are included in the training data for the default LLM used for Copilot inline suggestions:

* C
* C#
* C++
* Clojure
* CSS
* Dart
* Dockerfile
* Elixir
* Emacs Lisp
* Go
* Haskell
* HTML
* Java
* JavaScript
* Julia
* Jupyter Notebook
* Kotlin
* Lua
* MATLAB
* Objective-C
* Perl
* PHP
* PowerShell
* Python
* R
* Ruby
* Rust
* Scala
* Shell
* Swift
* TeX
* TypeScript
* Vue

## Next steps

* [Getting code suggestions in your IDE with GitHub Copilot](/en/copilot/how-tos/completions/getting-code-suggestions-in-your-ide-with-github-copilot)