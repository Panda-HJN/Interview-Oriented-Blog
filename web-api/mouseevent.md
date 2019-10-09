# mouseEvent 

常触发于 click，dblclick，mouseup，mousedown 这四个事件

`new MouseEvent(typeArg, mouseEventInit)`可以创建一个mouseEvent

## 常用属性

1. clientX / clientY   
事件触发时事件对象在**应用客户端**区域的的X/Y坐标.

2. offsetX / offsetY   
事件触发时事件对象标在**目标节点**内边距边界的 X/Y偏移量.   
可以将左上角的padding和border边界视为为基准点;
这个值和 border-box还是content-box 没有关系

3. pageX / pageY   
事件触发时事件对象在**整个文档**区域的的X/Y坐标.
定位基于整个文档的边缘.

4. screenX / screenY   
事件触发时事件对象在**屏幕**区域的的X/Y坐标.


5. altKey / ctrlKey / shiftKey   
事件触发时,如果 alt / ctrl / shift 键也被按下,则返回 true, 用来判断是否事组合操作

6. buttons   
用来标识鼠标按下的一个或者多个按键。   
如果按下的键为多个,则值等于所有按键对应数值进行**或(|)**运算的结果.
    - 0  : 没有按键或者是没有初始化
    - 1  : 鼠标左键
    - 2  : 鼠标右键
    - 4  : 鼠标滚轮或者是中键
    - 8  : 第四按键 (通常是“浏览器后退”按键)
    - 16 : 第五按键 (通常是“浏览器前进”)

7. movementX /movementY  
提供了当前事件和上一个mousemove事件之间鼠标在水平方向上的移动值。   
也就是 : currentEvent.movementX = currentEvent.screenX - previousEvent.screenX.   
这两个属性需要和
`Element.requestPointerLock()`,
`Document.exitPointerLock()`配合使用(存疑)   
详见Pointer Lock API

--------------------------------------
[demo](https://jsbin.com/haconuxefo/edit?html,css,js,console,output)
