---
title: Emulador de Nintendo 64 no CentOS 7 - Mupen64plus
description: Instale o emulador de N64 no CentOS 7
header: Emulador de Nintendo 64 no CentOS 7 - Mupen64plus
---

Mupen64Plus é um emulador de N64 baseado em plug-ins multiplataforma que é capaz de reproduzir com precisão muitos jogos. Mupen64plus roda a partir do termianl Linux. Existe a possibilidade de executá-lo via interface gráfica se forem instaladas algumas bibliotecas de Python.
Neste tutorial ensinaremos como executar o Mupen64plus somente via linha de comando.

Para instalar o emulador Mupen64plus deveremos instalar o repositório Nux Dextop.
Nux Dextop é um repositório RPM de terceiros que contém pacotes multimídia e de área de trabalho para distribuições como RHEL, CentOS, Oracle Linux e Scientific Linux. Inclui várias aplicações gráficas, bem como programas de terminal. Alguns dos pacotes populares que você encontrará neste repositório incluem Remmina (uma ferramenta de compartilhamento de área de trabalho remota) , VLC media player e muito mais.

Neste post, mostraremos como habilitar o repositório Nux Dextop no CentOS 7 . Note que o repositório Nux Dextop deve coexistir com o repositório EPEL.

> NOTA: Como claramente declarado pelo mantenedor do repositório, este repositório pode entrar em conflito com outros repositórios RPM de terceiros, como Repoforge / RPMforge e ATrpms. Alguns dos pacotes podem ou não estar atualizados, portanto, instale-os por sua conta e risco.

Primeiro inicie importando a chave GPG do Nux Dextop para o seu sistema CentOS usando o seguinte comando:

```console
$ sudo rpm --import http://li.nux.ro/download/nux/RPM-GPG-KEY-nux.ro
```

Em seguida instalamos o repositório Nux Dextop:

```console
$ sudo yum -y install epel-release   
$ sudo rpm -Uvh http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-5.el7.nux.noarch.rpm
```

Em seguida verifique se o repositório foi instalado com sucesso:

```console
$ yum repolist | grep nux-dextop
```

Tendo o repositório sido instalado com sucesso a próxima etapa será instalar alguns pacotes necessários para rodar o Mupen64plus.

```console
$ sudo yum install libodb-boost-devel.x86_64 boost-devel.x86_64 minizip.x86_64 mupen64plus.x86_64
```

NOTA: O emulador Mupen64plus executa por linha de comando. Sendo assim abra-o pelo terminal da seguinte forma:

```console
$ mupen64plus /path/to/rom
```

Para fullscreen aperte [Alt] + [Enter] no teclado.
Caso tenha um joystick este será reconhecido de forma nativa.

Para mais informações: [https://mupen64plus.org/](https://mupen64plus.org/){:target="_blank"}

Boa diversão! E até a próxima!
