JavaScript实现强制重定向至HTTPS页面
***
代码如下:
```javascript
<script type="text/javascript">
var targetProtocol = "https:";
if (window.location.protocol != targetProtocol)
 window.location.href = targetProtocol +
  window.location.href.substring(window.location.protocol.length);
</script>
```
使用方法:插入到 `</head> `前面就ok了！

SSL好不容易部署好了,发现访问不能 跳转到https！

调试了一个晚上nginx -t  什么301 强制跳转都不行╮(╯﹏╰)╭

后面发现这篇文章:<a href="http://www.jb51.net/article/67555.htm" target="_blank">JavaScript实现强制重定向至HTTPS页面</a>意外的发现还不错！虽然不知道对网站收录seo 什么有没有坏处 不管他 反正博客就是折腾!!!

>过几天写一写 这ssl 折腾过程吧！ 睡觉去了   忘记了 明天把多说评论框在https下坑填了
