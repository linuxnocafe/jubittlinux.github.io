---
title: Recuperando o GRUB com System RescueCD
description: Recupere o GRUB a partir da distribuição System RescueCD.
header: Recuperando o GRUB com System RescueCD
---

[System Rescue CD](http://www.sysresccd.org/){:target="_blank"} é uma distribuição linux baseada em [Gentoo](https://www.gentoo.org/){:target="_blank"}, usada para corrigir problemas e fazer diagnósticos. Pode ser gravada em CD ou pendrive para rodar na inicialização. Conta com muitas ferramentas:

- GNU Parted: cria, redimensiona, move, copia partições e sistemas de arquivos;
- GParted: implementação gráfica do GNU Parted library;
- Partimage: cria imagem de partições e disco inteiros similar ao Ghost;
- ddrescue: tenta efetuar cópia corrigida da partição com erros;
- FSArchiver: semelhante ao Partimage. Pode clonar discos e criar imagem de partições;
- Ntfs3g: permite acesso de leitura e escrita às partições Windows em sistema de arquivos NTFS;
- sfdisk: salva e restaura tabela de partições;
- Test-disk: verifica e recupera tabela de partições apagadas. Suporta reiserfs, ntfs, fat32, ext2/3 e outros;
- Memtest+: teste de memória;
- Rsync: efetua backup remoto por sincronia de dados;
- Ferramentas de rede (Samba, NFS, ping, nslookup, ...).

Suponha que ocorra um problema na inicialização do sistema e o GRUB não funcione corretamente. O sistema operacional não inicia. Podemos usar o System Rescue CD para carregar o sistema instalado e reinstalar o GRUB.
Inicialize com o System Rescue e selecione a opção "**Boot an existing Linux installed on the disk**".

Podemos agora reinstalar o GRUB. A instalação requer um usuário com privilégios de administrador. Em sistemas Debian e derivados podemos recorrer ao apt-get:

> \# apt-get install grub

Crie uma pasta grub em /boot

> \# mkdir /boot/grub

Atualize o grub para criar o arquivo menu.lst

> \# update-grub

Adicione o grub ao setor MBR (Master Boot Record). As informações do setor MBR serão substituídas.

> \# grub-install hd0

Reinicie o sistema sem o System Rescue.





