# notes
趁懶惰病沒發作前隨手記一些有的沒的


## 作用域
程式碼中定義變數的區域，以變數宣告三兄弟來說，作用域分別為
| var | let | const |
|---------|---------|----------|
| function | block (大括號) | block (大括號) |

```javascript
// 知名面試題
for(var i = 0; i < 10; i++){
    setTimeout(function(){
        console.log(i);
    },100);
}   // 10,10,10,10,......

for(let i = 0; i < 10; i++){
    setTimeout(function(){
        console.log(i);
    },100);
}   // 1,2,3,4,5,6...
```

## 閉包
一般 function 裡的變數只會存在於 function 運行期間，利用回傳 function 的方式保留變數

```javascript
// 簡單的計數器

function counter() {
    var count = 0;
    return function() {
        count++;
        console.log(count);
    }
}

var counter1 = counter();
var counter2 = counter();

// 以 return function 的方式保留變數，並且不會互相影響
counter1(); // 1
counter2(); // 1

counter1(); // 2
counter2(); // 2

```


## this
關鍵字 this 會指向**調用**他的物件，以 java 來說，this 只能在物件裡使用，指向 instance 本身，js 可以在任何地方使用，但有沒有意義又是另外一個故事了，指定方式大概分為: 預設、隱含、指定、new、arrow function

#### 預設
| 非嚴格模式 | 嚴格模式 | Node.js |
|---------|---------|----------|
| window | undefined | global |

```javascript
function test1() {
    console.log(this);
};

function test2(){
    'use strict';
    console.log(this);
};

test1(); // window
test2(); // undefined
```

#### 隱含
物件.函式()，那函式裡面的 this 就會指向這個物件

```javascript
// 例1
function sayName() {
  console.log(this.name);
}

var dog = {
  name: '可愛的小狗勾',
  sayName: sayName
}

dog.sayName() // '可愛的小狗勾'

var anotherDog = dog.sayName;
anotherDog() // undefined
```
#### 指定
三巨頭: call、apply、bind，皆用來明確指定 function 裡的 this


#### new
#### arrow function
#### 參考資料
[彻底理解js中this的指向，不必硬背](https://www.cnblogs.com/pssp/p/5216085.html)  
[JavaScript 了解 this 與 new 函式](http://skyroxas.tw/javascript%E4%BA%86%E8%A7%A3-%E8%88%87-new-%E5%87%BD%E5%BC%8F/)  
[淺談 JavaScript 頭號難題 this：絕對不完整，但保證好懂](https://blog.techbridge.cc/2019/02/23/javascript-this/)  
