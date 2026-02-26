# Servidor Minecraft com Crafty Controller

Este repositorio contem os scripts para instalacao, execucao e atualizacao do Crafty Controller - painel web para gerenciar servidores Minecraft.

## Estrutura do Projeto

```
servidor/
+-- crafty-installer-4.0/   # Instalador oficial do Crafty Controller
|   +-- install_crafty.py
|   +-- install_crafty.sh
|   +-- ...
+-- minecraft/              # Ambiente de execucao do Crafty
    +-- .venv/              # Ambiente virtual Python
    +-- crafty-4/           # Codigo-fonte do Crafty Controller
    +-- run_crafty.sh       # Script para iniciar o servidor
    +-- update_crafty.sh    # Script para atualizar o servidor
```

## Pre-requisitos

- Linux (Ubuntu/Debian, Arch ou Fedora)
- sudo disponivel
- git instalado
- python3 e pip3 instalados

## Instalacao

Clone o repositorio e execute o script de instalacao:

```bash
git clone https://github.com/wendell0102/servidor.git
cd servidor/crafty-installer-4.0
bash install_crafty.sh
```

> O script verifica se sudo esta disponivel, detecta o gerenciador de pacotes (apt/pacman/dnf) e instala as dependencias Python automaticamente.

## Como Iniciar o Servidor

Apos a instalacao, use o script de execucao:

```bash
cd servidor
bash minecraft/run_crafty.sh
```

O script faz o seguinte:

```bash
#!/bin/bash
cd /workspaces/servidor/minecraft
source .venv/bin/activate
cd crafty-4
exec python3 main.py
```

Apos iniciar, acesse o painel web do Crafty em:

```
https://localhost:8443
```

O servidor Minecraft ficara disponivel na porta 25565.

## Como Atualizar o Servidor

```bash
bash minecraft/update_crafty.sh
```

O script de atualizacao realiza:
1. Pergunta se deseja sobrescrever alteracoes locais
2. Executa git pull para buscar as atualizacoes
3. Atualiza as dependencias Python via pip3

## Portas Utilizadas

| Porta | Servico                   |
|-------|---------------------------|
| 8443  | Painel Web (Crafty HTTPS) |
| 25565 | Servidor Minecraft        |

## Licenca

Veja o arquivo `crafty-installer-4.0/LICENSE` para detalhes.
