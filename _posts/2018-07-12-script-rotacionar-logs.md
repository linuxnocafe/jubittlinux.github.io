---
title: Script para rotacionar logs
description: Renomeie e limpe seus logs periodicamente.
header: Script para rotacionar logs
---

Aqui vai um script que escrevi para rotacionar e apagar logs antigos. Esta é uma alternativa simples ao logrotate do Linux.
Não esqueça de dar permissão de execução no arquivo do script.
Como sugestão de automatização, a tarefa deve ser agendada no cron do sistema para execução periódica.

Segue o script com os cometários sobre o que faz cada uma das linhas:

```bash
### 1. Identifica o interpretador de comandos a ser usado.
    #!/bin/bash  

### 2. for file in /path/to/*.log  
    for file in /path/to/\*.log  

### 3. Inicia a ação sobre cada arquivo a ser movido.
    do  

### 4. Pega o arquivo pelo nome e renomeia adicionando a data no fim do nome.
    mv "${file}" "${file}.$(date +"%Y-%m-%d")" 

### 5. Encerra cada ação, passando para a próxima etapa quando todos os elementos forem lidos (renomeados).
    done;  

### 6. Procura por arquivos cuja data da última modificação seja maior que cinco dias 
### (exceto os arquivos com extensão .swp, por exemplo), 
### deletando assim que achar a ocorrência.
    find /path/to/ -type f -not -name "*.swp" -mtime +5 -delete
```
