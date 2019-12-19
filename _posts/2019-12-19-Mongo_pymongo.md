---
layout: post
title: "20191219 Mongo and pymongo"

---
<h2>Overview</h2>
為了完成<span style="color:#ff0000">計算機網路</span>Final project 的 <span style="color:#acff59">CN_cnMessage</span>，以下有四點是當初助教有要求的項目：
<ul style="list-style-type:circle;">
    <li><span style="background-color:#ff0000">Registration</span></li>
    <li>Messaging</li>
    <li>File transfer</li>
    <li>UI</li>
</ul>
我是負責第一部分的Registration，在language python 已經完成<a href=https://github.com/wenlianghuang/Computer-Network-Final-Project/blob/my-own-code/GUI/RegistrationGui.py target="_blank" style="color:#acff59">大部分的結果</a>，但在最後一部分想要把帳號密碼丟到資料庫上是一個比較頭痛，最後在group決定，要用
<a style=color:#acff59;font-weight:bold href="https://api.mongodb.com/python/current/" target="_blank">pymongo</a>(python+ mongo)，而我在網路上看到mLab 的 free database(512MB)，以下我就針對mongo和pymongo來說明並記錄

<h2>Mongo</h2>