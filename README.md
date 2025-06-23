# MSU2 MINI烧录工具魔改及图片制作工具

## 项目简介

该项目包含了对 MSU2 MINI 烧录工具源代码的魔改，以实现对 Linux 系统的兼容。同时，还提供了一个相关的 Python 小工具 `1_video_to_36_pictures.py`，用于制作烧录所需的图片，可以将几乎所有视频格式（包括 jpg、gif 等动图格式）转化为 36 张图片。

## 环境要求
* **FFMPEG** ：该项目中的 `1_video_to_36_pictures.py` 工具需要借助 FFMPEG 来处理视频。FFMPEG 是一个开源的多媒体处理工具。
    * 如果愿意将 FFMPEG 添加到系统环境变量，则可在系统中方便地调用。
    * 若不愿意添加到环境变量，也可以在使用 `1_video_to_36_pictures.py` 工具时，通过指定 FFMPEG 的文件路径来使用。

* **Python** ：确保系统已安装 Python 运行环境，用于运行 `1_video_to_36_pictures.py` 工具。

## 工具使用

### MSU2 MINI 烧录工具魔改版

* 由于是魔改以兼容 Linux 系统，具体的使用方法与原版工具相同，按照指引进行烧录操作。

### 1_video_to_36_pictures.py 程序介绍

* **安装依赖** ：确保已安装 Python 环境和 FFMPEG 后，该工具无其他复杂依赖，可直接运行。
* **运行方式** ：在命令行中，进入到包含 `1_video_to_36_pictures.py` 文件的目录，运行以下命令（假设已将 FFMPEG 添加到系统环境变量，且视频文件名为 example_video.mp4）：
```python 1_video_to_36_pictures.py -i example_video.mp4```

* 如果未将 FFMPEG 添加到环境变量，则需要指定 FFMPEG 的完整路径来运行，例如：
```bash
python 1_video_to_36_pictures.py -i example_video.mp4
```
* **参数说明** ：
    可以    

    | 参数         | 说明                                       |
    |------------|------------------------------------------|
    | -h, --help | 显示帮助信息                                   |
    | -i         | str 输入视频或动图文件的路径                         |
    | -s         | float 截取视频的起始部分 (单位: 秒)                  |
    | -t         | float 截取视频的结束部分 (单位: 秒)                  |
    | -r         | int 旋转视频: 0 是不旋转，1 是顺时针 90 度，2 是逆时针 90 度 |
    | -rr        | int 额外连续转多次 (用于实现 180 度旋转)               |

* **源码配置修改方法**
* 除了通过命令行参数进行配置外，您还可以直接在1_video_to_36_pictures.py文件源码中修改以下配置项以保存您的个性化设置：
```python
video_path:str = "i.mp4"  # 默认视频文件路径
start_time:float = 10     # 默认截取视频的起始时间（秒）
end_time:float = 1000000  # 默认截取视频的结束时间（秒）
transpose:int = 1         # 默认旋转方式：0（不旋转），1（顺时针90°），2（逆时针90°）
rotate_time:int = 0       # 默认连续旋转次数（用于实现180°旋转）
ffmpeg_path = "ffmpeg"    # 默认FFMPEG路径
ffprobe_path = "ffprobe"  # 默认ffprobe路径
```
* **输出结果** ：运行成功后，会在脚本所在目录下的指定目录生成 36 张图片，这些图片可用于 MSU2 MINI 的烧录过程。

## 示例

假设你的 FFMPEG 已正确安装并添加到环境变量，且有一个名为 `my_animation.gif` 的动图文件，想要将其转换为 36 张图片用于烧录，可在命令行中执行：

```bash
python 1_video_to_36_pictures.py -i my_animation.gif -s 1 -t 2
```
或在源码修改配置
```python
video_path:str = "my_animation.gif"  # 默认视频文件路径
start_time:float = 10     # 默认截取视频的起始时间（秒）
end_time:float = 1000000  # 默认截取视频的结束时间（秒）
```
```bash
python 1_video_to_36_pictures.py
```

执行完成后，即可得到用于烧录的 36 张图片。

## 注意事项

* 在Linux端使用魔改后的 MSU2 MINI 烧录工具时 
权限如果不足的话需要
```bash
sudo usermod -aG dialout $USER
```
再重起电脑即可

* 对于 `1_video_to_36_pictures.py` 工具，可能会导致转换失败。如果遇到问题，请先检查视频文件的完整性和格式是否被 FFMPEG 支持。
