# HDRP_MASK_PACKER

A lightweight, browser-based utility designed to streamline the packing of grayscale PBR (Physically Based Rendering) maps into a single RGBA texture for **Unity HDRP**.

Stop wasting VRAM on multiple single-channel textures. Pack your data, preview your results in 3D, and export—all in one place.

## The Channel Mapping

The tool strictly adheres to the standard Unity HDRP Mask Map configuration:

| Channel | Map Purpose | Default Value |
| --- | --- | --- |
| **Red (R)** | **Metallic** | Black (0) |
| **Green (G)** | **Ambient Occlusion** | White (1) |
| **Blue (B)** | **Detail Mask** | Black (0) |
| **Alpha (A)** | **Smoothness** | White (1) |

## Key Features

* **Drag-and-Drop Workflow:** Quickly assign your maps to channels. No complex image editing software required.
* **3D Real-time Preview:** Verify your material's look using the built-in `Three.js` viewport. Switch between shapes (Sphere, Cube, Torus, Plane) and lighting presets (Studio, Dramatic, Outdoor, etc.).
* **Smart Preprocessing:**
* **Invert Alpha:** Toggle this to quickly convert Height maps into Smoothness maps.
* **Luma Calculation:** Allows for accurate grayscale conversion from color inputs.
* **Normal Map Flipping:** Fix shading issues on the fly by toggling the Green channel (essential for reconciling OpenGL/DirectX differences).


* **Export Flexibility:** Support for high-quality PNG or uncompressed 32-bit TGA formats.
* **Resolution Control:** Override source resolution for target-platform optimization.

## How to Use

1. **Load:** Drop your grayscale maps into the corresponding R, G, B, and A zones.
2. **Preview:** Use the 3D Viewport on the right to inspect your material. Swap lighting presets to ensure your roughness/metallic values react as expected.
3. **Adjust:** Toggle options like "Invert Alpha" or "Flip Normal G" if your preview looks physically incorrect.
4. **Execute:** Click `[ EXECUTE_PACK_DOWNLOAD ]`. The tool will composite the channels and trigger a browser download for the packed file.

## Technical Notes

* **Browser-Based:** Runs entirely in your browser using local canvas processing. No files are uploaded to a server; your data stays local.
* **Compatibility:** Designed for Unity HDRP `Mask Map` slots.
* **Normal Map Note:** The Normal map zone is for **preview purposes only**. The packer does not include the Normal map in the final channel-packed file, as Normals typically require their own dedicated high-precision map.