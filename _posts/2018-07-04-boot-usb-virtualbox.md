---
title: Boot por usb no virtualbox - Host Linux
description: Aprendar a dar boot por usb em máquina virtual no virtualbox.
header: Boot por usb no virtualbox - Host Linux
---

Um hipervisor, ou monitor de máquina virtual, é um software, firmware ou hardware que cria e roda máquinas virtuais (VMs). O computador no qual o hipervisor roda uma ou mais VMs é chamado de máquina hospedeira (host), e cada VM é chamada de máquina convidada (guest). [Wikipedia]

O VirtualBox não suporta boot de dispositivos usb por padrão. Mas você pode criar seu arquivo .vmdk que aponta para seu drive usb de boot.

Você deve adicionar sua conta de usuário ao grupo vboxusers para ver seu usb. Você também deve adicionar sua conta ao grupo disk ou você não conseguirá adicionar o arquivo .vmdk a sua máquina virtual. Siga as instruções abaixo.

Primeiro, você deve determinar qual o drive de usb no seu sistema. Isto é feito com o comando:

```console
$ sudo fdisk -l
```

Vamos supor que seu drive esteja montado como /dev/sdb1. Então, o drive físico sera /dev/sdb.

Em seguida, no terminal digite o seguinte para criar o arquivo .vmdk que aponta para o drive usb:

```console
$ sudo vboxmanage internalcommands createrawvmdk -filename  ~/usb.vmdk -rawdisk /dev/sdb
```

A saída deste comando deve ser algo como:

```console
RAW host disk access VMDK file /home/usuario/usb.vmdk created successfully.
```

No terminal execute o seguinte comando:

```console
$ sudo usermod -a -G vboxusers usuario
```

Adicione também ao grupo disk:

```console
$ sudo usermod -a -G disk usuario
```

Agora reinicie o sistema para as alterações tomarem efeito.

Depois de reiniciar:

Então, tudo que você necessita fazer é adicionar o .vmdk a sua máquina virtual para ter certeza de fazer o boot pelo pen drive. Na criação da máquina virtual:

![Boot por usb no VirtualBox](https://raw.githubusercontent.com/linuxnocafe/linuxnocafe.github.io/master/img/VB1.png)
