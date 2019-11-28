# lodash 里一些常用的API


## String 
- kebabCase(str) 转为中横线连接
- camelCase(str) 转换为小驼峰
- snakeCase(str) 转换为下划线,下划线连接确实像蛇
- startCase(str) 转换为空格连接(准确说是 start case)
- lowerCase(str) 转换为空线连接,同时转为小写
- upperCase(str) 转换为空格连接,同时转为大写
- capitalize(str) 首字母大写
- lowerFirst(str) 首字母小写
- toLower(str) 全转为小写
- toUpper(str) 全转为大写
- startsWithstr,target,index) target从 是否已str开头
- endsWith(str,target,index) target从 是否已str结尾
- pad(str,length,pad) 把str的长度拓展到len,前后使用pad来填充
- padStart(str,length,pad) 功能同pad,但是只是填充左侧
- padEnd(str,length,pad)功能同pad,但是只是填充右侧
- trim(str) 首尾去空格 ES5本身已提供
- trimEnd(str) 尾部去空格
- trimStart(str) 尾部去空格
- truncate(str,{length:num,separator:"..."}) 字符串截断长度到num,并用 separator 结尾
- words(str,reg) 拆str为由词组成的数组 reg可选,来设置匹配模式
