# SoftwareReuseDiscuss
##用户登录后始终在线，考虑低带宽、不稳定网络。
------------------
- **长连接心跳机制**:
- **消息不遗漏**:
- **消息不重复**:
- **消息压缩**:

##长连接心跳机制
  - **出现原因** ：在使用长连接的前提条件下，为确认客户端是处于连接状态还是断开的状态。常见应用是app的推送的服务。
  - **机制原理** : 维护一个长连接都需要心跳机制。心跳机制便是客户端发送一个心跳给服务器，服务器给客户端一个心跳应答，这样就形成客户端服务器的一次完整的握手，这个握手是让双方都知道他们之间的连接是没有断开，客户端是在线的。如果超过一个时间的阈值，客户端没有收到服务器的应答，或者服务器没有收到客户端的心跳，那么对客户端来说则断开与服务器的连接重新建立一个连接，对服务器来说只要断开这个连接即可。
  - **TCP keepalive** : [RFC1122#TCP Keep-Alives](https://tools.ietf.org/html/rfc1122#page-101)
  - **Http Keep-Alive** : HTTP协议采用“请求-应答”模式，当使用普通模式，即非KeepAlive模式时，每个请求/应答客户和服务器都要新建一个连接，完成之后立即断开连接（HTTP协议为无连接的协议）；当使用Keep-Alive模式（又称持久连接、连接重用）时，Keep-Alive功能使客户端到服务器端的连接持续有效，当出现对服务器的后继请求时，Keep-Alive功能避免了建立或者重新建立连接。启用Keep-Alive模式肯定更高效，性能更高。因为避免了建立/释放连接的开销。![有无keep-alive的比较](https://www.byvoid.com/upload/wp/2011/07/450px-HTTP_persistent_connection.svg_.png)
    - **TCP与HTTP**
--------------------------
#####`4月10日`前提交到Github上
