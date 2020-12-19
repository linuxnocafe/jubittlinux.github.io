---
title: Exibir asteriscos ao digitar a senha no terminal
description: Configure o sistema para exibir asterisco ao digitar a senha no terminal
header: Exibir asteriscos ao digitar a senha no terminal
---

A maior parte das aplicações mostram asterisco quando um usuário está digitando a senha, mas no terminal Linux quando um usuário executa o comando sudo para obter super privilégio nada é mostrado na tela.
Veremos a seguir como configurar o sistema para exibir asterisco quando digitar senhas no terminal.

Faça um backup do arquivo /etc/sudoers:

> $ sudo cp /etc/sudoers /etc/sudoers.bak

Vamos editar o arquivo sudoers:

> $ sudo visudo

Procure pela seguinte linha:

> Defaults env_reset

Adicione o termo "pwfeedback" a frente da linha mencionada.  
Deve ficar assim:

> Defaults env_reset,pwfeedback

Agora salve e saia do "vi".
Caso a linha procurada não exista no arquivo você deve adicionar a mesma, da forma como orientamos acima.
Isso pode acontecer caso seu sistema seja Arch Linux.

Execute o seguinte comando para reiniciar o terminal:

> $ reset

Pronto! Agora você poderá ver asteriscos quando digitar a senha no terminal!
