---
title: Downgrade de pacote no Arch Linux
description: Aprenda a retroceder um pacote no Arch Linux
header: Downgrade de pacote no Arch Linux
---

No arch Linux existe um comando chamado downgrade que permite fazer o retrocesso de um pacote instalado para qualquer versão anterior. Este utilitário faz a checagem do seu cache local e dos servidores remotos (repositórios Arch Linux) para as versões mais velhas de um pacote requisitado. Você pode escolher qualquer pacote da lista e instalá-lo.

Este pacote não está disponível nos repositórios oficiais. É necessário adicionar o repositório "archlinuxfr" a sua lista.

Para isso, edite /etc/pacman.conf:

> $ sudo nano /etc/pacman.conf

Adicione as seguintes linhas:

> [archlinuxfr]  
SigLevel = Never  
Server = http://repo.archlinux.fr/$arch  

Salve e feche o arquivo. CTRL + X, seguido de CTRL + O.

Atualize os repositórios com o comando a seguir:

> $ sudo pacman -Sy

Agora instale o utilitário "Downgrade":

> $ sudo pacman -S downgrade

Depois de finalizada a instalação vamos proceder com o downgrade propriamente dito. Digamos que você queira fazer downgrade do navegador Opera.
Proceda da seguinte forma:

> $ sudo downgrade opera

O comando acima vai listar todas as versões disponíveis para o pacote opera. Selecione o pacote pelo número da lista e tecle enter. Pronto! O downgrade será finalizado! 
