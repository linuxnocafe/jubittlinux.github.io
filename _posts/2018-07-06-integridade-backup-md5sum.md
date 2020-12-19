---
title: Validando a integridade de um backup com md5sum
description: Verifique a integridade de um backup por meio de script usando md5sum.
header: Validando a integridade de um backup com md5sum
---

Em informática, cópia de segurança (em inglês: backup) é a cópia de dados de um dispositivo de armazenamento a outro para que possam ser restaurados em caso da perda dos dados originais, o que pode envolver apagamentos acidentais ou corrupção de dados. (Wikipedia)

Vamos criar um script para validar backup e verificar a integridade dos dados. O procedimento será feito a partir do programa md5sum nativo das distribuições Linux.
md5sum é um programa de computador de código aberto que permite verificar a integridade de arquivos transmitidos por rede, como a internet, garantindo que os dados não tenham sidos corrompidos durante a transferência. Está disponível para Windows e é instalado por padrão na maioria dos sistemas UNIX, GNU/Linux e Mac OS.

O md5sum é capaz de calcular uma soma de verificação a partir do arquivo, criando uma "impressão digital" na forma de uma número hexadecimal usando o algorítimo MD5. (Wikipedia)

O MD5 é um hash de 32 caracteres, com 16 caracteres diferentes (abcdef0123456789) isso dá: 1208925819614629174706176 combinações. (Site Viva o Linux)

A ideia do script é: a partir de um conjunto de hashs md5sum gravadas num arquivo convertem-se estas hashs em uma única hash a ser gravada numa variável. O processo é feito na origem e no destino com a finalidade de se comparar as hashs finais e saber o estado do backup.

Para acessar o script que criamos [clique aqui](https://1drv.ms/t/s!AkSYEMI3hdChgVBjASEfNgyYcrV6). 
