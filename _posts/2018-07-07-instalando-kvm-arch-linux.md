---
title: Instalando o KVM no Arch Linux e derivados
description: Aprenda a instalar o KVM, um sistema de virtualização baseado no Kernel Linux.
header: Instalando o KVM no Arch Linux e derivados
---

Usuários de linux não necessitam de VMware ou VirtualBox para rodarem máquinas virtuais. KVM (Kernel-Based Virtual Machine) é uma infraestrutura de virtualização baseada no kernel Linux. Usando KVM é possível executar vários sistemas operacionais incluindo Linux, Microsoft Windows, e qualquer outro sistema operacional.

Neste artigo vamos ver como instalar o KVM no Arch Linux e no Manjaro.

**Verificando o suporte do Hardware**

Antes de instalar o KVM é necessário checar se o hardware do seu computador suporta máquinas virtuais. Para processadores Intel o KVM requer VT-x e para processadores AMD requer AMD-V.

Para checar digite no terminal:

```console
$ LC_ALL=C lscpu | grep Virtualization
```

Exemplo de saída:

```bash
$ LC_ALL=C lscpu | grep Virtualization  
Virtualization:      VT-x
```

Se seu computador suportar virtualização a saída do comando deve ser "Virtualization: VT-x" ou "Virtualization: AMD-V".

Se nada for exibido é provável que seu PC não possa ser usado para instalar máquinas virtuais. Não é o fim do mundo. Alguns fabricantes às vezes desabilitam esta configuração por padrão. Para ter certeza, cheque a BIOS do seu computador. Consulte o fabricante e o manual para verificar como entrar na BIOS.

**Verificando o suporte do Kernel**

Você também necessita ter o módulo do Kernel instalado no seu computador para suportar o KVM.

No terminal digite o seguinte comando para verificar:

```console
$ zgrep CONFIG_KVM /proc/config.gz
```

Cheque a saída. Você deve ver CONFIG_KVM_INTEL ou CONFIG_KVM_AMD como 'm' ou 'y'. Abaixo a saída no meu PC:

```bash
$ zgrep CONFIG_KVM /proc/config.gz
CONFIG_KVM_GUEST=y  
# CONFIG_KVM_DEBUG_FS is not set  
CONFIG_KVM_MMIO=y  
CONFIG_KVM_ASYNC_PF=y  
CONFIG_KVM_VFIO=y  
CONFIG_KVM_GENERIC_DIRTYLOG_READ_PROTECT=y  
CONFIG_KVM_COMPAT=y  
CONFIG_KVM=m  
CONFIG_KVM_INTEL=m  
CONFIG_KVM_AMD=m  
CONFIG_KVM_MMU_AUDIT=y  
```

**Instalando o KVM (Virtual Machine Manager)**

Digite no terminal o seguinte comando:

```console
$ sudo pacman -S virt-manager qemu vde2 ebtables dnsmasq bridge-utils openbsd-netcat
```

Os próximos dois passos são muito importantes e frequentemente ignorados por muitos usuários. Tenha certeza de concluí-los. Quando você executar o Virtual Machine Manager depois da instalação você verá o erro "adduser: The group 'libvirtd' does not exist".

Habilite o serviço através do seguinte comando:

```console
$ sudo systemctl enable libvirtd.service
```

Inicie o serviço através do seguinte comando:

```console
$ sudo systemctl start libvirtd.service
```

O Virtual Machine Manager agora deve estar instalado no seu computador. Você pode executá-lo procurando por "Virtual Machine Manager" nas suas aplicações, e não KVM!

**Troubleshooting**

Caso em futuras execuções da máquina virtual você se depare com o erro "network 'default' is not active", execute os seguintes comandos:

```console
$ sudo virsh net-list --all
```

```console
$ sudo virsh net-autostart default
```

```console
$ sudo virsh net-start default
```

Para mais detalhes de troubleshooting consulte o seguinte link:  
[http://ask.xmodulo.com/network-default-is-not-active.html](https://www.xmodulo.com/network-default-is-not-active.html)
