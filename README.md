# MaketsGA
Hands On Neural Network inside Metatrader

In this article, we attempt an approach to the use of architecture and modeling of deep neural networks inside metatrader 5 plataform "IN THE BOX" without external librarys.

Let's try to demonstrate how we can optimize a neural network of any dimension using genetic algorithms inside our trading platform.

We are NOT going to train a network to predict a single value (let's try our best) we are going to train a network to discover a complex trading strategy by itself without the limitation of human knowledge.


# Mandatory Literature
It is assumed that readers are familiar with the basic concepts of deep networks and financial markets. 

Attached are some interesting articles to familiarize the reader with the technology that is intended to be developed.

1.-[THIRD GENERATION NEURAL NETWORKS: DEEP NETWORKS](https://www.mql5.com/en/articles/1103).

2.-[EVALUATION AND SELECTION OF VARIABLES FOR MACHINE LEARNING MODELS](https://www.mql5.com/en/articles/2029).

3.-[RANDOM FORESTS PREDICT TRENDS](https://www.mql5.com/en/articles/1165)

4.-[MARKET THEORY](https://www.mql5.com/en/articles/1825)

# About Forex Makets and Metatrader
The Forex market is a decentralized global market of all currencies that are traded around the world. This market is the largest and most liquid in the world, with a daily trading volume in excess of 5 trillion dollars. The other stock markets in the world togethers not come close to this.

Metatrader is a popular software among individual and institutional traders. The main features that make it a reliable and popular software is that most Brokers, Market Makers (ECN) and Banks have acquired its license and offer their clients the possibility to trade with it. It also makes it possible to trade in the markets independently of the Borker without changing the platform.
Of course Metatrader incorporates a tecnical module and object-oriented programming language (in version 5) with you can develop  your own indicators and/or fully automatic trading robots, this makes Metatrader a good choice for both an individual trader and an institutional trader looking for a robust platform.

# About Quantitative Traders
Quantitative trading provides a new science or strategy to operate in the financial markets applying statistical models and in recent years models related to machine learning/deep learning.

What are we trying to do with quantitative trading? 

Usually quantitave traders download(csv,sql etc..) financial timeseries then apply a treatment to the data if necessary (normalization PCA etc...). Finally they train a network(python/R etc..) normally with the objective of reducing the error between the prediction and the real value and finally they take a decision(automatic or not) based on model single prediction value. (This sounds interesting python and r have hundreds of liberties for machine learning some of them interesting as recently google library TensorFlow)

In other words we have price for time T-1....T-n as independent variables and we try to predict a T+1 price as dependent variable.


# Motivations about MarketsGA and Quantitative Traders problems

The main problems about quantitative trader encounters when operating in real market is that they are exposed to market volatility, rapid market movements, price slippage and the constant noise produced by the randomness of the market structure itself.

This means that a quantitative trader who is dedicated to predicting a value based on past values is NOT enough to develop a successful FOREX trading system. You need a complex system that can manage the volume of the operation, the risk of it and the capital of the account (and others...).

Can you imagine to train a network of any input dimension any internal dimension and any output dimension to try to discover a full complex trading system INSIDE TRADING PLATFORM?

# Basic concepts about GA
Genetic algorithms are based on the genetic process of biologically living organisms. Where in a closed environment of X species only the strongest (or the best adapted) to the environment survive in a new species to evolve to a new specie with a mixted gens of the survivors.

Genes->Parameter to be optimized

Species->Each species contains a certain amount of genes all together offer a solution to a specific problem.

Population-->Population is a group of species all together perform a generation

Evolution->Evolution is the step that is generated between one generation and another, where there is a mixture of genes that generates new species and new species are born with a certain mutation.

Fitness function--> The fitness function is the function that will tell us how good a species is and will be used to maximize the value.

![alt text](https://github.com/nopaixx/TensorFlow-GeneticsAlgo/blob/master/GA%20grafic.jpg)

# Genetics algorithms basis Neural Netowrk weigth optimization
As indicated in the introduction of the article we will try to optimize a neural network of any input dimension any internal dimension and any output dimension. However, to facilitate the exposure we will use the simplest Neural Network structure named percepton.

![alt text](https://github.com/nopaixx/MaketsGA/blob/master/percepton.jpg)

As you probably already know, we must then find the values W1..WN that comply with the following formula

![alt text](https://github.com/nopaixx/MaketsGA/blob/master/formulapercepton.jpg)

Now we need optimize all Wn weigth using Genetics Algorithms, and we apply a binary transformatión of all weigth where all group of gene in specie represent a Wn weigth(note we initialized weigth in random way)

![alt text](https://github.com/nopaixx/MaketsGA/blob/master/wtobin.jpg)


After applying the fitness function in each species we can obtain the best species of each generation and create new species that are born through the process of random crossover based on their progenitors (plus a small mutation).

![alt text](https://github.com/nopaixx/MaketsGA/blob/master/newspecieborn.jpg)


# Loss function vs fitness function
The loss function in a machine learning represents the error between the predicted value vs. the true value, usually the objective of the neural network is to minimize the error, understanding that a minor error come to a better final result. The most common loss functions are MAE, MSE for regression problems and crossentropy for classification problems. (It's not the purpose of this document to analyze the performance of these functions).

The main difference between the gradient descent method and the genetic algorithms to optimize the weights of a neural network, is that, while in the first we must process over and over again the function of lost epoch to epoch to see how the error decreases, with the genetic algorithm we do not need to process the network any time of training simply we should run several networks (piloted by the genes of a species) and check how good is(or bad have done).

To know how good is a species we will process all the actions performed to the fitness function. The design and development of the fitness function is a more important key element for the proper functioning of the genetic algorithm and will determine the success of the complex trading system.

# Our Fitness function
The main objective of the document is the creation of a neural network optimized by genetic algorithm in order to discover a complex trading system capable of making any decision available on the platform. This includes both opening and closing trades as well as managing open trades at all times and making decisions regarding the performance of trades and capital management. For this reason our loss function will be based on:

![alt text](https://github.com/nopaixx/MaketsGA/blob/master/fitness_function.jpg)
[More info about ratio sharpe](https://es.wikipedia.org/wiki/Ratio_de_Sharpe).

In summary our fitness function tell us how good is a specie before to evolve a new population of species and our fitness function value is equal to final_balance * ratio_sharpe. I have chosen a ratio shape because in its base the ratio shape includes a risk renatability analysis based on a reference environment and we therefore want our fitness function to include a risk analysis of each investment. In summary, the more benefit based on ratio shape the better.
(sure fitness function could be improved in future)

```
fitness_function=TesterStatistics(STAT_PROFIT)*TesterStatistics(STAT_SHARPE_RATIO);

```

# Software arquitecture
-onthebox
-tradedoubles

# geneticsevolution.mqh


# speciestrader.mqh


# backtesting analisis

# Future improvements

# Conclusions















