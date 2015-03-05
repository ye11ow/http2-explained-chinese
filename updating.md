# 4. 升级HTTP（未完成）

改善HTTP协议显然是极好的。我们可以着手于以下几个方面：

  1. 降低协议对延迟的敏感
  2. 修复pipelining和head of line blocking的问题
  3. 防止主机需求更多连接数量
  4. 保持所有现有的接口，内容，URI格式和结构
  5. 由IETF的HTTPbis工作组来建立

**4.1. IETF和HTTPbis工作组**

The Internet Engineering Task Force (IETF)是一个开发和推广互联网标准的组织，主要是协议层面。他们最出名的工作是TCP、DNS、FTPRFC

**4.1.1. **

**4.2. http2起源于SPDY**

SPDY是由Google牵头开发的协议。

当HTTPbis小组决定开始制定http2的时候，SPDY已经充分证实了它是一个非常好用的方案。当时已经有人成功部署SPDY，并且也有一些文章讨论他的性能。因此，http2便采用了SPDY/3草案，进行一些修改之后发布了http2的draft-00