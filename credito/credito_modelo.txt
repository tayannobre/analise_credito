# ANALISE DE CREDITO 

# instalando o pacote NaiveBayes
install.packages("e1071")

# carregando o pacote
library(e1071)

# carregando o conjunto de dados 
creditO = read.csv(file.choose(), sep = ",", header = T)
creditO
head(creditO)

## criando uma amostra para 70% treino e 30% teste.
amostra = sample(2,1000, replace = T, prob = c(0.7,0.3))
amostra


creditotreino = creditO[amostra==1,] # criando um vetor para separar o dataset, 1(treino)
creditoteste = creditO[amostra==2,] # criando um vetor para separar o dataset, (teste)
creditotreino
creditoteste

# criação do modelo
modelo = naiveBayes(CLASSE  ~ . , creditotreino  )
modelo

# clase do modelo
class(modelo)

# verificando o desempenho do meu modelo
predicao = predict(modelo, creditoteste)
predicao

# criando a matriz de confusão do modelo
confusao = table(creditoteste$CLASSE, predicao)
confusao

# taxa de acerto 
taxadeacerto = (confusao[1] + confusao[4]) / sum(confusao)
taxadeacerto

# taxa de erro
taxaerro = (confusao[2] + confusao[3]) / sum(confusao)
taxaerro


# TESTANDO O MODELO 

# carregando o arquivo "novocredito"
novocredito = read.csv(file.choose(), sep=",", header=T)
novocredito

# fazendo a previsão se o novo cliente é "bom" ou "ruim" pagador.
predict(modelo, novocredito)