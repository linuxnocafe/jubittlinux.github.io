---
title: lsof em 9 exemplos práticos
description: Aprenda a usar o comando lsof para listar arquivos abertos por processos
header: lsof em 9 exemplos práticos
---

lsof significa "LiSt Open Files" e é usado para descobrir qual arquivo está em uso por qual processo.
A seguir vamos ver alguns exemplos para o comando lsof.

1) Lista todos os arquivos abertos:

```console
# lsof
```

![Exemplo lsof](https://raw.githubusercontent.com/linuxnocafe/linuxnocafe.github.io/master/img/lsof-sample.png)

Onde FD significa File Descriptor e pode conter os seguintes valores:

cwd - current working directory  
rtd - root directory  
txt - program text  
mem - memory-mapped file  

Também na coluna FD podem constar valores como 1u como file descriptors seguidos de seu modo de acesso:

r - acesso de leitura  
w - acesso de escrita  
u - acesso de leitura e escrita  

Na coluna TYPE consta o tipo de identificação:

DIR - Directory  
REG - Regular File  
CHR - Character Special File  
FIFO - First In First Out  

2) Listar arquivos abertos por determinado usuário:

```console
# lsof -u usuario
```

3) Achar processos rodando em uma porta específica:

```console
# lsof -i TCP:53
```

4) Listar somente arquivos abertos com protocolo IPv4 ou IPv6:

```console
# lsof -i 4
```

```console
> \# lsof -i 6
```

5) Listar arquivos abertos no intervalo de portas TCP 1-1024:

```console
# lsof -i TCP:1-1024
```

6) Listar arquivos abertos por processos excluindo um determinado usuário:

```console
# lsof -i -u^usuario
```

7) Listar todas as conexões:

```console
# lsof -i
```

8) Listar processos pelo PID. No exemplo a seguir listamos processos pelo PID 1:

```console
> \# lsof -p 1
```

9) Matar/encerrar toda atividade de um usuário específico:

```console
# kill -9 lsof -t -u usuario
```

Até a próxima!
