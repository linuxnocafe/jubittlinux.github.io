---
title: Introdução à história dos containers
description: Do chroot ao Docker, uma breve história
header: Introdução à história dos containers
---

Ema março de 2018 o Docker completou cinco anos de existência. Mas essa não foi a primeira vez que ouvimos falar em conteiners. Em homenagem ao Docker, vamos fazer uma viagem ao passado e dar uma olhada nos principais marcos da vida útil dos containers virtualizados.

**1979: Unix V7**

O primeiro registro de conteiners refere-se ao chroot. Este foi implementado durante o desenvolvimento do Unix V7, em 1979. O chroot foi introduzido, mudando o diretório raiz de um processo e seus filhos para um novo local no sistema de arquivos. Esse avanço foi o início do isolamento do processo: a segregação do acesso a arquivos para cada processo. Chroot foi adicionado ao BSD em 1982. 

![Chroot como sistema de isolamento](https://raw.githubusercontent.com/linuxnocafe/linuxnocafe.github.io/master/img/chroot-sample.png#responsive)


**2000: Jails - FreeBSD**

Um pequeno provedor de hospedagem surgiu com o Jails do FreeBSD, para conseguir uma separação clara entre os seus serviços e os de seus clientes para fins de segurança e facilidade de administração.
O FreeBSD Jails permite que os administradores particionem um sistema em vários sistemas menores e independentes - chamados de “jails” - com a capacidade de designar um endereço IP para cada sistema e configuração.

**2001: Linux VServer**

Como o FreeBSD Jails, o Linux VServer é um mecanismo que pode particionar sistemas de arquivos, endereços de rede e memória num sistema. Originado em 2001, este sistema de virtualização foi implementado por patch no Kernel Linux. Patchs experimentais ainda estão disponíveis, mas o útimo patch estável foi lançado em 2006.

**2004: Solaris Containers**

Em 2004, o primeiro beta público de Containers Solaris  foi lançado. O recurso separa e limita os recursos por zonas.

**2005: Open VZ (Open Virtuzzo)**

Essa é uma tecnologia de virtualização em nível de sistema operacional. Usa um kernel Linux corrigido para virtualização, isolamento, gerenciamento de recursos e verificação. O código não foi lançado como parte do kernel oficial do Linux.

**2006: Process Containers**

Process Containers (lançado pelo Google em 2006) foi projetado para limitar, contabilizar e isolar o uso de recursos (CPU, memória, E / S de disco, rede) de uma coleção de processos. Ele foi renomeado para “Grupos de Controle (cgroups)” um ano depois e acabou se fundindo ao kernel Linux 2.6.24.

**2008: LXC**

O LXC (LinuX Containers) foi a primeira e mais completa implementação do gerenciador de containers do Linux. Foi implementado em 2008. Funciona em um único kernel Linux sem a necessidade de correções. 

**2011: Warden**

A CloudFoundry iniciou o Warden em 2011, usando o LXC nos estágios iniciais e depois substituindo-o por sua própria implementação. Warden pode isolar ambientes em qualquer sistema operacional, sendo executado como um daemon e fornecendo uma API para gerenciamento de containers. Foi desenvolvido um modelo cliente-servidor para gerenciar uma coleção de containers em vários hosts, e Warden inclui um serviço para gerenciar cgroups, namespaces e o ciclo de vida do processo.

**2013: LMCTFY**

Let Me Contain That For You (LMCTFY). As aplicações podem ser feitas com “conhecimento de container”, criando e gerenciando seus próprios sub-recipientes. A implantação ativa no LMCTFY foi interrompida em 2015 depois que o Google começou a contribuir com os principais conceitos do LMCTFY para o libcontainer, que agora faz parte da Open Container Foundation .

**2013: Docker**

Quando o Docker surgiu em 2013, os containers explodiram em popularidade. Não é coincidência o crescimento do  Docker e o uso de containers andarem de mãos dadas. Assim como Warden fez, o Docker também usou o LXC em seus estágios iniciais e depois substituiu esse gerenciador de container por sua própria biblioteca, o libcontainer. Mas não há dúvidas de que o Docker se separou do pacote oferecendo um ecossistema inteiro para o gerenciamento de containers.  

**2017: as ferramentas de container se tornam maduras**

Centenas de ferramentas foram desenvolvidas para facilitar o gerenciamento de containers. Embora esses tipos de ferramentas existam há anos, 2017 é o ano em que muitas delas conquistaram suas chances. Basta olhar para o Kubernetes; desde sua adoção na Cloud Computing Foundation (CNCF) em 2016, a VMWare , Azure , AWS e até Docker anunciaram suporte a sua infraestrutura.  

**Kubernetes cresce**

Em 2017, o projeto de código aberto demonstrou grandes avanços no sentido de se tornar uma tecnologia mais madura. O Kubernetes suporta classes de aplicativos cada vez mais complexas, permitindo, assim, a transição corporativa para a nuvem híbrida e para os microsserviços. Na DockerCon em Copenhague, a Docker anunciou que oferecerá suporte ao orquestrador de containers Kubernetes, e o Azure e a AWS entraram em acordo. O Kubernetes parece ter um futuro brilhante à frente como a plataforma de orquestração de fato.  

![História dos conteiners](https://raw.githubusercontent.com/linuxnocafe/linuxnocafe.github.io/master/img/container-history.jpg#responsive)
