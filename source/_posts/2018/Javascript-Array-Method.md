---
title: Javascript Array Method
date: 2018-06-05 13:45:33
categories: JavaScript
tags: 
    - JavaScript
    - ES6
---


## <center>Javascript Array Method</center>
在工作中，常常會遇到需要處理陣列的資料時候，所以熟悉 Javascript 裡的陣列方法是必須的，在剛學習時，常常會忘記也不清楚這些方法`return`回來的結果是甚麼、會不會改變原陣列中的資料。  

所以在這邊做了個筆記，整理一下自己常使用的 JS 陣列方法，方便自己以後能夠快速查找，也希望對參考此篇文章的讀者有幫助。(有些自己不常用的陣列方法這邊就先不提，若未來常使用到會再做補充)

---

## <center> 陣列內容操作</center>

### 在開頭或結尾處添加或移除一個元素 push()、pop()、unshift()、shift()


如果要在陣列的開頭或結尾處添加或移除一個元素，這邊介紹4個方法，分別是`push()`、`pop()`、`unshift()`、`shift()`。

`push()`是從陣列最後面 '**塞入**' 一個值。

`pop()`是從陣列最後面 '**拿出**' 一個值。

`unshift()`是從陣列最前面 '**塞入**' 一個值。

`shift()`是從陣列最前面 '**拿出**' 一個值。

`push`與`shift`會在加入新元素之後回傳陣列的'**最新長度**'，而`pop`與`shift`會回傳'**被移除的元素**'。    

看一下例子:
```js
const arr = ['b', 'c', 'd'];
arr.push('e');    //['b', 'c', 'd', 'e']     //回傳4
arr.pop();        //['b', 'c', 'd']          //回傳'e'
arr.unshift('a');   //['a', 'b', 'c', 'd']     //回傳4
arr.shift();      //['b', 'c', 'd']          //回傳'a'
```

### 在結尾處添加多個元素 concat()


`concat()`方法可以在陣列結尾處加入多個元素，並回傳'**一個新的陣列**'。

如果將陣列傳入`concat`，他會拆開這些傳入的陣列，並將他們的元素加入原本的陣列。

看一下例子:
```js
const arr = [1, 2, 3];
arr.concat(4, 5, 6);      //回傳新陣列[1, 2, 3, 4, 5, 6]
arr.concat([4, 5, 6]);    //回傳新陣列[1, 2, 3, 4, 5, 6]
arr.concat([4, 5], 6);    //回傳新陣列[1, 2, 3, 4, 5, 6]
arr.concat([4, [5, 6]]);  //回傳新陣列[1, 2, 3, 4, [5, 6]]
//concat只會拆解所傳入的陣列，並不會拆開這些陣列裡的陣列
//原本陣列 arr 並不會被修改
```

### 陣列反轉 reverse()


`reverse()`方法能夠反轉陣列的順序:
```js
const arr = [1, 2, 3];
arr.reverse();   
console.log(arr);  //[3, 2, 1]
```

### 陣列排序 sort()


`sort()`方法是以Unicode字串碼順序來排序英文與數字。

```js
//英文 : 按照第一個字母排序:
const strArr = ['ant', 'cat', 'dog', 'bear'];
strArr.sort();
console.log(strArr);  //['ant', 'bear', 'cat', 'dog']

//數字 : 按照數字第一個字排序:
const numArr = [98, 120, 29, 41];
console.log(numArr);  //[120, 29, 41, 98]
```

數字這樣的排列，通常不是我們所想要的結果。

所以一般在使用`sort()`時，會加入一個' 排序函式(compareFunction) '，並同時傳入2個參數。

```js
const numArr = [98, 120, 29, 41];
numArr.sort((a, b) => a - b);
console.log(numArr);  //[29, 41, 98, 120]
```

### 在任何位置加入或移除元素 splice()


`splice()`方法可以就地修改字串，在任何索引加入或移除元素。方法中的第一個參數是'要開始修改的索引'，第二個是'要移除的元素數量'(若不想移除任何元素，就使用 '0' )，其餘的參數就是'所要加入的元素'。

`splice()`方法會回傳一個陣列，陣列內容是被刪除的元素，若沒有元素被移除，則回傳一個空陣列。

```js
const arr = [1, 5, 7];      
arr.splice(1, 0, 2, 3, 4);  //回傳[];  arr現在是 [1, 2, 3, 4, 5, 7]
arr.splice(5, 0, 6);        //回傳[];  arr現在是 [1, 2, 3, 4, 5, 6, 7]
arr.splice(1, 2);           //回傳[2, 3];  arr現在是 [1, 4, 5, 6, 7]
arr.splice(2, 1, 'a', 'b'); //回傳[5];  arr現在是 [1, 4, 'a', 'b', 6, 7]
```

---

## <center> 陣列轉換 </center>

### 比對資料 map()、filter()

**map()**

`map()` 方法可以轉換陣列中的每一個元素，它會將所有陣列中的元素依序分別傳入一次至 callback 函式當中，並'**建立一個新的陣列**'，其內容為原陣列的每一個元素經由回呼函式 (Callback Function) 運算後所回傳的結果之集合。

先看個簡單的例子:
```js
const fruits = [{name: 'Apple', price: 100},{name: 'Banana', price: 200}];
const names = fruits.map(a => a.name);      //['Apple', 'Banana']
const prices = fruits.map(a => a.price);    //[100, 200]
const discount = price.map(a => a.a*0.8);   //[80, 160]
```
當你提供的函式被呼叫時，最多可以使用三個參數宣告回呼函式：元素本身、元素索引、以及陣列本身(較少用到)。

接續上述範例，如果水果與價格被存放在兩個不同的陣列當中，但我們又想結合他們:
```js
const items = ['Apple', 'Banana'];
const prices = [100 ,200];
const fruits = items.map( (x, i) => ({name: x, price: prices[i]}) );
//必須將物件用括號包起來，不然箭頭函式會將大括號視為區塊標示
console.log(fruits) ;
// [{name: 'Apple', price: 100},{name: 'Banana', price: 200}]
```
在這個範例中，我們使用了元素本身 (x) ，也使用了它的索引 (i) ，之所以需要索引，是因為我們要將 items 與 prices 裡面的元素用他們的索引連結起來，在這裡 map 會從各陣列拉入資訊，將字串陣列轉換為物件陣列。

**filter()**

`filter()` 方法的目的是移除陣列中不想要的東西，會回傳一個'**已移除元素的新陣列**'。
```js
const peoples = [
    {name: 'Alex', age: 13},
    {name: 'John', age: 19},
    {name: 'Cart', age: 25}
]
peoples.filter(a => a.age > 20); //[{name: 'Cart', age: 25}]
```

---

## <center> 特別的方法 </center>

### 陣列魔法 reduce()


`reduce()` 方法將一個累加器及陣列中每項元素（由左至右）傳入回呼函式，將陣列化為單一值。
上面我們有介紹過`map()`方法可以轉換陣列中的每一個元素，但`reduce()`會轉換整個陣列，它通常會被用來將陣列精簡為一個值，例如加總陣列的數字或計算平均值。但是`reduce()`提供的單值可以是物件或另一個陣列，所以`reduce()`也有`map()`與`filter()`的功能。

`map()`與`filter()`方法中，傳入回呼的第一個元素一定是目前陣列的元素，但`reduce()`所傳入回呼函式的第一個值是個'**累加器**'，再來才是元素本身、元素索引、以及陣列本身。

除了接收回呼之外也可接收累加器的初始值，例:
```js
const arr = [3, 2, 9, 7];
const sum = arr.reduce((a,b) => a += b, 0);
console.log(sum);  //21
```
這時被傳入 reduce 的函式會接收兩個參數 : 累加器 (a) 、目前陣列元素 (b) ，而累加器的初始值是'0'。
此時函式被呼叫時，會使用陣列的第一個元素 (3) 來呼叫函式。a的初始值是 0 ， b 的值是 3 ，這時函式會回傳a與b的總和 (3) ，它會變成下一個步驟a的值。

若不設定累加器初始值 (undefined) ，則會使用陣列的第二個元素 (2) 來呼叫函式。 a的初始值是 3 ， b 的值是 2 ，這時函式會回傳 a 與 b 的總和 (5) ，它會變成下一個步驟 a 的值。(相當於將陣列第一個元素當做是累加器初始值)

---

## <center> 相關連結 </center>

* [[JS30] - Day4](https://yehjing.github.io/Blog/2018/js30-4.html/)

