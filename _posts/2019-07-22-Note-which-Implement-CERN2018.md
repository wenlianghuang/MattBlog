---
layout: post
title: "一些在CERN2018 執行檔用途"
tags:
    - "HGCAL"
---
<h2>為了避免太久沒有使用的執行檔和他相對存在的folder，以下有一些有用的執行檔紀錄</h2>

<h3><span style="color:#ff0000">bundle exec jekyll server -p 4000:</span></h3>
為了重新執行MattBlog website

<span style="font-style:italic;font-weight:bold;color:#ff0000">注意:</span>在github建立的免費靜態網站中是於rails，所以要確定在現行下預設是哪一種version，若跟和當初架構網站的version不同，可以用 `rvm <your version>`來重新處理(目前可行的方法....)


<h3><span style="color:#ff0000">./OrgMl -w (ex:MC) -c (ex:nocut) -r (ex:E1E7TraRes) -d (ex:tmp) -n (ex:E1E7)</span></h3>
./OrgML 主要是為了把raw 的 file 取出 E1 , E7 , E19 的energy 放入新的root file，主要就是為了之後的./SecSquare_Layer_Classification 來做tmva的original machine learning

<h3><span style="color:#ff0000">./ReaderPO -n (ex)E1E7 -w (ex)SeedOne</span></h3>
pwd: /home/wehuang/work2/new_workspace/CMSSW_10_2_6/root6_space/HGCAL_Testing_Deep_Learning/CERNTB2018/OrgML/ReaderPODir/

Reason of Implementation: 為了要做出不同的input Data/MC和Reader of ouput data/MC(ref: 20190625-HGCAL-input-variable-record.md) input Data/MC 是放在 folder <span style="color:#ff0000">InputMCDataPlot</span>裡面之中，而Reader of output data/MC 在是放在parent folder "OrgML",ex: <span style="color:#ff0000">E1E7DataMCBDTRes.png</span>

Attention: The origin implementation is <span style="#ffff00">tmpSecReader.cc</span>, but know it can be replaced by files in ReaderDir/


<h3><span style="color:#ff0000">./SecSquare_Layer_Classification</span></h3>

pwd: /home/wehuang/work2/new_workspace/CMSSW_10_2_6/root6_space/HGCAL_Testing_Deep_Learning/CERNTB2018/OrgML/

There are four parameters in python file

<span style="font-style:italic;font-weight:bold">TMVA file:</span> It is in the TMVA_rootfile directory, ex:TMVA_Seed_One_Layer.root 
<br/>

<span style="font-style:italic;font-weight:bold">Corresponding Directory:</span> Training result directory, there are some file like overtraining_x.png, .weight.xml, .class.C
<br/>

<span style="font-style:italic;font-weight:bold">Energy root file:</span> Like E1E7, E1E19... root file
<br/>

<span style="font-style:italic;font-weight:bold">Range of layer:</span> From layer 1 to layer 28 and choose the range I want to use 
<br/>

<h3><span style="color:#ff0000">./CNNResponse -s (one or many variable)  -p(particle energy name)</span></h3>
pwd:
/home/wehuang/work2/new_workspace/CMSSW_10_2_6/root6_space/HGCAL_Testing_Deep_Learning/CERNTB2018/CNNPlotCPP

There is the ratio particle of the training output and generate plots

<h3><span style="color:#ff0000">在 folder ReaderPODir下 ./ReaderPO -n(ex:E1E7) -w(ex:Seedone)</span></h3>
pwd:
/home/wehuang/work2/new_workspace/CMSSW_10_2_6/root6_space/HGCAL_Testing_Deep_Learning/CERNTB2018/OrgML/ReaderPODir

有兩種: Whole & Indiv，如果用Whole的話可以直接使用./ReaderPO，若用Indiv的話，請使用python script的PythonScriptReaderPO.py和shell script的ReaderPOShellScript.sh
