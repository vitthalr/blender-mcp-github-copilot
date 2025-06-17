# BlenderMCP - Blender Model Context Protocol Integration

BlenderMCP connects Blender to GitHub Copilot through the Model Context Protocol (MCP), allowing GitHub Copilot to directly interact with and control Blender. This integration enables prompt-assisted 3D modeling, scene creation, and manipulation.

## Table of Contents
- [Installation](#installation)
  - [Prerequisites](#prerequisites)
  - [Installing the Blender Addon](#installing-the-blender-addon)
  - [GitHub Copilot Integration](#github-copilot-integration)
- [Capabilities](#capabilities)
- [Example Commands](#example-commands)
- [Limitations & Security Considerations](#limitations--security-considerations)
- [Disclaimer](#disclaimer)

## Installation

### Prerequisites

- <a href="https://code.visualstudio.com/Download" target="_blank">Visual Studio Code</a>
- <a href="https://aka.ms/github/copilot" target="_blank">GitHub Copilot</a>
- <a href="https://www.blender.org/download/" target="_blank">Blender 3.0 or newer</a>
- Python 3.10 or newer (installation steps below)
- UV package manager (installation steps below)

#### macOS Installation

If you're on a Mac, please open Terminal and run the following commands one by one:

**1. Install Homebrew**
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then configure Homebrew: 
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc
```
```bash
eval "$(/opt/homebrew/bin/brew shellenv)"
```

**2. Install Python**
```bash
brew install python
```

**3. Install UV**
```bash
brew install uv
```

#### Windows Installation

If you're on Windows, please open PowerShell and run the following commands one by one:

**1. Install Python**
```powershell
winget install -e --id Python.Python.3.11
```

**2. Install UV**
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex" 
```

Then add UV to your PATH:
```powershell
$env:Path = "C:\Users\$env:USERNAME\.local\bin;$env:Path"
```

For other operating systems, installation instructions are available on the UV website: <a href="https://docs.astral.sh/uv/getting-started/installation/" target="_blank">Install UV</a>

### Installing the Blender Addon

1. Download the `addon.py` file from <a href="https://raw.githubusercontent.com/ahujasid/blender-mcp/refs/heads/main/addon.py" target="_blank">this link</a> and save it to your computer
2. Open Blender
3. Go to Edit > Preferences > Add-ons
4. Click "Install..." and select the saved `addon.py` file
5. Enable the addon by checking the box next to "Interface: Blender MCP"

### GitHub Copilot Integration

Go to Visual Studio Code:
1. Press `Cmd + Shift + P` (macOS) or `Ctrl + Shift + P` (Windows/Linux)
2. Select `MCP: Add Server`
3. Select "Command (Stdio)" and enter command `uvx blender-mcp`
4. Add a unique identifier such as `mcpServer`
5. Open Copilot chat in Visual Studio Code and start prompting!

After setup, your `settings.json` should contain something like this:
```json
{
    "mcpServer": {
        "blender": {
            "command": "uvx",
            "args": [
                "blender-mcp"
            ]
        }
    }
}
```

### Capabilities

BlenderMCP allows GitHub Copilot to:

- Get scene and object information
- Create, delete, and modify 3D shapes
- Apply or create materials for objects
- Execute any Python code in Blender
- Download models, assets, and HDRIs through <a href="https://polyhaven.com/" target="_blank">Poly Haven</a>
- Generate AI-powered 3D models through <a href="https://hyper3d.ai/" target="_blank">Hyper3D Rodin</a>

### Example Commands

Here are some examples of what you can ask GitHub Copilot to do:

- "Create a low poly scene in a dungeon, with a dragon guarding a pot of gold" - <a href="https://www.youtube.com/watch?v=DqgKuLYUv00" target="_blank">Demo</a>
- "Create a beach vibe using HDRIs, textures, and models like rocks and vegetation from Poly Haven" - <a href="https://www.youtube.com/watch?v=I29rn92gkC4" target="_blank">Demo</a>
- "Given this reference image, create a Blender scene that matches it" - <a href="https://www.youtube.com/watch?v=FDRb03XPiRo" target="_blank">Demo</a>
- "Generate a 3D model of a garden gnome through Hyper3D"
- "Get information about the current scene, and make a three.js sketch from it" - <a href="https://www.youtube.com/watch?v=jxbNI5L7AH8" target="_blank">Demo</a>
- "Make this car red and metallic" 
- "Create a sphere and place it above the cube"
- "Make the lighting look like a professional studio"
- "Point the camera at the scene, and make it isometric"

## Limitations & Security Considerations

- The `execute_blender_code` tool allows running arbitrary Python code in Blender, which can be powerful but potentially dangerous. Use with caution in production environments. **ALWAYS save your work before using it**.
- Poly Haven requires downloading models, textures, and HDRI images. If you do not want to use this feature, you can disable it in the Blender MCP addon's preferences panel within Blender (Edit > Preferences > Add-ons > Interface: Blender MCP).
- Complex operations might need to be broken down into smaller steps for best results.

## Disclaimer

This is a third-party integration and not officially made or endorsed by Blender. Developed by <a href="https://x.com/sidahuj" target="_blank">Siddharth</a>.
