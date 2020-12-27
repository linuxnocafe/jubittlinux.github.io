---
title: Executando arquivos AppImage
description: Saiba o que é AppImage e como executá-los.
header: Executando arquivos AppImage
---

Um software Linux típico cria arquivos em vários locais, exigindo permissão de root para fazer essas alterações no sistema.
AppImage não faz isso. Na verdade, o AppImage não instala realmente o software. AppImage é uma imagem compactada com todas as dependências e bibliotecas necessárias para executar o software desejado. AppImage é um formato de software universal compatível com a grande maioria das distribuições Linux.

Quando você executa o arquivo AppImage, o software é executado. Não há extração, nem instalação. Se você exclui o arquivo AppImage, o software é removido.

Características interessantes do AppImage:

* Independente de distribuição;
* Não há necessidade de instalar e compilar o software: basta clicar e executar;
* Não há necessidade de permissão root: os arquivos do sistema não são tocados;
* Os softwares são removidos apenas com a exclusão do arquivo AppImage.

Para executar um AppImage baixe o arquivo desejado. Aqui no nosso exemplo ele será "aplicativo.AppImage".

Entre na /home do seu usuário e crie um diretório para o ".AppImage" que você acabou de baixar. É neste diretório que deve ficar o seu ".AppImage" recém baixado. É importante ter um diretório para cada ".AppImage" por uma questão de organização. Caso o ".AppImage" fique na /home do seu usuário misturado a outros arquivos tendência é que você acabe se esquecendo dele e pode acidentalmente excluí-lo.

```console
$ cd ~/ ; mkdir Aplicativo
```

Agora mova o arquivo ".AppImage" baixado para o diretório que foi criado. No caso a seguir o ".AppImage" foi baixado dentro do diretório ~/Downloads.

```console
$ mv ~/Downloads/aplicativo.AppImage ~/Aplicativo/
```

Dê permissão de execução:

```console
$ cd ~/Aplicativo/

$ chmod +x aplicativo.AppImage
```

Execute da sequinte forma:

```console
$ ./aplicativo.AppImage
```


Até a próxima!
