Nginx永久301跳转https写法
***
最近安装ssl证书,但是nginx如何转向https我百度了很久 ！

最终在国外找到以为大神的写法,很好用 
>作者:以下解决方案似乎很清楚简单，一切都在一个服务器块中定义。所以使用这个设置我强制一切到https：//www.domain.tld，所以两个处理程序在这里是非HTTPS和非WWW在HTTPS。有两个IF，但如果你不想重复整个SSL块两次来处理它...这是做的方式。
```php
server {
listen 80;
listen 443 ssl;

server_name domain.tld www.domain.tld; //自行改成自己的网站

# global HTTP handler
if ($scheme = http) {
        return 301 https://www.domain.tld$request_uri;
}

# global non-WWW HTTPS handler
if ($http_host = domain.tld){
        return 303 https://www.domain.tld$request_uri;
}
}
```
>转载自:http://stackoverflow.com/questions/32486739/force-www-and-https-in-nginx-conf-ssl/36777526#36777526
