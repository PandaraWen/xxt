拯救地球
==============

版本：0.1  
作者：[文绍斌](mailto:ultraman_wen@sina.com)

本文档用于描述“拯救地球”的客户端接口
******************************
索引
----
* 上行接口
	*	[注册接口](#注册接口)
* 下行接口

接口说明
--------

<h2>注册接口</h2>
域名:http://xxtforios.duapp.com/?op=regist&name=one&passwd=1
#### 请求参数
	* 姓名 -- name
	* 密码 -- passwd
#### 返回字段
	* 错误标记 -- error
	* 信息 -- msg
#### 样例
{
  error: 0,
  msg: "access successfully",
}
[↑返回顶部](#拯救地球)
