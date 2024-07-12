# Como fazer um mapa animado com dados do IBGE ❤

![](image.png)
<button class="custom-button" onclick="window.location.href='https://medium.com/rladiesbh/como-fazer-um-mapa-animado-com-dados-do-ibge-feffd73c8b6b'">medium.com/rladiesbh</button>

Este repositório contém um projeto em R que utiliza dados do Instituto Brasileiro de Geografia e Estatística (IBGE) para criar mapas animados da população estimada dos municípios brasileiros entre 2001 e 2019.

## Introdução

Trabalhando ou não com dados, com certeza você já deve ter ouvido falar sobre o nosso [_Instituto Brasileiro de Geografia e Estatística (IBGE)_](https://www.ibge.gov.br/institucional/o-ibge.html). O IBGE é uma entidade da administração pública federal, vinculada ao Ministério da Economia, responsável por prover todas as informações estatísticas oficiais do nosso país. Através do seu trabalho analítico, o IBGE nos fornece informações espaço-temporais importantes, como dados sociodemográficos, de ocupação e de uso da terra, sobre a indústria, o meio ambiente e a agricultura, além de cartas e mapas com delimitações do território brasileiro.

Com o objetivo de homenagear a fundação dessa instituição, hoje comemora-se o **Dia da Criação do IBGE**. Foi em 06 de julho de 1934 que o _Decreto de Lei nº 24.609_ foi sancionado, iniciando o projeto que se tornou a instituição que conhecemos atualmente. Para que essa data tão importante não passe em branco, este projeto ensina como fazer um mapa animado utilizando dados fornecidos pelo IBGE.

![**População estimada para os municípios brasileiros entre 2001 e 2019 (fonte de dados: SIDRA - IBGE, 2020**).](https://github.com/mmfava/niver_IBGE/blob/master/pop_BR.gif?raw=true)

## Estrutura do Repositório

O repositório contém os seguintes arquivos e diretórios:

- `aniversario_ibge.qmd`: Documento Quarto que contém o código para gerar os mapas animados.
- `tab.csv`: Planilha com os dados de população estimada para os municípios brasileiros entre 2001 e 2019, hospedada no GitHub.
- `README.md`: Este arquivo de documentação que fornece uma visão geral do repositório e instruções de uso.

## Pacotes Necessários

Para executar este projeto, você precisará dos seguintes pacotes R:
* `readr`
* `sp`
* `sf`
* `brazilmaps`
* `cartography`
* `reshape2`
* `animation`
* `remotes`

## Instalação

### Passo a Passo

1. Clone o repositório:

    ```sh
    git clone https://github.com/mmfava/niver_IBGE.git
    cd niver_IBGE
    ```

2. Abra o projeto no RStudio.

3. Execute o código abaixo para instalar e carregar todos os pacotes necessários:

    ```r
    ## Instalação e carregamento dos pacotes
    required_packages <- c("readr", "sp", "sf", "brazilmaps", "cartography", "reshape2", "animation", "remotes")

    # Função para instalar pacotes que não estão instalados
    install_if_missing <- function(packages) {
        new_packages <- packages[!(packages %in% installed.packages()[, "Package"])]
        if (length(new_packages)) {
            install.packages(new_packages)
        }
    }

    # Chama a função para instalar os pacotes necessários
    install_if_missing(required_packages)

    # Carrega os pacotes
    lapply(required_packages, library, character.only = TRUE)

    # Instalação do pacote brazilmaps se não estiver disponível
    if (!requireNamespace("brazilmaps", quietly = TRUE)) {
        remotes::install_github("rpradosiqueira/brazilmaps")
        library(brazilmaps)
    }

    # Instalação do pacote animation se não estiver disponível
    if (!requireNamespace("animation", quietly = TRUE)) {
        # - SE problema com instalação do magick, 
        #   rodar no terminal: `sudo apt-get install libmagick++-dev`
        remotes::install_github("yihui/animation")
        library(animation)
    }
    ```

## Uso

1. Abra o arquivo `aniversario_ibge.qmd` no RStudio.

2. Execute o documento Quarto para gerar os mapas animados.

Com a finalização do laço, o gif é aberto e você poderá verificar o resultado. O arquivo ficará salvo no seu _working directory_ com o nome **“pop_brasil.gif”**. 

## Referências

* Pacote [readr](https://CRAN.R-project.org/package=readr): Hadley Wickham, Jim Hester e Romain Francois (2018). readr: Read Rectangular Text Data. R package version 1.3.1. https://CRAN.R-project.org/package=readr
* Pacote [brazilmaps](http://github.com/rpradosiqueira/brazilmaps): Renato Prado Siqueira (2020). brazilmaps: Brazilian Maps from Different Geographic Levels. R package version 0.1.0. http://github.com/rpradosiqueira/brazilmaps
* Pacote [sp](https://cran.r-project.org/web/packages/sp/index.html): Pebesma, E.J., R.S. Bivand, 2005. Classes and methods for spatial data in R. R News 5 (2), https://cran.r-project.org/doc/Rnews/.
* Pacote [sf](https://cran.r-project.org/web/packages/sf/index.html): Pebesma, E., 2018. Simple Features for R: Standardized Support for Spatial Vector Data. The R Journal 10 (1), 439-446, https://doi.org/10.32614/RJ-2018-009
* Pacote [cartography](https://cran.r-project.org/web/packages/cartography/index.html): Giraud, T. e Lambert, N. (2016). cartography: Create and Integrate Maps in your R Workflow. JOSS, 1(4). doi: 10.21105/joss.00054.
* Pacote [reshape2](https://cran.r-project.org/web/packages/reshape2/index.html): Hadley Wickham (2007). Reshaping Data with the reshape Package. Journal of Statistical Software, 21(12), 1-20. URL http://www.jstatsoft.org/v21/i12/.
* Pacote [animation](https://cran.r-project.org/web/packages/animation/index.html): Yihui Xie (2013). animation: An R Package for Creating Animations and Demonstrating Statistical Methods. Journal of Statistical Software, 53(1), 1-27. URL http://www.jstatsoft.org/v53/i01/.
* Pacote [remotes](https://cran.r-project.org/web/packages/remotes/index.html): Csárdi G, Hester J, Wickham H, Chang W, Morgan M, Tenenbaum D (2024). remotes: R Package Installation from Remote Repositories, Including 'GitHub'. R package version 2.5.0, https://github.com/r-lib/remotes#readme, https://remotes.r-lib.org.

---

Espero que você tenha gostado desse tutorial! Desejo ver suas gifs animadas em comemoração ao aniversário do nosso IBGE ♡

Um abraço forte! 

✿

M.


Qualquer dúvida é só me escrever em: _mariliabioufpr@gmail.com_. 

