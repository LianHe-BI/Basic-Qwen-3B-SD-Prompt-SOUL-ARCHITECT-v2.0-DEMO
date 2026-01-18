 # 🌌 SOUL_ARCHITECT_v2.0_CORE
# [STATUS]: STABLE_DEPLOYMENT
# [TARGET_ARCH]: NVIDIA_BLACKWELL | NVIDIA_ADA_LOVELACE

[**English_Version**](#-philosophy) | [**Chinese_Version**](#-简介)

---

## 🏛️ Philosophy

/* * SOUL ARCHITECT v2.0 is not a conventional text-extension plugin. 
 * It is a "Digital Architect" deeply reconstructed based on the hardware 
 * characteristics of the NVIDIA Blackwell architecture.
 */

* **REJECT_LITERARY_TRAP**: 
    - Bypasses "eloquent prose" that image models cannot parse.
    - Focuses on physical parameter reconstruction: {Subsurface_Scattering, Anisotropic_Filtering}.
* **BLACKWELL_COMPUTING_DIVIDEND**: 
    - Native BF16 Sparse Computing via Tensor Cores.
    - Aggressive weight distribution for VAE/U-Net decoders to reach "physical ceiling."
* **AESTHETIC_SNOBBERY**: 
    - Trained with [alpha: 64, loss: 0.47].
    - A "madman model" that forcibly corrects or refuses "low-fidelity" concepts.

> [CRITICAL]: DO NOT treat this as a chatbot.

---

## 🏮 简介

/* * SOUL ARCHITECT v2.0 并非传统意义上的文本扩展插件，
 * 而是基于 Blackwell 硬件特性深度重构的“数字建筑师”。
 */

* **拒绝“信达雅”的文学陷阱**: 
    - 摒弃无效感性修辞，专注于物理参数重构。
    - 将模糊构思强制转化为硬核渲染指令。
* **Blackwell 架构算力红利**: 
    - 利用原生 BF16 稀疏计算能力，压榨显存纹理表现力。
    - 追求针对 VAE/U-Net 解码器最剧烈的词权分配。
* **审美偏执**: 
    - 存在极严重的审美洁癖，对“生活化烟火气”通过权重强行纠偏。
    - 一个过拟合并极度挑剔的疯子模型。

### 🕊️ Acknowledgments / 特别致敬
# [SOURCE]: Alibaba_Qwen2.5-3B-Raw
# [CREDIT]: Thanks to the Alibaba team for the powerful bilingual foundation.

---

## 🖼️ Gallery / 视觉引导区

# [PREVIEW_01]: Translucent Biomechanical Butterfly
# [RENDER_PATH]: assets/WebUI Demo1.png
<p align="center">
  < img src="assets/WebUI Demo2.png" width="45%" />
  < img src="assets/WebUI Demo3.png" width="45%" />
</p >

# [PREVIEW_02]: Physical Showcase
# [RENDER_PATH]: assets/WebUI.jpg
<p align="center">
  < img src="assets/loading.jpg" width="90%" />
</p >

---

## 🚀 Deployment / 快速启动指南

### 1. Base_Model_Preparation
# Action: Download original Qwen2.5-3B-Raw weights.

### 2. Environment_Config
# Remote_Link: pan.baidu.com/s/1EsBXxka4bNeUmRn6RmCTkw (Code: 8888)
# Package: arch20_runtime_env.tar.gz
# MD5_Checksum: b8ae84b60ae7a5b1496efa27f46f67c4

$md5sum arch20_runtime_env.tar.gz$ tar -xzvf arch20_runtime_env.tar.gz
$ conda activate ./arch20_runtime

### 3. Execution_Flow
# Edit app.py: MODEL_PATH = "/your/local/path/Qwen2.5-3B-Raw"
# Edit app.py: CORE_PATH = "./models/binary_cores/architect_v2.core"

$ python app.py
# [NETWORK]: Access UI via http://0.0.0.0:8888

---

## 📂 Directory_Structure / 目录结构清单
* `app.py`: Intelligent launcher & Path adaptation.
* `core/engine.py`: Inference logic (BF16 Tensor Core alignment).
* `models/binary_cores/`: Fine-tuned .core weights.
* `tools/smelt_v2.py`: Weight remelting utility.

## 💻 Hardware_Requirements / 硬件与配置要求
* **GPU**: NVIDIA Blackwell (RTX 50) | Ada Lovelace (RTX 40).
* **VRAM**: 8GB+ (Native BF16).
* **OS**: Linux (Ubuntu 24.04+) | WSL2.
* **Driver**: nvidia_driver_580_open (CUDA 12.8+ Support).

---

## 📜 License_&_Disclaimer / 协议与免责

* **Research_Study**: Technical research and aesthetic experimentation only.
* **Commercial_Use**: Allowed with attribution (Cite: SOUL ARCHITECT v2.0).
* **Liability**: Do not generate prohibited content.
* **Dev_Note**: Developed in 15 days. Coding assisted by Gemini & ChatGPT.
# [WARNING]: This is a DEMO version. Proceed with caution.

---

## 🛠️ Dependency_Registry / 所需库清单
# If not using pre-built Conda environment, manual install required:

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

# [EOF]: End of Soul_Architect_Document.
