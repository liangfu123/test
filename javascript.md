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

# 流程控制

* if

* if-else

* if-else if...

* switch-case

  >switch(表达式){
  >
  >​	case 值1:代码1;break;
  >
  >​	case 值2:代码2;break;
  >
  >​	...
  >
  >​	default:代码3;(default后面的break可以省略)
  >
  >}

* while

* do-while

* for

* for in 

  > 遍历数组对象和json格式

  ```javascript
  		var arrArray = [1,2,3,4,7,5,6]; 
  		for(var a in arrArray){
  			console.log(arrArray[a]);
  		}
  
  		var json = {"name":"liangfu","age":"20"};  
  		for(var key in json){
  			console.log(key + "------" + json[key]);
  		}
  ```

## break和continue关键字使用

* break关键字：在循环中，遇到break，立刻跳出当前所在循环
* continue关键字：在循环中，遇到continue，直接开始下一次循环

# 数组

* 创建数组
  * var 数组名 = new Array();
  * var 数组名 = [];



# 函数

* 函数的定义

  >function 函数的名字（）{
  >
  >​	函数体
  >
  >}

* 函数的调用

  > 函数名（）；

* 函数的参数

  > function 函数名（x）{
  >
  > }
  >
  > function 函数名（x,y）{
  >
  > }

* 函数的返回值 return 

## 函数表达式

* var 变量 = 匿名函数；

  > var f1 = function () {
  >
  > };
  >
  > f1();//调用

* 函数可作为参数，作为返回值使用；

  * 作为参数

    ```javascript
    function eat(callback){
        setTimeout(function(){
            console.log("吃饭了");
            callback();
        },1000)
    }
    
    eat(function(){
        console.log("去唱歌");
    })
    ```

  * 作为返回值

    ```javascript
    function genFun (type) {
      return function (obj) {
        return Object.prototype.toString.call(obj) === type
      }
    }
    
    var isArray = genFun('[object Array]')
    var isObject = genFun('[object Object]')
    
    console.log(isArray([])) // => true
    console.log(isArray({})) // => true
    ```

  * 函数闭包

    ```javascript
    function getFun(){
        var count = 0;
        return {
            getCount : function(){
                console.log(count);
            },
            addCount : function(){
                count++;
                console.log(count);
            }
        }
    }
    
    getFun().getCount();
    getFun().addCount();
    ```

## 创建对象三种方式

* 调用系统的构造函数创建对象

  * var 变量名 = new Object();

* 自定义构造函数创建对象

  ```javascript
  function Person(){}
  var p = new Person();
  ```

  ```javascript
  function Person(name,sex,age){
  	this.name = name;
  	this.sex = sex;
  	this.age = age;
  }
  var p = new Pserson("梁富","女",30);
  ```

  * 函数和构造函数区别：名字首字母是否大写

* 字面量方式创建对象

  ```javascript
  var obj = {};
  obj.name = "小白"；
  obj.age = 20;
  obj.sayHi = funciton (){
  	console.log("我是:"+this.name);
  }
  obj.sayHi();//调用
  ```

  ```javascript
  var obj = {
  	name : "liangfu",
  	age : 20,
  	sayHi : function(){
  		console.log("我是:"+this.name);
  	},
  	eat : function(){
  		conaole.log("我喜欢吃鱼");
  	}
  }
  //调用
  obj.sayHi();
  obj.eat();
  ```

## JSON格式

* json 也是一个对象,无论是键还是值都用双引号括起来

  ```javascript
  var json = {
  	"name" : "liangfu",
  	"age" : "20",
  	"sex" : "女"
  };
  ```

* 遍历对象

  > 不能通过for循环遍历，可以通过for-in循环

  ```javascript
  for(var key in json){
  	console.log(key + "=======" + json[key]);
  }
  
  ```

  

## 内置对象

* js学习中三种对象

  > 1.内置对象-----js系统自带
  >
  > 2.自定义对象-----自定义构造函数创建的对象
  >
  > 3.浏览器对象

* Math

  * 属性
  * 方法
    * floor(x)下舍入
    * max(x,y)
    * min(x,y)
    * random()返回0~1之间的随机数
    * round(x)四舍五入为整数

* Date

  * 方法
    * Date()
    * getTime()
    * getDate()
    * getMonth()
    * getFullYear()
    * getDay()

* String

  * 属性
    * length
  * 方法
    * charAt()
    * concat()
    * replace()
    * split()把字符串分割为字符串数组
    * toString()
    * valueOf()
    * indexOf()定位字符串中某一个指定字符首次出现的位置
    * match()查找字符串中特定字符，如果找到返回这个字符

* Array

  * 属性
    * length
  * 方法
    * reverse()
    * sort()
    * toString()

* Object

## 工厂函数

* 使用构造函数，会存在浪费内存的情况

  ```javascript
  function Person(name,age){
      this.name = name;
      this.age = age;
      this.type = "human";
      this.sayHi = function(){
          console.log("我的名字：" + this.name + "年龄：" + this.age);
      }
  }
  
  var p = new Person("梁富"，20);
  ```

  > 以上代码，type和sayHi每次创建实例对象时，该代码都是重复的，因此会浪费内存
  >
  > 解决：把共享的代码定义到函数外部，使用prototype

  ```javascript
  function Person(name,age){
      this.name = name;
      this.age = age;
  }
  Person.prototype.type = "human";
  Person.prototype.sayHi = function (){
      console.log("我的名字：" + this.name + "年龄：" + this.age);
  };
  
  var p = new Person("梁富",20);
  p.sayHi();
  
  //更简单的原型语法
  Person.prototype = {
      constructor : Person,//手动将constructor指向正确的构造函数
      type : "human",
      sayHi : function() {
          console.log("我的名字：" + this.name + "年龄：" + this.age);
      }
  }
  ```

  * 原型对象使用建议：
    * 私有成员（一般是非函数）放到构造函数中
    * 共享成员（一般是函数）放到原型对象中

## 函数递归

```javascript
	function jiecheng2(num){ 
			if(num <= 1){
				return 1;
			}else {
				return num * jiecheng2(num-1);
			}
		}
 console.log(jiecheng2(10));
```

## 正则表达式

* 支持正则表达式的String对象的方法
  * search()
  * match()
  * replace()
  * split()

## 事件

* onchange

* onblur元素失去焦点

* onclick鼠标点击

* onfocus元素获得焦点

* onload某页面或图像加载完成

* onselect文本被选择

* onsubmit点击提交按钮时

  ```javascript
  <form action="" mehtod="" onsubmit="return checkForm()" />
  ```

## DOM对象

* Document Object Model  文档对象模型

  * Window对象
    * 属性
      * closed
      * document
      * location
    * 方法
      * alert()
      * close()关闭浏览器窗口
      * confirm()
      * open()
      * prompt()
      * setInterval()
      * setTimeout()
  * Location对象
    * 属性
      * href
      * port
      * host
  * Document对象：用来访问页面中的所有元素
    * 属性
      * cookie
      * URL
      * body
    * 方法
      * close()
      * getElementById()
      * getElementByName()
      * getElementByTagName()
      * write()
  * Form对象
  * Button对象
  * ...

  

  