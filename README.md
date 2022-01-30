# Fuzzy-Modeling

## Abstract  
В целом, почему проблема важна и что делается в статье (что оцениваются параметры как с точки зрения метрических характеристик, так и топологические и тд...), что исследуется множество возможных моделей генерации графа, чтобы приблизить граф структурного коннектома.
## 1. Introduction  
Описание проблемы, что получено и что исследовано до меня, кто интересовался и что сделал уже. Почему в целом нечеткое моделирование может помочь. 
## 2. Basic definitions 
Про определения, каоторые используются
## 3. Estimated parameters 
G = (V,E)  
##### 3.1 Edge density  
The parameter called an edge density illustrates the density of a graph G, that is the maximum number of edges (full graph) is equal to $ n(n-1)/2$, where n - number of vertices. Therefore, edge density $ \epsilon = 2 |E| / (n(n-1)) $. This parameter reflects general structure of a graph and do not depends on the weight of edges.  
##### 3.2 $F_1$  
```LaTeX
F_1(x)=P(i~j,d_{i,j}<x)
```
$F_1$ is a function that gives a joint probability that two vertices are adjacent and within a certain distance from each other.
##### 3.3 $F_2$  
```LaTeX
F_2(x)=P(d_{i,j}<x)
```
$F_2$ is a function that gives a probability that two vertices are within a certain distance from each other.
##### 3.4 Degrees vector
A vector of intensities $\overline{p}$ is a vector with the length n (number of nodes) and each of coordinates gives the degree of the corresponding node. Degrees distribution is an extremelly important parameter that allow to build integrated estimation of a graph including edge dencity, is it appropriate to use a geometric component or not (that is a vertex with a higher degree is more likely to connect to a new vertex) and others.  
##### 3.4 Maximum degree
The parameter called maximum degree shows the degree of node with the maximum number of the adjacent ones.  
##### 3.5 Number of triangles, clasterization coefficient
The number of triangles of a graph gives the information about possible clusterization process, that shows a general structure of a network. Clusters are particularly significant object related to connectomes, since connectomes can be divided into the large regions with the neurons which have similar functions.  
##### 3.6 Eigenvalues
The eigenvalues of adjacency matrices strongly correspond to the local and global properties of the network such as degree, clustering coeficient and so on. Eigenvalues provides global and comlex comparing characteristic of a graph.  
##### 3.7 PageRanks
The PageRank vector illustrate importance of nodes. This parameter reflects the probability to be in the node after random walk.  
##### 3.8 [Geometry score](https://github.com/kseniashilova/Fuzzy-Modeling/blob/main/Geometry%20Score%20A%20Method%20For%20Comparing%20Generative%20Adversarial%20Networks.pdf)
## 4. Estimations to linguistic variables
Как перевести измеренные характеристики в лингвистические переменные
## 5. Коэффициенты для каждого метода - в зависимости от того, что больше нужно (топологические, метрические характеристики и тд)  
Как в общем виде представить, какие характеристики более важные, то есть ввести коэффициенты в общем виде (альфа, бета и тд)
## 6. Description of algorithms  
Описать какие алгоритмы существуют для генерации графа, приближенного к коннектому
## 7. Results of experiment
Какая модель оказалось лучшей? совпадает ли это с ожиданиями?
## 8. Conclusion
## References 
