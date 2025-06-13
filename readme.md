
# BlenderMCP - Blender Model Context Protocol Integration

BlenderMCP connects Blender to GithubCopilot through the Model Context Protocol (MCP), allowing GitHubCopilot to directly interact with and control Blender. This integration enables prompt assisted 3D modeling, scene creation, and manipulation.


## Installation


### Prerequisites

- Visual Studio Code: https://code.visualstudio.com/Download
- GitHub Copilot: https://aka.ms/github/copilot
- Blender 3.0 or newer: - https://www.blender.org/download/
- Python 3.10 or newer (steps below)
- uv package manager (steps below)
<br>

**If you're on a Mac, please open Terminal and run the following commands one by one:**
**1. Brew**
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then do following: - 
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc
```
```bash
eval "$(/opt/homebrew/bin/brew shellenv)"
```
**2. Python**
```bash
brew install python
```

**3. UV**
```bash
brew install uv
```


### Installing the Blender Addon

1. Open the [addon.py](https://raw.githubusercontent.com/ahujasid/blender-mcp/refs/heads/main/addon.py) file and save it.
1. Open Blender
2. Go to Edit > Preferences > Add-ons
3. Click "Install..." and select the saved `addon.py` file
4. Enable the addon by checking the box next to "Interface: Blender MCP"


### GitHub Copilot Integration
Go to **Visual Studio Code**:
1. Press `cmd + shift + p`
2. Select `MCP: Add Server`. 
3. Select Command(Stdio) and enter command `uvx blender-mcp`
4. add unique Identifier as `mcpServer` or anything**
5. Open Copilot chat in Visual Studio Code and start prompting!


Not: after that your Settings.json Should look like this: -
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



#### Capabilities

- Get scene and object information 
- Create, delete and modify shapes
- Apply or create materials for objects
- Execute any Python code in Blender
- Download the right models, assets and HDRIs through [Poly Haven](https://polyhaven.com/)
- AI generated 3D models through [Hyper3D Rodin](https://hyper3d.ai/)


### Example Commands

Here are some examples of what you can ask Claude to do:

- "Create a low poly scene in a dungeon, with a dragon guarding a pot of gold" [Demo](https://www.youtube.com/watch?v=DqgKuLYUv00)
- "Create a beach vibe using HDRIs, textures, and models like rocks and vegetation from Poly Haven" [Demo](https://www.youtube.com/watch?v=I29rn92gkC4)
- Give a reference image, and create a Blender scene out of it [Demo](https://www.youtube.com/watch?v=FDRb03XPiRo)
- "Generate a 3D model of a garden gnome through Hyper3D"
- "Get information about the current scene, and make a threejs sketch from it" [Demo](https://www.youtube.com/watch?v=jxbNI5L7AH8)
- "Make this car red and metallic" 
- "Create a sphere and place it above the cube"
- "Make the lighting like a studio"
- "Point the camera at the scene, and make it isometric"

## Limitations & Security Considerations

- The `execute_blender_code` tool allows running arbitrary Python code in Blender, which can be powerful but potentially dangerous. Use with caution in production environments. ALWAYS save your work before using it.
- Poly Haven requires downloading models, textures, and HDRI images. If you do not want to use it, please turn it off in the checkbox in Blender. 
- Complex operations might need to be broken down into smaller steps


## Disclaimer

This is a third-party integration and not made by Blender. Made by [Siddharth](https://x.com/sidahuj)
