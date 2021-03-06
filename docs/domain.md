# 主域301重定向

你的网站可能有多个域名访问，比如：`www.xuexb.com`、`xuexb.com`等，设置主域意思是不管用户输入哪个域名，都会`301`重定向到主域上，设置主域可以对`SEO`更友好，比如：

> 以xuexb.com为主域

```
www.xuexb.com => xuexb.com
www.xuexb.com/search/xxoo => xuexb.com/search/xxoo
www.xuexb.com/a/b/c/404.html => xuexb.com/a/b/c/404.html
```

配置文件核心：

```
server {
    # 设置多个域名
    server_name www.xuexb.com xuexb.com;

    # 判断host是不是xuexb.com，如果不是则直接301重定向，permanent表示301
    if ( $host != 'xuexb.com' ){
        rewrite ^/(.*)$ http://xuexb.com/$1 permanent;
    }
}
```

---

[点击查看nginx全局变量](https://echo.xuexb.com/api/dump/path?a=1&%E4%B8%AD%E6%96%87=%E5%A5%BD%E7%9A%84#123)
