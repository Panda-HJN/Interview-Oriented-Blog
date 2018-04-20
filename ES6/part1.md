前了个言

一个语法为什么要存在?面对标准偶尔会冒出这样的问题。    
解决办法大致就是
1. 触类旁通，去看看其他语言有没有这个语法，怎么用的
2. 反证法，如果不用这个语法，该怎么实现需求

所以写这个系列以做总结

# let const

先说个坑
```js
function text1(){
    if(true){
       console.log(a)
    }else{
       //
    }
}
// Uncaught ReferenceError: a is not defined
```
显然结果会报错   

那么如果在不会被执行的else里声明呢？

```js
function text1(){
    if(true){
       console.log(b)
    }else{
       var b 
    }
}
// undefined
```
不会被执行的else 却声明了b.（js good parts 这本书里建议了 所有var 要放在函数开始处。以防这些问题出现）

正是这不符合逻辑的变量提升催生了 const let 的出现。

```js
{
    let a = 1
    {
        console.log(a)
        // Uncaught ReferenceError: a is not defined
        // 块级作用域即拿不到里面的也拿不到外面的
        // let a 之前的地方是临时死去，使用就报错
        let a = 2
        {
            let a = 3
        }
    }
}



···