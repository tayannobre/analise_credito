# 🏦 Análise de Crédito com Naive Bayes (R)

Este repositório contém um projeto simples de **Machine Learning** aplicado à **análise de crédito de clientes**, utilizando o algoritmo **Naive Bayes** no R.

---

## 📊 Objetivo
Prever se um cliente é considerado **"bom" ou "ruim" pagador** com base em atributos como renda, idade, histórico de crédito, entre outros.

---

## ⚙️ Etapas do Projeto

1. **Instalando e carregando o pacote**
   ```R
   install.packages("e1071")
   library(e1071)

2. **Carregando o dataset**
   ```R
   creditO = read.csv(file.choose(), sep=",", header=T)

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
   novocredito = read.csv(file.choose(), sep=",", header=T) # carregando um novo conjunto de dados para o qual você quero se os novos clientes são "bom" ou "ruim" pagador.
   predict(modelo, novocredito) # fazendo a previsão se o novo cliente é "bom" ou "ruim" pagador.


## 📈 Resultados Obtidos  

Após o treinamento do modelo com **70% dos dados para treino** e **30% para teste**, foram obtidos os seguintes resultados:  

### 🔹 Matriz de Confusão

## 📊 Matriz de Confusão do Modelo

A matriz de confusão do modelo Naive Bayes treinado é a seguinte:

| Classe Real \ Classe Prevista | bom | ruim |
|-------------------------------|-----|------|
| **bom**                        | 180 | 22   |
| **ruim**                       | 51  | 39   |

**Explicação:**  
- **Linhas** → Classe real do cliente (`bom` ou `ruim`).  
- **Colunas** → Classe prevista pelo modelo (`bom` ou `ruim`).  
- **Diagonal principal** (180 e 39) → acertos do modelo.  
- **Valores fora da diagonal** (22 e 51) → erros do modelo.


### 🔹 Métricas
- **Taxa de acerto (acurácia):** `0.75` (75%)  
- **Taxa de erro:** `0.25` (25%)  

### 🔹 Teste com novos clientes
O modelo foi testado em um novo conjunto de dados (`novocredito.csv`), e a predição foi:  
- [1] ruim bom  bom  bom  bom  bom  ruim bom 
- Levels: bom ruim 

**Observação**
- O conjunto de dados (`novocredito.csv`) contém 6 novos registros ( novos clientes) que ainda não possuem a classificação (classe) preenchida. O modelo irá prever automaticamente se cada cliente é bom ou ruim.

## 📝 Considerações Finais

Este projeto é um exemplo inicial de Machine Learning para análise de crédito usando Naive Bayes no R.

O modelo teve uma taxa de acerto global de 75%, funcionando melhor para clientes bons do que para clientes ruins.

Limitações: base de dados pequena e uso de apenas um modelo simples.
