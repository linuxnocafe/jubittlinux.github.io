---
title: Pesquisando caracteres dentro de arquivos e diretórios
description: Use o comando grep para fazer pesquisas dentro de arquivos e diretórios
header: Pesquisando caracteres dentro de arquivos e diretórios
---

Este post irá orientá-lo sobre como achar cadeias de caracteres específicas dentro de arquivos ou diretórios. Uma maneira simples de resolver isso é usando a ferramenta de busca de padrões "grep", que é um utilitário de linha de comando. O "grep" é poderoso, eficiente e confiável. É o mais popular para encontrar padrões e palavras dentro de arquivos ou diretórios em sistemas Unix-like.

Dentro da /home do usuário vamos criar um diretório chamado "frutas" e em seguida vamos inserir uma sequência de nome de frutas em um arquivo .txt chamado "minhas_frutas.txt". Os nomes serão inseridos usando o comando "echo" de forma que cada item fique sozinho em cada linha (haverá quebra de linha).

```console
$ cd ~/
$ mkdir frutas
$ echo -en 'banana \nabacaxi \nmaçã \nuva \nlaranja n\' > ~/frutas/minhas_frutas.txt
```

O comando abaixo listará todos os arquivos contendo uma linha com o texto “banana”, procurando de forma recursiva no diretório "frutas" dentro da /home do usuário (~). Criamos o diretório de nome "frutas" mas você pode criar um diretório de nome qualquer dentro da sua /home para pode praticar.

```console
$ grep -Rw ~/frutas -e 'banana' 
/home/user/frutas/minhas_frutas.txt:banana 
```

Onde a opção -R diz ao "grep" para ler todos os arquivos em cada diretório, recursivamente. A opção -w instrui o "grep" a selecionar apenas as linhas contendo correspondências que formam palavras inteiras. A opção -e é usado para especificar a string (padrão) a ser pesquisada.

Para ignorar caixa alta use a opção -i:

```console
$ grep -Riw ~/frutas -e 'LARANJA' 
/home/user/frutas/minhas_frutas.txt:laranja 
```

Para saber a linha exata em que aparece a string procurada use a opção -n:

```console
$ grep -Rinw ~/frutas -e 'LARANJA' 
/home/user/frutas/minhas_frutas.txt:5:laranja 
```

Você também pode especificar o tipo de arquivo a ser pesquisado usando a opção "--include". No exemplo a seguir temos um arquivo em bash ".sh" que contém a mensagem "Hello! Prefiro abacaxi.". No caso abaixo estamos procurando pela palavra "Hello" em arquivos ".sh".

```console
$ grep -Rnw ~/frutas --include=\*.sh -e 'Hello'
/home/user/frutas/frutas.sh:4:echo "Hello! Prefiro abacaxi."
```

Além disso, é possível procurar por mais de um padrão, usando a opção -e duas vezes, como a seguir:

```console
$ grep -Rinw ~/frutas -e 'laranja' -e 'abacaxi'
/home/user/frutas/frutas.sh:4:echo "Hello! Prefiro abacaxi."
/home/user/frutas/minhas_frutas.txt:2:abacaxi 
/home/user/frutas/minhas_frutas.txt:5:laranja 
```

Até o próximo tutorial!

