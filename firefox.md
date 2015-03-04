# Firefox里的http2

Firefox紧跟着http2的草案，并且很早之前就实现了它的测试环境。在http2协议开发的时候，客户端和服务器需要支持协议草案的版本，这也让测试变得非常繁琐。请一定注意你的客户端和服务器需要协商好它们支持的版本。

**9.1. 首先，确保它已被启用**

从发布于2015年1月13日的Firefox 35之后，http2支持是默认开启的。

在地址栏里进入'about:config'，再搜索一个名为“network.http.spdy.enabled.http2draft”的选项，确保它被设置为`true`。

***9.2. TLS-only**

请记住Firefox只在TLS上实现了http2。你只会在看到http2只在`https://`的网站里得到支持。

**9.3. 透明！**

【图片】截图表Firefox正在使用http2 draft-12


在UI上，没有任何元素标明你正在使用http2。但想确认也并不复杂，一种方法是启用“Web developer->Network”，再查看响应头里面服务器发回来的内容。这个响应是“HTTP/2.0”，并且Firefox也插入了一个自己头“X-Firefox-Spdy:”，如上面截图所示。

你在这里看到的头文件是网络工具把二进制的http2格式转换成类似HTTP 1.x显示方式的文本格式。

**9.4. 图形化HTTP/2**

有一些Firefox的插件可以图形化HTTP/2，比如[SPDY Indicator](https://addons.mozilla.org/en-US/firefox/addon/spdy-indicator/)。