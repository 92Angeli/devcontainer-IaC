# DevContainer para IaC: Terraform e Ansible

Ambiente de desenvolvimento baseado em container para trabalhar com Infrastructure as Code (IaC) usando Terraform e Ansible.

## Ferramentas incluidas

- Terraform CLI 1.9.5
- Python 3.11
- Ansible e `ansible-lint`
- Collections Ansible `community.docker` e `community.general`
- Bibliotecas Python `docker`, `requests` e `paramiko`
- Git e cliente OpenSSH
- Extensoes do VS Code para Terraform, Ansible, Python, containers e YAML

## Pre-requisitos

- Docker Engine ou Docker Desktop em execucao
- Visual Studio Code com a extensao [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Como usar

Clone o repositorio e abra a pasta no VS Code:

```bash
git clone https://github.com/92Angeli/devcontainer-IaC.git
cd devcontainer-IaC
code .
```

Quando solicitado, selecione **Reopen in Container** (ou execute **Dev Containers: Reopen in Container** na paleta de comandos). O VS Code construira a imagem definida em `.devcontainer/Dockerfile`.

O DevContainer monta a pasta `.ssh` do usuario do host em `/home/vscode/.ssh` para permitir autenticacao SSH a partir do ambiente. Nao coloque chaves privadas, credenciais ou arquivos de estado do Terraform no repositorio.
