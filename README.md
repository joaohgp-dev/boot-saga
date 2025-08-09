<h3 align=center> ⚠️ Este documento ainda está sendo escrito ⚠️  </h2>

***
# Boot Saga

## Contexto:
Em 2024, mergulhei em uma intensa jornada acadêmica, explorando diversas linguagens e ferramentas. Com a diminuição da demanda em 2025, comecei a organizar meu ambiente digital e a explorar soluções open source e distribuições Linux.

## Motivações:
Estou em busca de flexibilidade e compatibilidade, além de novas oportunidades para aprofundar meu conhecimento em áreas que me apaixonam, como hardware e sistemas operacionais.

## Objetivo:
Meu objetivo é facilitar o processo de instalação e configuração para entusiastas, registrando de forma clara as etapas, fontes, materiais, ferramentas e repositórios.

> ### Sumário  
> [1. Pré instalação](#pr%C3%A9-instala%C3%A7%C3%A3o)  
> * [1.1. Pré instalação do Windows 11](#pr%C3%A9-instala%C3%A7%C3%A3o-do-windows-11)  
>   * [1.1.1. Preparando a mídia de instalação](#preparando-a-m%C3%ADdia-de-instala%C3%A7%C3%A3o)  
>   * [1.1.2. Escolhendo softwares do sistema](#escolhendo-softwares-do-sistema)  
>   * [1.1.3. Personalizando a instalação com unattend.xml](#personalizando-a-instala%C3%A7%C3%A3o-com-unattendxml)
>   * [1.1.4. Backup de arquivos](#backup-de-arquivos)
> 
> **🏗️ Tópicos em produção 🚧**
> 
> * [1.2. Pré instalação do Arch Linux]()  
>   * [1.2.1. Preparando a mídia de instalação]()
>   * [1.2.2. Planejando seu sistema operacional]()
>   * [1.2.3. |OPICIONAL| Criando um script de instalação]()
>
> [2. Instalação]()  
> * [2.1. Instalação do Windows 11]()
>   * [2.1.1. Inicializando pela mídia de instalação]()  
> * [2.2. Instalação do Arch Linux]()
>
> [3. Pós instalação]()  

## Pré instalação

### Pré instalação do Windows 11

Neste contexto, o Windows 11 atua como um sistema secundário complementar, agregando compatibilidade e ampliando as ferramentas disponíveis. Realizarei uma instalação mínima, limpa e personalizada, focando no essencial e priorizando alternativas open source.

#### Preparando a mídia de instalação

Primeiramente, é necessário baixar a imagem do Windows 11 e preparar um pendrive bootável. A imagem pode ser baixada diretamente do [site](https://www.microsoft.com/pt-br/software-download/windows11) da Microsoft. Para criar um pendrive bootável, recomendo o **Microsoft Media Tool** (encontrado no link anterior) e o [**Rufus**](https://rufus.ie/pt_BR/) para Windows. Para Linux, recomendo o [WoeUSB](https://github.com/WoeUSB/WoeUSB). Siga as instruções do programa escolhido.
> [!WARNING]  
> Para evitar conflitos, não utilize as opções avançadas do **Rufus**, visto que posteriormente usaremos outro método para personalizar a instalação.

#### Escolhendo softwares do sistema

A escolha dos softwares é uma decisão pessoal. Recomendo que você instale pelo menos um emulador de terminal, um navegador de internet e uma IDE. Abaixo, compartilho minha lista com softwares Open Source:

**Para programação:**
| Nome                | Função                                | Página oficial                                                                                             |  
| ------------------- | ------------------------------------- | ---------------------------------------------------------------------------------------------------------- |  
| Chocolatey          | Gerenciador de Pacotes                | [https://chocolatey.org/](https://chocolatey.org/)                                                         |  
| Windows Terminal    | Emulador de Terminal                  | [https://learn.microsoft.com/pt-br/windows/terminal/](https://learn.microsoft.com/pt-br/windows/terminal/) |  
| Zen Browser         | Navegador                             | [https://zen-browser.app/](https://zen-browser.app/)                                                       |  
| VSCodium            | Ambiente de desenvolvimento integrado | [https://vscodium.com/#intro](https://vscodium.com/#intro)                                                 |  
| Git                 | Versionador de software               | [https://git-scm.com/](https://git-scm.com/)                                                               |  

**Utilitários:**
| Nome                | Função                               | Página oficial                                                   |  
| ------------------- | ------------------------------------ | ---------------------------------------------------------------- |  
| 7-zip               | Gerenciador de arquivos compactados  | [https://www.7-zip.org/](https://www.7-zip.org/)                 |  
| Notepad++           | Editor de texto                      | [https://notepad-plus-plus.org/](https://notepad-plus-plus.org/) |  
| ShareX              | Ferramenta de captura                | [https://getsharex.com/](https://getsharex.com/)                 |  
| ImageGlass          | Reprodutor de imagem                 | [https://imageglass.org/](https://imageglass.org/)               |  
| VLC                 | Reprodutor de vídeo e áudio          | [https://www.videolan.org/](https://www.videolan.org/)           |  
| Localsend           | Compartilhar arquivos localmente     | [https://localsend.org/pt-BR](https://localsend.org/pt-BR)       |  

#### Personalizando a instalação com unattend.xml

> [!CAUTION]  
> Se você planeja instalar **ambos os sistemas no mesmo disco**, certas medidas de segurança são necessárias, algumas das quais é possível implementar no arquivo de resposta `unattend.xml`. Confira os seguintes tópicos da Arch Wiki para mais informações:
> * [A partição do sistema EFI criada pelo Windows Setup é muito pequena](https://wiki.archlinux.org/title/Dual_boot_with_Windows#The_EFI_system_partition_created_by_Windows_Setup_is_too_small)
> * [Inicialização rápida e hibernação](https://wiki.archlinux.org/title/Dual_boot_with_Windows#Fast_Startup_and_hibernation)
> * [Hibernação e sistemas multiboot](https://wiki.archlinux.org/title/EFI_system_partition#Hibernation_and_multi_boot_systems)
>
> **SEM AS MEDIDAS CORRETAS, HÁ RISCO DE CORRUPÇÃO DO SISTEMA**.

Uma vez que a mídia de instalação esteja pronta, precisamos criar um arquivo de resposta chamado `unattend.xml`, que é um método oficial para fazer instalações personalizadas, para mais informações consulte a documentação [aqui](https://learn.microsoft.com/pt-br/windows-hardware/manufacture/desktop/update-windows-settings-and-scripts-create-your-own-answer-file-sxs?view=windows-11). Estarei utilizando o [Schneegans autounattend.xml generator](https://schneegans.de/windows/unattend-generator/?) para gerar esse arquivo, recomendo fortemente que explore todas as opções, pesquise e se informe; Eu nunca mais toquei na interface do instalador porque todos os processos de instalação do Windows 11, configurações, debloat e instalação de programas é feito automaticamente na instalação.

Vou estar enfatizando algumas opções que podem ser úteis para previnir certos problemas, sinta se livre para fazer as próprias escolhas, desde que tenha se informado e tomado as devidas providências, não deve encontrar dificuldades.  
* **Configurações de setup**: Algumas opções importantes para cenários específicos.
* **Particionamento e formatação**: Recomento utilizar a opção de script para evitar retrabalho e problemas na instalação do Arch, recomendo a leitura do [tópico de instalação documentação da Arch Wiki](https://wiki.archlinux.org/title/Dual_boot_with_Windows#Installation). Abaixo vou deixar o meu script como exemplo, adapte para seu caso.
```cmd
SELECT DISK=0
CLEAN
CONVERT GPT
CREATE PARTITION EFI SIZE=580
FORMAT QUICK FS=FAT32 LABEL="System"
CREATE PARTITION MSR SIZE=16
CREATE PARTITION PRIMARY
SHRINK MINIMUM=301000
FORMAT QUICK FS=NTFS LABEL="Windows"
CREATE PARTITION PRIMARY SIZE=1000
FORMAT QUICK FS=NTFS LABEL="Recovery"
SET ID="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
GPT ATTRIBUTES=0x8000000000000001
```
* **Contas de usuário**: Caso você queira pular a nescessidade de vincular uma conta Microsoft pode configurar contas locais aqui.
* **Ajustes do sistema**: Muitas opções úteis se encontram nessa sessão, aproveite o máximo que puder.
* **Setup de WLAN/Wifi**: Caso precise de uma conexão com a internet, isso se aplica para ao próximo tópico. É nescessário configurar uma conexão aqui.
* **Utilize scripts personalizados**: Uma excelente opção para usuários mais avançados, você pode conferir alguns exemplos fornecidos pela própria ferramenta [aqui](https://schneegans.de/windows/unattend-generator/samples/). Caso não tenha experiência com PowerShell recomendo a leitura da documentação oficial [aqui](https://learn.microsoft.com/en-us/powershell/).

**| OPCIONAL | Automatizando a instalação de softwares via script**

Eu vou estar inserindo um script personalizado para instalar os softwares que listei, uma alternativa simples é utilizar um gerenciador de pacotes como o Chocolatey.
Ex usando chocolatey (Você pode conferir os softwares disponíveis [aqui](https://community.chocolatey.org/packages)):
```ps1
# Instala o gerenciador de pacotes Chocolatey
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iwr https://community.chocolatey.org/install.ps1 -UseBasicParsing | iex

# Usa o Chocolatey para instalar softwares via linha de comando.
choco install git.install --version 2.50.1 -y
choco install vlc --version 3.0.21 -y
choco install vscodium.install --version 1.102.35058 -y
choco install zen-browser --version 1.14.9-b --pre -y
```

Por último, recomendo fazer a leitura da página de uso da ferramenta [aqui](https://schneegans.de/windows/unattend-generator/usage/), revise as opções selecionadas, baixe o arquivo e siga as instruções de uso.

#### Backup de arquivos

> [!WARNING]
> Antes de iniciar a instalação certifique-se de fazer backup de arquivos, senhas e qualquer dado que esteja armazenado localmente, pois a instalação **apagará completamente qualquer dado salvo no computador**.

<h1>👷‍♂️Este material ainda está sendo redigido!<br /> Fique atento as atualizações!</h1>
