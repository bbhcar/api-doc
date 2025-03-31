BBH Software 软件接口

API 地址前缀: https://www.bbhcar.top/api

除了登录接口和地址中带有/anonymous/的接口,其余所有接口需要在header添加

```
Header Authorization: Bearer token  
#token 为登录接口返回的 token
```

- 登录接口
  /auth/token 请求方式: POST, Body  输入用户名密码

```
{
    "username":"admin",
    "password":"P@ssw0rd"
}
```

返回

```
{
    "token": "eyJhbGciOiJIUzUxMiJ9.eyJodHRwczovL2JiaGNhci5jb20vY2xhaW0vcm9sZXMiOlsiUk9MRV9BRE1JTiIsIlJPTEVfVVNFUiJdLCJodHRwczovL3ZhZ3Rvb2xzLmNvbS9jbGFpbS9tb2JpbGUiOiIxMzg4ODg4ODg4OCIsImh0dHBzOi8vYmJoY2FyLmNvbS9jbGFpbS9lbmFibGVkIjp0cnVlLCJodHRwczovL2JiaGNhci5jb20vY2xhaW0vdXNlcm5hbWUiOiJhZG1pbiIsImV4cCI6MTc0MDkyNTQ0OCwiaHR0cHM6Ly9iYmhjYXIuY29tL2NsYWltL2NyZWF0ZWQiOjE3NDAzMjA2NDg3MTksImh0dHBzOi8vYmJoY2FyLmNvbS9jbGFpbS91c2VySWQiOiI4ODdkZTc4NjgwMDg0ZTRhOTdkYTJjYTAxMDhlOWEyMiJ9.zLP0zLYlDjyngn5qFGbl16mYAb43-oVA_TyT0rs6od-EIZp5moQ0UmdCrslMIGPxfCh_vAMCLVDbefZ6B-8Qhw"
}
```

![1](https://github.com/user-attachments/assets/80cd5b63-2e64-48ed-b20f-5fb5fe89da00)

登录过程中第2个接口，获取用户信息，和判断用户是否有BBH权限：

user/profile GET请求

Authorization - Bearer Token == “登录时候的token”

```
返回：
{
    "id": "147cda6eeba34345ba1d8aaf5bda5a47",
    "changeVersion": 0,
    "createdBy": "887de78680084e4a97da2ca0108e9a22",
    "createdDate": 1742921396000,
    "lastModifiedBy": "887de78680084e4a97da2ca0108e9a22",
    "lastModifiedDate": 1742922845000,
    "username": "admin",
    "password": "",
    "mobile": "+1-2705515111",
    "status": true,
    "roles": [
        "ROLE_USER",
        "ROLE_ADMIN",
        "ROLE_BBH"
    ],
    "comboId": "b2455f95054341609b6652a5c250fc89",
    "comboName": "Internationality",
    "expireTime": 4082457600000,
    "userType": "4",
    "realName": "刘书宝",
    "remark": "Audi Vito",
    "port": "vWpI58fj3hIPvmUUazwqLiWjOX+sADiTyY41WCmrdyZ1wlIuYRRKjb+bnXT9HW5XySLXoIxSSGn3pGEWbFj+dM0Tk+83MzeeHadpzagQ/ojTgF9Gpi2B1yUnse264beIczgZv+tF14F2nuh1b+rlAywZ3sd+XivLgi1eqfFIYj654V8Yufjrvz6vu6ym8bXuj2PHDJjymHrjod2VHIBYXcrnNQYIa/46X2ONJ5S3n0E=",
    "online": false,
    "clientOnline": false,
    "serverOnline": false,
    "combo": {
        "id": "b2455f95054341609b6652a5c250fc89",
        "comboName": "Internationality",
        "comboContent": "USB国内+USB国际+DOIP国内+DOIP国际+SoftEther VPN国际+SoftEther VPN国内+全球加速",
        "comboPrice": "355欧元含税",
        "comboValidity": "365",
        "comboItems": [
            {
                "id": "7e09c882b44e43be8ad40469b912fb80",
                "itemName": "USB国内",
                "areaType": 1,
                "itemSort": 1
            }
        ]
    },
    "connectType": "USB",
    "connectIp": "47.122.127.90",
    "connectPort": "12345"
}
```

判定其中：

"roles": [
        "ROLE_BBH" 如果有则可以登录，如果没有则提示“当前用户无权限”

取其中信息显示到软件中：

 "comboName": "Internationality", 用户权限（套餐）

 "username": "admin", 用户名称

 "expireTime": 4082457600000, 到期时间（需要对时间戳进行转换明文）
 
 
![2](https://github.com/user-attachments/assets/42bec69d-2a6a-40f7-8043-813622b7ea8a)

此处为用户登录完的第一界面，如果在此界面没有操作超过60秒，则自动关闭软件。

此处点击客户端调用接口获取服务器列表：

  /program/server/getServerList?areaType=1&pageNo=1&pageSize=20 国内

  /program/server/getServerList?areaType=2&pageNo=1&pageSize=20 国际

Authorization - Bearer Token == “登录时候的token”

请求方式 GET areaType 1 = 国内 2 = 国际  （此处可以通过用户列表判断"areaType": 为1还是为2,还是都有）

如果只有1 则请求国内，如果只有2则请求国际，如果同时有1和2，则请求国内和国际。

返回：例如国内：

```
{
    "data": [
        {
            "id": "e9b40d63c3c142f6a940e1c4c96773d0",
            "changeVersion": 0,
            "createdBy": "admin1",
            "createdDate": 1742747172000,
            "lastModifiedBy": "admin1",
            "lastModifiedDate": 1742747172000,
            "serverAddr": "47.122.127.90",
            "domain": "ccn.bbhcar.com",
            "serverName": "Central China",
            "areaDesc": "华中-武汉",
            "areaType": 1
        }
    ],
    "paging": {
        "firstPage": 1,
        "lastPage": 1,
        "nextPage": 0,
        "prevPage": 0,
        "currentPage": 1,
        "totalPage": 1,
        "rowCount": 5,
        "pageSize": 20,
        "hasNext": false,
        "hasPrev": false,
        "hasFirst": true,
        "hasLast": true,
        "startOffset": 0
    }
}
```

![3](https://github.com/user-attachments/assets/51d26dbd-d2d1-40c2-a503-d1b2c4c6daf1)

服务器的下拉菜单，取返回值，平通知Ping IP或域名，ping1次然后把延迟返回到列表，默认延迟最低到列表，用户可以自己选择 或点击刷新查看最新延迟状态，如果软件为中文界面则取"areaDesc": 内容，如果英文界面则取"serverName": 显示到列表当中，在后面显示延迟。

用户选择好服务器后点击USB或DOIP或Soft，用户是否有权限点击对应按钮，权限判定如下：

重点：判定用户的角色规则--取comboItems套餐列表中的ID判断用户权限和客户端列表允许点击

```
"comboItems": [
            {
                "id": "7e09c882b44e43be8ad40469b912fb80",
                "itemName": "USB国内",
                "areaType": 1,
                "itemSort": 1
            },
            {
                "id": "12c890670f214ce09d363ac7c642d624",
                "itemName": "全球加速",
                "areaType": 2,
                "itemSort": 7
            }
```

 "areaType": 1, 为国内  ； "areaType": 2, 为国际

若只有一个ID  "id": "7e09c882b44e43be8ad40469b912fb80", 则用户只能点击USB按钮，ID写死在软件中判断用。

其中id": "12c890670f214ce09d363ac7c642d624为全球加速，后面会标记用途。（服务端位置）



以下为三个客户端按钮的上报，逻辑通用。

- 上报客户端连接信息
  user/report-client-connection-infomation 请求方式 PUT

- Authorization - Bearer Token == “登录时候的token”

  请求：

  ```
  {
      "connectType": "USB", //此处若客户点击USB则上报USB，  有三个USB或DOIP或SOFT
      "connectIp": "111.23.3.90",  //此处为客户端选择的服务器IP 也可以是域名
      "connectPort": "NPS" 
  }
  ```

      "connectPort": 说明
      //此处为按钮选择，如果usb中则显示连接为nps 其余为frp p2p vpn
      //如果doip下，连接为nps 其余为frp p2p 
      //如果soft下，连接为bridge

  返回：200状态

  

  以下为心跳检测功能，设定心跳上报时间为30秒/次。此处是在点击客户端或服务端时候选择心跳上报

  - 心跳检测
    https://www.bbhcar.top/api/online/check?clientId=&clientType=&heartbeatType= 请求方式 GET

  | 参数          | 说明                                                         |
  | ------------- | ------------------------------------------------------------ |
  | programId     | 应用ID 固定0acc1e73b1ce474db7c2b74a7d1d04af                  |
  | clientId      | 客户端ID，需要生成一个UUID 去除掉-之后的字符串，在同一个检测心跳的流程中应该保持不变 |
  | clientType    | 客户端类型，客户端 S 服务端 C                                |
  | heartbeatType | 心跳类型，登录 LOGIN， 保持 KEEPALIVE                        |

  返回

  ```
  {"onlineStatus": "online"}
  # 如果结果为 offline 则客户端立即下线
  ```

  heartbeatType第一次发要LIGIN然后保持KEEPALIVE。如果超过30秒不上报，则自动离线或异地登录检测。


  
![4](https://github.com/user-attachments/assets/01f29b91-6272-40f3-af47-4d96d384397d)

  以下是服务端接口信息：同时按照心跳方式上报

  /user/client-connection-infomation 

  服务端获取客户端连接信息 请求方式GET

  返回

  ```
  {
      "userId": "147cda6eeba34345ba1d8aaf5bda5a47",
      "connectType": "USB",
      "connectIp": "wcn.bbhcar.com",
      "connectPort": "NPS",
      "vpn": {
          "id": "f5c77c00354749109035dcbad94f9c4d",
          "changeVersion": 0,
          "createdBy": "admin",
          "createdDate": 1742494111000,
          "lastModifiedBy": "admin1",
          "lastModifiedDate": 1742786520000,
          "vpnName": "West China",
          "vpnType": 2,
          "vpnIp": "47.108.67.36",
          "vpnIPSec": "aoiV6AkVArlu/Srl4WkYsw==",
          "username": "/EIel1vx25MVX5JCwKej6A==",
          "password": "1qnc7c/XPO57PvnVlEAA4sBI8x8eF9ycBs0Ev/wcKuWGBUMsTloLHU1ge9W1ba+frM1Hxze/n68lofu8knBhmQ==",
          "vpnDesc": "华西-成都"
      }
  }
  ```

  ```
      取信息如下
      "connectType": "USB",  //连接
      "connectIp": "wcn.bbhcar.com", //服务器
      "connectPort": "NPS"  //端到端
      
      //服务器：
      "vpnName": "West China",  //英文界面取
      "vpnDesc": "华西-成都"  //中文界面取
      
      如果点击全球加速：（此处信息为加密，需要特定方式解密）
      "vpnIPSec": "aoiV6AkVArlu/Srl4WkYsw==",
      "username": "/EIel1vx25MVX5JCwKej6A==",
      "password": "1qnc7c/XPO57PvnVlEAA4sBI8x8eF9ycBs0Ev/wcKuWGBUMsTloLHU1ge9W1ba+frM1Hxze/n68lofu8knBhmQ==",
      
  ```

  查询客户端在线状态--此处在点进服务端端时候，和心跳一起上报和请求

  /online/client-status?programId= 

  GET请求

  Authorization - Bearer Token == “登录时候的token”    //返回：Online为在线

  ```
  {
      "onlineStatus": "offline"
  }
  ```



 工具箱获取接口：
 
![5](https://github.com/user-attachments/assets/19161655-2a94-4c50-be50-2a3e6e57a38c)

- 工具箱列表
  /toolbox/getToolBoxListByToolTypeAndUserType?keyword=b&toolType=USB&userType=1&pageNo=1&pageSize=20 请求方式 GET

- user_type 免费套餐1   //此处请求判定用户套餐是否为Free和Test 只查免费套餐  其余为空

- toolType 分为四种 USB ，DOIP ，SOFT ，SERVER

- 返回

- ```
  {
      "data": [
          {
              "id": "DA95751CE7E1448FAF60A1FFD8BBE037",
              "changeVersion": 0,
              "createdBy": "SYSTEM",
              "createdDate": 1740366766000,
              "toolName": "bbhdesk",  //工具名称
              "toolIcon": "https://ffdkajfldsdjf",  //工具图标
              "toolUrl": "https://ffdkajfldsdjf",  //工具下载链接
              "toolSort": 1,
              "toolType": "USB",  //工具分类
              "userType": 1,      //用户套餐
              "toolDesc": "BBHDesc 是远程控制工具"
          },
  ```

  依照用户选择的工具进行对应的查询

`

  查看公告
/program/announcement 请求方式 GET
返回
```
{
    "id": "070a1b10a5ef4ef6aa478b7cc603bd68",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740408778000,
    "lastModifiedBy": "admin",
    "lastModifiedDate": 1741456428000,
    "announcementCn": "感谢使用BBH共享工具\n官方网站:www.bbhcar.com\n软件支持USB、DOIP等以太网端口的共享实现跨地区诊断用户车辆\n\n--当前版本v5.1.0 更新说明：\n· 升级DOIP模式的车辆连接读取VIN错误",
    "announcementEn": "Thanks for using BBH sharing tool\nOfficial website: www.bbhcar.com\nThe software supports sharing of Ethernet ports such as USB and DOIP to diagnose users' vehicles across regions\n\n--Current version v5.1.0 Update Notes:\n· Upgrade DOIP mode vehicle connection reading VIN error"
}
```
以上接口文档完成！！！
