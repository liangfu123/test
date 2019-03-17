# html
##文本格式化标签

+ <b></b><strong></strong> 粗体
+ <i></i><em></em> 斜体
+ <s></s><del></del> 加删除线
+ <u></u><ins></ins> 加下划线

>strong em del ins 强调

##特殊字符
	&lt;(小于号<)
	&gt;(大于号>)
##列表标签

+ 无序列表ul(重点)

+ 有序列表ol

+ 自定义列表(理解)

  ```
  	<dl>
  		<dt>名词1</dt>
  		<dd>名词1解释1</dd>
  		<dd>名词1解释2</dd>
  	</dl>
  ```

##表格table
###表格属性
>border
>cellspacing 设置单元格与单元格边框间距
>cellpadding 设置单元格内容与单元格边框间距
>width
>height
>align

###表头标签
	<th></th>
###表格标题
	<caption></caption>(该标签只能在table标签之后)
###合并单元格
	跨行合并：rowspan
	跨列合并：colspan
##表单标签
###input控件
+ type
  + text
  + password
  + radio(单选按钮)
  + checkbox(复选框)
  + button
  + submit
  + reset
  + image(图像形式的提交按钮)
  + file(文件域)

+ name
+ value
+ size(input控件在页面中显示的宽度)
+ checked
+ maxlength(正整数；控件允许输入的最多字符数)

###label标签
>作用：  用于绑定一个表单元素, 当点击label标签的时候, 被绑定的表单元素就会获得输入焦点
```
<label for="male">Male</label>
<input type="radio" name="sex" id="male" value="male">
```
###textarea控件(文本域)
```
<textarea cols="每行中的字符数" rows="显示的行数">
  文本内容
</textarea>
```
###下拉菜单select
###表单域form
#CSS
##css选择器
###1.标签选择器(元素选择器)
###2.类选择器(class)
+ 多类名选择器

```
<div class="pink fontWeight font20">亚瑟</div>
<div class="font20">刘备</div>
<div class="font14 pink">安其拉</div>
```
###3.id选择器
> id选择器和类选择器的区别：使用次数。
>
> id选择器 是唯一的；而一个标签类名可以有多个。同一个页面，不允许出现相同名字的id，允许相同名字的class。

###4.通配符选择器
	"*"
##css复合选择器
###1.交集选择器
	p.one   选择的是： 类名为 .one  的 段落标签。
###2.并集选择器
	.one, p , #test {color: #F00;}(只要逗号隔开)
###3.后代选择器
	.class h3 {color: red;}
###4.子元素选择器
	.demo > h3 {color: red;}   说明  h3 一定是demo 亲儿子。  demo 元素包含着h3
###5.伪类选择器
+ 链接伪类选择器

  + :link 未访问的链接

  + :visited 已访问的链接 

  + :hover 鼠标移动到链接上

  + :active 选定的链接

    > 注意书写时按顺序：lv ha

##css字体样式属性

+ font-size

  相对长度单位：
  	em(相对当前对象内文本的字体尺寸)
  	px

+ font-family(字体)

		css Unicode字体(解决设置中文字体编码错误)

```
p{font-family:"微软雅黑";}
```
+ font-weight:字体粗细

		属性值：normal,bold,bolder,lighter,100~900
	400=normal,700=bold

+ font-style:字体风格

		italic(斜体)

+ font:综合设置字体样式(重点)

		选择器{font:font-style font-weight font-size font-family;}
	注意：可以省略（取默认值），但必须保留font-size和font-family,必须顺序书写

##css外观属性
+ color
+ line-height:行间距
+ text-align:文本内容水平对齐方式
+ text-indent:首行缩进
+ text-decoration:文本装饰
   + none
   + underline(下划线)
   + overline(文本上的一条线)
   + line-through(穿过文本的一条线)

##标签显示模式(display)
###1.块元素(block-level)
>独占一行或多整行，可以设置宽度(默认是容器的100%)、高度、对齐等
>常见：<h1>~<h6>,<p>,<div>,<ul>,<ol>,<li>

###2.行内元素(inline-level)
>和相邻的行内元素在一行上，宽高无效；水平上padding和maigin可以设置，竖直方向无效
>常见：<a>、<strong>、<b>、<em>、<i>、<del>、<s>、<ins>、<u>、<span>

###3.行内块元素(inline-block)
> 常见：<img />,<input />,<td>

###4.标签显示模式转换  display
+ display:inline;
+ display:block;
+ display:inline-block;

##css三大特性
+ 层叠
+ 继承
+ 优先级
  + 继承或者* 0,0,0,0
  + 标签           0,0,0,1
  + 类，伪类   0,0,1,0
  + id               0,1,0,0
  + 行内样式   1,0,0,0
  + !important 无穷大

> 权重可以叠加

##css背景background
+ background-position背景位置
+ background-repeat是否重复
+ background-attachment背景固定还是滚动

##css盒子模型
###盒子边框border
+ border-style
  + none
  + solid实线
  + dashed虚线

```
border : border-width || border-style || border-color 
```
+border-radius圆角边框css3

###内边距padding
>边框与内容之间的距离

+ 一个值：上下左右
+ 两个值：上下，左右
+ 三个值：上，左右，下
+ 四个值：上，右，下，左（顺时针）

###外边距margin

> 取值顺序与内边距相同

###外边距实现盒子居中
>margin:0 auto;
>背景图片更改位置：background-position

###清除元素的默认内外边距
```
{
   padding:0;         
   margin:0;          
}
```
###解决外边距塌陷
+ 相邻块元素垂直外边距的合并，解决方案
  + 1.可以为父元素定义1像素的上边框或上内边距。
  + 2.可以为父元素添加overflow:hidden。

###盒子阴影
+ box-shadow

```
box-shadow:水平阴影 垂直阴影 模糊距离 阴影尺寸 阴影颜色  内/外阴影；

box-shadow: 0 15px 30px  rgba(0, 0, 0, .4);
```
###浮动float
###清除浮动
>选择器{clear:both;}
>left,right,both

> overflow:hidden;

## 定位position

### 静态定位static

### 相对定位relative

> 相对于自身的位置
>
> 不脱标
>
> 占有位置

### 绝对定位absolute

> 相对于已定位的父级元素移动
>
> 若父元素没有丁诶，以浏览器当前窗口为准对齐
>
> 完全脱标
>
> 不占位置

### 固定定位fixed

> 固定定位与父元素没关系，只认浏览器
>
> 完全脱标
>
> 不占位置
>
> 不随着滚动条滚动

#### 子绝父相

> 子级用绝对定位，不占位置，可以放到父盒子的任意地方
>
> 父级用相对定位，占位置

#### 加定位，浮动的盒子居中对齐

> 加了定位和浮动的盒子，margin:0 auto;失效

> 解决办法：left 50% + margin-left盒子宽度的一半（负值）

####叠放次序(z-index)

> 例如：z-ind    ex:999;

> 注意：z-index只有在定位中才能用，取值越大，层级越高



