---
title: Instalando o LibreOffice no Oracle Solaris 11
description: Aprenda a instalar o LibreOffice no Oracle Solaris 11.
header: Instalando o LibreOffice no Oracle Solaris
---

Para instalar o Libreoffice no Solaris 11 precisamos adicionar um repositório chamado OpenCashew (opencsw).

Para registrar um novo repositório execute com permissão de administrador:

```console
# pkg set-publisher -G '*' -g http://sfe.opencsw.org/localhosts11 localhosts11
```

Quando seu repositório estiver pronto você pode intalar o LibreOffice.

LibreOffice 4.4.x vem em 2 pacotes: libreoffice4 libreoffice4-desktop-int  
LibreOffice 5.2.x vem em 2 pacotes: libreoffice52 libreoffice52-desktop-int

Escolha a opção que quer instalar.

Para LibreOffice 5.2.x execute:

```console
# pkg install -v libreoffice52 libreoffice52-desktop-int
```

Para LibreOffice 4.4.x execute:

```console
# pkg install -v libreoffice4 libreoffice4-desktop-int
```

Durante a instalação o pkg irá instalar todas as bibliotecas necessárias e outros pacotes.

Se a instalação falhar por causa da internet você terá de executar novamente o comando e ele continuará de onde parou.

Quando a instalação acabar você pode iniciar o libreoffice do seu desktop: menu Aplicações -> Escritório -> LibreOffice.

Você pode checar se há atualizações executando o seguinte:

```console
# pkg refresh
```

```console
# pkg update -nv
```
