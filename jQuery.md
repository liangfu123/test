# JQuery库

## Jquery语法

* $(selector).action()
  * $:定义jQuery
  * (selector):查询和查找html元素
  * action()执行对元素的操作
    * $(this).hide()隐藏当前元素
    * $("p").hide()隐藏p标签元素
    * $("#test").hide()隐藏id为test的元素
    * $(".test").hide()隐藏class="test"的元素

## Jquery选择器

* 元素选择器
  * $("p")
  * $("p.test")
  * $("p#test")
* 属性选择器
  * $("[href]")选取所有带href属性的元素
  * $("[href='#']")选取所有带href属性值为#的元素
  * $("[href!='#']")
* css选择器

## Jquery事件

* ready()文档就绪

  ```javascript
  $(document).ready(function(){
      //在文档加载后激活该函数
  });
  ```

* change()

* click()

* focus()

* submit()

* ...

## Jquery效果函数

* show()
* hide()
* toggle()在元素的显示与隐藏间切换
* animate()
* ...

## Jquery文档操作方法

* addClass()
* after()
* append()
* attr()设置或者返回被选元素的属性值
* empty()
* remove()
* relpace()

## Jquery属性操作方法

* attr()
* html()
* val()

## Jquery AJAX请求

* $.ajax(options)

  * contentType
  * data
  * dataType
  * success
  * type
  * url

  ```javascript
  $.ajax({
      type: "POST",
      url: "some.do",
      data: "",
      success: function(data){
          alert(data);
      }
  });
  ```

* $.get(url,data,callback,type)

  * data             Map

  * callback       function

  * type              String           xml,html,script,json,text

    ```   javascript
    $.get("product.do",{name: "liangfu",age: 20},function(data){
        alert(data);
    },"json")
    ```

* $.post(url,data,callback,type)

* $.getJSON(url,data,callback)

  ```javascript
  $.getJSON("test.js", { name: "John", time: "2pm" }, function(json){
    alert("JSON Data: " + json.users[3].name);
  });
  ```

* $(selector).load(url,data,callback)

  * data              Map,String

  ```javascript
  $("#sub").load("product.do",{name : "梁富"},function(data){
     alert(data); 
  });
  ```

  

