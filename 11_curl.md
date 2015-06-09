# 11. curl中的http2

curl项目从2013年9月就开始对http2提供实验性的支持。

为了遵从curl的要旨，我们尽可能地支持http2的每个方面。curl通常被当作一个网站连接测试工具，希望这也能在http2上得以延续。

curl使用一个叫做[nghttp2](https://nghttp2.org/)的库来支持http2帧层的功能。

##11.1 跟HTTP 1.x非常相似 

curl会在内部把收到的http2头部转换为HTTP1.x风格的头部再呈现给用户，这样一来，它们就和目前的HTTP非常类似。这也使得无论是用curl还是HTTP，转换都非常容易。<!-- TOREVIEW -->类似地，curl会用相同的方式对发出的HTTP头部做转换，即发给curl的HTTP 1.x风格头部会在被发送到http2服务器之前完成转换。这使得户无需关心底层到底使用的是哪个版本的HTTP协议。

##11.2 不安全的纯文本

curl通过升级头部支持基于标准TCP的http2. 当发起一个使用http2的HTTP请求，如果可能，curl会请求服务器把连接升级到http2.<!-- TOREVIEW -->

##11.3 TLS和相关库

curl可以使用许多不同TLS的底层库来提供TLS支持，http2也得这样。TLS兼容http2的挑战来自于对APLN以及一些NPN扩展的支持。

基于最新版本的OpenSSL或NSS编译curl可以同时获得ALPN和NPN支持。而使用GnuTLS或PolarSSL只能得到ALPN。

##11.4 命令行中使用

无论是用纯文本还是通过TLS，必须使用`--http2`参数来让curl使用http2。默认未使用该参数的情况下，curl会使用HTTP/1.1。

##11.5 libcurl参数

应用程序和从前一样使用`https://`或者`http://`风格的URL，但你可以通过将`curl_easy_setopt`的`SURLOPT_HTTP_VERSION`参数设置为`CURL_HTTP_VERSION_2`来使libcurl尝试使用http2。它将优先尽可能地使用http2，如果不行的话，会继续使用HTTP 1.1。
