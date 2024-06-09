title: 變數
author: Timothy
tags:
  - JavaScript
categories:
  - JavaScript
date: 2024-06-05 21:38:47
description: 最簡單也最重要的變數觀念
cover: https://images.unsplash.com/photo-1507721999472-8ed4421c4af2?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
---
程式（program）是一組特殊的指令，用來告訴電腦要執行什麼任務。當在程式執行的過程中，需要重複使用到特定資料時，最簡單的方式就是將資料存放到容器中記錄起來。

若資料在程式執行的過程中是會變動的，會將該容器稱為**變數**（variable），也就是說「變數是用來記錄資料在程式執行的過程中之狀態（state）」。

要確保資料在程式執行的過程中都不會變動時，會將該容器稱為**常數**（constant）。當常數被宣告並賦予初始值後，程式執行的過程中將無法再對常數重新賦值。

## 宣告變數

JavaScript 是動態型別的程式語言，在宣告變數時，**不需要**明確指定變數的資料型別。JavaScript 也是弱型別的程式語言，當兩個不同型別的資料進行運算時，允許**型別轉換**。

```js
let milkPrice = 40;
```

宣告一個變數，變數名稱為 `milkPrice`，並賦予 `milkPrice` 值為 40。

## 宣告變數的方式

JavaScript 有三種宣告變數的方式：`let`、`const`、`var`。

### let

使用 `let` 宣告變數，若有設定初始值，可以對該變數重新賦值。

```js
let milkPrice = 40;
console.log(`milk price: ${milkPrice}`);  // milk price: 40
```

宣告一個變數，變數名稱為 `milkPrice`，並賦予 `milkPrice` 值為 40。

```js
const DISCOUNT = 0.8;
milkPrice = milkPrice * DISCOUNT;
console.log(`milk price: ${milkPrice}`);  // milk price: 32
```

存取變數 `milkPrice`，並重新賦予 `milkPrice` 值為 32。

### const

使用 `const` 宣告變數，若變數為基本型別（primitive type），**不可**再對該變數重新賦值。

```js
const DISCOUNT = 0.8;
DISCOUNT = 0.75;
```

```txt
Uncaught TypeError: Assignment to constant variable.
```

若變數為物件型別（object type），則可以對**該變數內的資料**重新賦值。

### var

使用 `var` 宣告變數，會汙染**全域變數**，容易產生不可預期的錯誤。

主要是因為將變數宣告成全域變數會發生以下情況：

1. 變數名稱衝突，發生預期外的程式錯誤

2. 佔用記憶體，無法回收

現在大多使用 `let`、`const` 宣告變數，避免汙染全域變數的問題發生。

### 宣告變數的限制

在宣告變數時，變數的命名有以下限制：

1. 變數名稱有區分大小寫，例如：`mikePrice`、`milkprice` 是兩個不同的變數

2. 第一個字元不可為**數字**，例如：`1price`

3. 第一個字元可為特殊符號，例如：`$price`、`_price`

4. 可以使用中文命名變數

5. **不可使用[保留字（JavaScript Reserved Words）](https://www.w3schools.com/js/js_reserved.asp)**

## 變數與記憶體

使用瀏覽器（browser）執行 JavaScript 時，變數資料會被儲存在瀏覽器的記憶體空間中，每個分頁都有**獨立的記憶體空間**，變數資料不會在不同分頁中共享。

當瀏覽器**重新載入**（reload）時，該分頁的記憶體空間會被清空，變數資料不復存在。

## 資料型別（Data Types）

### 基本型別（primitive type）

* 數值（number）
* 字串（string）
* 布林（boolean）
* 空值（null）
* 未定義（undefined）

### 物件型別（object type）

* 陣列（array）
* 物件（object）
* 函式（function）

## 判斷資料型別

使用 `typeof` 可以檢查變數的資料型別，回傳值的資料型別為**字串**（string）。

```js
typeof 614   // 'number'
typeof 3.14  // 'number'
typeof -31   // 'number'
typeof NaN   // 'number'
```

不過，`typeof` 無法**精準**的判斷資料型別，以下是一些容易混淆的地方：

* `typeof null` 會回傳「object」。照理說 `null` 應該屬於基本型別之一，不應該是物件型別，但根據 w3c 的說明，可以將這件事視為一個 bug：

  > You can consider it a bug in JavaScript that `typeof null` is an object. It should be null.

* `typeof [1, 3, 5]` 會回傳「object」。typeof 無法將物件型別中的陣列細分出來。

* `typeof function() {}` 會回傳「function」。雖然函式也是一種特殊的物件型別。

* `typeof NaN` 會回傳「number」。要檢查資料是否為 NaN 時，可以使用 `isNaN()` 方法，如果是 NaN 會回傳 true。
