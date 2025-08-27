# 🏦 Análise de Crédito com Naive Bayes (R)

Este repositório contém um projeto inicial de **Machine Learning** aplicado à **análise de crédito de clientes**, utilizando o algoritmo **Naive Bayes** no R. O objetivo é prever se um cliente é considerado **"bom" ou "ruim" pagador** com base em atributos como renda, idade, histórico de crédito, entre outros.

---

```R
# Instalando e carregando o pacote
install.packages("e1071")
library(e1071)

# Carregando o conjunto de dados
creditO <- read.csv(file.choose(), sep = ",", header = TRUE)
head(creditO)

# Divisão em treino e teste
amostra <- sample(2, nrow(creditO), replace=TRUE, prob=c(0.7,0.3))
creditotreino <- creditO[amostra==1,]
creditoteste  <- creditO[amostra==2,]

dim(creditotreino)
dim(creditoteste)

# Criação do modelo Naive Bayes
modelo <- naiveBayes(CLASSE ~ ., creditotreino)
class(modelo)

# Predição e avaliação do modelo
predicao <- predict(modelo, creditoteste)
confusao <- table(creditoteste$CLASSE, predicao)

taxadeacerto <- (confusao[1] + confusao[4]) / sum(confusao)
taxadeerro   <- (confusao[2] + confusao[3]) / sum(confusao)

taxadeacerto
taxadeerro

# Testando novos clientes
novocredito <- read.csv(file.choose(), sep=",", header=TRUE)
predict(modelo, novocredito)

   
