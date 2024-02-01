# Aula 5 - Criando projetos no RStudio

![](<.gitbook/assets/0 (6).jpeg>)

Aula 5 - Scripts com o RStudio

### Objetivo <a href="#cdan1i8cqvyd" id="cdan1i8cqvyd"></a>

Aprender a criar e organizar projetos no RStudio. Estabelecer um fluxo de trabalho para a análise de dados.

### Videoaulas <a href="#mka3bqiy47xj" id="mka3bqiy47xj"></a>

[**Criar projetos com o RStudio - Watch Video**](https://youtu.be/zGrI77\_97RQ)

[![](<.gitbook/assets/1 (6).gif>)](https://youtu.be/zGrI77\_97RQ)

### Organizando tudo em um projeto <a href="#hpsq7w2jzcao" id="hpsq7w2jzcao"></a>

Normalmente o fluxo de trabalho com R envolve a depuração e seleção dos dados, a aplicação dos modelos e a análise dos resultados, que podem ser em formato de gráficos, tabelas ou um conjunto de valores correspondentes aos parâmetros verificados. Essa sequência de procedimentos é realizada repetidamente, com ajustes, correções ou mudança de alguns valores para testar as possibilidades do estudo.

Ao contrário do que muitos imaginam, analisar dados é uma tarefa reflexiva. Dificilmente os resultados conclusivos surgem em uma única análise. Por isso, quem se propõe a fazer um estudo sério, deve buscar explorar caminhos e se questionar sobre os resultados antes da disseminação final. Na grande maioria das vezes, uma pesquisa é repleta de idas e vindas, com várias revisões dos modelos adotados e diferentes visualizações dos resultados, até que as conclusões se tornem sólidas o suficiente para a divulgação.

### Criar e gerenciar projetos <a href="#v16chz50yncu" id="v16chz50yncu"></a>

Para organizar todo o material e o fluxo da pesquisa, o RStudio apresenta um recurso chamado de "projetos''. Essa ferramenta foi pensada para auxiliar os desenvolvedores na criação de bibliotecas em R. Mas é simples e bastante útil para qualquer tipo de projeto.

Quando se cria um novo projeto, conforme a Figura 1, o RStudio cria um arquivo com a extensão .Rproj o coloca no diretório raiz do projeto. Esse arquivo contém as informações e preferências do projeto.

Fig. 1 - Criar um novo projeto no RStudio

![](<.gitbook/assets/2 (1).png>)

Um novo projeto começa com uma nova seção do R. O projeto pode ser vinculado ao [GitHub ](https://beatrizmilz.github.io/RLadies-Git-RStudio-2019/#1)ou outro sistema de controle de versões para acompanhamento das alterações realizadas nos códigos, recurso útil principalmente para trabalhos em grupo.

Tendo sido criado um novo projeto, é recomendável definir uma estrutura no diretório de arquivos. Sem uma clara organização desde o início, em pouco tempo as pastas se tornam um amontoado de documentos irrecuperáveis. Achar um arquivo específico em um diretório desorganizado é uma tarefa quase impossível. Ter uma informação que não se pode recuperar é o mesmo que não a ter.

Qualquer critério de organização será sempre uma escolha que melhor se adeque à rotina de quem está fazendo o trabalho. Mas, não pode ser algo tão pessoal que se torne um empecilho para que outros possam ter acesso ao conteúdo armazenado. Manter uma estrutura lógica que possa ser intuitivamente compreensível é importante até porque a organização do diretório de arquivos ajuda a reprodutibilidade da pesquisa.

### Os passos da análise de dados <a href="#vogil2wos5xo" id="vogil2wos5xo"></a>

Normalmente, o fluxo de trabalho com R envolve a depuração e seleção dos dados, a aplicação dos modelos e a análise dos resultados, que podem ser em formato de gráficos, tabelas ou um conjunto de valores correspondentes aos parâmetros verificados. Essa sequência de procedimentos é realizada repetidamente, com ajustes, correções ou mudança de alguns valores para testar as possibilidades do estudo.

Analisar dados é uma tarefa reflexiva. Dificilmente os resultados conclusivos surgem na primeira visualização dos dados. Por isso, quem se propõe a fazer um estudo sério, deve buscar explorar caminhos e se questionar sobre os resultados antes da disseminação final. Na grande maioria das vezes, uma pesquisa é repleta de idas e vindas, com várias revisões dos modelos adotados e diferentes visualizações dos resultados, até que as conclusões se tornem sólidas o suficiente para a divulgação.

Um processo de análise de dados quase sempre segue as seguintes etapas:

1. fazer as configurações necessárias no software, com a inicialização e ajuste do ambiente que irá rodar os dados;
2. abrir e selecionar os dados, o que normalmente requer a importação, conversão, correção, tratamento, agrupamento, seleção de variáveis e filtragem de casos;
3. proceder uma análise para responder alguma pergunta ou fazer alguma predição;
4. disseminar os resultados e dispor o material analisado para replicação, comparação e aprofundamento dos estudos.

Por isso, manter todos os arquivos gerados durante uma pesquisa em um projeto é importante para não haver dispersão e confusão. Um projeto ajuda a colaboração e reprodutibilidade dos resultados, na medida em que todo material produzido estará disposto de forma clara e organizada. Apesar de ser um instrumento indispensável para o andamento de uma pesquisa, um projeto no RStudio é apenas um diretório padronizado para o armazenamento dos arquivos de ambiente, histórico, gráficos e scripts gerados durante o trabalho. A organização das pastas e do material em cada pasta cabe a quem está usando o RStudio.

### **Agora é com você** <a href="#id-42rtjqg2igtn" id="id-42rtjqg2igtn"></a>

1. Abra o RStudio
2. Crie um projeto em um diretório de sua preferência
3. Nomeie o projeto conforme sua preferência
4. Com o projeto criado, crie um novo script
5. Nomeie o script conforme sua preferência e salve-o em sua pasta do projeto
6. No script reproduza os passos do vídeo da aula 5, para importar os dados do Atlas referentes aos Estados para uma pasta de dados específica em seu projeto
7. Depois, faça um gráfico de dispersão com o addin esquisse, correlacionado o IDHM\_L, IDHM\_R, com o IDHM como legenda de cor e a população dos Estados como o tamanho dos pontos, conforme mostrado no vídeo
8. Importe o código do gráfico (ggplot2) para o script.
9. Não se esqueça de inserir comentários em seu script, preferencialmente separando as etapas da pesquisa
10. Execute o script linha a linha, posicionando o cursor na primeira linha, com **Ctrl+Enter**, para verificar se não há erros. Se houver, procure identificá-los e corrigi-los na linha especificada do script (se problema persistir ou se não estiver claro o que você está fazendo, mande uma mensagem pelo Google Sala de Aula)
11. Salve a imagem gerada em uma pasta criada especificamente para gráficos dentro do seu projeto
12. Feche o projeto, salvando a área de ambiente e todas as variáveis criadas.
13. Após terminar, devolva a atividade (não é necessário enviar nenhum arquivo, apenas registrar a devolução para que fique assinalado que você concluiu essa etapa). Depois envie um comentário para informar se tudo deu certo. Comente o que você achou do fluxo de trabalho com o RStudio.

Se você não conseguir… tiver problemas com o esquisse…

[https://youtu.be/F96tMqKcXxE](https://youtu.be/F96tMqKcXxE)

[![](<.gitbook/assets/3 (1).png>)](https://youtu.be/F96tMqKcXxE)

#### Sobre esse conteúdo <a href="#id-5n6cvmjko2cf" id="id-5n6cvmjko2cf"></a>

Este conteúdo digital é parte do curso online "Introdução aos Indicadores Sociais com o software R", de autoria do Prof. Ronaldo Baltar e da Prof.ª Cláudia Siqueira Baltar, como atividade do Projeto de extensão "Indicadores sociais como subsídio para o monitoramento e avaliação das ações dos municípios paranaenses em direção à Agenda 2030", vinculado ao ObPPP (Observatório de Populações e Políticas Públicas) e ao InfoSoc (Informática aplicada à Pesquisa Social), ambos projetos do Dept.º C. Soc. - CLCH/UEL.
