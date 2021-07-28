---
title: "免費個人網站架設--利用 Hugo & GitHub Page"
date: 2021-07-25T15:46:47+08:00
draft: false  # 是否為草稿?

# post thumb 標題圖片
#image: "images/post/logo.jpg"

# meta description
description: "記錄我的第一個Blog的製作過程~"

# taxonomies
categories: 
  - "Experience sharing"
tags:
  - "Web Frame"
  - "GitHub page"

# post type
type: "post"
---

在程式領域中，以Github和個人Blog紀錄所學是十分常見的。對於剛踏入這個領域的我而言，一個能夠快速架站的Hugo非常合我的胃口。



#### 以下為我認為符合我需求的幾個理由:

###### **方便且快速** 

   Hugo官網有提供他人所製作的主題，可以依個人喜好下載後再做修改，省下相當多時間，同時也降低了製作門檻。   

###### **官方文件清楚** 

   若想製作符合自己需求的網頁版型，可以在官網查詢相對應的功能該如何撰寫，並適時補足html的基礎，對於網頁開發的初學者相對友善。

###### **免費**

   這個應該不用多說了XD


關於架設的步驟，小弟這邊就不獻醜了，大家可以參考以下文章:

[為了 SEO！我離開了 Medium，改在 GitHub 上自架個人網站](https://kucw.github.io/blog/2021/1/from-medium-to-github/)


實際上這個網站跟文章也是依照上列文章作者'Kucw'在Hahow上的課程一步步實作出來的。以下就暫且依照實作步驟分享實作心得:

##### **一、 環境建置及主題下載**

要使用Hugo及Github pages架設網站，首先創建Github帳號，並前往[Hugo](https://github.com/gohugoio/hugo/releases)下載並安裝與個人電腦對應的版本，解壓縮後拖曳出'exampleSite'資料夾，再將其他資料夾放入'exampleSite'資料夾，並於內新增一個'themes'資料夾。

同時下載自己喜歡的[主題](https://themes.gohugo.io/)
'themes'資料夾。值得一提的是，不同的主題所支援的功能可能會有差異，不熟悉html的讀者需多加注意，或是可以依照官方文件的提示加入對應的功能。

##### **二、 個人化設定**

針對資料夾內的'config.toml'編輯，修改對應的編碼，存檔後於'cmd'內執行`hugo server`，個人網站即在locall host運行了。不過目前只在個人的電腦上運行，其他人仍無法看到。

##### **三、 與他人分享個人網站**

在完成個人網站能成功顯示後，我們於'cmd'執行`hugo`，即可獲取此網站的程式碼資料，該資料會存在'public'資料夾。

將該資料夾上傳至Github轉成個人網站。這裡需特別注意，若要使用Github pages轉換網站，repo有限制的格式，須為'帳號.github.io'。

#### **總結**

Hugo為十分方便的架站工具，大部分的操作經過一兩次就能熟悉，html門檻也相對較低，不過若想透過Hugo建立個人風格強烈的網站，仍需摸索。

作為踏入這個領域的第一步，在撰寫這篇文章的同時，本人尚未深入學習html，希望能隨著學習的過程慢慢補足。

