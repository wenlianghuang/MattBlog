---
layout: post
title: "Some TMVAGuide notes"
date: 2019-06-26
tags:
    - "HGCAL"

---

# Some note in the TMVAGuide Books
## MLP(Multilayer perceptron)
ex: factory.BookMethod(dataloader, TMVA.Types.kMLP,'MLP','H    :!V:NeuronType=tanh:VarTransform=N:NCycles=600:Hid    denLayers=N-1,N+5:TestRate=8:UseRagulator')

| Options | Array | Default | Predefine Values | Description |
| ------ | ------ | ------- | ------ | ------- |
| NCycles | - | 500 | - | Number of training cycles |
| HiddenLayers | - | N,N-1 | - | Specification of hidden layer architecture |


## MLP ANN(Artificial Neuro Network)
ex: factory.BookMEthod(dataloader, TMVA.Types.kMLP,'MLPANN','H    :!V:NeuronType=tanh:VarTransform=N:NCycles=600:Hid    denLayers=N-1,N+5:TestRate=8:UseRagulator')

| Option     | Array  | Default  | Predefine Values  | Description  |
| --- | --- | --- | --- | --- |
| RandomSeed |-|1|-| Random Seed for initial synapse weights(0 means uniquie seed for each run) |
| HiddenLayers | - | N,N-1 | - | Specification of hidden layer architecture | 
| ValidationFactor | - | 0.5 | - | Fraction of events in trainning tree used for validation |
| LearningMethod | - | Stochastic | Stochastic,<br>Batch,<br>SteepestDescent,<br>RibierePolak,<br>FletcherReeves,<br>BFGS| Learning Method |

RandomSeed: Default: 1 Description: Random Seed for initial synapse weights(0 means uniquie seed for each run)

## BoostedFisher
ex: factory.BookMethod(dataloader, TMVA.Types.kFisher,    'BoostedFisher','Boost_Num=20:Boost_Transform=log:    Boost_Type=AdaBoost:Boost_AdaBoostBeta=0.2')
```bash
Boost_Transform: 

```


