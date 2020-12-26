---
title: Gerenciando senhas com GPG
description: Saiba como gerenciar senhas com o utilitário GPG
header: Gerenciando senhas com GPG
---

Existem muitas ferramentas disponíves no mercado para gerenciamento de senhas e credenciais. São os famosos cofres de senha. Se você usa Linux saiba que existe uma solução nativa no seu sistema operacinal. A ferramenta chama-se GPG (GnuPGP, versão livre da ferramenta PGP).
O GPG permite encriptar dados e também gerar assinaturas para sua comunicação online.
Aqui neste tutorial vamos ver duas maneiras como o GPG pode ser usado no Linux para proteger seus dados.

A primeira maneira é usando o GPG diretamente sobre os arquivos que você tenha criado como, por exemplo, um arquivo de texto contendo senhas.
A segunda maneira que explicaremos é o uso do GPG através do utilitário "Pass" da linha de comando. "Pass" é conhecido como "The Standard Unix Password Manager", isto é, o gerenciodaor padrão de senhas do Unix. Este é um programa que interage com o GPG para criptografar e armazenar suas crendenciais localmente.

Se você armazena suas senhas em blocos de nota sem qualquer restrição de acesso, saiba que esta é uma péssima prática em termos de segurança. 

Veja a seguir como usar o GPG para proteger suas informações.

**1. Primeiro método: encriptar arquivos pela linha de comando com o utilitário GPG.**

Criamos um arquivo chamado "cryptography" na /home do usuário. Este arquivo a príncipio é do tipo texto e pode ser aberto sem impedimento para exibição do conteúdo.
Para verificar o tipo de arquivo use o comando "file".

```console
$ cd ~/

$ echo "Olá! Este arquivo foi encriptado." > cryptography

$ file cryptography
cryptography: UTF-8 Unicode text
```

Abra seu terminal e execute as etapas a seguir:

```console
$ gpg -c cryptography
```

Uma janela irá abrir e você deve inserir uma chave (senha) para encriptar o arquivo. Em seguida será pedido para você digitar novamente a chave para confirmação.

Esta chave deve ser de preferência única, isto é, você não deve usá-la em outros lugares. Também é recomendado que seja do tipo "passphrase". 
Uma "passphrase" deve conter no mínimo 25 caracteres, misturar letras maiúsculas e minúsculas, números e caracteres especiais.
Não armazene esta chave em meios digitais. Tente decorar. E tome cuidado porque se esquecer a chave (senha) não será possível acessar novamente seu arquivo criptografado.

Com GPG também é possível escolher o tipo de criptografia que quer utilizar. Por padrão, o algoritmo atualmente usado é AES-256.
A versão 2.2.4 do GnuPG suporta os seguintes algoritmos de criptografia:

> **Criptografia**: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH, CAMELLIA128, CAMELLIA192, CAMELLIA256
**Hash**: SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224

Para mais informações digite no terminal:

```console
$ gpg --help
```

Para escolher outro tipo de algoritmo utilize a opção "-c --cipher-algo=BLOWFISH" onde BLOWFISH é o nome do algoritmo a ser usado. Exemplo:

```console
$ gpg -c --cipher-algo=BLOWFISH cryptography
```

E agora vamos acessar o arquivo encriptado. Existe a possibilidade de desencriptar o arquivo e gerar uma versão aberta dele que pode ficar no seu computador. Mas essa não é uma boa prática de segurança. O melhor é que este arquivo seja desencriptado somente para uma consulta. 

Consultando o arquivo encriptado e expurgando o conteúdo na sua tela no terminal: 

```console
$ gpg -d cryptography.gpg
gpg: dados criptografados com BLOWFISH
gpg: criptografado com 1 frase secreta
Olá! Este arquivo foi encriptado.
```

Observe que se você executar novamente o comando anterior não será necessário digitar a chave de novo. Isso não quer dizer que a criptografia parou de funcionar.
Acontece que este procedimento ficou registrado na sua atual sessão de usuário. Quando você reiniciar o computador e quiser consultar o arquivo "cryptography" será necessário digitar a senha de novo. Este é um ponto em desfavor do uso deste primeiro método que estou mostrando. Você pode encerrar o processo do agente do GPG como mostrarei a seguir. Para fazer com que a senha solicitada na próxima consulta do arquivo faz-se necessário encerrar o processo do agente do GPG.

Para encerrar o processo do agente GPG:

```console
$ gpgconf --kill gpg-agent
```

Após isso sua senha será solicitada novamente caso queira consultar o arquivo criptografado.

**2. Segundo método: gerenciar credenciais pelo utilitário "Pass".**

O utilitário "Pass" fornece dois fatores de proteção. O primeiro fator é que ele obrigada o usuário a criar sua assinatura digital antes de começar a guardar as credencias. O segundo fator de proteção é que você fica impedido de acessar seu arquivo criptografado se não tiver a assinatura digital. Mesmo que você saiba a senha, sem a presença da assinatura digital o "Pass" não funcionará. Então, é um trabalho que só funciona quando os dois fatores trabalham em conjunto: a assinatura digital e a senha correta. A assinatura digital é única e nunca se repete.
Se decidir usar o utilitário "Pass" você terá que fazer o backup dos arquivos das credenciais criptografadas e também da sua assinatura digital. Se perder a assinatura digital com a qual criptografou as credenciais é tchau e benção! Nunca mais vai conseguir acessar as credenciais que criptografou. 

> Importante: a assinatura digital é única e não se repete. Você não vai conseguir criar outra assinatura digital igual a que foi comprometida ou perdida, mesmo informando as mesmas características no processo de criação.

Instale o "Pass" a partir do seu repositório:

```console
$ sudo apt install pass
```

"Pass" armazena os dados na /home do usuário num diretório de nome ".password-store".
Para visualizar:

```console
$ cd ~/

$ ls -la | grep .password-store
drwx------  3 user	user	4096 dez 20 17:05 .password-store
```

Gerando a chave GPG (assinatura digital):

```bash
$ gpg --full-generate-key
gpg (GnuPG) 2.2.4; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

gpg: keybox '/home/user/.gnupg/pubring.kbx' created
Por favor selecione o tipo de chave desejado:
   (1) RSA e RSA (padrão)
   (2) DSA e Elgamal
   (3) DSA (apenas assinatura)
   (4) RSA (apenas assinar)
Sua opção? 1
RSA chaves podem ter o seu comprimento entre 1024 e 4096 bits.
Que tamanho de chave você quer? (3072) 2048
O tamanho de chave pedido é 2048 bits
Por favor especifique por quanto tempo a chave deve ser válida.
         0 = chave não expira
      <n>  = chave expira em n dias
      <n>w = chave expira em n semanas
      <n>m = chave expira em n meses
      <n>y = chave expira em n anos
A chave é valida por? (0) 0
A chave não expira nunca
Está correto (s/N)? s

GnuPG precisa construir uma ID de usuário para identificar sua chave.

Nome completo: Bola de Uranio
Endereço de correio eletrônico: boladeuranio@email.com
Comentário: Nenhum comentario
Você selecionou este identificador de usuário:
    "Bola de Uranio (Nenhum comentario) <boladeuranio@email.com>"

Muda (N)ome, (C)omentário, (E)ndereço ou (O)k/(S)air? O
Precisamos gerar muitos bytes aleatórios. É uma boa idéia realizar outra
atividade (digitar no teclado, mover o mouse, usar os discos) durante a
geração dos números primos; isso dá ao gerador de números aleatórios
uma chance melhor de conseguir entropia suficiente.
Precisamos gerar muitos bytes aleatórios. É uma boa idéia realizar outra
atividade (digitar no teclado, mover o mouse, usar os discos) durante a
geração dos números primos; isso dá ao gerador de números aleatórios
uma chance melhor de conseguir entropia suficiente.
gpg: /home/user/.gnupg/trustdb.gpg: banco de dados de confiabilidade criado
gpg: chave 4D48944FA82B0348 marcada como plenamente confiável
gpg: directory '/home/user/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/user/.gnupg/openpgp-revocs.d/209320EE191F65C169EA6E734D48944FA82B0348.rev'
chaves pública e privada criadas e assinadas.

pub   rsa2048 2020-12-20 [SC]
      209320EE191F65C169EA6E734D48944FA82B0348
uid                      Bola de Uranio (Nenhum comentario) <boladeuranio@email.com>
sub   rsa2048 2020-12-20 [E]
```


No fim do procedimento acima será aberta uma janela para inserir a senha que será usada para criar a assinatura digital. Você pode criar uma chave com dados fictícios para fazer uso local.

O próximo passo é iniciar o "Pass" pela primeira vez. Vai precisar do ID da chave que criou no procedimento acima. Caso esteja em dúvida e queira consultar quais os IDs disponíveis pode usar o comando abaixo:

```console
$ gpg --list-keys
gpg: checando o trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: profundidade: 0 válidas:   1 assinadas:   0 confiança: 0-, 0q, 0n, 0m, 0f, 1u
/home/user/.gnupg/pubring.kbx
-------------------------------
pub   rsa2048 2020-12-20 [SC]
      209320EE191F65C169EA6E734D48944FA82B0348
uid           [final] Bola de Uranio (Nenhum comentario) <boladeuranio@email.com>
sub   rsa2048 2020-12-20 [E]
```

Iniciando o "Pass" pela primeira vez:

```console
$ pass init 209320EE191F65C169EA6E734D48944FA82B0348
Password store initialized for 209320EE191F65C169EA6E734D48944FA82B0348
```

Agora está pronto para usar. E você pode inserir credenciais. 
Inserindo as credenciais:

```console
$ pass insert Negocios/my-user@email.com
mkdir: foi criado o diretório '/home/user/.password-store/Negocios'
Enter password for Negocios/my-user@email.com: 
Retype password for Negocios/my-user@email.com: 

$ pass insert Compras/my-user@email.com
mkdir: foi criado o diretório '/home/user/.password-store/Compras'
Enter password for Compras/my-user@email.com: 
Retype password for Compras/my-user@email.com: 
```

Para entender como isso é armazenado use o comando "pass". Você vai ver que as informações são armazenadas na forma de árvore. E o que fizemos acima foi armazenar uma credencial em cada categoria. 

```console
$ pass
Password Store
├── Compras
│   └── my-user@email.com
└── Negocios
    └── my-user@email.com
```

Agora vamos usar uma credencial. Após digitar o comando abaixo uma janela será aberta solictando a senha que você usou para criar sua assinatura digital. 

```console
$ pass -c Compras/my-user@email.com
Copied Compras/my-user@email.com to clipboard. Will clear in 45 seconds.
```

A senha da crencial armazenada foi transferida para a memória ram e estará disponível para uso por 45 segundos. Este é um recurso de proteção interessante, já que muitas formas de roubo de informação podem envolver o dump da memória ram.

Removendo credencial:

```console
$ pass rm Compras/my-user@email.com
Are you sure you would like to delete Compras/my-user@email.com? [y/N] y
removido '/home/user/.password-store/Compras/my-user@email.com.gpg'
```

Será necessário manter backup dos arquivos armazenados em no diretório oculto .password-store e também fazer o export da chave (assinatura digital) que fica armazenada em em outro diretório oculto chamado .gnupg.

**Backup das credenciais:**

```console
$ cd ~/

$ cp -R .password-store/ backup-password/

$ tar -zcvf backup-password.tar.gz backup-password
```

**Restaurar Backup:**

```console
$ cd ~/

$ tar -zxvf backup-password.tar.gz 

$ mv .password-store/ old_password-store/

$ mv backup-password/ .password-store/
```

**Backup das assinaturas:**

```console
$ cp -R .gnupg/ backup-gnupg/

$ tar -zcvf backup-gnupg.tar.gz /home/$USER/backup-gnupg

$ tar -zxvf backup-gnupg.tar.gz -C ~/.gnupg
```

**Restaurar assinaturas**

```console
$ cd ~/

$ tar -zxvf backup-gnupg.tar.gz 

$ mv .gnupg/ old_gnupg/

$ mv backup-gnupg/ .gnupg/
```

O que fizemos na última etapa acima foi exportar o diretório com todos os arquivos que estruturam as chaves criadas pelo usuário.
É possível também exportar e importar somente uma única chave GPG:

```console
$ cd ~/

$ gpg --list-secret-keys
/home/user/.gnupg/pubring.kbx
-------------------------------
sec   rsa2048 2020-12-20 [SC]
      209320EE191F65C169EA6E734D48944FA82B0348
uid           [final] Bola de Uranio (Nenhum comentario) <boladeuranio@email.com>
ssb   rsa2048 2020-12-20 [E]

$ gpg --export-secret-key 209320EE191F65C169EA6E734D48944FA82B0348 > my-key.asc

$ gpg --import my-key.asc
```

Se tentar visualizar o arquivo my-key.asc verá que o mesmo é ilegível. 
Agora guarde seus backups em local seguro. E não esqueça de fazer cópias periódicas de ambos.

> Recomendo fazer os dois tipos de backup da chave: faça o backup do diretório pelo "tar" e exporte também sua chave para formato .asc usando o comando "gpg".

"Pass" também é compatível com a GUI (Graphical User Interface) chamada "QtPass". "QtPass" é uma interface simples, intuitiva e muito fácil de usar.
Não achei uma maneira de exportar e importar backup usando QtPass. Então, o backup e a importação do mesmo terão que ser feitos pela maneira demonstrada acima.

Para instalar o QtPass:

```console
$ sudo apt install qtpass
```

Consulte o site da ferramenta "Pass" para mais informações. Não se esqueça também de usar o comando "man pass" para ver as opções de uso.
Também é possível implementar o "Pass" como servidor para gerenciar credenciais de muitos usuários. Você terá que criar um Git server para isso.
Com o "Pass" você também pode gerenciar credenciais por grupos. Isso é interessante caso decida usar a ferramenta em ambiente corporativo.

**Para saber mais:**

[https://gnupg.org/](https://gnupg.org/)
[https://www.passwordstore.org/](https://www.passwordstore.org/)
[https://wiki.archlinux.org/index.php/Pass](https://wiki.archlinux.org/index.php/Pass)
