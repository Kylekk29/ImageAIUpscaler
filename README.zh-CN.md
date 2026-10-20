[English](README.md) | **简体中文**

# Image AI Upscaler（AI 图片放大）

一个用 [Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) 做 AI 图片放大的 **Google Colab Notebook**。上传图片，即可放大到最高 32 倍分辨率，并可调节锐度、保留元数据。

## 功能

- **AI 放大** - Real-ESRGAN 引擎（AI 最高 4 倍，再用 Lanczos 后处理放大到最高 32 倍）
- **人脸增强** - 可选的 GFPGAN 人脸修复
- **支持 HEIC/HEIF** - 开箱即用地支持 iPhone 照片格式
- **保留元数据** - EXIF 信息在整个处理流程中保持不变
- **锐度控制** - 放大后可调节的 USM 锐化
- **分辨率上限** - 输出可限制在 4K/8K/12K/16K，或不设上限
- **分块处理** - 基于分块的 AI 推理，让大图也能在显存内完成
- **自动修复** - 自动修补 Real-ESRGAN 已知的兼容性问题
- **ZIP 下载** - 所有增强后的图片自动打包，可直接下载

## 使用方法

1. **在 Colab 中打开** - 把这个 Notebook 上传到 Google Colab
2. **启用 GPU** - 运行时 > 更改运行时类型 > 硬件加速器：GPU (T4)
3. **运行第 1 个单元格** - 安装 Real-ESRGAN 并下载 AI 权重（约 2-3 分钟）
4. **运行第 2 个单元格** - 配置参数并上传图片
5. **下载** - 处理完成后，ZIP 文件会自动下载

## 参数

| 参数 | 默认值 | 说明 |
|---|---|---|
| upscale_factor | 6 | 总放大倍数（2-32） |
| tile_size | 512 | AI 推理的分块大小（0 = 整张图） |
| enhance_faces | False | 启用 GFPGAN 人脸增强 |
| opencv_method | Lanczos4 | 后处理重采样方法 |
| apply_sharpness | True | 应用 USM 锐化 |
| sharpness_intensity | 0.6 | 锐化强度（0.1-2.0） |
| max_edge_resolution | 8K | 最长边的上限 |
| output_folder | /content/output | 输出目录 |

## 说明

- AI 引擎只做 4 倍放大；超过 4 倍的部分用 Lanczos 重采样完成
- 大图（超过 2000 万像素）可能需要调低分块大小，以适应显存
- HEIC/HEIF 文件在处理时会转换为 JPEG
- EXIF 元数据会从原图保留下来

## 许可证

MIT，见 [LICENSE](LICENSE)。
