---
title: Entrevista com Patrick Volkerding
description: Leia uma entrevista de Patrick Volkerding, criador do Slackware Linux, concedida no ano de 1994.
header: Entrevista com Patrick Volkerding
---

Abril 01, de 1994 by Phill Hugues. 

Na primeira edição do Linux Journal nós entrevistamos Linus Torvalds. Nesta edição nós entrevistaremos Patrick Volkerding, o criador do Slackware, uma das distribuições mais populares.

**Linux Journal:** Primeiro eu gostaria de saber um pouco sobre você. Quantos anos você tem?

**Pat:** Eu tenho 27 anos.

**Linux Journal:** O que você faz por trabalho, estudo, etc?

**Pat:** Por estudo, bem... Eu finalmente consegui meu bacharelado em ciência da computação da Moorhead State University na última primavera. Num plano de 8 anos, na verdade. Eu comecei engenharia da computação na Universidade de Boston em 85, cursei por 2 anos, e então tirei um ano fora antes de transferir para ciência da computação na MSU.

Eu recentemente consegui um emprego para uma empresa sediada em São Francisco que faz sistemas de arquivamentos médicos controlados por Linux. É um trabalho muito interessante.

**Linux Journal:** Estou procurando artigos sobre uso comercial de Linux. Eu ficaria realmente interessado num artigo sobre o que você está fazendo lá. O que você faz por diversão?

Eu faço todo tipo de coisa por diversão. Linux é meu grande projeto divertido neste momento – fico muito louco às vezes tentando manter-me com todo desenvolvimento em andamento; por agora, semana passada, a nova biblioteca C, GCC, e o kernel foram todos lançados com poucos dias de diferença. Felizmente, eu gosto de manter minha máquina atualizada. A julgar pelo correio que eu recebo quando as coisas ficam para trás, assim como todas as outras coisas.

**Linux Journal:** Hmmmm... Outras coisas?

**Pat:** Bem, eu gosto de preparar minha própria cerveja. Esse foi meu grande hobby até que o Linux começou a exigir mais do meu tempo. É um processo divertido. Minha parte favorita é acender meu queimador de 140K BTU e ferver assim por uma hora. O aroma que libera quando você joga o lúpulo para a ferver é magnífico! A fermentação caseira foi minha grande curtição antes de me deparar com o Linux.

Eu também adoro música, especialmente The Grateful Dead. Eu fui para, oh … 75 ou mais de seus shows. Os verões de 87 e 88 eu segui a banda por todo os EUA em meu conversível Firebird de 67. Eu também tenho muitos equipamentos de gravação portátil e gravo os shows sempre que posso. The Dead deixou seus fãs fazerem isso, o que é bastante original no mundo da música. Eu toco violão, também. Ainda estou esperando que Jerry [Garcia] me convide para o palco.

**Linux Journal:** Outra coisa estúpida? Eu fui para somente uns 30 ou 40 shows. Meu primeiro show foi em 1974 e eu tenho cerca de 100 fitas de show gravadas. Agora, na real. Quando você começou a trabalhar com computadores?

**Pat:** De volta em 1973, quando eu era apenas um garoto, eu fui em uma viagem de campo com a minha classe para o departamento de informática na Universidade Dakota do Norte. O quarto onde eles guardavam as máquinas me deixou totalmente maravilhado - muitas máquinas grandes zumbindo com luzes piscantes por todos os lados e filas de drivers grandes com bandejas de disco. Um dos operadores me mostrou como jogar Star Trek num decodificador. Foi vício instantâneo.

Naquela época, pensei, não havia jeito de ter um computador em casa. Eu nem mesmo pensava que tais coisas existissem, então comecei a me interessar por eletronica, que era mais acessível.

Eu construí portas lógicas de relés e coisas assim. Quando surgiram os primeiros computadores pessoais como o TRS-80, Apple II e o Atari 400/800, tornei-me uma peça fixa em muitas das lojas que os venderam. Eu não poderia pagar por um, mas os donos de loja me deixaram usar suas máquinas. Eu aprendi BASIC e escrevi pequenos programas de demonstração da loja para garantir que eu seria bem-vindo lá.

Eu tive um Apple II Plus com um modem 300 AppleCat por volta de 1980, quando foi uma máquina moderna. Eu usei o Apple como meu único computador até 1990. Eu até tinha um compilador C e um sistema operacional semelhante ao Unix para ele. No entanto, não era nada parecido com o Linux.

**Linux Journal:** Quando você começou a trabalhar com Linux?

**Pat:** Eu ouvi pela primeira vez sobre Linux no final de 1992 de um amigo chamado Wes em uma festa em Fargo, Dakota do Norte. Eu não o baixei imediatamente, mas quando eu precisava encontrar um intérprete LISP para um projeto na escola, me lembrei de ver as pessoas mencionarem que clisp roda no Linux. Então, eu acabei baixando uma das versões da distribuição SLS do Peter MacDonald.

**Linux Journal:** Descreva o que é Slackware?

**Pat:** Bem, eu acho que posso presumir que todos nós sabemos o que é Linux. Slackware consiste de um Linux básico (o kernel, bibliotecas compartilhadas, e utilitários básicos), e um número de pacotes de software opcionais como GNU C e compilador C++, rede e correio, e o sistema de janela X.

**Linux Journal:** Por que você decidiu fazer uma distribuição?

**Pat:** Essa é boa. Eu realmente nunca decidi fazer uma distribuição. O que aconteceu foi que meu professor de AI (artificial intelligence) queria que eu lhe mostrasse como instalar o Linux para que ele pudesse usá-lo em sua máquina em casa, e compartilhá-lo com alguns alunos de pós-graduação que também estavam fazendo um monte de trabalho no LISP. Então, entramos no laboratório de PC e instalamos a versão SLS do Linux.

Tendo lidado com o Linux por algumas semanas, eu montei uma pilha de notas descrevendo todas as pequenas coisas que precisavam ser corrigidas depois que a instalação principal estava completa. Depois de passar quase tanto tempo passando pela lista e reconfigurando o que precisava, como tínhamos colocado o software na máquina, o meu professor olhou para mim e disse: "Existe alguma maneira de corrigir os discos de instalação para que novas máquinas tenham essas correções imediatamente? ". Esse foi o início do projeto. Eu mudei partes dos scripts de instalação originais do SLS, corrigindo alguns bugs e adicionando um recurso que instalava pacotes importantes como as bibliotecas compartilhadas e a imagem do kernel automaticamente.

Também editei os arquivos de descrição nos discos de instalação para torná-los mais informativos. Mais importante ainda, eu passei pelos pacotes de software, corrigindo os problemas que encontrei. A maioria dos pacotes funcionou perfeitamente bem, mas alguns precisavam de ajuda. O correio, rede e o uucp software tinham um número de permissões de arquivo incorreto que o impediam de funcionar. Algumas aplicações despejaram memória sem explicação – para estas eu saí procurando código-fonte na rede. SLS só veio com o código-fonte para uma pequena parte da distribuição, mas muitas vezes havia, de qualquer maneira, novas versões, então eu peguei a fonte e os portei. Quando eu comecei na tarefa, eu acho que o kernel do Linux estava em torno de 0.98pl4 (alguém pode se lembrar que melhor do que eu ...), e eu coloquei melhores lançamentos SLS para o meu professor através da versão 0.99pl9. Por esta altura eu tinha ficado à frente do SLS em talvez metade dos pacotes na distribuição, e tinha feito alguma reconfiguração na maior parte da metade restante. Eu tinha feito alguma codificação eu mesmo para corrigir problemas de longa data como um bug que dizia que os usuários não tinham "Nunca logado" sempre que eles não estavam online. A diferença entre SLS e Slackware estava começando a ser mais do que apenas aparência.

Em maio, ou talvez até junho de 93, eu trouxe minha própria distribuição até as bibliotecas 4.4.1 C e o kernel do Linux 0.99pl11A. Isso trouxe melhorias significativas para a rede e realmente parecia estabilizar o sistema. Meus amigos do MSU achavam ótimo e me pediram para colocá-lo em FTP. Eu pensei que com certeza o SLS estaria lançando uma nova versão que incluísse essas coisas em breve, então eu segurei por algumas semanas. Durante este tempo eu vi um monte de pessoas perguntando na net quando haveria um lançamento que incluísse algumas dessas coisas novas, então eu fiz um post intitulado "Alguém quer um sistema SLS-como 0.99pl11?" Eu obtive uma resposta tremenda para o post.

Depois de falar com o sysadmin local na MSU, eu obtive permissão para abrir um servidor FTP anônimo em uma das máquinas - um antigo 3b2. Eu fiz um anúncio e assisti com horror como múltiplas conexões de FTP quebraram o 3b2 muitas e muitas vezes. Aqueles que obtiveram cópias do lançamento do Slackware 1.00 disseram algumas coisas boas sobre isso na net. Meus problemas de espaço de arquivo também não duraram muito. Algumas pessoas associadas ao Walnut Creek CDROM (e, ironicamente, membros do grupo central do 386BSD) me ofereceram um espaço de arquivo em ftp.cdrom.com.

**Linux Journal:** Por que você o chamou de Slackware?

**Pat:** Meu amigo J.R. "Bob" Dobbs sugeriu isso. ; ^) Embora eu tenha visto as pessoas dizerem que ele carrega conotações negativas, eu comecei a gostar do nome. Foi assim, comecei a chamá-lo de volta quando era realmente apenas uma versão hackeada do SLS e eu não tinha nenhuma intenção de colocá-lo para a obtenção pública. Quando eu finalmente coloquei para FTP, eu mantive o nome. Eu acho que eu o nomeei "Slackware" porque eu não queria que as pessoas tomassem tudo isso a sério no começo.

É uma grande responsabilidade a criação de software para, possivelmente, milhares de pessoas usarem (e encontrar bugs). Além disso, eu acho que soa melhor do que "Microsoft", não é?

**Linux Journal:** Algumas das pessoas aqui em Seattle chamam-no MicroSquish. :-) Eu admito que eu inicialmente evitei ir de SLS para Slackware porque eu não levei o nome a sério. Mas o feedback que eu ouvi na Internet apontou que eu deveria levá-lo a sério. O que você esperava que acontecesse com a distribuição?

**Pat:** Eu nunca planejei para que durasse tanto tempo quanto tem. Eu pensei que Peter MacDonald (da SLS) iria dar uma olhada no que eu estava fazendo e iria corrigir os problemas com SLS. Em vez disso, ele reivindicou direitos de distribuição nos scripts de instalação do Slackware, uma vez que eles foram derivados daqueles incluídos no SLS. Eu tinha permissão para manter o que eu tinha para FTP, mas disse a Peter que eu não faria outras mudanças no Slackware até que eu tivesse escrito novos scripts de instalação para substituir os que vieram do SLS. Eu escrevi os novos scripts, e depois de colocar tanto trabalho eu não ia desistir. Fiz tudo o que podia para tornar o Slackware a escolha ideal, integrando novos softwares e atualizações no lançamento tão rápido quanto elas saíam. É um monte de trabalho, e às vezes me pergunto quão longe posso ir.

**Linux Journal:** Que tipo de ajuda você recebeu?

**Pat:** Mais recentemente, Savio Lam escreveu o programa dialog usado para criar os menus de instalação de cores na versão mais recente do Slackware (1.1.2). Ian Kluft colocou o pacote smail junto para mim. A coleção newspak de Vince Shakan de scripts de configuração foi muito útil para compilar aplicativos como elm e Taylor UUCP. Louis LaBash acaba de contribuir com um kit para compilar uma versão do perl com IPC de trabalho. No início, Allen Gwinn me enviou o pacote lpd. Todos os usuários que me enviaram relatórios de bugs ajudaram muito, também.

Para além de alguns pacotes-chave das equipes de desenvolvimento em que confio, como o GNU GCC de H.J. Lu ou o pacote XFree86 2.0, compilei quase todo o software. Há ainda alguns bits restantes de SLS no pacote - você pode vê-los procurando arquivos com 1992 nas timestamps.

**Linux Journal:** Você tem alguma ideia do número de cópias do Slackware que são usadas hoje?

**Pat:** Milhares, mas seria difícil estimar um número exato. Eu não tenho ideia de quantos CDs foram impressos com o Slackware neles, mas eu posso pensar em quatro empresas que os produziram. Harald T. Alvestrand, que está tentando contar os usuários de Linux, postou esta estimativa: Eu não afirmo que esses números são de alguma forma imparciais. São apenas as 240 descrições de máquinas que chegaram ao contador.

Dos sete "desconhecidos", dois foram erros ortográficos de slackware. Há vieses no somatório também; Um que listou "slackware, sls" tem apenas o "slackware" como parte contada. Pelo menos, é um dado.

**Linux Journal:** O Slackware tem futuro?

**Pat:** Eu gostaria de pensar que sim. Eu realmente gosto de trabalhar com Linux, e tive uma ótima experiência fazendo um pacote completo como Slackware, disponível e fácil suficiente para iniciantes instalarem. Ian Murdock (da distribuição debian) e eu temos pensado em torno de uma fusão desde o outono passado. É possível que isso possa eventualmente acontecer.

Neste ponto, eu tenho alguns scripts agradáveis que criam pacotes, incluindo os scripts de instalação que criam os links simbólicos. Diferente de responder meu e-mail, não é tão difícil manter o Slackware atualizado. Se eu vou me preocupar em manter minha própria máquina atualizada, eu também poderia estar atualizando os pacotes no site FTP ao mesmo tempo.

**Linux Journal:** Você quer/espera algum benefício comercial do Slackware?

**Pat:** Eu não aceitei nenhum até agora. Seria bom ganhar dinheiro como resultado disso, mas não de vender o pacote real. Não estou interessado em entrar no negócio de CD-ROM por correspondência ou algo parecido, mas minha experiência com o Linux me ensinou muitas habilidades valiosas. Parece que o projeto me salvou de uma vida de COBOL. O que mais eu poderia pedir?

**Linux Journal:** Obrigado por isso. Eu acho que os leitores ficarão muito interessados nesta coluna de entrevista mensal e eu realmente quero entrevistar pessoas de todas as caminhadas Linux.

**Pat:** Claro! 

Fonte: [http://www.linuxjournal.com/article/2750](URL)

![Patrick Volkerding](https://raw.githubusercontent.com/linuxnocafe/linuxnocafe.github.io/master/img/patrick-volkerding.jpg)
