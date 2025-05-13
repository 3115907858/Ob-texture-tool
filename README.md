# Oblivion Remastered Texture Processor 

A simple tool for texture processing written in Python and Opencv to quickly split and merge multi-channel composite textures in Oblivion Remastered.

## Features

- **Texture Splitting**: Split composite PBR textures into separate component channels
- **Texture Merging**: Combine separate component channels into composite PBR textures
- **Support for Multiple Texture Types**:
  - NNRM (Normal+Roughness+Metallic)
  - NNRE (Normal+Roughness+Emissive)
  - NNR (Normal+Roughness)
  - NNRAO (Normal+Roughness+Ambient Occlusion)
  - NNRS (Normal+Roughness+Specular)
  - NNAoO (Normal+Ambient Occlusion+Opacity)
- **Intuitive Interface**: Clean dark-themed UI with real-time preview thumbnails
- **Custom Normal Map Processing**: B-channel processing options (fill white or calculate Z component)

## Usage

### Splitting Textures

1. Select the "Split Textures" operation mode
2. Choose the texture type to process (NNRM, NNRE, NNR, etc.)
3. Click the "Browse" button to select the source texture file (ensure the filename ends with `_TextureType.png`, e.g., `brick_NNRM.png`)
4. Select the B-channel of Normal Map processing method:
   - **Fill White**: Fill the B channel of the normal map with white (255)
   - **Calculate Z**: Calculate the Z component from the X and Y channels
5. Click "Start Processing" to begin

The application will create separate component files, such as:
- `brick_N.png` (Normal map)
- `brick_R.png` (Roughness map)
- `brick_M.png` (Metallic map, for NNRM only)

### Merging Textures

1. Select the "Merge Textures" operation mode
2. Choose the texture type to create (NNRM, NNRE, NNR, etc.)
3. Select the corresponding file for each required component (e.g., N, R, M)
4. Click "Start Processing" to begin

The application will create a merged texture file, e.g., `brick_NNRM.png`

## File Naming Conventions

To ensure the application works correctly, please follow these file naming conventions:

- **Source Textures**: `basename_TextureType.png` (e.g., `brick_NNRM.png`)
- **Split Components**: `basename_Component.png` (e.g., `brick_N.png`, `brick_R.png`)

The application relies on these naming conventions to properly identify and process files.

## Notes

1. **Image Channel Requirements**:
   - In split mode, ensure the input file has the correct number of channels (3 or 4 channels)
   - In merge mode, the application will automatically convert grayscale images to the required channels

2. **Image Dimensions**:
   - When merging, if component images have different dimensions, the application will automatically resize them to match the dimensions of the first loaded component (typically the normal map)

3. **16-bit Image Support**:
   - The application can process 16-bit images but will convert them to 8-bit for operations
   - If you need to maintain 16-bit precision, consider using professional image editing software

4. **File Overwriting**:
   - Before processing, the application will check if output files with the same name already exist
   - If they exist, you will be prompted to confirm overwriting

5. **Common Troubleshooting**:
   - If the "Start Processing" button does not respond, check the log area for error messages
   - Ensure all input files have the correct format and number of channels

## Logging System

The console area at the bottom of the application displays processing steps, warnings, and errors. Logs are color-coded as follows:

- Gray: Informational messages
- Yellow: Warnings
- Red: Errors
- Green: Success

## Example Workflow

### Texture Splitting Workflow
1. Export a composite texture (e.g., NNRM) from FModel
2. Use Texture Processor to split it into separate channels
3. Modify individual texture in Substance Painter or other image editing softwares
4. Use Texture Processor to merge the channels back into a composite texture
5. Import the final texture into your game engine or 3D software

## Advanced Usage

### Custom Normal Map Generation

When splitting textures, you can choose how to handle the blue (B) channel of the normal map:

- **Fill White**: Suitable for some game engines that expect the B channel of normal maps to be pure white
- **Calculate Z**: Calculates the Z component based on X and Y channel values, suitable for engines that require precise normal vectors

## Developer Information

This tool is built with Python and the following key libraries:

- **OpenCV**: For image processing and manipulation
- **NumPy**: For efficient array operations
- **CustomTkinter**: For modernized UI elements
- **Pillow**: For image I/O and format support


## Contributions

Contributions are welcome! Feel free to submit issues or pull requests.

---

For any questions or suggestions, welcome to contact
