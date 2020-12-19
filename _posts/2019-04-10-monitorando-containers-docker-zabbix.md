---
title: Monitorando containers Docker no Zabbix
description: Monitore containers Docker no Zabbix com Dockbix
header: Monitorando containers Docker no Zabbix
---


Dockbix é uma solução para ser implementada junto a ferramenta Zabbix de monitoramento. Dockbix permite monitorar containers em Docker e gerar gráficos e métricas a partir disso. Trata-se de um container que monitora outros containers.  

![Containers monitorados pelo Dockbix container](https://raw.githubusercontent.com/linuxnocafe/linuxnocafe.github.io/master/img/dockbix.png)

Dockbix está presente no Dockerhub em duas versões: a gratuita com algumas limitações e a paga, sendo esta última mais completa.

Aqui vai uma lista de prós e contras da versão Freeware (limitada):

**Prós:**  
  - Integração com vários templates do Zabbix;  
  - Métricas e gráficos por container;  
  - Integração com Grafana;  
  - Consome pouquíssimo recurso da máquina.  

**Contras:**  
  - Solução Freeware com algumas limitações;  
  - Não permite atachar ao container para executar um shell;  
  - Não suporta parâmetro restart always, o que torna a ferramenta manual em sua implementação e manutenção.

A implementação deve ser feita conforme a orientação disponibilizada no dockerhub. Segue o link:
[Dockbix](https://hub.docker.com/r/monitoringartist/dockbix-agent-xxl-limited/)

Como sugestão corretiva a uma limitação da versão Freeware disponibilizamos um script para que você possa automatizar a execução do container do Dockbix. Trata-se de um script a ser inserido na crontab de seu sistema Linux para que periodicamente este possa verificar se o Dockbix está de pé. Caso não esteja de pé o mesmo será iniciado.  

        #!/bin/bash
	CONTAINER=dockbix-agent-xxl
	RUNNING=$(docker inspect --format="{{ .State.Running }}" $CONTAINER)

        if [ "$RUNNING" == true ]; then
                echo "##############################################################"
                echo "$CONTAINER is running!!!"
                echo "##############################################################"
                exit 0
        else
                echo "##############################################################"
                echo "$CONTAINER is not running. Starting container now!"
                echo "##############################################################"
                docker stop dockbix-agent-xxl
                docker rm dockbix-agent-xxl
	            docker run --name=dockbix-agent-xxl -p 10050:10050  
	            --privileged -v /:/rootfs -v /var/run:/var/run  
	            -e "ZA_Server=IP_ADD" -e "ZA_ServerActive=IP_ADD"  
	            -d monitoringartist/dockbix-agent-xxl-limited:latest
                exit 0
        fi	

O script acima apresenta o seguinte modo de ação:  
Verificar se o container de nome "dockbix-agent-xxl" está em execução. Isto é feito através da inspeção do estado do container. O comando de inspeção "docker inspect" é armazenado numa variável chamada RUNNING que será testada logo a frente. Caso a varirável RUNNING apresente o conteúdo verdadeiro (true), então consta que o container do Dockbix está de pé. Caso contrário segue-se para o próximo estágio da instrução que é quando o Dockbix é iniciado.  
  
  
