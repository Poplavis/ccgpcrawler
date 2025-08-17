# ccgpcrawler
A python crawler for ccgp site.
Due to legal issues, only the implementation plan is explained here.
由于爬虫涉及法律问题，这里仅对实现方案做简单解释。

## 使用python框架
1. DrissionPage - 驱动浏览器完成浏览器初始化与图形验证码测试
2. Httpx - 轻量型爬虫框架，快速抓取接口数据

## 网站分析

网站设计了很多反扒策略

1. 图片验证码

通过图片验证码就可以拦截大部分爬虫，如BaiduSpider等，经过测试，也可以看到，百度并不能搜索到ccgp相关数据。

网站的验证码还是用了特殊的图片，色差非常低，人眼分辨也存在一定难度。

这一步使用了手工处理，**DrissionPage**驱动浏览器打开网站，并手动处理图形验证码。

2. 加密接口

数据请求接口是根据图片验证码识别结果生成的加密接口，且有效期极短。

且数据接口需要按照格式发起请求，请求格式不对，响应就是406或者500。

特别需要注意headers参数设置。

---

处理了以上问题，就可以爬取数据了。
