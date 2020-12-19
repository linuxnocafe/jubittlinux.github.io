---
title: Otimizando o tempo de boot do Linux
description: Veja algumas dicas para otimizar o boot do Linux
header: Otimizando o tempo de boot do Linux
---

O tempo de boot de um S.O. depende de vários fatores. Hardware e configurações do sistema são dois fatores.
Veremos nest post como otimizar o boot de um sistema Linux desabilitando alguns serviços que não interferem na inicialização.
As dicas a seguir são aplicáveis a qualquer distribuição mas neste caso estamos numa distro baseada em systemd. No meu caso estou usando Fedora 30. Meu hardware é composto por um processador Xeon 3040, 4 gb de memória ram DDR2 e um SSD.

Numa primeira análise com "systemd-analyze" podemos ver algums informações onde consta o tempo de boot do sistema:

> [juliana@fedora-linux ~]$ systemd-analyze  
Startup finished in 1.703s (kernel) + 4.394s (initrd) + 11.976s (userspace) = 18.074s  
graphical.target reached after 11.939s in userspace  

Devemos ter em mente que o tempo de boot mostrado acima não computa o tempo de exibição da tela de POST da BIOS. Portanto, aprender a configurar a BIOS é assunto que não abordaremos aqui, mas que pode trazer benefício reduzindo o tempo de carga do sistema como um todo.
O tempo exibido por "systemd-analyze" é computado a partir do boot do Kernel, isto é, a partir da entrada exibida pelo grub na tela.

Vamos fazer uma análise mais detalhada dos serviços usando "systemd-analyze blame":

> [juliana@fedora-linux ~]$ systemd-analyze blame  
        11.098s dnf-makecache.service  
          6.657s gssproxy.service  
          6.285s NetworkManager-wait-online.service  
          3.526s dvboxrv.service  
          2.930s sssd.service  
          2.830s dkms.service  
          2.818s systemd-machined.service  
          2.579s udisks2.service  
          2.262s akmods.service  
          2.118s systemd-udev-settle.service  
          2.106s dracut-initqueue.service  
          1.907s lvm2-monitor.service  
          1.551s plymouth-quit-wait.service  
          1.192s systemd-logind.service  
          1.018s polkit.service  
           960ms systemd-udevd.service  
           881ms ModemManager.service  
           833ms systemd-journald.service  
           740ms initrd-switch-root.service  
           714ms libvirtd.service  
           707ms abrtd.service  
           577ms NetworkManager.service  
           417ms systemd-vconsole-setup.service  
           351ms rtkit-daemon.service  
           326ms cups.service  
           306ms smartd.service  
           304ms systemd-udev-trigger.service  
           286ms avahi-daemon.service  
           279ms initrd-parse-etc.service  
           270ms systemd-journal-flush.service  
           200ms rsyslog.service  
           176ms dracut-pre-pivot.service  
           175ms chronyd.service  
           155ms livesys.service  
           151ms netcf-transaction.service  
           136ms user@1000.service  
           122ms accounts-daemon.service  
           115ms dracut-cmdline.service  
           107ms preload.service  
           102ms dev-mqueue.mount  
           101ms dev-disk-by\x2duuid-fff31ecf\x2dccf0\x2d428a\x2d9145\x2d370a0abc8a76.swap  
           100ms sys-kernel-debug.mount  
            97ms kmod-static-nodes.service  
            94ms auditd.service  
            91ms dev-hugepages.mount  
            91ms systemd-sysctl.service  
            80ms dbus-broker.service  
            80ms nfs-convert.service  
            77ms var-lib-nfs-rpc_pipefs.mount  
            72ms livesys-late.service  
            70ms systemd-tmpfiles-setup-dev.service  
            70ms systemd-fsck@dev-disk-by\x2duuid-4f83ec16\x2de0e9\x2d40a7\x2db0f5\x2dc0e6491cc4fe.service  
            68ms lightdm.service  
            66ms cpupower.service  
            64ms systemd-tmpfiles-clean.service  
            60ms systemd-remount-fs.service  
            58ms vboxautostart-service.service  
            56ms systemd-fsck@dev-disk-by\x2duuid-30d8a2cf\x2d831c\x2d4d5a\x2db162\x2d89fef71cdae1.service  
            51ms initrd-cleanup.service  
            50ms systemd-tmpfiles-setup.service  
            45ms vboxballoonctrl-service.service  
            44ms dracut-pre-udev.service  
            44ms systemd-fsck-root.service  
            44ms systemd-random-seed.service  
            42ms dmraid-activation.service  
            37ms import-state.service  
            33ms plymouth-switch-root.service  
            32ms boot.mount  
            30ms systemd-update-utmp-runlevel.service  
            26ms home.mount  
            26ms vboxweb-service.service  
            22ms user-runtime-dir@1000.service  
            21ms sysroot.mount  
            19ms plymouth-start.service  
            18ms plymouth-read-write.service  
            17ms systemd-update-utmp.service  
            16ms dracut-shutdown.service  
            16ms systemd-user-sessions.service  
            15ms initrd-udevadm-cleanup-db.service  
            15ms rpc-statd-notify.service  
            13ms tmp.mount  
             9ms sys-kernel-config.mount  
           136us iscsi-shutdown.service  


Quais serviços desabilitar?

Para saber quais serviços desabilitar teremos que pesquisar e estudar um pouco o sistema para saber o que faz cada serviço e o que pode ocorrer caso algum deles seja desabilitado. No meu caso, após um pouco de pesquisa, eu desabilitei os seguintes serviços:


  * **NetworkManager-wait-online.service** serve para acessar automaticamente recursos remotos.


  * **sssd.service** utilizado para logins com usuários de rede. Serviço relacionado ao ldap. Se você não faz login por rede pode desabilitar.


  * **lvm2-monitor.service** gerencia unidades configuradas em LVM. Se você não usa LVM pode desabilitar.



  * **ModemManager.service** serve para emparelhamento de aparelhos via bluetooth ou banda móvel.


  * **dvboxrv.service, vboxballoonctrl-service.service, vboxautostart-service.service, vboxweb-service.service** serviços relacionados ao VirtualBox. É seguro desabilitar.



  * **abrtd.service** ferramenta de relatório de crash do sistema. Pode ser desabilitado para não rodar na inicialização.  

  * **cups.service** serviço de impressão.

  * **libvirtd.service** relacionado à virtualização.


  * **avahi-daemon.service** permite descobrir automaticamente os recursos de rede e se conectar a eles.


  * **accounts-daemon.service** permite programas obterem e manipularem informações de contas de usuários.

Desabilitando um serviço:

> $ sudo systemctl disable nome-do-serviço.service

Também existe a opção mascarar o serviço. É uma opção mais forte que disable, pois não permite que o serviço se inicie de forma alguma, nem manualmente.

> $ sudo systemctl mask nome-do-serviço.service 

Para desmacarar:

> $ sudo systemctl unmask nome-do-serviço.service 

Após desabilitar alguns serviços analisamos de novo o tempo de boot do sistema. Conforme podemos ver houve uma pequena redução no tempo de boot.

> [juliana@fedora-linux ~]$ systemd-analyze  
Startup finished in 1.700s (kernel) + 4.570s (initrd) + 10.420s (userspace) = 16.691s  
graphical.target reached after 10.387s in userspace  

Podemos também gerar um gráfico:  

> $ systemd-analyze plot > boot.svg  

![Gráfico do tempo de boot](https://raw.githubusercontent.com/linuxnocafe/linuxnocafe.github.io/master/img/tempo-boot-linux.png)

Este foi o resultado obtido numa primeira triagem. Podemos pesquisar mais e refinar mais ainda o processo de boot.
Espero ter ajudado.

Até próxima!
