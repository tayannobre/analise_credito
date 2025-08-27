# analise_credito

# 🏦 Análise de Crédito com Naive Bayes (R)

Este repositório contém um projeto inicial de **Machine Learning** aplicado à **análise de crédito de clientes**, utilizando o algoritmo **Naive Bayes** no R.

---

## 📊 Objetivo
Prever se um cliente é considerado **"bom" ou "ruim" pagador** com base em atributos como renda, idade, histórico de crédito, entre outros.

---

## ⚙️ Etapas do Projeto

1. **Instalação do pacote e carregamento do pacote**
   ```R
   install.packages("e1071")
   library(e1071)
   
2. **Importar dataset**
   ```R
   creditO <- read.csv(file.choose(), sep = ",", header = TRUE)
   - 2.1. **Visualizar primeiras linhas**
   ```R
   head(creditO)

3. **Divisão em treino e teste**
   ```R
   amostra <- sample(2, nrow(creditO), replace=TRUE, prob=c(0.7,0.3))
   creditotreino <- creditO[amostra==1,]
   creditoteste  <- creditO[amostra==2,]

   
