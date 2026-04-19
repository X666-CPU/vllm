# =============================================================================
# 阿里云个人版专用 · 极简 vLLM OpenAI 镜像 (v0.19.0)
# 自动适配 CUDA 13.0.0 + Python 3.12
# =============================================================================

ARG CUDA_VERSION=13.0.0
ARG PYTHON_VERSION=3.12
ARG UBUNTU_VERSION=22.04

FROM nvidia/cuda:${CUDA_VERSION}-base-ubuntu${UBUNTU_VERSION}

ENV DEBIAN_FRONTEND=noninteractive
WORKDIR /app

# 安装系统依赖
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 python3-pip python3-venv git \
    && rm -rf /var/lib/apt/lists/*

# 使用 venv 避免权限问题
RUN python3 -m venv /venv
ENV PATH="/venv/bin:$PATH"

# 更新 pip
RUN pip install --upgrade pip

# 直接安装 vLLM 0.19.0 + openai 服务器
RUN pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130
RUN pip install vllm==0.19.0 openai

# 暴露 API 端口
EXPOSE 8000

# 启动命令（和官方 vllm-openai 一样）
ENTRYPOINT ["vllm", "serve"]
