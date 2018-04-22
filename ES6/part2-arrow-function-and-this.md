# this 与 箭头函数
## ES5的函数
- 具名函数
```js
function fun1(p1,p2,p3){
    console.log(1)
    return 2
}
```

- 匿名函数
```js
var fun1 = function (p1,p2,p3){
    console.log(1)
    return 2
}
```
    1. 声明一个匿名函数
    2. 声明一个变量
    3. 把匿名函数赋给变量

## 箭头函数
箭头函数只能做赋值
```js
let fun1 =  (p1,p2,p3)=>{
    console.log(1)
    return 2
}

//如果只有一个参数，可以不写圆括号
let fun2 =  p=>{
    console.log(1)
    return 2
}
//如果函数体只有一行，可以不写大括号
let fun2 =  p=>{return p +1}
let fun3 =  p=>p+1 //省略了大括号也必须省略掉 return
```

## 为什么要使用箭头函数？
在ES5中，函数使用起来面临的最大问题是函数的`this`。   
this是 call的第一个参数，是函数的执行上下文...（就像python的self）
箭头函数最大的用处是提供了一种弱化了this的代码执行方式。
