---
title: Configurando o GCC na IDE Geany
description: Aprenda a configurar o compilador GCC na IDE Geany
header: Configurando o GCC na IDE Geany
---

Geany é uma IDE (Integrated Development Environment), ou Ambiente de Desenvolvimento Integrado, pouco conhecida mas muito leve e eficiente. Tem suporte a muitas linguagens (programação, marcação e estilos). Algumas delas são: C, Java, PHP, Python, Perl, Pascal, HTML. Está disponível para Linux, FreeBSD, NetBSD, OpenBSD, MacOS X, AIX v5.3, Solaris Express e Windows. Geralmente, roda em qualquer plataforma com suporte às biliotecas GTK+.  

Principais funcionalidades:  
- Destaque colorido para sintaxe;  
- Dobramento de código (parcialmente implementado);  
- Autocompletar;  
- Autofechamento para tags XMl e HTML;  
- Lista de símbolos;  
- Navegar código;  
- Construção (compilar e executar);  
- Gerenciamento de projeto;  
- Extensão de plugins;  
- Acesso ao terminal de sua preferência (configurável).  

Instalando Geany no Arch:

```console
$ sudo pacman -S geany
```

Instalando Geany no Debian e derivados:

```console
$ sudo apt install geany
```

O GCC (GNU Compiler Collection) é um conjunto de compiladores de linguagem de programação. Originalmente suportava somente a linguagem C e era denominado GNU C Compiler. Posteriormente ganhou suporte à outras linguagens. Para configurá-lo na Geany acesse o menu "Construir >> Definir comandos de construção". 

Na seção "Comandos independentes" adicione as seguintes configurações:  

Construir -> gcc -Wall -o "%e" "%f"  
Construir -> gcc -Wall -c "%f"    

Na seção "Executar comandos" adicione o seguinte:

Execute ->  ./%e                

Deve ficar como a seguir:

![Geany-Definir Comandos de Construir](https://raw.githubusercontent.com/linuxnocafe/linuxnocafe.github.io/master/img/geany-gcc-1.png#responsive)
 
Clique em [ OK ]. Escreva um programa em C e salve com a extensão .c. Por exemplo, "meu-programa.c". Aperte [ F9 ] para construir e [ F5 ] para executar.

No diretório em que foi criado o programa vai aparecer um segundo objeto com o mesmo nome, mas sem extensão ponto c.

Então, no terminal, execute:  

```console
$ ./meu-programa 
```

