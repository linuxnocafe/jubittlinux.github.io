---
title: Executando arquivos AppImage
description: Saiba o que é AppImage e como executá-los.
header: Executando arquivos AppImage
---

AppImage é um formato de software universal compatível com a grande maioria das distribuições Linux.

Um software Linux típico cria arquivos em vários locais, exigindo permissão de root para fazer essas alterações no sistema.
AppImage não faz isso. Na verdade, o AppImage não instala realmente o software. AppImage é uma imagem compactada com todas as dependências e bibliotecas necessárias para executar o software desejado.

Quando você executa o arquivo AppImage, o software é executado. Não há extração, nem instalação. Se você exclui o arquivo AppImage, o software é removido.

Características interessantes do AppImage:

* Independente de distribuição;
* Não há necessidade de instalar e compilar o software: basta clicar e executar;
* Não há necessidade de permissão root: os arquivos do sistema não são tocados;
* Os softwares são removidos apenas com a exclusão do arquivo AppImage.

Para executar um AppImage baixe o arquivo desejado. Aqui no nosso exemplo ele será "aplicativo.AppImage".

Entre no diretório onde baixou:

> $ cd ~/Downloads/

Dê permissão de execução:

> $ chmod +x aplicativo.AppImage

Execute da sequinte forma:

> $ ./aplicativo.AppImage

Para criar um lançador no menu de programas (atalho):

> $ sudo chmod ugo+x Downloads/aplicativo.AppImage

> $ sudo cp Downloads/aplicativo.AppImage /usr/bin/

Até a próxima!
