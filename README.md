 🌌 SOUL ARCHITECT v2.0 DEMO (Open Source)

> 微调核心：Architect_v2_PRO | 适配架构：NVIDIA Blackwell & Ada Lovelace

简介（Gemini生成）
SOUL ARCHITECT v2.0 并非传统意义上的文本扩展插件，而是一个基于 Blackwell 硬件特性深度重构的“数字建筑师”。它在审美取向与指令精度上，与现有方案有着本质的区别：
1. 拒绝“信达雅”的文学陷阱
相较于目前主流的本地 Prompt 生成器（如简单的 Llama/Gemma 微调版）或在线大模型（如 GPT-4、Claude），本模型彻底摒弃了无效的感性修辞。现有生成器往往沉溺于“信达雅”的文字游戏，输出大量 AI 绘画模型无法解析的虚词；而 SOUL ARCHITECT 专注于物理参数的重构，将模糊的构思强制转化为 Subsurface Scattering（次表面散射）或 Anisotropic Filtering（各向异性过滤）等硬核渲染指令。
2. Blackwell 架构的算力红利
与在线大模型相比，本模型实现了完全本地化与隐私保护。在 Blackwell 架构下，它能利用原生的 BF16 稀疏计算能力，在极短的时间内压榨出显卡的每一丝纹理表现力。它不追求 GPT 式的“创意对话”，而追求针对 VAE/U-Net 解码器 抖动最剧烈的词权分配，确保生成的每一组指令都能触达图像质感的“物理天花板”。

这是一个专注于“意境构筑”的 AI SD Prompt 提示词引擎的DEMO版本。它通过对底座模型进行高强度的偏执审美（alpha=64,loss=0.47）训练，能够将碎片化的构思转化为极具物理质感、光影考究的专业级绘画指令，但模型存在极严重的审美洁癖。如果你试图让它描述“杂乱的城中村”、“廉价的塑料感”或“生活化的烟火气”，它会通过微调权重强行纠偏，或者输出占位符或者拒绝输出，这是个过拟合并极度挑剔的疯子模型，对于不需要 AI 绘画、只想看文字的人来说，这些输出毫无阅读美感，并且显得枯燥乏味。

不要试图把它当成聊天机器人

特别致敬
本项目基于 阿里研发的 Qwen2.5-3B-Raw 大模型进行研究与深度微调。感谢阿里团队提供的优秀底座，其强大的中英双语理解能力和轻量化的参数规模，为我们进行极致的审美实验与学习研究提供了可能。

快速启动指南 (Deployment)
为了让大家能顺利启动，请遵循以下步骤：
 * 准备底座：
   首先需要先下载 [Qwen2.5-3B-Raw](https://huggingface.co/Qwen/Qwen2.5-3B?hl=zh-CN) 的原版模型
 
 * 环境配置：
   考虑到环境依赖（约8GB）较为复杂，我已将完整的 Conda 虚拟环境 打包上传至云盘。
   虚拟环境网盘地址：https://pan.baidu.com/s/1EsBXxka4bNeUmRn6RmCTkw 
   提取码: 8888 
   下载后请对照该MD5校验码：b8ae84b60ae7a5b1496efa27f46f67c4  包体名称：arch20_runtime_env.tar.gz
   请务必在 WSL2 或 Linux 环境内 使用命令 tar -xzvf arch20_runtime_env.tar.gz 进行解压
   # 下载后在终端输入：
md5sum arch20_runtime_env.tar.gz
# 确认输出为: b8ae84b60ae7a5b1496efa27f46f67c4
建议把解压后的arch20_runtime放在env目录下
   下载并解压后，请先进入该环境：
   conda activate /你的路径/arch20_runtime

 * 定位路径：
   在终端中切换到本项目（/data/return 对应的解压目录）所在的文件夹
 
 * 执行启动：
   先修改app.py内模型指向路径为本地正确路径
   # 找到 app.py 中的以下配置并修改：
MODEL_PATH = "/你的路径/Qwen2.5-3B-Raw" 
CORE_PATH = "./models/binary_cores/architect_v2.core"
   再在bash终端内运行启动器：python app.py
快速启动方式：
# 1. 激活环境
conda activate /your/path/arch20_runtime

# 2. 进入项目目录
cd SOUL_ARCHITECT_v2

# 3. 启动引擎
python app.py

 * 访问界面：
   启动成功后，终端会输出一个本地 IP 地址（如 http://0.0.0.0:8888）。右键点击该地址或将其复制到浏览器访问，即可开启构筑界面
   
目录结构清单
 * app.py：智能启动器（已处理路径自适应与端口检测）
 * core/engine.py：开源推理逻辑核心，核心权重采用 BF16 固化处理，在 Blackwell 架构上通过 Tensor Core 实现零时延精度对齐
 * models/binary_cores/：微调后的 .core 权重文件
 * tools/smelt_v2.py：权重重熔工具

硬件与配置要求 (Requirements)
为了保证推理速度（建议 2-4 秒内）和 BF16 精度，建议配置如下：
 * 显卡：首选 NVIDIA Blackwell 架构显卡（如 RTX 50 系列），亦兼容 Ada Lovelace (RTX 40 系列)，暂不支持AMD，Intel显卡，未来可能引入CPU硬解 
 * 显存：建议 8GB 及以上（BF16 原生加载）
 * 系统：Linux (Ubuntu 24.04+ 最佳) 或 Windows Subsystem for Linux (WSL2)
 * 显卡驱动要求：nvidia_driver_580_open 版本最佳

若遇到 CUDA 初始化失败，请检查驱动版本是否支持 CUDA 12.8+ 运行时库
 
商业与开源协议
 * 研究学习：本项目部分开源，仅供技术研究与审美实验使用
 * 商用规范：本微调模型及代码允许在商业场景中使用，但请务必在显著位置标明出处（指引至本项目仓库或提及 SOUL ARCHITECT v2.0）
 * 责任声明：请勿将本模型用于生成违规内容

免责声明
该作品由本人历经15天的草率开发而成，目前的可用水平顶多称作demo，研究工作中充分利用了Gemini，ChatGPT进行代码编译，本人只是作了架构实现路径的研究和方向取舍相关的工作，希望各位大佬手下留情🙏。

简要展示：
用户输入：漂浮在极地极光下的透明机械仿生蝴蝶

ARCHITECT v2.0 |DEMO| 1.92S
漂浮在北极光下的半透明机器生物蝴蝶，呈现出梦幻般的光影效果

POSITIVE PROMPT (RAW PHOTO)
Floating, Polar Aurora, Transparent, Mechanical, Butterfly, Ethereal, Glowing, Magical, Surreal, cinematic lighting, depth of field, high fidelity, texture details, ray traced shadows, global illumination, photorealistic, raw photo style, film grain
NEGATIVE PROMPT
Blurry, Distorted, Ugly, Cartoonish, Flat Art Style, Oversaturated, Pixelated, blurry, low quality, distorted, ugly, watermark, text, lowres, monochrome, cartoon, illustration

用户输入：阳光穿透装满冰块的苏打水，气泡正沿着杯壁急速上升并在表面破裂，冰块边缘在融化，折射出晃动的焦散光斑

ARCHITECT v2.0 |DEMO| 2.65S
阳光照亮充满冰块和苏打汽水的杯子，液体中的气泡快速向上移动并炸裂，在液面形成闪烁光影，冰棱逐渐融化产生彩虹效果

POSITIVE PROMPT (RAW PHOTO)
Sparkling, Crystal Clear, Radiant Light, Droplets Dancing, Prism Effect, Refreshing Vapor, cinematic lighting, depth of field, high fidelity, texture details, ray traced shadows, global illumination, photorealistic, raw photo style, film grain
NEGATIVE PROMPT
Cloudy Water, Slow Motion, Disrupted Patterns, Lackluster Glow, Flat Surface, Murky Reflection, blurry, low quality, distorted, ugly, watermark, text, lowres, monochrome, cartoon, illustration

（反例演示）不要试图输入类似如下的自然语言内容，它的表现很差

用户输入：一张布满划痕和烟头烫痕的暗红色皮质吧台，上面倒扣着一个破碎的威士忌杯，残留的金色液体正顺着桌缘滴落，背景是昏暗且充满烟雾的廉价酒吧。

ARCHITECT v2.0 |DEMO| 2.18S
褪色皮革吧台上沾染污渍与烧焦痕迹，残破酒杯中金液滑落，阴郁廉价酒吧环境

POSITIVE PROMPT (RAW PHOTO)
Refurbished, Smooth Surface, Shiny Liquid, Elegant Details, Luxurious Texture, Opulent Atmosphere, cinematic lighting, depth of field, high fidelity, texture details, ray traced shadows, global illumination, photorealistic, raw photo style, film grain
NEGATIVE PROMPT
Scratched, Burnt Marks, Broken Glass, Drooping Liquids, Cheap Setting, Gloomy Ambiance, blurry, low quality, distorted, ugly, watermark, text, lowres, monochrome, cartoon, illustration

如果你不打算使用预构建的 Conda 环境，可以参考以下核心组件版本进行手动安装。本项目基于最新的 CUDA 12.8 环境开发：
accelerate==1.12.0
aiofiles==24.1.0
annotated-doc==0.0.4
annotated-types==0.7.0
anyio==4.12.1
brotli==1.2.0
certifi==2026.1.4
charset-normalizer==3.4.4
click==8.3.1
cuda-bindings==12.9.4
cuda-pathfinder==1.2.2
Cython==3.2.4
fastapi==0.128.0
ffmpy==1.0.0
filelock==3.20.3
fsspec==2026.1.0
gradio==6.3.0
gradio_client==2.0.3
groovy==0.1.2
h11==0.16.0
hf-xet==1.2.0
httpcore==1.0.9
httpx==0.28.1
huggingface-hub==0.36.0
idna==3.11
Jinja2==3.1.6
markdown-it-py==4.0.0
MarkupSafe==3.0.2
mdurl==0.1.2
mpmath==1.3.0
networkx==3.6.1
numpy==2.4.1
nvidia-cublas-cu12==12.8.4.1
nvidia-cuda-cupti-cu12==12.8.90
nvidia-cuda-nvrtc-cu12==12.8.93
nvidia-cuda-runtime-cu12==12.8.90
nvidia-cudnn-cu12==9.10.2.21
nvidia-cufft-cu12==11.3.3.83
nvidia-cufile-cu12==1.13.1.3
nvidia-curand-cu12==10.3.9.90
nvidia-cusolver-cu12==11.7.3.90
nvidia-cusparse-cu12==12.5.8.93
nvidia-cusparselt-cu12==0.7.1
nvidia-nccl-cu12==2.28.9
nvidia-nvjitlink-cu12==12.8.93
nvidia-nvshmem-cu12==3.4.5
nvidia-nvtx-cu12==12.8.90
orjson==3.11.5
packaging==25.0
pandas==2.3.3
peft==0.18.1
pillow==12.1.0
psutil==7.2.1
pydantic==2.12.5
pydantic_core==2.41.5
pydub==0.25.1
Pygments==2.19.2
python-dateutil==2.9.0.post0
python-multipart==0.0.21
pytz==2025.2
PyYAML==6.0.3
regex==2026.1.15
requests==2.32.5
rich==14.2.0
safehttpx==0.1.7
safetensors==0.7.0
semantic-version==2.10.0
sentencepiece==0.2.1
shellingham==1.5.4
six==1.17.0
starlette==0.50.0
sympy==1.14.0
tokenizers==0.22.2
tomlkit==0.13.3
torch==2.11.0.dev20260115+cu128
torchaudio==2.11.0.dev20260115+cu128
torchvision==0.25.0.dev20260115+cu128
tqdm==4.67.1
transformers==4.57.6
triton==3.6.0+git9844da95
typer==0.21.1
typing-inspection==0.4.2
typing_extensions==4.15.0
tzdata==2025.3
urllib3==2.6.3
uvicorn==0.40.0

 🌌 SOUL ARCHITECT v2.0
Fine-tuning Core: Architect_v2_PRO | Architecture: NVIDIA Blackwell & Ada Lovelace Optimized
🏛️ Philosophy
SOUL ARCHITECT v2.0 is not a conventional text-extension plugin. It is a "Digital Architect" deeply reconstructed based on the hardware characteristics of the NVIDIA Blackwell architecture. It maintains a fundamental distinction from existing solutions in both aesthetic orientation and command precision:
Beyond the "Literary Trap": Unlike mainstream local prompt generators (simple Llama/Gemma tunes) or LLMs (GPT-4, Claude), this model completely abandons ineffective emotional rhetoric. While others indulge in "expressive prose" that image models cannot parse, SOUL ARCHITECT focuses on Physical Parameter Reconstruction. It forcibly converts vague concepts into hardcore rendering instructions such as Subsurface Scattering or Anisotropic Filtering.
Blackwell Computing Dividend: Achieving 100% localization and privacy, this model exploits the native BF16 Sparse Computing capabilities of the Blackwell architecture. It doesn't pursue "creative dialogue"; it pursues the most aggressive weight distribution for VAE/U-Net decoders, ensuring every prompt hits the "physical ceiling" of image texture.
Aesthetic Snobbery: This is a "madman model" trained with high-intensity aesthetic bias (alpha=64, loss=0.47). It possesses a severe aesthetic elitism. If you attempt to describe "cluttered slums," "cheap plastics," or "mundane smoke," it will forcibly correct the input via fine-tuned weights or simply refuse output. It is designed for visual perfectionists, not for those seeking reading pleasure.
DO NOT treat this as a chatbot.
🕊️ Special Acknowledgments
This project is researched and fine-tuned based on Alibaba's Qwen2.5-3B-Raw. Deep gratitude to the Alibaba team for providing an exceptional base model. Its powerful bilingual understanding and lightweight parameter scale made this extreme aesthetic experiment possible.
🚀 Quick Start (Deployment)
1. Prepare the Base
Download the original [Qwen2.5-3B-Raw](https://huggingface.co/Qwen/Qwen2.5-3B?hl=zh-CN) model weights first.
2. Environment Configuration
The environment dependencies (~8GB) are complex. A pre-packaged Conda Virtual Environment is provided via cloud storage:https://pan.baidu.com/s/1EsBXxka4bNeUmRn6RmCTkw 
Link: Baidu Network Disk (Code: 8888)
MD5 Checksum: b8ae84b60ae7a5b1496efa27f46f67c4
Package Name: arch20_runtime_env.tar.gz
Installation (WSL2 / Linux):
# Verify integrity
md5sum arch20_runtime_env.tar.gz

# Extract and Activate
tar -xzvf arch20_runtime_env.tar.gz
conda activate ./arch20_runtime
3. Execution
Modify the model paths in app.py:
MODEL_PATH = "/your/path/Qwen2.5-3B-Raw"
CORE_PATH = "./models/binary_cores/architect_v2.core"
Launch the Engine:
python app.py
Access the interface via http://0.0.0.0:8888 once the terminal outputs the local IP.
📂 Repository Structure
app.py: Intelligent launcher with path adaptation and port detection.
core/engine.py: Open-source inference logic. Core weights are BF16-hardened for zero-latency precision alignment on Blackwell Tensor Cores.
models/binary_cores/: Fine-tuned .core weight files.
tools/smelt_v2.py: Weight remelting utility.
💻 Hardware Requirements
To ensure inference speeds (target: 2-4s) and BF16 precision:
GPU: NVIDIA Blackwell (RTX 50-series) preferred; Ada Lovelace (RTX 40-series) compatible. Note: AMD/Intel GPUs are not currently supported.
VRAM: 8GB+ (Native BF16 loading).
OS: Linux (Ubuntu 24.04+ recommended) or WSL2.
Driver: nvidia_driver_580_open or higher (Supports CUDA 12.8+).
📜 License & Ethics
Research: This project is partially open-source for technical research and aesthetic experimentation only.
Commercial Use: Allowed, provided that the source is prominently cited (link to this repository or mention SOUL ARCHITECT v2.0).
Responsibility: Do not use this model to generate prohibited or illegal content.
⚠️ Disclaimer
This work is a "demo" developed over 15 days of intensive experimentation. Coding was assisted by Gemini and ChatGPT. My role involved architectural implementation path research and directional decision-making. Please handle with care. 🙏
🛠️ Manual Installation (Alternative)
If you choose not to use the pre-built Conda environment, ensure your local environment matches CUDA 12.8:
accelerate==1.12.0
aiofiles==24.1.0
annotated-doc==0.0.4
annotated-types==0.7.0
anyio==4.12.1
brotli==1.2.0
certifi==2026.1.4
charset-normalizer==3.4.4
click==8.3.1
cuda-bindings==12.9.4
cuda-pathfinder==1.2.2
Cython==3.2.4
fastapi==0.128.0
ffmpy==1.0.0
filelock==3.20.3
fsspec==2026.1.0
gradio==6.3.0
gradio_client==2.0.3
groovy==0.1.2
h11==0.16.0
hf-xet==1.2.0
httpcore==1.0.9
httpx==0.28.1
huggingface-hub==0.36.0
idna==3.11
Jinja2==3.1.6
markdown-it-py==4.0.0
MarkupSafe==3.0.2
mdurl==0.1.2
mpmath==1.3.0
networkx==3.6.1
numpy==2.4.1
nvidia-cublas-cu12==12.8.4.1
nvidia-cuda-cupti-cu12==12.8.90
nvidia-cuda-nvrtc-cu12==12.8.93
nvidia-cuda-runtime-cu12==12.8.90
nvidia-cudnn-cu12==9.10.2.21
nvidia-cufft-cu12==11.3.3.83
nvidia-cufile-cu12==1.13.1.3
nvidia-curand-cu12==10.3.9.90
nvidia-cusolver-cu12==11.7.3.90
nvidia-cusparse-cu12==12.5.8.93
nvidia-cusparselt-cu12==0.7.1
nvidia-nccl-cu12==2.28.9
nvidia-nvjitlink-cu12==12.8.93
nvidia-nvshmem-cu12==3.4.5
nvidia-nvtx-cu12==12.8.90
orjson==3.11.5
packaging==25.0
pandas==2.3.3
peft==0.18.1
pillow==12.1.0
psutil==7.2.1
pydantic==2.12.5
pydantic_core==2.41.5
pydub==0.25.1
Pygments==2.19.2
python-dateutil==2.9.0.post0
python-multipart==0.0.21
pytz==2025.2
PyYAML==6.0.3
regex==2026.1.15
requests==2.32.5
rich==14.2.0
safehttpx==0.1.7
safetensors==0.7.0
semantic-version==2.10.0
sentencepiece==0.2.1
shellingham==1.5.4
six==1.17.0
starlette==0.50.0
sympy==1.14.0
tokenizers==0.22.2
tomlkit==0.13.3
torch==2.11.0.dev20260115+cu128
torchaudio==2.11.0.dev20260115+cu128
torchvision==0.25.0.dev20260115+cu128
tqdm==4.67.1
transformers==4.57.6
triton==3.6.0+git9844da95
typer==0.21.1
typing-inspection==0.4.2
typing_extensions==4.15.0
tzdata==2025.3
urllib3==2.6.3
uvicorn==0.40.0
