---
title: Ingressando Debian e derivados no domínio Active Directory
description: Aprenda a ingressar uma estação Debian no domínio Active Directory.
header: Ingressando Debian e derivados no domínio Active Directory
---

Neste passo a passo mostraremos como ingressar um Linux Debian ou derivado no domínio Microsoft Active Directory através da linha de comando. Isto irá nos permitir autenticar via SSH no Linux com contas de usuários AD, provendo uma fonte central de autenticação.

Há inúmeros meios de se fazer isso, porém o jeito mais fácil que encontrei foi pela linha de comando.

Neste exemplo estou usando Debian 9 e Windows Server 2012 R2, contudo a versão de Windows não importa. Estamos assumindo que o nosso domínio já está preparado e configurado. Nós estamos simplesmente ingressando o Debian no domínio existente.

**Preparando o Debian**

Primeiro temos que instalar os pacotes abaixo:

> \# sudo apt-get install sssd realmd -y

O Debian deve estar apto a resolver o domínio Active Directory para que possa ingressar. Temos que verificar o servidor DNS em /etc/resolv.conf e confirmar se algum dos DNS’s é referente ao servidor que queremos ingressar.

**Ingressando Debian ao domínio Windows**

Para ingressar no domínio usaremos o comando “realm join”, como mostrado abaixo. É necessário especificar o nome do usuário do domínio que tem privilégios para ingressar a estação.

> \# realm join –user=administrator example.com  
Password for administrator:

Uma vez digitada a senha da conta solicitada, os arquivos /etc/sssd/sssd.conf e /etc/krb.conf serão configurados. Isso é muito bom porque editar estes arquivos manualmente pode ocasionar diversos tipos de problemas quando ingressando no domínio. O arquivo /etc/krb5.keytab também é criado durante o processo.

Podemos confirmar que ingressamos no domínio executando o comando “realm list”, como mostrado abaixo:

> \# realm list  
example.com  
type: kerberos  
realm-name: EXAMPLE.COM  
domain-name: example.com  
configured: kerberos-member  
server-software: active-directory  
client-software: sssd  
required-package: oddjob  
required-package: oddjob-mkhomedir  
required-package: sssd  
required-package: adcli  
required-package: samba-common-tools  
login-formats: %U@example.com  
login-policy: allow-realm-logins  

Uma vez concluído com sucesso, um objeto referente a estação será criado no Active Directory no container referente a “computers”.  
Agora que ingressamos no domínio podemos fazer alguns testes. Por padrão, se queremos especificar algum usuário temos que especificar também o nome do domínio. Por exemplo, com o comando “id” abaixo não obtemos nada para “administrator”, porém “administrator@example.com” mostra a UID da conta, bem como os grupos a que esta conta pertence no domínio Active Directory.  

> \# id administrator  
id: administrator: no such user

> \# id administrator@example.com  
uid=1829600500(administrator@example.com) gid=1829600513(domain users@example.com) groups=1829600513(domain users@example.com),1829600512(domain admins@example.com),1829600572(denied rodc password replication group@example.com),1829600519(enterprise admins@example.com),1829600518(schema admins@example.com),1829600520(group policy creator owners@example.com)  

Nós podemos modificar este comportamente modificando o arquivo /etc/sssd/sssd.conf, nas seguintes linhas:  

> use_fully_qualified_names = True  
fallback_homedir = /home/%u@%d  

Modifique de acordo com as linhas abaixo, que não requerem um FQDN (fully qualified domain name) a ser especificado. Isso também modifica o comportamente do diretório /home evitando que tenha um FQDN especificado depois do nome do usuário.  

> use_fully_qualified_names = False  
fallback_homedir = /home/%u  

Para aplicar as mudanças reinicie o sssd:  

> \# systemctl restart sssd  

Agora estaremos aptos a encontrar contas de usuários sem especificar o domínio. Ver exemplo abaixo:  

> \# id administrator  
uid=1829600500(administrator) gid=1829600513(domain users) groups=1829600513(domain users),1829600512(domain admins),1829600572(denied rodc password replication group),1829600520(group policy creator owners),1829600519(enterprise admins),1829600518(schema admins)  

Se ainda assim não funcionar você deve tentar limpar o cache do sssd.  

**Configurando pam para criar diretório na home automaticamente**

Em Debian e derivados a criação do diretório home do usuário não ocorre de forma automática após o primeiro login. Por isso devemos adicionar uma informação ao /etc/pam.d/common-session  

> $ echo "session required pam_mkhomedir.so skel=/etc/skel/ umask=0022" | sudo tee -a /etc/pam.d/common-session 

**Configurando SSH e acesso sudo**

Agora que ingressamos o Debian com sucesso no domínio, nós podemos conectar via SSH com qualquer usuário do domínio Active Directory com as configurações padrão:  

> \# ssh user1@localhost  
user1@localhost’s password:  
Creating home directory for user1.  

Podemos também restringir acesso SSH modificando o arquivo /etc/ssh/sshd_config. Não esqueça de reiniciar o serviço de SSH se fizer alguma modificação.  

Podemos também modificar as configurações de sudo para permitir que nossa conta do domínio tenha o desejado nível de acesso. Podemos criar um grupo no Active Directory chamado “sudoers”, colocar o usuário nele, e então permitir que esse grupo tenha acesso sudo criando o arquivo /etc/sudoers.d/ que permitirá o acesso root ser controlado pelo AD. Abaixo um exemplo, o grupo “sudoers” terá acesso root pleno.  

> \# cat /etc/sudoers.d/sudoers  
%sudoers ALL=(ALL) ALL  

Este grupo existe apenas no Active Directory. Nosso Linux pode ver que user1 é membro do Active Directory, e de acordo com a configuração acima permitir acesso root a este usuário.  

Com isso, nosso user1 estará apto a usar o comando sudo para executar comando com privilégios root.  

> [user1@debian ~]$ sudo su  
[sudo] password for user1:  
[root@debian user1]#  
[root@debian user1]# whoami  
root  

**Deixando o domínio**

Podemos fazer o processo inverso e remover a estação do domínio, simplesmente executando “realm leave” seguido do domínio, como mostrado abaixo:  

> \# realm leave example.com  

Isso irá deletar o objeto “computador” que foi criado no Active Directory, também removerá o arquivo keytab e voltará as configurações originais de sssd.conf e krb5.conf.  

