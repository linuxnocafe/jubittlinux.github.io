---
title: Gerenciando pacotes no Python com PIP 
description: Gerencie pacotes no Python com o utilitário PIP
header: Gerenciando pacotes no Python com PIP
---


Como acontece com quase qualquer linguagem de programação, o Python suporta bibliotecas e estruturas de terceiros que você pode instalar para evitar ter que reinventar a roda a cada novo projeto. Você pode encontrá-los em um repositório central chamado PyPI (Python Package Index).

PIP é um acrônimo recursivo que significa “PIP Installs Packages” ou “Preferred Installer Program”. É um utilitário de linha de comando que permite instalar, reinstalar ou desinstalar pacotes com um comando simples e direto.

Se você estiver usando o Python 2.7.9 (ou superior), o PIP vem instalado com o Python por padrão. Se você estiver usando uma versão mais antiga do Python, precisará usar as etapas de instalação abaixo. Caso contrário, pule para a etapa posterior deste post para saber como começar a usar o PIP.

Primeiramente vamos verificar se o python está instalado e em qual versão:

```console
$ python --version
```

Para verificar se a versão 3.X está presente:

```console
$ python3 --version
```

Se você obtiver um número de versão significa que o Python está pronto para ser usado.

Se você receber uma mensagem “Python is not defined”, será necessário primeiro instalar o Python corretamente. Visite o site do Python para obter instruções.

O Linux já vem com Python instalado por padrão. Verifique a versão do Python em seu sistema, como mostrado acima, para instalar a versão correta de PIP.

Instalando em Debian e derivados (Python 2.x):

```console
$ sudo apt-get install python-pip
```

Instalando em Debian e derivados (Python 3.x):

```console
> $ sudo apt-get install python3-pip
```

Arch Linux (Python 2.x):

```console
$ sudo pacman -S python2-pip
```

Arch Linux(Python 3.x):

```console
$ sudo pacman -S python-pip
```

CentOS (Python 2.x):

```console
$ sudo yum upgrade python-setuptools  
$ sudo yum install python-pip python-wheel
```

CentOS (Python 3.x):

```console
$ sudo yum install python3 python3-wheel
```

Embora o próprio PIP não seja atualizado com muita frequência, ainda é importante manter-se atualizado sobre as novas versões, pois pode haver correções importantes para bugs, compatibilidade e falhas de segurança. Felizmente, atualizar o PIP é muito rápido e simples.

```console
$ pip install -U pip
```console

Pode ser que você precise usar pip3 dependendo da versão de Python instalada em seu sistema. Fica assim:

```console
$ pip install -U pip3
```

Os usuários do Python 2.x devem usar o pip enquanto os usuários do Python 3.x devem usar o pip3 ao emitir comandos PIP.

Quando o PIP estiver pronto, você pode começar a instalar pacotes:

```console
$ pip install package-name
```

Para instalar uma versão específica de um pacote em vez da versão mais recente:

```console
$ pip install package-name==2.0.0
```

Para procurar por um pacote específico:

```console
$ pip search package
```

Para ver detalhes sobre um pacote instalado:

```console
$ pip show package-name
```

Para listar todos os pacotes instalados:

```console
$ pip list
```

Para listar todos os pacotes desatualizados:

```console
$ pip list --outdated
```

Para atualizar um pacote desatualizado:

```console
$ pip install package-name --upgrade
```

Observe que as versões mais antigas de um pacote são automaticamente removidas pelo PIP ao atualizar para uma versão mais recente desse pacote.

Para reinstalar completamente um pacote:

```console
$ pip install package-name --upgrade --force-reinstall
```

Para remover completamente um pacote:

```console
$ pip uninstall package-name  
```


