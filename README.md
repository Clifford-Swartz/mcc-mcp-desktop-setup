# MPLAB AI Coding Assistant 2.0 + MCC MCP — setup kit

Everything needed to set up the AI Coding Assistant 2.0 with the MCC MCP tools on a Windows PC **without the Microchip VPN**. You need administrator rights on the PC to install the XC32 compiler. The installers are attached to this repo's [Releases](https://github.com/Clifford-Swartz/mcc-mcp-desktop-setup/releases/latest) page.

| File | What it is |
|---|---|
| `mplab-ai-coding-assistant-win32-x64-2.0.18.vsix` | MPLAB AI Coding Assistant 2.0 (Windows x64) |
| `mplab-mcp-tools-0.0.3-pre.30.vsix` | MCP Tools for MCC (pre-release) |
| `pic32cm_jh01_cnano_getting_started.zip` | Ready-made Harmony test project for the PIC32CM JH01 Curiosity Nano |

Everything else comes from the public VS Code Marketplace.

## 1. Install VS Code and the MPLAB extensions

1. Install [Visual Studio Code](https://code.visualstudio.com/).
2. Open the Extensions view (`Ctrl+Shift+X`), search for **MPLAB Extension Pack**, and select **Install**. This brings in MCC, the toolchain manager, and the other MPLAB extensions.

## 2. Install the two VSIX files

Download both `.vsix` files from [Releases](https://github.com/Clifford-Swartz/mcc-mcp-desktop-setup/releases/latest). For each one:

1. Open the Command Palette (`Ctrl+Shift+P`).
2. Run **Extensions: Install from VSIX…** and select the file.

Install the AI Coding Assistant first, then MCP Tools. No reload is usually needed.

## 3. Open a Harmony project

MCP Tools only works with **MCC Harmony projects on 32-bit Cortex devices**.

1. Unzip `pic32cm_jh01_cnano_getting_started.zip` from Releases (or use your own Harmony project).
2. In VS Code, select **File > Open Folder…** and open the unzipped folder.
3. If a **Restricted Mode** banner appears at the top, select **Manage**, then **Trust**. The MPLAB extensions don't run in Restricted Mode.

## 4. Let VS Code install the XC32 compiler

When the project opens, MPLAB reports that the configuration uses XC32, which is not installed. Select **xc32 — Download and install**. VS Code downloads the XC32 installer and runs it; approve the Windows administrator prompt when it appears.

## 5. Start the MCC MCP tools

1. Wait for the notification **MCP Server started on http://localhost:7777/mcp**.
2. Open the **MCP Tools** view (MCP icon in the Activity Bar). Under **Project Rules**, select **Add Rules**. This adds an instruction file that tells the AI assistant to configure peripherals through MCC instead of writing code by hand.
3. Open the **MPLAB AI Coding Assistant** (AI icon in the Activity Bar) and select **Connect to Microchip** to sign in.
4. Restart or reconnect the assistant so it picks up the MCC tools.

## 6. Try it

Ask the assistant, one at a time:

- "Show me the current project information."
- "List the components in the MCC configuration."
- "Add a UART at 115200 baud and generate code."
- "Build the project."

## Troubleshooting

- **XC32 install fails:** the installer needs administrator rights. On a managed work PC, ask IT to install MPLAB XC32 instead.
- **No MPLAB icons in the Activity Bar:** the folder is in Restricted Mode. Trust it (step 3).
- **"No project is open":** open exactly one project folder in one VS Code window.
- **MCC tools time out the first time:** MCC can take several minutes to start on first use. Wait, then ask again.
- **Port 7777 already in use:** run **MPLAB MCP TOOLS: Change Server port** from the Command Palette, then reconnect the assistant.
- **MCP Tools rewrites shared settings:** each time it starts, it updates the MCP settings for Claude Code, Continue/MPLAB AI, GitHub Copilot and Cursor in your user folder to point at its port. That's expected.

---
Pre-release software for evaluation. Questions: clifford.swartz@microchip.com
