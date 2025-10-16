FROM mcr.microsoft.com/windows/servercore:ltsc2022

# Switch to PowerShell
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop';"]

# Install Git
RUN Invoke-WebRequest -Uri "https://github.com/git-for-windows/git/releases/download/v2.51.0.windows.2/Git-2.51.0.2-64-bit.exe" -OutFile "GitInstaller.exe"
RUN Start-Process -FilePath .\GitInstaller.exe -ArgumentList '/VERYSILENT', '/NORESTART', '/SUPPRESSMSGBOXES' -Wait

WORKDIR "C:\\usr\\src\\windows"

# Install python
RUN Invoke-WebRequest "https://github.com/astral-sh/python-build-standalone/releases/download/20251014/cpython-3.12.12+20251014-x86_64-pc-windows-msvc-install_only_stripped.tar.gz" -OutFile python.tar.gz
RUN tar -xzf python.tar.gz

# Install uv
RUN Invoke-WebRequest "https://github.com/astral-sh/uv/releases/download/0.9.3/uv-x86_64-pc-windows-msvc.zip" -OutFile uv.tar.gz
RUN tar -xzf uv.tar.gz

SHELL ["cmd", "/S", "/C"]

# Point UV to Python
ENV UV_PYTHON="C:\\usr\\src\\windows\\python"
