<div align="center">

<img height="110" src="LynxHubIcon.png" alt="LynxHub Icon">

# [LynxHub](https://github.com/KindaBrazy/LynxHub) Extension Development Guide

Comprehensive guide for creating extensions for LynxHub.

</div>

---

## Table of Contents

- [Setup Environment](#setup-environment)
- [Developing an Extension](#developing-an-extension)
- [Extension Configuration and API Reference](#extension-configuration-and-api-reference)
    - [Renderer Tips: `Extension.tsx`](#renderer-tips-extensiontsx)
    - [Main Tips: `lynxExtension.ts`](#main-tips-lynxextensionts)

---

## Setup Environment

Follow these steps to prepare your environment for developing and testing LynxHub extensions:

1. **[Set up the LynxHub Development Environment][lynxhub-dev-env]**
2. **[Start Developing Your Extension](#developing-an-extension)**

---

## Developing an Extension

### Step 1: Configure Extension Details

- Edit the [`lynxExtension.json`][lynx-extension-json] file with your extension's metadata and configuration.

### Step 2: Implement Renderer Functionality

- Modify the [`Extension.tsx`][extension-tsx] file.
- Refer to [Renderer Tips: `Extension.tsx`](#renderer-tips-extensiontsx) for best practices.

### Step 3: Implement Main Process Functionality

- Modify the [`lynxExtension.ts`][lynx-extension-ts] file.
- Refer to [Main Tips: `lynxExtension.ts`](#main-tips-lynxextensionts) for best practices.

### Step 4: Test Your Extension

- Start the development server:
  ```bash
  npm run dev
  ```

### Step 5: Build Your Extension

- Run the following command to build your extension:
  ```bash
  npm run build:extension
  ```
- Copy `lynxExtension.json` to a custom folder in LynxHub's `extensions` directory.
- Inside your custom folder:
    - Create a `scripts` folder.
    - Move the `main` and `renderer` folders from the `extOut` directory to the `scripts` folder.

> [!IMPORTANT]
> Ensure the following structure for LynxHub to recognize your extension:
>
> **Extension Root Folder**
> - `lynxExtension.json`
> - `scripts/`
>   - `main/`
>     - `mainEntry.mjs`
>   - `renderer/`
>     - `rendererEntry.mjs`

---

## Extension Configuration and API Reference

For details on available types and APIs, refer to:

- [`ExtensionTypes_Main.ts`][extension-types-main]
- [`ExtensionTypes_Renderer_Api.ts`][extension-types-renderer-api]

---

### Renderer Tips: `Extension.tsx`

- **Mandatory Export**: The file must export an `InitialExtensions` method.
- **Example Implementation**: A basic implementation is provided in the InitialExtensions method for you to use as a
  reference or starting point.
- **Execution Context**: Runs in the Electron renderer process (browser-like environment).
- **Purpose**: Executes in the Electron renderer process (browser environment).

---

### Main Tips: `lynxExtension.ts`

- **Mandatory Export**: The file must export an `initialExtension` method.
- **Example Implementation**: A basic implementation is provided in the initialExtension method for you to use as a
  reference or starting point.
- **Execution Context**: Runs in the Electron main process (Node.js environment).
- **Purpose**: Executes in the Electron main process (Node.js environment)

[lynxhub-dev-env]:https://github.com/KindaBrazy/LynxHub?tab=readme-ov-file#-development

[lynx-extension-json]:https://github.com/KindaBrazy/LynxHub/blob/master/src/main/extension/lynxExtension.json

[extension-tsx]:https://github.com/KindaBrazy/LynxHub/blob/master/src/renderer/extension/Extension.tsx

[lynx-extension-ts]:https://github.com/KindaBrazy/LynxHub/blob/master/src/main/extension/lynxExtension.ts

[extension-types-main]:https://github.com/KindaBrazy/LynxHub/blob/master/src/main/Managements/Plugin/Extensions/ExtensionTypes_Main.ts

[extension-types-renderer-api]:https://github.com/KindaBrazy/LynxHub/blob/master/src/renderer/src/App/Extensions/ExtensionTypes_Renderer_Api.ts
