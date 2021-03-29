# notes
趁懶惰病沒發作前隨手記一些有的沒的


## 作用域
程式碼中定義變數的區域，以變數宣告三兄弟來說，作用域分別為
| var | let | const |
|---------|---------|----------|
| function | block (大括號) | block (大括號) |

```javascript
//知名面試題
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
## this
