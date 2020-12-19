---
title: Executando sudo sem senha
description: Aprenda a configurar o sudo para não ter de digitar senha.
header: Executando sudo sem senha
---

sudo ("super user do") é uma ferramenta para executar comandos e programas com poderes de outro usuário, geralmente um superusuário. Ao usar sudo como superusuário você delega poderes de root ao comando executado, pelo tempo de cinco minutos. Isso quer dizer que, durante cinco minutos após digitar a senha para sudo você poderá invocá-lo novamente sem ter que digitar a senha de novo.

A seguir vamos ver como utilizar o sudo sem ter de fornecer senha.

Digite a seguinte linha como usuário administrador ou forneça poder de superusuário através do sudo:

> $ sudo visudo

Nota: não edite diretamente o arquivo /etc/sudoers. Use o comando visudo para isso.

Localize a seguinte linha:

> root&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ALL=(ALL)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ALL

Agora, abaixo desta, adicione o usuário desejado como a seguir:

> usuario&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ALL=(ALL)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NOPASSWD:ALL

Pronto! Agora o usuário adicionado ao sudoers não precisará digitar senha para executar comandos privilegiados.
Seja cauteloso, pois nesta situação você não terá oportunidade de pensar duas vezes ao executar um comando elevado podendo, assim, danificar o sistema.
