# Análise Exploratoria de Dados da Bolsa de Valores

Este repositório contém uma análise exploratória de dados da bolsa de valores. 

- A base de dados utilizada para a realização dessa aula prática se encontra no seguinte arquivo: ''[BANCO DE DADOS] Bolsa de Valores ''

- E online no seguinte link: https://docs.google.com/spreadsheets/d/1sGaR2Nkfi025rTzztCyDX7q-ZztHsK7U_SqXQr76dQ4/edit#gid=0

Foram realizados 3 processos para a análise dos dados: 

## 1. Trabalhando com Percentual: Transformação de valores, regressão e variação

Na coluna ‘’D’’ os valores estão em formato decimal, precisamos  transforma-los em percentuais, para isso, adicionei uma nova coluna chamada **'Variação %'** com a fórmula

```
 =D2/100.
```

Queremos calcular o valor ao qual a a ação começou o dia. Calcularemos o valor inicial do dia usando regressão percentual. Para isso, criamos uma coluna de **valor inicial** e aplicamos a seguinte formula:

 `X = 9,5/(1+0,5)` 

- 9,59,5 é o valor ao qual a ação fechou no final do dia.
- 0,05 é a variação percentual ao longo do dia (ou seja, 5%).

Passando essa formula para uma linguagem ao qual o Google Sheets entende, irei usar na nova coluna criada com o nome **Valor Inicial (R$),** o seguinte codigo:

```
=C2/(1+L2)
```
