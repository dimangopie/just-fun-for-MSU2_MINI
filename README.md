# MSU2 MINI烧录工具魔改及图片制作工具

## 项目简介

该项目包含了对 MSU2 MINI 烧录工具源代码的魔改，以实现对 Linux 系统的兼容。同时，还提供了一个相关的 Python 小工具 `1_video_to_36_pictures.py`，用于制作烧录所需的图片，可以将几乎所有视频格式（包括 jpg、gif 等动图格式）转化为 36 张图片。

## 目录结构

```
.
├── MSU2_MINI_Linux_Burner（魔改后的烧录工具源代码及相关文件）
└── 1_video_to_36_pictures.py（视频转图片工具）
```

## 环境要求

  * **FFMPEG** ：该项目中的 `1_video_to_36_pictures.py` 工具需要借助 FFMPEG 来处理视频。FFMPEG 是一个开源的多媒体处理工具。
    * 如果愿意将 FFMPEG 添加到系统环境变量，则可在系统中方便地调用。
    * 若不愿意添加到环境变量，也可以在使用 `1_video_to_36_pictures.py` 工具时，通过指定 FFMPEG 的文件路径来使用。

  * **Python** ：确保系统已安装 Python 运行环境，用于运行 `1_video_to_36_pictures.py` 工具。

## 工具使用

### MSU2 MINI 烧录工具魔改版

  * 由于是魔改以兼容 Linux 系统，具体的使用方法可能与原版工具有所不同，请参考魔改后的工具内的相关文档或说明文件，按照指引进行烧录操作。

### 1_video_to_36_pictures.py

  * **安装依赖** ：确保已安装 Python 环境后，该工具无其他复杂依赖，可直接运行。
  * **运行方式** ：在命令行中，进入到包含 `1_video_to_36_pictures.py` 文件的目录，运行以下命令（假设已将 FFMPEG 添加到系统环境变量，且视频文件名为 example_video.mp4）：
**`python 1_video_to_36_pictures.py --input example_video.mp4`**

    * 如果未将 FFMPEG 添加到环境变量，则需要指定 FFMPEG 的完整路径来运行，例如：
**`python 1_video_to_36_pictures.py --input example_video.mp4 --ffmpeg /path/to/your/ffmpeg`**

  * **参数说明** ：

| 参数名 | 说明 | 是否必填 |
|------|------|------|
| --input | 输入的视频文件路径 | 是 |
| --ffmpeg | FFMPEG 文件路径（如果未添加到环境变量则必填） | 否 |

  * **输出结果** ：运行成功后，会在脚本所在目录下生成 36 张图片，这些图片可用于 MSU2 MINI 的烧录过程。

## 示例

假设你的 FFMPEG 已正确安装并添加到环境变量，且有一个名为 `my_animation.gif` 的动图文件，想要将其转换为 36 张图片用于烧录，可在命令行中执行：

```bash
python 1_video_to_36_pictures.py --input my_animation.gif
```

执行完成后，即可得到用于烧录的 36 张图片。

## 注意事项

  * 在使用魔改后的 MSU2 MINI 烧录工具时，请确保按照正确的操作流程进行烧录，以免对设备造成损坏。
  * 对于 `1_video_to_36_pictures.py` 工具，如果输入的视频格式较为特殊或损坏，可能会导致转换失败。如果遇到问题，请先检查视频文件的完整性和格式是否被 FFMPEG 支持。