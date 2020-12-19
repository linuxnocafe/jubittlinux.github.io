---
title: Gerenciamento de pacotes no Arch Linux
description: Aprenda a gerenciar pacotes no Arch Linux.
header: Gerenciamento de pacotes no Arch Linux
---

O gerenciador de pacotes do Arch linux é o pacman (package manager). Vamos ver alguns comandos úteis a seguir.

**Instalar Pacote:**

> $ sudo pacman -S pacote_nome

**Instalar grupo de pacotes**:

> $ sudo pacman -S pacote_nome1 pacote_nome2

**Remover pacote:**

> $ sudo pacman -R pacote_nome

**Atualizar o sistema:**

> $ sudo pacman -Su

**Sincronizar repositórios e em seguida atualizar o sistema:**

> $ sudo pacman -Syu

**Baixar pacote sem instalar:**

> $ sudo pacman -Sw pacote_nome

**Instalar pacote local (já baixado):**

> $ sudo pacman -U /caminho/para/pacote

**Mostrar versão dos pacotes instalados:**

> $ sudo pacman -Q

**Salvar numa lista a versão dos pacotes instalados:**

> $ sudo pacman -Q > instalado.txt

**Remover pacote e todas as dependências:**

> $ sudo pacman -Rsc pacote_nome

**Remover pacote e seu arquivo de configuração:**

> $ sudo pacman -Rn pacote_nome

**Procurar um pacote:**

> $ sudo pacman -Ss pacote_nome

**Mostrar a qual pacote pertence um arquivo:**

> $ sudo pacman -Qo /caminho/para/arquivo

**Mostrar qual pacote fornece um arquivo:**

> $ sudo pacman -Ql

**Mostrar pacotes órfãos sem dependências:**

> $ sudo pacman -Qdt

**Listar pacote e suas dependências em forma de árvore:**

> $ sudo pactree pacote_nome

Para mais detalhes consulte:  
[Fonte: Wiki ArchBSD: Pacman](https://wiki.pacbsd.org/index.php/Pacman)
