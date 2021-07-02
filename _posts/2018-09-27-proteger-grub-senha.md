---
title: Protegendo o GRUB com senha
description: Proteja o GRUB com senha e evite alterações indevidas do sistema.
header: Protegendo o GRUB com senha
---

O GRUB (GRand Unifield Bootloader) por padrão carrega diretamente o sistema e permite alteração em suas configurações de inicialização. Esta característica torna tudo mais prático mas por outro lado abre uma brecha para pessoas má intencionadas digitarem comandos e até mesmo alterarem a senha de root.  
Para proteger o sistema de alterações indevidas é possível configurar o GRUB para solicitar senha.
Mas não esqueça de configurar também a bios ou uefi da máquina, caso contrário se o usuário puder acessar as configurações de boot do dispositivo a proteção do GRUB irá por água abaixo. Pois carregar o sistema através de uma mídia permite que alterações e estragos sejam feitos no sistema residente.

Veremos a seguir duas maneiras principais de proteger o GRUB.

**Proteção do menu GRUB**  

Se você quiser proteger o sistema antes do carregamento e evitar o uso da linha de comando é possível adicionar usuário/senha a um arquivo de configuração do GRUB.

Para isso gere uma hash usando o algoritimo pbkdf2 através do seguinte comando:

```bash
$ grub-mkpasswd-pbkdf2  
[...]
Your PBKDF2 is grub.pbkdf2.sha512.10000.hashkey...
```

Então, adicione a hash gerada ao arquivo /etc/grub.d/40_custom:

```bash
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
###### Adicionando o usuário e a hash gerada:
set superusers="usuario"  
password_pbkdf2 usuario grub.pbkdf2.sha512.10000.hashkey...
```

Agora, reconstrua suas entradas do GRUB:

```console
$ sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Pronto! Agora o GRUB solicitará senha para carregar o sistema e para permitir acesso ao menu de configuração.

**Protegendo o GRUB somente contra edições e opções de console**  

Esta opção permite que o sistema carregue sem pedir senha, mas impede que alterações sejam feitas no menu de configurações impedindo, assim, que o usuário digite comandos indesejados e invoque um shell, por exemplo.

Faça o procedimento da etapa acima, gerando a hash e adicionando-a ao /etc/grub.d/40_custom. Abra o arquivo /etc/grub.d/10_linux e adicione a opção "--unrestricted" à variável "CLASS".

```console
$ sudo vi /etc/grub.d/10_linux
```

Procure pela variável "CLASS" (que deve estar no início do arquivo) escrita da seguinte forma:

```console
CLASS="--class gnu-linux --class gnu --class os"
```

Adicione "--unrestricted":

```console
CLASS="--unrestricted --class gnu-linux --class gnu --class os"
```

Reconstrua o GRUB:

```console
$ sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Pronto! O sistema carregará sem pedir senha mas o acesso ao console do GRUB e seus parâmetros estarão restritos.

Para saber mais:

[Proteger GRUB com password - Arch Wiki](https://wiki.archlinux.org/index.php/GRUB/Tips_and_tricks#Password_protection_of_GRUB_edit_and_console_options_only){:target="_blank"}  
[Ubuntu - GRUB2](https://help.ubuntu.com/community/Grub2){:target="_blank"}
