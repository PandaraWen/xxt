xxt
==============

版本：0.1  
作者：[文绍斌](mailto:ultraman_wen@sina.com)

本文档用于描述“xxt”的客户端接口
******************************
索引
----
* 上行接口
  * [注册接口](#注册接口)
  * [登陆接口](#登陆接口)
* 下行接口
  * [好友列表接口](#好友列表接口)
  * [动态列表接口](#动态列表接口)
  * [日历列表接口](#日历列表接口)
 
接口说明
--------
<h1>上行接口</h1>

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
[↑返回顶部](#xxt)

<h2>登陆接口</h2>
域名:http://xxtforios.duapp.com/?op=login&name=one&passwd=1
#### 请求参数
	* 姓名 -- name
	* 密码 -- passwd
#### 返回字段
	* 错误标记 -- error
	* 信息 -- msg
        * 数据 -- data，字典
          * 标识 -- mauth
          * 昵称 -- nick
          * 学位 -- degree
          * 用户名 -- name
#### 样例
    { 
      error: 0,
      msg: "login success",
      data: {
        mauth: "69206c6971528ae2e0c32ddeb21653df",
        nick: "一",
        degree: "学士",
        name: "one"
      }
    }
[↑返回顶部](#xxt)

<h2>发表动态接口</h2>
域名:http://xxtforios.duapp.com/?op=postfeed&mauth=69206c6971528ae2e0c32ddeb21653df&name=one&content=百度已经完全落后了么&option=1
#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth
	* 动态内容 -- content
	* 可见性设置 -- option，0:全局，1:盆友，2:自己，不设置默认为0
#### 返回字段
  	* 错误标记 -- error
  	* 信息 -- msg
#### 样例
    {
        "error": 0,
        "msg": "access successfully"
    }
[↑返回顶部](#xxt)

<h1>下行接口</h1>

<h2>好友列表接口</h2>
域名:http://xxtforios.duapp.com/?op=friendlist&mauth=69206c6971528ae2e0c32ddeb21653df&name=one
#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth, name 与 mauth对应
#### 返回字段
	* 错误标记 -- error
	* 信息 -- msg
	* 数据 -- data，数组
		* 昵称 -- nick
		* 学位 -- degree
		* 用户名 -- name
#### 样例
    {
        "error": 0,
        "msg": "access successfully",
        "data": [
            {
                "name": "three",
                "degree": "学士",
                "nick": "三"
            },
            {
                "name": "pandara",
                "degree": "博士",
                "nick": "烧饼"
            }
        ]
    }
[↑返回顶部](#xxt)

<h2>动态列表接口</h2>
域名:http://xxtforios.duapp.com/?op=feedlist&mauth=69206c6971528ae2e0c32ddeb21653df&name=one&perpage=10&page=1
#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth, name 与 mauth对应
	* 每页 -- perpage, 默认10
	* 页码 -- page, 默认0
#### 返回字段
	* 错误标记 -- error
	* 信息 -- msg
	* 数据 -- data，数组
		* 昵称 -- nick
		* 用户名 -- name
		* 热度 -- heat
		* 发布时间 -- dateline
		* 内容 -- content
#### 样例
	{
	    "error": 0,
	    "msg": "access successfully",
	    "data": [
	        {
	            "content": "百度已经完全落后了么",
	            "name": "one",
	            "heat": "0",
	            "dateline": "1393395437",
	            "nick": "一"
	        },
	        {
	            "content": "百度已经完全落后了么",
	            "name": "one",
	            "heat": "0",
	            "dateline": "1393395406",
	            "nick": "一"
	        },
	        {
	            "content": "百度已经完全落后了么",
	            "name": "one",
	            "heat": "0",
	            "dateline": "1393394680",
	            "nick": "一"
	        },
	        {
	            "content": "腾讯与阿里巴巴的世界大战",
	            "name": "pandara",
	            "heat": "0",
	            "dateline": "1393387170",
	            "nick": "烧饼"
	        }
	    ]
	}
[↑返回顶部](#xxt)

<h2>日历列表接口</h2>
域名:http://xxtforios.duapp.com/?op=calendarlist&mauth=69206c6971528ae2e0c32ddeb21653df&name=one
#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth, name 与 mauth对应
#### 返回字段
	* 错误标记 -- error
	* 信息 -- msg
	* 数据 -- data，数组
		* 提醒日期 -- alarmdateline
		* 重复设置 -- option
		* 提醒内容 -- content
#### 样例
	{
	    "error": 0,
	    "msg": "access successfully",
	    "data": [
	        {
	            "alarmdateline": "1410484438",
	            "option": "0",
	            "content": "起床鸟"
	        }
	    ]
	}
[↑返回顶部](#xxt)



