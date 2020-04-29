---
layout: post
title: "How to solve the training can not increase accuracy"
permalink: "2020/02/27/Sovle-Problem-Training.html"
date: "2020-02-27"
tags:
    - "HGCAL"
---
<h3>Because it's hard to increase the accuracy of CNN with continuous energy include pre-selection and cut input. I try to use some solution and record them</h3>
1.Because the events number of electron is 30 times than Pion, maybe it is the problem. I try to set the number of pion equals to the number of electron: Pion:Electron == 1000000:40000<br/>

<span style="color:#ff0000;font-family:cursive;">The result:</span><code class="masthead-title">Still have  the same problem</code>

2.Except the pre-selection, I also cut the input MC at first in the continuous energy. In the previous, I didn't cut the input MC in the discontinuous, maybe it is also the problem<br/>

<span style="color:#ff0000;font-family:cursive;">The result:</span><code class ="masthead-title">I go back to the most original continuous energy(no peam and no EtotalofLayer region),the result seems that the accuracy can increase and loss decrease. However; there is some mistake, when I <span style="color:#ff0000">normalize with all the entry of their energy </span> in Pion and Electron, so I want to write down the sub title to try to solve my problems</code>
<ul>
    <li>2.1 MC energy has already unit GeV, maybe I should not use the unnecessary normalization<br/> <span style="color:#ff0000;font-family:cursive;">MC result:</span> training acc:0.9687 val_acc:0.8368 testing acc:0.932 seems good?</li>
    <li>2.2 Using pre-selection and do again<br/> <span style="color:#ff0000;font-family:cursive;">MC result:</span> training acc:0.9997 val_acc:1.0000 
    testing acc:1.000 ==><font size="5">Still have problem QQ</font></li>
    <li>2.3 Normalization in plot, unnormalization with csv file</li>
    <li>2.4 Have to check the real number of pion and electron: <br/>
    1st pion(2889),electron(3090)<br/>
    2nd pion(2889),electron(3090)<br/>
    Seems they are the same ==> Correct!</li>
    <li>2.5 Maybe I need more pion with preselection,so at first, I will rebuild my pion with 1999975</li>
    <li>2.6 Have to checke the larger real number of pion and electron: <br/>
    1st pion(5282),electron(11466)<br/>
    <span style="color:#ff0000;font-family:cursive;">MC result:</span>training: 0.9082 val_acc 0.8444 testing:0.866</li>
    <div class="bob-container">
        <div class="bob-row">
            <div class="bob-2item">
                <img alt="" src="https://user-images.githubusercontent.com/13759047/75626642-247cba80-5c04-11ea-9520-6ca1df3bde7b.png" />
                <div style="height:43px; text-align: center;">Accuracy of 200000 pion and 150000 electron</div>
            </div>
            <div class="bob-2item">
                <img alt="" src="https://user-images.githubusercontent.com/13759047/75626717-eaf87f00-5c04-11ea-9003-1df0d7aa8315.png" />
                <div style="height:43px; text-align: center;">Loss of 200000 pion and 150000 electron</div>
            </div>
        </div>
    </div>
    <img alt="" src="https://user-images.githubusercontent.com/13759047/75629140-66186000-5c1a-11ea-929e-1420934dbd68.png">
    <div style="height:43px; text-align: center;">ROC</div>
    <li>2.8 Generate more MC(3000000 pion)</li>
    <li>2.9 Beacuse pion and electron do not need to pre-select my data, so I have to use my "true" event of pion and electron <span style="color:#ff0000;font-family:cursive;">MC result(epochs = 500): </span> training: 0.9142 ,val_acc 0.9131 ,testing:0.902</li>
    <div class="bob-container">
        <div class="bob-row">
            <div class="bob-2item">
                <img alt="" src="https://user-images.githubusercontent.com/13759047/75745138-5e0f0c00-5d51-11ea-8553-c7167a2d57be.png" />
                <div style="height:43px; text-align: center;">Accuracy of 200000 pion and 150000 electron</div>
            </div>
            
        
            
            <div class="bob-2item">
                <img alt="" src="https://user-images.githubusercontent.com/13759047/75745532-8cd9b200-5d52-11ea-9438-c47418608b39.png" />
                <div style="height:43px; text-align: center;">Loss of 200000 pion and 150000 electron</div>
            </div>
        </div>
    </div>" />
                <div style="height:43px; text-align: center;">Loss of 200000 pion and 150000 electron</div>
            </div>
        </div>
    </div>

    
</ul>



3.Still try to show the CNN with its input disconinuous energy implement accuracy and loss image result.<br/>
4.Python sklearn libarary have a function <a href="https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html" target="_blank">"train_test_split"</a>, and attent to the paramter "shuffle", the "x" and "y" can shuffle <span style="color:#ff0000">togather</span>
5.Pion Normalized = 0.0174,Electron Normalized = 0.0053,multiply 1000 of normalization.