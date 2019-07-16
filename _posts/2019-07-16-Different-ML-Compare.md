---
layout: post
title: "ML Comparing Records"
date: 2019-07-16
tags:
    - "HGCAL"
---
<br>
Record some different Machine Learning and try to see that it can display the unusual peak 

first we see the origin training result of BDT

<h2>
    <span style="color:rgba(0,0,0,0.7)">E1E7 Results:</span>
</h2>
![E1E7DataMCBDTRes](https://user-images.githubusercontent.com/13759047/61263133-69a9c480-a7ba-11e9-99d5-66976a1c80db.png)
we can refer to the [Input Variable Record](https://wenlianghuang.github.io/MattBlog/2019/06/25/HGCAL-input-variable-records.html) and find the input MC and Data can separate very well. 
Although it is not 100%, we guess that the problem is not input Data and MC, so I tranform the problem to the training method.Common name: <span id="target" style="color:rgba(255,0,0,1)">Machine Learning</span>

There are several Machine Learning mehtod below I try to disappear the peak of E1/E7

<span style="color:rgba(255,0,0,0.7)">Fisher type:</span><br>

| Type | Simpe Description | Noted |
|------|-------------------|-------|
|[Fisher](https://en.wikipedia.org/wiki/Linear_discriminant_analysis)|||
|BosstedFisher|||

<img src="https://user-images.githubusercontent.com/13759047/61274506-87892080-a7de-11e9-9018-e96429fde550.png" title="Fisher" width="500px" height="400px" class="inline-block">
<img src="https://user-images.githubusercontent.com/13759047/61274504-87892080-a7de-11e9-9fdc-2a71754b9704.png" title="BoostedFisher" width="500px" height="400px" class="inline-block">
<span style="color:rgba(255,0,0,0.7)">MLP</span>

| Type | Simple Description | Noted |
|------|-------------------|--------|
|[MLP](https://en.wikipedia.org/wiki/Multilayer_perceptron)|||
|MLP ANN|||

<img src="https://user-images.githubusercontent.com/13759047/61274510-8821b700-a7de-11e9-8c64-3c64865df1d2.png" title="MLP" width="500px" height="400px" class="inline-block">


<span style="color:rgba(255,0,0,0.7)">BDT</span>

| Type | Simple Description | Noted |
|------|--------------------|-------|
|[BDT](https://en.wikipedia.org/wiki/Boosting_(machine_learning))|||
|[BDTG](https://en.wikipedia.org/wiki/Gradient_boosting)|||

<img src="https://user-images.githubusercontent.com/13759047/61274502-86f08a00-a7de-11e9-97b5-e0dc037b77ab.png" title="BDT" width="500px" height="400px">
<img src="https://user-images.githubusercontent.com/13759047/61274503-87892080-a7de-11e9-8e38-4740a0c40f0b.png" title="BDTG" width="500px" height="400px">


<span style="color:rgba(255,0,0,0.7)">DNN</span>

| Type | Simple Description | Noted |
|------|--------------------|-------|
|[DNN](https://en.wikipedia.org/wiki/Deep_learning)|||

<img src="https://user-images.githubusercontent.com/13759047/61274505-87892080-a7de-11e9-9a21-880ade3992c9.png" title="DNN_CPU" width="500px" height="400px">

<a href="https://wenlianghuang.github.io/MattBlog/2019/06/25/HGCAL-input-variable-records.html">refer to 0625 diary</a>
