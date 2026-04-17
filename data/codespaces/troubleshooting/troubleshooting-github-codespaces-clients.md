# Troubleshooting GitHub Codespaces clients

This article provides troubleshooting information for issues you may encounter with the client you use for GitHub Codespaces.

<div class="ghd-tool webui">

## Troubleshooting the Visual Studio Code web client

If you encounter issues using GitHub Codespaces in a browser that is not Chromium-based, try switching to a Chromium-based browser, such as Google Chrome or Microsoft Edge. Alternatively, check for known issues with your browser in the [`microsoft/vscode`](https://github.com/microsoft/vscode/issues?q=is%3Aissue+is%3Aopen) repository by searching for issues labeled with the name of your browser, such as [`firefox`](https://github.com/microsoft/vscode/issues?q=is%3Aissue+is%3Aopen+label%3Afirefox) or [`safari`](https://github.com/Microsoft/vscode/issues?q=is%3Aopen+is%3Aissue+label%3Asafari).

If you encounter issues using GitHub Codespaces in a Chromium-based browser, you can check if you're experiencing another known issue with VS Code in the [`microsoft/vscode`](https://github.com/microsoft/vscode/issues?q=is%3Aissue+is%3Aopen) repository.

### Differences from working in VS Code locally

When you open a codespace in your browser, using the VS Code web client, you will notice some differences from working in a local workspace in the VS Code desktop application. For example, some key bindings will be different or missing, and some extensions may behave differently. For a summary, see: [Known limitations and adaptions](https://code.visualstudio.com/docs/remote/codespaces#_known-limitations-and-adaptations) in the VS Code docs.

You can check for known issues and log new issues with the VS Code experience in the [`microsoft/vscode`](https://github.com/microsoft/vscode/issues?q=is%3Aissue+is%3Aopen+codespaces) repository.

### Visual Studio Code Insiders

Visual Studio Code Insiders is the most frequent release of VS Code. It has all the latest features and bug fixes, but may also occasionally contain new issues that result in a broken build.

If you are using an Insiders build and notice broken behavior, we recommend switching to Visual Studio Code Stable and trying again.

Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="Manage" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> in the bottom left of the editor and select **Switch to Stable Version...**. If the VS Code web client doesn't load, or <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="Manage" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> isn't available, you can force switching to Visual Studio Code Stable by appending `?vscodeChannel=stable` to your codespace URL and loading the codespace at that URL.

If the problem isn't fixed in Visual Studio Code Stable, check for known issues and, if required, log a new issue with the VS Code experience, in the [`microsoft/vscode`](https://github.com/microsoft/vscode/issues?q=is%3Aissue+is%3Aopen+codespaces) repository.

### Troubleshooting the Simple Browser

When you have started a web application in a codespace, you can preview the running application in the Simple Browser embedded in VS Code. In some projects, the application automatically opens in a Simple Browser tab in the editor when the application starts. This happens if, in the `devcontainer.json` configuration file for the codespace, the `onAutoForward` property of the port the application runs on is set to `openPreview`.

```json
"portsAttributes": {
  "3000": {
    "label": "Application",
    "onAutoForward": "openPreview"
  }
}
```

If the Simple Browser tab does not open automatically, you can open the Simple Browser manually to view the application.

1. In VS Code, click the **Ports** tab.
2. Right-click the port, then click **Preview in Editor**.

   ![Screenshot of the pop-up menu in the VS Code Ports tab. The menu entry "Preview in Editor" is highlighted with a dark orange outline.](/assets/images/help/codespaces/preview-in-editor-vscode.png)

#### The simple browser tab does not open automatically

If the `devcontainer.json` configuration file specifies `"onAutoForward": "openPreview"` for a port, but the Simple Browser does not open automatically when an application starts, check that the application has started on the port specified in the configuration. The application might start on a different port if the intended port is busy.

To implement the port configuration specified in `devcontainer.json`, GitHub Codespaces writes the configuration to VS Code's `settings.json` file when a codespace is created. You can check that the configuration has been correctly written to `settings.json` in your codespace.

1. In the terminal in your codespace, enter the following command.

   ```bash copy
   cat ~/.vscode-remote/data/Machine/settings.json
   ```

2. Verify that the `settings.json` file contains lines like the following.

   ```json
    "remote.portsAttributes": {
        "3000": {
            "label": "Application",
            "onAutoForward": "openPreview"
        }
    }
   ```

If the `settings.json` file doesn't contain these settings, check whether you have dotfiles enabled, and whether any configuration in your dotfiles is overwriting the `settings.json` file. For more information, see [Personalizing GitHub Codespaces for your account](/en/codespaces/setting-your-user-preferences/personalizing-github-codespaces-for-your-account#dotfiles).

#### The application does not load

Occasionally, you may find that the Simple Browser tab opens, but displays an error page icon or a blank page instead of your running application. This can happen if the web application you are loading includes a content security policy (CSP) that restricts the domains in which the site's pages may be embedded. For more information, see [CSP: frame-ancestors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) on the mdn website.

You may be able to change your application's `frame-ancestors` security policy locally to make the application display in the Simple Browser. Alternatively, if a `frame-ancestors` policy is causing the problem, you should be able to view the application by opening it in a regular browser tab rather than the simple browser. To do this, click the **Ports** tab in VS Code, right-click the port, and click **Open in Browser**.

</div>

<div class="ghd-tool vscode">

## VS Code troubleshooting

When you open a codespace in the VS Code desktop application, you may notice a few differences compared with working in a local workspace, but the experience should be similar.

If you encounter problems, you can check for known issues and log new issues with the VS Code experience in the [`microsoft/vscode`](https://github.com/microsoft/vscode/issues?q=is%3Aissue+is%3Aopen+codespaces) repository.

### Visual Studio Code Insiders

Visual Studio Code Insiders is the most frequent release of VS Code. It has all the latest features and bug fixes, but may also occasionally contain new issues that result in a broken build.

If you are using an Insiders build and notice broken behavior, we recommend switching to Visual Studio Code Stable and trying again.

To switch to Visual Studio Code Stable, close the Visual Studio Code Insiders application, open the Visual Studio Code Stable application, and re-open your codespace.

If the problem isn't fixed in Visual Studio Code Stable, check for known issues and, if required, log a new issue with the VS Code experience, in the [`microsoft/vscode`](https://github.com/microsoft/vscode/issues?q=is%3Aissue+is%3Aopen+codespaces) repository.

### Troubleshooting the Simple Browser

When you have started a web application in a codespace, you can preview the running application in the Simple Browser embedded in VS Code. In some projects, the application automatically opens in a Simple Browser tab in the editor when the application starts. This happens if, in the `devcontainer.json` configuration file for the codespace, the `onAutoForward` property of the port the application runs on is set to `openPreview`.

```json
"portsAttributes": {
  "3000": {
    "label": "Application",
    "onAutoForward": "openPreview"
  }
}
```

If the Simple Browser tab does not open automatically, you can open the Simple Browser manually to view the application.

1. In VS Code, click the **Ports** tab.
2. Right-click the port, then click **Preview in Editor**.

   ![Screenshot of the pop-up menu in the VS Code Ports tab. The menu entry "Preview in Editor" is highlighted with a dark orange outline.](/assets/images/help/codespaces/preview-in-editor-vscode.png)

#### The simple browser tab does not open automatically

If the `devcontainer.json` configuration file specifies `"onAutoForward": "openPreview"` for a port, but the Simple Browser does not open automatically when an application starts, check that the application has started on the port specified in the configuration. The application might start on a different port if the intended port is busy.

To implement the port configuration specified in `devcontainer.json`, GitHub Codespaces writes the configuration to VS Code's `settings.json` file when a codespace is created. You can check that the configuration has been correctly written to `settings.json` in your codespace.

1. In the terminal in your codespace, enter the following command.

   ```bash copy
   cat ~/.vscode-remote/data/Machine/settings.json
   ```

2. Verify that the `settings.json` file contains lines like the following.

   ```json
    "remote.portsAttributes": {
        "3000": {
            "label": "Application",
            "onAutoForward": "openPreview"
        }
    }
   ```

If the `settings.json` file doesn't contain these settings, check whether you have dotfiles enabled, and whether any configuration in your dotfiles is overwriting the `settings.json` file. For more information, see [Personalizing GitHub Codespaces for your account](/en/codespaces/setting-your-user-preferences/personalizing-github-codespaces-for-your-account#dotfiles).

#### The application does not load

Occasionally, you may find that the Simple Browser tab opens, but displays an error page icon or a blank page instead of your running application. This can happen if the web application you are loading includes a content security policy (CSP) that restricts the domains in which the site's pages may be embedded. For more information, see [CSP: frame-ancestors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) on the mdn website.

You may be able to change your application's `frame-ancestors` security policy locally to make the application display in the Simple Browser. Alternatively, if a `frame-ancestors` policy is causing the problem, you should be able to view the application by opening it in a regular browser tab rather than the simple browser. To do this, click the **Ports** tab in VS Code, right-click the port, and click **Open in Browser**.

</div>