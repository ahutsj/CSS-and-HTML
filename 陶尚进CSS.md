# CSS学习笔记
在学习CSS前，应具有一定的html基础。
## 什么是CSS
* CSS指层叠样式表 (Cascading Style Sheets)
* 样式定义如何显示HTML元素
* 样式通常存储在样式表中
* 把样式添加到 HTML 4.0 中，是为了解决内容与表现分离的问题
* 外部样式表可以极大提高工作效率
* 外部样式表通常存储在 CSS 文件中
* 多个样式定义可层叠为一个
HTML 标签原本被设计为用于定义文档内容，样式表定义如何显示 HTML 元素，就像 HTML 中的字体标签和颜色属性所起的作用那样。样式通常保存在外部的 .css 文件中。我们只需要编辑一个简单的 CSS 文档就可以改变所有页面的布局和外观。
## CSS语法
先看2个实例：
```css
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>AHUTSJ_CSS</title>
<style>
body {background-color:yellow;}
h1   {font-size:36pt;}
h2   {color:blue;}
p    {margin-left:50px;}
</style>
</head>

<body>

<h1>这个标题设置的大小为 36 pt</h1>
<h2>这个标题设置的颜色为蓝色：blue</h2>

<p>这个段落的左外边距为 50 像素：50px</p> 

</body>
</html>
```
```css
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>AHUTSJ_CSS</title>
<style>
body {background-color:tan;}
h1   {color:maroon;font-size:20pt;}
hr   {color:navy;}
p    {font-size:11pt;margin-left:15px;}
a:link    {color:green;}
a:visited {color:yellow;}
a:hover   {color:black;}
a:active  {color:blue;}
</style>
</head>

<body>

<h1>这是标题</h1>
<hr>

<p>你可以看到这个段落是
被设定的 CSS 渲染的。</p>

<p><a href="https://www.baidu.com" 
target="_blank">这是一个链接</a></p>

</body>
</html>
```
### CSS规则
CSS 规则由两个主要的部分构成：**选择器**，以及**一条或多条声明**:
`h1 {color:maroon;font-size:20pt;}}`
其中：h1是选择器，即需要改变样式的HTMl元素。
每条声明由一个属性和一个值组成。如 color 是属性，与之相对应的 maroon 是值；font-size是属性，20pt 是值。每个属性有一个值，属性和值被冒号分开。
CSS声明总是以分号(;)结束，声明总以大括号({})括起来:
`p {color:red;text-align:center;}`
为了让CSS可读性更强，你可以每行只描述一个属性:
```css
p
{
color:red;
text-align:center;
}
```
### CSS注释
CSS注释以 "/*" 开始, 以 "*/" 结束, 实例如下:
```css
/*这是个注释*/
p
{
text-align:center;
/*这是另一个注释*/
color:black;
font-family:arial;
}
```
## CSS id 和 class
如果你要在HTML元素中设置CSS样式，你需要在元素中设置"id" 和 "class"选择器。
### id选择器
id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式。HTML元素以id属性来设置id选择器,**CSS 中 id 选择器以 "#" 来定义**。以下的样式规则应用于元素属性 id="para1":
```css
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8"> 
<title>AHUTSJ_CSS</title> 
<style>
#para1
{
	text-align:center;
	color:red;
} 
</style>
</head>

<body>
<h1 id="para1">hello</h1>/*通过id与#para1匹配，选择只为此标题设置成之前预设的style*/
<h1>world</h1>
<p id="para1">Hello World!</p>/*通过id与#para1匹配，选择只为此段落设置成之前预设的style*/
<p>这个段落不受该样式的影响。</p>
</body>
</html>
```
**注意**： id属性不要以数字开头，数字开头的id在 Mozilla/Firefox 浏览器中不起作用。
### class选择器
class 选择器用于描述一组元素的样式，class 选择器有别于id选择器，class可以在多个元素中使用。class 选择器在HTML中以class属性表示, **在 CSS 中，类选择器以一个点"."号显示**：
```css
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
<style>
.center
{
	text-align:center;
}
</style>
</head>

<body>
<h1 class="center">标题居中</h1>/*所有拥有 center 类的 HTML 元素均为居中*/
<p class="center">段落居中。</p> /*所有拥有 center 类的 HTML 元素均为居中*/
</body>
</html>
```
同时也可以指定特定的HTML元素使用class：
```css
p.center
{
	text-align:center;/*所有的 p 元素使用 class="center" 让该元素的文本居中*/
    /*其余元素不受影响，如 h1 也有class="center"不受影响*/
}
```
**注意**：与id类似，类名的第一个字符不能使用数字！它无法在 Mozilla 或 Firefox 中起作用。
## CSS创建
当读到一个样式表时，浏览器会根据它来格式化 HTML 文档。
### 如何插入样式表
插入样式表的方法有三种：
* 外部样式表(External style sheet)
* 内部样式表(Internal style sheet)
* 内联样式(Inline style)
### 外部样式表
当样式需要应用于很多页面时，外部样式表将是理想的选择。在使用外部样式表的情况下，你可以通过改变一个文件来改变整个站点的外观。每个页面使用 link 标签链接到样式表。 link 标签在（文档的）头部：
```css
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
/*浏览器会从文件 mystyle.css 中读到样式声明，并根据它来格式文档*/
</head>
```
外部样式表可以在任何文本编辑器中进行编辑。文件不能包含任何的 html 标签。样式表应该以 .css 扩展名进行保存。下面是一个样式表文件的例子：
```css
hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("/images/back40.gif");}
```
**注意**：不要在属性值和单位之间加上空格。如:"margin-left: 20 px"，正确的写法是 "margin-left: 20px"。
### 内部样式表
由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势。请慎用这种方法，例如当样式仅需要在一个元素上应用一次时。要使用内联样式，你需要在相关的标签内使用样式（style）属性。Style 属性可以包含任何 CSS 属性。本例展示如何改变段落的颜色和左外边距：
`<p style="color:sienna;margin-left:20px">这是一个段落。</p>`


