---
layout: post
title: "Some TMVAGuide notes"
date: 2019-06-26
---

# Some note in the TMVAGuide Books
## MLP(Multilayer perceptron)
ex: factory.BookMEthod(dataloader, TMVA.Types.kMLP,'MLP','H    :!V:NeuronType=tanh:VarTransform=N:NCycles=600:Hid    denLayers=N-1,N+5:TestRate=8:UseRagulator')
```bash
NCycles: Default 3000 Description: Number of training cycles

HiddenLayers: Default N,N-1 Description: Specification of hidden layer architecture

```
## MLP ANN(Artificial Neuro Network)
```bash
| Option     | Array  | Default  | Predefine Values  | Description  |
| ---------  | ------ | -------  | ----------------  | -----------  |
| RandomSeed |   -    |  1       |          -        | Random seed for initial synapse weights (0 means unique seed for each run; default value ’1’) |
RandomSeed: Default: 1 Description: Random Seed for initial synapse weights(0 means uniquie seed for each run)
```
## BoostedFisher
ex: factory.BookMethod(dataloader, TMVA.Types.kFisher,    'BoostedFisher','Boost_Num=20:Boost_Transform=log:    Boost_Type=AdaBoost:Boost_AdaBoostBeta=0.2')
```bash
Boost_Transform: 

```

