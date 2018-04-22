# var 与块级作用域
## var的问题
因为 ES5 的限制，为了一个简单的局部变量问题，要写繁琐的立即执行函数。

```html
    <ul id="box">
        <li>点我显示0</li>
        <li>点我显示1</li>
        <li>点我显示2</li>
        <li>点我显示3</li>
        <li>点我显示4</li>   
    </ul>
    <script>
        var liNodes = document.querySelectorAll('#box li')
        for(var i= 0; i<liNodes.length;i++){
            (function(){
                var j = arguments[0]
                liNodes[j].onClick=function(){
                    console.log(j)
                }
            })(i)
        }
    </script>
```
变量提升也造成了不少麻烦，下面代码中 else 里不会被执行的代码却影响到了会执行的代码，声明了a。

```js
function test(){
    if(true){
       console.log(a)
    }else{
       var a 
    }
}
test()// undefined
```
大部分规范都要求所有 var 要放在函数开始处。以防变量提升导致的问题。   

正是这些麻烦和不符合逻辑的结果催生了 let const 和**块级作用域**的出现。

## let const
let 所声明的变量只会被声明一次，同一个作用域内再次声明会报错。   
一组`{}`构成了一个块级作用域。(for 循环中 let 编译器做了一点魔法)   
let 声明的变量会乖乖呆在所在位置,`let a`之前的地方是临时死区，即拿不到里面的a也拿不到外面的a.   
使用a就报错
```js
{
    let a = 1
    let a = 2//Identifier 'a' has already been declared
    {
        console.log(a)
        // Uncaught ReferenceError: a is not defined
        // let a 之前的地方是临时死区，即拿不到里面的也拿不到外面的,使用a就报错
        let a = 2//let 声明的变量会乖乖呆在所在位置
        console.log(a) //2
        {
            let a = 3
        }
    }
}
console.log(a)// Uncaught ReferenceError: a is not defined
```

有了let后 上面的代码可以简化成
```html
    <ul id="box">
        <li>点我显示0</li>
        <li>点我显示1</li>
        <li>点我显示2</li>
        <li>点我显示3</li>
        <li>点我显示4</li>   
    </ul>
    <script>
        var liNodes = document.querySelectorAll('#box li')
        for(var i= 0; i<liNodes.length;i++){
            let j = i                
            liNodes[j].onClick=function(){
                    console.log(j)
            }
        }
    </script>
```
const 的行为和 let 完全一致，区别是 let 可以再次赋值。 const 则是声明了个不可变的常量。   


----------------------------
let 和 const 把var造成的问题都解决了