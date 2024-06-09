title: 版型管理
author: Timothy
tags:
  - HTML
  - CSS
categories:
  - web-layout
date: 2024-06-03 22:15:00
description: 掌握關鍵知識，就能規劃出精準到位的版型
cover: https://images.unsplash.com/photo-1540612597331-63c67ea382fc?q=80&w=1780&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
---
章節重點：

* HTML 元素的容器特性
* 盒模型
* 排版實務觀念

## 前置環境

* 建立並載入 HTML、CSS 檔案
* [Reset CSS](https://meyerweb.com/eric/tools/css/reset/)：override user agent stylesheet
* 熟練 [Emmet](https://docs.emmet.io/cheat-sheet/)
* 參考[練功菜單](https://hackmd.io/iE6mxohOS-ujKU398Ewk1w)多加練習
* HTML structure

  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
    </head>

    <body>
      <h1>This is a heading</h1>
      <p>This is a paragraph</p>
    </body>
  </html>
  ```

### HTML 常用標籤

* heading

  ```html
  <h1>Heading level 1</h1>
  <h2>Heading level 2</h2>
  <h3>Heading level 3</h3>
  <h4>Heading level 4</h4>
  <h5>Heading level 5</h5>
  <h6>Heading level 6</h6>
  ```

* paragraph

  ```html
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
  ```

* image & relative URL

  ```html
  <img src="./images/google-logo.png" alt="Google logo">
  ```

* image & absolute URL

  ```html
  <img src="https://cdn.usbrandcolors.com/images/logos/google-logo.svg" alt="Google logo">
  ```

* hyperlink

  ```html
  <a href="https://www.google.com" target="_blank">前往 Google 首頁</a>
  ```

* list & list item

  ```html
  <ul class="menu">
    <li>beef</li>
    <li>pork</li>
    <li>chicken</li>
  </ul>
  ```

### CSS 選取器

* HTML tag selector
  * `h1`、`p`、`img`、`a`、`ul`
* class selector
  * `.container`、`.header`、`.menu`、`.main`、`.footer`
* pseudo-class selector
  * `a:link`
  * `a:visited`
  * `a:hover`
  * `a:focus`
  * `a:active`

## HTML 元素的容器特性

* 網頁元素的排版，都和**容器的設計**有關
* 網頁元素的佈局，可以區分為外容器（container）與內元件（item）兩種性質
  * 範例網站：[Yahoo 首頁](https://tw.yahoo.com/)、[Yahoo 新聞](https://tw.news.yahoo.com/)
* 網頁元素都有預設的 `display` 屬性，常見的屬性值為**區塊元素**（block-level element）與**行內元素**（inline element）兩種

### 區塊元素

* 盡可能佔滿父層容器的寬度
* 可以調整元素的寬度與高度
* 元素總是從新的一行開始佈局
* 例子：`<h1>` - `<h6>`、`<p>`、`<ul>`、`<li>`、`<div>`

### 行內元素

* 只佔據元素內容需要的寬度
* 不能調整元素的寬度與高度
* 元素不會從新的一行開始佈局
* 例子：`<a>`、`<img>`、`<input>`、`<textarea>`、`<span>`

## 盒模型

每個 HTML 元素，都可以視為一個盒子，設定 `width` 和 `height` 來調整盒子的寬度與高度，用盒模型來表示「元素在瀏覽器頁面上，所佔據的空間範圍」。

一個元素所佔據的空間範圍，是由四個層層包裹的矩形所構成，由內而外分別是「content-box（藍色）、padding-box（綠色）、border-box（黃色）、margin-box（橙色）」

![box model](https://imgur.com/4WvZ19Z.png)

### 外邊距（margin）

margin 是用來設定元素與其他元素之間的距離。

從盒模型的角度來看，邊框（border）以外的空間皆屬於 margin 的空間範圍。

### 內邊距（padding）

padding 是用來設定元素內容（content）與 border 之間的留白空間，避免元素內容緊貼於 border。

從盒模型的角度來看，元素內容至 border 以內的空間皆屬於 padding 的空間範圍。

### box-sizing

box-sizing 是用來**設定盒模型的計算方式**，
也就是設定 `width` 和 `height` 作用的空間範圍。

box-sizing 有兩種屬性值，一種是預設值 **`content-box`**，`width` 和 `height` 作用在元素內容上。

![content-box](https://imgur.com/O7fNAmB.png)

另一種是 **`border-box`**，`width` 和 `height` 作用在邊框上。

![border-box](https://imgur.com/HUivkLG.png)

現行網頁開發的過程中，都會加上以下程式碼片段：

```css
*, *:before, *:after {
  box-sizing: border-box;
}
```

這樣做的目的，是將盒模型設定成 `border-box`，`width` 和 `height` 的作用範圍包含 **content、padding 與 border**，這樣就不需要再額外計算 padding 和 border 佔據的空間，降低網頁元素跑版的情況發生。

* 參考文章：[CSS 習作｜Box Sizing 盒模型計算方式](https://vocus.cc/article/649bbb8afd897800010e97b6)

## 排版實務觀念

### line-height

在網頁排版中，文字本身是不具有高度的，文字的高度是由行距（line-height）所產生。

![line-height](https://imgur.com/qHazEb5.png)

### 圖片細節

包裹在 `<div>` 內的 `<img>` 元素，底部都有 **3px 的間距**。

在網頁排版中，圖片的性質與文字字元相似，而圖片與文字字元的 `vertical-align` 預設為 baseline，其底部的空間是預留給諸如：g、p、y 等字元使用。

![baseline](https://imgur.com/gnbchEm.png)

設定 `<img>` 的 `vertical-align` 屬性，表明圖片不需要這樣的預留空間，即可解決圖片底部有 3px 間距的問題。

```css
img {
  vertical-align: middle;
}
```

### 容器相關

* 不輕易寫死容器的高度

  容器的高度，應由內元件的內容**自適應推擠產生**；若是將容器高度寫死，容易導致內元件跑版。

* margin 與 padding

  * margin 與 padding 的推擠方向盡量一致，避免邊距重疊（margin collapsing）的問題發生。

  * 從父層元素設定 padding，統一外容器與內元件的內邊距。

### 類別名稱相關

* 網頁排版的每個區塊，都要自訂 class 名稱。
* class 名稱的順序：**共用性質**的 class 名稱，應放在自訂的 class 名稱之後。
  
  ```html
  <div class="profile container"></div>
  ```

### 滿版式網頁設計

範例網站：

* [蝦皮](https://shopee.tw/)
* [IT 鐵人邦](https://ithelp.ithome.com.tw/)
