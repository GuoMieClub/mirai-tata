# mirai-tata
tata through mirai

8.2事件后，酷Q跑路，通过酷Q搭建的獭进入死亡倒计时(有的已经死亡)。本篇教程意在帮助獭獭秽土转生。
本人不会编程，本篇教程全靠手动尝试与请教大佬。如有错误，概不负责。
獭獭的秽土转生目前主要有3种方式，皆通过mirai框架及其插件(`miraiOK`+`native`+`http`, `miraiOK`+`cqhttp-mirai`)和变体(`cqhttp-go`).

### 1. 搭建獭獭（三选一）

##### 1.1  `miraiOK`+`native`+`http` 套娃实现反向ws链接
1) 首先请自行下载[miraiOK](https://github.com/yimo0908/mirai-tata/raw/master/miraiOK.exe), [mirai-native插件](https://github.com/iTXTech/mirai-native/releases), [http插件包](https://github.com/yimo0908/mirai-tata/raw/master/httpapi.zip).

2) 新建一个文件夹(以英文命名, eg. tata)，将`miraiOK`放入其中并运行，使其自动生成框架相关文件和文件夹.

3) 关闭`miraiOK`，将`mirai-native- *. *. *.jar`放入`plugins`文件夹，再次启动`miraiOK`，等到控制台提示登录后关闭.

4) 将http插件包里的`http.dll` `http.json`放入`plugins\MiraiNative\plugins`文件夹，将其余文件放入`plugins\MiraiNative\libraries`文件夹.

5) 再次启动，
→若在控制台提示登录的下一行出现
>```
>[INFO] [MiraiNative] Native Plugin (w json) CQHTTP has been loaded with code 0
>```
则表示加载http插件成功，直接进行下一步.  

→若在控制台提示登录的下一行出现
>```
>[INFO] [MiraiNative] Native Plugin (w json) CQHTTP has been loaded with code 126
>```
则需要补全电脑的vc库，再进行下一步.

6) 将从獭窝下载的`QQ号.json`文件放入`plugins\MiraiNative\data\io.github.richardchien.coolqhttpapi\config`文件夹内（有些獭窝下载的是`config.json`文件，请自行重命名）

7) 启动`miraiOK.exe`，控制台出现登录提示后，在控制台输入

>login QQ账号 QQ密码

并回车，进行登录即可。  
————→若配置并登录成功，则会在控制台出现獭的配置信息，在`plugins\MiraiNative\data\io.github.richardchien.coolqhttpapi\log`文件夹也会出现相应日志。  
  
##### 1.2 `miraiOK`+`cqhttp-mirai` 直接实现反向ws链接

1) 首先请自行下载[miraiOK](https://github.com/yimo0908/mirai-tata/raw/master/miraiOK.exe), [cqhttp-mirai插件](https://github.com/yyuueexxiinngg/cqhttp-mirai/releases)

2) 新建一个文件夹(以英文命名, eg. tata)，将`miraiOK.exe`放入其中并运行，使其自动生成框架相关文件和文件夹.

3) 关闭`miraiOK`，将`cqhttp-mirai-. *. * -all.jar`放入`plugins`文件夹，再次启动`miraiOK.exe`，等到控制台提示登录后关闭.

4) 复制以下代码并更改`plugins\CQHTTPMirai\setting.yml`文件内容。
>``` yaml
># 本文件只测试了主窝 食材村(笔窝) 风窝 鸡窝，其他窝不一定适用，请自行尝试
>debug: true
># Debug日志输出选项
>'1234567890':
># 要进行配置的QQ号
>  cacheImage: true
>  # 是否缓存所有收到的图片
>  http:
>    enable: false
>    host: 0.0.0.0
>    port: 5700
>    accessToken: ""
>    postUrl: ""
>    # 事件及数据上报URL,即塔塔露提供的url
>    postMessageFormat: string
>    secret: ""
>  ws_reverse:
>    - enable: true 
>      # 可选，是否启用反向客户端,即是否启用獭獭
>      postMessageFormat: string
>      reverseHost: 
>      # 主窝 xn--v9x.net
>      # 食材村（笔窝）bot.pencilss.top
>      # 风窝 temp.dead-war.cn
>      # 鸡窝 tata.guomie.club
>      reversePort: 
>      # 主窝、食材村(笔窝)和鸡窝填80，风窝填8002
>      reversePath: /ws
>      useUniversal: true
>      reconnectInterval: 3000
>      accessToken: ""
>      # 访问口令，獭窝申请的时候的token
># 本文件只测试了主窝 食材村(笔窝) 风窝 鸡窝，其他窝不一定适用，请自行尝试
>```

5) 保存后启动`miraiOK.exe`，控制台出现登录提示后，在控制台输入

>login QQ账号 QQ密码

并回车，进行登录即可。  
————→若配置并登录成功，则会在控制台出现以下信息。
```
[DEBUG] [CQHTTPMirai] Host: bot.pencilss.top, Port: 80, Enable: true, Use Universal: true
[DEBUG] [CQHTTPMirai] bot.pencilss.top:80-Client-Universal 开始启动
[DEBUG] [CQHTTPMirai] bot.pencilss.top:80-Client-Universal Websocket Client启动完毕
```
信息根据窝的不同，会有差异。  

##### ~~1.3 `cqhttp-go` 直接实现反向ws链接~~  
~~先请自行下载 [go-cqhttp](https://github.com/Mrs4s/go-cqhttp/releases)~~

~~新建一个文件夹(以英文命名, eg. tata)，将`go-cqhttp.exe`放入其中并运行，使其自动生成框架相关文件和文件夹，然后关闭`go-cqhttp`，编辑`config.json`~~

~~**自己编辑，我也不会**~~  
`"uin"`: QQ账号  
`"password"`: "QQ密码"  
`"access_token"`: "獭獭のtoken"  
`"post_urls"`: {"塔塔露のurl": ""}  
`"reverse_url"`: "獭窝のws地址"
>```json 
>{
>	"uin": ,
>	"password": "",
>	"encrypt_password": false,
>	"password_encrypted": "",
>	"enable_db": true,
>	"access_token": "",
>	"relogin": true,
>	"relogin_delay": 3,
>	"http_config": {
>		"enabled": true,
>		"host": "0.0.0.0",
>		"port": 5700,
>		"timeout": 0,
>		"post_urls": {"": ""},
>		"post_message_format": "string"
>	},
>	"ws_config": {
>		"enabled": false,
>		"host": "0.0.0.0",
>		"port": 6700
>	},
>	"ws_reverse_servers": [
>		{
>			"enabled": true,
>			"reverse_url": "",
>			"reverse_api_url": "",
>			"reverse_event_url": "",
>			"reverse_reconnect_interval": 3000
>		}
>	],
>	"debug": false
>}
>```

~~保存后启动`go-cqhttp.exe`即可。~~


### 2. 自动登录

打开miraiOK**根目录**下的config.txt，会看到以下内容
```
#DEBUG
#NOUPDATE
#在----------下面可以添加需要在每次启动时输入得指令
#请注意，指令部分中#并不起效，miraiOK会原样输入到console
例如:
login 123456789 TestMiraiOK
say 655057127 MiraiOK_published!
----------
```
这些内容不用管，直接在最后加上 
>login QQ账号 QQ密码

并回车，保存文件即可实现自动登录。  
eg.  
```
#DEBUG
#NOUPDATE
#在----------下面可以添加需要在每次启动时输入得指令
#请注意，指令部分中#并不起效，miraiOK会原样输入到console
例如:
login 123456789 TestMiraiOK
say 655057127 MiraiOK_published!
----------
login 1234567890 0987654321

```
还可以写上
>say QQ号 [words]
 
即可在登录成功，插件加载完成后向该QQ号发送words对应的消息.(ps.[words]中不支持空格)  
eg.
>say 12332112345 hello_world

即可在登录成功，插件加载完成后向12332112345发送hello_world

### 3. 更新

##### 3.1 `miraiOK`+`native`+`http` 更新方式

关闭`miraiOK`，下载新的`mirai-native- *. *. *.jar`，将旧的删除，新的放进去，并将`plugins\MiraiNative`文件夹下的`CQP.dll`也删了，重启miraiOK.  

##### 3.2 `miraiOK`+`cqhttp-mirai` 更新方式

关闭`miraiOK`，下载新的`cqhttp-mirai-. *. * -all.jar`，将旧的删除，新的放进去，重启miraiOK.

##### ~~3.3 `cqhttp-go` 更新方式~~

~~关闭`cqhttp-go`，下载新的`cqhttp-go`，将旧的删除，重启`cqhttp-go` （大概）~~

### 4. QA与bug

QA没有，不想写。  
bug很多，也不想写  
自己[进群](https://jq.qq.com/?_wv=1027&k=5L3hY4w)问万能的群友，或者[百度](https://www.baidu.com)。
