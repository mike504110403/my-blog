---
title: "python selenium 設置及基本指令"
date: 2021-07-30T15:46:47+08:00
draft: false  # 是否為草稿?

# post thumb 標題圖片
#image: "images/post/logo.jpg"

# meta description
description: "使用selenium進行簡單自動化-爬蟲篇"

# taxonomies
categories: 
  - "Experience sharing"
  
tags:
  - "Web Automation"
  - "selenium"
  - "Python"
  

# post type
type: "post"
---

Python的selenium工具提供方便的網頁自動化功能，此篇針對簡易爬蟲的部分記錄。

#### 安裝及Browser Driver

如同Python的其他工具，selenium也能透過pip套件進行安裝，也可以使用Pycharm內的interpreter新增。

由於要使用selenium自動開啟瀏覽器，我們還需要下載對應的最新版browser driver至相應的路徑內。

為了避免繁瑣且須持續更新的下載步驟，這邊我們使用[Web Driver Manager](https://pypi.org/project/webdriver-manager/)工具，可以省下不少工作。

#### 網頁自動化操作

在selenium中，我們可以必須先引入相關的package以及command，詳細可以參考[selenium手冊](https://www.selenium.dev/documentation/en/)，例如:

```python
from selenium import webdriver  # webdriver package
from webdriver_manager.chrome import ChromeDriverManager  # wdm package
```

接下來我們可以嘗試以下指令跳轉頁面:

```python
# 使用.wdm指定driver位置
driver = webdriver.Chrome(ChromeDriverManager().install())  # 將webdriver設至變數driver

# 若未安裝wdm，也可以使用以下指令
# driver = webdriver.Chrome(executable_path="C:\\browser_drivers\\chromedriver.exe")

driver.maximize_window()  # 最大化視窗
driver.get("url1")  # 開啟指定url1
driver.get("url2")  # 跳轉至url2
driver.back()  # 回到上一頁(url1)
driver.forward()  # 回到下一頁(url2)

driver.close  # 關閉瀏覽器
```

我們也可以試著進行其他網頁操作，如點擊特定選項、輸入字元等，這裡以爬取Dcard上文章為例:

```python
from selenium import webdriver  # webdriver package
from selenium.webdriver.common.keys import Keys
from webdriver_manager.chrome import ChromeDriverManager  # drivermanager package
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait  # 引入網頁讀取條件套件
from selenium.webdriver.support import expected_conditions as EC
import time

driver = webdriver.Chrome(ChromeDriverManager().install()
driver.maximize_window()
driver.get("https://www.dcard.tw/f")

#於搜尋欄輸入文字
search = driver.find_element_by_name("query")
search.clear()  # 清空輸入欄位
search.send_keys("python")  # 輸入文字
search.send_keys(Keys.RETURN)  # enter

# 等待看板顯示後再開始取title
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.CLASS_NAME, ""))  # 選定條件有關之element
)

# 將標題放入titles list
titles = driver.find_elements_by_class_name("")  # 填入標題檔之element

# 寫出標題
for title in titles:
    print(title.text)
time.sleep(5)

# 點擊特定標籤
link = driver.find_element_by_link_text("")  #選定特定title  
link.click()

time.sleep(5)
driver.close()  # 關閉視窗
```

如上述，我們可以將特定頁面的標題寫至list，也可以點擊任一文章進行跳轉。

除此之外，我們也可以透過選定特定element進行操作，詳見[selenium手冊](https://www.selenium.dev/documentation/en/support_packages/working_with_select_elements/)

#### 總結

selenium提供了許多方便的功能讓網頁能自動化的操作，可以協助我們減少日常繁瑣的工作，對QA而言更是十分重要的工具，後續我會繼續更新selenium於測試上的相關應用。