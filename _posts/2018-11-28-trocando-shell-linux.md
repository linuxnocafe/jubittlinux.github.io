---
title: Trocando o shell do Linux
description: Altere o shell padrão do Linux e saia do bash
header: Trocando o shell do Linux
---

Shell é a camada entre o usuário e o Kernel. O shell do Linux é um poderoso interpretador de comandos. Existem vários tipos de shell. O bash (Bourne Again Shell) é padrão no Linux. A seguir vamos ver algumas dicas sobre o shell e, assim, mudá-lo quando preciso.

Ver quais shells estão disponíveis:

> $ cat /etc/shells

ou

> $ chsh -l

Ver o shell atual:

> $ env \| grep $SHELL

Mudar de shell permanentemente:

> $ chsh -s /bin/zsh

Instalar outro shell (Arch):

> $ sudo pacman -S zsh
