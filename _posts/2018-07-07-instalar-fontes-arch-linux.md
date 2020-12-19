---
title: Instalando fontes básicas no Arch Linux
description: Aprenda a instalar fontes básicas no Arch Linux e melhore o visual do seu sistema.
header: Instalando fontes básicas no Arch Linux
---

Após instalar o Arch Linux considere instalar as seguintes fontes para melhorar o visual do seu sistema:

> $ sudo pacman -S ttf-dejavu ttf-liberation noto-fonts

Agora faça o reload do cache:

> $ fc-cache -vf

**ttf-dejavu:**

DejaVu fornece uma versão expandida da família de fontes Vera buscando por qualidade e ampla cobertura Unicode enquanto mantém o estilo original Vera. DejaVu atualmente trabalha em conformidade com os padrões europeus de multilingua (Multilingual European Standards -- MES-1 e MES-2) para cobertura Unicode. As fontes DejaVu fornecem variações serifa, sans e monoespaçadas. (Fonte: packages debian)

**ttf-liberation:**

Liberation é o nome coletivo de três famílias de fontes TrueType: Liberation Mono, Liberation Sans e Liberation Serif. Estas fontes são metricamente compatíveis com as fontes Courier New, Arial e Times New Roman, da Monotype Corporation, que são mais utilizadas no Windows e no Office. (Fonte: Wikipedia)

**noto-fonts:**

Noto Sans é uma família tipográfica desenvolvida pela Google com o objetivo de criar uma harmonização visual para todas as linguagens do mundo, através da cobertura de todos os caracteres codificados sob o padrão Unicode em todas as línguas. (Fonte: Wikipedia)
