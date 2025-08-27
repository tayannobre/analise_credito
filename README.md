# 🏦 Análise de Crédito com Naive Bayes (R)

Este repositório contém um projeto inicial de **Machine Learning** aplicado à **análise de crédito de clientes**, utilizando o algoritmo **Naive Bayes** no R.

---

## 📊 Objetivo
Prever se um cliente é considerado **"bom" ou "ruim" pagador** com base em atributos como renda, idade, histórico de crédito, entre outros.

---

## ⚙️ Etapas do Projeto

1. **Instalação do pacote**
   ```R
   install.packages("e1071")
   library(e1071)

2. **Carregando o dataset**
   ```R
   creditO = read.csv("data/credito.csv", sep=",", header=TRUE)

3. **Divisão em treino e teste**
   ```R
   amostra = sample(2, nrow(creditO), replace=TRUE, prob=c(0.7,0.3)) # criando uma amostra para 70% treino e 30% teste.
   creditotreino = creditO[amostra==1,] # criando um vetor para separar o dataset, 1(treino)
   creditoteste  = creditO[amostra==2,] # criando um vetor para separar o dataset, 2(teste)

4. **Criação do modelo Naive Bayes**
   ```R
   modelo = naiveBayes(CLASSE ~ ., creditotreino)
   modelo # visualização do modelo

5. **Predição e desempenho do modelo**
   ```R
   predicao = predict(modelo, creditoteste) # predição do modelo 
   confusao = table(creditoteste$CLASSE, predicao) # criando uma matriz de confusão 
   taxadeacerto = (confusao[1] + confusao[4]) / sum(confusao) # taxa de acerto (acurácia do modelo)
   taxaerro = (confusao[2] + confusao[3]) / sum(confusao) # taxa de erro


6. **Testando o modelo (testando novos clientes)**
   ```R
   novocredito = read.csv("data/novocredito.csv", sep=",", header=TRUE) # carregando um novo conjunto de dados para o qual você quero se os novos clientes são "bom" ou "ruim" pagador.
   predict(modelo, novocredito) # fazendo a previsão se o novo cliente é "bom" ou "ruim" pagador.


## 📈 Resultados Obtidos  

Após o treinamento do modelo com **70% dos dados para treino** e **30% para teste**, foram obtidos os seguintes resultados:  

### 🔹 Matriz de Confusão
