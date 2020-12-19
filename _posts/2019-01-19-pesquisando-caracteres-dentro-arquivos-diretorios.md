---
title: Pesquisando caracteres dentro de arquivos e diretórios
description: Use o comando grep para fazer pesquisas dentro de arquivos e diretórios
header: Pesquisando caracteres dentro de arquivos e diretórios
---

Este post irá orientá-lo sobre como achar cadeias de caracteres específicas dentro de arquivos ou diretórios.
Uma maneira simples de resolver isso é usando a ferramenta de busca de padrões grep, que é um utilitário de linha de comando. O grep é poderoso, eficiente e confiável. É o mais popular para encontrar padrões e palavras dentro de arquivos ou diretórios em sistemas Unix-like.

O comando abaixo listará todos os arquivos contendo uma linha com o texto “banana”, procurando de forma recursiva no diretório /bin dentro da home do usuário (~).

> $ grep -Rw ~/bin -e 'banana'  
/home/juliana/bin/minhas_frutas.txt:banana

Onde a opção -R diz ao grep para ler todos os arquivos em cada diretório, recursivamente. A opção -w instrui o grep a selecionar apenas as linhas contendo correspondências que formam palavras inteiras. A opção -e é usado para especificar a string (padrão) a ser pesquisada.

Você deve usar o comando sudo ao pesquisar determinados diretórios ou arquivos que requerem permissões de root, a não ser que você esteja gerenciando seu sistema com a conta root.

Para ignorar caixa alta use a opção -i:

> $ grep -Riw ~/bin -e 'MELANCIA'  
/home/juliana/bin/minhas_frutas.txt:melancia

Para saber a linha exata em que aparece a string procurada use a opção -n:

> $ grep -Rinw ~/bin -e 'MELANCIA'  
/home/juliana/bin/minhas_frutas.txt:4:melancia

Supondo que existem vários tipos de arquivos em um diretório que você deseja pesquisar, você também pode especificar o tipo de arquivo a ser pesquisado usando a opção --include:

> $ grep -Rnw --include=\\*.sh ~/bin -e 'melancia'  
/home/juliana/bin/minhas_frutas.sh:4:melancia  
/home/juliana/bin/minhas_frutas.sh:9:melancia  

Além disso, é possível procurar por mais de um padrão, usando a opção -e duas vezes, como a seguir:

> $ grep -Rinw ~/bin -e 'abacate' -e 'banana'  
/home/juliana/bin/minhas_frutas.txt:1:banana  
/home/juliana/bin/minhas_frutas.txt:3:abacate  
/home/juliana/bin/minhas_frutas.sh:1:banana  
/home/juliana/bin/minhas_frutas.sh:3:abacate  


Até o próximo tutorial!

