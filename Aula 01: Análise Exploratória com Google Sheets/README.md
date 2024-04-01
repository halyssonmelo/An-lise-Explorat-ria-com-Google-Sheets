# Análise Exploratoria de Dados da Bolsa de Valores

Este repositório contém uma análise exploratória de dados da bolsa de valores. 

A base de dados utilizada para a realização dessa aula prática se encontra no seguinte em:  

E online no seguinte link: https://docs.google.com/spreadsheets/d/1sGaR2Nkfi025rTzztCyDX7q-ZztHsK7U_SqXQr76dQ4/edit#gid=0

Foram realizados 3 processos para a análise dos dados: 

## 1. Trabalhando com Percentual: Transformação de valores, regressão e variação

### Determinando o valor inicial das ações no dia:

Primeiro, para garantir a precisão dos meus cálculos, é essencial que os valores na coluna 'D', atualmente em formato decimal, sejam convertidos em valores percentuais. Para isso, vou acrescentar uma nova coluna chamada **'Variação %'**, na qual aplicarei a seguinte fórmula:

```
=D2/100.

```

Com a transformação dos valores concluída, podemos avançar para o cálculo do valor inicial do dia. Para isso, vamos empregar um conceito matemático conhecido como regressão percentual.

Nossa fórmula matemática será a seguinte:

`X = 9,5/(1+0,5)`

Onde:

- 9,5 é o valor final das ações ao final do dia.
- 0,05 é a variação percentual ao longo do dia (ou seja, 5%).

Para traduzir esta fórmula para uma linguagem que o Google Sheets compreenda, na nova coluna intitulada **Valor Inicial (R$)**, usarei o seguinte código:

```
=C2/(1+L2)

```

## 2. Utilizando o VLOOKUP para importação de dados

### Exportando dados de outra base

Agora, além da porcentagem inicial das ações, queremos saber o quanto isso representa em dinheiro.

Para isso, precisamos saber o total de ações no mercado da empresa em questão. Vamos usar outra base de dados, chamada "Total Ações", onde possuímos a quantidade teórica de ações disponíveis no mercado.

Precisamos combinar essa base com a nossa base atual. Para isso, usaremos uma função chamada VLOOKUP no Sheets.

Vamos criar uma coluna chamada "Quantidade de ações" na nossa tabela base e aplicar o seguinte código nela:

```
=VLOOKUP(A2;Total_de_acoes!A:B;2;0)

```

Essencialmente, essa fórmula procura o valor na célula A2 na planilha atual, na planilha "Total_de_acoes", na coluna A. Quando encontra esse valor, retorna o valor correspondente na coluna B.

O código retorna o valor exato correspondente na coluna B da planilha "Total_de_acoes". 

Da mesma forma utilizarei o VLOOKUP para importar os nomes das empresas contidos na planilha ‘’Ticker”, criando a coluna chamada ‘’Nome da Empresa’’. O código será o seguinte:

```
=VLOOKUP(A2;Ticker!A:B;2;0)
```

### Calculando a variação em dinheiro

Temos o valor inicial da variação e o valor final, mas cada empresa tem uma quantidade de ações que já importamos da planilha "Total_de_acoes” para a nossa planilha base, na coluna ‘’N’’.

A quantidade de ações afeta o valor a ser convertido em dinheiro. Para calcular, usamos a fórmula:

Valor da Variação em Reais=(Valor Final−Valor Inicial)×Quantidade de Açoes

Na fórmula:

- **Valor Final**: O valor de fechamento da ação.
- **Valor Inicial**: O valor de abertura da ação.
- **Quantidade de Ações**: O número de ações que possui ou quer calcular a variação.

Subtraia o valor inicial do valor final para obter a variação do preço da ação e, então, multiplique pela quantidade de ações para calcular o valor total da variação em reais.

Para o sheets, usaremos o seguinte código:

O código para calcular a variação em dinheiro no Google Sheets é o seguinte:

```
=(C2-B2)*N2

```

Neste código:

- C2 é a célula que contém o Valor Final.
- B2 é a célula que contém o Valor Inicial.
- N2 é a célula que contém a Quantidade de Ações.

Este código subtrai o Valor Inicial do Valor Final e multiplica o resultado pela Quantidade de Ações. O resultado é o Valor da Variação em Reais.

Assim, o cálculo da variação monetária das ações é automatizado no Google Sheets, permitindo uma análise rápida e eficiente dos dados da bolsa de valores.

Após aplicar a formula, iremos observar valores muito grandes e desordenados sem virgula ou separação. Para isso, precisamos transformar esses valores em formato de moeda,.

## 3. Utilizando o IF

Criaremos uma coluna "Resultado" para classificar o desempenho das empresas com base na variação monetária previamente calculada. Este critério nos permitirá identificar as empresas cujas ações registraram crescimento, aquelas que apresentaram queda e aquelas que permaneceram estáveis. Para alcançar esse objetivo, utilizaremos a cláusula "IF" em nosso código. O código a ser utilizado é o seguinte:
