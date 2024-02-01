# Aula 4 - Scripts com o RStudio

![](<.gitbook/assets/0 (7).jpeg>)

Aula 4 - Scripts com o RStudio

### Objetivo <a href="#cdan1i8cqvyd" id="cdan1i8cqvyd"></a>

Aprender a criar e executar um script no RStudio. Começar a conhecer os operadores básicos e a estrutura da linguagem R.

### Videoaulas <a href="#mka3bqiy47xj" id="mka3bqiy47xj"></a>

[Scripts com o RStudio - Watch Video](https://youtu.be/w92uETEvvbY)

[![](<.gitbook/assets/1 (7).gif>)](https://youtu.be/w92uETEvvbY)

### Criando um _script_ com o RStudio <a href="#id-6bljzuh224sw" id="id-6bljzuh224sw"></a>

Um script é um texto com uma sequência de comandos que são executados pelo interpretador do R. Para passar instruções curtas para o R, com duas ou três linhas, pode-se digitar diretamente no terminal interativo do R. Para códigos mais complexos, com várias linhas, o ideal é que seja feito em um arquivo de texto para ser depois executado no R. Esse arquivo de texto, vamos chamar de script.

Um script no RStudio é um arquivo de texto simples, que se usa para executar os comandos na sequência estabelecida pelo autor. O RStudio possui também várias opções de criação de textos, inclusive para outras linguagens de programação, como C++, Phyton, Stan, SQL e também arquivos textos simples, páginas HTML entre outros.

O R e o RStudio salvam e reconhecem automaticamente arquivos de script quando um documento de texto possui a extensão .R

### Uma visão geral do RStudio <a href="#id-4k34we5m3inh" id="id-4k34we5m3inh"></a>

O editor de código do RStudio possui várias vantagens, por exemplo, faz a complementação do código ao se digitar e faz o realce em cores diferentes dos elementos do código em R, como comandos, variáveis, números, comentários.

#### &#x20;Criar um script no RStudio <a href="#g7y8n24cju4" id="g7y8n24cju4"></a>

Um novo script no RStudio pode ser iniciado clicando-se no menu:

\[ File ] → \[ New File ] → \[ New R script ]

Ou pode também ser criado pressionando-se simultaneamente a combinação de teclas ctrl + Shift + N.

Para se executar um script linha a linha (o ideal quando se está iniciando um código e se quer depurar cada passo das instruções), posiciona-se o cursor na linha que se quer começar a executar e clica-se no botão **RUN**, no menu do lado direito superior da janela do editor de scripts do RStudio. Pode-se também executar esse comando clicando-se nas teclas **Control+Enter**. Para ajudar a memorizar esse comando, quando se está editando um texto e clica-se em Enter, abre-se cria-se uma nova linha. **Control+Enter** executa-se uma linha.

Para rodar todo o script de uma vez, ou seja, do início ao fim do texto de script, usa-se a combinação de teclas **Control+Alt+R** (para ajudar você a se lembrar, em inglês “executar todo o script” é “ **Run All** script”, daí Control+**Alt**+**R**).

Executar todo o script de uma vez só deve ser feito quando já se tem tudo depurado e livre de erros. Usualmente, executa-se um script muitas vezes linha a linha (**Control+Enter**) para ajustar o código e identificar erros.

Veja uma ilustração sobre como criar um novo script, digitar uma rotina e executá-la linha a linha:

![](<.gitbook/assets/2 (5).gif>)

Nesse exemplo, foi criado um código onde um vetor chamado **notas** recebe uma combinação de valores referentes às notas de 8 estudantes com a função **c( )**. Em seguida, é executada a função para calcular a média dos estudantes **mean(notas)**,

As partes do texto seguidos por **#** são comentários, que servem para a documentação e não são executados pelo R.

\# Exemplo de comentário em um código que calcula

\# as notas de um grupo de estudantes

\# ------------------------------------------

\# atribui conjunto de dados à variável notas

notas <- c(10, 7, 8, 4, 9, 5, 7, 8)

mean(notas) # calcula a média

Quando se executa esse script com a combinação de teclas Control+Enter, linha a linha, o R cria o vetor notas com os oito valores, calcula a média e devolve o resultado na janela do terminal interativo, logo abaixo da janela de script:

\> \[1] 7.25

Um detalhe que costuma confundir quem está começando a usar o R é o valor \[1] entre colchetes que antecede o resultado.

Esse número mostra que se trata do primeiro valor na primeira linha de resultados. Tem por finalidade somente ajudar a visualização da resposta quando a sequência de saída contiver muitas linhas.

Por exemplo, se for digitado o comando no Console do R para que sejam listados em sequência os números de 1 a 50, que pode ser feito inserindo dois pontos entre os números

\> 1:50 # a função : significa uma sequência de números de 1 até 50

O R retornará

\[1] 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27

\[28] 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50

A primeira linha da resposta começa com a marca \[1], que é o primeiro número da sequência de 1 até 27. A segunda linha começa com o vigésimo oitavo número \[28] da sequência que vai de 28 a 50.

Em respostas muito longas, com muitas linhas, esse tipo de marcação ajuda na localização dos valores procurados.

#### Nome das funções e operadores no R <a href="#id-2h9nmv9sg2b" id="id-2h9nmv9sg2b"></a>

Os nomes de funções e operadores no R, não são arbitrários. De modo geral, procuram ser uma representação mnemônica (em inglês) da operação que se está realizando. Por exemplo, **c( )** significa combinar (to combine) uma sequência de valores em um único vetor.

O operador **<-** é uma representação mnemônica de uma seta, indicando que o valor da direita será repassado para o vetor à esquerda da seta. A função **mean()** é o termo em inglês para a média.

Os nomes abreviados das funções podem parecer complicados de início, mas quando se compreende o seu significado, torna-se bastante útil para a escrita dos códigos. Seguindo o princípio de quanto mais letras a digitar, mais tempo se perde e mais erros aparecem, os nomes de funções e operações no R básico, em geral, procuram ser os mais abreviados possível.

É importante ter em conta que o R faz diferença entre letras maiúsculas e minúsculas. Por exemplo, mean() está correto. Já Mean() irá gerar um erro no terminal do R.

Muitos erros ocorrem na criação de scripts pela confusão entre maiúsculas e minúsculas.

Infelizmente, não há um padrão. Algumas funções contêm apenas letras minúsculas, outras mesclam maiúsculas e minúsculas, ou só maiúsculas.

Ao ler os scripts de exemplo, sempre preste muita atenção em como as funções são grafadas.

#### Operadores básicos <a href="#ffqksngyucdu" id="ffqksngyucdu"></a>

O R possui os seguintes operadores básicos:

<- Atribuição

\= Atribuição

\+ Adição

\- Subtração

\* Multiplicação

/ Divisão

^ Potência

exp() Exponencial

sqrt() Raiz quadrada

log() Logaritmo

log10() Logaritmo na base 10

O símbolo <- é operador de atribuição. Na maioria das linguagens de computação o operador de atribuição é o símbolo =\
No R, pode-se usar tanto o operador =, quanto o operador <-, que se parece com uma seta apontando para a esquerda.

O operador <- é utilizado preferencialmente pelos usuários R, no lugar do operador = , para evitar uma confusão lógica. Por exemplo, em computação, o seguinte código é válido e bastante comum em outras linguagens:

x = x + 1

Logicamente, um número não pode jamais ser igual a ele mesmo mais um. Mas, em computação, isso é possível porque o código deve ser lido como uma sequência de passos. Primeiro, o operador + acrescenta o valor 1 à variável x. Depois o operador = atribui o novo valor à própria variável, isto é, atualiza o valor de x.

Para evitar essa confusão, deve-se preferir o operador de atribuição <-, que deixa visualmente claro que se está passando o valor da direita para a variável à esquerda x <- x + 1 . Existe também o operador ->. Pode se escrever x + 1 -> x . Mas, não é comum.

Os códigos a seguir são idênticos, mas deve se dar preferência para a segunda notação em R:

x = 2

y = 3

z = x + y

x <- 2

y <- 3

z <- x + y

Em ambos os casos, o valor de z será 5.

Observe que há uma ordem de precedência entre os operadores aritméticos: /\*-+

Para alterar a ordem, pode-se utilizar parênteses.

x <- 6

y <- 2

w <- 3

z <- x / y + w #a divisão antes da soma

z

\[1] 6 #resultado

z <- x /( y + w) #a soma antes da divisão

z

\[1] 1.2 #resultado

### **Agora é com você** <a href="#id-42rtjqg2igtn" id="id-42rtjqg2igtn"></a>

1º) Abra o RStudio

2º) Crie um novo script em branco **Ctrl+Shift+N**

3º) Digite o seguinte código (você pode copiar e colar, mas digitar é melhor para você começar a se familiarizar com o código):

\# Exemplo de código em R que

\# atribui um conjunto de dados com as notas

\# de alunos a uma variável e, em seguida,

\# calcula a média da turma

notas <- c(10,7,8,4,9,5,7,8)

mean(notas) # calcula a média

4º) Execute o script linha a linha, posicionando o cursor na primeira linha, com **Ctrl+Enter** ou execute todo o script de uma só vez, teclando **Ctrl+Alt+R** (teste as duas formas para ver a diferença)

5º) Verifique o resultado na Aba Console com o valor da média das notas: \[1] 7.25



#### Sobre esse conteúdo <a href="#id-5n6cvmjko2cf" id="id-5n6cvmjko2cf"></a>

Este conteúdo digital é parte do curso online "Introdução aos Indicadores Sociais com o software R", de autoria do Prof. Ronaldo Baltar e da Prof.ª Cláudia Siqueira Baltar, como atividade do Projeto de extensão "Indicadores sociais como subsídio para o monitoramento e avaliação das ações dos municípios paranaenses em direção à Agenda 2030", vinculado ao ObPPP (Observatório de Populações e Políticas Públicas) e ao InfoSoc (Informática aplicada à Pesquisa Social), ambos projetos do Dept.º C. Soc. - CLCH/UEL.
