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

所以做了個筆記，整理一下 JS 中的陣列方法，方便自己以後能夠快速查找，也希望對路過的人有幫助。


## <center> 操作陣列內容</center>

### <center>在開頭或結尾處添加或移除一個元素</center>

#### <center>push()、pop()、unshift()、shift()</center>
如果要在陣列的開頭或結尾處添加或移除一個元素，這邊介紹4個方法，分別是
`push()`、`pop()`、`unshift()`、`shift()`。

`push()`是從陣列最後面 '**塞入**' 一個值。

`pop()`是從陣列最前面 '**拿出**' 一個值。

`unshift()`是從陣列最後面 '**塞入**' 一個值。

`shift()`是從陣列最前面 '**拿出**' 一個值。

`push`與`shift`會在加入新元素之後回傳陣列的'**最新長度**'，而`pop`與`shift`會
回傳'**被移除的元素**'。    

看一下例子:
```js
const arr = ['b', 'c', 'd'];
arr.push('e');    //['b', 'c', 'd', 'e']     //回傳4
arr.pop();        //['b', 'c', 'd']          //回傳'e'
arr.unshift('a');   //['a', 'b', 'c', 'd']     //回傳4
arr.shift();      //['b', 'c', 'd']          //回傳'a'
```

### <center>在結尾處添加多個元素</center>

#### <center>concat()</center>

`concat()`方法可以在陣列結尾處加入多個元素，並回傳'**一個新的陣列**'。

如果將陣列傳入`concat`，他會拆開這些傳入的陣列，並將他們的元素加入原本的陣列。

看一下例子:
```js
const arr = [1, 2, 3];
arr.concat(4, 5, 6);       //回傳新陣列[1, 2, 3, 4, 5, 6]
arr.concat([4, 5, 6]);     //回傳新陣列[1, 2, 3, 4, 5, 6]
arr.concat([4, 5], 6);    //回傳新陣列[1, 2, 3, 4, 5, 6]
arr.concat([4, [5, 6]]);  //回傳新陣列[1, 2, 3, 4, [5, 6]]
//concat只會拆解所傳入的陣列，並不會拆開這些陣列裡的陣列
//原本陣列 arr 並不會被修改
```

## <center> 反轉與排序陣列 </center>

### <center>反轉陣列的排序 </center>

#### <center>reverse()</center>

`reverse()`能夠反轉陣列的順序:
```js
const arr = [1, 2, 3];
arr.reverse();   
console.log(arr);  //[3, 2, 1]
```

#### <center> sort() </center>

`sort()`是以Unicode字串碼順序來排序英文與數字。

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

## <center> 比對、過濾資料 </center>

### <center> 比對資料 </center>






## <center> 相關連結 </center>

