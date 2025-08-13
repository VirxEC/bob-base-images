FROM debian:bullseye-slim
RUN dpkg --add-architecture i386 && apt update
RUN apt install -y wget
RUN mkdir -pm755 /etc/apt/keyrings
RUN wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
RUN wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/debian/dists/bullseye/winehq-bullseye.sources
RUN apt update
RUN apt install --install-recommends -y winehq-staging
RUN apt install -y git libarchive-tools binutils

# Windows prep
WORKDIR "/usr/src/win"

# Install windows python
RUN wget https://github.com/astral-sh/python-build-standalone/releases/download/20250808/cpython-3.12.11+20250808-x86_64-pc-windows-msvc-install_only_stripped.tar.gz -O python.tar.gz
RUN bsdtar -xf python.tar.gz

# Install windows uv
RUN wget https://github.com/astral-sh/uv/releases/download/0.8.9/uv-x86_64-pc-windows-msvc.zip -O uv.zip
RUN bsdtar -xf uv.zip

# Install windows git (for pip git dependencies)
RUN wget https://github.com/git-for-windows/git/releases/download/v2.50.1.windows.1/MinGit-2.50.1-64-bit.zip -O git.zip
RUN mkdir git
RUN bsdtar -xf git.zip --directory git

# Linux prep
WORKDIR "/usr/src/linux"

# Install linux python
RUN wget https://github.com/astral-sh/python-build-standalone/releases/download/20250808/cpython-3.12.11+20250808-x86_64_v2-unknown-linux-gnu-install_only_stripped.tar.gz -O python.tar.gz
RUN bsdtar -xf python.tar.gz

# Install linux uv
RUN wget https://github.com/astral-sh/uv/releases/download/0.8.9/uv-x86_64-unknown-linux-gnu.tar.gz -O uv.tar.gz
RUN bsdtar -xf uv.tar.gz
RUN mv uv-*/** .
