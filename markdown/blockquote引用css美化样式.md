blockquote引用css美化样式
***
>原本的`blockquote`样式不好看;作为一个不会写代码的小白后面就百度一下找到了几个不错的`blockquote`css样式,就分享给大家了

样式1
===
```css
blockquote {
	background: #f9f9f9;
	border-left: 10px solid #ccc;
	margin: 1.5em 10px;
	padding: .5em 10px;
	quotes: "\201C""\201D""\2018""\2019";
}

blockquote:before {
	color: #ccc;
	content: open-quote;
	font-size: 4em;
	line-height: .1em;
	margin-right: .25em;
	vertical-align: -.4em;
}

blockquote p {
	display: inline;
}
```
效果图:

http://ww1.sinaimg.cn/large/006eY07Igy1femdx8jfayj30l503m0sq

样式2
===
```css
blockquote{
  display:block;
  background: #fff;
  padding: 15px 20px 15px 45px;
  margin: 0 0 20px;
  position: relative;
 
  /*字体*/
  font-family: Georgia, serif;
  font-size: 16px;
  line-height: 1.2;
  color: #666;
  text-align: justify;
  
  /*边框 - (选项)*/
  border-left: 15px solid #c76c0c;
  border-right: 2px solid #c76c0c;
 
  /*盒子阴影 - (选项)*/
  -moz-box-shadow: 2px 2px 15px #ccc;
  -webkit-box-shadow: 2px 2px 15px #ccc;
  box-shadow: 2px 2px 15px #ccc;
}
blockquote::before{
  content: "\201C"; /*左双引号的Unicode编码*/
 
  /*字体*/
  font-family: Georgia, serif;
  font-size: 60px;
  font-weight: bold;
  color: #999;
 
  /*位置*/
  position: absolute;
  left: 10px;
  top:5px;
}
blockquote::after{
  content: ""; /*如果要显示右双引号，则写 content: "\201D"; */
}
```

效果图:

http://ww1.sinaimg.cn/large/006eY07Igy1femdy5sx0ij30dw04s0tb

样式3
===
```css
blockquote {
 background-color: #eae6f3;
 border-left: 1em solid #5236a0;
 margin: 1.0em 0 1.0em;
 padding: 1em 1em 1em 1em;
 position: relative;
 color: #888;
}
blockquote:before {
  color: #392570;
  content: "\201C";
  font-size: 5em;
  line-height: 0em;
  margin-right: 0em;
  vertical-align: -0.4em;
}
blockquote:after {
  color: #392570;
  content: "\201D";
  font-size: 5em;
  position:absolute;
  right:3px;
  bottom: 0em;
  line-height: 0.1em;
}
```
效果图:

http://ww1.sinaimg.cn/large/006eY07Igy1femdyhalvqj30dw04maah

样式4
===
```css
Blockquote {
	background: #d9e9ff;
	padding: 10px 15px 10px 15px;
	margin: 1em 3em 1em 3em;
	font-size: .8em;
	border-style: dotted dotted dotted solid;
	border-width: 1px 1px 1px 5px;
	border-color: #5bbcdd;
	line-height: 200%;
}   
```
效果图:

http://ww1.sinaimg.cn/large/006eY07Igy1feme0ie1pbj30kf02y74h

样式5
===
```css
blockquote {
	color: #2b2b2b;
	background: url(images/patt.png) repeat;
	margin: 10px 20px;
	padding: 8px 16px;
	border: 1px solid  #CCC;
	border-radius: 5px;
	-webkit-border-radius: 5px;
	-moz-border-radius: 5px;
}  
```
效果图:

http://ww1.sinaimg.cn/large/006eY07Igy1feme1ti4qsj30jv06u0tf

样式6
===
```css
blockquote:before, blockquote:after, q:before, q:after {
	content: "";
}

blockquote, q {
	quotes: "" "";
}

blockquote {
	margin: 1.5em;
	color: #666;
	font-style: italic;
}

blockquote {
	padding: 0 0 0 15px;
	margin: 0 0 18px;
	border-left: 5px solid #eee
}

blockquote {
	border-color: #ddd;
	border-color: rgba(0,0,0,0.15)
}  
```
效果图:

http://ww1.sinaimg.cn/large/006eY07Igy1feme318p38j30hf09q75i

>以上代码来自网络，版权原作者所有！
