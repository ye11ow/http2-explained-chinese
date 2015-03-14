#curl中的http2

curl项目从2013年9月就开始对http2提供实验性的支持。

为了遵从curl的要旨，我们尽可能地支持http2的每个方面。curl通常被当作一个测试工具，用以连接网站，希望这些能在http2上得以延续。

curl使用一个独立的库——[nghttp2](https://nghttp2.org/)来支持http2架构的功能。

##11.1 像HTTP 1.x 一样 

curl会在内部把收到的http2头部转换为HTTP1.x风格的头部再递交给用户，这样一来，它们就和目前的HTTP非常类似，使得无论是用curl还是HTTP，转换都非常容易。类似地，curl会用相同的方式对发出的HTTP头部做转换，即发给curl的HTTP 1.x风格头部会在被连接到http2服务器之前完成转换。这同时也使用户无需关心底层到底使用的是HTTP哪个版本的协议。

##11.2 不安全的纯文本
curl通过升级头部支持基于标准TCP的http2. 当发起一个使用http2的HTTP请求，如果可能，curl会请求服务器把连接升级到http2.

##11.3 TLS和相关库
由于curl的TLS后端，它支持相当大范围的TLS库，并且此后端对http2的支持依然有效。LTS兼容http2的挑战来自于对APLN以及一些NPN扩展的支持。

基于最新版本的OpenSSL或NSS编译curl可以同时获得ALPN和NPN支持，而使用GunTLS或PolarSSL只能得到ALPN。

##11.4 命令行中使用
无论是用纯文本还是通过TLS，必须使用 -http2 选项告知curl使用http2。默认情况下，curl依旧使用HTTP/1.1。

##11.5 libcurl 选项

应用程序和从前一样使用https:// 或者 http:// 链接，但如果设置了curl_easy_setopt的SURLOPT_HTTP_VERSION 选项为 CURL_HTTP_VERSION_2 使libcurl尝试使用http2，它将在配合HTTP1.1的基础上，尽可能地使用http2。
