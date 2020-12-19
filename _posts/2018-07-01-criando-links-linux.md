---
title: Criando Links
description: Aprenda a criar links, arquivos especiais que remetem a outro arquivo.
header: Criando Links
---

Os links, que em português chamamos atalhos, são arquivos especiais que remetem a outro arquivo armazenado no computador.
No Linux, temos dois tipos de atalhos: os atalhos físicos (hard links) e os atalhos simbólicos (soft links).

Atalho físico é simplesmente um outro nome atribuído a determinado arquivo: em palavras mais simples, é como se fosse um apelido do arquivo. Não há diferença alguma entre usar o arquivo em si ou seu atalho físico, pois, de fato, trata-se de um único arquivo porém com dois nomes.

O atalho simbólico, também chamado soft-link ou symlink é, de fato, um simples atalho: ao abri-lo, ele nos remeterá ao arquivo original, que será aberto e, eventualmente, alterado e salvo.
Um atalho simbólico pode ser excluído a qualquer momento sem que o arquivo ao qual se refira sofra qualquer alteração. Para quem já tem familiaridade com o sistema operacional Windows, os atalhos simbólicos funcionam exatamente como ícones de atalho desse sistema: podem ser movidos, renomeados e excluídos, mas o arquivo ao qual se referem permanecerá inalterado.

Por exemplo, para criar um link físico chamado texto_usuario para o arquivo meu_texto.txt, basta digitar a seguinte linha:

> $ ln meu_texto.txt texto_usuario

É importante lembrar que, dessa forma, criamos um atalho um atalho físico, isto é, qualquer operação feita em texto_usuario se refletirá no arquivo meu_texto.txt, e vice-versa.
Para criar um link simbólico, basta acrescentar a opção -s. Um exemplo disso é a linha de comando a seguir:

> $ ln -s meu_texto.txt texto_usuario

Assim, o atalho criado será do tipo simbólico: qualquer alteração feita em texto_usuario interessará ao arquivo meu_texto.txt, porém, a exclusão do atalho texto_usuario não acarretará a perda do arquivo em si.

Os links são arquivos especiais e podem ser identificados com a letra "l" ao digitar ls no terminal. Exemplo:

> $ ls -l

Fonte: Curso prático de Linux - Ferrari, Fabrício Augusto. 
