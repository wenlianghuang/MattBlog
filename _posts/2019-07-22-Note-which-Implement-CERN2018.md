---
layout: post
title: "一些在CERN2018 執行檔用途"
tags:
    - "HGCAL"
---
<br/>

<h3><span style="color:#ff0000">bundle exec jekyll server -p 4000:</span></h3>
為了重新執行MattBlog website


<h3><span style="color:#ff0000">./ReaderPO -n (ex)E1E7 -s (ex)SeedOne</span></h3>
pwd: /home/wehuang/work2/new_workspace/CMSSW_10_2_6/root6_space/HGCAL_Testing_Deep_Learning/CERNTB2018/OrgML/ReaderPODir/

Reson of Implementation: 為了要做出不同的input Data/MC和Reader of ouput data/MC(ref: 20190625-HGCAL-input-variable-record.md)

Attention: The origin implementation is <span style="#ffff00">tmpSecReader.cc</span>, but know it can be replaced by files in ReaderDir/

<h3><span style="color:#ff0000">./SecSquare_Layer_Classification</span></h3>

pwd: /home/wehuang/work2/new_workspace/CMSSW_10_2_6/root6_space/HGCAL_Testing_Deep_Learning/CERNTB2018/OrgML/

<h4>There are four parameters in python file:</h4><br/>
TMVA file: It is in the TMVA_rootfile directory, ex:TMVA_Seed_One_Layer.root 
<br/>
<br/>
Corresponding Directory: Training result directory, there are some file like overtraining_x.png, .weight.xml, .class.C
<br/>
<br/>
Energy root file: Like E1E7, E1E19... root file
<br/>
<br/>
Range of layer: From layer 1 to layer 28 and choose the range I want to use 
<br/>
<br/>

<h3><span style="color:#ff0000">./CNNResponse -s (one or many variable)  -p(particle energy name)</span></h3>
pwd:
/home/wehuang/work2/new_workspace/CMSSW_10_2_6/root6_space/HGCAL_Testing_Deep_Learning/CERNTB2018/CNNPlotCPP

There is the ratio particle of the training output and generate plots

