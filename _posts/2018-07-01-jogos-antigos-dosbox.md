---
title: Emulando jogos antigos no DOSBox
description: Aprendar a rodar jogos antigos no Linux usando DOSBox.
header: Emulando jogos antigos no DOSBox
---

Minha infância foi marcada por jogos como Prince of Persia, Doom, Home Alone e Hocus Pocus.
Com a evolução do Windows muitos jogos e programas deixaram de funcionar neste S.O.. Eis que surge DOSBox para sanar este problema.
DOSBox é um emulador de computadores IBM PC com os antigos MS-DOS.
Muitas placas de vídeo e som antigas também são emuladas.
Adicionalmente o DOSBox existe para vários sistemas operativos.
Pode ser usado nos novos MS-Windows , Linux , FreeBSD e seus descendentes incluindo o Mac OS X.
DosBox também permite rodar programas feitos originalmente para DOS.
DosBox está presente no repositório de quase todas as distribuições.
Para instalá-lo no Ubuntu abra o terminal e digite:

> $ sudo apt-get install dosbox

Crie um diretório dentro da sua pasta de usuário. Lá serão armazenados os jogos. Criei uma chamada games.
Abra o programa DOSBox. No terminal deste digite:

> Z:\> mount c /home/usuario/games

Para entendimento:



> - mount -> será montado um diretório;
- c -> drive em que será montado o diretório;
- /home/usuario/jogos -> diretório que será montado no drive C.

Após isso digite:

> Z:\> c:

A partir daí basta utilizar os comandos do DOS para chamar os jogos e programas. 
