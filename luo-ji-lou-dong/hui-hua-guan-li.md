# 会话管理



HTTP协议的特性

* 无连接：每次连接只处理一个请求。服务器处理完客户的请求，并收到客户的应答后，即断开连接，采用这种方式可以节省传输时间。 
* 无状态：
  *  指协议对于事务处理没有记忆能力，服务器不知道客户端是什么状态。 ·
  * 我们给服务器发送HTTP请求之后，服务器根据请求，会给我们发送数据过来，但是发送完，不会记录任何信息。 
* 会话 ：执行会话最简单、最常见的方式是向每名用户发布一个唯一的会话令牌或标识符，用户在每一个请求中提交这个令牌。

## 令牌有含义

* 用户名称：如user、admin、system 
* 用户标识：如0001、0002、0003 
* 用户权限：如admin、00101、01000

有含义，有规律的令牌可能会被预测，权限验证参数应设置的较为复杂，使攻击者难以猜测其含义；权限验证参数不应显示在URL中；

Cookie数据存放在客户的浏览器上，可能影响机密性、完整性；Session数据放在服务器上，可能影响可用性，可采取重要信息存储在Session中，其他信息存储在Cookie中。

## 令牌可预测

用户令牌具有一定规律，可被他人预测，如： 

* 顺序码：身份证号、学号、手机号等
* 时间戳：当前时间、注册时间、或时间戳的变形

## 令牌可获取



用户令牌采取不安全的传输、存储，易被他人获取

* 用户令牌在URL中传输 ·
  * 明文传输 。
  * 发送给他人 
* 用户令牌存储在日志中 ·
  * 未授权用户易获取

## 令牌不失效

用户令牌采取不安全的传输、存储，易被他人获取

* 令牌有效期过长 
  * 是否需要在一段时间后使令牌失效？·
  * 是否需要在关闭浏览器时使令牌失效？ 
* 令牌尝试次数过多 ·可以考虑在令牌提交次数过多时候使令牌失效。 
* 无效的令牌重置的手段 ·注销后令牌是否还有效？

