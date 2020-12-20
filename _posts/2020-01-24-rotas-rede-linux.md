---
title: Configure e entenda rotas no Linux
description: Entenda como configurar rotas de rede no Linux
header: Configure e entenda rotas no Linux
---

No esquema abaixo, temos duas redes individuais. São elas 192.168.1.0 e 192.168.3.0, ambas com máscara de rede 255.255.255.0.
Também temos uma máquina que serve de gateway com três placas de rede.
A primeira placa é conectada ao endereço de rede 192.168.1.0, a segunda placa é conectada a 192.168.3.0 e a terceira placa é conectada à internet.

![Rotas de rede no Linux](https://raw.githubusercontent.com/linuxnocafe/linuxnocafe.github.io/master/img/rotas.png#responsive)

A seguir tornaremos uma rede acessível a outra.

Para que a rede 192.168.3.0 seja acessível de 192.168.1.0 necessitamos adicionar uma rota de entrada de forma que possamos pingar 192.168.3.x de 192.168.1.x. O ponto em comum é o gateway.

Então, em cada máquina na rede 192.168.1.0 um gateway padrão será adicionado como mostrado abaixo:

```console
$ route add default gw 192.168.1.10
```

Agora quando 192.168.1.1 pingar 192.168.3.1 o tráfego sairá pelo gateway via 192.168.1.10.

No gateway adicionamos a seguinte entrada:

```console
$ route add -net 192.168.3.0 netmask 255.255.255.0 gw 192.168.3.10
```

Agora todos os pacotes endereçados a 192.168.3.x serão encaminhados através da interface 192.168.3.10, que então entrega os pacotes à máquina endereçada.

Para que a rede 192.168.1.0 seja acessível de 192.168.3.0 necessitamos adicionar uma rota em cada máquina, similarmente ao que foi feito acima.

```console
$ route add default gw 192.168.3.10
```

No gateway adicionamos a seguinte entrada:

```console
$ route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.10
```

Agora as máquina de 192.168.3.0 conseguem pingar as máquinas de 192.168.1.0 permitindo acesso à internet. No exemplo acima interconectamos duas redes diferentes.
Agora precisamos acessar a internet a partir dessas duas redes. Para isso, podemos adicionar uma rota padrão ao endereço 125.150.60.59 o qual se conecta à internet da seguinte forma:

```console
$ route add default gw 125.250.60.59
```

Assim, se uma das máquinas pertencentes a uma das redes acima (por exemplo  192.168.3.2) tentar pingar o google (8.8.8.8) ocorrerá a seguinte sequência:  

- Como o destino 8.8.8.8 não é nenhuma máquina da rede 192.168.3.0, então o tráfego será encaminhado ao gateway pela interface 192.168.3.10; 
- No gateway, então o destino é checado de novo. É verificado se o destino pertence à rede 192.168.1.0. Em nosso exemplo isso não ocorre;
- Então é verificado se o destino pertence à rede 192.168.2.0 e assim sucessivamente;
- Finalmente, chega-se a rota padrão para encaminhar os pacotes. Em nosso caso o endereço 125.250.60.59.

