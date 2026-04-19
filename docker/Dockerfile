# 阿里云免费版专用 · 超小 vLLM 0.19.0
FROM nvidia/cuda:12.1.1-base-ubuntu22.04

ENV DEBIAN_FRONTEND=noninteractive

# 最小化安装
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 python3-pip \
    && rm -rf /var/lib/apt/lists/*

# 安装核心包（不占空间）
RUN pip install --no-cache-dir torch==2.4.0 vllm==0.19.0

EXPOSE 8000
ENTRYPOINT ["vllm", "serve"]
