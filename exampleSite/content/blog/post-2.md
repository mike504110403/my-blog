---
title: "MVC網頁框架--利用Flask具功能的微型網頁"
date: 2021-07-28T15:46:47+08:00
draft: false  # 是否為草稿?

# post thumb 標題圖片
#image: "images/post/logo.jpg"

# meta description
description: "紀錄python的flask套件及MVC框架概念的學習"

# taxonomies
categories: 
  - "Experience sharing"
  
tags:
  - "Web Frame"
  - "Flask"
  - "Python"
  

# post type
type: "post"
---

此篇文章為線上課程[Django + Flask 雙框架實戰](https://hiskio.com/courses/373/about)的Flask部分實作心得。

Flask為Python的網頁框架，能夠連結資料庫快速建立靜態網頁。

所謂"MVC"即為: Model、Views、Controller，將網頁的不同階段整合並分類於不同的檔案及資料夾，因此更方便於協作及管理。

#### **以下為MVC架構的概念:**

* Model -- 負責與資料庫溝通
* View -- 處理有關顯示的部分
* Controller -- 邏輯處理(路由、顯示、計算)

#### **實作上的基本流程如下:**

照官方說明安裝[Flask](https://flask.palletsprojects.com/en/2.0.x/installation/)後，建立虛擬環境並建立MVC對應資料夾，如圖:

![](/images/flask1.jpg)

"App"指的是應用程式，指的是此次架的Flask網頁，其下有"models"用於存放與功能模塊的py檔，"views"存放的為控制如何顯示的py檔，而"templates"存放views所顯示的所有網頁之html檔。

其中，router.py為此App的Controller，主導邏輯處理。

我們首先須於router.py中定義路由吉所使用的http協定，並傳至處理顯示的views資料夾中

```python
# index page
@app.route('/', methods=['GET'])  # 使用裝飾器定義路由
def index():
    return views.index()  # view去顯示根目錄(於views/user.py內撰寫
```

再由views內的function決定如何顯示，這邊我們使用 flask所導入的`render_template`指令使`views.index()`顯示index.html。

```python
# Render the index page
class views:
    def index():
        return render_template('users/index.html')  # 將template 內的index.html 渲染出來
```

以上便是flask網頁框架的基本概念，而功能模塊的部分(如資料庫連結、網頁跳轉)等。

即是在models中的py檔進行撰寫，並注意數值及參數地傳出及傳入。

此篇不詳加介紹，若讀者有興趣，可以參考我的github上關於此次課程的[實作](https://github.com/mike504110403/flask_demo_git)。


#### **總結:**
flask提供了許多套件簡化了網頁的開發，MVC框架亦讓協作開發的分工與管理更加容易。

對於要開發簡單功能的靜態網頁而言，實為一個方便的工具，若之後繼續深入摸索，我會再新增文章詳細介紹flask有關的套件。

