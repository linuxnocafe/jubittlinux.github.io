---
title: Implementando Logrotate
description: Aprenda a implementar logrotate para rotacionar seus logs e evitar acúmulos.
header: Implementando Logrotate
---

Em poucas palavras, logrotate irá renomear ou comprimir o log principal quando uma condição for encontrada, então o próximo evento será guardado num arquivo vazio.
Adicionalmente, logrotate removerá "velhos" arquivos de log e manterá os mais recentes. Claro, temos que decidir o que "velhos" significa e com que frequência queremos que logrotate limpe os logs para nós.

Para instalar logrotate use seu gerenciador de pacotes. No CentOS:

> \# yum install logrotate

O arquivo de configuração primária para o logrotate, que abrange os parametros padrões é /etc/logrotate.conf; configurações adicionais específicas são incluídas no diretório /etc/logrotate.d. Valores de configuração específicas sobreescrevem os parametros no arquivo de configuração primária.

Em resumo, a configuração do logrotate é feita em duas etapas separadas:  
- Editando-se /etc/logrotate.conf  
- Editando-se a configuração específica relacionada ao serviço que é armazenada no diretório /etc/logrotate.d/

O arquivo principal logrotate.conf contém uma configuração genérica. Segue um exemplo de configuração padrão do logrotate.conf:  

>      weekly  
     rotate 4  
     create  
     dateext  
     include /etc/logrotate.d  
     /var/log/wtmp {  
           monthly  
           create 0664 root utmp  
               minsize 1M  
           rotate 1  
      }


Agora vamos adicionar um novo arquivo de log a ser rotacionado. Vamos supor que tenhamos um arquivos de log chamado:

> /var/log/linux.log

situado no diretório /var/log e que necessita ser rotacionado diariamente. Primeiro, necessitamos criar um novo arquivo de configuração de logrotate para acomodar nosso novo log:

> \# vi /etc/logrotate.d/linux

Insira a seguinte configuração:

> /var/log/linux.log {  
    missingok  
    notifempty  
    compress  
    size 20k  
    daily  
    create 0600 root root  
}

A seguir uma breve explicação do arquivo criado:

- missingok - não mostra erro se o arquivo de log estiver faltando
- notifempty - não rotaciona o log se estiver vazio
- compress - versões antigas do arquivo de log são comprimidas com gzip
- size - o arquivo de log só é rotacionado se maior que 20k
- daily - rotação diária
- create - cria um novo arquivo de log com permissões 600 onde o proprietário e o grupo é o usuário root

Agora vamos simular a execução do logrotate (dry run):

> \# logrotate -d /etc/logrotate.d/linux

Para forçar a execução do logrotate mesmo quando as condições não são alcançadas:

> \# logrotate -vf /etc/logrotate.d/linux

Troubleshotting:

Se a rotação der a mensagem de erro "Skipping log because parent directory has insecure permission" defina na configuração qual usuário e grupo devem trabalhar na execução da rotação:

> \# vi /etc/logrotate.d/linux

Insira a seguinte configuração (exemplo genérico):

> file-to-be-rotated {  
    su user group  
    rotate 4  
}  
