---
layout: post
title: "New code of makePlotsPrepare.cxx"
permalink: "2020/02/21/makePlotsPrepare.html"
date: "2020-02-21"
tags: 
    - "HGCAL"
---

ene = simHitCellEnEE->at(ihit) //in GeV MC

ene = rechit_energy->at(ihit)*ESCALE //in MIP Data

for MC: hit_Rawenergy[i] = ene //in GeV 
for Data: hit_Rawenergy[i] = ene*ENEPERMIP //in GeV

normalization = ``$ y=\sum_{i=1}^n g(x_i) $``