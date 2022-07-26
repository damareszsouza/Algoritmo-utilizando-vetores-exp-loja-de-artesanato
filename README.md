# Algoritmo-utilizando-vetores-exp-loja-de-artesanato

Ir para o conteúdo principal
Damares Costa de Souza 
Moodle - IFRS

Programação Básica com Java III - Turma 2022B
Painel Meus cursos  PBJIII2022B 2. Vetores  2.3. Exemplos de Algoritmos Utilizando Vetores
 
2.3. Exemplos de Algoritmos Utilizando Vetores
1. Uma Loja de Artesanato
Nesta seção vamos resolver o problema descrito abaixo:

Uma pequena loja de artesanato possui apenas um vendedor e comercializa dez tipos de objetos. O vendedor recebe, mensalmente, salário de R$ 1100,00, acrescido de 5% do valor total de suas vendas. O valor unitário dos objetos deve ser informado e armazenado em um vetor; a quantidade vendida de cada peça deve ficar em outro vetor, mas na mesma posição. Crie um programa que receba os preços e as quantidades vendidas, armazenando-as em seus respectivos vetores (ambos com tamanho dez). Depois, determine e mostre:

um relatório contendo quantidade vendida, valor unitário e valor total de cada objeto;
valor total geral das vendas e o valor da comissão que será paga ao vendedor;
o valor do objeto mais vendido e sua posição no vetor (não se preocupe com empates).
A primeira coisa que precisamos nos preocupar nesse problema, como em todos os outros que já resolvemos até aqui,  é quais são os dados que precisaremos receber do usuário (entrada de dados) e como eles serão armazenados pelo programa. Segundo o enunciado do exercício, os dados que o programa deve receber do usuário são o valor unitário dos objetos vendidos pela loja e as quantidades vendidas de cada um deles. Segundo o mesmo enunciado, precisamos armazenar esses dados em vetores. Para declarar os vetores precisamos responder duas perguntas:

Qual o tamanho dos vetores (quantidade de posições)? Segundo o enunciado do problema, cada vetor deverá ter tamanho dez.
Qual o tipo de dados utilizado para as posições de cada vetor?  O valor unitário de um produto é um número real, portanto o tipo utilizado deverá ser o tipo real. Já as quantidades vendidas de cada objeto corresponde a valores inteiros (a loja não venderá frações de objetos). Assim, é possível utilizar o tipo inteiro para esse vetor.
Desse modo, podemos escrever a primeira parte do algoritmo em pseudocódigo para esse problema como mostrado abaixo. 



Algoritmo “LojaArtesanato”

var

vetValorUnit : vetor [1..10] de real

vetQuanVend: vetor [1..10] de inteiro

cont : inteiro

inicio

para cont de 1 até 10 faça

leia vetValorUnit[cont], vetQuantVend[cont]

fim para

fim



Neste algoritmo já incluímos também o código para leitura de ambos os vetores, utilizando uma estrutura para...faça, similar ao que já fizemos nos exemplos anteriores. Note que a leitura de ambos os vetores está sendo realizada em um único para..faça pois as respectivas posições de cada vetor correspondem ao mesmo produto.

Agora é possível gerar o relatório dos produtos solicitado pelo problema. É necessário mostrar a quantidade vendida, o valor unitário e o valor total de cada objeto. Como as informações necessárias para efetuar esses cálculos estão nos vetores que lemos anteriormente, será necessário percorrê-los, acessando cada posição. Já sabemos como fazer isso: utilizando uma estrutura para..faça!

Para gerar os valores de quantidade vendida e valor unitário de cada objeto, basta mostrar os respectivos valores em cada vetor. O valor total de cada objeto será calculado multiplicando-se seu valor unitário pela quantidade vendida. Assim, acrescentando o código necessário para efetuar essas operações, chegamos ao algoritmo mostrado na abaixo.



Algoritmo “LojaArtesanato”

var

vetValorUnit : vetor [1..10] de real

vetQuanVend: vetor [1..10] de inteiro

cont : inteiro

total: real

inicio

para cont de 1 até 10 faça

leia vetValorUnit[cont], vetQuantVend[cont]

fim para

 

para cont de 1 até 10 faça

       escreva cont, vetQuantVend[cont], vetValorUnit[cont]

       total ← vetValorUnit[cont] * vetQuantVend[cont]

escreva total

fim para

fim



Precisamos também calcular o valor total geral e a comissão do vendedor. O valor total geral é calculado somando-se o valor total de cada objeto. Podemos fazer esse cálculo utilizando a própria estrutura para...faça que fizemos agora há pouco. O valor da comissão será de 5% sobre o valor total geral. Assim, obtemos o pseudocódigo mostrado abaixo.



Algoritmo “LojaArtesanato”

var

vetValorUnit : vetor [1..10] de real

vetQuanVend: vetor [1..10] de inteiro

cont : inteiro

total, totalGeral, comissao : real

inicio

para cont de 1 até 10 faça

leia vetValorUnit[cont], vetQuantVend[cont]

fim para

totalGeral ← 0

para cont de 1 até 10 faça

       escreva cont, vetQuantVend[cont], vetValorUnit[cont]

       total ← vetValorUnit[cont] * vetQuantVend[cont]

escreva total

       totalGeral ← totalGeral + total

fim para

comissao ← totalGeral * 0.05

escreva totalGeral, comissao

fim



A última etapa de nossa solução diz respeito à mostrar o valor do objeto mais vendido e o número de seu índice nos vetores utilizados no programa. Um objeto será o mais vendido se a quantidade vendida dele for a maior. No tópico anterior já construímos um algoritmo para verificar o maior elemento de uma lista. Neste problema devemos encontrar o maior valor presente no vetor vetQuantVend. Podemos então pensar no trecho de código abaixo:



       objMaisVend ← vetQuantVend[1]

para cont de 2 até 10 faça

se vetQuantVend[cont] > objMaisVend então

             objMaisVend ← vetQuantVend[cont]

fim se

fim para



Neste trecho de código fizemos uma cópia do algoritmo do maior valor em uma lista mostrado no tópico anteiror, substituindo maior por objMaisVend (uma variável que declararemos em nosso algoritmo da loja) e substituindo nota pela referência a uma posição do vetor vetQuandVend. Este código, ao final, armazenará na variável objMaisVend o valor da maior quantidade vendida.

Porém, neste problema, precisamos do número do índice do objeto com a maior quantidade vendida! Para fazer isso, vamos fazer uma rápida modificação no código, como mostrado abaixo:



       objMaisVend ← 1

para cont de 2 até 10 faça

se vetQuantVend[cont] > vetQuantVend[objMaisVend] então

             objMaisVend ← cont

fim se

fim para



Com esta modificação, a variável objMaisVend armazenará o número do índice da posição do vetor vetQuantVend com a maior quantidade vendida. Este índice corresponde ao objeto mais vendido. O trecho de algoritmo começa assumindo que o objeto mais vendido é o correspondente ao índice 1 (o primeiro) e depois procura por uma posição com uma quantidade maior. Se encontrar, armazena o índice desta posição.
Assim, estamos prontos a construir a versão final de nosso algoritmo. A figura abaixo mostra o algoritmo completo.



Algoritmo “LojaArtesanato”

var

vetValorUnit : vetor [1..10] de real

vetQuanVend: vetor [1..10] de inteiro

cont, objMaisVend : inteiro

total, totalGeral, comissao : real

inicio

para cont de 1 até 10 faça

leia vetValorUnit[cont], vetQuantVend[cont]

fim para

totalGeral ← 0

para cont de 1 até 10 faça

       escreva cont, vetQuantVend[cont], vetValorUnit[cont]

       total ← vetValorUnit[cont] * vetQuantVend[cont]

escreva total

       totalGeral ← totalGeral + total

fim para

comissao ← totalGeral * 0.05

escreva totalGeral, comissão

objMaisVend ← 1

 

para cont de 2 até 10 faça

se vetQuantVend[cont] > vetQuantVend[objMaisVend] então

             objMaisVend ← cont

fim se

fim para

 

escreva objMaisVend, vetorValorUnit[objMaisVend]


fim
Seguir para...
Pular Índice
Índice
1. Uma Loja de Artesanato
2. Somando os Elementos de um Vetor
3. Utilizando os Elementos de um Vetor como Contadores
4. Corrigindo Provas de Múltipla Escolha
5. Procurando Números em um Vetor
Academi
Dúvidas? 
Perguntas frequentes

Fale conosco | Suporte | Contato

Informação
Termos e Condições de Uso
Aviso de Privacidade e Proteção de Dados Pessoais
Contato
Rua Gen. Osório, 348, Bento Gonçalves/RS
Siga-nos
Copyright © 2017 - Desenvolvido por LMSACE.com. Distribuído por Moodle
