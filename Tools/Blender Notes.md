- [ ] MacOS Downloading **5.1.2** on *July 12th 2026*
- [ ] 

### To add an HDRi environment:
[Brandon3D Tutorial](https://brandon3d.com/hdri/) 
1. In the **World** properties panel tab, see **Surface** is set to **Background** by default
2. Open the **Shader** layout or open a **Shader** panel
3. Change from **Object** mode in the Shader Panel to **World** mode
4. Add an **Environment Texture** node
5. Open your **.exr** or **.hdr** texture
6. Select **Linear** and **Equirectangular**
7. Wire the **Color** output fo the **Environment Texture** node to the **Color** input of the **Background** node (leave that ouputting to **Color** of the **World Output** node)
8. Install **Node Wrangler** plugin and press **Ctrl+T** to generate inputs for the **Environment Texture** node. Or do the following steps manually
	1. Create a **Mapping** vector node as input to **Vector** on the **Environment Texture** node
	2. Create a **Texture Coordinate** node and wire it's **Generated** output to **Mapping**'s **Vector** input
9. Use the **Rotation Z-axis** on the **Mapping** node to rotate the HDRi texture
10. (In the **Viewport Shading** dropdown of the main viewport, select **Scene World** to show the HDRi)