---
layout: post
title: "New code of makePlotsPrepare.cxx"
date: "2020-02-21"
tags: 
    - "HGCAL"
---

ene = simHitCellEnEE->at(ihit) //in GeV MC

ene = rechit_energy->at(ihit)*ESCALE //in MIP Data

for MC: hit_Rawenergy[i] = ene //in GeV 
for Data: hit_Rawenergy[i] = ene*ENEPERMIP //in GeV

normalization = 
:blush: