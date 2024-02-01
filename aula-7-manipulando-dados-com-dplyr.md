# Aula 7 - Manipulando dados com dplyr

![](<.gitbook/assets/0 (3).jpeg>)

Aula 7 - Manipulando dados com dplyr

### Objetivo <a href="#cdan1i8cqvyd" id="cdan1i8cqvyd"></a>

Aprender as operações básicas de tratamento de dados com o pacote dplyr, parte da coleção tidyverse.

### &#x20;<a href="#mka3bqiy47xj" id="mka3bqiy47xj"></a>

### Videoaula <a href="#id-1159jby6uze" id="id-1159jby6uze"></a>

Esse primeiro vídeo é um material introdutório que foi preparado para uma formação de alunos do projeto InfoSoc/UEL. Mas serve como uma visão geral sobre a importância do pacote {tidyverse}

[**Formato básico dos dados: Tidy data (Tabelas Retangulares) - Watch Video**](https://youtu.be/Pf0dtLivT2w)

[![](<.gitbook/assets/1 (3).gif>)](https://youtu.be/Pf0dtLivT2w)

Os dois vídeos seguintes tratam da base de dados dos Indicadores Sociais do Atlas Brasil IPEA,PNUD, FJP.

[**Importar dados do excel e ver sumário descritivo com {summarytools} - Watch Video**](https://youtu.be/Z1Yc88abUUM)

[![](<.gitbook/assets/2 (2).gif>)](https://youtu.be/Z1Yc88abUUM)

[**Tratamento de dados de indicadores sociais com {dplyr} - Watch Video**](https://youtu.be/c1XHCDQiyQI)

[![](<.gitbook/assets/3 (1).gif>)](https://youtu.be/c1XHCDQiyQI)

### Script utilizado nas duas vídeo aulas <a href="#doj0gfjamxzt" id="doj0gfjamxzt"></a>

\
Manipulando dados com dplyr

\# --------------------------

\# ---------

\# Primeiro vídeo\
\# -------------

\# 1. Importar os dados

library(tidyverse)

library(readxl)

munic\_tbl <- read\_excel("dados/Atlas 2013\_municipal, estadual e Brasil.xlsx",

sheet = "MUN 91-00-10")

View(munic\_tbl)

\# 2. Inspeção inicial para identificar valores mínimos, média e máximos

\# valores ausentes (na) e o formato da distribuição de frequência dos dados

@install.packages("summarytools")

library(summarytools)

view(dfSummary(munic\_tbl))

\# ---------

\# Segundo vídeo\
\# -------------

\# Criar uma variável com o município por

\# classe de tamanho de população

\# classe de tamanho da população Total IBGE

\#

\# Até 5.000

\# 5.001 a 20.000

\# 20.001 a 100.000

\# 100.001 a 500.000

\# Mais de 500.000

\# Classificação ONU para IDH e IDHM

\# Muito baixo: 0 a 0,499.

\# Baixo: 0,500 a 0,599.

\# Médio: 0,600 a 0,699.

\# Alto: 0,700 a 0,799.

\# Muito alto: 0,800 a 1.

\# Taxa de Urbanização

\#Script de tratamento dos dados

library(tidyverse)

munic\_tbl |>

select(ANO, UF, Codmun7, Município, IDHM, IDHM\_E, IDHM\_L, IDHM\_R, POP, pesotot, pesourb, pesoRUR) %>%

mutate(classe\_pop = case\_when(

(POP < 5001) \~ "1) Até 5.000",

(POP > 5000 & POP < 20001) \~ "2) 5.001 a 20.000",

(POP > 20000 & POP < 100001) \~ "3) 20.001 a 100.000",

(POP > 100000 & POP < 500001) \~ "4) 100.001 a 500.000",

(POP > 500000) \~ "5) Mais de 500.000",

)) |>

mutate(classe\_idhm = case\_when(

(IDHM < 0.5) \~ "Muito baixo",

(IDHM >= 0.5 & IDHM < 0.6) \~ "Baixo",

(IDHM >= 0.6 & IDHM < 0.7) \~ "Médio",

(IDHM >= 0.7 & IDHM < 0.8) \~ "Alto",

(IDHM >= 0.8) \~ "Muito Alto",

)) |>

mutate(taxa\_urbanizacao = (pesourb / pesotot) \* 100) |>

mutate(urbano\_rural = case\_when(

(taxa\_urbanizacao >= 50) \~ "Urbano",

(taxa\_urbanizacao < 50) \~ "Rural")) -> m2\_munic

m2\_munic |>

group\_by(ANO,urbano\_rural) |>

summarise(media = mean(IDHM),total\_de\_municipios = n())

m2\_munic |>

group\_by(ANO,classe\_pop) |>

summarise(media = mean(IDHM),total\_de\_municipios = n())

### O tratamento de dados <a href="#id-74ojtdtihan3" id="id-74ojtdtihan3"></a>

De todas as etapas que envolvem operações computacionais, certamente o tratamento de dados é a fase que mais consome tempo. Qualquer que seja a área, os dados raramente estarão prontos para a análise. Um bom tempo deverá ser dedicado para organizá-los de modo a que se possa extrair de uma coleção de informações algum tipo de conhecimento propriamente.

De modo geral, chama-se de tratamento de dados todas as etapas de planejamento (ou desenho) da estrutura de dados, a importação, limpeza, formatação e adequação, o tratamento dos casos faltantes, a ordenação, extração, combinação e manipulação das variáveis para análise.

Todas essas etapas podem ser feitas com o R somente ou em combinação com algum software especializado em gerenciamento de banco de dados.

### Um alicate para o tratamento de dados <a href="#id-52h94jczk7zm" id="id-52h94jczk7zm"></a>

O R básico possui um formato de linguagem compacto, para agilizar a digitação durante as consultas interativas. Mas, se esse tipo de notação favorece a rapidez na obtenção de respostas pelo console do computador, por outro lado, dificulta a documentação dos scripts mais longos, como normalmente se faz em pesquisa com dados sociais.

O código compacto também não é muito intuitivo. Várias funções e símbolos inseridos em uma única linha não é uma representação clara das etapas da análise. Pensando nisso, a ideia que deu origem ao pacote {dplyr}, segundo seu autor - Hadley Wickham\*, procurou aproximar as funções do R da estratégia mais comumente usada por quem faz análise de dados: "**dividir-calcular-combinar**".

Essa estratégia de dividir e conquistar, concentra os passos para análise de dados em três conjuntos básicos de operações:

1. seleção dos casos e variáveis a serem estudadas em um conjunto de dados
2. aplicação de funções para cálculo de resultado para cada grupo selecionado
3. combinação dos resultados para a análise propriamente do material

O pacote {dplyr} foi criado exatamente para realizar essas operações de forma direta, tanto para quem escreve, quanto para quem lê os scripts. O termo **dplyr** significa algo como d, uma referência a dados e “plyr”, que soa em inglês como plier (“pláier”), que quer dizer "alicate" em tradução para o português. Ou seja, um “alicate” para manipular os dados. Faz também alusão a um conjunto de funções muito usadas no R básico para esse mesmo tipo de procedimento: apply(), sapply(), lapplay(). As funções do pacote {dplyr} necessariamente não substituem as funções apply(), do R básico, mas permitem que as operações fundamentais de tratamento de dados com o R sejam feitas de forma bem mais intuitiva.

### As funções básicas no pacote dplyr e o pipe %>% <a href="#kynqdk3vys3v" id="kynqdk3vys3v"></a>

O pacote dplyr possui funções específicas para realização de cada uma das etapas da análise de dados.

#### Dividir <a href="#qjdf5o8agtgz" id="qjdf5o8agtgz"></a>

Para a escolha dos casos que serão analisados, utiliza-se a função **filter()**

A seleção e variáveis a serem estudadas é feita com a função **select()**

Pode-se reordenar os casos com a função **arrange()**

#### Calcular <a href="#l9oqwq65nlgn" id="l9oqwq65nlgn"></a>

Para criar novas variáveis calculadas a partir das variáveis existentes ou de condições relacionadas aos casos selecionados, existe a função **mutate()**

#### Combinar <a href="#id-7m5v053c0p57" id="id-7m5v053c0p57"></a>

Para apresentar resultados agregados, ou seja, para se extrair informações combinando a seleção de casos e variáveis, utiliza-se a função **summarize()**

O R básico possui uma função para apresentar um resumo dos dados, chamada de summary(). A função summarize() do pacote dplyr vai além, permite a construção de resultados conforme o objetivo de análise da pesquisa.

A função summarize() torna-se ainda mais versátil quando aplicada em conjunto com a função **group\_by()**, que permite agrupar os casos para análise comparativa.

Todas essas funções podem ser conectadas em sequência com o conector (pipe) **%>%** do pacote {magritr}, que é instalado juntamente com o pacote {dplyr} ou com {tidyverse}.

### Funções auxiliares <a href="#ht4lyffy1zlg" id="ht4lyffy1zlg"></a>

O pacote dplyr possui várias outras funções que auxiliam o tratamento de dados. Algumas que podemos destacar:

* rename() - permite renomear as variáveis
* na.omit() - excluir os casos com valores omissos (no R são identificados como na)
* count() - conta as categorias em uma variável
* add\_row() - adiciona casos (linhas) à sua base de dados
* add\_column() - adiciona variáveis (colunas) à sua base de dados
* Há várias outras funções que podem ser utilizadas, conforme se pode observar na folha de referência sobre as funções do pacote {dplyr}: [clique aqui para ver](https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf)

### Material adicional <a href="#i60pr17e679u" id="i60pr17e679u"></a>

Comparação entre Dplyr, R básico e SQL (Structured Query Language). O SQL que será utilizado no curso posterior sobre Construção de Indicadores Sociais com o R. Mas, para adiantar, segue uma visão inicial comparativa.

[**Selecionando casos e variáveis com o R básico, SQL e dplyr - Watch Video**](https://youtu.be/-JLsX8CBLxM)

[![](<.gitbook/assets/4 (1).gif>)](https://youtu.be/-JLsX8CBLxM)

### &#x20;<a href="#alcte38wd2ky" id="alcte38wd2ky"></a>

### Agora é com você <a href="#w6hnkko08ch5" id="w6hnkko08ch5"></a>

1. Reproduz o script apresentado na videoaula
2. Importe a planilha do Atlas Brasil com os indicadores municipais
3. Crie uma visão descritiva dos dados com o pacote {summarytools}
4. Utilize o pacote {dplyr}, que faz parte do pacote {tidyverse] e selecione as seguintes variáveis ANO, UF, Codmun7, Município, IDHM, IDHM\_E, IDHM\_L, IDHM\_R, POP, pesotot, pesourb, pesoRUR
5. Crie quatro novas variáveis na base sobre indicadores municipais:
   1. classe de tamanho de população, conforme definição do IBGE
   2. classe de IDHM, conforme definição do PNUD
   3. taxa de urbanização
   4. identificação de município rural ou urbano
6. Verifique se o IDHM médio varia entre 1991, 2000 e 2010 por identificação de município rural e urbano
7. Verifique se o IDHM médio varia entre 1991, 2000 e 2010 por classe de tamanho de população
8. Verifique se o IDHM Educação médio varia entre 1991, 2000 e 2010 por identificação de município rural e urbano
9. Verifique se o IDHM Educação médio varia entre 1991, 2000 e 2010 por classe de tamanho de população
10. Verifique se o IDHM Renda médio varia entre 1991, 2000 e 2010 por identificação de município rural e urbano
11. Verifique se o IDHM Renda médio varia entre 1991, 2000 e 2010 por classe de tamanho de população
12. Verifique se o IDHM Longevidade médio varia entre 1991, 2000 e 2010 por identificação de município rural e urbano
13. Verifique se o IDHM Longevidade médio varia entre 1991, 2000 e 2010 por classe de tamanho de população
14. Salve o seu script no diretório de projetos em uma pasta específica para os scripts.



### Comparação entre Dplyr e R básico <a href="#i50osj39ipu1" id="i50osj39ipu1"></a>

Nesse curso introdutório, vamos dar ênfase às funções do pacote {tidyverse}, em especial ao pacote de manipulação e tratamento de dados {dplyr}. Mas, para quem quiser se aprofundar, vamos mostrar as funções do Tidyverse e a correspondência com o R básico. Esse conteúdo não é necessário para fazer as atividades propostas.

Na tabela a seguir, há uma comparação das funções do dplyr e do R básico, sendo que df significa um data.frame (a base de dados que se está analisando, por exemplo o Atlas Brasil). As letras x, y, z referem-se a variáveis na base de dados.

Por exemplo, usando dplyr para ordenar os dados que estão em uma base de dados, denominada de atlas\_2013 (seria o df na tabela abaixo), pelo valor crescente da variável IDHM (seria o x na tabela abaixo), utiliza-se o seguinte código com o dplyr:

arrange(atlas\_2013, IDHM)

No R básico, a função equivalente seria:

atlas\_2013\[order(IDHM), ,drop = FALSE]

| **dplyr**                    | **R básico**                                                                                                                                              |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| arrange(df, x)               | df\[order(x), , drop = FALSE]                                                                                                                             |
| distinct(df, x)              | df\[!duplicated(x), , drop = FALSE], [unique()](https://rdrr.io/r/base/unique.html)                                                                       |
| filter(df, x)                | df\[which(x), , drop = FALSE], [subset()](https://rdrr.io/r/base/subset.html)                                                                             |
| mutate(df, z = x + y)        | df$z <- df$x + df$y, [transform()](https://rdrr.io/r/base/transform.html)                                                                                 |
| pull(df, 1)                  | df\[\[1]]                                                                                                                                                 |
| pull(df, x)                  | df$x                                                                                                                                                      |
| rename(df, y = x)            | names(df)\[names(df) == "x"] <- "y"                                                                                                                       |
| relocate(df, y)              | df\[union("y", names(df))]                                                                                                                                |
| select(df, x, y)             | df\[c("x", "y")], [subset()](https://rdrr.io/r/base/subset.html)                                                                                          |
| select(df, starts\_with("x") | df\[grepl(names(df), "^x")]                                                                                                                               |
| summarise(df, mean(x))       | mean(df$x), [tapply()](https://rdrr.io/r/base/tapply.html), [aggregate()](https://rdrr.io/r/stats/aggregate.html), [by()](https://rdrr.io/r/base/by.html) |
| slice(df, c(1, 2, 5))        | df\[c(1, 2, 5), , drop = FALSE]                                                                                                                           |

[Fonte: https://dplyr.tidyverse.org/articles/base.html](https://dplyr.tidyverse.org/articles/base.html)

### &#x20;<a href="#ph3thayxh8w1" id="ph3thayxh8w1"></a>

#### Sobre esse conteúdo <a href="#id-5n6cvmjko2cf" id="id-5n6cvmjko2cf"></a>

Este conteúdo digital é parte do curso online "Introdução aos Indicadores Sociais com o software R", de autoria do Prof. Ronaldo Baltar e da Prof.ª Cláudia Siqueira Baltar, como atividade do Projeto de extensão "Indicadores sociais como subsídio para o monitoramento e avaliação das ações dos municípios paranaenses em direção à Agenda 2030", vinculado ao ObPPP (Observatório de Populações e Políticas Públicas) e ao InfoSoc (Informática aplicada à Pesquisa Social), ambos projetos do Dept.º C. Soc. - CLCH/UEL.
