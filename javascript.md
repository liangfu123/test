# 变量

+ 变量声明 var
+ 变量命名规则
  + 字母、数字、下划线、$符号组成，不能以数字开头
  + 不能是关键字和保留字
  + 区分大小写
+ 变量命名规范
  + 变量名必须有意义
  + 遵守驼峰命名

> 案例：
>
> 交换两个变量的值：三种方法

# 数据类型

+ 6种

  + number

    > 不要判断两个浮点数是否相等，结果是错误的

    > 数值范围：
    >
    > 最大值Number.MIN_VALUE
    >
    > 最小值Number.MAX_VALUE

    > 数值判断：
    >
    > NaN：不是一个数字（与任何值都不相等）
    >
    > isNaN：是不是一个数字

  + string

    + 字符串长度 str.length

  + boolean

  + null

  + undefined

  + object

  > nul其实就是object

+ 获取变量类型 typeof

  ```
  var name = "小白";
  console.log(typeof name);
  ```

# 数据类型转换

+ toString()
+ String()
+ Number()
+ parseInt()
+ parseFloat()
+ Boolean()

# 操作符

+ 算数运算符： + 	- 	*	 / 	%

+ 一元运算符:    ++    --

  + ++i

    > 先自身加一，再参与运算

  + i++

    > 先参与运算，再自身加一

+ 逻辑运算符

  > && 	 ||  	!

+ 关系运算符

  > < 	>	>=	<=	== 	!=	===	    !==

+ 赋值运算符

  > = 	+= 	-= 	*=	 /= 	%=

+ 三元运算符

  > 表达式1？表达式2：表达式3；