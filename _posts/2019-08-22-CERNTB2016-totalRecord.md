---
layout: post
title: "所有的CERNT2016報告紀錄事項"
date: 2019-08-22
tags:
    - "DiaryRecord"
---
<br>
<h1 style="color:#ff0000;font-weight:bold">先用中文把研究的過程和經驗寫下來，然後再用<a href="https://www.xm1math.net/texmaker/" style="font-style:italic">texmaker</a>用英文轉換成我最後的論文</h1>
<br>

從2018/09開始，我們已經知道在2016 CMS為了要準備蓋出新的加速器(L3)而先用試用<span style="color:rgb(255,210,0)">HGCAL 六角形</span>，
然後實際打入以後的情形做出了解和判斷。
可是如果每次打入HGCAL似乎非常浪費時間和金錢，是否先用MC產生出適合的particle，然後利用Deep Learnging的方式來train出適合的particle，
之後再用比較簡單的方式用實際的data去打入六角形HGCAL，比對Data和MC的差別，之後再繼續調整，因為兩者之間並沒有誰是絕對的，
不管是Data或Monte Carlo。


而接下來，我要找一個適合的deep learning method可以seperate原來的在Monte Carlo 的 particles。
跟真實中要打入HGCAL一樣，在deep learning也是要用圖像的方式來seperate，所以我們選擇了
<a href="https://en.wikipedia.org/wiki/Convolutional_neural_network" style="color:rgb(255,210,0)">Convolution Neural Network(CNN)</a>(詳細之後再說明)，
但在Keras,Tensorflow..的相關<span style="color:#ff0000">high-level neural networks API</span>，
都是使用正方的圖形，而沒辦法使用在HGCAL裡獨特的六角形，所以在有限的情況下，將六角形和其中的particle energy 轉變成14x14的正方形圖形，
但原先的六角形是比14x14的正方形還來得小，因此補上energy 為零的格點，產生之後要來training的圖片(see. Fig1)，而在準備的過程中，
因為在2016CMS建立的monte carlo和 Data beam to the HGCAL較為稀少，只有完整的electron data energy 20GeV, 32GeV, 70GeV, 100GeV, 150GeV, 200GeV, 250GeV. 
electron monte carlo energy 20GeV, 32GeV, 70GeV,100GeV,125GeV,200GeV,250GeV，還有少部分的 pion data energy 150GeV和 pion monte carlo energy 125GeV。


接下來就要把14x14正方形的圖放入Convolution Neural Networks進行，因為在2016時我們預計產生的實驗型HGCAL有8個layer(Fig. 1)，
當然之後會產生更多的layer，但現在我們就先利用目前的8layer來進行training。而有另外一件事執得注意，雖然在市面上最流行的neural network API是Keras 和 Tensorflow，
但Tensorflow下要使用 CNN method，image最多只能用3 layer(RGB)來training，而Keras上並無限制。在要beam to HGCAL不管是monte carlo 或 data都是完整的 8 layer，所以決定使用Keras來做完整的training。
但正如 Table 1.上所說，

