---
layout: post
title: "Continuous MC and CNN"
date: "2020-02-05"
tags: 
    - "HGCAL"
permalink: "2020/02/05/Continuous-MC-and-CNN.html"
---
<h2>Overview</h2>
因為接下來我要去參加活動，所以先快速列下這幾天我嘗試做的事情(<font style="color:f0e68c">已結束</font>)

1.3D CNN: 就如老師所說，在實際上運作的ＨＧＣＡＬ是三維的硬體，所以我們還是希望可以用3D CNN來試試看是否和實際上的三維硬體到底有什麼的差別，但誠如<a href="https://keras.io/layers/convolutional/" target="_blank">keras 3D CNN</a>所說，如果要(batch, filters, new_conv_dim1, new_conv_dim2, new_conv_dim3)五維的結果，可是目前我只有四維(缺少new_conv_dim3)，看來還要思考一下該怎麼做才能多一個維度才能執行3D CNN，（20200211)以下有<a href="https://www.machinecurve.com/index.php/2019/10/18/a-simple-conv3d-example-with-keras/">這個</a>還有<a href="https://medium.com/shashwats-blog/3d-mnist-b922a3d07334" target="_blank">這個</a>都是很好的3D MNIST用來做CNN的範例，執得細細了解
<hr>

2.Continuous energy CNN:在一月中也和老師討論過，因為我們已經做新的continuous energy，並在non-preselection 和 preselection在Original machine learning 的差別，現在我就只要用CNN training來做比較，就像以前所做的方式，但我還沒完成，目前現在進行csv file 轉成 npz 的pion 和 electron，但有可能會memory segmentation的問題，希望晚上就可以出爐
目前結論：有成功產生file:PionElectron100GeVContinResult.npz，但接下來卻出現"<span style="color:#ff0000">IOError: Failed to write to /tmp/wehuang/tmp26AydS-numpy.npy: 9601401600 requested and 9250707392 written</span>"<br/>
pion time: 3774s<br/>
electron time: 9942s<br/>
20200206 0846：現在找出問題了，應該是有<span style="color:#ff0000">memory 不夠的問題</span>，而疑似解決的方式在<a href="https://github.com/numpy/numpy/issues/5336" target="_blank">這裡</a>，而暫時的解決方案是減少到900000的pion和900000來執行看看<br/>
結果:一樣有memory error的問題QQ<br/>
有另外一個解決方案，就是用<a href="https://jennaweng0621.pixnet.net/blog/post/403784246-%5Bpython%5D-memory-error解決方法" target="_blank">python gc.collect</a>來釋放記憶體，明天早上就可證明結果
<hr>

3.Preselection in Contiuous Energy:因為在之前preselection我們都只暫時考慮"> 80GeV" 可是在continuous energy的狀況下有太多額外的event,所以我先給一個region ">80GeV & <100GeV"來看看
<hr>

4.<span style="color:#ff0000">溫故知新</span>在html中，<div class"名稱">，在.css檔案是<span style="color:#aa759f">".名稱"</span>
<hr>

<span style="color:#f0e68c">(解決)</span>5.Continuous energy preselection have some problem...:<br/>
原來我以為preselect之後就可以下降我原有的AUC image，結過並沒有!!!還是有很高的accuracy in CNN，我稍微想了一下，問題很有可能出在跟傳統的machine learning一樣，如果你在continuous energy在一開始就先cut region in 70~100GeV(pBeam)，然後再用pre-selection的話，這樣pion & electron就<span style="color:#ff0000">不那麼好分</span>，可是如果沒有pBeam cut region而直接用pre selection的話，pion & electron就變得<span style="color:#ff0000">非常好分</span>(AUC 甚至超過0.99)，所以在當務之急就是把在Writecsv下也要有範圍 70GEV< pBeam < 100GEV，在用CNN重新跑過一次
<hr>

<span style="color:#f0e68c">(衍生問題)</span>6.Preselection MC太少:<br/>
在兩層(pBeam和preselection)的cut的狀況下，MC太少導致training 和 testing的差距很大,AUC number根本不夠用，要解決的有下列兩種:
<ul>
    <li>6.1: gen 更多的MC，目前有1 million的MC,但我的lxplus的權限到期了...(一年為限)</li>
    <li>6.2: 稍微增加pBeam的valu,從70~100GeV 增加到60~130GeV</li>
</ul>
<br/>
我先用6.2來做training，結果的確accuracy也下降了，但還是希望幾天我利用lxplus的crab產生更多的MC(預計2 million events)，這樣可以增加保險
<hr>

7.把data放進MC CNN的model再train一次並看結果:
13110: Electron<br/>
14213: Pion
<ul>
    <li>7.1 100GeV Data</li>
    <ul>
        <li>7.1.1 100GeV Pion event number: <span style="color:#ff0000">162817</span></li>
        <li>7.1.2 100GeV Electron evnt number: <span style="color:#ff0000">306828</span></li>
        <span>7.1.3. Accuracy: <span style="color:#ff0000">0.566</span>
    </ul>
    <li>7.2 20GeV Data</li>
    <ul>
        <li>7.2.1 20GeV Pion event number: <span style="color:#ff0000">197318</span></li>
        <li>7.2.2 20GeV Electron event number: <span style="color:#ff0000">120109</span></li>
        <li>7.2.3 Accuracy: <span style="color:#ff0000">0.711</span></li>
    </ul>
    <li>7.3 30GeV Data</li>
    <ul>
        <li>7.3.1 30GeV Pion event number: <span style="color:#ff0000">146797</span></li>
        <li>7.3.2 30GeV Electron event number: <span style="color:#ff0000">138427</span></li>
        <li>7.3.3 Accuracy: <span style="color:#ff0000">0.620</span></li>
    </ul>
    <li>7.4 50GeV Data</li>
    <ul>
        <li>7.4.1 50GeV Pion event number: <span style="color:#ff0000">204490</span></li>
        <li>7.4.2 50GeV Electron event number: <span style="color:#ff0000">432488</span></li>
        <li>7.4.3 Accuracy: <span style="color:#ff0000"></span></li>
    </ul>
    <li>7.5 80GeV Data</li>
    <ul>
        <li>7.5.1 80GeV Pion event number: <span style="color:#ff0000">249690</span></li>
        <li>7.5.2 80GeV Electron event number: <span style="color:#ff0000">162817</span></li>
        <li>7.5.3 Accuracy: <span style="color#ff0000"></span></li>
    </ul>
    <li>7.6 200GeV Data</li>
    <ul>
        <li>7.6.1 200GeV Pion event number: <span style="color:#ff0000">258638</span></li>
        <li>7.6.2 200GeV Electron event number: <span style="color:#ff0000">233672</span></li>
        <li>7.6.3 Accuracy: <span style="color#ff0000"></span></li>
    </ul>
    <li>7.7 250GeV Data </li>
    <ul>
        <li>7.7.1 250GeV Pion event number: <span style="color:#ff0000">213846</span></li>
        <li>7.7.2 250Gev Electron event number: <span style="color:#ff0000">271826</span></li>
        <li>7.7.3 Accuracy: <span style="color:#ff0000"></span></li>
    </ul>
    <li>7.8 300GeV Data </li>
    <ul>
        <li>7.8.1 300GeV Pion event number: <span style="color:#ff0000">325841</span></li>
        <li>7.8.2 300GeV Electron evnt number: <span style="color:#ff0000">322977</span></li>
        <li>7.8.3 Accuracy: <span style="color:#ff0000"></span></li>
    </ul>
</ul>
