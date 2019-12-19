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
因為在網路上(官方也有)有很多的方式來下載Mongo，在此就不多贅述，我們先從<a style=color:#acff59; href="https://mlab.com" target="_blank">mLab的網站開始</a>:
<ul style="list-style-type:circle;">
    <li>Sign Up or Log In</li>
    <li>Choose free database(512MB)</li>
    <li>Build your first cluster</li>
    <li>Create your first database user</li>
    <li>Whitelist your IP address(I use 0.0.0.0/0</li>
    <li>Load Sample(Option)</li>
    <li>Connect to your cluster</li> 
</ul>

<br><br>
Fig.1是我generate一個新的database
![Mongo_result_image1](https://user-images.githubusercontent.com/13759047/71159668-0ea45e00-2281-11ea-8419-c3cfb302b33c.png)
<br/>

接下來可以在terminal 執行 <code>mongo "mongodb+srv://cluster0-ejyss.mongodb.net/test" --username WenLiangMatt</code>，再輸入密碼就可以進入mongo

<span style="color:#ff0000">注意1</span>：在log in remote mongo中有個"Error while trying to show server startup warnings: user is not allowed to do action [getLog] on [admin.]" 雖然最後還是成功進入mongo並寫入各種的資料,但不是很確定有其他的問題

<span style="color:#ff0000">注意2</span>：雖然他有512MB的免費資料庫，但一產生就用掉344MB,是不是在final project最後資料庫用盡，還有待觀察

<span style="color:#ff0000">注意3</span>：盡量在mongo就產生database和table，其他的細節在可以留在pymongo

以下有幾個可以在mongo下執行:
<ul style="list-style-type:circle">
    <li>use "database name" : create database</li>
    <li>show dbs: List all databases.</li>
    <li>show collections:show the table in database</li>
    <li>db.Dropdatabase(): delete database</li>
    <li>db.[table].* : any implementation in the specific table of its database</li>
    
</ul>