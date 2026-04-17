# Support for different types of custom instructions

Find out which environments support which types of custom instructions.

This reference article provides details of which types of custom instructions are supported in various environments. For more information about the various types of custom instructions for GitHub Copilot, see [About customizing GitHub Copilot responses](/en/copilot/concepts/prompting/response-customization).

## GitHub.com

<table>
  <thead>
    <tr>
      <th style="width: 25%">Copilot feature</th>
      <th>Types of custom instructions supported</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Copilot Chat </td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">👤</span> &nbsp;<strong>Personal</strong> instructions.</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">🏢</span> &nbsp;<strong>Organization</strong> instructions.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot cloud agent</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">🤖</span> &nbsp;<strong>Agent</strong> instructions (using <code>AGENTS.md</code>, <code>CLAUDE.md</code> or <code>GEMINI.md</code> files).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">🏢</span> &nbsp;<strong>Organization</strong> instructions.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot code review</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">🏢</span> &nbsp;<strong>Organization</strong> instructions.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Visual Studio Code

<table>
  <thead>
    <tr>
      <th style="width: 25%">Copilot feature</th>
      <th>Types of custom instructions supported</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Copilot Chat </td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">🤖</span> &nbsp;<strong>Agent</strong> instructions (using an <code>AGENTS.md</code> file).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot cloud agent</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">🤖</span> &nbsp;<strong>Agent</strong> instructions (using <code>AGENTS.md</code>, <code>CLAUDE.md</code> or <code>GEMINI.md</code> files).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot code review</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Visual Studio

<table>
  <thead>
    <tr>
      <th style="width: 25%">Copilot feature</th>
      <th>Types of custom instructions supported</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Copilot Chat </td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot code review</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## JetBrains IDEs

<table>
  <thead>
    <tr>
      <th style="width: 25%">Copilot feature</th>
      <th>Types of custom instructions supported</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Copilot Chat </td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot cloud agent</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">🤖</span> &nbsp;<strong>Agent</strong> instructions (using <code>AGENTS.md</code>, <code>CLAUDE.md</code> or <code>GEMINI.md</code> files).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot code review</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Eclipse

<table>
  <thead>
    <tr>
      <th style="width: 25%">Copilot feature</th>
      <th>Types of custom instructions supported</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Copilot Chat </td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot cloud agent</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">🤖</span> &nbsp;<strong>Agent</strong> instructions (using <code>AGENTS.md</code>, <code>CLAUDE.md</code> or <code>GEMINI.md</code> files).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot code review</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;">Custom instructions are currently not supported.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Xcode

<table>
  <thead>
    <tr>
      <th style="width: 25%">Copilot feature</th>
      <th>Types of custom instructions supported</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Copilot Chat </td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot cloud agent</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">🤖</span> &nbsp;<strong>Agent</strong> instructions (using <code>AGENTS.md</code>, <code>CLAUDE.md</code> or <code>GEMINI.md</code> files).</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Copilot code review</td>
      <td>
        <ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
          <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Copilot CLI

<ul style="list-style: none; padding-left: 1.5em; margin-left: 0;">
  <li style="text-indent: -1.6em;"><span aria-hidden="true">📦</span> &nbsp;<strong>Repository-wide</strong> instructions (using the <code>.github/copilot-instructions.md</code> file).</li>
  <li style="text-indent: -1.6em;"><span aria-hidden="true">📂</span> &nbsp;<strong>Path-specific</strong> instructions (using <code>.github/instructions/**/*.instructions.md</code> files).</li>
  <li style="text-indent: -1.6em;"><span aria-hidden="true">🤖</span> &nbsp;<strong>Agent</strong> instructions (using an <code>AGENTS.md</code> file).</li>
</ul>

## Further reading

* [Adding repository custom instructions for GitHub Copilot](/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
* [Adding personal custom instructions for GitHub Copilot](/en/copilot/how-tos/configure-custom-instructions/add-personal-instructions)
* [Adding organization custom instructions for GitHub Copilot](/en/copilot/how-tos/configure-custom-instructions/add-organization-instructions)