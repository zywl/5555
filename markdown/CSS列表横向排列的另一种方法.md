CSS列表横向排列的另一种方法
***

列表`<ul>``<dl>`等默认是纵向排列。我们需要它横向排列时通常会用float来实现，但是使用了float也通常会引发一些排版问题。今天我学到了另一种方法：
设定`<li>`标签的display:inline，把`<li>`设定为内联元素来实现横向排列的效果，不需要使用float。

```html
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>列表横向排列的另一种方法</title>
<style type="text/css">
ul li{display:inline;background:#F93; padding:5px;}}
</style>
</head>

<body>
<ul>
    <li>Item1</li>
    <li>Item2</li>
    <li>Item3</li>
    <li>Item4</li>
</ul>
</body>
</html>
```
###效果：

http://ww1.sinaimg.cn/large/006eY07Igy1femertmf3ej306p016jri
 
等等，为什么li之间有空隙？？？
解决办法是：把li写成一行

```html
<ul>
    <li>Item1</li><li>Item2</li><li>Item3</li><li>Item4</li>
</ul>
```
对，就是写成这样子（不知道是不是bug）

http://ww1.sinaimg.cn/large/006eY07Igy1femetpel22j305w011jrg

这个方法有一个弊端：li转为内联元素后，width、height就无效了，只能用padding来撑开宽高。也有一些不便。自己根据需要取舍吧。

转载自:http://www.cnblogs.com/linyewei/p/4025515.html
