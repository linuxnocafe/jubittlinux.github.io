---
title: Adicionando parâmetros ao Kernel do Ubuntu
description: Aprenda a passar parâmetros ao Kernel do Ubuntu.
header: Adicionando parâmetros ao Kernel do Ubuntu
---

Às vezes se faz necessário passar parâmetros para o kernel Linux. Por exemplo, para desabilitarmos a aceleração 3D de placas Nvidia que estejam usando Nouveau, no Ubuntu, podemos proceder como será mostrado neste tutorial.

No terminal digite:

> $ sudo vi /etc/default/grub  

Ache a linha que comece com GRUB_CMDLINE_LINUX_DEFAULT e adicione ao final nouveau.noaccel=1. Como a seguir:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.noaccel=1"  

Por final, atualize o grub:

> $ sudo update-grub  

Na próxima inicialização o kernel deve carregar com o novo parâmetro. Para remover o parâmetro de forma permanente edite novamente o arquivo e apague o que foi inserido. Atualize o grub novamente.

Para verificar as mudanças aplicadas, você pode ver os parâmetros que o kernel carregou executando o seguinte comando:

> $ cat /proc/cmdline
