---
layout: post
title: "20190926 How to build New MC"
date: 2019-09-26
tags:
    - "HGCAL"
permalink:
---

<h3>
    <a name="CMSSW10_6_0_pre4">Build New CMSSW 10 6 0</a>
</h3>
<a href="https://twiki.cern.ch/twiki/bin/viewauth/CMS/HgcalSimulation#Explanation_about_the_xml_files" target="_blank">Related WebSite</a>

SLC = "Scientific Linux CERN" 

<span style="color:#ff0000">WARNING:</span> Developer's area is created for architecture slc7_amd64_gcc700 while your <span style="color:#ff0000">current OS is SLC6.</span>
暫時解決之道：ntugrid5 is only OS SLC6,<span style="color:#ff0000">先用lxplus(他有 OS slc7)</span>

<h3>HGCalTBCERN170_ele_E100_cfg.py:</h3>
    line 26: process.maxEvents = cms.untracked.PSet(
        input = cms.untracked.int32(10)
    )
    line 64: process.TFileService = cms.Service("TFileService",fileName = cms.string("TBGenSim.root"))
    line 90: PartID = cms.vint(32) ---Electron

    Question: <span style="color:#ff0000">If the number of events in one file is too many?</span>

接下來我討論很多該如何寫自己的namespace of c/c++ 跟 makefile 的一些語法概念：
<br>
<a href="http://maxubuntu.blogspot.com/2010/02/makefile.html"><span style="color:#ff0000">makefile</span></a>
>wildcare: 在folder中去找所有的file，ex: .cc, .h ...<br>
notdir:把原先的subfolder通通拿掉，只留單純的file<br>
patsubst:替換，例如從.cxx 到 .o<br>