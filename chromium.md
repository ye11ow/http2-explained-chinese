# Chromium里的http2（未校对）

Chromium团队已经实现了HTTP/2并且很早之前就在dev和beta分支里面提供了支持。从2015年1月27日发布的Chrome 40起，http2已经默认为一些用户启用。刚开始用户的数量会很少，但会慢慢增加。

SPDY的支持将会被移除。在2015年2月的一篇博客里面有如下一段话：

Chrome has supported SPDY since Chrome 6, but since most of the benefis are present
in HTTP/2, it’s time to say goodbye. We plan to remove support for SPDY in early 2016


**10.1. 首先，确保它已被启用**