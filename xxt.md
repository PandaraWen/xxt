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
  * [发布动态接口](#发布动态接口)
  * [发送反馈接口](#发送反馈接口)
  * [发送对话接口](#发送对话接口)
* 下行接口
  * [好友列表接口](#好友列表接口)
  * [动态列表接口](#动态列表接口)
  * [日历列表接口](#日历列表接口)
  * [对话详情接口](#对话详情接口)
  * [对话列表接口](#对话列表接口)
  * [个人详细信息接口](#个人详细信息接口)

接口说明
--------
<h1>上行接口</h1>

<h2>注册接口</h2>
域名:http://xxtforios.duapp.com/?op=regist&name=one&passwd=1
#### 请求参数
	* 姓名 -- name
	* 密码 -- passwd
	* 昵称 -- nick 可选
#### 返回字段
	* 错误标记 -- error
	* 信息 -- msg
	* 个人信息 -- data
#### 样例
	{
		error: 0
		msg: "access successfully"
		-data: {
			mauth: "b3bc6de7072711e6e50083a0d564bb89"
			nick: "十二宫"
			degree: ""
			name: "twelve"
			avatarurl: ""
		}
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
          * 头像url -- avatarurl
#### 样例
    	{
		error: 0
		msg: "login success"
		-data: {
			mauth: "bcf51899f50473a60454972e13c6158c"
			nick: "烧饼"
			degree: "博士"
			name: "pandara"
			avatarurl: http://xxtforphp-image.stor.sinaapp.com/avatar/pandara.jpeg
		}
	}
[↑返回顶部](#xxt)

<h2>发表动态接口</h2>
域名:http://xxtforios.duapp.com/?op=postfeed&mauth=69206c6971528ae2e0c32ddeb21653df&name=one&content=百度已经完全落后了么&option=1
#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth
	* 动态内容 -- content(可选)
	* 动态标题 -- title
	* 可见性设置 -- option，0:全局，1:盆友，2:自己，不设置默认为0
	* 动态类型 -- kind, 0:全部，1:只有朋友，2:只有自己，不设置默认0
#### 返回字段
  	* 错误标记 -- error
  	* 信息 -- msg
#### 样例
    {
        "error": 0,
        "msg": "access successfully"
    }
[↑返回顶部](#xxt)

<h2>发送反馈接口</h2>
域名:http://xxtforphp.sinaapp.com/?op=postfeedback&mauth=bcf51899f50473a60454972e13c6158c&name=pandara&content=做得非常棒
#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth
	* 反馈内容 -- content
#### 返回字段
  	* 错误标记 -- error
  	* 信息 -- msg
#### 样例
    {
        "error": 0,
        "msg": "access successfully"
    }
[↑返回顶部](#xxt)

<h2>发送对话接口</h2>
域名:http://xxtforphp.sinaapp.com/?op=postchat&mauth=bcf51899f50473a60454972e13c6158c&name=pandara&content=来聊聊天吧~&toname=one

#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth
	* 发送对象 -- toname
	* 对话内容 -- content
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
		* 标题 -- title
#### 样例
	{
	    "error": 0,
	    "msg": "access successfully",
	    "data": [
	        {
	            "title": "百度已经完全落后了么",
	            "content": "百度已经完全落后了么",
	            "name": "one",
	            "heat": "0",
	            "dateline": "1393395437",
	            "nick": "一"
	        },
	        {
	            "title": "百度已经完全落后了么",
	            "content": "百度已经完全落后了么",
	            "name": "one",
	            "heat": "0",
	            "dateline": "1393395406",
	            "nick": "一"
	        },
	        {
	            "title": "百度已经完全落后了么",
	            "content": "百度已经完全落后了么",
	            "name": "one",
	            "heat": "0",
	            "dateline": "1393394680",
	            "nick": "一"
	        },
	        {
	            "title": "腾讯与阿里巴巴的世界大战",
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
		* 创建日期 -- createdateline
#### 样例
	{
	    "error": 0,
	    "msg": "access successfully",
	    "data": [
	        {
	            "alarmdateline": "1410484438",
		        "createdateline": "1356784920",
	            "option": "0",
	            "content": "起床鸟"
	        }
	    ]
	}
[↑返回顶部](#xxt)

<h2>对话详情接口</h2>
域名:http://xxtforphp.sinaapp.com/?op=chatlist&mauth=bcf51899f50473a60454972e13c6158c&name=pandara&toname=one
#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth, name 与 mauth对应
	* 对话对象 -- toname
	* 页码 -- page, 默认0
	* 每页条数 -- perpage, 默认10
#### 返回字段
	* 错误标记 -- error
	* 信息 -- msg
	* 数据 -- data，字典
		* 发送方用户信息 -- fromuser 
		* 接收方用户信息 -- touser
		* 对话内容列表 -- chatlist
			* 对话的id -- id
			* 发送方的名字 -- fromname
			* 接收方的名字 -- toname
			* 对话内容 -- content
			* 发送日期 -- dateline
#### 样例
	{
		error: 0
		msg: "access successfully"
		-data: {
			-fromuser: {
				name: "pandara"
				nick: "烧饼"
				degree: "博士"
			}
			-touser: {
				name: "one"
				nick: "一"
				degree: "学士"
			}
			-chatlist: [
				-{
					id: "16"
					fromname: "pandara"
					toname: "one"
					content: "来聊聊天吧~012"
					dateline: "1393915635"
				}
				-{
					id: "15"
					fromname: "pandara"
					toname: "one"
					content: "来聊聊天吧~010"
					dateline: "1393915404"
				}
			]
		}
	}
[↑返回顶部](#xxt)

<h2>对话列表接口</h2>
域名:http://xxtforphp.sinaapp.com/?op=allchatlist&mauth=bcf51899f50473a60454972e13c6158c&name=pandara&page=0&perpage=1
#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth, name 与 mauth对应
	* 页码 -- page, 默认0
	* 每页 -- perpage, 默认10
#### 返回字段
	* 错误标记 -- error
	* 信息 -- msg
	* 数据 -- data，数组
		* 发送方用户名 -- fromname
		* 接收方用户名 -- toname
		* 最新一条对话内容 -- content
		* 最新一条对话时间 -- dateline
		* 对方的用户信息 -- touserinfo
#### 样例
	{
		error: 0
		msg: "access successfully"
		-data: [
			-{
				fromname: "pandara"
				toname: "three"
				content: "来聊聊天吧~005"
				dateline: "1393925106"
				-touserinfo: {
					name: "three"
					nick: "三"
					degree: "学士"
				}
			}
		]
	}
[↑返回顶部](#xxt)

<h2>个人详细信息接口</h2>
域名:http://xxtforphp.sinaapp.com/?op=detailinfo&mauth=bcf51899f50473a60454972e13c6158c&name=pandara
#### 请求参数
	* 姓名 -- name
	* 标识 -- mauth, name 与 mauth对应
	* 目标的用户名 -- name
#### 返回字段
	* 错误标记 -- error
	* 信息 -- msg
	* 数据 -- data，字典
		
#### 样例
	{
		error: 0
		msg: "access successfully"
		-data: {
			nick: "李敏镐"
			name: "one"
			degree: "学士"
			avatarurl: http://xxtforphp-image.stor.sinaapp.com/avatar/one.jpeg
			introduce: " 李敏镐是一个能使周围的气氛活跃起来的人。"
			discourse: "▪2013 日本韩流十周年大赏男演员部门第八名 李敏镐 （获奖）"
			program: "《继承者们》、韩版《城市猎人》、韩版《花样男子》、《信义》"
			school: "建国大学电影艺术学院"
			email: "ultraman_wen@sina.com"
		}
	}
[↑返回顶部](#xxt)

