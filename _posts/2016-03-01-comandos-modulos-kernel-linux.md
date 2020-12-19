---
title: Comandos básicos para manipular módulos do Kernel
description: Aprenda comandos básicos para manipular módulos do Kernel Linux.
header: Comandos básicos para manipular módulos do Kernel
---

Os módulos são componentes do kernel que carregam quando solicitados por algum aplicativo e descarregam após o uso.
Auxiliam a interação do kernel com diversos dispositivos do sistema.
A administração do kernel linux pode exigir em algum momento a manipulação de um módulo. Isto pode ocorrer em diversas ocasiões como,
por exemplo, quando há um conflito entre módulos de mesma função, que são oriundos de desenvolvedores diferentes, gerando, assim, a necessidade de carregar ou descarregar temporariamente a fim de testar um determinado funcionamento. Um exemplo bem conhecido é o conflito entre os drivers Nvidia e Nouveau e seus respectivos módulos.

**lsmod**  
Lista os módulos carregados no sistema. Não possui parâmetros para adicionar ao comando.

> \# lsmod

**modprobe**  
Carrega os módulos e as pendências necessárias para o funcionamento do módulo.

\# modprobe [parametros] [nome-do-modulo]

Exemplo:

> \# modprobe usbcore

Alguns parâmetros:

-a : insere módulos  
-d [diretório] : diretório onde os módulos podem ser encontrados  
-r : remove módulos  
-V ou --version : Exibe informações sobre o comando

Os módulos podem ser encontrados em /lib/modules/versao-kernel.

**insmod**  
Carrega o módulo mas não carrega pendências.

> \# insmod [nome-do-modulo]

Forçar o carregamento:

> \# insmod -f [nome-do-modulo]

A opção acima não é recomenda. Use para carregar um módulo compilado de outro kernel.

Verifica o carregamento:

> \# lsmod \| grep [nome-do-modulo]

**depmod**  
Verifica as dependências do módulo. As dependências são verificadas e gravadas no arquivo /lib/modules/versao-do-kernel/modules.dep. No meu caso é /lib/modules/4.1.18-1-lts/modules.dep.

Exemplo:

> \# depmod -a

Alguns parâmetros:

-a : verifica as dependências de todos os módulos  
-b [diretório] : define o nome do diretório base para gravar o arquivo de saída  
-h : informa os módulos processados  
-V : informa a versão do utilitário

**modinfo**  
Exibe informações sobre o módulo.

> \# modinfo [parametros] [nome-do-modulo]

Alguns parâmetros:
-a : mostra o autor
-d : mostra um breve resumo
-l : mostra licença
-p : mostra parâmetros específicos

Exemplos:

> \# modinfo -a processor  
Paul Diefenbaugh

Ou de outra forma, citando o diretório:

> \# modinfo -a /lib/modules/4.1.18-1 lts/kernel/drivers/powercap/intel_rapl.ko.gz  
Jacob Pan

**rmmod**  
Descarrega um módulo do sistema, mas somente descarrega e não exclui. Na próxima inicialização o módulo é carregado de novo.

> \# rmmod [nome-do-modulo]
