---
title: Tarball em 11 exemplos
description: Aprenda a usar o comando tar para agrupar arquivos.
header: Tarball em 11 exemplos
---

Tarball é um termo usado para um grupo de arquivos empacotados conjuntamente. O termo sugere uma bola de alcatrão (tar), um derivado do carvão, de consistência pegajosa usada como selante em coberturas e outras obras de construção  
"tar" (Tape ARchive) é um comando que agrupa diversos arquivos em um único, a partir de outros, possibilitando que sejam depois extraídos separadamente. Um arquivo "tar" tem o sufixo ".tar".  
Podemos usar "tar" juntamente com gzip (.gz) e bzip2 (.bz2) para criar arquivos comprimidos, visto que "tar" não comprime; somente agrupa.  
Outros formatos de compactação: zip e rar. Mas estes não serão abordados aqui. O foco aqui é o tarball.
Tarball é bastante útil quando quando queremos, por exemplo, enviar vários arquivos por email ou transferí-los de um dispositivo para outro.
Muitos downloads para Linux estão no formato tar, por isso é bastante útil conhecer esta ferramenta.

Sintaxe:

> tar [opções] arquivo.tar arquivo1 arquivo2 ...

Resumo das opções que vamos ver:   


|---|---|
| -A  | --catenate --concatenate |
| -c  | --create   |
| -r  | --append|
| -t  | -- list  |
| -x  | --extract --get   |
| -C  | --directory DIR  |
| -f  | --file F  |
| -j  | --bzip   |
| -v  | --verbose  |
| -z  | --gzip  |
|     | --delete  |  
|     |   |

1-) Empacotando alguns arquivos:

> $ tar -cf minhaslistas.tar lista1.txt  lista2.txt lista3.txt...

2-) Listando os arquivos no tarball:

> $ tar -tf minhaslistas.tar

3-) Extraindo todos os arquivos:

> $ tar -xf minhaslistas.tar

4-) Deletando um componente:

> $ tar --delete -f  minhaslistas.tar  lista2.txt 

5-) Adicionando um componente ao final. O arquivo será inserido no final do tarball:

> $ tar -rf minhaslistas.tar lista2.txt  

Agora vamos listar o conteúdo:  

> $ tar -tf minhaslistas.tar  
lista1.txt  
lista3.txt  
lista2.txt

6-) Concatenando tarballs:  

> $ tar -Af minhaslistas.tar outroarquivo.tar

7-) Extraindo para um diretório já existente:

> $ tar -xvf minhaslistas.tar -C /home/usuario/extraidos

8-) Criar tar compactado com gzip (tar + gzip):

> $ tar -cvzf minhaslistas.tar.gz lista1.txt lista2.txt

9-) Extrair gzip:

> $ tar -xvzf minhaslistas.tar.gz

10-) Criar tar compactado com bzip2 (tar + bzip2):

> $ tar -cvjf minhaslistas.tar.bz2 lista1.txt lista2.txt 

11-) Extrair bzip2:

> $ tar -xvjf minhaslistas.tar.bz2
