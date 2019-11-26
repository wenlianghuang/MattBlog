---
layout: post
title: "20190926 How to build New MC"
date: 2019-09-26
tags:
    - "HGCAL"
permalink:
---

<h3>
    <a name="CMSSW10_6_0_pre4">Build New CMSSW 10_6_0</a>
</h3>
<a href="https://twiki.cern.ch/twiki/bin/viewauth/CMS/HgcalSimulation#Explanation_about_the_xml_files" target="_blank">Related WebSite</a>

SLC = "Scientific Linux CERN" 

<span style="color:#ff0000">WARNING:</span> Developer's area is created for architecture slc7_amd64_gcc700 while your <span style="color:#ff0000">current OS is SLC6.</span>
暫時解決之道：ntugrid5 is only OS SLC6,<span style="color:#ff0000">先用lxplus(他有 OS slc7)</span>

<h2><a href="https://github.com/cms-sw/cmssw"><span style="color:#ff0000">CMSSW github</span></a></h2>
<h3>HGCalTBCERN170_ele_E100_cfg.py:</h3>
    
    line 26: process.maxEvents = cms.untracked.PSet(
        input = cms.untracked.int32(10)
    )

    line 64: process.TFileService = cms.Service("TFileService",fileName = cms.string("TBGenSim.root"))
    
    line 90: PartID = cms.vint(32) ---Electron

    Question: If the number of events in one file is too many?
接下來我討論很多該如何寫自己的namespace of c/c++ 跟 makefile 的一些語法概念：
<br>
<a href="http://maxubuntu.blogspot.com/2010/02/makefile.html"><span style="color:#ff0000">makefile</span></a>
>wildcare: 在folder中去找所有的file，ex: .cc, .h ...<br>
notdir:把原先的subfolder通通拿掉，只留單純的file<br>
patsubst:替換，例如從.cxx 轉換為 .o<br>
<span style="color:#ff0000">注意：</span>在makefile中每有辦法像是*.cc,*.o...所有的file在subfolder狀況下轉換，你只能一個一個來轉換<br>
<span style="color:#ff0000">.PHONY: </span> 為了避免目標和檔名有所重疊，也就是不會試圖去查詢一些隱含規則。ex: clean 是makefile中原本就存在的，但如果我們在makefile中多寫一次clean，那當我們用"make clean"時，就沒辦法rm想要的file，而利用.PHONY: clean就可以避面這樣的衝突<br/>

2019/10/02 00:26

特別注意，在很久之前，因為TBGenSim.root有些particle數量太多導致本身的server會自動quit，而我曾經在把數量在切個更小，但我現在完全想不出到底是在寫什麼...

雖然還沒有完全了解我原來寫的是什麼，但可以猜測的是，我是把output100GeV.root 切成 五個小份等之後在真的要train electron和pion時再合併起來
發現!!原來的TBGenSim{}.root實在切割時並沒有原先的內容input切割的file
寫到PreSplitTFile function 就會發生segmentation fault的問題，明天繼續 10/02發現我原先寫的code只能適用再Data,（ex:rechit_direct,event...)在MC上都沒有，當然會有segmentation fault的問題orz

2019/10/01 17:20

原先以為在makePlots.cxx在code上面有問題(和8 layer的makePlots.cxx相同)但後來發覺從line 698 ~ line 709其實和我現在做實驗上其實目前沒有關聯，所以可以先跳過

10/03<br/>
先暫時把一些未完待續的website:
><a href="https://stackoverflow.com/questions/4181703/how-to-concatenate-string-variables-in-bash" target="_blank">string variable in Bash</a><br/>
<a href="http://zake7749.github.io/2015/03/17/SocketProgramming/" target="_blank">TCP Socket Programming 學習筆記</a><br/>
<a href="https://www.geeksforgeeks.org/operator-overloading-c/" target="_blank">Operator Overloading note</a><br/>
<a href="https://root.cern.ch/how/how-quickly-inspect-content-file" target="_blank">Some useful implementation for root</a><br/>
<a href="https://www.itread01.com/p/160037.html" target="_blank">linux下的shell運算</a><br>
<a href="https://root.cern.ch/function-integration" target="_blank">Function Integration for Root</a><br>

sed -i '2s/'Fuck'/'Ha'/g' ThankandFuck.txt

<a href="https://root.cern/doc/master/index.html" target="_blank">Root Reference</a><br>
nslookup<br>
condor_submit tmpSUB.SU<br>