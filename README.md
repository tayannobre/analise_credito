# 🏦 Análise de Crédito com Naive Bayes (R)

Este repositório contém um projeto inicial de **Machine Learning** aplicado à **análise de crédito de clientes**, utilizando o algoritmo **Naive Bayes** no R.

---

## 1. Objetivo

Prever se um cliente é considerado **"bom" ou "ruim" pagador** com base em atributos como renda, idade, histórico de crédito, entre outros.

---

## 2. Instalação e Carregamento do Pacote

```R
install.packages("e1071")
library(e1071)

---

## 3. Carregamento do Conjunto de Dados

```R
creditO <- read.csv(file.choose(), sep = ",", header = TRUE)

### Visualizando as primeiras linhas

```R
head(creditO)





