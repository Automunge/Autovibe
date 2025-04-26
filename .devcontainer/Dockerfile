# ** Base Image **  
# Start from the official devcontainers Python image (Ubuntu-based with Python pre-installed)
FROM mcr.microsoft.com/devcontainers/python:0-3.11

# Switch to root for installation tasks (if not already root)
USER root

# ** Install OS Packages **  
# Update apt and install any system dependencies for ML libs or Rust (if needed)
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get install -y --no-install-recommends \
       build-essential curl git ca-certificates \ 
       libopenmpi-dev libssl-dev \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# ** Python: Install ML Libraries **  
# Upgrade pip first, then install common data science and ML packages
RUN python -m pip install --upgrade pip && \ 
    pip install numpy scipy pandas scikit-learn matplotlib seaborn \ 
    jupyterlab notebook # \ 
    # torch torchvision torchaudio \ 
    # tensorflow==2.13.*  keras \ 
    # deap 

# ** (Optional) Rust: Additional Setup **  
# [Rust is installed via devcontainer Feature in this config, so no manual install here]
# But if you weren't using the Feature, you could install Rust with rustup like:
# RUN curl https://sh.rustup.rs -sSf | bash -s -- -y --default-toolchain stable && \
#     echo 'export PATH="$HOME/.cargo/bin:$PATH"' >> /etc/bash.bashrc

# ** Final Setup **  
# Switch back to non-root user (the devcontainer base image uses 'vscode' user)  
USER vscode
