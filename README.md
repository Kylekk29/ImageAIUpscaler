# Image AI Upscaler

A **Google Colab notebook** for AI-powered image upscaling using [Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN). Upload an image and get it enhanced up to 32x resolution with sharpness control and metadata preservation.

## Features

- **AI Upscaling** - Real-ESRGAN engine (up to 4x AI, then up to 32x with Lanczos post-upscale)
- **Face Enhancement** - Optional GFPGAN face refinement
- **HEIC/HEIF Support** - iPhone photo format supported out of the box
- **Metadata Preservation** - EXIF data preserved through the entire pipeline
- **Sharpness Control** - Adjustable unsharp mask after upscaling
- **Resolution Limits** - Cap output at 4K/8K/12K/16K or no limit
- **Tile Processing** - Tile-based AI inference to handle large images within GPU memory
- **Auto Bugfix** - Patches known Real-ESRGAN compatibility issues automatically
- **ZIP Download** - All enhanced images packaged and ready to download

## How to Use

1. **Open in Colab** - Upload this notebook to Google Colab
2. **Enable GPU** - Runtime > Change runtime type > Hardware accelerator: GPU (T4)
3. **Run Cell 1** - Installs Real-ESRGAN and downloads AI weights (~2-3 min)
4. **Run Cell 2** - Configure settings and upload your images
5. **Download** - ZIP file downloads automatically after processing

## Parameters

| Parameter | Default | Description |
|---|---|---|
| upscale_factor | 6 | Total upscale factor (2-32) |
| tile_size | 512 | AI inference tile size (0=full image) |
| enhance_faces | False | Enable GFPGAN face enhancement |
| opencv_method | Lanczos4 | Post-upscale resampling method |
| apply_sharpness | True | Apply unsharp mask |
| sharpness_intensity | 0.6 | Sharpness strength (0.1-2.0) |
| max_edge_resolution | 8K | Cap longest edge |
| output_folder | /content/output | Output directory |

## Notes

- AI engine does 4x upscale; factors above 4x use Lanczos post-resize
- Large images (>20MP) may need lower tile sizes for GPU memory
- HEIC/HEIF files are converted to JPEG during processing
- EXIF metadata is preserved from source images

## License

MIT
