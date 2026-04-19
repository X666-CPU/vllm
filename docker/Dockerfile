FROM nvidia/cuda:12.1.1-base-ubuntu22.04

ENV DEBIAN_FRONTEND=noninteractive

# 最小系统
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 python3-pip \
    && rm -rf /var/lib/apt/lists/*

# 正确版本：不指定torch，让vllm自己装对应版本
RUN pip install --no-cache-dir vllm==0.19.0

EXPOSE 8000
ENTRYPOINT ["vllm", "serve"]
