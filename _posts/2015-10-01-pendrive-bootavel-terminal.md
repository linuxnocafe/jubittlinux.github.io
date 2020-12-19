---
title: Criando pendrive bootável pelo terminal
description: Aprenda a criar um pendrive bootável pelo terminal usando o comando dd.
header: Criando pendrive bootável pelo terminal
---

Inicializar o sistema por uma mídia usb é bastante útil e econômico porque pode poupar cds e dvds gravados que talvez não sejam usados mais de uma vez. É possível fazer o boot a partir do pendrive para instalar o sistema operacional. Você precisa ter a imagem no formato .iso para gravá-la no dispositivo usb. No Linux é possível fazer a gravação pelo terminal e dispensar programas como Unetbootin.

Use de preferência um pendrive previamente formatado.
Coloque o pendrive na entrada usb. Digite:

> $ sudo fdisk -l

Procure pelo pendrive. Usei um de 8GB. Antente para o tamanho da unidade na hora de localizar. A saída:

> Disco /dev/sdb: 7,5 GiB, 8016363520 bytes, 15656960 setores  
Unidades: setor de 1 * 512 = 512 bytes  
Tamanho de setor (lógico/físico): 512 bytes / 512 bytes  
Tamanho E/S (mínimo/ótimo): 512 bytes / 512 bytes  
Tipo de rótulo do disco: dos  
Identificador do disco: 0x68ceed8e

O pendrive está identificado como "Disco /dev/sdb: 7,5 GiB, 8016363520 bytes, 15656960 setores". Não coloquei acima mas também serão listadas as partições; por exemplo /dev/sdb1 e /dev/sdb2. Mas não é a partição que vamos indicar na gravação é a unidade (/dev/sdX).

Desmonte:

> $ sudo umount /dev/sdb

Para funcionar corretamente é necessário fazer a gravação com a unidade desmontada.

Agora vamos usar o comando dd para enviar a imagem a ser gravada. Certifique-se que a imagem está no formato .iso.

A sintaxe é assim:

> $ sudo dd bs=4M if=/caminho/imagem-de-boot.iso of=/dev/sdb

Você pode usar a opção block size (bs) para especificar a taxa de transferência de dados. Mas é dispensável. Agora aguarde a finalização. Demora um pouco.

Depois de finalizado chegou a hora de testar. Reinicie. É bom saber se a inicialização do computador a ser usado é UEFI ou BIOS porque é necessário alterar as configurações de boot, como desabilitar UEFI e habilitar USB em primeiro lugar.  A primeira vez que usei este tipo de mídia bootável tive dificuldade para inicializar e achei que fosse problema na gravação. Mas a questão foi que a imagem no pendrive não iniciou automaticamente e precisei pressionar "F8" para ter acesso a um menu com a opção dos dispositivos. Por isso, em caso de dúvida procure informações sobre a placa-mãe.
