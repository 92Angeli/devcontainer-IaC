# Imagem base otimizada da Microsoft para Dev Containers com Python 3.11 no Debian Bookworm
FROM mcr.microsoft.com/devcontainers/python:1-3.11-bookworm

# Evita prompts interativos durante a instalação de pacotes
ENV DEBIAN_FRONTEND=noninteractive

# Argumentos para instalação oficial do HashiCorp Terraform
ARG TERRAFORM_VERSION="1.9.5"

# 1. Instalar dependências básicas do sistema e utilitários de rede
RUN find /etc/apt/sources.list.d -type f -iname '*yarn*' -delete \
    && apt-get update && apt-get install -y --no-install-recommends \
    curl \
    gnupg \
    software-properties-common \
    unzip \
    git \
    openssh-client \
    iputils-ping \
    net-tools \
    && rm -rf /var/lib/apt/lists/*

# 2. Instalar o HashiCorp Terraform oficial
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg \
    && echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/hashicorp.list \
    && apt-get update && apt-get install -y terraform=${TERRAFORM_VERSION}* \
    && rm -rf /var/lib/apt/lists/*

# 3. Instalar o Ansible Engine e bibliotecas Python essenciais
RUN pip install --no-cache-dir \
    ansible \
    ansible-lint \
    docker \
    requests \
    paramiko

# 4. Instalar Ansible Collections essenciais para Docker e Proxmox
USER vscode
RUN ansible-galaxy collection install community.docker community.general

# Retorna ao usuário vscode padrão do Dev Container
USER vscode