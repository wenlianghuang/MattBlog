---
layout: post
title: "2019/09/06coding瑣事"
date: "2019-09-06"
---

<div class="ThemeinArticle">
HGCAL</div>
>1.先用Etotal of each layer畫出histogram 的 image，接著做preselection，然後在將layer1 ~ layer28 的 variable 做training.<br>
2.根據老師的說法，electron很快就死在layer下並留下record，所以Eshower大約從0.8~1，而pion則可能飛比較遠，distribution也較為寬廣<br>
3.天祥有提到，在E1/E7中的E1不是在hexagon的正中心，而是energy最大的點當成E1(Eseed)，向外ring發展<br>
4.擬定要寄個Andreas請他幫我generate量個多的monte carlo（量而已，其餘不變)，然後老師修改，我再寄出去<br>
5.今天HGCal beam test meeting討論到如果E1 & E7 都為<span style="font-weight:bold;color:#ff00ff">0</span>時，E1/E7應該設為0 or 1，昱潭給了一個很好的建議，他說再Belle E1 和 E7 如果都是0的話，你可以將E1/E7 value設為 <span style="font-weight:bold;color:#ff00ff">-999</span>因為他並不是在0~1，事實上beam test 完全沒有留在hexagon layer留下痕跡，在這樣的狀況下或許會有比較好的training結果，明天可以跟老師討論一下<br>
6.目前我拿到的完整的monte carlo 只有<span style="font-weight:bold;color:#ff00ff">8To17Oct_withMCP and noSmearingSamples</span><br>

<div class="ThemeinArticle">jekyll
<br>
<a href="https://tingtinghsu.github.io/blog/articles/2018-08-25-github_jekyll_blog" target="_blank">1.快速建構靜待網站</a> 和 <a href="https://tingtinghsu.github.io/blog/articles/2018-12-26-change_them_for_jekyll_blog" target="_blank">更換jekyll主題</a><br>
<a href="https://blog.hubspot.com/marketing/jump-link-same-page" target="_blank">2.連結特定line of website</a><br>
<a href="https://github.com/samanyougarg/hanuman" target="_blank">3.我要建立一個新的jekyll 靜態網站</a><br>
<a href="https://stackoverflow.com/questions/54087856/cant-find-gem-bundler-0-a-with-executable-bundle-gemgemnotfoundexceptio" target="_blank">4.(Question and Solution) can't find gem bundler (>= 0.a) with executable bundle (Gem::GemNotFoundException) during bundle install with gem</a><br>
<a href="https://andy6804tw.github.io/2019/01/04/git-remove-remote/" target="_blank">5.git remote version and remote remove</a><br>
</div>
<br>
<div class="ThemeinArticle">Java tutorial
<br>
<a href="https://www.w3schools.com/java/java_packages.asp" target="_blank">1.How to use package in Java</a><br>
<a href="https://openhome.cc/Gossip/JavaEssence/PackageAndModifier.html" target="_blank">2.package 與存取修飾</a><br>
<a href="https://www.javatpoint.com/online-exam-project-in-java-swing-without-database" target="_blank">3.Example OnelineTest<span style="color:#ff0000">(已完成 20190918刪除)</span></a><br>
<a href="https://www.wibibi.com/info.php?tid=240" target="_blank">4."a href" syntax and example</a><br>

5.今天有練習extends, implements,ScrollPane...，明天再詳細解<br>
</div>