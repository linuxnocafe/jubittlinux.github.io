---
title: Controle de recursos com ulimit
description: Configure ulimit evitando, assim, que processos autorreplicantes travem o sistema.
header: Controle de recursos com ulimit
---

Ulimit é um comando que permite controlar recursos disponibilizados para o shell e para processos inicializados por este. 
É importante na prevenção de fork bomb; um tipo de processo malicioso e autorreplicante que satura o sistema e gera travamentos inesperados.

Programas ou usuários podem gerar processos autorreplicantes. Exemplo de fork no bash:

> :(){   
    :|: &   
};:   

Significado:  
Define a função dois pontos. Chama a si mesmo e canaliza para outra chamada que vai para segundo plano. Fim da função. Chama novamente.

Escrevendo os caracters sequencialmente, fica assim:
Obs: não digite isso no terminal.

> :(){ :|: & };: 

Para prevenir que o sistema trave, com o acúmulo indefinido de processos, é necessário limitar o número máximo a ser executado. Se for abaixo de 100 pode ser que alguns serviços tenham problemas para carregar dependendo da quantidade de programas usados simultaneamente. Depois de aplicada a limitação, o fork morrerá ao atingir o limite e os processos voltarão ao normal.

Com permissão plena acesse o arquivo /etc/security/limits.conf:

> \# nano /etc/security/limits.conf

E adicione as seguintes linhas no final (exemplo):

<pre>
*   soft    nproc   400  
*   hard    nproc   500 
</pre>

Salve [ctrl + O] e saia [ctrl + X]. Reinicie.

Se não quiser que a alteração afete o usuário administrador substitua o asterisco pelos nomes dos usuários a serem limitados, ou aplique aos grupos.
