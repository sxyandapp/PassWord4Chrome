**懒得看介绍的可直接下载：** https://gitee.com/sxyandapp/PassWord4Chrome/attach_files

---

chrome密码插件，能自动或手动保存密码到指定服务器，所有密码信息经过aes加密后上传。本地不保存任何密码信息。
此项目fork自github项目2PassWord：https://github.com/Likkrit/2PassWord.git
此项目对原项目进行了如下修改和优化：
	* 所有请求的地址中去掉了/.json的后缀
	* delete请求时，将请求参数通过url传输改为通过http请求的body传输
	* 添加手动添加密码功能
	* 其他界面优化

由于对请求进行了修改，因此不能保证还能正常使用Google Firebase或野狗云（google得翻墙，至于野狗云，感觉快倒闭了）。
如果你有自己的服务器，可以自己搭建服务器端（自己的才是安全的），亦或后期我会开放我的服务器供使用。

服务器端实现原理介绍：
此插件会将所有的数据通过http请求的body传输，消息体为json格式。
此插件目前共有3种类型的请求，get、patch、delete，下面分别介绍：
* get请求：
无任何参数，响应体直接相应json即可。
* patch请求：
请求的json格式中，key值为/分隔的属性列表，需要通过这个列表判断将value值追加到哪里，举例：
{"/data/id":"123456"}
表示需要将服务器端保存的对象的data属性的id属性修改为123456
响应体为空字符串或{}。

* delete请求：
请求的json格式和patch请求类似，不同的是通过key值列表判断要删除哪个属性;
响应体为空字符串或{}。

* 打包：通过chrome扩展功能管理的打包功能打包

---

 _原始作者及介绍：https://github.com/Likkrit/2PassWord.git_ 
