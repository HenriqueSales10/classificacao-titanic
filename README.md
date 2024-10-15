# Predição dos sobreviventes do Titanic
Esta atividade utiliza o conjunto de dados do Titanic, disponível no Kaggle através do link https://www.kaggle.com/c/titanic/data, para prever a sobrevivência dos passageiros usando o algoritmo de classificação k-Nearest Neighbors (k-NN). A seguir, uma breve explicação do processo de carregamento, pré-processamento dos dados, implementação do modelo e avaliação do desempenho.

# 1. Carregamento e Pré-processamento dos Dados
Carregamento dos Dados
Os dados foram carregados diretamente do arquivo CSV que está anexado neste reposítório. As colunas principais incluem informações sobre os passageiros, como classe social (Pclass), idade (Age), tarifa (Fare), sexo (Sex), entre outras.

Tratamento de Valores Nulos
Coluna Age: Contém valores nulos, que foram preenchidos pela média de idades.
Coluna Cabin: Possui muitos valores faltantes e foi desconsiderada no modelo final.
Coluna Embarked: Apenas 2 valores nulos foram encontrados, mas não usados no modelo final.
Codificação de Variáveis Categóricas
A coluna Sex foi convertida para uma variável binária (0 para feminino e 1 para masculino), utilizando a técnica de codificação "dummy".

Seleção de Variáveis
As variáveis escolhidas para o modelo foram:

Pclass: Classe do passageiro (1ª, 2ª, ou 3ª classe)
Age: Idade do passageiro
Fare: Preço da passagem
Sex_male: Sexo do passageiro (0: feminino, 1: masculino)
A variável alvo (variável a ser prevista) é a coluna Survived, que indica se o passageiro sobreviveu (1) ou não (0).

# 2. Implementação do Algoritmo k-NN
Divisão do Conjunto de Dados
Os dados foram divididos em conjuntos de treino e teste na proporção 70%/30% para garantir que o modelo fosse treinado e testado corretamente.

Modelo k-NN
O modelo k-Nearest Neighbors foi implementado utilizando k=3, o que significa que o algoritmo considera os 3 vizinhos mais próximos para determinar a classe de um novo ponto. A função KNeighborsClassifier da biblioteca scikit-learn foi utilizada para treinar o modelo.

Treinamento e Previsão
O modelo foi treinado com o conjunto de treino, e previsões foram feitas no conjunto de teste.

# 3. Avaliação de Desempenho
Acurácia
O modelo k-NN obteve uma acurácia de 68%, o que indica que o modelo conseguiu prever corretamente 68% das observações do conjunto de teste.

Matriz de Confusão
A matriz de confusão foi gerada para analisar os erros e acertos nas previsões. Esta matriz mostra:

Quantos passageiros que realmente sobreviveram foram corretamente identificados.
Quantos passageiros que não sobreviveram foram classificados corretamente como não sobreviventes.
Erros, como sobreviventes classificados como não sobreviventes, e vice-versa.
A matriz de confusão pode ser usada para calcular outras métricas como precisão, recall, e F1-score, que fornecem uma análise mais detalhada do desempenho.

# 4. Observações e Melhorias Possíveis
Número de Variáveis: Apenas quatro variáveis foram utilizadas para treinar o modelo. O uso de mais variáveis, como SibSp (número de irmãos/cônjuges a bordo) e Parch (número de pais/filhos a bordo), poderia melhorar a precisão do modelo.
Normalização dos Dados: O k-NN é sensível à escala dos dados, então normalizar as variáveis numéricas pode melhorar o desempenho do modelo.
Escolha do k: O valor de k=3 foi definido. Realizando testes com um número maior de vizinhos, a porcentagem de acurácia diminuiu.
Modelo Simples: Embora o k-NN seja fácil de implementar, outros algoritmos de classificação, como a Regressão Logística, Árvores de Decisão ou Random Forest, podem ser comparados para ver se melhoram a previsão de sobrevivência.
