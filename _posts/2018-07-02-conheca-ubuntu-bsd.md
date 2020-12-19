---
title: Conheça o UbuntuBSD
description: Conheça o UbuntuBSD, um Ubuntu com Kernel BSD.
header: Conheça o UbuntuBSD
---

O que você faz quando os desenvolvedores do seu sistema operacional optam por um design que você detesta? Se seu sistema tem o código base proprietário, você tem apenas poucas escolhas, e nenhuma delas são muito satisfatórias.

Você poderia aceitar. Você pode voltar a versão antiga, pelo menos até o suporte oficial desaparecer e você ser deixado a mercê dos chacais virtuais. Ou, você pode reclamar amargamente na esperança de alguém se preocupar. E se nenhuma abordagem funcionar pra você, você pode mudar de sistema, apesar de provavelmente ter que abandonar seus aplicativos e dados.

No mundo do software livre, você tem mais escolhas. Porque seu sistema é feito de componentes livres, reutilizáveis, você poderia juntar-se a um sistema similar que vai ao encontro das suas necessidades. E, você pode liberá-lo para que outros usuários possam se beneficiar também.

É exatamente o que aconteceu no caso do UbuntuBSD. Quando a Canonical decidiu adotar o systemd no Ubuntu, alguns usuários ficaram longe de serem agradados. Jon Boden foi um deles. Mas, graças a flexibilidade do software FOSS (free and open source software), ele foi capaz de construir sua própria versão do Ubuntu sem o systemd – e sua solução foi bastante intrigante.

Muitos derivados do Ubuntu existem no mundo, até agora, todos eles tem uma coisa em comum: são sistemas operacionais Linux. Com UbuntuBSD, Jon quebrou o modelo usando o FreeBSD como base.

FreeBSD desfrutou de um maior seguimento no mundo do servidor do que no desktop. Uma razão para isso é que a instalação padrão não inclui um ambiente para desktop, apesar da maioria dos ambientes de Linux mais populares poderem ser instalados no BSD.

A nova distribuição UbuntuBSD oferece um instalador simples baseado em texto. Tem uma opção de instalar o ambiente de desktop XFCE, junto com a maioria dos pacotes que você acharia no Xubuntu.

Usuários que esperam uma experiência idêntica ao Ubuntu deveriam rever suas expectativas antes de mudarem. Embora a nova distro cubra muito do mesmo aspecto, há muitas diferenças importantes.

Embora BSD e Linux sejam muito similares, eles não são idênticos. Os dois projetos tem histórias muito diferentes e incluem características diferentes. Eles tem um ancestral comum no Unix mas ambos evoluíram em direções diferentes. Estas diferenças significam que o BSD não é um substituto perfeito do kernel Linux.

BSD inclui uma camada de compatibilidade que permite rodar a maioria dos nativos binários do Linux, mas há exceções. Aplicações que se baseiam em chamada de baixo nível no Linux irão quebrar no BSD. E, há aplicações de alto nível que dependem do systemd em si. Isto inclui o desktop Gnome e outros apps populares.

Dito isto, a maioria dos usuários-alvo para a nova distribuição são administradores experientes que estão bem cientes dessas dependências. Na verdade, é a rede emaranhada de interdependências que o systemd adicionou ao ecossistema Linux que motivou este projeto. Para muitos, esta é razão suficiente para se afastar da moda corrente que é o Ubuntu.

O Systemd teve uma rápida aceitação desde que foi lançado no Red Hat Linux. O objetivo do seu design era fornecer uma base unificada para todas as distribuições de Linux, sendo adotado por muitos dos grandes usuários. Mas embora a expansão do systemd tenha sido prodigiosa, também foi controversa.

Antes de adotar o systemd, a Canonical estava entre os seus críticos mais abertos. Mark Shuttleworth certa vez o chamou de "enormemente invasivo e dificilmente justificado".

Naquela época, o Ubuntu utilizava o daemon init Upstart, desenvolvido sob a liderança da Canonical. Mas, quando o Debian mudou para o systemd, o Ubuntu seguiu o mesmo caminho.

Embora existam muitos argumentos contra o systemd, as objeções mais comuns são as de que ele viola os princípios básicos da filosofia UNIX. O conceito essencial é que cada peça de software deve se concentrar em fazer uma coisa bem feita. Isso implica usar programas mais simples para construir uma ampla gama de sistemas diferentes. No entanto, o systemd assume uma série de responsabilidades e as fecha em um único processo. Por um lado, isso leva a um sistema mais fácil de configurar, mas alguns argumentam que se colocam todos os recursos em um único lugar.

Independentemente da sua posição no debate, projetos como a distribuição UbuntuBSD oferecem uma ampla gama de opções para a comunidade FOSS (free and open source software). E, há casos onde o kernel BSD proverá melhor performance que o Linux.

Fonte: [http://www.linuxjournal.com/content/ubuntubsd](URL)
