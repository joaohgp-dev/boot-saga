# ⚠️-| Este documento ainda está sendo escrito |-⚠️

# Boot Saga

## Contexto:

Em 2024, mergulhei em uma intensa jornada acadêmica, explorando diversas linguagens e ferramentas. Com a diminuição da demanda em 2025, comecei a organizar meu ambiente digital e a explorar soluções open source e distribuições Linux.

## Motivações:

Estou em busca de flexibilidade e compatibilidade, além de novas oportunidades para aprofundar meu conhecimento em áreas que me apaixonam, como hardware e sistemas operacionais.

## Objetivo:

Meu objetivo é facilitar o processo de instalação e configuração para entusiastas, registrando de forma clara as etapas, fontes, materiais, ferramentas e repositórios.

### Windows 11:

Neste contexto, o Windows 11 atua como um sistema secundário complementar, agregando compatibilidade e ampliando as ferramentas disponíveis. Realizarei uma instalação mínima, limpa e personalizada, focando no essencial e priorizando alternativas open source.

#### Pré-instalação:

Primeiramente, é necessário baixar a imagem do Windows 11 e preparar um pendrive bootável. A imagem pode ser baixada diretamente do [site](https://www.microsoft.com/pt-br/software-download/windows11) da Microsoft. Para criar um pendrive bootável, recomendo o **Microsoft Media Tool** (encontrado no link anterior) e o [**Rufus**](https://rufus.ie/pt_BR/) para Windows. Para Linux, recomendo o [WoeUSB](https://github.com/WoeUSB/WoeUSB). Siga as instruções do programa escolhido.

> [!WARNING]  
> Para evitar conflitos, não utilize as opções avançadas do **Rufus**, visto que posteriormente usaremos outro método para personalizar a instalação.

Uma vez que o pendrive esteja pronto, precisamos criar o arquivo `unattend.xml`, que é um método oficial para fazer instalações personalizadas. Estarei utilizando o [Schneegans autounattend.xml generator](https://schneegans.de/windows/unattend-generator/?) para gerar esse arquivo.

> [!CAUTION]  
> Se você planeja instalar **ambos** os sistemas no **mesmo disco**, certas medidas de segurança são necessárias. Confira os seguintes tópicos da Arch Wiki para mais informações:
> * [Inicialização rápida e hibernação](https://wiki.archlinux.org/title/Dual_boot_with_Windows#Fast_Startup_and_hibernation)
> * [Hibernação e sistemas multiboot](https://wiki.archlinux.org/title/EFI_system_partition#Hibernation_and_multi_boot_systems)
>
> **SEM AS MEDIDAS CORRETAS, HÁ RISCO DE CORRUPÇÃO DO SISTEMA**.

# 👷‍♂️Este material ainda está sendo redigido! Fique atento as atualizações!
