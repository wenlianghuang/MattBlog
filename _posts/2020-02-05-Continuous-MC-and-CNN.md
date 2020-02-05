---
layout: post
title: "Continuous MC and CNN"
date: "2020-02-05"
tags: "HGCAL"
---
<h2>Overview</h2>
因為接下來我要去參加活動，所以先快速列下這幾天我嘗試做的事情
1.3D CNN: 就如老師所說，在實際上運作的ＨＧＣＡＬ是三維的硬體，所以我們還是希望可以用3D CNN來試試看是否和實際上的三維硬體到底有什麼的差別，但誠如<a href="https://keras.io/layers/convolutional/" target="_blank">keras 3D CNN</a>所說，如果要(batch, filters, new_conv_dim1, new_conv_dim2, new_conv_dim3)五維的結果，可是目前我只有四維(缺少new_conv_dim3)，看來還要思考一下該怎麼做才能多一個維度才能執行3D CNN

2.Continuous energy CNN: 在一月中也和老師討論過，因為我們已經做新的continuous energy，並在non-preselection 和 preselection在Original machine learning 的差別，現在我就只要用CNN training來做比較，就像以前所做的方式，但我還沒完成，目前現在進行csv file 轉成 npz 的pion 和 electron，但有可能會memory segmentation的問題，希望晚上就可以出爐
目前結論：有成功產生file:PionElectron100GeVContinResult.npz，但接下來卻出現"<span style="color:#ff0000">IOError: Failed to write to /tmp/wehuang/tmp26AydS-numpy.npy: 9601401600 requested and 9250707392 written</span>"這樣的問題，我會在睡覺前<span style="color:#ff0000">重新implement一次</span>，明天早上再看結果

pion time: 3774s
electron time: 9942s