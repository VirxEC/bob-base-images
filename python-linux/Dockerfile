FROM debian:bullseye-slim

RUN apt update && apt install -y wget git libarchive-tools binutils

WORKDIR "/usr/src/linux"

# Install python
RUN wget https://github.com/astral-sh/python-build-standalone/releases/download/20251014/cpython-3.12.12+20251014-x86_64_v2-unknown-linux-gnu-install_only_stripped.tar.gz -O python.tar.gz
RUN bsdtar -xf python.tar.gz

# Install uv
RUN wget https://github.com/astral-sh/uv/releases/download/0.9.3/uv-x86_64-unknown-linux-gnu.tar.gz -O uv.tar.gz
RUN bsdtar -xf uv.tar.gz
RUN mv uv-*/** .

# Point UV to Python
ENV UV_PYTHON="/usr/src/linux/python"
