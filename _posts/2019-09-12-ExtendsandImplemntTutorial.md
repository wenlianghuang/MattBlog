---
layout: post
title: "0911 Java Tutorial Extends and Implements"
date: "2019-09-12"
tags:
    - "DiaryRecord"

---

<h3><span style="color:#D2691E">Java Extends</span></h3>
Extends 就像是 children時要加 paraent的class，也就是說，children 是包括在parent裡已有的variable, methond...也可以說children是<span style="color:#ff0000">inheritance</span>of parent.這在C/C++中已經有類似的行為，但：<br>
注意1：<span style="color:#FFD700">在JAVA中只允許單一繼承(Single Inheritance)</span><br>
注意2：Inheritance of constructor要特別多寫一個<span style="color:#FFD700">"super(variable in Father's class)"</span>，如果沒有寫的話，在compile時就會發生錯誤<br>
The code in my folder paht is: /Users/Apple/Desktop/JavaTest/ExtendsExample/src/app/ExtendExample.java
<br>
<h3><span style="color:#D2691E">Java Implement</span></h3>
但如果我們有一個parent class，但有很多不同個children class，會比較混亂，在這樣的情形下，Java產生了一個新的解決之道: <span style="color:#FFD700">Implements</span>，也就是在class下多了<span style="color:#FFD700">Interface</span>，在interface下只有method，而當childrend class extended by parent class，如果要改變原來的method，就可以比較清楚，如果沒有更改也可以繼承在parent的interface，本意應該是讓interface可以跟variable分開，也讓其中的method更多元化的利用，<a href="https://openhome.cc/Gossip/Java/Interface.html">詳情請看這個</a>