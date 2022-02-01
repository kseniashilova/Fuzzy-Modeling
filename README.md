# Fuzzy-Modeling

Models definning and the experement: https://colab.research.google.com/drive/1R3xN1R1r6LasQB-Jk4K58Qilx7fRQqJ1?usp=sharing
## Abstract  
В целом, почему проблема важна и что делается в статье (что оцениваются параметры как с точки зрения метрических характеристик, так и топологические и тд...), что исследуется множество возможных моделей генерации графа, чтобы приблизить граф структурного коннектома.
## 1. Introduction  
Описание проблемы, что получено и что исследовано до меня, кто интересовался и что сделал уже. Почему в целом нечеткое моделирование может помочь. 
## 2. Basic definitions 
Про определения, которые используются
## 3. Estimated parameters 
To compare two graphs we provide some characteristics that can be computed on the graphs. There are parameters that are related to topological structure of a graph, that is they do not depend on weights of the edges. The main parameters independent of distances are edge density, degrees vector, maximum degree, number of triangles, clasterization coefficient and page rank vector.  The characteristic that provides some information about distances between nodes are so-called F1 and F2 functions (functions that gives a joint probability that two vertices are adjacent and within a certain distance from each other and that two vertices are within a certain distance from each other), and moreover the eigenvalues of adjacency matrix. Besides, we can compute the weights distribution as the parameter that is not such global and complex.
##### 3.1 Edge density  
The parameter called an edge density illustrates the density of a graph G, that is the maximum number of edges (full graph) is equal to $ n(n-1)/2$, where n - number of vertices. Therefore, edge density $ \epsilon = 2 |E| / (n(n-1)) $. This parameter reflects general structure of a graph and do not depends on the weight of edges. 
##### 3.2 Connected components
The parameter illustrates the number of connected components of a graph. This characteristic is the simplest way to concern the topological properties of a graph.
##### 3.3 Degrees vector
A vector of degrees is a vector with the length n (number of nodes) and each of coordinates gives the degree of the corresponding node. Degrees distribution is an extremelly important parameter that allow to build integrated estimation of a graph including edge dencity, is it appropriate to use a geometric component or not (that is a vertex with a higher degree is more likely to connect to a new vertex) and others properties.   
##### 3.4 Number of triangles
The number of triangles of a graph gives the information about possible clusterization process, ability of nodes to connect with neightbours. The parameter shows a general structure of a network.
##### 3.5 Clustering coefficient
Clusters are particularly significant object related to connectomes, since connectomes can be divided into the large regions with the neurons which have similar functions.  
##### 3.6 PageRank vector
The PageRank vector illustrate importance of nodes. This parameter reflects the probability to be in the node after random walk.
##### 3.7 Eigenvalues
The eigenvalues of adjacency matrices strongly correspond to the local and global properties of the network such as degree, clustering coeficient and so on. Eigenvalues provides global and comlex comparing characteristic of a graph.  
##### 3.8 Weights vector
The vector of weights of the graph edges can illustrate the maximum, minimum, the most frequent and so on number from the set of the weights, distances between teo nodes.      
 

## 4. Description of algorithms  
##### 4.1 Erdos-Renyi model
The Erdos-Renyi model of generating a random graph has the input of the number of nodes and the edge density. Then, the points are randomly placed in a space and the probability that the two choosen nodes have an edge is equal to the edge density.  
##### 4.2 Geometric model
The random geometic graph is the concept of N randomly distributed nodes in a space, where each two node is adjacent if the distance between them do to exceed some given treshold. The input of model is N (number of nodes) and t (treshold value).  
##### 4.3 Barabasi-Albert model
The Barabasi-Albert model of generating a random graph get as an initial value N (number of nodes). Then, the selected M (M >= 2 and M < N, usually M = 2) nodes are placed in a space and each new node becomes connected with M existed nodes, besides the probability to be connected with a vertex is proportional to degree of this vertex and equal to the degree divided by the sum of degrees. It is the concept called "the rich get richer".  
##### 4.4 Chung Lu model
The Chung-Lu model required as an input the vector of expected degrees of the nodes. Then each node is assigned a weight from this vector and the two selected nodel get a connection edge with the probability proportional to the product of their weights, namely, is equal to the product of weights divided by the sum of the weights vector elements. 
##### 4.5 Simple Geometric Chung Lu model  
The Simple Geometric Chung Lu model illustrate how to combine the random geometic graph model and the Chung Lu model. The input of the model is the vector of expected degrees of the nodes. The process of the graph building: points are placed independently and randomly in the space, then they are assosiated to the element of the nodes weihts vector. Then, the probability of the existing connection between two nodes can be calculated as the product of the weights divided by the sum of the weights vector elements normalized by the distance between them.  
   
## 5. Estimations to linguistic labels
To construct the fuzzy model it is nessesary to define the correspondence of the computational estimate and the linguistic label. All of metrics, that is presented in the section 3, can be used to demonstrate the relative error of the approximation of other graph. That is we compare two graphs, however one of them is reference. Consequently, the linguistic variable indicate the quality of the graph approximation estimated by certain parameter. This is an open question, how to define the number of the linguistic terms, nevertheless in this paper we consider 7 labels as an optimal number providing sufficient accuracy. The set of labels is defined as {the similarity is extremely high, the similarity is very high, the similarity is high, the similarity is medium, the similarity is low, the similarity is very low, the similarity is extremely low}.   
As a membership function, it is convenient to define a piecewise‐defined function triangular function for each linguistic term. In this case, trapezoidal membership functions is the unnecessary complication of charts, because there are enough linguistic labels to get the result. 
*******ФУНКЦИЯ В ОБЩЕМ ВИДЕ  
  
In fact, the relative error is measured as a float number. Then it is mandatory to define all linguistic terms corresponding to the linguistic labels on the segment from 0 to 15 (because the experements did not give the greater result for an error).    
To make a assumptions, we put that  
* {the similarity is extremely high} has the core of 0 and the support from 0 to 0.2
* {the similarity is very high} has the core of 0.2 and the support from 0 to 0.4  
* {the similarity is high} has the core of 0.4 and the support from 0.2 to 0.6  
* {the similarity is medium} has the core of 0.5 and the support from 0.3 to 0.7  
* {the similarity is low} has the core of 0.6 and the support from 0.4 to 0.8  
* {the similarity is very low} has the core of 0.8 and the support from 0.6 to 1 
* {the similarity is extremely low} has the core of the segment [1; 15] and the support from 0.8 to 15. (the only trapezoidal membership function that illustrate that all of a quite large relative errors demonstrate the extremely low similarity)  
 
![](https://github.com/kseniashilova/Fuzzy-Modeling/blob/main/membership_finctions.png)   

## 6. Experiment
The five different models mentioned above was considered during the experement. To start with the model generated a graph was described with python code, as well as the calculation of parameters for estimating.  Then, the relative error of each approximation was calculated and fixed. There were 100 iterations of the random graph construction, which were averaged. As the main result obtained by this step, it can be considered a vector of 8 averaged estimated relative errors (for each parameter) for all generation models.  
| Model\Similarity   | edge density   | connected components | degrees vector | triangles | clustering coeff | PageRank vector | eigenvalues| weights|
|--------------------|----------------|----------------------|----------------|-----------|------------------|-----------------|------------|--------|
| Erdos-Renyi        |       0.03     |        0.5           |     0.47       |   0.85    |      0.67        |       0.19      |    11.09   | 11.05  |
| Geometric          |       0.75     |        3.48          |     0.81       |   0.97    |      0.14        |       0.14      |    0.47    | 1.72   |
| Barabasi-Albert    |       0.7      |        0.5           |     0.73       |   0.99    |      0.67        |       0.54      |    5.55    | 10.47  |
| Chung Lu           |       0.07     |        0.49          |     0.09       |   0.33    |      0.09        |       0.3       |    10.89   | 11.04  |
| Geometric Chung Lu |       0.65     |        0.5           |     0.57       |   1.33    |      0.38        |       0.25      |    12.38   | 10.15  |

  
   
The problem is to estimate the model according to eight pre-prepared criteria. To get the enough correct result it is needed to determine the system of rules. The linguistic label for output estimation are the same as for the input ones.  

##### Rules:  
IF similarity of any parameter is "extremely high" THEN graph similarity is "extremely high".  
IF similarity of any parameter is "very high" THEN graph similarity is "very high".  
IF similarity of any parameter is "high" THEN graph similarity is "high".  
IF similarity of any parameter is "medium" THEN graph similarity is "medium".  
IF similarity of any parameter is "low" THEN graph similarity is "low".  
IF similarity of any parameter is "very low" THEN graph similarity is "very low".  
IF similarity of any parameter is "extremely low" THEN graph similarity is "extremely low".  
  
    
Then, let us consider each model separately using the Mamdani model.  
#### 6.1 Erdos-Renyi model
![](https://github.com/kseniashilova/Fuzzy-Modeling/blob/main/erdos_renyi_res.png)
#### 6.2 Geometric model
![](https://github.com/kseniashilova/Fuzzy-Modeling/blob/main/geometric_res.png)
#### 6.3 Barabasi-Albert model 
![](https://github.com/kseniashilova/Fuzzy-Modeling/blob/main/barabasi_albert_res.png)
#### 6.4 Chung Lu model 
![](https://github.com/kseniashilova/Fuzzy-Modeling/blob/main/chung_lu_res.png)
##### 6.5 Simple Geometric Chung Lu model  
![](https://github.com/kseniashilova/Fuzzy-Modeling/blob/main/geom_chung_lu_res.png)
## 7. Conclusion
## References 
