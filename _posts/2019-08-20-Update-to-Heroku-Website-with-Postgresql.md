---
layout: post
title: "在Postgresql下如何上傳Heroku website?"
date: 2019-08-20
tags:
    - "RailsRecord"
---
<br>
自從泰北回台灣以後，我就一直想要把local的網站丟到Heroku實際上的website，但問題是：在local上是利用<a href="https://www.sqlite.org/index.html" target="_blank" style="color:#ff0000">SQLite3(sqlite3)</a>，如果要上傳Heroku的話，splite3沒有辦法執行，一定要<a href="https://www.postgresql.org" target="_blank" style="color:#ff0000">PostgreSQL(pg)</a>才能上傳，而安裝和執行PostgreSQL有以下幾個步驟。

1.在一開始rails new 時就要多加 database(-d) = postgresql,確保database system 是用PostgreSQL 而不是 SQLite 

2.但為了檢視postgresql 和 sqlite的差別，我們還是將 "gem sqlite3" 放入Gemfile中的development: :test do 裡面

3.在Gemfile中開一個 "group :production do"，裡面用"gem pg"來產生一個postgresql

4.<a style="color:#ff0000">注意: </a> 如果在這時候利用localhost來執行本機的website，會看到"fe_sendauth: no password supplied"這樣的error，且如果利用"rails db:migrate"來先處理資料表，會得到類似的結果。原因是postgresql 會要求內部要先產生<a style="color:#ff0000">username & password</a>，不然他就無法繼續。

5.<a href="https://www.youtube.com/watch?v=A72L2mGRPQU" target="_blank">先來看一下相關的影片</a>
> 1.Using brew install postgresql來安裝(type is 11.4 here)
<br>
  2.先用 "sudo su"來更改裡面的 "/Library/PostgreSQL/11/data/pg_hba.conf，把<span style="text-decoration:underline">md5</span>改成<span style="text-decoration:underline">trust</span>
  ![pg_hba_screenshot](https://user-images.githubusercontent.com/13759047/63325528-ea7d5280-c35c-11e9-94bf-5ada4363680b.png)
  3.Using <a href="https://serverfault.com/questions/110154/whats-the-default-superuser-username-password-for-postgres-after-a-new-install" target="_blank">"sudo -u postgres psql postgres"</a>進入postgresql 的 interpretor
<br>
  4."create role `your username` with creatdb login password `your password`" 在postgresql產生了username 和 password，並用 "\du"來看 database
</br>
  5.將config/database.yml裡的development和test他們的username and password重新寫進去裡面

6.用"bin/rails db:migrate"來處理model和database之間的對應，接者用"bin/rails server"來執行local server

7.用git來add & commit，接著用"heroku create"來create new free website，最後再用git push heroku master來上傳heroku的github


