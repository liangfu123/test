#HTML5
##语义标签
> 和div盒子一样，只是标签名更好识别div布局

```
<header>头部</header>
<nav>导航</nav>
<main><!-- 主体 -->
	<article>左边</article>
	<aside>右边</aside>
</main>
<footer>底部</footer>
```

> 兼容性问题解决：

> 方式一：手动创建标签
>
> 方式二：引入第三方插件 html5shiv.min.js(IE8及以下版本不支持HTML5,引入文件可以兼容)

##表单的新增type属性
+ emai

  ```
  <input type="email">
  <!-- 默认提供电子邮箱的完整验证 -->
  ```

+ tel

  ```
  <input type="tel">
  <!-- 会在移动端打开数字键盘 -->
  ```

+ url

  ```
  <input type="url">
  <!-- 网址：验证只能输入合法的网址，必须包含http:// -->
  ```

+ number

  ```
  <input type="number" value="60" max="100" min="0">
  <!-- number:验证只能输入数字（包含小数点）
  value：默认值 -->
  ```

+ search

  ```
  <input type="search">
  <!-- 提供更好的输入体验 -->
  ```

+ range

  ```
  <input type="range" max="100" min="0" value="50">
  <!-- 范围 -->
  ```

+ color

  ```
  <input type="color">
  <!-- 颜色 -->
  ```

+ time

  ```
  <input type="time">
  <!-- 时间：时分秒 -->
  ```

+ date

  ```
  <input type="date">
  <!-- 日期：年月日 -->
  ```

+ datetime

  ```
  <input type="datetime">
  <!-- 日期时间 datetime:大多数浏览器不支持。用于屏幕阅读器 -->
  ```

+ datetime-loacl

  ```
  <input type="datetime-local">
  <!-- 日期时间：用这个 -->
  ```

+ month

  ```
  <input type="month">
  <!-- 月份 -->
  ```

+ week

  ```
  <input type="week">
  <!-- 星期 -->
  ```

##表单中新增其他属性

<input type="text" name="username" placeholder="请输入用户名" autofocus autocomplete="on">

+ placeholder:提示文本

+ autofocus:自动获取焦点

+ autocomplete:自动完成（on:打开 off:关闭）

> 成功提交过；必须有name属性

<input type="tel" name="userphone" required pattern="^(\+86)?1\d{10}$">

+ required:必须输入

+ pattern:正则表达式验证

<input type="file" name="photo" multiple>

+ multiple:可以选择多个文件

<input type="email" name="email" multiple>

+ multiple:允许输入多个邮箱地址，以逗号分隔

<form action="" id="myForm"></form>
<input type="text" name="address" form="myForm">

+ form:指定在表单外的 表单元素 数据跟表单一起提交

##表单新增元素（标签）

+ datalist

  ```
  	<!--不仅可以选择，还应该可以输入-->
      <!--建立输入框与datalist的关联  list="datalist的id号"-->
  专业：<input type="text" list="subjects"> <br>
      <datalist id="subjects">
          <!--创建选项值：value:具体的值 label:提示信息，辅助值-->
          <!--option可以是单标签也可以是双标签-->
          <option value="英语" label="不会"/>
          <option value="前端与移动开发" label="前景非常好"></option>
          <option value="java" label="使用人数多"></option>
          <option value="javascript" label="做特效"></option>
          <option value="c" label="不知道"></option>
      </datalist>
  ```

  ```
  网址：<input type="url" list="urls">
      <datalist id="urls">
          <!--如果input输入框的type类型是url,那么value值必须添加http://-->
          <option value="http://www.baidu.com" label="百度"></option>
          <option value="http://www.sohu.com"></option>
          <option value="http://www.163.com"></option>
      </datalist>
  ```

+ keygen

<keygen></keygen>
<!-- 加密 -->

+ output

<output>总金额：￥100.00</output>

##表单新增事件

+ oninput:监听指定元素的内容改变

+ onkeyup:键盘弹起的时候触发

+ oninvalid:验证不通过时触发

##进度条

<progress value="100" max="100">

+ value:当前进度值

<meter max="100" min="0" high="80" low="40" value="30"></meter>

+ 度量器：衡量当前进度值

##多媒体标签

<audio src="路径" controls autoplay loop></audio>

+ controls:音频播放器控制面板

+ autoplay:自动播放

+ loop:循环播放

<video src="路径" poster="路径" controls height="600"></video>

+ controls:视频播放器控制面板

+ autoplay:自动播放

+ loop:循环播放

+ poster:用户播放前的显示封面

+ width:视频的宽度

+ height:视频的高度

> 视频始终保持原始的高宽比例，所以只用设置一个高，或者一个宽，两个都设置没用

<video controls>
    <source src="视频路径" type="video/flv">
    <source src="视频路径" type="video/mp4">
</video>

+ source:设置多个视频源（不同浏览器支持视频格式不同）

##dom操作

> query查询 Selector 选择器 querySelector(选择器名称)

document.querySelector(".green");
document.querySelector("#red");

+ querySelector：获取单个元素

document.querySelectorAll("li");
document.querySelectorAll("li")[0];

+ querySelectorAll：获取满足条件的所有元素--数组

> 类样式操作classList

document.querySelector("li").classList.add("red");

+ add:添加

document.querySelector(".blue").classList.remove("blue");

+ remove:移除

document.querySelectorAll("li")[2].classList.toggle("green");

+ toggle:切换元素样式（没有样式则添加，有则移除）

document.querySelectorAll("li")[3].classList.contains("red");

+ contains:判断是否包含指定的样式

<p data-school-name="itcast">传智播客</p>
var p=document.querySelector("p");
p.dataset["schoolName"];

+ data-开头

##接口

+ 网络接口

window.addEventListener("online",function(){
    alert("网络连通了");
});

> ononline:网络连通的时候触发这个事件

window.addEventListener("offline",function(){
    alert("网络断开了");  
})

> onoffline:网络断开时触发

+ 全屏接口

  ```
    window.onload=function(){
      var div = document.querySelector("div");
      <!-- 全屏操作 -->
      document.querySelector("#full").onclick=function(){
        if(div.requestFullScreen){
          div.requestFullScreen();
        }
        else if(div.webkitRequestFullScreen){
          div.webkitRequestFullScreen();
        }
        else if(div.mozRequestFullScreen){
          div.mozRequestFullScreen();
        }
        else if(div.msRequestFullScreen){
          div.msRequestFullScreen();
        }
      }
      <!-- 退出全屏 -->
      <!-- 判断是否是全屏状态 -->
  }
  ```

  > 主要方法：

  > 1.requestFullScreen() 开启全屏

    + 注意：不同浏览器添加不同前缀

      > chrome:webkit firefox:moz ie:ms opera:o

  > 2.cancelFullScreen() 退出全屏

    + 注意：也加前缀

    + 注意：只能用document来实现

      > document.cancelFullScreen()

  > 3.fullScreenElement 是否全屏

    + 注意：加前缀

    + 注意：只能用document实现

      > document.fullscreenElement

+ FileReader

> 即时预览

> 即时：当用户选择文件之后立刻进行预览处理 onchange

> 预览：通过文件读取对象的readAsDataURL()完成

> FileReader:读取文件内容
>
> 1.readAsText():读取文本文件
>
> 2.readBinaryString():读取任意类型文件
>
> 3.readAsDataURL():读取base64编码的字符串形式
>
> 4.abort():中断读取

  ```
   var reader = new FileReader();
   var file = document.querySelector("#myFile").files;
   reader.readAsDataURL(file[0]);
  ```

> 获取数据(FileReader事件模型)

  > onload:文件读取成功完成时触发

  > onprogress:读取文件过程中持续触发

```
    reader.onload=function(){
        document.querySelector("img").src=reader.result;
    }
    reader.onprogress=function(e){
        var percent= e.loaded/ e.total*100+"%";
        div.style.width=percent;
    } 
```

+ 拖拽接口

  + 1.为元素添加draggable="true"

    > <p id="pe" draggable="true">试着把我拖过去</p>

  + 2.拖拽事件

    > ondrag     整个拖拽过程一直调用（持续）
    > ondragstart    拖拽开始时调用
    > ondragleave    鼠标离开拖拽元素时调用
    > ondragend    拖拽结束时调用

  + 3.目标元素事件

    >ondragenter    应用于目标元素，当拖拽元素进入时调用
    >ondragover    应用于目标元素，当停留在目标元素上时调用
    >ondrop        应用于目标元素，当在目标元素上松开鼠标时调用
    >ondragleave    应用于目标元素，当鼠标离开目标元素时调用

    > 1.在ondrop中添加被拖拽的元素

    div2.appendChild(p)

    > 2.在ondragover中阻止浏览器的默认行为，浏览器默认阻止ondrop事件

    div2.ondragover=function(e){
      e.preventDefault();
    }

  + 4.通用-拖拽

    + 使用dataTransfer.setData(format,data)存数据

    + 使用dataTransfer.getData("text/html")获取数据（只能在drop事件中获取）

## 新增选择器

+ 属性选择器

  + 格式：E[attr]（查找属性为attr的E标签）
    + li[style] {text-decoration: underline;}
  + 格式：E[attr=value]（查找attr属性值为value的E标签）
    + li[class=red] {font-size: 16px;}
  + 格式：E[attr*=value]（查找attr属性值中包含value值的E标签）
    + li[class*=red] {font-size: 16px;}
  + 格式：E[attr^=value]（查找attr属性值中以value值开头的E标签）
    + li[class^=red] {font-size: 16px;}
  + 格式：E[attr$=value]（查找attr属性值中以value值结束的E标签）
    + li[class$=red] {font-size: 16px;}

+ 兄弟选择器

  + 兄弟伪类+（查找当前元素相邻的满足条件的元素）
    + .first + li {color: red;}
  + 兄弟伪类-（查找当前元素满足条件的所有兄弟元素）
    + .first - li {color: blue;}

+ 伪类选择器

  + E:first-child

  + E:first-of-type

  + E:last-of-type

  + E:nth-child(索引 || 关键字 || 表达式)

    + li:nth-child(5) {background: pink;}
    + li:nth-child(even) {} //even偶数
    + li:nth-child(odd) {} //odd奇数

  + E:nth-of-type(索引 || 关键字 || 表达式)

  + E:nth-last-of-type(索引 || 关键字 || 表达式)

  + E:nth-of-type(索引 || 关键字 || 表达式)

  + E:empty

  + E:target

    > 可以为锚点目标元素加样式
    >
    > h2:target {color: red;}
    >
    > <a href="#title1">CSS (层叠样式表)</a>
    >
    > <h2 id="title1">CSS (层叠样式表)</h2>

+ 伪元素

  + ::before

  + ::after

    > 注意：必须添加 content: ""，默认隐藏;
    >
    > 默认是行级元素，要设置高宽，必须转换为块元素

  + ::first-letter

    > 获取第一个字符：实现首字下沉

  + ::first-line

    > 获取第一行内容：

  + ::selection

    > 设置当前选中内容的样式

## 颜色使用

+ rgb(红，绿，蓝)
+ hsl(颜色(0~360),饱和度(0%~100%),明度(0%~100%))
+ rgba(红，绿，蓝，透明度)
+ opacity:0.5;通过opacity设置透明度
+ hsla(颜色(0~360),饱和度(0%~100%),明度(0%~100%),透明度)

## 阴影

+ text-shadow: offsetX offsetY blur color;

  > 文本阴影
  >
  > text-shadow: -2px -2px 5px red;
  >
  > 多层阴影：用逗号连接

+ box-shadow:h v blur spread color inset;

  > 边框阴影
  >
  > h：水平方向的偏移值
  >
  > v：垂直方向的偏移值
  >
  > blur：模糊，可选，默认0
  >
  > spread：阴影尺寸，可选，默认0
  >
  > inset：内阴影，可选，默认外阴影
  >
  > box-shadow: 3px 3px 3px #ccc inset,-3px -3px 3px #ccc inset;

## 盒模型

+ box-sizing:border-box;
  + 设置的width是内容的宽度，盒子的最终高宽依然是width+padding+border
+ box-sizing:content-box;
  + 设置的width是盒子的最终宽度，包含padding+border，现在设置padding，border不会撑开盒子,只会减小内容区域

## 圆角

+ border-radius
  + 设置一个值：四个角一样
  + 设置两个值：左上/右下，右上/左下
  + 设置三个值：左上，右上/左下，右下
  + 设置四个值：左上，右上，右下，左下

## 渐变

+ 线性渐变
  + background:linear-gradient(方向，开始颜色 位置，颜色2 位置，颜色3 位置...);
  + background: linear-gradient(to right,red 0%,red 50%,blue 50%,blue 100%);
+ 径向渐变
  + background: radial-gradient(形状 大小 坐标,颜色1，颜色2...);
  + background: radial-gradient(circle farthest-side at 50px 50px,red,blue);
+ 重复渐变
  + background: repeating-linear-gradient(45deg, #fff 0%,#fff 10%, #000 10%,#000 20%);

## 过渡

+ transition:属性名称 过渡时间  时间函数  延迟
  + transition: left 2s linear 0s;
  + transition:all 2s steps(4);
  + 时间函数：控制运动的速度

+ 二维变换

  + 使用transform实现元素移动

    + transform:translateX(300px);水平方向移动

    + transform:translateY(300px);垂直方向移动

    + transform:scaleX(0.5);缩放

    + transform:scaleY(0.5);缩放

      > 旋转rotate

    + transform-origin: left top;旋转，设置旋转轴心（1.x/y 2.关键字）

    + transform: translateX(700px) rotate(-90deg);

      > 斜切

    + transform:skew(-30deg);

    + transform:skew(30deg,-30deg);

  + 添加过渡效果

    + transition: transform 2s;

+ 三维变换

  + 3D移动
    + translate3d(X方向的偏移，Y方向的偏移，Z方向的偏移)
  + 缩放
    + scale3d(x方向上的缩放，y方向的缩放，z方向的缩放)
  + 旋转
    + rotate3d(x,y,z,angle)
  + 添加过渡
    + transition: transform 2s;

+ 实现任意元素居中

  ```
  position: absolute;
  <-- 定位百分比是参照父容器的宽高 -->
  left:50%;
  top:50%;
  <-- 用transform实现元素居中，百分比是参照元素本身的宽高 -->
  transform: translate(-50%,-50%);
  ```

## 动画

+ animation-name:指定动画名称

+ animation-duration:设置动画总耗时

+ animation-iteration-count:设置动画的播放次数，默认一次

+ animation-direction:设置动画交替（alternate:来回交替）

+ animation-delay:设置动画延迟

+ animation-fill-mode:设置动画结束时状态

  + forwards：保留动画结束时状态
  + backwards：不会保留动画结束时状态，若延迟，立刻进入动画初始状态
  + both：保留动画结束时状态，若延迟，立刻进入动画初始状态

+ animation-timing-function:设置动画时间函数

+ animation-play-state:设置动画播放状态

  + paused：暂停
  + running：播放

+ 创建动画

  ```
  @keyframes moveTest {
              /*百分比是指整个动画耗时的百分比  10s*/
              /*0%{
                  transform: translate(0,0);
              }*/
              /*from:0%*/
              from{
                  transform: translate(0,0) rotate(45deg);
              }
              /*0~1*/
              50%{
                  transform: translate(0,500px);
              }
              /*1~2*/
              /*100%{
                  transform: translate(500px,600px);
              }*/
              /*to:100%*/
              to{
                  transform: translate(500px,600px);
              }
          }
  ```

## 布局

+ 多列布局

  + column-count设置列数
  + column-rule列间隔样式
  + column-gap列间隔大小
  + column-width列宽
  + column-span设置跨列显示

+ 伸缩布局

  + display: flex;

    > 设置父元素为伸缩盒子，其子元素自动变成伸缩项

  + justify-content

    > 设置子元素排列方式

    + flex-start
    + flex-end
    + center
    + space-between
    + space-around

  + flex-wrap

    > 控制子元素是否换行

    + nowrap 不换行
    + wrap 换行
    + wrap-reverse 翻转

  + flex-direction

    > 设置子元素排列方向，主轴方向

    + row	水平排列，从左到右
    + row-reverse 水平排列，从右到左
    + column 垂直排列，从上到下
    + column-reverse 垂直排列，从下到上

  + flex-flow

    > flex-wrap和flex-direction的综合

    + flex-flow: row wrap;

  + flex-grow

    > 设置子元素占剩余空间的比例值，默认为0，不占剩余空间

    + flex-grow: 1;

  + flex-shrink

    > 设置收缩比例，默认为1

  + flex

    > 设置当前伸缩子项占剩余空间比例值

  + align-items

    > 设置子元素在侧轴方向上的对齐方式

    + center 居中对齐
    + flex-start 顶对齐
    + flex-end 底对齐
    + stretch 拉伸
    + baseline 文本基线