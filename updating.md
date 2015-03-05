# 4. 升级HTTP（未完成）

改善HTTP协议显然是极好的。我们可以着手于以下几个方面：

  1. 让协议不要太对延迟敏感
  2. 修复pipelining和head of line blocking的问题
  3. 防止主机继续的需求更多连接数量
  4. 保持所有现有的接口，内容，URI格式和结构
  5. 由IETF的HTTPbis工作组来建立

**4.1. IETF和HTTPbis工作组**

**4.1.1. **

**4.2. http2起源于SPDY**

SPDY是由Google牵头开发的协议。

当HTTPbis小组决定开始制定http2的时候，SPDY已经充分证实了它是一个非常好用的方案。当时已经有人成功部署SPDY，并且也有一些文章讨论他的性能。因此，http2便采用了SPDY/3草案，进行一些修改之后发布了http2的draft-00