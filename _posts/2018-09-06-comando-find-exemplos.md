---
title: Comando find em 10 exemplos
description: Aprenda a usar o comando find com 10 exemplos.
header: Comando find em 10 exemplos
---

1-) Procurando por arquivos de tipo específico, no diretório corrente (representado por ponto):

> $ find . -name "*.txt"

2-) Busca case insensitive (insensível a caixa alta):

> $ find -iname nomearquivo.txt

3-) Buscando arquivos que não correspondem ao procurado, no diretório corrente:

> $ find . -not -name "*.txt"

4-) Mostrando todos os arquivos vazios, no diretório corrente:

> $ find . -empty

5-) Mostrando arquivos que pertencem a um grupo específico, no diretório corrente:

> $ find . -group meugrupo -name "*.txt"

6-) Mostrando arquivos possuídos por um usuário específico, no diretório corrente:

> $ find . -user nomeusuario -name "*.txt"

7-) Mostrando arquivos modificados um minuto atrás, no diretório corrente:

> $ find . -mmin 1 -name "*.txt"

8-) Comparando arquivos modificados recentemente, no diretório corrente:  
O seguinte comando busca arquivos modificados mais recentemente que o arquivo especificado.

> $ find . -newer velho.txt -name "*.txt"

9-) Procurando arquivos pelo inode, no diretório corrente:

> $ find . -inum 2946

10-) Buscando arquivos com base no último acesso (um minuto atrás):

> $ find -amin 1 -name "*.txt"
