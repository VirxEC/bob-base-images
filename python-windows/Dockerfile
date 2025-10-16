FROM mcr.microsoft.com/windows/servercore:ltsc2022

# Switch to PowerShell
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop';"]

# Download & install Git
RUN Invoke-WebRequest -Uri "https://github.com/git-for-windows/git/releases/download/v2.51.0.windows.2/Git-2.51.0.2-64-bit.exe" -OutFile "GitInstaller.exe"
RUN Start-Process -FilePath .\GitInstaller.exe -ArgumentList '/VERYSILENT', '/NORESTART', '/SUPPRESSMSGBOXES' -Wait

# Add Git Bash to PATH
RUN setx PATH "$($env:PATH);C:\\Program Files\\Git\\bin;C:\\Program Files\\Git\\usr\\bin"

SHELL ["C:\\Program Files\\Git\\bin\\bash.exe", "-c"]

WORKDIR "C:/usr/src/windows"

# Download and extract standalone Python
RUN wget https://github.com/astral-sh/python-build-standalone/releases/download/20251014/cpython-3.12.12+20251014-x86_64-pc-windows-msvc-install_only_stripped.tar.gz -O python.tar.gz && \
    tar -xf python.tar.gz

# Download and extract uv binary
RUN wget https://github.com/astral-sh/uv/releases/download/0.9.3/uv-x86_64-pc-windows-msvc.zip -O uv.tar.gz && \
    tar -xf uv.tar.gz && \
    mv uv-*/** .

# Switch back to CMD
SHELL ["cmd", "/S", "/C"]

# Point UV to Python
ENV UV_PYTHON="C:\\usr\\src\\windows\\python"
